---
title: İfade ağaçları özeti
description: Kod veri olarak yorumlar ve yapı bu koduna göre yeni işlevselliği dinamik programlar oluşturmak için ifade ağaçları nasıl kullanabileceğiniz hakkında bilgiler bulabilirsiniz.
ms.date: 06/20/2016
ms.assetid: eb687ebd-1149-4453-9fc1-12a084495a66
ms.openlocfilehash: 99b9463df096d3aada19ed7995b04ef4bd41c179
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646572"
---
# <a name="expression-trees-summary"></a>İfade ağaçları özeti

[Önceki--İfade çevirme](expression-trees-translating.md)

Bu seride, nasıl kullanacağınızı öğrendiniz *ifade ağaçları* kod veri olarak yorumlar ve yapı bu koduna göre yeni işlevselliği dinamik programlar oluşturmak için.

Bir algoritma amacı anlamak için ifade ağaçları inceleyebilirsiniz. Yalnızca bu kodu inceleyebilirsiniz değil. Özgün koda değiştirilmiş sürümlerini temsil yeni ifade ağaçları oluşturabilirsiniz.

Ayrıca, bir algoritma aramak için ifade ağaçları kullanma ve başka bir dil ya da ortam bu algoritmayı çevirir. 

## <a name="limitations"></a>Sınırlamalar

Vardır bazı yeni C# iyi ifade ağaçları Çevir olmayan dil öğeleri. İfade ağaçları içeremez `await` ifadelerini veya `async` lambda ifadeleri. İçinde eklenen özelliklerin birçoğu C# 6 yayın tam olarak ifade ağaçlarında olarak yazılmış görünmez. Bunun yerine, eşdeğer, eski sözdizimi ifade ağaçlarında yeni özellikler sunulur. Bu gibi düşünebilirsiniz ilişkin bir sınırlama kadar olmayabilir. Aslında, yeni dil özellikleri sunulduğunda ifade ağaçları yorumlar kodunuzu yine de büyük olasılıkla aynı çalışacağını anlamına gelir.

Bu kısıtlamalarla bile ifade ağaçları yorumlama ve bir veri yapısı olarak temsil edilen kod değiştirme dayanan dinamik algoritmaları oluşturmanıza olanak sağlar. Güçlü bir araçtır ve ne yaptıkları gerçekleştirmek için Entity Framework gibi zengin kitaplıkları sağlar .NET ekosisteminin özelliklerinden biridir.
