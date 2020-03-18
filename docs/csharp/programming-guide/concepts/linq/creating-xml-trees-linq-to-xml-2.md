---
title: C# Dilinde XML Ağaçları Oluşturma (LINQ to XML)
ms.date: 08/31/2018
ms.assetid: cc74234a-0bac-4327-9c8c-5a2ead15b595
ms.openlocfilehash: 4794e4fe019b30d8f2acb3eb255bb77ba2f7f290
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169551"
---
# <a name="creating-xml-trees-in-c-linq-to-xml"></a><span data-ttu-id="bed30-102">C# 'da XML ağaçları oluşturma (LINQ-XML)</span><span class="sxs-lookup"><span data-stu-id="bed30-102">Creating XML trees in C# (LINQ to XML)</span></span>
<span data-ttu-id="bed30-103">Bu bölümde C#'da XML ağaçları oluşturma hakkında bilgi verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bed30-103">This section provides information about creating XML trees in C#.</span></span>  
  
 <span data-ttu-id="bed30-104">Linq sorgularının sonuçlarını bir <xref:System.Xml.Linq.XElement>içerik olarak kullanma hakkında bilgi için bkz: Fonksiyonel Yapı [(LINQ to XML) (C#)](./functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="bed30-104">For information about using the results of LINQ queries as the content for an <xref:System.Xml.Linq.XElement>, see [Functional Construction (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md).</span></span>  
  
## <a name="constructing-elements"></a><span data-ttu-id="bed30-105">Öğeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="bed30-105">Constructing elements</span></span>
 <span data-ttu-id="bed30-106">Ve <xref:System.Xml.Linq.XAttribute> oluşturucuların <xref:System.Xml.Linq.XElement> imzaları, öğenin içeriğini veya özniteliği oluşturucuya bağımsız değişken olarak geçirmenize izin verebiliyor.</span><span class="sxs-lookup"><span data-stu-id="bed30-106">The signatures of the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> constructors let you pass the contents of the element or attribute as arguments to the constructor.</span></span> <span data-ttu-id="bed30-107">Oluşturuculardan biri değişken sayıda bağımsız değişken aldığından, herhangi bir sayıda alt öğeyi geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bed30-107">Because one of the constructors takes a variable number of arguments, you can pass any number of child elements.</span></span> <span data-ttu-id="bed30-108">Tabii ki, bu alt öğelerin her biri kendi alt öğeleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="bed30-108">Of course, each of those child elements can contain their own child elements.</span></span> <span data-ttu-id="bed30-109">Herhangi bir öğe için, herhangi bir sayıda öznitelik ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bed30-109">For any element, you can add any number of attributes.</span></span>  
  
 <span data-ttu-id="bed30-110">Eklerken <xref:System.Xml.Linq.XNode> (dahil) <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute> veya nesneler, yeni içeriğin üst öğesi yoksa, nesneler yalnızca XML ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="bed30-110">When adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="bed30-111">Yeni içerik zaten ebeveynliyse ve başka bir XML ağacının parçasıysa, yeni içerik klonlanır ve yeni klonlanan içerik XML ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="bed30-111">If the new content already is parented, and is part of another XML tree, the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span> <span data-ttu-id="bed30-112">Bu konudaki son örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="bed30-112">The last example in this topic demonstrates this.</span></span>  
  
 <span data-ttu-id="bed30-113">Bir `contacts` <xref:System.Xml.Linq.XElement>, oluşturmak için aşağıdaki kodu kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bed30-113">To create a `contacts`<xref:System.Xml.Linq.XElement>, you could use the following code:</span></span>  
  
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
  
 <span data-ttu-id="bed30-114">Düzgün girintisi varsa, nesneleri <xref:System.Xml.Linq.XElement> oluşturmak için kod yakından temel XML yapısına benzer.</span><span class="sxs-lookup"><span data-stu-id="bed30-114">If indented properly, the code to construct <xref:System.Xml.Linq.XElement> objects closely resembles the structure of the underlying XML.</span></span>  
  
## <a name="xelement-constructors"></a><span data-ttu-id="bed30-115">XElement yapıcılar</span><span class="sxs-lookup"><span data-stu-id="bed30-115">XElement constructors</span></span>  
 <span data-ttu-id="bed30-116">Sınıf, <xref:System.Xml.Linq.XElement> işlevsel yapı için aşağıdaki yapıcıları kullanır.</span><span class="sxs-lookup"><span data-stu-id="bed30-116">The <xref:System.Xml.Linq.XElement> class uses the following constructors for functional construction.</span></span> <span data-ttu-id="bed30-117">Bazı diğer yapıcılar için <xref:System.Xml.Linq.XElement>olduğunu unutmayın , ancak işlevsel inşaat için kullanılmadığı için burada listelenmez.</span><span class="sxs-lookup"><span data-stu-id="bed30-117">Note that there are some other constructors for <xref:System.Xml.Linq.XElement>, but because they are not used for functional construction they are not listed here.</span></span>  
  
|<span data-ttu-id="bed30-118">Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="bed30-118">Constructor</span></span>|<span data-ttu-id="bed30-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bed30-119">Description</span></span>|  
|-----------------|-----------------|  
|`XElement(XName name, object content)`|<span data-ttu-id="bed30-120">Bir <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="bed30-120">Creates an <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="bed30-121">`name` Parametre öğenin adını belirtir; `content` öğenin içeriğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bed30-121">The `name` parameter specifies the name of the element; `content` specifies the content of the element.</span></span>|  
|`XElement(XName name)`|<span data-ttu-id="bed30-122">Belirtilen ada <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XName> başharfleri olan bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bed30-122">Creates an <xref:System.Xml.Linq.XElement> with its <xref:System.Xml.Linq.XName> initialized to the specified name.</span></span>|  
|`XElement(XName name, params object[] content)`|<span data-ttu-id="bed30-123">Belirtilen ada <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XName> başharfleri olan bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bed30-123">Creates an <xref:System.Xml.Linq.XElement> with its <xref:System.Xml.Linq.XName> initialized to the specified name.</span></span> <span data-ttu-id="bed30-124">Öznitelikler ve/veya alt öğeler parametre listesinin içeriğinden oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="bed30-124">The attributes and/or child elements are created from the contents of the parameter list.</span></span>|  
  
 <span data-ttu-id="bed30-125">Parametre `content` son derece esnektir.</span><span class="sxs-lookup"><span data-stu-id="bed30-125">The `content` parameter is extremely flexible.</span></span> <span data-ttu-id="bed30-126">Geçerli bir alt olan herhangi bir nesne <xref:System.Xml.Linq.XElement>türünü destekler.</span><span class="sxs-lookup"><span data-stu-id="bed30-126">It supports any type of object that is a valid child of an <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="bed30-127">Aşağıdaki kurallar, bu parametrede geçirilen farklı nesne türleri için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="bed30-127">The following rules apply to different types of objects passed in this parameter:</span></span>  
  
- <span data-ttu-id="bed30-128">Metin içeriği olarak bir dize eklenir.</span><span class="sxs-lookup"><span data-stu-id="bed30-128">A string is added as text content.</span></span>  
  
- <span data-ttu-id="bed30-129">Bir <xref:System.Xml.Linq.XElement> alt öğe olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="bed30-129">An <xref:System.Xml.Linq.XElement> is added as a child element.</span></span>  
  
- <span data-ttu-id="bed30-130">Bir <xref:System.Xml.Linq.XAttribute> öznitelik olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="bed30-130">An <xref:System.Xml.Linq.XAttribute> is added as an attribute.</span></span>  
  
- <span data-ttu-id="bed30-131">Bir <xref:System.Xml.Linq.XProcessingInstruction> <xref:System.Xml.Linq.XComment>, <xref:System.Xml.Linq.XText> veya alt içerik olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="bed30-131">An <xref:System.Xml.Linq.XProcessingInstruction>, <xref:System.Xml.Linq.XComment>, or <xref:System.Xml.Linq.XText> is added as child content.</span></span>  
  
- <span data-ttu-id="bed30-132">Bir <xref:System.Collections.IEnumerable> numaranumaralanır ve bu kurallar sonuçlara özyinelemeli olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="bed30-132">An <xref:System.Collections.IEnumerable> is enumerated, and these rules are applied recursively to the results.</span></span>  
  
- <span data-ttu-id="bed30-133">Başka bir tür `ToString` için, yöntemi çağrılır ve sonuç metin içeriği olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="bed30-133">For any other type, its `ToString` method is called and the result is added as text content.</span></span>  
  
### <a name="creating-an-xelement-with-content"></a><span data-ttu-id="bed30-134">İçerikle XElement Oluşturma</span><span class="sxs-lookup"><span data-stu-id="bed30-134">Creating an XElement with content</span></span>  
 <span data-ttu-id="bed30-135">Tek bir <xref:System.Xml.Linq.XElement> yöntem çağrısıyla basit içerik içeren bir yöntem oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bed30-135">You can create an <xref:System.Xml.Linq.XElement> that contains simple content with a single method call.</span></span> <span data-ttu-id="bed30-136">Bunu yapmak için, içeriği ikinci parametre olarak aşağıdaki gibi belirtin:</span><span class="sxs-lookup"><span data-stu-id="bed30-136">To do this, specify the content as the second parameter, as follows:</span></span>  
  
```csharp  
XElement n = new XElement("Customer", "Adventure Works");  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="bed30-137">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="bed30-137">This example produces the following output:</span></span>  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
 <span data-ttu-id="bed30-138">İçerik olarak herhangi bir nesne türünü geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bed30-138">You can pass any type of object as the content.</span></span> <span data-ttu-id="bed30-139">Örneğin, aşağıdaki kod içerik olarak kayan nokta numarası içeren bir öğe oluşturur:</span><span class="sxs-lookup"><span data-stu-id="bed30-139">For example, the following code creates an element that contains a floating point number as content:</span></span>  
  
```csharp  
XElement n = new XElement("Cost", 324.50);  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="bed30-140">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="bed30-140">This example produces the following output:</span></span>  
  
```xml  
<Cost>324.5</Cost>  
```  
  
 <span data-ttu-id="bed30-141">Kayan nokta numarası kutulanır ve yapıcıya aktarılır.</span><span class="sxs-lookup"><span data-stu-id="bed30-141">The floating point number is boxed and passed in to the constructor.</span></span> <span data-ttu-id="bed30-142">Kutulu sayı bir dize dönüştürülür ve öğenin içeriği olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bed30-142">The boxed number is converted to a string and used as the content of the element.</span></span>  
  
### <a name="creating-an-xelement-with-a-child-element"></a><span data-ttu-id="bed30-143">Alt öğeyle xele oluşturma</span><span class="sxs-lookup"><span data-stu-id="bed30-143">Creating an XElement with a child element</span></span>  
 <span data-ttu-id="bed30-144">İçerik bağımsız değişkeni <xref:System.Xml.Linq.XElement> için sınıfın bir örneğini geçerseniz, oluşturucu alt öğeiçeren bir öğe oluşturur:</span><span class="sxs-lookup"><span data-stu-id="bed30-144">If you pass an instance of the <xref:System.Xml.Linq.XElement> class for the content argument, the constructor creates an element with a child element:</span></span>  
  
```csharp  
XElement shippingUnit = new XElement("ShippingUnit",  
    new XElement("Cost", 324.50)  
);  
Console.WriteLine(shippingUnit);  
```  
  
 <span data-ttu-id="bed30-145">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="bed30-145">This example produces the following output:</span></span>  
  
```xml  
<ShippingUnit>  
  <Cost>324.5</Cost>  
</ShippingUnit>  
```  
  
### <a name="creating-an-xelement-with-multiple-child-elements"></a><span data-ttu-id="bed30-146">Birden çok alt öğeiçeren bir XElement oluşturma</span><span class="sxs-lookup"><span data-stu-id="bed30-146">Creating an XElement with multiple child elements</span></span>  
 <span data-ttu-id="bed30-147">İçerik için bir dizi <xref:System.Xml.Linq.XElement> nesne geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bed30-147">You can pass in a number of <xref:System.Xml.Linq.XElement> objects for the content.</span></span> <span data-ttu-id="bed30-148"><xref:System.Xml.Linq.XElement> Nesnelerin her biri bir alt öğe olarak dahildir.</span><span class="sxs-lookup"><span data-stu-id="bed30-148">Each of the <xref:System.Xml.Linq.XElement> objects is included as a child element.</span></span>  
  
```csharp  
XElement address = new XElement("Address",  
    new XElement("Street1", "123 Main St"),  
    new XElement("City", "Mercer Island"),  
    new XElement("State", "WA"),  
    new XElement("Postal", "68042")  
);  
Console.WriteLine(address);  
```  
  
 <span data-ttu-id="bed30-149">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="bed30-149">This example produces the following output:</span></span>  
  
```xml  
<Address>  
  <Street1>123 Main St</Street1>  
  <City>Mercer Island</City>  
  <State>WA</State>  
  <Postal>68042</Postal>  
</Address>  
```  
  
 <span data-ttu-id="bed30-150">Yukarıdaki örneği genişleterek, aşağıdaki gibi tüm bir XML ağacı oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bed30-150">By extending the above example, you can create an entire XML tree, as follows:</span></span>  
  
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
  
 <span data-ttu-id="bed30-151">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="bed30-151">This example produces the following output:</span></span>  
  
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

### <a name="creating-an-xelement-with-an-xattribute"></a><span data-ttu-id="bed30-152">XAttribute ile XElement oluşturma</span><span class="sxs-lookup"><span data-stu-id="bed30-152">Creating an XElement with an XAttribute</span></span>
 <span data-ttu-id="bed30-153">İçerik bağımsız değişkeni <xref:System.Xml.Linq.XAttribute> için sınıfın bir örneğini geçerseniz, oluşturucu özniteliği olan bir öğe oluşturur:</span><span class="sxs-lookup"><span data-stu-id="bed30-153">If you pass an instance of the <xref:System.Xml.Linq.XAttribute> class for the content argument, the constructor creates an element with an attribute:</span></span>

```csharp  
XElement phone = new XElement("Phone",  
    new XAttribute("Type", "Home"),  
    "555-555-5555");  
Console.WriteLine(phone);  
```  
  
 <span data-ttu-id="bed30-154">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="bed30-154">This example produces the following output:</span></span>  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>
```

### <a name="creating-an-empty-element"></a><span data-ttu-id="bed30-155">Boş bir öğe oluşturma</span><span class="sxs-lookup"><span data-stu-id="bed30-155">Creating an empty element</span></span>  
 <span data-ttu-id="bed30-156">Boş <xref:System.Xml.Linq.XElement>bir , oluşturucuya herhangi bir içerik geçirmedin.</span><span class="sxs-lookup"><span data-stu-id="bed30-156">To create an empty <xref:System.Xml.Linq.XElement>, you do not pass any content to the constructor.</span></span> <span data-ttu-id="bed30-157">Aşağıdaki örnek boş bir öğe oluşturur:</span><span class="sxs-lookup"><span data-stu-id="bed30-157">The following example creates an empty element:</span></span>  
  
```csharp  
XElement n = new XElement("Customer");  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="bed30-158">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="bed30-158">This example produces the following output:</span></span>  
  
```xml  
<Customer />  
```  
  
### <a name="attaching-vs-cloning"></a><span data-ttu-id="bed30-159">Yapıştırma ve klonlama</span><span class="sxs-lookup"><span data-stu-id="bed30-159">Attaching vs. cloning</span></span>  
 <span data-ttu-id="bed30-160">Daha önce de belirtildiği <xref:System.Xml.Linq.XNode> gibi, <xref:System.Xml.Linq.XElement>eklerken <xref:System.Xml.Linq.XAttribute> (dahil) veya nesneler, yeni içeriğin üst öğesi yoksa, nesneler yalnızca XML ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="bed30-160">As mentioned previously, when adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="bed30-161">Yeni içerik zaten ebeveynliyse ve başka bir XML ağacının parçasıysa, yeni içerik klonlanır ve yeni klonlanan içerik XML ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="bed30-161">If the new content already is parented and is part of another XML tree, the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span>  

<span data-ttu-id="bed30-162">Aşağıdaki örnek, bir ağaca bir üst öğe eklediğinizde ve bir ağaca üst öğesi eklemediğinizde davranışı gösterir.</span><span class="sxs-lookup"><span data-stu-id="bed30-162">The following example demonstrates the behavior when you add a parented element to a tree, and when you add an element with no parent to a tree.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="bed30-163">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bed30-163">See also</span></span>

- [<span data-ttu-id="bed30-164">XML Ağaçları Oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="bed30-164">Creating XML Trees (C#)</span></span>](./linq-to-xml-overview.md)
