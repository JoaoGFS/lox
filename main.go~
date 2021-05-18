package main

import (
	"fmt"
	"os"

	"ed.local/utils"
)

var hadError bool

func main() {
	if len(os.Args) > 2 {
		fmt.Println("Usage: lox [script]")
		os.Exit(64)
	} else if len(os.Args) == 2 {
		runFile(os.Args[1])
	} else {
		runPrompt()
	}
}

func runFile(file string) {
	src := utils.ReadTextFile(file)

	run(src)

	if hadError {
		os.Exit(65)
	}
}

func runPrompt() {
	var line string
	for {
		line = utils.ReadLine("> ")
		if line == "\n" {
			break
		}
		run(line)
	}
}

// TODO: finish run()
func run(source string) {
	scanner := Scanner{
		source:  source,
		start:   0,
		current: 0,
		line:    1,
	}

	fmt.Println(scanner.scanTokens())
}

func Error(line int, message string) {
	Report(line, "", message)
}

func Report(line int, where string, message string) {
	fmt.Printf("[line %v] Error %v: %v", line, where, message)
	hadError = true
}
