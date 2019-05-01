---
title: XSLT Stil Sayfalarını Genişletme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: df4ba2bf-a99e-4d22-bbf3-04fc67669dbc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ff952df59dc8291b12df2b238052d4c40c834e2a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61966497"
---
# <a name="extending-xslt-style-sheets"></a><span data-ttu-id="a31dc-102">XSLT Stil Sayfalarını Genişletme</span><span class="sxs-lookup"><span data-stu-id="a31dc-102">Extending XSLT Style Sheets</span></span>
<span data-ttu-id="a31dc-103">Bu bölümde, XSLT işlevselliği genişletmek için farklı yöntemler açıklanır.</span><span class="sxs-lookup"><span data-stu-id="a31dc-103">This section describes the different methods of extending the XSLT functionality.</span></span> <span data-ttu-id="a31dc-104">Genişletme nesneleri veya parametreleri kullanarak ekleyebileceğiniz <xref:System.Xml.Xsl.XsltArgumentList> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a31dc-104">You can add extension objects or parameters using the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span> <span data-ttu-id="a31dc-105">Parametreleri ve genişletme nesneleri stil sayfası içinden çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="a31dc-105">The extension objects or parameters can then be called from the style sheet.</span></span> <span data-ttu-id="a31dc-106">Ayrıca, ayrıca komut dosyası blokları stil sayfası kullanılarak gömebilirsiniz `msxsl:script` öğesi.</span><span class="sxs-lookup"><span data-stu-id="a31dc-106">In addition, you can also embed script blocks into the style sheet by using the `msxsl:script` element.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a31dc-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="a31dc-107">In This Section</span></span>  
 [<span data-ttu-id="a31dc-108">XSLT Genişletme Nesneleri</span><span class="sxs-lookup"><span data-stu-id="a31dc-108">XSLT Extension Objects</span></span>](../../../../docs/standard/data/xml/xslt-extension-objects.md)  
 <span data-ttu-id="a31dc-109">Kullanımını açıklar <xref:System.Xml.Xsl.XsltArgumentList> işlem XSLT genişletme nesneleri için sınıf.</span><span class="sxs-lookup"><span data-stu-id="a31dc-109">Discusses using the <xref:System.Xml.Xsl.XsltArgumentList> class to process XSLT extension objects.</span></span>  
  
 [<span data-ttu-id="a31dc-110">XSLT Parametreleri</span><span class="sxs-lookup"><span data-stu-id="a31dc-110">XSLT Parameters</span></span>](../../../../docs/standard/data/xml/xslt-parameters.md)  
 <span data-ttu-id="a31dc-111">Kullanımını açıklar <xref:System.Xml.Xsl.XsltArgumentList> işlem XSLT parametreleri sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a31dc-111">Discusses using the <xref:System.Xml.Xsl.XsltArgumentList> class to process XSLT parameters.</span></span>  
  
 [<span data-ttu-id="a31dc-112">msxsl:script Kullanan Betik Blokları</span><span class="sxs-lookup"><span data-stu-id="a31dc-112">Script Blocks Using msxsl:script</span></span>](../../../../docs/standard/data/xml/script-blocks-using-msxsl-script.md)  
 <span data-ttu-id="a31dc-113">Kullanımını açıklar `msxsl:script` öğesi.</span><span class="sxs-lookup"><span data-stu-id="a31dc-113">Discusses using the `msxsl:script` element.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a31dc-114">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="a31dc-114">Related Sections</span></span>  
 [<span data-ttu-id="a31dc-115">XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="a31dc-115">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
