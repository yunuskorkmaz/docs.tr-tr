---
title: Bir öğenin değerini alma (LINQ to XML) (C#)
description: Öğelerin değerini alma hakkında bilgi edinin. Bkz. dize çevrim, tamsayı atama ve değer özelliği kullanma örnekleri.
ms.date: 07/20/2015
ms.assetid: 4228c007-07c9-4cf2-a45b-e7074c109581
ms.openlocfilehash: eb750927d74c3068d7ab06caba9835110bd77a09
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301547"
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-c"></a><span data-ttu-id="0e04b-104">Bir öğenin değerini alma (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="0e04b-104">How to retrieve the value of an element (LINQ to XML) (C#)</span></span>

<span data-ttu-id="0e04b-105">Bu makale, öğelerin değerinin nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0e04b-105">This article shows how to get the value of elements.</span></span> <span data-ttu-id="0e04b-106">Değeri almanın iki ana yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="0e04b-106">There are two main ways to get the value:</span></span>

- <span data-ttu-id="0e04b-107">Bir <xref:System.Xml.Linq.XElement> veya öğesini <xref:System.Xml.Linq.XAttribute> istenen türe atayın.</span><span class="sxs-lookup"><span data-stu-id="0e04b-107">Cast an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XAttribute> to the desired type.</span></span> <span data-ttu-id="0e04b-108">Daha sonra açık dönüştürme işleci, öğe veya özniteliğin içeriğini belirtilen türe dönüştürür ve değişkenine atar.</span><span class="sxs-lookup"><span data-stu-id="0e04b-108">The explicit conversion operator then converts the contents of the element or attribute to the specified type and assigns it to your variable.</span></span>

- <span data-ttu-id="0e04b-109"><xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>Veya özelliklerini kullanın <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="0e04b-109">Use the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> or <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> properties.</span></span> <span data-ttu-id="0e04b-110">Bu özellikleri kullanarak da değeri ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e04b-110">You can also set the value using these properties.</span></span>

<span data-ttu-id="0e04b-111">C# ile, atama genellikle daha iyi bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="0e04b-111">With C#, casting is generally the better approach.</span></span> <span data-ttu-id="0e04b-112">Öğesi veya özniteliğini null atanabilir bir değer türüne ayarlarsanız, kod, var olabilen veya varolmayan bir öğenin (veya özniteliğin) değeri alınırken yazmak daha basittir.</span><span class="sxs-lookup"><span data-stu-id="0e04b-112">If you cast the element or attribute to a nullable value type, the code is simpler to write when retrieving the value of an element (or attribute) that might or might not exist.</span></span> <span data-ttu-id="0e04b-113">Bu makaledeki [Son örnekte](#element-might-not-exist-example) , öğenin mevcut olmadığı durumlarda atama daha basit olduğu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0e04b-113">The [last example](#element-might-not-exist-example) in this article demonstrates that casting is simpler in the case where the element might not exist.</span></span> <span data-ttu-id="0e04b-114">Ancak, özelliğini kullanarak bir öğenin içeriğini atama aracılığıyla ayarlayamazsınız <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="0e04b-114">However, you cannot set the contents of an element through casting, as you can through <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="string-cast-example"></a><span data-ttu-id="0e04b-115">Dize atama örneği</span><span class="sxs-lookup"><span data-stu-id="0e04b-115">String cast example</span></span>  
 <span data-ttu-id="0e04b-116">Bir öğenin değerini almak için, <xref:System.Xml.Linq.XElement> nesneyi istediğiniz türe atayın.</span><span class="sxs-lookup"><span data-stu-id="0e04b-116">To retrieve the value of an element, cast the <xref:System.Xml.Linq.XElement> object to your desired type.</span></span> <span data-ttu-id="0e04b-117">Bir öğeyi şu şekilde bir dizeye çevirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0e04b-117">You can cast an element to a string, as follows:</span></span>  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (string)e);  
```  
  
 <span data-ttu-id="0e04b-118">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="0e04b-118">This example produces the following output:</span></span>  
  
```output  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="integer-cast-example"></a><span data-ttu-id="0e04b-119">Tamsayı atama örneği</span><span class="sxs-lookup"><span data-stu-id="0e04b-119">Integer cast example</span></span>  
 <span data-ttu-id="0e04b-120">Ayrıca, öğeleri dize dışındaki türlere de çevirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e04b-120">You can also cast elements to types other than string.</span></span> <span data-ttu-id="0e04b-121">Örneğin, bir tamsayı içeren bir öğeye sahipseniz, `int` aşağıdaki kodda gösterildiği gibi, öğesini öğesine çevirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0e04b-121">For example, if you have an element that contains an integer, you can cast it to `int`, as shown in the following code:</span></span>  
  
```csharp  
XElement e = new XElement("Age", "44");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (int)e);  
```  
  
 <span data-ttu-id="0e04b-122">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="0e04b-122">This example produces the following output:</span></span>  
  
```output  
<Age>44</Age>  
Value of e:44  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="0e04b-123">Şu veri türleri için açık atama işleçleri sağlar: `string` , `bool` ,, `bool?` `int` , `int?` , `uint` , `uint?` , `long` , `long?` , `ulong` , `ulong?` , `float` , `float?` , `double` , `double?` , `decimal` , `decimal?` , `DateTime` , `DateTime?` `TimeSpan` `TimeSpan?` `GUID` `GUID?` ,,,,,,,,,,,, ve</span><span class="sxs-lookup"><span data-stu-id="0e04b-123">provides explicit cast operators for the following data types: `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="0e04b-124">nesneler için aynı atama işleçlerini sağlar <xref:System.Xml.Linq.XAttribute> .</span><span class="sxs-lookup"><span data-stu-id="0e04b-124">provides the same cast operators for <xref:System.Xml.Linq.XAttribute> objects.</span></span>  
  
## <a name="value-property-example"></a><span data-ttu-id="0e04b-125">Value özelliği örneği</span><span class="sxs-lookup"><span data-stu-id="0e04b-125">Value property example</span></span>  
 <span data-ttu-id="0e04b-126"><xref:System.Xml.Linq.XElement.Value%2A>Bir öğenin içeriğini almak için özelliğini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0e04b-126">You can use the <xref:System.Xml.Linq.XElement.Value%2A> property to retrieve the contents of an element:</span></span>  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + e.Value);  
```  
  
 <span data-ttu-id="0e04b-127">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="0e04b-127">This example produces the following output:</span></span>  
  
```output  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="element-might-not-exist-example"></a><span data-ttu-id="0e04b-128">Öğe mevcut olmayabilir örnek</span><span class="sxs-lookup"><span data-stu-id="0e04b-128">Element might not exist example</span></span>
 <span data-ttu-id="0e04b-129">Bazen, var olup olmadığından emin olmadığınız halde bir öğenin değerini almaya çalışırsınız.</span><span class="sxs-lookup"><span data-stu-id="0e04b-129">Sometimes you try to retrieve the value of an element even though you're not sure if it exists.</span></span> <span data-ttu-id="0e04b-130">Bu durumda, başvurulan öğeyi null olabilen bir başvuru türüne veya null yapılabilir değer türüne atadığınızda, öğe yoksa atanan değişken olarak ayarlanır `null` .</span><span class="sxs-lookup"><span data-stu-id="0e04b-130">In this case, when you assign the casted element to a nullable reference type or nullable value type, if the element does not exist, the assigned variable is set to `null`.</span></span> <span data-ttu-id="0e04b-131">Aşağıdaki kod, öğe ne zaman olabileceği veya mevcut olmadığında, özelliği kullanmak için, atama kullanmanın daha kolay olduğunu gösterir <xref:System.Xml.Linq.XElement.Value%2A> .</span><span class="sxs-lookup"><span data-stu-id="0e04b-131">The following code shows that when the element might or might not exist, it is easier to use casting than to use the <xref:System.Xml.Linq.XElement.Value%2A> property.</span></span>  
  
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
  
 <span data-ttu-id="0e04b-132">Bu kod şu çıkışı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="0e04b-132">This code produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="0e04b-133">Genel olarak, öğelerin ve özniteliklerin içeriğini almak için atama kullanırken daha basit bir kod yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e04b-133">In general, you can write simpler code when using casting to retrieve the contents of elements and attributes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e04b-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e04b-134">See also</span></span>

- [<span data-ttu-id="0e04b-135">LINQ to XML eksenleri (C#)</span><span class="sxs-lookup"><span data-stu-id="0e04b-135">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
