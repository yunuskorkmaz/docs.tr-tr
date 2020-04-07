---
title: Bir öğenin değeri (LINQ - XML) (C#) nasıl alınır?
ms.date: 07/20/2015
ms.assetid: 4228c007-07c9-4cf2-a45b-e7074c109581
ms.openlocfilehash: c4bb78e937fe0de08242923cdd7cd638abf571c7
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805824"
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-c"></a><span data-ttu-id="94fe2-102">Bir öğenin değeri (LINQ - XML) (C#) nasıl alınır?</span><span class="sxs-lookup"><span data-stu-id="94fe2-102">How to retrieve the value of an element (LINQ to XML) (C#)</span></span>

<span data-ttu-id="94fe2-103">Bu makalede, öğelerin değerini almak için nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="94fe2-103">This article shows how to get the value of elements.</span></span> <span data-ttu-id="94fe2-104">Değeri elde etmenin iki ana yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="94fe2-104">There are two main ways to get the value:</span></span>

- <span data-ttu-id="94fe2-105">Bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XAttribute> bir istenilen türe döküm.</span><span class="sxs-lookup"><span data-stu-id="94fe2-105">Cast an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XAttribute> to the desired type.</span></span> <span data-ttu-id="94fe2-106">Açık dönüştürme işleci daha sonra öğenin içeriğini dönüştürür veya belirtilen türe atfeder ve değişkeninize atar.</span><span class="sxs-lookup"><span data-stu-id="94fe2-106">The explicit conversion operator then converts the contents of the element or attribute to the specified type and assigns it to your variable.</span></span>

- <span data-ttu-id="94fe2-107">Özellikleri <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> veya <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> özelliklerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="94fe2-107">Use the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> or <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> properties.</span></span> <span data-ttu-id="94fe2-108">Bu özellikleri kullanarak değeri de ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94fe2-108">You can also set the value using these properties.</span></span>

<span data-ttu-id="94fe2-109">C# ile, döküm genellikle daha iyi bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="94fe2-109">With C#, casting is generally the better approach.</span></span> <span data-ttu-id="94fe2-110">Öğeyi veya özniteliği boşalabilir bir değer türüne atarsanız, var olabilecek veya var olmayan bir öğenin (veya öznitelik) değerini alırken kod yazmak daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="94fe2-110">If you cast the element or attribute to a nullable value type, the code is simpler to write when retrieving the value of an element (or attribute) that might or might not exist.</span></span> <span data-ttu-id="94fe2-111">Bu makaledeki [son örnek,](#element-might-not-exist-example) öğenin var olmadığı durumlarda dökümün daha basit olduğunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="94fe2-111">The [last example](#element-might-not-exist-example) in this article demonstrates that casting is simpler in the case where the element might not exist.</span></span> <span data-ttu-id="94fe2-112">Ancak, bir öğenin içeriğini, özellik aracılığıyla olduğu <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> gibi, döküm yoluyla ayarlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="94fe2-112">However, you cannot set the contents of an element through casting, as you can through <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="string-cast-example"></a><span data-ttu-id="94fe2-113">String döküm örneği</span><span class="sxs-lookup"><span data-stu-id="94fe2-113">String cast example</span></span>  
 <span data-ttu-id="94fe2-114">Bir öğenin değerini almak için <xref:System.Xml.Linq.XElement> nesneyi istediğiniz türe atın.</span><span class="sxs-lookup"><span data-stu-id="94fe2-114">To retrieve the value of an element, cast the <xref:System.Xml.Linq.XElement> object to your desired type.</span></span> <span data-ttu-id="94fe2-115">Bir öğeyi aşağıdaki gibi bir dize atabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="94fe2-115">You can cast an element to a string, as follows:</span></span>  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (string)e);  
```  
  
 <span data-ttu-id="94fe2-116">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="94fe2-116">This example produces the following output:</span></span>  
  
```output  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="integer-cast-example"></a><span data-ttu-id="94fe2-117">İnteger döküm örneği</span><span class="sxs-lookup"><span data-stu-id="94fe2-117">Integer cast example</span></span>  
 <span data-ttu-id="94fe2-118">Ayrıca, dize dışındaki türlere öğeleri de atabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94fe2-118">You can also cast elements to types other than string.</span></span> <span data-ttu-id="94fe2-119">Örneğin, bir arameger içeren bir öğeniz varsa, aşağıdaki `int`kodda gösterildiği gibi bu öğeyi şu şekilde atabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="94fe2-119">For example, if you have an element that contains an integer, you can cast it to `int`, as shown in the following code:</span></span>  
  
```csharp  
XElement e = new XElement("Age", "44");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (int)e);  
```  
  
 <span data-ttu-id="94fe2-120">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="94fe2-120">This example produces the following output:</span></span>  
  
```output  
<Age>44</Age>  
Value of e:44  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="94fe2-121">aşağıdaki veri türleri için açık `string`döküm `bool` `bool?`operatörleri `int` `int?`sağlar: `uint?` `long`, `long?` `ulong`, `ulong?` `float`, `float?` `uint` `double`, `double?` `decimal`, `decimal?` `DateTime` `DateTime?` `TimeSpan` `TimeSpan?`, , `GUID`, `GUID?`, , , , , , , , , , , ,</span><span class="sxs-lookup"><span data-stu-id="94fe2-121">provides explicit cast operators for the following data types: `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="94fe2-122">nesneler için <xref:System.Xml.Linq.XAttribute> aynı döküm işleçleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="94fe2-122">provides the same cast operators for <xref:System.Xml.Linq.XAttribute> objects.</span></span>  
  
## <a name="value-property-example"></a><span data-ttu-id="94fe2-123">Değer özelliği örneği</span><span class="sxs-lookup"><span data-stu-id="94fe2-123">Value property example</span></span>  
 <span data-ttu-id="94fe2-124">Bir öğenin <xref:System.Xml.Linq.XElement.Value%2A> içeriğini almak için özelliği kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="94fe2-124">You can use the <xref:System.Xml.Linq.XElement.Value%2A> property to retrieve the contents of an element:</span></span>  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + e.Value);  
```  
  
 <span data-ttu-id="94fe2-125">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="94fe2-125">This example produces the following output:</span></span>  
  
```output  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="element-might-not-exist-example"></a><span data-ttu-id="94fe2-126">Öğe örnek olmayabilir</span><span class="sxs-lookup"><span data-stu-id="94fe2-126">Element might not exist example</span></span>
 <span data-ttu-id="94fe2-127">Bazen var olup olmadığından emin olmamanız aletin değerini almaya çalışırsınız.</span><span class="sxs-lookup"><span data-stu-id="94fe2-127">Sometimes you try to retrieve the value of an element even though you're not sure if it exists.</span></span> <span data-ttu-id="94fe2-128">Bu durumda, döküm öğeyi nullable başvuru türüne veya nullable değer türüne atadığınızda, öğe yoksa, `null`atanan değişken .</span><span class="sxs-lookup"><span data-stu-id="94fe2-128">In this case, when you assign the casted element to a nullable reference type or nullable value type, if the element does not exist, the assigned variable is set to `null`.</span></span> <span data-ttu-id="94fe2-129">Aşağıdaki kod, öğe var olabilir veya olmayabilir, <xref:System.Xml.Linq.XElement.Value%2A> özelliği kullanmak için daha döküm kullanmak daha kolay olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="94fe2-129">The following code shows that when the element might or might not exist, it is easier to use casting than to use the <xref:System.Xml.Linq.XElement.Value%2A> property.</span></span>  
  
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
  
 <span data-ttu-id="94fe2-130">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="94fe2-130">This code produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="94fe2-131">Genel olarak, öğelerin ve özniteliklerin içeriğini almak için döküm kullanırken daha basit kod yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94fe2-131">In general, you can write simpler code when using casting to retrieve the contents of elements and attributes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94fe2-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94fe2-132">See also</span></span>

- [<span data-ttu-id="94fe2-133">LINQ - XML Eksenleri (C#)</span><span class="sxs-lookup"><span data-stu-id="94fe2-133">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
