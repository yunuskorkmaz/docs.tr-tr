---
title: Dinamik güncelleştirmeleri NodeLists ve NamedNodeMaps
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 76c511fd-6704-4ca4-8078-860a68d898ad
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1de133d0208f1b86ad3240cdc00d8016af0a160c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="dynamic-updates-to-nodelists-and-namednodemaps"></a>Dinamik güncelleştirmeleri NodeLists ve NamedNodeMaps
Çünkü **XmlNodeList** ve **XmlNamedNodeMap** XML belgesi belleğe yüklenir ve değiştirilmekte olduğundan, henüz bir düğüm kümesini içeren World Wide Web Konsorsiyumu (W3C) bildiren bu nesneler Bu düğümler dinamik olarak gerek kümesi içerir. Temel alınan belge değişirse, diğer bir deyişle, ardından bu iki nesne verileri aynı zamanda değiştirmeniz gerekir. Bu nedenle, varsa bir **XmlNodeList** belirli bir öğenin (örneğin, X öğesi) tüm alt öğelerini içeren ve ardından ek öğe, belgenin öğesi X altında Q, öğesine ekleyin. **XmlNodeList** bu yeni bir öğesi kendi koleksiyonuna eklenen Q de olmalıdır. Aynı durum geçerlidir ters. Bir düğüm eklenirse **XmlNodeList**, temel alınan belge de güncelleştirilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
