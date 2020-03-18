---
title: LINQ - XML vs. DOM (C#)
ms.date: 07/20/2015
ms.assetid: 51c0e3d2-c047-4e6a-a423-d61a882400b7
ms.openlocfilehash: 92d0da494829d57517d52fe93a3cbcf1398fdbe4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168395"
---
# <a name="linq-to-xml-vs-dom-c"></a><span data-ttu-id="c8143-102">LINQ - XML vs. DOM (C#)</span><span class="sxs-lookup"><span data-stu-id="c8143-102">LINQ to XML vs. DOM (C#)</span></span>
<span data-ttu-id="c8143-103">Bu bölümde, geçerli baskın [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XML programlama API'si, W3C Document Object Model (DOM) arasındaki bazı temel farklar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c8143-103">This section describes some key differences between [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] and the current predominant XML programming API, the W3C Document Object Model (DOM).</span></span>  
  
## <a name="new-ways-to-construct-xml-trees"></a><span data-ttu-id="c8143-104">XML Ağaçları Oluşturmanın Yeni Yolları</span><span class="sxs-lookup"><span data-stu-id="c8143-104">New Ways to Construct XML Trees</span></span>  
 <span data-ttu-id="c8143-105">W3C DOM'da, aşağıdan yukarıya bir XML ağacı oluşturursunuz; diğer bir şekilde, bir belge oluşturursunuz, öğeler oluşturursunuz ve sonra öğeleri belgeye eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="c8143-105">In the W3C DOM, you build an XML tree from the bottom up; that is, you create a document, you create elements, and then you add the elements to the document.</span></span>  
  
 <span data-ttu-id="c8143-106">Örneğin, aşağıdaki, DOM Microsoft uygulamasını kullanarak bir XML ağacı oluşturmak <xref:System.Xml.XmlDocument>için tipik bir yol olacaktır:</span><span class="sxs-lookup"><span data-stu-id="c8143-106">For example, the following would be a typical way to create an XML tree using the Microsoft implementation of DOM, <xref:System.Xml.XmlDocument>:</span></span>  
  
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
  
 <span data-ttu-id="c8143-107">Bu kodlama stili, XML ağacının yapısı hakkında görsel olarak çok fazla bilgi sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="c8143-107">This style of coding does not visually provide much information about the structure of the XML tree.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="c8143-108">bir XML ağacı oluşturmak için bu yaklaşımı destekler, ama aynı zamanda alternatif bir yaklaşım, *fonksiyonel inşaat*destekler.</span><span class="sxs-lookup"><span data-stu-id="c8143-108">supports this approach to constructing an XML tree, but also supports an alternative approach, *functional construction*.</span></span> <span data-ttu-id="c8143-109">Fonksiyonel yapı <xref:System.Xml.Linq.XElement> bir <xref:System.Xml.Linq.XAttribute> XML ağacı oluşturmak için ve yapıcılar kullanır.</span><span class="sxs-lookup"><span data-stu-id="c8143-109">Functional construction uses the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> constructors to build an XML tree.</span></span>  
  
 <span data-ttu-id="c8143-110">İşlevsel yapıyı kullanarak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] aynı XML ağacını nasıl oluşturacağınız aşağıda açıklanmıştır:</span><span class="sxs-lookup"><span data-stu-id="c8143-110">Here is how you would construct the same XML tree by using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] functional construction:</span></span>  
  
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
  
 <span data-ttu-id="c8143-111">XML ağacını oluşturmak için kodu girintisi altta yatan XML yapısını gösterir dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="c8143-111">Notice that indenting the code to construct the XML tree shows the structure of the underlying XML.</span></span>  
  
 <span data-ttu-id="c8143-112">Daha fazla bilgi için Bkz. [XML Ağaçları Oluşturma (C#)](./linq-to-xml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c8143-112">For more information, see [Creating XML Trees (C#)](./linq-to-xml-overview.md).</span></span>  
  
## <a name="working-directly-with-xml-elements"></a><span data-ttu-id="c8143-113">Doğrudan XML Elemanları ile Çalışma</span><span class="sxs-lookup"><span data-stu-id="c8143-113">Working Directly with XML Elements</span></span>  
 <span data-ttu-id="c8143-114">XML ile program yaptığınızda, birincil odak genellikle XML öğeleri ve belki de öznitelikleri üzerindedir.</span><span class="sxs-lookup"><span data-stu-id="c8143-114">When you program with XML, your primary focus is usually on XML elements and perhaps on attributes.</span></span> <span data-ttu-id="c8143-115">, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]doğrudan XML öğeleri ve öznitelikleri ile çalışabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8143-115">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can work directly with XML elements and attributes.</span></span> <span data-ttu-id="c8143-116">Örneğin, aşağıdakileri yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c8143-116">For example, you can do the following:</span></span>  
  
- <span data-ttu-id="c8143-117">Belge nesnesi hiç kullanmadan XML öğeleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c8143-117">Create XML elements without using a document object at all.</span></span> <span data-ttu-id="c8143-118">Bu, XML ağaçlarının parçalarıyla çalışmanız gerektiğinde programlamayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="c8143-118">This simplifies programming when you have to work with fragments of XML trees.</span></span>  
  
- <span data-ttu-id="c8143-119">Nesneleri `T:System.Xml.Linq.XElement` doğrudan bir XML dosyasından yükleyin.</span><span class="sxs-lookup"><span data-stu-id="c8143-119">Load `T:System.Xml.Linq.XElement` objects directly from an XML file.</span></span>  
  
- <span data-ttu-id="c8143-120">Nesneleri `T:System.Xml.Linq.XElement` bir dosyaya veya akışa seri hale getirmek.</span><span class="sxs-lookup"><span data-stu-id="c8143-120">Serialize `T:System.Xml.Linq.XElement` objects to a file or a stream.</span></span>  
  
 <span data-ttu-id="c8143-121">Bunu, XML belgesinin XML ağacı için mantıksal bir kapsayıcı olarak kullanıldığı W3C DOM ile karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="c8143-121">Compare this to the W3C DOM, in which the XML document is used as a logical container for the XML tree.</span></span> <span data-ttu-id="c8143-122">DOM'da, öğeler ve öznitelikler de dahil olmak üzere XML düğümleri, bir XML belgesi bağlamında oluşturulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c8143-122">In DOM, XML nodes, including elements and attributes, must be created in the context of an XML document.</span></span> <span data-ttu-id="c8143-123">Burada, DOM'da bir ad öğesi oluşturmak için kodun bir parçası ver:</span><span class="sxs-lookup"><span data-stu-id="c8143-123">Here is a fragment of the code to create a name element in DOM:</span></span>  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlElement name = doc.CreateElement("Name");  
name.InnerText = "Patrick Hines";  
doc.AppendChild(name);  
```  
  
 <span data-ttu-id="c8143-124">Birden çok belge arasında bir öğe kullanmak istiyorsanız, düğümleri belgeler arasında almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c8143-124">If you want to use an element across multiple documents, you must import the nodes across documents.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="c8143-125">karmaşıklığı bu katmanı önler.</span><span class="sxs-lookup"><span data-stu-id="c8143-125">avoids this layer of complexity.</span></span>  
  
 <span data-ttu-id="c8143-126">LINQ'u XML'e kullanırken, sınıfı yalnızca belgenin <xref:System.Xml.Linq.XDocument> kök düzeyinde bir yorum veya işleme yönergesi eklemek istiyorsanız kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="c8143-126">When using LINQ to XML, you use the <xref:System.Xml.Linq.XDocument> class only if you want to add a comment or processing instruction at the root level of the document.</span></span>  
  
## <a name="simplified-handling-of-names-and-namespaces"></a><span data-ttu-id="c8143-127">Adların ve Ad Alanlarının Basitleştirilmiş Kullanımı</span><span class="sxs-lookup"><span data-stu-id="c8143-127">Simplified Handling of Names and Namespaces</span></span>  
 <span data-ttu-id="c8143-128">Adları, ad alanlarını ve ad alanı öneklerini işleme genellikle XML programlamanın karmaşık bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="c8143-128">Handling names, namespaces, and namespace prefixes is generally a complex part of XML programming.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="c8143-129">ad alanı önekleri ile başa çıkma gereksinimini ortadan kaldırarak adları ve ad alanlarını basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="c8143-129">simplifies names and namespaces by eliminating the requirement to deal with namespace prefixes.</span></span> <span data-ttu-id="c8143-130">Ad alanı önekleri denetlemek istiyorsanız, yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8143-130">If you want to control namespace prefixes, you can.</span></span> <span data-ttu-id="c8143-131">Ancak ad alanı öneklerini açıkça denetlememeye karar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] verirseniz, gerekirse serileştirme sırasında ad alanı önekleri atar veya değilse varsayılan ad alanları kullanarak serihale eder.</span><span class="sxs-lookup"><span data-stu-id="c8143-131">But if you decide to not explicitly control namespace prefixes, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will assign namespace prefixes during serialization if they are required, or will serialize using default namespaces if they are not.</span></span> <span data-ttu-id="c8143-132">Varsayılan ad alanları kullanılırsa, ortaya çıkan belgede ad alanı önekleri olmaz.</span><span class="sxs-lookup"><span data-stu-id="c8143-132">If default namespaces are used, there will be no namespace prefixes in the resulting document.</span></span> <span data-ttu-id="c8143-133">Daha fazla bilgi için [Bkz. NameSpaces Genel Bakış (LINQ - XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="c8143-133">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="c8143-134">DOM ile ilgili bir diğer sorun da düğüm adını değiştirmenize izin vermemedir.</span><span class="sxs-lookup"><span data-stu-id="c8143-134">Another problem with the DOM is that it does not let you change the name of a node.</span></span> <span data-ttu-id="c8143-135">Bunun yerine, yeni bir düğüm oluşturmanız ve özgün düğüm kimliğini kaybederek tüm alt düğümleri kopyalamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c8143-135">Instead, you have to create a new node and copy all the child nodes to it, losing the original node identity.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="c8143-136"><xref:System.Xml.Linq.XName> özelliği bir düğüm üzerinde ayarlamanızı sağlayarak bu sorunu önler.</span><span class="sxs-lookup"><span data-stu-id="c8143-136">avoids this problem by enabling you to set the <xref:System.Xml.Linq.XName> property on a node.</span></span>  
  
## <a name="static-method-support-for-loading-xml"></a><span data-ttu-id="c8143-137">XML Yükleme için Statik Yöntem Desteği</span><span class="sxs-lookup"><span data-stu-id="c8143-137">Static Method Support for Loading XML</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="c8143-138">örnek yöntemleri yerine statik yöntemler kullanarak XML yüklemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8143-138">lets you load XML by using static methods, instead of instance methods.</span></span> <span data-ttu-id="c8143-139">Bu yükleme ve ayrışma kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="c8143-139">This simplifies loading and parsing.</span></span> <span data-ttu-id="c8143-140">Daha fazla bilgi için, [bir dosyadan (C#) XML nasıl yüklenir'](./how-to-load-xml-from-a-file.md)e bakın.</span><span class="sxs-lookup"><span data-stu-id="c8143-140">For more information, see [How to load XML from a file (C#)](./how-to-load-xml-from-a-file.md).</span></span>  
  
## <a name="removal-of-support-for-dtd-constructs"></a><span data-ttu-id="c8143-141">DTD Yapıları için Desteğin Kaldırılması</span><span class="sxs-lookup"><span data-stu-id="c8143-141">Removal of Support for DTD Constructs</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="c8143-142">varlıklar ve varlık başvuruları için desteği kaldırarak XML programlamayı daha da basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="c8143-142">further simplifies XML programming by removing support for entities and entity references.</span></span> <span data-ttu-id="c8143-143">Varlıkların yönetimi karmaşıktır ve nadiren kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c8143-143">The management of entities is complex, and is rarely used.</span></span> <span data-ttu-id="c8143-144">Desteklerini kaldırmak performansı artırır ve programlama arabirimini basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="c8143-144">Removing their support increases performance and simplifies the programming interface.</span></span> <span data-ttu-id="c8143-145">Bir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ağaç doldurulduğunda, tüm DTD varlıkları genişletilir.</span><span class="sxs-lookup"><span data-stu-id="c8143-145">When a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tree is populated, all DTD entities are expanded.</span></span>  
  
## <a name="support-for-fragments"></a><span data-ttu-id="c8143-146">Parçalar için Destek</span><span class="sxs-lookup"><span data-stu-id="c8143-146">Support for Fragments</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="c8143-147">`XmlDocumentFragment` sınıf için bir eşdeğer sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="c8143-147">does not provide an equivalent for the `XmlDocumentFragment` class.</span></span> <span data-ttu-id="c8143-148">Ancak, çoğu durumda, `XmlDocumentFragment` kavram <xref:System.Collections.Generic.IEnumerable%601> olarak yazılan bir sorgunun sonucu olarak <xref:System.Xml.Linq.XNode>işlenebilir <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement>, veya .</span><span class="sxs-lookup"><span data-stu-id="c8143-148">In many cases, however, the `XmlDocumentFragment` concept can be handled by the result of a query that is typed as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XNode>, or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="support-for-xpathnavigator"></a><span data-ttu-id="c8143-149">XPathNavigator desteği</span><span class="sxs-lookup"><span data-stu-id="c8143-149">Support for XPathNavigator</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="c8143-150">ad alanında <xref:System.Xml.XPath.XPathNavigator> uzantı yöntemleri aracılığıyla destek sağlar. <xref:System.Xml.XPath?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="c8143-150">provides support for <xref:System.Xml.XPath.XPathNavigator> through extension methods in the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="c8143-151">Daha fazla bilgi için bkz. <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c8143-151">For more information, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
## <a name="support-for-white-space-and-indentation"></a><span data-ttu-id="c8143-152">Beyaz Alan ve Girintinasyon desteği</span><span class="sxs-lookup"><span data-stu-id="c8143-152">Support for White Space and Indentation</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="c8143-153">dom daha basit beyaz boşluk işler.</span><span class="sxs-lookup"><span data-stu-id="c8143-153">handles white space more simply than the DOM.</span></span>  
  
 <span data-ttu-id="c8143-154">Ortak bir senaryo girintisi XML okumak, herhangi bir beyaz boşluk metin düğümleri olmadan bir bellek XML ağacı oluşturmak (yani, beyaz boşluk koruyarak değil), XML bazı işlemler gerçekleştirmek ve sonra girintiyle XML kaydetmek.</span><span class="sxs-lookup"><span data-stu-id="c8143-154">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="c8143-155">XML'yi biçimlendirme yle seri hale aldığınızda, XML ağacında yalnızca önemli beyaz boşluk korunur.</span><span class="sxs-lookup"><span data-stu-id="c8143-155">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="c8143-156">Bu, '' [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]için varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="c8143-156">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="c8143-157">Başka bir yaygın senaryo okumak ve zaten kasıtlı olarak girintilmiş xml değiştirmektir.</span><span class="sxs-lookup"><span data-stu-id="c8143-157">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="c8143-158">Bu girintiyi herhangi bir şekilde değiştirmek istemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8143-158">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="c8143-159">XML'i [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]yüklerken veya ayrıştırırken beyaz alanı koruyarak ve XML'i seri hale rirken biçimlendirmeyi devre dışı bırakarak bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8143-159">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can do this by preserving white space when you load or parse the XML and disabling formatting when you serialize the XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="c8143-160">DOM'un yaptığı <xref:System.Xml.Linq.XText> gibi, özel bir <xref:System.Xml.XmlNodeType.Whitespace> düğüm türüne sahip olmak yerine beyaz alanı düğüm olarak depolar.</span><span class="sxs-lookup"><span data-stu-id="c8143-160">stores white space as an <xref:System.Xml.Linq.XText> node, instead of having a specialized <xref:System.Xml.XmlNodeType.Whitespace> node type, as the DOM does.</span></span>  
  
## <a name="support-for-annotations"></a><span data-ttu-id="c8143-161">Ek Açıklamalar için Destek</span><span class="sxs-lookup"><span data-stu-id="c8143-161">Support for Annotations</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="c8143-162">öğeler genişletilebilir ek açıklamaları destekler.</span><span class="sxs-lookup"><span data-stu-id="c8143-162">elements support an extensible set of annotations.</span></span> <span data-ttu-id="c8143-163">Bu, şema bilgileri, öğenin kullanıcı arabirimi bağlantısına bağlı olup olmadığı veya uygulamaya özgü başka herhangi bir tür de dahil olmak üzere bir öğe hakkındaki çeşitli bilgileri izlemek için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="c8143-163">This is useful for tracking miscellaneous information about an element, such as schema information, information about whether the element is bound to a UI, or any other kind of application-specific information.</span></span> <span data-ttu-id="c8143-164">Daha fazla bilgi [için Linq'den XML Ek Açıklamaları'na](./linq-to-xml-annotations.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="c8143-164">For more information, see [LINQ to XML Annotations](./linq-to-xml-annotations.md).</span></span>  
  
## <a name="support-for-schema-information"></a><span data-ttu-id="c8143-165">Şema Bilgi Desteği</span><span class="sxs-lookup"><span data-stu-id="c8143-165">Support for Schema Information</span></span>  
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="c8143-166"><xref:System.Xml.Schema?displayProperty=nameWithType> ad alanında uzantı yöntemleri aracılığıyla XSD doğrulaması için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8143-166">provides support for XSD validation through extension methods in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="c8143-167">Bir XML ağacının Bir XSD ile uyumlu olduğunu doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8143-167">You can validate that an XML tree complies with an XSD.</span></span> <span data-ttu-id="c8143-168">XML ağacını şema sonrası doğrulama bilgi kümesi (PSVI) ile doldurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8143-168">You can populate the XML tree with the post-schema-validation infoset (PSVI).</span></span> <span data-ttu-id="c8143-169">Daha fazla bilgi [için, XSD](./how-to-validate-using-xsd-linq-to-xml.md) <xref:System.Xml.Schema.Extensions>ve .</span><span class="sxs-lookup"><span data-stu-id="c8143-169">For more information, see [How to validate using XSD](./how-to-validate-using-xsd-linq-to-xml.md) and <xref:System.Xml.Schema.Extensions>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c8143-170">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8143-170">See also</span></span>

- [<span data-ttu-id="c8143-171">Başlarken (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="c8143-171">Getting Started (LINQ to XML)</span></span>](./linq-to-xml-overview.md)
