---
title: "Nasıl yapılır: bir düğümü parça dönüştürme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 73a6c582-b9d7-4fa7-9a05-6d931e1f3de8
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: dc3683cfe27bfed0f89cba4e0df0b0515fc6f287
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-transform-a-node-fragment"></a><span data-ttu-id="f3d46-102">Nasıl yapılır: bir düğümü parça dönüştürme</span><span class="sxs-lookup"><span data-stu-id="f3d46-102">How to: Transform a Node Fragment</span></span>
<span data-ttu-id="f3d46-103">Dönüştürme zaman bulunan verileri bir <xref:System.Xml.XmlDocument> veya <xref:System.Xml.XPath.XPathDocument> XSLT dönüştürmeleri bir bütün olarak belgeye nesne.</span><span class="sxs-lookup"><span data-stu-id="f3d46-103">When you transform data contained in an <xref:System.Xml.XmlDocument> or <xref:System.Xml.XPath.XPathDocument> object the XSLT transformations apply to a document as a whole.</span></span> <span data-ttu-id="f3d46-104">Belge kök düğümü dışında bir düğümünde geçirirseniz, diğer bir deyişle, bu dönüştürme süreci yüklenen belgedeki tüm düğümleri erişmesini engellemez.</span><span class="sxs-lookup"><span data-stu-id="f3d46-104">In other words, if you pass in a node other than the document root node, this does not prevent the transformation process from accessing all nodes in the loaded document.</span></span> <span data-ttu-id="f3d46-105">Bir düğüm parça dönüştürmek için yalnızca düğüm parça içeren ayrı bir nesne oluşturmak ve gerekir, nesneyi geçirmek <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f3d46-105">To transform a node fragment, you must create a separate object containing just the node fragment, and pass that object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="f3d46-106">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="f3d46-106">Procedures</span></span>  
  
#### <a name="to-transform-a-node-fragment"></a><span data-ttu-id="f3d46-107">Bir düğüm parça dönüştürmek için</span><span class="sxs-lookup"><span data-stu-id="f3d46-107">To transform a node fragment</span></span>  
  
1.  <span data-ttu-id="f3d46-108">Kaynak belge içeren bir nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f3d46-108">Create an object containing the source document.</span></span>  
  
2.  <span data-ttu-id="f3d46-109">Dönüştürmek istediğiniz düğümü parça bulun.</span><span class="sxs-lookup"><span data-stu-id="f3d46-109">Locate the node fragment you wish to transform.</span></span>  
  
3.  <span data-ttu-id="f3d46-110">Ayrı bir nesne yalnızca düğüm parça ile oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f3d46-110">Create separate object with just the node fragment.</span></span>  
  
4.  <span data-ttu-id="f3d46-111">Düğüm parça geçirmek <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f3d46-111">Pass the node fragment to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3d46-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="f3d46-112">Example</span></span>  
 <span data-ttu-id="f3d46-113">Aşağıdaki örnek, bir düğüm parça dönüştürür ve sonuçlarını konsola çıkarır.</span><span class="sxs-lookup"><span data-stu-id="f3d46-113">The following example transforms a node fragment and outputs the results to the console.</span></span>  
  
 [!code-csharp[XSLT_NodeFrag#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_NodeFrag/CS/xslt_frag.cs#1)]
 [!code-vb[XSLT_NodeFrag#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_NodeFrag/VB/xslt_frag.vb#1)]  
  
### <a name="input"></a><span data-ttu-id="f3d46-114">Giriş</span><span class="sxs-lookup"><span data-stu-id="f3d46-114">Input</span></span>  
  
##### <a name="booksxml"></a><span data-ttu-id="f3d46-115">Books.XML</span><span class="sxs-lookup"><span data-stu-id="f3d46-115">books.xml</span></span>  
 [!code-xml[XML_Core_Files#1](../../../../samples/snippets/xml/VS_Snippets_Data/XML_Core_Files/XML/books.xml#1)]  
  
##### <a name="singlexsl"></a><span data-ttu-id="f3d46-116">Single.xsl</span><span class="sxs-lookup"><span data-stu-id="f3d46-116">single.xsl</span></span>  
 [!code-xml[XSLT_NodeFrag#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_NodeFrag/XML/single.xsl#2)]  
  
### <a name="output"></a><span data-ttu-id="f3d46-117">Çıkış</span><span class="sxs-lookup"><span data-stu-id="f3d46-117">Output</span></span>  
 <span data-ttu-id="f3d46-118">GÜVENİRLİK Man'ye kitap başlığı olduğu</span><span class="sxs-lookup"><span data-stu-id="f3d46-118">Book title is The Confidence Man.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3d46-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f3d46-119">See Also</span></span>  
 [<span data-ttu-id="f3d46-120">XslCompiledTransform sınıfını kullanma</span><span class="sxs-lookup"><span data-stu-id="f3d46-120">Using the XslCompiledTransform Class</span></span>](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
