---
title: Var Olan Düğümleri Kopyalama
ms.date: 03/30/2017
ms.assetid: 2aa8f65c-cc62-4638-9c46-129dc15be786
ms.openlocfilehash: b4ae24f9776456033a876e8ae4d1515d2f669fe0
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830954"
---
# <a name="copy-existing-nodes"></a>Var Olan Düğümleri Kopyalama
XML Belge Nesne Modeli (DOM), **selectSingleNode**, **ChildNodes [int i]**, **öznitelikler [int i]** gibi bir düğümü seçmek için kullanabileceğiniz birçok yöntem ve özellik vardır. Düğüm seçildikten sonra, söz konusu düğüm türü için çalışan INSERT yöntemlerinden birini kullanarak ağaca ekleyebilirsiniz. Ağaca bir düğüm eklemeye yönelik tek kısıtlama, belgenin düğüm eklendikten sonra yine de doğru biçimlendirilmiş olması gerekir. Varolan bir düğüm DOM ağacına eklendiğinde, özgün konumundan kaldırılır ve hedef konumuna eklenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](xml-document-object-model-dom.md)
