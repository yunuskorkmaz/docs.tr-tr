---
title: "Dinamik güncelleştirmeleri NodeLists ve NamedNodeMaps"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76c511fd-6704-4ca4-8078-860a68d898ad
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8a7abbb7344530ca993b8d07b774da17e6d0349b
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="dynamic-updates-to-nodelists-and-namednodemaps"></a>Dinamik güncelleştirmeleri NodeLists ve NamedNodeMaps
Çünkü **XmlNodeList** ve **XmlNamedNodeMap** XML belgesi belleğe yüklenir ve değiştirilmekte olduğundan, henüz bir düğüm kümesini içeren World Wide Web Konsorsiyumu (W3C) bildiren bu nesneler Bu düğümler dinamik olarak gerek kümesi içerir. Temel alınan belge değişirse, diğer bir deyişle, ardından bu iki nesne verileri aynı zamanda değiştirmeniz gerekir. Bu nedenle, varsa bir **XmlNodeList** belirli bir öğenin (örneğin, X öğesi) tüm alt öğelerini içeren ve ardından ek öğe, belgenin öğesi X altında Q, öğesine ekleyin. **XmlNodeList** bu yeni bir öğesi kendi koleksiyonuna eklenen Q de olmalıdır. Aynı durum geçerlidir ters. Bir düğüm eklenirse **XmlNodeList**, temel alınan belge de güncelleştirilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
