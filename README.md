def minimax(node, depth, is_maximizing_player, leaves, index):
    if depth == 0:  
        return leaves[index]
    
    if is_maximizing_player:
        best_value = -float('inf')
        for i in range(2):  
            child_index = 2 * index + i
            if child_index < len(leaves):
                value = minimax(node, depth - 1, False, leaves, child_index)
                best_value = max(best_value, value)
        return best_value
    else:
        best_value = float('inf')
        for i in range(2):  
            child_index = 2 * index + i
            if child_index < len(leaves):
                value = minimax(node, depth - 1, True, leaves, child_index)
                best_value = min(best_value, value)
        return best_value
leaves = [-1, 3, -5, 8, 1, -4, 4, -3, 5, -1, 4, 3, -2, -5, 9, 8, 6, 1, -4, 2, 4, 7, 3, -3]
root_value = minimax("Root", depth=3, is_maximizing_player=True, leaves=leaves, index=0)
print("Optimal value for the root (MAX):", root_value)
