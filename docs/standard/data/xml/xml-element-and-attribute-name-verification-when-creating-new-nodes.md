---
title: Yeni Düğümler Oluştururken XML Öğesi ve Öznitelik Adı Doğrulaması
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: b489f647-a175-4659-ada4-170058bb41d0
ms.openlocfilehash: 7c99ffa9d139d94d26c562cb1668f1b855bed32d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709952"
---
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a>Yeni Düğümler Oluştururken XML Öğesi ve Öznitelik Adı Doğrulaması
XML Belge Nesne Modeli (DOM), yeni öğe düğümleri veya öznitelik düğümleri oluştururken adların geçerliliğini denetler. Adlar geçersiz karakterler içeriyorsa, bir özel durum oluşturulur. Adların geçerli ve doğru şekilde kodlandığından emin olmak için, adı kodlamak ve uygulama düzeyinde geri yüklemek için **XmlConvert** sınıfını kullanmanız gerekir. **XmlWriter** 'ın ıyı biçimlendirilmiş XML 'nin oluşturulduğundan emin olmak için ek iş yapan yöntemleri vardır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
