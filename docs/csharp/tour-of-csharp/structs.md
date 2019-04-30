---
title: C# yapılar - C# dili turu
description: Değer türleri, yapılar çağırılır, C# temellerini öğrenin
ms.date: 08/10/2016
ms.assetid: 88a74571-f741-4a31-a2b5-1ccf165535b8
ms.openlocfilehash: d22cb23fe095874f24d7c002dfdb3eefdde66722
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675760"
---
# <a name="structs"></a>Yapılar

Sınıflar gibi ***yapılar*** veri yapıları, veri üyeleri ve işlev üyeleri içerebilir, ancak farklı sınıflar, yapılar değer türleri ve yığın ayırma gerektirmez. Bir sınıf türünün bir değişkeni dinamik olarak ayrılan bir nesneye başvuru depoladığı bir yapı türünün değişkenini doğrudan, struct'ın verileri depolar. Yapı türleri, kullanıcı tarafından belirtilen devralma desteklemez ve tüm yapı türleri örtülü olarak tür devralmasına <xref:System.ValueType>, devralınan, örtük olarak buna karşılık `object`.

Yapılar değer semantiklere sahip küçük veri yapıları için özellikle yararlıdır. Karmaşık sayılar, koordinat sisteminde noktaları veya anahtar-değer çiftlerinin bir sözlükteki tüm iyi yapılar örnekleridir. Küçük veri yapıları için sınıflar, bir uygulama bellek ayırmaları sayısında büyük bir fark yapabilirsiniz yerine yapılar kullanımını gerçekleştirir. Örneğin, aşağıdaki program oluşturur ve 100 noktaları dizisini başlatır. İle `Point` sınıfı olarak uygulanır, 101 ayrı nesneler örneği oluşturulur; bir dizi ve her biri 100 öğeleri için.

[!code-csharp[PointClassUse](../../../samples/snippets/csharp/tour/structs/Program.cs#L5-L13)]

Bir yapının nokta yapmak için kullanılan bir alternatiftir.

[!code-csharp[PointStruct](../../../samples/snippets/csharp/tour/structs/Point.cs#L3-L11)]

Şimdi, yalnızca bir nesne örneği — bir dizi — ve `Point` depolanan satır içi dizi örnekleridir.

Yapı Oluşturucuları ile çağrılır `new` işleci, bir sınıf oluşturucusuna benzer. Ancak, dinamik olarak yönetilen yığındaki bir nesne ayırma ve buna bir başvuru döndürmek yerine, bir yapı Oluşturucu yalnızca yapı değerini kendisi (genellikle geçici bir konuma yığın üzerinde) döndürür ve bu değer daha sonra gerektiğinde kopyalanır.

Sınıfları ile bu iki değişken aynı nesneye başvurmak mümkün ve dolayısıyla işlemler diğer değişkenin başvurduğu nesneyi etkileyebilir bir değişken üzerinde mümkün olur. Yapılar, her değişkenleri kendi veri kopyası vardır ve yapılan işlemlerin diğerini etkilemesi olanaklı birinde değil. Örneğin, aşağıdaki kod parçası tarafından üretilen çıkış noktası bir sınıf veya yapı olduğuna bağlıdır.

[!code-csharp[PointUse](../../../samples/snippets/csharp/tour/structs/Program.cs#L19-L22)]

Varsa `Point` bir sınıf çıkış 20 çünkü `a` ve `b` aynı nesneye başvuru. Varsa `Point` bir yapı çıktı 10 çünkü atamasını `a` için `b` değeri bir kopyasını oluşturur ve bu kopyayı sonraki atamaya tarafından etkilenmez `a.x`.

Önceki örnekte iki yapılar sınırlamaları vurgular. İlk olarak, bir yapının tamamını kopyalama atama ve değerin parametre geçirme başvuru türleri ile yapılar ile daha pahalı olabilir. Bu nedenle, bir nesne başvurusu kopyalama daha genellikle daha az verimlidir. İkinci dışında `in`, `ref`, ve `out` parametreleri, bu durumlarda, çeşitli kullanımları kullanıma kuralları yapı birimleri için başvuru oluşturmak mümkün değildir.

>[!div class="step-by-step"]
>[Önceki](classes-and-objects.md)
>[İleri](arrays.md)
