---
title: 'Nasıl yapılır: bir öğe (LINQ to XML) değerini alma (C#)'
ms.date: 07/20/2015
ms.assetid: 4228c007-07c9-4cf2-a45b-e7074c109581
ms.openlocfilehash: 7537c111e7d869f8a3e2458706864960820f9764
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45520353"
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-c"></a><span data-ttu-id="3d56c-102">Nasıl yapılır: bir öğe (LINQ to XML) değerini alma (C#)</span><span class="sxs-lookup"><span data-stu-id="3d56c-102">How to: Retrieve the Value of an Element (LINQ to XML) (C#)</span></span>
<span data-ttu-id="3d56c-103">Bu konuda, öğelerin değerini alma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3d56c-103">This topic shows how to get the value of elements.</span></span> <span data-ttu-id="3d56c-104">Bunu yapmak için iki ana yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="3d56c-104">There are two main ways to do this.</span></span> <span data-ttu-id="3d56c-105">Dönüştürülecek bir yolu olan bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XAttribute> istenen türe.</span><span class="sxs-lookup"><span data-stu-id="3d56c-105">One way is to cast an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XAttribute> to the desired type.</span></span> <span data-ttu-id="3d56c-106">Açık dönüştürme işleci öğe veya öznitelik içeriğini belirtilen türe dönüştürür ve değişkeninize atar.</span><span class="sxs-lookup"><span data-stu-id="3d56c-106">The explicit conversion operator then converts the contents of the element or attribute to the specified type and assigns it to your variable.</span></span> <span data-ttu-id="3d56c-107">Alternatif olarak, <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> özelliği veya <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="3d56c-107">Alternatively, you can use the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property or the <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="3d56c-108">C# ile ancak atama genellikle daha iyi bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="3d56c-108">With C#, however, casting is generally the better approach.</span></span> <span data-ttu-id="3d56c-109">Cast öğesi veya özniteliği için boş değer atanabilir bir tür, ne zaman yazmak daha basit kodudur var olmayabilir veya değeri bir öğenin (veya öznitelik) alma.</span><span class="sxs-lookup"><span data-stu-id="3d56c-109">If you cast the element or attribute to a nullable type, the code is simpler to write when retrieving the value of an element (or attribute) that might or might not exist.</span></span> <span data-ttu-id="3d56c-110">Bu konu Son örnekte bu gösterir.</span><span class="sxs-lookup"><span data-stu-id="3d56c-110">The last example in this topic demonstrates this.</span></span> <span data-ttu-id="3d56c-111">Ancak aracılığıyla mümkün olduğunca atama, öğenin içeriğini ayarlanamıyor <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="3d56c-111">However, you cannot set the contents of an element through casting, as you can through <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d56c-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="3d56c-112">Example</span></span>  
 <span data-ttu-id="3d56c-113">Bir öğenin değerini almak için yalnızca cast <xref:System.Xml.Linq.XElement> istenen türünüz için nesne.</span><span class="sxs-lookup"><span data-stu-id="3d56c-113">To retrieve the value of an element, you just cast the <xref:System.Xml.Linq.XElement> object to your desired type.</span></span> <span data-ttu-id="3d56c-114">Her zaman bir dize için bir öğe gibi çevirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3d56c-114">You can always cast an element to a string, as follows:</span></span>  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (string)e);  
```  
  
 <span data-ttu-id="3d56c-115">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="3d56c-115">This example produces the following output:</span></span>  
  
```  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a><span data-ttu-id="3d56c-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="3d56c-116">Example</span></span>  
 <span data-ttu-id="3d56c-117">Ayrıca dize dışındaki türler için öğeleri çevirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3d56c-117">You can also cast elements to types other than string.</span></span> <span data-ttu-id="3d56c-118">Bir tamsayı içeren bir öğe varsa, örneğin, kendisine çevirebilirsiniz `int`aşağıdaki kodda gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="3d56c-118">For example, if you have an element that contains an integer, you can cast it to `int`, as shown in the following code:</span></span>  
  
```csharp  
XElement e = new XElement("Age", "44");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (int)e);  
```  
  
 <span data-ttu-id="3d56c-119">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="3d56c-119">This example produces the following output:</span></span>  
  
```  
<Age>44</Age>  
Value of e:44  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="3d56c-120"> Aşağıdaki veri türleri için açık tür dönüştürme işleçleri sağlar: `string\`, `bool\`, `bool?\`, `int\`, `int?\`, `uint\`, `uint?\`, `long\`, `long?\`, `ulong\`, `ulong?` , `float\`, `float?\`, `double\`, `double?\`, `decimal\`, `decimal?\`, `DateTime\`, `DateTime?\`, `TimeSpan\`, `TimeSpan?\`, `GUID\`, ve `GUID?\`.</span><span class="sxs-lookup"><span data-stu-id="3d56c-120"> provides explicit cast operators for the following data types: `string\`, `bool\`, `bool?\`, `int\`, `int?\`, `uint\`, `uint?\`, `long\`, `long?\`, `ulong\`, `ulong?\`, `float\`, `float?\`, `double\`, `double?\`, `decimal\`, `decimal?\`, `DateTime\`, `DateTime?\`, `TimeSpan\`, `TimeSpan?\`, `GUID\`, and `GUID?\`.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="3d56c-121"> aynı atama işleçleri sağlar <xref:System.Xml.Linq.XAttribute> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="3d56c-121"> provides the same cast operators for <xref:System.Xml.Linq.XAttribute> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d56c-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="3d56c-122">Example</span></span>  
 <span data-ttu-id="3d56c-123">Kullanabileceğiniz <xref:System.Xml.Linq.XElement.Value%2A> özelliği, bir öğenin içeriğini almak için:</span><span class="sxs-lookup"><span data-stu-id="3d56c-123">You can use the <xref:System.Xml.Linq.XElement.Value%2A> property to retrieve the contents of an element:</span></span>  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");   
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + e.Value);  
```  
  
 <span data-ttu-id="3d56c-124">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="3d56c-124">This example produces the following output:</span></span>  
  
```  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a><span data-ttu-id="3d56c-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="3d56c-125">Example</span></span>  
 <span data-ttu-id="3d56c-126">Bazen varolduğundan emin değilseniz olsa bile, bir öğenin değeri alınmaya çalışıldı.</span><span class="sxs-lookup"><span data-stu-id="3d56c-126">Sometimes you try to retrieve the value of an element even though you are not sure it exists.</span></span> <span data-ttu-id="3d56c-127">Bu durumda, atadığınızda Integer öğesi null yapılabilir bir tür (ya da `string` veya boş değer atanabilir türleri [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]), öğe atanmış mevcut değilse değişkeni ayarlamanız yeterlidir `null`.</span><span class="sxs-lookup"><span data-stu-id="3d56c-127">In this case, when you assign the casted element to a nullable type (either `string` or one of the nullable types in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]), if the element does not exist the assigned variable is just set to `null`.</span></span> <span data-ttu-id="3d56c-128">Aşağıdaki kodu öğesi olabilir ya da mevcut, atama kullanımı çok daha kolay olduğunu gösteriyor <xref:System.Xml.Linq.XElement.Value%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="3d56c-128">The following code shows that when the element might or might not exist, it is easier to use casting than to use the <xref:System.Xml.Linq.XElement.Value%2A> property.</span></span>  
  
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
  
 <span data-ttu-id="3d56c-129">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="3d56c-129">This code produces the following output:</span></span>  
  
```  
c1:child 1 content  
c2:2  
c3:element does not exist  
c4:element does not exist  
  
v1:child 1 content  
v2:2  
v3:element does not exist  
v4:element does not exist  
```  
  
 <span data-ttu-id="3d56c-130">Genel olarak, öğeleri ve özniteliklerinin içeriğini almak için atama kullanırken daha basit bir kod yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3d56c-130">In general, you can write simpler code when using casting to retrieve the contents of elements and attributes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d56c-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3d56c-131">See Also</span></span>

- [<span data-ttu-id="3d56c-132">LINQ to XML eksenleri (C#)</span><span class="sxs-lookup"><span data-stu-id="3d56c-132">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
