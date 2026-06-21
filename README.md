// ==========================
// STORAGE.JS
// Website Asset Factory
// ==========================

const StorageManager = {

    // Save Data

    save(key, value) {

        try {

            localStorage.setItem(
                key,
                JSON.stringify(value)
            );

            return true;

        } catch (error) {

            console.error(
                "Storage Save Error:",
                error
            );

            return false;

        }

    },

    // Get Data

    get(key) {

        try {

            const data =
            localStorage.getItem(key);

            return data
                ? JSON.parse(data)
                : null;

        } catch (error) {

            console.error(
                "Storage Read Error:",
                error
            );

            return null;

        }

    },

    // Remove Data

    remove(key) {

        localStorage.removeItem(key);

    },

    // Clear Storage

    clear() {

        localStorage.clear();

    }

};

// ==========================
// LOGO STORAGE
// ==========================

function saveLogoData(data) {

    StorageManager.save(
        "logoData",
        data
    );

}

function getLogoData() {

    return StorageManager.get(
        "logoData"
    );

}

// ==========================
// BANNER STORAGE
// ==========================

function saveBannerData(data) {

    StorageManager.save(
        "bannerData",
        data
    );

}

function getBannerData() {

    return StorageManager.get(
        "bannerData"
    );

}

// ==========================
// OG IMAGE STORAGE
// ==========================

function saveOGData(data) {

    StorageManager.save(
        "ogData",
        data
    );

}

function getOGData() {

    return StorageManager.get(
        "ogData"
    );

}

// ==========================
// FAVICON STORAGE
// ==========================

function saveFaviconData(data) {

    StorageManager.save(
        "faviconData",
        data
    );

}

function getFaviconData() {

    return StorageManager.get(
        "faviconData"
    );

}

// ==========================
// THEME STORAGE
// ==========================

function saveTheme(theme) {

    StorageManager.save(
        "siteTheme",
        theme
    );

}

function getTheme() {

    return StorageManager.get(
        "siteTheme"
    );

}

// ==========================
// RECENT ACTIVITY
// ==========================

function addRecentActivity(action) {

    let activities =
    StorageManager.get(
        "recentActivities"
    ) || [];

    activities.unshift({

        action,
        date:
        new Date()
        .toLocaleString()

    });

    activities =
    activities.slice(0, 10);

    StorageManager.save(
        "recentActivities",
        activities
    );

}

function getRecentActivities() {

    return StorageManager.get(
        "recentActivities"
    ) || [];

}

// ==========================
// PROJECT STATS
// ==========================

function updateStats() {

    let stats =
    StorageManager.get(
        "projectStats"
    ) || {

        logos: 0,
        banners: 0,
        favicons: 0,
        ogImages: 0

    };

    return stats;

}

function increaseStat(type) {

    let stats =
    updateStats();

    if(stats[type] !== undefined){

        stats[type]++;

    }

    StorageManager.save(
        "projectStats",
        stats
    );

}

function getStats() {

    return updateStats();

}

// ==========================
// INIT
// ==========================

console.log(
`
📦 Storage Manager Loaded

Available Storage:
✔ Logo Data
✔ Banner Data
✔ OG Data
✔ Favicon Data
✔ Theme Settings
✔ Recent Activities
✔ Project Statistics
`
);