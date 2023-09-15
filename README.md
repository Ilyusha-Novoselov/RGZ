# 1. Задача
Мобильный робот движется по плоскости. Робот - материальная точка с координатой (Cx, Cy); робот может двигаться в любом направлении без ограничений. Также на плоскости находятся объекты-препятствия. Заданы начальная и конечная координаты робота Init=(Initx, Inity) и Goal=(Goalx, Goaly), дополнительно может быть задано несколько промежуточных координат. 
Задача: найти кратчайший путь для робота из начальной координаты в конечную, не приводящий к столкновению робота с препятствиями. При наличии дополнительных координат путь должен проходить через каждую дополнительную координату минимум по одному разу. Если путь не возможен - сообщить об этом.

# 2. Описание использованных и разработанных алгоритмов
•	Point RandomSample() – функция, которая возвращает рандомную конфигурацию из свободного пространства сцены;  
•	vector<int> Near(vector<Point>& points_of_graph, Point& X, int k) – функция, которая получает на вход все точки графа, конкретную точку X и число k, которое показывает, сколько ближайших вершин к данной точке X должна вернуть функция;  
•	bool CollisionFree(Point& p1, Point& p2, vector<Triangle>& all_triangles) – функция, которая проверяет на коллизию отрезок p1,p2 со всеми треугольниками;  
•	bool CollisionFree(Point& p1, Point& p2, vector<Triangle>& all_triangles, vector<Point> points_of_graph) – функция, которая проверяет на коллизию с треугольниками, так еще и с точками графа;  
•	bool CollisionFree(Point& p1, Point& p2, vector<Triangle>& all_triangles, vector<Point> points_of_graph, Circle Qinit, Circle Qgoal) – функция, которая проверяет на коллизию с треугольниками, так еще и с начальной и конечной точкой сцены;  
•	vector<Point> PRM(int N, int k, Point& qinit, Point& qgoal, vector<Triangle>& all_triangles, Graph& g) – функция, которая выполнение построение графа, не пересекаясь с препятствиями. Возвращает ассоциативный массив с координатами вершин графа, а в адрес самого графа записывает все его номера вершин и ребра.   

# 3. Описание возможностей интерфейса
•	Есть 3 кнопки красного цвета, которые позволяют редактировать сцену. Если они светятся красным, то значит, что кнопки не активны. Щелкая по сцене ничего не произойдет. Когда происходит нажатие на одну из кнопок («Треугольник», «Начальная точка», «Конечная точка»), она начинает подсвечиваться зеленым. Это означает, что следующие координаты щелчков по сцене будут запоминаться программой. После нажатия по кнопке «Треугольник» необходимо нажать три раза по сцене, после чего построится треугольник по трем точкам. Соответствующие промежуточные точки будут подсвечиваться.  
•	При нажатии на кнопку «Начальная/Конечная точка» аналогичным образом задается начало и конец пути робота. После чего мы можем построить путь, щелкнув на соответствующую кнопку («Построить путь»).  
•	Также можно редактировать кол-во точек графа, для большей точности нахождения кратчайшего пути (Кнопка «Кол-во точек графа»)  
•	Кнопка «Кол-во ребер вершины» отвечает за кол-во соединяемых ребер с каждой вершиной графа. Аналогично влияет на точность результата.  
•	Кнопка «Очистка сцены» - возвращает сцену в начальное положение, которое было при запуске, удаляя все элементы со сцены.  
•	Кнопка «Сохранить» позволяет указать путь, куда сохранить сцену. Сохранение производится в txt файл.  
•	Структура txt файла:  
Координаты qinit;  
Координаты qgoal;  
Координаты треугольников.  
•	Кнопка «Загрузить» позволяет выбрать нужный txt и загрузить сцену, после чего её можно будет редактировать;  
![image](https://github.com/Ilyusha-Novoselov/RGZ/assets/119160923/9f8a4699-966a-458f-b4b7-4c7fab9fc8da)

