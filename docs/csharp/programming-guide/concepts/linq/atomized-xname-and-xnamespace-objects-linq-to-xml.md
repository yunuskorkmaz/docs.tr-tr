---
title: Atomize XName ve XNamespace Nesneler (LINQ xml için) (C#)
ms.date: 07/20/2015
ms.assetid: a5b21433-b49d-415c-b00e-bcbfb0d267d7
ms.openlocfilehash: bc5066440d87f5485ae9099d7a7f4f5e9e66b4ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70204265"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-c"></a>Atomize XName ve XNamespace Nesneler (LINQ xml için) (C#)
<xref:System.Xml.Linq.XName>ve <xref:System.Xml.Linq.XNamespace> nesneler *atomize*edilir; diğer bir şey, aynı nitelikli adı içeriyorsa, aynı nesneye başvururlar. Bu, sorgular için performans avantajları sağlar: Eşitlik için iki atomize adı karşılaştırdığınızda, temel ara dilyalnızca iki başvurunun aynı nesneye işaret edip etmediğini belirlemek zorundadır. Temel kod, zaman alıcı olacaktır dize karşılaştırmaları yapmak zorunda değildir.  
  
## <a name="atomization-semantics"></a>Atomizasyon Semantik  
 Atomizasyon, iki <xref:System.Xml.Linq.XName> nesneaynı yerel ada sahipse ve aynı ad alanındaysa, aynı örneği paylaştıkları anlamına gelir. Aynı şekilde, iki <xref:System.Xml.Linq.XNamespace> nesne aynı ad alanı URI varsa, aynı örneği paylaşır.  
  
 Bir sınıfın atomize nesneleri etkinleştirebilmesi için, sınıfın oluşturucusu ortak değil, özel olmalıdır. Bunun nedeni, eğer oluşturucu ortak sayılsaydı, atomize olmayan bir nesne yaratabiliyordunuz. Ve <xref:System.Xml.Linq.XName> <xref:System.Xml.Linq.XNamespace> sınıflar bir dize dönüştürmek için örtülü <xref:System.Xml.Linq.XName> <xref:System.Xml.Linq.XNamespace>bir dönüştürme işleci uygulamak veya . Bu nesnelerin bir örneğini bu şekilde elde elabilirsiniz. Oluşturucuya erişilmeden erişilemeden bir oluşturucu kullanarak bir örnek alamazsınız.  
  
 <xref:System.Xml.Linq.XName>ve <xref:System.Xml.Linq.XNamespace> aynı zamanda, karşılaştırılan iki nesnenin aynı örne yapılan atıflar olup olmadığını belirlemek için eşitlik ve eşitsizlik işleçlerini uygulayın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod bazı <xref:System.Xml.Linq.XElement> nesneler oluşturur ve aynı adların aynı örneği paylaştığını gösterir.  
  
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
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```output  
r1 and r2 have names that refer to the same instance.  
The name of r1 and the name in 'n' refer to the same instance.  
```  
  
 Daha önce de belirtildiği gibi, atomize nesnelerin yararı, bir parametre <xref:System.Xml.Linq.XName> olarak alan eksen yöntemlerinden birini kullandığınızda, eksen yönteminin yalnızca iki adın istenen öğeleri seçmek için aynı örneğe başvurulacağını belirlemesi gerektiğidir.  
  
 Aşağıdaki örnek, <xref:System.Xml.Linq.XName> atomizasyon <xref:System.Xml.Linq.XContainer.Descendants%2A> deseni nedeniyle daha iyi performansa sahip olan yöntem çağrısına geçer.  
  
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
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```xml  
<C1>1</C1>  
<C1>1</C1>  
```  
