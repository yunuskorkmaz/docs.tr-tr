---
title: DOM düğümü içeriği kaldırma
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 615d81a7-f44f-416c-a9ab-bfe03f85e6e4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e4acbdb53b20c10362385b468c2eb13ab9b17eef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568517"
---
# <a name="removing-node-content-in-the-dom"></a><span data-ttu-id="463e5-102">DOM düğümü içeriği kaldırma</span><span class="sxs-lookup"><span data-stu-id="463e5-102">Removing Node Content in the DOM</span></span>
<span data-ttu-id="463e5-103">Devralınan düğüm türleri için <xref:System.Xml.XmlCharacterData>, hangi <xref:System.Xml.XmlComment>, <xref:System.Xml.XmlText>, <xref:System.Xml.XmlCDataSection>, <xref:System.Xml.XmlWhitespace>, ve <xref:System.Xml.XmlSignificantWhitespace> düğüm türlerini kullanarak karakterlerini kaldırabilirsiniz <xref:System.Xml.XmlCharacterData.DeleteData%2A> aralığını kaldırır yöntemi karakter düğümünden.</span><span class="sxs-lookup"><span data-stu-id="463e5-103">For node types that inherit from <xref:System.Xml.XmlCharacterData>, which are the <xref:System.Xml.XmlComment>, <xref:System.Xml.XmlText>, <xref:System.Xml.XmlCDataSection>, <xref:System.Xml.XmlWhitespace>, and <xref:System.Xml.XmlSignificantWhitespace> node types, you can remove characters using the <xref:System.Xml.XmlCharacterData.DeleteData%2A> method, which removes a range of characters from the node.</span></span> <span data-ttu-id="463e5-104">İçerik tamamen kaldırmak istiyorsanız, içeriğin bulunduğu düğümü kaldırın.</span><span class="sxs-lookup"><span data-stu-id="463e5-104">If you want to remove content completely, you remove the node that contains the content.</span></span> <span data-ttu-id="463e5-105">Düğüm tutmak istediğiniz, ancak içeriğin yanlış olduğundan, içeriği değiştirin.</span><span class="sxs-lookup"><span data-stu-id="463e5-105">If you want to keep the node, but the content is incorrect, then modify the content.</span></span> <span data-ttu-id="463e5-106">Bir düğümün içeriğini değiştirme hakkında daha fazla bilgi için bkz: [değiştirme düğümleri, içerik ve bir XML belgesi değerleri](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="463e5-106">For information on modifying the content of a node, see [Modifying Nodes, Content, and Values in an XML Document](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="463e5-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="463e5-107">See Also</span></span>  
 [<span data-ttu-id="463e5-108">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="463e5-108">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
