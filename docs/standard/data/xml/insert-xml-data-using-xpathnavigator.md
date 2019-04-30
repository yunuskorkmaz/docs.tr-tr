---
title: XPathNavigator Kullanarak XML Verileri Ekleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 2ed8c28b-b88d-4be7-9c87-92df01f0821f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 224e4f3db31e4818833eb8411f44f547538534fc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61650251"
---
# <a name="insert-xml-data-using-xpathnavigator"></a><span data-ttu-id="1fe82-102">XPathNavigator Kullanarak XML Verileri Ekleme</span><span class="sxs-lookup"><span data-stu-id="1fe82-102">Insert XML Data using XPathNavigator</span></span>
<span data-ttu-id="1fe82-103"><xref:System.Xml.XPath.XPathNavigator> Sınıf bir XML belgesinde eşdüzey, alt öğe ve öznitelik düğümleri eklemek için kullanılan yöntemler kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="1fe82-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to insert sibling, child, and attribute nodes in an XML document.</span></span> <span data-ttu-id="1fe82-104">Bu yöntemleri kullanmak için <xref:System.Xml.XPath.XPathNavigator> nesne olmalıdır düzenlenemez, diğer bir deyişle, kendi <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> özelliği olmalıdır `true`.</span><span class="sxs-lookup"><span data-stu-id="1fe82-104">In order to use these methods, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be `true`.</span></span>  
  
 <span data-ttu-id="1fe82-105"><xref:System.Xml.XPath.XPathNavigator> bir XML belgesi düzenleyebilirsiniz nesneleri <xref:System.Xml.XmlDocument.CreateNavigator%2A> yöntemi <xref:System.Xml.XmlDocument> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1fe82-105"><xref:System.Xml.XPath.XPathNavigator> objects that can edit an XML document are created by the <xref:System.Xml.XmlDocument.CreateNavigator%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="1fe82-106"><xref:System.Xml.XPath.XPathNavigator> tarafından oluşturulan nesnelerin <xref:System.Xml.XPath.XPathDocument> sınıfı salt okunurdur ve tüm düzenleme yöntemlerini kullanmayı dener bir <xref:System.Xml.XPath.XPathNavigator> nesnesi tarafından oluşturulan bir <xref:System.Xml.XPath.XPathDocument> nesne sonuçlanıyor bir <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="1fe82-106"><xref:System.Xml.XPath.XPathNavigator> objects created by the <xref:System.Xml.XPath.XPathDocument> class are read-only and any attempt to use the editing methods of an <xref:System.Xml.XPath.XPathNavigator> object created by an <xref:System.Xml.XPath.XPathDocument> object results in a <xref:System.NotSupportedException>.</span></span>  
  
 <span data-ttu-id="1fe82-107">Düzenlenebilir oluşturma hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator> nesneleri bkz [XPathDocument ve XmlDocument kullanarak XML verileri okuma](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span><span class="sxs-lookup"><span data-stu-id="1fe82-107">For more information about creating editable <xref:System.Xml.XPath.XPathNavigator> objects, see [Reading XML Data using XPathDocument and XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span></span>  
  
## <a name="inserting-nodes"></a><span data-ttu-id="1fe82-108">Düğümler ekleme</span><span class="sxs-lookup"><span data-stu-id="1fe82-108">Inserting Nodes</span></span>  
 <span data-ttu-id="1fe82-109"><xref:System.Xml.XPath.XPathNavigator> Sınıfı eşdüzey, alt öğe ve öznitelik düğümleri bir XML belgesinde eklemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="1fe82-109">The <xref:System.Xml.XPath.XPathNavigator> class provides methods to insert sibling, child, and attribute nodes in an XML document.</span></span> <span data-ttu-id="1fe82-110">Geçerli konumu ile ilgili farklı konumlarda düğümleri ve öznitelikler eklemek bu yöntemleri izin bir <xref:System.Xml.XPath.XPathNavigator> nesne ve aşağıdaki bölümlerde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="1fe82-110">These methods allow you to insert nodes and attributes in different locations in relation to the current position of an <xref:System.Xml.XPath.XPathNavigator> object and are described in the following sections.</span></span>  
  
### <a name="inserting-sibling-nodes"></a><span data-ttu-id="1fe82-111">Eşdüzey düğümler ekleme</span><span class="sxs-lookup"><span data-stu-id="1fe82-111">Inserting Sibling Nodes</span></span>  
 <span data-ttu-id="1fe82-112"><xref:System.Xml.XPath.XPathNavigator> Sınıfı eşdüzey düğümleri eklemek için aşağıdaki yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="1fe82-112">The <xref:System.Xml.XPath.XPathNavigator> class provides the following methods to insert sibling nodes.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A>  
  
 <span data-ttu-id="1fe82-113">Bu yöntemler eşdüzey düğümleri önceki ve sonraki düğümü Ekle bir <xref:System.Xml.XPath.XPathNavigator> nesne üzerinde konumlandırılmış şu anda.</span><span class="sxs-lookup"><span data-stu-id="1fe82-113">These methods insert sibling nodes before and after the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="1fe82-114"><xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> Ve <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> yöntemleri aşırı ve kabul bir `string`, <xref:System.Xml.XmlReader> nesnesi veya <xref:System.Xml.XPath.XPathNavigator> parametre olarak eklenecek eşdüzey düğüm içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="1fe82-114">The <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> methods are overloaded and accept a `string`, <xref:System.Xml.XmlReader> object, or <xref:System.Xml.XPath.XPathNavigator> object containing the sibling node to add as parameters.</span></span> <span data-ttu-id="1fe82-115">Her iki yöntem aynı zamanda sonuç bir <xref:System.Xml.XmlWriter> eşdüzey düğümleri eklemek için kullanılan nesne.</span><span class="sxs-lookup"><span data-stu-id="1fe82-115">Both methods also return an <xref:System.Xml.XmlWriter> object used to insert sibling nodes.</span></span>  
  
 <span data-ttu-id="1fe82-116"><xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> Ve <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> yöntemleri eklemek tek Eşdüzey Düğüm önce ve sonra düğümü bir <xref:System.Xml.XPath.XPathNavigator> nesne şu anda yerde konumlandırılır ad alanı öneki, yerel ad, ad alanı URI ve parametre olarak belirtilen değeri kullanarak.</span><span class="sxs-lookup"><span data-stu-id="1fe82-116">The <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> methods insert a single sibling node before and after the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on using the namespace prefix, local name, namespace URI, and value specified as parameters.</span></span>  
  
 <span data-ttu-id="1fe82-117">Aşağıdaki örnekte yeni bir `pages` önce eklenen öğe `price` ilk alt öğenin `book` öğesinde `contosoBooks.xml` dosya.</span><span class="sxs-lookup"><span data-stu-id="1fe82-117">In the following example a new `pages` element is inserted before the `price` child element of the first `book` element in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#19](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#19)]
 [!code-csharp[XPathNavigatorMethods#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#19)]
 [!code-vb[XPathNavigatorMethods#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#19)]  
  
 <span data-ttu-id="1fe82-118">Örnek alan `contosoBooks.xml` girdi olarak dosya.</span><span class="sxs-lookup"><span data-stu-id="1fe82-118">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="1fe82-119">Hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> ve <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> yöntemleri bkz <xref:System.Xml.XPath.XPathNavigator> sınıfı başvuru belgeleri.</span><span class="sxs-lookup"><span data-stu-id="1fe82-119">For more information about the <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> methods, see the <xref:System.Xml.XPath.XPathNavigator> class reference documentation.</span></span>  
  
### <a name="inserting-child-nodes"></a><span data-ttu-id="1fe82-120">Alt düğümler ekleme</span><span class="sxs-lookup"><span data-stu-id="1fe82-120">Inserting Child Nodes</span></span>  
 <span data-ttu-id="1fe82-121"><xref:System.Xml.XPath.XPathNavigator> Sınıfı alt düğümler eklemek için aşağıdaki yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="1fe82-121">The <xref:System.Xml.XPath.XPathNavigator> class provides the following methods to insert child nodes.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A>  
  
 <span data-ttu-id="1fe82-122">Bu yöntemler ekleme ve sonuna ve düğümünün alt düğümleri listesini başına alt düğümler başına bir <xref:System.Xml.XPath.XPathNavigator> nesne üzerinde konumlandırılmış şu anda.</span><span class="sxs-lookup"><span data-stu-id="1fe82-122">These methods append and prepend child nodes to the end of and the beginning of the list of child nodes of the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="1fe82-123">"Eşdüzey düğümleri ekleme" bölümünde, yöntemler gibi <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> ve <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> yöntemleri kabul bir `string`, <xref:System.Xml.XmlReader> nesnesi veya <xref:System.Xml.XPath.XPathNavigator> parametre olarak eklenecek alt düğüm içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="1fe82-123">Like the methods in the "Inserting Sibling Nodes" section, the <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> methods accept a `string`, <xref:System.Xml.XmlReader> object, or <xref:System.Xml.XPath.XPathNavigator> object containing the child node to add as parameters.</span></span> <span data-ttu-id="1fe82-124">Her iki yöntem aynı zamanda sonuç bir <xref:System.Xml.XmlWriter> alt düğümler eklemek için kullanılan nesne.</span><span class="sxs-lookup"><span data-stu-id="1fe82-124">Both methods also return an <xref:System.Xml.XmlWriter> object used to insert child nodes.</span></span>  
  
 <span data-ttu-id="1fe82-125">Ayrıca, "Eşdüzey düğümleri ekleme" bölümündeki yöntemleri ister <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> ve <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> yöntemleri sonuna ve düğümünün alt düğümleri listesini başına tek bir alt düğümü ekleme bir <xref:System.Xml.XPath.XPathNavigator> nesne şu anda yerde konumlandırılır kullanarak ad alanı öneki, yerel ad, ad alanı URI ve parametre olarak belirtilen değeri.</span><span class="sxs-lookup"><span data-stu-id="1fe82-125">Also like the methods in the "Inserting Sibling Nodes" section, the <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> methods insert a single child node to the end of and the beginning of the list of child nodes of the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on using the namespace prefix, local name, namespace URI, and value specified as parameters.</span></span>  
  
 <span data-ttu-id="1fe82-126">Aşağıdaki örnekte, yeni bir `pages` alt öğesi ilk alt öğelerini listesine eklenmiş `book` öğesinde `contosoBooks.xml` dosya.</span><span class="sxs-lookup"><span data-stu-id="1fe82-126">In the following example, a new `pages` child element is appended to the list of child elements of the first `book` element in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#2)]
 [!code-csharp[XPathNavigatorMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#2)]
 [!code-vb[XPathNavigatorMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#2)]  
  
 <span data-ttu-id="1fe82-127">Örnek alan `contosoBooks.xml` girdi olarak dosya.</span><span class="sxs-lookup"><span data-stu-id="1fe82-127">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="1fe82-128">Hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> ve <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> yöntemleri bkz <xref:System.Xml.XPath.XPathNavigator> sınıfı başvuru belgeleri.</span><span class="sxs-lookup"><span data-stu-id="1fe82-128">For more information about the <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> methods, see the <xref:System.Xml.XPath.XPathNavigator> class reference documentation.</span></span>  
  
### <a name="inserting-attribute-nodes"></a><span data-ttu-id="1fe82-129">Öznitelik düğümleri ekleme</span><span class="sxs-lookup"><span data-stu-id="1fe82-129">Inserting Attribute Nodes</span></span>  
 <span data-ttu-id="1fe82-130"><xref:System.Xml.XPath.XPathNavigator> Sınıfı, öznitelik düğümleri eklemek için aşağıdaki yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="1fe82-130">The <xref:System.Xml.XPath.XPathNavigator> class provides the following methods to insert attribute nodes.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A>  
  
 <span data-ttu-id="1fe82-131">Bu yöntemleri öznitelik düğümleri üzerinde öğe düğümü Ekle bir <xref:System.Xml.XPath.XPathNavigator> nesne üzerinde konumlandırılmış şu anda.</span><span class="sxs-lookup"><span data-stu-id="1fe82-131">These methods insert attribute nodes on the element node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="1fe82-132"><xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> Yöntemi öğesi düğümde bir öznitelik düğümü oluşturur bir <xref:System.Xml.XPath.XPathNavigator> nesne şu anda yerde konumlandırılır ad alanı öneki, yerel ad, ad alanı URI ve parametre olarak belirtilen değeri kullanarak.</span><span class="sxs-lookup"><span data-stu-id="1fe82-132">The <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> method creates an attribute node on the element node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on using the namespace prefix, local name, namespace URI, and value specified as parameters.</span></span> <span data-ttu-id="1fe82-133"><xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> Yöntemi döndürür bir <xref:System.Xml.XmlWriter> öznitelik düğümleri eklemek için kullanılan nesne.</span><span class="sxs-lookup"><span data-stu-id="1fe82-133">The <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> method returns an <xref:System.Xml.XmlWriter> object used to insert attribute nodes.</span></span>  
  
 <span data-ttu-id="1fe82-134">Aşağıdaki örnekte, yeni `discount` ve `currency` öznitelikleri üzerinde oluşturulan `price` ilk alt öğenin `book` öğesinde `contosoBooks.xml` kullanarak dosya <xref:System.Xml.XmlWriter> döndürülen nesne <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> yöntem.</span><span class="sxs-lookup"><span data-stu-id="1fe82-134">In the following example, new `discount` and `currency` attributes are created on the `price` child element of the first `book` element in the `contosoBooks.xml` file using the <xref:System.Xml.XmlWriter> object returned from the <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> method.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#8](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#8)]
 [!code-csharp[XPathNavigatorMethods#8](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#8)]
 [!code-vb[XPathNavigatorMethods#8](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#8)]  
  
 <span data-ttu-id="1fe82-135">Örnek alan `contosoBooks.xml` girdi olarak dosya.</span><span class="sxs-lookup"><span data-stu-id="1fe82-135">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="1fe82-136">Hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> ve <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> yöntemleri bkz <xref:System.Xml.XPath.XPathNavigator> sınıfı başvuru belgeleri.</span><span class="sxs-lookup"><span data-stu-id="1fe82-136">For more information about the <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> and <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> methods, see the <xref:System.Xml.XPath.XPathNavigator> class reference documentation.</span></span>  
  
## <a name="copying-nodes"></a><span data-ttu-id="1fe82-137">Düğümleri kopyalama</span><span class="sxs-lookup"><span data-stu-id="1fe82-137">Copying Nodes</span></span>  
 <span data-ttu-id="1fe82-138">Bazı durumlarda içeriği başka bir XML belgesi bir XML belgesi doldurmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1fe82-138">In certain cases you may want to populate an XML document with the contents from another XML document.</span></span> <span data-ttu-id="1fe82-139">Her iki <xref:System.Xml.XPath.XPathNavigator> sınıfı ve <xref:System.Xml.XmlWriter> sınıfı düğümlerine kopyalayabilir bir <xref:System.Xml.XmlDocument> mevcut bir nesne <xref:System.Xml.XmlReader> nesne veya <xref:System.Xml.XPath.XPathNavigator> nesne.</span><span class="sxs-lookup"><span data-stu-id="1fe82-139">Both the <xref:System.Xml.XPath.XPathNavigator> class and the <xref:System.Xml.XmlWriter> class can copy nodes to an <xref:System.Xml.XmlDocument> object from an existing <xref:System.Xml.XmlReader> object or <xref:System.Xml.XPath.XPathNavigator> object.</span></span>  
  
 <span data-ttu-id="1fe82-140"><xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> Ve <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> yöntemlerinin <xref:System.Xml.XPath.XPathNavigator> tümü, kabul eden aşırı yüklemeler sahip sınıf bir <xref:System.Xml.XPath.XPathNavigator> nesnesi veya bir <xref:System.Xml.XmlReader> bir parametre olarak nesne.</span><span class="sxs-lookup"><span data-stu-id="1fe82-140">The <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class all have overloads that can accept an <xref:System.Xml.XPath.XPathNavigator> object or an <xref:System.Xml.XmlReader> object as a parameter.</span></span>  
  
 <span data-ttu-id="1fe82-141"><xref:System.Xml.XmlWriter.WriteNode%2A> Yöntemi <xref:System.Xml.XmlWriter> sınıfında, kabul eden aşırı yüklemeler bir <xref:System.Xml.XmlNode>, <xref:System.Xml.XmlReader>, veya <xref:System.Xml.XPath.XPathNavigator> nesne.</span><span class="sxs-lookup"><span data-stu-id="1fe82-141">The <xref:System.Xml.XmlWriter.WriteNode%2A> method of the <xref:System.Xml.XmlWriter> class has overloads that can accept an <xref:System.Xml.XmlNode>, <xref:System.Xml.XmlReader>, or <xref:System.Xml.XPath.XPathNavigator> object.</span></span>  
  
 <span data-ttu-id="1fe82-142">Aşağıdaki örnekte tüm kopyalar `book` bir belgeden öğelerine.</span><span class="sxs-lookup"><span data-stu-id="1fe82-142">The following example copies all the `book` elements from one document to another.</span></span>  
  
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
  
## <a name="inserting-values"></a><span data-ttu-id="1fe82-143">Değerleri ekleniyor</span><span class="sxs-lookup"><span data-stu-id="1fe82-143">Inserting Values</span></span>  
 <span data-ttu-id="1fe82-144"><xref:System.Xml.XPath.XPathNavigator> Sağlar sınıfını <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> ve <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> değerleri için bir düğüm eklemek için yöntemleri bir <xref:System.Xml.XmlDocument> nesne.</span><span class="sxs-lookup"><span data-stu-id="1fe82-144">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods to insert values for a node into an <xref:System.Xml.XmlDocument> object.</span></span>  
  
### <a name="inserting-untyped-values"></a><span data-ttu-id="1fe82-145">Yazılmamış değerler ekleme</span><span class="sxs-lookup"><span data-stu-id="1fe82-145">Inserting Untyped Values</span></span>  
 <span data-ttu-id="1fe82-146"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Yöntemi yalnızca ekler yazılmamış `string` düğümün değeri olarak bir parametre olarak geçirilen değer <xref:System.Xml.XPath.XPathNavigator> nesne üzerinde konumlandırılmış şu anda.</span><span class="sxs-lookup"><span data-stu-id="1fe82-146">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method simply inserts the untyped `string` value passed as a parameter as the value of the node the <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="1fe82-147">Değer, her türlü olmadan veya şema bilgileri kullanılabilir durumdaysa, yeni değer düğüm türüne göre geçerli olduğu doğrulanıyor olmadan eklenir.</span><span class="sxs-lookup"><span data-stu-id="1fe82-147">The value is inserted without any type or without verifying that the new value is valid according to the type of the node if schema information is available.</span></span>  
  
 <span data-ttu-id="1fe82-148">Aşağıdaki örnekte, <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> tümünü güncelleştirmek için kullanılan yöntemi `price` öğelerinde `contosoBooks.xml` dosya.</span><span class="sxs-lookup"><span data-stu-id="1fe82-148">In the following example, the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method is used to update all `price` elements in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 <span data-ttu-id="1fe82-149">Örnek alan `contosoBooks.xml` girdi olarak dosya.</span><span class="sxs-lookup"><span data-stu-id="1fe82-149">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="inserting-typed-values"></a><span data-ttu-id="1fe82-150">Yazılan değerleri ekleniyor</span><span class="sxs-lookup"><span data-stu-id="1fe82-150">Inserting Typed Values</span></span>  
 <span data-ttu-id="1fe82-151">Bir düğüm türü basit bir W3C XML Şeması olduğunda tür, tarafından eklenen yeni değer <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> yöntemi değeri ayarlanmadan önce basit türe ilişkin modelleri karşı denetlenir.</span><span class="sxs-lookup"><span data-stu-id="1fe82-151">When the type of a node is a W3C XML Schema simple type, the new value inserted by the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method is checked against the facets of the simple type before the value is set.</span></span> <span data-ttu-id="1fe82-152">Yeni değer düğüm türüne göre geçerli değilse (örneğin, bir değeri ayarlamak `-1` türü olan bir öğede `xs:positiveInteger`), bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="1fe82-152">If the new value is not valid according to the type of the node (for example, setting a value of `-1` on an element whose type is `xs:positiveInteger`), it results in an exception.</span></span>  
  
 <span data-ttu-id="1fe82-153">Aşağıdaki örnek, değerini değiştirme girişiminde `price` ilk öğenin `book` öğesinde `contosoBooks.xml` dosyasını bir <xref:System.DateTime> değeri.</span><span class="sxs-lookup"><span data-stu-id="1fe82-153">The following example attempts to change the value of the `price` element of the first `book` element in the `contosoBooks.xml` file to a <xref:System.DateTime> value.</span></span> <span data-ttu-id="1fe82-154">XML şema türü olduğundan `price` öğesi olarak tanımlanmış olan `xs:decimal` içinde `contosoBooks.xsd` dosyaları, bu sonuçları bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="1fe82-154">Because the XML Schema type of the `price` element is defined as `xs:decimal` in the `contosoBooks.xsd` files, this results in an exception.</span></span>  
  
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
  
 <span data-ttu-id="1fe82-155">Örnek alan `contosoBooks.xml` girdi olarak dosya.</span><span class="sxs-lookup"><span data-stu-id="1fe82-155">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="1fe82-156">Bu örnek ayrıca alır `contosoBooks.xsd` girdi olarak.</span><span class="sxs-lookup"><span data-stu-id="1fe82-156">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
## <a name="the-innerxml-and-outerxml-properties"></a><span data-ttu-id="1fe82-157">Sınıfının InnerXml ve OuterXml özellikleri</span><span class="sxs-lookup"><span data-stu-id="1fe82-157">The InnerXml and OuterXml Properties</span></span>  
 <span data-ttu-id="1fe82-158"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özelliklerini <xref:System.Xml.XPath.XPathNavigator> sınıfını değiştirin XML işaretlemesini düğümlerin bir <xref:System.Xml.XPath.XPathNavigator> nesne üzerinde konumlandırılmış şu anda.</span><span class="sxs-lookup"><span data-stu-id="1fe82-158">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class change the XML markup of the nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="1fe82-159"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Özelliğini değiştirir XML işaretlemesini alt düğümlerin bir <xref:System.Xml.XPath.XPathNavigator> nesne şu anda yerde konumlandırılır üzerinde belirli XML ayrıştırılmış içeriğiyle `string`.</span><span class="sxs-lookup"><span data-stu-id="1fe82-159">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on with the parsed contents of the given XML `string`.</span></span> <span data-ttu-id="1fe82-160">Benzer şekilde, <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özelliğini değiştirir XML işaretlemesini alt düğümlerin bir <xref:System.Xml.XPath.XPathNavigator> nesne şu anda yerde konumlandırılır üzerinde geçerli düğüm yanı sıra kendisini.</span><span class="sxs-lookup"><span data-stu-id="1fe82-160">Similarly, the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on as well as the current node itself.</span></span>  
  
 <span data-ttu-id="1fe82-161">Bu konuda, açıklanan yöntemlerin yanı sıra <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özellikler XML belgesinde düğümleri ve değerler eklemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1fe82-161">In addition to the methods described in this topic, the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties can be used to insert nodes and values in an XML document.</span></span> <span data-ttu-id="1fe82-162">Kullanma hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> düğümleri ve değerler eklemek için özellikleri görmek [değiştirme XPathNavigator kullanarak XML verilerini](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) konu.</span><span class="sxs-lookup"><span data-stu-id="1fe82-162">For more information about using the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties to insert nodes and values, see the [Modify XML Data using XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) topic.</span></span>  
  
## <a name="namespace-and-xmllang-conflicts"></a><span data-ttu-id="1fe82-163">Namespace ve XML: lang çakışmaları</span><span class="sxs-lookup"><span data-stu-id="1fe82-163">Namespace and xml:lang Conflicts</span></span>  
 <span data-ttu-id="1fe82-164">Ad alanı kapsamına ilgili belirli çakışma ve `xml:lang` bildirimleri eklerken kullanarak XML verilerini oluşabilir <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> ve <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> yöntemlerinin <xref:System.Xml.XPath.XPathNavigator> elesınıfı<xref:System.Xml.XmlReader>parametre olarak nesne.</span><span class="sxs-lookup"><span data-stu-id="1fe82-164">Certain conflicts related to the scope of namespace and `xml:lang` declarations can occur when inserting XML data using the <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class that take <xref:System.Xml.XmlReader> objects as parameters.</span></span>  
  
 <span data-ttu-id="1fe82-165">Olası ad çakışmalarını aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1fe82-165">The following are the possible namespace conflicts.</span></span>  
  
- <span data-ttu-id="1fe82-166">Bir ad alanı kapsamındaki içinde ise <xref:System.Xml.XmlReader> nerede önek için ad alanı URI eşlemesi içinde değil, nesnenin bağlam <xref:System.Xml.XPath.XPathNavigator> nesnenin bağlamı, yeni bir ad alanı bildirimi yeni eklenen düğümüne eklenir.</span><span class="sxs-lookup"><span data-stu-id="1fe82-166">If there is a namespace in-scope within the <xref:System.Xml.XmlReader> object's context, where the prefix to namespace URI mapping is not in the <xref:System.Xml.XPath.XPathNavigator> object's context, a new namespace declaration is added to the newly inserted node.</span></span>  
  
- <span data-ttu-id="1fe82-167">Kapsamdaki aynı ad URI ise, her ikisi içinde <xref:System.Xml.XmlReader> nesnenin bağlam ve <xref:System.Xml.XPath.XPathNavigator> nesnenin bağlamı, ancak her iki içerikte eşlenmiş farklı bir önek varsa, yeni bir ad alanı bildirimi, ön eki yeni eklenen düğümüne eklenir ve ad alanı URI alınan <xref:System.Xml.XmlReader> nesne.</span><span class="sxs-lookup"><span data-stu-id="1fe82-167">If the same namespace URI is in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but has a different prefix mapped to it in both contexts, a new namespace declaration is added to the newly inserted node, with the prefix and namespace URI taken from the <xref:System.Xml.XmlReader> object.</span></span>  
  
- <span data-ttu-id="1fe82-168">Kapsamdaki aynı ad alanı öneki ise öğesinde hem de <xref:System.Xml.XmlReader> nesnenin bağlam ve <xref:System.Xml.XPath.XPathNavigator> nesnenin bağlamı, ancak sahip farklı bir ad alanı URI eşlenmesi için her iki içerikte yeni bir ad alanı bildirimi yeni eklenen düğümüne eklenir, Bu ad alanı URI alınan önekiyle yeniden bildirir <xref:System.Xml.XmlReader> nesne.</span><span class="sxs-lookup"><span data-stu-id="1fe82-168">If the same namespace prefix is in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but has a different namespace URI mapped to it in both contexts, a new namespace declaration is added to the newly inserted node which re-declares that prefix with the namespace URI taken from <xref:System.Xml.XmlReader> object.</span></span>  
  
- <span data-ttu-id="1fe82-169">Varsa ön ek olarak, hem de ad alanı URI <xref:System.Xml.XmlReader> nesnenin bağlam ve <xref:System.Xml.XPath.XPathNavigator> nesnenin içeriği aynı olduğundan, hiçbir yeni ad alanı bildirimi yeni eklenen düğümüne eklenir.</span><span class="sxs-lookup"><span data-stu-id="1fe82-169">If the prefix as well as the namespace URI in both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context is the same, no new namespace declaration is added to the newly inserted node.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1fe82-170">Yukarıdaki açıklamada ile boş ad alanı bildirimi için de geçerlidir. `string` bir önek (örneğin, varsayılan ad alanı bildirimi) olarak.</span><span class="sxs-lookup"><span data-stu-id="1fe82-170">The description above also applies to namespace declarations with the empty `string` as a prefix (for example, the default namespace declaration).</span></span>  
  
 <span data-ttu-id="1fe82-171">Aşağıdaki yapılabilen `xml:lang` çakışıyor.</span><span class="sxs-lookup"><span data-stu-id="1fe82-171">The following are the possible `xml:lang` conflicts.</span></span>  
  
- <span data-ttu-id="1fe82-172">Varsa bir `xml:lang` kapsam içinde öznitelik <xref:System.Xml.XmlReader> nesnenin bağlam de <xref:System.Xml.XPath.XPathNavigator> nesnenin bağlamı bir `xml:lang` değeri alınan öznitelik <xref:System.Xml.XmlReader> nesne yeni eklenen düğümüne eklenir.</span><span class="sxs-lookup"><span data-stu-id="1fe82-172">If there is an `xml:lang` attribute in-scope within the <xref:System.Xml.XmlReader> object's context but not in the <xref:System.Xml.XPath.XPathNavigator> object's context, an `xml:lang` attribute whose value is taken from the <xref:System.Xml.XmlReader> object is added to the newly inserted node.</span></span>  
  
- <span data-ttu-id="1fe82-173">Varsa bir `xml:lang` kapsamındaki her ikisi içinde öznitelik <xref:System.Xml.XmlReader> nesnenin bağlam ve <xref:System.Xml.XPath.XPathNavigator> nesnenin bağlamı, ancak her farklı bir değere sahip bir `xml:lang` değeri alınan öznitelik <xref:System.Xml.XmlReader> eklenir Yeni eklenen düğüm.</span><span class="sxs-lookup"><span data-stu-id="1fe82-173">If there is an `xml:lang` attribute in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but each has a different value, an `xml:lang` attribute whose value is taken from the <xref:System.Xml.XmlReader> object is added to the newly inserted node.</span></span>  
  
- <span data-ttu-id="1fe82-174">Varsa bir `xml:lang` kapsamındaki her ikisi içinde öznitelik <xref:System.Xml.XmlReader> nesnenin bağlam ve <xref:System.Xml.XPath.XPathNavigator> nesnenin bağlamı, ancak her yeni aynı değere sahip `xml:lang` özniteliği, yeni eklenen düğümüne eklenir.</span><span class="sxs-lookup"><span data-stu-id="1fe82-174">If there is an `xml:lang` attribute in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but each with the same value, no new `xml:lang` attribute is added on the newly inserted node.</span></span>  
  
- <span data-ttu-id="1fe82-175">Varsa bir `xml:lang` kapsam içinde öznitelik <xref:System.Xml.XPath.XPathNavigator> nesnenin bağlamı, ancak hiçbiri varolan <xref:System.Xml.XmlReader> nesnenin bağlamı, Hayır `xml:lang` özniteliği, yeni eklenen düğümüne eklenir.</span><span class="sxs-lookup"><span data-stu-id="1fe82-175">If there is an `xml:lang` attribute in-scope within the <xref:System.Xml.XPath.XPathNavigator> object's context, but none existing in the <xref:System.Xml.XmlReader> object's context, no `xml:lang` attribute is added to the newly inserted node.</span></span>  
  
## <a name="inserting-nodes-with-xmlwriter"></a><span data-ttu-id="1fe82-176">XmlWriter ile düğüm ekleme</span><span class="sxs-lookup"><span data-stu-id="1fe82-176">Inserting Nodes with XmlWriter</span></span>  
 <span data-ttu-id="1fe82-177">"Düğümleri ve değerler ekleme" bölümünde açıklanan eşdüzey, alt öğe ve öznitelik düğümleri eklemek için kullanılan yöntemler aşırı yüklenmesi sebebiyledir.</span><span class="sxs-lookup"><span data-stu-id="1fe82-177">The methods used to insert sibling, child and attribute nodes described in the "Inserting Nodes and Values" section are overloaded.</span></span> <span data-ttu-id="1fe82-178"><xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> Ve <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> yöntemlerinin <xref:System.Xml.XPath.XPathNavigator> sınıfı döndürülecek bir <xref:System.Xml.XmlWriter> düğümleri eklemek için kullanılan nesne.</span><span class="sxs-lookup"><span data-stu-id="1fe82-178">The <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> and <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class return an <xref:System.Xml.XmlWriter> object used to insert nodes.</span></span>  
  
### <a name="unsupported-xmlwriter-methods"></a><span data-ttu-id="1fe82-179">Desteklenmeyen XmlWriter yöntemleri</span><span class="sxs-lookup"><span data-stu-id="1fe82-179">Unsupported XmlWriter Methods</span></span>  
 <span data-ttu-id="1fe82-180">Tüm bilgileri kullanarak bir XML belgesi yazmak için kullanılan yöntemleri <xref:System.Xml.XmlWriter> sınıfı tarafından desteklenen <xref:System.Xml.XPath.XPathNavigator> XPath veri modelini ve belge nesne modeli (DOM) arasındaki farkı nedeniyle sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1fe82-180">Not all of the methods used for writing information to an XML document using the <xref:System.Xml.XmlWriter> class are supported by the <xref:System.Xml.XPath.XPathNavigator> class due to difference between the XPath data model and the Document Object Model (DOM).</span></span>  
  
 <span data-ttu-id="1fe82-181">Aşağıdaki tabloda açıklanmıştır <xref:System.Xml.XmlWriter> sınıfı yöntemleri tarafından desteklenmeyen <xref:System.Xml.XPath.XPathNavigator> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1fe82-181">The following table describes the <xref:System.Xml.XmlWriter> class methods not supported by the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
|<span data-ttu-id="1fe82-182">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1fe82-182">Method</span></span>|<span data-ttu-id="1fe82-183">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1fe82-183">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.XmlWriter.WriteEntityRef%2A>|<span data-ttu-id="1fe82-184">Oluşturur bir <xref:System.NotSupportedException> özel durum.</span><span class="sxs-lookup"><span data-stu-id="1fe82-184">Throws a <xref:System.NotSupportedException> exception.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteDocType%2A>|<span data-ttu-id="1fe82-185">Oluşturur ve kök düzeyiyle göz ardı bir <xref:System.NotSupportedException> herhangi bir düzeyde XML belgesi olarak adlandırılan özel durum.</span><span class="sxs-lookup"><span data-stu-id="1fe82-185">Ignored at the root level and throws a <xref:System.NotSupportedException> exception if called at any other level in the XML document.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteCData%2A>|<span data-ttu-id="1fe82-186">Bir çağrı olarak kabul <xref:System.Xml.XmlWriter.WriteString%2A> eşdeğer karakter veya karakterler için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1fe82-186">Treated as a call to the <xref:System.Xml.XmlWriter.WriteString%2A> method for the equivalent character or characters.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteCharEntity%2A>|<span data-ttu-id="1fe82-187">Bir çağrı olarak kabul <xref:System.Xml.XmlWriter.WriteString%2A> eşdeğer karakter veya karakterler için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1fe82-187">Treated as a call to the <xref:System.Xml.XmlWriter.WriteString%2A> method for the equivalent character or characters.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteSurrogateCharEntity%2A>|<span data-ttu-id="1fe82-188">Bir çağrı olarak kabul <xref:System.Xml.XmlWriter.WriteString%2A> eşdeğer karakter veya karakterler için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1fe82-188">Treated as a call to the <xref:System.Xml.XmlWriter.WriteString%2A> method for the equivalent character or characters.</span></span>|  
  
 <span data-ttu-id="1fe82-189">Hakkında daha fazla bilgi için <xref:System.Xml.XmlWriter> sınıfı <xref:System.Xml.XmlWriter> sınıfı başvuru belgeleri.</span><span class="sxs-lookup"><span data-stu-id="1fe82-189">For more information about the <xref:System.Xml.XmlWriter> class, see the <xref:System.Xml.XmlWriter> class reference documentation.</span></span>  
  
### <a name="multiple-xmlwriter-objects"></a><span data-ttu-id="1fe82-190">Birden çok XmlWriter nesnesi</span><span class="sxs-lookup"><span data-stu-id="1fe82-190">Multiple XmlWriter Objects</span></span>  
 <span data-ttu-id="1fe82-191">Birden çok olması mümkündür <xref:System.Xml.XPath.XPathNavigator> nesneleri işaret eden bir XML farklı bölümlerine bir veya daha fazla açık belge <xref:System.Xml.XmlWriter> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="1fe82-191">It is possible to have multiple <xref:System.Xml.XPath.XPathNavigator> objects pointing to different parts of an XML document with one or more open <xref:System.Xml.XmlWriter> objects.</span></span> <span data-ttu-id="1fe82-192">Birden çok <xref:System.Xml.XmlWriter> nesneleri izin verilen ve tek iş parçacıklı senaryolarında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="1fe82-192">Multiple <xref:System.Xml.XmlWriter> objects are allowed and supported in single-threaded scenarios.</span></span>  
  
 <span data-ttu-id="1fe82-193">Birden çok kullanırken dikkate alınması gereken önemli notlar şunlardır <xref:System.Xml.XmlWriter> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="1fe82-193">The following are important notes to consider when using multiple <xref:System.Xml.XmlWriter> objects.</span></span>  
  
- <span data-ttu-id="1fe82-194">XML parçaları tarafından yazılan <xref:System.Xml.XmlWriter> nesneleri XML'e eklenen zaman belge <xref:System.Xml.XmlWriter.Close%2A> yöntemi her <xref:System.Xml.XmlWriter> nesne çağrılır.</span><span class="sxs-lookup"><span data-stu-id="1fe82-194">XML fragments written by <xref:System.Xml.XmlWriter> objects are added to the XML document when the <xref:System.Xml.XmlWriter.Close%2A> method of each <xref:System.Xml.XmlWriter> object is called.</span></span> <span data-ttu-id="1fe82-195">O noktaya kadar <xref:System.Xml.XmlWriter> nesnesi bağlantısı kesilmiş bir parça yazma.</span><span class="sxs-lookup"><span data-stu-id="1fe82-195">Until that point, the <xref:System.Xml.XmlWriter> object is writing a disconnected fragment.</span></span> <span data-ttu-id="1fe82-196">Bir işlem tarafından yazılan tüm parçaları bir XML belgesi üzerinde gerçekleştirilirse bir <xref:System.Xml.XmlWriter> önce nesne <xref:System.Xml.XmlWriter.Close%2A> çağrıldı, etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="1fe82-196">If an operation is performed on the XML document, any fragments being written by an <xref:System.Xml.XmlWriter> object, before the <xref:System.Xml.XmlWriter.Close%2A> has been called, are not affected.</span></span>  
  
- <span data-ttu-id="1fe82-197">Açık ise <xref:System.Xml.XmlWriter> belirli bir XML alt ağaç ve bu alt ağaç nesnesi silindiğinde <xref:System.Xml.XmlWriter> nesne alt ağacı için yine de ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="1fe82-197">If there is an open <xref:System.Xml.XmlWriter> object on a particular XML subtree and that subtree is deleted, the <xref:System.Xml.XmlWriter> object may still add to the sub-tree.</span></span> <span data-ttu-id="1fe82-198">Alt ağacı, yalnızca silinen bir parçası haline gelir.</span><span class="sxs-lookup"><span data-stu-id="1fe82-198">The subtree simply becomes a deleted fragment.</span></span>  
  
- <span data-ttu-id="1fe82-199">Birden çok <xref:System.Xml.XmlWriter> nesneleri, XML belgesi içindeki aynı noktada açıldığında, sırayı XML belgesinde eklenen <xref:System.Xml.XmlWriter> nesneleri kapatılır, bunlar açık sırasına göre değil.</span><span class="sxs-lookup"><span data-stu-id="1fe82-199">If multiple <xref:System.Xml.XmlWriter> objects are opened at the same point in the XML document, they are added to the XML document in the order in which the <xref:System.Xml.XmlWriter> objects are closed, not in the order in which they were opened.</span></span>  
  
 <span data-ttu-id="1fe82-200">Aşağıdaki örnek, oluşturur bir <xref:System.Xml.XmlDocument> nesne, oluşturur bir <xref:System.Xml.XPath.XPathNavigator> nesne ve kullandığı <xref:System.Xml.XmlWriter> tarafından döndürülen nesne <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> ilk kitap yapısını oluşturmak için gereken yöntemini `books.xml` dosya.</span><span class="sxs-lookup"><span data-stu-id="1fe82-200">The following example creates an <xref:System.Xml.XmlDocument> object, creates an <xref:System.Xml.XPath.XPathNavigator> object, and then uses the <xref:System.Xml.XmlWriter> object returned by the <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> method to create the structure of the first book in the `books.xml` file.</span></span> <span data-ttu-id="1fe82-201">Örnek olarak sonra kaydeder `book.xml` dosya.</span><span class="sxs-lookup"><span data-stu-id="1fe82-201">The example then saves it as the `book.xml` file.</span></span>  
  
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
  
## <a name="saving-an-xml-document"></a><span data-ttu-id="1fe82-202">Bir XML belgesi kaydediliyor</span><span class="sxs-lookup"><span data-stu-id="1fe82-202">Saving an XML Document</span></span>  
 <span data-ttu-id="1fe82-203">Yapılan değişiklikler kaydedilirken bir <xref:System.Xml.XmlDocument> nesne bu konuda açıklanan yöntemlerden sonucunu yöntemleri kullanılarak gerçekleştirilir gibi <xref:System.Xml.XmlDocument> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1fe82-203">Saving changes made to an <xref:System.Xml.XmlDocument> object as the result of the methods described in this topic is performed using the methods of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="1fe82-204">Yapılan değişiklikleri kaydetme hakkında daha fazla bilgi için bir <xref:System.Xml.XmlDocument> nesne, bkz: [kaydetme ve belge yazma](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span><span class="sxs-lookup"><span data-stu-id="1fe82-204">For more information about saving changes made to an <xref:System.Xml.XmlDocument> object, see [Saving and Writing a Document](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fe82-205">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1fe82-205">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="1fe82-206">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="1fe82-206">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="1fe82-207">XPathNavigator Kullanarak XML Verilerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="1fe82-207">Modify XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="1fe82-208">XPathNavigator Kullanarak XML Verilerini Kaldırma</span><span class="sxs-lookup"><span data-stu-id="1fe82-208">Remove XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)
