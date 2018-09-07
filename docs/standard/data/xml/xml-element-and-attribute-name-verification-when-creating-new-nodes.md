---
title: XML öğesi ve yeni düğümler oluştururken öznitelik adı doğrulaması
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: b489f647-a175-4659-ada4-170058bb41d0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 008cf14e63b8458feebf26eaf27be516bb79f933
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44070325"
---
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a>XML öğesi ve yeni düğümler oluştururken öznitelik adı doğrulaması
Yeni Öğe düğümlerinin veya öznitelik düğümleri oluşturulurken, XML belge nesne modeli (DOM) adlarını geçerliliğini denetler. Ad geçersiz karakterler içeriyorsa bir özel durum oluşturulur. Adları geçerli ve kodlanmış doğru, kullanmanız gereken emin olmak için **XmlConvert** adı kodlama ve bir uygulama düzeyinde çözülmesi için sınıf. **XmlWriter** doğru biçimlendirilmiş XML oluşturulan emin olmak için ek iş yapması yöntemlerine sahiptir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
