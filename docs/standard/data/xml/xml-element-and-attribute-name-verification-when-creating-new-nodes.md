---
title: "XML öğesi ve yeni düğümler oluştururken, öznitelik adı doğrulaması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b489f647-a175-4659-ada4-170058bb41d0
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 36b9761cefb1dba47c88d053773c89e4312dee9d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a><span data-ttu-id="598e5-102">XML öğesi ve yeni düğümler oluştururken, öznitelik adı doğrulaması</span><span class="sxs-lookup"><span data-stu-id="598e5-102">XML Element and Attribute Name Verification when Creating New Nodes</span></span>
<span data-ttu-id="598e5-103">XML belge nesne modeli (DOM) oluştururken yeni öğe düğüm veya öznitelik düğümleri adlarını geçerliliğini denetler.</span><span class="sxs-lookup"><span data-stu-id="598e5-103">The XML Document Object Model (DOM) checks the validity of the names when creating new element nodes or attribute nodes.</span></span> <span data-ttu-id="598e5-104">Adları geçersiz karakterler içeriyorsa, özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="598e5-104">If the names contain illegal characters, an exception is thrown.</span></span> <span data-ttu-id="598e5-105">Adları geçerli ve kodlanmış doğru, kullanmanız gereken emin olmak için **XmlConvert** adı kodlamak ve bir uygulama düzeyinde kod çözme sınıfı.</span><span class="sxs-lookup"><span data-stu-id="598e5-105">To ensure that names are valid and encoded correctly, you need to use the **XmlConvert** class to encode the name and decode it back at an application level.</span></span> <span data-ttu-id="598e5-106">**XmlWriter** doğru biçimlendirilmiş XML oluşturulduğundan emin olmak için ek bir iş yapmanıza yöntemlerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="598e5-106">The **XmlWriter** has methods that do additional work to ensure well-formed XML is generated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="598e5-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="598e5-107">See Also</span></span>  
 [<span data-ttu-id="598e5-108">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="598e5-108">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
