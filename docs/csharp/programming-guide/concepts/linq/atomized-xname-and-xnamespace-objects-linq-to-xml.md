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
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-c"></a><span data-ttu-id="f9bf1-102">Atomize XName ve XNamespace Nesneler (LINQ xml için) (C#)</span><span class="sxs-lookup"><span data-stu-id="f9bf1-102">Atomized XName and XNamespace Objects (LINQ to XML) (C#)</span></span>
<span data-ttu-id="f9bf1-103"><xref:System.Xml.Linq.XName>ve <xref:System.Xml.Linq.XNamespace> nesneler *atomize*edilir; diğer bir şey, aynı nitelikli adı içeriyorsa, aynı nesneye başvururlar.</span><span class="sxs-lookup"><span data-stu-id="f9bf1-103"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> objects are *atomized*; that is, if they contain the same qualified name, they refer to the same object.</span></span> <span data-ttu-id="f9bf1-104">Bu, sorgular için performans avantajları sağlar: Eşitlik için iki atomize adı karşılaştırdığınızda, temel ara dilyalnızca iki başvurunun aynı nesneye işaret edip etmediğini belirlemek zorundadır.</span><span class="sxs-lookup"><span data-stu-id="f9bf1-104">This yields performance benefits for queries: When you compare two atomized names for equality, the underlying intermediate language only has to determine whether the two references point to the same object.</span></span> <span data-ttu-id="f9bf1-105">Temel kod, zaman alıcı olacaktır dize karşılaştırmaları yapmak zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="f9bf1-105">The underlying code does not have to do string comparisons, which would be time consuming.</span></span>  
  
## <a name="atomization-semantics"></a><span data-ttu-id="f9bf1-106">Atomizasyon Semantik</span><span class="sxs-lookup"><span data-stu-id="f9bf1-106">Atomization Semantics</span></span>  
 <span data-ttu-id="f9bf1-107">Atomizasyon, iki <xref:System.Xml.Linq.XName> nesneaynı yerel ada sahipse ve aynı ad alanındaysa, aynı örneği paylaştıkları anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f9bf1-107">Atomization means that if two <xref:System.Xml.Linq.XName> objects have the same local name, and they are in the same namespace, they share the same instance.</span></span> <span data-ttu-id="f9bf1-108">Aynı şekilde, iki <xref:System.Xml.Linq.XNamespace> nesne aynı ad alanı URI varsa, aynı örneği paylaşır.</span><span class="sxs-lookup"><span data-stu-id="f9bf1-108">In the same way, if two <xref:System.Xml.Linq.XNamespace> objects have the same namespace URI, they share the same instance.</span></span>  
  
 <span data-ttu-id="f9bf1-109">Bir sınıfın atomize nesneleri etkinleştirebilmesi için, sınıfın oluşturucusu ortak değil, özel olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f9bf1-109">For a class to enable atomized objects, the constructor for the class must be private, not public.</span></span> <span data-ttu-id="f9bf1-110">Bunun nedeni, eğer oluşturucu ortak sayılsaydı, atomize olmayan bir nesne yaratabiliyordunuz.</span><span class="sxs-lookup"><span data-stu-id="f9bf1-110">This is because if the constructor were public, you could create a non-atomized object.</span></span> <span data-ttu-id="f9bf1-111">Ve <xref:System.Xml.Linq.XName> <xref:System.Xml.Linq.XNamespace> sınıflar bir dize dönüştürmek için örtülü <xref:System.Xml.Linq.XName> <xref:System.Xml.Linq.XNamespace>bir dönüştürme işleci uygulamak veya .</span><span class="sxs-lookup"><span data-stu-id="f9bf1-111">The <xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> classes implement an implicit conversion operator to convert a string into an <xref:System.Xml.Linq.XName> or <xref:System.Xml.Linq.XNamespace>.</span></span> <span data-ttu-id="f9bf1-112">Bu nesnelerin bir örneğini bu şekilde elde elabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f9bf1-112">This is how you get an instance of these objects.</span></span> <span data-ttu-id="f9bf1-113">Oluşturucuya erişilmeden erişilemeden bir oluşturucu kullanarak bir örnek alamazsınız.</span><span class="sxs-lookup"><span data-stu-id="f9bf1-113">You cannot get an instance by using a constructor, because the constructor is inaccessible.</span></span>  
  
 <span data-ttu-id="f9bf1-114"><xref:System.Xml.Linq.XName>ve <xref:System.Xml.Linq.XNamespace> aynı zamanda, karşılaştırılan iki nesnenin aynı örne yapılan atıflar olup olmadığını belirlemek için eşitlik ve eşitsizlik işleçlerini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="f9bf1-114"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> also implement the equality and inequality operators, to determine whether the two objects being compared are references to the same instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9bf1-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="f9bf1-115">Example</span></span>  
 <span data-ttu-id="f9bf1-116">Aşağıdaki kod bazı <xref:System.Xml.Linq.XElement> nesneler oluşturur ve aynı adların aynı örneği paylaştığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f9bf1-116">The following code creates some <xref:System.Xml.Linq.XElement> objects and demonstrates that identical names share the same instance.</span></span>  
  
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
  
 <span data-ttu-id="f9bf1-117">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="f9bf1-117">This example produces the following output:</span></span>  
  
```output  
r1 and r2 have names that refer to the same instance.  
The name of r1 and the name in 'n' refer to the same instance.  
```  
  
 <span data-ttu-id="f9bf1-118">Daha önce de belirtildiği gibi, atomize nesnelerin yararı, bir parametre <xref:System.Xml.Linq.XName> olarak alan eksen yöntemlerinden birini kullandığınızda, eksen yönteminin yalnızca iki adın istenen öğeleri seçmek için aynı örneğe başvurulacağını belirlemesi gerektiğidir.</span><span class="sxs-lookup"><span data-stu-id="f9bf1-118">As mentioned earlier, the benefit of atomized objects is that when you use one of the axis methods that take an <xref:System.Xml.Linq.XName> as a parameter, the axis method only has to determine that two names reference the same instance to select the desired elements.</span></span>  
  
 <span data-ttu-id="f9bf1-119">Aşağıdaki örnek, <xref:System.Xml.Linq.XName> atomizasyon <xref:System.Xml.Linq.XContainer.Descendants%2A> deseni nedeniyle daha iyi performansa sahip olan yöntem çağrısına geçer.</span><span class="sxs-lookup"><span data-stu-id="f9bf1-119">The following example passes an <xref:System.Xml.Linq.XName> to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method call, which then has better performance because of the atomization pattern.</span></span>  
  
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
  
 <span data-ttu-id="f9bf1-120">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="f9bf1-120">This example produces the following output:</span></span>  
  
```xml  
<C1>1</C1>  
<C1>1</C1>  
```  
