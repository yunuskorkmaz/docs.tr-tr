---
title: C# Delegeleri - C# dilinde bir tur
description: C# temsilcileriyle geç bağlanmayı öğrenin
ms.date: 02/27/2020
ms.assetid: 3cc27357-3ac2-43a1-aad0-86a77b88f884
ms.openlocfilehash: b1740ddc65dcb0ee8775f4cbaa8356293ea55fae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78159175"
---
# <a name="delegates"></a>Temsilciler

***Temsilci türü,*** belirli bir parametre listesi ve dönüş türüne sahip yöntemlere yapılan başvuruları temsil eder. Temsilciler, yöntemleri değişkenlere atanabilen ve parametre olarak geçirilebilen varlıklar olarak ele alabilen varlıklar olarak ele alabilmektir. Temsilciler, diğer bazı dillerde bulunan işlev işaretçileri kavramına benzer. Işlev işaretçilerinaksine, temsilciler nesne yönelimli ve tür güvenlidir.

Aşağıdaki örnek, .. `Function`

[!code-csharp[DelegateExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L3-L37)]

`Function` Temsilci türünün bir örneği, bağımsız değişken alan ve bir değer döndüren herhangi bir `double` `double` yönteme başvurur. Yöntem, `Apply` bir , sonuçları ile a `double[]` `double[]` dönen elemanları için verilen bir İşlev uygular. `Main` Yöntemde, `Apply` bir `double[]`üç farklı işlevleri uygulamak için kullanılır.

Temsilci, statik bir yönteme `Square` (önceki `Math.Sin` örnekte gibi) veya örnek yöntemine (önceki örnekte olduğu gibi) `m.Multiply` başvuru yapabilir. Örnek bir yönteme başvuran bir temsilci de belirli bir nesneye başvurur ve örnek `this` yöntemi temsilci aracılığıyla çağrıldığında, bu nesne çağırmada olur.

Temsilciler, beyan edildiğinde oluşturulan "satır dışı yöntemler" olan anonim işlevler kullanılarak da oluşturulabilir. Anonim işlevler, çevreleyen yöntemlerin yerel değişkenlerini görebilir. Aşağıdaki örnek bir sınıf oluşturmaz:

[!code-csharp[LambdaExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L44-L44)]

Bir temsilci, başvurulmadığı yöntemin sınıfını bilmez veya önemsemaz; önemli olan tek şey, başvurulan yöntemin temsilciyle aynı parametrelere ve dönüş türüne sahip olmasıdır.

>[!div class="step-by-step"]
>[Önceki](interfaces.md)
>[Sonraki](attributes.md)
