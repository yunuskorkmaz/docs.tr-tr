---
title: DOM’daki Düğüm İçeriğini Kaldırma
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 615d81a7-f44f-416c-a9ab-bfe03f85e6e4
ms.openlocfilehash: f5086bdea8ff1f0ee5329f347223ebb4a6bd71da
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710342"
---
# <a name="removing-node-content-in-the-dom"></a><span data-ttu-id="b236f-102">DOM’daki Düğüm İçeriğini Kaldırma</span><span class="sxs-lookup"><span data-stu-id="b236f-102">Removing Node Content in the DOM</span></span>
<span data-ttu-id="b236f-103"><xref:System.Xml.XmlComment>, <xref:System.Xml.XmlText> <xref:System.Xml.XmlSignificantWhitespace> <xref:System.Xml.XmlCharacterData.DeleteData%2A> <xref:System.Xml.XmlCharacterData> <xref:System.Xml.XmlCDataSection>,, <xref:System.Xml.XmlWhitespace>, Ve düğüm türleri olan öğesinden devraldığı düğüm türleri için, düğümünden bir karakter aralığını kaldıran yöntemini kullanarak karakterleri kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b236f-103">For node types that inherit from <xref:System.Xml.XmlCharacterData>, which are the <xref:System.Xml.XmlComment>, <xref:System.Xml.XmlText>, <xref:System.Xml.XmlCDataSection>, <xref:System.Xml.XmlWhitespace>, and <xref:System.Xml.XmlSignificantWhitespace> node types, you can remove characters using the <xref:System.Xml.XmlCharacterData.DeleteData%2A> method, which removes a range of characters from the node.</span></span> <span data-ttu-id="b236f-104">İçeriği tamamen kaldırmak istiyorsanız, içeriği içeren düğümü kaldırırsınız.</span><span class="sxs-lookup"><span data-stu-id="b236f-104">If you want to remove content completely, you remove the node that contains the content.</span></span> <span data-ttu-id="b236f-105">Düğümü korumak istiyorsanız, ancak içerik yanlış ise içeriği değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b236f-105">If you want to keep the node, but the content is incorrect, then modify the content.</span></span> <span data-ttu-id="b236f-106">Bir düğümün içeriğini değiştirme hakkında daha fazla bilgi için bkz. [BIR XML belgesindeki düğümleri, içeriği ve değerleri değiştirme](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="b236f-106">For information on modifying the content of a node, see [Modifying Nodes, Content, and Values in an XML Document](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b236f-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b236f-107">See also</span></span>

- [<span data-ttu-id="b236f-108">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="b236f-108">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
