---
title: LINQ to XML vs. DOM
ms.date: 07/20/2015
ms.assetid: 18c36130-d598-40b7-9007-828232252978
ms.openlocfilehash: b25993fba4d878beb881dfdc46effe5a8ab3485b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331697"
---
# <a name="linq-to-xml-vs-dom-visual-basic"></a><span data-ttu-id="23184-102">LINQ to XML vs DOM (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="23184-102">LINQ to XML vs. DOM (Visual Basic)</span></span>
<span data-ttu-id="23184-103">Bu bölümde [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ve geçerli önceden baskın XML programlama API 'SI, W3C Belge Nesne Modeli (DOM) arasındaki bazı önemli farklılıklar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="23184-103">This section describes some key differences between [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] and the current predominant XML programming API, the W3C Document Object Model (DOM).</span></span>  
  
## <a name="new-ways-to-construct-xml-trees"></a><span data-ttu-id="23184-104">XML ağaçları oluşturmak için yeni yollar</span><span class="sxs-lookup"><span data-stu-id="23184-104">New Ways to Construct XML Trees</span></span>  
 <span data-ttu-id="23184-105">W3C DOM 'da, aşağıdan yukarıya bir XML ağacı oluşturursunuz; diğer bir deyişle, bir belge oluşturur, öğeler oluşturur ve sonra öğeleri belgeye eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="23184-105">In the W3C DOM, you build an XML tree from the bottom up; that is, you create a document, you create elements, and then you add the elements to the document.</span></span>  
  
 <span data-ttu-id="23184-106">Örneğin, aşağıdaki, DOM 'ın Microsoft uygulamasını kullanarak bir XML ağacı oluşturmanın tipik bir yoludur <xref:System.Xml.XmlDocument>:</span><span class="sxs-lookup"><span data-stu-id="23184-106">For example, the following would be a typical way to create an XML tree using the Microsoft implementation of DOM, <xref:System.Xml.XmlDocument>:</span></span>  
  
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
  
 <span data-ttu-id="23184-107">Bu kodlama stili, XML ağacının yapısı hakkında görsel olarak çok fazla bilgi sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="23184-107">This style of coding does not visually provide much information about the structure of the XML tree.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="23184-108">, bir XML ağacı oluşturmak için bu yaklaşımı destekler, ancak alternatif bir yaklaşım, *işlevsel oluşturma*da destekler.</span><span class="sxs-lookup"><span data-stu-id="23184-108">supports this approach to constructing an XML tree, but also supports an alternative approach, *functional construction*.</span></span> <span data-ttu-id="23184-109">Visual Basic, işlevsel oluşturma bir XML ağacı oluşturmak için XML değişmez değerlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="23184-109">In Visual Basic, functional construction uses XML literals to build an XML tree.</span></span>  
  
 <span data-ttu-id="23184-110">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] işlevsel oluşturma kullanarak aynı XML ağacını nasıl oluşturabileceğiniz aşağıda açıklanmıştır:</span><span class="sxs-lookup"><span data-stu-id="23184-110">Here is how you would construct the same XML tree by using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] functional construction:</span></span>  
  
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
  
 <span data-ttu-id="23184-111">XML ağacını oluşturmak için kodun girintilendiği, temel alınan XML 'nin yapısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="23184-111">Notice that indenting the code to construct the XML tree shows the structure of the underlying XML.</span></span>  
  
 <span data-ttu-id="23184-112">Daha fazla bilgi için bkz. [xml ağaçları oluşturma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="23184-112">For more information, see [Creating XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span></span>  
  
## <a name="working-directly-with-xml-elements"></a><span data-ttu-id="23184-113">Doğrudan XML öğeleriyle çalışma</span><span class="sxs-lookup"><span data-stu-id="23184-113">Working Directly with XML Elements</span></span>  
 <span data-ttu-id="23184-114">XML ile programlama yaptığınızda, birincil odağınızı genellikle XML öğelerinde ve belki de özniteliklerde bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="23184-114">When you program with XML, your primary focus is usually on XML elements and perhaps on attributes.</span></span> <span data-ttu-id="23184-115">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], doğrudan XML öğeleri ve özniteliklerle çalışabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="23184-115">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can work directly with XML elements and attributes.</span></span> <span data-ttu-id="23184-116">Örneğin şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="23184-116">For example, you can do the following:</span></span>  
  
- <span data-ttu-id="23184-117">Bir belge nesnesi kullanmadan XML öğeleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="23184-117">Create XML elements without using a document object at all.</span></span> <span data-ttu-id="23184-118">Bu, XML ağaçlarının parçaları ile çalışmanız gerektiğinde programlamayı basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="23184-118">This simplifies programming when you have to work with fragments of XML trees.</span></span>  
  
- <span data-ttu-id="23184-119">Nesneleri doğrudan bir XML dosyasından yükleme `T:System.Xml.Linq.XElement`.</span><span class="sxs-lookup"><span data-stu-id="23184-119">Load `T:System.Xml.Linq.XElement` objects directly from an XML file.</span></span>  
  
- <span data-ttu-id="23184-120">`T:System.Xml.Linq.XElement` nesnelerini bir dosyaya veya akışa serileştirme.</span><span class="sxs-lookup"><span data-stu-id="23184-120">Serialize `T:System.Xml.Linq.XElement` objects to a file or a stream.</span></span>  
  
 <span data-ttu-id="23184-121">Bu, XML belgesinin XML ağacı için bir mantıksal kapsayıcı olarak kullanıldığı W3C DOM ile karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="23184-121">Compare this to the W3C DOM, in which the XML document is used as a logical container for the XML tree.</span></span> <span data-ttu-id="23184-122">DOM 'da, öğeler ve öznitelikler dahil XML düğümlerinin bir XML belgesi bağlamında oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="23184-122">In DOM, XML nodes, including elements and attributes, must be created in the context of an XML document.</span></span> <span data-ttu-id="23184-123">DOM 'da bir ad öğesi oluşturmak için kodun bir parçası aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="23184-123">Here is a fragment of the code to create a name element in DOM:</span></span>  
  
```vb  
Dim doc As XmlDocument = New XmlDocument()  
Dim name As XmlElement = doc.CreateElement("Name")  
name.InnerText = "Patrick Hines"  
doc.AppendChild(name)  
```  
  
 <span data-ttu-id="23184-124">Birden çok belge genelinde bir öğe kullanmak istiyorsanız düğümleri belgeler arasında içeri aktarmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="23184-124">If you want to use an element across multiple documents, you must import the nodes across documents.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="23184-125">bu karmaşıklık katmanını önler.</span><span class="sxs-lookup"><span data-stu-id="23184-125">avoids this layer of complexity.</span></span>  
  
 <span data-ttu-id="23184-126">LINQ to XML kullanırken, yalnızca belgenin kök düzeyinde bir yorum veya işleme yönergesi eklemek istiyorsanız <xref:System.Xml.Linq.XDocument> sınıfını kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="23184-126">When using LINQ to XML, you use the <xref:System.Xml.Linq.XDocument> class only if you want to add a comment or processing instruction at the root level of the document.</span></span>  
  
## <a name="simplified-handling-of-names-and-namespaces"></a><span data-ttu-id="23184-127">Adları ve ad alanlarını Basitleştirilmiş olarak Işleme</span><span class="sxs-lookup"><span data-stu-id="23184-127">Simplified Handling of Names and Namespaces</span></span>  
 <span data-ttu-id="23184-128">Adları, ad alanlarını ve ad alanı öneklerini işleme genellikle XML programlamanın karmaşık bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="23184-128">Handling names, namespaces, and namespace prefixes is generally a complex part of XML programming.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="23184-129">, ad alanı önekleriyle uğraşmak için gereksinimi ortadan kaldırarak adları ve ad alanlarını basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="23184-129">simplifies names and namespaces by eliminating the requirement to deal with namespace prefixes.</span></span> <span data-ttu-id="23184-130">Ad alanı öneklerini denetlemek istiyorsanız, kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="23184-130">If you want to control namespace prefixes, you can.</span></span> <span data-ttu-id="23184-131">Ancak ad alanı öneklerini açıkça denetistemediğinize karar verirseniz [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], gerektiğinde serileştirme sırasında ad alanı öneklerini atayacaktır veya varsayılan ad alanlarını kullanarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="23184-131">But if you decide to not explicitly control namespace prefixes, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will assign namespace prefixes during serialization if they are required, or will serialize using default namespaces if they are not.</span></span> <span data-ttu-id="23184-132">Varsayılan ad alanları kullanılırsa, sonuçta elde edilen belgede ad alanı önekleri olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="23184-132">If default namespaces are used, there will be no namespace prefixes in the resulting document.</span></span> <span data-ttu-id="23184-133">Daha fazla bilgi için bkz. [ad alanlarına genel bakış (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="23184-133">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="23184-134">DOM ile ilgili başka bir sorun da bir düğümün adını değiştirmenize izin vermez.</span><span class="sxs-lookup"><span data-stu-id="23184-134">Another problem with the DOM is that it does not let you change the name of a node.</span></span> <span data-ttu-id="23184-135">Bunun yerine, yeni bir düğüm oluşturmanız ve tüm alt düğümleri buna kopyalamanız ve özgün düğüm kimliğini kaybetmemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="23184-135">Instead, you have to create a new node and copy all the child nodes to it, losing the original node identity.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="23184-136">, bir düğümdeki <xref:System.Xml.Linq.XName> özelliğini ayarlamanıza olanak tanıyarak bu sorunu önler.</span><span class="sxs-lookup"><span data-stu-id="23184-136">avoids this problem by enabling you to set the <xref:System.Xml.Linq.XName> property on a node.</span></span>  
  
## <a name="static-method-support-for-loading-xml"></a><span data-ttu-id="23184-137">XML yükleme için statik yöntem desteği</span><span class="sxs-lookup"><span data-stu-id="23184-137">Static Method Support for Loading XML</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="23184-138">, örnek yöntemleri yerine statik yöntemler kullanarak XML yüklemenize imkan tanır.</span><span class="sxs-lookup"><span data-stu-id="23184-138">lets you load XML by using static methods, instead of instance methods.</span></span> <span data-ttu-id="23184-139">Bu, yükleme ve ayrıştırma işlemlerini basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="23184-139">This simplifies loading and parsing.</span></span> <span data-ttu-id="23184-140">Daha fazla bilgi için bkz. [nasıl yapılır: dosyadan XML yükleme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md).</span><span class="sxs-lookup"><span data-stu-id="23184-140">For more information, see [How to: Load XML from a File (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md).</span></span>  
  
## <a name="removal-of-support-for-dtd-constructs"></a><span data-ttu-id="23184-141">DTD yapıları için desteği kaldırma</span><span class="sxs-lookup"><span data-stu-id="23184-141">Removal of Support for DTD Constructs</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="23184-142">varlıklar ve varlık başvuruları desteğini kaldırarak XML programlamayı basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="23184-142">further simplifies XML programming by removing support for entities and entity references.</span></span> <span data-ttu-id="23184-143">Varlıkların yönetimi karmaşıktır ve nadiren kullanılır.</span><span class="sxs-lookup"><span data-stu-id="23184-143">The management of entities is complex, and is rarely used.</span></span> <span data-ttu-id="23184-144">Desteğinin kaldırılması performansı artırır ve programlama arabirimini basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="23184-144">Removing their support increases performance and simplifies the programming interface.</span></span> <span data-ttu-id="23184-145">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ağaç doldurulduktan sonra tüm DTD varlıkları genişletilir.</span><span class="sxs-lookup"><span data-stu-id="23184-145">When a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tree is populated, all DTD entities are expanded.</span></span>  
  
## <a name="support-for-fragments"></a><span data-ttu-id="23184-146">Parçalar için destek</span><span class="sxs-lookup"><span data-stu-id="23184-146">Support for Fragments</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="23184-147">, `XmlDocumentFragment` sınıfı için bir eşdeğer sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="23184-147">does not provide an equivalent for the `XmlDocumentFragment` class.</span></span> <span data-ttu-id="23184-148">Ancak çoğu durumda `XmlDocumentFragment` kavramı, <xref:System.Xml.Linq.XNode><xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Xml.Linq.XElement><xref:System.Collections.Generic.IEnumerable%601> olarak yazılmış bir sorgunun sonucu tarafından işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="23184-148">In many cases, however, the `XmlDocumentFragment` concept can be handled by the result of a query that is typed as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XNode>, or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="support-for-xpathnavigator"></a><span data-ttu-id="23184-149">XPathNavigator desteği</span><span class="sxs-lookup"><span data-stu-id="23184-149">Support for XPathNavigator</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="23184-150">, <xref:System.Xml.XPath?displayProperty=nameWithType> ad alanındaki genişletme yöntemleri aracılığıyla <xref:System.Xml.XPath.XPathNavigator> için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="23184-150">provides support for <xref:System.Xml.XPath.XPathNavigator> through extension methods in the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="23184-151">Daha fazla bilgi için bkz. <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="23184-151">For more information, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
## <a name="support-for-white-space-and-indentation"></a><span data-ttu-id="23184-152">Boşluk ve girintileme desteği</span><span class="sxs-lookup"><span data-stu-id="23184-152">Support for White Space and Indentation</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="23184-153">, DOM 'dan daha fazla boşluk işler.</span><span class="sxs-lookup"><span data-stu-id="23184-153">handles white space more simply than the DOM.</span></span>  
  
 <span data-ttu-id="23184-154">Yaygın bir senaryo, girintili XML 'yi okumak, boşluk metin düğümleri olmadan bir bellek içi XML ağacı oluşturmaktır (diğer bir deyişle, beyaz alanı korumadan), XML üzerinde bazı işlemleri gerçekleştirir ve ardından XML 'i girintilemeli olarak kaydeder.</span><span class="sxs-lookup"><span data-stu-id="23184-154">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="23184-155">XML 'yi biçimlendirme ile serileştirçalıştığınızda, XML ağacında yalnızca önemli boşluk korunur.</span><span class="sxs-lookup"><span data-stu-id="23184-155">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="23184-156">Bu, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]için varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="23184-156">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="23184-157">Diğer bir yaygın senaryo, daha önce kasıtlı olarak girintili olan XML 'i okuyup değiştirmektir.</span><span class="sxs-lookup"><span data-stu-id="23184-157">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="23184-158">Bu Girintiyi istediğiniz şekilde değiştirmek istemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="23184-158">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="23184-159">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], XML 'i yüklediğinizde veya ayrıştırdığınızda veya XML 'yi seri hale alırken biçimlendirmeyi devre dışı bıraktığınızda boşluğu koruyarak bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="23184-159">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can do this by preserving white space when you load or parse the XML and disabling formatting when you serialize the XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="23184-160">, DOM gibi özelleştirilmiş bir <xref:System.Xml.XmlNodeType.Whitespace> düğüm türüne sahip olmak yerine, alanı <xref:System.Xml.Linq.XText> bir düğüm olarak depolar.</span><span class="sxs-lookup"><span data-stu-id="23184-160">stores white space as an <xref:System.Xml.Linq.XText> node, instead of having a specialized <xref:System.Xml.XmlNodeType.Whitespace> node type, as the DOM does.</span></span>  
  
## <a name="support-for-annotations"></a><span data-ttu-id="23184-161">Ek açıklamalar için destek</span><span class="sxs-lookup"><span data-stu-id="23184-161">Support for Annotations</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="23184-162">öğeleri, genişletilebilir bir ek açıklama kümesini destekler.</span><span class="sxs-lookup"><span data-stu-id="23184-162">elements support an extensible set of annotations.</span></span> <span data-ttu-id="23184-163">Bu, şema bilgileri, öğenin bir kullanıcı arabirimine bağlanıp bağlanmayacağı veya başka bir uygulamaya özgü bilgi türü gibi bir öğeyle ilgili çeşitli bilgileri izlemek için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="23184-163">This is useful for tracking miscellaneous information about an element, such as schema information, information about whether the element is bound to a UI, or any other kind of application-specific information.</span></span> <span data-ttu-id="23184-164">Daha fazla bilgi için bkz. [LINQ to XML ek açıklamaları](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-annotations.md).</span><span class="sxs-lookup"><span data-stu-id="23184-164">For more information, see [LINQ to XML Annotations](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-annotations.md).</span></span>  
  
## <a name="support-for-schema-information"></a><span data-ttu-id="23184-165">Şema bilgileri için destek</span><span class="sxs-lookup"><span data-stu-id="23184-165">Support for Schema Information</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="23184-166">, <xref:System.Xml.Schema?displayProperty=nameWithType> ad alanındaki genişletme yöntemleri aracılığıyla XSD doğrulaması için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="23184-166">provides support for XSD validation through extension methods in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="23184-167">Bir XML ağacının bir XSD ile uyumlu olduğunu doğrulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="23184-167">You can validate that an XML tree complies with an XSD.</span></span> <span data-ttu-id="23184-168">XML ağacını şema-doğrulama sonrası bilgi kümesi (PSVı) ile doldurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="23184-168">You can populate the XML tree with the post-schema-validation infoset (PSVI).</span></span> <span data-ttu-id="23184-169">Daha fazla bilgi için bkz. [nasıl yapılır: xsd ve <xref:System.Xml.Schema.Extensions>kullanarak doğrulama](../../../../visual-basic/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md) .</span><span class="sxs-lookup"><span data-stu-id="23184-169">For more information, see [How to: Validate Using XSD](../../../../visual-basic/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md) and <xref:System.Xml.Schema.Extensions>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23184-170">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="23184-170">See also</span></span>

- [<span data-ttu-id="23184-171">Başlarken (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="23184-171">Getting Started (LINQ to XML)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
