---
title: "Varolan düğümleri kopyalayın"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2aa8f65c-cc62-4638-9c46-129dc15be786
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 11f3915dfebd7ad9d3144c9bedcd7f42b4754359
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="copy-existing-nodes"></a><span data-ttu-id="0a27a-102">Varolan düğümleri kopyalayın</span><span class="sxs-lookup"><span data-stu-id="0a27a-102">Copy Existing Nodes</span></span>
<span data-ttu-id="0a27a-103">Birçok yöntemleri ve özellikleri de XML belge nesne modeli (gibi bir düğümü seçmek için kullanabileceğiniz DOM) **SelectSingleNode**, **ChildNodes [int t]**, **öznitelikleri [int t]**.</span><span class="sxs-lookup"><span data-stu-id="0a27a-103">There are many methods and properties in the XML Document Object Model (DOM)you can use to select a node, such as **SelectSingleNode**, **ChildNodes[int i]**, **Attributes[int i]**.</span></span> <span data-ttu-id="0a27a-104">Düğüm seçildikten sonra bu belirli düğüm türü için iş Ekle yöntemlerden birini kullanarak ağaca ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0a27a-104">Once the node is selected, you can insert it into the tree using one of the insert methods that work for that particular node type.</span></span> <span data-ttu-id="0a27a-105">Ağacına bir düğüm eklemek için yalnızca düğüm eklendikten sonra belgenin hala doğru biçimlendirilmiş olması gerektiğini kısıtlamadır.</span><span class="sxs-lookup"><span data-stu-id="0a27a-105">The only restriction to inserting a node into the tree is that the document must still be well-formed after the node is inserted.</span></span> <span data-ttu-id="0a27a-106">Varolan bir düğümü DOM ağacına takıldığında, özgün konumundan kaldırılır ve hedef konumuna eklendi.</span><span class="sxs-lookup"><span data-stu-id="0a27a-106">When an existing node is inserted into the DOM tree, it is removed from its original position and added to its target position.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a27a-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0a27a-107">See Also</span></span>  
 [<span data-ttu-id="0a27a-108">XML belge nesne modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="0a27a-108">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
