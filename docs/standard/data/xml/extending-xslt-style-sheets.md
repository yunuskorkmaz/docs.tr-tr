---
title: "XSLT stil sayfaları genişletme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df4ba2bf-a99e-4d22-bbf3-04fc67669dbc
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: aea28532dd81745b8d018cbeed454bbd008c8ed7
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="extending-xslt-style-sheets"></a><span data-ttu-id="7b917-102">XSLT stil sayfaları genişletme</span><span class="sxs-lookup"><span data-stu-id="7b917-102">Extending XSLT Style Sheets</span></span>
<span data-ttu-id="7b917-103">Bu bölümde XSLT işlevselliği genişletmek için farklı yöntemler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7b917-103">This section describes the different methods of extending the XSLT functionality.</span></span> <span data-ttu-id="7b917-104">Uzantı nesneleri veya kullanarak parametreler ekleyebilirsiniz <xref:System.Xml.Xsl.XsltArgumentList> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7b917-104">You can add extension objects or parameters using the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span> <span data-ttu-id="7b917-105">Uzantı nesneleri veya parametreleri stil sayfası içinden çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="7b917-105">The extension objects or parameters can then be called from the style sheet.</span></span> <span data-ttu-id="7b917-106">Ayrıca, aynı zamanda komut dosyası blokları stil sayfasına kullanarak eklenebilir `msxsl:script` öğesi.</span><span class="sxs-lookup"><span data-stu-id="7b917-106">In addition, you can also embed script blocks into the style sheet by using the `msxsl:script` element.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7b917-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="7b917-107">In This Section</span></span>  
 [<span data-ttu-id="7b917-108">XSLT Genişletme Nesneleri</span><span class="sxs-lookup"><span data-stu-id="7b917-108">XSLT Extension Objects</span></span>](../../../../docs/standard/data/xml/xslt-extension-objects.md)  
 <span data-ttu-id="7b917-109">Kullanarak anlatılmaktadır <xref:System.Xml.Xsl.XsltArgumentList> işlem XSLT uzantısı nesnelere sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7b917-109">Discusses using the <xref:System.Xml.Xsl.XsltArgumentList> class to process XSLT extension objects.</span></span>  
  
 [<span data-ttu-id="7b917-110">XSLT Parametreleri</span><span class="sxs-lookup"><span data-stu-id="7b917-110">XSLT Parameters</span></span>](../../../../docs/standard/data/xml/xslt-parameters.md)  
 <span data-ttu-id="7b917-111">Kullanarak anlatılmaktadır <xref:System.Xml.Xsl.XsltArgumentList> işlem XSLT parametreleri sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7b917-111">Discusses using the <xref:System.Xml.Xsl.XsltArgumentList> class to process XSLT parameters.</span></span>  
  
 [<span data-ttu-id="7b917-112">msxsl:script Kullanan Betik Blokları</span><span class="sxs-lookup"><span data-stu-id="7b917-112">Script Blocks Using msxsl:script</span></span>](../../../../docs/standard/data/xml/script-blocks-using-msxsl-script.md)  
 <span data-ttu-id="7b917-113">Kullanarak anlatılmaktadır `msxsl:script` öğesi.</span><span class="sxs-lookup"><span data-stu-id="7b917-113">Discusses using the `msxsl:script` element.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7b917-114">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="7b917-114">Related Sections</span></span>  
 [<span data-ttu-id="7b917-115">XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="7b917-115">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
