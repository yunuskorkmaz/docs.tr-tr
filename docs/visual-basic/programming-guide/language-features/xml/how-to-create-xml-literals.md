---
title: "Nasıl yapılır: XML Değişmez Değerleri Oluşturma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: XML literals [Visual Basic], creating
ms.assetid: 573a6db5-b14d-4e42-b356-8cc7e2d77745
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ce1bf763529b436158c2d74811c4938182166f92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-xml-literals-visual-basic"></a><span data-ttu-id="c0ee6-102">Nasıl yapılır: XML Değişmez Değerleri Oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c0ee6-102">How to: Create XML Literals (Visual Basic)</span></span>
<span data-ttu-id="c0ee6-103">Değişmez değer XML kullanarak doğrudan kod içinde bir XML belgesi, parça veya öğesi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c0ee6-103">You can create an XML document, fragment, or element directly in code by using an XML literal.</span></span> <span data-ttu-id="c0ee6-104">Bu konudaki örnekler üç alt öğeleri olan bir XML öğesi oluşturma ve bir XML belgesi nasıl oluşturacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="c0ee6-104">The examples in this topic demonstrate how to create an XML element that has three child elements, and how to create an XML document.</span></span>  
  
 <span data-ttu-id="c0ee6-105">Aynı zamanda [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] oluşturmak için API'lerini [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nesneleri.</span><span class="sxs-lookup"><span data-stu-id="c0ee6-105">You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects.</span></span> <span data-ttu-id="c0ee6-106">Daha fazla bilgi için bkz. <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="c0ee6-106">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
### <a name="to-create-an-xml-element"></a><span data-ttu-id="c0ee6-107">Bir XML öğesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c0ee6-107">To create an XML element</span></span>  
  
-   <span data-ttu-id="c0ee6-108">XML satır içi gerçek XML sözdizimi aynı XML değişmez sözdizimini kullanarak oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c0ee6-108">Create the XML inline by using the XML literal syntax, which is the same as the actual XML syntax.</span></span>  
  
     [!code-vb[VbXMLSamples#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-xml-literals_1.vb)]  
  
     <span data-ttu-id="c0ee6-109">Kodu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c0ee6-109">Run the code.</span></span> <span data-ttu-id="c0ee6-110">Bu kod çıktısı şöyledir:</span><span class="sxs-lookup"><span data-stu-id="c0ee6-110">The output of this code is:</span></span>  
  
     `<contact>`  
  
     `<name>Patrick Hines</name>`  
  
     `<phone type="home">206-555-0144</phone>`  
  
     `<phone type="work">425-555-0145</phone>`  
  
     `</contact>`  
  
### <a name="to-create-an-xml-document"></a><span data-ttu-id="c0ee6-111">Bir XML belgesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c0ee6-111">To create an XML document</span></span>  
  
-   <span data-ttu-id="c0ee6-112">XML belge satır içi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c0ee6-112">Create the XML document inline.</span></span> <span data-ttu-id="c0ee6-113">Aşağıdaki kod değişmez değer sözdizimi, bir XML bildirimi, bir işleme yönergesi, açıklama ve başka bir öğe içeren bir öğeyi içeren bir XML belgesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c0ee6-113">The following code creates an XML document that has literal syntax, an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
     [!code-vb[VbXMLSamples#30](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-xml-literals_2.vb)]  
  
     <span data-ttu-id="c0ee6-114">Kodu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c0ee6-114">Run the code.</span></span> <span data-ttu-id="c0ee6-115">Bu kod çıktısı şöyledir:</span><span class="sxs-lookup"><span data-stu-id="c0ee6-115">The output of this code is:</span></span>  
  
     `<?xml-stylesheet type="text/xsl" href="show_book.xsl"?>`  
  
     `<!-- Tests that the application works. -->`  
  
     `<books>`  
  
     `<book/>`  
  
     `</books>`  
  
## <a name="see-also"></a><span data-ttu-id="c0ee6-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c0ee6-116">See Also</span></span>  
 [<span data-ttu-id="c0ee6-117">XML</span><span class="sxs-lookup"><span data-stu-id="c0ee6-117">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [<span data-ttu-id="c0ee6-118">Visual Basic'de XML oluşturma</span><span class="sxs-lookup"><span data-stu-id="c0ee6-118">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="c0ee6-119">XML öğesi değişmez değeri</span><span class="sxs-lookup"><span data-stu-id="c0ee6-119">XML Element Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [<span data-ttu-id="c0ee6-120">XML belgesi değişmez değeri</span><span class="sxs-lookup"><span data-stu-id="c0ee6-120">XML Document Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
