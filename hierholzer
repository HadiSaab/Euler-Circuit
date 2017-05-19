"""
:author:    Hadi Saab
:studentID: 2419 1493
:since:     14/05/2017
:modified:  18/05/2017
"""
import string


def DGraph(vertix_set, n):
    adj_list = []
    edge_list = []
    vertices_list = [_ for _ in range(len(vertix_set))]
    even_edged = [[0, 0] for _ in range(len(vertix_set))]

    j = 0
    for entry1 in vertix_set:
        word1 = entry1[1:]
        edges_list = []
        i = 0
        for entry2 in vertix_set:
            word2 = entry2[:n-1]
            if word1 == word2:
                edges_list.append((j, i))
                edge_list.append((j, i))
                # first index is outgoing edges
                even_edged[i][0] += 1
                # second index is incoming edges
                even_edged[j][1] += 1
            i += 1
        j += 1
        adj_list.append(edges_list)

    print(adj_list)
    print(edge_list)
    print(vertices_list)
    print(even_edged)

    # If all nodes have an even degree of incoming and outgoing then continue
    feasible = True
    for i in even_edged:
        if i[0] % 2 != 0 and i[1] % 2 != 0:
            feasible = False
            break

    if feasible:
        hierholzer(vertices_list, edges_list)


def outgoing_edges(vertex, edges):
    # iterate through edge list to check outgoing edges from vertex
    return [edge for edge in edges if edge[0] == vertex]


def incoming_edges(vertex, edges):
    # iterate through edge list to check incoming edges to vertex
    return [edge for edge in edges if edge[1] == vertex]


def cycle(vertex, edges):
    path = [vertex]
    next_path = outgoing_edges(vertex, edges)
    while next_path:
        v_edge = next_path[0]
        edges.remove(v_edge)
        vertex = v_edge[1]
        next_path = outgoing_edges(vertex, edges)

    return path, edges


def hierholzer(vertices, edges):
    source = vertices[0]
    circuit, edges = cycle(source, edges)
    


def get_path(finish, predecessor):
    """
    Finds the shortest path from a source node to a finishing node by backtracking from its predecessor.
    :param finish: Finishing node, F, position
    :param predecessor: array of previous pointing nodes.
    :return: a Path array of visited nodes/vertices.
    """
    vertix = finish
    path = [vertix]
    while predecessor[vertix] != 0:
        path.append(predecessor[vertix])
        vertix = predecessor[vertix]
    path = list(reversed(path))

    return path

# Validates input to certain range
def input_range(prompt, min_val, max_val):
    valid = False
    while not valid:
        valid = True
        value_input = int(input(prompt))
        if value_input < min_val:
            print("Must be greater than or equal to " + str(min_val))
            valid = False
        elif value_input > max_val:
            print("Must be less than " + str(max_val))
            valid = False

    return value_input


# Calls on recursive variations of alphabet of length m.
def permutation(alphabet, n):
    vertices = []
    recur_perm_of_k(alphabet, "", len(alphabet), n, vertices)
    return vertices


# Recursively generates all variations of length, n, of alphabetical
# characters of length m.
def recur_perm_of_k(alphabet, prefix, length, n, vertices):
    # Base Case
    if n == 0:
        vertices.append(prefix)
        return prefix

    for i in range(length):
        new_prefix = prefix + alphabet[i]

        recur_perm_of_k(alphabet, new_prefix, length, n - 1, vertices)

    return vertices


# Creates alphabet of size m.
def create_alphabet(m):
    complete_alphabet = string.ascii_uppercase
    alphabet = complete_alphabet[:m]
    return alphabet


if __name__ == "__main__":
    m = input_range("Enter the number of alphabetical characters, m: ", 2, 5)
    n = input_range("Enter the size of the string, n: ", 2, 3)

    alphabet = create_alphabet(m)
    vertice_list = permutation(alphabet, n)
    print(vertice_list)

    DGraph(vertice_list, n)

    # graph = DGraph(m, n)
    # circuit = e_circuit(graph, m, n, graph)
    # if circuit is not None:
        # print("E circuit found!")
        # print("".join([convert_base(x, m) for x in circuit]))
    # else:
        # print("E circuit not found!")
