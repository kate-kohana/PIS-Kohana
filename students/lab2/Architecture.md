# Архитектура Book Service

## Принципы
- Domain Layer **НЕ зависит** от Infrastructure Layer
- Все зависимости направлены **внутрь** (к Domain)
- Порты (интерфейсы) определены в Application Layer
- Адаптеры реализуют порты в Infrastructure Layer

## Поток данных (пример: добавление книги)
1. Controller получает HTTP POST /api/books
2. Вызывает AddBookUseCase.add_book(command)
3. BookService проверяет дубликат через BookRepository
4. Создаёт доменную модель Book
5. Сохраняет через BookRepository.save()
6. Обновляет ShelfRepository (счётчик книг)
7. Индексирует через SearchIndexService
8. Возвращает book_id клиенту

## Входящие порты
- AddBookUseCase — добавить книгу
- MoveBookUseCase — перенести книгу
- GetShelfUseCase — получить содержимое полки

## Исходящие порты
- BookRepository — хранение книг
- ShelfRepository — управление полками
- SearchIndexService — поисковая индексация
