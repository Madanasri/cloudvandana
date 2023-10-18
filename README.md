import java.util.Arrays;
import java.util.Collections;
import java.util.List;

public class ShuffleArray {
    public static void main(String[] args) {
        Integer[] array = {1, 2, 3, 4, 5, 6, 7};
        
        // Convert the array to a list for shuffling
        List<Integer> list = Arrays.asList(array);
        
        // Shuffle the list
        Collections.shuffle(list);
        
        // Convert the shuffled list back to an array
        list.toArray(array);
        
        // Print the shuffled array
        System.out.println("Shuffled Array: " + Arrays.toString(array));
    }
}



import java.util.HashMap;
import java.util.Scanner;

public class RomanToInteger {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter a Roman numeral: ");
        String romanNumeral = scanner.nextLine().toUpperCase();
        scanner.close();

        int result = romanToInt(romanNumeral);

        if (result != -1) {
            System.out.println("Roman numeral " + romanNumeral + " is equivalent to integer " + result);
        } else {
            System.out.println("Invalid Roman numeral.");
        }
    }

    public static int romanToInt(String s) {
        HashMap<Character, Integer> romanMap = new HashMap<>();
        romanMap.put('I', 1);
        romanMap.put('V', 5);
        romanMap.put('X', 10);
        romanMap.put('L', 50);
        romanMap.put('C', 100);
        romanMap.put('D', 500);
        romanMap.put('M', 1000);

        int result = 0;
        int prevValue = 0;

        for (int i = s.length() - 1; i >= 0; i--) {
            int curValue = romanMap.get(s.charAt(i));

            if (curValue < prevValue) {
                result -= curValue;
            } else {
                result += curValue;
            }

            prevValue = curValue;
        }

        // Check for invalid Roman numerals
        if (result != -1) {
            return result;
        } else {
            return -1;
        }
    }
}




import java.util.HashSet;
import java.util.Scanner;
import java.util.Set;

public class PangramChecker {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter a sentence: ");
        String input = scanner.nextLine();
        scanner.close();

        if (isPangram(input)) {
            System.out.println("The input is a pangram.");
        } else {
            System.out.println("The input is not a pangram.");
        }
    }

    public static boolean isPangram(String input) {
        // Remove spaces and convert to lowercase for consistent checking
        input = input.replaceAll(" ", "").toLowerCase();
        
        Set<Character> alphabetSet = new HashSet<>();
        
        for (int i = 0; i < input.length(); i++) {
            char c = input.charAt(i);
            
            if (Character.isLetter(c)) {
                alphabetSet.add(c);
            }
        }

        return alphabetSet.size() == 26; // There are 26 letters in the English alphabet
    }
}



function reverseWords(sentence) {
    // Split the sentence into words
    const words = sentence.split(' ');

    // Reverse each word and store them in an array
    const reversedWords = words.map(word => {
        return word.split('').reverse().join('');
    });

    // Join the reversed words to form the reversed sentence
    const reversedSentence = reversedWords.join(' ');

    return reversedSentence;
}

// Example usage:
const inputSentence = "This is a sunny day";
const reversedSentence = reverseWords(inputSentence);
console.log(reversedSentence);



const arr = [4, 2, 7, 1, 9, 3];

arr.sort(function(c, d) {
  return d - c;
});

console.log(arr);




<!DOCTYPE html>
<html>
<head>
    <title>Basic Calculator</title>
    <style>
        /* Add some basic styling for the calculator */
        body {
            font-family: Arial, sans-serif;
            text-align: center;
        }
        #calculator {
            width: 300px;
            margin: 0 auto;
            padding: 10px;
            background-color: #f2f2f2;
            border: 1px solid #ccc;
        }
    </style>
</head>
<body>
    <div id="calculator">
        <h2>Basic Calculator</h2>
        <input type="text" id="result" readonly>
        <br>
        <button onclick="clearResult()">C</button>
        <button onclick="appendToResult('7')">7</button>
        <button onclick="appendToResult('8')">8</button>
        <button onclick="appendToResult('9')">9</button>
        <button onclick="appendToResult('+')">+</button>
        <br>
        <button onclick="appendToResult('4')">4</button>
        <button onclick="appendToResult('5')">5</button>
        <button onclick="appendToResult('6')">6</button>
        <button onclick="appendToResult('-')">-</button>
        <br>
        <button onclick="appendToResult('1')">1</button>
        <button onclick="appendToResult('2')">2</button>
        <button onclick="appendToResult('3')">3</button>
        <button onclick="appendToResult('*')">*</button>
        <br>
        <button onclick="appendToResult('0')">0</button>
        <button onclick="calculateResult()">=</button>
        <button onclick="appendToResult('/')">/</button>
    </div>

    <script>
        // JavaScript functions for the calculator
        function appendToResult(value) {
            document.getElementById('result').value += value;
        }

        function clearResult() {
            document.getElementById('result').value = '';
        }

        function calculateResult() {
            try {
                document.getElementById('result').value = eval(document.getElementById('result').value);
            } catch (error) {
                document.getElementById('result').value = 'Error';
            }
        }
    </script>
</body>
</html>



<!DOCTYPE html>
<html>
<head>
    <title>Survey Form</title>
    <style>
        /* Add some basic styling for the form and popup */
        body {
            font-family: Arial, sans-serif;
            text-align: center;
        }
        #survey-form {
            width: 300px;
            margin: 0 auto;
            padding: 20px;
            background-color: #f2f2f2;
            border: 1px solid #ccc;
        }
        #popup {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.7);
            z-index: 1;
            justify-content: center;
            align-items: center;
        }
        #popup-content {
            background-color: #fff;
            padding: 20px;
            border-radius: 5px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
        }
    </style>
</head>
<body>
    <form id="survey-form">
        <label for="first-name">First Name:</label>
        <input type="text" id="first-name" required><br><br>

        <label for="last-name">Last Name:</label>
        <input type="text" id="last-name" required><br><br>

        <label for="date-of-birth">Date of Birth:</label>
        <input type="date" id="date-of-birth" required><br><br>

        <label for="country">Country:</label>
        <select id="country" required>
            <option value="USA">USA</option>
            <option value="Canada">Canada</option>
            <option value="UK">UK</option>
            <!-- Add more countries as needed -->
        </select><br><br>

        <label>Gender:</label>
        <label for="male">Male</label>
        <input type="checkbox" id="male">
        <label for="female">Female</label>
        <input type="checkbox" id="female"><br><br>

        <label for="profession">Profession:</label>
        <input type="text" id="profession" required><br><br>

        <label for="email">Email:</label>
        <input type="email" id="email" required><br><br>

        <label for="mobile-number">Mobile Number:</label>
        <input type="tel" id="mobile-number" required><br><br>

        <button type="button" id="submit-button" onclick="submitForm()">Submit</button>
        <button type="button" id="reset-button" onclick="resetForm()">Reset</button>
    </form>

    <div id="popup">
        <div id="popup-content">
            <h2>Survey Results</h2>
            <p>First Name: <span id="popup-first-name"></span></p>
            <p>Last Name: <span id="popup-last-name"></span></p>
            <p>Date of Birth: <span id="popup-date-of-birth"></span></p>
            <p>Country: <span id="popup-country"></span></p>
            <p>Gender: <span id="popup-gender"></span></p>
            <p>Profession: <span id="popup-profession"></span></p>
            <p>Email: <span id="popup-email"></span></p>
            <p>Mobile Number: <span id="popup-mobile-number"></span></p>
            <button type="button" onclick="closePopup()">Close</button>
        </div>
    </div>

    <script>
        function submitForm() {
            // Get values from form fields
            const firstName = document.getElementById('first-name').value;
            const lastName = document.getElementById('last-name').value;
            const dateOfBirth = document.getElementById('date-of-birth').value;
            const country = document.getElementById('country').value;
            const genderMale = document.getElementById('male').checked ? 'Male' : '';
            const genderFemale = document.getElementById('female').checked ? 'Female' : '';
            const profession = document.getElementById('profession').value;
            const email = document.getElementById('email').value;
            const mobileNumber = document.getElementById('mobile-number').value;

            // Display values in the popup
            document.getElementById('popup-first-name').textContent = firstName;
            document.getElementById('popup-last-name').textContent = lastName;
            document.getElementById('popup-date-of-birth').textContent = dateOfBirth;
            document.getElementById('popup-country').textContent = country;
            document.getElementById('popup-gender').textContent = genderMale + ' ' + genderFemale;
            document.getElementById('popup-profession').textContent = profession;
            document.getElementById('popup-email').textContent = email;
            document.getElementById('popup-mobile-number').textContent = mobileNumber;

            // Show the popup
            document.getElementById('popup').style.display = 'flex';
        }

        function resetForm() {
            // Reset form fields
            document.getElementById('survey-form').reset();
        }

        function closePopup() {
            // Close the popup
            document.getElementById('popup').style.display = 'none';
        }
    </script>
</body>
</html>



