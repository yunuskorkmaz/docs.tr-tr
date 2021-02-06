---
description: 'Hakkında daha fazla bilgi edinin: varlık başvuruları korunur'
title: Varlık Başvuruları Korunur
ms.date: 03/30/2017
ms.assetid: 000a6cae-5972-40d6-bd6c-a9b7d9649b3c
ms.openlocfilehash: 189096d2dd87731a06fdb805ba5f041c041e26b9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99629636"
---
# <a name="entity-references-are-preserved"></a><span data-ttu-id="42d36-103">Varlık Başvuruları Korunur</span><span class="sxs-lookup"><span data-stu-id="42d36-103">Entity References are Preserved</span></span>

<span data-ttu-id="42d36-104">Varlık başvurusu genişletilmemişse ancak korunmadığında, XML Belge Nesne Modeli (DOM) bir varlık başvurusuyla karşılaştığında bir **XmlEntityReference** düğümü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="42d36-104">When the entity reference is not expanded, but preserved, the XML Document Object Model (DOM) builds an **XmlEntityReference** node when it encounters an entity reference.</span></span>  
  
 <span data-ttu-id="42d36-105">Aşağıdaki XML 'i kullanarak</span><span class="sxs-lookup"><span data-stu-id="42d36-105">Using the following XML,</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="42d36-106">DOM, başvuruyla karşılaştığında bir **XmlEntityReference** düğümü oluşturur `&publisher;` .</span><span class="sxs-lookup"><span data-stu-id="42d36-106">the DOM builds an **XmlEntityReference** node when it encounters the `&publisher;` reference.</span></span> <span data-ttu-id="42d36-107">**XmlEntityReference** , varlık bildiriminde içerikten kopyalanmış alt düğümleri içerir.</span><span class="sxs-lookup"><span data-stu-id="42d36-107">The **XmlEntityReference** contains child nodes copied from the content in the entity declaration.</span></span> <span data-ttu-id="42d36-108">Önceki kod örneği varlık bildiriminde metin içerir, bu nedenle bir **XmlText** düğümü varlık başvurusu düğümünün alt düğümü olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="42d36-108">The preceding code example contains text in the entity declaration, so an **XmlText** node is created as the child node of the entity reference node.</span></span>  
  
 <span data-ttu-id="42d36-109">![Korunan varlık başvuruları için ağaç yapısı](media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span><span class="sxs-lookup"><span data-stu-id="42d36-109">![Tree structure for preserved entity references](media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span></span>  
<span data-ttu-id="42d36-110">Korunan varlık başvuruları için ağaç yapısı</span><span class="sxs-lookup"><span data-stu-id="42d36-110">Tree structure for entity references that are preserved</span></span>  
  
 <span data-ttu-id="42d36-111">**XmlEntityReference** alt düğümleri, varlık bildirimi Ile karşılaşıldığında **XmlEntity** düğümünden oluşturulan tüm alt düğümlerin kopyalardır.</span><span class="sxs-lookup"><span data-stu-id="42d36-111">The child nodes of the **XmlEntityReference** are copies of all the child nodes created from the **XmlEntity** node when the entity declaration was encountered.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="42d36-112">**XmlEntity** 'den kopyalanmış düğümler, varlık başvurusu düğümü altına yerleştirildiğinde her zaman tam kopya değildir.</span><span class="sxs-lookup"><span data-stu-id="42d36-112">The nodes copied from the **XmlEntity** are not always exact copies once placed under the entity reference node.</span></span> <span data-ttu-id="42d36-113">Varlık başvurusu düğümünde kapsamda olan ve alt düğümlerin son yapılandırmasını etkileyen ad alanları olabilir.</span><span class="sxs-lookup"><span data-stu-id="42d36-113">There can be namespaces that are in scope at the entity reference node, and that affects the final configuration of the child nodes.</span></span>  
  
 <span data-ttu-id="42d36-114">Varsayılan olarak, gibi genel varlıklar `&abc;` korunur ve **XmlEntityReference** düğümleri her zaman oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="42d36-114">By default, general entities like `&abc;` are preserved and **XmlEntityReference** nodes always created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42d36-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="42d36-115">See also</span></span>

- [<span data-ttu-id="42d36-116">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="42d36-116">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
