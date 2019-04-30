---
title: Parçalara ayrılmış XName ve XNamespace nesneleri (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: a5b21433-b49d-415c-b00e-bcbfb0d267d7
ms.openlocfilehash: ff5677e84d0a4401c9d3ce8c43e7743385cdd432
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61668443"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-c"></a><span data-ttu-id="a0804-102">Parçalara ayrılmış XName ve XNamespace nesneleri (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="a0804-102">Atomized XName and XNamespace Objects (LINQ to XML) (C#)</span></span>
<span data-ttu-id="a0804-103"><xref:System.Xml.Linq.XName> ve <xref:System.Xml.Linq.XNamespace> nesneler *parçalara ayrılmış*; diğer bir deyişle, bunlar, bunlar aynı tam ada içeriyorsa, aynı nesneye başvurur.</span><span class="sxs-lookup"><span data-stu-id="a0804-103"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> objects are *atomized*; that is, if they contain the same qualified name, they refer to the same object.</span></span> <span data-ttu-id="a0804-104">Bu, sorgular için performans avantajlarının verir: Eşitlik için iki parçalara ayrılmış ad karşılaştırdığınızda, temel alınan Ara dil, yalnızca iki başvurunun aynı nesneye işaret olup olmadığını belirlemek vardır.</span><span class="sxs-lookup"><span data-stu-id="a0804-104">This yields performance benefits for queries: When you compare two atomized names for equality, the underlying intermediate language only has to determine whether the two references point to the same object.</span></span> <span data-ttu-id="a0804-105">Arka plandaki kod, zaman alıcı olabilir karşılaştırmalar, dize yok.</span><span class="sxs-lookup"><span data-stu-id="a0804-105">The underlying code does not have to do string comparisons, which would be time consuming.</span></span>  
  
## <a name="atomization-semantics"></a><span data-ttu-id="a0804-106">Parçalara ayırma semantiği</span><span class="sxs-lookup"><span data-stu-id="a0804-106">Atomization Semantics</span></span>  
 <span data-ttu-id="a0804-107">Parçalara ayırma anlamına iki <xref:System.Xml.Linq.XName> nesneler aynı yerel ada sahip ve aynı ad alanında oldukları, aynı örneğini paylaşırlar.</span><span class="sxs-lookup"><span data-stu-id="a0804-107">Atomization means that if two <xref:System.Xml.Linq.XName> objects have the same local name, and they are in the same namespace, they share the same instance.</span></span> <span data-ttu-id="a0804-108">Aynı şekilde, iki <xref:System.Xml.Linq.XNamespace> nesnelerin aynı ad alanı URI vardır, aynı örneğini paylaşırlar.</span><span class="sxs-lookup"><span data-stu-id="a0804-108">In the same way, if two <xref:System.Xml.Linq.XNamespace> objects have the same namespace URI, they share the same instance.</span></span>  
  
 <span data-ttu-id="a0804-109">Parçalara ayrılmış nesneleri etkinleştirmek bir sınıf için bir sınıf için oluşturucu özel ve ortak olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a0804-109">For a class to enable atomized objects, the constructor for the class must be private, not public.</span></span> <span data-ttu-id="a0804-110">Bu durum, kurucu ortak, parçalara ayrılmış olmayan bir nesne oluşturabilirsiniz olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="a0804-110">This is because if the constructor were public, you could create a non-atomized object.</span></span> <span data-ttu-id="a0804-111"><xref:System.Xml.Linq.XName> Ve <xref:System.Xml.Linq.XNamespace> sınıfları uygulayan bir dizeye dönüştürmek için bir örtülü dönüştürme işlecine bir <xref:System.Xml.Linq.XName> veya <xref:System.Xml.Linq.XNamespace>.</span><span class="sxs-lookup"><span data-stu-id="a0804-111">The <xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> classes implement an implicit conversion operator to convert a string into an <xref:System.Xml.Linq.XName> or <xref:System.Xml.Linq.XNamespace>.</span></span> <span data-ttu-id="a0804-112">Örneği bu nesnelerin nereden budur.</span><span class="sxs-lookup"><span data-stu-id="a0804-112">This is how you get an instance of these objects.</span></span> <span data-ttu-id="a0804-113">Oluşturucusuna erişilemediğinden bir kurucu kullanarak örneği alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="a0804-113">You cannot get an instance by using a constructor, because the constructor is inaccessible.</span></span>  
  
 <span data-ttu-id="a0804-114"><xref:System.Xml.Linq.XName> ve <xref:System.Xml.Linq.XNamespace> Ayrıca iki olan başvuruları aynı örneğe karşılaştırılan nesne olup olmadığını belirlemek için eşitlik ve eşitsizlik, işleçler.</span><span class="sxs-lookup"><span data-stu-id="a0804-114"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> also implement the equality and inequality operators, to determine whether the two objects being compared are references to the same instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0804-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="a0804-115">Example</span></span>  
 <span data-ttu-id="a0804-116">Aşağıdaki kod, bazı oluşturur <xref:System.Xml.Linq.XElement> nesneleri ve aynı örnek paylaşım aynı adları gösterir.</span><span class="sxs-lookup"><span data-stu-id="a0804-116">The following code creates some <xref:System.Xml.Linq.XElement> objects and demonstrates that identical names share the same instance.</span></span>  
  
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
  
 <span data-ttu-id="a0804-117">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="a0804-117">This example produces the following output:</span></span>  
  
```  
r1 and r2 have names that refer to the same instance.  
The name of r1 and the name in 'n' refer to the same instance.  
```  
  
 <span data-ttu-id="a0804-118">Alan eksen yöntemlerden birini kullandığınızda, daha önce bahsedildiği gibi faydası parçalara ayrılmış nesnelerin ise bir <xref:System.Xml.Linq.XName> parametre olarak, eksen yöntemi yalnızca iki başvuru istenen öğeleri seçmek için aynı örnek adlarını belirlemek vardır.</span><span class="sxs-lookup"><span data-stu-id="a0804-118">As mentioned earlier, the benefit of atomized objects is that when you use one of the axis methods that take an <xref:System.Xml.Linq.XName> as a parameter, the axis method only has to determine that two names reference the same instance to select the desired elements.</span></span>  
  
 <span data-ttu-id="a0804-119">Aşağıdaki örnek geçen bir <xref:System.Xml.Linq.XName> için <xref:System.Xml.Linq.XContainer.Descendants%2A> ardından parçalara ayırma deseni nedeniyle daha iyi performans olan yöntem çağrısı.</span><span class="sxs-lookup"><span data-stu-id="a0804-119">The following example passes an <xref:System.Xml.Linq.XName> to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method call, which then has better performance because of the atomization pattern.</span></span>  
  
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
  
 <span data-ttu-id="a0804-120">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="a0804-120">This example produces the following output:</span></span>  
  
```xml  
<C1>1</C1>  
<C1>1</C1>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a0804-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0804-121">See also</span></span>

- [<span data-ttu-id="a0804-122">Performans (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="a0804-122">Performance (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/performance-linq-to-xml.md)
