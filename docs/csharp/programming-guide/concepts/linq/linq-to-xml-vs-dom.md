---
title: LINQ-XML vs. DOM (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 51c0e3d2-c047-4e6a-a423-d61a882400b7
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 049b60477c7c6de2254dfc355a741a4beb1a725f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="linq-to-xml-vs-dom-c"></a><span data-ttu-id="1cbed-102">LINQ-XML vs. DOM (C#)</span><span class="sxs-lookup"><span data-stu-id="1cbed-102">LINQ to XML vs. DOM (C#)</span></span>
<span data-ttu-id="1cbed-103">Bu bölümde arasındaki bazı temel farklar açıklanmaktadır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ve geçerli baskın XML programlama API, W3C belge nesne modeli (DOM).</span><span class="sxs-lookup"><span data-stu-id="1cbed-103">This section describes some key differences between [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] and the current predominant XML programming API, the W3C Document Object Model (DOM).</span></span>  
  
## <a name="new-ways-to-construct-xml-trees"></a><span data-ttu-id="1cbed-104">XML ağaçları oluşturmak için yeni yöntemler</span><span class="sxs-lookup"><span data-stu-id="1cbed-104">New Ways to Construct XML Trees</span></span>  
 <span data-ttu-id="1cbed-105">W3C DOM'da, aşağıdan bir XML ağacı oluşturmak; diğer bir deyişle, bir belge oluşturun, öğeleri oluşturmak ve ardından öğeleri belgeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1cbed-105">In the W3C DOM, you build an XML tree from the bottom up; that is, you create a document, you create elements, and then you add the elements to the document.</span></span>  
  
 <span data-ttu-id="1cbed-106">Örneğin, aşağıdaki DOM, Microsoft uygulamasını kullanarak bir XML ağacı oluşturmak için tipik bir yol olabilir <xref:System.Xml.XmlDocument>:</span><span class="sxs-lookup"><span data-stu-id="1cbed-106">For example, the following would be a typical way to create an XML tree using the Microsoft implementation of DOM, <xref:System.Xml.XmlDocument>:</span></span>  
  
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
  
 <span data-ttu-id="1cbed-107">Kodlama bu stili görsel olarak XML ağaç yapısı hakkında daha bilgi sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="1cbed-107">This style of coding does not visually provide much information about the structure of the XML tree.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="1cbed-108">bir XML ağacı oluşturmak için bu yaklaşım destekler, ancak ayrıca alternatif bir yaklaşım destekler *işlevsel yapım*.</span><span class="sxs-lookup"><span data-stu-id="1cbed-108"> supports this approach to constructing an XML tree, but also supports an alternative approach, *functional construction*.</span></span> <span data-ttu-id="1cbed-109">İşlev oluşturma kullanan <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XAttribute> bir XML ağacı yapı oluşturucuları.</span><span class="sxs-lookup"><span data-stu-id="1cbed-109">Functional construction uses the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> constructors to build an XML tree.</span></span>  
  
 <span data-ttu-id="1cbed-110">İşte kullanarak aynı XML ağaç nasıl oluşturmak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] işlev oluşturma:</span><span class="sxs-lookup"><span data-stu-id="1cbed-110">Here is how you would construct the same XML tree by using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] functional construction:</span></span>  
  
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
  
 <span data-ttu-id="1cbed-111">XML ağacını oluşturmak için kod girintileme temel alınan XML yapısını gösterdiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="1cbed-111">Notice that indenting the code to construct the XML tree shows the structure of the underlying XML.</span></span>  
  
 <span data-ttu-id="1cbed-112">Daha fazla bilgi için bkz: [XML ağaçları (C#) oluşturma](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="1cbed-112">For more information, see [Creating XML Trees (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md).</span></span>  
  
## <a name="working-directly-with-xml-elements"></a><span data-ttu-id="1cbed-113">Doğrudan XML öğeleri ile çalışma</span><span class="sxs-lookup"><span data-stu-id="1cbed-113">Working Directly with XML Elements</span></span>  
 <span data-ttu-id="1cbed-114">XML ile program birincil odağı genellikle XML öğeleri ve belki de öznitelikleri olur.</span><span class="sxs-lookup"><span data-stu-id="1cbed-114">When you program with XML, your primary focus is usually on XML elements and perhaps on attributes.</span></span> <span data-ttu-id="1cbed-115">İçinde [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], doğrudan XML öğeleri ve öznitelikleri ile çalışabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1cbed-115">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can work directly with XML elements and attributes.</span></span> <span data-ttu-id="1cbed-116">Örneğin, aşağıdakileri yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1cbed-116">For example, you can do the following:</span></span>  
  
-   <span data-ttu-id="1cbed-117">XML öğeleri, bir belge nesnesi kullanmadan oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1cbed-117">Create XML elements without using a document object at all.</span></span> <span data-ttu-id="1cbed-118">Bu XML ağaçları parçaları ile çalışmak olduğunda programlama kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="1cbed-118">This simplifies programming when you have to work with fragments of XML trees.</span></span>  
  
-   <span data-ttu-id="1cbed-119">Yük `T:System.Xml.Linq.XElement` nesneleri doğrudan bir XML dosyası.</span><span class="sxs-lookup"><span data-stu-id="1cbed-119">Load `T:System.Xml.Linq.XElement` objects directly from an XML file.</span></span>  
  
-   <span data-ttu-id="1cbed-120">Seri hale `T:System.Xml.Linq.XElement` nesneleri bir dosyaya veya bir akış.</span><span class="sxs-lookup"><span data-stu-id="1cbed-120">Serialize `T:System.Xml.Linq.XElement` objects to a file or a stream.</span></span>  
  
 <span data-ttu-id="1cbed-121">Bu XML belge için XML ağacı mantıksal bir kapsayıcı olarak kullanıldığını W3C DOM karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="1cbed-121">Compare this to the W3C DOM, in which the XML document is used as a logical container for the XML tree.</span></span> <span data-ttu-id="1cbed-122">DOM'da, XML düğümlerini, öğeleri ve öznitelikleri içeren bir XML belgesi bağlamında oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1cbed-122">In DOM, XML nodes, including elements and attributes, must be created in the context of an XML document.</span></span> <span data-ttu-id="1cbed-123">Name öğesi DOM'da oluşturmak için kod parçacığını şöyledir:</span><span class="sxs-lookup"><span data-stu-id="1cbed-123">Here is a fragment of the code to create a name element in DOM:</span></span>  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlElement name = doc.CreateElement("Name");  
name.InnerText = "Patrick Hines";  
doc.AppendChild(name);  
```  
  
 <span data-ttu-id="1cbed-124">Bir öğenin birden çok belge boyunca kullanmak istiyorsanız, düğümleri belgeler arasında içeri aktarmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1cbed-124">If you want to use an element across multiple documents, you must import the nodes across documents.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="1cbed-125">Bu katman karmaşıklık önler.</span><span class="sxs-lookup"><span data-stu-id="1cbed-125"> avoids this layer of complexity.</span></span>  
  
 <span data-ttu-id="1cbed-126">LINQ-XML kullanırken, kullandığınız <xref:System.Xml.Linq.XDocument> yalnızca belge kök düzeyinde bir açıklama veya işlem yönergesi eklemek istiyorsanız sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1cbed-126">When using LINQ to XML, you use the <xref:System.Xml.Linq.XDocument> class only if you want to add a comment or processing instruction at the root level of the document.</span></span>  
  
## <a name="simplified-handling-of-names-and-namespaces"></a><span data-ttu-id="1cbed-127">Basitleştirilmiş işleme adları ve ad alanları</span><span class="sxs-lookup"><span data-stu-id="1cbed-127">Simplified Handling of Names and Namespaces</span></span>  
 <span data-ttu-id="1cbed-128">Adları, ad alanları ve ad alanı öneklerini işleme genellikle bir karmaşık XML programlama parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="1cbed-128">Handling names, namespaces, and namespace prefixes is generally a complex part of XML programming.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="1cbed-129">adları ve ad alanları ile ad alanı öneklerini dağıtılacak gereksinimi ortadan kaldırarak basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="1cbed-129"> simplifies names and namespaces by eliminating the requirement to deal with namespace prefixes.</span></span> <span data-ttu-id="1cbed-130">Ad alanı öneklerini denetlemek istiyorsanız, şunları yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1cbed-130">If you want to control namespace prefixes, you can.</span></span> <span data-ttu-id="1cbed-131">Ancak, ad alanı öneklerini açıkça denetlemek karar verirseniz [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] gereklidir veya değillerse varsayılan ad alanlarını kullanma seri ad alanı öneklerini seri hale getirme sırasında atar.</span><span class="sxs-lookup"><span data-stu-id="1cbed-131">But if you decide to not explicitly control namespace prefixes, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will assign namespace prefixes during serialization if they are required, or will serialize using default namespaces if they are not.</span></span> <span data-ttu-id="1cbed-132">Varsayılan ad kullandıysanız, sonuçta elde edilen belgede ad alanı öneklerini olacaktır.</span><span class="sxs-lookup"><span data-stu-id="1cbed-132">If default namespaces are used, there will be no namespace prefixes in the resulting document.</span></span> <span data-ttu-id="1cbed-133">Daha fazla bilgi için bkz: [XML ad alanları (C#) çalışma](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="1cbed-133">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="1cbed-134">DOM başka bir sorun, bir düğümün adı değiştirmenize izin vermez, olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="1cbed-134">Another problem with the DOM is that it does not let you change the name of a node.</span></span> <span data-ttu-id="1cbed-135">Bunun yerine, yeni bir düğüm oluşturmak ve tüm alt düğümleri, kopyalama özgün düğüm kimliği kaybetme gerekir.</span><span class="sxs-lookup"><span data-stu-id="1cbed-135">Instead, you have to create a new node and copy all the child nodes to it, losing the original node identity.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="1cbed-136">ayarlamanıza olanak sağlayarak bu sorunu önler <xref:System.Xml.Linq.XName> bir düğümde özelliği.</span><span class="sxs-lookup"><span data-stu-id="1cbed-136"> avoids this problem by enabling you to set the <xref:System.Xml.Linq.XName> property on a node.</span></span>  
  
## <a name="static-method-support-for-loading-xml"></a><span data-ttu-id="1cbed-137">XML yükleme desteği statik yöntemi</span><span class="sxs-lookup"><span data-stu-id="1cbed-137">Static Method Support for Loading XML</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="1cbed-138">XML yerine örnek yöntemleri statik yöntemler kullanarak yük olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="1cbed-138"> lets you load XML by using static methods, instead of instance methods.</span></span> <span data-ttu-id="1cbed-139">Bu, yükleme ve ayrıştırma basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="1cbed-139">This simplifies loading and parsing.</span></span> <span data-ttu-id="1cbed-140">Daha fazla bilgi için bkz: [nasıl yapılır: yük XML dosyasından (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md).</span><span class="sxs-lookup"><span data-stu-id="1cbed-140">For more information, see [How to: Load XML from a File (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md).</span></span>  
  
## <a name="removal-of-support-for-dtd-constructs"></a><span data-ttu-id="1cbed-141">DTD yapıları desteğinin kaldırılması</span><span class="sxs-lookup"><span data-stu-id="1cbed-141">Removal of Support for DTD Constructs</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="1cbed-142">Daha fazla XML varlıkları ve varlık başvuruları desteği kaldırarak programlama basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="1cbed-142"> further simplifies XML programming by removing support for entities and entity references.</span></span> <span data-ttu-id="1cbed-143">Varlık Yönetimi karmaşıktır ve nadiren kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1cbed-143">The management of entities is complex, and is rarely used.</span></span> <span data-ttu-id="1cbed-144">Destek kaldırma performansı artırır ve programlama arabirimi basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="1cbed-144">Removing their support increases performance and simplifies the programming interface.</span></span> <span data-ttu-id="1cbed-145">Zaman bir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ağaç doldurulur, tüm DTD varlıklar genişletilir.</span><span class="sxs-lookup"><span data-stu-id="1cbed-145">When a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tree is populated, all DTD entities are expanded.</span></span>  
  
## <a name="support-for-fragments"></a><span data-ttu-id="1cbed-146">Parçaları için destek</span><span class="sxs-lookup"><span data-stu-id="1cbed-146">Support for Fragments</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="1cbed-147">için eşdeğer bir sağlamaz `XmlDocumentFragment` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1cbed-147"> does not provide an equivalent for the `XmlDocumentFragment` class.</span></span> <span data-ttu-id="1cbed-148">Çoğu durumda, ancak `XmlDocumentFragment` kavram olarak yazılan bir sorgunun sonucu tarafından işlenebilir <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XNode>, veya <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="1cbed-148">In many cases, however, the `XmlDocumentFragment` concept can be handled by the result of a query that is typed as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XNode>, or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="support-for-xpathnavigator"></a><span data-ttu-id="1cbed-149">XPathNavigator desteği</span><span class="sxs-lookup"><span data-stu-id="1cbed-149">Support for XPathNavigator</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="1cbed-150">için destek sağlar <xref:System.Xml.XPath.XPathNavigator> uzantı yöntemleri aracılığıyla <xref:System.Xml.XPath?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="1cbed-150"> provides support for <xref:System.Xml.XPath.XPathNavigator> through extension methods in the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="1cbed-151">Daha fazla bilgi için bkz. <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1cbed-151">For more information, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
## <a name="support-for-white-space-and-indentation"></a><span data-ttu-id="1cbed-152">Boşluk ve girinti desteği</span><span class="sxs-lookup"><span data-stu-id="1cbed-152">Support for White Space and Indentation</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="1cbed-153">beyaz alan daha basit bir şekilde işler DOM'den</span><span class="sxs-lookup"><span data-stu-id="1cbed-153"> handles white space more simply than the DOM.</span></span>  
  
 <span data-ttu-id="1cbed-154">Girintili XML okuma, bir bellek içi XML ağacı boşluk metin düğüm (diğer bir deyişle, değil koruma boşluk) olmadan oluşturmak, XML bazı işlemleri ve ardından XML girintileme ile kaydetmek için yaygın bir senaryo değil.</span><span class="sxs-lookup"><span data-stu-id="1cbed-154">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="1cbed-155">Biçimlendirmeye sahip XML serileştirme, yalnızca önemli boşluk XML ağacında korunur.</span><span class="sxs-lookup"><span data-stu-id="1cbed-155">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="1cbed-156">Varsayılan davranışı budur [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1cbed-156">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="1cbed-157">Okumak ve özellikle girintili zaten XML değiştirmek için başka bir yaygın bir senaryo değil.</span><span class="sxs-lookup"><span data-stu-id="1cbed-157">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="1cbed-158">Bu girinti herhangi bir şekilde değiştirmek istemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1cbed-158">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="1cbed-159">İçinde [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], yükleme veya XML Ayrıştırma boşluk koruma ve XML serileştirme zaman biçimlendirme devre dışı bırakma bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1cbed-159">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can do this by preserving white space when you load or parse the XML and disabling formatting when you serialize the XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="1cbed-160">boşluk olarak depolayan bir <xref:System.Xml.Linq.XText> özelleştirilmiş sahip olmak yerine düğümü <xref:System.Xml.XmlNodeType.Whitespace> düğüm türü DOM yapar.</span><span class="sxs-lookup"><span data-stu-id="1cbed-160"> stores white space as an <xref:System.Xml.Linq.XText> node, instead of having a specialized <xref:System.Xml.XmlNodeType.Whitespace> node type, as the DOM does.</span></span>  
  
## <a name="support-for-annotations"></a><span data-ttu-id="1cbed-161">Ek açıklamalar için destek</span><span class="sxs-lookup"><span data-stu-id="1cbed-161">Support for Annotations</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="1cbed-162">öğeleri açıklamalarının genişletilebilir bir kümesini destekler.</span><span class="sxs-lookup"><span data-stu-id="1cbed-162"> elements support an extensible set of annotations.</span></span> <span data-ttu-id="1cbed-163">Bu, şema bilgileri, bir kullanıcı Arabirimi bağlı öğe olup olmadığı hakkında bilgi veya diğer tür uygulamaya özgü bilgileri gibi bir öğe hakkında çeşitli bilgi izlemek için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="1cbed-163">This is useful for tracking miscellaneous information about an element, such as schema information, information about whether the element is bound to a UI, or any other kind of application-specific information.</span></span> <span data-ttu-id="1cbed-164">Daha fazla bilgi için bkz: [LINQ-XML ek açıklamaları](http://msdn.microsoft.com/library/e2f0052d-61e2-48d4-9ea4-356c9cab35d5).</span><span class="sxs-lookup"><span data-stu-id="1cbed-164">For more information, see [LINQ to XML Annotations](http://msdn.microsoft.com/library/e2f0052d-61e2-48d4-9ea4-356c9cab35d5).</span></span>  
  
## <a name="support-for-schema-information"></a><span data-ttu-id="1cbed-165">Şema bilgileri için destek</span><span class="sxs-lookup"><span data-stu-id="1cbed-165">Support for Schema Information</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="1cbed-166">genişletme yöntemleri aracılığıyla için XSD doğrulaması desteği sağlar <xref:System.Xml.Schema?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="1cbed-166"> provides support for XSD validation through extension methods in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="1cbed-167">Bir XML ağacı bir XSD ile uyumlu doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1cbed-167">You can validate that an XML tree complies with an XSD.</span></span> <span data-ttu-id="1cbed-168">XML ağaç sonrası doğrulama schema bilgi (PSVI) ile doldurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1cbed-168">You can populate the XML tree with the post-schema-validation infoset (PSVI).</span></span> <span data-ttu-id="1cbed-169">Daha fazla bilgi için bkz: [nasıl yapılır: kullanarak XSD doğrulamak](http://msdn.microsoft.com/library/481a97fa-6e96-46f2-8c9a-415555fac33b) ve <xref:System.Xml.Schema.Extensions>.</span><span class="sxs-lookup"><span data-stu-id="1cbed-169">For more information, see [How to: Validate Using XSD](http://msdn.microsoft.com/library/481a97fa-6e96-46f2-8c9a-415555fac33b) and <xref:System.Xml.Schema.Extensions>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cbed-170">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1cbed-170">See Also</span></span>  
 [<span data-ttu-id="1cbed-171">Başlarken (LINQ-XML)</span><span class="sxs-lookup"><span data-stu-id="1cbed-171">Getting Started (LINQ to XML)</span></span>](../../../../csharp/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
