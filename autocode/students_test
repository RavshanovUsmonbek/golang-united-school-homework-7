package coverage

import (
	"os"
	"testing"
	"time"
	"sort"
)

// DO NOT EDIT THIS FUNCTION
func init() {
	content, err := os.ReadFile("students_test.go")
	if err != nil {
		panic(err)
	}
	err = os.WriteFile("autocode/students_test", content, 0644)
	if err != nil {
		panic(err)
	}
}

// WRITE YOUR CODE BELOW
func TestPersonSortWithBirthday(t *testing.T){
	var p People 
	
	p = append(p, Person{
		firstName: "Usmonbek", 
		lastName: "Ravshanov", 
		birthDay: time.Date(1997, time.July, 28, 0, 0, 0, 0, time.UTC)})
	
	p = append(p, Person{
		firstName: "Usmonbek", 
		lastName: "Ravshanov", 
		birthDay: time.Date(1999, time.July, 28, 0, 0, 0, 0, time.UTC)})
	
	p = append(p, Person{
		firstName: "Usmonbek", 
		lastName: "Ravshanov", 
		birthDay: time.Date(1998, time.July, 28, 0, 0, 0, 0, time.UTC)})

	p = append(p, Person{
		firstName: "Usmonbek", 
		lastName: "Ravshanov", 
		birthDay: time.Date(2000, time.July, 28, 0, 0, 0, 0, time.UTC)})

	sort.Sort(p)
	testPeople := []time.Time{
		time.Date(2000, time.July, 28, 0, 0, 0, 0, time.UTC),
		time.Date(1999, time.July, 28, 0, 0, 0, 0, time.UTC),
		time.Date(1998, time.July, 28, 0, 0, 0, 0, time.UTC),
		time.Date(1997, time.July, 28, 0, 0, 0, 0, time.UTC),
	} 
	for index, value := range p {
		if testPeople[index] != value.birthDay {
			t.Errorf("Expected: %v, got: %v", testPeople[index], value.birthDay)
		} 
	}		
}

func TestPersonSortWithFirstName(t *testing.T){
	var p People 
	
	p = append(p, Person{
		firstName: "Alex", 
		lastName: "Ravshanov", 
		birthDay: time.Date(1997, time.July, 28, 0, 0, 0, 0, time.UTC)})
	
	p = append(p, Person{
		firstName: "Bob", 
		lastName: "Ravshanov", 
		birthDay: time.Date(1997, time.July, 28, 0, 0, 0, 0, time.UTC)})
	
	p = append(p, Person{
		firstName: "Cara", 
		lastName: "Ravshanov", 
		birthDay: time.Date(1997, time.July, 28, 0, 0, 0, 0, time.UTC)})

	p = append(p, Person{
		firstName: "Usmonbek", 
		lastName: "Ravshanov", 
		birthDay: time.Date(1997, time.July, 28, 0, 0, 0, 0, time.UTC)})

	sort.Sort(p)
	testPeople := []string{"Alex", "Bob", "Cara", "Usmonbek"} 
	for index, value := range p {
		if testPeople[index] != value.firstName {
			t.Errorf("Expected: %v, got: %v", testPeople[index], value.firstName)
		} 
	}
}

func TestPersonSortWithLastName(t *testing.T){
	var p People 
	
	p = append(p, Person{
		firstName: "Alex", 
		lastName: "Alison", 
		birthDay: time.Date(1997, time.July, 28, 0, 0, 0, 0, time.UTC)})

	p = append(p, Person{
		firstName: "Alex", 
		lastName: "Ravshanov", 
		birthDay: time.Date(1997, time.July, 28, 0, 0, 0, 0, time.UTC)})

	p = append(p, Person{
		firstName: "Alex", 
		lastName: "Green", 
		birthDay: time.Date(1997, time.July, 28, 0, 0, 0, 0, time.UTC)})

	p = append(p, Person{
		firstName: "Alex", 
		lastName: "Bing", 
		birthDay: time.Date(1997, time.July, 28, 0, 0, 0, 0, time.UTC)})


	sort.Sort(p)
	testPeople := []string{"Alison", "Bing", "Green", "Ravshanov"} 
	for index, value := range p {
		if testPeople[index] != value.lastName {
			t.Errorf("Expected: %v, got: %v", testPeople[index], value.lastName)
		} 
	}
}
//////////////////////// Matrix tests
var TestString string = "1 2 3\n3 4 5\n 9 9 9"
var MatrixCreateErrorMsg string = "Unable to create matrix"
var ErrorMsg string = "Expected: %d, got: %d"

func TestMatrixCreateWithDifferentRowLength(t *testing.T){
	testString := "1 2 3\n2 3 4\n4"
	_, err := New(testString)
	if err == nil {
		t.Errorf("Matrix created with variable length of rows:\n%s", testString)
	}
}

func TestMatrixCreateWithNotNumbers(t *testing.T){
	testString := "1 2 3\n2 3 4\nB C D"
	_, err := New(testString)
	if err == nil {
		t.Errorf("Matrix containing Nan element has been created")
	}
}

func TestMatrixCreateSuccessCase(t *testing.T){
	expectedMatrix := []int{1, 2, 3, 3, 4, 5, 9, 9, 9}
	matrix, err := New(TestString)
	if err != nil {
		t.Errorf("Unexpected matrix failure with error: %s", err)
	}
	if matrix.cols != 3 {
		t.Errorf("Expected column size: 3, Got: %d", matrix.cols)
	}
	if matrix.rows != 3 {
		t.Errorf("Expected column size: 3, Got: %d", matrix.rows)
	}
	for index, elem := range matrix.data {
		if expectedMatrix[index] != elem {
			expected := expectedMatrix[index]
			t.Errorf("Not matching matrix element. Expected in %d index: %d, got: %d", index, expected, elem)
		}
	}
}

func TestGetMatrixInRowRepresentation(t *testing.T){
	expectedMatrix := [][]int{{1, 2, 3}, {3, 4, 5}, {9, 9, 9}}
	matrix, err := New(TestString)
	if err != nil {
		t.Error(MatrixCreateErrorMsg)
	}

	rows := matrix.Rows()
	if len(rows) != len(expectedMatrix){
		t.Errorf("Number of rows " + ErrorMsg, len(expectedMatrix), len(rows))
	}
	for rowIndex, row := range rows {
		if len(row) != len(expectedMatrix[rowIndex]){
			expLength := len(expectedMatrix[rowIndex])
			t.Errorf("Row's length doesn't match. "+ ErrorMsg, expLength, len(row))
		}
		for colIndex, elem := range row {
			if expectedMatrix[rowIndex][colIndex] != elem {
				expEl := expectedMatrix[rowIndex][colIndex]
				t.Errorf("Elements don't match. " + ErrorMsg, expEl, elem)
			}
		}
	}
}


func TestGetMatrixInColRepresentation(t *testing.T){
	expectedMatrix := [][]int{{1, 3, 9}, {2, 4, 9}, {3, 5, 9}}
	matrix, err := New(TestString)

	if err != nil {
		t.Error(MatrixCreateErrorMsg)
	}

	cols := matrix.Cols()
	if len(cols) != len(expectedMatrix){
		t.Errorf("Number of cols expected: %d, got: %d", len(expectedMatrix), len(cols))
	}
	for colIndex, col := range cols {
		if len(col) != len(expectedMatrix[colIndex]){
			expLength := len(expectedMatrix[colIndex])
			t.Errorf("Column's length doesn't match. "+ ErrorMsg, expLength, len(col))
		}
		for rowIndex, elem := range col {
			if expectedMatrix[colIndex][rowIndex] != elem {
				expEl := expectedMatrix[colIndex][rowIndex]
				t.Errorf("Elements don't match. "+ ErrorMsg, expEl, elem)
			}
		}
	}
}

func TestSetValueWithRowSmallerThanZero(t *testing.T){
	matrix, err := New(TestString)

	if err != nil {
		t.Error(MatrixCreateErrorMsg)
	}
	isSet := matrix.Set(2, -1, 56)
	if isSet {
		t.Error("Check for rows smaller than zero was not caugth")
	}
}

func TestSetValueWithRowGreaterThanMaxRowCount(t *testing.T){
	matrix, err := New(TestString)

	if err != nil {
		t.Error(MatrixCreateErrorMsg)
	}
	isSet := matrix.Set(2, 5, 56)
	if isSet {
		t.Error("Check for row greater than maximum row count was not caugth")
	}
}

func TestSetValueWithColSmallerThanZero(t *testing.T){
	matrix, err := New(TestString)

	if err != nil {
		t.Error(MatrixCreateErrorMsg)
	}
	isSet := matrix.Set(-1, 2, 56)
	if isSet {
		t.Error("Check for column smaller than zero was not caugth")
	}
}

func TestSetValueWithColumnGreaterThanMaxRowCount(t *testing.T){
	matrix, err := New(TestString)

	if err != nil {
		t.Error(MatrixCreateErrorMsg)
	}
	isSet := matrix.Set(5, 1, 56)
	if isSet {
		t.Error("Check for column greater than maximum column count was not caugth")
	}
}


func TestSetValueSuccessCase(t *testing.T){
	matrix, err := New(TestString)
	row := 1
	col := 1
	value := 56

	if err != nil {
		t.Error(MatrixCreateErrorMsg)
	}
	isSet := matrix.Set(row, col, value)
	if !isSet {
		t.Error("Could not set value with valid row and column indices")
	}
	
	if matrix.data[row*matrix.cols+col] != value {
		expected := matrix.data[row*matrix.cols+col]
		t.Errorf("elements don't match after set. "+ ErrorMsg, expected, value)
	} 
}


