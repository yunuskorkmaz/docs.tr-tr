---
title: C# ' de XML ağaçları oluşturma-LINQ to XML
description: C# ' de bir XML ağacını LINQ to XML XElement ve XAttribute oluşturucularını kullanarak oluşturabilirsiniz ve kodu temel alınan XML yapısına benzer hale getirebilirsiniz.
ms.date: 08/31/2018
ms.assetid: cc74234a-0bac-4327-9c8c-5a2ead15b595
ms.openlocfilehash: 97bf40d84f40eabf6fa84f10bf4febb7697b10f5
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553911"
---
# <a name="create-xml-trees-in-c-linq-to-xml"></a><span data-ttu-id="41650-103">C# dilinde XML ağaçları oluşturma (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="41650-103">Create XML trees in C# (LINQ to XML)</span></span>

<span data-ttu-id="41650-104">Bu makalede C# dilinde XML ağaçları oluşturma hakkında bilgi sağlanır.</span><span class="sxs-lookup"><span data-stu-id="41650-104">This article provides information about creating XML trees in C#.</span></span>

<span data-ttu-id="41650-105">LINQ sorgularının sonuçlarını bir için içerik olarak kullanma hakkında daha fazla bilgi için <xref:System.Xml.Linq.XElement> bkz. [işlevsel oluşturma](functional-construction.md).</span><span class="sxs-lookup"><span data-stu-id="41650-105">For information about using the results of LINQ queries as the content for an <xref:System.Xml.Linq.XElement>, see [Functional construction](functional-construction.md).</span></span>

## <a name="construct-elements"></a><span data-ttu-id="41650-106">Yapı öğeleri</span><span class="sxs-lookup"><span data-stu-id="41650-106">Construct elements</span></span>

<span data-ttu-id="41650-107">Ve oluşturucuların imzaları, <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute> öğe veya özniteliğin içeriğini oluşturucuya bağımsız değişken olarak geçirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="41650-107">The signatures of the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> constructors let you pass the contents of the element or attribute as arguments to the constructor.</span></span> <span data-ttu-id="41650-108">Oluşturuculardan biri değişken sayıda bağımsız değişken kullandığından, herhangi bir sayıda alt öğe geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41650-108">Because one of the constructors takes a variable number of arguments, you can pass any number of child elements.</span></span> <span data-ttu-id="41650-109">Kuşkusuz, bu alt öğelerin her biri kendi alt öğelerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="41650-109">Of course, each of those child elements can contain their own child elements.</span></span> <span data-ttu-id="41650-110">Herhangi bir öğe için istediğiniz sayıda öznitelik ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41650-110">For any element, you can add any number of attributes.</span></span>

<span data-ttu-id="41650-111"><xref:System.Xml.Linq.XNode>(Dahil <xref:System.Xml.Linq.XElement> ) veya nesneleri eklerken <xref:System.Xml.Linq.XAttribute> , yeni içeriğin üst öğesi yoksa, nesneler yalnızca XML ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="41650-111">When adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="41650-112">Yeni içerik zaten üst öğe ise ve başka bir XML ağacının parçasıysa, yeni içerik kopyalanır ve yeni kopyalanan içerik XML ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="41650-112">If the new content already is parented, and is part of another XML tree, the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span> <span data-ttu-id="41650-113">Bu makaledeki Son örnekte bu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="41650-113">The last example in this article demonstrates this.</span></span>

<span data-ttu-id="41650-114">Oluşturmak için `contacts` <xref:System.Xml.Linq.XElement> aşağıdaki kodu kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="41650-114">To create a `contacts` <xref:System.Xml.Linq.XElement>, you could use the following code:</span></span>

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

<span data-ttu-id="41650-115">Doğru şekilde girintilense, nesneleri oluşturmak için kullanılan kod, <xref:System.Xml.Linq.XElement> temel ALıNAN XML yapısına benzer.</span><span class="sxs-lookup"><span data-stu-id="41650-115">If indented properly, the code to construct <xref:System.Xml.Linq.XElement> objects closely resembles the structure of the underlying XML.</span></span>

## <a name="xelement-constructors"></a><span data-ttu-id="41650-116">XElement oluşturucuları</span><span class="sxs-lookup"><span data-stu-id="41650-116">XElement constructors</span></span>

<span data-ttu-id="41650-117"><xref:System.Xml.Linq.XElement>Sınıfı, işlevsel oluşturma için aşağıdaki oluşturucuları kullanır.</span><span class="sxs-lookup"><span data-stu-id="41650-117">The <xref:System.Xml.Linq.XElement> class uses the following constructors for functional construction.</span></span> <span data-ttu-id="41650-118">İçin başka bazı oluşturucular olduğuna <xref:System.Xml.Linq.XElement> , ancak işlevsel oluşturma için kullanıldıklarından, burada listelenmemiştir.</span><span class="sxs-lookup"><span data-stu-id="41650-118">Note that there are some other constructors for <xref:System.Xml.Linq.XElement>, but because they're not used for functional construction they're not listed here.</span></span>

|<span data-ttu-id="41650-119">Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="41650-119">Constructor</span></span>|<span data-ttu-id="41650-120">Description</span><span class="sxs-lookup"><span data-stu-id="41650-120">Description</span></span>|
|-----------------|-----------------|
|`XElement(XName name, object content)`|<span data-ttu-id="41650-121">Oluşturur <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="41650-121">Creates an <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="41650-122">`name`Parametresi, öğesinin adını belirtir; `content` öğesinin içeriğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="41650-122">The `name` parameter specifies the name of the element; `content` specifies the content of the element.</span></span>|
|`XElement(XName name)`|<span data-ttu-id="41650-123"><xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XName> Başlatıldıktan sonra belirtilen ada sahip bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="41650-123">Creates an <xref:System.Xml.Linq.XElement> with its <xref:System.Xml.Linq.XName> initialized to the specified name.</span></span>|
|`XElement(XName name, params object[] content)`|<span data-ttu-id="41650-124"><xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XName> Başlatıldıktan sonra belirtilen ada sahip bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="41650-124">Creates an <xref:System.Xml.Linq.XElement> with its <xref:System.Xml.Linq.XName> initialized to the specified name.</span></span> <span data-ttu-id="41650-125">Öznitelikler ve/veya alt öğeleri parametre listesinin içeriğinden oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="41650-125">The attributes and/or child elements are created from the contents of the parameter list.</span></span>|

<span data-ttu-id="41650-126">`content`Parametresi son derece esnektir.</span><span class="sxs-lookup"><span data-stu-id="41650-126">The `content` parameter is extremely flexible.</span></span> <span data-ttu-id="41650-127">Geçerli bir alt öğesi olan herhangi bir nesne türünü destekler <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="41650-127">It supports any type of object that's a valid child of an <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="41650-128">Bu parametreye geçirilen farklı nesne türleri için aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="41650-128">The following rules apply to different types of objects passed in this parameter:</span></span>

- <span data-ttu-id="41650-129">Metin içeriği olarak bir dize eklenir.</span><span class="sxs-lookup"><span data-stu-id="41650-129">A string is added as text content.</span></span>
- <span data-ttu-id="41650-130">Bir <xref:System.Xml.Linq.XElement> alt öğesi olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="41650-130">An <xref:System.Xml.Linq.XElement> is added as a child element.</span></span>
- <span data-ttu-id="41650-131">Bir <xref:System.Xml.Linq.XAttribute> öznitelik olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="41650-131">An <xref:System.Xml.Linq.XAttribute> is added as an attribute.</span></span>
- <span data-ttu-id="41650-132"><xref:System.Xml.Linq.XProcessingInstruction>, <xref:System.Xml.Linq.XComment> Veya <xref:System.Xml.Linq.XText> alt içerik olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="41650-132">An <xref:System.Xml.Linq.XProcessingInstruction>, <xref:System.Xml.Linq.XComment>, or <xref:System.Xml.Linq.XText> is added as child content.</span></span>
- <span data-ttu-id="41650-133">Bir <xref:System.Collections.IEnumerable> numaralandırılır ve bu kurallar sonuçlara özyinelemeli olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="41650-133">An <xref:System.Collections.IEnumerable> is enumerated, and these rules are applied recursively to the results.</span></span>
- <span data-ttu-id="41650-134">Diğer herhangi bir tür için, `ToString` metodu çağrılır ve sonuç metin içeriği olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="41650-134">For any other type, its `ToString` method is called and the result is added as text content.</span></span>

## <a name="example-create-an-xelement-with-content"></a><span data-ttu-id="41650-135">Örnek: içerikle birlikte XElement oluşturma</span><span class="sxs-lookup"><span data-stu-id="41650-135">Example: Create an XElement with content</span></span>

<span data-ttu-id="41650-136"><xref:System.Xml.Linq.XElement>Tek bir yöntem çağrısıyla basit içerik içeren bir oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41650-136">You can create an <xref:System.Xml.Linq.XElement> that contains simple content with a single method call.</span></span> <span data-ttu-id="41650-137">Bunu yapmak için, içeriği ikinci parametre olarak aşağıdaki gibi belirtin:</span><span class="sxs-lookup"><span data-stu-id="41650-137">To do this, specify the content as the second parameter, as follows:</span></span>

```csharp
XElement n = new XElement("Customer", "Adventure Works");
Console.WriteLine(n);
```

<span data-ttu-id="41650-138">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="41650-138">This example produces the following output:</span></span>

```xml
<Customer>Adventure Works</Customer>
```

<span data-ttu-id="41650-139">Herhangi bir nesne türünü içerik olarak geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41650-139">You can pass any type of object as the content.</span></span> <span data-ttu-id="41650-140">Örneğin, aşağıdaki kod, içerik olarak kayan noktalı sayı içeren bir öğe oluşturur:</span><span class="sxs-lookup"><span data-stu-id="41650-140">For example, the following code creates an element that contains a floating point number as content:</span></span>

```csharp
XElement n = new XElement("Cost", 324.50);
Console.WriteLine(n);
```

<span data-ttu-id="41650-141">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="41650-141">This example produces the following output:</span></span>

```xml
<Cost>324.5</Cost>
```

<span data-ttu-id="41650-142">Kayan nokta numarası paketlenmelidir ve oluşturucuya geçirilir.</span><span class="sxs-lookup"><span data-stu-id="41650-142">The floating point number is boxed and passed in to the constructor.</span></span> <span data-ttu-id="41650-143">Kutulanmış sayı bir dizeye dönüştürülür ve öğesinin içeriği olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="41650-143">The boxed number is converted to a string and used as the content of the element.</span></span>

## <a name="example-create-an-xelement-with-a-child-element"></a><span data-ttu-id="41650-144">Örnek: bir alt öğe ile XElement oluşturma</span><span class="sxs-lookup"><span data-stu-id="41650-144">Example: Create an XElement with a child element</span></span>

<span data-ttu-id="41650-145"><xref:System.Xml.Linq.XElement>İçerik bağımsız değişkeni için sınıfının bir örneğini geçirirseniz, Oluşturucu bir alt öğesi olan bir öğesi oluşturur:</span><span class="sxs-lookup"><span data-stu-id="41650-145">If you pass an instance of the <xref:System.Xml.Linq.XElement> class for the content argument, the constructor creates an element with a child element:</span></span>

```csharp
XElement shippingUnit = new XElement("ShippingUnit",
    new XElement("Cost", 324.50)
);
Console.WriteLine(shippingUnit);
```

<span data-ttu-id="41650-146">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="41650-146">This example produces the following output:</span></span>

```xml
<ShippingUnit>
  <Cost>324.5</Cost>
</ShippingUnit>
```

## <a name="example-create-an-xelement-with-multiple-child-elements"></a><span data-ttu-id="41650-147">Örnek: birden çok alt öğe içeren bir XElement oluşturma</span><span class="sxs-lookup"><span data-stu-id="41650-147">Example: Create an XElement with multiple child elements</span></span>

<span data-ttu-id="41650-148"><xref:System.Xml.Linq.XElement>İçerik için bir dizi nesne geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41650-148">You can pass in a number of <xref:System.Xml.Linq.XElement> objects for the content.</span></span> <span data-ttu-id="41650-149">Nesnelerin her biri <xref:System.Xml.Linq.XElement> bir alt öğe olarak dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="41650-149">Each of the <xref:System.Xml.Linq.XElement> objects is included as a child element.</span></span>

```csharp
XElement address = new XElement("Address",
    new XElement("Street1", "123 Main St"),
    new XElement("City", "Mercer Island"),
    new XElement("State", "WA"),
    new XElement("Postal", "68042")
);
Console.WriteLine(address);
```

<span data-ttu-id="41650-150">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="41650-150">This example produces the following output:</span></span>

```xml
<Address>
  <Street1>123 Main St</Street1>
  <City>Mercer Island</City>
  <State>WA</State>
  <Postal>68042</Postal>
</Address>
```

<span data-ttu-id="41650-151">Önceki örneği genişleterek, bir XML ağacının tamamını aşağıdaki gibi oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="41650-151">By extending the previous example, you can create an entire XML tree, as follows:</span></span>

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

<span data-ttu-id="41650-152">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="41650-152">This example produces the following output:</span></span>

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

## <a name="example-create-an-xelement-with-an-xattribute"></a><span data-ttu-id="41650-153">Örnek: XAttribute ile XElement oluşturma</span><span class="sxs-lookup"><span data-stu-id="41650-153">Example: Create an XElement with an XAttribute</span></span>

<span data-ttu-id="41650-154"><xref:System.Xml.Linq.XAttribute>İçerik bağımsız değişkeni için sınıfının bir örneğini geçirirseniz, Oluşturucu bir özniteliği olan bir öğesi oluşturur:</span><span class="sxs-lookup"><span data-stu-id="41650-154">If you pass an instance of the <xref:System.Xml.Linq.XAttribute> class for the content argument, the constructor creates an element with an attribute:</span></span>

```csharp
XElement phone = new XElement("Phone",
    new XAttribute("Type", "Home"),
    "555-555-5555");
Console.WriteLine(phone);
```

<span data-ttu-id="41650-155">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="41650-155">This example produces the following output:</span></span>

```xml
<Phone Type="Home">555-555-5555</Phone>
```

## <a name="example-create-an-empty-element"></a><span data-ttu-id="41650-156">Örnek: boş bir öğe oluştur</span><span class="sxs-lookup"><span data-stu-id="41650-156">Example: Create an empty element</span></span>

<span data-ttu-id="41650-157">Boş bir oluşturmak için <xref:System.Xml.Linq.XElement> , oluşturucuya herhangi bir içerik geçirmeyin.</span><span class="sxs-lookup"><span data-stu-id="41650-157">To create an empty <xref:System.Xml.Linq.XElement>, don't pass any content to the constructor.</span></span> <span data-ttu-id="41650-158">Aşağıdaki örnek boş bir öğe oluşturur:</span><span class="sxs-lookup"><span data-stu-id="41650-158">The following example creates an empty element:</span></span>

```csharp
XElement n = new XElement("Customer");
Console.WriteLine(n);
```

<span data-ttu-id="41650-159">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="41650-159">This example produces the following output:</span></span>

```xml
<Customer />
```

## <a name="example-attach-vs-clone"></a><span data-ttu-id="41650-160">Örnek: Ekle ve Kopyala</span><span class="sxs-lookup"><span data-stu-id="41650-160">Example: Attach vs. clone</span></span>

<span data-ttu-id="41650-161">Daha önce belirtildiği gibi, <xref:System.Xml.Linq.XNode> (dahil <xref:System.Xml.Linq.XElement> ) veya nesneleri eklerken (dahil), <xref:System.Xml.Linq.XAttribute> yeni içeriğin üst öğesi yoksa, nesneler yalnızca XML ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="41650-161">As mentioned previously, when adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="41650-162">Yeni içerik zaten üst öğe ise ve başka bir XML ağacının parçasıysa, yeni içerik kopyalanır ve yeni kopyalanan içerik XML ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="41650-162">If the new content already is parented and is part of another XML tree, the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span>

<span data-ttu-id="41650-163">Aşağıdaki örnek, bir ağaca bir üst öğeye sahip bir öğe eklediğinizde ve bir ağaca üst öğesi olmayan bir öğe eklediğinizde oluşan davranışı gösterir:</span><span class="sxs-lookup"><span data-stu-id="41650-163">The following example demonstrates the behavior when you add a parented element to a tree, and when you add an element with no parent to a tree:</span></span>

```csharp
// Create a tree with a child element.
XElement xmlTree1 = new XElement("Root",
    new XElement("Child1", 1)
);

// Create an element that's not parented.
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

// This example produces the following output:
//    Child1 was cloned
//    Child2 was attached
```

## <a name="see-also"></a><span data-ttu-id="41650-164">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41650-164">See also</span></span>

- [<span data-ttu-id="41650-165">İşlevsel oluşturma</span><span class="sxs-lookup"><span data-stu-id="41650-165">Functional construction</span></span>](functional-construction.md)
