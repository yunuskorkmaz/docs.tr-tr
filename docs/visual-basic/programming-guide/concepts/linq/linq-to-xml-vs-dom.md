---
title: LINQ to XML ile. DOM (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 18c36130-d598-40b7-9007-828232252978
ms.openlocfilehash: a0a23a773e927155ca22456ea403549b255718ad
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43554314"
---
# <a name="linq-to-xml-vs-dom-visual-basic"></a><span data-ttu-id="87187-102">LINQ to XML ile. DOM (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87187-102">LINQ to XML vs. DOM (Visual Basic)</span></span>
<span data-ttu-id="87187-103">Bu bölümde arasındaki bazı temel farklar açıklanmaktadır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ve geçerli hakim XML programlama API, W3C belge nesne modeli (DOM).</span><span class="sxs-lookup"><span data-stu-id="87187-103">This section describes some key differences between [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] and the current predominant XML programming API, the W3C Document Object Model (DOM).</span></span>  
  
## <a name="new-ways-to-construct-xml-trees"></a><span data-ttu-id="87187-104">XML ağaçlarını oluşturmak için yeni yollar</span><span class="sxs-lookup"><span data-stu-id="87187-104">New Ways to Construct XML Trees</span></span>  
 <span data-ttu-id="87187-105">W3C DOM, aşağıdan bir XML ağacı oluşturmak; diğer bir deyişle, bir belge oluşturun, öğeleri oluşturmak ve sonra belgeyi öğeleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="87187-105">In the W3C DOM, you build an XML tree from the bottom up; that is, you create a document, you create elements, and then you add the elements to the document.</span></span>  
  
 <span data-ttu-id="87187-106">DOM, Microsoft uygulamasını kullanarak bir XML ağacı oluşturmak için normal bir şekilde aşağıdaki gibi olur <xref:System.Xml.XmlDocument>:</span><span class="sxs-lookup"><span data-stu-id="87187-106">For example, the following would be a typical way to create an XML tree using the Microsoft implementation of DOM, <xref:System.Xml.XmlDocument>:</span></span>  
  
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
  
 <span data-ttu-id="87187-107">Kodlama bu stil, görsel olarak XML ağacının yapısı hakkında daha bilgi sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="87187-107">This style of coding does not visually provide much information about the structure of the XML tree.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="87187-108"> bir XML ağacı oluşturmak için bu yaklaşımı destekler, ancak ayrıca alternatif bir yaklaşım destekler *işlevsel oluşturma*.</span><span class="sxs-lookup"><span data-stu-id="87187-108"> supports this approach to constructing an XML tree, but also supports an alternative approach, *functional construction*.</span></span> <span data-ttu-id="87187-109">İşlevsel oluşturma, Visual Basic'te, bir XML ağacı oluşturmak için XML sabit değerleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="87187-109">In Visual Basic, functional construction uses XML literals to build an XML tree.</span></span>  
  
 <span data-ttu-id="87187-110">İşte nasıl kullanarak aynı XML ağacı oluşturmak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] işlevsel oluşturma:</span><span class="sxs-lookup"><span data-stu-id="87187-110">Here is how you would construct the same XML tree by using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] functional construction:</span></span>  
  
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
  
 <span data-ttu-id="87187-111">Girintileme kodu XML ağacı oluşturmak için temel alınan XML yapısını gösterdiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="87187-111">Notice that indenting the code to construct the XML tree shows the structure of the underlying XML.</span></span>  
  
 <span data-ttu-id="87187-112">Daha fazla bilgi için [XML ağaçları oluşturma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="87187-112">For more information, see [Creating XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span></span>  
  
## <a name="working-directly-with-xml-elements"></a><span data-ttu-id="87187-113">Doğrudan XML öğeleri ile çalışma</span><span class="sxs-lookup"><span data-stu-id="87187-113">Working Directly with XML Elements</span></span>  
 <span data-ttu-id="87187-114">XML ile program, birincil odak noktası genellikle XML öğeleri ve belki de öznitelikleri olur.</span><span class="sxs-lookup"><span data-stu-id="87187-114">When you program with XML, your primary focus is usually on XML elements and perhaps on attributes.</span></span> <span data-ttu-id="87187-115">İçinde [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], doğrudan XML öğeleri ve öznitelikleri ile çalışabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87187-115">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can work directly with XML elements and attributes.</span></span> <span data-ttu-id="87187-116">Örneğin, aşağıdakileri yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="87187-116">For example, you can do the following:</span></span>  
  
-   <span data-ttu-id="87187-117">XML öğeleri, bir belge nesnesi kullanmadan oluşturun.</span><span class="sxs-lookup"><span data-stu-id="87187-117">Create XML elements without using a document object at all.</span></span> <span data-ttu-id="87187-118">Bu XML ağaçlarını parçalarını ile çalışacak şekilde olduğunda programlama kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="87187-118">This simplifies programming when you have to work with fragments of XML trees.</span></span>  
  
-   <span data-ttu-id="87187-119">Yük `T:System.Xml.Linq.XElement` doğrudan XML dosyasından nesneleri.</span><span class="sxs-lookup"><span data-stu-id="87187-119">Load `T:System.Xml.Linq.XElement` objects directly from an XML file.</span></span>  
  
-   <span data-ttu-id="87187-120">Seri hale getirme `T:System.Xml.Linq.XElement` nesneleri bir dosyaya veya bir akış.</span><span class="sxs-lookup"><span data-stu-id="87187-120">Serialize `T:System.Xml.Linq.XElement` objects to a file or a stream.</span></span>  
  
 <span data-ttu-id="87187-121">W3C XML belgesi için XML ağacı mantıksal kapsayıcı olarak kullanılır DOM karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="87187-121">Compare this to the W3C DOM, in which the XML document is used as a logical container for the XML tree.</span></span> <span data-ttu-id="87187-122">DOM'da, XML düğüm öğeleri ve öznitelikleri dahil olmak üzere, bir XML belgesi bağlamında oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="87187-122">In DOM, XML nodes, including elements and attributes, must be created in the context of an XML document.</span></span> <span data-ttu-id="87187-123">DOM'da bir name öğesi oluşturmak için kodun bir parçasını şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="87187-123">Here is a fragment of the code to create a name element in DOM:</span></span>  
  
```vb  
Dim doc As XmlDocument = New XmlDocument()  
Dim name As XmlElement = doc.CreateElement("Name")  
name.InnerText = "Patrick Hines"  
doc.AppendChild(name)  
```  
  
 <span data-ttu-id="87187-124">Bir öğe arasında birden çok belge kullanmak istiyorsanız, düğümleri belgeler arasında içeri aktarmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="87187-124">If you want to use an element across multiple documents, you must import the nodes across documents.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="87187-125"> Bu katman, karmaşıklığı ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="87187-125"> avoids this layer of complexity.</span></span>  
  
 <span data-ttu-id="87187-126">LINQ to XML kullanarak, kullandığınız <xref:System.Xml.Linq.XDocument> belgenin kök düzeyinde bir açıklama veya işleme yönergesi eklemek isterseniz sınıfı.</span><span class="sxs-lookup"><span data-stu-id="87187-126">When using LINQ to XML, you use the <xref:System.Xml.Linq.XDocument> class only if you want to add a comment or processing instruction at the root level of the document.</span></span>  
  
## <a name="simplified-handling-of-names-and-namespaces"></a><span data-ttu-id="87187-127">Basitleştirilmiş işleme adları ve ad alanları</span><span class="sxs-lookup"><span data-stu-id="87187-127">Simplified Handling of Names and Namespaces</span></span>  
 <span data-ttu-id="87187-128">Adları, ad alanları ve ad alanı öneklerini işleme genellikle karmaşık, bir XML programlama parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="87187-128">Handling names, namespaces, and namespace prefixes is generally a complex part of XML programming.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="87187-129"> adları ve ad alanları ile ad alanı öneklerini başa çıkma gereksinimi ortadan kaldırarak basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="87187-129"> simplifies names and namespaces by eliminating the requirement to deal with namespace prefixes.</span></span> <span data-ttu-id="87187-130">Ad alanı ön ekleri denetlemek istiyorsanız, bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87187-130">If you want to control namespace prefixes, you can.</span></span> <span data-ttu-id="87187-131">Ancak, ad alanı öneklerini açıkça denetlemek karar verirseniz [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] gereklidir veya yoksa varsayılan ad alanlarını kullanarak serileştirmek seri hale getirme sırasında ad alanı öneklerini atar.</span><span class="sxs-lookup"><span data-stu-id="87187-131">But if you decide to not explicitly control namespace prefixes, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will assign namespace prefixes during serialization if they are required, or will serialize using default namespaces if they are not.</span></span> <span data-ttu-id="87187-132">Varsayılan ad kullandıysanız, sonuçta elde edilen belgede hiçbir ad alanı öneklerini olacaktır.</span><span class="sxs-lookup"><span data-stu-id="87187-132">If default namespaces are used, there will be no namespace prefixes in the resulting document.</span></span> <span data-ttu-id="87187-133">Daha fazla bilgi için [(Visual Basic) XML ad alanları ile çalışma](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="87187-133">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="87187-134">Bu düğümün adını değiştirmenize izin vermez, DOM başka bir sorun var.</span><span class="sxs-lookup"><span data-stu-id="87187-134">Another problem with the DOM is that it does not let you change the name of a node.</span></span> <span data-ttu-id="87187-135">Bunun yerine, yeni bir düğüm oluştur ve tüm alt düğümleri, kopyalama özgün düğüm kimliğini kaybetme gerekir.</span><span class="sxs-lookup"><span data-stu-id="87187-135">Instead, you have to create a new node and copy all the child nodes to it, losing the original node identity.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="87187-136"> Ayarlanacak sağlayarak bu sorunu önler <xref:System.Xml.Linq.XName> düğümünde özelliği.</span><span class="sxs-lookup"><span data-stu-id="87187-136"> avoids this problem by enabling you to set the <xref:System.Xml.Linq.XName> property on a node.</span></span>  
  
## <a name="static-method-support-for-loading-xml"></a><span data-ttu-id="87187-137">XML yüklenirken statik yöntemi desteği</span><span class="sxs-lookup"><span data-stu-id="87187-137">Static Method Support for Loading XML</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="87187-138"> XML yerine örnek yöntemleri statik yöntemler kullanarak devredebilmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="87187-138"> lets you load XML by using static methods, instead of instance methods.</span></span> <span data-ttu-id="87187-139">Bu, yükleme ve ayrıştırma kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="87187-139">This simplifies loading and parsing.</span></span> <span data-ttu-id="87187-140">Daha fazla bilgi için [nasıl yapılır: yük XML dosyasından (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md).</span><span class="sxs-lookup"><span data-stu-id="87187-140">For more information, see [How to: Load XML from a File (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md).</span></span>  
  
## <a name="removal-of-support-for-dtd-constructs"></a><span data-ttu-id="87187-141">DTD yapıları desteğinin kaldırılması</span><span class="sxs-lookup"><span data-stu-id="87187-141">Removal of Support for DTD Constructs</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="87187-142"> Daha fazla XML varlıkları ve varlık başvuruları desteği kaldırarak programlama basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="87187-142"> further simplifies XML programming by removing support for entities and entity references.</span></span> <span data-ttu-id="87187-143">Varlık Yönetimi karmaşıktır ve nadiren kullanılır.</span><span class="sxs-lookup"><span data-stu-id="87187-143">The management of entities is complex, and is rarely used.</span></span> <span data-ttu-id="87187-144">Destek kaldırma performansı artırır ve programlama arabirimi basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="87187-144">Removing their support increases performance and simplifies the programming interface.</span></span> <span data-ttu-id="87187-145">Olduğunda bir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ağaç eklendiğinden, tüm DTD'nin varlıkları genişletilir.</span><span class="sxs-lookup"><span data-stu-id="87187-145">When a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tree is populated, all DTD entities are expanded.</span></span>  
  
## <a name="support-for-fragments"></a><span data-ttu-id="87187-146">Parçaları için destek</span><span class="sxs-lookup"><span data-stu-id="87187-146">Support for Fragments</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="87187-147"> için eşdeğer sağlamaz `XmlDocumentFragment` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="87187-147"> does not provide an equivalent for the `XmlDocumentFragment` class.</span></span> <span data-ttu-id="87187-148">Çoğu durumda, ancak `XmlDocumentFragment` kavram olarak yazılmış bir sorgu sonucunu tarafından işlenebilir <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XNode>, veya <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="87187-148">In many cases, however, the `XmlDocumentFragment` concept can be handled by the result of a query that is typed as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XNode>, or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="support-for-xpathnavigator"></a><span data-ttu-id="87187-149">XPathNavigator desteği</span><span class="sxs-lookup"><span data-stu-id="87187-149">Support for XPathNavigator</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="87187-150"> için destek sağlar <xref:System.Xml.XPath.XPathNavigator> alanında uzantı yöntemlerini aracılığıyla <xref:System.Xml.XPath?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="87187-150"> provides support for <xref:System.Xml.XPath.XPathNavigator> through extension methods in the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="87187-151">Daha fazla bilgi için bkz. <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="87187-151">For more information, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
## <a name="support-for-white-space-and-indentation"></a><span data-ttu-id="87187-152">Boşluk ve girinti desteği</span><span class="sxs-lookup"><span data-stu-id="87187-152">Support for White Space and Indentation</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="87187-153"> daha basit, boşluk işleme yerli daha</span><span class="sxs-lookup"><span data-stu-id="87187-153"> handles white space more simply than the DOM.</span></span>  
  
 <span data-ttu-id="87187-154">Sık karşılaşılan bir senaryodur girintili XML oku, herhangi bir boşluk metin düğümleri (diğer bir deyişle, beyaz boşluk olmayan koruma) olmadan bir bellek içi XML ağacı oluşturmak, bazı XML işlemleri ve XML girintilemeli kaydedin sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="87187-154">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="87187-155">Biçimlendirme ile XML serileştirme, yalnızca önemli boşluk XML ağacındaki korunur.</span><span class="sxs-lookup"><span data-stu-id="87187-155">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="87187-156">Varsayılan davranışı budur [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="87187-156">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="87187-157">Başka bir yaygın bir senaryo, okuma ve değiştirme kasıtlı olarak girintili zaten XML sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="87187-157">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="87187-158">Bu girinti herhangi bir şekilde değiştirmek istemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87187-158">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="87187-159">İçinde [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], yükleme veya XML Ayrıştırma beyaz alanı koruma ve XML serileştirme seçildiğinde biçimlendirmeyi devre dışı bırakma bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87187-159">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can do this by preserving white space when you load or parse the XML and disabling formatting when you serialize the XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="87187-160"> boşluk olarak depolayan bir <xref:System.Xml.Linq.XText> özelleştirilmiş yerine düğüm, <xref:System.Xml.XmlNodeType.Whitespace> DOM düğüm türü yapar.</span><span class="sxs-lookup"><span data-stu-id="87187-160"> stores white space as an <xref:System.Xml.Linq.XText> node, instead of having a specialized <xref:System.Xml.XmlNodeType.Whitespace> node type, as the DOM does.</span></span>  
  
## <a name="support-for-annotations"></a><span data-ttu-id="87187-161">Ek açıklamalar için destek</span><span class="sxs-lookup"><span data-stu-id="87187-161">Support for Annotations</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="87187-162"> öğeleri ek açıklamalarını genişletilebilir bir kümesini destekler.</span><span class="sxs-lookup"><span data-stu-id="87187-162"> elements support an extensible set of annotations.</span></span> <span data-ttu-id="87187-163">Bu şema bilgileri, bir kullanıcı Arabirimi için bağlı öğe olup olmadığını hakkında bilgi veya diğer tür uygulamaya özgü bilgileri gibi bir öğe hakkında diğer bilgileri izlemek için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="87187-163">This is useful for tracking miscellaneous information about an element, such as schema information, information about whether the element is bound to a UI, or any other kind of application-specific information.</span></span> <span data-ttu-id="87187-164">Daha fazla bilgi için [LINQ to XML ek açıklamaları](https://msdn.microsoft.com/library/e2f0052d-61e2-48d4-9ea4-356c9cab35d5).</span><span class="sxs-lookup"><span data-stu-id="87187-164">For more information, see [LINQ to XML Annotations](https://msdn.microsoft.com/library/e2f0052d-61e2-48d4-9ea4-356c9cab35d5).</span></span>  
  
## <a name="support-for-schema-information"></a><span data-ttu-id="87187-165">Şema bilgileri için destek</span><span class="sxs-lookup"><span data-stu-id="87187-165">Support for Schema Information</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="87187-166"> Uzantı yöntemleri aracılığıyla XSD doğrulaması için destek sağlar <xref:System.Xml.Schema?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="87187-166"> provides support for XSD validation through extension methods in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="87187-167">Bir XML ağacı bir XSD ile uyumlu olduğunu doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87187-167">You can validate that an XML tree complies with an XSD.</span></span> <span data-ttu-id="87187-168">XML ağacı sonrası schema doğrulama bilgi kümesi (PSVI) ile doldurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87187-168">You can populate the XML tree with the post-schema-validation infoset (PSVI).</span></span> <span data-ttu-id="87187-169">Daha fazla bilgi için [nasıl yapılır: doğrulama kullanarak XSD](https://msdn.microsoft.com/library/481a97fa-6e96-46f2-8c9a-415555fac33b) ve <xref:System.Xml.Schema.Extensions>.</span><span class="sxs-lookup"><span data-stu-id="87187-169">For more information, see [How to: Validate Using XSD](https://msdn.microsoft.com/library/481a97fa-6e96-46f2-8c9a-415555fac33b) and <xref:System.Xml.Schema.Extensions>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87187-170">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="87187-170">See Also</span></span>  
 [<span data-ttu-id="87187-171">Başlarken (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="87187-171">Getting Started (LINQ to XML)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
