---
title: C#Öznitelikler- C# dilin turu
description: İçindeki öznitelikleri kullanarak bildirim temelli programlama hakkında bilgi edininC#
ms.date: 02/27/2020
ms.assetid: 753bcfe2-7ddd-4487-9513-ba70937fc8e9
ms.openlocfilehash: dc5b194c22fc2746ff8b0ab3e550e560a3666bbe
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159214"
---
# <a name="attributes"></a>Öznitelikler

Bir C# programdaki türler, Üyeler ve diğer varlıklar, davranışlarının belirli yönlerini denetleyen değiştiricilerin özelliklerini destekler. Örneğin, bir yöntemin erişilebilirliği `public`, `protected`, `internal`ve `private` değiştiricileri kullanılarak denetlenir. C#Bu özelliği, bildirim temelli bilgilerin Kullanıcı tanımlı türleri program varlıklarına iliştirilebilecek ve çalışma zamanında alınabilecek şekilde genelleştirir. Programlar, ***öznitelikleri***tanımlayarak ve kullanarak bu ek bildirime dayalı bilgileri belirtir.

Aşağıdaki örnek, ilişkili belgelerinin bağlantılarını sağlamak için program varlıklarına yerleştirilebilecek bir `HelpAttribute` özniteliği bildirir.

[!code-csharp[AttributeDefined](../../../samples/snippets/csharp/tour/attributes/Program.cs#L3-L20)]

Tüm öznitelik sınıfları, standart kitaplık tarafından sunulan <xref:System.Attribute> temel sınıfından türetilir. Öznitelikler, ilişkili bildirimden hemen önceki köşeli parantez içinde, adı ve bağımsız değişkenlerle birlikte uygulanabilir. Bir özniteliğin adı `Attribute`sonlanıyorsa, özniteliğe başvuruluyorsa adın bu bölümü atlanabilir. Örneğin `HelpAttribute` aşağıdaki gibi kullanılabilir.

[!code-csharp[AttributeApplied](../../../samples/snippets/csharp/tour/attributes/Program.cs#L22-L28)]

Bu örnek, `Widget` sınıfına bir `HelpAttribute` iliştirir. Bu, sınıfındaki `Display` yöntemine başka bir `HelpAttribute` ekler. Öznitelik sınıfının ortak oluşturucuları, özniteliği bir program varlığına eklendiğinde sağlanması gereken bilgileri denetler. Öznitelik sınıfının genel okuma-yazma özelliklerine (daha önce `Topic` özelliğine başvuru gibi) başvurarak ek bilgiler sunulabilir.

Öznitelikler tarafından tanımlanan meta veriler, yansıma kullanılarak çalışma zamanında okunabilir ve değiştirilebilir. Bu tekniği kullanarak belirli bir öznitelik istendiğinde, öznitelik sınıfı için Oluşturucu program kaynağında sağlanan bilgilerle çağrılır ve sonuçta elde edilen öznitelik örneği döndürülür. Özellikler aracılığıyla ek bilgiler sağlanmışsa, öznitelik örneği döndürülmeden önce bu özellikler verilen değerlere ayarlanır.

Aşağıdaki kod örneği, `Widget` sınıfı ve `Display` yöntemiyle ilişkili `HelpAttribute` örneklerinin nasıl alınacağını gösterir.

[!code-csharp[AttributeRead](../../../samples/snippets/csharp/tour/attributes/Program.cs#ReadAttributes)]

>[!div class="step-by-step"]
>[Öncekini](delegates.md)
