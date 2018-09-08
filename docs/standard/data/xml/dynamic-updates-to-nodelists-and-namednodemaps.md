---
title: NodeLists ve NamedNodeMaps dinamik güncelleştirmeleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 76c511fd-6704-4ca4-8078-860a68d898ad
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9f56ba8711988f2f7d743dc4ff7b69272e2642a2
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44207414"
---
# <a name="dynamic-updates-to-nodelists-and-namednodemaps"></a><span data-ttu-id="05ab5-102">NodeLists ve NamedNodeMaps dinamik güncelleştirmeleri</span><span class="sxs-lookup"><span data-stu-id="05ab5-102">Dynamic Updates to NodeLists and NamedNodeMaps</span></span>
<span data-ttu-id="05ab5-103">Çünkü **XmlNodeList** ve **XmlNamedNodeMap** XML belgesi belleğe yüklenir ve değiştirilmekte olduğundan, henüz bir dizi düğümü, içeren bildiren World Wide Web Consortium (W3C) bu nesneler dinamik olarak düğüm gereksinim kümesini içerir.</span><span class="sxs-lookup"><span data-stu-id="05ab5-103">Because the **XmlNodeList** and the **XmlNamedNodeMap** contain a set of nodes, yet the XML document is loaded into memory and is being modified, the World Wide Web Consortium (W3C) states that these objects that contain sets of nodes need to be dynamic.</span></span> <span data-ttu-id="05ab5-104">Temel alınan belge değişirse, diğer bir deyişle, sonra bu iki nesne verileri de değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="05ab5-104">That is, if the underlying document changes, then the data in these two objects should change also.</span></span> <span data-ttu-id="05ab5-105">Bu nedenle, varsa bir **XmlNodeList** (örneğin, X öğesi) belirli bir öğenin tüm alt öğelerini içeren ve ardından ek bir öğe, öğe Q, belgenin X öğesinin altına ekleyin. **XmlNodeList** o yeni öğe kendi koleksiyonuna eklediğiniz soru da olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="05ab5-105">Therefore, if you have an **XmlNodeList** that contains all the child elements of a particular element (for example, element X), then you add an additional element, element Q, to the document under element X. The **XmlNodeList** should also have that new element Q added to its collection.</span></span> <span data-ttu-id="05ab5-106">Aynı durum geçerlidir ters.</span><span class="sxs-lookup"><span data-stu-id="05ab5-106">The same is true in reverse.</span></span> <span data-ttu-id="05ab5-107">Bir düğüm eklenirse **XmlNodeList**, temel alınan belge de güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="05ab5-107">If a node is added to the **XmlNodeList**, the underlying document is updated as well.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05ab5-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05ab5-108">See also</span></span>

- [<span data-ttu-id="05ab5-109">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="05ab5-109">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
