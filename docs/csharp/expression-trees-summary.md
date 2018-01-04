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
ms.openlocfilehash: d2754493c782c2550a8b0bd0de274cb8100c78af
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="expression-trees-summary"></a>İfade ağaçları özeti

[Önceki--İfadeleri çevirme](expression-trees-translating.md)

Bu dizide nasıl kullanacağınızı gördünüz *ifade ağaçları* kodu verileri olarak yorumlar ve o koduna göre yeni işlevsellik yapı dinamik programları oluşturma.

Bir algoritma amacı anlamak için ifade ağaçları inceleyebilirsiniz. Yalnızca bu kodu inceleyebilirsiniz değil. Özgün kod değiştirilmiş sürümlerini temsil eden yeni ifade ağaçları oluşturabilirsiniz.

Bir algoritma aramak için ifade ağaçları kullanma ve başka bir dil veya ortamla bu algoritmayı çevir. 

## <a name="limitations"></a>Sınırlamalar

İyi ifade ağaçlara Çevir olmayan bazı yeni C# dil öğeleri vardır. İfade ağaçları içeremez `await` ifadelerini veya `async` lambda ifadeleri. C# 6 sürümde eklenen özelliklerin tam olarak ifade ağaçlarında yazılmış gibi görünmüyor. Bunun yerine, ifade ağaçları eşdeğer, önceki sözdiziminde daha yeni özellikleri sunulur. Bu düşündüğünüzden gibi sınırlandırılmasıdır kadar olmayabilir. Aslında, bu yeni dil özellikleri sunulduğunda ifade ağaçları yorumlar kodunuzu hala olasılıkla aynı çalışacağını anlamına gelir.

Bu kısıtlamalarla bile ifade ağaçları yorumlama ve veri yapısı olarak temsil edilir kodu değiştirme dayanan dinamik algoritmaları oluşturmanızı sağlar. Güçlü bir araçtır ve ne yaptıklarını gerçekleştirmek için Entity Framework gibi zengin kitaplıkları sağlar .NET ekosistemi özelliklerini biridir.

