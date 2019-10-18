---
title: "'typename' türündeki 'IsNot' işleneni, 'typename' boş değer atanabilir bir tür olduğundan, sadece 'Nothing' ile karşılaştırılabilir."
ms.date: 07/20/2015
f1_keywords:
- bc32128
- vbc32128
helpviewer_keywords:
- BC32128
ms.assetid: 1155b23a-ad75-4bab-b9da-73f35c767a36
ms.openlocfilehash: 06dc6f1532fecefba4e507bd0cc24aadc936d137
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524377"
---
# <a name="isnot-operand-of-type-typename-can-only-be-compared-to-nothing-because-typename-is-a-nullable-type"></a><span data-ttu-id="72040-102">'typename' türündeki 'IsNot' işleneni, 'typename' boş değer atanabilir bir tür olduğundan, sadece 'Nothing' ile karşılaştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="72040-102">'IsNot' operand of type 'typename' can only be compared to 'Nothing', because 'typename' is a nullable type</span></span>

<span data-ttu-id="72040-103">Null yapılabilir olarak belirtilen bir değişken, `IsNot` işleci kullanılarak `Nothing` dışındaki bir ifadeyle karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="72040-103">A variable declared as nullable has been compared to an expression other than `Nothing` using the `IsNot` operator.</span></span>

<span data-ttu-id="72040-104">**Hata kimliği:** BC32128</span><span class="sxs-lookup"><span data-stu-id="72040-104">**Error ID:** BC32128</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="72040-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="72040-105">To correct this error</span></span>

<span data-ttu-id="72040-106">Null yapılabilir bir türü `Nothing` dışındaki bir ifadeyle karşılaştırmak için `IsNot` işlecini kullanarak, null yapılabilir türde `GetType` yöntemini çağırın ve sonucu aşağıdaki örnekte gösterildiği gibi ifadesiyle karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="72040-106">To compare a nullable type to an expression other than `Nothing` by using the `IsNot` operator, call the `GetType` method on the nullable type and compare the result to the expression, as shown in the following example.</span></span>

```vb
Dim number? As Integer = 5

If number IsNot Nothing Then
  If number.GetType() IsNot Type.GetType("System.Int32") Then

  End If
End If
```

## <a name="see-also"></a><span data-ttu-id="72040-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72040-107">See also</span></span>

- [<span data-ttu-id="72040-108">Boş Değer Atanabilen Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="72040-108">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="72040-109">IsNot İşleci</span><span class="sxs-lookup"><span data-stu-id="72040-109">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
