---
title: C# Dilinde XML Ağaçları Oluşturma (LINQ to XML)
description: C# içinde, öğe oluşturma ve XElement oluşturucuları kullanma dahil XML ağaçları oluşturma hakkında bilgi edinin.
ms.date: 08/31/2018
ms.assetid: cc74234a-0bac-4327-9c8c-5a2ead15b595
ms.openlocfilehash: 3991f461c4c870a64320853ccd1d45026a8a6bf6
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105474"
---
# <a name="creating-xml-trees-in-c-linq-to-xml"></a><span data-ttu-id="56151-103">C# dilinde XML ağaçları oluşturma (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="56151-103">Creating XML trees in C# (LINQ to XML)</span></span>
<span data-ttu-id="56151-104">Bu bölüm C# dilinde XML ağaçları oluşturma hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="56151-104">This section provides information about creating XML trees in C#.</span></span>  
  
 <span data-ttu-id="56151-105">LINQ sorgularının sonuçlarını bir için içerik olarak kullanma hakkında daha fazla bilgi için <xref:System.Xml.Linq.XElement> bkz. [işlevsel oluşturma (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="56151-105">For information about using the results of LINQ queries as the content for an <xref:System.Xml.Linq.XElement>, see [Functional Construction (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md).</span></span>  
  
## <a name="constructing-elements"></a><span data-ttu-id="56151-106">Öğeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="56151-106">Constructing elements</span></span>
 <span data-ttu-id="56151-107">Ve oluşturucuların imzaları, <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute> öğe veya özniteliğin içeriğini oluşturucuya bağımsız değişken olarak geçirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="56151-107">The signatures of the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> constructors let you pass the contents of the element or attribute as arguments to the constructor.</span></span> <span data-ttu-id="56151-108">Oluşturuculardan biri değişken sayıda bağımsız değişken kullandığından, herhangi bir sayıda alt öğe geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56151-108">Because one of the constructors takes a variable number of arguments, you can pass any number of child elements.</span></span> <span data-ttu-id="56151-109">Kuşkusuz, bu alt öğelerin her biri kendi alt öğelerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="56151-109">Of course, each of those child elements can contain their own child elements.</span></span> <span data-ttu-id="56151-110">Herhangi bir öğe için istediğiniz sayıda öznitelik ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56151-110">For any element, you can add any number of attributes.</span></span>  
  
 <span data-ttu-id="56151-111"><xref:System.Xml.Linq.XNode>(Dahil <xref:System.Xml.Linq.XElement> ) veya nesneleri eklerken <xref:System.Xml.Linq.XAttribute> , yeni içeriğin üst öğesi yoksa, nesneler yalnızca XML ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="56151-111">When adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="56151-112">Yeni içerik zaten üst öğe ise ve başka bir XML ağacının parçasıysa, yeni içerik kopyalanır ve yeni kopyalanan içerik XML ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="56151-112">If the new content already is parented, and is part of another XML tree, the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span> <span data-ttu-id="56151-113">Bu konudaki son örnekte bu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="56151-113">The last example in this topic demonstrates this.</span></span>  
  
 <span data-ttu-id="56151-114">Oluşturmak için `contacts` <xref:System.Xml.Linq.XElement> aşağıdaki kodu kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="56151-114">To create a `contacts`<xref:System.Xml.Linq.XElement>, you could use the following code:</span></span>  
  
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
  
 <span data-ttu-id="56151-115">Doğru şekilde girintilense, nesneleri oluşturmak için kullanılan kod, <xref:System.Xml.Linq.XElement> temel ALıNAN XML yapısına benzer.</span><span class="sxs-lookup"><span data-stu-id="56151-115">If indented properly, the code to construct <xref:System.Xml.Linq.XElement> objects closely resembles the structure of the underlying XML.</span></span>  
  
## <a name="xelement-constructors"></a><span data-ttu-id="56151-116">XElement oluşturucuları</span><span class="sxs-lookup"><span data-stu-id="56151-116">XElement constructors</span></span>  
 <span data-ttu-id="56151-117"><xref:System.Xml.Linq.XElement>Sınıfı, işlevsel oluşturma için aşağıdaki oluşturucuları kullanır.</span><span class="sxs-lookup"><span data-stu-id="56151-117">The <xref:System.Xml.Linq.XElement> class uses the following constructors for functional construction.</span></span> <span data-ttu-id="56151-118">İçin başka bazı oluşturucular olduğunu <xref:System.Xml.Linq.XElement> , ancak işlevsel oluşturma için kullanıldıklarından, burada listelenmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="56151-118">Note that there are some other constructors for <xref:System.Xml.Linq.XElement>, but because they are not used for functional construction they are not listed here.</span></span>  
  
|<span data-ttu-id="56151-119">Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="56151-119">Constructor</span></span>|<span data-ttu-id="56151-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="56151-120">Description</span></span>|  
|-----------------|-----------------|  
|`XElement(XName name, object content)`|<span data-ttu-id="56151-121">Oluşturur <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="56151-121">Creates an <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="56151-122">`name`Parametresi, öğesinin adını belirtir; `content` öğesinin içeriğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="56151-122">The `name` parameter specifies the name of the element; `content` specifies the content of the element.</span></span>|  
|`XElement(XName name)`|<span data-ttu-id="56151-123"><xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XName> Başlatıldıktan sonra belirtilen ada sahip bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="56151-123">Creates an <xref:System.Xml.Linq.XElement> with its <xref:System.Xml.Linq.XName> initialized to the specified name.</span></span>|  
|`XElement(XName name, params object[] content)`|<span data-ttu-id="56151-124"><xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XName> Başlatıldıktan sonra belirtilen ada sahip bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="56151-124">Creates an <xref:System.Xml.Linq.XElement> with its <xref:System.Xml.Linq.XName> initialized to the specified name.</span></span> <span data-ttu-id="56151-125">Öznitelikler ve/veya alt öğeleri parametre listesinin içeriğinden oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="56151-125">The attributes and/or child elements are created from the contents of the parameter list.</span></span>|  
  
 <span data-ttu-id="56151-126">`content`Parametresi son derece esnektir.</span><span class="sxs-lookup"><span data-stu-id="56151-126">The `content` parameter is extremely flexible.</span></span> <span data-ttu-id="56151-127">Geçerli bir alt öğesi olan herhangi bir nesne türünü destekler <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="56151-127">It supports any type of object that is a valid child of an <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="56151-128">Bu parametreye geçirilen farklı nesne türleri için aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="56151-128">The following rules apply to different types of objects passed in this parameter:</span></span>  
  
- <span data-ttu-id="56151-129">Metin içeriği olarak bir dize eklenir.</span><span class="sxs-lookup"><span data-stu-id="56151-129">A string is added as text content.</span></span>  
  
- <span data-ttu-id="56151-130">Bir <xref:System.Xml.Linq.XElement> alt öğesi olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="56151-130">An <xref:System.Xml.Linq.XElement> is added as a child element.</span></span>  
  
- <span data-ttu-id="56151-131">Bir <xref:System.Xml.Linq.XAttribute> öznitelik olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="56151-131">An <xref:System.Xml.Linq.XAttribute> is added as an attribute.</span></span>  
  
- <span data-ttu-id="56151-132"><xref:System.Xml.Linq.XProcessingInstruction>, <xref:System.Xml.Linq.XComment> Veya <xref:System.Xml.Linq.XText> alt içerik olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="56151-132">An <xref:System.Xml.Linq.XProcessingInstruction>, <xref:System.Xml.Linq.XComment>, or <xref:System.Xml.Linq.XText> is added as child content.</span></span>  
  
- <span data-ttu-id="56151-133">Bir <xref:System.Collections.IEnumerable> numaralandırılır ve bu kurallar sonuçlara özyinelemeli olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="56151-133">An <xref:System.Collections.IEnumerable> is enumerated, and these rules are applied recursively to the results.</span></span>  
  
- <span data-ttu-id="56151-134">Diğer herhangi bir tür için, `ToString` metodu çağrılır ve sonuç metin içeriği olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="56151-134">For any other type, its `ToString` method is called and the result is added as text content.</span></span>  
  
### <a name="creating-an-xelement-with-content"></a><span data-ttu-id="56151-135">İçerikle XElement oluşturma</span><span class="sxs-lookup"><span data-stu-id="56151-135">Creating an XElement with content</span></span>  
 <span data-ttu-id="56151-136"><xref:System.Xml.Linq.XElement>Tek bir yöntem çağrısıyla basit içerik içeren bir oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56151-136">You can create an <xref:System.Xml.Linq.XElement> that contains simple content with a single method call.</span></span> <span data-ttu-id="56151-137">Bunu yapmak için, içeriği ikinci parametre olarak aşağıdaki gibi belirtin:</span><span class="sxs-lookup"><span data-stu-id="56151-137">To do this, specify the content as the second parameter, as follows:</span></span>  
  
```csharp  
XElement n = new XElement("Customer", "Adventure Works");  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="56151-138">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="56151-138">This example produces the following output:</span></span>  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
 <span data-ttu-id="56151-139">Herhangi bir nesne türünü içerik olarak geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56151-139">You can pass any type of object as the content.</span></span> <span data-ttu-id="56151-140">Örneğin, aşağıdaki kod, içerik olarak kayan noktalı sayı içeren bir öğe oluşturur:</span><span class="sxs-lookup"><span data-stu-id="56151-140">For example, the following code creates an element that contains a floating point number as content:</span></span>  
  
```csharp  
XElement n = new XElement("Cost", 324.50);  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="56151-141">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="56151-141">This example produces the following output:</span></span>  
  
```xml  
<Cost>324.5</Cost>  
```  
  
 <span data-ttu-id="56151-142">Kayan nokta numarası paketlenmelidir ve oluşturucuya geçirilir.</span><span class="sxs-lookup"><span data-stu-id="56151-142">The floating point number is boxed and passed in to the constructor.</span></span> <span data-ttu-id="56151-143">Kutulanmış sayı bir dizeye dönüştürülür ve öğesinin içeriği olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="56151-143">The boxed number is converted to a string and used as the content of the element.</span></span>  
  
### <a name="creating-an-xelement-with-a-child-element"></a><span data-ttu-id="56151-144">Alt öğesiyle XElement oluşturma</span><span class="sxs-lookup"><span data-stu-id="56151-144">Creating an XElement with a child element</span></span>  
 <span data-ttu-id="56151-145"><xref:System.Xml.Linq.XElement>İçerik bağımsız değişkeni için sınıfının bir örneğini geçirirseniz, Oluşturucu bir alt öğesi olan bir öğesi oluşturur:</span><span class="sxs-lookup"><span data-stu-id="56151-145">If you pass an instance of the <xref:System.Xml.Linq.XElement> class for the content argument, the constructor creates an element with a child element:</span></span>  
  
```csharp  
XElement shippingUnit = new XElement("ShippingUnit",  
    new XElement("Cost", 324.50)  
);  
Console.WriteLine(shippingUnit);  
```  
  
 <span data-ttu-id="56151-146">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="56151-146">This example produces the following output:</span></span>  
  
```xml  
<ShippingUnit>  
  <Cost>324.5</Cost>  
</ShippingUnit>  
```  
  
### <a name="creating-an-xelement-with-multiple-child-elements"></a><span data-ttu-id="56151-147">Birden çok alt öğe içeren bir XElement oluşturma</span><span class="sxs-lookup"><span data-stu-id="56151-147">Creating an XElement with multiple child elements</span></span>  
 <span data-ttu-id="56151-148"><xref:System.Xml.Linq.XElement>İçerik için bir dizi nesne geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56151-148">You can pass in a number of <xref:System.Xml.Linq.XElement> objects for the content.</span></span> <span data-ttu-id="56151-149">Nesnelerin her biri <xref:System.Xml.Linq.XElement> bir alt öğe olarak dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="56151-149">Each of the <xref:System.Xml.Linq.XElement> objects is included as a child element.</span></span>  
  
```csharp  
XElement address = new XElement("Address",  
    new XElement("Street1", "123 Main St"),  
    new XElement("City", "Mercer Island"),  
    new XElement("State", "WA"),  
    new XElement("Postal", "68042")  
);  
Console.WriteLine(address);  
```  
  
 <span data-ttu-id="56151-150">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="56151-150">This example produces the following output:</span></span>  
  
```xml  
<Address>  
  <Street1>123 Main St</Street1>  
  <City>Mercer Island</City>  
  <State>WA</State>  
  <Postal>68042</Postal>  
</Address>  
```  
  
 <span data-ttu-id="56151-151">Yukarıdaki örneği genişleterek, bir XML ağacının tamamını aşağıdaki gibi oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="56151-151">By extending the above example, you can create an entire XML tree, as follows:</span></span>  
  
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
  
 <span data-ttu-id="56151-152">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="56151-152">This example produces the following output:</span></span>  
  
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

### <a name="creating-an-xelement-with-an-xattribute"></a><span data-ttu-id="56151-153">XAttribute ile XElement oluşturma</span><span class="sxs-lookup"><span data-stu-id="56151-153">Creating an XElement with an XAttribute</span></span>
 <span data-ttu-id="56151-154"><xref:System.Xml.Linq.XAttribute>İçerik bağımsız değişkeni için sınıfının bir örneğini geçirirseniz, Oluşturucu bir özniteliği olan bir öğesi oluşturur:</span><span class="sxs-lookup"><span data-stu-id="56151-154">If you pass an instance of the <xref:System.Xml.Linq.XAttribute> class for the content argument, the constructor creates an element with an attribute:</span></span>

```csharp  
XElement phone = new XElement("Phone",  
    new XAttribute("Type", "Home"),  
    "555-555-5555");  
Console.WriteLine(phone);  
```  
  
 <span data-ttu-id="56151-155">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="56151-155">This example produces the following output:</span></span>  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>
```

### <a name="creating-an-empty-element"></a><span data-ttu-id="56151-156">Boş bir öğe oluşturma</span><span class="sxs-lookup"><span data-stu-id="56151-156">Creating an empty element</span></span>  
 <span data-ttu-id="56151-157">Boş bir oluşturmak için <xref:System.Xml.Linq.XElement> , oluşturucuya herhangi bir içerik geçirmeyin.</span><span class="sxs-lookup"><span data-stu-id="56151-157">To create an empty <xref:System.Xml.Linq.XElement>, you do not pass any content to the constructor.</span></span> <span data-ttu-id="56151-158">Aşağıdaki örnek boş bir öğe oluşturur:</span><span class="sxs-lookup"><span data-stu-id="56151-158">The following example creates an empty element:</span></span>  
  
```csharp  
XElement n = new XElement("Customer");  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="56151-159">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="56151-159">This example produces the following output:</span></span>  
  
```xml  
<Customer />  
```  
  
### <a name="attaching-vs-cloning"></a><span data-ttu-id="56151-160">Ekleme ile kopyalama</span><span class="sxs-lookup"><span data-stu-id="56151-160">Attaching vs. cloning</span></span>  
 <span data-ttu-id="56151-161">Daha önce belirtildiği gibi, <xref:System.Xml.Linq.XNode> (dahil <xref:System.Xml.Linq.XElement> ) veya nesneleri eklerken (dahil), <xref:System.Xml.Linq.XAttribute> yeni içeriğin üst öğesi yoksa, nesneler yalnızca XML ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="56151-161">As mentioned previously, when adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="56151-162">Yeni içerik zaten üst öğe ise ve başka bir XML ağacının parçasıysa, yeni içerik kopyalanır ve yeni kopyalanan içerik XML ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="56151-162">If the new content already is parented and is part of another XML tree, the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span>  

<span data-ttu-id="56151-163">Aşağıdaki örnek, bir ağaca bir üst öğeye sahip bir öğe eklediğinizde ve bir ağaca üst öğesi olmayan bir öğe eklediğinizde davranışını gösterir.</span><span class="sxs-lookup"><span data-stu-id="56151-163">The following example demonstrates the behavior when you add a parented element to a tree, and when you add an element with no parent to a tree.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="56151-164">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56151-164">See also</span></span>

- [<span data-ttu-id="56151-165">XML ağaçları oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="56151-165">Creating XML Trees (C#)</span></span>](./linq-to-xml-overview.md)
