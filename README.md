# maxlera.github.io

<html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
       
    </head>
  
    <body>

        <script>
            alert("Приветствую Вас в игре 'Виселица'!");

            alert(`                 Правила игры! 
            1) Игрок, который начинает игру, вводит слово, которое нужно угадать другому игроку
            2) В следующем поле, введите описание слова или легкая подсказка
            3) Играть и наслаждаться процесом
                                Приятной игры!`);

            let word = prompt("Введите своё задуманое слово !");
            word = word.toLocaleLowerCase();
            let discription = prompt("Опишите своё слово!");

            alert('Внимание!!! Передай телефон игроку, который будет угадывать слово.');
            alert(discription);

            let answerArray = [];
            for (let i = 0; i < word.length; i++) {
                answerArray[i] = "_";
            };

            let remainingLetters = word.length;
            let number = 0;

            while (remainingLetters > 0) {
                alert(answerArray.join(" "));

                let guess = prompt("Пожалуйста, введите букву или нажмите 'Отмена' для остановки игры.");
                guess = guess.toLocaleLowerCase();
                    if (guess === null) {
                        alert("До встречи! В следующей игре!");
                        break;
                    }
                    else if (guess.length != 1) {
                        alert("Пожалуйста, введите одну букву!!!");
                    }
                    else {
                        for (let j = 0; j < word.length; j++) {
                            if (word[j] === guess) {
                            answerArray[j] = guess;
                            remainingLetters--;
                            }
                        }
                    }
                    number++;
            };

            alert(answerArray.join(" "));
            alert(`Хорошая работа! Правильный ответ - ${word}! Ты угадал слово с ${number} попыток.`);

            let repeat = confirm("Повторим?");
                if (repeat) {
                    alert("Тогда предай очередь другому игроку!");
                    location.reload();
                }
                else {
                    alert("До встречи! В следующей игре!");
                }

        </script>

    </body>
      
</html>
