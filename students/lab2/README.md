# Book Service — сервис управления книгами

Вариант 19: Книги «Читаю/прочитал» 📚

## Архитектура
Сервис построен по принципам Чистой Архитектуры (Clean Architecture).

## Слои
- **Domain** — модели Book, Shelf, Review, исключения
- **Application** — use-cases: AddBook, MoveBook, GetShelf
- **Infrastructure** — REST контроллер, in-memory репозитории, заглушка поиска

## Запуск
```python
from src.infrastructure.config.dependency_injection import DependencyContainer

container = DependencyContainer()
controller = container.get_controller()
# controller.add_book({...})  # будет работать в Lab #4
