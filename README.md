// Ransomware Time Machine — educational demo

const files = [
    { name: "report.txt", content: "Original report", status: "Safe" },
    { name: "notes.txt", content: "Original notes", status: "Safe" },
    { name: "project.txt", content: "Project data", status: "Safe" }
];

// Save a clean snapshot
function takeSnapshot() {
    const snapshot = JSON.parse(JSON.stringify(files));
    console.log("Snapshot created successfully!");
    return snapshot;
}

// Simulate a ransomware attack
function simulateAttack() {
    files.forEach(file => {
        file.content = "[SIMULATED ENCRYPTED DATA]";
        file.status = "Damaged";
    });

    console.log("Warning: suspicious file changes detected!");
    displayFiles();
}

// Restore files from the snapshot
function restoreSnapshot(snapshot) {
    snapshot.forEach(savedFile => {
        const file = files.find(f => f.name === savedFile.name);

        if (file) {
            file.content = savedFile.content;
            file.status = "Restored";
        }
    });

    console.log("Recovery completed!");
    displayFiles();
}

// Display current file states
function displayFiles() {
    console.table(files);
}

// Run the demonstration
const backup = takeSnapshot();

simulateAttack();

restoreSnapshot(backup);
