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
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a>XML öğesi ve yeni düğümler oluştururken, öznitelik adı doğrulaması
XML belge nesne modeli (DOM) oluştururken yeni öğe düğüm veya öznitelik düğümleri adlarını geçerliliğini denetler. Adları geçersiz karakterler içeriyorsa, özel durum oluşur. Adları geçerli ve kodlanmış doğru, kullanmanız gereken emin olmak için **XmlConvert** adı kodlamak ve bir uygulama düzeyinde kod çözme sınıfı. **XmlWriter** doğru biçimlendirilmiş XML oluşturulduğundan emin olmak için ek bir iş yapmanıza yöntemlerine sahiptir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML belge nesne modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
