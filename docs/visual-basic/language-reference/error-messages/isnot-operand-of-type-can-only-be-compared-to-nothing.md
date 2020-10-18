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
# <a name="bc32128-isnot-operand-of-type-typename-can-only-be-compared-to-nothing-because-typename-is-a-nullable-type"></a>BC32128: ' TypeName ' null yapılabilir bir tür olduğundan, ' TypeName ' türündeki ' IsNot ' işleneni yalnızca ' Nothing ' ile karşılaştırılabilir

Null yapılabilir değer türü olarak belirtilen bir değişken işleci kullanmaktan başka bir ifadeyle karşılaştırıldı `Nothing` `IsNot` .

**Hata kimliği:** BC32128

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

Null yapılabilir bir türü işlecini kullanarak dışındaki bir ifadeyle karşılaştırmak için `Nothing` `IsNot` , `GetType` Aşağıdaki örnekte gösterildiği gibi, null yapılabilir türde yöntemi çağırın ve sonucu ifadesiyle karşılaştırın.

```vb
Dim number? As Integer = 5

If number IsNot Nothing Then
  If number.GetType() IsNot Type.GetType("System.Int32") Then

  End If
End If
```

## <a name="see-also"></a>Ayrıca bkz.

- [Null yapılabilir değer türleri](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [IsNot İşleci](../operators/isnot-operator.md)
