---
title: Varolan düğümleri kopyalayın
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 2aa8f65c-cc62-4638-9c46-129dc15be786
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2e7f5638d0d1f7bf450be526d7c295d4bb6a79eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33567919"
---
# <a name="copy-existing-nodes"></a><span data-ttu-id="cda69-102">Varolan düğümleri kopyalayın</span><span class="sxs-lookup"><span data-stu-id="cda69-102">Copy Existing Nodes</span></span>
<span data-ttu-id="cda69-103">Birçok yöntemleri ve özellikleri de XML belge nesne modeli (gibi bir düğümü seçmek için kullanabileceğiniz DOM) **SelectSingleNode**, **ChildNodes [int t]**, **öznitelikleri [int t]**.</span><span class="sxs-lookup"><span data-stu-id="cda69-103">There are many methods and properties in the XML Document Object Model (DOM)you can use to select a node, such as **SelectSingleNode**, **ChildNodes[int i]**, **Attributes[int i]**.</span></span> <span data-ttu-id="cda69-104">Düğüm seçildikten sonra bu belirli düğüm türü için iş Ekle yöntemlerden birini kullanarak ağaca ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cda69-104">Once the node is selected, you can insert it into the tree using one of the insert methods that work for that particular node type.</span></span> <span data-ttu-id="cda69-105">Ağacına bir düğüm eklemek için yalnızca düğüm eklendikten sonra belgenin hala doğru biçimlendirilmiş olması gerektiğini kısıtlamadır.</span><span class="sxs-lookup"><span data-stu-id="cda69-105">The only restriction to inserting a node into the tree is that the document must still be well-formed after the node is inserted.</span></span> <span data-ttu-id="cda69-106">Varolan bir düğümü DOM ağacına takıldığında, özgün konumundan kaldırılır ve hedef konumuna eklendi.</span><span class="sxs-lookup"><span data-stu-id="cda69-106">When an existing node is inserted into the DOM tree, it is removed from its original position and added to its target position.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cda69-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cda69-107">See Also</span></span>  
 [<span data-ttu-id="cda69-108">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="cda69-108">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
