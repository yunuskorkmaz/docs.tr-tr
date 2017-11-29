---
title: Atomized XName ve XNamespace nesneleri (LINQ-XML) (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: a5b21433-b49d-415c-b00e-bcbfb0d267d7
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cc3fdb907c46cf77ff6560b68ebc449380947e1c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-c"></a>Atomized XName ve XNamespace nesneleri (LINQ-XML) (C#)
<xref:System.Xml.Linq.XName>ve <xref:System.Xml.Linq.XNamespace> nesneler *atomized*; diğer bir deyişle, bunlar bunlar aynı tam adı içeriyorsa, aynı nesneye başvuruyor. Bu sorguları için performans avantajı verir: eşitlik için iki atomized adları karşılaştırdığınızda, temel alınan Ara dile yalnızca iki başvurunun aynı nesneye işaret olup olmadığını belirlemek vardır. Arka plandaki kod zaman alıcı olabilir karşılaştırmaları dize gerekmez.  
  
## <a name="atomization-semantics"></a>Atomization semantiği  
 Atomization anlamına gelir, iki <xref:System.Xml.Linq.XName> nesneler aynı yerel ada sahip ve aynı ad alanında oldukları, aynı örneğini paylaşırlar. Aynı şekilde, iki <xref:System.Xml.Linq.XNamespace> nesneler sahip aynı ad alanı URI, aynı örneğini paylaşırlar.  
  
 Bir sınıf atomized nesneleri etkinleştirmek sınıf oluşturucusu özel ve ortak değil olmalıdır. Oluşturucu ortak olsaydı, atomized olmayan bir nesne oluşturabilirsiniz olmasıdır. <xref:System.Xml.Linq.XName> Ve <xref:System.Xml.Linq.XNamespace> sınıfları uygulayan bir dizeye dönüştürmek için bir örtük dönüşüm işleci bir <xref:System.Xml.Linq.XName> veya <xref:System.Xml.Linq.XNamespace>. Bu nesneler örneği nereden budur. Oluşturucusu erişilemediğinden bir kurucu kullanarak bir örneği elde edilemiyor.  
  
 <xref:System.Xml.Linq.XName>ve <xref:System.Xml.Linq.XNamespace> da iki karşılaştırılan başvuruları aynı örneğini olan nesneleri olup olmadığını belirlemek için eşitlik ve eşitsizlik, işleçler.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod bazı oluşturur <xref:System.Xml.Linq.XElement> nesneleri ve aynı örnek paylaşım aynı adları gösterir.  
  
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
  
 Bu örnek şu çıkışı üretir:  
  
```  
r1 and r2 have names that refer to the same instance.  
The name of r1 and the name in 'n' refer to the same instance.  
```  
  
 Ele eksen yöntemlerden birini kullandığınızda, daha önce belirtildiği gibi faydası atomized nesnelerin ise bir <xref:System.Xml.Linq.XName> bir parametre olarak eksen yöntemi yalnızca iki başvuru istenen öğelerini seçmek için aynı örnek adlarını belirlemek vardır.  
  
 Aşağıdaki örnek geçirmeden bir <xref:System.Xml.Linq.XName> için <xref:System.Xml.Linq.XContainer.Descendants%2A> sonra daha iyi performans nedeniyle atomization düzeni sahip yöntem çağrısı.  
  
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
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<C1>1</C1>  
<C1>1</C1>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans (LINQ-XML) (C#)](../../../../csharp/programming-guide/concepts/linq/performance-linq-to-xml.md)
