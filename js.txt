const data = {
    questions: [
        { en: "What", pt: ["o que", "qual"] },
        { en: "Who", pt: ["quem"] },
        { en: "Where", pt: ["onde"] },
        { en: "When", pt: ["quando"] },
        { en: "Why", pt: ["por que", "porque"] },
        { en: "Which", pt: ["qual"] },
        { en: "Whose", pt: ["de quem"] },
        { en: "How", pt: ["como"] },
        { en: "How much", pt: ["quanto", "quanta"] },
        { en: "How many", pt: ["quantos", "quantas"] }
    ],
    pronouns: [
        { en: "I", pt: ["eu"] },
        { en: "You", pt: ["você", "tu"] },
        { en: "He", pt: ["ele"] },
        { en: "She", pt: ["ela"] },
        { en: "It", pt: ["ele", "ela"] },
        { en: "We", pt: ["nós"] },
        { en: "They", pt: ["eles", "elas"] },
        { en: "Me", pt: ["me", "mim"] },
        { en: "Him", pt: ["o", "lhe"] },
        { en: "Her", pt: ["a", "lhe"] },
        { en: "Us", pt: ["nos"] },
        { en: "Them", pt: ["os", "as", "lhes"] }
    ],
    adjectives: [
        { en: "Good", pt: ["bom", "boa"] },
        { en: "Bad", pt: ["ruim", "mau"] },
        { en: "Big", pt: ["grande"] },
        { en: "Small", pt: ["pequeno", "pequena"] },
        { en: "Hot", pt: ["quente"] },
        { en: "Cold", pt: ["frio", "fria"] },
        { en: "Fast", pt: ["rápido", "rápida"] },
        { en: "Slow", pt: ["lento", "lenta"] },
        { en: "New", pt: ["novo", "nova"] },
        { en: "Old", pt: ["velho", "antigo"] }
    ],
    verbs: [
        { en: "To be", pt: ["ser", "estar"] },
        { en: "To have", pt: ["ter"] },
        { en: "To do", pt: ["fazer"] },
        { en: "To go", pt: ["ir"] },
        { en: "To want", pt: ["querer"] },
        { en: "To need", pt: ["precisar"] },
        { en: "To like", pt: ["gostar"] },
        { en: "To eat", pt: ["comer"] },
        { en: "To drink", pt: ["beber"] },
        { en: "To speak", pt: ["falar"] }
    ],
    connectives: [
        { en: "And", pt: ["e"] },
        { en: "But", pt: ["mas"] },
        { en: "Or", pt: ["ou"] },
        { en: "Because", pt: ["porque", "por que"] },
        { en: "So", pt: ["então", "portanto"] },
        { en: "Yes", pt: ["sim"] },
        { en: "No", pt: ["não"] },
        { en: "Please", pt: ["por favor"] },
        { en: "Thank you", pt: ["obrigado", "obrigada"] },
        { en: "Sorry", pt: ["desculpe", "sinto muito"] }
    ]
};

const categorySelect = document.getElementById("category");
const englishWord = document.getElementById("english-word");
const answerInput = document.getElementById("answer");
const feedback = document.getElementById("feedback");

let currentWord = null;

document.getElementById("start").addEventListener("click", generateWord);
document.getElementById("check").addEventListener("click", checkAnswer);

function generateWord() {
    const category = categorySelect.value;
    const words = data[category];
    currentWord = words[Math.floor(Math.random() * words.length)];

    englishWord.textContent = currentWord.en;
    answerInput.value = "";
    feedback.textContent = "";
}

function checkAnswer() {
    if (!currentWord) return;

    const userAnswer = answerInput.value.trim().toLowerCase();

    const correct = currentWord.pt.some(
        t => t.toLowerCase() === userAnswer
    );

    if (correct) {
        feedback.textContent = "✔ Correto!";
        feedback.className = "correct";
    } else {
        feedback.textContent =
            `✖ Errado. Tradução correta: ${currentWord.pt.join(", ")}`;
        feedback.className = "wrong";
    }
}
