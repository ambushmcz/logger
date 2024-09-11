<?php
// Включаем отображение ошибок для отладки
error_reporting(E_ALL);
ini_set('display_errors', 1);

// Подключаем необходимые библиотеки
require 'vendor/autoload.php'; // Убедитесь, что необходимые библиотеки установлены через Composer

// Определяем константы
define('HASH', getenv('hash')); // Убедитесь, что переменная окружения 'hash' установлена

// Функция для шифрования сообщения
function encrypt($message, $key) {
    return base64_encode(openssl_encrypt($message, 'aes-256-cbc', $key, 0, substr($key, 0, 16)));
}

// Функция для расшифровки сообщения
function decrypt($message, $key) {
    return openssl_decrypt(base64_decode($message), 'aes-256-cbc', $key, 0, substr($key, 0, 16));
}

// Функция для логирования
function logText($password, $tag, $request) {
    if (base64_encode(md5($password, true)) === HASH) {
        $filename = ($tag !== 'default') ? "logs_$tag.txt" : 'logs.txt';
        $timestamp = (new DateTime('now', new DateTimeZone('UTC')))->setTimezone(new DateTimeZone('Europe/Moscow'))->format('d.m.Y H:i:s');
        $encryptedMessage = encrypt("[$tag] [$timestamp] $request", HASH) . "\n";
        
        file_put_contents($filename, $encryptedMessage, FILE_APPEND);
        return 'true';
    } else {
        return 'false';
    }
}

// Функция для получения логов
function getLogs($password, $tag) {
    if (base64_encode(md5($password, true)) === HASH) {
        $logs = [];
        
        if ($tag === 'default') {
            $filename = 'logs.txt';
            if (file_exists($filename)) {
                $logs = array_map('decrypt', file($filename, FILE_IGNORE_NEW_LINES), array_fill(0, count(file($filename)), HASH));
            } else {
                return '<h1>Логи не найдены для этого тега.</h1>';
            }
        } elseif ($tag === 'all') {
            foreach (glob('logs_*.txt') as $filename) {
                $fileLogs = array_map('decrypt', file($filename, FILE_IGNORE_NEW_LINES), array_fill(0, count(file($filename)), HASH));
                $logs = array_merge($logs, $fileLogs);
            }
        } else {
            $filename = "logs_$tag.txt";
            if (file_exists($filename)) {
                $logs = array_map('decrypt', file($filename, FILE_IGNORE_NEW_LINES), array_fill(0, count(file($filename)), HASH));
            } else {
                return '<h1>Логи не найдены для этого тега.</h1>';
            }
        }
        
        return implode("<br>", array_reverse($logs));
    } else {
        return '<h1>Доступ запрещен</h1>\nВозможно, ваш IP-адрес заблокирован. Свяжитесь с поддержкой.';
    }
}

// Обработка запросов
if ($_SERVER['REQUEST_METHOD'] === 'GET') {
    if (isset($_GET['action'])) {
        $action = $_GET['action'];
        $password = $_GET['password'] ?? 'NONE';
        $tag = $_GET['tag'] ?? 'default';
        $request = $_GET['request'] ?? 'NO_INFORMATION_GIVEN';

        if ($action === 'add') {
            echo logText($password, $tag, $request);
        } elseif ($action === 'logs') {
            echo getLogs($password, $tag);
        }
    } else {
        echo '<h1>Неверное действие</h1>';
    }
}
?>
