---
title: Varlık Başvuruları Korunur
ms.date: 03/30/2017
ms.assetid: 000a6cae-5972-40d6-bd6c-a9b7d9649b3c
ms.openlocfilehash: 484eb5c874c6de05acae7dcd87a477c186b81482
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687274"
---
# <a name="entity-references-are-preserved"></a><span data-ttu-id="d4cc1-102">Varlık Başvuruları Korunur</span><span class="sxs-lookup"><span data-stu-id="d4cc1-102">Entity References are Preserved</span></span>

<span data-ttu-id="d4cc1-103">Varlık başvurusu genişletilmemişse ancak korunmadığında, XML Belge Nesne Modeli (DOM) bir varlık başvurusuyla karşılaştığında bir **XmlEntityReference** düğümü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d4cc1-103">When the entity reference is not expanded, but preserved, the XML Document Object Model (DOM) builds an **XmlEntityReference** node when it encounters an entity reference.</span></span>  
  
 <span data-ttu-id="d4cc1-104">Aşağıdaki XML 'i kullanarak</span><span class="sxs-lookup"><span data-stu-id="d4cc1-104">Using the following XML,</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="d4cc1-105">DOM, başvuruyla karşılaştığında bir **XmlEntityReference** düğümü oluşturur `&publisher;` .</span><span class="sxs-lookup"><span data-stu-id="d4cc1-105">the DOM builds an **XmlEntityReference** node when it encounters the `&publisher;` reference.</span></span> <span data-ttu-id="d4cc1-106">**XmlEntityReference** , varlık bildiriminde içerikten kopyalanmış alt düğümleri içerir.</span><span class="sxs-lookup"><span data-stu-id="d4cc1-106">The **XmlEntityReference** contains child nodes copied from the content in the entity declaration.</span></span> <span data-ttu-id="d4cc1-107">Önceki kod örneği varlık bildiriminde metin içerir, bu nedenle bir **XmlText** düğümü varlık başvurusu düğümünün alt düğümü olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d4cc1-107">The preceding code example contains text in the entity declaration, so an **XmlText** node is created as the child node of the entity reference node.</span></span>  
  
 <span data-ttu-id="d4cc1-108">![Korunan varlık başvuruları için ağaç yapısı](media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span><span class="sxs-lookup"><span data-stu-id="d4cc1-108">![Tree structure for preserved entity references](media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span></span>  
<span data-ttu-id="d4cc1-109">Korunan varlık başvuruları için ağaç yapısı</span><span class="sxs-lookup"><span data-stu-id="d4cc1-109">Tree structure for entity references that are preserved</span></span>  
  
 <span data-ttu-id="d4cc1-110">**XmlEntityReference** alt düğümleri, varlık bildirimi Ile karşılaşıldığında **XmlEntity** düğümünden oluşturulan tüm alt düğümlerin kopyalardır.</span><span class="sxs-lookup"><span data-stu-id="d4cc1-110">The child nodes of the **XmlEntityReference** are copies of all the child nodes created from the **XmlEntity** node when the entity declaration was encountered.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d4cc1-111">**XmlEntity** 'den kopyalanmış düğümler, varlık başvurusu düğümü altına yerleştirildiğinde her zaman tam kopya değildir.</span><span class="sxs-lookup"><span data-stu-id="d4cc1-111">The nodes copied from the **XmlEntity** are not always exact copies once placed under the entity reference node.</span></span> <span data-ttu-id="d4cc1-112">Varlık başvurusu düğümünde kapsamda olan ve alt düğümlerin son yapılandırmasını etkileyen ad alanları olabilir.</span><span class="sxs-lookup"><span data-stu-id="d4cc1-112">There can be namespaces that are in scope at the entity reference node, and that affects the final configuration of the child nodes.</span></span>  
  
 <span data-ttu-id="d4cc1-113">Varsayılan olarak, gibi genel varlıklar `&abc;` korunur ve **XmlEntityReference** düğümleri her zaman oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d4cc1-113">By default, general entities like `&abc;` are preserved and **XmlEntityReference** nodes always created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4cc1-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4cc1-114">See also</span></span>

- [<span data-ttu-id="d4cc1-115">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="d4cc1-115">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
