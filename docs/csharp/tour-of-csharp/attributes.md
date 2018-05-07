---
title: C# öznitelikleri - C# dili turu
description: Öznitelikleri C# kullanarak bildirim temelli programlama hakkında bilgi edinin
ms.date: 08/10/2016
ms.assetid: 753bcfe2-7ddd-4487-9513-ba70937fc8e9
ms.openlocfilehash: d055f5386d1dddef0b70843a0a5fa6fc04922296
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="attributes"></a>Öznitelikler

Türleri, üyeleri ve diğer varlıklar bir C# programında davranışlarını belirli yönlerini denetlemek değiştiricileri destekler. Örneğin, bir yöntemin erişilebilirliğini kullanılarak denetlenir `public`, `protected`, `internal`, ve `private` değiştiricileri. Kullanıcı tanımlı tür tanımlayıcı bilgiler program varlıklara bağlı ve çalışma zamanında alınır, C# Bu yetenek genelleştirir. Programları belirtin Bu ek tanımlayıcı bilgiler tanımlama ve kullanma ***öznitelikleri***.

Aşağıdaki örnek bildiren bir `HelpAttribute` , ilişkili belgelere bağlantılar sağlamak için program varlıklar üzerinde yerleştirilebilir özniteliği.

[!code-csharp[AttributeDefined](../../../samples/snippets/csharp/tour/attributes/Program.cs#L3-L20)]

Tüm öznitelik sınıfları türetin <xref:System.Attribute> temel standart kitaplığı tarafından sağlanan sınıfı. Öznitelikler, tüm bağımsız değişkenleri köşeli ayraç içinde ilişkili bildirimi hemen önce yanı sıra bunların adı vererek uygulanabilir. Bir özniteliğin adı biterse `Attribute`, öznitelik başvurulduğunda adı kısmı atlanabilir. Örneğin, `HelpAttribute` özniteliği şu şekilde kullanılabilir.

[!code-csharp[AttributeApplied](../../../samples/snippets/csharp/tour/attributes/Program.cs#L22-L28)]

Bu örnek iliştirir bir `HelpAttribute` için `Widget` sınıfı. Başka bir ekler `HelpAttribute` için `Display` sınıfında yöntemi. Genel oluşturucular öznitelik sınıfı, öznitelik için bir program varlığı iliştirildiğinde sağlanmalıdır bilgileri denetler. Ek bilgi öznitelik sınıfı ortak okuma-yazma özelliklerini başvurarak sağlanabilir (referansı gibi `Topic` özelliği daha önce).

Yansıma yoluyla belirli bir öznitelik istendiğinde, program kaynağında sağlanan bilgileri ile öznitelik sınıfı oluşturucusu çağrılır ve sonuçta elde edilen özniteliği örneği döndürdü. Ek bilgi özelliklerinden verdiyse, öznitelik örneği döndürülmeden önce bu özellikleri belirtilen değerlere ayarlanır.

>[!div class="step-by-step"]
[Önceki](delegates.md)
