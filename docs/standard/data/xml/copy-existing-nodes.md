---
title: Var Olan Düğümleri Kopyalama
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 2aa8f65c-cc62-4638-9c46-129dc15be786
ms.openlocfilehash: 392490d04ff713529d501e199ac2496ff37de1a0
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289219"
---
# <a name="copy-existing-nodes"></a>Var Olan Düğümleri Kopyalama
XML Belge Nesne Modeli (DOM), **selectSingleNode**, **ChildNodes [int i]**, **öznitelikler [int i]** gibi bir düğümü seçmek için kullanabileceğiniz birçok yöntem ve özellik vardır. Düğüm seçildikten sonra, söz konusu düğüm türü için çalışan INSERT yöntemlerinden birini kullanarak ağaca ekleyebilirsiniz. Ağaca bir düğüm eklemeye yönelik tek kısıtlama, belgenin düğüm eklendikten sonra yine de doğru biçimlendirilmiş olması gerekir. Varolan bir düğüm DOM ağacına eklendiğinde, özgün konumundan kaldırılır ve hedef konumuna eklenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](xml-document-object-model-dom.md)
