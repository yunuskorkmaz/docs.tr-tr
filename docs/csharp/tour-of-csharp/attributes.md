---
title: C# Öznitelikleri - C# dilinde bir tur
description: "C'deki öznitelikleri kullanarak bildirimsel programlama hakkında bilgi edinin #"
ms.date: 02/27/2020
ms.assetid: 753bcfe2-7ddd-4487-9513-ba70937fc8e9
ms.openlocfilehash: dc5b194c22fc2746ff8b0ab3e550e560a3666bbe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78159214"
---
# <a name="attributes"></a>Öznitelikler

C# programındaki türler, üyeler ve diğer varlıklar, davranışlarının belirli yönlerini denetleyen değiştiricileri destekler. Örneğin, bir yöntemin `public`erişilebilirliği , , `protected` `internal`, ve `private` değiştiriciler kullanılarak denetlenir. C# bu özelliği, kullanıcı tarafından tanımlanan bildirimsel bilgi türlerinin program varlıklarına eklenebilir ve çalışma zamanında alınabilecek şekilde genelleştirir. Programlar ***öznitelikleri***tanımlayarak ve kullanarak bu ek bildirim bilgilerini belirtir.

Aşağıdaki örnek, ilişkili `HelpAttribute` belgelerine bağlantılar sağlamak için program varlıklarına yerleştirilebilen bir öznitelik bildirir.

[!code-csharp[AttributeDefined](../../../samples/snippets/csharp/tour/attributes/Program.cs#L3-L20)]

Tüm öznitelik sınıfları, <xref:System.Attribute> standart kitaplık tarafından sağlanan taban sınıftan türetilmiştir. Öznitelikler, ilişkili bildirimden hemen önce kare parantez içinde, herhangi bir bağımsız değişkenle birlikte adlarını vererek uygulanabilir. Bir öznitelik adı sona `Attribute`ererse, öznitelik başvurulduğunda adın bu bölümü atlanabilir. Örneğin, `HelpAttribute` aşağıdaki gibi kullanılabilir.

[!code-csharp[AttributeApplied](../../../samples/snippets/csharp/tour/attributes/Program.cs#L22-L28)]

Bu örnek `HelpAttribute` `Widget` sınıfa a iliştirimi. Sınıftaki `HelpAttribute` yönteme `Display` bir tane daha ekler. Öznitelik sınıfının ortak oluşturucuları, öznitelik bir program varlığına iliştirildiğinde sağlanması gereken bilgileri denetler. Öznitelik sınıfının genel okuma-yazma özelliklerine (daha önce ki `Topic` özelliğe başvuru gibi) başvurarak ek bilgiler sağlanabilir.

Özniteliklertarafından tanımlanan meta veriler, yansıma kullanılarak çalışma zamanında okunabilir ve işlenebilir. Bu teknik kullanılarak belirli bir öznitelik istendiğinde, öznitelik sınıfının oluşturucusu program kaynağında sağlanan bilgilerle çağrılır ve ortaya çıkan öznitelik örneği döndürülür. Özellikler aracılığıyla ek bilgi sağlanmışsa, bu özellikler öznitelik örneği döndürülmeden önce verilen değerlere ayarlanır.

Aşağıdaki kod `HelpAttribute` `Widget` örneği, sınıfla ve yöntemiyle ilişkili örnekleri `Display` nasıl elde edilebildiğini gösterir.

[!code-csharp[AttributeRead](../../../samples/snippets/csharp/tour/attributes/Program.cs#ReadAttributes)]

>[!div class="step-by-step"]
>[Önceki](delegates.md)
