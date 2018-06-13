---
title: 'Nasıl yapılır: alt öğeleri yöntemi (C#) kullanarak tek bir alt öğesi bulunamıyor'
ms.date: 07/20/2015
ms.assetid: 6f735be9-0293-4680-8007-ca9d96bfebed
ms.openlocfilehash: e08e07e0d32146a14b90b9d6463e6e58a233a923
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33316965"
---
# <a name="how-to-find-a-single-descendant-using-the-descendants-method-c"></a>Nasıl yapılır: alt öğeleri yöntemi (C#) kullanarak tek bir alt öğesi bulunamıyor
Kullanabileceğiniz <xref:System.Xml.Linq.XContainer.Descendants%2A> hızlı bir şekilde tek bir benzersiz olarak bulmak için kod yazma eksen yöntemi adlı öğesi. Belirli bir ada sahip belirli bir alt öğesi bulmak istediğiniz durumlarda bu kullanışlı bir tekniktir. İstenen öğesine gitmek için kod yazma, ancak daha hızlı ve kolay kullanılarak kod yazmaya görülür <xref:System.Xml.Linq.XContainer.Descendants%2A> ekseni.  
  
## <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Linq.Enumerable.First%2A> standart sorgu işleci.  
  
```csharp  
XElement root = XElement.Parse(@"<Root>  
  <Child1>  
    <GrandChild1>GC1 Value</GrandChild1>  
  </Child1>  
  <Child2>  
    <GrandChild2>GC2 Value</GrandChild2>  
  </Child2>  
  <Child3>  
    <GrandChild3>GC3 Value</GrandChild3>  
  </Child3>  
  <Child4>  
    <GrandChild4>GC4 Value</GrandChild4>  
  </Child4>  
</Root>");  
string grandChild3 = (string)  
    (from el in root.Descendants("GrandChild3")  
    select el).First();  
Console.WriteLine(grandChild3);  
```  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```  
GC3 Value  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir ad alanı XML aynı sorgu gösterir. Daha fazla bilgi için bkz: [XML ad alanları (C#) çalışma](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
```csharp  
XElement root = XElement.Parse(@"<aw:Root xmlns:aw='http://www.adventure-works.com'>  
  <aw:Child1>  
    <aw:GrandChild1>GC1 Value</aw:GrandChild1>  
  </aw:Child1>  
  <aw:Child2>  
    <aw:GrandChild2>GC2 Value</aw:GrandChild2>  
  </aw:Child2>  
  <aw:Child3>  
    <aw:GrandChild3>GC3 Value</aw:GrandChild3>  
  </aw:Child3>  
  <aw:Child4>  
    <aw:GrandChild4>GC4 Value</aw:GrandChild4>  
  </aw:Child4>  
</aw:Root>");  
XNamespace aw = "http://www.adventure-works.com";  
string grandChild3 = (string)  
    (from el in root.Descendants(aw + "GrandChild3")  
     select el).First();  
Console.WriteLine(grandChild3);  
```  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```  
GC3 Value  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Temel sorgu (LINQ-XML) (C#)](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
