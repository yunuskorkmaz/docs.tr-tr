---
title: 'Nasıl yapılır: ad alanı öneklerini denetleme (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 2fcf28a5-31b6-409d-84ea-27c22f71fc9f
ms.openlocfilehash: 5ba415452a8671466c3a4c71a88731e5bd3cda60
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348384"
---
# <a name="how-to-control-namespace-prefixes-visual-basic-linq-to-xml"></a>Nasıl yapılır: ad alanı öneklerini denetleme (Visual Basic) (LINQ to XML)
Bu konuda, ad alanı öneklerini nasıl denetleyebileceğinizi açıklar.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Bu örnek iki ad alanı bildirir. `http://www.adventure-works.com` ad alanının ön ek `aw`sahip olduğunu ve `www.fourthcoffee.com` ad alanının `fc`öneki olduğunu belirtir.  
  
### <a name="code"></a>Kod  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
Imports <xmlns:fc="www.fourthcoffee.com">  
  
Module Module1  
  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <fc:Child>  
                    <aw:DifferentChild>other content</aw:DifferentChild>  
                </fc:Child>  
                <aw:Child2>c2 content</aw:Child2>  
                <fc:Child3>c3 content</fc:Child3>  
            </aw:Root>  
        Console.WriteLine(root)  
    End Sub  
  
End Module  
```  
  
### <a name="comments"></a>Açıklamalar  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ad alanlarına genel bakış (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md)
