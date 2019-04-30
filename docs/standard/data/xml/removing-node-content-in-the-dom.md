---
title: DOM’daki Düğüm İçeriğini Kaldırma
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 615d81a7-f44f-416c-a9ab-bfe03f85e6e4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 737766586ee920a87c25dd42896bdfb14ae69d98
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698713"
---
# <a name="removing-node-content-in-the-dom"></a><span data-ttu-id="aafdf-102">DOM’daki Düğüm İçeriğini Kaldırma</span><span class="sxs-lookup"><span data-stu-id="aafdf-102">Removing Node Content in the DOM</span></span>
<span data-ttu-id="aafdf-103">Devralınan düğüm türleri için <xref:System.Xml.XmlCharacterData>, hangi <xref:System.Xml.XmlComment>, <xref:System.Xml.XmlText>, <xref:System.Xml.XmlCDataSection>, <xref:System.Xml.XmlWhitespace>, ve <xref:System.Xml.XmlSignificantWhitespace> düğüm türlerini kullanarak karakterler kaldırabilirsiniz <xref:System.Xml.XmlCharacterData.DeleteData%2A> çeşitli kaldıran yöntemi düğümünden karakter.</span><span class="sxs-lookup"><span data-stu-id="aafdf-103">For node types that inherit from <xref:System.Xml.XmlCharacterData>, which are the <xref:System.Xml.XmlComment>, <xref:System.Xml.XmlText>, <xref:System.Xml.XmlCDataSection>, <xref:System.Xml.XmlWhitespace>, and <xref:System.Xml.XmlSignificantWhitespace> node types, you can remove characters using the <xref:System.Xml.XmlCharacterData.DeleteData%2A> method, which removes a range of characters from the node.</span></span> <span data-ttu-id="aafdf-104">İçeriği tamamen kaldırmak istiyorsanız, içeriğin bulunduğu düğümü kaldırın.</span><span class="sxs-lookup"><span data-stu-id="aafdf-104">If you want to remove content completely, you remove the node that contains the content.</span></span> <span data-ttu-id="aafdf-105">Ardından düğümü tutmak istediğiniz, ancak içerik yanlış, içeriği değiştirin.</span><span class="sxs-lookup"><span data-stu-id="aafdf-105">If you want to keep the node, but the content is incorrect, then modify the content.</span></span> <span data-ttu-id="aafdf-106">Bir düğüm içeriğini değiştirme hakkında daha fazla bilgi için bkz: [değiştirme düğümleri, içeriği ve değerleri bir XML belgesi](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="aafdf-106">For information on modifying the content of a node, see [Modifying Nodes, Content, and Values in an XML Document](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aafdf-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aafdf-107">See also</span></span>

- [<span data-ttu-id="aafdf-108">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="aafdf-108">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
