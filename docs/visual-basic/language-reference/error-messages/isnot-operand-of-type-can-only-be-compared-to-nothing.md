---
title: "'typename' türündeki 'IsNot' işleneni, 'typename' boş değer atanabilir bir tür olduğundan, sadece 'Nothing' ile karşılaştırılabilir."
ms.date: 07/20/2015
f1_keywords:
- bc32128
- vbc32128
helpviewer_keywords:
- BC32128
ms.assetid: 1155b23a-ad75-4bab-b9da-73f35c767a36
ms.openlocfilehash: caa009606825225dd4063780f9a22fb82f21cf4e
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271297"
---
# <a name="isnot-operand-of-type-typename-can-only-be-compared-to-nothing-because-typename-is-a-nullable-type"></a>'typename' türündeki 'IsNot' işleneni, 'typename' boş değer atanabilir bir tür olduğundan, sadece 'Nothing' ile karşılaştırılabilir.
Boş değer atanabilir olarak bildirilen bir değişken için bir ifade dışında karşılaştırıldığında `Nothing` kullanarak `IsNot` işleci.  
  
 **Hata Kimliği:** BC32128  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Boş değer atanabilir bir tür için bir ifade dışında Karşılaştırılacak `Nothing` kullanarak `IsNot` işleç, çağrı `GetType` yöntemi boş değer atanabilir tür ve karşılaştırma sonucu aşağıdaki örnekte gösterildiği gibi bir ifade.  
  
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
