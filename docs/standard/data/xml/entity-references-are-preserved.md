---
title: Varlık Başvuruları Korunur
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 000a6cae-5972-40d6-bd6c-a9b7d9649b3c
ms.openlocfilehash: 0fd427388a065bd4c689d087c22fd6d69046b8a9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710927"
---
# <a name="entity-references-are-preserved"></a><span data-ttu-id="f2687-102">Varlık Başvuruları Korunur</span><span class="sxs-lookup"><span data-stu-id="f2687-102">Entity References are Preserved</span></span>
<span data-ttu-id="f2687-103">Varlık başvurusu genişletilmemişse ancak korunmadığında, XML Belge Nesne Modeli (DOM) bir varlık başvurusuyla karşılaştığında bir **XmlEntityReference** düğümü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f2687-103">When the entity reference is not expanded, but preserved, the XML Document Object Model (DOM) builds an **XmlEntityReference** node when it encounters an entity reference.</span></span>  
  
 <span data-ttu-id="f2687-104">Aşağıdaki XML 'i kullanarak</span><span class="sxs-lookup"><span data-stu-id="f2687-104">Using the following XML,</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="f2687-105">DOM, `&publisher;` başvuruyla karşılaştığında bir **XmlEntityReference** düğümü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f2687-105">the DOM builds an **XmlEntityReference** node when it encounters the `&publisher;` reference.</span></span> <span data-ttu-id="f2687-106">**XmlEntityReference** , varlık bildiriminde içerikten kopyalanmış alt düğümleri içerir.</span><span class="sxs-lookup"><span data-stu-id="f2687-106">The **XmlEntityReference** contains child nodes copied from the content in the entity declaration.</span></span> <span data-ttu-id="f2687-107">Önceki kod örneği varlık bildiriminde metin içerir, bu nedenle bir **XmlText** düğümü varlık başvurusu düğümünün alt düğümü olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f2687-107">The preceding code example contains text in the entity declaration, so an **XmlText** node is created as the child node of the entity reference node.</span></span>  
  
 <span data-ttu-id="f2687-108">![Korunan varlık başvuruları için ağaç yapısı](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span><span class="sxs-lookup"><span data-stu-id="f2687-108">![Tree structure for preserved entity references](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span></span>  
<span data-ttu-id="f2687-109">Korunan varlık başvuruları için ağaç yapısı</span><span class="sxs-lookup"><span data-stu-id="f2687-109">Tree structure for entity references that are preserved</span></span>  
  
 <span data-ttu-id="f2687-110">**XmlEntityReference** alt düğümleri, varlık bildirimi Ile karşılaşıldığında **XmlEntity** düğümünden oluşturulan tüm alt düğümlerin kopyalardır.</span><span class="sxs-lookup"><span data-stu-id="f2687-110">The child nodes of the **XmlEntityReference** are copies of all the child nodes created from the **XmlEntity** node when the entity declaration was encountered.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f2687-111">**XmlEntity** 'den kopyalanmış düğümler, varlık başvurusu düğümü altına yerleştirildiğinde her zaman tam kopya değildir.</span><span class="sxs-lookup"><span data-stu-id="f2687-111">The nodes copied from the **XmlEntity** are not always exact copies once placed under the entity reference node.</span></span> <span data-ttu-id="f2687-112">Varlık başvurusu düğümünde kapsamda olan ve alt düğümlerin son yapılandırmasını etkileyen ad alanları olabilir.</span><span class="sxs-lookup"><span data-stu-id="f2687-112">There can be namespaces that are in scope at the entity reference node, and that affects the final configuration of the child nodes.</span></span>  
  
 <span data-ttu-id="f2687-113">Varsayılan olarak, gibi `&abc;` genel varlıklar korunur ve **XmlEntityReference** düğümleri her zaman oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f2687-113">By default, general entities like `&abc;` are preserved and **XmlEntityReference** nodes always created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2687-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2687-114">See also</span></span>

- [<span data-ttu-id="f2687-115">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="f2687-115">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
