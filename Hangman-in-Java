import java.util.Scanner;
import java.lang.Character;
 
/**
 * Hangman Find The Word To Save The Man
 *
 * @author Süleyman Yasir Kula
 * @version 1.00 2012/12/29
 */
 
public class Hangman
{
    public static void main( String[] args )
    {
        Scanner scan = new Scanner( System.in );
 
        // CONSTANTS
        String[] WORDS1 = new String[] { "New York", "Los Angeles", "Chicago", "Houston", "Philadelphia", "Phoenix", "San Antonio", "San Diego", "Dallas", "San Jose", "Indianapolis", "San Francisco", "Detroit", "Seattle", "Denver", "Las Vegas", "Kansas City", "Atlanta", "Lincoln", "Istanbul", "Ankara" };
        String[] WORDS2 = new String[] { "Abraham Lincoln", "Martin Luther King", "Albert Einstein", "Elvis Presley", "George Washington", "Leonardo Da Vinci", "Gandhi", "Napoleon", "Michelangelo", "Mozart", "Neil Armstrong", "William Shakespeare", "Thomas Edison", "Walt Disney", "Cleopatra", "Mohammad Ali", "Benjamin Franklin", "John Lennon", "Michael Jackson", "Michael Jordan", "Alexander Graham Bell", "Ataturk", "George Bush", "Bill Clinton", "Oprah Winfrey", "Isaac Newton", "Bill Gates", "Vladimir Putin", "Madonna", "Tom Cruise", "Britney Spears", "Tom Hanks", "Bob Dylan", "Pele", "Stephen Hawking", "Harrison Ford", "Jay Leno" };
        String[] WORDS3 = new String[] { "The Shawshank Redemption", "The Godfather", "Twelve Anry Men", "The Dark Knight", "Harry Potter", "The Lord of The Rings", "Fight Club", "Star Wars", "Avatar", "Inception", "Matrix", "Memento", "Alien", "Aliens", "Wall E", "Gladiator", "Spartacus", "The Green Mile", "Walking Dead", "Prestige", "Reservoir Dogs", "Tsubasa", "Pokemon", "Madagascar", "Tron", "Leverage", "Merlin", "Doctor Who", "Taxi Driver", "Toy Story", "Lion King", "Braveheart", "Superman", "Smallville", "Blade Runner", "SpongeBob SquarePants", "The Avengers", "Scarface", "Jaws", "The Sixth Sense", "The Wizard of Oz", "Finding Nemo", "V for Vendetta", "Terminator", "Slumdog Millionaire", "Twelve Monkeys", "Ratatouille", "Star Trek", "Rain Man", "Jurassic Park" };
        String[] WORDS4 = new String[] { "Grand Theft Auto", "Mario", "The Sims", "Tetris", "Call of Duty", "FIFA", "Pro Evolution Soccer", "PES", "Need for Speed", "Mass Effect", "DOTA", "Sonic the Hedgehog", "The Legend of Zelda", "Gran Turismo", "Resident Evil", "Donkey Kong", "Halo", "Battlefield", "Medal of Honor", "Bejeweled", "Zuma", "Tekken", "Guitar Hero", "Harry Potter", "Star Wars", "Street Fighter", "Metal Gear", "Mortal Kombat", "Counter Strike", "Half Life", "Assassins Creed", "God of War", "Diablo", "Lemmings", "Rayman", "World of Warcraft", "Warcraft", "SimCity", "Minecraft", "Prince of Persia", "Uncharted", "Dead Space", "The Elder Scrolls", "Fallout", "Driver", "Burnout", "Worms", "Red Dead Redemption", "Devil May Cry", "Starcraft", "Mass Effect", "Civilization", "Hitman", "Saints Row", "Rollercoaster Tycoon", "Bioshock", "Doom", "Max Payne" };
//      String[] HINTS  = new String[] { "A city", "A famous person", "A movie/TV series", "A digital game" };
 
        // VARIABLES
        String currentWord;
        String wordToShow;
        String usedLetters;
 
        int lives;
        int category;
 
        float seconds;
        long startTime;
        long finishTime;
 
        boolean completed;
        boolean letterMatched;
 
        char currentLetter;
        char playAgain;
 
        // PROGRAM CODE
        // Greet user
        System.out.println( "Greetings, and welcome. I wanna play a game. So, let the game begin!\n" );
 
        do
        {
            // GAME CODE
            // 1- Pick a word and set number of lives
            System.out.println( "1: Cities \n2: Famous people \n3: Movies/TV series \n4: Digital Games" );
            System.out.print( "Pick a category (1-4) (Other numbers for random category): " );
            category = scan.nextInt();
 
            if( category < 1 || category > 4 )
            {
                category = (int)( Math.random() * 4 + 1 );
            }
 
            if( category == 1 )
            {
                currentWord = WORDS1[ ( int ) ( Math.random() * WORDS1.length ) ];
                System.out.println( "\nChoosed: Cities" );
            }
            else if( category == 2 )
            {
                currentWord = WORDS2[ ( int ) ( Math.random() * WORDS2.length ) ];
                System.out.println( "\nChoosed: Famous people" );
            }
            else if( category == 3 )
            {
                currentWord = WORDS3[ ( int ) ( Math.random() * WORDS3.length ) ];
                System.out.println( "\nChoosed: Movies/TV series" );
            }
            else
            {
                currentWord = WORDS4[ ( int ) ( Math.random() * WORDS4.length ) ];
                System.out.println( "\nChoosed: Digital Games" );
            }
 
            wordToShow = convertWord( currentWord );
            lives = 9;
            completed = false;
            usedLetters = "";
 
            startTime = System.nanoTime();
 
            // 2- While user has live(s) remaining - do:
            while( lives > 0 && !completed )
            {
                // 2.1- Show a hangman scene and the number of lives
                System.out.println( "\n" + drawHangman( lives ) );
                System.out.println( "\nYou have " + ( lives - 1 ) + " more live(s)." );
 
                // 2.2- Show the current word with the known letters (if there is any)
                System.out.println( "\nWORD: " + wordToShow );
 
                // 2.3- Show used letters
                System.out.print( "\nUSED LETTERS: " );
 
                if( usedLetters.length() == 0 )
                {
                    System.out.println( "none\n" );
                }
                else
                {
                    for( int i = 0; i < usedLetters.length(); i++ )
                    {
                        System.out.print( usedLetters.charAt( i ) + " " );
                    }
 
                    System.out.println( "\n" );
                }
 
                // 2.4- Ask a letter from user and decrement lives if letter is not in the word, otherwise change the wordToShow properly
                do
                {
                    System.out.println( "Enter a letter you haven't entered ( A-Z ): " );
                    currentLetter = scan.next().charAt( 0 );
                    currentLetter = (char) Character.toUpperCase( (int) currentLetter );
                }
                while( !letterIsNew( currentLetter, usedLetters ) || (int) currentLetter < 65 || (int) currentLetter > 90 ); // 65: A and 90: Z in ASCII table
 
                letterMatched = false;
                for( int i = 0; i < currentWord.length(); i++ )
                {
                    if( Character.toUpperCase( currentWord.charAt( i ) ) == currentLetter ) // If letter is matched
                    {
                        if( i == 0 )
                        {
                            wordToShow = currentLetter + wordToShow.substring( 1 );
                        }
                        else if( i == currentWord.length() - 1 )
                        {
                            wordToShow = wordToShow.substring( 0, wordToShow.length() - 1 ) + currentLetter;
                        }
                        else
                        {
                            wordToShow = wordToShow.substring( 0, i ) + currentLetter + wordToShow.substring( i + 1 );
                        }
 
                        letterMatched = true;
                    }
                }
 
                if( !letterMatched )
                {
                    lives--;
                }
 
                // 2.5- Add currentLetter to usedLetters
                usedLetters = addNewLetterTo( usedLetters, currentLetter );
 
                // 2.6- Check whether user has won or not
                completed = true;
                for( int i = 0; i < wordToShow.length(); i++ )
                {
                    if( wordToShow.charAt( i ) == '-' )
                    {
                        completed = false;
                    }
                }
 
                // 2.7- Scroll down to make the previous part invisible
                for( int i = 0; i < 25; i++ )
                {
                    System.out.println();
                }
            }
 
            finishTime = System.nanoTime();
 
            seconds = ( float ) ( finishTime - startTime ) / 1000000000;
 
            if( lives == 0 )
            {
                System.out.println( drawHangman( 0 ) + "\n" );
                System.out.println( "  O   O  OOOO  O  O    O    OOOO  OOO  OOO   U \n" +
                                    "   O O   O  O  O  O    O    O  O  O     O    U \n" +
                                    "    O    O  O  O  O    O    O  O  OOO   O    U \n" +
                                    "    O    O  O  O  O    O    O  O    O   O      \n" +
                                    "    O    OOOO  OOOO    OOO  OOOO  OOO   O    * \n" );
                System.out.println( "You couldn't find the word " + currentWord.toUpperCase() + ". It took you " + seconds + " seconds to lose!!\n" );
 
            }
            else // Assert: User won the game ( i.e completed = true )
            {
                System.out.println( drawHangman( lives ) + "\n" );
                System.out.println( "  O   O  OOOO  O  O    O         O   OOOO  O   O   U \n" +
                                    "   O O   O  O  O  O    O    O    O   O  O  OO  O   U \n" +
                                    "    O    O  O  O  O     O   O   O    O  O  O O O   U \n" +
                                    "    O    O  O  O  O      O O O O     O  O  O  OO     \n" +
                                    "    O    OOOO  OOOO       O   O      OOOO  O   O   * \n" );
                System.out.println( "You have found the word " + wordToShow + " with " + ( lives - 1 ) + " more live(s) left in " + seconds + " seconds!\n" );
            }
 
            // 3- Ask if user wants to play again
            do
            {
                System.out.print( "Are you ready for another challenge (y/n): " );
                playAgain = scan.next().charAt( 0 );
            }
            while( playAgain != 'y' && playAgain != 'n' && playAgain != 'Y' && playAgain != 'N' );
 
            if( playAgain == 'Y' || playAgain == 'y' )
            {
                // Scroll down to make the previous part invisible
                for( int i = 0; i < 32; i++ )
                {
                    System.out.println();
                }
            }
        }
        while( playAgain != 'n' && playAgain != 'N' );
 
        // Assert: User wants to finish the game
        System.out.println( "\nSo be it...\n" );
    }
 
    // *** METHODS ***
    public static String addNewLetterTo( String usedLetters, char currentLetter )
    {
        // Add new letter in a way such that result will be in alphabetical order
        int i;
 
        if( usedLetters.length() == 0 )
        {
            usedLetters = "" + currentLetter;
        }
        else
        {
            i = 0;
            while( i < usedLetters.length() && (int) usedLetters.charAt( i ) < (int) currentLetter )
            {
                i++;
            }
 
            if( i == usedLetters.length() )
            {
                usedLetters = usedLetters + currentLetter;
            }
            else
            {
                usedLetters = usedLetters.substring( 0, i ) + currentLetter + usedLetters.substring( i  );
            }
        }
 
        return usedLetters;
    }
 
    public static boolean letterIsNew( char letter, String usedLetters )
    {
        for( int i = 0; i < usedLetters.length(); i++ )
        {
            if( usedLetters.charAt( i ) == letter )
            {
                return false;
            }
        }
 
        return true;
    }
 
    public static String convertWord( String word )
    {
        String result;
        result = "";
 
        for( int i = 0; i < word.length(); i++ )
        {
            if( word.charAt( i ) == ' ' )
            {
                result = result + " ";
            }
            else
            {
                result = result + "-";
            }
        }
 
        return result;
    }
 
    public static String drawHangman( int lives )
    {
        if( lives == 9 )
        {
            return " /-----\\ \n" +
                   " | ^ ^ |  \n" +
                   " |  |  |  \n" +
                   " |  V  |  \n" +
                  " \\-----/  \n";
        }
        else if( lives == 8 )
        {
            return " /-----\\ \n" +
                   " | ^ ^ |  \n" +
                   " |  |  |  \n" +
                   " |  V  |  \n" +
                  " \\-----/  \n" +
                   "    |     \n" +
                   "    |     \n" +
                   "    |     \n" +
                   "    |     \n" +
                   "    |      ";
        }
        else if( lives == 7 )
        {
            return " /-----\\ \n" +
                   " | | | |  \n" +
                   " |  |  |  \n" +
                   " |  -  |  \n" +
                  " \\-----/  \n" +
                   "    |     \n" +
                   "  /-|     \n" +
                   "  | |     \n" +
                   "  0 |     \n" +
                   "    |       ";
        }
        else if( lives == 6 )
        {
            return " /-----\\ \n" +
                   " | | | |  \n" +
                   " |  |  |  \n" +
                   " |  -  |  \n" +
                  " \\-----/  \n" +
                   "    |     \n" +
                   "  /-|-\\  \n" +
                   "  | | |   \n" +
                   "  0 | 0   \n" +
                   "    |       ";
        }
        else if( lives == 5 )
        {
            return " /-----\\ \n" +
                   " | | | |  \n" +
                   " |  |  |  \n" +
                   " |  ^  |  \n" +
                  " \\-----/  \n" +
                   "    |     \n" +
                   "  /-|-\\  \n" +
                   "  | | |   \n" +
                   "  0 | 0   \n" +
                   "    |     \n" +
                   "   /      \n" +
                   "  |       \n" +
                   "  V         ";
        }
        else if( lives == 4 )
        {
            return " /-----\\ \n" +
                   " | | | |  \n" +
                   " |  |  |  \n" +
                   " |  ^  |  \n" +
                  " \\-----/  \n" +
                   "    |     \n" +
                   "  /-|-\\  \n" +
                   "  | | |   \n" +
                   "  0 | 0   \n" +
                   "    |     \n" +
                   "   / \\   \n" +
                   "  |   |   \n" +
                   "  V   V     ";
        }
        else if( lives == 3 )
        {
            return " /          \n" +
                   " |          \n" +
                   " | /-----\\ \n" +
                   " | | O O |  \n" +
                   " | |  |  |  \n" +
                   " | |  ~  |  \n" +
                  " | \\-----/  \n" +
                   " |    |     \n" +
                   " |  /-|-\\  \n" +
                   " |  | | |   \n" +
                   " |  0 | 0   \n" +
                   " |    |     \n" +
                   " |   / \\   \n" +
                   " |  |   |   \n" +
                   " |  V   V     ";
        }
        else if( lives == 2 )
        {
            return " /            \n" +
                   " |            \n" +
                   " | /-----\\  \n" +
                   " | | O O |    \n" +
                   " | |  |  |    \n" +
                   " | |  ~  |    \n" +
                  " | \\-----/    \n" +
                   " |    |       \n" +
                   " |  /-|-\\    \n" +
                   " |  | | |     \n" +
                   " |  0 | 0     \n" +
                   " |    |       \n" +
                   " |   / \\     \n" +
                   " |  |   |     \n" +
                   " |  V   V     \n" +
                   " |  -----     \n" +
                   " |  |   |     \n" +
                   "--- |   |       ";
        }
        else if( lives == 1 )
        {
            return " /---------\\ \n" +
                   " |    |    |  \n" +
                   " | /-----\\ -  \n" +
                   " | | O O |    \n" +
                   " | |  |  |    \n" +
                   " | |  ~  |    \n" +
                  " | \\-----/    \n" +
                   " |    |       \n" +
                   " |  /-|-\\    \n" +
                   " |  | | |     \n" +
                   " |  0 | 0     \n" +
                   " |    |       \n" +
                   " |   / \\     \n" +
                   " |  |   |     \n" +
                   " |  V   V     \n" +
                   " |  -----     \n" +
                   " |  |   |     \n" +
                   "--- |   |       ";
        }
        else
        {
            return " /---------\\ \n" +
                   " |    |    |  \n" +
                   " | /-----\\ -  \n" +
                   " | | * * |    \n" +
                   " | |  |  |    \n" +
                   " | | RIP |    \n" +
                  " | \\-----/    \n" +
                   " |    |       \n" +
                   " |  /-|-\\    \n" +
                   " |  | | |     \n" +
                   " |  0 | 0     \n" +
                   " |    |       \n" +
                   " |   / \\     \n" +
                   " |  |   |  --|\n" +
                   " |  V   V    |\n" +
                   " |           |\n" +
                   " |           |\n" +
                   "---        --|  ";
        }
    }
 
} 
