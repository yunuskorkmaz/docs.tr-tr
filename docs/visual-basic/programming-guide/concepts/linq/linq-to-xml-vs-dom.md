---
title: LINQ-XML vs. DOM (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 18c36130-d598-40b7-9007-828232252978
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1f89d3ded61daf16d4a59ccabb4d58625cae4a58
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="linq-to-xml-vs-dom-visual-basic"></a><span data-ttu-id="2cdad-102">LINQ-XML vs. DOM (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2cdad-102">LINQ to XML vs. DOM (Visual Basic)</span></span>
<span data-ttu-id="2cdad-103">Bu bölümde arasındaki bazı temel farklar açıklanmaktadır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ve geçerli baskın XML programlama API, W3C belge nesne modeli (DOM).</span><span class="sxs-lookup"><span data-stu-id="2cdad-103">This section describes some key differences between [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] and the current predominant XML programming API, the W3C Document Object Model (DOM).</span></span>  
  
## <a name="new-ways-to-construct-xml-trees"></a><span data-ttu-id="2cdad-104">XML ağaçları oluşturmak için yeni yöntemler</span><span class="sxs-lookup"><span data-stu-id="2cdad-104">New Ways to Construct XML Trees</span></span>  
 <span data-ttu-id="2cdad-105">W3C DOM'da, aşağıdan bir XML ağacı oluşturmak; diğer bir deyişle, bir belge oluşturun, öğeleri oluşturmak ve ardından öğeleri belgeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2cdad-105">In the W3C DOM, you build an XML tree from the bottom up; that is, you create a document, you create elements, and then you add the elements to the document.</span></span>  
  
 <span data-ttu-id="2cdad-106">Örneğin, aşağıdaki DOM, Microsoft uygulamasını kullanarak bir XML ağacı oluşturmak için tipik bir yol olabilir <xref:System.Xml.XmlDocument>:</span><span class="sxs-lookup"><span data-stu-id="2cdad-106">For example, the following would be a typical way to create an XML tree using the Microsoft implementation of DOM, <xref:System.Xml.XmlDocument>:</span></span>  
  
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
  
 <span data-ttu-id="2cdad-107">Kodlama bu stili görsel olarak XML ağaç yapısı hakkında daha bilgi sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="2cdad-107">This style of coding does not visually provide much information about the structure of the XML tree.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="2cdad-108">bir XML ağacı oluşturmak için bu yaklaşım destekler, ancak ayrıca alternatif bir yaklaşım destekler *işlevsel yapım*.</span><span class="sxs-lookup"><span data-stu-id="2cdad-108"> supports this approach to constructing an XML tree, but also supports an alternative approach, *functional construction*.</span></span> <span data-ttu-id="2cdad-109">Visual Basic'te işlevsel yapım bir XML ağacı oluşturmak için XML değişmez değerleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="2cdad-109">In Visual Basic, functional construction uses XML literals to build an XML tree.</span></span>  
  
 <span data-ttu-id="2cdad-110">İşte kullanarak aynı XML ağaç nasıl oluşturmak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] işlev oluşturma:</span><span class="sxs-lookup"><span data-stu-id="2cdad-110">Here is how you would construct the same XML tree by using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] functional construction:</span></span>  
  
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
  
 <span data-ttu-id="2cdad-111">XML ağacını oluşturmak için kod girintileme temel alınan XML yapısını gösterdiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="2cdad-111">Notice that indenting the code to construct the XML tree shows the structure of the underlying XML.</span></span>  
  
 <span data-ttu-id="2cdad-112">Daha fazla bilgi için bkz: [XML ağaçları oluşturma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="2cdad-112">For more information, see [Creating XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span></span>  
  
## <a name="working-directly-with-xml-elements"></a><span data-ttu-id="2cdad-113">Doğrudan XML öğeleri ile çalışma</span><span class="sxs-lookup"><span data-stu-id="2cdad-113">Working Directly with XML Elements</span></span>  
 <span data-ttu-id="2cdad-114">XML ile program birincil odağı genellikle XML öğeleri ve belki de öznitelikleri olur.</span><span class="sxs-lookup"><span data-stu-id="2cdad-114">When you program with XML, your primary focus is usually on XML elements and perhaps on attributes.</span></span> <span data-ttu-id="2cdad-115">İçinde [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], doğrudan XML öğeleri ve öznitelikleri ile çalışabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2cdad-115">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can work directly with XML elements and attributes.</span></span> <span data-ttu-id="2cdad-116">Örneğin, aşağıdakileri yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2cdad-116">For example, you can do the following:</span></span>  
  
-   <span data-ttu-id="2cdad-117">XML öğeleri, bir belge nesnesi kullanmadan oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2cdad-117">Create XML elements without using a document object at all.</span></span> <span data-ttu-id="2cdad-118">Bu XML ağaçları parçaları ile çalışmak olduğunda programlama kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="2cdad-118">This simplifies programming when you have to work with fragments of XML trees.</span></span>  
  
-   <span data-ttu-id="2cdad-119">Yük `T:System.Xml.Linq.XElement` nesneleri doğrudan bir XML dosyası.</span><span class="sxs-lookup"><span data-stu-id="2cdad-119">Load `T:System.Xml.Linq.XElement` objects directly from an XML file.</span></span>  
  
-   <span data-ttu-id="2cdad-120">Seri hale `T:System.Xml.Linq.XElement` nesneleri bir dosyaya veya bir akış.</span><span class="sxs-lookup"><span data-stu-id="2cdad-120">Serialize `T:System.Xml.Linq.XElement` objects to a file or a stream.</span></span>  
  
 <span data-ttu-id="2cdad-121">Bu XML belge için XML ağacı mantıksal bir kapsayıcı olarak kullanıldığını W3C DOM karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="2cdad-121">Compare this to the W3C DOM, in which the XML document is used as a logical container for the XML tree.</span></span> <span data-ttu-id="2cdad-122">DOM'da, XML düğümlerini, öğeleri ve öznitelikleri içeren bir XML belgesi bağlamında oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2cdad-122">In DOM, XML nodes, including elements and attributes, must be created in the context of an XML document.</span></span> <span data-ttu-id="2cdad-123">Name öğesi DOM'da oluşturmak için kod parçacığını şöyledir:</span><span class="sxs-lookup"><span data-stu-id="2cdad-123">Here is a fragment of the code to create a name element in DOM:</span></span>  
  
```vb  
Dim doc As XmlDocument = New XmlDocument()  
Dim name As XmlElement = doc.CreateElement("Name")  
name.InnerText = "Patrick Hines"  
doc.AppendChild(name)  
```  
  
 <span data-ttu-id="2cdad-124">Bir öğenin birden çok belge boyunca kullanmak istiyorsanız, düğümleri belgeler arasında içeri aktarmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2cdad-124">If you want to use an element across multiple documents, you must import the nodes across documents.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="2cdad-125">Bu katman karmaşıklık önler.</span><span class="sxs-lookup"><span data-stu-id="2cdad-125"> avoids this layer of complexity.</span></span>  
  
 <span data-ttu-id="2cdad-126">LINQ-XML kullanırken, kullandığınız <xref:System.Xml.Linq.XDocument> yalnızca belge kök düzeyinde bir açıklama veya işlem yönergesi eklemek istiyorsanız sınıfı.</span><span class="sxs-lookup"><span data-stu-id="2cdad-126">When using LINQ to XML, you use the <xref:System.Xml.Linq.XDocument> class only if you want to add a comment or processing instruction at the root level of the document.</span></span>  
  
## <a name="simplified-handling-of-names-and-namespaces"></a><span data-ttu-id="2cdad-127">Basitleştirilmiş işleme adları ve ad alanları</span><span class="sxs-lookup"><span data-stu-id="2cdad-127">Simplified Handling of Names and Namespaces</span></span>  
 <span data-ttu-id="2cdad-128">Adları, ad alanları ve ad alanı öneklerini işleme genellikle bir karmaşık XML programlama parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="2cdad-128">Handling names, namespaces, and namespace prefixes is generally a complex part of XML programming.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="2cdad-129">adları ve ad alanları ile ad alanı öneklerini dağıtılacak gereksinimi ortadan kaldırarak basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="2cdad-129"> simplifies names and namespaces by eliminating the requirement to deal with namespace prefixes.</span></span> <span data-ttu-id="2cdad-130">Ad alanı öneklerini denetlemek istiyorsanız, şunları yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2cdad-130">If you want to control namespace prefixes, you can.</span></span> <span data-ttu-id="2cdad-131">Ancak, ad alanı öneklerini açıkça denetlemek karar verirseniz [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] gereklidir veya değillerse varsayılan ad alanlarını kullanma seri ad alanı öneklerini seri hale getirme sırasında atar.</span><span class="sxs-lookup"><span data-stu-id="2cdad-131">But if you decide to not explicitly control namespace prefixes, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will assign namespace prefixes during serialization if they are required, or will serialize using default namespaces if they are not.</span></span> <span data-ttu-id="2cdad-132">Varsayılan ad kullandıysanız, sonuçta elde edilen belgede ad alanı öneklerini olacaktır.</span><span class="sxs-lookup"><span data-stu-id="2cdad-132">If default namespaces are used, there will be no namespace prefixes in the resulting document.</span></span> <span data-ttu-id="2cdad-133">Daha fazla bilgi için bkz: [XML ad alanları (Visual Basic) ile çalışma](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="2cdad-133">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="2cdad-134">DOM başka bir sorun, bir düğümün adı değiştirmenize izin vermez, olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="2cdad-134">Another problem with the DOM is that it does not let you change the name of a node.</span></span> <span data-ttu-id="2cdad-135">Bunun yerine, yeni bir düğüm oluşturmak ve tüm alt düğümleri, kopyalama özgün düğüm kimliği kaybetme gerekir.</span><span class="sxs-lookup"><span data-stu-id="2cdad-135">Instead, you have to create a new node and copy all the child nodes to it, losing the original node identity.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="2cdad-136">ayarlamanıza olanak sağlayarak bu sorunu önler <xref:System.Xml.Linq.XName> bir düğümde özelliği.</span><span class="sxs-lookup"><span data-stu-id="2cdad-136"> avoids this problem by enabling you to set the <xref:System.Xml.Linq.XName> property on a node.</span></span>  
  
## <a name="static-method-support-for-loading-xml"></a><span data-ttu-id="2cdad-137">XML yükleme desteği statik yöntemi</span><span class="sxs-lookup"><span data-stu-id="2cdad-137">Static Method Support for Loading XML</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="2cdad-138">XML yerine örnek yöntemleri statik yöntemler kullanarak yük olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="2cdad-138"> lets you load XML by using static methods, instead of instance methods.</span></span> <span data-ttu-id="2cdad-139">Bu, yükleme ve ayrıştırma basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="2cdad-139">This simplifies loading and parsing.</span></span> <span data-ttu-id="2cdad-140">Daha fazla bilgi için bkz: [nasıl yapılır: yük XML dosyasından (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md).</span><span class="sxs-lookup"><span data-stu-id="2cdad-140">For more information, see [How to: Load XML from a File (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md).</span></span>  
  
## <a name="removal-of-support-for-dtd-constructs"></a><span data-ttu-id="2cdad-141">DTD yapıları desteğinin kaldırılması</span><span class="sxs-lookup"><span data-stu-id="2cdad-141">Removal of Support for DTD Constructs</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="2cdad-142">Daha fazla XML varlıkları ve varlık başvuruları desteği kaldırarak programlama basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="2cdad-142"> further simplifies XML programming by removing support for entities and entity references.</span></span> <span data-ttu-id="2cdad-143">Varlık Yönetimi karmaşıktır ve nadiren kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2cdad-143">The management of entities is complex, and is rarely used.</span></span> <span data-ttu-id="2cdad-144">Destek kaldırma performansı artırır ve programlama arabirimi basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="2cdad-144">Removing their support increases performance and simplifies the programming interface.</span></span> <span data-ttu-id="2cdad-145">Zaman bir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ağaç doldurulur, tüm DTD varlıklar genişletilir.</span><span class="sxs-lookup"><span data-stu-id="2cdad-145">When a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tree is populated, all DTD entities are expanded.</span></span>  
  
## <a name="support-for-fragments"></a><span data-ttu-id="2cdad-146">Parçaları için destek</span><span class="sxs-lookup"><span data-stu-id="2cdad-146">Support for Fragments</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="2cdad-147">için eşdeğer bir sağlamaz `XmlDocumentFragment` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="2cdad-147"> does not provide an equivalent for the `XmlDocumentFragment` class.</span></span> <span data-ttu-id="2cdad-148">Çoğu durumda, ancak `XmlDocumentFragment` kavram olarak yazılan bir sorgunun sonucu tarafından işlenebilir <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XNode>, veya <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="2cdad-148">In many cases, however, the `XmlDocumentFragment` concept can be handled by the result of a query that is typed as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XNode>, or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="support-for-xpathnavigator"></a><span data-ttu-id="2cdad-149">XPathNavigator desteği</span><span class="sxs-lookup"><span data-stu-id="2cdad-149">Support for XPathNavigator</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="2cdad-150">için destek sağlar <xref:System.Xml.XPath.XPathNavigator> uzantı yöntemleri aracılığıyla <xref:System.Xml.XPath?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="2cdad-150"> provides support for <xref:System.Xml.XPath.XPathNavigator> through extension methods in the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="2cdad-151">Daha fazla bilgi için bkz. <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2cdad-151">For more information, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
## <a name="support-for-white-space-and-indentation"></a><span data-ttu-id="2cdad-152">Boşluk ve girinti desteği</span><span class="sxs-lookup"><span data-stu-id="2cdad-152">Support for White Space and Indentation</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="2cdad-153">beyaz alan daha basit bir şekilde işler DOM'den</span><span class="sxs-lookup"><span data-stu-id="2cdad-153"> handles white space more simply than the DOM.</span></span>  
  
 <span data-ttu-id="2cdad-154">Girintili XML okuma, bir bellek içi XML ağacı boşluk metin düğüm (diğer bir deyişle, değil koruma boşluk) olmadan oluşturmak, XML bazı işlemleri ve ardından XML girintileme ile kaydetmek için yaygın bir senaryo değil.</span><span class="sxs-lookup"><span data-stu-id="2cdad-154">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="2cdad-155">Biçimlendirmeye sahip XML serileştirme, yalnızca önemli boşluk XML ağacında korunur.</span><span class="sxs-lookup"><span data-stu-id="2cdad-155">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="2cdad-156">Varsayılan davranışı budur [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2cdad-156">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="2cdad-157">Okumak ve özellikle girintili zaten XML değiştirmek için başka bir yaygın bir senaryo değil.</span><span class="sxs-lookup"><span data-stu-id="2cdad-157">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="2cdad-158">Bu girinti herhangi bir şekilde değiştirmek istemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2cdad-158">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="2cdad-159">İçinde [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], yükleme veya XML Ayrıştırma boşluk koruma ve XML serileştirme zaman biçimlendirme devre dışı bırakma bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2cdad-159">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can do this by preserving white space when you load or parse the XML and disabling formatting when you serialize the XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="2cdad-160">boşluk olarak depolayan bir <xref:System.Xml.Linq.XText> özelleştirilmiş sahip olmak yerine düğümü <xref:System.Xml.XmlNodeType.Whitespace> düğüm türü DOM yapar.</span><span class="sxs-lookup"><span data-stu-id="2cdad-160"> stores white space as an <xref:System.Xml.Linq.XText> node, instead of having a specialized <xref:System.Xml.XmlNodeType.Whitespace> node type, as the DOM does.</span></span>  
  
## <a name="support-for-annotations"></a><span data-ttu-id="2cdad-161">Ek açıklamalar için destek</span><span class="sxs-lookup"><span data-stu-id="2cdad-161">Support for Annotations</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="2cdad-162">öğeleri açıklamalarının genişletilebilir bir kümesini destekler.</span><span class="sxs-lookup"><span data-stu-id="2cdad-162"> elements support an extensible set of annotations.</span></span> <span data-ttu-id="2cdad-163">Bu, şema bilgileri, bir kullanıcı Arabirimi bağlı öğe olup olmadığı hakkında bilgi veya diğer tür uygulamaya özgü bilgileri gibi bir öğe hakkında çeşitli bilgi izlemek için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="2cdad-163">This is useful for tracking miscellaneous information about an element, such as schema information, information about whether the element is bound to a UI, or any other kind of application-specific information.</span></span> <span data-ttu-id="2cdad-164">Daha fazla bilgi için bkz: [LINQ-XML ek açıklamaları](http://msdn.microsoft.com/library/e2f0052d-61e2-48d4-9ea4-356c9cab35d5).</span><span class="sxs-lookup"><span data-stu-id="2cdad-164">For more information, see [LINQ to XML Annotations](http://msdn.microsoft.com/library/e2f0052d-61e2-48d4-9ea4-356c9cab35d5).</span></span>  
  
## <a name="support-for-schema-information"></a><span data-ttu-id="2cdad-165">Şema bilgileri için destek</span><span class="sxs-lookup"><span data-stu-id="2cdad-165">Support for Schema Information</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="2cdad-166">genişletme yöntemleri aracılığıyla için XSD doğrulaması desteği sağlar <xref:System.Xml.Schema?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="2cdad-166"> provides support for XSD validation through extension methods in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="2cdad-167">Bir XML ağacı bir XSD ile uyumlu doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2cdad-167">You can validate that an XML tree complies with an XSD.</span></span> <span data-ttu-id="2cdad-168">XML ağaç sonrası doğrulama schema bilgi (PSVI) ile doldurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2cdad-168">You can populate the XML tree with the post-schema-validation infoset (PSVI).</span></span> <span data-ttu-id="2cdad-169">Daha fazla bilgi için bkz: [nasıl yapılır: kullanarak XSD doğrulamak](http://msdn.microsoft.com/library/481a97fa-6e96-46f2-8c9a-415555fac33b) ve <xref:System.Xml.Schema.Extensions>.</span><span class="sxs-lookup"><span data-stu-id="2cdad-169">For more information, see [How to: Validate Using XSD](http://msdn.microsoft.com/library/481a97fa-6e96-46f2-8c9a-415555fac33b) and <xref:System.Xml.Schema.Extensions>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cdad-170">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2cdad-170">See Also</span></span>  
 [<span data-ttu-id="2cdad-171">Başlarken (LINQ-XML)</span><span class="sxs-lookup"><span data-stu-id="2cdad-171">Getting Started (LINQ to XML)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
