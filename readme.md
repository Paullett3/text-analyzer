ALGORITHM Sentence_Analyzer
VAR
    length_counter : INTEGER
    word_counter : INTEGER
    vowel_counter : INTEGER
    sentence : STRING
    current_char : CHARACTER
    i : INTEGER

BEGIN
    // --- 1. INITIALIZATION ---
    // Set all counters to zero before we start
    length_counter := 0
    word_counter := 0
    vowel_counter := 0
    i := 0  // This tracks which character we are reading

    // Ask the user for input
    Write("Please enter a sentence ending with a point: ")
    Read(sentence)

    // --- 2. THE LOOP ---
    // We look at the first character
    current_char := sentence[i]

    // Repeat this block WHILE the character is NOT a point
    WHILE (current_char <> ".") DO
        
        // A. Update Length
        // We found a character, so add 1 to length
        length_counter := length_counter + 1

        // B. Check for Vowels
        // Check if the character is in our list of vowels
        IF (current_char = "a" OR current_char = "e" OR current_char = "i" OR 
            current_char = "o" OR current_char = "u") THEN
            vowel_counter := vowel_counter + 1
        END_IF

        // C. Check for Words
        // If we find a space, a word has just ended
        IF (current_char = " ") THEN
            word_counter := word_counter + 1
        END_IF

        // --- Move to the next character ---
        i := i + 1
        current_char := sentence[i]

    END_WHILE

    // --- 3. FINAL ADJUSTMENT ---
    // We must count the point itself as part of the length (optional, depending on strict instructions)
    // But usually, "length of sentence" includes the punctuation.
    length_counter := length_counter + 1 

    // The last word ends with a point, not a space, so we add 1 to the word count
    // (Only if the sentence wasn't empty)
    IF (length_counter > 1) THEN
        word_counter := word_counter + 1
    END_IF

    // --- 4. OUTPUT RESULTS ---
    Write("Length of sentence: ", length_counter)
    Write("Number of words: ", word_counter)
    Write("Number of vowels: ", vowel_counter)

# Project: Sentence Analysis Algorithm

## 📌 Overview
This algorithm is designed to analyze a sentence sequentially, character by character, until a termination signal (a period `.`) is reached. It solves the problem of extracting statistical data from text without using high-level built-in functions.

 Logic Breakdown
1.Sequential Access: The algorithm reads the string one index at a time (`sentence[i]`).
2. The While Loop: This is used because we do not know the length of the sentence beforehand; we only know it ends with a specific character (`.`).
3. Conditional Checks (If/Else): inside the loop, we filter characters:
    Is it a vowel? -> Add to `vowel_counter`
    Is it a space? -> Add to `word_counter`
    Is it a char?  -> Add to `length_counter`

Variables
`length_counter`: Total characters including spaces and the point.
`word_counter`: Counts spaces, then adds +1 at the end to get total words.
`vowel_counter`: Tracks occurrences of [a, e, i, o, u].
