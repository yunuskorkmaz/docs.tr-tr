---
description: 'Daha fazla bilgi edinin: nasıl yapılır: XML alt öğelerine erişme (Visual Basic)'
title: 'Nasıl yapılır: XML Bağımlı Öğelerine Erişme'
ms.date: 07/20/2015
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
ms.openlocfilehash: d8f3176a91c2f637f49d2754513f3253399ee8ed
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100433180"
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a>Nasıl yapılır: XML Bağımlı Öğelerine Erişme (Visual Basic)

Bu örnek, bir alt eksen özelliğinin, belirtilen bir ada sahip olan ve bir XML öğesi altında bulunan tüm XML öğelerine erişmek için nasıl kullanılacağını gösterir. Özellikle, alt `Value` eksen özelliğinin döndürdüğü koleksiyondaki ilk öğenin değerini almak için özelliğini kullanır `name` . Alt `name` eksen özelliği, nesnesinde bulunan adlı tüm öğeleri alır `name` `contacts` . Bu örnek, `phone` nesnesinde bulunan adlı tüm alt öğelere erişmek için alt eksen özelliğini de kullanır `phone` `contacts` .  
  
## <a name="example"></a>Örnek  

 [!code-vb[VbXMLSamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#31)]  
  
## <a name="compile-the-code"></a>Kodu derle  

 Bu örnek şunları gerektirir:  
  
- <xref:System.Xml.Linq>Ad alanına başvuru.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>
- [XML Descendant Axis Özelliği](../../../language-reference/xml-axis/xml-descendant-axis-property.md)
- [XML Value Özelliği](../../../language-reference/xml-axis/xml-value-property.md)
- [Visual Basic'de XML'e Erişme](accessing-xml.md)
- [XML](index.md)
