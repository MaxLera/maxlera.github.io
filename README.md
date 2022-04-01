# maxlera.github.io
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Function for Hangman</title>
</head>
<body>
    
    <script>
        function greatings(){
            alert("Приветствую Вас в игре 'Виселица'!");

            alert(`                 Правила игры! 
        1) Игрок, который начинает игру, вводит слово, которое нужно угадать другому игроку
        2) В следующем поле, введите описание слова или легкая подсказка
        3) Играть и наслаждаться процесом
                Приятной игры!`);
            return;
        }
        function pickWord(){
            let word = prompt("Введите своё задуманое слово !");
            if (word === "" || word === " " || word === null) {
                alert("Пожалуйста, введите слово, которое нужно отгадать!!!");
                    return pickWord();
            }
                return word.toLocaleLowerCase(); 
        }
        function discriptions(){
            let dis = prompt("Опишите своё слово!");
            if (dis === "" || dis === " " || dis === null) {
                alert("Пожалуйста, введите описание своего слова!!!");
                    return discriptions();
            }
            return dis;
        }
        function nextGamer(){
            alert('Внимание!!! Передай телефон игроку, который будет угадывать слово.');
            alert(discription);
                return;
        }
        function setupAsnwerArray(){
            let answerArray = [];
            for (let i = 0; i < word.length; i++) {
                answerArray[i] = "_";
            };
            return answerArray;
        }
        function guessProcess(){
            showProgress();
            guess = getGuess();

            if (guess === null || guess === " " || guess.length != 1) {
                alert("Пожалуйста, введите одну букву!!!");
                getGuess();
            }
            else {
                updateGameState();
            }
        }
        function showProgress(){
            alert(answerArray.join(" "));
            alert(`Осталось угадать ${remainingLetters} букв(-ы) в слове!`);
        }
        function getGuess(){
            let guess = prompt("Пожалуйста, введите букву или нажмите 'Отмена' для остановки игры.");
                if (guess === null || guess === " " || guess.length != 1) {
                    alert("Пожалуйста, введите одну букву!!!");
                    return getGuess();
                }
                return guess.toLocaleLowerCase();   
        }
        function updateGameState(){
            for (let j = 0; j < word.length; j++) {
                if (word[j] === guess) {
                    answerArray[j] = guess;
                }
            }
            let counter = 0;
            for (let index = 0; index < word.length; index++) {
                if (answerArray[index] !== "_") {
                    counter++;
                }
            }
            remainingLetters -= counter;

            return remainingLetters;
        }
        function repeat(){
            let repeat = confirm("Повторим?");
            if (repeat) {
                alert("Тогда предай очередь другому игроку!");
                location.reload();
            }
            else {
                alert("До встречи! В следующей игре!");
            }
        }
        function conrgats(){
            alert(answerArray.join(" "));
            alert(`Хорошая работа! Правильный ответ - ${word}! Ты угадал слово с ${number} попыток.`);
        }

        greatings();
        let word = pickWord();
        let discription = discriptions();
        nextGamer();
        let answerArray = setupAsnwerArray(word);
        let remainingLetters = word.length;
        let number = 0;
        let guess;

        while (remainingLetters > 0) {
            guessProcess();
            number++;
        };

        conrgats();
        repeat();

    </script>

</body>
</html>
