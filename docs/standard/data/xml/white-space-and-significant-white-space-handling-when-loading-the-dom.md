---
description: 'Daha fazla bilgi edinin: DOM yüklenirken boşluk ve önemli boşluk Işleme'
title: DOM Yüklerken Boşluk ve Önemli Boşluk İşleme
ms.date: 03/30/2017
ms.assetid: 1b141a0a-50d8-4ebd-83cd-a84449bb22b2
ms.openlocfilehash: b863f5921bf3e9e3da9489d02a7bd09d25f38c7d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782825"
---
# <a name="white-space-and-significant-white-space-handling-when-loading-the-dom"></a><span data-ttu-id="3df45-103">DOM Yüklerken Boşluk ve Önemli Boşluk İşleme</span><span class="sxs-lookup"><span data-stu-id="3df45-103">White Space and Significant White Space Handling when Loading the DOM</span></span>

<span data-ttu-id="3df45-104">Belge yüklenirken, boşluk koruma ve belge ağacında **XmlWhitespace** düğümleri oluşturma seçeneğini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3df45-104">When loading the document, you can set the option to preserve white space and create **XmlWhitespace** nodes in the document tree.</span></span> <span data-ttu-id="3df45-105">Boşluk düğümleri oluşturmak için **PreserveWhitespace** özelliğini true olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="3df45-105">To create white space nodes, set the **PreserveWhitespace** property to true.</span></span> <span data-ttu-id="3df45-106">Özelliği **false** olarak ayarlandıysa, varsayılan değer olan boşluk düğümleri oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="3df45-106">If the property is set to **false**, which is the default, white space nodes are not created.</span></span> <span data-ttu-id="3df45-107">Önemli beyaz alanlar düğümleri her zaman korunur ve **XmlSignificantWhitespace** düğümleri her zaman bu verileri temsil etmek Için, **PreserveWhitespace** bayrağının ayarından bağımsız olarak her zaman bellekte oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3df45-107">Significant white spaces nodes are always preserved, and **XmlSignificantWhitespace** nodes are always created in memory to represent this data, regardless of the setting of the **PreserveWhitespace** flag.</span></span>  
  
 <span data-ttu-id="3df45-108">Belge bir okuyucudan yüklenirse, **XmlDocument** sınıfında **PreserveWhitespace** bayrak özelliğinin ayarlanması yalnızca **XmlTextReader** üzerinde **WhitespaceHandling** özelliği **WhitespaceHandling. None** olarak ayarlanmamışsa **XmlWhitespace** düğümlerinin oluşturulmasını etkiler.</span><span class="sxs-lookup"><span data-stu-id="3df45-108">If the document is loaded from a reader, then setting of the **PreserveWhitespace** flag property on the **XmlDocument** class affects the creation of **XmlWhitespace** nodes only when the **WhitespaceHandling** property on the **XmlTextReader** is not set to **WhitespaceHandling.None**.</span></span> <span data-ttu-id="3df45-109">Bu, okuyucudaki **WhitespaceHandling** özelliğinin değeridir. Bu, **XmlDocument** üzerindeki bu bayrağın ayarından önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="3df45-109">It is the value of the **WhitespaceHandling** property on the reader that takes precedence over the setting of that flag on the **XmlDocument**.</span></span> <span data-ttu-id="3df45-110">**XmlSignificantWhitespace** hakkında daha fazla bilgi için bkz <xref:System.Xml.XmlSignificantWhitespace> ..</span><span class="sxs-lookup"><span data-stu-id="3df45-110">For more information on **XmlSignificantWhitespace**, see <xref:System.Xml.XmlSignificantWhitespace>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3df45-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3df45-111">See also</span></span>

- [<span data-ttu-id="3df45-112">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="3df45-112">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
