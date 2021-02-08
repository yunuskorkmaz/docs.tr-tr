---
description: 'Daha fazla bilgi edinin: yeni düğümler oluştururken XML öğesi ve öznitelik adı doğrulama'
title: Yeni Düğümler Oluştururken XML Öğesi ve Öznitelik Adı Doğrulaması
ms.date: 03/30/2017
ms.assetid: b489f647-a175-4659-ada4-170058bb41d0
ms.openlocfilehash: 07b878424df57c34c5dc2b614fdff9a5dcef26bf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782721"
---
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a><span data-ttu-id="1b022-103">Yeni Düğümler Oluştururken XML Öğesi ve Öznitelik Adı Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="1b022-103">XML Element and Attribute Name Verification when Creating New Nodes</span></span>

<span data-ttu-id="1b022-104">XML Belge Nesne Modeli (DOM), yeni öğe düğümleri veya öznitelik düğümleri oluştururken adların geçerliliğini denetler.</span><span class="sxs-lookup"><span data-stu-id="1b022-104">The XML Document Object Model (DOM) checks the validity of the names when creating new element nodes or attribute nodes.</span></span> <span data-ttu-id="1b022-105">Adlar geçersiz karakterler içeriyorsa, bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1b022-105">If the names contain illegal characters, an exception is thrown.</span></span> <span data-ttu-id="1b022-106">Adların geçerli ve doğru şekilde kodlandığından emin olmak için, adı kodlamak ve uygulama düzeyinde geri yüklemek için **XmlConvert** sınıfını kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1b022-106">To ensure that names are valid and encoded correctly, you need to use the **XmlConvert** class to encode the name and decode it back at an application level.</span></span> <span data-ttu-id="1b022-107">**XmlWriter** 'ın ıyı biçimlendirilmiş XML 'nin oluşturulduğundan emin olmak için ek iş yapan yöntemleri vardır.</span><span class="sxs-lookup"><span data-stu-id="1b022-107">The **XmlWriter** has methods that do additional work to ensure well-formed XML is generated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b022-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1b022-108">See also</span></span>

- [<span data-ttu-id="1b022-109">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="1b022-109">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
