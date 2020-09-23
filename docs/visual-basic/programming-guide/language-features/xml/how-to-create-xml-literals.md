---
title: 'Nasıl yapılır: XML Değişmez Değerleri Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], creating
ms.assetid: 573a6db5-b14d-4e42-b356-8cc7e2d77745
ms.openlocfilehash: c7ad8d684dde31550b6e1b74c098d152b227f6c1
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058228"
---
# <a name="how-to-create-xml-literals-visual-basic"></a><span data-ttu-id="3abab-102">Nasıl yapılır: XML Değişmez Değerleri Oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3abab-102">How to: Create XML Literals (Visual Basic)</span></span>

<span data-ttu-id="3abab-103">Bir XML sabit değeri kullanarak doğrudan kodda bir XML belgesi, parça veya öğe oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3abab-103">You can create an XML document, fragment, or element directly in code by using an XML literal.</span></span> <span data-ttu-id="3abab-104">Bu konudaki örneklerde, üç alt öğesi olan bir XML öğesinin nasıl oluşturulacağı ve bir XML belgesinin nasıl oluşturulacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3abab-104">The examples in this topic demonstrate how to create an XML element that has three child elements, and how to create an XML document.</span></span>  
  
 <span data-ttu-id="3abab-105">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]API 'leri, nesneleri oluşturmak için de kullanabilirsiniz [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="3abab-105">You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects.</span></span> <span data-ttu-id="3abab-106">Daha fazla bilgi için bkz. <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="3abab-106">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
### <a name="to-create-an-xml-element"></a><span data-ttu-id="3abab-107">Bir XML öğesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="3abab-107">To create an XML element</span></span>  
  
- <span data-ttu-id="3abab-108">XML sabit değeri olan XML değişmez sözdizimini kullanarak XML satır içi oluşturun, bu da gerçek XML sözdizimi ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="3abab-108">Create the XML inline by using the XML literal syntax, which is the same as the actual XML syntax.</span></span>  
  
     [!code-vb[VbXMLSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
     <span data-ttu-id="3abab-109">Kodu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3abab-109">Run the code.</span></span> <span data-ttu-id="3abab-110">Bu kodun çıktısı:</span><span class="sxs-lookup"><span data-stu-id="3abab-110">The output of this code is:</span></span>  
  
     `<contact>`  
  
     `<name>Patrick Hines</name>`  
  
     `<phone type="home">206-555-0144</phone>`  
  
     `<phone type="work">425-555-0145</phone>`  
  
     `</contact>`  
  
### <a name="to-create-an-xml-document"></a><span data-ttu-id="3abab-111">Bir XML belgesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="3abab-111">To create an XML document</span></span>  
  
- <span data-ttu-id="3abab-112">XML belgesini satır içi olarak oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3abab-112">Create the XML document inline.</span></span> <span data-ttu-id="3abab-113">Aşağıdaki kod, değişmez sözdizimi, XML bildirimi, işleme yönergesi, açıklama ve başka bir öğesi içeren bir öğesi olan bir XML belgesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3abab-113">The following code creates an XML document that has literal syntax, an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
     [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
     <span data-ttu-id="3abab-114">Kodu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3abab-114">Run the code.</span></span> <span data-ttu-id="3abab-115">Bu kodun çıktısı:</span><span class="sxs-lookup"><span data-stu-id="3abab-115">The output of this code is:</span></span>  
  
     `<?xml-stylesheet type="text/xsl" href="show_book.xsl"?>`  
  
     `<!-- Tests that the application works. -->`  
  
     `<books>`  
  
     `<book/>`  
  
     `</books>`  
  
## <a name="see-also"></a><span data-ttu-id="3abab-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3abab-116">See also</span></span>

- [<span data-ttu-id="3abab-117">XML</span><span class="sxs-lookup"><span data-stu-id="3abab-117">XML</span></span>](index.md)
- [<span data-ttu-id="3abab-118">Visual Basic'de XML Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3abab-118">Creating XML in Visual Basic</span></span>](creating-xml.md)
- [<span data-ttu-id="3abab-119">XML Öğesi Değişmez Değeri</span><span class="sxs-lookup"><span data-stu-id="3abab-119">XML Element Literal</span></span>](../../../language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="3abab-120">XML Belgesi Değişmez Değeri</span><span class="sxs-lookup"><span data-stu-id="3abab-120">XML Document Literal</span></span>](../../../language-reference/xml-literals/xml-document-literal.md)
