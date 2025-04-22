# Документация по проектной практике. Часть 1. Проектная детельность

## Введение

Проект "Ментор МГПУ" направлен на создание интеллектуального ассистента для преподавателей Московского городского педагогического университета.
Цель: разработка LLM-агностичной платформы с ИИ-ментором, способного:

- Отвечать на вопросы по методикам преподавания
- Анализировать педагогические кейсы с использованием RAG (Retrieval-Augmented Generation)

## Технологический стек

### Backend

- **Node.js** + **TypeScript** (основная платформа)
- **PostgreSQL** с расширением `pgvector` для работы с векторными данными
- **Ollama** модели для embeddings и генерации текста (gemma, ...)

### Frontend

- **React** + **TypeScript** (ядро приложения)
- **CSS Modules** с методологией BEM
- **Gravity UI Kit** (дизайн-система Яндекса)
- Адаптивная верстка с mobile-first подходом

### Инфраструктура

- **Docker** + **Docker Compose** (оркестрация)
- **GitLab CI/CD** для автоматизации сборки
- Авторизация через **VK OAuth 2.0**
- Мониторинг: **Prometheus** + **Grafana**

## Архитектурные решения

Было решено взять NodeJS и PostgreSQL так как это наиболее быстрые для реализации продукта технологии.
На фронтенде было решено взять готовую UI библиотеку и Дизайн-систему Gravity-UI от Яндекса, чтобы не тратить время на разработку собственной дизайн-системы

### Ключевые особенности

1. **LLM-агностичность**:

```typescript
interface LLMProvider {
  generate(prompt: string, context: string[]): Promise<string>;
  embed(text: string): Promise<number[]>;
}

class OllamaAdapter implements LLMProvider { ... }
```

2. **Векторный поиск**:

```sql
CREATE TABLE document_embeddings (
  id SERIAL PRIMARY KEY,
  content TEXT,
  embedding VECTOR(384)
);

CREATE INDEX ON document_embeddings USING ivfflat (embedding);
```

## Этапы разработки

### 1. Исследовательская фаза

- Анализ потребностей преподавателей (опрос 120+ человек)
- Сравнение LLM-провайдеров (GPT-4, Claude, Mixtral, Yandex, Ollama, Deepseek)
- Тестирование embedding-моделей

### 2. Реализация

- Настройка CI/CD pipeline
- Интеграция VK ID для авторизации
- Реализация RAG-цепочки:

```typescript
async function retrieveAndGenerate(query: string) {
  const embedding = await model.embed(query);
  const context = await db.search(embedding);
  return llm.generate(query, context);
}
```

## Заключение

Проект демонстрирует эффективное сочетание современных AI-технологий с практическими потребностями образовательного процесса.
