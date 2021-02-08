---
description: "Daha fazla bilgi edinin: DOM 'dan düğümleri kaldırma"
title: DOM’dan Düğümleri Kaldırma
ms.date: 03/30/2017
ms.assetid: 0a98e0ca-0555-45c1-ab69-0d8d20ca1abd
ms.openlocfilehash: b5e85157c194b034289a46140a44d2a9d1109061
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783098"
---
# <a name="removing-nodes-from-the-dom"></a><span data-ttu-id="35389-103">DOM’dan Düğümleri Kaldırma</span><span class="sxs-lookup"><span data-stu-id="35389-103">Removing Nodes from the DOM</span></span>

<span data-ttu-id="35389-104">XML Belge Nesne Modeli (DOM) bir düğümü kaldırmak için, <xref:System.Xml.XmlNode.RemoveChild%2A> belirli bir düğümü kaldırmak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="35389-104">To remove a node from the XML Document Object Model (DOM), use the <xref:System.Xml.XmlNode.RemoveChild%2A> method to remove a specific node.</span></span> <span data-ttu-id="35389-105">Bir düğümü kaldırdığınızda, yöntemi kaldırılan düğüme ait olan alt ağacı kaldırır; diğer bir deyişle, bir yaprak düğüm değildir.</span><span class="sxs-lookup"><span data-stu-id="35389-105">When you remove a node, the method removes the subtree belonging to the node being removed; that is, if it is not a leaf node.</span></span>  
  
 <span data-ttu-id="35389-106">DOM 'dan birden fazla düğümü kaldırmak için, <xref:System.Xml.XmlNode.RemoveAll%2A> geçerli düğümün varsa tüm alt öğeleri ve öznitelikleri kaldırmak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="35389-106">To remove multiple nodes from the DOM, use the <xref:System.Xml.XmlNode.RemoveAll%2A> method to remove all the children and attributes, if applicable, of the current node.</span></span>  
  
 <span data-ttu-id="35389-107">İle çalışıyorsanız <xref:System.Xml.XmlNamedNodeMap> , yöntemini kullanarak bir düğümü kaldırabilirsiniz <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> .</span><span class="sxs-lookup"><span data-stu-id="35389-107">If you are working with an <xref:System.Xml.XmlNamedNodeMap>, you can remove a node using the <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> method.</span></span>  
  
 <span data-ttu-id="35389-108">Öznitelikleri kaldırmak için bkz. [Dom 'daki bir öğe düğümünden öznitelikleri kaldırma](removing-attributes-from-an-element-node-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="35389-108">To remove attributes, see [Removing Attributes from an Element Node in the DOM](removing-attributes-from-an-element-node-in-the-dom.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35389-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="35389-109">See also</span></span>

- [<span data-ttu-id="35389-110">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="35389-110">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
