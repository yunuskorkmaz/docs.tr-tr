---
title: 'Nasıl yapılır: özniteliklerin koleksiyonunu alma (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: a07e9645-b45b-403b-b698-f652f904c7d2
ms.openlocfilehash: ff260660057c3b75f4cc92c37c67fca0a0b7f192
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347570"
---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-visual-basic"></a>Nasıl yapılır: özniteliklerin koleksiyonunu alma (LINQ to XML) (Visual Basic)
Bu konuda <xref:System.Xml.Linq.XElement.Attributes%2A> yöntemi tanıtılmaktadır. Bu yöntem bir öğenin özniteliklerini alır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir öğenin özniteliklerinin toplanması arasında nasıl yineleme yapılacağını gösterir.  
  
```vb  
Dim val = _  
    <Value ID="1243" Type="int" ConvertableTo="double">100</Value>  
Dim listOfAttributes As IEnumerable(Of XAttribute) = _  
    From att In val.Attributes() _  
    Select att  
For Each att As XAttribute In listOfAttributes  
    Console.WriteLine(att)  
Next  
```  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```console  
ID="1243"  
Type="int"  
ConvertableTo="double"  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML eksenleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
