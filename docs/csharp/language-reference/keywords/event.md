---
title: olay - C# Referans
ms.date: 07/20/2015
f1_keywords:
- event
- remove
- event_CSharpKeyword
- add
helpviewer_keywords:
- event keyword [C#]
ms.assetid: 7858fd85-153b-4259-85d0-6aa13c35f174
ms.openlocfilehash: eb1805ed55921497fea88e6b39989c876ef003d1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713564"
---
# <a name="event-c-reference"></a>olay (C# referansı)

Anahtar `event` kelime, yayımcı sınıfında bir olayı bildirmek için kullanılır.

## <a name="example"></a>Örnek

Aşağıdaki örnek, temel temsilci türü olarak <xref:System.EventHandler> kullanan bir olayın nasıl bildirilen ve yükseltilen gösterilmektedir. Genel <xref:System.EventHandler%601> temsilci türünün nasıl kullanılacağını ve bir olaya nasıl abone olunur ve bir olay işleyicisi yöntemini nasıl oluşturabilirsiniz'ı gösteren tam kod örneği [için ,.NET Framework Yönergelerine uygun olayların nasıl yayımlandırılabildiğini](../../programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)görün.

[!code-csharp[csrefKeywordsModifiers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#7)]

Olaylar, yalnızca beyan edildikleri sınıf veya yapı nın içinden çağrılabilen özel bir çok noktaya yayın temsilcisi türüdür (yayımcı sınıfı). Diğer sınıflar veya structs olay abone olursa, yayımcı sınıf olay yükseltir onların olay işleyici yöntemleri çağrılır. Daha fazla bilgi ve kod örnekleri [için, Bkz. Olaylar](../../programming-guide/events/index.md) ve [Temsilciler.](../../programming-guide/delegates/index.md)

Olaylar [genel,](./public.md) [özel,](./private.md) [korumalı,](./protected.md) [dahili,](./internal.md) [korumalı dahili](./protected-internal.md)veya [özel korumalı](./private-protected.md)olarak işaretlenebilir. Bu erişim değiştiriciler, sınıfın kullanıcılarının olaya nasıl erişebileceğini tanımlar. Daha fazla bilgi için [Erişim Değiştiriciler'e](../../programming-guide/classes-and-structs/access-modifiers.md)bakın.

## <a name="keywords-and-events"></a>Anahtar kelimeler ve olaylar

Aşağıdaki anahtar kelimeler olaylar için geçerlidir.

|Anahtar kelime|Açıklama|Daha fazla bilgi edinmek için|
|-------------|-----------------|--------------------------|
|[Statik](./static.md)|Sınıfın hiçbir örneği olmasa bile, olayı arayanların istediği zaman kullanılabilir hale getirir.|[Statik Sınıflar ve Statik Sınıf Üyeleri](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)|
|[virtual](./virtual.md)|Türetilen sınıfların [geçersiz kılma](./override.md) anahtar sözcük kullanarak olay davranışını geçersiz kılmasına izin verir.|[Devralma](../../programming-guide/classes-and-structs/inheritance.md)|
|[sealed](./sealed.md)|Türemiş sınıflar için artık sanal olmadığını belirtir.||
|[Soyut](./abstract.md)|Derleyici `add` ve `remove` olay erişimengellerini oluşturmaz ve bu nedenle türetilmiş sınıfların kendi uygulamalarını sağlaması gerekir.||

Statik [anahtar](./static.md) sözcük kullanılarak bir olay statik bir olay olarak ilan edilebilir. Bu, sınıfın hiçbir örneği olmasa bile olayı her zaman arayanların kullanımına açık hale getirir. Daha fazla bilgi için Statik [Sınıflar ve Statik Sınıf Üyeleri'ne](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)bakın.

Bir [olay, sanal](./virtual.md) anahtar sözcüğü kullanılarak sanal bir olay olarak işaretlenebilir. Bu, türetilen sınıfların [geçersiz kılma](./override.md) anahtar sözcük kullanarak olay davranışını geçersiz kılmasına olanak tanır. Daha fazla bilgi için [Bkz. Kalıtım.](../../programming-guide/classes-and-structs/inheritance.md) Sanal bir olayı geçersiz kılan bir olay, türemiş sınıflar için artık sanal olmadığını belirten [mühürlenebilir.](./sealed.md) Son olarak, bir olay [soyut](./abstract.md)olarak ilan edilebilir, bu `add` da `remove` derleyicinin ve olay erişimengellerini oluşturamayacağı anlamına gelir. Bu nedenle türemiş sınıflar kendi uygulamalarını sağlamalıdır.

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Kelimeler](./index.md)
- [Ekle](./add.md)
- [Kaldırmak](./remove.md)
- [Değiştiriciler](index.md)
- [Temsilciler nasıl birleştirilir (Çok Noktaya Yayın Temsilcileri)](../../programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)
