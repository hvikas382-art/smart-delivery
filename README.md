# smart-delivery
Smart Delivery is a web-based delivery management system that helps delivery personnel manage packages, prioritize deliveries, and find the shortest delivery route using Dijkstra’s Algorithm.
<!DOCTYPE html>
<html lang="en">

<head>

<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Smart Delivery - Delivery Boy</title>

<style>

/* =====================================================
   BASIC
===================================================== */

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: Arial, Helvetica, sans-serif;
}

body {
    background: #f1f5f9;
    color: #1e293b;
}


/* =====================================================
   LOGIN PAGE
===================================================== */

#loginPage {

    min-height: 100vh;

    display: flex;
    justify-content: center;
    align-items: center;

    background:
    linear-gradient(
        135deg,
        #0f172a,
        #1e3a8a
    );
}


.login-box {

    width: 390px;

    background: white;

    padding: 40px;

    border-radius: 18px;

    box-shadow:
    0 20px 50px rgba(0,0,0,.3);
}


.logo {

    text-align: center;

    font-size: 45px;

    margin-bottom: 10px;
}


.login-box h1 {

    text-align: center;

    color: #0f172a;
}


.subtitle {

    text-align: center;

    color: #64748b;

    margin:
    8px 0 30px;
}


.input-group {

    margin-bottom: 20px;
}


.input-group label {

    display: block;

    font-weight: bold;

    margin-bottom: 7px;
}


.input-group input {

    width: 100%;

    padding: 13px;

    border:
    1px solid #cbd5e1;

    border-radius: 8px;

    font-size: 15px;

    outline: none;
}


.input-group input:focus {

    border-color: #2563eb;
}


/* PASSWORD */

.password-wrapper {

    position: relative;
}


.password-wrapper input {

    padding-right: 50px;
}


.password-toggle {

    position: absolute;

    right: 8px;

    top: 50%;

    transform:
    translateY(-50%);

    border: none;

    background: transparent;

    cursor: pointer;

    font-size: 20px;
}


/* LOGIN BUTTON */

.login-btn {

    width: 100%;

    padding: 14px;

    background: #2563eb;

    color: white;

    border: none;

    border-radius: 8px;

    font-size: 16px;

    font-weight: bold;

    cursor: pointer;
}


.login-btn:hover {

    background: #1d4ed8;
}


.login-error {

    color: #dc2626;

    text-align: center;

    margin-top: 15px;

    display: none;
}


.login-info {

    margin-top: 20px;

    padding: 12px;

    background: #eff6ff;

    border-radius: 8px;

    color: #1e40af;

    font-size: 13px;
}


/* =====================================================
   DASHBOARD
===================================================== */

#dashboard {

    display: none;
}


/* NAVBAR */

.navbar {

    background: #0f172a;

    color: white;

    height: 70px;

    padding: 0 5%;

    display: flex;

    align-items: center;

    justify-content: space-between;
}


.navbar-left {

    display: flex;

    align-items: center;

    gap: 12px;
}


.navbar-logo {

    font-size: 30px;
}


.navbar h2 span {

    color: #60a5fa;
}


.profile {

    display: flex;

    align-items: center;

    gap: 15px;
}


.logout-btn {

    padding:
    9px 16px;

    background: #dc2626;

    color: white;

    border: none;

    border-radius: 7px;

    cursor: pointer;
}


.logout-btn:hover {

    background: #b91c1c;
}


/* MAIN */

.container {

    width: 92%;

    max-width: 1250px;

    margin: 30px auto;
}


/* =====================================================
   WELCOME
===================================================== */

.welcome {

    background:
    linear-gradient(
        135deg,
        #2563eb,
        #1e40af
    );

    color: white;

    padding: 28px;

    border-radius: 15px;

    margin-bottom: 25px;
}


.welcome h1 {

    margin-bottom: 8px;
}


/* =====================================================
   STATISTICS
===================================================== */

.stats {

    display: grid;

    grid-template-columns:
    repeat(4,1fr);

    gap: 18px;

    margin-bottom: 25px;
}


.stat-card {

    background: white;

    padding: 22px;

    border-radius: 12px;

    box-shadow:
    0 4px 15px rgba(0,0,0,.07);

    cursor: pointer;

    transition: .2s;
}


.stat-card:hover {

    transform:
    translateY(-4px);

    box-shadow:
    0 8px 20px rgba(0,0,0,.12);
}


.stat-card.active {

    border:
    3px solid #2563eb;
}


.stat-icon {

    font-size: 27px;

    margin-bottom: 8px;
}


.stat-card h3 {

    color: #64748b;

    font-size: 14px;
}


.stat-card p {

    font-size: 30px;

    font-weight: bold;

    margin-top: 7px;
}


/* =====================================================
   MAIN GRID
===================================================== */

.main-grid {

    display: grid;

    grid-template-columns:
    1.1fr 1fr;

    gap: 25px;
}


.section {

    background: white;

    border-radius: 14px;

    padding: 23px;

    box-shadow:
    0 4px 15px rgba(0,0,0,.07);

    margin-bottom: 25px;
}


.section-title {

    display: flex;

    justify-content:
    space-between;

    align-items: center;

    margin-bottom: 18px;
}


/* =====================================================
   PACKAGE CARD
===================================================== */

.package-card {

    border:
    1px solid #e2e8f0;

    border-radius: 12px;

    padding: 17px;

    margin-bottom: 12px;

    cursor: pointer;

    position: relative;

    transition: .2s;
}


.package-card:hover {

    border-color: #2563eb;

    transform:
    translateY(-2px);
}


.package-card.selected {

    border:
    2px solid #2563eb;

    background: #eff6ff;
}


.priority-number {

    position: absolute;

    top: 15px;

    left: 15px;

    width: 30px;

    height: 30px;

    border-radius: 50%;

    background: #2563eb;

    color: white;

    display: flex;

    align-items: center;

    justify-content: center;

    font-weight: bold;
}


.package-content {

    margin-left: 45px;
}


.package-header {

    display: flex;

    justify-content:
    space-between;

    align-items: center;
}


.priority {

    padding:
    5px 10px;

    border-radius: 20px;

    font-size: 12px;

    font-weight: bold;
}


.express {

    background: #fee2e2;

    color: #dc2626;
}


.same-day {

    background: #ffedd5;

    color: #ea580c;
}


.standard {

    background: #dcfce7;

    color: #16a34a;
}


.package-info {

    margin-top: 10px;

    color: #64748b;

    font-size: 14px;

    line-height: 1.8;
}


.tracking {

    color: #2563eb;

    font-weight: bold;
}


/* =====================================================
   DETAILS
===================================================== */

.no-selection {

    height: 300px;

    display: flex;

    align-items: center;

    justify-content: center;

    color: #94a3b8;

    text-align: center;
}


.details-content {

    display: none;
}


.details-row {

    display: flex;

    justify-content:
    space-between;

    padding: 13px 0;

    border-bottom:
    1px solid #e2e8f0;
}


.details-row span:first-child {

    color: #64748b;
}


.details-row span:last-child {

    font-weight: bold;
}


.destination-box {

    margin-top: 20px;

    padding: 17px;

    background: #eff6ff;

    border-radius: 10px;
}


.destination-box h3 {

    color: #1d4ed8;

    margin-bottom: 8px;
}


/* =====================================================
   BUTTONS
===================================================== */

.route-btn {

    width: 100%;

    padding: 13px;

    margin-top: 20px;

    background: #16a34a;

    color: white;

    border: none;

    border-radius: 8px;

    font-weight: bold;

    cursor: pointer;
}


.route-btn:hover {

    background: #15803d;
}


.status-btn {

    width: 100%;

    padding: 12px;

    margin-top: 10px;

    background: #f59e0b;

    color: white;

    border: none;

    border-radius: 8px;

    font-weight: bold;

    cursor: pointer;
}


/* =====================================================
   SHORTEST ROUTE RESULT
===================================================== */

.route-result {

    margin-top: 20px;

    padding: 20px;

    background: #f0fdf4;

    border:
    1px solid #bbf7d0;

    border-radius: 10px;

    display: none;
}


.route-result h3 {

    color: #15803d;

    margin-bottom: 15px;
}


.route-distance {

    font-size: 28px;

    font-weight: bold;

    color: #15803d;

    margin: 10px 0;
}


.route-path {

    margin-top: 15px;

    padding: 15px;

    background: white;

    border-radius: 8px;

    color: #166534;

    font-weight: bold;

    line-height: 1.8;
}


/* =====================================================
   ALGORITHM INFO
===================================================== */

.algorithm-info {

    background: #f8fafc;

    border:
    1px solid #e2e8f0;

    padding: 20px;

    border-radius: 10px;

    line-height: 1.8;

    font-size: 14px;
}


/* EMPTY */

.empty {

    padding: 40px;

    text-align: center;

    color: #94a3b8;
}


/* =====================================================
   RESPONSIVE
===================================================== */

@media(max-width:900px) {

    .stats {

        grid-template-columns:
        repeat(2,1fr);
    }

    .main-grid {

        grid-template-columns: 1fr;
    }
}


@media(max-width:600px) {

    .stats {

        grid-template-columns:
        1fr 1fr;
    }

    .navbar {

        padding: 0 15px;
    }

    .driver-name {

        display: none;
    }

    .container {

        width: 94%;
    }

    .package-header {

        flex-direction: column;

        align-items: flex-start;

        gap: 8px;
    }
}

</style>

</head>


<body>


<!-- =====================================================
     LOGIN
===================================================== -->

<div id="loginPage">

    <div class="login-box">

        <div class="logo">
            🚚
        </div>

        <h1>
            Smart Delivery
        </h1>

        <p class="subtitle">
            Delivery Boy Login
        </p>


        <!-- USERNAME -->

        <div class="input-group">

            <label>
                Username
            </label>

            <input
                type="text"
                id="username"
                placeholder="Enter username"
            >

        </div>


        <!-- PASSWORD -->

        <div class="input-group">

            <label>
                Password
            </label>

            <div class="password-wrapper">

                <input
                    type="password"
                    id="password"
                    placeholder="Enter password"
                >

                <button
                    type="button"
                    class="password-toggle"
                    onclick="togglePassword()"
                    id="eyeButton"
                >
                    👁️
                </button>

            </div>

        </div>


        <button
            class="login-btn"
            onclick="login()"
        >
            Login
        </button>


        <p
            id="loginError"
            class="login-error"
        >
            ❌ Invalid username or password
        </p>


        <div class="login-info">

            <strong>
                Demo Login
            </strong>

            <br><br>

            Username:
            deliveryboy@123

            <br>

            Password:
            delivery@258

        </div>

    </div>

</div>



<!-- =====================================================
     DASHBOARD
===================================================== -->

<div id="dashboard">


    <!-- NAVBAR -->

    <nav class="navbar">

        <div class="navbar-left">

            <div class="navbar-logo">
                🚚
            </div>

            <h2>
                Smart<span>Delivery</span>
            </h2>

        </div>


        <div class="profile">

            <span class="driver-name">
                👤 Delivery Boy
            </span>

            <button
                class="logout-btn"
                onclick="logout()"
            >
                Logout
            </button>

        </div>

    </nav>



    <div class="container">


        <!-- WELCOME -->

        <div class="welcome">

            <h1>
                Welcome, Delivery Boy 👋
            </h1>

            <p>
                Deliver packages according to priority
                using the shortest route.
            </p>

        </div>



        <!-- =================================================
             STATISTICS
        ================================================== -->

        <div class="stats">


            <!-- ALL -->

            <div
                class="stat-card active"
                id="allCard"
                onclick="filterPackages('All')"
            >

                <div class="stat-icon">
                    📦
                </div>

                <h3>
                    Total Packages
                </h3>

                <p id="totalPackages">
                    5
                </p>

            </div>


            <!-- EXPRESS -->

            <div
                class="stat-card"
                onclick="filterPackages('Express')"
            >

                <div class="stat-icon">
                    🔴
                </div>

                <h3>
                    Express Packages
                </h3>

                <p id="expressCount">
                    2
                </p>

            </div>


            <!-- SAME DAY -->

            <div
                class="stat-card"
                onclick="filterPackages('Same-day')"
            >

                <div class="stat-icon">
                    🟠
                </div>

                <h3>
                    Same-day Packages
                </h3>

                <p id="sameDayCount">
                    1
                </p>

            </div>


            <!-- STANDARD -->

            <div
                class="stat-card"
                onclick="filterPackages('Standard')"
            >

                <div class="stat-icon">
                    🟢
                </div>

                <h3>
                    Standard Packages
                </h3>

                <p id="standardCount">
                    2
                </p>

            </div>

        </div>



        <!-- =================================================
             MAIN
        ================================================== -->

        <div class="main-grid">


            <!-- PACKAGE LIST -->

            <div class="section">

                <div class="section-title">

                    <h2>
                        📦 Assigned Packages
                    </h2>

                    <span id="filterText">
                        All Packages
                    </span>

                </div>


                <div id="packageList">
                </div>

            </div>



            <!-- DETAILS -->

            <div class="section">

                <div class="section-title">

                    <h2>
                        📍 Package Details
                    </h2>

                </div>


                <div
                    id="noSelection"
                    class="no-selection"
                >

                    <div>

                        <div style="font-size:45px;">
                            📦
                        </div>

                        <p>
                            Click a package to see
                            delivery details.
                        </p>

                    </div>

                </div>


                <div
                    id="detailsContent"
                    class="details-content"
                >

                    <div class="details-row">

                        <span>
                            Customer
                        </span>

                        <span id="detailCustomer">
                        </span>

                    </div>


                    <div class="details-row">

                        <span>
                            Tracking ID
                        </span>

                        <span
                            id="detailTracking"
                            class="tracking"
                        >
                        </span>

                    </div>


                    <div class="details-row">

                        <span>
                            Priority
                        </span>

                        <span id="detailPriority">
                        </span>

                    </div>


                    <div class="details-row">

                        <span>
                            Current Location
                        </span>

                        <span id="detailCurrent">
                        </span>

                    </div>


                    <div class="destination-box">

                        <h3>
                            🏠 Delivery Destination
                        </h3>

                        <p id="detailDestination">
                        </p>

                    </div>


                    <button
                        class="route-btn"
                        onclick="findShortestRoute()"
                    >
                        📏 Find Shortest Distance
                    </button>


                    <button
                        class="status-btn"
                        onclick="markDelivered()"
                    >
                        ✅ Mark Package as Delivered
                    </button>


                    <!-- RESULT -->

                    <div
                        id="routeResult"
                        class="route-result"
                    >

                        <h3>
                            ✅ Shortest Route Found
                        </h3>


                        <p>
                            Algorithm Used:
                            <strong>
                                Dijkstra's Algorithm
                            </strong>
                        </p>


                        <div
                            class="route-distance"
                            id="routeDistance"
                        >
                        </div>


                        <div class="route-path">

                            <strong>
                                🚚 Shortest Route
                            </strong>

                            <br><br>

                            <span id="routePath">
                            </span>

                        </div>

                    </div>

                </div>

            </div>

        </div>



        <!-- =================================================
             DSA EXPLANATION
        ================================================== -->

        <div class="section">

            <div class="section-title">

                <h2>
                    🧠 Dijkstra Route Information
                </h2>

            </div>


            <div class="algorithm-info">

                <strong>
                    How the system finds the shortest distance:
                </strong>

                <br><br>

                The delivery locations are represented
                as a weighted graph.

                <br><br>

                <strong>
                    Nodes:
                </strong>

                Mangaluru,
                Vamanjoor,
                St Joseph Engineering College,
                Puttur

                <br><br>

                <strong>
                    Edges:
                </strong>

                Roads connecting the locations.

                <br><br>

                <strong>
                    Edge Weight:
                </strong>

                Distance in kilometres.

                <br><br>

                When the delivery boy selects a package,
                the system uses
                <strong>
                    Dijkstra's Algorithm
                </strong>
                to calculate the shortest route from
                Mangaluru to the package destination.

            </div>

        </div>


    </div>

</div>



<script>

/* =====================================================
   LOGIN
===================================================== */

const correctUsername =
    "deliveryboy@123";

const correctPassword =
    "delivery@258";


function login() {

    const username =
        document.getElementById(
            "username"
        ).value;

    const password =
        document.getElementById(
            "password"
        ).value;


    if (
        username === correctUsername &&
        password === correctPassword
    ) {

        document.getElementById(
            "loginPage"
        ).style.display = "none";


        document.getElementById(
            "dashboard"
        ).style.display = "block";


        document.getElementById(
            "loginError"
        ).style.display = "none";


        loadPackages();

    }

    else {

        document.getElementById(
            "loginError"
        ).style.display = "block";

    }

}


/* =====================================================
   SHOW / HIDE PASSWORD
===================================================== */

function togglePassword() {

    const password =
        document.getElementById(
            "password"
        );

    const eye =
        document.getElementById(
            "eyeButton"
        );


    if (
        password.type === "password"
    ) {

        password.type = "text";

        eye.innerText = "🙈";

    }

    else {

        password.type = "password";

        eye.innerText = "👁️";

    }

}


/* =====================================================
   LOGOUT
===================================================== */

function logout() {

    document.getElementById(
        "dashboard"
    ).style.display = "none";


    document.getElementById(
        "loginPage"
    ).style.display = "flex";


    document.getElementById(
        "username"
    ).value = "";


    document.getElementById(
        "password"
    ).value = "";

}


/* =====================================================
   PACKAGES
===================================================== */

let packages = [

    {
        id: "PKG-LR-001",

        customer: "Likith Raj",

        priority: "Express",

        current: "Mangaluru",

        destination: "Puttur",

        status: "Pending"
    },


    {
        id: "PKG-SV-002",

        customer: "Savan",

        priority: "Express",

        current: "Mangaluru",

        destination: "Vamanjoor",

        status: "Pending"
    },


    {
        id: "PKG-VM-003",

        customer: "Vijith M",

        priority: "Same-day",

        current: "Mangaluru",

        destination:
        "St Joseph Engineering College",

        status: "Pending"
    },


    {
        id: "PKG-MK-004",

        customer: "Malikarjun",

        priority: "Standard",

        current: "Mangaluru",

        destination: "Vamanjoor",

        status: "Pending"
    },


    {
        id: "PKG-VK-005",

        customer: "Vikas",

        priority: "Standard",

        current: "Mangaluru",

        destination: "Vamanjoor",

        status: "Pending"
    }

];


/* =====================================================
   PRIORITY
===================================================== */

function priorityValue(priority) {

    if (
        priority === "Express"
    )
        return 1;


    if (
        priority === "Same-day"
    )
        return 2;


    return 3;

}


/* =====================================================
   FILTER
===================================================== */

let currentFilter = "All";


function filterPackages(filter) {

    currentFilter = filter;


    document
        .querySelectorAll(".stat-card")
        .forEach(
            card =>
            card.classList.remove(
                "active"
            )
        );


    if (filter === "All") {

        document
            .getElementById(
                "allCard"
            )
            .classList.add(
                "active"
            );

    }


    event.currentTarget.classList.add(
        "active"
    );


    if (filter === "All") {

        document.getElementById(
            "filterText"
        ).innerText =
            "All Packages";

    }

    else {

        document.getElementById(
            "filterText"
        ).innerText =
            filter +
            " Packages";

    }


    renderPackages();

}


/* =====================================================
   RENDER PACKAGES
===================================================== */

function renderPackages() {

    let sorted =
        [...packages];


    /*
        Priority sorting
    */

    sorted.sort(
        (a,b) =>
        priorityValue(a.priority)
        -
        priorityValue(b.priority)
    );


    /*
        Filter
    */

    if (
        currentFilter !== "All"
    ) {

        sorted =
            sorted.filter(
                p =>
                p.priority ===
                currentFilter
            );

    }


    const list =
        document.getElementById(
            "packageList"
        );


    list.innerHTML = "";


    if (
        sorted.length === 0
    ) {

        list.innerHTML = `
            <div class="empty">
                No packages available.
            </div>
        `;

        return;

    }


    sorted.forEach(
        (pkg,index) => {


        let priorityClass =
            pkg.priority
            .toLowerCase()
            .replace(
                " ",
                "-"
            );


        const card =
            document.createElement(
                "div"
            );


        card.className =
            "package-card";


        card.onclick =
            function() {

                showPackage(
                    pkg
                );

            };


        card.innerHTML = `

            <div class="priority-number">
                ${index + 1}
            </div>


            <div class="package-content">


                <div class="package-header">

                    <h3>
                        ${pkg.customer}
                    </h3>


                    <span
                        class="
                        priority
                        ${priorityClass}
                        "
                    >
                        ${pkg.priority}
                    </span>

                </div>


                <div class="package-info">


                    <div>

                        📦 Tracking:

                        <span
                            class="tracking"
                        >
                            ${pkg.id}
                        </span>

                    </div>


                    <div>

                        📍 From:

                        ${pkg.current}

                    </div>


                    <div>

                        🏠 To:

                        ${pkg.destination}

                    </div>


                    <div>

                        Status:

                        ${pkg.status}

                    </div>


                </div>


            </div>

        `;


        list.appendChild(
            card
        );

    });

}


/* =====================================================
   LOAD
===================================================== */

function loadPackages() {

    packages.sort(
        (a,b) =>
        priorityValue(
            a.priority
        )
        -
        priorityValue(
            b.priority
        )
    );


    updateStatistics();

    renderPackages();

}


/* =====================================================
   STATISTICS
===================================================== */

function updateStatistics() {

    document.getElementById(
        "totalPackages"
    ).innerText =
        packages.length;


    document.getElementById(
        "expressCount"
    ).innerText =
        packages.filter(
            p =>
            p.priority ===
            "Express"
        ).length;


    document.getElementById(
        "sameDayCount"
    ).innerText =
        packages.filter(
            p =>
            p.priority ===
            "Same-day"
        ).length;


    document.getElementById(
        "standardCount"
    ).innerText =
        packages.filter(
            p =>
            p.priority ===
            "Standard"
        ).length;

}


/* =====================================================
   SELECT PACKAGE
===================================================== */

let selectedPackage = null;


function showPackage(pkg) {

    selectedPackage =
        pkg;


    document.getElementById(
        "noSelection"
    ).style.display =
        "none";


    document.getElementById(
        "detailsContent"
    ).style.display =
        "block";


    document.getElementById(
        "detailCustomer"
    ).innerText =
        pkg.customer;


    document.getElementById(
        "detailTracking"
    ).innerText =
        pkg.id;


    document.getElementById(
        "detailPriority"
    ).innerText =
        pkg.priority;


    document.getElementById(
        "detailCurrent"
    ).innerText =
        pkg.current;


    document.getElementById(
        "detailDestination"
    ).innerText =
        pkg.destination;


    document.getElementById(
        "routeResult"
    ).style.display =
        "none";

}


/* =====================================================
   GRAPH
===================================================== */

const graph = {


    "Mangaluru": {

        "Vamanjoor": 8,

        "Puttur": 18,

        "St Joseph Engineering College": 12

    },


    "Vamanjoor": {

        "Mangaluru": 8,

        "St Joseph Engineering College": 5,

        "Puttur": 15

    },


    "St Joseph Engineering College": {

        "Mangaluru": 12,

        "Vamanjoor": 5,

        "Puttur": 10

    },


    "Puttur": {

        "Mangaluru": 18,

        "Vamanjoor": 15,

        "St Joseph Engineering College": 10

    }

};


/* =====================================================
   DIJKSTRA
===================================================== */

function dijkstra(
    graph,
    start,
    target
) {

    let distances = {};

    let previous = {};

    let visited =
        new Set();


    /*
        Initialize
    */

    for (
        let node in graph
    ) {

        distances[node] =
            Infinity;

        previous[node] =
            null;

    }


    distances[start] = 0;


    /*
        Main loop
    */

    while (
        visited.size
        <
        Object.keys(
            graph
        ).length
    ) {


        let current =
            null;


        let smallest =
            Infinity;


        /*
            Find nearest
            unvisited node
        */

        for (
            let node in distances
        ) {

            if (
                !visited.has(
                    node
                )
                &&
                distances[node]
                <
                smallest
            ) {

                smallest =
                    distances[node];

                current =
                    node;

            }

        }


        if (
            current === null
        )
            break;


        visited.add(
            current
        );


        /*
            Check neighbors
        */

        for (
            let neighbor
            in graph[current]
        ) {


            let distance =
                graph[current]
                [neighbor];


            let newDistance =
                distances[current]
                +
                distance;


            if (
                newDistance
                <
                distances[
                    neighbor
                ]
            ) {

                distances[
                    neighbor
                ] =
                    newDistance;


                previous[
                    neighbor
                ] =
                    current;

            }

        }

    }


    /*
        Build path
    */

    let path = [];

    let current =
        target;


    while (
        current !== null
    ) {

        path.unshift(
            current
        );


        current =
            previous[
                current
            ];

    }


    return {

        distance:
            distances[target],

        path:
            path

    };

}


/* =====================================================
   FIND SHORTEST DISTANCE
===================================================== */

function findShortestRoute() {

    if (
        !selectedPackage
    ) {

        alert(
            "Please select a package first."
        );

        return;

    }


    let destination =
        selectedPackage
        .destination;


    /*
        Convert destination
        to graph node
    */

    if (
        destination.includes(
            "Vamanjoor"
        )
    ) {

        destination =
            "Vamanjoor";

    }


    else if (
        destination.includes(
            "Puttur"
        )
    ) {

        destination =
            "Puttur";

    }


    else if (
        destination.includes(
            "St Joseph"
        )
    ) {

        destination =
            "St Joseph Engineering College";

    }


    /*
        Run Dijkstra
    */

    const result =
        dijkstra(
            graph,
            "Mangaluru",
            destination
        );


    /*
        Display
    */

    document.getElementById(
        "routeResult"
    ).style.display =
        "block";


    document.getElementById(
        "routeDistance"
    ).innerText =
        result.distance +
        " km";


    document.getElementById(
        "routePath"
    ).innerText =
        result.path.join(
            "  →  "
        );

}


/* =====================================================
   MARK DELIVERED
===================================================== */

function markDelivered() {

    if (
        !selectedPackage
    ) {

        alert(
            "Please select a package first."
        );

        return;

    }


    selectedPackage.status =
        "Delivered";


    alert(
        selectedPackage.customer +
        "'s package has been delivered!"
    );


    updateStatistics();

    renderPackages();


    document.getElementById(
        "detailsContent"
    ).style.display =
        "none";


    document.getElementById(
        "noSelection"
    ).style.display =
        "flex";


    selectedPackage =
        null;

}


/* =====================================================
   ENTER KEY LOGIN
===================================================== */

document
    .getElementById(
        "password"
    )
    .addEventListener(
        "keypress",
        function(event) {

            if (
                event.key ===
                "Enter"
            ) {

                login();

            }

        }
    );

</script>

</body>

</html>


