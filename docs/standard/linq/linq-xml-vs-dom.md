---
title: LINQ to XML ile DOM Karşılaştırması
description: LINQ to XML ve DOM arasında önemli farklılıklar vardır. LINQ to XML, oluşturdukları XML ağaçlarının yapısını daha iyi gösteren işlevsel oluşturma ve XML sabit değerlerini destekler.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 51c0e3d2-c047-4e6a-a423-d61a882400b7
ms.openlocfilehash: 905fe1b47361e2b96c79bc56cb831b3cb298e4de
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553325"
---
# <a name="linq-to-xml-vs-dom"></a><span data-ttu-id="f8fdd-104">LINQ to XML ile DOM Karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="f8fdd-104">LINQ to XML vs. DOM</span></span>

<span data-ttu-id="f8fdd-105">Bu makalede, LINQ to XML ve geçerli önceden baskın XML programlama API 'SI, W3C Belge Nesne Modeli (DOM) arasındaki bazı önemli farklılıklar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f8fdd-105">This article describes some key differences between LINQ to XML and the current predominant XML programming API, the W3C Document Object Model (DOM).</span></span>

## <a name="new-ways-to-construct-xml-trees"></a><span data-ttu-id="f8fdd-106">XML ağaçları oluşturmak için yeni yollar</span><span class="sxs-lookup"><span data-stu-id="f8fdd-106">New ways to construct XML trees</span></span>

<span data-ttu-id="f8fdd-107">W3C DOM 'da, aşağıdan yukarıya bir XML ağacı oluşturursunuz; diğer bir deyişle, bir belge oluşturur, öğeler oluşturur ve sonra öğeleri belgeye eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="f8fdd-107">In the W3C DOM, you build an XML tree from the bottom up; that is, you create a document, you create elements, and then you add the elements to the document.</span></span>

<span data-ttu-id="f8fdd-108">Örneğin, aşağıdaki örnek, DOM 'ın Microsoft uygulamasını kullanarak bir XML ağacı oluşturmak için tipik bir yol kullanır <xref:System.Xml.XmlDocument> .</span><span class="sxs-lookup"><span data-stu-id="f8fdd-108">For example, the following example uses a typical way to create an XML tree using the Microsoft implementation of DOM, <xref:System.Xml.XmlDocument>.</span></span>

```csharp
XmlDocument doc = new XmlDocument();
XmlElement name = doc.CreateElement("Name");
name.InnerText = "Patrick Hines";
XmlElement phone1 = doc.CreateElement("Phone");
phone1.SetAttribute("Type", "Home");
phone1.InnerText = "206-555-0144";
XmlElement phone2 = doc.CreateElement("Phone");
phone2.SetAttribute("Type", "Work");
phone2.InnerText = "425-555-0145";
XmlElement street1 = doc.CreateElement("Street1");
street1.InnerText = "123 Main St";
XmlElement city = doc.CreateElement("City");
city.InnerText = "Mercer Island";
XmlElement state = doc.CreateElement("State");
state.InnerText = "WA";
XmlElement postal = doc.CreateElement("Postal");
postal.InnerText = "68042";
XmlElement address = doc.CreateElement("Address");
address.AppendChild(street1);
address.AppendChild(city);
address.AppendChild(state);
address.AppendChild(postal);
XmlElement contact = doc.CreateElement("Contact");
contact.AppendChild(name);
contact.AppendChild(phone1);
contact.AppendChild(phone2);
contact.AppendChild(address);
XmlElement contacts = doc.CreateElement("Contacts");
contacts.AppendChild(contact);
doc.AppendChild(contacts);
```

```vb
Dim doc As XmlDocument = New XmlDocument()
Dim name As XmlElement = doc.CreateElement("Name")
name.InnerText = "Patrick Hines"
Dim phone1 As XmlElement = doc.CreateElement("Phone")
phone1.SetAttribute("Type", "Home")
phone1.InnerText = "206-555-0144"
Dim phone2 As XmlElement = doc.CreateElement("Phone")
phone2.SetAttribute("Type", "Work")
phone2.InnerText = "425-555-0145"
Dim street1 As XmlElement = doc.CreateElement("Street1")
street1.InnerText = "123 Main St"
Dim city As XmlElement = doc.CreateElement("City")
city.InnerText = "Mercer Island"
Dim state As XmlElement = doc.CreateElement("State")
state.InnerText = "WA"
Dim postal As XmlElement = doc.CreateElement("Postal")
postal.InnerText = "68042"
Dim address As XmlElement = doc.CreateElement("Address")
address.AppendChild(street1)
address.AppendChild(city)
address.AppendChild(state)
address.AppendChild(postal)
Dim contact As XmlElement = doc.CreateElement("Contact")
contact.AppendChild(name)
contact.AppendChild(phone1)
contact.AppendChild(phone2)
contact.AppendChild(address)
Dim contacts As XmlElement = doc.CreateElement("Contacts")
contacts.AppendChild(contact)
doc.AppendChild(contacts)
Console.WriteLine(doc.OuterXml)
```

<span data-ttu-id="f8fdd-109">Bu kodlama stili, XML ağacının yapısını gizler.</span><span class="sxs-lookup"><span data-stu-id="f8fdd-109">This style of coding hides the structure of the XML tree.</span></span> <span data-ttu-id="f8fdd-110">LINQ to XML, yapıyı daha iyi gösteren alternatif bir yaklaşım olan *işlevsel oluşturma*da destekler.</span><span class="sxs-lookup"><span data-stu-id="f8fdd-110">LINQ to XML also supports an alternative approach, *functional construction*, that better shows the structure.</span></span> <span data-ttu-id="f8fdd-111">Bu yaklaşım <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XAttribute> oluşturucularla yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="f8fdd-111">This approach can be done with the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> constructors.</span></span> <span data-ttu-id="f8fdd-112">Visual Basic, XML değişmez değerleri ile de yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="f8fdd-112">In Visual Basic, it can also be done with XML literals.</span></span> <span data-ttu-id="f8fdd-113">Bu örnekte, işlevsel oluşturma kullanılarak aynı XML ağacının oluşturulması gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="f8fdd-113">This example demonstrates construction of the same XML tree using functional construction:</span></span>

```csharp
XElement contacts =
    new XElement("Contacts",
        new XElement("Contact",
            new XElement("Name", "Patrick Hines"),
            new XElement("Phone", "206-555-0144",
                new XAttribute("Type", "Home")),
            new XElement("phone", "425-555-0145",
                new XAttribute("Type", "Work")),
            new XElement("Address",
                new XElement("Street1", "123 Main St"),
                new XElement("City", "Mercer Island"),
                new XElement("State", "WA"),
                new XElement("Postal", "68042")
            )
        )
    );
```

```vb
Dim contacts = _
    <Contacts>
        <Contact>
            <Name>Patrick Hines</Name>
            <Phone Type="Home">206-555-0144</Phone>
            <Phone Type="Work">425-555-0145</Phone>
            <Address>
                <Street1>123 Main St</Street1>
                <City>Mercer Island</City>
                <State>WA</State>
                <Postal>68042</Postal>
            </Address>
        </Contact>
    </Contacts>
```

<span data-ttu-id="f8fdd-114">XML ağacını oluşturmak için kodun girintilendiği, temel alınan XML 'nin yapısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f8fdd-114">Notice that indenting the code to construct the XML tree shows the structure of the underlying XML.</span></span> <span data-ttu-id="f8fdd-115">Visual Basic sürümü XML sabit değerlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f8fdd-115">The Visual Basic version uses XML literals.</span></span>

<span data-ttu-id="f8fdd-116">Daha fazla bilgi için bkz. [xml ağaçları](functional-construction.md).</span><span class="sxs-lookup"><span data-stu-id="f8fdd-116">For more information, see [XML trees](functional-construction.md).</span></span>

## <a name="work-directly-with-xml-elements"></a><span data-ttu-id="f8fdd-117">Doğrudan XML öğeleriyle çalışma</span><span class="sxs-lookup"><span data-stu-id="f8fdd-117">Work directly with XML elements</span></span>

<span data-ttu-id="f8fdd-118">XML ile programlama yaptığınızda, birincil odağınızı genellikle XML öğelerinde ve belki de özniteliklerde bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8fdd-118">When you program with XML, your primary focus is usually on XML elements and perhaps on attributes.</span></span> <span data-ttu-id="f8fdd-119">LINQ to XML, doğrudan XML öğeleri ve özniteliklerle çalışabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8fdd-119">In LINQ to XML, you can work directly with XML elements and attributes.</span></span> <span data-ttu-id="f8fdd-120">Örneğin, şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f8fdd-120">For example, you can do the following:</span></span>

- <span data-ttu-id="f8fdd-121">Bir belge nesnesi kullanmadan XML öğeleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f8fdd-121">Create XML elements without using a document object at all.</span></span> <span data-ttu-id="f8fdd-122">Bu, XML ağaçlarının parçaları ile çalışmanız gerektiğinde programlamayı basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="f8fdd-122">This simplifies programming when you have to work with fragments of XML trees.</span></span>
- <span data-ttu-id="f8fdd-123">`T:System.Xml.Linq.XElement`Nesneleri doğrudan BIR XML dosyasından yükleyin.</span><span class="sxs-lookup"><span data-stu-id="f8fdd-123">Load `T:System.Xml.Linq.XElement` objects directly from an XML file.</span></span>
- <span data-ttu-id="f8fdd-124">`T:System.Xml.Linq.XElement`Nesneleri bir dosyaya veya akışa serileştirme.</span><span class="sxs-lookup"><span data-stu-id="f8fdd-124">Serialize `T:System.Xml.Linq.XElement` objects to a file or a stream.</span></span>

<span data-ttu-id="f8fdd-125">Bu, XML belgesinin XML ağacı için bir mantıksal kapsayıcı olarak kullanıldığı W3C DOM ile karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="f8fdd-125">Compare this to the W3C DOM, in which the XML document is used as a logical container for the XML tree.</span></span> <span data-ttu-id="f8fdd-126">DOM 'da, öğeler ve öznitelikler dahil XML düğümlerinin bir XML belgesi bağlamında oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f8fdd-126">In DOM, XML nodes, including elements and attributes, must be created in the context of an XML document.</span></span> <span data-ttu-id="f8fdd-127">DOM 'da bir ad öğesi oluşturmak için bir kod parçası aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="f8fdd-127">Here is a fragment of code to create a name element in DOM:</span></span>

```csharp
XmlDocument doc = new XmlDocument();
XmlElement name = doc.CreateElement("Name");
name.InnerText = "Patrick Hines";
doc.AppendChild(name);
```

```vb
Dim doc As XmlDocument = New XmlDocument()
Dim name As XmlElement = doc.CreateElement("Name")
name.InnerText = "Patrick Hines"
doc.AppendChild(name)
```

<span data-ttu-id="f8fdd-128">Birden çok belge genelinde bir öğe kullanmak istiyorsanız düğümleri belgeler arasında içeri aktarmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f8fdd-128">If you want to use an element across multiple documents, you must import the nodes across documents.</span></span> <span data-ttu-id="f8fdd-129">LINQ to XML bu karmaşıklık katmanını önler.</span><span class="sxs-lookup"><span data-stu-id="f8fdd-129">LINQ to XML avoids this layer of complexity.</span></span>

<span data-ttu-id="f8fdd-130">LINQ to XML kullanırken, <xref:System.Xml.Linq.XDocument> yalnızca belgenin kök düzeyinde bir yorum veya işleme yönergesi eklemek istiyorsanız sınıfını kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="f8fdd-130">When using LINQ to XML, you use the <xref:System.Xml.Linq.XDocument> class only if you want to add a comment or processing instruction at the root level of the document.</span></span>

## <a name="simplified-handling-of-names-and-namespaces"></a><span data-ttu-id="f8fdd-131">Adları ve ad alanlarını Basitleştirilmiş olarak işleme</span><span class="sxs-lookup"><span data-stu-id="f8fdd-131">Simplified handling of names and namespaces</span></span>

<span data-ttu-id="f8fdd-132">Adları, ad alanlarını ve ad alanı öneklerini işleme genellikle XML programlamanın karmaşık bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="f8fdd-132">Handling names, namespaces, and namespace prefixes is generally a complex part of XML programming.</span></span> <span data-ttu-id="f8fdd-133">LINQ to XML, ad alanı önekleriyle uğraşmak için gereksinimi ortadan kaldırarak adları ve ad alanlarını basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="f8fdd-133">LINQ to XML simplifies names and namespaces by eliminating the requirement to deal with namespace prefixes.</span></span> <span data-ttu-id="f8fdd-134">Ad alanı öneklerini denetlemek istiyorsanız, kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8fdd-134">If you want to control namespace prefixes, you can.</span></span> <span data-ttu-id="f8fdd-135">Ancak ad alanı öneklerini açıkça denetistemediğinize karar verirseniz LINQ to XML, gerektiğinde serileştirme sırasında ad alanı öneklerini atayacaktır veya varsayılan ad alanlarını kullanarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="f8fdd-135">But if you decide to not explicitly control namespace prefixes, LINQ to XML will assign namespace prefixes during serialization if they're required, or will serialize using default namespaces if they're not.</span></span> <span data-ttu-id="f8fdd-136">Varsayılan ad alanları kullanılırsa, sonuçta elde edilen belgede ad alanı önekleri olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="f8fdd-136">If default namespaces are used, there will be no namespace prefixes in the resulting document.</span></span> <span data-ttu-id="f8fdd-137">Daha fazla bilgi için bkz. [ad alanlarına genel bakış](namespaces-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f8fdd-137">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

<span data-ttu-id="f8fdd-138">DOM ile ilgili başka bir sorun da bir düğümün adını değiştirmenize izin vermez.</span><span class="sxs-lookup"><span data-stu-id="f8fdd-138">Another problem with the DOM is that it doesn't let you change the name of a node.</span></span> <span data-ttu-id="f8fdd-139">Bunun yerine, yeni bir düğüm oluşturmanız ve tüm alt düğümleri buna kopyalamanız ve özgün düğüm kimliğini kaybetmemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f8fdd-139">Instead, you have to create a new node and copy all the child nodes to it, losing the original node identity.</span></span> <span data-ttu-id="f8fdd-140">LINQ to XML, bir düğümdeki özelliği ayarlamanıza olanak tanıyarak bu sorunu önler <xref:System.Xml.Linq.XName> .</span><span class="sxs-lookup"><span data-stu-id="f8fdd-140">LINQ to XML avoids this problem by enabling you to set the <xref:System.Xml.Linq.XName> property on a node.</span></span>

## <a name="static-method-support-for-loading-xml"></a><span data-ttu-id="f8fdd-141">XML yükleme için statik yöntem desteği</span><span class="sxs-lookup"><span data-stu-id="f8fdd-141">Static method support for loading XML</span></span>

<span data-ttu-id="f8fdd-142">LINQ to XML, örnek yöntemleri yerine statik yöntemler kullanarak XML yüklemenize imkan tanır.</span><span class="sxs-lookup"><span data-stu-id="f8fdd-142">LINQ to XML lets you load XML by using static methods, instead of instance methods.</span></span> <span data-ttu-id="f8fdd-143">Bu, yükleme ve ayrıştırma işlemlerini basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="f8fdd-143">This simplifies loading and parsing.</span></span> <span data-ttu-id="f8fdd-144">Daha fazla bilgi için bkz. [XML dosyasından XML yükleme](load-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="f8fdd-144">For more information, see [How to load XML from a file](load-xml-file.md).</span></span>

## <a name="removal-of-support-for-dtd-constructs"></a><span data-ttu-id="f8fdd-145">DTD yapıları için desteği kaldırma</span><span class="sxs-lookup"><span data-stu-id="f8fdd-145">Removal of support for DTD constructs</span></span>

<span data-ttu-id="f8fdd-146">LINQ to XML varlıklar ve varlık başvuruları desteğini kaldırarak XML programlamayı basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="f8fdd-146">LINQ to XML further simplifies XML programming by removing support for entities and entity references.</span></span> <span data-ttu-id="f8fdd-147">Varlıkların yönetimi karmaşıktır ve nadiren kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f8fdd-147">The management of entities is complex, and is rarely used.</span></span> <span data-ttu-id="f8fdd-148">Desteğinin kaldırılması performansı artırır ve programlama arabirimini basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="f8fdd-148">Removing their support increases performance and simplifies the programming interface.</span></span> <span data-ttu-id="f8fdd-149">LINQ to XML ağaç doldurulduktan sonra tüm DTD varlıkları genişletilir.</span><span class="sxs-lookup"><span data-stu-id="f8fdd-149">When a LINQ to XML tree is populated, all DTD entities are expanded.</span></span>

## <a name="support-for-fragments"></a><span data-ttu-id="f8fdd-150">Parçalar için destek</span><span class="sxs-lookup"><span data-stu-id="f8fdd-150">Support for fragments</span></span>

<span data-ttu-id="f8fdd-151">LINQ to XML sınıfı için eşdeğer değildir `XmlDocumentFragment` .</span><span class="sxs-lookup"><span data-stu-id="f8fdd-151">LINQ to XML doesn't provide an equivalent for the `XmlDocumentFragment` class.</span></span> <span data-ttu-id="f8fdd-152">Ancak çoğu durumda `XmlDocumentFragment` kavram, <xref:System.Collections.Generic.IEnumerable%601> veya ' nin yazıldığı bir sorgunun sonucu tarafından işlenebilir <xref:System.Xml.Linq.XNode> <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="f8fdd-152">In many cases, however, the `XmlDocumentFragment` concept can be handled by the result of a query that's typed as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XNode>, or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>.</span></span>

## <a name="support-for-xpathnavigator"></a><span data-ttu-id="f8fdd-153">XPathNavigator desteği</span><span class="sxs-lookup"><span data-stu-id="f8fdd-153">Support for XPathNavigator</span></span>

<span data-ttu-id="f8fdd-154">LINQ to XML <xref:System.Xml.XPath.XPathNavigator> ad alanındaki genişletme yöntemlerine yönelik destek sağlar <xref:System.Xml.XPath?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f8fdd-154">LINQ to XML provides support for <xref:System.Xml.XPath.XPathNavigator> through extension methods in the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="f8fdd-155">Daha fazla bilgi için bkz. <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f8fdd-155">For more information, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>

## <a name="support-for-white-space-and-indentation"></a><span data-ttu-id="f8fdd-156">Boşluk ve girintileme desteği</span><span class="sxs-lookup"><span data-stu-id="f8fdd-156">Support for white space and indentation</span></span>

<span data-ttu-id="f8fdd-157">LINQ to XML, DOM 'dan daha fazla boşluk işler.</span><span class="sxs-lookup"><span data-stu-id="f8fdd-157">LINQ to XML handles white space more simply than the DOM.</span></span>

<span data-ttu-id="f8fdd-158">Yaygın bir senaryo, girintili XML 'yi okumak, boşluk metin düğümleri olmadan bir bellek içi XML ağacı oluşturmaktır (yani, beyaz boşluğu korumadan), XML üzerinde bazı işlemler yapın ve ardından XML 'i girintilemeli olarak kaydeder.</span><span class="sxs-lookup"><span data-stu-id="f8fdd-158">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), do some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="f8fdd-159">XML 'yi biçimlendirme ile serileştirçalıştığınızda, XML ağacında yalnızca önemli boşluk korunur.</span><span class="sxs-lookup"><span data-stu-id="f8fdd-159">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="f8fdd-160">Bu, LINQ to XML için varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="f8fdd-160">This is the default behavior for LINQ to XML.</span></span>

<span data-ttu-id="f8fdd-161">Diğer bir yaygın senaryo, daha önce kasıtlı olarak girintili olan XML 'i okuyup değiştirmektir.</span><span class="sxs-lookup"><span data-stu-id="f8fdd-161">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="f8fdd-162">Bu Girintiyi istediğiniz şekilde değiştirmek istemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8fdd-162">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="f8fdd-163">LINQ to XML, bunu şu şekilde yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f8fdd-163">In LINQ to XML, you can do this by:</span></span>

- <span data-ttu-id="f8fdd-164">XML 'i yüklediğinizde veya ayrıştırdığınızda boşluk koruma.</span><span class="sxs-lookup"><span data-stu-id="f8fdd-164">Preserving white space when you load or parse the XML.</span></span>
- <span data-ttu-id="f8fdd-165">XML 'yi seri hale alırken biçimlendirmeyi devre dışı bırakma.</span><span class="sxs-lookup"><span data-stu-id="f8fdd-165">Disabling formatting when you serialize the XML.</span></span>

<span data-ttu-id="f8fdd-166">LINQ to XML, <xref:System.Xml.Linq.XText> Dom gibi özelleştirilmiş bir düğüm türüne sahip olmak yerine, boşluk olarak bir düğüm olarak depolar <xref:System.Xml.XmlNodeType.Whitespace> .</span><span class="sxs-lookup"><span data-stu-id="f8fdd-166">LINQ to XML stores white space as an <xref:System.Xml.Linq.XText> node, instead of having a specialized <xref:System.Xml.XmlNodeType.Whitespace> node type, as the DOM does.</span></span>

## <a name="support-for-annotations"></a><span data-ttu-id="f8fdd-167">Ek açıklamalar için destek</span><span class="sxs-lookup"><span data-stu-id="f8fdd-167">Support for annotations</span></span>

<span data-ttu-id="f8fdd-168">LINQ to XML öğeleri, genişletilebilir bir ek açıklama kümesini destekler.</span><span class="sxs-lookup"><span data-stu-id="f8fdd-168">LINQ to XML elements support an extensible set of annotations.</span></span> <span data-ttu-id="f8fdd-169">Bu, şema bilgileri, öğenin bir kullanıcı arabirimine bağlanıp bağlanmayacağı veya başka bir uygulamaya özgü bilgi türü gibi bir öğeyle ilgili çeşitli bilgileri izlemek için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="f8fdd-169">This is useful for tracking miscellaneous information about an element, such as schema information, information about whether the element is bound to a UI, or any other kind of application-specific information.</span></span> <span data-ttu-id="f8fdd-170">Daha fazla bilgi için bkz. [LINQ to XML ek açıklamaları](linq-xml-annotations.md).</span><span class="sxs-lookup"><span data-stu-id="f8fdd-170">For more information, see [LINQ to XML annotations](linq-xml-annotations.md).</span></span>

## <a name="support-for-schema-information"></a><span data-ttu-id="f8fdd-171">Şema bilgileri için destek</span><span class="sxs-lookup"><span data-stu-id="f8fdd-171">Support for schema information</span></span>

<span data-ttu-id="f8fdd-172">LINQ to XML, ad alanındaki genişletme yöntemleri aracılığıyla XSD doğrulaması için destek sağlar <xref:System.Xml.Schema?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f8fdd-172">LINQ to XML provides support for XSD validation through extension methods in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="f8fdd-173">Bir XML ağacının bir XSD ile uyumlu olduğunu doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8fdd-173">You can validate that an XML tree complies with an XSD.</span></span> <span data-ttu-id="f8fdd-174">XML ağacını şema-doğrulama sonrası bilgi kümesi (PSVı) ile doldurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8fdd-174">You can populate the XML tree with the post-schema-validation infoset (PSVI).</span></span> <span data-ttu-id="f8fdd-175">Daha fazla bilgi için bkz. [XSD kullanarak doğrulama](validate-xsd.md) ve <xref:System.Xml.Schema.Extensions> .</span><span class="sxs-lookup"><span data-stu-id="f8fdd-175">For more information, see [How to validate using XSD](validate-xsd.md) and <xref:System.Xml.Schema.Extensions>.</span></span>

## <a name="see-also"></a><span data-ttu-id="f8fdd-176">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f8fdd-176">See also</span></span>

- [<span data-ttu-id="f8fdd-177">LINQ to XML genel bakış</span><span class="sxs-lookup"><span data-stu-id="f8fdd-177">LINQ to XML overview</span></span>](linq-xml-overview.md)
