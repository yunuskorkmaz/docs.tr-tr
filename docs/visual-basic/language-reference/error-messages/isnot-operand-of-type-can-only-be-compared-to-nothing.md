---
title: "'typename' türündeki 'IsNot' işleneni, 'typename' boş değer atanabilir bir tür olduğundan, sadece 'Nothing' ile karşılaştırılabilir."
ms.date: 07/20/2015
f1_keywords:
- bc32128
- vbc32128
helpviewer_keywords:
- BC32128
ms.assetid: 1155b23a-ad75-4bab-b9da-73f35c767a36
ms.openlocfilehash: be2a3239b2ca520c4051a1504f91a766b4401a05
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834029"
---
# <a name="isnot-operand-of-type-typename-can-only-be-compared-to-nothing-because-typename-is-a-nullable-type"></a><span data-ttu-id="c66af-102">'typename' türündeki 'IsNot' işleneni, 'typename' boş değer atanabilir bir tür olduğundan, sadece 'Nothing' ile karşılaştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="c66af-102">'IsNot' operand of type 'typename' can only be compared to 'Nothing', because 'typename' is a nullable type</span></span>
<span data-ttu-id="c66af-103">Boş değer atanabilir olarak bildirilen bir değişken için bir ifade dışında karşılaştırıldığında `Nothing` kullanarak `IsNot` işleci.</span><span class="sxs-lookup"><span data-stu-id="c66af-103">A variable declared as nullable has been compared to an expression other than `Nothing` using the `IsNot` operator.</span></span>  
  
 <span data-ttu-id="c66af-104">**Hata Kimliği:** BC32128</span><span class="sxs-lookup"><span data-stu-id="c66af-104">**Error ID:** BC32128</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c66af-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="c66af-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="c66af-106">Boş değer atanabilir bir tür için bir ifade dışında Karşılaştırılacak `Nothing` kullanarak `IsNot` işleç, çağrı `GetType` yöntemi boş değer atanabilir tür ve karşılaştırma sonucu aşağıdaki örnekte gösterildiği gibi bir ifade.</span><span class="sxs-lookup"><span data-stu-id="c66af-106">To compare a nullable type to an expression other than `Nothing` by using the `IsNot` operator, call the `GetType` method on the nullable type and compare the result to the expression, as shown in the following example.</span></span>  
  
```vb  
Dim number? As Integer = 5  
  
If number IsNot Nothing Then  
  If number.GetType() IsNot Type.GetType("System.Int32") Then   
  
  End If  
End If  
```  
  
## <a name="see-also"></a><span data-ttu-id="c66af-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c66af-107">See also</span></span>

- [<span data-ttu-id="c66af-108">Boş Değer Atanabilen Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="c66af-108">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="c66af-109">IsNot İşleci</span><span class="sxs-lookup"><span data-stu-id="c66af-109">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
