---
title: XSLT stil sayfaları genişletme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: df4ba2bf-a99e-4d22-bbf3-04fc67669dbc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ff952df59dc8291b12df2b238052d4c40c834e2a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568829"
---
# <a name="extending-xslt-style-sheets"></a><span data-ttu-id="f0809-102">XSLT stil sayfaları genişletme</span><span class="sxs-lookup"><span data-stu-id="f0809-102">Extending XSLT Style Sheets</span></span>
<span data-ttu-id="f0809-103">Bu bölümde XSLT işlevselliği genişletmek için farklı yöntemler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f0809-103">This section describes the different methods of extending the XSLT functionality.</span></span> <span data-ttu-id="f0809-104">Uzantı nesneleri veya kullanarak parametreler ekleyebilirsiniz <xref:System.Xml.Xsl.XsltArgumentList> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f0809-104">You can add extension objects or parameters using the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span> <span data-ttu-id="f0809-105">Uzantı nesneleri veya parametreleri stil sayfası içinden çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="f0809-105">The extension objects or parameters can then be called from the style sheet.</span></span> <span data-ttu-id="f0809-106">Ayrıca, aynı zamanda komut dosyası blokları stil sayfasına kullanarak eklenebilir `msxsl:script` öğesi.</span><span class="sxs-lookup"><span data-stu-id="f0809-106">In addition, you can also embed script blocks into the style sheet by using the `msxsl:script` element.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f0809-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="f0809-107">In This Section</span></span>  
 [<span data-ttu-id="f0809-108">XSLT Genişletme Nesneleri</span><span class="sxs-lookup"><span data-stu-id="f0809-108">XSLT Extension Objects</span></span>](../../../../docs/standard/data/xml/xslt-extension-objects.md)  
 <span data-ttu-id="f0809-109">Kullanarak anlatılmaktadır <xref:System.Xml.Xsl.XsltArgumentList> işlem XSLT uzantısı nesnelere sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f0809-109">Discusses using the <xref:System.Xml.Xsl.XsltArgumentList> class to process XSLT extension objects.</span></span>  
  
 [<span data-ttu-id="f0809-110">XSLT Parametreleri</span><span class="sxs-lookup"><span data-stu-id="f0809-110">XSLT Parameters</span></span>](../../../../docs/standard/data/xml/xslt-parameters.md)  
 <span data-ttu-id="f0809-111">Kullanarak anlatılmaktadır <xref:System.Xml.Xsl.XsltArgumentList> işlem XSLT parametreleri sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f0809-111">Discusses using the <xref:System.Xml.Xsl.XsltArgumentList> class to process XSLT parameters.</span></span>  
  
 [<span data-ttu-id="f0809-112">msxsl:script Kullanan Betik Blokları</span><span class="sxs-lookup"><span data-stu-id="f0809-112">Script Blocks Using msxsl:script</span></span>](../../../../docs/standard/data/xml/script-blocks-using-msxsl-script.md)  
 <span data-ttu-id="f0809-113">Kullanarak anlatılmaktadır `msxsl:script` öğesi.</span><span class="sxs-lookup"><span data-stu-id="f0809-113">Discusses using the `msxsl:script` element.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f0809-114">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="f0809-114">Related Sections</span></span>  
 [<span data-ttu-id="f0809-115">XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="f0809-115">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
