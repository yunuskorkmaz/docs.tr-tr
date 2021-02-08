---
description: 'Daha fazla bilgi edinin: NodeLists ve NamedNodeMaps için dinamik güncelleştirmeler'
title: NodeLists ve NamedNodeMaps Dinamik Güncelleştirmeleri
ms.date: 03/30/2017
ms.assetid: 76c511fd-6704-4ca4-8078-860a68d898ad
ms.openlocfilehash: 4e4b88d0e084e32fdb27f3d5762e305a4e900f1e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783384"
---
# <a name="dynamic-updates-to-nodelists-and-namednodemaps"></a>NodeLists ve NamedNodeMaps Dinamik Güncelleştirmeleri

**XmlNodeList** ve **XmlNamedNodeMap** bir düğüm kümesi içerdiğinden, XML belgesi belleğe yüklenmiş ve değiştirilmekte olduğundan, World Wide Web Konsorsiyumu (W3C) düğüm kümelerini içeren bu nesnelerin dinamik olması gerektiğini belirtir. Diğer bir deyişle, temeldeki belge değişirse, bu iki nesnelerdeki verilerin de değiştirilmesi gerekir. Bu nedenle, belirli bir öğenin tüm alt öğelerini içeren bir **XmlNodeList** varsa (örneğin, öğesi x), öğe x ' in altındaki belgeye, ek bir öğe olan soru-cevap ekleyin. **XmlNodeList** aynı zamanda koleksiyonuna yeni bir s öğesi eklenmiş olmalıdır. Aynı değer ters de geçerlidir. **XmlNodeList** nesnesine bir düğüm eklenirse, temel alınan belge de güncelleştirilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](xml-document-object-model-dom.md)
