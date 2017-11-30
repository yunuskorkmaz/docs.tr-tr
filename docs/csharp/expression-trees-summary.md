---
title: "İfade ağaçları özeti"
description: "Kodu verileri olarak yorumlar ve o koduna göre yeni işlevsellik yapı dinamik programlar oluşturmak için ifade ağaçları nasıl kullanabileceğiniz özetleri."
keywords: .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: eb687ebd-1149-4453-9fc1-12a084495a66
ms.openlocfilehash: 8088ce0c138cdb05a6e4a4fb6467e43efd252ba7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="expression-trees-summary"></a>İfade ağaçları özeti

[Önceki--İfadeleri çevirme](expression-trees-translating.md)

Bu dizide nasıl kullanacağınızı gördünüz *ifade ağaçları* kodu verileri olarak yorumlar ve o koduna göre yeni işlevsellik yapı dinamik programları oluşturma.

Bir algoritma amacı anlamak için ifade ağaçları inceleyebilirsiniz. Yalnızca bu kodu inceleyebilirsiniz değil. Özgün kod değiştirilmiş sürümlerini temsil eden yeni ifade ağaçları oluşturabilirsiniz.

Bir algoritma aramak için ifade ağaçları kullanma ve başka bir dil veya ortamla bu algoritmayı çevir. 

## <a name="limitations"></a>Sınırlamalar

İyi ifade ağaçlara Çevir olmayan bazı yeni C# dil öğeleri vardır. İfade ağaçları içeremez `await` ifadelerini veya `async` lambda ifadeleri. C# 6 sürümde eklenen özelliklerin tam olarak ifade ağaçlarında yazılmış gibi görünmüyor. Bunun yerine, ifade ağaçları eşdeğer, önceki sözdiziminde daha yeni özellikleri sunulur. Bu düşündüğünüzden gibi sınırlandırılmasıdır kadar olmayabilir. Aslında, bu yeni dil özellikleri sunulduğunda ifade ağaçları yorumlar kodunuzu hala olasılıkla aynı çalışacağını anlamına gelir.

Bu kısıtlamalarla bile ifade ağaçları yorumlama ve veri yapısı olarak temsil edilir kodu değiştirme dayanan dinamik algoritmaları oluşturmanızı sağlar. Güçlü bir araçtır ve ne yaptıklarını gerçekleştirmek için Entity Framework gibi zengin kitaplıkları sağlar .NET ekosistemi özelliklerini biridir.

