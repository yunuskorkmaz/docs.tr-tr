---
title: C# Dilinde XML Ağaçları Oluşturma (LINQ to XML)
ms.date: 08/31/2018
ms.assetid: cc74234a-0bac-4327-9c8c-5a2ead15b595
ms.openlocfilehash: a77171ebbc07e54f6988fb97aff197b4c6d31721
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594625"
---
# <a name="creating-xml-trees-in-c-linq-to-xml"></a><span data-ttu-id="88ac5-102">İçinde C# xml ağaçları oluşturma (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="88ac5-102">Creating XML trees in C# (LINQ to XML)</span></span>
<span data-ttu-id="88ac5-103">Bu bölüm içinde C#xml ağaçları oluşturma hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="88ac5-103">This section provides information about creating XML trees in C#.</span></span>  
  
 <span data-ttu-id="88ac5-104">LINQ sorgularının sonuçlarını bir <xref:System.Xml.Linq.XElement>için içerik olarak kullanma hakkında daha fazla bilgi için bkz. [işlevsel oluşturma (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="88ac5-104">For information about using the results of LINQ queries as the content for an <xref:System.Xml.Linq.XElement>, see [Functional Construction (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md).</span></span>  
  
## <a name="constructing-elements"></a><span data-ttu-id="88ac5-105">Öğeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="88ac5-105">Constructing elements</span></span>
 <span data-ttu-id="88ac5-106"><xref:System.Xml.Linq.XElement> Ve<xref:System.Xml.Linq.XAttribute> oluşturucuların imzaları, öğe veya özniteliğin içeriğini oluşturucuya bağımsız değişken olarak geçirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="88ac5-106">The signatures of the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> constructors let you pass the contents of the element or attribute as arguments to the constructor.</span></span> <span data-ttu-id="88ac5-107">Oluşturuculardan biri değişken sayıda bağımsız değişken kullandığından, herhangi bir sayıda alt öğe geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="88ac5-107">Because one of the constructors takes a variable number of arguments, you can pass any number of child elements.</span></span> <span data-ttu-id="88ac5-108">Kuşkusuz, bu alt öğelerin her biri kendi alt öğelerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="88ac5-108">Of course, each of those child elements can contain their own child elements.</span></span> <span data-ttu-id="88ac5-109">Herhangi bir öğe için istediğiniz sayıda öznitelik ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="88ac5-109">For any element, you can add any number of attributes.</span></span>  
  
 <span data-ttu-id="88ac5-110">(Dahil <xref:System.Xml.Linq.XNode> <xref:System.Xml.Linq.XElement>) veya<xref:System.Xml.Linq.XAttribute> nesneleri eklerken, yeni içeriğin üst öğesi yoksa, nesneler yalnızca XML ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="88ac5-110">When adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="88ac5-111">Yeni içerik zaten üst öğe ise ve başka bir XML ağacının parçasıysa, yeni içerik kopyalanır ve yeni kopyalanan içerik XML ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="88ac5-111">If the new content already is parented, and is part of another XML tree, the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span> <span data-ttu-id="88ac5-112">Bu konudaki son örnekte bu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="88ac5-112">The last example in this topic demonstrates this.</span></span>  
  
 <span data-ttu-id="88ac5-113">`contacts` Oluşturmak<xref:System.Xml.Linq.XElement>için aşağıdaki kodu kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="88ac5-113">To create a `contacts`<xref:System.Xml.Linq.XElement>, you could use the following code:</span></span>  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),   
            new XElement("Phone", "206-555-0144"),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
```  
  
 <span data-ttu-id="88ac5-114">Doğru şekilde girintilense, nesneleri oluşturmak <xref:System.Xml.Linq.XElement> için kullanılan kod, temel alınan XML yapısına benzer.</span><span class="sxs-lookup"><span data-stu-id="88ac5-114">If indented properly, the code to construct <xref:System.Xml.Linq.XElement> objects closely resembles the structure of the underlying XML.</span></span>  
  
## <a name="xelement-constructors"></a><span data-ttu-id="88ac5-115">XElement oluşturucuları</span><span class="sxs-lookup"><span data-stu-id="88ac5-115">XElement constructors</span></span>  
 <span data-ttu-id="88ac5-116"><xref:System.Xml.Linq.XElement> Sınıfı, işlevsel oluşturma için aşağıdaki oluşturucuları kullanır.</span><span class="sxs-lookup"><span data-stu-id="88ac5-116">The <xref:System.Xml.Linq.XElement> class uses the following constructors for functional construction.</span></span> <span data-ttu-id="88ac5-117">İçin <xref:System.Xml.Linq.XElement>başka bazı oluşturucular olduğunu, ancak işlevsel oluşturma için kullanıldıklarından, burada listelenmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="88ac5-117">Note that there are some other constructors for <xref:System.Xml.Linq.XElement>, but because they are not used for functional construction they are not listed here.</span></span>  
  
|<span data-ttu-id="88ac5-118">Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="88ac5-118">Constructor</span></span>|<span data-ttu-id="88ac5-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="88ac5-119">Description</span></span>|  
|-----------------|-----------------|  
|`XElement(XName name, object content)`|<span data-ttu-id="88ac5-120"><xref:System.Xml.Linq.XElement>Oluşturur.</span><span class="sxs-lookup"><span data-stu-id="88ac5-120">Creates an <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="88ac5-121">`name` Parametresi, öğesinin adını belirtir; `content` öğenin içeriğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="88ac5-121">The `name` parameter specifies the name of the element; `content` specifies the content of the element.</span></span>|  
|`XElement(XName name)`|<span data-ttu-id="88ac5-122">Başlatıldıktan sonra <xref:System.Xml.Linq.XElement> belirtilen ada sahip bir oluşturur. <xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="88ac5-122">Creates an <xref:System.Xml.Linq.XElement> with its <xref:System.Xml.Linq.XName> initialized to the specified name.</span></span>|  
|`XElement(XName name, params object[] content)`|<span data-ttu-id="88ac5-123">Başlatıldıktan sonra <xref:System.Xml.Linq.XElement> belirtilen ada sahip bir oluşturur. <xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="88ac5-123">Creates an <xref:System.Xml.Linq.XElement> with its <xref:System.Xml.Linq.XName> initialized to the specified name.</span></span> <span data-ttu-id="88ac5-124">Öznitelikler ve/veya alt öğeleri parametre listesinin içeriğinden oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="88ac5-124">The attributes and/or child elements are created from the contents of the parameter list.</span></span>|  
  
 <span data-ttu-id="88ac5-125">`content` Parametresi son derece esnektir.</span><span class="sxs-lookup"><span data-stu-id="88ac5-125">The `content` parameter is extremely flexible.</span></span> <span data-ttu-id="88ac5-126">Geçerli bir <xref:System.Xml.Linq.XElement>alt öğesi olan herhangi bir nesne türünü destekler.</span><span class="sxs-lookup"><span data-stu-id="88ac5-126">It supports any type of object that is a valid child of an <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="88ac5-127">Bu parametreye geçirilen farklı nesne türleri için aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="88ac5-127">The following rules apply to different types of objects passed in this parameter:</span></span>  
  
- <span data-ttu-id="88ac5-128">Metin içeriği olarak bir dize eklenir.</span><span class="sxs-lookup"><span data-stu-id="88ac5-128">A string is added as text content.</span></span>  
  
- <span data-ttu-id="88ac5-129">Bir <xref:System.Xml.Linq.XElement> alt öğesi olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="88ac5-129">An <xref:System.Xml.Linq.XElement> is added as a child element.</span></span>  
  
- <span data-ttu-id="88ac5-130">Bir <xref:System.Xml.Linq.XAttribute> öznitelik olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="88ac5-130">An <xref:System.Xml.Linq.XAttribute> is added as an attribute.</span></span>  
  
- <span data-ttu-id="88ac5-131"><xref:System.Xml.Linq.XProcessingInstruction>, Veyaalt<xref:System.Xml.Linq.XText>içerikolarakeklenir. <xref:System.Xml.Linq.XComment></span><span class="sxs-lookup"><span data-stu-id="88ac5-131">An <xref:System.Xml.Linq.XProcessingInstruction>, <xref:System.Xml.Linq.XComment>, or <xref:System.Xml.Linq.XText> is added as child content.</span></span>  
  
- <span data-ttu-id="88ac5-132">Bir <xref:System.Collections.IEnumerable> numaralandırılır ve bu kurallar sonuçlara özyinelemeli olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="88ac5-132">An <xref:System.Collections.IEnumerable> is enumerated, and these rules are applied recursively to the results.</span></span>  
  
- <span data-ttu-id="88ac5-133">Diğer herhangi bir tür için, `ToString` metodu çağrılır ve sonuç metin içeriği olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="88ac5-133">For any other type, its `ToString` method is called and the result is added as text content.</span></span>  
  
### <a name="creating-an-xelement-with-content"></a><span data-ttu-id="88ac5-134">İçerikle XElement oluşturma</span><span class="sxs-lookup"><span data-stu-id="88ac5-134">Creating an XElement with content</span></span>  
 <span data-ttu-id="88ac5-135">Tek bir yöntem çağrısıyla <xref:System.Xml.Linq.XElement> basit içerik içeren bir oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="88ac5-135">You can create an <xref:System.Xml.Linq.XElement> that contains simple content with a single method call.</span></span> <span data-ttu-id="88ac5-136">Bunu yapmak için, içeriği ikinci parametre olarak aşağıdaki gibi belirtin:</span><span class="sxs-lookup"><span data-stu-id="88ac5-136">To do this, specify the content as the second parameter, as follows:</span></span>  
  
```csharp  
XElement n = new XElement("Customer", "Adventure Works");  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="88ac5-137">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="88ac5-137">This example produces the following output:</span></span>  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
 <span data-ttu-id="88ac5-138">Herhangi bir nesne türünü içerik olarak geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="88ac5-138">You can pass any type of object as the content.</span></span> <span data-ttu-id="88ac5-139">Örneğin, aşağıdaki kod, içerik olarak kayan noktalı sayı içeren bir öğe oluşturur:</span><span class="sxs-lookup"><span data-stu-id="88ac5-139">For example, the following code creates an element that contains a floating point number as content:</span></span>  
  
```csharp  
XElement n = new XElement("Cost", 324.50);  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="88ac5-140">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="88ac5-140">This example produces the following output:</span></span>  
  
```xml  
<Cost>324.5</Cost>  
```  
  
 <span data-ttu-id="88ac5-141">Kayan nokta numarası paketlenmelidir ve oluşturucuya geçirilir.</span><span class="sxs-lookup"><span data-stu-id="88ac5-141">The floating point number is boxed and passed in to the constructor.</span></span> <span data-ttu-id="88ac5-142">Kutulanmış sayı bir dizeye dönüştürülür ve öğesinin içeriği olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="88ac5-142">The boxed number is converted to a string and used as the content of the element.</span></span>  
  
### <a name="creating-an-xelement-with-a-child-element"></a><span data-ttu-id="88ac5-143">Alt öğesiyle XElement oluşturma</span><span class="sxs-lookup"><span data-stu-id="88ac5-143">Creating an XElement with a child element</span></span>  
 <span data-ttu-id="88ac5-144">İçerik bağımsız değişkeni için <xref:System.Xml.Linq.XElement> sınıfının bir örneğini geçirirseniz, Oluşturucu bir alt öğesi olan bir öğesi oluşturur:</span><span class="sxs-lookup"><span data-stu-id="88ac5-144">If you pass an instance of the <xref:System.Xml.Linq.XElement> class for the content argument, the constructor creates an element with a child element:</span></span>  
  
```csharp  
XElement shippingUnit = new XElement("ShippingUnit",  
    new XElement("Cost", 324.50)  
);  
Console.WriteLine(shippingUnit);  
```  
  
 <span data-ttu-id="88ac5-145">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="88ac5-145">This example produces the following output:</span></span>  
  
```xml  
<ShippingUnit>  
  <Cost>324.5</Cost>  
</ShippingUnit>  
```  
  
### <a name="creating-an-xelement-with-multiple-child-elements"></a><span data-ttu-id="88ac5-146">Birden çok alt öğe içeren bir XElement oluşturma</span><span class="sxs-lookup"><span data-stu-id="88ac5-146">Creating an XElement with multiple child elements</span></span>  
 <span data-ttu-id="88ac5-147">İçerik için bir dizi <xref:System.Xml.Linq.XElement> nesne geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="88ac5-147">You can pass in a number of <xref:System.Xml.Linq.XElement> objects for the content.</span></span> <span data-ttu-id="88ac5-148"><xref:System.Xml.Linq.XElement> Nesnelerin her biri bir alt öğe olarak dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="88ac5-148">Each of the <xref:System.Xml.Linq.XElement> objects is included as a child element.</span></span>  
  
```csharp  
XElement address = new XElement("Address",  
    new XElement("Street1", "123 Main St"),  
    new XElement("City", "Mercer Island"),  
    new XElement("State", "WA"),  
    new XElement("Postal", "68042")  
);  
Console.WriteLine(address);  
```  
  
 <span data-ttu-id="88ac5-149">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="88ac5-149">This example produces the following output:</span></span>  
  
```xml  
<Address>  
  <Street1>123 Main St</Street1>  
  <City>Mercer Island</City>  
  <State>WA</State>  
  <Postal>68042</Postal>  
</Address>  
```  
  
 <span data-ttu-id="88ac5-150">Yukarıdaki örneği genişleterek, bir XML ağacının tamamını aşağıdaki gibi oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="88ac5-150">By extending the above example, you can create an entire XML tree, as follows:</span></span>  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),                                                   
            new XElement("Phone", "206-555-0144"),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
Console.WriteLine(contacts);  
```  
  
 <span data-ttu-id="88ac5-151">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="88ac5-151">This example produces the following output:</span></span>  
  
```xml  
<Contacts>  
  <Contact>  
    <Name>Patrick Hines</Name>  
    <Phone>206-555-0144</Phone>  
    <Address>  
      <Street1>123 Main St</Street1>  
      <City>Mercer Island</City>  
      <State>WA</State>  
      <Postal>68042</Postal>  
    </Address>  
  </Contact>  
</Contacts>  
```  

### <a name="creating-an-xelement-with-an-xattribute"></a><span data-ttu-id="88ac5-152">XAttribute ile XElement oluşturma</span><span class="sxs-lookup"><span data-stu-id="88ac5-152">Creating an XElement with an XAttribute</span></span>
 <span data-ttu-id="88ac5-153">İçerik bağımsız değişkeni için <xref:System.Xml.Linq.XAttribute> sınıfının bir örneğini geçirirseniz, Oluşturucu bir özniteliği olan bir öğesi oluşturur:</span><span class="sxs-lookup"><span data-stu-id="88ac5-153">If you pass an instance of the <xref:System.Xml.Linq.XAttribute> class for the content argument, the constructor creates an element with an attribute:</span></span>

```csharp  
XElement phone = new XElement("Phone",  
    new XAttribute("Type", "Home"),  
    "555-555-5555");  
Console.WriteLine(phone);  
```  
  
 <span data-ttu-id="88ac5-154">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="88ac5-154">This example produces the following output:</span></span>  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>
```   

### <a name="creating-an-empty-element"></a><span data-ttu-id="88ac5-155">Boş bir öğe oluşturma</span><span class="sxs-lookup"><span data-stu-id="88ac5-155">Creating an empty element</span></span>  
 <span data-ttu-id="88ac5-156">Boş <xref:System.Xml.Linq.XElement>bir oluşturmak için, oluşturucuya herhangi bir içerik geçirmeyin.</span><span class="sxs-lookup"><span data-stu-id="88ac5-156">To create an empty <xref:System.Xml.Linq.XElement>, you do not pass any content to the constructor.</span></span> <span data-ttu-id="88ac5-157">Aşağıdaki örnek boş bir öğe oluşturur:</span><span class="sxs-lookup"><span data-stu-id="88ac5-157">The following example creates an empty element:</span></span>  
  
```csharp  
XElement n = new XElement("Customer");  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="88ac5-158">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="88ac5-158">This example produces the following output:</span></span>  
  
```xml  
<Customer />  
```  
  
### <a name="attaching-vs-cloning"></a><span data-ttu-id="88ac5-159">Ekleme ile kopyalama</span><span class="sxs-lookup"><span data-stu-id="88ac5-159">Attaching vs. cloning</span></span>  
 <span data-ttu-id="88ac5-160">Daha önce belirtildiği gibi, ( <xref:System.Xml.Linq.XNode> dahil) <xref:System.Xml.Linq.XElement>veya <xref:System.Xml.Linq.XAttribute> nesneleri eklerken (dahil), yeni içeriğin üst öğesi yoksa, nesneler yalnızca XML ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="88ac5-160">As mentioned previously, when adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="88ac5-161">Yeni içerik zaten üst öğe ise ve başka bir XML ağacının parçasıysa, yeni içerik kopyalanır ve yeni kopyalanan içerik XML ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="88ac5-161">If the new content already is parented and is part of another XML tree, the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span>  

<span data-ttu-id="88ac5-162">Aşağıdaki örnek, bir ağaca bir üst öğeye sahip bir öğe eklediğinizde ve bir ağaca üst öğesi olmayan bir öğe eklediğinizde davranışını gösterir.</span><span class="sxs-lookup"><span data-stu-id="88ac5-162">The following example demonstrates the behavior when you add a parented element to a tree, and when you add an element with no parent to a tree.</span></span>

```csharp  
// Create a tree with a child element.  
XElement xmlTree1 = new XElement("Root",  
    new XElement("Child1", 1)  
);  
  
// Create an element that is not parented.  
XElement child2 = new XElement("Child2", 2);  
  
// Create a tree and add Child1 and Child2 to it.  
XElement xmlTree2 = new XElement("Root",  
    xmlTree1.Element("Child1"),  
    child2  
);  
  
// Compare Child1 identity.  
Console.WriteLine("Child1 was {0}",  
    xmlTree1.Element("Child1") == xmlTree2.Element("Child1") ?  
    "attached" : "cloned");  
  
// Compare Child2 identity.  
Console.WriteLine("Child2 was {0}",  
    child2 == xmlTree2.Element("Child2") ?  
    "attached" : "cloned");  

// The example displays the following output:  
//    Child1 was cloned  
//    Child2 was attached  
```

## <a name="see-also"></a><span data-ttu-id="88ac5-163">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88ac5-163">See also</span></span>

- [<span data-ttu-id="88ac5-164">XML ağaçları oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="88ac5-164">Creating XML Trees (C#)</span></span>](./linq-to-xml-overview.md)
