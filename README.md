# Ex.No.6 AI-Assisted Programming and Debugging

## Name: Shadhanashree SV
## Register No: 212223230202


## AIM

To use AI tools and effective prompts to generate, debug, optimize, test, and analyze Python, C, and Java programs, and to compare AI-assisted programming with manual coding.

## OBJECTIVE

To understand how AI tools can assist programmers in different stages of software development:

- Code generation
- Bug identification and debugging
- Code optimization
- Complexity analysis
- Unit-test generation
- Comparison with manual coding
- Code-quality analysis

The same programming scenario is implemented in Python, C, and Java to evaluate AI-assisted programming across different languages.

## SCENARIO

IoT Sensor Data Processing

An IoT device collects multiple sensor readings from an industrial environment.

The program must:

- Accept multiple sensor readings.
- Validate the readings.
- Calculate minimum, maximum, and average values.
- Identify readings above a threshold of 100.
- Handle invalid or empty input.

The program is developed in Python, C, and Java using AI assistance.

## AI TOOLS USED

1) ChatGPT – Code generation, debugging, optimization and analysis
2) Google Gemini – Code generation and optimization
3) Microsoft Copilot – Code analysis and test generation
4) Python, C and Java environments – Program execution and verification
   
## PROCEDURE

The following workflow is followed for all three languages:

Prompt → Generate → Execute → Find Bugs → Fix → Optimize → Analyze Complexity → Generate Tests → Verify → Compare

### 1. PYTHON

## Prompt 1 – Code Generation

~~~
Act as a Python programmer. Write a beginner-friendly IoT sensor data processing program that accepts 
multiple sensor readings, calculates the minimum, maximum and average values, and identifies readings 
above a threshold of 100. Include input validation and use a function for modularity. Explain the logic briefly.

~~~

Code: 

~~~
def analyze_sensor_data(readings, threshold):
    minimum = min(readings)
    maximum = max(readings)
    average = sum(readings) / len(readings)
    abnormal = [x for x in readings if x > threshold]

    return minimum, maximum, average, abnormal


readings = [45, 67, 89, 120, 75]
threshold = 100

result = analyze_sensor_data(readings, threshold)

print("Minimum:", result[0])
print("Maximum:", result[1])
print("Average:", result[2])
print("Abnormal Values:", result[3])
~~~

## Output

~~~
Minimum: 45
Maximum: 120
Average: 79.2
Abnormal Values: [120]

~~~

## Prompt 2 – Bug Identification and Debugging

~~~
Analyze the Python program for syntax, logical and runtime errors. 
Check especially for empty input, invalid negative readings and incorrect boundary conditions. 
Explain the errors and provide corrected code.

~~~

Bug Identified:

The original program does not properly handle an empty list. Functions such as min() and max() will produce an error, and division by zero can occur while calculating the average.

Corrected Code:

~~~
def analyze_sensor_data(readings, threshold):
    valid = [x for x in readings if x >= 0]

    if not valid:
        return None

    minimum = min(valid)
    maximum = max(valid)
    average = sum(valid) / len(valid)
    abnormal = [x for x in valid if x > threshold]

    return minimum, maximum, average, abnormal


readings = [45, 67, 89, 120, 75]
threshold = 100

result = analyze_sensor_data(readings, threshold)

if result:
    print("Minimum:", result[0])
    print("Maximum:", result[1])
    print("Average:", result[2])
    print("Abnormal Values:", result[3])
else:
    print("No valid sensor readings.")

~~~

## Prompt 3 – Code Optimization

~~~
Optimize the corrected Python program for readability, modularity and efficiency without changing its functionality.
Use meaningful names and avoid unnecessary operations.

~~~

Optimization:

The code was improved using:

- Meaningful variable names
- Input validation
- Modular function design
- Simple list processing
- Clear conditional logic

## Prompt 4 – Complexity Analysis

~~~
Analyze the time and auxiliary space complexity of this Python sensor-processing program for n sensor readings. 
Explain the complexity briefly.

~~~

Analysis:

The program processes the readings a fixed number of times.

1) Time Complexity: O(n).
2) Auxiliary Space Complexity: O(n).

The additional lists used for valid and abnormal readings require memory proportional to the input size.

## Prompt 5 – Unit Test Generation

~~~
Generate unit test cases for the Python sensor-processing program. 
Include normal, boundary, abnormal, invalid and empty inputs with expected outputs.

~~~


| Test Case | Input         | Expected Result          |
| --------- | ------------- | ------------------------ |
| TC01      | `[45,67,89]`  | Normal                   |
| TC02      | `[0,50,100]`  | No abnormal value        |
| TC03      | `[120,130]`   | Abnormal values detected |
| TC04      | `[-10,50,80]` | Negative value ignored   |
| TC05      | `[]`          | No valid readings        |


### 2. C

## Prompt 1 – Code Generation

~~~
Act as a C programmer. Write a program for IoT sensor data processing that accepts multiple sensor readings, 
calculates minimum, maximum and average values, and identifies values above 100. 
Include input validation and modular functions. Keep the code beginner-friendly.

~~~

AI-Generated Code:

~~~
#include <stdio.h>

void analyze(int readings[], int n, int threshold)
{
    int min = readings[0];
    int max = readings[0];
    int sum = 0;

    for (int i = 0; i < n; i++)
    {
        if (readings[i] < min)
            min = readings[i];

        if (readings[i] > max)
            max = readings[i];

        sum += readings[i];
    }

    printf("Minimum: %d\n", min);
    printf("Maximum: %d\n", max);
    printf("Average: %.2f\n", (float)sum / n);
}

int main()
{
    int readings[] = {45, 67, 89, 120, 75};
    analyze(readings, 5, 100);

    return 0;
}
~~~

Output:

~~~
Minimum: 45
Maximum: 120
Average: 79.20

~~~

## Prompt 2 – Bug Identification and Debugging

~~~
Analyze this C program for runtime, logical and boundary errors. 
Check empty input, array access, division by zero, integer division and invalid readings. Provide corrected code.

~~~

Bug Identified:

The program accesses readings[0] even when the number of readings is zero. It also does not validate negative readings.

Correction:

~~~
if (n <= 0)
{
    printf("No valid sensor readings.\n");
    return;
}

~~~

The average is calculated using:

(float)sum / count

to ensure floating-point division.

## Prompt 3 – Code Optimization

~~~
Optimize the corrected C program for readability, efficiency and safe input handling. Keep the implementation simple and modular.
~~~

Optimization:

- Added input-size validation.
- Used a separate processing function.
- Used floating-point division for average.
- Used meaningful variables.
- Removed unnecessary operations.
- Prompt 4 – Complexity Analysis

~~~
Determine the time and auxiliary space complexity of the C sensor-processing program for n readings.
~~~

Time Complexity: O(n)
Auxiliary Space Complexity: O(1)

The array is traversed a constant number of times and only a fixed number of additional variables are used.

## Prompt 5 – Unit Test Generation

~~~
Generate unit test cases for the C sensor-processing program covering normal, boundary, abnormal, invalid and empty input.
~~~

| Test Case | Input         | Expected Result          |
| --------- | ------------- | ------------------------ |
| TC01      | `{45,67,89}`  | Normal                   |
| TC02      | `{0,50,100}`  | No abnormal value        |
| TC03      | `{120,130}`   | Abnormal values detected |
| TC04      | `{-10,50,80}` | Invalid value handled    |
| TC05      | Empty input   | Error handled safely     |


## 3. JAVA
   
## Prompt 1 – Code Generation

~~~
Act as a Java programmer. Create a beginner-friendly IoT sensor data processing program that calculates minimum,
maximum and average values and identifies readings above 100. Use a method for modularity and include input validation.
~~~

AI-Generated Code:

~~~
public class SensorAnalysis {

    static void analyze(int[] readings, int threshold) {

        int min = readings[0];
        int max = readings[0];
        int sum = 0;

        for (int value : readings) {
            if (value < min)
                min = value;

            if (value > max)
                max = value;

            sum += value;
        }

        System.out.println("Minimum: " + min);
        System.out.println("Maximum: " + max);
        System.out.println("Average: " +
                (double) sum / readings.length);
    }

    public static void main(String[] args) {

        int[] readings = {45, 67, 89, 120, 75};

        analyze(readings, 100);
    }
}

~~~

Output:

~~~

Minimum: 45
Maximum: 120
Average: 79.2
~~~

## Prompt 2 – Bug Identification and Debugging

~~~
Analyze this Java program for runtime and logical errors.
Check empty arrays, invalid readings, array access and average calculation.
Provide corrected code and explain the corrections briefly.

~~~

Bug Identified:

The program directly accesses readings[0]. An empty array causes an ArrayIndexOutOfBoundsException.

Correction:
~~~
if (readings == null || readings.length == 0) {
    System.out.println("No valid sensor readings.");
    return;
}
~~~

Invalid negative readings are also ignored during processing.

## Prompt 3 – Code Optimization
~~~
Optimize the corrected Java program for readability, modularity and efficient processing while preserving the same functionality.
~~~

- Optimization
- Added null and empty-array checks.
- Used a separate method.
- Used meaningful variable names.
- Ignored invalid readings.
- Used enhanced for loops.

## Prompt 4 – Complexity Analysis

~~~
Analyze the time and auxiliary space complexity of the Java sensor-processing program for n readings.
~~~


Time Complexity: O(n)
Auxiliary Space Complexity: O(1)

The input array is processed linearly and only a fixed number of variables are used.

## Prompt 5 – Unit Test Generation

~~~
Generate unit test cases for the Java sensor-processing program covering normal, boundary, abnormal, invalid and empty inputs.
~~~


| Test Case | Input         | Expected Result          |
| --------- | ------------- | ------------------------ |
| TC01      | `{45,67,89}`  | Normal                   |
| TC02      | `{0,50,100}`  | No abnormal value        |
| TC03      | `{120,130}`   | Abnormal values detected |
| TC04      | `{-10,50,80}` | Invalid value handled    |
| TC05      | `{}`          | Empty input handled      |


## AI OUTPUT COMPARISON

The three AI tools were compared based on their usefulness during the experiment.

| Parameter       | ChatGPT   | Gemini    | Copilot   |
| --------------- | --------- | --------- | --------- |
| Code Generation | Very Good | Very Good | Good      |
| Debugging       | Very Good | Good      | Very Good |
| Optimization    | Good      | Very Good | Good      |
| Unit Tests      | Very Good | Good      | Very Good |
| Explanation     | Detailed  | Detailed  | Concise   |
| Overall         | Very Good | Very Good | Very Good |


The comparison shows that different AI tools may produce different solutions for the same requirement. Therefore, the generated code must be executed and verified before use.

## MANUAL CODING VS AI-ASSISTED CODING

| Parameter        | Manual Coding                 | AI-Assisted Coding      |
| ---------------- | ----------------------------- | ----------------------- |
| Development Time | Higher                        | Lower                   |
| Code Generation  | Manual                        | AI-assisted             |
| Debugging        | Manual                        | AI-assisted             |
| Optimization     | Programmer-dependent          | AI suggestions          |
| Test Generation  | Manual                        | Faster                  |
| Error Risk       | Programmer-dependent          | AI may introduce errors |
| Learning         | Strong conceptual involvement | Requires verification   |
| Productivity     | Moderate                      | Higher                  |


## CODE QUALITY ANALYSIS

The generated programs were evaluated based on:

1) Correctness – Verified through execution and test cases.
   
2) Readability – Improved using meaningful names and simple logic.
   
3) Modularity – Functions/methods were used for processing.
   
4) Efficiency – All three implementations have O(n) time complexity.
   
5) Maintainability – Clear and modular code is easier to modify.
   
6) Error Handling – Empty and invalid inputs were considered.
    
7) Testing – Unit test cases were generated and verified.

AI-generated code was useful for reducing development time, but execution and manual verification were necessary to ensure correctness.

## OBSERVATION

The experiment showed that prompt quality directly affects the quality of AI-generated programming solutions. Prompts containing the programming language, role, requirements, constraints, expected behavior, and desired output produced more useful responses.

AI tools were helpful in generating code, identifying errors, suggesting optimizations, analyzing complexity, and creating test cases. However, the generated code still required human review and execution.

## RESULT

Python, C, and Java programs for IoT sensor data processing were successfully generated using AI-assisted programming.

The programs were debugged, optimized, analyzed for complexity, and tested using AI-generated prompts. The outputs of multiple AI tools were compared, and AI-assisted programming was compared with manual coding.

Thus, the experiment successfully demonstrated the use of effective AI prompting throughout the programming and debugging workflow.

## CONCLUSION

AI tools can assist programmers throughout the software development process, from code generation to debugging and testing. However, AI-generated code should not be accepted without verification.
