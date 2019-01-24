---
title: 'Nasıl yapılır: XML değişmez değerleri (Visual Basic) oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], creating
ms.assetid: 573a6db5-b14d-4e42-b356-8cc7e2d77745
ms.openlocfilehash: 0e74dccac0b3528fe73d091670a3368328baeaab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54560600"
---
# <a name="how-to-create-xml-literals-visual-basic"></a><span data-ttu-id="c53e2-102">Nasıl yapılır: XML değişmez değerleri (Visual Basic) oluşturma</span><span class="sxs-lookup"><span data-stu-id="c53e2-102">How to: Create XML Literals (Visual Basic)</span></span>
<span data-ttu-id="c53e2-103">XML değişmez değeri kullanarak doğrudan kod içinde bir XML belgesi, parça veya öğesi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c53e2-103">You can create an XML document, fragment, or element directly in code by using an XML literal.</span></span> <span data-ttu-id="c53e2-104">Bu konudaki örnekler, üç alt öğeleri olan bir XML öğesi oluşturma ve bir XML belgesi oluşturma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c53e2-104">The examples in this topic demonstrate how to create an XML element that has three child elements, and how to create an XML document.</span></span>  
  
 <span data-ttu-id="c53e2-105">Ayrıca [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] oluşturmak için API'ler [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nesneleri.</span><span class="sxs-lookup"><span data-stu-id="c53e2-105">You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects.</span></span> <span data-ttu-id="c53e2-106">Daha fazla bilgi için bkz. <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="c53e2-106">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
### <a name="to-create-an-xml-element"></a><span data-ttu-id="c53e2-107">Bir XML öğesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c53e2-107">To create an XML element</span></span>  
  
-   <span data-ttu-id="c53e2-108">XML satır içi gerçek XML sözdizimi aynıdır XML değişmez değer sözdizimini kullanarak oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c53e2-108">Create the XML inline by using the XML literal syntax, which is the same as the actual XML syntax.</span></span>  
  
     [!code-vb[VbXMLSamples#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-xml-literals_1.vb)]  
  
     <span data-ttu-id="c53e2-109">Kodu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c53e2-109">Run the code.</span></span> <span data-ttu-id="c53e2-110">Bu kodun çıktısı şöyledir:</span><span class="sxs-lookup"><span data-stu-id="c53e2-110">The output of this code is:</span></span>  
  
     `<contact>`  
  
     `<name>Patrick Hines</name>`  
  
     `<phone type="home">206-555-0144</phone>`  
  
     `<phone type="work">425-555-0145</phone>`  
  
     `</contact>`  
  
### <a name="to-create-an-xml-document"></a><span data-ttu-id="c53e2-111">Bir XML belgesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c53e2-111">To create an XML document</span></span>  
  
-   <span data-ttu-id="c53e2-112">XML belge satır içi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c53e2-112">Create the XML document inline.</span></span> <span data-ttu-id="c53e2-113">Aşağıdaki kod, değişmez değer söz dizimi, bir XML bildirimi, bir işlem yönergesi, bir açıklama ve başka bir öğe içeren bir öğeyi içeren bir XML belgesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c53e2-113">The following code creates an XML document that has literal syntax, an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
     [!code-vb[VbXMLSamples#30](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-xml-literals_2.vb)]  
  
     <span data-ttu-id="c53e2-114">Kodu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c53e2-114">Run the code.</span></span> <span data-ttu-id="c53e2-115">Bu kodun çıktısı şöyledir:</span><span class="sxs-lookup"><span data-stu-id="c53e2-115">The output of this code is:</span></span>  
  
     `<?xml-stylesheet type="text/xsl" href="show_book.xsl"?>`  
  
     `<!-- Tests that the application works. -->`  
  
     `<books>`  
  
     `<book/>`  
  
     `</books>`  
  
## <a name="see-also"></a><span data-ttu-id="c53e2-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c53e2-116">See also</span></span>
- [<span data-ttu-id="c53e2-117">XML</span><span class="sxs-lookup"><span data-stu-id="c53e2-117">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [<span data-ttu-id="c53e2-118">Visual Basic'de XML oluşturma</span><span class="sxs-lookup"><span data-stu-id="c53e2-118">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="c53e2-119">XML Öğesi Değişmez Değeri</span><span class="sxs-lookup"><span data-stu-id="c53e2-119">XML Element Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="c53e2-120">XML Belgesi Değişmez Değeri</span><span class="sxs-lookup"><span data-stu-id="c53e2-120">XML Document Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
