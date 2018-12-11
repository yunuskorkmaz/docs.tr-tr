---
title: C#Diziler - Turu C# dil
description: En temel koleksiyon türü dizilerdir C# dil
ms.date: 08/10/2016
ms.assetid: a440704c-9e88-4c75-97dd-bfe30ca0fb97
ms.openlocfilehash: 8685e6ad08eb74534cdad499099b3d12da0a497a
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153312"
---
# <a name="arrays"></a>Diziler

Bir ***dizi*** hesaplanan dizinlerini erişilen değişken bir sayı içeren bir veri yapısıdır. Bir dizi içindeki değişkenler olarak da bilinir ***öğeleri*** dizinin tümü aynı türde ve bu tür çağrılır ***öğe türü*** dizi.

Dizi türleri, başvuru türleridir ve bir dizi değişkeni bildirimi yalnızca kenara alanı başvuru bir dizi örneği için ayarlar. Gerçek bir dizi örnekleri, new işleci kullanılarak çalışma zamanında dinamik olarak oluşturulur. Yeni işlemi belirtir ***uzunluğu*** sonra Örneğin ömrü boyunca sabittir yeni dizi örneği. Dizinleri öğelerinden oluşan bir dizi aralığından `0` için `Length - 1`. `new` İşleci, örneğin, sıfır olan tüm sayısal türler için varsayılan değerlerine bir dizinin öğeleri otomatik olarak başlatır ve `null` tüm başvuru türleri için.

Aşağıdaki örnek, bir dizi oluşturur. `int` öğeleri, dizi başlatır ve dizinin içeriği yazdırır.

[!code-csharp[ArraySample](../../../samples/snippets/csharp/tour/arrays/Program.cs#L3-L18)]

Bu örneği oluşturur ve üzerinde çalıştığı bir ***tek boyutlu dizi***. C# ' yı da destekler ***çok boyutlu diziler***. Olarak da bilinen bir dizinin boyut sayısını yazın ***derece*** dizi türü köşeli ayraç yazılan virgül sayısı artı bir dizi türünde olduğu. Aşağıdaki örnek bir tek boyutlu, iki boyutlu bir ve üç boyutlu bir dizi sırasıyla ayırır.

[!code-csharp[ArrayRank](../../../samples/snippets/csharp/tour/arrays/Program.cs#L24-L26)]

`a1` Dizi 10 öğe içeriyor `a2` dizi içeriyor 50 (10 × 5) öğeleri ve `a3` dizi içeriyor (10 × 5 × 2) 100 öğeleri.
Bir dizinin öğe türü bir dizi türü de dahil olmak üzere herhangi bir tür olabilir. Bir dizi türünde öğelere sahip bir dizi adlandırılan bir ***düzensiz dizi*** öğe dizisi uzunluklarının tümünü değil aynı olmak zorunda olduğu. Aşağıdaki örnekte dizi ayırır `int`:

[!code-csharp[ArrayAllocation](../../../samples/snippets/csharp/tour/arrays/Program.cs#L31-L34)]

İlk satır, üç öğeyle her türü bir dizi oluşturur `int[]` ve her bir başlangıç değeri ile `null`. Sonraki satırların başvurular değişen uzunlukları örneklerini tek bir dizi üç öğeleri ardından başlatın.

New işleci Başlangıç değerlerini kullanarak belirtilen dizi öğelerinin izin veren bir ***dizi Başlatıcısı***, sınırlayıcılar arasında yazılan ifadeler listesi olduğu `{` ve `}`. Aşağıdaki örnek ayırır ve başlatan bir `int[]` üç öğelerle.

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L39-L39)]

Dizinin uzunluğu arasında ifadelerin sayısından algılanır Not {ve}. Yerel değişken ve alan bildirimleri kısalttık daha fazla sağlayacak şekilde dizi türü açıklandı gerekmez.

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L44-L44)]

Önceki örneklerin her ikisi de aşağıdakine eşdeğerdir:

[!code-csharp[ArrayAssignment](../../../samples/snippets/csharp/tour/arrays/Program.cs#L49-L53)]

>[!div class="step-by-step"]
>[Önceki](structs.md)
>[İleri](interfaces.md)