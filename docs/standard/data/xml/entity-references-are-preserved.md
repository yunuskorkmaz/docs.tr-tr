---
title: Varlık başvuruları korunur
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 000a6cae-5972-40d6-bd6c-a9b7d9649b3c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b1c48e42e55025aff0ce1a24a3ef45ddf8005eab
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44204327"
---
# <a name="entity-references-are-preserved"></a><span data-ttu-id="6a9e2-102">Varlık başvuruları korunur</span><span class="sxs-lookup"><span data-stu-id="6a9e2-102">Entity References are Preserved</span></span>
<span data-ttu-id="6a9e2-103">Varlık başvurusu genişletilmiş, ancak korunur, XML belge nesne modeli (DOM) derlemeleri bir **XmlEntityReference** bir varlık başvurusu karşılaştığında düğümü.</span><span class="sxs-lookup"><span data-stu-id="6a9e2-103">When the entity reference is not expanded, but preserved, the XML Document Object Model (DOM) builds an **XmlEntityReference** node when it encounters an entity reference.</span></span>  
  
 <span data-ttu-id="6a9e2-104">Aşağıdaki XML kullanarak</span><span class="sxs-lookup"><span data-stu-id="6a9e2-104">Using the following XML,</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="6a9e2-105">DOM derlemeleri bir **XmlEntityReference** karşılaştığında bu düğüm `&publisher;` başvuru.</span><span class="sxs-lookup"><span data-stu-id="6a9e2-105">the DOM builds an **XmlEntityReference** node when it encounters the `&publisher;` reference.</span></span> <span data-ttu-id="6a9e2-106">**XmlEntityReference** varlık bildiriminde içeriğinden kopyalanan alt düğümleri içerir.</span><span class="sxs-lookup"><span data-stu-id="6a9e2-106">The **XmlEntityReference** contains child nodes copied from the content in the entity declaration.</span></span> <span data-ttu-id="6a9e2-107">Yukarıdaki kod örneğinde metni varlık bildirimde, bu nedenle içeren bir **XmlText** düğüm varlık referans düğümün alt düğümü olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6a9e2-107">The preceding code example contains text in the entity declaration, so an **XmlText** node is created as the child node of the entity reference node.</span></span>  
  
 <span data-ttu-id="6a9e2-108">![Ağaç yapısı Korunan varlık başvuruları için](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span><span class="sxs-lookup"><span data-stu-id="6a9e2-108">![Tree structure for preserved entity references](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span></span>  
<span data-ttu-id="6a9e2-109">Korunur varlık başvuruları için ağaç yapısı</span><span class="sxs-lookup"><span data-stu-id="6a9e2-109">Tree structure for entity references that are preserved</span></span>  
  
 <span data-ttu-id="6a9e2-110">Alt düğümleri **XmlEntityReference** tüm alt kopyalarını oluşturulan düğümlerdir **XmlEntity** varlık bildirimi karşılaştığında düğümü.</span><span class="sxs-lookup"><span data-stu-id="6a9e2-110">The child nodes of the **XmlEntityReference** are copies of all the child nodes created from the **XmlEntity** node when the entity declaration was encountered.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6a9e2-111">Öğesinden kopyalanan düğümleri **XmlEntity** olmayan her zaman tam kopya varlık referans düğümün altında kez yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="6a9e2-111">The nodes copied from the **XmlEntity** are not always exact copies once placed under the entity reference node.</span></span> <span data-ttu-id="6a9e2-112">Varlık referans düğümün kapsamda bulunan ad olabilir ve bu alt düğümlerin son yapılandırma etkiler.</span><span class="sxs-lookup"><span data-stu-id="6a9e2-112">There can be namespaces that are in scope at the entity reference node, and that affects the final configuration of the child nodes.</span></span>  
  
 <span data-ttu-id="6a9e2-113">Varsayılan olarak, genel varlıklar ister `&abc;` korunur ve **XmlEntityReference** düğümleri her zaman oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6a9e2-113">By default, general entities like `&abc;` are preserved and **XmlEntityReference** nodes always created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a9e2-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a9e2-114">See also</span></span>

- [<span data-ttu-id="6a9e2-115">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="6a9e2-115">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
