---
title: "Değer türü &#39; type1 &#39; dönüştürülemiyor &#39; type2 &#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: efa6fcd4d996fb3277cc4cac2af16a86a2d65977
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="value-of-type-39type139-cannot-be-converted-to-39type239"></a>Değer türü &#39; type1 &#39; dönüştürülemiyor &#39; type2 &#39;
'Type1' türünün değeri 'type2' dönüştürülemiyor. 'Value' özelliği ilk öğesi dize değerini almak için kullanabileceğiniz '\<parentElement >'.  
  
 Belirli bir türünü değişmez değer XML dolaylı olarak bir girişiminde bulunuldu. XML değişmez değeri belirtilen türe örtük olarak atanamaz.  
  
 **Hata Kimliği:** BC31194  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Kullanım `Value` değer olarak başvurmak için değişmez değer XML özelliğinin bir `String`. Kullanım `CType` işlevi, başka bir tür dönüştürme işlevi veya <xref:System.Convert> sınıfı değeri belirtilen tür olarak yayınlanamıyor.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Convert>  
 [Tür dönüşüm işlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [XML değişmez değerleri](../../../visual-basic/language-reference/xml-literals/index.md)  
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)
