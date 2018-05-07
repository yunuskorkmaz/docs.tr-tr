---
title: C# yapılar - C# dili turu
description: C# temelleri yapılar adlı türleri, değer öğrenin
ms.date: 08/10/2016
ms.assetid: 88a74571-f741-4a31-a2b5-1ccf165535b8
ms.openlocfilehash: dca21fe5c5f3f97bc067eb79229a608e89c0fcda
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="structs"></a>Yapılar

Sınıfları, ister ***yapılar*** veri üyeleri ve işlev üyeleri içerebilir veri yapılarını, ancak farklı sınıflar, yapılar değer türleri ve yığın ayırma gerektirmez. Sınıf türü bir değişken dinamik olarak ayrılan bir nesneye başvuru depoladığı bir yapı türünde bir değişken doğrudan yapısı veri depolar. Struct türleri, kullanıcı tarafından belirtilen devralma desteklemez ve tüm yapı türleri örtük olarak türünden devralan <xref:System.ValueType>, hangi de örtük olarak Aç devraldığı `object`.

Yapılar değer semantiklerine sahip küçük veri yapıları için özellikle yararlıdır. Karmaşık numaralar, koordinat sistemi noktaları veya anahtar-değer çiftleri sözlükteki tüm iyi yapılar gösterilebilir. Küçük veri yapıları için sınıflar, bir uygulama bellek ayırmaları sayısı büyük bir fark yaratabilir yerine yapılar kullanımını gerçekleştirir. Örneğin, aşağıdaki programı oluşturur ve 100 puan dizisini başlatır. İle `Point` bir sınıf olarak uygulanan, 101 ayrı nesneler örneği oluşturulmadan — bir dizi ve her biri için 100 öğeleri için.

[!code-csharp[PointClassUse](../../../samples/snippets/csharp/tour/structs/Program.cs#L5-L13)]

Yapı noktası yapmak için kullanılan bir alternatiftir.

[!code-csharp[PointStruct](../../../samples/snippets/csharp/tour/structs/Point.cs#L3-L11)]

Şimdi, yalnızca bir nesne örneği — bir dizi — ve `Point` saklı satır içi dizideki örnekleridir.

Yapı oluşturucuları yeni işleciyle çağrılır, ancak bu bellek göstermez tahsis edilir. Dinamik bir nesne ayırma ve kendisine bir başvuru döndürme, yerine bir yapı Oluşturucu yalnızca yapısı değeri kendisini (genellikle geçici bir konuma yığında) döndürür ve bu değer daha sonra gerektiğinde kopyalanır.

Sınıflar ile aynı nesneye başvurmak iki değişken için olası ve böylece olası bir değişkeni tarafından başvurulan nesne etkilemek için bir değişken üzerinde işlemler için. Yapılar, her değişkenleri veri kendi kopyasına sahip ve bir diğer etkileyen işlemler için kullanılamaz. Örneğin, aşağıdaki kod parçası tarafından üretilen çıkış noktası bir sınıf veya yapı olduğuna bağlıdır.

[!code-csharp[PointUse](../../../samples/snippets/csharp/tour/structs/Program.cs#L19-L22)]

Varsa `Point` bir sınıf çıkış 20 çünkü bir ve b aynı nesne başvurusu. Noktası yapı çıktı 10 çünkü ise, atanması `a` için `b` değeri bir kopyasını oluşturur ve bu kopyayı sonraki atamayı tarafından etkilenmez `a.x`.

Önceki örnekte iki yapılar sınırlamaları vurgular. İlk olarak, bir yapının tamamını kopyalama atama ve değerin parametre geçirme yapılar başvuru türleri ile birlikte daha pahalı olabilir bir nesne başvurusu kopyalama daha genellikle daha az verimlidir. İkinci dışında `in`, `ref`, ve `out` parametreleri, bu kullanımları durumlarda çeşitli giden kuralları yapılar başvuruları oluşturmak mümkün değildir.

>[!div class="step-by-step"]
[Önceki](classes-and-objects.md)
[sonraki](arrays.md)
