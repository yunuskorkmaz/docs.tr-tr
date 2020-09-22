---
title: Nesne veya sınıf olay kümesini desteklemiyor
ms.date: 07/20/2015
f1_keywords:
- vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
ms.openlocfilehash: e55a5515d88bd2782e31fdea7c07e16c595d43b5
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873659"
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a>Nesne veya sınıf olay kümesini desteklemiyor

`WithEvents`Belirtilen olay kümesi için olay kaynağı olarak çalışmayan bir bileşeni olan bir değişken kullanmaya çalıştınız. Örneğin, bir nesnenin olaylarını havuza almak istiyordunuz ve ardından ilk nesne için başka bir nesne oluşturun `Implements` . Olayları uygulanan nesnesinden havuzunuza uyacağını düşünebilseniz de, bu durum her zaman değildir. `Implements` yalnızca Yöntemler ve özellikler için bir arabirim uygular. `WithEvents``UserControls`, öğesini yükseltmek için gereken tür bilgisi çalışma zamanında kullanılabilir olmadığından Private için desteklenmez `ObjectEvent` .  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Olayları kaynak olmayan bir bileşen için havuza yükleyemezsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WithEvents](../modifiers/withevents.md)
- [Implements Deyimi](../statements/implements-statement.md)
