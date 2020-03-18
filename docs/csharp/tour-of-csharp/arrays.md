---
title: C# Dizileri - C# dilinde bir tur
description: Diziler C# dilindeki en temel koleksiyon türüdür
ms.date: 02/27/2020
ms.assetid: a440704c-9e88-4c75-97dd-bfe30ca0fb97
ms.openlocfilehash: 3e045c0933a21beab6958c7851546ba6e0b55ef9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78159201"
---
# <a name="arrays"></a>Diziler

***Dizi,*** hesaplanan endeksler aracılığıyla erişilen bir dizi değişken içeren bir veri yapısıdır. Dizinin ***öğeleri*** olarak da adlandırılan bir dizide bulunan değişkenlerin tümü aynı türdendir ve bu türe dizinin ***öğe türü*** denir.

Dizi türleri başvuru türleridir ve bir dizi değişkeninin bildirimi yalnızca bir dizi örneğine başvuru için bir alan ayırır. Gerçek dizi örnekleri, yeni işleç kullanılarak çalışma zamanında dinamik olarak oluşturulur. Yeni işlem, yeni dizi örneğinin ***uzunluğunu*** belirtir ve bu örnek, daha sonra örneğin ömrü için sabitlenir. Bir dizinin `0` öğelerinin `Length - 1`endeksleri. İşletici, `new` örneğin tüm sayısal türler ve `null` tüm başvuru türleri için sıfır olan bir dizinin öğelerini varsayılan değerine otomatik olarak aparat eder.

Aşağıdaki örnek, bir dizi `int` öğe oluşturur, diziyi baş harfe alerler ve dizinin içeriğini yazdırır.

[!code-csharp[ArraySample](../../../samples/snippets/csharp/tour/arrays/Program.cs#L3-L18)]

Bu ***örnek, tek boyutlu***bir dizi oluşturur ve çalışır. C# aynı zamanda ***çok boyutlu dizileri***de destekler. Dizi türünün ***sıralaması*** olarak da bilinen bir dizi türünün boyut sayısı, bir artı dizi türünün kare ayraçları arasında yazılmış virgül sayısıdır. Aşağıdaki örnek, sırasıyla tek boyutlu, iki boyutlu ve üç boyutlu bir dizi ayırır.

[!code-csharp[ArrayRank](../../../samples/snippets/csharp/tour/arrays/Program.cs#L24-L26)]

Dizi `a1` 10 eleman `a2` içerir, dizi 50 (10 × `a3` 5) eleman içerir ve dizi 100 (10 × 5 × 2) elemanlar içerir.
Bir dizinin öğe türü, bir dizi türü de dahil olmak üzere herhangi bir tür olabilir. Öğe dizilerinin uzunluklarının hepsinin aynı olması gerekmedığından, dizi türüöğelerine sahip bir diziye bazen ***pürüzlü dizi*** denir. Aşağıdaki örnek, bir dizi dizi `int`ayırır:

[!code-csharp[ArrayAllocation](../../../samples/snippets/csharp/tour/arrays/Program.cs#L31-L34)]

İlk satır, her biri tür `int[]` ve her biri başlangıç değeri `null`ne olacak olmak üzere üç öğeden oluşan bir dizi oluşturur. Sonraki satırlar daha sonra değişen uzunluklarda tek tek dizi örneklerine başvurularla üç öğeyi başolarak ortaya alır.

Yeni işleç, dizi elemanlarının ilk değerlerinin bir ***dizi baş harferkullanılarak***belirtilmesine izin verir, `{` bu `}`da sınırlayıcılar ve . Aşağıdaki örnek üç öğeli bir `int[]` ayırır ve başharfleri.

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L39-L39)]

Dizinin uzunluğu { ve }arasındaki ifade sayısından çıkarılır. Yerel değişken ve alan bildirimleri, dizi türünün yeniden ifade edilmesine gerek olmayacak şekilde daha da kısaltılabilir.

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L44-L44)]

Önceki örneklerin her ikisi de aşağıdaki koda eşdeğerdir:

[!code-csharp[ArrayAssignment](../../../samples/snippets/csharp/tour/arrays/Program.cs#L49-L53)]

>[!div class="step-by-step"]
>[Önceki](classes-and-objects.md)
>[Sonraki](interfaces.md)
