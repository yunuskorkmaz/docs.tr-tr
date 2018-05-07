---
title: Atomized XName ve XNamespace nesneleri (LINQ-XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 21ee7585-7df9-40b4-8c76-a12bb5f29bb3
ms.openlocfilehash: e311de901a9a54bd4fc6ee56d425cc16b4978e8f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-visual-basic"></a>Atomized XName ve XNamespace nesneleri (LINQ-XML) (Visual Basic)
<xref:System.Xml.Linq.XName> ve <xref:System.Xml.Linq.XNamespace> nesneler *atomized*; diğer bir deyişle, bunlar bunlar aynı tam adı içeriyorsa, aynı nesneye başvuruyor. Bu sorguları için performans avantajı verir: eşitlik için iki atomized adları karşılaştırdığınızda, temel alınan Ara dile yalnızca iki başvurunun aynı nesneye işaret olup olmadığını belirlemek vardır. Arka plandaki kod zaman alıcı olabilir karşılaştırmaları dize gerekmez.  
  
## <a name="atomization-semantics"></a>Atomization semantiği  
 Atomization anlamına gelir, iki <xref:System.Xml.Linq.XName> nesneler aynı yerel ada sahip ve aynı ad alanında oldukları, aynı örneğini paylaşırlar. Aynı şekilde, iki <xref:System.Xml.Linq.XNamespace> nesneler sahip aynı ad alanı URI, aynı örneğini paylaşırlar.  
  
 Bir sınıf atomized nesneleri etkinleştirmek sınıf oluşturucusu özel ve ortak değil olmalıdır. Oluşturucu ortak olsaydı, atomized olmayan bir nesne oluşturabilirsiniz olmasıdır. <xref:System.Xml.Linq.XName> Ve <xref:System.Xml.Linq.XNamespace> sınıfları uygulayan bir dizeye dönüştürmek için bir örtük dönüşüm işleci bir <xref:System.Xml.Linq.XName> veya <xref:System.Xml.Linq.XNamespace>. Bu nesneler örneği nereden budur. Oluşturucusu erişilemediğinden bir kurucu kullanarak bir örneği elde edilemiyor.  
  
 <xref:System.Xml.Linq.XName> ve <xref:System.Xml.Linq.XNamespace> da iki karşılaştırılan başvuruları aynı örneğini olan nesneleri olup olmadığını belirlemek için eşitlik ve eşitsizlik, işleçler.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod bazı oluşturur <xref:System.Xml.Linq.XElement> nesneleri ve aynı örnek paylaşım aynı adları gösterir.  
  
```vb  
Dim r1 As New XElement("Root", "data1")  
Dim r2 As XElement = XElement.Parse("<Root>data2</Root>")  
  
If DirectCast(r1.Name, Object) = DirectCast(r2.Name, Object) Then  
    Console.WriteLine("r1 and r2 have names that refer to the same instance.")  
Else  
    Console.WriteLine("Different")  
End If  
  
Dim n As XName = "Root"  
  
If DirectCast(n, Object) = DirectCast(r1.Name, Object) Then  
    Console.WriteLine("The name of r1 and the name in 'n' refer to the same instance.")  
Else  
    Console.WriteLine("Different")  
End If  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```  
r1 and r2 have names that refer to the same instance.  
The name of r1 and the name in 'n' refer to the same instance.  
```  
  
 Ele eksen yöntemlerden birini kullandığınızda, daha önce belirtildiği gibi faydası atomized nesnelerin ise bir <xref:System.Xml.Linq.XName> bir parametre olarak eksen yöntemi yalnızca iki başvuru istenen öğelerini seçmek için aynı örnek adlarını belirlemek vardır.  
  
 Aşağıdaki örnek geçirmeden bir <xref:System.Xml.Linq.XName> için <xref:System.Xml.Linq.XContainer.Descendants%2A> sonra daha iyi performans nedeniyle atomization düzeni sahip yöntem çağrısı.  
  
```vb  
Dim root As New XElement("Root", New XElement("C1", 1), New XElement("Z1", New XElement("C1", 2), New XElement("C1", 1)))  
  
Dim query = From e In root.Descendants("C1") Where CInt(e) = 1e  
  
For Each z As var In query  
    Console.WriteLine(z)  
Next  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<C1>1</C1>  
<C1>1</C1>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans (LINQ-XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
