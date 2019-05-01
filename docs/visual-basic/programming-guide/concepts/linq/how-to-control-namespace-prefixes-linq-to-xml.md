---
title: 'Nasıl yapılır: Denetim Namespace önekleri (Visual Basic) (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 2fcf28a5-31b6-409d-84ea-27c22f71fc9f
ms.openlocfilehash: 7e5a05d2fa93e61338f450d0a4d890fa94c04fd2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61855406"
---
# <a name="how-to-control-namespace-prefixes-visual-basic-linq-to-xml"></a>Nasıl yapılır: Denetim Namespace önekleri (Visual Basic) (LINQ to XML)
Bu konuda, ad alanı öneklerini nasıl denetleyebileceğiniz açıklanmaktadır.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Bu örnek iki ad alanları bildirir. Belirtir `http://www.adventure-works.com` ad alanı öneki olan `aw`ve `www.fourthcoffee.com` ad alanı öneki olan `fc`.  
  
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

- [XML ad alanları (Visual Basic) ile çalışma](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
