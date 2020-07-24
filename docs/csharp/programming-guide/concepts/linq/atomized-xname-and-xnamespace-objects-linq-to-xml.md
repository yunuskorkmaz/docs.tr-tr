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
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-c"></a><span data-ttu-id="e4129-103">Atomlanmış XName ve XNamespace nesneleri (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="e4129-103">Atomized XName and XNamespace Objects (LINQ to XML) (C#)</span></span>
<span data-ttu-id="e4129-104"><xref:System.Xml.Linq.XName>ve <xref:System.Xml.Linq.XNamespace> nesneleri *atomlanmış*olur; diğer bir deyişle, aynı nitelikli adı içeriyorsa, aynı nesneye başvurur.</span><span class="sxs-lookup"><span data-stu-id="e4129-104"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> objects are *atomized*; that is, if they contain the same qualified name, they refer to the same object.</span></span> <span data-ttu-id="e4129-105">Bu, sorgular için performans avantajları sağlar: iki atomılı adı eşitlik için karşılaştırdığınızda, temel alınan ara dilin yalnızca iki başvuruyu aynı nesneye işaret edip etmediğini belirlemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e4129-105">This yields performance benefits for queries: When you compare two atomized names for equality, the underlying intermediate language only has to determine whether the two references point to the same object.</span></span> <span data-ttu-id="e4129-106">Temel alınan kodun, zaman alıcı olabilecek dize karşılaştırmaları yapması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="e4129-106">The underlying code does not have to do string comparisons, which would be time consuming.</span></span>  
  
## <a name="atomization-semantics"></a><span data-ttu-id="e4129-107">Atomleştirme semantiği</span><span class="sxs-lookup"><span data-stu-id="e4129-107">Atomization Semantics</span></span>  
 <span data-ttu-id="e4129-108">Atomleştirme <xref:System.Xml.Linq.XName> , iki nesnenin aynı yerel ada sahip olması ve aynı ad alanında olmaları durumunda aynı örneği paylaştıkları anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e4129-108">Atomization means that if two <xref:System.Xml.Linq.XName> objects have the same local name, and they are in the same namespace, they share the same instance.</span></span> <span data-ttu-id="e4129-109">Aynı şekilde, iki <xref:System.Xml.Linq.XNamespace> nesne aynı ad alanı URI 'sine sahip ise, aynı örneği paylaşır.</span><span class="sxs-lookup"><span data-stu-id="e4129-109">In the same way, if two <xref:System.Xml.Linq.XNamespace> objects have the same namespace URI, they share the same instance.</span></span>  
  
 <span data-ttu-id="e4129-110">Atomlanmış nesneleri etkinleştirmek için bir sınıf için, sınıf için Oluşturucu genel değil, özel olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e4129-110">For a class to enable atomized objects, the constructor for the class must be private, not public.</span></span> <span data-ttu-id="e4129-111">Bunun nedeni, oluşturucunun genel olması, atomsuz olmayan bir nesne oluşturmanız olabilir.</span><span class="sxs-lookup"><span data-stu-id="e4129-111">This is because if the constructor were public, you could create a non-atomized object.</span></span> <span data-ttu-id="e4129-112"><xref:System.Xml.Linq.XName>Ve <xref:System.Xml.Linq.XNamespace> sınıfları bir dizeyi bir veya içine dönüştürmek için örtük bir dönüştürme işleci uygular <xref:System.Xml.Linq.XName> <xref:System.Xml.Linq.XNamespace> .</span><span class="sxs-lookup"><span data-stu-id="e4129-112">The <xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> classes implement an implicit conversion operator to convert a string into an <xref:System.Xml.Linq.XName> or <xref:System.Xml.Linq.XNamespace>.</span></span> <span data-ttu-id="e4129-113">Bu nesnelerin bir örneğini alma işlemi budur.</span><span class="sxs-lookup"><span data-stu-id="e4129-113">This is how you get an instance of these objects.</span></span> <span data-ttu-id="e4129-114">Oluşturucuya erişilemediği için bir oluşturucuyu kullanarak bir örnek alınamaz.</span><span class="sxs-lookup"><span data-stu-id="e4129-114">You cannot get an instance by using a constructor, because the constructor is inaccessible.</span></span>  
  
 <span data-ttu-id="e4129-115"><xref:System.Xml.Linq.XName><xref:System.Xml.Linq.XNamespace>Ayrıca, karşılaştırılan iki nesnenin aynı örneğe başvuru olup olmadığını anlamak için eşitlik ve eşitsizlik işleçlerini da uygulayın.</span><span class="sxs-lookup"><span data-stu-id="e4129-115"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> also implement the equality and inequality operators, to determine whether the two objects being compared are references to the same instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4129-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="e4129-116">Example</span></span>  
 <span data-ttu-id="e4129-117">Aşağıdaki kod bazı nesneler oluşturur <xref:System.Xml.Linq.XElement> ve aynı adların aynı örneği paylaşılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e4129-117">The following code creates some <xref:System.Xml.Linq.XElement> objects and demonstrates that identical names share the same instance.</span></span>  
  
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
  
 <span data-ttu-id="e4129-118">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="e4129-118">This example produces the following output:</span></span>  
  
```output  
r1 and r2 have names that refer to the same instance.  
The name of r1 and the name in 'n' refer to the same instance.  
```  
  
 <span data-ttu-id="e4129-119">Daha önce belirtildiği gibi, atomlanmış nesnelerin avantajı bir parametre olarak alan eksen yöntemlerinden birini kullandığınızda <xref:System.Xml.Linq.XName> , eksen yönteminin yalnızca iki adların istenen öğeleri seçmek için aynı örneğe başvurmadığını belirlemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e4129-119">As mentioned earlier, the benefit of atomized objects is that when you use one of the axis methods that take an <xref:System.Xml.Linq.XName> as a parameter, the axis method only has to determine that two names reference the same instance to select the desired elements.</span></span>  
  
 <span data-ttu-id="e4129-120">Aşağıdaki örnek, bir <xref:System.Xml.Linq.XName> <xref:System.Xml.Linq.XContainer.Descendants%2A> ' ı yöntem çağrısına geçirir ve daha sonra atomleştirme düzeniyle daha iyi performansa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e4129-120">The following example passes an <xref:System.Xml.Linq.XName> to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method call, which then has better performance because of the atomization pattern.</span></span>  
  
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
  
 <span data-ttu-id="e4129-121">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="e4129-121">This example produces the following output:</span></span>  
  
```xml  
<C1>1</C1>  
<C1>1</C1>  
```  
