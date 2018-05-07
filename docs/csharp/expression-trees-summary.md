---
title: İfade ağaçları özeti
description: Kodu verileri olarak yorumlar ve o koduna göre yeni işlevsellik yapı dinamik programlar oluşturmak için ifade ağaçları nasıl kullanabileceğiniz özetleri.
ms.date: 06/20/2016
ms.assetid: eb687ebd-1149-4453-9fc1-12a084495a66
ms.openlocfilehash: e0d46aa67b61fd4e1d2bcc20b4a567524bb00301
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="expression-trees-summary"></a>İfade ağaçları özeti

[Önceki--İfadeleri çevirme](expression-trees-translating.md)

Bu dizide nasıl kullanacağınızı gördünüz *ifade ağaçları* kodu verileri olarak yorumlar ve o koduna göre yeni işlevsellik yapı dinamik programları oluşturma.

Bir algoritma amacı anlamak için ifade ağaçları inceleyebilirsiniz. Yalnızca bu kodu inceleyebilirsiniz değil. Özgün kod değiştirilmiş sürümlerini temsil eden yeni ifade ağaçları oluşturabilirsiniz.

Bir algoritma aramak için ifade ağaçları kullanma ve başka bir dil veya ortamla bu algoritmayı çevir. 

## <a name="limitations"></a>Sınırlamalar

İyi ifade ağaçlara Çevir olmayan bazı yeni C# dil öğeleri vardır. İfade ağaçları içeremez `await` ifadelerini veya `async` lambda ifadeleri. C# 6 sürümde eklenen özelliklerin tam olarak ifade ağaçlarında yazılmış gibi görünmüyor. Bunun yerine, ifade ağaçları eşdeğer, önceki sözdiziminde daha yeni özellikleri sunulur. Bu düşündüğünüzden gibi sınırlandırılmasıdır kadar olmayabilir. Aslında, bu yeni dil özellikleri sunulduğunda ifade ağaçları yorumlar kodunuzu hala olasılıkla aynı çalışacağını anlamına gelir.

Bu kısıtlamalarla bile ifade ağaçları yorumlama ve veri yapısı olarak temsil edilir kodu değiştirme dayanan dinamik algoritmaları oluşturmanızı sağlar. Güçlü bir araçtır ve ne yaptıklarını gerçekleştirmek için Entity Framework gibi zengin kitaplıkları sağlar .NET ekosistemi özelliklerini biridir.

