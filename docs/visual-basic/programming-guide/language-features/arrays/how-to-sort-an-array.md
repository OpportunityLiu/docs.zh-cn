---
title: 如何：在 Visual Basic 中对数组进行排序
ms.date: 07/20/2015
f1_keywords:
- Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
ms.openlocfilehash: a067c40e1dd0e881516cbc7769cb9afb879d1b9d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646286"
---
# <a name="how-to-sort-an-array-in-visual-basic"></a>如何：在 Visual Basic 中对数组进行排序
此示例声明的数组`String`对象命名的`zooAnimals`、 填充它，并按字母顺序排序。  
  
## <a name="example"></a>示例  
  
```  
Private Sub sortAnimals()  
    Dim zooAnimals(2) As String  
    zooAnimals(0) = "lion"  
    zooAnimals(1) = "turtle"  
    zooAnimals(2) = "ostrich"  
    Array.Sort(zooAnimals)  
End Sub  
```  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要：  
  
-   访问 mscorlib.dll 和<xref:System>命名空间。  
  
## <a name="robust-programming"></a>可靠编程  
 以下情况可能会导致异常：  
  
-   数组为空 (<xref:System.ArgumentNullException>类)  
  
-   数组是多维数组 (<xref:System.RankException>类)  
  
-   数组的一个或多个元素不实现<xref:System.IComparable>接口 (<xref:System.InvalidOperationException>类)  
  
## <a name="see-also"></a>请参阅  
 <xref:System.Array.Sort%2A?displayProperty=nameWithType>  
 [数组](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [数组疑难解答](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)  
 [集合](../../concepts/collections.md)  
 [For Each...Next 语句](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
