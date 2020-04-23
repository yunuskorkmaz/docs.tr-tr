---
title: Nullable başvuru türlerini kullanmak için kod tabanınızı güncelleştirin
description: Nullable başvuru türlerini kullanmak için kod tabanınızı yükseltmek için en iyi stratejiyi seçin.
ms.technology: csharp-null-safety
ms.date: 07/31/2019
ms.openlocfilehash: b4a10863aea5c47b47c2a017afb20786b1e67528
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82103529"
---
# <a name="update-libraries-to-use-nullable-reference-types-and-communicate-nullable-rules-to-callers"></a>Geçersiz başvuru türlerini kullanmak ve arayanlara geçersiz kuralları iletmek için kitaplıkları güncelleştirme

[Nullable başvuru türlerinin](nullable-references.md) eklenmesi, her değişken `null` için bir değere izin verilip verilmediğini veya beklenmediğini bildirebileceğiniz anlamına gelir. Buna ek olarak, bir dizi `AllowNull`öznitelik uygulayabilirsiniz: `NotNullIfNotNull` , , `DisallowNull` `MaybeNull` `NotNull` `NotNullWhen`, , `MaybeNullWhen`, , ve tamamen bağımsız değişken ve dönüş değerleri null durumları açıklamak için. Bu kod yazmak gibi büyük bir deneyim sağlar. Nullable olmayan bir değişken ' olarak `null`ayarlanmış olabilir uyarılar alırsınız. Geçersiz bir değişken, başvurudan çıkmadan önce null-check-checked değilse uyarılar alırsınız. Kitaplıklarınızı güncellemek zaman alabilir, ancak ödemeler buna değer. Derleyiciye bir `null` değere *ne zaman* izin verildiği veya ne zaman yasakolduğu hakkında ne kadar çok bilgi sağlarsanız, API'nizin kullanıcıları o kadar iyi uyarılar alır. Tanıdık bir örnekle başlayalım. Kitaplığınızın kaynak dizesini almak için aşağıdaki API'ye sahip olduğunu düşünün:

```csharp
bool TryGetMessage(string key, out string message)
```

Önceki örnek .NET'teki tanıdık `Try*` deseni izler. Bu API için iki başvuru `key` bağımsız `message` değişkeni vardır: ve parametre. Bu API, bu bağımsız değişkenlerin nullness ile ilgili aşağıdaki kurallara sahiptir:

- Arayanlar için `key`argüman `null` olarak geçmemelidir.
- Arayanlar, değeri bağımsız değişken `null` olarak olan `message`bir değişkeni geçirebilir.
- `TryGetMessage` Yöntem dönerse, `true`değeri null `message` değildir. İade değeri `false,` `message` (ve null durumu) değeri ise null.

Kural tamamen `key` değişken türü ile ifade `key` edilebilir: nullable olmayan bir referans türü olmalıdır. Parametre `message` daha karmaşıktır. Bu `null` argüman olarak izin verir, ama garanti, `out` başarı, bu argüman null değildir. Bu senaryolar için, beklentileri açıklamak için daha zengin bir kelime gerekir.

Kitaplığınızı geçersiz başvurular için güncelleştirmek, bazı `?` değişkenlere ve tür adlarına serpintiden daha fazlasını gerektirir. Önceki örnek, API'lerinizi incelemeniz ve her giriş bağımsız değişkeni için beklentilerinizi göz önünde bulundurmanız gerektiğini gösterir. İade değeri garantilerini ve yöntemin `out` `ref` iadesi üzerine herhangi bir veya bağımsız değişkeni göz önünde bulundurun. Ardından bu kuralları derleyiciye iletin ve derleyici arayanlar bu kurallara uymadığında uyarılar sağlar.

Bu iş zaman alır. Diğer gereksinimleri ve teslim edilebilirleri dengelerken kitaplığınızı veya uygulamanızı geçersiz kılınabilir hale getirecek stratejilerle başlayalım. Geçersiz başvuru türlerini etkinleştiren devam eden geliştirmeyi nasıl dengelersiniz göreceğiniz. Genel tür tanımları için zorlukları öğreneceksiniz. Tek tek API'larda ön ve sonrası koşulları açıklamak için öznitelikleri uygulamayı öğreneceksiniz.

## <a name="choose-a-strategy-for-nullable-reference-types"></a>Nullable başvuru türleri için bir strateji seçin

İlk seçenek, geçersiz başvuru türlerinin varsayılan olarak açık mı yoksa kapalı mı olması gerektiğidir. İki stratejiniz var:

- Tüm proje için geçersiz başvuru türlerini etkinleştirin ve hazır olmayan kodda devre dışı edin.
- Yalnızca nullable başvuru türleri için açıklamalı olan kod için nullable başvuru türlerini etkinleştirin.

İlk strateji, geçersiz başvuru türleri için güncellerken kitaplığa diğer özellikler eklerken en iyi şekilde çalışır. Tüm yeni gelişme geçersiz farkındadır. Varolan kodu güncelleştirerken, bu sınıflarda nullable başvuru türlerini etkinleştirin.

Bu ilk stratejiyi izleyerek aşağıdakileri yaparsınız:

1. Öğeyi `<Nullable>enable</Nullable>` *csproj* dosyalarınıza ekleyerek tüm proje için nullable başvuru türlerini etkinleştirin.
1. Projenizdeki `#nullable disable` her kaynak dosyaya pragma ekleyin.
1. Her dosya üzerinde çalışırken, pragma kaldırın ve herhangi bir uyarı adresi.

Bu ilk strateji, her dosyaya pragma eklemek için daha ön çalışma vardır. Avantajı, projeye eklenen her yeni kod dosyasının boşalınabilen etkin olmasıdır. Herhangi bir yeni iş farkında geçersiz olacaktır; yalnızca varolan kodun güncelleştirilmesi gerekir.

İkinci strateji, kitaplık genellikle kararlıysa daha iyi çalışır ve geliştirmenin ana odak noktası geçersiz başvuru türlerini benimsemektir. API'lere açıklama eklerken geçersiz başvuru türlerini açarsınız. Bitirdikten sonra, tüm proje için geçersiz başvuru türlerini etkinleştirin.

Bu ikinci stratejiyi takip ederek aşağıdakileri yaparsınız:

1. Nullable `#nullable enable` farkında yapmak istediğiniz dosyaya pragma ekleyin.
1. Tüm uyarıları ele alın.
1. Tüm kitaplığı geçersiz kılınana kadar bu ilk iki adıma devam edin.
1. Öğeyi `<Nullable>enable</Nullable>` *csproj* dosyalarınıza ekleyerek tüm proje için geçersiz türleri etkinleştirin.
1. Pragmaları `#nullable enable` kaldırın, çünkü artık ihtiyaç duyulmaz.

Bu ikinci strateji daha az iş ön vardır. Takas, yeni bir dosya oluşturduğunuzda ilk görevin pragmayı eklemek ve onu geçersiz kılınabilir hale getirmek olmasıdır. Ekibinizdeki herhangi bir geliştirici unutursa, bu yeni kod artık tüm kodu geçersiz kılmak için birikme çalışmasının biriktirme listesindedir.

Seçtiğiniz bu stratejilerden hangisi, projenizde ne kadar etkin geliştirme nin gerçekleştiğine bağlıdır. Projeniz ne kadar olgun ve istikrarlı sayılsa, ikinci strateji de o kadar iyi. Ne kadar çok özellik geliştirilirse, ilk strateji o kadar iyi.

## <a name="should-nullable-warnings-introduce-breaking-changes"></a>Geçersiz uyarılar kırılma değişikliklerine neden olmalı mı?

Nullable başvuru türlerini etkinleştirmeden önce, değişkenler *geçersiz olarak*kabul edilir. Nullable başvuru türlerini etkinleştirdikten sonra, tüm bu değişkenler *nullable değildir.* Derleyici, bu değişkenler null olmayan değerlere başharflemedeğilse uyarılar verir.

Olası bir diğer uyarı kaynağı da, değer başharfe atılmamışsa iade değerleridir.

Derleyici uyarılarıele ilk adım, bağımsız `?` değişkenlerin veya iade değerlerinin ne zaman null olabileceğini belirtmek için parametre ve iade türlerinde ek açıklamalar kullanmaktır. Başvuru değişkenleri null olmamalıdır, özgün bildirimi doğrudur. Bunu yaptığınızda, amacınız sadece uyarıları düzeltmek değildir. Daha önemli amaç, derleyicinin olası null değerleri için niyetinizi anlamasını sağlamaktır. Uyarıları incelerken, kitaplığınız için bir sonraki önemli kararınızı verirsiniz. Tasarım amacınızı daha net bir şekilde iletmek için API imzalarını değiştirmeyi düşünüyor musunuz? Daha önce incelenen `TryGetMessage` yöntem için daha iyi bir API imzası olabilir:

```csharp
string? TryGetMessage(string key);
```

İade değeri başarı veya başarısızlık gösterir ve değer bulunursa değeri taşır. Çoğu durumda, API imzalarını değiştirmek boş değerleri nasıl ilettiklerini artırabilir.

Ancak, genel kitaplıklar veya büyük kullanıcı tabanlarına sahip kitaplıklar için, api imza değişiklikleri sunmamayı tercih edebilirsiniz. Bu gibi durumlar ve diğer yaygın desenler için, bir bağımsız değişken veya `null`iade değeri ne zaman olabilir daha net tanımlamak için öznitelikleri uygulayabilirsiniz. API'nizin yüzeyini değiştirmeyi düşünseniz de düşünmeseniz de, tür ek açıklamalarının bağımsız `null` değişkenler veya döndürme değerleri için değerleri açıklamak için tek başına yeterli olmadığını görürsünüz. Bu gibi durumlarda, bir API'yi daha net açıklamak için öznitelikleri uygulayabilirsiniz.

## <a name="attributes-extend-type-annotations"></a>Öznitelikler tür ek açıklamalarını genişletir

Değişkenlerin null durumu hakkında ek bilgi ifade etmek için çeşitli öznitelikler eklenmiştir. C# 8'den önce yazdığınız tüm kodlar nullable referans türlerini tanıttı *null habersiz*oldu. Bu, herhangi bir başvuru türü değişkeninin null olabileceği, ancak null denetimlerin gerekli olmadığı anlamına gelir. Bir kez kodunuzu *farkında geçersiz*olduğunda, bu kurallar değişir. Referans türleri hiçbir `null` zaman değer olmamalıdır ve geçersiz başvuru `null` türleri referans gösterilmeden önce karşı denetlenmelidir.

API senaryoda gördüğünüz gibi, API'lerinizin `TryGetValue` kuralları büyük olasılıkla daha karmaşıktır. API'lerinizin çoğu, değişkenlerin ne zaman olabilir veya `null`olamaz için daha karmaşık kurallara sahiptir. Bu gibi durumlarda, bu kuralları ifade etmek için öznitelikleri kullanırsınız. API'nizin anlambilimini açıklayan öznitelikler, [geçersiz çözümlemesi etkileyen Öznitelikler](./language-reference/attributes/nullable-analysis.md)makalesinde bulunur.

## <a name="generic-definitions-and-nullability"></a>Genel tanımlar ve nullability

Genel türlerin ve genel yöntemlerin null durumunu doğru bir şekilde iletmek özel bakım gerektirir. Bu, nullable değer türü ve nullable referans türü temelde farklı olduğu gerçeğinden kaynaklanmaktadır. An, `int?` derleyici tarafından eklenen bir `string?` öznitelik ile ise eşanlamlıdır. `string` `Nullable<int>` Sonuç olarak derleyici bir `T?` veya bir `T` `class` `struct`olup olmadığını bilmeden doğru kod oluşturamaz.

Bu, kapalı bir genel tür için tür bağımsız değişkeni olarak geçersiz bir türü (değer türü veya başvuru türü) kullanamayacağınız anlamına gelmez. Her `List<string?>` `List<int?>` ikisi de ve `List<T>`geçerli anlık vardır.

Bunun anlamı, kısıtlamalar olmadan genel `T?` bir sınıf veya yöntem bildiriminde kullanamadığınızdır. Örneğin, <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable%7B%60%600%7D)?displayProperty=nameWithType> döndürmek `T?`için değiştirilmez. Bu sınırlamayı, kısıtlama yı `struct` `class` veya kısıtlamayı ekleyerek aşabilirsiniz. Bu kısıtlamalardan herhangi biriyle, derleyici hem de `T` . `T?`

Genel bir tür bağımsız değişkeni için kullanılan türlerin nullable olmayan türleri olarak kısıtlamak isteyebilirsiniz. Bunu, bu tür `notnull` bağımsız değişkenine kısıtlama ekleyerek yapabilirsiniz. Bu kısıtlama uygulandığında, tür bağımsız değişkeni nullable türü olmamalıdır.
