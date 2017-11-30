---
title: "Boşluk ve DOM yüklenirken önemli boşluk işleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b141a0a-50d8-4ebd-83cd-a84449bb22b2
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 82401a18132801f9aa5368832b96be3cb67a8642
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="white-space-and-significant-white-space-handling-when-loading-the-dom"></a><span data-ttu-id="5cbec-102">Boşluk ve DOM yüklenirken önemli boşluk işleme</span><span class="sxs-lookup"><span data-stu-id="5cbec-102">White Space and Significant White Space Handling when Loading the DOM</span></span>
<span data-ttu-id="5cbec-103">Belge yüklenirken boşluk korumak ve oluşturmak için seçeneği ayarlayabilirsiniz **XmlWhitespace** belge ağacında düğümlerin.</span><span class="sxs-lookup"><span data-stu-id="5cbec-103">When loading the document, you can set the option to preserve white space and create **XmlWhitespace** nodes in the document tree.</span></span> <span data-ttu-id="5cbec-104">Beyaz alan düğümleri oluşturmak için **PreserveWhitespace** özelliğinin true.</span><span class="sxs-lookup"><span data-stu-id="5cbec-104">To create white space nodes, set the **PreserveWhitespace** property to true.</span></span> <span data-ttu-id="5cbec-105">Özellik ayarlanmışsa **yanlış**, varsayılan, boşluk düğümleri oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="5cbec-105">If the property is set to **false**, which is the default, white space nodes are not created.</span></span> <span data-ttu-id="5cbec-106">Her zaman önemli boşluk düğümleri korunur, ve **XmlSignificantWhitespace** düğümleri her zaman oluşturulan ayarından bağımsız olarak bu verileri temsil etmek için bellek **PreserveWhitespace** bayrak.</span><span class="sxs-lookup"><span data-stu-id="5cbec-106">Significant white spaces nodes are always preserved, and **XmlSignificantWhitespace** nodes are always created in memory to represent this data, regardless of the setting of the **PreserveWhitespace** flag.</span></span>  
  
 <span data-ttu-id="5cbec-107">Belge bir reader yüklerse, ardından ayarıyla **PreserveWhitespace** özelliği bayrak **XmlDocument** sınıfı etkiler oluşturulmasını **XmlWhitespace** düğümler yalnızca **WhitespaceHandling** özelliği **XmlTextReader** ayarlanmazsa **WhitespaceHandling.None**.</span><span class="sxs-lookup"><span data-stu-id="5cbec-107">If the document is loaded from a reader, then setting of the **PreserveWhitespace** flag property on the **XmlDocument** class affects the creation of **XmlWhitespace** nodes only when the **WhitespaceHandling** property on the **XmlTextReader** is not set to **WhitespaceHandling.None**.</span></span> <span data-ttu-id="5cbec-108">Bu değeri **WhitespaceHandling** bu bayrağı ayarı üzerinden önceliklidir üzerinde okuyucu özellikte **XmlDocument**.</span><span class="sxs-lookup"><span data-stu-id="5cbec-108">It is the value of the **WhitespaceHandling** property on the reader that takes precedence over the setting of that flag on the **XmlDocument**.</span></span> <span data-ttu-id="5cbec-109">Daha fazla bilgi için **XmlSignificantWhitespace**, bkz: <xref:System.Xml.XmlSignificantWhitespace>.</span><span class="sxs-lookup"><span data-stu-id="5cbec-109">For more information on **XmlSignificantWhitespace**, see <xref:System.Xml.XmlSignificantWhitespace>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cbec-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5cbec-110">See Also</span></span>  
 [<span data-ttu-id="5cbec-111">XML belge nesne modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="5cbec-111">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
