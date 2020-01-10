---
title: XPathNavigator Kullanarak XML Verileri Ekleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 2ed8c28b-b88d-4be7-9c87-92df01f0821f
ms.openlocfilehash: 68c003467d837fe79d5e275968e47fa5dc3490cc
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710732"
---
# <a name="insert-xml-data-using-xpathnavigator"></a><span data-ttu-id="01bc9-102">XPathNavigator Kullanarak XML Verileri Ekleme</span><span class="sxs-lookup"><span data-stu-id="01bc9-102">Insert XML Data using XPathNavigator</span></span>
<span data-ttu-id="01bc9-103"><xref:System.Xml.XPath.XPathNavigator> sınıfı, bir XML belgesine eşdüzey, alt ve öznitelik düğümleri eklemek için kullanılan bir yöntemler kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="01bc9-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to insert sibling, child, and attribute nodes in an XML document.</span></span> <span data-ttu-id="01bc9-104">Bu yöntemleri kullanabilmeniz için <xref:System.Xml.XPath.XPathNavigator> nesnesi düzenlenebilir olmalıdır, yani <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> özelliği `true`olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="01bc9-104">In order to use these methods, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be `true`.</span></span>  
  
 <span data-ttu-id="01bc9-105">bir XML belgesini düzenleyebilen <xref:System.Xml.XPath.XPathNavigator> nesneleri, <xref:System.Xml.XmlDocument> sınıfının <xref:System.Xml.XmlDocument.CreateNavigator%2A> yöntemiyle oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="01bc9-105"><xref:System.Xml.XPath.XPathNavigator> objects that can edit an XML document are created by the <xref:System.Xml.XmlDocument.CreateNavigator%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="01bc9-106"><xref:System.Xml.XPath.XPathDocument> sınıfı tarafından oluşturulan <xref:System.Xml.XPath.XPathNavigator> nesneleri salt okunurdur ve bir <xref:System.Xml.XPath.XPathDocument> nesnesi tarafından oluşturulan <xref:System.Xml.XPath.XPathNavigator> nesnesinin Editing yöntemlerini kullanma girişimleri bir <xref:System.NotSupportedException>sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="01bc9-106"><xref:System.Xml.XPath.XPathNavigator> objects created by the <xref:System.Xml.XPath.XPathDocument> class are read-only and any attempt to use the editing methods of an <xref:System.Xml.XPath.XPathNavigator> object created by an <xref:System.Xml.XPath.XPathDocument> object results in a <xref:System.NotSupportedException>.</span></span>  
  
 <span data-ttu-id="01bc9-107">Düzenlenebilir <xref:System.Xml.XPath.XPathNavigator> nesneleri oluşturma hakkında daha fazla bilgi için bkz. [XPathDocument ve XmlDocument kullanarak XML verilerini okuma](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span><span class="sxs-lookup"><span data-stu-id="01bc9-107">For more information about creating editable <xref:System.Xml.XPath.XPathNavigator> objects, see [Reading XML Data using XPathDocument and XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span></span>  
  
## <a name="inserting-nodes"></a><span data-ttu-id="01bc9-108">Düğüm ekleme</span><span class="sxs-lookup"><span data-stu-id="01bc9-108">Inserting Nodes</span></span>  
 <span data-ttu-id="01bc9-109"><xref:System.Xml.XPath.XPathNavigator> sınıfı, bir XML belgesine eşdüzey, alt ve öznitelik düğümleri eklemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="01bc9-109">The <xref:System.Xml.XPath.XPathNavigator> class provides methods to insert sibling, child, and attribute nodes in an XML document.</span></span> <span data-ttu-id="01bc9-110">Bu yöntemler, bir <xref:System.Xml.XPath.XPathNavigator> nesnesinin geçerli konumuyla ilişkili olarak farklı konumlara düğüm ve öznitelik eklemenize olanak tanır ve aşağıdaki bölümlerde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="01bc9-110">These methods allow you to insert nodes and attributes in different locations in relation to the current position of an <xref:System.Xml.XPath.XPathNavigator> object and are described in the following sections.</span></span>  
  
### <a name="inserting-sibling-nodes"></a><span data-ttu-id="01bc9-111">Eşdüzey düğümler ekleme</span><span class="sxs-lookup"><span data-stu-id="01bc9-111">Inserting Sibling Nodes</span></span>  
 <span data-ttu-id="01bc9-112"><xref:System.Xml.XPath.XPathNavigator> sınıfı eşdüzey düğümleri eklemek için aşağıdaki yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="01bc9-112">The <xref:System.Xml.XPath.XPathNavigator> class provides the following methods to insert sibling nodes.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A>  
  
 <span data-ttu-id="01bc9-113">Bu yöntemler, düğüm bir <xref:System.Xml.XPath.XPathNavigator> nesnesi üzerinde konumlandırılmadan önce ve sonra eşdüzey düğümler ekler.</span><span class="sxs-lookup"><span data-stu-id="01bc9-113">These methods insert sibling nodes before and after the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="01bc9-114"><xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> ve <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> yöntemleri aşırı yüklendi ve parametre olarak eklemek için eşdüzey düğümü içeren bir `string`, <xref:System.Xml.XmlReader> nesnesi veya <xref:System.Xml.XPath.XPathNavigator> nesnesi kabul eder.</span><span class="sxs-lookup"><span data-stu-id="01bc9-114">The <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> methods are overloaded and accept a `string`, <xref:System.Xml.XmlReader> object, or <xref:System.Xml.XPath.XPathNavigator> object containing the sibling node to add as parameters.</span></span> <span data-ttu-id="01bc9-115">Her iki yöntem de eşdüzey düğümleri eklemek için kullanılan bir <xref:System.Xml.XmlWriter> nesnesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="01bc9-115">Both methods also return an <xref:System.Xml.XmlWriter> object used to insert sibling nodes.</span></span>  
  
 <span data-ttu-id="01bc9-116"><xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> ve <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> yöntemleri, düğüm bir <xref:System.Xml.XPath.XPathNavigator> nesnesi şu anda ad alanı ön eki, yerel ad, ad alanı URI 'SI ve parametre olarak belirtilen değer kullanılarak konumlandırılmış bir bir eşdüzey düğüm ekler.</span><span class="sxs-lookup"><span data-stu-id="01bc9-116">The <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> methods insert a single sibling node before and after the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on using the namespace prefix, local name, namespace URI, and value specified as parameters.</span></span>  
  
 <span data-ttu-id="01bc9-117">Aşağıdaki örnekte, `contosoBooks.xml` dosyasındaki ilk `book` öğesinin `price` alt öğesinden önce yeni bir `pages` öğesi eklenir.</span><span class="sxs-lookup"><span data-stu-id="01bc9-117">In the following example a new `pages` element is inserted before the `price` child element of the first `book` element in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#19](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#19)]
 [!code-csharp[XPathNavigatorMethods#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#19)]
 [!code-vb[XPathNavigatorMethods#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#19)]  
  
 <span data-ttu-id="01bc9-118">Örnek, `contosoBooks.xml` dosyasını girdi olarak alır.</span><span class="sxs-lookup"><span data-stu-id="01bc9-118">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="01bc9-119"><xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> ve <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> yöntemleri hakkında daha fazla bilgi için bkz. <xref:System.Xml.XPath.XPathNavigator> sınıfı başvuru belgeleri.</span><span class="sxs-lookup"><span data-stu-id="01bc9-119">For more information about the <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> methods, see the <xref:System.Xml.XPath.XPathNavigator> class reference documentation.</span></span>  
  
### <a name="inserting-child-nodes"></a><span data-ttu-id="01bc9-120">Alt düğümler ekleniyor</span><span class="sxs-lookup"><span data-stu-id="01bc9-120">Inserting Child Nodes</span></span>  
 <span data-ttu-id="01bc9-121"><xref:System.Xml.XPath.XPathNavigator> sınıfı alt düğümleri eklemek için aşağıdaki yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="01bc9-121">The <xref:System.Xml.XPath.XPathNavigator> class provides the following methods to insert child nodes.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A>  
  
 <span data-ttu-id="01bc9-122">Bu yöntemler, alt düğümleri sonuna ekler ve sonuna eklenmiş bir <xref:System.Xml.XPath.XPathNavigator> nesnesi olan düğümün alt düğümlerinin listesinin başlangıcına eklenir.</span><span class="sxs-lookup"><span data-stu-id="01bc9-122">These methods append and prepend child nodes to the end of and the beginning of the list of child nodes of the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="01bc9-123">"Eşdüzey düğüm ekleme" bölümündeki Yöntemler gibi <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> ve <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> yöntemleri, parametre olarak eklemek için alt düğümü içeren bir `string`, <xref:System.Xml.XmlReader> nesnesi veya <xref:System.Xml.XPath.XPathNavigator> nesnesi kabul eder.</span><span class="sxs-lookup"><span data-stu-id="01bc9-123">Like the methods in the "Inserting Sibling Nodes" section, the <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> methods accept a `string`, <xref:System.Xml.XmlReader> object, or <xref:System.Xml.XPath.XPathNavigator> object containing the child node to add as parameters.</span></span> <span data-ttu-id="01bc9-124">Her iki yöntem de alt düğümleri eklemek için kullanılan bir <xref:System.Xml.XmlWriter> nesnesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="01bc9-124">Both methods also return an <xref:System.Xml.XmlWriter> object used to insert child nodes.</span></span>  
  
 <span data-ttu-id="01bc9-125">Ayrıca, "eşdüzey düğüm ekleme" bölümündeki Yöntemler gibi <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> ve <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> yöntemleri, bir <xref:System.Xml.XPath.XPathNavigator> nesnesi şu anda ad alanı ön eki, yerel ad, ad alanı URI 'SI ve parametre olarak belirtilen değer kullanılarak konumlandırılmış olan bir nesnesinin sonuna tek bir alt düğüm ekler.</span><span class="sxs-lookup"><span data-stu-id="01bc9-125">Also like the methods in the "Inserting Sibling Nodes" section, the <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> methods insert a single child node to the end of and the beginning of the list of child nodes of the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on using the namespace prefix, local name, namespace URI, and value specified as parameters.</span></span>  
  
 <span data-ttu-id="01bc9-126">Aşağıdaki örnekte, yeni bir `pages` alt öğesi, `contosoBooks.xml` dosyasındaki ilk `book` öğesinin alt öğelerinin listesine eklenir.</span><span class="sxs-lookup"><span data-stu-id="01bc9-126">In the following example, a new `pages` child element is appended to the list of child elements of the first `book` element in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#2)]
 [!code-csharp[XPathNavigatorMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#2)]
 [!code-vb[XPathNavigatorMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#2)]  
  
 <span data-ttu-id="01bc9-127">Örnek, `contosoBooks.xml` dosyasını girdi olarak alır.</span><span class="sxs-lookup"><span data-stu-id="01bc9-127">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="01bc9-128"><xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> ve <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> yöntemleri hakkında daha fazla bilgi için bkz. <xref:System.Xml.XPath.XPathNavigator> sınıfı başvuru belgeleri.</span><span class="sxs-lookup"><span data-stu-id="01bc9-128">For more information about the <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> methods, see the <xref:System.Xml.XPath.XPathNavigator> class reference documentation.</span></span>  
  
### <a name="inserting-attribute-nodes"></a><span data-ttu-id="01bc9-129">Öznitelik düğümleri ekleniyor</span><span class="sxs-lookup"><span data-stu-id="01bc9-129">Inserting Attribute Nodes</span></span>  
 <span data-ttu-id="01bc9-130"><xref:System.Xml.XPath.XPathNavigator> sınıfı, öznitelik düğümleri eklemek için aşağıdaki yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="01bc9-130">The <xref:System.Xml.XPath.XPathNavigator> class provides the following methods to insert attribute nodes.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A>  
  
 <span data-ttu-id="01bc9-131">Bu yöntemler, nesne düğümüne öznitelik düğümleri ekler bir <xref:System.Xml.XPath.XPathNavigator> nesnesi şu anda üzerinde konumlanır.</span><span class="sxs-lookup"><span data-stu-id="01bc9-131">These methods insert attribute nodes on the element node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="01bc9-132"><xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> yöntemi, öğe düğümünde bir öznitelik düğümü oluşturur <xref:System.Xml.XPath.XPathNavigator> nesnesi şu anda ad alanı ön eki, yerel adı, ad alanı URI 'SI ve parametre olarak belirtilen değer kullanılarak konumlandırılmış.</span><span class="sxs-lookup"><span data-stu-id="01bc9-132">The <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> method creates an attribute node on the element node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on using the namespace prefix, local name, namespace URI, and value specified as parameters.</span></span> <span data-ttu-id="01bc9-133"><xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> yöntemi öznitelik düğümleri eklemek için kullanılan bir <xref:System.Xml.XmlWriter> nesnesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="01bc9-133">The <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> method returns an <xref:System.Xml.XmlWriter> object used to insert attribute nodes.</span></span>  
  
 <span data-ttu-id="01bc9-134">Aşağıdaki örnekte, `contosoBooks.xml` yönteminden döndürülen <xref:System.Xml.XmlWriter> nesnesi kullanılarak <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> dosyasındaki ilk `book` öğesinin `price` alt öğesinde yeni `discount` ve `currency` öznitelikleri oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="01bc9-134">In the following example, new `discount` and `currency` attributes are created on the `price` child element of the first `book` element in the `contosoBooks.xml` file using the <xref:System.Xml.XmlWriter> object returned from the <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> method.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#8](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#8)]
 [!code-csharp[XPathNavigatorMethods#8](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#8)]
 [!code-vb[XPathNavigatorMethods#8](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#8)]  
  
 <span data-ttu-id="01bc9-135">Örnek, `contosoBooks.xml` dosyasını girdi olarak alır.</span><span class="sxs-lookup"><span data-stu-id="01bc9-135">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="01bc9-136"><xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> ve <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> yöntemleri hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator> sınıf başvurusu belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="01bc9-136">For more information about the <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> and <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> methods, see the <xref:System.Xml.XPath.XPathNavigator> class reference documentation.</span></span>  
  
## <a name="copying-nodes"></a><span data-ttu-id="01bc9-137">Düğümler kopyalanıyor</span><span class="sxs-lookup"><span data-stu-id="01bc9-137">Copying Nodes</span></span>  
 <span data-ttu-id="01bc9-138">Belirli durumlarda, bir XML belgesini başka bir XML belgesinden içerik ile doldurmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01bc9-138">In certain cases you may want to populate an XML document with the contents from another XML document.</span></span> <span data-ttu-id="01bc9-139"><xref:System.Xml.XPath.XPathNavigator> sınıfı ve <xref:System.Xml.XmlWriter> sınıfı, düğümleri varolan bir <xref:System.Xml.XmlReader> nesnesinden veya <xref:System.Xml.XPath.XPathNavigator> nesnesinden bir <xref:System.Xml.XmlDocument> nesnesine kopyalayabilir.</span><span class="sxs-lookup"><span data-stu-id="01bc9-139">Both the <xref:System.Xml.XPath.XPathNavigator> class and the <xref:System.Xml.XmlWriter> class can copy nodes to an <xref:System.Xml.XmlDocument> object from an existing <xref:System.Xml.XmlReader> object or <xref:System.Xml.XPath.XPathNavigator> object.</span></span>  
  
 <span data-ttu-id="01bc9-140"><xref:System.Xml.XPath.XPathNavigator> sınıfının <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> ve <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> yöntemlerinin hepsi, bir <xref:System.Xml.XPath.XPathNavigator> nesnesini veya bir <xref:System.Xml.XmlReader> nesnesini parametre olarak kabul edebilecek aşırı yüklemeleri vardır.</span><span class="sxs-lookup"><span data-stu-id="01bc9-140">The <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class all have overloads that can accept an <xref:System.Xml.XPath.XPathNavigator> object or an <xref:System.Xml.XmlReader> object as a parameter.</span></span>  
  
 <span data-ttu-id="01bc9-141"><xref:System.Xml.XmlWriter> sınıfının <xref:System.Xml.XmlWriter.WriteNode%2A> yöntemi <xref:System.Xml.XmlNode>, <xref:System.Xml.XmlReader>veya <xref:System.Xml.XPath.XPathNavigator> nesnesini kabul edebilecek aşırı yüklemelerden oluşur.</span><span class="sxs-lookup"><span data-stu-id="01bc9-141">The <xref:System.Xml.XmlWriter.WriteNode%2A> method of the <xref:System.Xml.XmlWriter> class has overloads that can accept an <xref:System.Xml.XmlNode>, <xref:System.Xml.XmlReader>, or <xref:System.Xml.XPath.XPathNavigator> object.</span></span>  
  
 <span data-ttu-id="01bc9-142">Aşağıdaki örnek, tüm `book` öğelerini bir belgeden diğerine kopyalar.</span><span class="sxs-lookup"><span data-stu-id="01bc9-142">The following example copies all the `book` elements from one document to another.</span></span>  
  
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
  
## <a name="inserting-values"></a><span data-ttu-id="01bc9-143">Değer ekleme</span><span class="sxs-lookup"><span data-stu-id="01bc9-143">Inserting Values</span></span>  
 <span data-ttu-id="01bc9-144"><xref:System.Xml.XPath.XPathNavigator> sınıfı, bir düğümün değerlerini <xref:System.Xml.XmlDocument> nesnesine eklemek için <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> ve <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="01bc9-144">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods to insert values for a node into an <xref:System.Xml.XmlDocument> object.</span></span>  
  
### <a name="inserting-untyped-values"></a><span data-ttu-id="01bc9-145">Türsüz değerler ekleme</span><span class="sxs-lookup"><span data-stu-id="01bc9-145">Inserting Untyped Values</span></span>  
 <span data-ttu-id="01bc9-146"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A> yöntemi, bir parametre olarak geçirilen türsüz `string` değerini, <xref:System.Xml.XPath.XPathNavigator> nesnenin şu anda konumlandığını düğümün değeri olarak ekler.</span><span class="sxs-lookup"><span data-stu-id="01bc9-146">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method simply inserts the untyped `string` value passed as a parameter as the value of the node the <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="01bc9-147">Değer, herhangi bir tür olmadan veya şema bilgileri kullanılabiliyorsa düğüm türüne göre yeni değerin geçerli olduğunu doğrulamadan eklenir.</span><span class="sxs-lookup"><span data-stu-id="01bc9-147">The value is inserted without any type or without verifying that the new value is valid according to the type of the node if schema information is available.</span></span>  
  
 <span data-ttu-id="01bc9-148">Aşağıdaki örnekte, `contosoBooks.xml` dosyasındaki tüm `price` öğelerini güncelleştirmek için <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> yöntemi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="01bc9-148">In the following example, the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method is used to update all `price` elements in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 <span data-ttu-id="01bc9-149">Örnek, `contosoBooks.xml` dosyasını girdi olarak alır.</span><span class="sxs-lookup"><span data-stu-id="01bc9-149">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="inserting-typed-values"></a><span data-ttu-id="01bc9-150">Yazılan değerler ekleniyor</span><span class="sxs-lookup"><span data-stu-id="01bc9-150">Inserting Typed Values</span></span>  
 <span data-ttu-id="01bc9-151">Bir düğümün türü bir W3C XML şeması basit türü olduğunda, <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> yöntemi tarafından yerleştirilen yeni değer, değer ayarlanmadan önce basit türdeki modellerle denetlenir.</span><span class="sxs-lookup"><span data-stu-id="01bc9-151">When the type of a node is a W3C XML Schema simple type, the new value inserted by the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method is checked against the facets of the simple type before the value is set.</span></span> <span data-ttu-id="01bc9-152">Yeni değer düğüm türüne göre geçerli değilse (örneğin, türü `xs:positiveInteger`olan bir öğe üzerinde `-1` değerini ayarlamak), bir özel durumla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="01bc9-152">If the new value is not valid according to the type of the node (for example, setting a value of `-1` on an element whose type is `xs:positiveInteger`), it results in an exception.</span></span>  
  
 <span data-ttu-id="01bc9-153">Aşağıdaki örnek `contosoBooks.xml` dosyasındaki ilk `book` öğesinin `price` öğesinin değerini bir <xref:System.DateTime> değerine değiştirmeyi dener.</span><span class="sxs-lookup"><span data-stu-id="01bc9-153">The following example attempts to change the value of the `price` element of the first `book` element in the `contosoBooks.xml` file to a <xref:System.DateTime> value.</span></span> <span data-ttu-id="01bc9-154">`price` öğesinin XML şeması türü `contosoBooks.xsd` dosyalarında `xs:decimal` olarak tanımlandığından, bu durum bir özel durumla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="01bc9-154">Because the XML Schema type of the `price` element is defined as `xs:decimal` in the `contosoBooks.xsd` files, this results in an exception.</span></span>  
  
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
  
 <span data-ttu-id="01bc9-155">Örnek, `contosoBooks.xml` dosyasını girdi olarak alır.</span><span class="sxs-lookup"><span data-stu-id="01bc9-155">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="01bc9-156">Örnek ayrıca `contosoBooks.xsd` giriş olarak alır.</span><span class="sxs-lookup"><span data-stu-id="01bc9-156">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
## <a name="the-innerxml-and-outerxml-properties"></a><span data-ttu-id="01bc9-157">InnerXml ve OuterXml özellikleri</span><span class="sxs-lookup"><span data-stu-id="01bc9-157">The InnerXml and OuterXml Properties</span></span>  
 <span data-ttu-id="01bc9-158"><xref:System.Xml.XPath.XPathNavigator> sınıfının <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özellikleri, <xref:System.Xml.XPath.XPathNavigator> nesnenin şu anda konumlandırılmış olduğu düğümlerin XML işaretlemesini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="01bc9-158">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class change the XML markup of the nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="01bc9-159"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> özelliği, alt düğümlerin XML işaretlemesini değiştirir <xref:System.Xml.XPath.XPathNavigator> bir nesne şu anda belirtilen XML `string`ayrıştırılmış içeriğiyle konumlandırılmış.</span><span class="sxs-lookup"><span data-stu-id="01bc9-159">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on with the parsed contents of the given XML `string`.</span></span> <span data-ttu-id="01bc9-160">Benzer şekilde, <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özelliği, alt düğümlerin XML işaretlemesini de değiştirir ve o durumda geçerli düğümün kendisi de şu anda konumlandırılmış olan <xref:System.Xml.XPath.XPathNavigator> bir nesne.</span><span class="sxs-lookup"><span data-stu-id="01bc9-160">Similarly, the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on as well as the current node itself.</span></span>  
  
 <span data-ttu-id="01bc9-161">Bu konuda açıklanan yöntemlere ek olarak, <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özellikleri bir XML belgesine düğüm ve değer eklemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="01bc9-161">In addition to the methods described in this topic, the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties can be used to insert nodes and values in an XML document.</span></span> <span data-ttu-id="01bc9-162"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özelliklerini kullanarak düğüm ve değer ekleme hakkında daha fazla bilgi için bkz. [XPathNavigator kullanarak XML verilerini değiştirme](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) konusu.</span><span class="sxs-lookup"><span data-stu-id="01bc9-162">For more information about using the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties to insert nodes and values, see the [Modify XML Data using XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) topic.</span></span>  
  
## <a name="namespace-and-xmllang-conflicts"></a><span data-ttu-id="01bc9-163">Namespace ve XML: lang çakışmaları</span><span class="sxs-lookup"><span data-stu-id="01bc9-163">Namespace and xml:lang Conflicts</span></span>  
 <span data-ttu-id="01bc9-164">Ad alanı ve `xml:lang` bildirimlerinin kapsamı ile ilgili bazı çakışmalar, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> nesneleri parametre olarak alan <xref:System.Xml.XPath.XPathNavigator> sınıfının <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> ve <xref:System.Xml.XmlReader> yöntemleri kullanılarak XML verileri eklenirken meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="01bc9-164">Certain conflicts related to the scope of namespace and `xml:lang` declarations can occur when inserting XML data using the <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class that take <xref:System.Xml.XmlReader> objects as parameters.</span></span>  
  
 <span data-ttu-id="01bc9-165">Olası ad alanı çakışmaları aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="01bc9-165">The following are the possible namespace conflicts.</span></span>  
  
- <span data-ttu-id="01bc9-166"><xref:System.Xml.XmlReader> nesnenin bağlamı içinde kapsam içinde bir ad alanı varsa, ad alanı URI eşlemesinin öneki <xref:System.Xml.XPath.XPathNavigator> nesnenin bağlamında değilse, yeni eklenen düğüme yeni bir ad alanı bildirimi eklenir.</span><span class="sxs-lookup"><span data-stu-id="01bc9-166">If there is a namespace in-scope within the <xref:System.Xml.XmlReader> object's context, where the prefix to namespace URI mapping is not in the <xref:System.Xml.XPath.XPathNavigator> object's context, a new namespace declaration is added to the newly inserted node.</span></span>  
  
- <span data-ttu-id="01bc9-167">Aynı ad alanı URI 'SI hem <xref:System.Xml.XmlReader> nesnenin bağlamı hem de <xref:System.Xml.XPath.XPathNavigator> nesnesinin bağlamı içinde kapsam içindeyse, ancak her iki bağlamda da eşlenmiş farklı bir ön eke sahipse, yeni eklenen düğüme yeni bir ad alanı bildirimi eklenir ve bu, <xref:System.Xml.XmlReader> nesnesinden alınan önek ve ad alanı URI 'SI olur.</span><span class="sxs-lookup"><span data-stu-id="01bc9-167">If the same namespace URI is in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but has a different prefix mapped to it in both contexts, a new namespace declaration is added to the newly inserted node, with the prefix and namespace URI taken from the <xref:System.Xml.XmlReader> object.</span></span>  
  
- <span data-ttu-id="01bc9-168">Aynı ad alanı öneki hem <xref:System.Xml.XmlReader> nesnenin bağlamı hem de <xref:System.Xml.XPath.XPathNavigator> nesnesinin bağlamı içinde kapsam içindeyse, ancak her iki bağlamda de kendisine eşlenmiş farklı bir ad alanı URI 'SI varsa, bu öneki <xref:System.Xml.XmlReader> nesnesinden alınan ad alanı URI 'SI ile yeniden bildiren yeni eklenen düğüme yeni bir ad alanı bildirimi eklenir.</span><span class="sxs-lookup"><span data-stu-id="01bc9-168">If the same namespace prefix is in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but has a different namespace URI mapped to it in both contexts, a new namespace declaration is added to the newly inserted node which re-declares that prefix with the namespace URI taken from <xref:System.Xml.XmlReader> object.</span></span>  
  
- <span data-ttu-id="01bc9-169">Hem <xref:System.Xml.XmlReader> nesnenin bağlamında hem de <xref:System.Xml.XPath.XPathNavigator> nesnenin bağlamı aynı olan ad alanı URI 'SI aynıysa, yeni eklenen düğüme yeni bir ad alanı bildirimi eklenmez.</span><span class="sxs-lookup"><span data-stu-id="01bc9-169">If the prefix as well as the namespace URI in both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context is the same, no new namespace declaration is added to the newly inserted node.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="01bc9-170">Yukarıdaki açıklama aynı zamanda bir ön ek olarak boş `string` olan ad alanı bildirimleri için de geçerlidir (örneğin, varsayılan ad alanı bildirimi).</span><span class="sxs-lookup"><span data-stu-id="01bc9-170">The description above also applies to namespace declarations with the empty `string` as a prefix (for example, the default namespace declaration).</span></span>  
  
 <span data-ttu-id="01bc9-171">Olası `xml:lang` çakışmaları aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="01bc9-171">The following are the possible `xml:lang` conflicts.</span></span>  
  
- <span data-ttu-id="01bc9-172"><xref:System.Xml.XmlReader> nesnenin bağlamı içinde kapsam içinde `xml:lang` bir öznitelik varsa, ancak <xref:System.Xml.XPath.XPathNavigator> nesnesinin bağlamında, değeri <xref:System.Xml.XmlReader> nesnesinden alınmış bir `xml:lang` özniteliği yeni eklenen düğüme eklenir.</span><span class="sxs-lookup"><span data-stu-id="01bc9-172">If there is an `xml:lang` attribute in-scope within the <xref:System.Xml.XmlReader> object's context but not in the <xref:System.Xml.XPath.XPathNavigator> object's context, an `xml:lang` attribute whose value is taken from the <xref:System.Xml.XmlReader> object is added to the newly inserted node.</span></span>  
  
- <span data-ttu-id="01bc9-173">Hem <xref:System.Xml.XmlReader> nesnenin bağlamı hem de <xref:System.Xml.XPath.XPathNavigator> nesnesinin bağlamı içinde kapsam içinde bir `xml:lang` özniteliği varsa, ancak her biri farklı bir değere sahipse, <xref:System.Xml.XmlReader> nesnesinden değeri alınmış bir `xml:lang` özniteliği yeni eklenen düğüme eklenir.</span><span class="sxs-lookup"><span data-stu-id="01bc9-173">If there is an `xml:lang` attribute in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but each has a different value, an `xml:lang` attribute whose value is taken from the <xref:System.Xml.XmlReader> object is added to the newly inserted node.</span></span>  
  
- <span data-ttu-id="01bc9-174">Hem <xref:System.Xml.XmlReader> nesnenin bağlamı hem de <xref:System.Xml.XPath.XPathNavigator> nesnesinin bağlamı içinde kapsam içinde bir `xml:lang` özniteliği varsa, ancak her biri aynı değere sahip olan yeni eklenen düğüme yeni bir `xml:lang` özniteliği eklenmez.</span><span class="sxs-lookup"><span data-stu-id="01bc9-174">If there is an `xml:lang` attribute in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but each with the same value, no new `xml:lang` attribute is added on the newly inserted node.</span></span>  
  
- <span data-ttu-id="01bc9-175"><xref:System.Xml.XPath.XPathNavigator> nesnesinin bağlamı içinde kapsam içinde bir `xml:lang` özniteliği varsa, ancak <xref:System.Xml.XmlReader> nesnenin bağlamında yok, yeni eklenen düğüme hiçbir `xml:lang` özniteliği eklenmez.</span><span class="sxs-lookup"><span data-stu-id="01bc9-175">If there is an `xml:lang` attribute in-scope within the <xref:System.Xml.XPath.XPathNavigator> object's context, but none existing in the <xref:System.Xml.XmlReader> object's context, no `xml:lang` attribute is added to the newly inserted node.</span></span>  
  
## <a name="inserting-nodes-with-xmlwriter"></a><span data-ttu-id="01bc9-176">XmlWriter ile düğüm ekleme</span><span class="sxs-lookup"><span data-stu-id="01bc9-176">Inserting Nodes with XmlWriter</span></span>  
 <span data-ttu-id="01bc9-177">"Düğüm ve değer ekleme" bölümünde açıklanan eşdüzey, alt ve öznitelik düğümlerini eklemek için kullanılan yöntemler aşırı yüklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="01bc9-177">The methods used to insert sibling, child and attribute nodes described in the "Inserting Nodes and Values" section are overloaded.</span></span> <span data-ttu-id="01bc9-178"><xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> sınıfının <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> ve <xref:System.Xml.XPath.XPathNavigator> yöntemleri, düğümleri eklemek için kullanılan bir <xref:System.Xml.XmlWriter> nesnesi döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="01bc9-178">The <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> and <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class return an <xref:System.Xml.XmlWriter> object used to insert nodes.</span></span>  
  
### <a name="unsupported-xmlwriter-methods"></a><span data-ttu-id="01bc9-179">Desteklenmeyen XmlWriter yöntemleri</span><span class="sxs-lookup"><span data-stu-id="01bc9-179">Unsupported XmlWriter Methods</span></span>  
 <span data-ttu-id="01bc9-180"><xref:System.Xml.XmlWriter> sınıfını kullanarak bir XML belgesine bilgi yazmak için kullanılan yöntemlerin hepsi, XPath veri modeli ve Belge Nesne Modeli (DOM) arasındaki fark nedeniyle <xref:System.Xml.XPath.XPathNavigator> sınıfı tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="01bc9-180">Not all of the methods used for writing information to an XML document using the <xref:System.Xml.XmlWriter> class are supported by the <xref:System.Xml.XPath.XPathNavigator> class due to difference between the XPath data model and the Document Object Model (DOM).</span></span>  
  
 <span data-ttu-id="01bc9-181">Aşağıdaki tabloda, <xref:System.Xml.XPath.XPathNavigator> sınıfı tarafından desteklenmeyen <xref:System.Xml.XmlWriter> sınıfı yöntemleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="01bc9-181">The following table describes the <xref:System.Xml.XmlWriter> class methods not supported by the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
|<span data-ttu-id="01bc9-182">Yöntem</span><span class="sxs-lookup"><span data-stu-id="01bc9-182">Method</span></span>|<span data-ttu-id="01bc9-183">Açıklama</span><span class="sxs-lookup"><span data-stu-id="01bc9-183">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.XmlWriter.WriteEntityRef%2A>|<span data-ttu-id="01bc9-184"><xref:System.NotSupportedException> özel durumu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="01bc9-184">Throws a <xref:System.NotSupportedException> exception.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteDocType%2A>|<span data-ttu-id="01bc9-185">Kök düzeyinde yok sayılır ve XML belgesinde başka bir düzeyde çağrılırsa bir <xref:System.NotSupportedException> özel durumu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="01bc9-185">Ignored at the root level and throws a <xref:System.NotSupportedException> exception if called at any other level in the XML document.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteCData%2A>|<span data-ttu-id="01bc9-186">Denk karakter veya karakterler için <xref:System.Xml.XmlWriter.WriteString%2A> yöntemine bir çağrı olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="01bc9-186">Treated as a call to the <xref:System.Xml.XmlWriter.WriteString%2A> method for the equivalent character or characters.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteCharEntity%2A>|<span data-ttu-id="01bc9-187">Denk karakter veya karakterler için <xref:System.Xml.XmlWriter.WriteString%2A> yöntemine bir çağrı olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="01bc9-187">Treated as a call to the <xref:System.Xml.XmlWriter.WriteString%2A> method for the equivalent character or characters.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteSurrogateCharEntity%2A>|<span data-ttu-id="01bc9-188">Denk karakter veya karakterler için <xref:System.Xml.XmlWriter.WriteString%2A> yöntemine bir çağrı olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="01bc9-188">Treated as a call to the <xref:System.Xml.XmlWriter.WriteString%2A> method for the equivalent character or characters.</span></span>|  
  
 <span data-ttu-id="01bc9-189"><xref:System.Xml.XmlWriter> sınıfı hakkında daha fazla bilgi için bkz. <xref:System.Xml.XmlWriter> sınıf başvurusu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="01bc9-189">For more information about the <xref:System.Xml.XmlWriter> class, see the <xref:System.Xml.XmlWriter> class reference documentation.</span></span>  
  
### <a name="multiple-xmlwriter-objects"></a><span data-ttu-id="01bc9-190">Birden çok XmlWriter nesnesi</span><span class="sxs-lookup"><span data-stu-id="01bc9-190">Multiple XmlWriter Objects</span></span>  
 <span data-ttu-id="01bc9-191">Bir veya daha fazla açık <xref:System.Xml.XmlWriter> nesnesi olan bir XML belgesinin farklı bölümlerine işaret eden birden çok <xref:System.Xml.XPath.XPathNavigator> nesnesi olması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="01bc9-191">It is possible to have multiple <xref:System.Xml.XPath.XPathNavigator> objects pointing to different parts of an XML document with one or more open <xref:System.Xml.XmlWriter> objects.</span></span> <span data-ttu-id="01bc9-192">Çoklu <xref:System.Xml.XmlWriter> nesneleri tek iş parçacıklı senaryolarda kullanılabilir ve desteklenir.</span><span class="sxs-lookup"><span data-stu-id="01bc9-192">Multiple <xref:System.Xml.XmlWriter> objects are allowed and supported in single-threaded scenarios.</span></span>  
  
 <span data-ttu-id="01bc9-193">Birden çok <xref:System.Xml.XmlWriter> nesnesi kullanırken göz önünde bulundurmanız gereken önemli notlar aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="01bc9-193">The following are important notes to consider when using multiple <xref:System.Xml.XmlWriter> objects.</span></span>  
  
- <span data-ttu-id="01bc9-194"><xref:System.Xml.XmlWriter> nesneleri tarafından yazılan XML parçaları, her bir <xref:System.Xml.XmlWriter> nesnesinin <xref:System.Xml.XmlWriter.Close%2A> yöntemi çağrıldığında XML belgesine eklenir.</span><span class="sxs-lookup"><span data-stu-id="01bc9-194">XML fragments written by <xref:System.Xml.XmlWriter> objects are added to the XML document when the <xref:System.Xml.XmlWriter.Close%2A> method of each <xref:System.Xml.XmlWriter> object is called.</span></span> <span data-ttu-id="01bc9-195">Bu noktaya kadar <xref:System.Xml.XmlWriter> nesnesi bağlantısı kesik bir parça yazıyor.</span><span class="sxs-lookup"><span data-stu-id="01bc9-195">Until that point, the <xref:System.Xml.XmlWriter> object is writing a disconnected fragment.</span></span> <span data-ttu-id="01bc9-196">XML belgesinde bir işlem gerçekleştirilirse, <xref:System.Xml.XmlWriter.Close%2A> çağrılmadan önce bir <xref:System.Xml.XmlWriter> nesnesi tarafından yazılan parçalar etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="01bc9-196">If an operation is performed on the XML document, any fragments being written by an <xref:System.Xml.XmlWriter> object, before the <xref:System.Xml.XmlWriter.Close%2A> has been called, are not affected.</span></span>  
  
- <span data-ttu-id="01bc9-197">Belirli bir XML alt ağacında açık bir <xref:System.Xml.XmlWriter> nesnesi varsa ve bu alt ağaç silinirse, <xref:System.Xml.XmlWriter> nesnesi yine de alt ağaca eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="01bc9-197">If there is an open <xref:System.Xml.XmlWriter> object on a particular XML subtree and that subtree is deleted, the <xref:System.Xml.XmlWriter> object may still add to the sub-tree.</span></span> <span data-ttu-id="01bc9-198">Alt ağaç yalnızca silinmiş bir parça haline gelir.</span><span class="sxs-lookup"><span data-stu-id="01bc9-198">The subtree simply becomes a deleted fragment.</span></span>  
  
- <span data-ttu-id="01bc9-199">Birden çok <xref:System.Xml.XmlWriter> nesnesi, XML belgesinde aynı noktada açılırsa, XML belgesine, açıldıkları sırada değil, <xref:System.Xml.XmlWriter> nesnelerinin kapatıldığı sırada eklenirler.</span><span class="sxs-lookup"><span data-stu-id="01bc9-199">If multiple <xref:System.Xml.XmlWriter> objects are opened at the same point in the XML document, they are added to the XML document in the order in which the <xref:System.Xml.XmlWriter> objects are closed, not in the order in which they were opened.</span></span>  
  
 <span data-ttu-id="01bc9-200">Aşağıdaki örnek bir <xref:System.Xml.XmlDocument> nesnesi oluşturur, bir <xref:System.Xml.XPath.XPathNavigator> nesnesi oluşturur ve sonra `books.xml` dosyasındaki ilk kitabın yapısını oluşturmak için <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> yöntemi tarafından döndürülen <xref:System.Xml.XmlWriter> nesnesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="01bc9-200">The following example creates an <xref:System.Xml.XmlDocument> object, creates an <xref:System.Xml.XPath.XPathNavigator> object, and then uses the <xref:System.Xml.XmlWriter> object returned by the <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> method to create the structure of the first book in the `books.xml` file.</span></span> <span data-ttu-id="01bc9-201">Örnek daha sonra bu dosyayı `book.xml` dosyası olarak kaydeder.</span><span class="sxs-lookup"><span data-stu-id="01bc9-201">The example then saves it as the `book.xml` file.</span></span>  
  
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
  
## <a name="saving-an-xml-document"></a><span data-ttu-id="01bc9-202">XML belgesi kaydetme</span><span class="sxs-lookup"><span data-stu-id="01bc9-202">Saving an XML Document</span></span>  
 <span data-ttu-id="01bc9-203">Bu konuda açıklanan yöntemlerin sonucu olarak, bir <xref:System.Xml.XmlDocument> nesnesine yapılan değişiklikler kaydetme, <xref:System.Xml.XmlDocument> sınıfının yöntemleri kullanılarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="01bc9-203">Saving changes made to an <xref:System.Xml.XmlDocument> object as the result of the methods described in this topic is performed using the methods of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="01bc9-204"><xref:System.Xml.XmlDocument> nesne üzerinde yapılan değişiklikleri kaydetme hakkında daha fazla bilgi için bkz. [bir belge kaydetme ve yazma](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span><span class="sxs-lookup"><span data-stu-id="01bc9-204">For more information about saving changes made to an <xref:System.Xml.XmlDocument> object, see [Saving and Writing a Document](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01bc9-205">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01bc9-205">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="01bc9-206">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="01bc9-206">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="01bc9-207">XPathNavigator Kullanarak XML Verilerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="01bc9-207">Modify XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="01bc9-208">XPathNavigator Kullanarak XML Verilerini Kaldırma</span><span class="sxs-lookup"><span data-stu-id="01bc9-208">Remove XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)
