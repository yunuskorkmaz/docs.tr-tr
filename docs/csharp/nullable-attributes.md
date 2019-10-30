---
title: API 'Leri, null beklentilerini tanımlamak için özniteliklerle yükseltin
description: Bu makalede, bağımsız değişkenlerin null durumunu ve API 'lerden dönüş değerlerini açıklayan açıklayıcı öznitelikler ekleme işlemleri ve teknikleri açıklanmaktadır
ms.technology: csharp-null-safety
ms.date: 07/31/2019
ms.openlocfilehash: 102598843b091ea25e6456aeedcccf43f056250d
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039375"
---
# <a name="update-libraries-to-use-nullable-reference-types-and-communicate-nullable-rules-to-callers"></a>Kitaplıkları null yapılabilir başvuru türleri kullanacak şekilde güncelleştirme ve arayanlara null olabilecek kuralları iletişim kurma

[Null yapılabilir başvuru türlerinin](nullable-references.md) eklenmesi, her değişken için `null` değerine izin verilip verilmeyeceğini veya beklenmediğini bildirebilmeniz anlamına gelir. Bu, kod yazarken harika bir deneyim sağlar. Null atanabilir olmayan bir değişken `null` olarak ayarlanmayabilir, uyarılar alırsınız. Nullable bir değişken, başvuru yapılmadan önce null olarak işaretli değilse uyarılar alırsınız. Kitaplıklarınızın güncelleştirilmesi zaman alabilir, ancak ödeme bu duruma göre yapılır. `null` değere izin verildiğinde ya da yasaklanmış *olduğunda* derleyiciye daha fazla bilgi SAĞLARSANıZ, API 'nizin kullanıcıları daha iyi uyarıları alır. Tanıdık bir örnekle başlayalım. Kitaplığınızın bir kaynak dizesini almak için aşağıdaki API 'ye sahip olduğunu düşünün:

```csharp
bool TryGetMessage(string key, out string message)
```

Yukarıdaki örnekte, .NET 'teki tanıdık `Try*` deseninin ardından yer verilmiştir. Bu API için iki başvuru bağımsız değişkeni vardır: `key` ve `message` parametresi. Bu API, bu bağımsız değişkenlerin nulldurumuyla ilgili aşağıdaki kurallara sahiptir:

- Çağıranlar, `key` için bağımsız değişken olarak `null` iletmemelidir.
- Çağıranlar, değeri `null` olan bir değişkeni `message` için bağımsız değişken olarak geçirebilir.
- `TryGetMessage` yöntemi `true`döndürürse `message` değeri null değildir. Dönüş değeri `false,` ise `message` (ve null durumunun) değeri null olur.

`key` kuralı, değişken türü ile tamamen ifade edilebilir: `key` null yapılamayan bir başvuru türü olmalıdır. `message` parametresi daha karmaşıktır. Bağımsız değişken olarak `null` ' ı sağlar, ancak başarıyı, `out` bağımsız değişkeninin null olmadığını garanti eder. Bu senaryolar için beklentileri betimleyen daha zengin bir sözlük gerekir.

Boş değer atanabilir başvurular için kitaplığınızın güncelleştirilmesi, bazı değişkenlerde ve tür adlarında Sprink `?` ' dan fazla olmalıdır. Yukarıdaki örnek, API 'lerinizi incelemeniz ve her giriş bağımsız değişkeni için beklentilerinizi göz önünde bulundurmanız gerektiğini gösterir. Dönüş değeri için garantiler ve yöntemin döndürdüğü `out` ya da `ref` bağımsız değişkenlerini göz önünde bulundurun. Sonra bu kuralları derleyiciye iletmeyin ve bu kurallar tarafından çağıranlar olmadığında Derleyici uyarılar sağlar.

Bu iş zaman alır. Diğer gereksinimleri ve teslim edilebilirleri dengelarken, kitaplığınızı veya uygulamanızı null yapılabilir hale getirme stratejileriyle başlayalım. Devam eden geliştirmeyi nasıl dengeleyebilirsiniz, null yapılabilir başvuru türleri etkinleştiriliyor. Genel tür tanımları için zorluk öğrenirsiniz. Tek tek API 'lerde ön ve son koşulları betimleyen öznitelikler uygulamayı öğreneceksiniz.

## <a name="choose-a-nullable-strategy"></a>Null yapılabilir bir strateji seçin

İlk seçenek, null yapılabilir başvuru türlerinin varsayılan olarak açık veya kapalı olması gerekip gerekmediğini belirtir. İki stratejileriniz vardır:

- Tüm proje için null yapılabilir başvuru türlerini etkinleştirin ve devre dışı olan kodda devre dışı bırakın.
- Yalnızca Nullable başvuru türleri için açıklama eklenmiş kod için null yapılabilir başvuru türlerini etkinleştirin.

İlk strateji, null yapılabilir başvuru türleri için güncelleştirdiğinizde, kitaplığa başka özellikler eklerken en iyi şekilde kullanılır. Tüm yeni geliştirmeler null yapılabilir. Mevcut kodu güncelleştirdiğinizde bu sınıflarda null yapılabilir başvuru türlerini etkinleştirirsiniz.

Bu ilk stratejiyi izleyerek şunları yapın:

1. *Csproj* dosyalarınıza `<Nullable>enable</Nullable>` öğesini ekleyerek projenin tamamına ait null yapılabilir türleri etkinleştirin. 
1. `#nullable disable` pragma öğesini projenizdeki her kaynak dosyaya ekleyin. 
1. Her dosya üzerinde çalışırken, pragmayı kaldırın ve tüm uyarıları çözün.

Bu ilk stratejide, her dosyaya pragma eklemek için daha fazla yukarı iş vardır. Avantajı, projeye eklenen her yeni kod dosyasının null yapılabilir olmasını sağlar. Herhangi bir yeni iş, null yapılabilir. yalnızca var olan kodun güncellenmesi gerekiyor.

İkinci strateji, kitaplığın genellikle kararlı olması ve geliştirmenin ana odağının null yapılabilir başvuru türlerini benimsemeniz durumunda daha iyi bir şekilde çalışacaktır. API 'Leri not yazarken null yapılabilir başvuru türlerini açabilirsiniz. İşiniz bittiğinde, tüm proje için null yapılabilir başvuru türlerini etkinleştirirsiniz.

Bu ikinci stratejiyi izleyerek şunları yapın:

1. `#nullable enable` pragma 'ı, null yapılabilir yapmak istediğiniz dosyaya ekleyin.
1. Tüm uyarıları çözün.
1. Tüm kitaplığı null yapılabilir olarak farkında olana kadar bu ilk iki adıma devam edin.
1. *Csproj* dosyalarınıza `<Nullable>enable</Nullable>` öğesini ekleyerek projenin tamamına ait null yapılabilir türleri etkinleştirin. 
1. Artık gerekli olmadığından `#nullable enable` pragmalarını kaldırın.

Bu ikinci stratejinin daha az iş ön ucu vardır. Zorunluluğunu getirir, yeni bir dosya oluşturduğunuz ilk görevin pragmasını eklemek ve null yapılabilir olduğunu fark edevidir. Takımınızdaki herhangi bir geliştirici unutur, bu yeni kod artık tüm kod Nullable olarak uyumlu hale getirmek için iş kapsamındedir.

Seçtiğiniz bu Stratejiler, projenizde ne kadar etkin geliştirme gerçekleştireceğinize bağlıdır. Projeniz ne kadar fazla olgun ve kararlı, ikinci strateji daha iyidir. Daha fazla geliştirmekte olan özellikler, ilk strateji daha iyidir.

## <a name="should-nullable-warnings-introduce-breaking-changes"></a>Null yapılabilir uyarılar, son değişiklikleri mi göstermelidir?

Null yapılabilir başvuru türlerini etkinleştirmeden önce, değişkenler *null yapılabilir zorunluluvou*olarak değerlendirilir. Null yapılabilir başvuru türlerini etkinleştirdikten sonra, bu değişkenlerin hepsi *null değer atanamaz*. Bu değişkenler null olmayan değerlere başlatılamıyorsa, derleyici uyarılar verebilir.

Büyük olasılıkla başka bir uyarı kaynağı, değer başlatılmamış olduğunda değerler döndürür.

Derleyici uyarılarını adresleyen ilk adım, parametre üzerinde `?` ek açıklamalarını ve bağımsız değişkenlerin veya dönüş değerlerinin null olabileceğini göstermek için dönüş türlerini kullanmaktır. Başvuru değişkenleri null olmamalı, özgün bildirim doğru olur. Bunu yaparken hedefiniz yalnızca uyarıları düzeltemedi. Daha önemli hedef, derleyicinin olası null değerler için amacınızı anlaması sağlamaktır. Uyarıları incelerken, kitaplığınız için bir sonraki önemli kararına ulaşabilirsiniz. Tasarım amacınızı daha net bir şekilde iletmek için API imzalarını değiştirmeyi düşünmek istiyor musunuz? Daha önce incelenen `TryGetMessage` yöntemi için daha iyi bir API imzası şu olabilir:

```csharp
string? TryGetMessage(string key);
```

Dönüş değeri başarılı veya başarısız olduğunu gösterir ve değer bulunursa değeri taşır. Çoğu durumda, API imzalarını değiştirmek, null değerleri nasıl ilettikleri iyileştirebilirler.

Ancak, genel kitaplıklar veya büyük Kullanıcı temellerine sahip kitaplıklar için herhangi bir API imza değişikliğine giriş yapmayı tercih edebilirsiniz. Bu durumlar ve diğer yaygın desenler için, bir bağımsız değişken veya dönüş değeri `null` olduğunda daha net bir şekilde tanımlanacak öznitelikler uygulayabilirsiniz. API 'nizin yüzeyini değiştirmeyi göz önünde bulundurmayın, büyük olasılıkla tür ek açıklamaların bağımsız değişkenler veya dönüş değerleri için `null` değerlerini açıklamak için yeterli olmadığını fark edersiniz. Bu örneklerde, bir API 'yi daha net bir şekilde anlatmak için öznitelikler uygulayabilirsiniz. 

## <a name="attributes-extend-type-annotations"></a>Öznitelikler tür ek açıklamalarını Genişlet

Değişkenlerin null durumu hakkında ek bilgileri ifade etmek için çeşitli öznitelikler eklenmiştir. 8 ' den önce C# yazdığınız tüm kod null yapılabilir başvuru türleri olarak *null zorunluluvou*idi. Yani herhangi bir başvuru türü değişkeni null olabilir, ancak null denetimleri gerekli değildir. Kodunuz *Nullable olarak farkında*olduktan sonra bu kurallar değişir. Başvuru türleri asla `null` değer olmamalı ve null yapılabilir başvuru türleri başvurulmadan önce `null` karşı denetlenmelidir.

API 'nizin kuralları `TryGetValue` API senaryosuyla gördüğünüz gibi büyük olasılıkla daha karmaşıktır. Birçok API 'niz, değişkenlerin `null`veya ne zaman oluşturulabileceğine ilişkin daha karmaşık kurallara sahiptir. Bu durumlarda, bu kuralları ifade etmek için aşağıdaki özniteliklerden birini kullanacaksınız:

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): null yapılamayan bir giriş bağımsız değişkeni null olabilir.
- [Disallownull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): null olabilen bir giriş bağımsız değişkeni hiçbir şekilde null olmamalıdır.
- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): null yapılamayan bir dönüş değeri null olabilir.
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): null olabilen bir dönüş değeri hiçbir şekilde null olmaz.
- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): yöntem belirtilen `bool` değerini döndürdüğünde null yapılamayan bir giriş bağımsız değişkeni null olabilir.
- [Notnullne zaman](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): yöntem belirtilen `bool` değerini döndürdüğünde null olabilen bir giriş bağımsız değişkeni null olmaz.
- [Notnullifnotnull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): belirtilen parametrenin bağımsız değişkeni null değilse, dönüş değeri null olamaz.

Yukarıdaki açıklamalar, her bir özniteliğin yaptığı işe yönelik hızlı bir başvurudur. Aşağıdaki her bölümde davranışı ve anlamı daha kapsamlı bir şekilde açıklanmıştır.

Bu özniteliklerin eklenmesi, derleyiciye API 'nizin kuralları hakkında daha fazla bilgi verir. Kodu çağırma özelliği, null yapılabilir etkin bir bağlamda derlenirse, derleyici bu kuralları ihlal ettiklerinde çağıranları uyarır. Bu öznitelikler, uygulamanızda ek denetimleri etkinleştirmez.

## <a name="specify-preconditions-allownull-and-disallownull"></a>Önkoşulları belirtin: `AllowNull` ve `DisallowNull`

Makul bir varsayılan değere sahip olduğu için hiçbir süre `null` döndürmediği bir okuma/yazma özelliği düşünün. Çağıranlar, bu varsayılan değere ayarlarken Set erişimcisine `null` ' a geçer. Örneğin, bir sohbet odasında ekran adı isteyen bir mesajlaşma sistemi düşünün. Hiçbiri sağlanmazsa, sistem rastgele bir ad üretir:

```csharp
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName;
```

Önceki kodu null olabilir bir zorunluluvou bağlamında derlerken her şey iyidir. Null yapılabilir başvuru türlerini etkinleştirdikten sonra `ScreenName` özelliği null atanamaz bir başvuru haline gelir. Bu, `get` erişimcisi için doğrudur: hiçbir şekilde `null` döndürmez. Çağıranlar `null` için döndürülen özelliği denetmek zorunda değildir. Ancak şimdi özelliği `null` olarak ayarlamak bir uyarı oluşturur. Bu tür bir kodu desteklemeye devam etmek için, aşağıdaki kodda gösterildiği gibi, <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute?displayProperty=nameWithType> özniteliğini özelliğe eklersiniz: 

```csharp
[AllowNull]
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName = GenerateRandomScreenName();
```

Bu makalede ele alınan bu ve diğer özniteliklerin kullanılması için <xref:System.Diagnostics.CodeAnalysis> için `using` yönergesi eklemeniz gerekebilir. Özniteliği, `set` erişimcisine değil, özelliğe uygulanır. `AllowNull` özniteliği *ön koşulları*belirtir ve yalnızca girişler için geçerlidir. `get` erişimcisinin dönüş değeri var, ancak giriş bağımsız değişkeni yok. Bu nedenle `AllowNull` özniteliği yalnızca `set` erişimcisi için geçerlidir.

Yukarıdaki örnekte, bir bağımsız değişkende `AllowNull` özniteliği eklenirken ne aranacağı gösterilmektedir:

1. Bu değişken için genel sözleşme `null` olmamalı, bu nedenle null atanamaz bir başvuru türü istiyorsunuz.
1. Giriş değişkeninin en yaygın kullanım olmasa da `null` olması senaryoları vardır.

Çoğu kez bu özniteliğe özellikler veya `in`, `out` ve `ref` bağımsız değişkenleri gerekecektir. `AllowNull` özniteliği, genellikle null olmayan bir değişken olduğunda en iyi seçenektir, ancak önkoşul olarak `null` izin vermeniz gerekir.

`DisallowNull`kullanmaya yönelik senaryolar ile karşıtlık: Bu özniteliği, null yapılabilir bir türdeki bir giriş değişkeninin `null`olmaması gerektiğini belirtmek için kullanırsınız. `null` varsayılan değer olduğu ancak istemciler yalnızca null olmayan bir değere ayarlayabileceği bir özelliği düşünün. Aşağıdaki kodu göz önünde bulundurun:

```csharp
public string ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string _comment;
```

Yukarıdaki kod, tasarımınızı `ReviewComment` `null` olabilir, ancak `null` ' ye ayarlayabilmenin en iyi yoludur. Bu kod null yapılabilir olduğunda, bu kavramı <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute?displayProperty=nameWithType>kullanarak çağıranlara daha net bir şekilde ifade edebilirsiniz:

```csharp
[DisallowNull] 
public string? ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string? _comment;
```

Null yapılabilir bir bağlamda, `ReviewComment` `get` erişimcisi `null` varsayılan değerini döndürebilir. Derleyici, erişim öncesinde denetlenmesi gerektiğini uyarır. Ayrıca, arayanlara `null` gibi görünse de çağıranlar tarafından açıkça `null` olarak ayarlanmamalıdır. `DisallowNull` özniteliği bir *ön koşul*de belirtir, `get` erişimcisini etkilemez. Aşağıdaki özellikleri gözlemlerseniz `DisallowNull` özniteliğini kullanmayı seçmeniz gerekir:

1. Değişken, genellikle ilk örneği oluşturulduğunda çekirdek senaryolarında `null` olabilir.
1. Değişken açıkça `null` olarak ayarlanmamalıdır.

Bu durumlar, başlangıçta *null yükümlülüğü*oluşturulan kodda ortaktır. Nesne özelliklerinin iki ayrı başlatma işlemi olarak ayarlanmış olması olabilir. Bazı özelliklerin bazı zaman uyumsuz çalışma tamamlandıktan sonra ayarlanmış olması olabilir.

`AllowNull` ve `DisallowNull` öznitelikleri, değişkenlerde önkoşulların Bu değişkenlerde boş değer atanabilir açıklamalarıyla eşleşmeyebilir belirtmenize olanak tanır. Bunlar, API 'nizin özellikleri hakkında daha ayrıntılı bilgi sağlar. Bu ek bilgiler, arayanların API 'nizi doğru şekilde kullanmasına yardımcı olur. Aşağıdaki öznitelikleri kullanarak önkoşulları belirtdüğünü unutmayın:

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): null yapılamayan bir giriş bağımsız değişkeni null olabilir.
- [Disallownull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): null olabilen bir giriş bağımsız değişkeni hiçbir şekilde null olmamalıdır.

## <a name="specify-post-conditions-maybenull-and-notnull"></a>Son koşulları belirtin: `MaybeNull` ve `NotNull`

Aşağıdaki imzaya sahip bir yönteminiz olduğunu varsayalım:

```csharp
public Customer FindCustomer(string lastName, string firstName)
```

Aranan ad bulunamadığı zaman `null` döndürmek için bunun gibi bir yöntem yazmış oldunuz. `null`, kaydın bulunamadığını açıkça gösterir. Bu örnekte, büyük olasılıkla `Customer` ' dan `Customer?` ' e kadar dönüş türünü değiştirirsiniz. Dönüş değerinin null yapılabilir bir başvuru türü olarak bildirilmesi, bu API 'nin amacını açıkça belirtir. 

[Genel tanımlar ve null değer verilebilme](#generic-definitions-and-nullability) kapsamında, tekniği genel yöntemlerle çalışmayan nedenler için. Benzer bir kalıbı izleyen genel bir yönteminiz olabilir:

```csharp
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

Dönüş değerinin `T?` olduğunu belirtemezsiniz. Aranan öğe bulunamadığında Yöntem `null` döndürür. `T?` bir dönüş türü bildiremiyoruz, bu ek açıklamayı Yöntem döndürecek şekilde `MaybeNull` ekleyin:

```csharp
[return: MaybeNull]
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

Yukarıdaki kod, arayanlara sözleşmenin null yapılamayan bir tür gösterdiği anlamına gelir, ancak *dönüş değeri gerçekten null olabilir.*  API 'niz null yapılamayan bir tür olması gerektiğinde (genellikle genel bir tür parametresi) `MaybeNull` özniteliğini kullanın, ancak `null` ' in döndürüldüğü örnekler olabilir.

Bir dönüş değeri veya `out` ya da `ref` bağımsız değişkeninin tür null yapılabilir bir tür olmasına rağmen null olmadığını belirtebilirsiniz. Bir dizinin birçok öğe tutabilecek kadar büyük olmasını sağlayan bir yöntemi düşünün. Giriş bağımsız değişkeninin kapasitesi yoksa, yordam yeni bir dizi ayırır ve var olan tüm öğeleri buna kopyalar. Giriş bağımsız değişkeni `null` ise, yordam yeni depolama alanı ayırır. Yeterli kapasite varsa, yordam hiçbir şey yapmaz:

```csharp
public void EnsureCapacity<T>(ref T[] storage, int size)
```

Bu yordamı aşağıdaki şekilde çağırabilirsiniz:

```csharp
// messages has the default value (null) when EnsureCapacity is called:
EnsureCapacity<string>(ref messages, 10);
// messages is not null.
EnsureCapacity<string>(messages, 50);
```

Null başvuru türlerini etkinleştirdikten sonra, önceki kodun uyarı olmadan derlendiğinden emin olmak istersiniz. Yöntem döndüğünde, `storage` bağımsız değişkeninin null olmaması garanti edilir. Ancak, null başvurusuyla `EnsureCapacity` çağırmak kabul edilebilir. `storage` null yapılabilir bir başvuru türü yapabilirsiniz ve `NotNull` koşul sonrası parametre bildirimine ekleyebilirsiniz:

```csharp
public void EnsureCapacity<T>([NotNull]ref T[]? storage, int size)
```

Yukarıdaki kod, mevcut sözleşmeyi çok açık bir şekilde ifade eder: çağıranlar `null` değeri ile bir değişken geçirebilir, ancak dönüş değeri hiçbir şekilde null olmamalıdır. `NotNull` özniteliği, `null` bağımsız değişken olarak geçirilebilecek `ref` ve `out` bağımsız değişkenleri için en yararlı seçenektir, ancak yöntemin döndürdüğü bağımsız değişkenin null olmaması garanti edilir.

Aşağıdaki öznitelikleri kullanarak koşulsuz Sonkoşulları belirtirsiniz:

- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): null yapılamayan bir dönüş değeri null olabilir.
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): null olabilen bir dönüş değeri hiçbir şekilde null olmaz.

## <a name="specify-conditional-post-conditions-notnullwhen-maybenullwhen-and-notnullifnotnull"></a>Koşullu koşulları belirtin: `NotNullWhen`, `MaybeNullWhen` ve `NotNullIfNotNull`

Büyük olasılıkla `string` yöntemi <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType>hakkında bilgi sahibisiniz. Bu yöntem, bağımsız değişken null veya boş bir dize olduğunda `true` döndürür. Bu bir null denetim biçimidir: çağıranların null olması gerekmez; Yöntem `false` döndürürse bağımsız değişkeni denetleyin. Bu null yapılabilir bir yöntemi gibi bir yöntem oluşturmak için bağımsız değişkenini null yapılabilir bir türe ayarlarsınız ve `NotNullWhen` özniteliğini eklersiniz:

```csharp
bool IsNullOrEmpty([NotNullWhen(false)]string? value);
```

Bu, derleyiciye dönüş değeri `false` olan herhangi bir kodun null denetimli olması gerektiğini bildirir. Özniteliğin eklenmesi, derleyicinin statik analizine `IsNullOrEmpty` ' ı, gerekli null denetimini gerçekleştirdiğinden bildirir: `false` ' i döndürdüğünde, giriş bağımsız değişkeni `null` değildir.

```csharp
string? userInput = GetUserInput();
if (!(string.IsNullOrEmpty(userInput))
{
   int messageLength = userInput.Length; // no null check needed.
}
// null check needed on userInput here.
```

<xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType> yöntemine .NET Core 3,0 için yukarıda gösterildiği gibi açıklama eklenir. Kod tabanınızda, null değerler için nesnelerin durumunu kontrol eden benzer yöntemlere sahip olabilirsiniz. Derleyici özel null denetim yöntemlerini tanımaz ve ek açıklamaları kendiniz eklemeniz gerekir. Özniteliğini eklediğinizde, derleyicinin statik analizi, sınanan değişkenin null olarak işaretli olduğunu bilir.

Bu öznitelikler için başka bir kullanım `Try*` ' dır. `ref` ve `out` değişkenlerine yönelik Sonkoşulları, dönüş değeri üzerinden iletilir. Daha önce gösterilen bu yöntemi göz önünde bulundurun:

```csharp
bool TryGetMessage(string key, out string message)
```

Yukarıdaki yöntem tipik bir .NET deyimidir OM: return değeri, `message` ' ın bulunan değere ayarlandığını veya bir ileti bulunamazsa varsayılan değere ayarlandığını gösterir. Yöntem `true` döndürürse, `message` değeri null değil; Aksi takdirde, yöntem `message` ' yi null olarak ayarlar.

`NotNullWhen` özniteliğini kullanarak bu deyimden iletişim kurabilirsiniz. Null yapılabilir başvuru türleri için imzayı güncelleştirdiğinizde `message` `string?` yapın ve bir öznitelik ekleyin:

```csharp
bool TryGetMessage(string key, [NotNullWhen(true)] out string? message)
```

Yukarıdaki örnekte, `TryGetMessage` `true` ' i döndürdüğünde `message` ' ın değeri null değil olarak bilinir. Kod tabanınızda benzer yöntemlere aynı şekilde açıklama eklemek gerekir: bağımsız değişkenler `null` olabilir ve Yöntem `true` ' i döndürdüğünde null olmadığı bilinmektedir.

Ayrıca ihtiyacınız olabilecek bir son öznitelik vardır. Bazen bir dönüş değerinin null durumu, bir veya daha fazla giriş bağımsız değişkenlerinin null durumuna bağlıdır. Bu yöntemler, belirli giriş bağımsız değişkenleri `null` olmadığında null olmayan bir değer döndürür. Bu yöntemlere doğru bir şekilde açıklama eklemek için `NotNullIfNotNull` özniteliğini kullanırsınız. Aşağıdaki yöntemi göz önünde bulundurun:

```csharp
string GetTopLevelDomainFromFullUrl(string url);
```

`url` bağımsız değişkeni null değilse, çıktı `null`olmaz. Null yapılabilir başvurular etkinleştirildikten sonra, bu imza doğru şekilde çalışarak API 'niz hiçbir şekilde null girişi kabul etmez. Ancak, giriş null ise, dönüş değeri de null olabilir. Bu nedenle, imzayı aşağıdaki kodla değiştirebilirsiniz:

```csharp
string? GetTopLevelDomainFromFullUrl(string? url);
```

Bu da çalışır, ancak arayanlara ek `null` denetimleri uygulamaya zorlanır. Sözleşme, dönüş değerinin `null` olması ve yalnızca `url` giriş bağımsız değişkeni `null` ' dir. Bu sözleşmeyi ifade etmek için, aşağıdaki kodda gösterildiği gibi bu yönteme açıklama ekleyebilirsiniz:

```csharp
[return: NotNullIfNotNull("url")]
string? GetTopLevelDomainFromFullUrl(string? url);
```

Dönüş değeri ve bağımsız değişkenine her ikisi de `?` `null` olduğunu belirten. Öznitelik, `url` bağımsız değişkeni `null` olmadığında dönüş değerinin null olmaması gerektiğini açıklığa kavuşturmaz.

Şu öznitelikleri kullanarak koşullu Sonkoşulları belirtirsiniz:

- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): yöntem belirtilen `bool` değerini döndürdüğünde null yapılamayan bir giriş bağımsız değişkeni null olabilir.
- [Notnullne zaman](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): yöntem belirtilen `bool` değerini döndürdüğünde null olabilen bir giriş bağımsız değişkeni null olmaz.
- [Notnullifnotnull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): belirtilen parametrenin giriş bağımsız değişkeni null değilse, dönüş değeri null olamaz.

## <a name="generic-definitions-and-nullability"></a>Genel tanımlar ve null değer alabilirlik

Genel türlerin ve genel yöntemlerin null durumuna doğru bir şekilde iletişim kurmak için özel bakım yapılması gerekir. Bu, null olabilen bir değer türünün ve null olabilen bir başvuru türünün temelde farklı olduğu gerçekten farklıdır. `int?`, `Nullable<int>`için bir eş anladır, ancak derleyici tarafından eklenen bir özniteliğe sahip `string?` `string`. Sonuç olarak, `T` ' in `class` mi yoksa `struct` mi olduğunu bilmeksizin, derleyicinin `T?` için doğru kod üretmesidir. 

Bu, kapalı bir genel türün tür bağımsız değişkeni olarak null yapılabilir bir tür (değer türü veya başvuru türü) kullanmayacağınız anlamına gelmez. Hem `List<string?>` hem de `List<int?>` `List<T>` ' nin geçerli örneklemelerinden oluşur. 

Ne anlama geliyor, bir genel sınıfta veya yöntem bildiriminde kısıtlama olmadan `T?` kullanmayacağınız anlamına gelir. Örneğin, <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable%7B%60%600%7D)?displayProperty=nameWithType> `T?`döndürecek şekilde değiştirilmez. `struct` veya `class` kısıtlamasını ekleyerek bu sınırlamayı aşabilirsiniz. Bu kısıtlamalardan biri ile derleyici, `T` ve `T?` için nasıl kod üretireceğini bilir.

Genel tür bağımsız değişkeni için kullanılan türleri null yapılamayan türler olacak şekilde kısıtlamak isteyebilirsiniz. Bunu, bu tür bağımsız değişkenine `notnull` kısıtlamasını ekleyerek yapabilirsiniz. Bu kısıtlama uygulandığında tür bağımsız değişkeni null yapılabilir bir tür olmamalıdır.

## <a name="conclusions"></a>Sonuçlar

Null yapılabilir başvuru türleri eklemek, `null` olabilecek değişkenlere yönelik API beklentilerinizi tanımlayan bir başlangıç sözlüğü sağlar. Ek öznitelikler, değişkenlerin null durumunu ön koşullar ve Postconditions olarak tanımlamaya yönelik daha zengin bir sözlük sağlar. Bu öznitelikler beklentilerinizi daha net bir şekilde anlatır ve API 'lerinizi kullanan geliştiriciler için daha iyi bir deneyim sağlar.

Bir null yapılabilir bağlam için kitaplıkları güncelleştirdiğinizde, API 'lerinizi kullanıcılarına doğru kullanım için bu öznitelikleri ekleyin. Bu öznitelikler, giriş bağımsız değişkenlerinin ve dönüş değerlerinin Null durumunu tam olarak açıklamanıza yardımcı olur:

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): null yapılamayan bir giriş bağımsız değişkeni null olabilir.
- [Disallownull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): null olabilen bir giriş bağımsız değişkeni hiçbir şekilde null olmamalıdır.
- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): null yapılamayan bir dönüş değeri null olabilir.
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): null olabilen bir dönüş değeri hiçbir şekilde null olmaz.
- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): yöntem belirtilen `bool` değerini döndürdüğünde null yapılamayan bir giriş bağımsız değişkeni null olabilir.
- [Notnullne zaman](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): yöntem belirtilen `bool` değerini döndürdüğünde null olabilen bir giriş bağımsız değişkeni null olmaz.
- [Notnullifnotnull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): belirtilen parametrenin giriş bağımsız değişkeni null değilse, dönüş değeri null olamaz.
