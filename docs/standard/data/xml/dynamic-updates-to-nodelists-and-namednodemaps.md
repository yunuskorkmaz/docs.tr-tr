---
title: NodeLists ve NamedNodeMaps Dinamik Güncelleştirmeleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 76c511fd-6704-4ca4-8078-860a68d898ad
ms.openlocfilehash: 0199f24e9ef8dd28f91976edd50f78399dc893ef
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84292091"
---
# <a name="dynamic-updates-to-nodelists-and-namednodemaps"></a><span data-ttu-id="c2719-102">NodeLists ve NamedNodeMaps Dinamik Güncelleştirmeleri</span><span class="sxs-lookup"><span data-stu-id="c2719-102">Dynamic Updates to NodeLists and NamedNodeMaps</span></span>
<span data-ttu-id="c2719-103">**XmlNodeList** ve **XmlNamedNodeMap** bir düğüm kümesi içerdiğinden, XML belgesi belleğe yüklenmiş ve değiştirilmekte olduğundan, World Wide Web Konsorsiyumu (W3C) düğüm kümelerini içeren bu nesnelerin dinamik olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c2719-103">Because the **XmlNodeList** and the **XmlNamedNodeMap** contain a set of nodes, yet the XML document is loaded into memory and is being modified, the World Wide Web Consortium (W3C) states that these objects that contain sets of nodes need to be dynamic.</span></span> <span data-ttu-id="c2719-104">Diğer bir deyişle, temeldeki belge değişirse, bu iki nesnelerdeki verilerin de değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="c2719-104">That is, if the underlying document changes, then the data in these two objects should change also.</span></span> <span data-ttu-id="c2719-105">Bu nedenle, belirli bir öğenin tüm alt öğelerini içeren bir **XmlNodeList** varsa (örneğin, öğesi x), öğe x ' in altındaki belgeye, ek bir öğe olan soru-cevap ekleyin. **XmlNodeList** aynı zamanda koleksiyonuna yeni bir s öğesi eklenmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c2719-105">Therefore, if you have an **XmlNodeList** that contains all the child elements of a particular element (for example, element X), then you add an additional element, element Q, to the document under element X. The **XmlNodeList** should also have that new element Q added to its collection.</span></span> <span data-ttu-id="c2719-106">Aynı değer ters de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c2719-106">The same is true in reverse.</span></span> <span data-ttu-id="c2719-107">**XmlNodeList**nesnesine bir düğüm eklenirse, temel alınan belge de güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c2719-107">If a node is added to the **XmlNodeList**, the underlying document is updated as well.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2719-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2719-108">See also</span></span>

- [<span data-ttu-id="c2719-109">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="c2719-109">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
