# multiprocessing

1. Multiprocessing in Python is a built-in package that allows the system to run multiple processes simultaneously.It is useful for speeding up your code and handling large datasets and tasks.

2. Multiprocessing uses two or more CPUs to increase computing power, whereas multithreading uses a single process with multiple code segments to increase computing power.
Multithreading focuses on generating computing threads from a single process, whereas multiprocessing increases computing power by adding CPUs.

3.import multiprocessing

def print_cube(num):
	"""
	function to print cube of given num
	"""
	print("Cube: {}".format(num * num * num))

def print_square(num):
	"""
	function to print square of given num
	"""
	print("Square: {}".format(num * num))

if __name__ == "__main__":

	p1 = multiprocessing.Process(target=print_square, args=(10, ))
	p2 = multiprocessing.Process(target=print_cube, args=(10, ))


	p1.start()

	p2.start()


	p1.join()

	p2.join()

	print("Done!")

 4. The Pool class in multiprocessing can handle an enormous number of processes. It allows you to run multiple jobs per process (due to its ability to queue the jobs). 
Python multiprocessing Pool can be used for parallel execution of a function across multiple input values, distributing the input data across processes (data parallelism).

5. To create a pool of processes in Python, you can use the `multiprocessing` module's `Pool` class. The `multiprocessing. Pool` object will maintain a collection of worker processes, to which you can submit tasks to be executed concurrently.
from multiprocessing import Pool
def (x):
    return x*x

if __name__ == '__main__':
    with Pool(5) as p:
        print(p.map(f, [1, 2, 3]))

6. import multiprocessing
import os

def worker1():

	print("ID of process running worker1: {}".format(os.getpid()))

def worker2():

	print("ID of process running worker2: {}".format(os.getpid()))

if __name__ == "__main__":

	print("ID of main process: {}".format(os.getpid()))

	p1 = multiprocessing.Process(target=worker1)
	p2 = multiprocessing.Process(target=worker2)

	p1.start()
	p2.start()

	print("ID of process p1: {}".format(p1.pid))
	print("ID of process p2: {}".format(p2.pid))

	p1.join()
	p2.join()

	print("Both processes finished execution!")

	print("Process p1 is alive: {}".format(p1.is_alive()))
	print("Process p2 is alive: {}".format(p2.is_alive()))
