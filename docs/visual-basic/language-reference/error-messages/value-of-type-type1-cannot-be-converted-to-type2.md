---
title: Değer türü &#39;type1&#39; dönüştürülemiyor &#39;type2&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: 9e59d3bc5e2bfca3628248d08ffc475334d4da79
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602768"
---
# <a name="value-of-type-39type139-cannot-be-converted-to-39type239"></a>Değer türü &#39;type1&#39; dönüştürülemiyor &#39;type2&#39;
'Type1' türünün değeri 'type2' dönüştürülemiyor. 'Value' özelliği ilk öğesi dize değerini almak için kullanabileceğiniz '\<parentElement >'.  
  
 Belirli bir türünü değişmez değer XML dolaylı olarak bir girişiminde bulunuldu. XML değişmez değeri belirtilen türe örtük olarak atanamaz.  
  
 **Hata Kimliği:** BC31194  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Kullanım `Value` değer olarak başvurmak için değişmez değer XML özelliğinin bir `String`. Kullanım `CType` işlevi, başka bir tür dönüştürme işlevi veya <xref:System.Convert> sınıfı değeri belirtilen tür olarak yayınlanamıyor.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Convert>  
 [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [XML Değişmez Değerleri](../../../visual-basic/language-reference/xml-literals/index.md)  
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)
