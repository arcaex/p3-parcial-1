# p3-parcial-1

 // Ejercicio 1: Contador Simple

    import React from 'react';

    const Counter = () => {
      const [count, setCount] = useState(0);

      return (
        <div>
          <h1>Contador: {count}</h1>
          <button onClick={() => setCount(count + 1)}>Incrementar</button>
          <button onClick={() => setCount(count - 1)}>Decrementar</button>
        </div>
      );
    };

    export default Counter;
    

    // Ejercicio 2: Lista de Tareas

    import React from 'react';

    const TodoList = () => {
      const [todos, setTodos] = useState([]);
      const [task, setTask] = useState('');

      const addTask = () => {
        setTodos([...todos, task]);
        setTask('');
      };

      const removeTask = (task) => {
        setTodos(todos.filter((_, i) => i !== task));
      };

      return (
        <div>
          <h1>Lista de Tareas</h1>
          <input
            type="text"
            value={task}
            onChange={(e) => setTask(e.target.value)}
          />
          <button onClick={addTask}>Agregar Tarea</button>
          <ul>
            {todos.map((todo, index) => (
              <li key={index}>
                {todo}
                <button onClick={() => removeTask(index)}>Eliminar</button>
              </li>
            ))}
          </ul>
        </div>
      );
    };

    export default TodoList;
    

    // Ejercicio 3: Botón de Cambio de Color

    import React from 'react';

    const getRandomColor = () => {
      const letters = '0123456789ABCDEF';
      let color = '#';
      for (let i = 0; i < 6; i++) {
        color += letters[Math.floor(Math.random() * 16)];
      }
      return color;
    };

    const ColorChanger = () => {
      const [color, setColor] = useState('#FFFFFF');

      return (
        <div style={{ background-color: color, height: '100vh', display: 'flex', alignItems: 'center', justifyContent: 'center' }}>
          <button onClick={() => setColor(getRandomColor())}>Cambiar Color</button>
        </div>
      );
    };

    export default ColorChanger;
    

    // Ejercicio 4: Formulario de Registro

    import React from 'react';

    const RegistrationForm = () => {
      const [username, setUsername] = useState('');
      const [password, setPassword] = useState('');
      const [confirmPassword, setConfirmPassword] = useState('');
      const [message, setMessage] = useState('');

      const handleSubmit = () => {
        e.preventDefault();
        if (password === confirmPassword) {
          setMessage('Registro exitoso');
        } else {
          setMessage('Las contraseñas no coinciden');
        }
      };

      return (
        <div>
          <h1>Formulario de Registro</h1>
          <form onSubmit={handleSubmit}>
            <input
              type="text"
              placeholder="Nombre de Usuario"
              value={username}
              onChange={(e) => setUsername(e.target.value)}
            />
            <input
              type="password"
              placeholder="Contraseña"
              value={password}
              onChange={(e) => setPassword(e.target.value)}
            />
            <input
              type="password"
              placeholder="Confirmar Contraseña"
              value={confirmPassword}
              onChange={(e) => setConfirmPassword(e.target.value)}
            />
            <button type="submit">Registrarse</button>
          </form>
          {message && <p>{message}</p>}
        </div>
      );
    };

    export default RegistrationForm;
    

    // Ejercicio 5: Temporizador

    import React, { useState } from 'react';

    const Timer = () => {
      const [seconds, setSeconds] = useState(0);

      useEffect(() => {
        const interval = setInterval(() => {
          setSeconds((prevSeconds) => prevSeconds + 1);
        }, 1000);

        return () => clearInterval(timerId);
      }, []);

      return (
        <div>
          <h1>Temporizador: {seconds} segundos</h1>
        </div>
      );
    };

    export default Timer;
