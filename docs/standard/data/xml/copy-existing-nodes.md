---
description: 'Hakkında daha fazla bilgi edinin: var olan düğümleri kopyalama'
title: Var Olan Düğümleri Kopyalama
ms.date: 03/30/2017
ms.assetid: 2aa8f65c-cc62-4638-9c46-129dc15be786
ms.openlocfilehash: 48bc1fd4f0eeb16691d6f9c0631998db9a54bba1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783436"
---
# <a name="copy-existing-nodes"></a><span data-ttu-id="70853-103">Var Olan Düğümleri Kopyalama</span><span class="sxs-lookup"><span data-stu-id="70853-103">Copy Existing Nodes</span></span>

<span data-ttu-id="70853-104">XML Belge Nesne Modeli (DOM), **selectSingleNode**, **ChildNodes [int i]**, **öznitelikler [int i]** gibi bir düğümü seçmek için kullanabileceğiniz birçok yöntem ve özellik vardır.</span><span class="sxs-lookup"><span data-stu-id="70853-104">There are many methods and properties in the XML Document Object Model (DOM)you can use to select a node, such as **SelectSingleNode**, **ChildNodes[int i]**, **Attributes[int i]**.</span></span> <span data-ttu-id="70853-105">Düğüm seçildikten sonra, söz konusu düğüm türü için çalışan INSERT yöntemlerinden birini kullanarak ağaca ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70853-105">Once the node is selected, you can insert it into the tree using one of the insert methods that work for that particular node type.</span></span> <span data-ttu-id="70853-106">Ağaca bir düğüm eklemeye yönelik tek kısıtlama, belgenin düğüm eklendikten sonra yine de doğru biçimlendirilmiş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="70853-106">The only restriction to inserting a node into the tree is that the document must still be well-formed after the node is inserted.</span></span> <span data-ttu-id="70853-107">Varolan bir düğüm DOM ağacına eklendiğinde, özgün konumundan kaldırılır ve hedef konumuna eklenir.</span><span class="sxs-lookup"><span data-stu-id="70853-107">When an existing node is inserted into the DOM tree, it is removed from its original position and added to its target position.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70853-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70853-108">See also</span></span>

- [<span data-ttu-id="70853-109">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="70853-109">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
