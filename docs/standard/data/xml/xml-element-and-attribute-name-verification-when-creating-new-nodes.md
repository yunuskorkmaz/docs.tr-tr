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
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 36b9761cefb1dba47c88d053773c89e4312dee9d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a>XML öğesi ve yeni düğümler oluştururken, öznitelik adı doğrulaması
XML belge nesne modeli (DOM) oluştururken yeni öğe düğüm veya öznitelik düğümleri adlarını geçerliliğini denetler. Adları geçersiz karakterler içeriyorsa, özel durum oluşur. Adları geçerli ve kodlanmış doğru, kullanmanız gereken emin olmak için **XmlConvert** adı kodlamak ve bir uygulama düzeyinde kod çözme sınıfı. **XmlWriter** doğru biçimlendirilmiş XML oluşturulduğundan emin olmak için ek bir iş yapmanıza yöntemlerine sahiptir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
