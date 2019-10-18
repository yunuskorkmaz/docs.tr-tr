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
# <a name="isnot-operand-of-type-typename-can-only-be-compared-to-nothing-because-typename-is-a-nullable-type"></a>'typename' türündeki 'IsNot' işleneni, 'typename' boş değer atanabilir bir tür olduğundan, sadece 'Nothing' ile karşılaştırılabilir.

Null yapılabilir olarak belirtilen bir değişken, `IsNot` işleci kullanılarak `Nothing` dışındaki bir ifadeyle karşılaştırılır.

**Hata kimliği:** BC32128

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

Null yapılabilir bir türü `Nothing` dışındaki bir ifadeyle karşılaştırmak için `IsNot` işlecini kullanarak, null yapılabilir türde `GetType` yöntemini çağırın ve sonucu aşağıdaki örnekte gösterildiği gibi ifadesiyle karşılaştırın.

```vb
Dim number? As Integer = 5

If number IsNot Nothing Then
  If number.GetType() IsNot Type.GetType("System.Int32") Then

  End If
End If
```

## <a name="see-also"></a>Ayrıca bkz.

- [Boş Değer Atanabilen Değer Türleri](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [IsNot İşleci](../../../visual-basic/language-reference/operators/isnot-operator.md)
