---
title: XML öğesi ve yeni düğümler oluştururken öznitelik adı doğrulaması
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: b489f647-a175-4659-ada4-170058bb41d0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 008cf14e63b8458feebf26eaf27be516bb79f933
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44216047"
---
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a><span data-ttu-id="9834d-102">XML öğesi ve yeni düğümler oluştururken öznitelik adı doğrulaması</span><span class="sxs-lookup"><span data-stu-id="9834d-102">XML Element and Attribute Name Verification when Creating New Nodes</span></span>
<span data-ttu-id="9834d-103">Yeni Öğe düğümlerinin veya öznitelik düğümleri oluşturulurken, XML belge nesne modeli (DOM) adlarını geçerliliğini denetler.</span><span class="sxs-lookup"><span data-stu-id="9834d-103">The XML Document Object Model (DOM) checks the validity of the names when creating new element nodes or attribute nodes.</span></span> <span data-ttu-id="9834d-104">Ad geçersiz karakterler içeriyorsa bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9834d-104">If the names contain illegal characters, an exception is thrown.</span></span> <span data-ttu-id="9834d-105">Adları geçerli ve kodlanmış doğru, kullanmanız gereken emin olmak için **XmlConvert** adı kodlama ve bir uygulama düzeyinde çözülmesi için sınıf.</span><span class="sxs-lookup"><span data-stu-id="9834d-105">To ensure that names are valid and encoded correctly, you need to use the **XmlConvert** class to encode the name and decode it back at an application level.</span></span> <span data-ttu-id="9834d-106">**XmlWriter** doğru biçimlendirilmiş XML oluşturulan emin olmak için ek iş yapması yöntemlerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="9834d-106">The **XmlWriter** has methods that do additional work to ensure well-formed XML is generated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9834d-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9834d-107">See also</span></span>

- [<span data-ttu-id="9834d-108">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="9834d-108">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
