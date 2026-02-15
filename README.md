
<!DOCTYPE html>
<html lang="ar" dir="rtl">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width,initial-scale=1" />
    <title>نظام التقارير</title>

      <script type="importmap">
{
  "imports": {
    "vite": "https://esm.sh/vite@^7.3.0",
    "path": "https://esm.sh/path@^0.12.7",
    "url": "https://esm.sh/url@^0.11.4"
  }
}
</script>
  <script type="module" crossorigin src="/assets/index-CJxJGOLZ.js"></script>
  <link rel="stylesheet" crossorigin href="/assets/index-BIK5r2sv.css">
</head>
  <body>
    <div class="tabs">
        <button id="ps-tab" class="active">نموذج تقرير الأمن العام</button>
        <button id="hp-tab">نموذج تقرير أمن الطرق</button>
    </div>

    <div id="ps-wrap" class="report-wrap active">
        <h1>نموذج تقرير الأمن العام</h1>
        <img src="https://i.ibb.co/cqzWFGk/logo.png" alt="شعار الأمن العام" class="report-logo">
        <div class="bar">
          <h3>دليل استخدام</h3>
          <div class="legend-item">
            <span class="color-box orange"></span>
            <span><b>اللون البرتقالي:</b> يعني أن الرمز مكرر.</span>
          </div>
          <div class="legend-item">
            <span class="color-box red"></span>
            <span><b>اللون الأحمر مع خط:</b> يعني أن الوحدة مسجلة خروج.</span>
          </div>
          <div class="legend-item">
            <span class="color-box green"></span>
            <span><b>اللون الأخضر:</b> يعني أن الرمز صحيح ومسجل.</span>
          </div>
        </div>
        <div class="bar">
          <h3>لصق تقرير نائب العمليات السابق</h3>
          <textarea id="ps-pasteArea" rows="10" style="width: 100%; background: #0f172a; color: #fff; border: 1px solid #1d4ed8; border-radius: 6px; padding: 8px; box-sizing: border-box;" placeholder="الصق التقرير هنا..."></textarea>
          <div class="actions">
              <button class="btn main" id="ps-parseReportQuickBtn">تحليل سريع</button>
              <button class="btn ghost" id="ps-clearFormBtn">مسح النموذج</button>
          </div>
          <div id="ps-parseMsg" style="text-align: center; margin-top: 10px; color: #60a5fa; font-weight: 700; display: none;"></div>
        </div>
        <div class="row">
          <div class="label">نوع التقرير:</div>
          <select id="ps-reportType">
            <option value="تحديث 1">تحديث 1</option>
            <option value="تحديث 2">تحديث 2</option>
            <option value="تحديث 3">تحديث 3</option>
            <option value="تحديث 4">تحديث 4</option>
            <option value="تقرير">تقرير</option>
          </select>
        </div>
        <div class="bar">
          <div class="row">
            <div class="label">وقت البداية:</div>
            <select id="ps-startHour"></select>:<select id="ps-startMin"></select>
            <select id="ps-startPeriod">
              <option value="ص">ص</option>
              <option value="م">م</option>
            </select>
          </div>
          <div class="row">
            <div class="label">وقت النهاية:</div>
            <select id="ps-endHour"></select>:<select id="ps-endMin"></select>
            <select id="ps-endPeriod">
              <option value="ص">ص</option>
              <option value="م">م</option>
            </select>
          </div>
        </div>
        <h3>القائمة الرئيسية</h3>
        <div id="ps-mainList" class="units"></div>
        <div id="ps-mainList-actions" class="actions" style="justify-content: flex-start; min-height: 20px;"></div>
        <hr class="divider" />
        <div id="ps-activatedPatrolsSection">
          <h3>الدورات المفعلة</h3>
          <div class="row" style="margin-bottom: 14px;">
            <div class="label" style="min-width: 140px;">نوع الدورات المفعلة:</div>
            <select id="ps-addSectionSelect" style="flex-grow: 1;"></select>
            <button class="btn main" id="ps-addSectionBtn" style="margin-right: 8px;">+ إضافة</button>
          </div>
          <div id="ps-dynamicSectionsContainer"></div>
        </div>
        <hr class="divider" />
        <h3>سين 1 :</h3>
        <div id="ps-s1List" class="units"></div>
        <div id="ps-s1List-actions" class="actions"></div>
        <hr class="divider" />
        <h3>سين 2 :</h3>
        <div id="ps-s2List" class="units"></div>
        <div id="ps-s2List-actions" class="actions"></div>
        <hr class="divider" />
        <h3>باء 1 :</h3>
        <div id="ps-b1List" class="units"></div>
        <div id="ps-b1List-actions" class="actions"></div>
        <hr class="divider" />
        <h3>باء 2 :</h3>
        <div id="ps-b2List" class="units"></div>
        <div id="ps-b2List-actions" class="actions"></div>
        <hr class="divider" />
        <h3>تسجيل خروج</h3>
        <div id="ps-logoutList" class="units"></div>
        <div class="actions">
          <button class="btn ghost" id="ps-addLogout">+ إضافة تسجيل خروج</button>
        </div>
        <hr class="divider" />
        <h3>سبب نزول التقرير مبكرا</h3>
        <div id="ps-earlyReasonSection" class="bar" style="padding-top: 6px; padding-bottom: 6px;">
          <div class="row"><label for="ps-reasonNone"><input type="radio" id="ps-reasonNone" name="ps-earlyReason" value="none" checked>لا يوجد</label></div>
          <div class="row"><label for="ps-reasonRestart"><input type="radio" id="ps-reasonRestart" name="ps-earlyReason" value="restart">ريستارت</label></div>
          <div class="row"><label for="ps-reasonRealignment"><input type="radio" id="ps-reasonRealignment" name="ps-earlyReason" value="realignment">اعادة اصطفاف</label></div>
          <div class="row">
            <label for="ps-reasonOther"><input type="radio" id="ps-reasonOther" name="ps-earlyReason" value="other">اخر:</label>
            <input type="text" id="ps-otherReasonText" placeholder="اكتب السبب هنا" style="display:none; flex-grow: 1; margin-right: 8px;">
          </div>
        </div>
        <div class="actions"><button class="btn main" id="ps-copyBtn">📋 نسخ التقرير</button></div>
        <div class="success" id="ps-okMsg">✅ تم نسخ التقرير</div>
    </div>

    <div id="hp-wrap" class="report-wrap">
        <h1>نموذج تقرير أمن الطرق</h1>
        <img src="https://i.ibb.co/M5GygNv4/logo.png" alt="شعار أمن الطرق" class="report-logo">
        <div class="bar">
          <h3>دليل استخدام</h3>
          <div class="legend-item">
            <span class="color-box orange"></span>
            <span><b>اللون البرتقالي:</b> يعني أن الرمز مكرر.</span>
          </div>
          <div class="legend-item">
            <span class="color-box red"></span>
            <span><b>اللون الأحمر مع خط:</b> يعني أن الوحدة مسجلة خروج.</span>
          </div>
          <div class="legend-item">
            <span class="color-box green"></span>
            <span><b>اللون الأخضر:</b> يعني أن الرمز صحيح ومسجل.</span>
          </div>
        </div>
        <div class="bar">
          <h3>لصق تقرير نائب العمليات السابق</h3>
          <textarea id="hp-pasteArea" rows="10" style="width: 100%; background: #0f172a; color: #fff; border: 1px solid #1d4ed8; border-radius: 6px; padding: 8px; box-sizing: border-box;" placeholder="الصق التقرير هنا..."></textarea>
          <div class="actions">
              <button class="btn main" id="hp-parseReportQuickBtn">تحليل سريع</button>
              <button class="btn ghost" id="hp-clearFormBtn">مسح النموذج</button>
          </div>
          <div id="hp-parseMsg" style="text-align: center; margin-top: 10px; font-weight: 700; display: none;"></div>
        </div>
        <div class="row">
          <div class="label">نوع التقرير:</div>
          <select id="hp-reportType">
            <option value="تحديث 1">تحديث 1</option>
            <option value="تحديث 2">تحديث 2</option>
            <option value="تحديث 3">تحديث 3</option>
            <option value="تحديث 4">تحديث 4</option>
            <option value="تقرير">تقرير</option>
          </select>
        </div>
        <div class="bar">
          <div class="row">
            <div class="label">وقت البداية:</div>
            <select id="hp-startHour"></select>:<select id="hp-startMin"></select>
            <select id="hp-startPeriod">
              <option value="ص">ص</option>
              <option value="م">م</option>
            </select>
          </div>
          <div class="row">
            <div class="label">وقت النهاية:</div>
            <select id="hp-endHour"></select>:<select id="hp-endMin"></select>
            <select id="hp-endPeriod">
              <option value="ص">ص</option>
              <option value="م">م</option>
            </select>
          </div>
        </div>
        <h3>القائمة الرئيسية</h3>
        <div id="hp-mainList" class="units"></div>
        <div id="hp-mainList-actions" class="actions" style="justify-content: flex-start; min-height: 20px;"></div>
        <hr class="divider" />
        <div id="hp-activatedPatrolsSection">
          <h3>الدورات المفعلة</h3>
          <div class="row" style="margin-bottom: 14px;">
            <div class="label" style="min-width: 140px;">نوع الدورات المفعلة:</div>
            <select id="hp-addSectionSelect" style="flex-grow: 1;"></select>
            <button class="btn main" id="hp-addSectionBtn" style="margin-right: 8px;">+ إضافة</button>
          </div>
          <div id="hp-dynamicSectionsContainer"></div>
        </div>
        <hr class="divider" />
        <h3>جيم :</h3>
        <div id="hp-s1List" class="units"></div>
        <div id="hp-s1List-actions" class="actions"></div>
        <hr class="divider" />
        <h3>لام :</h3>
        <div id="hp-s2List" class="units"></div>
        <div id="hp-s2List-actions" class="actions"></div>
        <hr class="divider" />
        <h3>دال 1 :</h3>
        <div id="hp-d1List" class="units"></div>
        <div id="hp-d1List-actions" class="actions"></div>
        <hr class="divider" />
        <h3>دال 2 :</h3>
        <div id="hp-d2List" class="units"></div>
        <div id="hp-d2List-actions" class="actions"></div>
        <hr class="divider" />
        <h3>تسجيل خروج</h3>
        <div id="hp-logoutList" class="units"></div>
        <div class="actions">
          <button class="btn ghost" id="hp-addLogout">+ إضافة تسجيل خروج</button>
        </div>
        <hr class="divider" />
        <h3>سبب نزول التقرير مبكرا</h3>
        <div id="hp-earlyReasonSection" class="bar" style="padding-top: 6px; padding-bottom: 6px;">
          <div class="row"><label for="hp-reasonNone"><input type="radio" id="hp-reasonNone" name="hp-earlyReason" value="none" checked>لا يوجد</label></div>
          <div class="row"><label for="hp-reasonRestart"><input type="radio" id="hp-reasonRestart" name="hp-earlyReason" value="restart">ريستارت</label></div>
          <div class="row"><label for="hp-reasonRealignment"><input type="radio" id="hp-reasonRealignment" name="hp-earlyReason" value="realignment">اعادة اصطفاف</label></div>
          <div class="row">
            <label for="hp-reasonOther"><input type="radio" id="hp-reasonOther" name="hp-earlyReason" value="other">اخر:</label>
            <input type="text" id="hp-otherReasonText" placeholder="اكتب السبب هنا" style="display:none; flex-grow: 1; margin-right: 8px;">
          </div>
        </div>
        <div class="actions"><button class="btn main" id="hp-copyBtn">📋 نسخ التقرير</button></div>
        <div class="success" id="hp-okMsg">✅ تم نسخ التقرير</div>
    </div>

    <footer class="site-footer">
      © جميع الحقوق محفوظة لدى قيادة الامن العام في مقاطعة بوليتو
    </footer>

</body>
</html>
