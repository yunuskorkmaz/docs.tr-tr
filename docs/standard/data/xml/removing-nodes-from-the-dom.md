---
title: DOM’dan Düğümleri Kaldırma
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 0a98e0ca-0555-45c1-ab69-0d8d20ca1abd
ms.openlocfilehash: a34b92abc59215c3cb2b94afd88e2e30405b4e9a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710316"
---
# <a name="removing-nodes-from-the-dom"></a><span data-ttu-id="0fd97-102">DOM’dan Düğümleri Kaldırma</span><span class="sxs-lookup"><span data-stu-id="0fd97-102">Removing Nodes from the DOM</span></span>
<span data-ttu-id="0fd97-103">XML Belge Nesne Modeli (DOM) bir düğümü kaldırmak için, belirli bir düğümü kaldırmak <xref:System.Xml.XmlNode.RemoveChild%2A> için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0fd97-103">To remove a node from the XML Document Object Model (DOM), use the <xref:System.Xml.XmlNode.RemoveChild%2A> method to remove a specific node.</span></span> <span data-ttu-id="0fd97-104">Bir düğümü kaldırdığınızda, yöntemi kaldırılan düğüme ait olan alt ağacı kaldırır; diğer bir deyişle, bir yaprak düğüm değildir.</span><span class="sxs-lookup"><span data-stu-id="0fd97-104">When you remove a node, the method removes the subtree belonging to the node being removed; that is, if it is not a leaf node.</span></span>  
  
 <span data-ttu-id="0fd97-105">DOM 'dan birden fazla düğümü kaldırmak için, geçerli düğümün <xref:System.Xml.XmlNode.RemoveAll%2A> varsa tüm alt öğeleri ve öznitelikleri kaldırmak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0fd97-105">To remove multiple nodes from the DOM, use the <xref:System.Xml.XmlNode.RemoveAll%2A> method to remove all the children and attributes, if applicable, of the current node.</span></span>  
  
 <span data-ttu-id="0fd97-106">İle çalışıyorsanız <xref:System.Xml.XmlNamedNodeMap>, <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> yöntemini kullanarak bir düğümü kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0fd97-106">If you are working with an <xref:System.Xml.XmlNamedNodeMap>, you can remove a node using the <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> method.</span></span>  
  
 <span data-ttu-id="0fd97-107">Öznitelikleri kaldırmak için bkz. [Dom 'daki bir öğe düğümünden öznitelikleri kaldırma](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="0fd97-107">To remove attributes, see [Removing Attributes from an Element Node in the DOM](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fd97-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0fd97-108">See also</span></span>

- [<span data-ttu-id="0fd97-109">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="0fd97-109">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
