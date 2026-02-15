body {
    margin: 0;
    font-family: Tahoma,sans-serif;
    color: #fff;
    background-color: #013;
    background-image: linear-gradient(180deg,#0a0a1a,#013);
    background-attachment: fixed;
    transition: background .3s ease
}

body:before {
    content: "";
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-repeat: repeat;
    background-position: center;
    background-size: 250px;
    opacity: .03;
    z-index: 0;
    pointer-events: none;
    transition: background-image .3s ease-in-out;
    background-image: none
}

body.ps-active:before {
    background-image: url(https://i.ibb.co/cqzWFGk/logo.png)
}

body.hp-active:before {
    background-image: url(https://i.ibb.co/M5GygNv4/logo.png)
}

.tabs {
    display: flex;
    justify-content: center;
    gap: 10px;
    margin: 20px auto 0;
    padding: 0 16px;
    max-width: 900px;
    position: relative;
    z-index: 1
}

.tabs button {
    padding: 10px 20px;
    font-size: 16px;
    font-weight: 700;
    border: 2px solid #1c3f91;
    background-color: transparent;
    color: #60a5fa;
    border-radius: 8px;
    cursor: pointer;
    transition: background-color .2s,color .2s
}

.tabs button.active {
    background-color: #1d4ed8;
    color: #fff;
    border-color: #1d4ed8
}

.report-wrap {
    max-width: 900px;
    margin: 28px auto;
    padding: 16px;
    display: none;
    position: relative;
    z-index: 1
}

.report-wrap.active {
    display: block
}

h1 {
    text-align: center;
    margin-bottom: 18px
}

.report-logo {
    display: block;
    margin: 0 auto 24px;
    max-width: 150px;
    height: auto
}

h3 {
    display: flex;
    align-items: center;
    gap: 8px
}

.bar {
    border: 1px dashed #1c3f91;
    padding: 12px;
    margin-bottom: 16px;
    border-radius: 8px
}

.row {
    display: flex;
    gap: 8px;
    align-items: center;
    margin: 6px 0;
    flex-wrap: wrap
}

.label {
    min-width: 110px;
    font-weight: 700
}

select,input[type=text] {
    padding: 6px 8px;
    border: 1px solid #1d4ed8;
    background: #0f172a;
    color: #fff;
    border-radius: 6px
}

.name.readonly {
    background-color: #0a0f1e;
    border-color: #1c3f91;
    cursor: default
}

input[type=radio] {
    accent-color: #1d4ed8;
    vertical-align: middle;
    margin-left: 6px
}

label {
    vertical-align: middle;
    cursor: pointer
}

.units {
    display: flex;
    flex-direction: column;
    gap: 6px
}

.unit-row {
    display: flex;
    align-items: center;
    background: #00000029;
    border-radius: 6px;
    padding: 6px 8px;
    font-family: monospace
}

.center-part {
    display: flex;
    gap: 6px;
    align-items: center;
    flex-grow: 1;
    margin: 0 10px
}

.left-part,.right-part {
    display: flex;
    gap: 4px;
    align-items: center
}

.unit-row.shared {
    background: #00000017
}

.name {
    min-width: 160px
}

.num,.command-num-input {
    width: 60px;
    text-align: center
}

.btn {
    border: 0;
    border-radius: 6px;
    padding: 4px 8px;
    cursor: pointer;
    font-weight: 600
}

.btn.ghost {
    background: transparent;
    border: 1px solid #1d4ed8;
    color: #1d4ed8
}

.btn.icon {
    padding: 4px 6px
}

.btn.main {
    background: #1d4ed8;
    color: #fff
}

.actions {
    display: flex;
    gap: 10px;
    justify-content: center;
    margin: 14px 0;
    flex-wrap: wrap
}

.success {
    text-align: center;
    margin-top: 10px;
    color: #60a5fa;
    font-weight: 700;
    display: none
}

.divider {
    margin: 14px 0;
    border: 0;
    border-top: 1px dashed #1d4ed8
}

.legend-item {
    display: flex;
    align-items: center;
    gap: 8px;
    margin-bottom: 6px
}

.color-box {
    width: 16px;
    height: 16px;
    border-radius: 4px;
    border: 1px solid rgba(255,255,255,.2)
}

.color-box.orange {
    background-color: #fb923c
}

.color-box.red {
    background-color: #f87171
}

.color-box.green {
    background-color: #22c55e
}

.unit-header-row {
    background: transparent!important;
    padding: 10px 0 2px;
    font-weight: 700
}

.unit-header-row .name {
    background: transparent;
    border: none;
    color: #93c5fd;
    font-size: 1.1em;
    padding: 0
}

.site-footer {
    text-align: center;
    padding: 20px 16px;
    margin-top: 20px;
    color: #60a5fa;
    font-size: 14px;
    opacity: .8
}
