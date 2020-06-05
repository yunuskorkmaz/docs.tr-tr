---
title: Parçalara Ayrılmış XName ve XNamespace Nesneleri (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 21ee7585-7df9-40b4-8c76-a12bb5f29bb3
ms.openlocfilehash: 6a94bc0f2fd8013997e233b300fa19c12671bf29
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84383695"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-visual-basic"></a>Atomlanmış XName ve XNamespace nesneleri (LINQ to XML) (Visual Basic)

<xref:System.Xml.Linq.XName>ve <xref:System.Xml.Linq.XNamespace> nesneleri *atomlanmış*olur; diğer bir deyişle, aynı nitelikli adı içeriyorsa, aynı nesneye başvurur. Bu, sorgular için performans avantajları sağlar: iki atomılı adı eşitlik için karşılaştırdığınızda, temel alınan ara dilin yalnızca iki başvuruyu aynı nesneye işaret edip etmediğini belirlemesi gerekir. Temel alınan kodun, zaman alıcı olabilecek dize karşılaştırmaları yapması gerekmez.

## <a name="atomization-semantics"></a>Atomleştirme semantiği

Atomleştirme <xref:System.Xml.Linq.XName> , iki nesnenin aynı yerel ada sahip olması ve aynı ad alanında olmaları durumunda aynı örneği paylaştıkları anlamına gelir. Aynı şekilde, iki <xref:System.Xml.Linq.XNamespace> nesne aynı ad alanı URI 'sine sahip ise, aynı örneği paylaşır.

Atomlanmış nesneleri etkinleştirmek için bir sınıf için, sınıf için Oluşturucu genel değil, özel olmalıdır. Bunun nedeni, oluşturucunun genel olması, atomsuz olmayan bir nesne oluşturmanız olabilir. <xref:System.Xml.Linq.XName>Ve <xref:System.Xml.Linq.XNamespace> sınıfları bir dizeyi bir veya içine dönüştürmek için örtük bir dönüştürme işleci uygular <xref:System.Xml.Linq.XName> <xref:System.Xml.Linq.XNamespace> . Bu nesnelerin bir örneğini alma işlemi budur. Oluşturucuya erişilemediği için bir oluşturucuyu kullanarak bir örnek alınamaz.

<xref:System.Xml.Linq.XName><xref:System.Xml.Linq.XNamespace>Ayrıca, karşılaştırılan iki nesnenin aynı örneğe başvuru olup olmadığını anlamak için eşitlik ve eşitsizlik işleçlerini da uygulayın.

## <a name="example"></a>Örnek

Aşağıdaki kod bazı nesneler oluşturur <xref:System.Xml.Linq.XElement> ve aynı adların aynı örneği paylaşılacağını gösterir.

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

```console
r1 and r2 have names that refer to the same instance.
The name of r1 and the name in 'n' refer to the same instance.
```

Daha önce belirtildiği gibi, atomlanmış nesnelerin avantajı bir parametre olarak alan eksen yöntemlerinden birini kullandığınızda <xref:System.Xml.Linq.XName> , eksen yönteminin yalnızca iki adların istenen öğeleri seçmek için aynı örneğe başvurmadığını belirlemesi gerekir.

Aşağıdaki örnek, bir <xref:System.Xml.Linq.XName> <xref:System.Xml.Linq.XContainer.Descendants%2A> ' ı yöntem çağrısına geçirir ve daha sonra atomleştirme düzeniyle daha iyi performansa sahiptir.

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

- [Performans (LINQ to XML) (Visual Basic)](performance-linq-to-xml.md)
