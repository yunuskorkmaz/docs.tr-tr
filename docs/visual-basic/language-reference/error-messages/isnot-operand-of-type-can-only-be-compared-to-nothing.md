---
title: "'typename' türündeki 'IsNot' işleneni, 'typename' boş değer atanabilir bir tür olduğundan, sadece 'Nothing' ile karşılaştırılabilir."
ms.date: 07/20/2015
f1_keywords:
- bc32128
- vbc32128
helpviewer_keywords:
- BC32128
ms.assetid: 1155b23a-ad75-4bab-b9da-73f35c767a36
ms.openlocfilehash: 084978c1e047eebd60149af63c0ec9a1135225be
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163343"
---
# <a name="bc32128-isnot-operand-of-type-typename-can-only-be-compared-to-nothing-because-typename-is-a-nullable-type"></a><span data-ttu-id="43a70-102">BC32128: ' TypeName ' null yapılabilir bir tür olduğundan, ' TypeName ' türündeki ' IsNot ' işleneni yalnızca ' Nothing ' ile karşılaştırılabilir</span><span class="sxs-lookup"><span data-stu-id="43a70-102">BC32128: 'IsNot' operand of type 'typename' can only be compared to 'Nothing', because 'typename' is a nullable type</span></span>

<span data-ttu-id="43a70-103">Null yapılabilir değer türü olarak belirtilen bir değişken işleci kullanmaktan başka bir ifadeyle karşılaştırıldı `Nothing` `IsNot` .</span><span class="sxs-lookup"><span data-stu-id="43a70-103">A variable declared as a nullable value type has been compared to an expression other than `Nothing` using the `IsNot` operator.</span></span>

<span data-ttu-id="43a70-104">**Hata kimliği:** BC32128</span><span class="sxs-lookup"><span data-stu-id="43a70-104">**Error ID:** BC32128</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="43a70-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="43a70-105">To correct this error</span></span>

<span data-ttu-id="43a70-106">Null yapılabilir bir türü işlecini kullanarak dışındaki bir ifadeyle karşılaştırmak için `Nothing` `IsNot` , `GetType` Aşağıdaki örnekte gösterildiği gibi, null yapılabilir türde yöntemi çağırın ve sonucu ifadesiyle karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="43a70-106">To compare a nullable type to an expression other than `Nothing` by using the `IsNot` operator, call the `GetType` method on the nullable type and compare the result to the expression, as shown in the following example.</span></span>

```vb
Dim number? As Integer = 5

If number IsNot Nothing Then
  If number.GetType() IsNot Type.GetType("System.Int32") Then

  End If
End If
```

## <a name="see-also"></a><span data-ttu-id="43a70-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43a70-107">See also</span></span>

- [<span data-ttu-id="43a70-108">Null yapılabilir değer türleri</span><span class="sxs-lookup"><span data-stu-id="43a70-108">Nullable Value Types</span></span>](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="43a70-109">IsNot İşleci</span><span class="sxs-lookup"><span data-stu-id="43a70-109">IsNot Operator</span></span>](../operators/isnot-operator.md)
