---
title: C# temsilciler - C# dili turu
description: "Geç bağlama C# temsilciler ile bilgi edinin"
keywords: "Geç bağlama .NET csharp, temsilci, lambda,"
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 3cc27357-3ac2-43a1-aad0-86a77b88f884
ms.openlocfilehash: bb304b2e5c762a44aab931b5e8f7fe9c99805eba
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="delegates"></a>Temsilciler

A ***temsilci türü*** belirli bir parametre yöntemleriyle temsil başvuruları listesinde ve dönüş türü. Temsilciler yöntemleri değişkenleri için atanan ve parametre olarak geçirilen varlıklar olarak değerlendirmek mümkün kılar. Temsilciler diğer bazı dillerde bulunan işlev işaretçileri kavramı benzer, ancak işlev işaretçileri, nesne yönelimli ve tür kullanımı uyumlu temsilciler.

Aşağıdaki örnek bildirir ve adlı bir temsilci türü kullanan `Function`.

[!code-csharp[DelegateExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L3-L37)]

Örneği `Function` temsilci türü alır herhangi bir yöntemini başvuran bir `double` bağımsız değişkeni ve döndürür bir `double` değeri. `Apply` Yöntemi öğelerine verilen işlevin geçerli bir `double[]`, geri dönen bir `double[]` sonuçları. İçinde `Main` yöntemi, `Apply` üç farklı işleve uygulamak için kullanılan bir `double[]`.

Bir temsilci statik bir yöntem başvurusu yapabilir (gibi `Square` veya `Math.Sin` önceki örnekte) veya bir örnek yöntemi (gibi `m.Multiply` önceki örnekte). Örnek yöntemi başvuran bir temsilci Ayrıca belirli bir nesnenin başvuruda bulunduğundan ve temsilci örnek yöntemi çağrıldığında, bu nesne haline gelir `this` çağrısı.

Temsilciler ayrıca "üzerinde çalışma sırasında oluşturulan satır içi yöntemleri" anonim işlevler kullanılarak oluşturulabilir. Anonim işlevler çevresindeki yöntemlerin yerel değişkenler görebilirsiniz. Bu nedenle, yukarıdaki çarpanı örnek daha kolay çarpanı sınıfı kullanmadan yazılabilir:

[!code-csharp[LambdaExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L44-L44)]

Bir ilginç ve yararlı bir temsilci, bilmiyorsanız veya başvurduğu yöntemi sınıfı hakkında önemli olduğunu özelliğidir; önemli olan başvurulan yöntemi temsilci olarak dönüş türü ve aynı parametrelere sahip.

>[!div class="step-by-step"]
[Önceki](enums.md)
[sonraki](attributes.md)
