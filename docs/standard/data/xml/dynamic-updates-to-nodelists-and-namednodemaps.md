---
description: 'Daha fazla bilgi edinin: NodeLists ve NamedNodeMaps için dinamik güncelleştirmeler'
title: NodeLists ve NamedNodeMaps Dinamik Güncelleştirmeleri
ms.date: 03/30/2017
ms.assetid: 76c511fd-6704-4ca4-8078-860a68d898ad
ms.openlocfilehash: 4e4b88d0e084e32fdb27f3d5762e305a4e900f1e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783384"
---
# <a name="dynamic-updates-to-nodelists-and-namednodemaps"></a><span data-ttu-id="782fc-103">NodeLists ve NamedNodeMaps Dinamik Güncelleştirmeleri</span><span class="sxs-lookup"><span data-stu-id="782fc-103">Dynamic Updates to NodeLists and NamedNodeMaps</span></span>

<span data-ttu-id="782fc-104">**XmlNodeList** ve **XmlNamedNodeMap** bir düğüm kümesi içerdiğinden, XML belgesi belleğe yüklenmiş ve değiştirilmekte olduğundan, World Wide Web Konsorsiyumu (W3C) düğüm kümelerini içeren bu nesnelerin dinamik olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="782fc-104">Because the **XmlNodeList** and the **XmlNamedNodeMap** contain a set of nodes, yet the XML document is loaded into memory and is being modified, the World Wide Web Consortium (W3C) states that these objects that contain sets of nodes need to be dynamic.</span></span> <span data-ttu-id="782fc-105">Diğer bir deyişle, temeldeki belge değişirse, bu iki nesnelerdeki verilerin de değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="782fc-105">That is, if the underlying document changes, then the data in these two objects should change also.</span></span> <span data-ttu-id="782fc-106">Bu nedenle, belirli bir öğenin tüm alt öğelerini içeren bir **XmlNodeList** varsa (örneğin, öğesi x), öğe x ' in altındaki belgeye, ek bir öğe olan soru-cevap ekleyin. **XmlNodeList** aynı zamanda koleksiyonuna yeni bir s öğesi eklenmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="782fc-106">Therefore, if you have an **XmlNodeList** that contains all the child elements of a particular element (for example, element X), then you add an additional element, element Q, to the document under element X. The **XmlNodeList** should also have that new element Q added to its collection.</span></span> <span data-ttu-id="782fc-107">Aynı değer ters de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="782fc-107">The same is true in reverse.</span></span> <span data-ttu-id="782fc-108">**XmlNodeList** nesnesine bir düğüm eklenirse, temel alınan belge de güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="782fc-108">If a node is added to the **XmlNodeList**, the underlying document is updated as well.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="782fc-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="782fc-109">See also</span></span>

- [<span data-ttu-id="782fc-110">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="782fc-110">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
