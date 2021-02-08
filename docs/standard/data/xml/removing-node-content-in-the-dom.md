---
description: "Daha fazla bilgi edinin: DOM 'daki düğüm Içeriğini kaldırma"
title: DOM’daki Düğüm İçeriğini Kaldırma
ms.date: 03/30/2017
ms.assetid: 615d81a7-f44f-416c-a9ab-bfe03f85e6e4
ms.openlocfilehash: 44f8e0ee63ae8317d6b19558829ff3b676867845
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783124"
---
# <a name="removing-node-content-in-the-dom"></a><span data-ttu-id="de7cf-103">DOM’daki Düğüm İçeriğini Kaldırma</span><span class="sxs-lookup"><span data-stu-id="de7cf-103">Removing Node Content in the DOM</span></span>

<span data-ttu-id="de7cf-104">,,,, Ve düğüm türleri olan öğesinden devraldığı düğüm türleri için, <xref:System.Xml.XmlCharacterData> <xref:System.Xml.XmlComment> <xref:System.Xml.XmlText> <xref:System.Xml.XmlCDataSection> <xref:System.Xml.XmlWhitespace> <xref:System.Xml.XmlSignificantWhitespace> <xref:System.Xml.XmlCharacterData.DeleteData%2A> düğümünden bir karakter aralığını kaldıran yöntemini kullanarak karakterleri kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="de7cf-104">For node types that inherit from <xref:System.Xml.XmlCharacterData>, which are the <xref:System.Xml.XmlComment>, <xref:System.Xml.XmlText>, <xref:System.Xml.XmlCDataSection>, <xref:System.Xml.XmlWhitespace>, and <xref:System.Xml.XmlSignificantWhitespace> node types, you can remove characters using the <xref:System.Xml.XmlCharacterData.DeleteData%2A> method, which removes a range of characters from the node.</span></span> <span data-ttu-id="de7cf-105">İçeriği tamamen kaldırmak istiyorsanız, içeriği içeren düğümü kaldırırsınız.</span><span class="sxs-lookup"><span data-stu-id="de7cf-105">If you want to remove content completely, you remove the node that contains the content.</span></span> <span data-ttu-id="de7cf-106">Düğümü korumak istiyorsanız, ancak içerik yanlış ise içeriği değiştirin.</span><span class="sxs-lookup"><span data-stu-id="de7cf-106">If you want to keep the node, but the content is incorrect, then modify the content.</span></span> <span data-ttu-id="de7cf-107">Bir düğümün içeriğini değiştirme hakkında daha fazla bilgi için bkz. [BIR XML belgesindeki düğümleri, içeriği ve değerleri değiştirme](modifying-nodes-content-and-values-in-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="de7cf-107">For information on modifying the content of a node, see [Modifying Nodes, Content, and Values in an XML Document](modifying-nodes-content-and-values-in-an-xml-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de7cf-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="de7cf-108">See also</span></span>

- [<span data-ttu-id="de7cf-109">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="de7cf-109">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
