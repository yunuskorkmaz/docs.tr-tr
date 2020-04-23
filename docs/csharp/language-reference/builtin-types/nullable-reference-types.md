---
title: Nullable başvuru türleri - C# referans
description: C# nullable referans türleri ve bunları nasıl kullanacağı hakkında bilgi edinin
ms.date: 04/06/2020
ms.openlocfilehash: cb61b162b06faa51faabbcdd91e55618cdeaca73
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102703"
---
# <a name="nullable-reference-types-c-reference"></a>Nullable başvuru türleri (C# başvurusu)

> [!NOTE]
> Bu makale, geçersiz başvuru türlerini kapsar. Ayrıca geçersiz [değer türlerini](nullable-value-types.md)de bildirebilirsiniz.

Nullable başvuru türleri C# 8.0 ile başlayan kullanılabilir, *nullable farkında bağlamında*tercih kodu . Nullable başvuru türleri, null statik analiz uyarıları ve [null-affgiving işleci](../operators/null-forgiving.md) isteğe bağlı dil özellikleridir. Tümü varsayılan olarak kapatılır. *Nullable bağlam* yapı ayarları kullanılarak proje düzeyinde veya pragmas kullanılarak kod olarak denetlenir.

 Geçersiz bir farkında bağlamda:

- Bir başvuru türünden `T` bir değişken null olmayan olarak başharfe alınmalıdır ve `null`asla .
- `T?` Başvuru türünden bir değişken, `null` başvurudan `null`çıkmadan `null` önce karşı denetlenmeli veya atanmış olabilir.
- Bir `m` tür `T?` değişkeni, `m!`'deki gibi hükümsüz affedici işleci uyguladığınızda geçersiz olarak kabul edilir.

Nullable olmayan bir başvuru türü `T` ile nullable başvuru `T?` türü arasındaki ayrımlar, derleyicinin önceki kuralları yorumlaması tarafından uygulanır. Bir tür `T` değişkeni ve `T?` bir tür değişkeni aynı .NET türüyle temsil edilir. Aşağıdaki örnek, nullable olmayan bir dize ve nullable dize bildirir ve sonra null-affgiving işleci olmayan bir dize bir değer atamak için kullanır:

:::code language="csharp" source="snippets/NullableReferenceTypes.cs" id="SnippetCoreSyntax":::

Değişkenler `notNull` ve `nullable` her ikisi de <xref:System.String> türü ile temsil edilir. Nullable ve nullable türleri her ikisi de aynı tür olarak depolanır olduğundan, nullable başvuru türü kullanarak izin verilmez birkaç konum vardır. Genel olarak, nullable başvuru türü taban sınıf veya uygulanan arabirim olarak kullanılamaz. Nullable başvuru türü herhangi bir nesne oluşturma veya tür sınaması ifadesinde kullanılamaz. Geçersiz bir başvuru türü, üye erişim ifadesitürü olamaz. Aşağıdaki örnekler bu yapıları gösterir:

```csharp
public MyClass : System.Object? // not allowed
{
}

var nullEmpty = System.String?.Empty; // Not allowed
var maybeObject = new object?(); // Not allowed
try
{
    if (thing is string? nullableString) // not allowed
        Console.WriteLine(nullableString);
} catch (Exception? e) // Not Allowed
{
    Console.WriteLine("error");
}
```

## <a name="nullable-references-and-static-analysis"></a>Nullable referanslar ve statik analiz

Önceki bölümdeki örnekler, geçersiz başvuru türlerinin doğasını göstermektedir. Nullable başvuru türleri yeni sınıf türleri değil, varolan başvuru türlerinde ek açıklamalardır. Derleyici, kodunuzda olası null başvuru hatalarını bulmanıza yardımcı olmak için bu ek açıklamaları kullanır. Nullable olmayan başvuru türü ile nullable başvuru türü arasında çalışma süresi farkı yoktur. Derleyici, nullable olmayan başvuru türleri için herhangi bir çalışma zamanı denetimi eklemez. Faydaları derleme zaman analizinde yer alıyor. Derleyici, kodunuzdaki olası null hatalarını bulmanıza ve düzeltmenize yardımcı olan uyarılar oluşturur. Niyetinizi beyan ekarsınız ve derleyici, kodunuz bu amaca aykırı olduğunda sizi uyarır.

Nullable etkin bir bağlamda, derleyici herhangi bir başvuru türünde değişkenler üzerinde statik çözümleme gerçekleştirir, hem nullable ve unnullable. Derleyici, her başvuru değişkeninin null durumunu *null* veya *belki de null*olarak izler. Nullable olmayan bir başvurunun varsayılan durumu *null değildir.* Nullable başvuruvarsayılan durumu *belki null*.

Nullable olmayan başvuru türleri her zaman null durumları *null olmadığından*dereference için güvenli olmalıdır. Bu kuralı uygulamak için derleyici, nullable olmayan bir başvuru türü null olmayan bir değere başharfe sahip değilse uyarılar yayınlar. Yerel değişkenler beyan edildikleri yere atanmalıdır. Her yapıcı, her alanı, kendi gövdesinde, bir yapıcı olarak adlandırılan veya bir alan başharfi kullanarak atamalıdır. Derleyici, durumu *belki null*olan bir başvuruya geçersiz bir başvuru atanmışsa uyarılar yayınlar. Ancak, nullable olmayan bir başvuru *null olmadığından,* bu değişkenler de-referenced olduğunda hiçbir uyarı verilir.

Nullable başvuru türleri başharfe `null`atılabilir veya . Bu nedenle, statik çözümleme, bir değişkenin başvurudan kaybolmadan önce *null olmadığını* belirlemelidir. Nullable başvuru belki null *olarak*belirlenirse, nullable olmayan bir referans değişkenine atanamaz. Aşağıdaki sınıf aşağıdaki uyarılara örnek gösterir:

:::code language="csharp" source="snippets/NullableReferenceTypes.cs" id="SnippetClassWithNullable":::

Aşağıdaki snippet derleyicinin bu sınıfı kullanırken uyarıları nereye yayır gösterir:

:::code language="csharp" source="snippets/NullableReferenceTypes.cs" id="SnippetLocalWarnings":::

Önceki örnekler, başvuru değişkenlerinin null durumunu belirlemek için derleyicinin statik çözümlemesi gösterir. Derleyici, çözümlemesi için geçersiz denetimler ve atamalar için dil kuralları uygular.  Derleyici yöntem veya özelliklerin anlamtları hakkında varsayımlarda bulunamaz. Null denetimleri gerçekleştiren yöntemleri çağırırsanız, derleyici bu yöntemlerin bir değişkenin null durumunu etkilediğini bilemiyor. Derlemeyi bağımsız değişkenlerin ve döndürücü değerlerin anlambilimi hakkında bilgilendirmek için API'lerinize ekleyebileceğiniz birkaç öznitelik vardır. Bu öznitelikler .NET Core kitaplıklarında birçok yaygın API'ye uygulanmıştır. Örneğin, <xref:System.String.IsNullOrEmpty%2A> güncelleştirildi ve derleyici bu yöntemi doğru bir şekilde null denetim olarak yorumlar. Null state statik çözümlemesi için geçerli öznitelikler hakkında daha fazla bilgi için, [Nullable öznitelikleri](../attributes/nullable-analysis.md)makaleye bakın.

## <a name="setting-the-nullable-context"></a>Nullable bağlamı ayarlama

Nullable bağlamı denetlemenin iki yolu vardır. Proje düzeyinde, proje ayarını `<Nullable>enable</Nullable>` ekleyebilirsiniz. Tek bir C# kaynak dosyasında, `#nullable enable` nullable bağlamı etkinleştirmek için pragma ekleyebilirsiniz. [Nullable bir strateji belirleme](../../nullable-migration-strategies.md)ile ilgili makaleye bakın.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi [için, C# dil belirtimi](~/_csharplang/spec/introduction.md)için aşağıdaki önerilere bakın:

- [Boş değer atanabilir başvuru türleri](~/_csharplang/proposals/csharp-8.0/nullable-reference-types.md)
- [Taslak nullable referans türleri belirtimi](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md)

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [Boş değer atanabilen değer türleri](nullable-value-types.md)
