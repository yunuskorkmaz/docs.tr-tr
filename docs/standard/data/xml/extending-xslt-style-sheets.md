---
title: XSLT Stil Sayfalarını Genişletme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: df4ba2bf-a99e-4d22-bbf3-04fc67669dbc
ms.openlocfilehash: 04f9788fe34ba74d0cf12fdd37adf46e85777192
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710875"
---
# <a name="extending-xslt-style-sheets"></a><span data-ttu-id="d0495-102">XSLT Stil Sayfalarını Genişletme</span><span class="sxs-lookup"><span data-stu-id="d0495-102">Extending XSLT Style Sheets</span></span>
<span data-ttu-id="d0495-103">Bu bölümde XSLT işlevlerini genişletmek için farklı yöntemler açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="d0495-103">This section describes the different methods of extending the XSLT functionality.</span></span> <span data-ttu-id="d0495-104"><xref:System.Xml.Xsl.XsltArgumentList> sınıfını kullanarak uzantı nesneleri veya parametreler ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0495-104">You can add extension objects or parameters using the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span> <span data-ttu-id="d0495-105">Uzantı nesneleri veya parametreler daha sonra stil sayfasından çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="d0495-105">The extension objects or parameters can then be called from the style sheet.</span></span> <span data-ttu-id="d0495-106">Ayrıca, `msxsl:script` öğesini kullanarak de komut dosyası bloklarını stil sayfasına ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0495-106">In addition, you can also embed script blocks into the style sheet by using the `msxsl:script` element.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d0495-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="d0495-107">In This Section</span></span>  
 [<span data-ttu-id="d0495-108">XSLT Genişletme Nesneleri</span><span class="sxs-lookup"><span data-stu-id="d0495-108">XSLT Extension Objects</span></span>](../../../../docs/standard/data/xml/xslt-extension-objects.md)  
 <span data-ttu-id="d0495-109">XSLT uzantı nesnelerini işlemek için <xref:System.Xml.Xsl.XsltArgumentList> sınıfını kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="d0495-109">Discusses using the <xref:System.Xml.Xsl.XsltArgumentList> class to process XSLT extension objects.</span></span>  
  
 [<span data-ttu-id="d0495-110">XSLT Parametreleri</span><span class="sxs-lookup"><span data-stu-id="d0495-110">XSLT Parameters</span></span>](../../../../docs/standard/data/xml/xslt-parameters.md)  
 <span data-ttu-id="d0495-111">XSLT parametrelerini işlemek için <xref:System.Xml.Xsl.XsltArgumentList> sınıfını kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="d0495-111">Discusses using the <xref:System.Xml.Xsl.XsltArgumentList> class to process XSLT parameters.</span></span>  
  
 [<span data-ttu-id="d0495-112">msxsl:script Kullanan Betik Blokları</span><span class="sxs-lookup"><span data-stu-id="d0495-112">Script Blocks Using msxsl:script</span></span>](../../../../docs/standard/data/xml/script-blocks-using-msxsl-script.md)  
 <span data-ttu-id="d0495-113">`msxsl:script` öğesinin kullanımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="d0495-113">Discusses using the `msxsl:script` element.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d0495-114">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="d0495-114">Related Sections</span></span>  
 [<span data-ttu-id="d0495-115">XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="d0495-115">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
