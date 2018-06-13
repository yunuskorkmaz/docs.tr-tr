---
title: C# (LINQ-XML) XML ağaçları oluşturma
ms.date: 07/20/2015
ms.assetid: cc74234a-0bac-4327-9c8c-5a2ead15b595
ms.openlocfilehash: 4fcd0c14970dd4aabe4d51335f9a0a0a991ef019
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33335477"
---
# <a name="creating-xml-trees-in-c-linq-to-xml"></a><span data-ttu-id="60b5d-102">C# (LINQ-XML) XML ağaçları oluşturma</span><span class="sxs-lookup"><span data-stu-id="60b5d-102">Creating XML Trees in C# (LINQ to XML)</span></span>
<span data-ttu-id="60b5d-103">Bu bölümde XML ağaçları C# ' ta oluşturma hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="60b5d-103">This section provides information about creating XML trees in C#.</span></span>  
  
 <span data-ttu-id="60b5d-104">LINQ sorgularını sonuçlarını için içerik olarak kullanma hakkında bilgi için bir <xref:System.Xml.Linq.XElement>, bkz: [işlevsel yapımı (LINQ-XML) (C#)](../../../../csharp/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="60b5d-104">For information about using the results of LINQ queries as the content for an <xref:System.Xml.Linq.XElement>, see [Functional Construction (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span></span>  
  
## <a name="constructing-elements"></a><span data-ttu-id="60b5d-105">Öğeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="60b5d-105">Constructing Elements</span></span>  
 <span data-ttu-id="60b5d-106">İmzalarını <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XAttribute> oluşturucular öğe veya öznitelik içeriğini oluşturucuya bağımsız değişken olarak geçirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="60b5d-106">The signatures of the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> constructors let you pass the contents of the element or attribute as arguments to the constructor.</span></span> <span data-ttu-id="60b5d-107">Oluşturuculardan birine değişken sayıda bağımsız değişken aldığından herhangi bir sayıda alt öğelerini geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60b5d-107">Because one of the constructors takes a variable number of arguments, you can pass any number of child elements.</span></span> <span data-ttu-id="60b5d-108">Elbette, bu alt öğelerin her biri kendi alt öğelerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="60b5d-108">Of course, each of those child elements can contain their own child elements.</span></span> <span data-ttu-id="60b5d-109">Herhangi bir öğe için herhangi bir sayıda öznitelikler ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60b5d-109">For any element, you can add any number of attributes.</span></span>  
  
 <span data-ttu-id="60b5d-110">Eklerken <xref:System.Xml.Linq.XNode> (dahil olmak üzere <xref:System.Xml.Linq.XElement>) veya <xref:System.Xml.Linq.XAttribute> nesneler, yeni içeriğe üst öğeye sahipse, nesneleri basitçe bağlı XML ağacına.</span><span class="sxs-lookup"><span data-stu-id="60b5d-110">When adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="60b5d-111">Yeni içerik zaten üst öğe ve başka bir XML ağacının bir parçası ise, yeni içerik kopyalanabilen ve yeni kopyalanmış içerik XML ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="60b5d-111">If the new content already is parented, and is part of another XML tree, the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span> <span data-ttu-id="60b5d-112">Bu konudaki son örnek bu gösterir.</span><span class="sxs-lookup"><span data-stu-id="60b5d-112">The last example in this topic demonstrates this.</span></span>  
  
 <span data-ttu-id="60b5d-113">Oluşturmak için bir `contacts` <xref:System.Xml.Linq.XElement>, aşağıdaki kodu kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="60b5d-113">To create a `contacts`<xref:System.Xml.Linq.XElement>, you could use the following code:</span></span>  
  
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
  
 <span data-ttu-id="60b5d-114">Doğru şekilde oluşturmak için kodu girintili varsa <xref:System.Xml.Linq.XElement> nesneleri temel alınan XML yapısını yakından benzer.</span><span class="sxs-lookup"><span data-stu-id="60b5d-114">If indented properly, the code to construct <xref:System.Xml.Linq.XElement> objects closely resembles the structure of the underlying XML.</span></span>  
  
## <a name="xelement-constructors"></a><span data-ttu-id="60b5d-115">XElement oluşturucular</span><span class="sxs-lookup"><span data-stu-id="60b5d-115">XElement Constructors</span></span>  
 <span data-ttu-id="60b5d-116"><xref:System.Xml.Linq.XElement> Sınıfı, şu oluşturuculardan işlevsel yapımı için kullanır.</span><span class="sxs-lookup"><span data-stu-id="60b5d-116">The <xref:System.Xml.Linq.XElement> class uses the following constructors for functional construction.</span></span> <span data-ttu-id="60b5d-117">Diğer bir oluşturucuları için Not <xref:System.Xml.Linq.XElement>, ancak bunlar listelenmez burada işlevsel yapımı için kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="60b5d-117">Note that there are some other constructors for <xref:System.Xml.Linq.XElement>, but because they are not used for functional construction they are not listed here.</span></span>  
  
|<span data-ttu-id="60b5d-118">Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="60b5d-118">Constructor</span></span>|<span data-ttu-id="60b5d-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="60b5d-119">Description</span></span>|  
|-----------------|-----------------|  
|`XElement(XName name, object content)`|<span data-ttu-id="60b5d-120">Oluşturur bir <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="60b5d-120">Creates an <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="60b5d-121">`name` Parametresi; öğesinin adını belirtir `content` öğenin içeriğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="60b5d-121">The `name` parameter specifies the name of the element; `content` specifies the content of the element.</span></span>|  
|`XElement(XName name)`|<span data-ttu-id="60b5d-122">Oluşturur bir <xref:System.Xml.Linq.XElement> ile kendi <xref:System.Xml.Linq.XName> belirtilen adla başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="60b5d-122">Creates an <xref:System.Xml.Linq.XElement> with its <xref:System.Xml.Linq.XName> initialized to the specified name.</span></span>|  
|`XElement(XName name, params object[] content)`|<span data-ttu-id="60b5d-123">Oluşturur bir <xref:System.Xml.Linq.XElement> ile kendi <xref:System.Xml.Linq.XName> belirtilen adla başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="60b5d-123">Creates an <xref:System.Xml.Linq.XElement> with its <xref:System.Xml.Linq.XName> initialized to the specified name.</span></span> <span data-ttu-id="60b5d-124">Parametre listesi içeriğinden özniteliklerini ve/veya alt öğeleri oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="60b5d-124">The attributes and/or child elements are created from the contents of the parameter list.</span></span>|  
  
 <span data-ttu-id="60b5d-125">`content` Parametredir son derece esnek.</span><span class="sxs-lookup"><span data-stu-id="60b5d-125">The `content` parameter is extremely flexible.</span></span> <span data-ttu-id="60b5d-126">Geçerli bir alt nesne herhangi bir türde destekleyen bir <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="60b5d-126">It supports any type of object that is a valid child of an <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="60b5d-127">Bu parametreye geçirilen nesneleri farklı türleri için aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="60b5d-127">The following rules apply to different types of objects passed in this parameter:</span></span>  
  
-   <span data-ttu-id="60b5d-128">Bir dize metin içeriği eklenir.</span><span class="sxs-lookup"><span data-stu-id="60b5d-128">A string is added as text content.</span></span>  
  
-   <span data-ttu-id="60b5d-129">Bir <xref:System.Xml.Linq.XElement> bir alt öğesi eklenir.</span><span class="sxs-lookup"><span data-stu-id="60b5d-129">An <xref:System.Xml.Linq.XElement> is added as a child element.</span></span>  
  
-   <span data-ttu-id="60b5d-130">Bir <xref:System.Xml.Linq.XAttribute> bir özniteliği olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="60b5d-130">An <xref:System.Xml.Linq.XAttribute> is added as an attribute.</span></span>  
  
-   <span data-ttu-id="60b5d-131">Bir <xref:System.Xml.Linq.XProcessingInstruction>, <xref:System.Xml.Linq.XComment>, veya <xref:System.Xml.Linq.XText> alt içerik eklenir.</span><span class="sxs-lookup"><span data-stu-id="60b5d-131">An <xref:System.Xml.Linq.XProcessingInstruction>, <xref:System.Xml.Linq.XComment>, or <xref:System.Xml.Linq.XText> is added as child content.</span></span>  
  
-   <span data-ttu-id="60b5d-132">Bir <xref:System.Collections.IEnumerable> numaralandırılan ve bu kuralları sonuçlara özyinelemeli olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="60b5d-132">An <xref:System.Collections.IEnumerable> is enumerated, and these rules are applied recursively to the results.</span></span>  
  
-   <span data-ttu-id="60b5d-133">Diğer herhangi bir türü için kendi `ToString` yöntemi çağrılır ve sonuç metin içeriği eklenir.</span><span class="sxs-lookup"><span data-stu-id="60b5d-133">For any other type, its `ToString` method is called and the result is added as text content.</span></span>  
  
### <a name="creating-an-xelement-with-content"></a><span data-ttu-id="60b5d-134">İçerik ile bir XElement oluşturma</span><span class="sxs-lookup"><span data-stu-id="60b5d-134">Creating an XElement with Content</span></span>  
 <span data-ttu-id="60b5d-135">Oluşturabileceğiniz bir <xref:System.Xml.Linq.XElement> tek yöntem çağrısı basit içerikle içerir.</span><span class="sxs-lookup"><span data-stu-id="60b5d-135">You can create an <xref:System.Xml.Linq.XElement> that contains simple content with a single method call.</span></span> <span data-ttu-id="60b5d-136">Bunu yapmak için ikinci parametre olarak içeriği aşağıdaki gibi belirtin:</span><span class="sxs-lookup"><span data-stu-id="60b5d-136">To do this, specify the content as the second parameter, as follows:</span></span>  
  
```csharp  
XElement n = new XElement("Customer", "Adventure Works");  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="60b5d-137">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="60b5d-137">This example produces the following output:</span></span>  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
 <span data-ttu-id="60b5d-138">Herhangi bir türde nesne içeriği olarak geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60b5d-138">You can pass any type of object as the content.</span></span> <span data-ttu-id="60b5d-139">Örneğin, aşağıdaki kod bir kayan içeren bir öğeyi oluşturur nokta içerik olarak sayısı:</span><span class="sxs-lookup"><span data-stu-id="60b5d-139">For example, the following code creates an element that contains a floating point number as content:</span></span>  
  
```csharp  
XElement n = new XElement("Cost", 324.50);  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="60b5d-140">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="60b5d-140">This example produces the following output:</span></span>  
  
```xml  
<Cost>324.5</Cost>  
```  
  
 <span data-ttu-id="60b5d-141">Kayan nokta sayısı Kutulu ve oluşturucuya geçirilen.</span><span class="sxs-lookup"><span data-stu-id="60b5d-141">The floating point number is boxed and passed in to the constructor.</span></span> <span data-ttu-id="60b5d-142">Paketlenmiş numarası bir dizeye dönüştürülür ve öğenin içeriğini kullanılır.</span><span class="sxs-lookup"><span data-stu-id="60b5d-142">The boxed number is converted to a string and used as the content of the element.</span></span>  
  
### <a name="creating-an-xelement-with-a-child-element"></a><span data-ttu-id="60b5d-143">Bir XElement olan bir alt öğesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="60b5d-143">Creating an XElement with a Child Element</span></span>  
 <span data-ttu-id="60b5d-144">Örneği geçirirseniz <xref:System.Xml.Linq.XElement> sınıfı oluşturucusu içerik bağımsız değişkeni için bir alt öğesi ile öğenin oluşturur:</span><span class="sxs-lookup"><span data-stu-id="60b5d-144">If you pass an instance of the <xref:System.Xml.Linq.XElement> class for the content argument, the constructor creates an element with a child element:</span></span>  
  
```csharp  
XElement shippingUnit = new XElement("ShippingUnit",  
    new XElement("Cost", 324.50)  
);  
Console.WriteLine(shippingUnit);  
```  
  
 <span data-ttu-id="60b5d-145">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="60b5d-145">This example produces the following output:</span></span>  
  
```xml  
<ShippingUnit>  
  <Cost>324.5</Cost>  
</ShippingUnit>  
```  
  
### <a name="creating-an-xelement-with-multiple-child-elements"></a><span data-ttu-id="60b5d-146">Birden çok alt öğesi ile bir XElement oluşturma</span><span class="sxs-lookup"><span data-stu-id="60b5d-146">Creating an XElement with Multiple Child Elements</span></span>  
 <span data-ttu-id="60b5d-147">Bir süre içinde geçirdiğiniz <xref:System.Xml.Linq.XElement> içerik için nesneleri.</span><span class="sxs-lookup"><span data-stu-id="60b5d-147">You can pass in a number of <xref:System.Xml.Linq.XElement> objects for the content.</span></span> <span data-ttu-id="60b5d-148">Her biri <xref:System.Xml.Linq.XElement> nesneleri, bir alt öğesi eklenir.</span><span class="sxs-lookup"><span data-stu-id="60b5d-148">Each of the <xref:System.Xml.Linq.XElement> objects is included as a child element.</span></span>  
  
```csharp  
XElement address = new XElement("Address",  
    new XElement("Street1", "123 Main St"),  
    new XElement("City", "Mercer Island"),  
    new XElement("State", "WA"),  
    new XElement("Postal", "68042")  
);  
Console.WriteLine(address);  
```  
  
 <span data-ttu-id="60b5d-149">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="60b5d-149">This example produces the following output:</span></span>  
  
```xml  
<Address>  
  <Street1>123 Main St</Street1>  
  <City>Mercer Island</City>  
  <State>WA</State>  
  <Postal>68042</Postal>  
</Address>  
```  
  
 <span data-ttu-id="60b5d-150">Yukarıdaki örnekte genişleterek, tüm bir XML ağacında aşağıdaki gibi oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="60b5d-150">By extending the above example, you can create an entire XML tree, as follows:</span></span>  
  
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
  
 <span data-ttu-id="60b5d-151">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="60b5d-151">This example produces the following output:</span></span>  
  
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
  
### <a name="creating-an-empty-element"></a><span data-ttu-id="60b5d-152">Boş bir öğe oluşturma</span><span class="sxs-lookup"><span data-stu-id="60b5d-152">Creating an Empty Element</span></span>  
 <span data-ttu-id="60b5d-153">Boş bir oluşturmak için <xref:System.Xml.Linq.XElement>, herhangi bir içerik oluşturucuya geçmeyin.</span><span class="sxs-lookup"><span data-stu-id="60b5d-153">To create an empty <xref:System.Xml.Linq.XElement>, you do not pass any content to the constructor.</span></span> <span data-ttu-id="60b5d-154">Aşağıdaki örnek, boş bir öğesini oluşturur:</span><span class="sxs-lookup"><span data-stu-id="60b5d-154">The following example creates an empty element:</span></span>  
  
```csharp  
XElement n = new XElement("Customer");  
Console.WriteLine(n);  
```  
  
 <span data-ttu-id="60b5d-155">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="60b5d-155">This example produces the following output:</span></span>  
  
```xml  
<Customer />  
```  
  
### <a name="attaching-vs-cloning"></a><span data-ttu-id="60b5d-156">VS ekleniyor. Kopyalama</span><span class="sxs-lookup"><span data-stu-id="60b5d-156">Attaching vs. Cloning</span></span>  
 <span data-ttu-id="60b5d-157">Eklerken, daha önce belirtildiği gibi <xref:System.Xml.Linq.XNode> (dahil olmak üzere <xref:System.Xml.Linq.XElement>) veya <xref:System.Xml.Linq.XAttribute> nesneler, yeni içeriğe üst öğeye sahipse, nesneleri basitçe bağlı XML ağacına.</span><span class="sxs-lookup"><span data-stu-id="60b5d-157">As mentioned previously, when adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="60b5d-158">Yeni içerik zaten üst öğe ve başka bir XML ağacının bir parçası ise, yeni içerik kopyalanabilen ve yeni kopyalanmış içerik XML ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="60b5d-158">If the new content already is parented and is part of another XML tree, the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span>  
  
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
```  
  
 <span data-ttu-id="60b5d-159">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="60b5d-159">This example produces the following output:</span></span>  
  
```  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a><span data-ttu-id="60b5d-160">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="60b5d-160">See Also</span></span>  
 [<span data-ttu-id="60b5d-161">Oluşturma XML ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="60b5d-161">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
