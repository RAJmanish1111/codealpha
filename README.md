#include <iostream>
#include <string>
#include <algorithm>

using namespace std;
string toLowercase(string input)
{
    transform(input.begin(), input.end(), input.begin(), ::tolower);
    return input;
}

bool containsSubstring(string input, string keyword)
{
    return input.find(keyword) != string::npos;
}

string getResponse(string input)
{
    input = toLowercase(input);

    if (containsSubstring(input, "hello") || containsSubstring(input, "hi"))
    {
        return "Hello! How can I help you today?";
    }
    else if (containsSubstring(input, "how are you"))
    {
        return "I'm doing great, thanks for asking! just here,ready to chat with you.how about you? How are you doing?";
    }
    else if (containsSubstring(input, "weather"))
    {
        return "I'm sorry, I don't have access to real-time weather data.";
    }
    else
    {
        return "I'm sorry, I didn't understand your question.";
    }
}

int main()
{
    cout << "Welcome to the chatbot! You can start chatting. Type 'exit' to quit." << endl;

    string userInput;
    while (true)
    {
        cout << "You: ";
        getline(cin, userInput);

        if (toLowercase(userInput) == "exit")
        {
            cout << "Goodbye! Seeyou soon";
            break;
        }

        string response = getResponse(userInput);
        cout << "Bot: " << response << endl;
    }

    return 0;
}
