// Switch between tabs
function showTab(tabName) {
    const tabs = document.querySelectorAll('.tab'); // Get all tabs
    tabs.forEach(tab => tab.style.display = 'none'); // Hide all tabs
    document.getElementById(tabName).style.display = 'block'; // Show the selected tab
}

// Initially show the "writing" tab by default
showTab('writing');

// Word count update for novel writing
const novelTextArea = document.getElementById('novel-text');
novelTextArea.addEventListener('input', function() {
    const wordCount = novelTextArea.value.split(/\s+/).filter(word => word.length > 0).length;
    document.getElementById('word-count').innerText = 'Word count: ' + wordCount;
});

// Save and load novel text
function saveText() {
    const text = novelTextArea.value;
    localStorage.setItem('novelText', text);
    alert('Text saved!');
}

function loadText() {
    const savedText = localStorage.getItem('novelText');
    if (savedText) {
        novelTextArea.value = savedText;
    } else {
        alert('No saved text found!');
    }
}

// Canvas drawing (simple)
const canvas = document.getElementById('draw-canvas');
const ctx = canvas.getContext('2d');
let drawing = false;

canvas.addEventListener('mousedown', function(e) {
    drawing = true;
    ctx.beginPath();
    ctx.moveTo(e.offsetX, e.offsetY);
});

canvas.addEventListener('mousemove', function(e) {
    if (drawing) {
        ctx.lineTo(e.offsetX, e.offsetY);
        ctx.stroke();
    }
});

canvas.addEventListener('mouseup', function() {
    drawing = false;
});

function clearCanvas() {
    <Canva id="draw-canvas"width="500" height="300"></canva>
// Character profile management
let characterList = JSON.parse(localStorage.getItem('characters')) || [];

function saveCharacter() {
    const charName = document.getElementById('char-name').value;
    const charDescription = document.getElementById('char-description').value;

    if (charName && charDescription) {
        const newCharacter = { name: charName, description: charDescription };
        characterList.push(newCharacter);
        localStorage.setItem('characters', JSON.stringify(characterList));
        updateCharacterList();
    }
}

function updateCharacterList() {
    const charListDiv = document.getElementById('character-list');
    charListDiv.innerHTML = '';
    characterList.forEach((char, index) => {
        const charItem = document.createElement('div');
        charItem.classList.add('character-item');
        charItem.innerHTML = `<strong>${char.name}</strong>: ${char.description}`;
        charListDiv.appendChild(charItem);
    });
}

updateCharacterList(); // Initially load character profiles

<script src="scripts.js"></script>




