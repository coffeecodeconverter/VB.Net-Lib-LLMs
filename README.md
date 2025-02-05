# VB.Net-Lib-LLMs
VB.Net Lib - Interact with LLMs easily local (ollama / lm studio) or online (OpenAI)


# LLM Interaction Module

## Requirements
- .NET Framework 4.5.1 or higher
- `Newtonsoft.JSON` NuGet Package

## Description

This module provides a comprehensive solution for easily interacting with large language models (LLMs) both locally (e.g., using Ollama or LM Studio) and online (e.g., OpenAI). The module is highly configurable and allows for seamless integration with various LLM endpoints.

### Default Configuration:
By default, the module is set to use LM Studio as the preferred method. However, you can change the `"defaultAIEndpoint"` value to any endpoint you wish to use.

### Main Features:
- A single, highly configurable function that supports:
  - Streaming on/off.
  - Automatic detection to use Ollama, LM Studio, or OpenAI formatting based on the provided URL.
  - Support for setting parameters such as:
    - Temperature
    - TopP
    - MaxTokens
    - Model
    - Endpoint
    - Image data
- The ability to mix between multiple LLMs on a per-function call basis.

### Note:
The main function defaults to streaming the response asynchronously. You will need to create your own callback function to update UI elements, such as a textbox, with the captured responses.

## Main Function

```vb
Await AskAI()
```vb

## Bare Minimum Example
```vb
Await AskAI(userInput, callBackFunc:=AddressOf MyCallBackFunction)
```vb


## Using All Parameters Example
```vb
Await AskAI(userInput, systemPrompt, maxTokens, temperature, topP, modelName, imageData, endpoint, apiKey, streamResponse, AddressOf MyCallBackFunction)
```vb


## Example Callback function
```vb
Public Sub MyCallBackFunction(text As String)
    If TextBox_AIResponse.InvokeRequired Then
        TextBox_AIResponse.Invoke(New Action(Of String)(AddressOf MyCallBackFunction), text)
    Else
        TextBox_AIResponse.AppendText(text)
        TextBox_AIResponse.SelectionStart = TextBox_AIResponse.TextLength
        TextBox_AIResponse.ScrollToCaret()
    End If
End Sub
```vb





