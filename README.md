<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="utf-8" />
  <title>Массивы — простые решения</title>
  <style>
    body { font-family: Arial, sans-serif; padding: 20px; }
    button { display:block; margin:8px 0; padding:8px 12px; }
  </style>
</head>
<body>
  <h3>Задачи по массивам — простые решения (prompt / alert)</h3>

  <button onclick="task1()">1) Ввести 5 чисел и вывести в обратном порядке</button>
  <button onclick="task2()">2) Массив из 20 случайных чисел, вывести элементы с чётными индексами</button>
  <button onclick="task3()">3) Массив 10 чисел от -20 до 20, среднее арифметическое положительных</button>
  <button onclick="task4()">4) Массив 10 чисел от -5 до 5, посчитать +, -, 0</button>
  <button onclick="task5()">5) Массив 10 целых, сумма чётных и среднее нечётных</button>

<script>
function rnd(min, max){
  return Math.floor(Math.random() * (max - min + 1)) + min;
}

/* 1 */
function task1(){
  a = [];
  i = 0;
  while (i < 5){
    v = prompt("Введите число №" + (i+1) + " из 5:");
    if (v === null) return;
    a.push(Number(v));
    i = i + 1;
  }
  out = "";
  i = a.length - 1;
  while (i >= 0){
    out = out + a[i];
    if (i > 0) out = out + ", ";
    i = i - 1;
  }
  alert("Массив в обратном порядке:\n" + out);
}

/* 2 */
function task2(){
  a = [];
  i = 0;
  while (i < 20){
    a.push(rnd(0, 99)); // случайные 0..99
    i = i + 1;
  }
  out = "Массив (20):\n" + a.join(", ") + "\n\nЭлементы с чётными индексами (0,2,4...):\n";
  i = 0;
  first = true;
  while (i < a.length){
    if (i % 2 === 0){
      if (!first) out = out + ", ";
      out = out + a[i];
      first = false;
    }
    i = i + 1;
  }
  alert(out);
}

/* 3 */
function task3(){
  a = [];
  i = 0;
  while (i < 10){
    a.push(rnd(-20, 20));
    i = i + 1;
  }
  sum = 0;
  cnt = 0;
  i = 0;
  while (i < a.length){
    if (a[i] > 0){
      sum = sum + a[i];
      cnt = cnt + 1;
    }
    i = i + 1;
  }
  s = "Массив:\n" + a.join(", ") + "\n\n";
  if (cnt === 0){
    s = s + "Положительных элементов нет.";
  } else {
    s = s + "Среднее арифметическое положительных = " + (sum / cnt);
  }
  alert(s);
}

/* 4 */
function task4(){
  a = [];
  i = 0;
  while (i < 10){
    a.push(rnd(-5, 5));
    i = i + 1;
  }
  pos = 0;
  neg = 0;
  zer = 0;
  i = 0;
  while (i < a.length){
    if (a[i] > 0) pos = pos + 1;
    else if (a[i] < 0) neg = neg + 1;
    else zer = zer + 1;
    i = i + 1;
  }
  alert("Массив:\n" + a.join(", ") + "\n\nПоложительных: " + pos + "\nОтрицательных: " + neg + "\nНулей: " + zer);
}

/* 5 — изменил вывод: убрал сборку строки s, сделал проще (несколько alert'ов) */
function task5(){
  a = [];
  i = 0;
  while (i < 10){
    a.push(rnd(-20, 20)); // целые числа в диапазоне -20..20
    i = i + 1;
  }
  sumEven = 0;
  sumOdd = 0;
  cntOdd = 0;
  i = 0;
  while (i < a.length){
    if (a[i] % 2 === 0){
      sumEven = sumEven + a[i];
    } else {
      sumOdd = sumOdd + a[i];
      cntOdd = cntOdd + 1;
    }
    i = i + 1;
  }

  alert("Массив:\n" + a.join(", "));
  alert("Сумма чётных элементов: " + sumEven);
  if (cntOdd === 0) alert("Нечётных элементов нет");
  else alert("Среднее арифметическое нечётных: " + (sumOdd / cntOdd));
}
</script>
</body>
</html>
