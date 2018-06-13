---
title: '&#39;IsNot&#39; türünde işlenen &#39;typename&#39; yalnızca karşılaştırılabilir &#39;hiçbir şey&#39;, çünkü &#39;typename&#39; boş değer atanabilir bir tür'
ms.date: 07/20/2015
f1_keywords:
- bc32128
- vbc32128
helpviewer_keywords:
- BC32128
ms.assetid: 1155b23a-ad75-4bab-b9da-73f35c767a36
ms.openlocfilehash: 44cc17c73b476e5e322b9b58b021bc7bcd63167f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587602"
---
# <a name="39isnot39-operand-of-type-39typename39-can-only-be-compared-to-39nothing39-because-39typename39-is-a-nullable-type"></a><span data-ttu-id="6719d-102">&#39;IsNot&#39; türünde işlenen &#39;typename&#39; yalnızca karşılaştırılabilir &#39;hiçbir şey&#39;, çünkü &#39;typename&#39; boş değer atanabilir bir tür</span><span class="sxs-lookup"><span data-stu-id="6719d-102">&#39;IsNot&#39; operand of type &#39;typename&#39; can only be compared to &#39;Nothing&#39;, because &#39;typename&#39; is a nullable type</span></span>
<span data-ttu-id="6719d-103">Boş değer atanabilir olarak bildirilen bir değişken için bir ifade dışında karşılaştırıldığında `Nothing` kullanarak `IsNot` işleci.</span><span class="sxs-lookup"><span data-stu-id="6719d-103">A variable declared as nullable has been compared to an expression other than `Nothing` using the `IsNot` operator.</span></span>  
  
 <span data-ttu-id="6719d-104">**Hata Kimliği:** BC32128</span><span class="sxs-lookup"><span data-stu-id="6719d-104">**Error ID:** BC32128</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6719d-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="6719d-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="6719d-106">Boş değer atanabilir bir tür bir ifade için dışında karşılaştırmak için `Nothing` kullanarak `IsNot` işleç, çağrı `GetType` yöntemi null atanabilir tür ve karşılaştırma aşağıdaki örnekte gösterildiği gibi ifade sonucu.</span><span class="sxs-lookup"><span data-stu-id="6719d-106">To compare a nullable type to an expression other than `Nothing` by using the `IsNot` operator, call the `GetType` method on the nullable type and compare the result to the expression, as shown in the following example.</span></span>  
  
```vb  
Dim number? As Integer = 5  
  
If number IsNot Nothing Then  
  If number.GetType() IsNot Type.GetType("System.Int32") Then   
  
  End If  
End If  
```  
  
## <a name="see-also"></a><span data-ttu-id="6719d-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6719d-107">See Also</span></span>  
 [<span data-ttu-id="6719d-108">Boş Değer Atanabilen Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="6719d-108">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [<span data-ttu-id="6719d-109">IsNot İşleci</span><span class="sxs-lookup"><span data-stu-id="6719d-109">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
