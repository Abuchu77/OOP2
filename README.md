class Book:
    def __init__(self, title, author, ISBN, available_copies):
        self.title = title
        self.author = author
        self.ISBN = ISBN
        self.available_copies = available_copies

class Library:
    def __init__(self):
        self.books = []

    def add_book(self, book):
        self.books.append(book)

    def remove_book(self, ISBN):
        for book in self.books:
            if book.ISBN == ISBN:
                self.books.remove(book)
                return

    def search_book(self, title):
        for book in self.books:
            if book.title == title:
                return book
        return None

    def check_out_book(self, title):
        book = self.search_book(title)
        if book and book.available_copies > 0:
            book.available_copies -= 1
            return f"Checked out: {book.title} by {book.author}"
        elif book:
            return "No available copies of this book."
        else:
            return "Book not found in the library."

    def check_in_book(self, title):
        book = self.search_book(title)
        if book:
            book.available_copies += 1
            return f"Returned: {book.title} by {book.author}"
        else:
            return "Book not found in the library."

if __name__ == '__main__':
    library = Library()

    book1 = Book("The Catcher in the Rye", "J.D. Salinger", "123456789", 3)
    book2 = Book("To Kill a Mockingbird", "Harper Lee", "987654321", 2)

    library.add_book(book1)
    library.add_book(book2)

    print(library.check_out_book("The Catcher in the Rye"))
    print(library.check_in_book("The Catcher in the Rye"))
  
