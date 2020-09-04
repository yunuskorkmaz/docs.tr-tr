---
description: Event-C# başvurusu
title: Event-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- event
- remove
- event_CSharpKeyword
- add
helpviewer_keywords:
- event keyword [C#]
ms.assetid: 7858fd85-153b-4259-85d0-6aa13c35f174
ms.openlocfilehash: dff93496dfeceaf67777abe0b02ee2d620b3a5ca
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89466046"
---
# <a name="event-c-reference"></a>Event (C# Başvurusu)

`event`Anahtar sözcüğü bir yayımcı sınıfında bir olay bildirmek için kullanılır.

## <a name="example"></a>Örnek

Aşağıdaki örnek, <xref:System.EventHandler> temel alınan temsilci türü olarak kullanan bir olayın nasıl bildirilemeyeceğini ve tetiklemeyeceğini gösterir. Ayrıca, genel <xref:System.EventHandler%601> temsilci türünü kullanmayı ve bir olaya abone olmayı ve bir olay işleyici yöntemi oluşturmayı gösteren tüm kod örneği için bkz. [.net yönergelerine uygun olan olayları yayımlama](../../programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md).

[!code-csharp[csrefKeywordsModifiers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#7)]

Olaylar, yalnızca bildirildiği sınıf veya yapı içinden çağrılabilir olan özel bir çok noktaya yayın temsilcisi türüdür (yayımcı sınıfı). Diğer sınıflar veya yapılar olaya abone olursa, yayımcı sınıfı olayı harekete geçirirse olay işleyicisi yöntemleri çağırılır. Daha fazla bilgi ve kod örnekleri için bkz. [Olaylar](../../programming-guide/events/index.md) ve [Temsilciler](../../programming-guide/delegates/index.md).

Olaylar [ortak](./public.md), [özel](./private.md), [korumalı](./protected.md), [iç](./internal.md), [korunan iç](./protected-internal.md)veya [özel korumalı](./private-protected.md)olarak işaretlenebilir. Bu erişim değiştiricileri, sınıfın kullanıcılarının olaya nasıl erişekullanabileceğinizi tanımlar. Daha fazla bilgi için bkz. [erişim değiştiricileri](../../programming-guide/classes-and-structs/access-modifiers.md).

## <a name="keywords-and-events"></a>Anahtar sözcükler ve olaylar

Aşağıdaki anahtar sözcükler olaylar için geçerlidir.

|Sözcükle|Açıklama|Daha fazla bilgi edinmek için|
|-------------|-----------------|--------------------------|
|[static](./static.md)|Sınıfın bir örneği mevcut olmasa bile, olayı her zaman çağıranlar için kullanılabilir hale getirir.|[Statik Sınıflar ve Statik Sınıf Üyeleri](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)|
|[virtual](./virtual.md)|Türetilmiş sınıfların, [override](./override.md) anahtar sözcüğünü kullanarak olay davranışını geçersiz kılmasına izin verir.|[Devralma](../../programming-guide/classes-and-structs/inheritance.md)|
|[sealed](./sealed.md)|Türetilmiş sınıflar için artık sanal olmadığını belirtir.||
|[Soyut](./abstract.md)|Derleyici `add` ve `remove` olay erişimcisi blokları oluşturmaz ve bu nedenle türetilen sınıfların kendi uygulamasını sağlaması gerekir.||

[Static](./static.md) anahtar sözcüğü kullanılarak bir olay statik olay olarak bildirilemez. Bu, sınıfın bir örneği mevcut olmasa bile herhangi bir zamanda olayı çağıranlar için kullanılabilir hale getirir. Daha fazla bilgi için bkz. [statik sınıflar ve statik sınıf üyeleri](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).

Bir olay [sanal](./virtual.md) anahtar sözcüğü kullanılarak sanal bir olay olarak işaretlenebilir. Bu, türetilmiş sınıfların [override](./override.md) anahtar sözcüğünü kullanarak olay davranışını geçersiz kılmasını sağlar. Daha fazla bilgi için bkz. [Devralma](../../programming-guide/classes-and-structs/inheritance.md). Sanal bir olayı geçersiz kılan bir olay, türetilmiş sınıflar için artık sanal olmadığını belirten [mühürlü](./sealed.md)da olabilir. Son olarak, bir olay [soyut](./abstract.md)olarak bildirilmelidir, bu da derleyicinin `add` ve olay erişimcisi bloklarını üretmeyeceği anlamına gelir `remove` . Bu nedenle türetilen sınıfların kendi uygulamasını sağlaması gerekir.

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# anahtar sözcükleri](./index.md)
- [add](./add.md)
- [temizlenmesine](./remove.md)
- [Değiştiriciler](index.md)
- [Temsilcileri birleştirme (çok noktaya yayın temsilcileri)](../../programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)
