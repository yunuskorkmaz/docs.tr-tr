---
description: 'Hakkında daha fazla bilgi edinin: nesne veya sınıf olay kümesini desteklemiyor'
title: Nesne veya sınıf olay kümesini desteklemiyor
ms.date: 07/20/2015
f1_keywords:
- vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
ms.openlocfilehash: f13d47a6bb75a5e8394f5344b954afa523bedab3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795617"
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a>Nesne veya sınıf olay kümesini desteklemiyor

`WithEvents`Belirtilen olay kümesi için olay kaynağı olarak çalışmayan bir bileşeni olan bir değişken kullanmaya çalıştınız. Örneğin, bir nesnenin olaylarını havuza almak istiyordunuz ve ardından ilk nesne için başka bir nesne oluşturun `Implements` . Olayları uygulanan nesnesinden havuzunuza uyacağını düşünebilseniz de, bu durum her zaman değildir. `Implements` yalnızca Yöntemler ve özellikler için bir arabirim uygular. `WithEvents``UserControls`, öğesini yükseltmek için gereken tür bilgisi çalışma zamanında kullanılabilir olmadığından Private için desteklenmez `ObjectEvent` .

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Olayları kaynak olmayan bir bileşen için havuza yükleyemezsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [WithEvents](../modifiers/withevents.md)
- [Implements Deyimi](../statements/implements-statement.md)
