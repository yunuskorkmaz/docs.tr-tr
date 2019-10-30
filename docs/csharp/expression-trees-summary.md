---
title: İfade ağaçları Özeti
description: Kodu veri olarak yorumlayan ve bu koda göre yeni işlevsellik oluşturan dinamik programlar oluşturmak için, ifade ağaçlarını nasıl kullanabileceğinizi öğrenin.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: eb687ebd-1149-4453-9fc1-12a084495a66
ms.openlocfilehash: 43715c94b70f1cd7f758cde91ae7c8d1b2f70f9f
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73036751"
---
# <a name="expression-trees-summary"></a>İfade ağaçları Özeti

[Önceki--Ifadeleri çevirme](expression-trees-translating.md)

Bu seride, kod verileri olarak yorumlayan ve bu koda göre yeni işlevsellik oluşturan dinamik programlar oluşturmak için *ifade ağaçlarını* nasıl kullanabileceğinizi gördünüz.

Bir algoritmanın amacını anlamak için ifade ağaçlarını inceleyebilirsiniz. Bu kodu yalnızca inceleyebilirsiniz. Özgün kodun değiştirilmiş sürümlerini temsil eden yeni ifade ağaçları oluşturabilirsiniz.

Ayrıca, bir algoritmaya bakmak ve bu algoritmayı başka bir dile veya ortama çevirmek için ifade ağaçlarını de kullanabilirsiniz. 

## <a name="limitations"></a>Sınırlamalar

İfade ağaçlarına düzgün C# çevriolmayan bazı yeni dil öğeleri vardır. İfade ağaçları `await` ifade veya `async` lambda ifadesi içeremez. C# 6 sürümüne eklenen özelliklerin birçoğu tam olarak ifade ağaçlarında yazılmış şekilde görünmez. Bunun yerine, eşdeğer, Önceki sözdiziminde ifade ağaçlarında daha yeni özellikler kullanıma sunulacaktır. Bu işlem, düşündüğünüzden bir sınırlamanın büyük bir bölümü olmayabilir. Aslında, ifade ağaçlarını yorumlayan kodunuzun, yeni dil özellikleri tanıtıldığında muhtemelen aynı zamanda çalışmaya devam ettiği anlamına gelir.

Bu sınırlamalar da dahil olmak üzere, ifade ağaçları, veri yapısı olarak temsil edilen kodu yorumlama ve değiştirme konusunda temel alan dinamik algoritmalar oluşturmanızı sağlar. Bu güçlü bir araçtır ve .NET ekosisteminin, Entity Framework gibi zengin kitaplıkları sağlayan özelliklerden biridir.
