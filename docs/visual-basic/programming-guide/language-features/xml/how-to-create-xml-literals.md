---
title: 'Nasıl yapılır: XML Değişmez Değerleri Oluşturma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], creating
ms.assetid: 573a6db5-b14d-4e42-b356-8cc7e2d77745
ms.openlocfilehash: e5f8429b3ff02678bf8bf3e9e32bef6eb1a56831
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43483625"
---
# <a name="how-to-create-xml-literals-visual-basic"></a><span data-ttu-id="ce5a8-102">Nasıl yapılır: XML Değişmez Değerleri Oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce5a8-102">How to: Create XML Literals (Visual Basic)</span></span>
<span data-ttu-id="ce5a8-103">XML değişmez değeri kullanarak doğrudan kod içinde bir XML belgesi, parça veya öğesi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ce5a8-103">You can create an XML document, fragment, or element directly in code by using an XML literal.</span></span> <span data-ttu-id="ce5a8-104">Bu konudaki örnekler, üç alt öğeleri olan bir XML öğesi oluşturma ve bir XML belgesi oluşturma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ce5a8-104">The examples in this topic demonstrate how to create an XML element that has three child elements, and how to create an XML document.</span></span>  
  
 <span data-ttu-id="ce5a8-105">Ayrıca [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] oluşturmak için API'ler [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nesneleri.</span><span class="sxs-lookup"><span data-stu-id="ce5a8-105">You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects.</span></span> <span data-ttu-id="ce5a8-106">Daha fazla bilgi için bkz. <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="ce5a8-106">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
### <a name="to-create-an-xml-element"></a><span data-ttu-id="ce5a8-107">Bir XML öğesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="ce5a8-107">To create an XML element</span></span>  
  
-   <span data-ttu-id="ce5a8-108">XML satır içi gerçek XML sözdizimi aynıdır XML değişmez değer sözdizimini kullanarak oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ce5a8-108">Create the XML inline by using the XML literal syntax, which is the same as the actual XML syntax.</span></span>  
  
     [!code-vb[VbXMLSamples#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-xml-literals_1.vb)]  
  
     <span data-ttu-id="ce5a8-109">Kodu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ce5a8-109">Run the code.</span></span> <span data-ttu-id="ce5a8-110">Bu kodun çıktısı şöyledir:</span><span class="sxs-lookup"><span data-stu-id="ce5a8-110">The output of this code is:</span></span>  
  
     `<contact>`  
  
     `<name>Patrick Hines</name>`  
  
     `<phone type="home">206-555-0144</phone>`  
  
     `<phone type="work">425-555-0145</phone>`  
  
     `</contact>`  
  
### <a name="to-create-an-xml-document"></a><span data-ttu-id="ce5a8-111">Bir XML belgesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="ce5a8-111">To create an XML document</span></span>  
  
-   <span data-ttu-id="ce5a8-112">XML belge satır içi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ce5a8-112">Create the XML document inline.</span></span> <span data-ttu-id="ce5a8-113">Aşağıdaki kod, değişmez değer söz dizimi, bir XML bildirimi, bir işlem yönergesi, bir açıklama ve başka bir öğe içeren bir öğeyi içeren bir XML belgesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ce5a8-113">The following code creates an XML document that has literal syntax, an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
     [!code-vb[VbXMLSamples#30](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-xml-literals_2.vb)]  
  
     <span data-ttu-id="ce5a8-114">Kodu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ce5a8-114">Run the code.</span></span> <span data-ttu-id="ce5a8-115">Bu kodun çıktısı şöyledir:</span><span class="sxs-lookup"><span data-stu-id="ce5a8-115">The output of this code is:</span></span>  
  
     `<?xml-stylesheet type="text/xsl" href="show_book.xsl"?>`  
  
     `<!-- Tests that the application works. -->`  
  
     `<books>`  
  
     `<book/>`  
  
     `</books>`  
  
## <a name="see-also"></a><span data-ttu-id="ce5a8-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ce5a8-116">See Also</span></span>  
 [<span data-ttu-id="ce5a8-117">XML</span><span class="sxs-lookup"><span data-stu-id="ce5a8-117">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [<span data-ttu-id="ce5a8-118">Visual Basic'de XML oluşturma</span><span class="sxs-lookup"><span data-stu-id="ce5a8-118">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="ce5a8-119">XML Öğesi Değişmez Değeri</span><span class="sxs-lookup"><span data-stu-id="ce5a8-119">XML Element Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [<span data-ttu-id="ce5a8-120">XML Belgesi Değişmez Değeri</span><span class="sxs-lookup"><span data-stu-id="ce5a8-120">XML Document Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
