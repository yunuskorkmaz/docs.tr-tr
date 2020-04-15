---
title: 'C# Ayrılmış öznitelikler: Nullable statik çözümleme'
ms.date: 04/14/2020
description: Bu öznitelikler, nullable ve nullable referans türleri için daha iyi statik çözümleme sağlamak için derleyici tarafından yorumlanır.
ms.openlocfilehash: 0315d78db7517541efe578d8675c0f2fe45f5aea
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389865"
---
# <a name="reserved-attributes-contribute-to-the-compilers-null-state-static-analysis"></a>Ayrılmış öznitelikler derleyicinin null durum statik analizine katkıda bulunur

Nullable bağlamında, derleyici tüm başvuru türü değişkenlerinin null durumunu belirlemek için kodun statik çözümlemesi gerçekleştirir:

- *not null*: Değişkenin null olmayan bir değere atandığını belirleyen statik analiz.
- *belki null*: Statik çözümleme bir değişkene null olmayan bir değer atandığını belirleyemez.

API'lerinizin anlambilimi hakkında derleyiciye bilgi sağlayan bir dizi öznitelik uygulayabilirsiniz. Bu bilgiler derleyicinin statik çözümleme yapmasına ve bir değişkenin null ne zaman olmadığını belirlemesi için yardımcı olur. Bu makalede, bu özniteliklerin her birinin kısa bir açıklamasını ve bunların nasıl kullanılacağını sağlar. Tüm örnekler C# 8.0 veya daha yeni varsayar ve kod nullable bağlamında.

Tanıdık bir örnekle başlayalım. Kitaplığınızın kaynak dizesini almak için aşağıdaki API'ye sahip olduğunu düşünün:

```csharp
bool TryGetMessage(string key, out string message)
```

Önceki örnek .NET'teki tanıdık `Try*` deseni izler. Bu API için iki başvuru `key` bağımsız `message` değişkeni vardır: ve parametre. Bu API, bu bağımsız değişkenlerin nullness ile ilgili aşağıdaki kurallara sahiptir:

- Arayanlar için `key`argüman `null` olarak geçmemelidir.
- Arayanlar, değeri bağımsız değişken `null` olarak olan `message`bir değişkeni geçirebilir.
- `TryGetMessage` Yöntem dönerse, `true`değeri null `message` değildir. İade değeri `false,` `message` (ve null durumu) değeri ise null.

Kural değişken `key` türü ile ifade edilebilir: `key` nullable olmayan bir başvuru türü olmalıdır. Parametre `message` daha karmaşıktır. Bu `null` argüman olarak izin verir, ama garanti, `out` başarı, bu argüman null değildir. Bu senaryolar için, beklentileri açıklamak için daha zengin bir kelime gerekir.

Değişkenlerin null durumu hakkında ek bilgi ifade etmek için çeşitli öznitelikler eklenmiştir. C# 8'den önce yazdığınız tüm kodlar nullable referans türlerini tanıttı *null habersiz*oldu. Bu, herhangi bir başvuru türü değişkeninin null olabileceği, ancak null denetimlerin gerekli olmadığı anlamına gelir. Bir kez kodunuzu *farkında geçersiz*olduğunda, bu kurallar değişir. Referans türleri hiçbir `null` zaman değer olmamalıdır ve geçersiz başvuru `null` türleri referans gösterilmeden önce karşı denetlenmelidir.

API senaryoda gördüğünüz gibi, API'lerinizin `TryGetValue` kuralları büyük olasılıkla daha karmaşıktır. API'lerinizin çoğu, değişkenlerin ne zaman olabilir veya `null`olamaz için daha karmaşık kurallara sahiptir. Bu gibi durumlarda, bu kuralları ifade etmek için aşağıdaki özniteliklerden birini kullanırsınız:

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Nullolmayan bir giriş bağımsız değişkeni null olabilir.
- [DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): Nullable giriş bağımsız değişkeni asla null olmamalıdır.
- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Nullable olmayan bir iade değeri null olabilir.
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): Nullable iade değeri asla null olmayacaktır.
- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Yöntem belirtilen `bool` değeri döndürdüğünde nullable olmayan bir giriş bağımsız değişkeni olabilir.
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Yöntem belirtilen `bool` değeri döndürdüğünde nullable giriş bağımsız değişkeni null olmaz.
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): Belirtilen parametrenin bağımsız değişkeni null değilse, iade değeri null değildir.
- [DoesNotReturn](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute): Bir yöntem asla dönmez. Başka bir deyişle, her zaman bir özel durum atar.
- [DoesNotReturnIf](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute): İlişkili `bool` parametre belirtilen değere sahipse bu yöntem asla dönmez.

Önceki açıklamalar, her öznitelik ne hızlı bir başvuru vardır. Aşağıdaki her bölümde davranış ve anlamı daha ayrıntılı olarak açıklanır.

Bu özniteliklerin eklenmesi derleyiciye API'nizin kuralları hakkında daha fazla bilgi verir. Arama kodu boşetkinleştirilebilir bir bağlamda derlendiğinde, derleyici bu kuralları ihlal ettiklerinde arayanları uyarır. Bu öznitelikler, uygulamanız üzerinde ek denetimler etkinleştirmiyor.

## <a name="specify-preconditions-allownull-and-disallownull"></a>Ön koşulları `AllowNull` belirtin: ve`DisallowNull`

Makul bir varsayılan değere `null` sahip olduğu için asla geri dönmeyecek bir okuma/yazma özelliği düşünün. Arayanlar, `null` bu varsayılan değere ayarlarken ayarlanan erişime geçer. Örneğin, sohbet odasında ekran adı isteyen bir ileti sistemi düşünün. Hiçbiri sağlanmazsa, sistem rasgele bir ad oluşturur:

```csharp
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName;
```

Önceki kodu boş bir şekilde boş bir bağlamda derlediğinizde, her şey yolundadır. Nullable başvuru türlerini etkinleştirdikten sonra, `ScreenName` özellik nullable olmayan bir başvuru olur. Bu `get` erişimci için doğru: asla `null`geri dönmez. Arayanların döndürülen özelliği kontrol etmeleri `null`gerekmez. Ama şimdi bir `null` uyarı oluşturmak için özellik ayarı. Bu kod türünü desteklemeye devam etmek için, <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute?displayProperty=nameWithType> aşağıdaki kodda gösterildiği gibi özelliğe özniteliği eklersiniz:

```csharp
[AllowNull]
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName = GenerateRandomScreenName();
```

Bu ve bu `using` makalede <xref:System.Diagnostics.CodeAnalysis> tartışılan diğer öznitelikleri kullanmak için bir yönerge eklemeniz gerekebilir. `set` Öznitelik, erişime erişime değil, özelliğe uygulanır. Öznitelik `AllowNull` *ön koşulları*belirtir ve yalnızca girişler için geçerlidir. Erişime erişimin `get` bir iade değeri vardır, ancak giriş bağımsız değişkeni yoktur. Bu nedenle, `AllowNull` öznitelik yalnızca `set` erişimci için geçerlidir.

Önceki örnek, bir bağımsız değişkene `AllowNull` öznitelik eklerken nelere bakMası gerektiğini gösterir:

1. Bu değişken için genel sözleşme olmamalıdır `null`, bu yüzden geçersiz bir başvuru türü istiyorum.
1. Giriş değişkeninin en yaygın kullanım `null`olmasa da olması için senaryolar vardır.

Çoğu zaman özellikleri veya `in`, , `out`ve `ref` bağımsız değişkenler için bu öznitelik gerekir. Öznitelik, `AllowNull` bir değişken genellikle null olmayan en iyi seçimdir, `null` ancak bir ön koşul olarak izin vermek gerekir.

Kontrast bu kullanım `DisallowNull`senaryoları ile : Bu özniteliği, nullable başvuru türünden bir giriş `null`değişkeninin olmaması gerektiğini belirtmek için kullanırsınız. Varsayılan değerin `null` olduğu bir özellik düşünün, ancak istemciler onu yalnızca null olmayan bir değere ayarlayabilir. Aşağıdaki kodu inceleyin:

```csharp
public string ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string _comment;
```

Önceki kod, tasarımınızı `ReviewComment` ifade etmenin en iyi `null`yoludur, ancak bu kod `null`. Bu kod geçersiz kılınabilir farkında olduğunda, bu kavramı arayanlara <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute?displayProperty=nameWithType>şu anlama gelenlere daha net bir şekilde ifade edebilirsiniz:

```csharp
[DisallowNull]
public string? ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string? _comment;
```

Nullable bağlamında, `ReviewComment` `get` erişimci varsayılan değerini `null`döndürebilir. Derleyici, erişimden önce denetlemesi gerektiği konusunda uyarır. Ayrıca, arayanlar, olsa `null`bile, arayanlar açıkça ayarlamak gerektiğini uyarır . `null` Öznitelik `DisallowNull` de bir *ön koşul*belirtir, bu `get` erişimci etkilemez. Aşağıdakiler `DisallowNull` hakkında şu özellikleri gözlemlediğinizde özniteliği kullanırsınız:

1. Değişken, genellikle `null` ilk instantiated çekirdek senaryolarda olabilir.
1. Değişken açıkça ' olarak `null`ayarlanamamalıdır.

Bu durumlar aslında *geçersiz*habersiz kod yaygındır. Nesne özellikleri iki farklı başlatma işlemlerinde ayarlanmış olabilir. Bazı özellikler yalnızca bazı eşzamanlı çalışma tamamlandıktan sonra ayarlanmış olabilir.

Ve `AllowNull` `DisallowNull` öznitelikleri, değişkenler üzerindeki ön koşulların bu değişkenler üzerindeki geçersiz ek açıklamalarla eşleşmeyebileceğini belirtmenizi sağlar. Bunlar, API'nizin özellikleri hakkında daha fazla ayrıntı sağlar. Bu ek bilgiler, arayanların API'nizi doğru kullanmasına yardımcı olur. Aşağıdaki öznitelikleri kullanarak ön koşulları belirttiğinizi unutmayın:

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Nullolmayan bir giriş bağımsız değişkeni null olabilir.
- [DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): Nullable giriş bağımsız değişkeni asla null olmamalıdır.

## <a name="specify-post-conditions-maybenull-and-notnull"></a>Aşağıdaki koşulları belirtin: `MaybeNull` ve`NotNull`

Aşağıdaki imzayı içeren bir yönteminiz olduğunu varsayalım:

```csharp
public Customer FindCustomer(string lastName, string firstName)
```

Aranan ad bulunamadında dönmek `null` için büyük olasılıkla böyle bir yöntem yazmışsınızdır. Bu, `null` kaydın bulunamadıgini açıkça gösteriyor. Bu örnekte, büyük olasılıkla dönüş türünü `Customer` `Customer?`' den ' e değiştirirsiniz İade değerini nullable bir başvuru türü olarak bildirmek, bu API'nin amacını açıkça belirtir.

Genel tanımlar [ve nullability](../../nullable-attributes.md#generic-definitions-and-nullability) kapsamındaki nedenlerden dolayı bu teknik genel yöntemlerle çalışmaz. Benzer bir desen izleyen genel bir yöntem olabilir:

```csharp
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

İade değerinin `T?`. Aranan öğe `null` bulunamıyorsa yöntem döndürür. `T?` İade türünü bildiremediğinizi, yöntem iadesine `MaybeNull` ek açıklama eklersiniz:

```csharp
[return: MaybeNull]
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

Önceki kod, arayanlara sözleşmenin geçersiz bir tür ima ettiğini, ancak iade değerinin aslında null *olabileceğini* bildirir.  `MaybeNull` API'niz genellikle genel bir tür parametresi olan nullable olmayan bir tür olması gerektiğinde `null` özniteliği kullanın, ancak döndürülecek örnekler olabilir.

Tür geçersiz bir başvuru türü `out` olsa `ref` bile, iade değerinin veya bağımsız değişkenin null olmadığını da belirtebilirsiniz. Bir dizinin bir dizi öğeyi tutacak kadar büyük olmasını sağlayan bir yöntem düşünün. Giriş bağımsız değişkeninin kapasitesi yoksa, yordam yeni bir dizi ayırır ve varolan tüm öğeleri kopyalar. Giriş bağımsız değişkeni `null`ise, yordam yeni depolama ayırır. Yeterli kapasite varsa, rutin hiçbir şey yapmaz:

```csharp
public void EnsureCapacity<T>(ref T[] storage, int size)
```

Bu rutini aşağıdaki gibi adlandırabilirsiniz:

```csharp
// messages has the default value (null) when EnsureCapacity is called:
EnsureCapacity<string>(ref messages, 10);
// messages is not null.
EnsureCapacity<string>(messages, 50);
```

Null başvuru türlerini etkinleştirdikten sonra, önceki kodun uyarı olmadan derlediğinden emin olmak istersiniz. Yöntem döndüğünde, bağımsız `storage` değişkenin null olmaması garanti edilir. Ancak, null bir başvuru `EnsureCapacity` ile aramak için kabul edilebilir. Geçersiz bir `storage` başvuru türü yapabilir ve `NotNull` parametre bildirimine post-koşul ekleyebilirsiniz:

```csharp
public void EnsureCapacity<T>([NotNull]ref T[]? storage, int size)
```

Önceki kod varolan sözleşmeyi açıkça ifade eder: Arayanlar `null` değeri olan bir değişkeni geçirebilir, ancak iade değerinin hiçbir zaman null olmadığı garanti edilir. Öznitelik, `NotNull` bağımsız değişken `ref` `out` olarak `null` geçirilebileceği ve bağımsız değişkenler için en yararlı olan, ancak yöntem döndüğünde bu bağımsız değişkenin null olmaması garanti edilir.

Aşağıdaki öznitelikleri kullanarak koşulsuz postconditions belirtin:

- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Nullable olmayan bir iade değeri null olabilir.
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): Nullable iade değeri asla null olmayacaktır.

## <a name="specify-conditional-post-conditions-notnullwhen-maybenullwhen-and-notnullifnotnull"></a>Koşullu koşullar `NotNullWhen`belirtin: `MaybeNullWhen`, , ve`NotNullIfNotNull`

Muhtemelen yönteme `string` <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType>aşinasınızdır. Bağımsız değişken `true` null veya boş bir dize olduğunda bu yöntem döndürür. Bu bir null-check şeklidir: Arayanların yöntem dönerse `false`bağımsız değişkeni geçersiz olarak denetlemelerine gerek yoktur. Bu gibi bir yöntemi kullanılabilir farkında yapmak için, bağımsız değişkeni boşolabilir başvuru `NotNullWhen` türüne ayarlar ve özniteliği eklersiniz:

```csharp
bool IsNullOrEmpty([NotNullWhen(false)]string? value);
```

Bu, derleyiciye, iade değerinin bulunduğu `false` herhangi bir kodun geçersiz olarak kontrol edilmesine gerek olmadığını bildirir. Öznitelik eklenmesi gerekli null denetimi `IsNullOrEmpty` gerçekleştiren derleyicinin statik çözümlemesi bildirir: `false`döndürdüğünde, giriş `null`bağımsız değişkeni .

```csharp
string? userInput = GetUserInput();
if (!string.IsNullOrEmpty(userInput))
{
   int messageLength = userInput.Length; // no null check needed.
}
// null check needed on userInput here.
```

Yöntem <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType> yukarıda .NET Core 3.0 için gösterildiği gibi açıklamalı olacaktır. Kod tabanınızda, geçersiz değerler için nesnelerin durumunu denetleyen benzer yöntemler olabilir. Derleyici özel null denetim yöntemlerini tanımaz ve ek açıklamaları kendiniz eklemeniz gerekir. Öznitelik eklediğinizde, derleyicinin statik çözümlemesi test edilen değişkenin null denetlendiğini bilir.

Bu öznitelikler için `Try*` başka bir kullanım desendir. Postconditions ve `ref` `out` değişkenler iade değeri üzerinden iletilir. Daha önce gösterilen bu yöntemi göz önünde bulundurun:

```csharp
bool TryGetMessage(string key, out string message)
```

Önceki yöntem tipik bir .NET deyimini izler: döndürme `message` değeri, bulunan değere veya ileti bulunmazsa varsayılan değere ayarlandığını gösterir. Yöntem dönerse, `true`değeri `message` null değildir; aksi takdirde, `message` yöntem null ayarlar.

Bu deyimi `NotNullWhen` özniteliği kullanarak iletebilirsiniz. Geçersiz başvuru türleri için imzayı güncelleştirdiğinizde, bir `message` `string?` öznitelik yapın ve ekleyin:

```csharp
bool TryGetMessage(string key, [NotNullWhen(true)] out string? message)
```

Önceki örnekte, döndürdüğünde `message` `TryGetMessage` `true`değerinin null olmadığı bilinmektedir. Kod tabanınızdaki benzer yöntemlere aynı şekilde açıklama yapmalısınız: bağımsız `null`değişkenler yöntem döndüğünde `true`null olmayabilir ve bunlarla birlikte olduğu bilinmektedir.

İhtiyaç duyabileceğiniz son bir özellik daha vardır. Bazen bir iade değerinin null durumu, bir veya daha fazla giriş bağımsız değişkeninin null durumuna bağlıdır. Bu yöntemler, belirli giriş bağımsız değişkenleri olmadığında `null`null olmayan bir değer döndürecek. Bu yöntemlere doğru açıklama ekinvermek `NotNullIfNotNull` için özniteliği kullanırsınız. Aşağıdaki yöntemi göz önünde bulundurun:

```csharp
string GetTopLevelDomainFromFullUrl(string url);
```

`url` Bağımsız değişken null değilse, çıktı . `null` Geçersiz başvurular etkinleştirildikten sonra, API'nizin hiçbir zaman null girişi kabul etmemesi koşuluyla, bu imza doğru çalışır. Ancak, giriş null olabilir, o zaman döndürme değeri de null olabilir. Bu nedenle, imzayı aşağıdaki kodla değiştirebilirsiniz:

```csharp
string? GetTopLevelDomainFromFullUrl(string? url);
```

Bu da çalışır, ancak genellikle arayanlar `null` ekstra denetimler uygulamak için zorlar. Sözleşme, iade değerinin `null` yalnızca giriş bağımsız değişkeni `url` `null`. Bu sözleşmeyi ifade etmek için, aşağıdaki kodda gösterildiği gibi bu yönteme açıklama lar ekine bilirsiniz:

```csharp
[return: NotNullIfNotNull("url")]
string? GetTopLevelDomainFromFullUrl(string? url);
```

İade değeri ve bağımsız değişken, her ikisi `?` de olabilir belirten `null`ile açıklamalı edilmiştir . Öznitelik, `url` bağımsız değişken olmadığında geri dönüş değerinin null olmayacağını daha `null`da açıklar.

Bu öznitelikleri kullanarak koşullu posta koşullarını belirtirsiniz:

- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Yöntem belirtilen `bool` değeri döndürdüğünde nullable olmayan bir giriş bağımsız değişkeni olabilir.
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Yöntem belirtilen `bool` değeri döndürdüğünde nullable giriş bağımsız değişkeni null olmaz.
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): Belirtilen parametrenin giriş bağımsız değişkeni null değilse, iade değeri null değildir.

## <a name="verify-unreachable-code"></a>Erişilemenebilen kodu doğrulama

Bazı yöntemler, genellikle özel durum yardımcıları veya diğer yardımcı yöntemleri, her zaman bir özel durum atarak çıkmak. Veya, bir yardımcı Boolean bağımsız değişkeninin değerine dayalı bir özel durum atabilir.

İlk durumda, yöntem bildirimine `DoesNotReturn` öznitelik ekleyebilirsiniz. Derleyici size üç şekilde yardımcı olur. İlk olarak, derleyici, yöntemin özel durum atmadan çıkabileceği bir yol varsa bir uyarı yayınlar. İkinci olarak, derleyici, uygun `catch` bir yan tümceyle karşılaşıncaya kadar, bu yönteme yapılan bir çağrıdan sonra herhangi bir kodu *erişilemez*olarak işaretler. Üçüncü olarak, erişilebilen kod herhangi bir null durumları etkilemez. Bu yöntemi göz önünde bulundurun:

```csharp
[DoesNotReturn]
private void FailFast()
{
   throw new InvalidOperationException();
}

public void SetState(object containedField)
{
   if (!isInitialized)
      FailFast();

   // unreachable code:
   this.field = containedField;
}
```

İkinci durumda, yöntemin `DoesNotReturnIf` Boolean parametreöze özniteliği ekleyin. Önceki örneği aşağıdaki gibi değiştirebilirsiniz:

```csharp
private void FailFast([DoesNotReturnIf(false)]bool isValid)
{
   if (!isValid)
       throw new InvalidOperationException();
}

public void SetState(object containedField)
{
   FailFast(isInitialized);

   // unreachable code when "isInitialized" is false:
   this.field = containedField;
}
```

## <a name="summary"></a>Özet

Nullable başvuru türleri eklemek, API'ler'in değişkenler için `null`beklentilerini açıklamak için bir başlangıç sözcük dağarcığı sağlar. Ek öznitelikler, değişkenlerin null durumunu ön koşul ve koşul olarak tanımlamak için daha zengin bir sözcük dağarcığı sağlar. Bu öznitelikler, beklentilerinizi daha net bir şekilde açıklar ve API'lerinizi kullanan geliştiriciler için daha iyi bir deneyim sağlar.

Kitaplıkları boşbir bağlam için güncellerken, API'lerinizin kullanıcılarına doğru kullanıma rehberlik etmek için bu öznitelikleri ekleyin. Bu öznitelikler, giriş bağımsız değişkenlerinin ve döndürme değerlerinin null durumunu tam olarak açıklamanıza yardımcı olur:

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Nullolmayan bir giriş bağımsız değişkeni null olabilir.
- [DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): Nullable giriş bağımsız değişkeni asla null olmamalıdır.
- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Nullable olmayan bir iade değeri null olabilir.
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): Nullable iade değeri asla null olmayacaktır.
- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Yöntem belirtilen `bool` değeri döndürdüğünde nullable olmayan bir giriş bağımsız değişkeni olabilir.
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Yöntem belirtilen `bool` değeri döndürdüğünde nullable giriş bağımsız değişkeni null olmaz.
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): Belirtilen parametrenin giriş bağımsız değişkeni null değilse, iade değeri null değildir.
- [DoesNotReturn](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute): Bir yöntem asla dönmez. Başka bir deyişle, her zaman bir özel durum atar.
- [DoesNotReturnIf](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute): İlişkili `bool` parametre belirtilen değere sahipse bu yöntem asla dönmez.
