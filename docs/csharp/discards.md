---
title: Atarsa-C# Kılavuzu
description: ", Atanmamış, discardable değişkenleri ve atma 'un kullanılabileceği yollarla ilgili olarak, C# ' nin atma desteğini açıklar."
ms.technology: csharp-fundamentals
ms.date: 09/22/2020
ms.openlocfilehash: eefa81d3bd8d56c9296e01533aaf93c4725323a3
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102104958"
---
# <a name="discards---c-guide"></a>Atarsa-C# Kılavuzu

C# 7,0 ' den itibaren C#, uygulama kodunda kasıtlı olarak kullanılmamış olan yer tutucu değişkenleri olan atma 'yı destekler. Atma, atanmamış değişkenlere eşdeğerdir; Bunlar bir değere sahip değildir. Bir atma, derleyici ve kodunuzu okuyan diğerleri için amacı iletişim kurar: bir ifadenin sonucunu yok saymayı amaçlıyorsanız. Bir ifadenin sonucunu, bir tanımlama grubu ifadesinin bir veya daha fazla üyesini, `out` bir yönteme parametre veya bir model eşleştirme ifadesinin hedefini yok saymanız gerekebilir.

Yalnızca tek bir atma değişkeni olduğundan, bu değişken, depolama alanı bile ayrılmamış olabilir. Atma, bellek ayırmalarını azaltabilir. Atarsa, kodunuzun amacını açık hale getirir. Okunabilirliği ve bakım ve bakım özelliklerini geliştirir.

Bir değişkenin, adı olarak alt çizgi () atayarak bir atma olduğunu belirtirsiniz `_` . Örneğin, aşağıdaki yöntem çağrısı, birinci ve ikinci değerlerin dıştığı bir tanımlama grubu döndürür. `area` , önceden tanımlanmış bir değişken tarafından döndürülen üçüncü bileşene ayarlanır `GetCityInformation` :

```csharp
(_, _, area) = city.GetCityInformation(cityName);
```

C# 9,0 ' den başlayarak, bir lambda ifadesinin kullanılmayan giriş parametrelerini belirtmek için atarsa ' u kullanabilirsiniz. Daha fazla bilgi için [lambda ifadeleri](language-reference/operators/lambda-expressions.md) makalesinin [lambda ifadesinin giriş parametreleri](language-reference/operators/lambda-expressions.md#input-parameters-of-a-lambda-expression) bölümüne bakın.

`_`Geçerli bir atma olduğunda, değerini alma veya bir atama işleminde kullanma girişimi, "' \_ ' adı geçerli bağlamda mevcut değil" DERLEYICI hatası CS0301 oluşturur. Bu hataya `_` bir değer atanmadığından ve bir depolama konumu atanmayabilir. Gerçek bir değişkense, önceki örnekte olduğu gibi birden fazla değeri atlamadınız.

## <a name="tuple-and-object-deconstruction"></a>Demet ve nesne oluşturmayı kaldırma

Atma, uygulama kodunuz bazı demet öğeleri kullandığında ancak diğerlerini yoksaytığında tanımlama grupları ile çalışma konusunda faydalıdır. Örneğin, aşağıdaki yöntem, `QueryCityDataForYears` şehir adı, alanı, yıl, bu yıl için şehir popülasyonu, ikinci yıl ve bu ikinci yıl için şehir popülasyonu döndürür. Örnek, bu iki yıl arasındaki popülasyondaki değişikliği gösterir. Kayıt kümesinden kullanılabilen veriler, şehir alanıyla ilgilentik ve tasarım zamanında şehir adını ve iki tarihi biliyoruz. Sonuç olarak, yalnızca kayıt düzeninde depolanan iki popülasyon değeri ile ilgileniyoruz ve kalan değerlerini atma olarak işleyebilir.  

:::code language="csharp" source="snippets/discards/discard-tuple.cs" ID="DiscardTupleMember" :::

Atma ile tanımlama gruplarını kaldırma hakkında daha fazla bilgi için bkz. [tanımlama gruplarını ve diğer türleri kaldırma](deconstruct.md#deconstructing-tuple-elements-with-discards).

`Deconstruct`Bir sınıf, yapı veya arabirim yöntemi Ayrıca bir nesneden belirli bir veri kümesini almanıza ve oluşturmanıza olanak sağlar. Yalnızca ayrıştırılmış değerlerin yalnızca bir alt kümesiyle çalışmayı ilgileniyorsanız, atma ' yı kullanabilirsiniz. Aşağıdaki örnek, bir `Person` nesnesini dört dizeye (ilk ve son adlar, şehir ve eyalet) ayırır, ancak son adı ve durumu atar.

:::code language="csharp" source="snippets/discards/discard-class.cs" :::

Kullanıcı tanımlı türleri atma ile kaldırma hakkında daha fazla bilgi için bkz. [tanımlama gruplarını ve diğer türleri kaldırma](deconstruct.md#deconstructing-a-user-defined-type-with-discards).

## <a name="pattern-matching-with-switch"></a>İle eşleşen desenler `switch`

*Atma stili* , [anahtar ifadesiyle](language-reference/operators/switch-expression.md)birlikte bir model eşleme içinde kullanılabilir. Dahil her bir ifade, `null` her zaman atma düzeniyle eşleşir.

Aşağıdaki örnek, bir `ProvidesFormatInfo` `switch` nesnenin uygulama ve test olup olmadığını belirleyen bir ifade kullanan bir yöntemi tanımlar <xref:System.IFormatProvider> `null` . Ayrıca, başka bir türdeki null olmayan nesneleri işlemek için de atma modelini kullanır.

:::code language="csharp" source="snippets/discards/discard-pattern2.cs" ID="DiscardSwitchExample" :::

## <a name="calls-to-methods-with-out-parameters"></a>Parametrelere sahip yöntemlere çağrılar `out`

`Deconstruct`Kullanıcı tanımlı bir türü (bir sınıf, yapı veya arabirim örneği) oluşturmak için yöntemini çağırırken bağımsız değişkenlerin değerlerini atabilirsiniz `out` . Ancak `out` parametre ile herhangi bir yöntemi çağırırken bağımsız değişkenlerin değerini de atabilirsiniz `out` .

Aşağıdaki örnek, bir tarihin dize temsilinin geçerli kültür içinde geçerli olup olmadığını belirlemek için [DateTime. Trypari (dize, Out DateTime)](<xref:System.DateTime.TryParse(System.String,System.DateTime@)>) yöntemini çağırır. Örnek yalnızca tarih dizesini doğrulamaya ve tarihi ayıklamak için ayrıştırılmaya karşı düşünüldüğünde, `out` yöntemin bağımsız değişkeni bir atma işlemi olur.

:::code language="csharp" source="snippets/discards/discard-out1.cs" ID="DiscardOutParameter" :::

## <a name="a-standalone-discard"></a>Tek başına atma

Yok saymayı seçtiğiniz herhangi bir değişkeni belirtmek için tek başına atmayı kullanabilirsiniz. Bir bağımsız değişkenin null olmamasını sağlamak için bir atama kullanmak tipik bir kullanımdır. Aşağıdaki kod bir atamayı zorlamak için bir atma kullanır. Atamanın sağ tarafı, bağımsız değişken olduğunda bir oluşturmak için [null birleştirme işlecini](language-reference/operators/null-coalescing-operator.md) kullanır <xref:System.ArgumentNullException?displayProperty=nameWithType> `null` . Kod, atamanın sonucuna ihtiyaç duymazsa, atılır. İfade null denetimi zorlar. Atma amacınızı belirler: atamanın sonucu gerekli değildir veya kullanılmaz.

:::code language="csharp" source="snippets/discards/standalone-discard1.cs" ID="ArgNullCheck" :::

Aşağıdaki örnek, <xref:System.Threading.Tasks.Task> zaman uyumsuz bir işlem tarafından döndürülen nesneyi yoksaymak için tek başına atmayı kullanır. Görevin atanması, işlemin tamamlanmasında olduğu gibi oluşturduğu özel durumu gizleme etkisine sahiptir. Amacınızı açık hale getirir: `Task` ' ı atmak ve bu zaman uyumsuz işlemden oluşturulan tüm hataları yoksaymak istiyorsunuz.

:::code language="csharp" source="snippets/discards/standalone-discard1.cs" ID="SnippetDiscardTask" :::

Görevi bir atılsın atamadan aşağıdaki kod bir derleyici uyarısı oluşturur:

:::code language="csharp" source="snippets/discards/standalone-discard1.cs" ID="SnippetNoDiscardTask" :::

> [!NOTE]
> Bir hata ayıklayıcı kullanarak önceki iki örnekten birini çalıştırırsanız, özel durum oluştuğunda hata ayıklayıcı programı durdurur. Bir hata ayıklayıcı ekli olmadığında, her iki durumda da sessizce yok sayılır.

`_` aynı zamanda geçerli bir tanımlayıcıdır. Desteklenen bir bağlam dışında kullanıldığında, `_` atma olarak kabul edilir, ancak geçerli bir değişken olarak değerlendirilir. Adlı bir tanımlayıcı `_` zaten kapsamda ise, `_` tek başına atma olarak kullanılması şu şekilde olabilir:

- İstenen atma değeri atanarak kapsam içi değişkenin değerini yanlışlıkla değiştirme `_` . Örnek:
   :::code language="csharp" source="snippets/discards/standalone-discard2.cs" ID="VariableIdentifier" :::
- Tür güvenliğini ihlal eden bir derleyici hatası. Örnek:
   :::code language="csharp" source="snippets/discards/standalone-discard2.cs" ID="VariableTypeInference" :::
- Derleyici hatası CS0136, " \_ Bu ad bir yerel veya parametre tanımlamak için kapsayan bir yerel kapsamda kullanıldığı için," ' ' adlı yerel veya parametre bu kapsamda bildirilemez. " Örnek:
   :::code language="csharp" source="snippets/discards/standalone-discard2.cs" ID="CannotRedeclare" :::

## <a name="see-also"></a>Ayrıca bkz.

- [Demetleri ve diğer türleri ayrıştırma](deconstruct.md)
- [`is` sözcükle](language-reference/keywords/is.md)
- [`switch` sözcükle](language-reference/keywords/switch.md)
