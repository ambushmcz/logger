<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Логирование</title>
</head>
<body>
    <h1>Добавить запись в лог</h1>
    <form action="index.php" method="get">
        <input type="hidden" name="action" value="add">
        <label for="password">Пароль:</label>
        <input type="text" name="password" id="password" required>
        <br>
        <label for="tag">Тег:</label>
        <input type="text" name="tag" id="tag" value="default" required>
        <br>
        <label for="request">Запрос:</label>
        <input type="text" name="request" id="request" value="NO_INFORMATION_GIVEN" required>
        <br>
        <button type="submit">Добавить запись</button>
    </form>

    <h1>Просмотр логов</h1>
    <form action="index.php" method="get">
        <input type="hidden" name="action" value="logs">
        <label for="password">Пароль:</label>
        <input type="text" name="password" id="password" required>
        <br>
        <label for="tag">Тег:</label>
        <input type="text" name="tag" id="tag" value="all" required>
        <br>
        <button type="submit">Показать логи</button>
    </form>

    <div>
        <?php
        // Вставьте сюда код PHP из предыдущего ответа
        date_default_timezone_set('Europe/Moscow');

        if ($_SERVER['REQUEST_METHOD'] === 'GET') {
            if (isset($_GET['action']) && $_GET['action'] === 'add') {
                $password = isset($_GET['password']) ? $_GET['password'] : 'NONE';
                $tag = isset($_GET['tag']) ? $_GET['tag'] : 'default';
                $request = isset($_GET['request']) ? $_GET['request'] : 'NO_INFORMATION_GIVEN';

                $hash = base64_encode(md5($password, true));

                // Замените 'ваш_хэш_пароля' на фактический хэш
                if ($hash === getenv('hash')) {
                    $filename = $tag === 'default' ? 'logs.txt' : 'logs_' . $tag . '.txt';
                    $logEntry = '[' . $tag . '] [' . date('m.d.y H:i:s') . '] ' . $request . "\n";
                    $encryptedLogEntry = openssl_encrypt($logEntry, 'aes-256-cbc', getenv('hash'), 0, substr(getenv('hash'), 0, 16));
                    file_put_contents($filename, $encryptedLogEntry, FILE_APPEND);
                    echo 'Запись добавлена.';
                } else {
                    echo 'Ошибка: неверный пароль.';
                }
            } elseif (isset($_GET['action']) && $_GET['action'] === 'logs') {
                $password = isset($_GET['password']) ? $_GET['password'] : 'NONE';
                $tag = isset($_GET['tag']) ? $_GET['tag'] : 'all';

                $hash = base64_encode(md5($password, true));

                if ($hash === getenv('hash')) {
                    if ($tag === 'default') {
                        $filename = 'logs.txt';
                    } elseif ($tag === 'all') {
                        $logs = '';
                        foreach (glob('logs_*.txt') as $filename) {
                            $logs .= file_get_contents($filename);
                        }
                        $logs .= file_get_contents('logs.txt');
                        $decryptedLogs = array_map(function($line) {
                            return openssl_decrypt($line, 'aes-256-cbc', getenv('hash'), 0, substr(getenv('hash'), 0, 16));
                        }, explode("\n", $logs));
                        echo implode('<br>', array_reverse($decryptedLogs));
                        return;
                    } else {
                        $filename = 'logs_' . $tag . '.txt';
                    }

                    if (file_exists($filename)) {
                        $logs = file_get_contents($filename);
                        $decryptedLogs = array_map(function($line) {
                            return openssl_decrypt($line, 'aes-256-cbc', getenv('hash'), 0, substr(getenv('hash'), 0, 16));
                        }, explode("\n", $logs));
                        echo implode('<br>', array_reverse($decryptedLogs));
                    } else {
                        echo '<h1>Логи не найдены для этого тега.</h1>';
                    }
                } else {
                    echo '<h1>Доступ запрещен</h1><p>Возможно, ваш IP-адрес заблокирован. Свяжитесь с поддержкой.</p>';
                }
            }
        }
        ?>
    </div>
</body>
</html>
