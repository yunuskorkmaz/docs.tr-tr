---
title: API 'Leri, null beklentilerini tanımlamak için özniteliklerle yükseltin
description: Bu makalede, bağımsız değişkenlerin null durumunu ve API 'lerden dönüş değerlerini açıklayan açıklayıcı öznitelikler ekleme işlemleri ve teknikleri açıklanmaktadır
ms.date: 07/31/2019
ms.openlocfilehash: f8ff2063a3859954a5ccab006cd21c6a29dbc6b1
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710933"
---
# <a name="update-libraries-to-use-nullable-reference-types-and-communicate-nullable-rules-to-callers"></a>Kitaplıkları, null yapılabilir başvuru türlerini kullanacak şekilde güncelleştirin ve çağrı yapılabilir kuralları arayanlara iletişim kurar.

[Null yapılabilir başvuru türlerinin](nullable-references.md) eklenmesi, her değişken için bir `null` değere izin verilip verilmeyeceğini veya beklenmediğini bildirebilmeniz anlamına gelir. Bu, kod yazarken harika bir deneyim sağlar. Null yapılamayan bir değişken olarak `null`ayarlanmayabilir. Nullable bir değişken, başvuru yapılmadan önce null olarak işaretli değilse uyarılar alırsınız. Kitaplıklarınızın güncelleştirilmesi zaman alabilir, ancak ödeme bu duruma göre yapılır. Bir`null` değere izin verildiğinde veya yasaklanmış *olduğunda* derleyiciye sağladığınız daha fazla bilgi, API 'nizin Kullanıcı tarafından daha iyi uyarıları alır. Tanıdık bir örnekle başlayalım. Kitaplığınızın bir kaynak dizesini almak için aşağıdaki API 'ye sahip olduğunu düşünün:

```csharp
bool TryGetMessage(string key, out string message)
```

Yukarıdaki örnek, .net 'teki tanıdık `Try*` olan bir model izler. Bu API için iki başvuru bağımsız değişkeni vardır: `key` `message` ve parametresi. Bu API, bu bağımsız değişkenlerin nulldurumuyla ilgili aşağıdaki kurallara sahiptir:

- Çağıranlar için `null` `key`bağımsız değişken olarak geçmemelidir.
- Çağıranlar, değeri `null` `message`bağımsız değişkeni olan bir değişken geçirebilir.
- Yöntemi döndürürse `true`, değeri`message` null değildir. `TryGetMessage` Dönüş değeri `false,` `message` (ve null durumu) değeri null ise.

Kuralı `key` değişken türü ile tamamen ifade edilebilir: `key` null yapılamayan bir başvuru türü olmalıdır. `message` Parametresi daha karmaşıktır. Bağımsız değişken `null` olarak izin verir, ancak başarıyı, bu bağımsız değişkenin null olmadığını `out` garanti eder. Bu senaryolar için beklentileri betimleyen daha zengin bir sözlük gerekir.

Boş değer atanabilir başvurular için kitaplığınızın güncelleştirilmesi, bazı değişkenlerde ve tür `?` adlarından daha fazla spreninkini gerektirir. Yukarıdaki örnek, API 'lerinizi incelemeniz ve her giriş bağımsız değişkeni için beklentilerinizi göz önünde bulundurmanız gerektiğini gösterir. Dönüş değeri için garantiyi ve yöntemin dönüşi üzerinde `out` herhangi `ref` bir veya bağımsız değişkeni göz önünde bulundurun. Sonra bu kuralları derleyiciye iletmeyin ve bu kurallar tarafından çağıranlar olmadığında Derleyici uyarılar sağlar.

Bu iş zaman alır. Diğer gereksinimleri ve teslim edilebilirleri dengelarken, kitaplığınızı veya uygulamanızı null yapılabilir hale getirme stratejileriyle başlayalım. Devam eden geliştirmeyi nasıl dengeleyebilirsiniz, null yapılabilir başvuru türleri etkinleştiriliyor. Genel tür tanımları için zorluk öğrenirsiniz. Tek tek API 'lerde ön ve son koşulları betimleyen öznitelikler uygulamayı öğreneceksiniz.

## <a name="choose-a-nullable-strategy"></a>Null yapılabilir bir strateji seçin

İlk seçenek, null yapılabilir başvuru türlerinin varsayılan olarak açık veya kapalı olması gerekip gerekmediğini belirtir. İki stratejileriniz vardır:

- Tüm proje için null yapılabilir başvuru türlerini etkinleştirin ve devre dışı olan kodda devre dışı bırakın.
- Yalnızca Nullable başvuru türleri için açıklama eklenmiş kod için null yapılabilir başvuru türlerini etkinleştirin.

İlk strateji, null yapılabilir başvuru türleri için güncelleştirdiğinizde, kitaplığa başka özellikler eklerken en iyi şekilde kullanılır. Tüm yeni geliştirmeler null yapılabilir. Mevcut kodu güncelleştirdiğinizde bu sınıflarda null yapılabilir başvuru türlerini etkinleştirirsiniz.

Bu ilk stratejiyi izleyerek şunları yapın:

1. `<Nullable>enable</Nullable>` Öğeyi *csproj* dosyalarınıza ekleyerek projenin tamamına ait boş değer atanabilir türleri etkinleştirin. 
1. `#nullable disable` Pragmayı projenizdeki her kaynak dosyasına ekleyin. 
1. Her dosya üzerinde çalışırken, pragmayı kaldırın ve tüm uyarıları çözün.

Bu ilk stratejide, her dosyaya pragma eklemek için daha fazla yukarı iş vardır. Avantajı, projeye eklenen her yeni kod dosyasının null yapılabilir olmasını sağlar. Herhangi bir yeni iş, null yapılabilir. yalnızca var olan kodun güncellenmesi gerekiyor.

İkinci strateji, kitaplığın genellikle kararlı olması ve geliştirmenin ana odağının null yapılabilir başvuru türlerini benimsemeniz durumunda daha iyi bir şekilde çalışacaktır. API 'Leri not yazarken null yapılabilir başvuru türlerini açabilirsiniz. İşiniz bittiğinde, tüm proje için null yapılabilir başvuru türlerini etkinleştirirsiniz.

Bu ikinci stratejiyi izleyerek şunları yapın:

1. Null yapılabilir olmasını istediğiniz dosyaya pragmaekleyin.`#nullable enable`
1. Tüm uyarıları çözün.
1. Tüm kitaplığı null yapılabilir olarak farkında olana kadar bu ilk iki adıma devam edin.
1. `<Nullable>enable</Nullable>` Öğeyi *csproj* dosyalarınıza ekleyerek projenin tamamına ait boş değer atanabilir türleri etkinleştirin. 
1. Artık gerekli olmadığından pragmaları kaldırın. `#nullable enable`

Bu ikinci stratejinin daha az iş ön ucu vardır. Zorunluluğunu getirir, yeni bir dosya oluşturduğunuz ilk görevin pragmasını eklemek ve null yapılabilir olduğunu fark edevidir. Takımınızdaki herhangi bir geliştirici unutur, bu yeni kod artık tüm kod Nullable olarak uyumlu hale getirmek için iş kapsamındedir.

Seçtiğiniz bu Stratejiler, projenizde ne kadar etkin geliştirme gerçekleştireceğinize bağlıdır. Projeniz ne kadar fazla olgun ve kararlı, ikinci strateji daha iyidir. Daha fazla geliştirmekte olan özellikler, ilk strateji daha iyidir.

## <a name="should-nullable-warnings-introduce-breaking-changes"></a>Null yapılabilir uyarılar, son değişiklikleri mi göstermelidir?

Null yapılabilir başvuru türlerini etkinleştirmeden önce, değişkenler *null yapılabilir zorunluluvou*olarak değerlendirilir. Null yapılabilir başvuru türlerini etkinleştirdikten sonra, bu değişkenlerin hepsi *null değer atanamaz*. Bu değişkenler null olmayan değerlere başlatılamıyorsa, derleyici uyarılar verebilir.

Büyük olasılıkla başka bir uyarı kaynağı, değer başlatılmamış olduğunda değerler döndürür.

Derleyici uyarılarını adresleyen ilk adım, parametre ve dönüş türleri `?` üzerinde ek açıklamaların kullanılması ve bağımsız değişkenlerin veya dönüş değerlerinin null olabileceğini göstermek için kullanılır. Başvuru değişkenleri null olmamalı, özgün bildirim doğru olur. Bunu yaparken hedefiniz yalnızca uyarıları düzeltemedi. Daha önemli hedef, derleyicinin olası null değerler için amacınızı anlaması sağlamaktır. Uyarıları incelerken, kitaplığınız için bir sonraki önemli kararına ulaşabilirsiniz. Tasarım amacınızı daha net bir şekilde iletmek için API imzalarını değiştirmeyi düşünmek istiyor musunuz? Daha önce incelenen `TryGetMessage` Yöntem için daha iyi bir API imzası şu olabilir:


```csharp
string? TryGetMessage(string key);
```

Dönüş değeri başarılı veya başarısız olduğunu gösterir ve değer bulunursa değeri taşır. Çoğu durumda, API imzalarını değiştirmek, null değerleri nasıl ilettikleri iyileştirebilirler.

Ancak, genel kitaplıklar veya büyük Kullanıcı temellerine sahip kitaplıklar için herhangi bir API imza değişikliğine giriş yapmayı tercih edebilirsiniz. Bu durumlar ve diğer yaygın desenler için, bir bağımsız değişken veya dönüş değeri `null`olabileceği zaman daha net bir şekilde tanımlanacak öznitelikler uygulayabilirsiniz. API 'nizin yüzeyini değiştirmeyi göz önünde bulundurmayın, büyük olasılıkla tür ek açıklamalarını bağımsız değişkenlerin veya dönüş değerlerinin değerlerini tanımlamak `null` için yeterli olmadığını fark edeceksiniz. Bu örneklerde, bir API 'yi daha net bir şekilde anlatmak için öznitelikler uygulayabilirsiniz. 

## <a name="attributes-extend-type-annotations"></a>Öznitelikler tür ek açıklamalarını Genişlet

Değişkenlerin null durumu hakkında ek bilgileri ifade etmek için çeşitli öznitelikler eklenmiştir. 8 ' den önce C# yazdığınız tüm kod null yapılabilir başvuru türleri olarak *null zorunluluvou*idi. Yani herhangi bir başvuru türü değişkeni null olabilir, ancak null denetimleri gerekli değildir. Kodunuz *Nullable olarak farkında*olduktan sonra bu kurallar değişir. Başvuru türleri asla `null` değer olmamalı ve null yapılabilir başvuru türleri başvurulmadan `null` önce denetlenmelidir.

`TryGetValue` API 'si senaryosuyla gördüğünüz gibi API 'lerinizin kuralları büyük olasılıkla daha karmaşıktır. API 'lerinizin birçoğu, değişkenlerin ne zaman veya ne zaman oluşturulabileceğine `null`ilişkin daha karmaşık kurallara sahiptir. Bu durumlarda, bu kuralları ifade etmek için aşağıdaki özniteliklerden birini kullanacaksınız:

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Null olamayan bir giriş bağımsız değişkeni null olabilir.
- [Disallownull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): Null olabilen bir giriş bağımsız değişkeni hiçbir şekilde null olmamalıdır.
- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Null yapılamayan bir dönüş değeri null olabilir.
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): Nullable dönüş değeri hiçbir şekilde null olmaz.
- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Dönüş değeri bir koşula `out` uysa, null olamayan veya `ref` bağımsız değişken null olabilir.
- [Notnullne zaman](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Dönüş değeri `out` bir `ref` koşula uyan null yapılabilir veya bağımsız değişken null olamaz.
- [Notnullifnotnull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): giriş dize bağımsız değişkeni null olmadığında bir dize dönüş değeri null değil.

Yukarıdaki açıklamalar, her bir özniteliğin yaptığı işe yönelik hızlı bir başvurudur. Aşağıdaki her bölümde davranışı ve anlamı daha kapsamlı bir şekilde açıklanmıştır.

Bu özniteliklerin eklenmesi, derleyiciye API 'nizin kuralları hakkında daha fazla bilgi verir. Kodu çağırma özelliği, null yapılabilir etkin bir bağlamda derlenirse, derleyici bu kuralları ihlal ettiklerinde çağıranları uyarır. Bu öznitelikler, uygulamanızda ek denetimleri etkinleştirmez.

## <a name="specify-preconditions-allownull-and-disallownull"></a>Önkoşulları belirtin: `AllowNull` ve`DisallowNull`

Makul bir varsayılan değere sahip olduğu için hiçbir süre `null` döndürülmediği bir okuma/yazma özelliği düşünün. Çağıranlar `null` , bu varsayılan değere ayarlarken ayarlanan erişimciye geçer. Örneğin, bir sohbet odasında ekran adı isteyen bir mesajlaşma sistemi düşünün. Hiçbiri sağlanmazsa, sistem rastgele bir ad üretir:

```csharp
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName;
```

Önceki kodu null olabilir bir zorunluluvou bağlamında derlerken her şey iyidir. Null yapılabilir başvuru türlerini etkinleştirdikten sonra, `ScreenName` özelliği null yapılamayan bir başvuru haline gelir. Bu, `get` erişimci için doğrudur: hiçbir şekilde döndürmez `null`. Çağıranlar için `null`döndürülen özelliği denetmek zorunda değildir. Ancak şimdi özelliği bir uyarı oluşturacak `null` şekilde ayarlanıyor. Bu tür bir kodu desteklemeye devam etmek için, aşağıdaki kodda gösterildiği gibi <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute?displayProperty=nameWithType> özniteliğini özelliği ekleyin: 

```csharp
[AllowNull]
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName = GenerateRandomScreenName();
```

Bu makalede ele alınan bu ve `using` diğer özniteliklerin <xref:System.Diagnostics.CodeAnalysis> kullanılması için bir yönerge eklemeniz gerekebilir. Özniteliği, `set` erişimciye değil, özelliğine uygulanır. Öznitelik, *ön koşulları*belirtir ve yalnızca girişler için geçerlidir. `AllowNull` `get` Erişimcinin dönüş değeri var, ancak giriş bağımsız değişkeni yok. Bu nedenle, `AllowNull` öznitelik yalnızca `set` erişimci için geçerlidir.

Yukarıdaki örnekte, bir bağımsız değişkende `AllowNull` özniteliği eklenirken ne aranacağı gösterilmektedir:

1. Bu değişken için genel sözleşme bunun olmaması `null`, bu nedenle null atanamaz bir başvuru türü istemeniz gerekir.
1. Giriş değişkeninin en yaygın kullanımları olmadıkları halde olması `null`için senaryolar vardır.

Çoğu kez bu özniteliğe özellikler, veya `in`, `out`ve `ref` bağımsız değişkenler için ihtiyaç duyarsınız. Özniteliği genellikle null olmayan ancak önkoşul olarak izin vermeniz `null` gereken en iyi seçenektir. `AllowNull`

Kullanma `DisallowNull`senaryolarıyla karşıtlık: Bu özniteliği, null yapılabilir bir türdeki bir giriş değişkeninin olmaması `null`gerektiğini belirtmek için kullanırsınız. Varsayılan değer `null` olan, ancak istemciler yalnızca null olmayan bir değere ayarlayabileceği bir özelliği düşünün. Aşağıdaki kodu göz önünde bulundurun:

```csharp
public string ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string _comment;
```

Önceki kod, tasarımınızı `ReviewComment` `null`ifade etmenin en iyi yoludur, ancak olarak `null`ayarlanamaz. Bu kod null yapılabilir olduğunda, bu kavramı kullanarak <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute?displayProperty=nameWithType>çağıranlara daha net bir şekilde ifade edebilirsiniz:

```csharp
[DisallowNull] 
public string? ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string? _comment;
```

Null yapılabilir bir bağlamda, `ReviewComment` `get` erişimci varsayılan değerini `null`döndürebilir. Derleyici, erişim öncesinde denetlenmesi gerektiğini uyarır. Buna ek olarak, arayanlara açıkça ayarlanmaması `null` `null`durumunda bile arayanlara uyarır. Öznitelik bir *ön koşul*da belirtir, `get` erişimciyi etkilemez. `DisallowNull` Aşağıdaki özellikleri gözlemlerseniz `DisallowNull` özniteliğini kullanmayı seçmeniz gerekir:

1. Değişken, genellikle ilk `null` örneği oluşturulduğunda temel senaryolarda olabilir.
1. Değişken açıkça olarak `null`ayarlanmamalıdır.

Bu durumlar, başlangıçta *null yükümlülüğü*oluşturulan kodda ortaktır. Nesne özelliklerinin iki ayrı başlatma işlemi olarak ayarlanmış olması olabilir. Bazı özelliklerin bazı zaman uyumsuz çalışma tamamlandıktan sonra ayarlanmış olması olabilir.

`AllowNull` Ve`DisallowNull` öznitelikleri, değişkenlerde önkoşulların Bu değişkenlerde null yapılabilir ek açıklamalarıyla eşleşmeyebilir belirtmenize olanak tanır. Bunlar, API 'nizin özellikleri hakkında daha ayrıntılı bilgi sağlar. Bu ek bilgiler, arayanların API 'nizi doğru şekilde kullanmasına yardımcı olur. Aşağıdaki öznitelikleri kullanarak önkoşulları belirtdüğünü unutmayın:

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Null olamayan bir giriş bağımsız değişkeni null olabilir.
- [Disallownull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): Null olabilen bir giriş bağımsız değişkeni hiçbir şekilde null olmamalıdır.

## <a name="specify-post-conditions-maybenull-and-notnull"></a>Son koşulları belirtin: `MaybeNull` ve`NotNull`

Aşağıdaki imzaya sahip bir yönteminiz olduğunu varsayalım:

```csharp
public Customer FindCustomer(string lastName, string firstName)
```

Aranan ad bulunamadığı zaman döndürmek `null` için bunun gibi bir yöntem yazmış oluk. `null` Açıkça kaydın bulunamadığını gösterir. Bu örnekte, büyük olasılıkla ' dan `Customer` `Customer?`' a dönüş türünü değiştirirsiniz. Dönüş değerinin null yapılabilir bir başvuru türü olarak bildirilmesi, bu API 'nin amacını açıkça belirtir. 

[Genel tanımlar ve null değer verilebilme](#generic-definitions-and-nullability) kapsamında, tekniği genel yöntemlerle çalışmayan nedenler için. Benzer bir kalıbı izleyen genel bir yönteminiz olabilir:

```csharp
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

Dönüş değerinin `T?`olduğunu belirtemezsiniz. Yöntemi, aranan `null` öğe bulunamadığında döndürür. Bir `T?` dönüş türü bildirebileceğinizden, `MaybeNull` ek açıklamayı Yöntem döndürecek şekilde eklersiniz:

```csharp
[return: MaybeNull]
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

Yukarıdaki kod, arayanlara sözleşmenin null yapılamayan bir tür gösterdiği anlamına gelir, ancak *dönüş değeri gerçekten* null olabilir.  API 'niz null yapılamayan bir tür olması gerektiği zaman, genellikle genel bir tür parametresi olması durumunda `null` özniteliğikullanın,ancakdöndürülecekörneklerolabilir.`MaybeNull`

Ayrıca, tür null yapılabilir bir tür olsa da bir `out` dönüş `ref` değeri veya veya bağımsız değişkenin null olmadığını belirtebilirsiniz. Bir dizinin birçok öğe tutabilecek kadar büyük olmasını sağlayan bir yöntemi düşünün. Giriş bağımsız değişkeninin kapasitesi yoksa, yordam yeni bir dizi ayırır ve var olan tüm öğeleri buna kopyalar. Giriş bağımsız değişkeni ise `null`, yordam yeni depolama alanı ayırır. Yeterli kapasite varsa, yordam hiçbir şey yapmaz:

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

Null başvuru türlerini etkinleştirdikten sonra, önceki kodun uyarı olmadan derlendiğinden emin olmak istersiniz. Yöntemi `storage` döndürüldüğünde bağımsız değişkenin null olmaması garanti edilir. Ancak, bir null başvurusuyla çağırmak `EnsureCapacity` kabul edilebilir. Null yapılabilir bir `storage` başvuru türü yapabilir ve parametre bildirimine `NotNull` son koşulu ekleyebilirsiniz:

```csharp
public void EnsureCapacity<T>([NotNull]ref T[]? storage, int size)
```

Yukarıdaki kod, mevcut sözleşmeyi çok açık bir şekilde ifade eder: Çağıranlar `null` değeri olan bir değişken geçirebilir, ancak dönüş değeri hiçbir şekilde null olmamalıdır. `ref` `null` Özniteliği ve bağımsızdeğişkenolarakgeçirilebilecekbağımsızdeğişkenleriçinenyararlıseçenektir,ancakyöntemindöndürdüğüzamandeğişkeninnullolmamasıgarantiedilir.`out` `NotNull`

Aşağıdaki öznitelikleri kullanarak koşulsuz Sonkoşulları belirtirsiniz:

- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Null yapılamayan bir dönüş değeri null olabilir.
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): Nullable dönüş değeri hiçbir şekilde null olmaz.

## <a name="specify-conditional-post-conditions-notnullwhen-and-maybenullwhen"></a>Koşullu koşulları belirtin: `NotNullWhen` ve`MaybeNullWhen`

Büyük olasılıkla `string` yöntemiyle <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType>ilgili bilgi sahibisiniz. Bu yöntem boş `true` dize değil, bağımsız değişken null olmadığında döndürür. Bu bir null denetim biçimidir: Arayan çağıranları null değer döndürmesi gerekmez; yöntemin döndürdüğü `false`bağımsız değişkeni kontrol edin. Bu null yapılabilir bir yöntemi gibi bir yöntem oluşturmak için bağımsız değişkenini null yapılabilir bir türe ayarlarsınız ve `NotNullWhen` özniteliği ekleyebilirsiniz:

```csharp
bool IsNullOrEmpty([NotNullWhen(false)]string? value);
```

Bu, derleyicinin dönüş değerinin `false` null denetimli olması gereken herhangi bir kod olduğunu bildirir. Özniteliğin eklenmesi, derleyicinin statik analizini `IsNullOrEmpty` , gerekli null denetimini yerine getiren bildirir: döndüğünde `false`, giriş bağımsız değişkeni değildir `null`.

```csharp
string? userInput = GetUserInput();
if (!(string.IsNullOrEmpty(userInput))
{
   int messageLength = userInput.Length; // no null check needed.
}
// null check needed on userInput here.
```

Yöntemi <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType> , .NET Core 3,0 için yukarıda gösterildiği gibi açıklanacaktır. Kod tabanınızda, null değerler için nesnelerin durumunu kontrol eden benzer yöntemlere sahip olabilirsiniz. Derleyici özel null denetim yöntemlerini tanımaz ve ek açıklamaları kendiniz eklemeniz gerekir. Özniteliğini eklediğinizde, derleyicinin statik analizi, sınanan değişkenin null olarak işaretli olduğunu bilir.

Bu öznitelikler için başka bir kullanım de `Try*` modeldir. `ref` Ve`out` değişkenleri için Sonkoşulları, dönüş değeri üzerinden iletilir. Daha önce gösterilen bu yöntemi göz önünde bulundurun:

```csharp
bool TryGetMessage(string key, out string message)
```

Yukarıdaki yöntem tipik bir .net deyimidir OM: dönüş değeri, bulunan değer olarak ayarlanmış `message` olup olmadığını veya hiçbir ileti bulunamazsa varsayılan değere ayarlandığını gösterir. Yöntemi döndürürse `true`, `message` değeri null değildir; Aksi takdirde, yöntemi null olarak ayarlanır `message` .

`NotNullWhen` Özniteliği kullanarak bu deyimden iletişim kurabilirsiniz. Null yapılabilir başvuru türleri için imzayı güncelleştirdiğinizde bir `message` `string?` özniteliği oluşturun ve ekleyin:

```csharp
bool TryGetMessage(string key, [NotNullWhen(true)] out string? message)
```

Önceki örnekte, değeri `message` `TryGetMessage` döndüğünde `true`null değil olarak bilinir. Kod tabanınızda benzer yöntemlere aynı şekilde açıklama eklenmelidir: bağımsız değişkenler olabilir `null`ve `true`yöntem döndürüldüğünde null olmadığı bilinmektedir.

Ayrıca ihtiyacınız olabilecek bir son öznitelik vardır. Bazen bir dönüş değerinin null durumu, bir veya daha fazla giriş bağımsız değişkenlerinin null durumuna bağlıdır. Bu yöntemler, belirli giriş bağımsız değişkenleri `null`olmadığında null olmayan bir değer döndürür. Bu yöntemlere doğru şekilde açıklama eklemek için `NotNullIfNotNull` özniteliğini kullanırsınız. Aşağıdaki yöntemi göz önünde bulundurun:

```csharp
string GetTopLevelDomainFromFullUrl(string url);
```

Bağımsız değişken null değilse, çıktı değildir `null`. `url` Null yapılabilir başvurular etkinleştirildikten sonra, bu imza doğru şekilde çalışarak API 'niz hiçbir şekilde null girişi kabul etmez. Ancak, giriş null ise, dönüş değeri de null olabilir. Bu nedenle, imzayı aşağıdaki kodla değiştirebilirsiniz:

```csharp
string? GetTopLevelDomainFromFullUrl(string? url);
```

Bu da çalışır, ancak arayanlara çok fazla `null` denetim uygulamak için zorlayacaktır. Sözleşmenin dönüş değeri yalnızca giriş `null` `null`bağımsız değişkeni `url` olduğunda olacaktır. Bu sözleşmeyi ifade etmek için, aşağıdaki kodda gösterildiği gibi bu yönteme açıklama ekleyebilirsiniz:

```csharp
[return: NotNullIfNotNull("url")]
string? GetTopLevelDomainFromFullUrl(string? url);
```

Dönüş değerine ve bağımsız değişkenine, her iki durumda `?` `null`da olabilecek şekilde açıklama eklenmiş. Özniteliği, `url` `null`bağımsız değişken olmadığında dönüş değerinin null olmaması gerektiğini açıklığa kavuşturulur.

Şu öznitelikleri kullanarak koşullu Sonkoşulları belirtirsiniz:

- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Dönüş değeri bir koşula `out` uysa, null olamayan veya `ref` bağımsız değişken null olabilir.
- [Notnullne zaman](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Dönüş değeri `out` bir `ref` koşula uyan null yapılabilir veya bağımsız değişken null olamaz.
- [Notnullifnotnull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): Belirtilen parametrenin giriş bağımsız değişkeni null değilse, dönüş değeri null olamaz.

## <a name="generic-definitions-and-nullability"></a>Genel tanımlar ve null değer alabilirlik

Genel türlerin ve genel yöntemlerin null durumuna doğru bir şekilde iletişim kurmak için özel bakım yapılması gerekir. Bu, null olabilen bir değer türünün ve null olabilen bir başvuru türünün temelde farklı olduğu gerçekten farklıdır. , İçin `string?` `string` bir eş anlamlı olur, ancak derleyici tarafından eklenen bir özniteliktir. `int?` `Nullable<int>` Sonuç, derleyicisinin `T?` bir veya bir `T` `struct`olduğunu bilmeksizin doğru kodu oluşturabileceği bir `class` sonucudur. 

Bu, kapalı bir genel türün tür bağımsız değişkeni olarak null yapılabilir bir tür (değer türü veya başvuru türü) kullanmayacağınız anlamına gelmez. Her ikisi de `List<string?>` geçerli `List<T>`örneklerdir. `List<int?>` 

Bunun anlamı, kısıtlama olmadan genel bir sınıfta veya `T?` yöntem bildiriminde kullanmayacağınız anlamına gelir. Örneğin, <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable%7B%60%600%7D)?displayProperty=nameWithType> döndürülecek `T?`şekilde değiştirilmez. `struct` Ya`class` da kısıtlamasını ekleyerek bu sınırlamayı aşabilirsiniz. Bu kısıtlamalardan biri ile derleyici, hem hem de `T` `T?`için nasıl kod oluşturulacağını bilir.

Genel tür bağımsız değişkeni için kullanılan türleri null yapılamayan türler olacak şekilde kısıtlamak isteyebilirsiniz. Bunu, bu tür bağımsız değişkenine `notnull` kısıtlama ekleyerek yapabilirsiniz. Bu kısıtlama uygulandığında tür bağımsız değişkeni null yapılabilir bir tür olmamalıdır.

## <a name="conclusions"></a>Sonuçlar

Null yapılabilir başvuru türleri eklemek, `null`olabilecek değişkenlere yönelik API beklentilerinizi tanımlayan bir başlangıç sözlüğü sağlar. Ek öznitelikler, değişkenlerin null durumunu ön koşullar ve Postconditions olarak tanımlamaya yönelik daha zengin bir sözlük sağlar. Bu öznitelikler beklentilerinizi daha net bir şekilde anlatır ve API 'lerinizi kullanan geliştiriciler için daha iyi bir deneyim sağlar.

Bir null yapılabilir bağlam için kitaplıkları güncelleştirdiğinizde, API 'lerinizi kullanıcılarına doğru kullanım için bu öznitelikleri ekleyin. Bu öznitelikler, giriş bağımsız değişkenlerinin ve dönüş değerlerinin Null durumunu tam olarak açıklamanıza yardımcı olur:

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Null olamayan bir giriş bağımsız değişkeni null olabilir.
- [Disallownull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): Null olabilen bir giriş bağımsız değişkeni hiçbir şekilde null olmamalıdır.
- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Null yapılamayan bir dönüş değeri null olabilir.
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): Nullable dönüş değeri hiçbir şekilde null olmaz.
- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Dönüş değeri bir koşula `out` uysa, null olamayan veya `ref` bağımsız değişken null olabilir.
- [Notnullne zaman](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Dönüş değeri `out` bir `ref` koşula uyan null yapılabilir veya bağımsız değişken null olamaz.
- [Notnullifnotnull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): Belirtilen parametrenin giriş bağımsız değişkeni null değilse, dönüş değeri null olamaz.
