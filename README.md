import os

def fibonacci(limit):
    a, b = 0, 1
    sequence = []
    while a <= limit:
        sequence.append(a)
        a, b = b, a + b
    return sequence

def write_to_file(filename, sequence):
    with open(filename, "w") as file:
        for num in sequence:
            file.write(str(num) + "\n")
    print(f"Sequence written to {filename}")

def read_from_file(filename):
    if not os.path.exists(filename):
        print("File does not exist.")
        return
    with open(filename, "r") as file:
        data = file.readlines()
        print("Fibonacci sequence from file:")
        for line in data:
            print(line.strip())

def main():
    try:
        limit = int(input("Enter the upper limit for Fibonacci sequence: "))
        sequence = fibonacci(limit)
        print("Generated Fibonacci sequence:", sequence)
        filename = "fibonacci.txt"
        write_to_file(filename, sequence)
        read_from_file(filename)
    except ValueError:
        print("Please enter a valid integer.")

if __name__ == "__main__":
    main()
