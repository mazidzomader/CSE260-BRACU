#
def fast_mod_drift(base, exp):
    if exp == 0:
        return 1
    half = fast_mod_drift(base, exp // 2)
    
    if exp % 2 == 1:
        return (base * half * half) % 107
    return (half * half) % 107
#
def Fast_MOD_Drift_Revisited,(base, exp, mod):
    result = 1
    while exp > 0:
        if exp % 2 == 1:
            result = (result * base) % mod
        base = (base * base) % mod
        exp //= 2
    return result
def sum_mod(base, exp, mod):
    if base == 1:
        return exp % mod 
    
    x = mod_exponentiate(base, exp, mod * (base - 1))
    numerator = (base * (x - 1)) % (mod * (base - 1))
    denominator = base - 1  
    
    return (numerator // denominator) % mod  
# 
max_val = float('-inf')
max_before = temp[0]
 
for i in range(1, n):
    max_val = max(max_val, max_before + temp[i] ** 2)
    max_before = max(max_before, temp[i])
 
print(max_val)
#
def postorder_traversal(inord, preord):
    if inord == [] or preord == []:
        return []
    root = preord[0]
    root_idx = inord.index(root)
    left_inord = inord[:root_idx]
    right_inord = inord[root_idx+1:]
    left_preord = preord[1:1+len(left_inord)]
    right_preord = preord[1+len(left_inord):]
    left = postorder_traversal(left_inord, left_preord)
    right = postorder_traversal(right_inord, right_preord)
 
    arr = []
    for element in left:
        arr.append(element)
    for element in right:
        arr.append(element)
    arr.append(root)
    return arr
#
def Ordering_Binary_Tree(arr, left, right, return_list):
    if left > right:
        return
    mid = (left + right) // 2
    return_list.append(arr[mid])
    Ordering_Binary_Tree(arr, left, mid-1, return_list)
    Ordering_Binary_Tree(arr, mid + 1, right, return_list)
    return return_list
#
def merge(a, b):
    x, y= len(a), len(b)
    arr = []
    inv, i, j = 0, 0, 0
 
    while i < x and j < y:
        if a[i] < b[j]:
            arr.append(a[i])
            i += 1
        else:
            arr.append(b[j])
            inv += (x - i)  
            j += 1
 
    while i < x:
        arr.append(a[i])
        i += 1
 
    while j < y:
        arr.append(b[j])
        j += 1
 
    return (inv, arr)
 
def mergeSort(arr):
    if len(arr) <= 1:
        return (0, arr)  
 
    mid = len(arr) // 2
    a1 = mergeSort(arr[:mid])
    a2 = mergeSort(arr[mid:])
    merged = merge(a1[1], a2[1])  
    return (merged[0] + a1[0] + a2[0], merged[1])