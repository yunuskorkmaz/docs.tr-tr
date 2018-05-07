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
---
# <a name="39isnot39-operand-of-type-39typename39-can-only-be-compared-to-39nothing39-because-39typename39-is-a-nullable-type"></a>&#39;IsNot&#39; türünde işlenen &#39;typename&#39; yalnızca karşılaştırılabilir &#39;hiçbir şey&#39;, çünkü &#39;typename&#39; boş değer atanabilir bir tür
Boş değer atanabilir olarak bildirilen bir değişken için bir ifade dışında karşılaştırıldığında `Nothing` kullanarak `IsNot` işleci.  
  
 **Hata Kimliği:** BC32128  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Boş değer atanabilir bir tür bir ifade için dışında karşılaştırmak için `Nothing` kullanarak `IsNot` işleç, çağrı `GetType` yöntemi null atanabilir tür ve karşılaştırma aşağıdaki örnekte gösterildiği gibi ifade sonucu.  
  
```vb  
Dim number? As Integer = 5  
  
If number IsNot Nothing Then  
  If number.GetType() IsNot Type.GetType("System.Int32") Then   
  
  End If  
End If  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Boş Değer Atanabilen Değer Türleri](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [IsNot İşleci](../../../visual-basic/language-reference/operators/isnot-operator.md)
