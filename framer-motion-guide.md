# Использование framer-motion для анимации в React

`framer-motion` — это мощная библиотека для анимации в React, которая позволяет создавать плавные и интерактивные анимации с минимальными усилиями. В этой статье мы рассмотрим основные концепции и пример использования `framer-motion`.

## Установка

Для начала, установите библиотеку с помощью npm или yarn:

```
npm install framer-motion
или
yarn add framer-motion
```
## Основные концепции

### Анимационные состояния

`framer-motion` позволяет задавать различные состояния анимации для компонентов. Основные состояния:

- **initial**: начальное состояние элемента.
- **animate**: состояние, к которому элемент будет анимирован.
- **exit**: состояние, к которому элемент будет анимирован при его удалении из DOM.

## Пример использования

Рассмотрим пример компонента, который использует `framer-motion` для анимации появления и исчезновения содержимого.

```typescript
// components/MotionWrapper.tsx

"use client";

import { motion, AnimatePresence } from "framer-motion";
import { ReactNode } from "react";

interface MotionWrapperProps {
    children: ReactNode;
}

const MotionWrapper: React.FC<MotionWrapperProps> = ({ children }) => {
    const handleExitComplete = () => {
        console.log("Exit animation completed");
        // Здесь можно выполнять дополнительные действия после завершения анимации
    };

    return (
        <AnimatePresence onExitComplete={handleExitComplete}>
            <motion.div
                initial={{ opacity: 0 }} // Начальное состояние: невидимый
                animate={{ opacity: 1 }} // Конечное состояние: видимый
                exit={{ opacity: 0 }} // Состояние при выходе: невидимый
                transition={{ duration: 0.5 }} // Длительность анимации: 0.5 секунды
            >
                {children}
            </motion.div>
        </AnimatePresence>
    );
};

export default MotionWrapper;
```

### Объяснение кода

- **`initial={{ opacity: 0 }}`**: Элемент начинает с полной прозрачности (невидим).
- **`animate={{ opacity: 1 }}`**: Элемент плавно становится видимым.
- **`exit={{ opacity: 0 }}`**: При удалении из DOM элемент снова становится невидимым.
- **`transition={{ duration: 0.5 }}`**: Анимация длится 0.5 секунды.

### Использование компонента

Вы можете использовать `MotionWrapper` для анимации любого содержимого. Например:

```javascript
import MotionWrapper from './components/MotionWrapper';

const App = () => {
    return (
        <MotionWrapper>
            <h1>Привет, мир!</h1>
        </MotionWrapper>
    );
};

export default App;
```

### Заключение

`framer-motion` — это простой и мощный инструмент для создания анимаций в React-приложениях. 
С помощью этой библиотеки вы можете легко добавить динамичность и интерактивность в ваш интерфейс. 
Попробуйте использовать `framer-motion` в своих проектах и экспериментируйте с различными эффектами!

### Полезные ссылки

- [Документация framer-motion](https://www.framer.com/motion/introduction/)
- [GitHub framer-motion](https://github.com/framer/motion#readme)
