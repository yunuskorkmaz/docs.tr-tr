---
title: Parçalara ayrılmış XName ve XNamespace nesneleri (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: a5b21433-b49d-415c-b00e-bcbfb0d267d7
ms.openlocfilehash: 3ffeaac6d893b70c2c0d49d8d52d0372879cdf37
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43526403"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-c"></a>Parçalara ayrılmış XName ve XNamespace nesneleri (LINQ to XML) (C#)
<xref:System.Xml.Linq.XName> ve <xref:System.Xml.Linq.XNamespace> nesneler *parçalara ayrılmış*; diğer bir deyişle, bunlar, bunlar aynı tam ada içeriyorsa, aynı nesneye başvurur. Bu sorgular için performans avantajlarının verir: eşitlik için iki parçalara ayrılmış ad karşılaştırdığınızda, temel alınan Ara dil yalnızca iki başvurunun aynı nesneye işaret olup olmadığını belirlemek vardır. Arka plandaki kod, zaman alıcı olabilir karşılaştırmalar, dize yok.  
  
## <a name="atomization-semantics"></a>Parçalara ayırma semantiği  
 Parçalara ayırma anlamına iki <xref:System.Xml.Linq.XName> nesneler aynı yerel ada sahip ve aynı ad alanında oldukları, aynı örneğini paylaşırlar. Aynı şekilde, iki <xref:System.Xml.Linq.XNamespace> nesnelerin aynı ad alanı URI vardır, aynı örneğini paylaşırlar.  
  
 Parçalara ayrılmış nesneleri etkinleştirmek bir sınıf için bir sınıf için oluşturucu özel ve ortak olmalıdır. Bu durum, kurucu ortak, parçalara ayrılmış olmayan bir nesne oluşturabilirsiniz olmasıdır. <xref:System.Xml.Linq.XName> Ve <xref:System.Xml.Linq.XNamespace> sınıfları uygulayan bir dizeye dönüştürmek için bir örtülü dönüştürme işlecine bir <xref:System.Xml.Linq.XName> veya <xref:System.Xml.Linq.XNamespace>. Örneği bu nesnelerin nereden budur. Oluşturucusuna erişilemediğinden bir kurucu kullanarak örneği alınamıyor.  
  
 <xref:System.Xml.Linq.XName> ve <xref:System.Xml.Linq.XNamespace> Ayrıca iki olan başvuruları aynı örneğe karşılaştırılan nesne olup olmadığını belirlemek için eşitlik ve eşitsizlik, işleçler.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, bazı oluşturur <xref:System.Xml.Linq.XElement> nesneleri ve aynı örnek paylaşım aynı adları gösterir.  
  
```csharp  
XElement r1 = new XElement("Root", "data1");  
XElement r2 = XElement.Parse("<Root>data2</Root>");  
  
if ((object)r1.Name == (object)r2.Name)  
    Console.WriteLine("r1 and r2 have names that refer to the same instance.");  
else  
    Console.WriteLine("Different");  
  
XName n = "Root";  
  
if ((object)n == (object)r1.Name)  
    Console.WriteLine("The name of r1 and the name in 'n' refer to the same instance.");  
else  
    Console.WriteLine("Different");  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```  
r1 and r2 have names that refer to the same instance.  
The name of r1 and the name in 'n' refer to the same instance.  
```  
  
 Alan eksen yöntemlerden birini kullandığınızda, daha önce bahsedildiği gibi faydası parçalara ayrılmış nesnelerin ise bir <xref:System.Xml.Linq.XName> parametre olarak, eksen yöntemi yalnızca iki başvuru istenen öğeleri seçmek için aynı örnek adlarını belirlemek vardır.  
  
 Aşağıdaki örnek geçen bir <xref:System.Xml.Linq.XName> için <xref:System.Xml.Linq.XContainer.Descendants%2A> ardından parçalara ayırma deseni nedeniyle daha iyi performans olan yöntem çağrısı.  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("C1", 1),  
    new XElement("Z1",  
        new XElement("C1", 2),  
        new XElement("C1", 1)  
    )  
);  
  
var query = from e in root.Descendants("C1")  
            where (int)e == 1  
            select e;  
  
foreach (var z in query)  
    Console.WriteLine(z);  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<C1>1</C1>  
<C1>1</C1>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [Performans (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/performance-linq-to-xml.md)
