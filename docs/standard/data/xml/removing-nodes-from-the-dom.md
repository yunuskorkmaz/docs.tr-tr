---
title: DOM’dan Düğümleri Kaldırma
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 0a98e0ca-0555-45c1-ab69-0d8d20ca1abd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: be592466627e6ee7b23c608e0defe786548907ad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698674"
---
# <a name="removing-nodes-from-the-dom"></a><span data-ttu-id="0b3d3-102">DOM’dan Düğümleri Kaldırma</span><span class="sxs-lookup"><span data-stu-id="0b3d3-102">Removing Nodes from the DOM</span></span>
<span data-ttu-id="0b3d3-103">XML belge nesne modeli (DOM) öğesinden bir düğümü kaldırmak için <xref:System.Xml.XmlNode.RemoveChild%2A> belirli bir düğümü kaldırmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0b3d3-103">To remove a node from the XML Document Object Model (DOM), use the <xref:System.Xml.XmlNode.RemoveChild%2A> method to remove a specific node.</span></span> <span data-ttu-id="0b3d3-104">Yöntemi, bir düğümü kaldırdığınızda, kaldırılmakta olan düğüme ait alt ağacı kaldırır; diğer bir deyişle, bir yaprak düğüm değilse.</span><span class="sxs-lookup"><span data-stu-id="0b3d3-104">When you remove a node, the method removes the subtree belonging to the node being removed; that is, if it is not a leaf node.</span></span>  
  
 <span data-ttu-id="0b3d3-105">DOM'dan birden fazla düğüm kaldırmak için <xref:System.Xml.XmlNode.RemoveAll%2A> geçerli düğümünün (varsa), tüm alt öğeleri ve öznitelikleri kaldırmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0b3d3-105">To remove multiple nodes from the DOM, use the <xref:System.Xml.XmlNode.RemoveAll%2A> method to remove all the children and attributes, if applicable, of the current node.</span></span>  
  
 <span data-ttu-id="0b3d3-106">İle çalışıyorsanız bir <xref:System.Xml.XmlNamedNodeMap>, kullanarak bir düğümü kaldırmak <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0b3d3-106">If you are working with an <xref:System.Xml.XmlNamedNodeMap>, you can remove a node using the <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> method.</span></span>  
  
 <span data-ttu-id="0b3d3-107">Öznitelikleri kaldırmak için bkz: [DOM'da bir öğe düğümünden öznitelikleri kaldırma](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="0b3d3-107">To remove attributes, see [Removing Attributes from an Element Node in the DOM](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b3d3-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b3d3-108">See also</span></span>

- [<span data-ttu-id="0b3d3-109">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="0b3d3-109">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
