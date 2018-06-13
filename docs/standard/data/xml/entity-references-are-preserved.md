---
title: Varlık başvuruları korunur
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 000a6cae-5972-40d6-bd6c-a9b7d9649b3c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 652a044bf1b5293bc9c36477a46a78d9851f1810
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568491"
---
# <a name="entity-references-are-preserved"></a><span data-ttu-id="859ea-102">Varlık başvuruları korunur</span><span class="sxs-lookup"><span data-stu-id="859ea-102">Entity References are Preserved</span></span>
<span data-ttu-id="859ea-103">Varlık başvurusu genişletilmiş, ancak korunur, XML belge nesne modeli (DOM) derlemeler bir **XmlEntityReference** bir varlık başvurusunun karşılaştığında düğümü.</span><span class="sxs-lookup"><span data-stu-id="859ea-103">When the entity reference is not expanded, but preserved, the XML Document Object Model (DOM) builds an **XmlEntityReference** node when it encounters an entity reference.</span></span>  
  
 <span data-ttu-id="859ea-104">Aşağıdaki XML kullanarak</span><span class="sxs-lookup"><span data-stu-id="859ea-104">Using the following XML,</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="859ea-105">DOM derlemeler bir **XmlEntityReference** onu karşılaştığında düğümü `&publisher;` başvuru.</span><span class="sxs-lookup"><span data-stu-id="859ea-105">the DOM builds an **XmlEntityReference** node when it encounters the `&publisher;` reference.</span></span> <span data-ttu-id="859ea-106">**XmlEntityReference** varlık bildiriminin içeriği kopyalanan alt düğümleri içerir.</span><span class="sxs-lookup"><span data-stu-id="859ea-106">The **XmlEntityReference** contains child nodes copied from the content in the entity declaration.</span></span> <span data-ttu-id="859ea-107">Bu nedenle önceki kod örneğinde varlık bildiriminde metni içeren bir **XmlText** düğümü varlık referans düğümün alt düğümü olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="859ea-107">The preceding code example contains text in the entity declaration, so an **XmlText** node is created as the child node of the entity reference node.</span></span>  
  
 <span data-ttu-id="859ea-108">![Ağaç yapısı Korunan varlık başvuruları için](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span><span class="sxs-lookup"><span data-stu-id="859ea-108">![Tree structure for preserved entity references](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span></span>  
<span data-ttu-id="859ea-109">Korunur varlık başvuruları için ağaç yapısı</span><span class="sxs-lookup"><span data-stu-id="859ea-109">Tree structure for entity references that are preserved</span></span>  
  
 <span data-ttu-id="859ea-110">Alt düğümleri **XmlEntityReference** düğümleri oluşturulan tüm alt kopyalarıdır **XmlEntity** varlık bildirimi karşılaştığında düğümü.</span><span class="sxs-lookup"><span data-stu-id="859ea-110">The child nodes of the **XmlEntityReference** are copies of all the child nodes created from the **XmlEntity** node when the entity declaration was encountered.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="859ea-111">Kopyalanan düğümleri **XmlEntity** olmayan her zaman tam kopyaları kez varlık başvurusu düğümünde yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="859ea-111">The nodes copied from the **XmlEntity** are not always exact copies once placed under the entity reference node.</span></span> <span data-ttu-id="859ea-112">Varlık referans düğümün kapsamında bulunan ad alanları olabilir ve son yapılandırma alt düğümlerin etkiler.</span><span class="sxs-lookup"><span data-stu-id="859ea-112">There can be namespaces that are in scope at the entity reference node, and that affects the final configuration of the child nodes.</span></span>  
  
 <span data-ttu-id="859ea-113">Varsayılan olarak, genel varlıklar ister `&abc;` korunur ve **XmlEntityReference** her zaman oluşturulan düğümler.</span><span class="sxs-lookup"><span data-stu-id="859ea-113">By default, general entities like `&abc;` are preserved and **XmlEntityReference** nodes always created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="859ea-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="859ea-114">See Also</span></span>  
 [<span data-ttu-id="859ea-115">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="859ea-115">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
