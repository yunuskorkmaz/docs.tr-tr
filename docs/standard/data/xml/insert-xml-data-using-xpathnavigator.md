---
title: XPathNavigator Kullanarak XML Verileri Ekleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 2ed8c28b-b88d-4be7-9c87-92df01f0821f
ms.openlocfilehash: 1dbe1a709f7c1b527a1754ab943a0a10ff52c6e8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289193"
---
# <a name="insert-xml-data-using-xpathnavigator"></a><span data-ttu-id="13383-102">XPathNavigator Kullanarak XML Verileri Ekleme</span><span class="sxs-lookup"><span data-stu-id="13383-102">Insert XML Data using XPathNavigator</span></span>
<span data-ttu-id="13383-103">Sınıfı, bir <xref:System.Xml.XPath.XPathNavigator> XML belgesine eşdüzey, alt ve öznitelik düğümleri eklemek için kullanılan bir yöntemler kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="13383-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to insert sibling, child, and attribute nodes in an XML document.</span></span> <span data-ttu-id="13383-104">Bu yöntemleri kullanabilmeniz için <xref:System.Xml.XPath.XPathNavigator> nesnesi düzenlenebilir olmalıdır, yani <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> özelliği olmalıdır `true` .</span><span class="sxs-lookup"><span data-stu-id="13383-104">In order to use these methods, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be `true`.</span></span>  
  
 <span data-ttu-id="13383-105"><xref:System.Xml.XPath.XPathNavigator>bir XML belgesini düzenleyebilen nesneler, <xref:System.Xml.XmlDocument.CreateNavigator%2A> sınıfının yöntemiyle oluşturulur <xref:System.Xml.XmlDocument> .</span><span class="sxs-lookup"><span data-stu-id="13383-105"><xref:System.Xml.XPath.XPathNavigator> objects that can edit an XML document are created by the <xref:System.Xml.XmlDocument.CreateNavigator%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="13383-106"><xref:System.Xml.XPath.XPathNavigator>sınıfı tarafından oluşturulan nesneler <xref:System.Xml.XPath.XPathDocument> salt okunurdur ve bir <xref:System.Xml.XPath.XPathNavigator> nesne tarafından oluşturulan nesnenin Editing yöntemlerini kullanma girişimleri <xref:System.Xml.XPath.XPathDocument> bir ile sonuçlanır <xref:System.NotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="13383-106"><xref:System.Xml.XPath.XPathNavigator> objects created by the <xref:System.Xml.XPath.XPathDocument> class are read-only and any attempt to use the editing methods of an <xref:System.Xml.XPath.XPathNavigator> object created by an <xref:System.Xml.XPath.XPathDocument> object results in a <xref:System.NotSupportedException>.</span></span>  
  
 <span data-ttu-id="13383-107">Düzenlenebilir nesneler oluşturma hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator> bkz. [XPathDocument ve XMLDOCUMENT kullanarak XML verilerini okuma](reading-xml-data-using-xpathdocument-and-xmldocument.md).</span><span class="sxs-lookup"><span data-stu-id="13383-107">For more information about creating editable <xref:System.Xml.XPath.XPathNavigator> objects, see [Reading XML Data using XPathDocument and XmlDocument](reading-xml-data-using-xpathdocument-and-xmldocument.md).</span></span>  
  
## <a name="inserting-nodes"></a><span data-ttu-id="13383-108">Düğüm ekleme</span><span class="sxs-lookup"><span data-stu-id="13383-108">Inserting Nodes</span></span>  
 <span data-ttu-id="13383-109"><xref:System.Xml.XPath.XPathNavigator>Sınıfı, BIR XML belgesine eşdüzey, alt ve öznitelik düğümleri eklemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="13383-109">The <xref:System.Xml.XPath.XPathNavigator> class provides methods to insert sibling, child, and attribute nodes in an XML document.</span></span> <span data-ttu-id="13383-110">Bu yöntemler, bir nesnenin geçerli konumuyla ilişkili olarak farklı konumlara düğüm ve öznitelik eklemenize olanak sağlar <xref:System.Xml.XPath.XPathNavigator> ve aşağıdaki bölümlerde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="13383-110">These methods allow you to insert nodes and attributes in different locations in relation to the current position of an <xref:System.Xml.XPath.XPathNavigator> object and are described in the following sections.</span></span>  
  
### <a name="inserting-sibling-nodes"></a><span data-ttu-id="13383-111">Eşdüzey düğümler ekleme</span><span class="sxs-lookup"><span data-stu-id="13383-111">Inserting Sibling Nodes</span></span>  
 <span data-ttu-id="13383-112"><xref:System.Xml.XPath.XPathNavigator>Sınıfı eşdüzey düğümleri eklemek için aşağıdaki yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="13383-112">The <xref:System.Xml.XPath.XPathNavigator> class provides the following methods to insert sibling nodes.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A>  
  
 <span data-ttu-id="13383-113">Bu yöntemler, bir <xref:System.Xml.XPath.XPathNavigator> nesne üzerinde konumlanan düğümden önce ve sonra eşdüzey düğümler ekler.</span><span class="sxs-lookup"><span data-stu-id="13383-113">These methods insert sibling nodes before and after the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="13383-114"><xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>Ve <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> yöntemleri aşırı yüklenmiş ve `string` <xref:System.Xml.XmlReader> <xref:System.Xml.XPath.XPathNavigator> parametre olarak eklenecek eşdüzey düğümü içeren bir, nesne veya nesne kabul eder.</span><span class="sxs-lookup"><span data-stu-id="13383-114">The <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> methods are overloaded and accept a `string`, <xref:System.Xml.XmlReader> object, or <xref:System.Xml.XPath.XPathNavigator> object containing the sibling node to add as parameters.</span></span> <span data-ttu-id="13383-115">Her iki yöntem de <xref:System.Xml.XmlWriter> eşdüzey düğümleri eklemek için kullanılan bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="13383-115">Both methods also return an <xref:System.Xml.XmlWriter> object used to insert sibling nodes.</span></span>  
  
 <span data-ttu-id="13383-116"><xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A>Ve <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> yöntemleri, bir nesneden önce ve sonra bir <xref:System.Xml.XPath.XPathNavigator> nesne, ad alanı ön eki, yerel adı, ad alanı URI 'si ve parametre olarak belirtilen değer kullanılarak konumlandırılmış olan bir eşdüzey düğüm ekler.</span><span class="sxs-lookup"><span data-stu-id="13383-116">The <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> methods insert a single sibling node before and after the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on using the namespace prefix, local name, namespace URI, and value specified as parameters.</span></span>  
  
 <span data-ttu-id="13383-117">Aşağıdaki örnekte, `pages` `price` dosyasındaki ilk öğenin alt öğesinden önce yeni bir öğe eklenir `book` `contosoBooks.xml` .</span><span class="sxs-lookup"><span data-stu-id="13383-117">In the following example a new `pages` element is inserted before the `price` child element of the first `book` element in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#19](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#19)]
 [!code-csharp[XPathNavigatorMethods#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#19)]
 [!code-vb[XPathNavigatorMethods#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#19)]  
  
 <span data-ttu-id="13383-118">Örnek, `contosoBooks.xml` dosyayı bir giriş olarak alır.</span><span class="sxs-lookup"><span data-stu-id="13383-118">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="13383-119">, Ve yöntemleri hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> bkz <xref:System.Xml.XPath.XPathNavigator> . sınıf başvurusu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="13383-119">For more information about the <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> methods, see the <xref:System.Xml.XPath.XPathNavigator> class reference documentation.</span></span>  
  
### <a name="inserting-child-nodes"></a><span data-ttu-id="13383-120">Alt düğümler ekleniyor</span><span class="sxs-lookup"><span data-stu-id="13383-120">Inserting Child Nodes</span></span>  
 <span data-ttu-id="13383-121"><xref:System.Xml.XPath.XPathNavigator>Sınıfı alt düğümleri eklemek için aşağıdaki yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="13383-121">The <xref:System.Xml.XPath.XPathNavigator> class provides the following methods to insert child nodes.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A>  
  
 <span data-ttu-id="13383-122">Bu yöntemler, alt düğümleri sonuna ekler ve sonuna eklenmiş olan düğüm alt düğümleri listesinin başlangıcına <xref:System.Xml.XPath.XPathNavigator> eklenir.</span><span class="sxs-lookup"><span data-stu-id="13383-122">These methods append and prepend child nodes to the end of and the beginning of the list of child nodes of the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="13383-123">"Eşdüzey düğüm ekleme" bölümündeki Yöntemler gibi, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> ve <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> yöntemleri `string` <xref:System.Xml.XmlReader> <xref:System.Xml.XPath.XPathNavigator> parametre olarak eklenecek alt düğümü içeren bir, nesne veya nesne kabul eder.</span><span class="sxs-lookup"><span data-stu-id="13383-123">Like the methods in the "Inserting Sibling Nodes" section, the <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> methods accept a `string`, <xref:System.Xml.XmlReader> object, or <xref:System.Xml.XPath.XPathNavigator> object containing the child node to add as parameters.</span></span> <span data-ttu-id="13383-124">Her iki yöntem de <xref:System.Xml.XmlWriter> alt düğüm eklemek için kullanılan bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="13383-124">Both methods also return an <xref:System.Xml.XmlWriter> object used to insert child nodes.</span></span>  
  
 <span data-ttu-id="13383-125">Ayrıca, "eşdüzey düğüm ekleme" bölümündeki Yöntemler gibi, <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> ve yöntemleri, ' <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> nin sonuna tek bir alt düğüm ekler ve bir <xref:System.Xml.XPath.XPathNavigator> nesne şu anda ad alanı ön eki, yerel ad, ad alanı URI 'si ve parametre olarak belirtilen değer kullanılarak konumlandırılmış.</span><span class="sxs-lookup"><span data-stu-id="13383-125">Also like the methods in the "Inserting Sibling Nodes" section, the <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> methods insert a single child node to the end of and the beginning of the list of child nodes of the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on using the namespace prefix, local name, namespace URI, and value specified as parameters.</span></span>  
  
 <span data-ttu-id="13383-126">Aşağıdaki örnekte, `pages` dosyasındaki ilk öğenin alt öğeleri listesine yeni bir alt öğe eklenir `book` `contosoBooks.xml` .</span><span class="sxs-lookup"><span data-stu-id="13383-126">In the following example, a new `pages` child element is appended to the list of child elements of the first `book` element in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#2)]
 [!code-csharp[XPathNavigatorMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#2)]
 [!code-vb[XPathNavigatorMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#2)]  
  
 <span data-ttu-id="13383-127">Örnek, `contosoBooks.xml` dosyayı bir giriş olarak alır.</span><span class="sxs-lookup"><span data-stu-id="13383-127">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="13383-128">, Ve yöntemleri hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> bkz <xref:System.Xml.XPath.XPathNavigator> . sınıf başvurusu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="13383-128">For more information about the <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> methods, see the <xref:System.Xml.XPath.XPathNavigator> class reference documentation.</span></span>  
  
### <a name="inserting-attribute-nodes"></a><span data-ttu-id="13383-129">Öznitelik düğümleri ekleniyor</span><span class="sxs-lookup"><span data-stu-id="13383-129">Inserting Attribute Nodes</span></span>  
 <span data-ttu-id="13383-130"><xref:System.Xml.XPath.XPathNavigator>Sınıfı, öznitelik düğümleri eklemek için aşağıdaki yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="13383-130">The <xref:System.Xml.XPath.XPathNavigator> class provides the following methods to insert attribute nodes.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A>  
  
 <span data-ttu-id="13383-131">Bu yöntemler, bir nesne üzerinde konumlandırılmış olan öğe düğümüne öznitelik düğümleri ekler <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="13383-131">These methods insert attribute nodes on the element node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="13383-132"><xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A>Yöntemi, bir <xref:System.Xml.XPath.XPathNavigator> nesne şu anda ad alanı ön eki, yerel ad, ad alanı URI 'si ve parametre olarak belirtilen değer kullanılarak konumlandırılmış olan öğe düğümünde bir öznitelik düğümü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="13383-132">The <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> method creates an attribute node on the element node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on using the namespace prefix, local name, namespace URI, and value specified as parameters.</span></span> <span data-ttu-id="13383-133"><xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A>Yöntemi <xref:System.Xml.XmlWriter> öznitelik düğümleri eklemek için kullanılan bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="13383-133">The <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> method returns an <xref:System.Xml.XmlWriter> object used to insert attribute nodes.</span></span>  
  
 <span data-ttu-id="13383-134">Aşağıdaki örnekte, `discount` `currency` `price` `book` `contosoBooks.xml` yönteminden döndürülen nesneyi kullanarak dosyadaki ilk öğenin alt öğesinde yeni ve öznitelikleri oluşturulur <xref:System.Xml.XmlWriter> <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> .</span><span class="sxs-lookup"><span data-stu-id="13383-134">In the following example, new `discount` and `currency` attributes are created on the `price` child element of the first `book` element in the `contosoBooks.xml` file using the <xref:System.Xml.XmlWriter> object returned from the <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> method.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#8](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#8)]
 [!code-csharp[XPathNavigatorMethods#8](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#8)]
 [!code-vb[XPathNavigatorMethods#8](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#8)]  
  
 <span data-ttu-id="13383-135">Örnek, `contosoBooks.xml` dosyayı bir giriş olarak alır.</span><span class="sxs-lookup"><span data-stu-id="13383-135">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="13383-136">Ve yöntemleri hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> bkz <xref:System.Xml.XPath.XPathNavigator> . sınıf başvurusu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="13383-136">For more information about the <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> and <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> methods, see the <xref:System.Xml.XPath.XPathNavigator> class reference documentation.</span></span>  
  
## <a name="copying-nodes"></a><span data-ttu-id="13383-137">Düğümler kopyalanıyor</span><span class="sxs-lookup"><span data-stu-id="13383-137">Copying Nodes</span></span>  
 <span data-ttu-id="13383-138">Belirli durumlarda, bir XML belgesini başka bir XML belgesinden içerik ile doldurmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13383-138">In certain cases you may want to populate an XML document with the contents from another XML document.</span></span> <span data-ttu-id="13383-139">Hem <xref:System.Xml.XPath.XPathNavigator> sınıf hem de <xref:System.Xml.XmlWriter> sınıf, düğümleri varolan bir <xref:System.Xml.XmlDocument> <xref:System.Xml.XmlReader> nesne veya nesneden bir nesneye kopyalayabilir <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="13383-139">Both the <xref:System.Xml.XPath.XPathNavigator> class and the <xref:System.Xml.XmlWriter> class can copy nodes to an <xref:System.Xml.XmlDocument> object from an existing <xref:System.Xml.XmlReader> object or <xref:System.Xml.XPath.XPathNavigator> object.</span></span>  
  
 <span data-ttu-id="13383-140"><xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>Sınıfının, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> ve <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> yöntemlerinin hepsi bir <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XPath.XPathNavigator> nesne veya <xref:System.Xml.XmlReader> nesneyi parametre olarak kabul edebilecek aşırı yüklemeleridir.</span><span class="sxs-lookup"><span data-stu-id="13383-140">The <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class all have overloads that can accept an <xref:System.Xml.XPath.XPathNavigator> object or an <xref:System.Xml.XmlReader> object as a parameter.</span></span>  
  
 <span data-ttu-id="13383-141"><xref:System.Xml.XmlWriter.WriteNode%2A>Sınıfının yönteminde,, <xref:System.Xml.XmlWriter> <xref:System.Xml.XmlNode> <xref:System.Xml.XmlReader> veya nesnesini kabul edebilecek aşırı yüklemeler vardır <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="13383-141">The <xref:System.Xml.XmlWriter.WriteNode%2A> method of the <xref:System.Xml.XmlWriter> class has overloads that can accept an <xref:System.Xml.XmlNode>, <xref:System.Xml.XmlReader>, or <xref:System.Xml.XPath.XPathNavigator> object.</span></span>  
  
 <span data-ttu-id="13383-142">Aşağıdaki örnek, tüm `book` öğeleri bir belgeden diğerine kopyalar.</span><span class="sxs-lookup"><span data-stu-id="13383-142">The following example copies all the `book` elements from one document to another.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", String.Empty)  
  
Dim newBooks As XPathDocument = New XPathDocument("newBooks.xml")  
Dim newBooksNavigator As XPathNavigator = newBooks.CreateNavigator()  
  
Dim nav As XPathNavigator  
For Each nav in newBooksNavigator.SelectDescendants("book", "", false)  
    navigator.AppendChild(nav)  
Next  
  
document.Save("newBooks.xml");  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", String.Empty);  
  
XPathDocument newBooks = new XPathDocument("newBooks.xml");  
XPathNavigator newBooksNavigator = newBooks.CreateNavigator();  
  
foreach (XPathNavigator nav in newBooksNavigator.SelectDescendants("book", "", false))  
{  
    navigator.AppendChild(nav);  
}  
  
document.Save("newBooks.xml");  
```  
  
## <a name="inserting-values"></a><span data-ttu-id="13383-143">Değer ekleme</span><span class="sxs-lookup"><span data-stu-id="13383-143">Inserting Values</span></span>  
 <span data-ttu-id="13383-144"><xref:System.Xml.XPath.XPathNavigator>Sınıfı, <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> bir düğümün değerlerini bir nesnesine eklemek için ve yöntemlerini sağlar <xref:System.Xml.XmlDocument> .</span><span class="sxs-lookup"><span data-stu-id="13383-144">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods to insert values for a node into an <xref:System.Xml.XmlDocument> object.</span></span>  
  
### <a name="inserting-untyped-values"></a><span data-ttu-id="13383-145">Türsüz değerler ekleme</span><span class="sxs-lookup"><span data-stu-id="13383-145">Inserting Untyped Values</span></span>  
 <span data-ttu-id="13383-146"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A>Yöntemi, `string` bir parametre olarak geçirilen türsüz değeri <xref:System.Xml.XPath.XPathNavigator> nesnenin şu anda konumlandırılmış olan düğümün değeri olarak ekler.</span><span class="sxs-lookup"><span data-stu-id="13383-146">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method simply inserts the untyped `string` value passed as a parameter as the value of the node the <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="13383-147">Değer, herhangi bir tür olmadan veya şema bilgileri kullanılabiliyorsa düğüm türüne göre yeni değerin geçerli olduğunu doğrulamadan eklenir.</span><span class="sxs-lookup"><span data-stu-id="13383-147">The value is inserted without any type or without verifying that the new value is valid according to the type of the node if schema information is available.</span></span>  
  
 <span data-ttu-id="13383-148">Aşağıdaki örnekte, <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> yöntemi dosyadaki tüm öğeleri güncelleştirmek için kullanılır `price` `contosoBooks.xml` .</span><span class="sxs-lookup"><span data-stu-id="13383-148">In the following example, the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method is used to update all `price` elements in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 <span data-ttu-id="13383-149">Örnek, `contosoBooks.xml` dosyayı bir giriş olarak alır.</span><span class="sxs-lookup"><span data-stu-id="13383-149">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="inserting-typed-values"></a><span data-ttu-id="13383-150">Yazılan değerler ekleniyor</span><span class="sxs-lookup"><span data-stu-id="13383-150">Inserting Typed Values</span></span>  
 <span data-ttu-id="13383-151">Bir düğümün türü bir W3C XML şeması basit türü olduğunda, yöntemi tarafından yerleştirilen yeni değer, <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> değer ayarlanmadan önce basit türdeki modellerle denetlenir.</span><span class="sxs-lookup"><span data-stu-id="13383-151">When the type of a node is a W3C XML Schema simple type, the new value inserted by the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method is checked against the facets of the simple type before the value is set.</span></span> <span data-ttu-id="13383-152">Yeni değer, düğüm türüne göre geçerli değilse (örneğin, `-1` türü olan bir öğe üzerinde değerini ayarlamak `xs:positiveInteger` ), bir özel durumla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="13383-152">If the new value is not valid according to the type of the node (for example, setting a value of `-1` on an element whose type is `xs:positiveInteger`), it results in an exception.</span></span>  
  
 <span data-ttu-id="13383-153">Aşağıdaki örnek, `price` dosyasındaki ilk öğe öğesinin değerini `book` `contosoBooks.xml` bir değere değiştirmeye çalışır <xref:System.DateTime> .</span><span class="sxs-lookup"><span data-stu-id="13383-153">The following example attempts to change the value of the `price` element of the first `book` element in the `contosoBooks.xml` file to a <xref:System.DateTime> value.</span></span> <span data-ttu-id="13383-154">Öğesinin XML şeması türü `price` dosyalarda olarak tanımlandığından `xs:decimal` `contosoBooks.xsd` , bu durum bir özel durumla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="13383-154">Because the XML Schema type of the `price` element is defined as `xs:decimal` in the `contosoBooks.xsd` files, this results in an exception.</span></span>  
  
```vb  
Dim settings As XmlReaderSettings = New XmlReaderSettings()  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
settings.ValidationType = ValidationType.Schema  
  
Dim reader As XmlReader = XmlReader.Create("contosoBooks.xml", settings)  
  
Dim document As XmlDocument = New XmlDocument()  
document.Load(reader)  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.SetTypedValue(DateTime.Now)  
```  
  
```csharp  
XmlReaderSettings settings = new XmlReaderSettings();  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
settings.ValidationType = ValidationType.Schema;  
  
XmlReader reader = XmlReader.Create("contosoBooks.xml", settings);  
  
XmlDocument document = new XmlDocument();  
document.Load(reader);  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.SetTypedValue(DateTime.Now);  
```  
  
 <span data-ttu-id="13383-155">Örnek, `contosoBooks.xml` dosyayı bir giriş olarak alır.</span><span class="sxs-lookup"><span data-stu-id="13383-155">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="13383-156">Örnek de `contosoBooks.xsd` bir giriş olarak alır.</span><span class="sxs-lookup"><span data-stu-id="13383-156">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
## <a name="the-innerxml-and-outerxml-properties"></a><span data-ttu-id="13383-157">InnerXml ve OuterXml özellikleri</span><span class="sxs-lookup"><span data-stu-id="13383-157">The InnerXml and OuterXml Properties</span></span>  
 <span data-ttu-id="13383-158"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A>Sınıfının ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> Özellikleri, <xref:System.Xml.XPath.XPathNavigator> bir <xref:System.Xml.XPath.XPathNavigator> nesnenin şu anda konumlandırılmış olduğu düğümlerin XML işaretlemesini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="13383-158">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class change the XML markup of the nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="13383-159"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A>Özelliği, <xref:System.Xml.XPath.XPathNavigator> belirtilen XML 'nin ayrıştırılmış içeriğiyle bir nesne şu anda konumlandırılmış olan alt düğümlerin XML işaretlemesini değiştirir `string` .</span><span class="sxs-lookup"><span data-stu-id="13383-159">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on with the parsed contents of the given XML `string`.</span></span> <span data-ttu-id="13383-160">Benzer şekilde, <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özelliği de bir nesnenin şu anda bulunduğu alt DÜĞÜMLERIN XML işaretlemesini ve <xref:System.Xml.XPath.XPathNavigator> geçerli düğümün kendisini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="13383-160">Similarly, the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on as well as the current node itself.</span></span>  
  
 <span data-ttu-id="13383-161">Bu konuda açıklanan yöntemlere ek olarak, <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> ÖZELLIKLERI bir XML belgesine düğüm ve değer eklemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="13383-161">In addition to the methods described in this topic, the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties can be used to insert nodes and values in an XML document.</span></span> <span data-ttu-id="13383-162"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A>Ve özelliklerini kullanarak düğüm ve değer ekleme hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> bkz. [XPathNavigator kullanarak XML verilerini değiştirme](modify-xml-data-using-xpathnavigator.md) konusu.</span><span class="sxs-lookup"><span data-stu-id="13383-162">For more information about using the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties to insert nodes and values, see the [Modify XML Data using XPathNavigator](modify-xml-data-using-xpathnavigator.md) topic.</span></span>  
  
## <a name="namespace-and-xmllang-conflicts"></a><span data-ttu-id="13383-163">Namespace ve XML: lang çakışmaları</span><span class="sxs-lookup"><span data-stu-id="13383-163">Namespace and xml:lang Conflicts</span></span>  
 <span data-ttu-id="13383-164">Ad alanı ve bildirimlerin kapsamı ile ilgili bazı çakışmalar `xml:lang` <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> , <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> <xref:System.Xml.XPath.XPathNavigator> nesneleri parametre olarak alan sınıfın,, ve yöntemlerini kullanarak XML verileri eklenirken meydana gelebilir <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="13383-164">Certain conflicts related to the scope of namespace and `xml:lang` declarations can occur when inserting XML data using the <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class that take <xref:System.Xml.XmlReader> objects as parameters.</span></span>  
  
 <span data-ttu-id="13383-165">Olası ad alanı çakışmaları aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="13383-165">The following are the possible namespace conflicts.</span></span>  
  
- <span data-ttu-id="13383-166">Nesne bağlamında kapsam içinde bir ad alanı varsa <xref:System.Xml.XmlReader> , ad alanı URI eşlemesinin öneki <xref:System.Xml.XPath.XPathNavigator> nesnenin bağlamında değilse, yeni eklenen düğüme yeni bir ad alanı bildirimi eklenir.</span><span class="sxs-lookup"><span data-stu-id="13383-166">If there is a namespace in-scope within the <xref:System.Xml.XmlReader> object's context, where the prefix to namespace URI mapping is not in the <xref:System.Xml.XPath.XPathNavigator> object's context, a new namespace declaration is added to the newly inserted node.</span></span>  
  
- <span data-ttu-id="13383-167">Aynı ad alanı URI 'SI hem <xref:System.Xml.XmlReader> nesnenin bağlamı hem de nesnenin bağlamı içinde kapsam içindeyse <xref:System.Xml.XPath.XPathNavigator> , ancak her iki bağlamda da eşlenmiş farklı bir ön eke sahipse, yeni eklenen düğüme yeni bir ad alanı bildirimi eklenir, önek ve ad alanı URI 'si <xref:System.Xml.XmlReader> nesneden alınır.</span><span class="sxs-lookup"><span data-stu-id="13383-167">If the same namespace URI is in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but has a different prefix mapped to it in both contexts, a new namespace declaration is added to the newly inserted node, with the prefix and namespace URI taken from the <xref:System.Xml.XmlReader> object.</span></span>  
  
- <span data-ttu-id="13383-168">Aynı ad alanı öneki hem <xref:System.Xml.XmlReader> nesnenin bağlamı hem de nesnenin bağlamı içinde kapsam içindeyse <xref:System.Xml.XPath.XPathNavigator> , ancak her iki bağlamda de kendisine eşlenmiş farklı bir ad alanı URI 'si varsa, yeni eklenen düğüme, bu öneki nesnesinden alınan ad alanı URI 'si ile yeniden bildiren yeni bir ad alanı bildirimi eklenir <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="13383-168">If the same namespace prefix is in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but has a different namespace URI mapped to it in both contexts, a new namespace declaration is added to the newly inserted node which re-declares that prefix with the namespace URI taken from <xref:System.Xml.XmlReader> object.</span></span>  
  
- <span data-ttu-id="13383-169">Hem <xref:System.Xml.XmlReader> nesnenin bağlamında hem de nesnenin bağlamı aynı olan önek ve ad alanı URI 'si <xref:System.Xml.XPath.XPathNavigator> aynıysa, yeni eklenen düğüme yeni bir ad alanı bildirimi eklenmez.</span><span class="sxs-lookup"><span data-stu-id="13383-169">If the prefix as well as the namespace URI in both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context is the same, no new namespace declaration is added to the newly inserted node.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="13383-170">Yukarıdaki açıklama, bir ön ek olarak boş ad alanı bildirimleri için de geçerlidir `string` (örneğin, varsayılan ad alanı bildirimi).</span><span class="sxs-lookup"><span data-stu-id="13383-170">The description above also applies to namespace declarations with the empty `string` as a prefix (for example, the default namespace declaration).</span></span>  
  
 <span data-ttu-id="13383-171">Olası `xml:lang` Çakışmalar şunlardır.</span><span class="sxs-lookup"><span data-stu-id="13383-171">The following are the possible `xml:lang` conflicts.</span></span>  
  
- <span data-ttu-id="13383-172">Nesnenin `xml:lang` bağlamı içinde kapsam içinde olmayan bir öznitelik varsa <xref:System.Xml.XmlReader> , ancak nesne <xref:System.Xml.XPath.XPathNavigator> bağlamında, `xml:lang` değeri nesnesinden alınmış olan bir öznitelik <xref:System.Xml.XmlReader> yeni eklenen düğüme eklenir.</span><span class="sxs-lookup"><span data-stu-id="13383-172">If there is an `xml:lang` attribute in-scope within the <xref:System.Xml.XmlReader> object's context but not in the <xref:System.Xml.XPath.XPathNavigator> object's context, an `xml:lang` attribute whose value is taken from the <xref:System.Xml.XmlReader> object is added to the newly inserted node.</span></span>  
  
- <span data-ttu-id="13383-173">`xml:lang`Hem nesnenin bağlamı hem de nesnenin bağlamı içinde kapsam içinde bir öznitelik varsa <xref:System.Xml.XmlReader> <xref:System.Xml.XPath.XPathNavigator> , ancak her biri farklı bir değere sahipse, `xml:lang` değeri nesnesinden alınmış olan bir öznitelik <xref:System.Xml.XmlReader> yeni eklenen düğüme eklenir.</span><span class="sxs-lookup"><span data-stu-id="13383-173">If there is an `xml:lang` attribute in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but each has a different value, an `xml:lang` attribute whose value is taken from the <xref:System.Xml.XmlReader> object is added to the newly inserted node.</span></span>  
  
- <span data-ttu-id="13383-174">`xml:lang`Hem nesnenin bağlamı hem de nesnenin bağlamı içinde kapsam içinde bir öznitelik varsa <xref:System.Xml.XmlReader> <xref:System.Xml.XPath.XPathNavigator> , ancak her biri aynı değere sahip ise, yeni `xml:lang` eklenen düğüme yeni bir öznitelik eklenmez.</span><span class="sxs-lookup"><span data-stu-id="13383-174">If there is an `xml:lang` attribute in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but each with the same value, no new `xml:lang` attribute is added on the newly inserted node.</span></span>  
  
- <span data-ttu-id="13383-175">`xml:lang`Nesnenin bağlamı içinde kapsam içinde bir öznitelik varsa <xref:System.Xml.XPath.XPathNavigator> ancak <xref:System.Xml.XmlReader> nesnenin bağlamında yok, `xml:lang` yeni eklenen düğüme hiçbir öznitelik eklenmez.</span><span class="sxs-lookup"><span data-stu-id="13383-175">If there is an `xml:lang` attribute in-scope within the <xref:System.Xml.XPath.XPathNavigator> object's context, but none existing in the <xref:System.Xml.XmlReader> object's context, no `xml:lang` attribute is added to the newly inserted node.</span></span>  
  
## <a name="inserting-nodes-with-xmlwriter"></a><span data-ttu-id="13383-176">XmlWriter ile düğüm ekleme</span><span class="sxs-lookup"><span data-stu-id="13383-176">Inserting Nodes with XmlWriter</span></span>  
 <span data-ttu-id="13383-177">"Düğüm ve değer ekleme" bölümünde açıklanan eşdüzey, alt ve öznitelik düğümlerini eklemek için kullanılan yöntemler aşırı yüklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="13383-177">The methods used to insert sibling, child and attribute nodes described in the "Inserting Nodes and Values" section are overloaded.</span></span> <span data-ttu-id="13383-178"><xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>Sınıfının, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> , <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> ve yöntemleri, <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XmlWriter> düğümleri eklemek için kullanılan bir nesne döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="13383-178">The <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> and <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class return an <xref:System.Xml.XmlWriter> object used to insert nodes.</span></span>  
  
### <a name="unsupported-xmlwriter-methods"></a><span data-ttu-id="13383-179">Desteklenmeyen XmlWriter yöntemleri</span><span class="sxs-lookup"><span data-stu-id="13383-179">Unsupported XmlWriter Methods</span></span>  
 <span data-ttu-id="13383-180">Sınıf kullanarak bir XML belgesine bilgi yazmak için kullanılan yöntemlerin hepsi, <xref:System.Xml.XmlWriter> <xref:System.Xml.XPath.XPathNavigator> XPath veri modeli ve belge nesne MODELI (DOM) arasındaki fark nedeniyle sınıfı tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="13383-180">Not all of the methods used for writing information to an XML document using the <xref:System.Xml.XmlWriter> class are supported by the <xref:System.Xml.XPath.XPathNavigator> class due to difference between the XPath data model and the Document Object Model (DOM).</span></span>  
  
 <span data-ttu-id="13383-181">Aşağıdaki tablo, <xref:System.Xml.XmlWriter> sınıfı tarafından desteklenmeyen sınıf yöntemlerini açıklar <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="13383-181">The following table describes the <xref:System.Xml.XmlWriter> class methods not supported by the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
|<span data-ttu-id="13383-182">Yöntem</span><span class="sxs-lookup"><span data-stu-id="13383-182">Method</span></span>|<span data-ttu-id="13383-183">Description</span><span class="sxs-lookup"><span data-stu-id="13383-183">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.XmlWriter.WriteEntityRef%2A>|<span data-ttu-id="13383-184">Bir <xref:System.NotSupportedException> özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="13383-184">Throws a <xref:System.NotSupportedException> exception.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteDocType%2A>|<span data-ttu-id="13383-185">Kök düzeyinde yok sayılır ve <xref:System.NotSupportedException> XML belgesinde başka bir düzeyde çağrılırsa bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="13383-185">Ignored at the root level and throws a <xref:System.NotSupportedException> exception if called at any other level in the XML document.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteCData%2A>|<span data-ttu-id="13383-186"><xref:System.Xml.XmlWriter.WriteString%2A>Eşdeğer karakter veya karakterler için yönteme çağrı olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="13383-186">Treated as a call to the <xref:System.Xml.XmlWriter.WriteString%2A> method for the equivalent character or characters.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteCharEntity%2A>|<span data-ttu-id="13383-187"><xref:System.Xml.XmlWriter.WriteString%2A>Eşdeğer karakter veya karakterler için yönteme çağrı olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="13383-187">Treated as a call to the <xref:System.Xml.XmlWriter.WriteString%2A> method for the equivalent character or characters.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteSurrogateCharEntity%2A>|<span data-ttu-id="13383-188"><xref:System.Xml.XmlWriter.WriteString%2A>Eşdeğer karakter veya karakterler için yönteme çağrı olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="13383-188">Treated as a call to the <xref:System.Xml.XmlWriter.WriteString%2A> method for the equivalent character or characters.</span></span>|  
  
 <span data-ttu-id="13383-189">Sınıfı hakkında daha fazla bilgi için <xref:System.Xml.XmlWriter> bkz <xref:System.Xml.XmlWriter> . sınıf başvurusu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="13383-189">For more information about the <xref:System.Xml.XmlWriter> class, see the <xref:System.Xml.XmlWriter> class reference documentation.</span></span>  
  
### <a name="multiple-xmlwriter-objects"></a><span data-ttu-id="13383-190">Birden çok XmlWriter nesnesi</span><span class="sxs-lookup"><span data-stu-id="13383-190">Multiple XmlWriter Objects</span></span>  
 <span data-ttu-id="13383-191"><xref:System.Xml.XPath.XPathNavigator>Bir veya daha fazla açık nesne içeren BIR XML belgesinin farklı bölümlerine işaret eden birden çok nesne olması mümkündür <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="13383-191">It is possible to have multiple <xref:System.Xml.XPath.XPathNavigator> objects pointing to different parts of an XML document with one or more open <xref:System.Xml.XmlWriter> objects.</span></span> <span data-ttu-id="13383-192">Birden çok <xref:System.Xml.XmlWriter> nesneye izin verilir ve tek iş parçacıklı senaryolarda desteklenir.</span><span class="sxs-lookup"><span data-stu-id="13383-192">Multiple <xref:System.Xml.XmlWriter> objects are allowed and supported in single-threaded scenarios.</span></span>  
  
 <span data-ttu-id="13383-193">Birden çok nesne kullanırken göz önünde bulundurmanız gereken önemli notlar aşağıda verilmiştir <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="13383-193">The following are important notes to consider when using multiple <xref:System.Xml.XmlWriter> objects.</span></span>  
  
- <span data-ttu-id="13383-194">Nesneleri tarafından yazılan XML parçaları, <xref:System.Xml.XmlWriter> <xref:System.Xml.XmlWriter.Close%2A> her bir nesnenin YÖNTEMI çağrıldığında XML belgesine eklenir <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="13383-194">XML fragments written by <xref:System.Xml.XmlWriter> objects are added to the XML document when the <xref:System.Xml.XmlWriter.Close%2A> method of each <xref:System.Xml.XmlWriter> object is called.</span></span> <span data-ttu-id="13383-195">Bu noktaya kadar, <xref:System.Xml.XmlWriter> nesne bağlantısı kesik bir parça yazıyor.</span><span class="sxs-lookup"><span data-stu-id="13383-195">Until that point, the <xref:System.Xml.XmlWriter> object is writing a disconnected fragment.</span></span> <span data-ttu-id="13383-196">XML belgesinde bir işlem gerçekleştirilirse, kullanılmadan önce bir nesne tarafından yazılan tüm parçalar <xref:System.Xml.XmlWriter> <xref:System.Xml.XmlWriter.Close%2A> etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="13383-196">If an operation is performed on the XML document, any fragments being written by an <xref:System.Xml.XmlWriter> object, before the <xref:System.Xml.XmlWriter.Close%2A> has been called, are not affected.</span></span>  
  
- <span data-ttu-id="13383-197"><xref:System.Xml.XmlWriter>Belirli BIR XML alt ağacı üzerinde açık bir nesne varsa ve bu alt ağaç silinirse, <xref:System.Xml.XmlWriter> nesne hala alt ağaca eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="13383-197">If there is an open <xref:System.Xml.XmlWriter> object on a particular XML subtree and that subtree is deleted, the <xref:System.Xml.XmlWriter> object may still add to the sub-tree.</span></span> <span data-ttu-id="13383-198">Alt ağaç yalnızca silinmiş bir parça haline gelir.</span><span class="sxs-lookup"><span data-stu-id="13383-198">The subtree simply becomes a deleted fragment.</span></span>  
  
- <span data-ttu-id="13383-199"><xref:System.Xml.XmlWriter>XML belgesinde aynı noktada birden çok nesne açılırsa, XML belgesine, <xref:System.Xml.XmlWriter> nesneleri açıldığı sırada değil, bunların kapandıkları sırada eklenir.</span><span class="sxs-lookup"><span data-stu-id="13383-199">If multiple <xref:System.Xml.XmlWriter> objects are opened at the same point in the XML document, they are added to the XML document in the order in which the <xref:System.Xml.XmlWriter> objects are closed, not in the order in which they were opened.</span></span>  
  
 <span data-ttu-id="13383-200">Aşağıdaki örnek bir nesnesi oluşturur <xref:System.Xml.XmlDocument> , bir nesnesi oluşturur <xref:System.Xml.XPath.XPathNavigator> ve sonra, <xref:System.Xml.XmlWriter> <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> dosyadaki ilk kitabın yapısını oluşturmak için yöntemi tarafından döndürülen nesneyi kullanır `books.xml` .</span><span class="sxs-lookup"><span data-stu-id="13383-200">The following example creates an <xref:System.Xml.XmlDocument> object, creates an <xref:System.Xml.XPath.XPathNavigator> object, and then uses the <xref:System.Xml.XmlWriter> object returned by the <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> method to create the structure of the first book in the `books.xml` file.</span></span> <span data-ttu-id="13383-201">Örnek daha sonra dosyayı dosya olarak kaydeder `book.xml` .</span><span class="sxs-lookup"><span data-stu-id="13383-201">The example then saves it as the `book.xml` file.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
Using writer As XmlWriter = navigator.PrependChild()  
  
    writer.WriteStartElement("bookstore")  
    writer.WriteStartElement("book")  
    writer.WriteAttributeString("genre", "autobiography")  
    writer.WriteAttributeString("publicationdate", "1981-03-22")  
    writer.WriteAttributeString("ISBN", "1-861003-11-0")  
    writer.WriteElementString("title", "The Autobiography of Benjamin Franklin")  
    writer.WriteStartElement("author")  
    writer.WriteElementString("first-name", "Benjamin")  
    writer.WriteElementString("last-name", "Franklin")  
    writer.WriteElementString("price", "8.99")  
    writer.WriteEndElement()  
    writer.WriteEndElement()  
    writer.WriteEndElement()  
  
End Using  
  
document.Save("book.xml")  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
XPathNavigator navigator = document.CreateNavigator();  
  
using (XmlWriter writer = navigator.PrependChild())  
{  
    writer.WriteStartElement("bookstore");  
    writer.WriteStartElement("book");  
    writer.WriteAttributeString("genre", "autobiography");  
    writer.WriteAttributeString("publicationdate", "1981-03-22");  
    writer.WriteAttributeString("ISBN", "1-861003-11-0");  
    writer.WriteElementString("title", "The Autobiography of Benjamin Franklin");  
    writer.WriteStartElement("author");  
    writer.WriteElementString("first-name", "Benjamin");  
    writer.WriteElementString("last-name", "Franklin");  
    writer.WriteElementString("price", "8.99");  
    writer.WriteEndElement();  
    writer.WriteEndElement();  
    writer.WriteEndElement();  
}  
document.Save("book.xml");  
```  
  
## <a name="saving-an-xml-document"></a><span data-ttu-id="13383-202">XML belgesi kaydetme</span><span class="sxs-lookup"><span data-stu-id="13383-202">Saving an XML Document</span></span>  
 <span data-ttu-id="13383-203"><xref:System.Xml.XmlDocument>Bu konuda açıklanan yöntemlerin sonucu olarak bir nesne üzerinde yapılan değişikliklerin kaydedilmesi, sınıfının yöntemleri kullanılarak gerçekleştirilir <xref:System.Xml.XmlDocument> .</span><span class="sxs-lookup"><span data-stu-id="13383-203">Saving changes made to an <xref:System.Xml.XmlDocument> object as the result of the methods described in this topic is performed using the methods of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="13383-204">Bir nesne üzerinde yapılan değişiklikleri kaydetme hakkında daha fazla bilgi için <xref:System.Xml.XmlDocument> bkz. [belgeyi kaydetme ve yazma](saving-and-writing-a-document.md).</span><span class="sxs-lookup"><span data-stu-id="13383-204">For more information about saving changes made to an <xref:System.Xml.XmlDocument> object, see [Saving and Writing a Document](saving-and-writing-a-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13383-205">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13383-205">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="13383-206">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="13383-206">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="13383-207">XPathNavigator Kullanarak XML Verilerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="13383-207">Modify XML Data using XPathNavigator</span></span>](modify-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="13383-208">XPathNavigator Kullanarak XML Verilerini Kaldırma</span><span class="sxs-lookup"><span data-stu-id="13383-208">Remove XML Data using XPathNavigator</span></span>](remove-xml-data-using-xpathnavigator.md)
