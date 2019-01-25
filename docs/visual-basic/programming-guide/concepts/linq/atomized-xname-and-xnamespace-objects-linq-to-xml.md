---
title: Parçalara ayrılmış XName ve XNamespace nesneleri (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 21ee7585-7df9-40b4-8c76-a12bb5f29bb3
ms.openlocfilehash: adf766dcb69477fbad8581b075a7c0ee8a82f728
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54623683"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-visual-basic"></a>Parçalara ayrılmış XName ve XNamespace nesneleri (LINQ to XML) (Visual Basic)
<xref:System.Xml.Linq.XName> ve <xref:System.Xml.Linq.XNamespace> nesneler *parçalara ayrılmış*; diğer bir deyişle, bunlar, bunlar aynı tam ada içeriyorsa, aynı nesneye başvurur. Bu, sorgular için performans avantajlarının verir: Eşitlik için iki parçalara ayrılmış ad karşılaştırdığınızda, temel alınan Ara dil, yalnızca iki başvurunun aynı nesneye işaret olup olmadığını belirlemek vardır. Arka plandaki kod, zaman alıcı olabilir karşılaştırmalar, dize yok.  
  
## <a name="atomization-semantics"></a>Parçalara ayırma semantiği  
 Parçalara ayırma anlamına iki <xref:System.Xml.Linq.XName> nesneler aynı yerel ada sahip ve aynı ad alanında oldukları, aynı örneğini paylaşırlar. Aynı şekilde, iki <xref:System.Xml.Linq.XNamespace> nesnelerin aynı ad alanı URI vardır, aynı örneğini paylaşırlar.  
  
 Parçalara ayrılmış nesneleri etkinleştirmek bir sınıf için bir sınıf için oluşturucu özel ve ortak olmalıdır. Bu durum, kurucu ortak, parçalara ayrılmış olmayan bir nesne oluşturabilirsiniz olmasıdır. <xref:System.Xml.Linq.XName> Ve <xref:System.Xml.Linq.XNamespace> sınıfları uygulayan bir dizeye dönüştürmek için bir örtülü dönüştürme işlecine bir <xref:System.Xml.Linq.XName> veya <xref:System.Xml.Linq.XNamespace>. Örneği bu nesnelerin nereden budur. Oluşturucusuna erişilemediğinden bir kurucu kullanarak örneği alınamıyor.  
  
 <xref:System.Xml.Linq.XName> ve <xref:System.Xml.Linq.XNamespace> Ayrıca iki olan başvuruları aynı örneğe karşılaştırılan nesne olup olmadığını belirlemek için eşitlik ve eşitsizlik, işleçler.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, bazı oluşturur <xref:System.Xml.Linq.XElement> nesneleri ve aynı örnek paylaşım aynı adları gösterir.  
  
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
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```  
r1 and r2 have names that refer to the same instance.  
The name of r1 and the name in 'n' refer to the same instance.  
```  
  
 Alan eksen yöntemlerden birini kullandığınızda, daha önce bahsedildiği gibi faydası parçalara ayrılmış nesnelerin ise bir <xref:System.Xml.Linq.XName> parametre olarak, eksen yöntemi yalnızca iki başvuru istenen öğeleri seçmek için aynı örnek adlarını belirlemek vardır.  
  
 Aşağıdaki örnek geçen bir <xref:System.Xml.Linq.XName> için <xref:System.Xml.Linq.XContainer.Descendants%2A> ardından parçalara ayırma deseni nedeniyle daha iyi performans olan yöntem çağrısı.  
  
```vb  
Dim root As New XElement("Root", New XElement("C1", 1), New XElement("Z1", New XElement("C1", 2), New XElement("C1", 1)))  
  
Dim query = From e In root.Descendants("C1") Where CInt(e) = 1e  
  
For Each z As var In query  
    Console.WriteLine(z)  
Next  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<C1>1</C1>  
<C1>1</C1>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Performans (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
