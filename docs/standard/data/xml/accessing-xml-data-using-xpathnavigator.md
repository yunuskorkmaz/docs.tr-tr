---
title: "XML XPathNavigator kullanarak verilerine erişme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c57b46e6-5c77-408f-bc4e-67a5dcc9cc05
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 27f5bccc2ab5f229e8b726b3bff18ea7a590f5c0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="accessing-xml-data-using-xpathnavigator"></a><span data-ttu-id="efb0b-102">XML XPathNavigator kullanarak verilerine erişme</span><span class="sxs-lookup"><span data-stu-id="efb0b-102">Accessing XML Data using XPathNavigator</span></span>
<span data-ttu-id="efb0b-103"><xref:System.Xml.XPath.XPathNavigator> Sınıfı düğümleri gidin, XML verileri ayıklamak ve kesin türü belirtilmiş XML verilerine erişmek için yöntemler sağlar bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="efb0b-103">The <xref:System.Xml.XPath.XPathNavigator> class provides methods to navigate nodes, extract XML data and access strongly typed XML data in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="efb0b-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="efb0b-104">In This Section</span></span>  
 [<span data-ttu-id="efb0b-105">Düğüm kümesi Gezinti XPathNavigator kullanma</span><span class="sxs-lookup"><span data-stu-id="efb0b-105">Node Set Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)  
 <span data-ttu-id="efb0b-106">Düğüm kümesi gezinti yöntemlerini açıklar <xref:System.Xml.XPath.XPathNavigator> düğümler gitmek için kullanılan sınıf bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="efb0b-106">Describes the node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class used to navigate nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object.</span></span>  
  
 [<span data-ttu-id="efb0b-107">Özniteliği ve XPathNavigator kullanarak Namespace düğümü gezinme</span><span class="sxs-lookup"><span data-stu-id="efb0b-107">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)  
 <span data-ttu-id="efb0b-108">Öznitelik ve ad alanı düğümünü gezinti yöntemlerini açıklar <xref:System.Xml.XPath.XPathNavigator> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="efb0b-108">Describes the attribute and namespace node navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 [<span data-ttu-id="efb0b-109">XPathNavigator kullanarak XML veri ayıklamak</span><span class="sxs-lookup"><span data-stu-id="efb0b-109">Extract XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="efb0b-110">XML veri ayıklanıyor çeşitli yöntemleri açıklayan bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="efb0b-110">Describes the various methods of extracting XML data from an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object.</span></span>  
  
 [<span data-ttu-id="efb0b-111">XML verilerini XPathNavigator kullanarak yazılan kesinlikle erişme</span><span class="sxs-lookup"><span data-stu-id="efb0b-111">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="efb0b-112">Kesin türü belirtilmiş XML veri erişimi açıklayan bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> kullanarak nesne <xref:System.Xml.XPath.XPathNavigator> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="efb0b-112">Describes accessing strongly-typed XML data in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 [<span data-ttu-id="efb0b-113">Kullanıcı tanımlı işlevler ve değişkenler</span><span class="sxs-lookup"><span data-stu-id="efb0b-113">User Defined Functions and Variables</span></span>](../../../../docs/standard/data/xml/user-defined-functions-and-variables.md)  
 <span data-ttu-id="efb0b-114">Özel bir uygulama açıklar <xref:System.Xml.Xsl.XsltContext> arabirimler birlikte sınıfı <xref:System.Xml.Xsl.IXsltContextFunction> ve <xref:System.Xml.Xsl.IXsltContextVariable> uzantısı işlevleri ve değişkenler destekler.</span><span class="sxs-lookup"><span data-stu-id="efb0b-114">Describes implementing a custom <xref:System.Xml.Xsl.XsltContext> class along with the interfaces <xref:System.Xml.Xsl.IXsltContextFunction> and <xref:System.Xml.Xsl.IXsltContextVariable> that support extension functions and variables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efb0b-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="efb0b-115">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="efb0b-116">XPath veri modelini kullanarak işlem XML verileri</span><span class="sxs-lookup"><span data-stu-id="efb0b-116">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="efb0b-117">XPathDocument ve XmlDocument kullanarak XML verilerini okuma</span><span class="sxs-lookup"><span data-stu-id="efb0b-117">Reading XML Data using XPathDocument and XmlDocument</span></span>](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)  
 [<span data-ttu-id="efb0b-118">Seçildiğinde, Evaluating ve XML XPathNavigator kullanarak veri eşleştirme</span><span class="sxs-lookup"><span data-stu-id="efb0b-118">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="efb0b-119">XML XPathNavigator kullanarak verileri düzenleme</span><span class="sxs-lookup"><span data-stu-id="efb0b-119">Editing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="efb0b-120">XPathNavigator kullanarak şema doğrulaması</span><span class="sxs-lookup"><span data-stu-id="efb0b-120">Schema Validation using XPathNavigator</span></span>](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)
