---
title: Yeni Düğümler Oluştururken XML Öğesi ve Öznitelik Adı Doğrulaması
ms.date: 03/30/2017
ms.assetid: b489f647-a175-4659-ada4-170058bb41d0
ms.openlocfilehash: 0678f7daf5276a905ce890a5f6a0f64993fb08b0
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828823"
---
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a><span data-ttu-id="3695a-102">Yeni Düğümler Oluştururken XML Öğesi ve Öznitelik Adı Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="3695a-102">XML Element and Attribute Name Verification when Creating New Nodes</span></span>
<span data-ttu-id="3695a-103">XML Belge Nesne Modeli (DOM), yeni öğe düğümleri veya öznitelik düğümleri oluştururken adların geçerliliğini denetler.</span><span class="sxs-lookup"><span data-stu-id="3695a-103">The XML Document Object Model (DOM) checks the validity of the names when creating new element nodes or attribute nodes.</span></span> <span data-ttu-id="3695a-104">Adlar geçersiz karakterler içeriyorsa, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3695a-104">If the names contain illegal characters, an exception is thrown.</span></span> <span data-ttu-id="3695a-105">Adların geçerli ve doğru şekilde kodlandığından emin olmak için, adı kodlamak ve uygulama düzeyinde geri yüklemek için **XmlConvert** sınıfını kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3695a-105">To ensure that names are valid and encoded correctly, you need to use the **XmlConvert** class to encode the name and decode it back at an application level.</span></span> <span data-ttu-id="3695a-106">**XmlWriter** 'ın ıyı biçimlendirilmiş XML 'nin oluşturulduğundan emin olmak için ek iş yapan yöntemleri vardır.</span><span class="sxs-lookup"><span data-stu-id="3695a-106">The **XmlWriter** has methods that do additional work to ensure well-formed XML is generated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3695a-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3695a-107">See also</span></span>

- [<span data-ttu-id="3695a-108">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="3695a-108">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
