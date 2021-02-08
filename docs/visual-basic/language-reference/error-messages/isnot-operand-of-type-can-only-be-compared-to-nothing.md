---
description: "Hakkında daha fazla bilgi edinin: BC32128: ' TypeName ' türündeki ' IsNot ' işleneni, null yapılabilir bir tür olduğundan yalnızca ' Nothing ' ile karşılaştırılabilir"
title: "'typename' türündeki 'IsNot' işleneni, 'typename' boş değer atanabilir bir tür olduğundan, sadece 'Nothing' ile karşılaştırılabilir."
ms.date: 07/20/2015
f1_keywords:
- bc32128
- vbc32128
helpviewer_keywords:
- BC32128
ms.assetid: 1155b23a-ad75-4bab-b9da-73f35c767a36
ms.openlocfilehash: 732c8bee2ae352824c7d50bba8b2b35598d6f53b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795995"
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
