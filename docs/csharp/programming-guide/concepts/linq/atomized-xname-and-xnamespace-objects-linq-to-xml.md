---
title: Atomized XName ve XNamespace nesneleri (LINQ-XML) (C#)
ms.date: 07/20/2015
ms.assetid: a5b21433-b49d-415c-b00e-bcbfb0d267d7
ms.openlocfilehash: 85799741246f484bcb17a1ae7e320bd477872238
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33323215"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-c"></a><span data-ttu-id="2f647-102">Atomized XName ve XNamespace nesneleri (LINQ-XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="2f647-102">Atomized XName and XNamespace Objects (LINQ to XML) (C#)</span></span>
<span data-ttu-id="2f647-103"><xref:System.Xml.Linq.XName> ve <xref:System.Xml.Linq.XNamespace> nesneler *atomized*; diğer bir deyişle, bunlar bunlar aynı tam adı içeriyorsa, aynı nesneye başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="2f647-103"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> objects are *atomized*; that is, if they contain the same qualified name, they refer to the same object.</span></span> <span data-ttu-id="2f647-104">Bu sorguları için performans avantajı verir: eşitlik için iki atomized adları karşılaştırdığınızda, temel alınan Ara dile yalnızca iki başvurunun aynı nesneye işaret olup olmadığını belirlemek vardır.</span><span class="sxs-lookup"><span data-stu-id="2f647-104">This yields performance benefits for queries: When you compare two atomized names for equality, the underlying intermediate language only has to determine whether the two references point to the same object.</span></span> <span data-ttu-id="2f647-105">Arka plandaki kod zaman alıcı olabilir karşılaştırmaları dize gerekmez.</span><span class="sxs-lookup"><span data-stu-id="2f647-105">The underlying code does not have to do string comparisons, which would be time consuming.</span></span>  
  
## <a name="atomization-semantics"></a><span data-ttu-id="2f647-106">Atomization semantiği</span><span class="sxs-lookup"><span data-stu-id="2f647-106">Atomization Semantics</span></span>  
 <span data-ttu-id="2f647-107">Atomization anlamına gelir, iki <xref:System.Xml.Linq.XName> nesneler aynı yerel ada sahip ve aynı ad alanında oldukları, aynı örneğini paylaşırlar.</span><span class="sxs-lookup"><span data-stu-id="2f647-107">Atomization means that if two <xref:System.Xml.Linq.XName> objects have the same local name, and they are in the same namespace, they share the same instance.</span></span> <span data-ttu-id="2f647-108">Aynı şekilde, iki <xref:System.Xml.Linq.XNamespace> nesneler sahip aynı ad alanı URI, aynı örneğini paylaşırlar.</span><span class="sxs-lookup"><span data-stu-id="2f647-108">In the same way, if two <xref:System.Xml.Linq.XNamespace> objects have the same namespace URI, they share the same instance.</span></span>  
  
 <span data-ttu-id="2f647-109">Bir sınıf atomized nesneleri etkinleştirmek sınıf oluşturucusu özel ve ortak değil olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2f647-109">For a class to enable atomized objects, the constructor for the class must be private, not public.</span></span> <span data-ttu-id="2f647-110">Oluşturucu ortak olsaydı, atomized olmayan bir nesne oluşturabilirsiniz olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="2f647-110">This is because if the constructor were public, you could create a non-atomized object.</span></span> <span data-ttu-id="2f647-111"><xref:System.Xml.Linq.XName> Ve <xref:System.Xml.Linq.XNamespace> sınıfları uygulayan bir dizeye dönüştürmek için bir örtük dönüşüm işleci bir <xref:System.Xml.Linq.XName> veya <xref:System.Xml.Linq.XNamespace>.</span><span class="sxs-lookup"><span data-stu-id="2f647-111">The <xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> classes implement an implicit conversion operator to convert a string into an <xref:System.Xml.Linq.XName> or <xref:System.Xml.Linq.XNamespace>.</span></span> <span data-ttu-id="2f647-112">Bu nesneler örneği nereden budur.</span><span class="sxs-lookup"><span data-stu-id="2f647-112">This is how you get an instance of these objects.</span></span> <span data-ttu-id="2f647-113">Oluşturucusu erişilemediğinden bir kurucu kullanarak bir örneği elde edilemiyor.</span><span class="sxs-lookup"><span data-stu-id="2f647-113">You cannot get an instance by using a constructor, because the constructor is inaccessible.</span></span>  
  
 <span data-ttu-id="2f647-114"><xref:System.Xml.Linq.XName> ve <xref:System.Xml.Linq.XNamespace> da iki karşılaştırılan başvuruları aynı örneğini olan nesneleri olup olmadığını belirlemek için eşitlik ve eşitsizlik, işleçler.</span><span class="sxs-lookup"><span data-stu-id="2f647-114"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> also implement the equality and inequality operators, to determine whether the two objects being compared are references to the same instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f647-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="2f647-115">Example</span></span>  
 <span data-ttu-id="2f647-116">Aşağıdaki kod bazı oluşturur <xref:System.Xml.Linq.XElement> nesneleri ve aynı örnek paylaşım aynı adları gösterir.</span><span class="sxs-lookup"><span data-stu-id="2f647-116">The following code creates some <xref:System.Xml.Linq.XElement> objects and demonstrates that identical names share the same instance.</span></span>  
  
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
  
 <span data-ttu-id="2f647-117">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="2f647-117">This example produces the following output:</span></span>  
  
```  
r1 and r2 have names that refer to the same instance.  
The name of r1 and the name in 'n' refer to the same instance.  
```  
  
 <span data-ttu-id="2f647-118">Ele eksen yöntemlerden birini kullandığınızda, daha önce belirtildiği gibi faydası atomized nesnelerin ise bir <xref:System.Xml.Linq.XName> bir parametre olarak eksen yöntemi yalnızca iki başvuru istenen öğelerini seçmek için aynı örnek adlarını belirlemek vardır.</span><span class="sxs-lookup"><span data-stu-id="2f647-118">As mentioned earlier, the benefit of atomized objects is that when you use one of the axis methods that take an <xref:System.Xml.Linq.XName> as a parameter, the axis method only has to determine that two names reference the same instance to select the desired elements.</span></span>  
  
 <span data-ttu-id="2f647-119">Aşağıdaki örnek geçirmeden bir <xref:System.Xml.Linq.XName> için <xref:System.Xml.Linq.XContainer.Descendants%2A> sonra daha iyi performans nedeniyle atomization düzeni sahip yöntem çağrısı.</span><span class="sxs-lookup"><span data-stu-id="2f647-119">The following example passes an <xref:System.Xml.Linq.XName> to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method call, which then has better performance because of the atomization pattern.</span></span>  
  
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
  
 <span data-ttu-id="2f647-120">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="2f647-120">This example produces the following output:</span></span>  
  
```xml  
<C1>1</C1>  
<C1>1</C1>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2f647-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2f647-121">See Also</span></span>  
 [<span data-ttu-id="2f647-122">Performans (LINQ-XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="2f647-122">Performance (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/performance-linq-to-xml.md)
