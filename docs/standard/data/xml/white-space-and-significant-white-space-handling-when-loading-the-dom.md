---
title: DOM Yüklerken Boşluk ve Önemli Boşluk İşleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1b141a0a-50d8-4ebd-83cd-a84449bb22b2
ms.openlocfilehash: 834644a07d790401a1131d6d901f144ef90dc495
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710030"
---
# <a name="white-space-and-significant-white-space-handling-when-loading-the-dom"></a><span data-ttu-id="97a28-102">DOM Yüklerken Boşluk ve Önemli Boşluk İşleme</span><span class="sxs-lookup"><span data-stu-id="97a28-102">White Space and Significant White Space Handling when Loading the DOM</span></span>
<span data-ttu-id="97a28-103">Belge yüklenirken, boşluk koruma ve belge ağacında **XmlWhitespace** düğümleri oluşturma seçeneğini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97a28-103">When loading the document, you can set the option to preserve white space and create **XmlWhitespace** nodes in the document tree.</span></span> <span data-ttu-id="97a28-104">Boşluk düğümleri oluşturmak için **PreserveWhitespace** özelliğini true olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="97a28-104">To create white space nodes, set the **PreserveWhitespace** property to true.</span></span> <span data-ttu-id="97a28-105">Özelliği **false**olarak ayarlandıysa, varsayılan değer olan boşluk düğümleri oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="97a28-105">If the property is set to **false**, which is the default, white space nodes are not created.</span></span> <span data-ttu-id="97a28-106">Önemli beyaz alanlar düğümleri her zaman korunur ve **XmlSignificantWhitespace** düğümleri her zaman bu verileri temsil etmek Için, **PreserveWhitespace** bayrağının ayarından bağımsız olarak her zaman bellekte oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="97a28-106">Significant white spaces nodes are always preserved, and **XmlSignificantWhitespace** nodes are always created in memory to represent this data, regardless of the setting of the **PreserveWhitespace** flag.</span></span>  
  
 <span data-ttu-id="97a28-107">Belge bir okuyucudan yüklenirse, **XmlDocument** sınıfında **PreserveWhitespace** bayrak özelliğinin ayarlanması yalnızca **XmlTextReader** üzerinde **WhitespaceHandling** özelliği **WhitespaceHandling. None**olarak ayarlanmamışsa **XmlWhitespace** düğümlerinin oluşturulmasını etkiler.</span><span class="sxs-lookup"><span data-stu-id="97a28-107">If the document is loaded from a reader, then setting of the **PreserveWhitespace** flag property on the **XmlDocument** class affects the creation of **XmlWhitespace** nodes only when the **WhitespaceHandling** property on the **XmlTextReader** is not set to **WhitespaceHandling.None**.</span></span> <span data-ttu-id="97a28-108">Bu, okuyucudaki **WhitespaceHandling** özelliğinin değeridir. Bu, **XmlDocument**üzerindeki bu bayrağın ayarından önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="97a28-108">It is the value of the **WhitespaceHandling** property on the reader that takes precedence over the setting of that flag on the **XmlDocument**.</span></span> <span data-ttu-id="97a28-109">**XmlSignificantWhitespace**hakkında daha fazla bilgi için bkz <xref:System.Xml.XmlSignificantWhitespace>..</span><span class="sxs-lookup"><span data-stu-id="97a28-109">For more information on **XmlSignificantWhitespace**, see <xref:System.Xml.XmlSignificantWhitespace>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97a28-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="97a28-110">See also</span></span>

- [<span data-ttu-id="97a28-111">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="97a28-111">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
