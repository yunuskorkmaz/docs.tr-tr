---
title: DOM düğümleri kaldırma
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 0a98e0ca-0555-45c1-ab69-0d8d20ca1abd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ec786564e6246f10e10d600f4822442884323557
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568465"
---
# <a name="removing-nodes-from-the-dom"></a><span data-ttu-id="8919f-102">DOM düğümleri kaldırma</span><span class="sxs-lookup"><span data-stu-id="8919f-102">Removing Nodes from the DOM</span></span>
<span data-ttu-id="8919f-103">XML belge nesne modeli (DOM) gelen bir düğümünü kaldırmak için kullanın <xref:System.Xml.XmlNode.RemoveChild%2A> belirli bir düğümü çıkarmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="8919f-103">To remove a node from the XML Document Object Model (DOM), use the <xref:System.Xml.XmlNode.RemoveChild%2A> method to remove a specific node.</span></span> <span data-ttu-id="8919f-104">Yöntemi, bir düğümü kaldırdığınızda, kaldırılmakta olan düğüme ait alt ağacı kaldırır; diğer bir deyişle, bir yaprak düğüm değilse.</span><span class="sxs-lookup"><span data-stu-id="8919f-104">When you remove a node, the method removes the subtree belonging to the node being removed; that is, if it is not a leaf node.</span></span>  
  
 <span data-ttu-id="8919f-105">DOM birden çok düğüm kaldırmak için kullanın <xref:System.Xml.XmlNode.RemoveAll%2A> geçerli düğümünün varsa, tüm alt öğeleri ve öznitelikleri kaldırmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="8919f-105">To remove multiple nodes from the DOM, use the <xref:System.Xml.XmlNode.RemoveAll%2A> method to remove all the children and attributes, if applicable, of the current node.</span></span>  
  
 <span data-ttu-id="8919f-106">İle çalışıyorsanız bir <xref:System.Xml.XmlNamedNodeMap>, kullanarak bir düğümü kaldırma <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8919f-106">If you are working with an <xref:System.Xml.XmlNamedNodeMap>, you can remove a node using the <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> method.</span></span>  
  
 <span data-ttu-id="8919f-107">Öznitelikleri kaldırmak için bkz: [DOM öğesi düğümünde kaldırma özniteliklerden](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="8919f-107">To remove attributes, see [Removing Attributes from an Element Node in the DOM](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8919f-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8919f-108">See Also</span></span>  
 [<span data-ttu-id="8919f-109">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="8919f-109">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
