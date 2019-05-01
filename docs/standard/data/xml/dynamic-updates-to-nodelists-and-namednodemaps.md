---
title: NodeLists ve NamedNodeMaps Dinamik Güncelleştirmeleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 76c511fd-6704-4ca4-8078-860a68d898ad
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9f56ba8711988f2f7d743dc4ff7b69272e2642a2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934478"
---
# <a name="dynamic-updates-to-nodelists-and-namednodemaps"></a>NodeLists ve NamedNodeMaps Dinamik Güncelleştirmeleri
Çünkü **XmlNodeList** ve **XmlNamedNodeMap** XML belgesi belleğe yüklenir ve değiştirilmekte olduğundan, henüz bir dizi düğümü, içeren bildiren World Wide Web Consortium (W3C) bu nesneler dinamik olarak düğüm gereksinim kümesini içerir. Temel alınan belge değişirse, diğer bir deyişle, sonra bu iki nesne verileri de değiştirmeniz gerekir. Bu nedenle, varsa bir **XmlNodeList** (örneğin, X öğesi) belirli bir öğenin tüm alt öğelerini içeren ve ardından ek bir öğe, öğe Q, belgenin X öğesinin altına ekleyin. **XmlNodeList** o yeni öğe kendi koleksiyonuna eklediğiniz soru da olmalıdır. Aynı durum geçerlidir ters. Bir düğüm eklenirse **XmlNodeList**, temel alınan belge de güncelleştirilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
