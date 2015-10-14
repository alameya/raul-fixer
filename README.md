# raul-fixer

### Описание

Предназначен для правки *.phtml шаблонов проектов AdMeGroup, а также для того чтобы сделать этот мир лучше :stuck_out_tongue_winking_eye:

### Основные возможности

* Исправление ```<?php echo``` на ```<?=```
* Проставление забытых `<?php` вместо `<?`
* Проставление и удаление пробелов
* Замена табуляции  

### Установка
1. `cd installation_path`
2. `git clone git@github.com:alameya/raul-fixer.git .` 
3. `chmod +x raul-fixer`


### Обычное использование
```raul-fixer path/to/file```

### Использование в git pre-commit hook
Добавляем в switch pre-commit-cs-fixer еще один блок после блока php (заменяем `installation_path`)
```php
case 'phtml':
    $raulFixerOutput = [];
    exec('installation_path/raul-fixer ' . getcwd() .'/' . escapeshellarg($fileName), $raulFixerOutput);
    if (count(array_filter($raulFixerOutput))) {
        echo getcwd() . '/' . $fileName . PHP_EOL;
        $hasErrors = true;
    }
    break;
```

###### Предупреждение: иногда может некорректно отрабатывать если файл содержит регулярные выражения, но в 99.98% случаев работает как надо :grimacing: 