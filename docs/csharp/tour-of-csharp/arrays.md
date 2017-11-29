---
title: C# diziler - C# dili turu
description: "Dizi en temel C# dili koleksiyon türü olan"
keywords: .NET, csharp, dizi, koleksiyonu
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: a440704c-9e88-4c75-97dd-bfe30ca0fb97
ms.openlocfilehash: d7d5ae9f99ba1629a6f0aec57bebf74853cab27f
ms.sourcegitcommit: a19548e5167cbe7e9e58df4ffd8c3b23f17d5c7a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2017
---
# <a name="arrays"></a>Diziler

Bir ***dizi*** içeren bir dizi hesaplanan dizinlerini erişilen değişken bir veri yapısıdır. Bir dizinin içindeki değişkenleri olarak da bilinir ***öğeleri*** dizinin tümü aynı türde ve bu tür adlı ***öğe türü*** dizi.

Dizi türleri başvuru türleridir ve bir dizi değişkeni bildirimi yalnızca kenara bir dizi örneğine başvuru için alanı ayarlar. Gerçek dizi örnekleri yeni işlecini kullanarak çalışma zamanında dinamik olarak oluşturulur. Yeni işlem belirtir ***uzunluğu*** sonra örnek ömrü boyunca sabit yeni dizi örneği. Bir dizi aralıktan öğelerinin dizinlerini `0` için `Length - 1`. `new` İşleci, örneğin, sıfır olan tüm sayısal türler için varsayılan değerlerine dizi öğelerini otomatik olarak başlatır ve `null` tüm başvuru türleri.

Aşağıdaki örnek, bir dizi oluşturur `int` öğeleri, dizi başlatır ve dizinin içeriğini yazdırır.

[!code-csharp[ArraySample](../../../samples/snippets/csharp/tour/arrays/Program.cs#L3-L18)]

Bu örnek oluşturur ve çalıştırır bir ***tek boyutlu dizi***. C# ' yı da destekler ***çok boyutlu diziler***. Bir dizinin boyut sayısını yazın, olarak da bilinen ***derece*** dizi türü köşeli ayraç yazılmış virgül sayısı artı bir dizi türünde değil. Aşağıdaki örnek bir tek boyutlu, iki boyutlu bir ve üç boyutlu bir dizi sırasıyla ayırır.

[!code-csharp[ArrayRank](../../../samples/snippets/csharp/tour/arrays/Program.cs#L24-L26)]

`a1` Dizi 10 öğeleri içeren `a2` dizi içeriyor 50 (10 × 5) öğeleri ve `a3` dizi 100 (10 × 5 × 2) içeriyor öğeleri.
Bir dizi öğesi türü bir dizi türü de dahil olmak üzere herhangi bir türü olabilir. Bir dizi bir dizi türü öğelerin adlandırılan bir ***Basit dizi*** öğesi diziler uzunlukları tümü aynı olmak zorunda olduğundan. Aşağıdaki örnek oluşan bir dizi ayırır `int`:

[!code-csharp[ArrayAllocation](../../../samples/snippets/csharp/tour/arrays/Program.cs#L31-L34)]

İlk satır bir dizi üç öğeleri ile her tür oluşturur `int[]` ve her bir başlangıç değeriyle `null`. Sonraki satırların sonra başvuruları, değişken uzunlukta bağımsız dizi örneklerine üç öğeleriyle başlatır.

New işleci kullanılarak belirtilmesi için dizi öğelerinin ilk değerlerini verir bir ***dizi Başlatıcı***, arasında sınırlayıcıları yazılmış ifadeleri listesi olduğu `{` ve `}`. Aşağıdaki örnek ayırır ve başlatır bir `int[]` üç öğeye sahip.

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L39-L39)]

Dizi uzunluğu arasında ifadelerin numarasından algılanır Not {ve}. Yerel değişken ve alan bildirimleri kısaltılmış daha ayrıntılı şekilde dizi türü açıklandı gerekmez.

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L44-L44)]

Önceki örneklerde her ikisi de şuna eşdeğerdir:

[!code-csharp[ArrayAssignment](../../../samples/snippets/csharp/tour/arrays/Program.cs#L49-L53)]

>[!div class="step-by-step"]
[Önceki](structs.md)
[sonraki](interfaces.md)
