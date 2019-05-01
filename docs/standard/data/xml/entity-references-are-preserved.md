---
title: Varlık Başvuruları Korunur
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 000a6cae-5972-40d6-bd6c-a9b7d9649b3c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b1c48e42e55025aff0ce1a24a3ef45ddf8005eab
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934543"
---
# <a name="entity-references-are-preserved"></a><span data-ttu-id="514d3-102">Varlık Başvuruları Korunur</span><span class="sxs-lookup"><span data-stu-id="514d3-102">Entity References are Preserved</span></span>
<span data-ttu-id="514d3-103">Varlık başvurusu genişletilmiş, ancak korunur, XML belge nesne modeli (DOM) derlemeleri bir **XmlEntityReference** bir varlık başvurusu karşılaştığında düğümü.</span><span class="sxs-lookup"><span data-stu-id="514d3-103">When the entity reference is not expanded, but preserved, the XML Document Object Model (DOM) builds an **XmlEntityReference** node when it encounters an entity reference.</span></span>  
  
 <span data-ttu-id="514d3-104">Aşağıdaki XML kullanarak</span><span class="sxs-lookup"><span data-stu-id="514d3-104">Using the following XML,</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="514d3-105">DOM derlemeleri bir **XmlEntityReference** karşılaştığında bu düğüm `&publisher;` başvuru.</span><span class="sxs-lookup"><span data-stu-id="514d3-105">the DOM builds an **XmlEntityReference** node when it encounters the `&publisher;` reference.</span></span> <span data-ttu-id="514d3-106">**XmlEntityReference** varlık bildiriminde içeriğinden kopyalanan alt düğümleri içerir.</span><span class="sxs-lookup"><span data-stu-id="514d3-106">The **XmlEntityReference** contains child nodes copied from the content in the entity declaration.</span></span> <span data-ttu-id="514d3-107">Yukarıdaki kod örneğinde metni varlık bildirimde, bu nedenle içeren bir **XmlText** düğüm varlık referans düğümün alt düğümü olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="514d3-107">The preceding code example contains text in the entity declaration, so an **XmlText** node is created as the child node of the entity reference node.</span></span>  
  
 <span data-ttu-id="514d3-108">![Ağaç yapısı Korunan varlık başvuruları için](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span><span class="sxs-lookup"><span data-stu-id="514d3-108">![Tree structure for preserved entity references](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span></span>  
<span data-ttu-id="514d3-109">Korunur varlık başvuruları için ağaç yapısı</span><span class="sxs-lookup"><span data-stu-id="514d3-109">Tree structure for entity references that are preserved</span></span>  
  
 <span data-ttu-id="514d3-110">Alt düğümleri **XmlEntityReference** tüm alt kopyalarını oluşturulan düğümlerdir **XmlEntity** varlık bildirimi karşılaştığında düğümü.</span><span class="sxs-lookup"><span data-stu-id="514d3-110">The child nodes of the **XmlEntityReference** are copies of all the child nodes created from the **XmlEntity** node when the entity declaration was encountered.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="514d3-111">Öğesinden kopyalanan düğümleri **XmlEntity** olmayan her zaman tam kopya varlık referans düğümün altında kez yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="514d3-111">The nodes copied from the **XmlEntity** are not always exact copies once placed under the entity reference node.</span></span> <span data-ttu-id="514d3-112">Varlık referans düğümün kapsamda bulunan ad olabilir ve bu alt düğümlerin son yapılandırma etkiler.</span><span class="sxs-lookup"><span data-stu-id="514d3-112">There can be namespaces that are in scope at the entity reference node, and that affects the final configuration of the child nodes.</span></span>  
  
 <span data-ttu-id="514d3-113">Varsayılan olarak, genel varlıklar ister `&abc;` korunur ve **XmlEntityReference** düğümleri her zaman oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="514d3-113">By default, general entities like `&abc;` are preserved and **XmlEntityReference** nodes always created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="514d3-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="514d3-114">See also</span></span>

- [<span data-ttu-id="514d3-115">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="514d3-115">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
