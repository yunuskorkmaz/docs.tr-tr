---
title: C#Temsilciler- C# dilin turu
description: Temsilcilerle C# geç bağlamayı öğrenin
ms.date: 02/27/2020
ms.assetid: 3cc27357-3ac2-43a1-aad0-86a77b88f884
ms.openlocfilehash: b1740ddc65dcb0ee8775f4cbaa8356293ea55fae
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159175"
---
# <a name="delegates"></a>Temsilciler

Bir ***temsilci türü*** , belirli bir parametre listesi ve dönüş türü olan yöntemlere yapılan başvuruları temsil eder. Temsilciler, yöntemleri değişkenlere atanabilecek ve parametre olarak geçirilen varlıklar olarak işleme olanağı tanır. Temsilciler, bazı diğer dillerde bulunan işlev işaretçileri kavramına benzerdir. İşlev işaretçilerinden farklı olarak, temsilciler nesne odaklı ve tür açısından güvenlidir.

Aşağıdaki örnek, `Function`adlı bir temsilci türü bildirir ve kullanır.

[!code-csharp[DelegateExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L3-L37)]

`Function` temsilci türünün bir örneği, `double` bağımsız değişken alan ve `double` bir değer döndüren herhangi bir yönteme başvurabilir. `Apply` yöntemi, belirli bir Işlevi bir `double[]`öğelerine uygular, sonuçlarla bir `double[]` döndürüyor. `Main` yönteminde, bir `double[]`üç farklı işlevi uygulamak için `Apply` kullanılır.

Bir temsilci, statik bir yönteme (örneğin, `Square` veya önceki örnekteki `Math.Sin`) veya bir örnek yöntemine (önceki örnekte `m.Multiply` gibi) başvurabilir. Aynı zamanda bir örnek yöntemine başvuran bir temsilci belirli bir nesneye başvurur ve örnek yöntemi temsilci aracılığıyla çağrıldığında, bu nesne çağrıdan `this` olur.

Temsilciler, bildirildiği sırada oluşturulan "satır içi Yöntemler" olan anonim işlevler kullanılarak da oluşturulabilir. Anonim işlevler, çevresindeki yöntemlerin yerel değişkenlerini görebilir. Aşağıdaki örnek bir sınıf oluşturmaz:

[!code-csharp[LambdaExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L44-L44)]

Bir temsilci, başvurduğu yöntemin sınıfını bilmez veya ilgilenmez; her önemli şey, başvurulan yöntemin aynı parametrelere sahip olması ve temsilciyle aynı türde dönüş türüdür.

>[!div class="step-by-step"]
>[Önceki](interfaces.md)
>[İleri](attributes.md)
