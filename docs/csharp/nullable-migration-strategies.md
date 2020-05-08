---
title: Kod tabanınızı null yapılabilir başvuru türlerini kullanacak şekilde güncelleştirin
description: Kod tabanınızı, null yapılabilir başvuru türlerini kullanacak şekilde yükseltmek için en iyi stratejiyi seçin.
ms.technology: csharp-null-safety
ms.date: 07/31/2019
ms.openlocfilehash: 5909eb9ffe1f5398fc2eb74848b82f8fe9516548
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975335"
---
# <a name="update-libraries-to-use-nullable-reference-types-and-communicate-nullable-rules-to-callers"></a>Kitaplıkları null yapılabilir başvuru türleri kullanacak şekilde güncelleştirme ve arayanlara null olabilecek kuralları iletişim kurma

[Null yapılabilir başvuru türlerinin](nullable-references.md) eklenmesi, her değişken için bir `null` değere izin verilip verilmeyeceğini veya beklenmediğini bildirebilmeniz anlamına gelir. Ayrıca, bağımsız değişkenin ve dönüş değerlerinin null durumlarını tamamen anlatmak `AllowNull`için `DisallowNull`, `MaybeNull`, `NotNull`, `NotNullWhen`, `MaybeNullWhen`, ve `NotNullIfNotNull` birçok öznitelik uygulayabilirsiniz. Bu, kod yazarken harika bir deneyim sağlar. Null yapılamayan bir değişken olarak `null`ayarlanmayabilir. Nullable bir değişken, başvuru yapılmadan önce null olarak işaretli değilse uyarılar alırsınız. Kitaplıklarınızın güncelleştirilmesi zaman alabilir, ancak ödeme bu duruma göre yapılır. Bir `null` değere izin verildiğinde veya yasaklanmış *olduğunda* derleyiciye sağladığınız daha fazla bilgi, API 'nizin Kullanıcı tarafından daha iyi uyarıları alır. Tanıdık bir örnekle başlayalım. Kitaplığınızın bir kaynak dizesini almak için aşağıdaki API 'ye sahip olduğunu düşünün:

```csharp
bool TryGetMessage(string key, out string message)
```

Yukarıdaki örnek, .NET 'teki tanıdık `Try*` olan bir model izler. Bu API için iki başvuru bağımsız değişkeni vardır: `key` ve `message` parametresi. Bu API, bu bağımsız değişkenlerin nulldurumuyla ilgili aşağıdaki kurallara sahiptir:

- Çağıranlar için `null` `key`bağımsız değişken olarak geçmemelidir.
- Çağıranlar, değeri `null` bağımsız değişkeni olan bir değişken geçirebilir `message`.
- `TryGetMessage` Yöntemi döndürürse `true`, değeri null `message` değildir. Dönüş değeri `false,` `message` (ve null durumu) değeri null ise.

Kuralı `key` değişken türü ile tamamen ifade edilebilir: `key` null yapılamayan bir başvuru türü olmalıdır. `message` Parametresi daha karmaşıktır. Bağımsız değişken `null` olarak izin verir, ancak başarıyı, bu bağımsız değişkenin null olmadığını `out` garanti eder. Bu senaryolar için beklentileri betimleyen daha zengin bir sözlük gerekir.

Boş değer atanabilir başvurular için kitaplığınızın güncelleştirilmesi, bazı değişkenlerde ve tür `?` adlarından daha fazla spreninkini gerektirir. Yukarıdaki örnek, API 'lerinizi incelemeniz ve her giriş bağımsız değişkeni için beklentilerinizi göz önünde bulundurmanız gerektiğini gösterir. Dönüş değeri için garantiyi ve yöntemin dönüşi üzerinde `out` herhangi `ref` bir veya bağımsız değişkeni göz önünde bulundurun. Sonra bu kuralları derleyiciye iletmeyin ve bu kurallar tarafından çağıranlar olmadığında Derleyici uyarılar sağlar.

Bu iş zaman alır. Diğer gereksinimleri ve teslim edilebilirleri dengelarken, kitaplığınızı veya uygulamanızı null yapılabilir hale getirme stratejileriyle başlayalım. Devam eden geliştirmeyi nasıl dengeleyebilirsiniz, null yapılabilir başvuru türleri etkinleştiriliyor. Genel tür tanımları için zorluk öğrenirsiniz. Tek tek API 'lerde ön ve son koşulları betimleyen öznitelikler uygulamayı öğreneceksiniz.

## <a name="choose-a-strategy-for-nullable-reference-types"></a>Null yapılabilir başvuru türleri için bir strateji seçin

İlk seçenek, null yapılabilir başvuru türlerinin varsayılan olarak açık veya kapalı olması gerekip gerekmediğini belirtir. İki stratejileriniz vardır:

- Tüm proje için null yapılabilir başvuru türlerini etkinleştirin ve devre dışı olan kodda devre dışı bırakın.
- Yalnızca Nullable başvuru türleri için açıklama eklenmiş kod için null yapılabilir başvuru türlerini etkinleştirin.

İlk strateji, null yapılabilir başvuru türleri için güncelleştirdiğinizde, kitaplığa başka özellikler eklerken en iyi şekilde kullanılır. Tüm yeni geliştirmeler null yapılabilir. Mevcut kodu güncelleştirdiğinizde bu sınıflarda null yapılabilir başvuru türlerini etkinleştirirsiniz.

Bu ilk stratejiyi izleyerek şunları yapın:

1. `<Nullable>enable</Nullable>` Öğeyi *csproj* dosyalarınıza ekleyerek projenin tamamına ait null yapılabilir başvuru türlerini etkinleştirin.
1. `#nullable disable` Pragmayı projenizdeki her kaynak dosyasına ekleyin.
1. Her dosya üzerinde çalışırken, pragmayı kaldırın ve tüm uyarıları çözün.

Bu ilk stratejide, her dosyaya pragma eklemek için daha fazla yukarı iş vardır. Avantajı, projeye eklenen her yeni kod dosyasının null yapılabilir olmasını sağlar. Herhangi bir yeni iş, null yapılabilir. yalnızca var olan kodun güncellenmesi gerekiyor.

İkinci strateji, kitaplığın genellikle kararlı olması ve geliştirmenin ana odağının null yapılabilir başvuru türlerini benimsemeniz durumunda daha iyi bir şekilde çalışacaktır. API 'Leri not yazarken null yapılabilir başvuru türlerini açabilirsiniz. İşiniz bittiğinde, tüm proje için null yapılabilir başvuru türlerini etkinleştirirsiniz.

Bu ikinci stratejiyi izleyerek şunları yapın:

1. Null yapılabilir `#nullable enable` olmasını istediğiniz dosyaya pragma ekleyin.
1. Tüm uyarıları çözün.
1. Tüm kitaplığı null yapılabilir olarak farkında olana kadar bu ilk iki adıma devam edin.
1. `<Nullable>enable</Nullable>` Öğeyi *csproj* dosyalarınıza ekleyerek projenin tamamına ait boş değer atanabilir türleri etkinleştirin.
1. Artık gerekli `#nullable enable` olmadığından pragmaları kaldırın.

Bu ikinci stratejinin daha az iş ön ucu vardır. Zorunluluğunu getirir, yeni bir dosya oluşturduğunuz ilk görevin pragmasını eklemek ve null yapılabilir olduğunu fark edevidir. Takımınızdaki herhangi bir geliştirici unutur, bu yeni kod artık tüm kod Nullable olarak uyumlu hale getirmek için iş kapsamındedir.

Seçtiğiniz bu Stratejiler, projenizde ne kadar etkin geliştirme gerçekleştireceğinize bağlıdır. Projeniz ne kadar fazla olgun ve kararlı, ikinci strateji daha iyidir. Daha fazla geliştirmekte olan özellikler, ilk strateji daha iyidir.

## <a name="should-nullable-warnings-introduce-breaking-changes"></a>Null yapılabilir uyarılar, son değişiklikleri mi göstermelidir?

Null yapılabilir başvuru türlerini etkinleştirmeden önce, değişkenler *null yapılabilir zorunluluvou*olarak değerlendirilir. Null yapılabilir başvuru türlerini etkinleştirdikten sonra, bu değişkenlerin hepsi *null değer atanamaz*. Bu değişkenler null olmayan değerlere başlatılamıyorsa, derleyici uyarılar verebilir.

Büyük olasılıkla başka bir uyarı kaynağı, değer başlatılmamış olduğunda değerler döndürür.

Derleyici uyarılarını adresleyen ilk adım, parametre ve dönüş türleri `?` üzerinde ek açıklamaların kullanılması ve bağımsız değişkenlerin veya dönüş değerlerinin null olabileceğini göstermek için kullanılır. Başvuru değişkenleri null olmamalı, özgün bildirim doğru olur. Bunu yaparken hedefiniz yalnızca uyarıları düzeltemedi. Daha önemli hedef, derleyicinin olası null değerler için amacınızı anlaması sağlamaktır. Uyarıları incelerken, kitaplığınız için bir sonraki önemli kararına ulaşabilirsiniz. Tasarım amacınızı daha net bir şekilde iletmek için API imzalarını değiştirmeyi düşünmek istiyor musunuz? Daha önce incelenen `TryGetMessage` Yöntem için daha ıyı bir API imzası şu olabilir:

```csharp
string? TryGetMessage(string key);
```

Dönüş değeri başarılı veya başarısız olduğunu gösterir ve değer bulunursa değeri taşır. Çoğu durumda, API imzalarını değiştirmek, null değerleri nasıl ilettikleri iyileştirebilirler.

Ancak, genel kitaplıklar veya büyük Kullanıcı temellerine sahip kitaplıklar için herhangi bir API imza değişikliğine giriş yapmayı tercih edebilirsiniz. Bu durumlar ve diğer yaygın desenler için, bir bağımsız değişken veya dönüş değeri olabileceği zaman daha net bir şekilde tanımlanacak öznitelikler uygulayabilirsiniz `null`. API 'nizin yüzeyini değiştirmeyi göz önünde bulundurmayın, büyük olasılıkla tür ek açıklamalarını bağımsız değişkenlerin veya dönüş değerlerinin değerlerini tanımlamak `null` için yeterli olmadığını fark edeceksiniz. Bu örneklerde, bir API 'yi daha net bir şekilde anlatmak için öznitelikler uygulayabilirsiniz.

## <a name="attributes-extend-type-annotations"></a>Öznitelikler tür ek açıklamalarını Genişlet

Değişkenlerin null durumu hakkında ek bilgileri ifade etmek için çeşitli öznitelikler eklenmiştir. C# 8 ' den önce yazdığınız tüm kod null yapılabilir başvuru türleri olarak *null zorunluluvou*idi. Yani herhangi bir başvuru türü değişkeni null olabilir, ancak null denetimleri gerekli değildir. Kodunuz *Nullable olarak farkında*olduktan sonra bu kurallar değişir. Başvuru türleri asla `null` değer olmamalı ve null yapılabilir başvuru türleri başvurulmadan `null` önce denetlenmelidir.

`TryGetValue` API 'si senaryosuyla gördüğünüz gibi API 'lerinizin kuralları büyük olasılıkla daha karmaşıktır. API 'lerinizin birçoğu, değişkenlerin ne zaman veya ne zaman oluşturulabileceğine `null`ilişkin daha karmaşık kurallara sahiptir. Bu durumlarda, bu kuralları ifade etmek için öznitelikleri kullanacaksınız. API 'nizin semantiğini tanımlayan öznitelikler, [null yapılabilir Analizi etkileyen öznitelikler](./language-reference/attributes/nullable-analysis.md)hakkında makalesinde bulunur.

## <a name="generic-definitions-and-nullability"></a>Genel tanımlar ve null değer alabilirlik

Genel türlerin ve genel yöntemlerin null durumuna doğru bir şekilde iletişim kurmak için özel bakım yapılması gerekir. Bu, null olabilen bir değer türünün ve null olabilen bir başvuru türünün temelde farklı olduğu gerçekten farklıdır. , `int?` İçin `Nullable<int>`bir eş anlamlı olur, `string?` ancak `string` derleyici tarafından eklenen bir özniteliktir. Sonuç, derleyicisinin `T?` bir veya bir `T` `class` `struct`olduğunu bilmeksizin doğru kodu oluşturabileceği bir sonucudur.

Bu, kapalı bir genel türün tür bağımsız değişkeni olarak null yapılabilir bir tür (değer türü veya başvuru türü) kullanmayacağınız anlamına gelmez. Her `List<string?>` ikisi `List<int?>` de geçerli örneklerdir `List<T>`.

Bunun anlamı, kısıtlama olmadan genel bir sınıfta veya `T?` yöntem bildiriminde kullanmayacağınız anlamına gelir. Örneğin, <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable%7B%60%600%7D)?displayProperty=nameWithType> döndürülecek `T?`şekilde değiştirilmez. `struct` Ya `class` da kısıtlamasını ekleyerek bu sınırlamayı aşabilirsiniz. Bu kısıtlamalardan biri ile derleyici, hem hem de `T` için nasıl kod oluşturulacağını bilir. `T?`

Genel tür bağımsız değişkeni için kullanılan türleri null yapılamayan türler olacak şekilde kısıtlamak isteyebilirsiniz. Bunu, bu tür bağımsız değişkenine `notnull` kısıtlama ekleyerek yapabilirsiniz. Bu kısıtlama uygulandığında tür bağımsız değişkeni null yapılabilir bir tür olmamalıdır.

## <a name="late-initialized-properties-data-transfer-objects-and-nullability"></a>Gecikmeli başlatılan özellikler, Veri Aktarımı nesneler ve null değer düzeyi

Geç başlatılan özelliklerin null olabilmesini belirten, oluşturulduktan sonra ayarlanan anlamı, sınıfınızın özgün tasarım hedefini doğru bir şekilde ifade etmeye devam ettiğinden emin olmak için özel bir dikkat gerektirebilir.

Veri Aktarımı Objects (DTOs) gibi geç başlatılan özellikler içeren türler genellikle bir veritabanı ORM (nesne Ilişkisel Eşleyici), seri hale getirici veya başka bir kaynaktan özellikleri otomatik olarak dolduran başka bir bileşen gibi bir dış kitaplık tarafından örneklenmiştir.

Bir öğrenci 'yi temsil eden null yapılabilir başvuru türlerini etkinleştirmeden önce aşağıdaki DTO sınıfını göz önünde bulundurun:

```csharp
class Student
{
    [Required]
    public string FirstName { get; set; }

    [Required]
    public string LastName { get; set; }

    public string VehicleRegistration { get; set; }
}
```

Tasarım amacı (Bu `Required` durumda özniteliği tarafından belirtilir), bu sistemde `FirstName` ve `LastName` Özellikler **zorunludur**ve bu nedenle null değildir.

`VehicleRegistration` Özellik **zorunlu değil**, null olabilir.

Null yapılabilir başvuru türlerini etkinleştirdiğinizde, özelliklerden hangisinin boş değer atanabilir olabileceğini, özgün amacınızla tutarlı olduğunu belirtmek istersiniz:

```csharp
class Student
{
    [Required]
    public string FirstName { get; set; }

    [Required]
    public string LastName { get; set; }

    public string? VehicleRegistration { get; set; }
}
```

Bu DTO için, null olabilecek tek özellik ``VehicleRegistration``.

Ancak, derleyici hem hem `CS8618` de `FirstName` için uyarıları başlatır `LastName`ve null yapılamayan özelliklerin başlatılmamış olduğunu gösterir.

Derleyici uyarılarını özgün amacınızı sürdüren bir şekilde çözümlemek için kullanabileceğiniz üç seçenek mevcuttur. Bu seçeneklerden herhangi biri geçerlidir; kodlama stilinize ve tasarım gereksinimlerinize en uygun olanı seçmeniz gerekir.

### <a name="initialize-in-the-constructor"></a>Oluşturucuda Başlat

Başlatılmamış uyarıları çözümlemek için ideal yol, oluşturucudaki özellikleri başlatmaktır:

```csharp
class Student
{
    public Student(string firstName, string lastName)
    {
        FirstName = firstName;
        LastName = lastName;
    }

    [Required]
    public string FirstName { get; set; }

    [Required]
    public string LastName { get; set; }

    public string? VehicleRegistration { get; set; }
}
```

Bu yaklaşım yalnızca sınıfı örneğini oluşturmak için kullandığınız kitaplık, kurucudaki parametreleri geçirmeyi destekliyorsa işe yarar.

Ayrıca, bir kitaplık kurucudaki *bazı* özelliklerin geçirilmesini destekleyebilir, ancak tümünü desteklemez.
Örneğin, EF Core normal sütun özellikleri için [Oluşturucu bağlamasını](/ef/core/modeling/constructors) destekler, ancak gezinti özellikleri içermez.

Oluşturucuyu bağlamayı destekleme kapsamını anlamak için, sınıfınızı örnekleyen kitaplıktaki belgeleri denetleyin.

### <a name="property-with-nullable-backing-field"></a>Null yapılabilir destek alanı olan özellik

Oluşturucu bağlama sizin için çalışmazsa, bu sorunu gidermek için bir yol null yapılabilir bir yedekleme alanı olan null yapılamayan bir özelliğe sahip olur:

```csharp
private string? _firstName;

[Required]
public string FirstName
{
    set => _firstName = value;
    get => _firstName
           ?? throw new InvalidOperationException("Uninitialized " + nameof(FirstName))
}
```

Bu senaryoda, `FirstName` özelliği başlatılmadan önce ERIŞILIYORSA, API sözleşmesi yanlış kullanıldığı için kod bir `InvalidOperationException`oluşturur.

Bazı kitaplıkların, yedekleme alanları kullanılırken özel hususlar olabileceğini göz önünde bulundurmanız gerekir. Örneğin, EF Core [alanları](/ef/core/modeling/backing-field) doğru şekilde kullanmak için yapılandırılması gerekebilir.

### <a name="initialize-the-property-to-null"></a>Özelliği null olarak Başlat

Null olabilir bir yedekleme alanı kullanmanın bir alternatifi olarak veya sınıfınızı örnekleyen bir kitaplık Bu yaklaşımla uyumlu değilse, özelliği, null-forverme işlecinin ( `null` `!`) yardımıyla doğrudan ' a başlatabilirsiniz.

```csharp
[Required]
public string FirstName { get; set; } = null!;

[Required]
public string LastName { get; set; } = null!;

public string? VehicleRegistration { get; set; }
```

Çalışma zamanında gerçek bir null değeri, bir programlama hatasının sonucu hariç, özelliği düzgün bir şekilde başlatılmadan önce özelliğe erişerek hiçbir zaman gözlemleyeceksiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Var olan bir kod temelinin Nullable başvurulara geçirilmesi](tutorials/upgrade-to-nullable-references.md)
- [EF Core null yapılabilir başvuru türleriyle çalışma](/ef/core/miscellaneous/nullable-reference-types)
