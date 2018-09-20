---
title: DOM yükleme, boşluk ve önemli boşluk işleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1b141a0a-50d8-4ebd-83cd-a84449bb22b2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1d9bbb14320b84a6d417c5c28026b169092de219
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46326419"
---
# <a name="white-space-and-significant-white-space-handling-when-loading-the-dom"></a><span data-ttu-id="310ad-102">DOM yükleme, boşluk ve önemli boşluk işleme</span><span class="sxs-lookup"><span data-stu-id="310ad-102">White Space and Significant White Space Handling when Loading the DOM</span></span>
<span data-ttu-id="310ad-103">Belge yüklenirken bölünemez boşluğu koruyacak ve oluşturmak için seçeneği ayarlayabilirsiniz **XmlWhitespace** belge ağacında düğümleri.</span><span class="sxs-lookup"><span data-stu-id="310ad-103">When loading the document, you can set the option to preserve white space and create **XmlWhitespace** nodes in the document tree.</span></span> <span data-ttu-id="310ad-104">Boşluk düğümleri oluşturmak için **PreserveWhitespace** özelliği true.</span><span class="sxs-lookup"><span data-stu-id="310ad-104">To create white space nodes, set the **PreserveWhitespace** property to true.</span></span> <span data-ttu-id="310ad-105">Özellik ayarlanmışsa **false**, varsayılan değer olan, boşluk düğümleri oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="310ad-105">If the property is set to **false**, which is the default, white space nodes are not created.</span></span> <span data-ttu-id="310ad-106">Her zaman önemli boşluk düğümleri korunur, ve **XmlSignificantWhitespace** düğümleri her zaman bellek ayarından bağımsız olarak bu verileri temsil etmek için oluşturulan **PreserveWhitespace** bayrak.</span><span class="sxs-lookup"><span data-stu-id="310ad-106">Significant white spaces nodes are always preserved, and **XmlSignificantWhitespace** nodes are always created in memory to represent this data, regardless of the setting of the **PreserveWhitespace** flag.</span></span>  
  
 <span data-ttu-id="310ad-107">Belge okuyucudan yüklenirse, ardından ayarıyla **PreserveWhitespace** özellik bayrağını **XmlDocument** sınıfı etkiler oluşturulmasını **XmlWhitespace** düğümleri yalnızca **WhitespaceHandling** özelliği **XmlTextReader** ayarlı değil **WhitespaceHandling.None**.</span><span class="sxs-lookup"><span data-stu-id="310ad-107">If the document is loaded from a reader, then setting of the **PreserveWhitespace** flag property on the **XmlDocument** class affects the creation of **XmlWhitespace** nodes only when the **WhitespaceHandling** property on the **XmlTextReader** is not set to **WhitespaceHandling.None**.</span></span> <span data-ttu-id="310ad-108">Bu değeri **WhitespaceHandling** bu bayrağının ayarını üzerinde önceliklidir üzerinde okuyucu özelliği **XmlDocument**.</span><span class="sxs-lookup"><span data-stu-id="310ad-108">It is the value of the **WhitespaceHandling** property on the reader that takes precedence over the setting of that flag on the **XmlDocument**.</span></span> <span data-ttu-id="310ad-109">Daha fazla bilgi için **XmlSignificantWhitespace**, bkz: <xref:System.Xml.XmlSignificantWhitespace>.</span><span class="sxs-lookup"><span data-stu-id="310ad-109">For more information on **XmlSignificantWhitespace**, see <xref:System.Xml.XmlSignificantWhitespace>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="310ad-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="310ad-110">See also</span></span>

- [<span data-ttu-id="310ad-111">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="310ad-111">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
