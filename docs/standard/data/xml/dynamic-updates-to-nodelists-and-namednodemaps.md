---
title: NodeLists ve NamedNodeMaps Dinamik Güncelleştirmeleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 76c511fd-6704-4ca4-8078-860a68d898ad
ms.openlocfilehash: 58dfde94c2f37b0a09ee795b9df20296c9f86da6
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710979"
---
# <a name="dynamic-updates-to-nodelists-and-namednodemaps"></a><span data-ttu-id="2dbda-102">NodeLists ve NamedNodeMaps Dinamik Güncelleştirmeleri</span><span class="sxs-lookup"><span data-stu-id="2dbda-102">Dynamic Updates to NodeLists and NamedNodeMaps</span></span>
<span data-ttu-id="2dbda-103">**XmlNodeList** ve **XmlNamedNodeMap** bir düğüm kümesi içerdiğinden, XML belgesi belleğe yüklenmiş ve değiştirilmekte olduğundan, World Wide Web Konsorsiyumu (W3C) düğüm kümelerini içeren bu nesnelerin dinamik olması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2dbda-103">Because the **XmlNodeList** and the **XmlNamedNodeMap** contain a set of nodes, yet the XML document is loaded into memory and is being modified, the World Wide Web Consortium (W3C) states that these objects that contain sets of nodes need to be dynamic.</span></span> <span data-ttu-id="2dbda-104">Diğer bir deyişle, temeldeki belge değişirse, bu iki nesnelerdeki verilerin de değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="2dbda-104">That is, if the underlying document changes, then the data in these two objects should change also.</span></span> <span data-ttu-id="2dbda-105">Bu nedenle, belirli bir öğenin tüm alt öğelerini içeren bir **XmlNodeList** varsa (örneğin, öğesi x), öğe x ' in altındaki belgeye, ek bir öğe olan soru-cevap ekleyin. **XmlNodeList** aynı zamanda koleksiyonuna yeni bir s öğesi eklenmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2dbda-105">Therefore, if you have an **XmlNodeList** that contains all the child elements of a particular element (for example, element X), then you add an additional element, element Q, to the document under element X. The **XmlNodeList** should also have that new element Q added to its collection.</span></span> <span data-ttu-id="2dbda-106">Aynı değer ters de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="2dbda-106">The same is true in reverse.</span></span> <span data-ttu-id="2dbda-107">**XmlNodeList**nesnesine bir düğüm eklenirse, temel alınan belge de güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="2dbda-107">If a node is added to the **XmlNodeList**, the underlying document is updated as well.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dbda-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2dbda-108">See also</span></span>

- [<span data-ttu-id="2dbda-109">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="2dbda-109">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
