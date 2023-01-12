# Tarefa 1
```
SELECT 
  departamento.nome as departamento, pessoa.nome as pessoa, pessoa.salario as salario
FROM 
  pessoa
  JOIN departamento ON pessoa.DeptId = departamento.Id
  JOIN (
    SELECT deptId, MAX(salario) as salario
    FROM pessoa
    GROUP BY DeptId
  ) as maxSalario ON pessoa.DeptId = maxSalario.deptId AND pessoa.Salario = maxSalario.salario
```

# Tarefa 2
```
class Node:
    def __init__(self, val):
        self.val = val
        self.left = None
        self.right = None

def constructTree(nums):
    if not nums:
        return None
    maxVal = max(nums)
    maxIdx = nums.index(maxVal)

    left = nums[:maxIdx]
    left.sort(reverse=True)
    right = nums[maxIdx+1:]
    right.sort(reverse=True)

    root = Node(maxVal)
    root.left = constructTree(left)
    root.right = constructTree(right)
    return root

def getValues(node, values):
    if node:
        values.append(node.val)
        getValues(node.left, values)
        getValues(node.right, values)
```
