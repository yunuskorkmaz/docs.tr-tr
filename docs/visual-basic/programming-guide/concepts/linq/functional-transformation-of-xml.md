---
title: "İşlev dönüştürme XML (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fdbe5b91-f457-4b4e-a11b-def4bdd77bab
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 69cd09a017ab7fbf9fc56a6724abb4cc15b3e1cf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="functional-transformation-of-xml-visual-basic"></a><span data-ttu-id="8a375-102">İşlev dönüştürme XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a375-102">Functional Transformation of XML (Visual Basic)</span></span>
<span data-ttu-id="8a375-103">Bu konu, XML belgelerini değiştirme saf işlev dönüştürme yaklaşım açıklar ve yordam bir yaklaşım ile karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="8a375-103">This topic discusses the pure functional transformation approach to modifying XML documents, and contrasts it with a procedural approach.</span></span>  
  
## <a name="modifying-an-xml-document"></a><span data-ttu-id="8a375-104">Bir XML belgesi değiştirme</span><span class="sxs-lookup"><span data-stu-id="8a375-104">Modifying an XML Document</span></span>  
 <span data-ttu-id="8a375-105">Bir XML programcı için en yaygın görevlerden birini XML bir şekli'ndan diğerine dönüştürme.</span><span class="sxs-lookup"><span data-stu-id="8a375-105">One of the most common tasks for an XML programmer is transforming XML from one shape to another.</span></span> <span data-ttu-id="8a375-106">Bir XML belgesi şekli aşağıdakileri içeren belge yapıdır:</span><span class="sxs-lookup"><span data-stu-id="8a375-106">The shape of an XML document is the structure of the document, which includes the following:</span></span>  
  
-   <span data-ttu-id="8a375-107">Belgenin ifade hiyerarşisi.</span><span class="sxs-lookup"><span data-stu-id="8a375-107">The hierarchy expressed by the document.</span></span>  
  
-   <span data-ttu-id="8a375-108">Öğe ve öznitelik adları.</span><span class="sxs-lookup"><span data-stu-id="8a375-108">The element and attribute names.</span></span>  
  
-   <span data-ttu-id="8a375-109">Öğeleri ve özniteliklerinin veri türleri.</span><span class="sxs-lookup"><span data-stu-id="8a375-109">The data types of the elements and attributes.</span></span>  
  
 <span data-ttu-id="8a375-110">Genel olarak, XML bir şekle dönüştürme en etkili, saf işlevsel dönüşümünün yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="8a375-110">In general, the most effective approach to transforming XML from one shape to another is that of pure functional transformation.</span></span> <span data-ttu-id="8a375-111">Bu yaklaşımda, birincil Programcı görev tüm XML belge (veya bir veya daha fazla kesinlikle tanımlı düğümleri) uygulanan bir dönüşüm oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="8a375-111">In this approach, the primary programmer task is to create a transformation which is applied to the entire XML document (or to one or more strictly defined nodes).</span></span> <span data-ttu-id="8a375-112">İşlev dönüşümü gerçekleşir tartışmaya açık bir şekilde kod (programcı yaklaşımı hakkında bilgi sahibi olduktan sonra), en kolay en Bakımı yapılabilir kodu üretir ve genellikle daha alternatif yaklaşımlar compact olduğu.</span><span class="sxs-lookup"><span data-stu-id="8a375-112">Functional transformation is arguably the easiest to code (after a programmer is familiar with the approach), yields the most maintainable code, and is often more compact than alternative approaches.</span></span>  
  
### <a name="xml-functional-transformational-technologies"></a><span data-ttu-id="8a375-113">XML işlevsel Transformational teknolojileri</span><span class="sxs-lookup"><span data-stu-id="8a375-113">XML Functional Transformational Technologies</span></span>  
 <span data-ttu-id="8a375-114">Microsoft XML belgeleri kullanımı için iki işlev dönüştürme teknolojileri sunar: XSLT ve LINQ-XML.</span><span class="sxs-lookup"><span data-stu-id="8a375-114">Microsoft offers two functional transformation technologies for use on XML documents: XSLT and LINQ to XML.</span></span> <span data-ttu-id="8a375-115">XSLT desteklenir <xref:System.Xml.Xsl> yönetilen ad alanı ve yerel MSXML COM uygulama.</span><span class="sxs-lookup"><span data-stu-id="8a375-115">XSLT is supported in the <xref:System.Xml.Xsl> managed namespace and in the native COM implementation of MSXML.</span></span> <span data-ttu-id="8a375-116">XSLT XML belgelerini düzenleme için sağlam bir teknoloji olsa da, bir özel etki alanı, XSLT dili ve destekleyici API'lerini uzmanlık gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8a375-116">Although XSLT is a robust technology for manipulating XML documents, it requires expertise in a specialized domain, namely the XSLT language and its supporting APIs.</span></span>  
  
 <span data-ttu-id="8a375-117">LINQ-XML, C# veya Visual Basic kodundaki bir açıklayıcı ve güçlü şekilde kodu saf işlevsel dönüştürmeleri için gerekli araçları sağlar.</span><span class="sxs-lookup"><span data-stu-id="8a375-117">LINQ to XML provides the tools necessary to code pure functional transformations in an expressive and powerful way, within C# or Visual Basic code.</span></span> <span data-ttu-id="8a375-118">Örneğin, birçok LINQ örnek XML belgeleri için saf bir işlev yaklaşımı kullanın.</span><span class="sxs-lookup"><span data-stu-id="8a375-118">For example, many of the examples in the LINQ to XML documentation use a pure functional approach.</span></span> <span data-ttu-id="8a375-119">Ayrıca, [Öğreticisi: düzenleme içerik WordprocessingML belgedeki (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) öğretici, kullanırız LINQ-XML işlevsel bir yaklaşım Microsoft Word belgesinde bilgileri işlemek için.</span><span class="sxs-lookup"><span data-stu-id="8a375-119">Also, in the [Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial, we use LINQ to XML in a functional approach to manipulate information in a Microsoft Word document.</span></span>  
  
 <span data-ttu-id="8a375-120">Daha eksiksiz karşılaştırması LINQ-XML için diğer Microsoft XML teknolojileriyle, bkz: [LINQ-XML vs. Diğer XML teknolojileri](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md).</span><span class="sxs-lookup"><span data-stu-id="8a375-120">For a more complete comparison of LINQ to XML with other Microsoft XML technologies, see [LINQ to XML vs. Other XML Technologies](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md).</span></span>  
  
 <span data-ttu-id="8a375-121">Kaynak belge bir düzensiz yapısına sahip olduğunda XSLT belge merkezli dönüştürmeleri için önerilen araçtır.</span><span class="sxs-lookup"><span data-stu-id="8a375-121">XSLT is the recommended tool for  document-centric transformations when the source document has an irregular structure.</span></span> <span data-ttu-id="8a375-122">Ancak, LINQ-XML belge merkezli dönüşümler de gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8a375-122">However, LINQ to XML can also perform document-centric transforms.</span></span> <span data-ttu-id="8a375-123">Daha fazla bilgi için bkz: [nasıl yapılır: XML ağaçlarında XSLT stil (Visual Basic) dönüştürme LINQ'ten kullanım ek açıklamalar](../../../../visual-basic/programming-guide/concepts/linq/how-to-use-annotation-trees-to-transform-linq-to-xml-trees-in-an-xslt-style.md).</span><span class="sxs-lookup"><span data-stu-id="8a375-123">For more information, see [How to: Use Annotations to Transform LINQ to XML Trees in an XSLT Style (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-use-annotation-trees-to-transform-linq-to-xml-trees-in-an-xslt-style.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a375-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8a375-124">See Also</span></span>  
 [<span data-ttu-id="8a375-125">Giriş saf işlevsel Dönüşümleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a375-125">Introduction to Pure Functional Transformations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)  
 [<span data-ttu-id="8a375-126">LINQ-XML vs. Diğer XML teknolojileri</span><span class="sxs-lookup"><span data-stu-id="8a375-126">LINQ to XML vs. Other XML Technologies</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md)  
 [<span data-ttu-id="8a375-127">LINQ-XML vs. Diğer XML teknolojileri</span><span class="sxs-lookup"><span data-stu-id="8a375-127">LINQ to XML vs. Other XML Technologies</span></span>](http://msdn.microsoft.com/library/7ba1eecf-f09a-42de-bc80-22ca5b2e42d3)
