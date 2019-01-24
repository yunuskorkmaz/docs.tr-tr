---
title: Türü değeri &#39;type1&#39; dönüştürülemez &#39;type2&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: 657e0feb675e15b9ece00d40c3d1ebe932a29099
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568301"
---
# <a name="value-of-type-39type139-cannot-be-converted-to-39type239"></a>Türü değeri &#39;type1&#39; dönüştürülemez &#39;type2&#39;
'Type1' türünün değeri 'type2' olarak dönüştürülemez. 'Value' özelliğini ilk öğesinin dize değerini almak için kullanabileceğiniz '\<parentElement >'.  
  
 Belirli bir türe sabit değeri bir XML dolaylı olarak girişiminde bulunuldu. XML değişmez değeri belirtilen türe örtük olarak yayınlanamıyor.  
  
 **Hata Kimliği:** BC31194  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Kullanım `Value` özellik değeri olarak başvurmak için XML değişmez bir `String`. Kullanım `CType` işlev, başka bir tür dönüştürme işlevi veya <xref:System.Convert> belirtilen tür olarak değerde dönüştürme yapmak sınıfı.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Convert>
- [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [XML Değişmez Değerleri](../../../visual-basic/language-reference/xml-literals/index.md)
- [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)
