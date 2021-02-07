---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: düğüm parçasını dönüştürme'
title: 'Nasıl yapılır: Düğüm Parçasını Dönüştürme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73a6c582-b9d7-4fa7-9a05-6d931e1f3de8
ms.openlocfilehash: 9373491837fdfb176547aa7e01b8ebf72ae91bef
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99713773"
---
# <a name="how-to-transform-a-node-fragment"></a><span data-ttu-id="e6ea2-103">Nasıl yapılır: Düğüm Parçasını Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="e6ea2-103">How to: Transform a Node Fragment</span></span>

<span data-ttu-id="e6ea2-104">Bir veya nesnesinde bulunan verileri dönüştürdüğünüzde <xref:System.Xml.XmlDocument> <xref:System.Xml.XPath.XPathDocument> XSLT dönüştürmeleri bir belge için bir bütün olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="e6ea2-104">When you transform data contained in an <xref:System.Xml.XmlDocument> or <xref:System.Xml.XPath.XPathDocument> object the XSLT transformations apply to a document as a whole.</span></span> <span data-ttu-id="e6ea2-105">Diğer bir deyişle, belge kök düğümü dışında bir düğüm geçirirseniz, bu, dönüşüm işleminin yüklenen belgedeki tüm düğümlere erişmesini engellemez.</span><span class="sxs-lookup"><span data-stu-id="e6ea2-105">In other words, if you pass in a node other than the document root node, this does not prevent the transformation process from accessing all nodes in the loaded document.</span></span> <span data-ttu-id="e6ea2-106">Bir düğüm parçasını dönüştürmek için yalnızca düğüm parçasını içeren ayrı bir nesne oluşturmanız ve bu nesneyi yöntemine iletmeniz gerekir <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> .</span><span class="sxs-lookup"><span data-stu-id="e6ea2-106">To transform a node fragment, you must create a separate object containing just the node fragment, and pass that object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="e6ea2-107">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="e6ea2-107">Procedures</span></span>  
  
#### <a name="to-transform-a-node-fragment"></a><span data-ttu-id="e6ea2-108">Düğüm parçasını dönüştürmek için</span><span class="sxs-lookup"><span data-stu-id="e6ea2-108">To transform a node fragment</span></span>  
  
1. <span data-ttu-id="e6ea2-109">Kaynak belgeyi içeren bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e6ea2-109">Create an object containing the source document.</span></span>  
  
2. <span data-ttu-id="e6ea2-110">Dönüştürmek istediğiniz düğüm parçasını bulun.</span><span class="sxs-lookup"><span data-stu-id="e6ea2-110">Locate the node fragment you wish to transform.</span></span>  
  
3. <span data-ttu-id="e6ea2-111">Yalnızca düğüm parçamı ile ayrı bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e6ea2-111">Create separate object with just the node fragment.</span></span>  
  
4. <span data-ttu-id="e6ea2-112">Düğüm parçasını <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metoduna geçirin.</span><span class="sxs-lookup"><span data-stu-id="e6ea2-112">Pass the node fragment to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6ea2-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="e6ea2-113">Example</span></span>  

 <span data-ttu-id="e6ea2-114">Aşağıdaki örnek bir düğüm parçasını dönüştürür ve sonuçları konsola verir.</span><span class="sxs-lookup"><span data-stu-id="e6ea2-114">The following example transforms a node fragment and outputs the results to the console.</span></span>  
  
 [!code-csharp[XSLT_NodeFrag#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_NodeFrag/CS/xslt_frag.cs#1)]
 [!code-vb[XSLT_NodeFrag#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_NodeFrag/VB/xslt_frag.vb#1)]  
  
### <a name="input"></a><span data-ttu-id="e6ea2-115">Giriş</span><span class="sxs-lookup"><span data-stu-id="e6ea2-115">Input</span></span>  
  
##### <a name="booksxml"></a><span data-ttu-id="e6ea2-116">books.xml</span><span class="sxs-lookup"><span data-stu-id="e6ea2-116">books.xml</span></span>  

 [!code-xml[XML_Core_Files#1](../../../../samples/snippets/xml/VS_Snippets_Data/XML_Core_Files/XML/books.xml#1)]  
  
##### <a name="singlexsl"></a><span data-ttu-id="e6ea2-117">tek. Xsl</span><span class="sxs-lookup"><span data-stu-id="e6ea2-117">single.xsl</span></span>  

 [!code-xml[XSLT_NodeFrag#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_NodeFrag/XML/single.xsl#2)]  
  
### <a name="output"></a><span data-ttu-id="e6ea2-118">Çıktı</span><span class="sxs-lookup"><span data-stu-id="e6ea2-118">Output</span></span>  

 <span data-ttu-id="e6ea2-119">Kitap başlığı, güvenirlik Man.</span><span class="sxs-lookup"><span data-stu-id="e6ea2-119">Book title is The Confidence Man.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6ea2-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6ea2-120">See also</span></span>

- [<span data-ttu-id="e6ea2-121">XslCompiledTransform Sınıfını Kullanma</span><span class="sxs-lookup"><span data-stu-id="e6ea2-121">Using the XslCompiledTransform Class</span></span>](using-the-xslcompiledtransform-class.md)
