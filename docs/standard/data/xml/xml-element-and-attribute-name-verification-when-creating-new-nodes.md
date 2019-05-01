---
title: Yeni Düğümler Oluştururken XML Öğesi ve Öznitelik Adı Doğrulaması
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: b489f647-a175-4659-ada4-170058bb41d0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 008cf14e63b8458feebf26eaf27be516bb79f933
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61959050"
---
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a><span data-ttu-id="a7a44-102">Yeni Düğümler Oluştururken XML Öğesi ve Öznitelik Adı Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="a7a44-102">XML Element and Attribute Name Verification when Creating New Nodes</span></span>
<span data-ttu-id="a7a44-103">Yeni Öğe düğümlerinin veya öznitelik düğümleri oluşturulurken, XML belge nesne modeli (DOM) adlarını geçerliliğini denetler.</span><span class="sxs-lookup"><span data-stu-id="a7a44-103">The XML Document Object Model (DOM) checks the validity of the names when creating new element nodes or attribute nodes.</span></span> <span data-ttu-id="a7a44-104">Ad geçersiz karakterler içeriyorsa bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a7a44-104">If the names contain illegal characters, an exception is thrown.</span></span> <span data-ttu-id="a7a44-105">Adları geçerli ve kodlanmış doğru, kullanmanız gereken emin olmak için **XmlConvert** adı kodlama ve bir uygulama düzeyinde çözülmesi için sınıf.</span><span class="sxs-lookup"><span data-stu-id="a7a44-105">To ensure that names are valid and encoded correctly, you need to use the **XmlConvert** class to encode the name and decode it back at an application level.</span></span> <span data-ttu-id="a7a44-106">**XmlWriter** doğru biçimlendirilmiş XML oluşturulan emin olmak için ek iş yapması yöntemlerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a7a44-106">The **XmlWriter** has methods that do additional work to ensure well-formed XML is generated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7a44-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7a44-107">See also</span></span>

- [<span data-ttu-id="a7a44-108">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="a7a44-108">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
