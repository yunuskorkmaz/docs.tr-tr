---
title: "'type1' türünün değeri 'type2' olarak dönüştürülemez"
ms.date: 07/20/2015
f1_keywords:
- vbc31194
- bc31194
helpviewer_keywords:
- BC31194
ms.assetid: 03d50c31-addd-4c90-9c53-725b84f9782e
ms.openlocfilehash: c8480c6fab2bff931950ebc21d0a8affe3c41c66
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58827152"
---
# <a name="value-of-type-type1-cannot-be-converted-to-type2"></a>'type1' türünün değeri 'type2' olarak dönüştürülemez
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
