# test
""" Algorithmic Thinking Part 2 Project 4- Dynamic Programming"""

def build_scoring_matrix(alphabet, diag_score, off_diag_score, dash_score):
    """Takes a set of characters, "alphabet", and 3 scores
    and returns a dictionary of dictionaries whose entries
    are indexed by pairs of characters in the alphabet plus
    - """
    score_matrix = {}
    new_alphabet = alphabet.copy()
    new_alphabet.add("-")
    #print alphabet
    for letter in new_alphabet: 
        score_matrix[letter] = {}
        for letter2 in new_alphabet: 
            if letter2 == "-" or letter == "-":
                score_matrix[letter][letter2] = dash_score
            elif letter2 == letter: 
                score_matrix[letter][letter2]= diag_score
            else: 
                score_matrix[letter][letter2]=off_diag_score
    return score_matrix
    
#print build_scoring_matrix(set(['A','C','T']),10,4,-2)
#print build_scoring_matrix(set(['A', 'C', 'T', 'G']), 6, 2, -4) 
#expect: {'A': {'A': 6, 'C': 2, '-': -4, 'T': 2, 'G': 2}, 'C': {'A': 2, 'C': 6, '-': -4, 'T': 2, 'G': 2}, '-': {'A': -4, 'C': -4, '-': -4, 'T': -4, 'G': -4}, 'T': {'A': 2, 'C': 2, '-': -4, 'T': 6, 'G': 2}, 'G': {'A': 2, 'C': 2, '-': -4, 'T': 2, 'G': 6}}

#print build_scoring_matrix(set(['A', 'C', '-', 'T', 'G']), 6, 2, -4) 
