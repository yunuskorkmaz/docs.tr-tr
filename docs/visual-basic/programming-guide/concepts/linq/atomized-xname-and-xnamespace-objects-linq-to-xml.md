---
title: Parçalara ayrılmış XName ve XNamespace nesneleri (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 21ee7585-7df9-40b4-8c76-a12bb5f29bb3
ms.openlocfilehash: fe0c4429c89e0028b3b012c87684bd14048de27a
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57843448"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-visual-basic"></a><span data-ttu-id="c9a55-102">Parçalara ayrılmış XName ve XNamespace nesneleri (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9a55-102">Atomized XName and XNamespace Objects (LINQ to XML) (Visual Basic)</span></span>

<span data-ttu-id="c9a55-103"><xref:System.Xml.Linq.XName> ve <xref:System.Xml.Linq.XNamespace> nesneler *parçalara ayrılmış*; diğer bir deyişle, bunlar, bunlar aynı tam ada içeriyorsa, aynı nesneye başvurur.</span><span class="sxs-lookup"><span data-stu-id="c9a55-103"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> objects are *atomized*; that is, if they contain the same qualified name, they refer to the same object.</span></span> <span data-ttu-id="c9a55-104">Bu, sorgular için performans avantajlarının verir: Eşitlik için iki parçalara ayrılmış ad karşılaştırdığınızda, temel alınan Ara dil, yalnızca iki başvurunun aynı nesneye işaret olup olmadığını belirlemek vardır.</span><span class="sxs-lookup"><span data-stu-id="c9a55-104">This yields performance benefits for queries: When you compare two atomized names for equality, the underlying intermediate language only has to determine whether the two references point to the same object.</span></span> <span data-ttu-id="c9a55-105">Arka plandaki kod, zaman alıcı olabilir karşılaştırmalar, dize yok.</span><span class="sxs-lookup"><span data-stu-id="c9a55-105">The underlying code does not have to do string comparisons, which would be time consuming.</span></span>

## <a name="atomization-semantics"></a><span data-ttu-id="c9a55-106">Parçalara ayırma semantiği</span><span class="sxs-lookup"><span data-stu-id="c9a55-106">Atomization Semantics</span></span>

<span data-ttu-id="c9a55-107">Parçalara ayırma anlamına iki <xref:System.Xml.Linq.XName> nesneler aynı yerel ada sahip ve aynı ad alanında oldukları, aynı örneğini paylaşırlar.</span><span class="sxs-lookup"><span data-stu-id="c9a55-107">Atomization means that if two <xref:System.Xml.Linq.XName> objects have the same local name, and they are in the same namespace, they share the same instance.</span></span> <span data-ttu-id="c9a55-108">Aynı şekilde, iki <xref:System.Xml.Linq.XNamespace> nesnelerin aynı ad alanı URI vardır, aynı örneğini paylaşırlar.</span><span class="sxs-lookup"><span data-stu-id="c9a55-108">In the same way, if two <xref:System.Xml.Linq.XNamespace> objects have the same namespace URI, they share the same instance.</span></span>

<span data-ttu-id="c9a55-109">Parçalara ayrılmış nesneleri etkinleştirmek bir sınıf için bir sınıf için oluşturucu özel ve ortak olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c9a55-109">For a class to enable atomized objects, the constructor for the class must be private, not public.</span></span> <span data-ttu-id="c9a55-110">Bu durum, kurucu ortak, parçalara ayrılmış olmayan bir nesne oluşturabilirsiniz olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="c9a55-110">This is because if the constructor were public, you could create a non-atomized object.</span></span> <span data-ttu-id="c9a55-111"><xref:System.Xml.Linq.XName> Ve <xref:System.Xml.Linq.XNamespace> sınıfları uygulayan bir dizeye dönüştürmek için bir örtülü dönüştürme işlecine bir <xref:System.Xml.Linq.XName> veya <xref:System.Xml.Linq.XNamespace>.</span><span class="sxs-lookup"><span data-stu-id="c9a55-111">The <xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> classes implement an implicit conversion operator to convert a string into an <xref:System.Xml.Linq.XName> or <xref:System.Xml.Linq.XNamespace>.</span></span> <span data-ttu-id="c9a55-112">Örneği bu nesnelerin nereden budur.</span><span class="sxs-lookup"><span data-stu-id="c9a55-112">This is how you get an instance of these objects.</span></span> <span data-ttu-id="c9a55-113">Oluşturucusuna erişilemediğinden bir kurucu kullanarak örneği alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="c9a55-113">You cannot get an instance by using a constructor, because the constructor is inaccessible.</span></span>

<span data-ttu-id="c9a55-114"><xref:System.Xml.Linq.XName> ve <xref:System.Xml.Linq.XNamespace> Ayrıca iki olan başvuruları aynı örneğe karşılaştırılan nesne olup olmadığını belirlemek için eşitlik ve eşitsizlik, işleçler.</span><span class="sxs-lookup"><span data-stu-id="c9a55-114"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> also implement the equality and inequality operators, to determine whether the two objects being compared are references to the same instance.</span></span>

## <a name="example"></a><span data-ttu-id="c9a55-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="c9a55-115">Example</span></span>

<span data-ttu-id="c9a55-116">Aşağıdaki kod, bazı oluşturur <xref:System.Xml.Linq.XElement> nesneleri ve aynı örnek paylaşım aynı adları gösterir.</span><span class="sxs-lookup"><span data-stu-id="c9a55-116">The following code creates some <xref:System.Xml.Linq.XElement> objects and demonstrates that identical names share the same instance.</span></span>

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

<span data-ttu-id="c9a55-117">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="c9a55-117">This example produces the following output:</span></span>

```
r1 and r2 have names that refer to the same instance.
The name of r1 and the name in 'n' refer to the same instance.
```

<span data-ttu-id="c9a55-118">Alan eksen yöntemlerden birini kullandığınızda, daha önce bahsedildiği gibi faydası parçalara ayrılmış nesnelerin ise bir <xref:System.Xml.Linq.XName> parametre olarak, eksen yöntemi yalnızca iki başvuru istenen öğeleri seçmek için aynı örnek adlarını belirlemek vardır.</span><span class="sxs-lookup"><span data-stu-id="c9a55-118">As mentioned earlier, the benefit of atomized objects is that when you use one of the axis methods that take an <xref:System.Xml.Linq.XName> as a parameter, the axis method only has to determine that two names reference the same instance to select the desired elements.</span></span>

<span data-ttu-id="c9a55-119">Aşağıdaki örnek geçen bir <xref:System.Xml.Linq.XName> için <xref:System.Xml.Linq.XContainer.Descendants%2A> ardından parçalara ayırma deseni nedeniyle daha iyi performans olan yöntem çağrısı.</span><span class="sxs-lookup"><span data-stu-id="c9a55-119">The following example passes an <xref:System.Xml.Linq.XName> to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method call, which then has better performance because of the atomization pattern.</span></span>

```vb
Dim root As New XElement("Root", New XElement("C1", 1), New XElement("Z1", New XElement("C1", 2), New XElement("C1", 1)))

Dim query = From e In root.Descendants("C1") Where CInt(e) = 1e

For Each z As var In query
    Console.WriteLine(z)
Next
```

<span data-ttu-id="c9a55-120">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="c9a55-120">This example produces the following output:</span></span>

```xml
<C1>1</C1>
<C1>1</C1>
```

## <a name="see-also"></a><span data-ttu-id="c9a55-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c9a55-121">See also</span></span>

- [<span data-ttu-id="c9a55-122">Performans (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9a55-122">Performance (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
