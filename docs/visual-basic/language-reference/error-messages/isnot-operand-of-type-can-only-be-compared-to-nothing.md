---
title: "'typename' türündeki 'IsNot' işleneni, 'typename' boş değer atanabilir bir tür olduğundan, sadece 'Nothing' ile karşılaştırılabilir."
ms.date: 07/20/2015
f1_keywords:
- bc32128
- vbc32128
helpviewer_keywords:
- BC32128
ms.assetid: 1155b23a-ad75-4bab-b9da-73f35c767a36
ms.openlocfilehash: 1660971e2a1a11d7a2d14f222cd149edf4aa4c7b
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249519"
---
# <a name="isnot-operand-of-type-typename-can-only-be-compared-to-nothing-because-typename-is-a-nullable-type"></a>'typename' türündeki 'IsNot' işleneni, 'typename' boş değer atanabilir bir tür olduğundan, sadece 'Nothing' ile karşılaştırılabilir.

Nullable değer türü olarak bildirilen bir değişken `Nothing` `IsNot` işleci kullanarak dışında bir ifade ile karşılaştırılmıştır.

**Hata Kimliği:** BC32128

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

Nullable türü `Nothing` `IsNot` işleci kullanmak dışında bir ifadeyle karşılaştırmak için, `GetType` yöntemin nullable türündeki çağrısını arayın ve sonucu aşağıdaki örnekte gösterildiği gibi ifadeyle karşılaştırın.

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
