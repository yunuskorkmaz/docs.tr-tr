---
title: Var Olan Düğümleri Kopyalama
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 2aa8f65c-cc62-4638-9c46-129dc15be786
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eda5c9b4851b29c0a76e45414d7c47ba52252455
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61864136"
---
# <a name="copy-existing-nodes"></a><span data-ttu-id="b5acd-102">Var Olan Düğümleri Kopyalama</span><span class="sxs-lookup"><span data-stu-id="b5acd-102">Copy Existing Nodes</span></span>
<span data-ttu-id="b5acd-103">Birçok yöntem ve Özellikler içinde XML belge nesne modeli (gibi bir düğümü seçmek için kullanabileceğiniz DOM) vardır **SelectSingleNode**, **ChildNodes [int i]**, **öznitelikleri [int miyim]**.</span><span class="sxs-lookup"><span data-stu-id="b5acd-103">There are many methods and properties in the XML Document Object Model (DOM)you can use to select a node, such as **SelectSingleNode**, **ChildNodes[int i]**, **Attributes[int i]**.</span></span> <span data-ttu-id="b5acd-104">Düğüm seçildikten sonra bu belirli düğüm türü için çalışan INSERT yöntemlerden birini kullanarak ağaca ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5acd-104">Once the node is selected, you can insert it into the tree using one of the insert methods that work for that particular node type.</span></span> <span data-ttu-id="b5acd-105">Ağacına bir düğüm eklemek için tek bir kısıtlama düğüm ekledikten sonra belgeyi yine de iyi biçimlendirilmiş olması gerekliliğidir.</span><span class="sxs-lookup"><span data-stu-id="b5acd-105">The only restriction to inserting a node into the tree is that the document must still be well-formed after the node is inserted.</span></span> <span data-ttu-id="b5acd-106">Varolan bir düğümü DOM ağacına eklendiğinde, özgün konumundan kaldırıldı ve hedef konumuna eklendi.</span><span class="sxs-lookup"><span data-stu-id="b5acd-106">When an existing node is inserted into the DOM tree, it is removed from its original position and added to its target position.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5acd-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5acd-107">See also</span></span>

- [<span data-ttu-id="b5acd-108">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="b5acd-108">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
