---
title: LINQ-XML vs. DOM (C#)
ms.date: 07/20/2015
ms.assetid: 51c0e3d2-c047-4e6a-a423-d61a882400b7
ms.openlocfilehash: 819c507f02d6671592fd8c0239df50c1ea4325b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33333238"
---
# <a name="linq-to-xml-vs-dom-c"></a><span data-ttu-id="b529f-102">LINQ-XML vs. DOM (C#)</span><span class="sxs-lookup"><span data-stu-id="b529f-102">LINQ to XML vs. DOM (C#)</span></span>
<span data-ttu-id="b529f-103">Bu bölümde arasındaki bazı temel farklar açıklanmaktadır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ve geçerli baskın XML programlama API, W3C belge nesne modeli (DOM).</span><span class="sxs-lookup"><span data-stu-id="b529f-103">This section describes some key differences between [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] and the current predominant XML programming API, the W3C Document Object Model (DOM).</span></span>  
  
## <a name="new-ways-to-construct-xml-trees"></a><span data-ttu-id="b529f-104">XML ağaçları oluşturmak için yeni yöntemler</span><span class="sxs-lookup"><span data-stu-id="b529f-104">New Ways to Construct XML Trees</span></span>  
 <span data-ttu-id="b529f-105">W3C DOM'da, aşağıdan bir XML ağacı oluşturmak; diğer bir deyişle, bir belge oluşturun, öğeleri oluşturmak ve ardından öğeleri belgeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b529f-105">In the W3C DOM, you build an XML tree from the bottom up; that is, you create a document, you create elements, and then you add the elements to the document.</span></span>  
  
 <span data-ttu-id="b529f-106">Örneğin, aşağıdaki DOM, Microsoft uygulamasını kullanarak bir XML ağacı oluşturmak için tipik bir yol olabilir <xref:System.Xml.XmlDocument>:</span><span class="sxs-lookup"><span data-stu-id="b529f-106">For example, the following would be a typical way to create an XML tree using the Microsoft implementation of DOM, <xref:System.Xml.XmlDocument>:</span></span>  
  
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
  
 <span data-ttu-id="b529f-107">Kodlama bu stili görsel olarak XML ağaç yapısı hakkında daha bilgi sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="b529f-107">This style of coding does not visually provide much information about the structure of the XML tree.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="b529f-108"> bir XML ağacı oluşturmak için bu yaklaşım destekler, ancak ayrıca alternatif bir yaklaşım destekler *işlevsel yapım*.</span><span class="sxs-lookup"><span data-stu-id="b529f-108"> supports this approach to constructing an XML tree, but also supports an alternative approach, *functional construction*.</span></span> <span data-ttu-id="b529f-109">İşlev oluşturma kullanan <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XAttribute> bir XML ağacı yapı oluşturucuları.</span><span class="sxs-lookup"><span data-stu-id="b529f-109">Functional construction uses the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> constructors to build an XML tree.</span></span>  
  
 <span data-ttu-id="b529f-110">İşte kullanarak aynı XML ağaç nasıl oluşturmak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] işlev oluşturma:</span><span class="sxs-lookup"><span data-stu-id="b529f-110">Here is how you would construct the same XML tree by using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] functional construction:</span></span>  
  
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
  
 <span data-ttu-id="b529f-111">XML ağacını oluşturmak için kod girintileme temel alınan XML yapısını gösterdiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="b529f-111">Notice that indenting the code to construct the XML tree shows the structure of the underlying XML.</span></span>  
  
 <span data-ttu-id="b529f-112">Daha fazla bilgi için bkz: [XML ağaçları (C#) oluşturma](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="b529f-112">For more information, see [Creating XML Trees (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md).</span></span>  
  
## <a name="working-directly-with-xml-elements"></a><span data-ttu-id="b529f-113">Doğrudan XML öğeleri ile çalışma</span><span class="sxs-lookup"><span data-stu-id="b529f-113">Working Directly with XML Elements</span></span>  
 <span data-ttu-id="b529f-114">XML ile program birincil odağı genellikle XML öğeleri ve belki de öznitelikleri olur.</span><span class="sxs-lookup"><span data-stu-id="b529f-114">When you program with XML, your primary focus is usually on XML elements and perhaps on attributes.</span></span> <span data-ttu-id="b529f-115">İçinde [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], doğrudan XML öğeleri ve öznitelikleri ile çalışabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b529f-115">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can work directly with XML elements and attributes.</span></span> <span data-ttu-id="b529f-116">Örneğin, aşağıdakileri yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b529f-116">For example, you can do the following:</span></span>  
  
-   <span data-ttu-id="b529f-117">XML öğeleri, bir belge nesnesi kullanmadan oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b529f-117">Create XML elements without using a document object at all.</span></span> <span data-ttu-id="b529f-118">Bu XML ağaçları parçaları ile çalışmak olduğunda programlama kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="b529f-118">This simplifies programming when you have to work with fragments of XML trees.</span></span>  
  
-   <span data-ttu-id="b529f-119">Yük `T:System.Xml.Linq.XElement` nesneleri doğrudan bir XML dosyası.</span><span class="sxs-lookup"><span data-stu-id="b529f-119">Load `T:System.Xml.Linq.XElement` objects directly from an XML file.</span></span>  
  
-   <span data-ttu-id="b529f-120">Seri hale `T:System.Xml.Linq.XElement` nesneleri bir dosyaya veya bir akış.</span><span class="sxs-lookup"><span data-stu-id="b529f-120">Serialize `T:System.Xml.Linq.XElement` objects to a file or a stream.</span></span>  
  
 <span data-ttu-id="b529f-121">Bu XML belge için XML ağacı mantıksal bir kapsayıcı olarak kullanıldığını W3C DOM karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="b529f-121">Compare this to the W3C DOM, in which the XML document is used as a logical container for the XML tree.</span></span> <span data-ttu-id="b529f-122">DOM'da, XML düğümlerini, öğeleri ve öznitelikleri içeren bir XML belgesi bağlamında oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b529f-122">In DOM, XML nodes, including elements and attributes, must be created in the context of an XML document.</span></span> <span data-ttu-id="b529f-123">Name öğesi DOM'da oluşturmak için kod parçacığını şöyledir:</span><span class="sxs-lookup"><span data-stu-id="b529f-123">Here is a fragment of the code to create a name element in DOM:</span></span>  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlElement name = doc.CreateElement("Name");  
name.InnerText = "Patrick Hines";  
doc.AppendChild(name);  
```  
  
 <span data-ttu-id="b529f-124">Bir öğenin birden çok belge boyunca kullanmak istiyorsanız, düğümleri belgeler arasında içeri aktarmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b529f-124">If you want to use an element across multiple documents, you must import the nodes across documents.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="b529f-125"> Bu katman karmaşıklık önler.</span><span class="sxs-lookup"><span data-stu-id="b529f-125"> avoids this layer of complexity.</span></span>  
  
 <span data-ttu-id="b529f-126">LINQ-XML kullanırken, kullandığınız <xref:System.Xml.Linq.XDocument> yalnızca belge kök düzeyinde bir açıklama veya işlem yönergesi eklemek istiyorsanız sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b529f-126">When using LINQ to XML, you use the <xref:System.Xml.Linq.XDocument> class only if you want to add a comment or processing instruction at the root level of the document.</span></span>  
  
## <a name="simplified-handling-of-names-and-namespaces"></a><span data-ttu-id="b529f-127">Basitleştirilmiş işleme adları ve ad alanları</span><span class="sxs-lookup"><span data-stu-id="b529f-127">Simplified Handling of Names and Namespaces</span></span>  
 <span data-ttu-id="b529f-128">Adları, ad alanları ve ad alanı öneklerini işleme genellikle bir karmaşık XML programlama parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="b529f-128">Handling names, namespaces, and namespace prefixes is generally a complex part of XML programming.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="b529f-129"> adları ve ad alanları ile ad alanı öneklerini dağıtılacak gereksinimi ortadan kaldırarak basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="b529f-129"> simplifies names and namespaces by eliminating the requirement to deal with namespace prefixes.</span></span> <span data-ttu-id="b529f-130">Ad alanı öneklerini denetlemek istiyorsanız, şunları yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b529f-130">If you want to control namespace prefixes, you can.</span></span> <span data-ttu-id="b529f-131">Ancak, ad alanı öneklerini açıkça denetlemek karar verirseniz [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] gereklidir veya değillerse varsayılan ad alanlarını kullanma seri ad alanı öneklerini seri hale getirme sırasında atar.</span><span class="sxs-lookup"><span data-stu-id="b529f-131">But if you decide to not explicitly control namespace prefixes, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will assign namespace prefixes during serialization if they are required, or will serialize using default namespaces if they are not.</span></span> <span data-ttu-id="b529f-132">Varsayılan ad kullandıysanız, sonuçta elde edilen belgede ad alanı öneklerini olacaktır.</span><span class="sxs-lookup"><span data-stu-id="b529f-132">If default namespaces are used, there will be no namespace prefixes in the resulting document.</span></span> <span data-ttu-id="b529f-133">Daha fazla bilgi için bkz: [XML ad alanları (C#) çalışma](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="b529f-133">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="b529f-134">DOM başka bir sorun, bir düğümün adı değiştirmenize izin vermez, olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="b529f-134">Another problem with the DOM is that it does not let you change the name of a node.</span></span> <span data-ttu-id="b529f-135">Bunun yerine, yeni bir düğüm oluşturmak ve tüm alt düğümleri, kopyalama özgün düğüm kimliği kaybetme gerekir.</span><span class="sxs-lookup"><span data-stu-id="b529f-135">Instead, you have to create a new node and copy all the child nodes to it, losing the original node identity.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="b529f-136"> ayarlamanıza olanak sağlayarak bu sorunu önler <xref:System.Xml.Linq.XName> bir düğümde özelliği.</span><span class="sxs-lookup"><span data-stu-id="b529f-136"> avoids this problem by enabling you to set the <xref:System.Xml.Linq.XName> property on a node.</span></span>  
  
## <a name="static-method-support-for-loading-xml"></a><span data-ttu-id="b529f-137">XML yükleme desteği statik yöntemi</span><span class="sxs-lookup"><span data-stu-id="b529f-137">Static Method Support for Loading XML</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="b529f-138"> XML yerine örnek yöntemleri statik yöntemler kullanarak yük olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="b529f-138"> lets you load XML by using static methods, instead of instance methods.</span></span> <span data-ttu-id="b529f-139">Bu, yükleme ve ayrıştırma basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="b529f-139">This simplifies loading and parsing.</span></span> <span data-ttu-id="b529f-140">Daha fazla bilgi için bkz: [nasıl yapılır: yük XML dosyasından (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md).</span><span class="sxs-lookup"><span data-stu-id="b529f-140">For more information, see [How to: Load XML from a File (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md).</span></span>  
  
## <a name="removal-of-support-for-dtd-constructs"></a><span data-ttu-id="b529f-141">DTD yapıları desteğinin kaldırılması</span><span class="sxs-lookup"><span data-stu-id="b529f-141">Removal of Support for DTD Constructs</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="b529f-142"> Daha fazla XML varlıkları ve varlık başvuruları desteği kaldırarak programlama basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="b529f-142"> further simplifies XML programming by removing support for entities and entity references.</span></span> <span data-ttu-id="b529f-143">Varlık Yönetimi karmaşıktır ve nadiren kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b529f-143">The management of entities is complex, and is rarely used.</span></span> <span data-ttu-id="b529f-144">Destek kaldırma performansı artırır ve programlama arabirimi basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="b529f-144">Removing their support increases performance and simplifies the programming interface.</span></span> <span data-ttu-id="b529f-145">Zaman bir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ağaç doldurulur, tüm DTD varlıklar genişletilir.</span><span class="sxs-lookup"><span data-stu-id="b529f-145">When a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tree is populated, all DTD entities are expanded.</span></span>  
  
## <a name="support-for-fragments"></a><span data-ttu-id="b529f-146">Parçaları için destek</span><span class="sxs-lookup"><span data-stu-id="b529f-146">Support for Fragments</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="b529f-147"> için eşdeğer bir sağlamaz `XmlDocumentFragment` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b529f-147"> does not provide an equivalent for the `XmlDocumentFragment` class.</span></span> <span data-ttu-id="b529f-148">Çoğu durumda, ancak `XmlDocumentFragment` kavram olarak yazılan bir sorgunun sonucu tarafından işlenebilir <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XNode>, veya <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="b529f-148">In many cases, however, the `XmlDocumentFragment` concept can be handled by the result of a query that is typed as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XNode>, or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="support-for-xpathnavigator"></a><span data-ttu-id="b529f-149">XPathNavigator desteği</span><span class="sxs-lookup"><span data-stu-id="b529f-149">Support for XPathNavigator</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="b529f-150"> için destek sağlar <xref:System.Xml.XPath.XPathNavigator> uzantı yöntemleri aracılığıyla <xref:System.Xml.XPath?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="b529f-150"> provides support for <xref:System.Xml.XPath.XPathNavigator> through extension methods in the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="b529f-151">Daha fazla bilgi için bkz. <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b529f-151">For more information, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
## <a name="support-for-white-space-and-indentation"></a><span data-ttu-id="b529f-152">Boşluk ve girinti desteği</span><span class="sxs-lookup"><span data-stu-id="b529f-152">Support for White Space and Indentation</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="b529f-153"> beyaz alan daha basit bir şekilde işler DOM'den</span><span class="sxs-lookup"><span data-stu-id="b529f-153"> handles white space more simply than the DOM.</span></span>  
  
 <span data-ttu-id="b529f-154">Girintili XML okuma, bir bellek içi XML ağacı boşluk metin düğüm (diğer bir deyişle, değil koruma boşluk) olmadan oluşturmak, XML bazı işlemleri ve ardından XML girintileme ile kaydetmek için yaygın bir senaryo değil.</span><span class="sxs-lookup"><span data-stu-id="b529f-154">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="b529f-155">Biçimlendirmeye sahip XML serileştirme, yalnızca önemli boşluk XML ağacında korunur.</span><span class="sxs-lookup"><span data-stu-id="b529f-155">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="b529f-156">Varsayılan davranışı budur [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b529f-156">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="b529f-157">Okumak ve özellikle girintili zaten XML değiştirmek için başka bir yaygın bir senaryo değil.</span><span class="sxs-lookup"><span data-stu-id="b529f-157">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="b529f-158">Bu girinti herhangi bir şekilde değiştirmek istemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b529f-158">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="b529f-159">İçinde [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], yükleme veya XML Ayrıştırma boşluk koruma ve XML serileştirme zaman biçimlendirme devre dışı bırakma bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b529f-159">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can do this by preserving white space when you load or parse the XML and disabling formatting when you serialize the XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="b529f-160"> boşluk olarak depolayan bir <xref:System.Xml.Linq.XText> özelleştirilmiş sahip olmak yerine düğümü <xref:System.Xml.XmlNodeType.Whitespace> düğüm türü DOM yapar.</span><span class="sxs-lookup"><span data-stu-id="b529f-160"> stores white space as an <xref:System.Xml.Linq.XText> node, instead of having a specialized <xref:System.Xml.XmlNodeType.Whitespace> node type, as the DOM does.</span></span>  
  
## <a name="support-for-annotations"></a><span data-ttu-id="b529f-161">Ek açıklamalar için destek</span><span class="sxs-lookup"><span data-stu-id="b529f-161">Support for Annotations</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="b529f-162"> öğeleri açıklamalarının genişletilebilir bir kümesini destekler.</span><span class="sxs-lookup"><span data-stu-id="b529f-162"> elements support an extensible set of annotations.</span></span> <span data-ttu-id="b529f-163">Bu, şema bilgileri, bir kullanıcı Arabirimi bağlı öğe olup olmadığı hakkında bilgi veya diğer tür uygulamaya özgü bilgileri gibi bir öğe hakkında çeşitli bilgi izlemek için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="b529f-163">This is useful for tracking miscellaneous information about an element, such as schema information, information about whether the element is bound to a UI, or any other kind of application-specific information.</span></span> <span data-ttu-id="b529f-164">Daha fazla bilgi için bkz: [LINQ-XML ek açıklamaları](http://msdn.microsoft.com/library/e2f0052d-61e2-48d4-9ea4-356c9cab35d5).</span><span class="sxs-lookup"><span data-stu-id="b529f-164">For more information, see [LINQ to XML Annotations](http://msdn.microsoft.com/library/e2f0052d-61e2-48d4-9ea4-356c9cab35d5).</span></span>  
  
## <a name="support-for-schema-information"></a><span data-ttu-id="b529f-165">Şema bilgileri için destek</span><span class="sxs-lookup"><span data-stu-id="b529f-165">Support for Schema Information</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="b529f-166"> genişletme yöntemleri aracılığıyla için XSD doğrulaması desteği sağlar <xref:System.Xml.Schema?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="b529f-166"> provides support for XSD validation through extension methods in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="b529f-167">Bir XML ağacı bir XSD ile uyumlu doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b529f-167">You can validate that an XML tree complies with an XSD.</span></span> <span data-ttu-id="b529f-168">XML ağaç sonrası doğrulama schema bilgi (PSVI) ile doldurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b529f-168">You can populate the XML tree with the post-schema-validation infoset (PSVI).</span></span> <span data-ttu-id="b529f-169">Daha fazla bilgi için bkz: [nasıl yapılır: kullanarak XSD doğrulamak](http://msdn.microsoft.com/library/481a97fa-6e96-46f2-8c9a-415555fac33b) ve <xref:System.Xml.Schema.Extensions>.</span><span class="sxs-lookup"><span data-stu-id="b529f-169">For more information, see [How to: Validate Using XSD](http://msdn.microsoft.com/library/481a97fa-6e96-46f2-8c9a-415555fac33b) and <xref:System.Xml.Schema.Extensions>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b529f-170">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b529f-170">See Also</span></span>  
 [<span data-ttu-id="b529f-171">Başlarken (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="b529f-171">Getting Started (LINQ to XML)</span></span>](../../../../csharp/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
