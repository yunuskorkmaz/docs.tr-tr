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
ms.openlocfilehash: c041d5d2830222f3fae09a39f1ea10eb08772388
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a><span data-ttu-id="2d294-102">XML öğesi ve yeni düğümler oluştururken, öznitelik adı doğrulaması</span><span class="sxs-lookup"><span data-stu-id="2d294-102">XML Element and Attribute Name Verification when Creating New Nodes</span></span>
<span data-ttu-id="2d294-103">XML belge nesne modeli (DOM) oluştururken yeni öğe düğüm veya öznitelik düğümleri adlarını geçerliliğini denetler.</span><span class="sxs-lookup"><span data-stu-id="2d294-103">The XML Document Object Model (DOM) checks the validity of the names when creating new element nodes or attribute nodes.</span></span> <span data-ttu-id="2d294-104">Adları geçersiz karakterler içeriyorsa, özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="2d294-104">If the names contain illegal characters, an exception is thrown.</span></span> <span data-ttu-id="2d294-105">Adları geçerli ve kodlanmış doğru, kullanmanız gereken emin olmak için **XmlConvert** adı kodlamak ve bir uygulama düzeyinde kod çözme sınıfı.</span><span class="sxs-lookup"><span data-stu-id="2d294-105">To ensure that names are valid and encoded correctly, you need to use the **XmlConvert** class to encode the name and decode it back at an application level.</span></span> <span data-ttu-id="2d294-106">**XmlWriter** doğru biçimlendirilmiş XML oluşturulduğundan emin olmak için ek bir iş yapmanıza yöntemlerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="2d294-106">The **XmlWriter** has methods that do additional work to ensure well-formed XML is generated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d294-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2d294-107">See Also</span></span>  
 [<span data-ttu-id="2d294-108">XML belge nesne modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="2d294-108">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
