---
title: İfade Ağaçları Özeti
description: Kodu veri olarak yorumlayan ve bu koda dayalı yeni işlevler oluşturan dinamik programlar oluşturmak için ifade ağaçlarını nasıl kullanabileceğinizi özetler.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: eb687ebd-1149-4453-9fc1-12a084495a66
ms.openlocfilehash: 513244a987e295c81cfb5d00d9a0cfd6912074e0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79145897"
---
# <a name="expression-trees-summary"></a>İfade Ağaçları Özeti

[Önceki -- İfadeleri Çevirme](expression-trees-translating.md)

Bu seride, kodu veri olarak yorumlayan ve bu koda dayalı yeni işlevler oluşturan dinamik programlar oluşturmak için *ifade ağaçlarını* nasıl kullanabileceğinizi gördünüz.

Bir algoritmanın amacını anlamak için ifade ağaçlarını inceleyebilirsiniz. Sadece bu kodu inceleyebilir. Özgün kodun değiştirilmiş sürümlerini temsil eden yeni ifade ağaçları oluşturabilirsiniz.

Bir algoritmaya bakmak ve bu algoritmayı başka bir dile veya ortama çevirmek için ifade ağaçlarını da kullanabilirsiniz.

## <a name="limitations"></a>Sınırlamalar

İfade ağaçlarına iyi çevrilen bazı yeni C# dil öğeleri vardır. İfade ağaçları `await` ifadeler veya `async` lambda ifadeleri içeremez. C# 6 sürümünde eklenen özelliklerin çoğu ifade ağaçlarında yazıldığı gibi görünmüyor. Bunun yerine, daha yeni özellikler eşdeğer, önceki sözdizimi ifadeler ağaçlar maruz kalır. Bu düşündüğünüz kadar bir sınırlama olmayabilir. Aslında, ifade ağaçlarını yorumlayan kodunuzu yeni dil özellikleri tanıtıldığında büyük olasılıkla yine de aynı şekilde çalışacağı anlamına gelir.

Bu sınırlamalara rağmen, ifade ağaçları, veri yapısı olarak temsil edilen kodu yorumlamaya ve değiştirmeye dayanan dinamik algoritmalar oluşturmanıza olanak tanır. Bu güçlü bir araçtır ve .NET ekosisteminin entity framework gibi zengin kitaplıkların yaptıklarını gerçekleştirmesini sağlayan özelliklerinden biridir.
