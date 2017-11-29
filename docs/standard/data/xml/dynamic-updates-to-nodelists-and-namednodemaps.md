---
title: "Dinamik güncelleştirmeleri NodeLists ve NamedNodeMaps"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76c511fd-6704-4ca4-8078-860a68d898ad
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 459d746ff278ac4affa0318c1fad0aeb6a73e560
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="dynamic-updates-to-nodelists-and-namednodemaps"></a><span data-ttu-id="ad62c-102">Dinamik güncelleştirmeleri NodeLists ve NamedNodeMaps</span><span class="sxs-lookup"><span data-stu-id="ad62c-102">Dynamic Updates to NodeLists and NamedNodeMaps</span></span>
<span data-ttu-id="ad62c-103">Çünkü **XmlNodeList** ve **XmlNamedNodeMap** XML belgesi belleğe yüklenir ve değiştirilmekte olduğundan, henüz bir düğüm kümesini içeren World Wide Web Konsorsiyumu (W3C) bildiren bu nesneler Bu düğümler dinamik olarak gerek kümesi içerir.</span><span class="sxs-lookup"><span data-stu-id="ad62c-103">Because the **XmlNodeList** and the **XmlNamedNodeMap** contain a set of nodes, yet the XML document is loaded into memory and is being modified, the World Wide Web Consortium (W3C) states that these objects that contain sets of nodes need to be dynamic.</span></span> <span data-ttu-id="ad62c-104">Temel alınan belge değişirse, diğer bir deyişle, ardından bu iki nesne verileri aynı zamanda değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ad62c-104">That is, if the underlying document changes, then the data in these two objects should change also.</span></span> <span data-ttu-id="ad62c-105">Bu nedenle, varsa bir **XmlNodeList** belirli bir öğenin (örneğin, X öğesi) tüm alt öğelerini içeren ve ardından ek öğe, belgenin öğesi X altında Q, öğesine ekleyin. **XmlNodeList** bu yeni bir öğesi kendi koleksiyonuna eklenen Q de olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ad62c-105">Therefore, if you have an **XmlNodeList** that contains all the child elements of a particular element (for example, element X), then you add an additional element, element Q, to the document under element X. The **XmlNodeList** should also have that new element Q added to its collection.</span></span> <span data-ttu-id="ad62c-106">Aynı durum geçerlidir ters.</span><span class="sxs-lookup"><span data-stu-id="ad62c-106">The same is true in reverse.</span></span> <span data-ttu-id="ad62c-107">Bir düğüm eklenirse **XmlNodeList**, temel alınan belge de güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="ad62c-107">If a node is added to the **XmlNodeList**, the underlying document is updated as well.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad62c-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ad62c-108">See Also</span></span>  
 [<span data-ttu-id="ad62c-109">XML belge nesne modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="ad62c-109">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
