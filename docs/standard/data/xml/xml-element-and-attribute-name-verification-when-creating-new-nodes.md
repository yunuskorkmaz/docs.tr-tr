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
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a>Yeni Düğümler Oluştururken XML Öğesi ve Öznitelik Adı Doğrulaması

XML Belge Nesne Modeli (DOM), yeni öğe düğümleri veya öznitelik düğümleri oluştururken adların geçerliliğini denetler. Adlar geçersiz karakterler içeriyorsa, bir özel durum oluşturulur. Adların geçerli ve doğru şekilde kodlandığından emin olmak için, adı kodlamak ve uygulama düzeyinde geri yüklemek için **XmlConvert** sınıfını kullanmanız gerekir. **XmlWriter** 'ın ıyı biçimlendirilmiş XML 'nin oluşturulduğundan emin olmak için ek iş yapan yöntemleri vardır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](xml-document-object-model-dom.md)
