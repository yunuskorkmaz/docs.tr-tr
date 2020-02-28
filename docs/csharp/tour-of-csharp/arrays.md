---
title: C#Diziler- C# dilin turu
description: Diziler, C# dildeki en temel koleksiyon türüdür
ms.date: 02/27/2020
ms.assetid: a440704c-9e88-4c75-97dd-bfe30ca0fb97
ms.openlocfilehash: 3e045c0933a21beab6958c7851546ba6e0b55ef9
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159201"
---
# <a name="arrays"></a>Diziler

***Dizi*** , hesaplanan dizinler üzerinden erişilen çeşitli değişkenler içeren bir veri yapısıdır. Bir dizide bulunan değişkenler, dizi ***öğeleri*** de denir, hepsi aynı türdür ve bu tür dizinin ***öğe türü*** olarak adlandırılır.

Dizi türleri başvuru türlerdir ve bir dizi değişkeninin bildirimi, bir dizi örneğine yönelik bir başvuru için yalnızca alan ayırın. Gerçek dizi örnekleri, çalışma zamanında yeni işleci kullanılarak dinamik olarak oluşturulur. Yeni işlem, daha sonra örneğin ömrü boyunca düzeltilen yeni dizi örneğinin ***uzunluğunu*** belirtir. Dizi aralığının öğelerinin dizinleri `Length - 1``0`. `new` işleci, bir dizinin öğelerini otomatik olarak varsayılan değerlerine başlatır. Bu, örneğin, tüm sayısal türler için sıfır ve tüm başvuru türleri için `null`.

Aşağıdaki örnek `int` öğelerinden oluşan bir dizi oluşturur, diziyi başlatır ve dizinin içeriğini yazdırır.

[!code-csharp[ArraySample](../../../samples/snippets/csharp/tour/arrays/Program.cs#L3-L18)]

Bu örnek, ***tek boyutlu bir dizi***üzerinde oluşturur ve çalışır. C#, ***çok boyutlu dizileri***de destekler. Dizi türünün ***derecesi*** olarak da bilinen bir dizi türünün boyut sayısı, dizi türünün köşeli ayraçları arasına yazılan virgüllerin sayısıdır. Aşağıdaki örnek, sırasıyla tek boyutlu, iki boyutlu ve üç boyutlu bir diziyi ayırır.

[!code-csharp[ArrayRank](../../../samples/snippets/csharp/tour/arrays/Program.cs#L24-L26)]

`a1` dizi 10 öğe içeriyorsa, `a2` dizisi 50 (10 × 5) öğesi içerir ve `a3` dizisi 100 (10 × 5 × 2) öğe içerir.
Bir dizinin öğe türü, bir dizi türü de dahil olmak üzere herhangi bir tür olabilir. Dizi türündeki öğeleri içeren bir dizi, bazen öğe dizilerinin uzunluklarının tümünün aynı olması gerektiğinden ***pürüzlü dizi*** olarak adlandırılır. Aşağıdaki örnek, `int`dizi dizileri ayırır:

[!code-csharp[ArrayAllocation](../../../samples/snippets/csharp/tour/arrays/Program.cs#L31-L34)]

İlk satır, her biri `int[]` her biri `null`başlangıç değeri olan üç öğe içeren bir dizi oluşturur. Sonraki satırlar, Farklı uzunluklardaki ayrı dizi örneklerine yapılan başvurularla üç öğeyi başlatır.

New işleci, dizi öğelerinin başlangıç değerlerinin, `{` ve `}`sınırlayıcılarının yazıldığı bir ifade listesi olan ***dizi başlatıcısı***kullanılarak belirtilmesine izin verir. Aşağıdaki örnek, üç öğe ile bir `int[]` ayırır ve başlatır.

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L39-L39)]

Dizinin uzunluğu {ve} arasındaki ifade sayısından çıkarsanamıyor. Yerel değişken ve alan bildirimleri daha fazla kısaltılarak, dizi türünün yeniden oluşturulması gerekmez.

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L44-L44)]

Yukarıdaki örneklerin her ikisi de aşağıdaki koda eşdeğerdir:

[!code-csharp[ArrayAssignment](../../../samples/snippets/csharp/tour/arrays/Program.cs#L49-L53)]

>[!div class="step-by-step"]
>[Önceki](classes-and-objects.md)
>[İleri](interfaces.md)
