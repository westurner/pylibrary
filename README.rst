pylibrary
==========

Goal: Mashup book wish lists with local libraries

Challenge: Subject Grouping
----------------------------
Similar to curriculum challenge.

Given topic groups A, B, C and books A1, A2, A[n], B[n], C[n],
is it more effective to interleave or to cluster?

Positive Externality: Web Tours
--------------------------------
Wikipedia Flows etc.

Process
--------
Retrieve / Join Wish List
def join_wishlist(id):
    for item in get_wishlist(id):
        if hasattr(item, 'isbn'):
            book = worldcat.get(isbn=item.isbn)
            libraries_tbl.extend(libraries)
            books_tbl.extend(books)
            for library in libraries:
                book.availability.append(
                    (library, library.get_availability(book)))

flows = create_clusters/groups/flows(books)

def score(flow):
    """
    f( availability, distance, page count, due_date )
    """

scores_tbl.extend( imap(score, flows) )

display(top_n_scores(scores_tbl))
