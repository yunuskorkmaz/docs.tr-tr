---
title: "&#39; IsNot &#39; işlenen türü &#39; typename &#39; yalnızca karşılaştırılabilir &#39; Hiçbir şey &#39; çünkü &#39; typename &#39; boş değer atanabilir bir tür"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32128
- vbc32128
helpviewer_keywords:
- BC32128
ms.assetid: 1155b23a-ad75-4bab-b9da-73f35c767a36
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ec0ae1561bfbee998e7c65f6023012c0f982a8a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="39isnot39-operand-of-type-39typename39-can-only-be-compared-to-39nothing39-because-39typename39-is-a-nullable-type"></a>&#39; IsNot &#39; işlenen türü &#39; typename &#39; yalnızca karşılaştırılabilir &#39; Hiçbir şey &#39; çünkü &#39; typename &#39; boş değer atanabilir bir tür
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
 [Boş değer atanabilen değer türleri](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [IsNot işleci](../../../visual-basic/language-reference/operators/isnot-operator.md)
