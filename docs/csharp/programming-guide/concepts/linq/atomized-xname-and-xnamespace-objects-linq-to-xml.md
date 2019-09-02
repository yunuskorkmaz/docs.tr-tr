---
title: Atomlanmış XName ve XNamespace nesneleri (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: a5b21433-b49d-415c-b00e-bcbfb0d267d7
ms.openlocfilehash: bc5066440d87f5485ae9099d7a7f4f5e9e66b4ec
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204265"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-c"></a>Atomlanmış XName ve XNamespace nesneleri (LINQ to XML) (C#)
<xref:System.Xml.Linq.XName>ve <xref:System.Xml.Linq.XNamespace> nesneleri *atomlanmış*olur; diğer bir deyişle, aynı nitelikli adı içeriyorsa, aynı nesneye başvurur. Bu, sorgular için performans avantajları verir: İki atomılı adı eşitlik için karşılaştırdığınızda, temel alınan ara dilin yalnızca iki başvuruyu aynı nesneye işaret edip etmediğini belirlemesi gerekir. Temel alınan kodun, zaman alıcı olabilecek dize karşılaştırmaları yapması gerekmez.  
  
## <a name="atomization-semantics"></a>Atomleştirme semantiği  
 Atomleştirme, iki <xref:System.Xml.Linq.XName> nesnenin aynı yerel ada sahip olması ve aynı ad alanında olmaları durumunda aynı örneği paylaştıkları anlamına gelir. Aynı şekilde, iki <xref:System.Xml.Linq.XNamespace> nesne aynı ad alanı URI 'sine sahip ise, aynı örneği paylaşır.  
  
 Atomlanmış nesneleri etkinleştirmek için bir sınıf için, sınıf için Oluşturucu genel değil, özel olmalıdır. Bunun nedeni, oluşturucunun genel olması, atomsuz olmayan bir nesne oluşturmanız olabilir. Ve sınıfları bir <xref:System.Xml.Linq.XName> dizeyi bir veya <xref:System.Xml.Linq.XNamespace>içine dönüştürmek için örtük bir dönüştürme işleci uygular. <xref:System.Xml.Linq.XName> <xref:System.Xml.Linq.XNamespace> Bu nesnelerin bir örneğini alma işlemi budur. Oluşturucuya erişilemediği için bir oluşturucuyu kullanarak bir örnek alınamaz.  
  
 <xref:System.Xml.Linq.XName><xref:System.Xml.Linq.XNamespace> Ayrıca, karşılaştırılan iki nesnenin aynı örneğe başvuru olup olmadığını anlamak için eşitlik ve eşitsizlik işleçlerini da uygulayın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod bazı <xref:System.Xml.Linq.XElement> nesneler oluşturur ve aynı adların aynı örneği paylaşılacağını gösterir.  
  
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
  
 Daha önce belirtildiği gibi, atomlanmış nesnelerin avantajı bir parametre <xref:System.Xml.Linq.XName> olarak alan eksen yöntemlerinden birini kullandığınızda, eksen yönteminin yalnızca iki adların istenen öğeleri seçmek için aynı örneğe başvurmadığını belirlemesi gerekir.  
  
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
