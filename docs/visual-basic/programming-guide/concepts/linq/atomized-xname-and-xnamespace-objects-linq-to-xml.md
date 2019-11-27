---
title: Parçalara Ayrılmış XName ve XNamespace Nesneleri (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 21ee7585-7df9-40b4-8c76-a12bb5f29bb3
ms.openlocfilehash: 0ffed5d00364f6614b439480607ed521f52754ec
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345728"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-visual-basic"></a>Atomlanmış XName ve XNamespace nesneleri (LINQ to XML) (Visual Basic)

<xref:System.Xml.Linq.XName> ve <xref:System.Xml.Linq.XNamespace> nesneleri *atomlanmış*; diğer bir deyişle, aynı nitelikli adı içeriyorsa, aynı nesneye başvurur. Bu, sorgular için performans avantajları sağlar: iki atomılı adı eşitlik için karşılaştırdığınızda, temel alınan ara dilin yalnızca iki başvuruyu aynı nesneye işaret edip etmediğini belirlemesi gerekir. Temel alınan kodun, zaman alıcı olabilecek dize karşılaştırmaları yapması gerekmez.

## <a name="atomization-semantics"></a>Atomleştirme semantiği

Atomleştirme, iki <xref:System.Xml.Linq.XName> nesnenin aynı yerel ada sahip olması ve aynı ad alanında olmaları durumunda aynı örneği paylaştıkları anlamına gelir. Aynı şekilde, iki <xref:System.Xml.Linq.XNamespace> nesnesi aynı ad alanı URI 'sine sahip ise, aynı örneği paylaşır.

Atomlanmış nesneleri etkinleştirmek için bir sınıf için, sınıf için Oluşturucu genel değil, özel olmalıdır. Bunun nedeni, oluşturucunun genel olması, atomsuz olmayan bir nesne oluşturmanız olabilir. <xref:System.Xml.Linq.XName> ve <xref:System.Xml.Linq.XNamespace> sınıfları bir dizeyi <xref:System.Xml.Linq.XName> veya <xref:System.Xml.Linq.XNamespace>dönüştürmek için örtük bir dönüştürme işleci uygular. Bu nesnelerin bir örneğini alma işlemi budur. Oluşturucuya erişilemediği için bir oluşturucuyu kullanarak bir örnek alınamaz.

<xref:System.Xml.Linq.XName> ve <xref:System.Xml.Linq.XNamespace>, karşılaştırılan iki nesnenin aynı örneğe başvuru olup olmadığını anlamak için eşitlik ve eşitsizlik işleçlerini da uygular.

## <a name="example"></a>Örnek

Aşağıdaki kod bazı <xref:System.Xml.Linq.XElement> nesneler oluşturur ve aynı adların aynı örneği paylaşacağını gösterir.

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

Daha önce belirtildiği gibi, atomlanmış nesnelerin avantajı, bir <xref:System.Xml.Linq.XName> parametre olarak alan eksen yöntemlerinden birini kullandığınızda, eksen yönteminin yalnızca iki adların istenen öğeleri seçmek için aynı örneğe başvurulacağını belirlemesi gerekir.

Aşağıdaki örnek, bir <xref:System.Xml.Linq.XName> <xref:System.Xml.Linq.XContainer.Descendants%2A> yöntemi çağrısına geçirir ve bu da atomleştirme deseninin nedeniyle daha iyi performansa sahiptir.

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
