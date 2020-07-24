---
title: Atomlanmış XName ve XNamespace nesneleri (LINQ to XML) (C#)
description: Atomlanmış XName ve XNamespace nesneleri hakkında bilgi edinin ve sorgular için performans avantajları sağlar.
ms.date: 07/20/2015
ms.assetid: a5b21433-b49d-415c-b00e-bcbfb0d267d7
ms.openlocfilehash: 305a233adab5c860b5f9509ae25ccc5d633e7957
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104274"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-c"></a>Atomlanmış XName ve XNamespace nesneleri (LINQ to XML) (C#)
<xref:System.Xml.Linq.XName>ve <xref:System.Xml.Linq.XNamespace> nesneleri *atomlanmış*olur; diğer bir deyişle, aynı nitelikli adı içeriyorsa, aynı nesneye başvurur. Bu, sorgular için performans avantajları sağlar: iki atomılı adı eşitlik için karşılaştırdığınızda, temel alınan ara dilin yalnızca iki başvuruyu aynı nesneye işaret edip etmediğini belirlemesi gerekir. Temel alınan kodun, zaman alıcı olabilecek dize karşılaştırmaları yapması gerekmez.  
  
## <a name="atomization-semantics"></a>Atomleştirme semantiği  
 Atomleştirme <xref:System.Xml.Linq.XName> , iki nesnenin aynı yerel ada sahip olması ve aynı ad alanında olmaları durumunda aynı örneği paylaştıkları anlamına gelir. Aynı şekilde, iki <xref:System.Xml.Linq.XNamespace> nesne aynı ad alanı URI 'sine sahip ise, aynı örneği paylaşır.  
  
 Atomlanmış nesneleri etkinleştirmek için bir sınıf için, sınıf için Oluşturucu genel değil, özel olmalıdır. Bunun nedeni, oluşturucunun genel olması, atomsuz olmayan bir nesne oluşturmanız olabilir. <xref:System.Xml.Linq.XName>Ve <xref:System.Xml.Linq.XNamespace> sınıfları bir dizeyi bir veya içine dönüştürmek için örtük bir dönüştürme işleci uygular <xref:System.Xml.Linq.XName> <xref:System.Xml.Linq.XNamespace> . Bu nesnelerin bir örneğini alma işlemi budur. Oluşturucuya erişilemediği için bir oluşturucuyu kullanarak bir örnek alınamaz.  
  
 <xref:System.Xml.Linq.XName><xref:System.Xml.Linq.XNamespace>Ayrıca, karşılaştırılan iki nesnenin aynı örneğe başvuru olup olmadığını anlamak için eşitlik ve eşitsizlik işleçlerini da uygulayın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod bazı nesneler oluşturur <xref:System.Xml.Linq.XElement> ve aynı adların aynı örneği paylaşılacağını gösterir.  
  
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
  
```output  
r1 and r2 have names that refer to the same instance.  
The name of r1 and the name in 'n' refer to the same instance.  
```  
  
 Daha önce belirtildiği gibi, atomlanmış nesnelerin avantajı bir parametre olarak alan eksen yöntemlerinden birini kullandığınızda <xref:System.Xml.Linq.XName> , eksen yönteminin yalnızca iki adların istenen öğeleri seçmek için aynı örneğe başvurmadığını belirlemesi gerekir.  
  
 Aşağıdaki örnek, bir <xref:System.Xml.Linq.XName> <xref:System.Xml.Linq.XContainer.Descendants%2A> ' ı yöntem çağrısına geçirir ve daha sonra atomleştirme düzeniyle daha iyi performansa sahiptir.  
  
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
