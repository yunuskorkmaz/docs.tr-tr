---
title: Bir öğenin değeri (LINQ - XML) (C#) nasıl alınır?
ms.date: 07/20/2015
ms.assetid: 4228c007-07c9-4cf2-a45b-e7074c109581
ms.openlocfilehash: 17a7dac464e1ec40db357194000f5745cdf2f3a8
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249213"
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-c"></a><span data-ttu-id="013ac-102">Bir öğenin değeri (LINQ - XML) (C#) nasıl alınır?</span><span class="sxs-lookup"><span data-stu-id="013ac-102">How to retrieve the value of an element (LINQ to XML) (C#)</span></span>
<span data-ttu-id="013ac-103">Bu konu, öğelerin değerini nasıl elde edilebildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="013ac-103">This topic shows how to get the value of elements.</span></span> <span data-ttu-id="013ac-104">Bunu yapmanın iki ana yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="013ac-104">There are two main ways to do this.</span></span> <span data-ttu-id="013ac-105">Bir yolu istenilen <xref:System.Xml.Linq.XElement> türe <xref:System.Xml.Linq.XAttribute> bir veya bir döküm etmektir.</span><span class="sxs-lookup"><span data-stu-id="013ac-105">One way is to cast an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XAttribute> to the desired type.</span></span> <span data-ttu-id="013ac-106">Açık dönüştürme işleci daha sonra öğenin içeriğini dönüştürür veya belirtilen türe atfeder ve değişkeninize atar.</span><span class="sxs-lookup"><span data-stu-id="013ac-106">The explicit conversion operator then converts the contents of the element or attribute to the specified type and assigns it to your variable.</span></span> <span data-ttu-id="013ac-107">Alternatif olarak, <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> özelliği veya <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> mülkü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="013ac-107">Alternatively, you can use the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property or the <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="013ac-108">C # ile, ancak, döküm genellikle daha iyi bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="013ac-108">With C#, however, casting is generally the better approach.</span></span> <span data-ttu-id="013ac-109">Öğeyi veya özniteliği boşalabilir bir değer türüne atarsanız, var olabilecek veya var olmayan bir öğenin (veya öznitelik) değerini alırken kod yazmak daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="013ac-109">If you cast the element or attribute to a nullable value type, the code is simpler to write when retrieving the value of an element (or attribute) that might or might not exist.</span></span> <span data-ttu-id="013ac-110">Bu konudaki son örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="013ac-110">The last example in this topic demonstrates this.</span></span> <span data-ttu-id="013ac-111">Ancak, bir öğenin içeriğini, özellik aracılığıyla olduğu <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> gibi, döküm yoluyla ayarlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="013ac-111">However, you cannot set the contents of an element through casting, as you can through <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="013ac-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="013ac-112">Example</span></span>  
 <span data-ttu-id="013ac-113">Bir öğenin değerini almak için, <xref:System.Xml.Linq.XElement> nesneyi istediğiniz türe dökmeniz yalnızca</span><span class="sxs-lookup"><span data-stu-id="013ac-113">To retrieve the value of an element, you just cast the <xref:System.Xml.Linq.XElement> object to your desired type.</span></span> <span data-ttu-id="013ac-114">Bir öğeyi her zaman aşağıdaki gibi bir dize atabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="013ac-114">You can always cast an element to a string, as follows:</span></span>  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (string)e);  
```  
  
 <span data-ttu-id="013ac-115">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="013ac-115">This example produces the following output:</span></span>  
  
```output  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a><span data-ttu-id="013ac-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="013ac-116">Example</span></span>  
 <span data-ttu-id="013ac-117">Ayrıca, dize dışındaki türlere öğeleri de atabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="013ac-117">You can also cast elements to types other than string.</span></span> <span data-ttu-id="013ac-118">Örneğin, bir arameger içeren bir öğeniz varsa, aşağıdaki `int`kodda gösterildiği gibi bu öğeyi şu şekilde atabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="013ac-118">For example, if you have an element that contains an integer, you can cast it to `int`, as shown in the following code:</span></span>  
  
```csharp  
XElement e = new XElement("Age", "44");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (int)e);  
```  
  
 <span data-ttu-id="013ac-119">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="013ac-119">This example produces the following output:</span></span>  
  
```output  
<Age>44</Age>  
Value of e:44  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="013ac-120">aşağıdaki veri türleri için açık `string`döküm `bool` `bool?`operatörleri `int` `int?`sağlar: `uint?` `long`, `long?` `ulong`, `ulong?` `float`, `float?` `uint` `double`, `double?` `decimal`, `decimal?` `DateTime` `DateTime?` `TimeSpan` `TimeSpan?`, , `GUID`, `GUID?`, , , , , , , , , , , ,</span><span class="sxs-lookup"><span data-stu-id="013ac-120">provides explicit cast operators for the following data types: `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="013ac-121">nesneler için <xref:System.Xml.Linq.XAttribute> aynı döküm işleçleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="013ac-121">provides the same cast operators for <xref:System.Xml.Linq.XAttribute> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="013ac-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="013ac-122">Example</span></span>  
 <span data-ttu-id="013ac-123">Bir öğenin <xref:System.Xml.Linq.XElement.Value%2A> içeriğini almak için özelliği kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="013ac-123">You can use the <xref:System.Xml.Linq.XElement.Value%2A> property to retrieve the contents of an element:</span></span>  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + e.Value);  
```  
  
 <span data-ttu-id="013ac-124">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="013ac-124">This example produces the following output:</span></span>  
  
```output  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a><span data-ttu-id="013ac-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="013ac-125">Example</span></span>  
 <span data-ttu-id="013ac-126">Bazen var olduğundan emin olsanız bile bir öğenin değerini almaya çalışırsınız.</span><span class="sxs-lookup"><span data-stu-id="013ac-126">Sometimes you try to retrieve the value of an element even though you are not sure it exists.</span></span> <span data-ttu-id="013ac-127">Bu durumda, döküm öğeyi nullable bir başvuru türüne veya nullable değer türüne atadığınızda, öğe yoksa `null`atanan değişken sadece .</span><span class="sxs-lookup"><span data-stu-id="013ac-127">In this case, when you assign the casted element to a nullable reference type, or nullable value type, if the element does not exist the assigned variable is just set to `null`.</span></span> <span data-ttu-id="013ac-128">Aşağıdaki kod, öğe var olabilir veya olmayabilir, <xref:System.Xml.Linq.XElement.Value%2A> özelliği kullanmak için daha döküm kullanmak daha kolay olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="013ac-128">The following code shows that when the element might or might not exist, it is easier to use casting than to use the <xref:System.Xml.Linq.XElement.Value%2A> property.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child1", "child 1 content"),  
    new XElement("Child2", "2")  
);  
  
// The following assignments show why it is easier to use  
// casting when the element might or might not exist.  
  
string c1 = (string)root.Element("Child1");  
Console.WriteLine("c1:{0}", c1 == null ? "element does not exist" : c1);  
  
int? c2 = (int?)root.Element("Child2");  
Console.WriteLine("c2:{0}", c2 == null ? "element does not exist" : c2.ToString());  
  
string c3 = (string)root.Element("Child3");  
Console.WriteLine("c3:{0}", c3 == null ? "element does not exist" : c3);  
  
int? c4 = (int?)root.Element("Child4");  
Console.WriteLine("c4:{0}", c4 == null ? "element does not exist" : c4.ToString());  
  
Console.WriteLine();  
  
// The following assignments show the required code when using  
// the Value property when the element might or might not exist.  
// Notice that this is more difficult than the casting approach.  
  
XElement e1 = root.Element("Child1");  
string v1;  
if (e1 == null)  
    v1 = null;  
else  
    v1 = e1.Value;  
Console.WriteLine("v1:{0}", v1 == null ? "element does not exist" : v1);  
  
XElement e2 = root.Element("Child2");  
int? v2;  
if (e2 == null)  
    v2 = null;  
else  
    v2 = Int32.Parse(e2.Value);  
Console.WriteLine("v2:{0}", v2 == null ? "element does not exist" : v2.ToString());  
  
XElement e3 = root.Element("Child3");  
string v3;  
if (e3 == null)  
    v3 = null;  
else  
    v3 = e3.Value;  
Console.WriteLine("v3:{0}", v3 == null ? "element does not exist" : v3);  
  
XElement e4 = root.Element("Child4");  
int? v4;  
if (e4 == null)  
    v4 = null;  
else  
    v4 = Int32.Parse(e4.Value);  
Console.WriteLine("v4:{0}", v4 == null ? "element does not exist" : v4.ToString());  
```  
  
 <span data-ttu-id="013ac-129">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="013ac-129">This code produces the following output:</span></span>  
  
```output  
c1:child 1 content  
c2:2  
c3:element does not exist  
c4:element does not exist  
  
v1:child 1 content  
v2:2  
v3:element does not exist  
v4:element does not exist  
```  
  
 <span data-ttu-id="013ac-130">Genel olarak, öğelerin ve özniteliklerin içeriğini almak için döküm kullanırken daha basit kod yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="013ac-130">In general, you can write simpler code when using casting to retrieve the contents of elements and attributes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="013ac-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="013ac-131">See also</span></span>

- [<span data-ttu-id="013ac-132">LINQ - XML Eksenleri (C#)</span><span class="sxs-lookup"><span data-stu-id="013ac-132">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
