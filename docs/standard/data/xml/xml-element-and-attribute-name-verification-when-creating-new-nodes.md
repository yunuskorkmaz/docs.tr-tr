---
title: XML öğesi ve yeni düğümler oluştururken, öznitelik adı doğrulaması
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: b489f647-a175-4659-ada4-170058bb41d0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: de11c190310dec90bd23d044f77d0c38e3a34fcf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568855"
---
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a><span data-ttu-id="ea6c5-102">XML öğesi ve yeni düğümler oluştururken, öznitelik adı doğrulaması</span><span class="sxs-lookup"><span data-stu-id="ea6c5-102">XML Element and Attribute Name Verification when Creating New Nodes</span></span>
<span data-ttu-id="ea6c5-103">XML belge nesne modeli (DOM) oluştururken yeni öğe düğüm veya öznitelik düğümleri adlarını geçerliliğini denetler.</span><span class="sxs-lookup"><span data-stu-id="ea6c5-103">The XML Document Object Model (DOM) checks the validity of the names when creating new element nodes or attribute nodes.</span></span> <span data-ttu-id="ea6c5-104">Adları geçersiz karakterler içeriyorsa, özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="ea6c5-104">If the names contain illegal characters, an exception is thrown.</span></span> <span data-ttu-id="ea6c5-105">Adları geçerli ve kodlanmış doğru, kullanmanız gereken emin olmak için **XmlConvert** adı kodlamak ve bir uygulama düzeyinde kod çözme sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ea6c5-105">To ensure that names are valid and encoded correctly, you need to use the **XmlConvert** class to encode the name and decode it back at an application level.</span></span> <span data-ttu-id="ea6c5-106">**XmlWriter** doğru biçimlendirilmiş XML oluşturulduğundan emin olmak için ek bir iş yapmanıza yöntemlerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ea6c5-106">The **XmlWriter** has methods that do additional work to ensure well-formed XML is generated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea6c5-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ea6c5-107">See Also</span></span>  
 [<span data-ttu-id="ea6c5-108">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="ea6c5-108">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
