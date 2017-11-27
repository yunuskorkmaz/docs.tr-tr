---
title: "Dil ile tümleşik eksenleri Visual Basic (LINQ-XML)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d450a556-a134-4261-b011-44e399660894
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d648ba7c8710f73c4aeb8dad3983f219c5fe1815
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="language-integrated-axes-in-visual-basic-linq-to-xml"></a><span data-ttu-id="b9999-102">Dil ile tümleşik eksenleri Visual Basic (LINQ-XML)</span><span class="sxs-lookup"><span data-stu-id="b9999-102">Language-Integrated Axes in Visual Basic (LINQ to XML)</span></span>
<span data-ttu-id="b9999-103">Bu bölümde doğrudan yerleşik özellikleri açıklanmıştır [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] XML erişim kolaylaştırmak için dili.</span><span class="sxs-lookup"><span data-stu-id="b9999-103">This section describes features built directly into the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] language to make it easy to access XML.</span></span> <span data-ttu-id="b9999-104">XML belgeleri için LINQ örneklerin çoğu bu tümleşik kullanın [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] eksenleri.</span><span class="sxs-lookup"><span data-stu-id="b9999-104">Many of the examples in the LINQ to XML documentation use these integrated [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] axes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b9999-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="b9999-105">In This Section</span></span>  
  
|<span data-ttu-id="b9999-106">Konu</span><span class="sxs-lookup"><span data-stu-id="b9999-106">Topic</span></span>|<span data-ttu-id="b9999-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b9999-107">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="b9999-108">XML alt Axis özelliği</span><span class="sxs-lookup"><span data-stu-id="b9999-108">XML Child Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)|<span data-ttu-id="b9999-109">Aşağıdaki alt erişim sağlar: bir <xref:System.Xml.Linq.XElement> nesne, bir <xref:System.Xml.Linq.XDocument> nesnesi, bir koleksiyonu <xref:System.Xml.Linq.XElement> nesneleri veya koleksiyonu <xref:System.Xml.Linq.XDocument> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="b9999-109">Provides access to the children of one of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="b9999-110">Bu eksen eşdeğerdir <xref:System.Xml.Linq.XContainer.Elements%2A> ekseni.</span><span class="sxs-lookup"><span data-stu-id="b9999-110">This axis is equivalent to the <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span>|  
|[<span data-ttu-id="b9999-111">XML Descendant Axis özelliği</span><span class="sxs-lookup"><span data-stu-id="b9999-111">XML Descendant Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)|<span data-ttu-id="b9999-112">Aşağıdaki alt öğelere erişim sağlar: bir <xref:System.Xml.Linq.XElement> nesne, bir <xref:System.Xml.Linq.XDocument> nesne ya da bir koleksiyonu <xref:System.Xml.Linq.XElement> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="b9999-112">Provides access to the descendants of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, or a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="b9999-113">Bu eksen eşdeğerdir <xref:System.Xml.Linq.XContainer.Descendants%2A> ekseni.</span><span class="sxs-lookup"><span data-stu-id="b9999-113">This axis is equivalent to the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>|  
|[<span data-ttu-id="b9999-114">XML özniteliği Axis özelliği</span><span class="sxs-lookup"><span data-stu-id="b9999-114">XML Attribute Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)|<span data-ttu-id="b9999-115">Bir özniteliğin erişim sağlayan bir <xref:System.Xml.Linq.XElement> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="b9999-115">Provides access to an attribute of an <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="b9999-116">Bu eksen kabaca eşdeğerdir <xref:System.Xml.Linq.XElement.Attribute%2A> ekseni.</span><span class="sxs-lookup"><span data-stu-id="b9999-116">This axis is roughly equivalent to the <xref:System.Xml.Linq.XElement.Attribute%2A> axis.</span></span> <span data-ttu-id="b9999-117">Bu eksen farklıdır <xref:System.Xml.Linq.XElement.Attribute%2A> , eksen döndürdüğü özniteliğinin değeri olmayan bir <xref:System.Xml.Linq.XAttribute> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="b9999-117">This axis differs from the <xref:System.Xml.Linq.XElement.Attribute%2A> axis in that it returns the value of the attribute, not an <xref:System.Xml.Linq.XAttribute> object.</span></span>|  
|[<span data-ttu-id="b9999-118">Extension Indexer özelliği</span><span class="sxs-lookup"><span data-stu-id="b9999-118">Extension Indexer Property</span></span>](../../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)|<span data-ttu-id="b9999-119">Bir koleksiyondaki tek tek öğelere erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="b9999-119">Provides access to individual elements in a collection.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b9999-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b9999-120">See Also</span></span>  
 [<span data-ttu-id="b9999-121">LINQ-XML eksenleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9999-121">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
