---
title: 'C# ayrılmış öznitelikleri: Nullable statik analiz'
ms.date: 02/02/2021
description: Bu öznitelikler, null yapılabilir ve null yapılamayan başvuru türleri için daha iyi statik analiz sağlamak üzere derleyici tarafından yorumlanır.
ms.openlocfilehash: 91bba16506e2e8bbac9fdef2d1c4badcf59c1546
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100432575"
---
# <a name="reserved-attributes-contribute-to-the-compilers-null-state-static-analysis"></a>Ayrılmış öznitelikler derleyicinin null durum statik analizine katkıda bulunur

Null yapılabilir bir bağlamda, derleyici, tüm başvuru türü değişkenlerinin null durumunu tespit etmek üzere kodun statik analizini yapar:

- *null değil*: statik analiz bir değişkene null olmayan bir değer atandığını belirler.
- *null olabilir*: statik analiz, bir değişkene null olmayan bir değer atandığını belirleyemiyor.

Derleyiciye API 'Ler hakkında bilgi sağlayan öznitelikleri uygulayabilirsiniz. Bu bilgiler derleyicinin statik analiz gerçekleştirmesini ve bir değişkenin ne zaman null olmadığını belirlemesine yardımcı olur. Bu makalede, bu özniteliklerin her biri ve nasıl kullanılacağı hakkında kısa bir açıklama sunulmaktadır. Tüm örneklerde C# 8,0 veya üzeri varsayılır ve kod null yapılabilir bir bağlamda yer almıyor.

Tanıdık bir örnekle başlayalım. Kitaplığınızın bir kaynak dizesini almak için aşağıdaki API 'ye sahip olduğunu düşünün:

```csharp
bool TryGetMessage(string key, out string message)
```

Yukarıdaki örnek, `Try*` .net 'teki tanıdık olan bir model izler. Bu API için iki başvuru bağımsız değişkeni vardır: `key` ve `message` parametresi. Bu API, bu bağımsız değişkenlerin nulldurumuyla ilgili aşağıdaki kurallara sahiptir:

- Çağıranlar `null` için bağımsız değişken olarak geçmemelidir `key` .
- Çağıranlar, değeri bağımsız değişkeni olan bir değişken geçirebilir `null` `message` .
- `TryGetMessage`Yöntemi döndürürse `true` , değeri `message` null değildir. Dönüş değeri `false,` `message` (ve null durumu) değeri null ise.

Kuralı `key` değişken türüne göre ifade edilebilir: `key` null yapılamayan bir başvuru türü olmalıdır. `message`Parametresi daha karmaşıktır. `null`Bağımsız değişken olarak izin verir, ancak başarıyı, bu `out` bağımsız değişkenin null olmadığını garanti eder. Bu senaryolar için beklentileri betimleyen daha zengin bir sözlük gerekir.

Değişkenlerin null durumu hakkında ek bilgileri ifade etmek için çeşitli öznitelikler eklenmiştir. C# 8 ' den önce yazdığınız tüm kod null yapılabilir başvuru türleri olarak *null zorunluluvou* idi. Yani herhangi bir başvuru türü değişkeni null olabilir, ancak null denetimleri gerekli değildir. Kodunuz *Nullable olarak farkında* olduktan sonra bu kurallar değişir. Başvuru türleri asla `null` değer olmamalı ve null yapılabilir başvuru türleri `null` başvurulmadan önce denetlenmelidir.

API 'si senaryosuyla gördüğünüz gibi API 'lerinizin kuralları büyük olasılıkla daha karmaşıktır `TryGetValue` . API 'lerinizin birçoğu, değişkenlerin ne zaman veya ne zaman oluşturulabileceğine ilişkin daha karmaşık kurallara sahiptir `null` . Bu durumlarda, bu kuralları ifade etmek için aşağıdaki özniteliklerden birini kullanacaksınız:

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): null yapılamayan bir giriş bağımsız değişkeni null olabilir.
- [Disallownull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): null olabilen bir giriş bağımsız değişkeni hiçbir şekilde null olmamalıdır.
- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): null yapılamayan bir dönüş değeri null olabilir.
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): null olabilen bir dönüş değeri hiçbir şekilde null olmaz.
- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): yöntem belirtilen değeri döndürdüğünde null yapılamayan bir giriş bağımsız değişkeni null olabilir `bool` .
- [Notnullne zaman](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): yöntem belirtilen değeri döndürdüğünde null yapılabilir giriş bağımsız değişkeni null olmaz `bool` .
- [Notnullifnotnull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): belirtilen parametrenin bağımsız değişkeni null değilse, dönüş değeri null olamaz.
- Hayır: bir yöntem hiçbir [şekilde döndürmez.](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute) Diğer bir deyişle, her zaman bir özel durum oluşturur.
- Yok [: ilişkili](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute) `bool` parametre belirtilen değere sahipse, bu yöntem hiçbir şekilde döndürmez.
- [Membernotnull](xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute): yöntem döndüğünde listelenen üye null olmaz.
- [Membernotnullne zaman](xref:System.Diagnostics.CodeAnalysis.MemberNotNullWhenAttribute): yöntem belirtilen değeri döndürdüğünde listelenen üye null olmaz `bool` .

Yukarıdaki açıklamalar, her bir özniteliğin yaptığı işe yönelik hızlı bir başvurudur. Aşağıdaki her bölümde davranışı ve anlamı daha kapsamlı bir şekilde açıklanmıştır.

Bu özniteliklerin eklenmesi, derleyiciye API 'nizin kuralları hakkında daha fazla bilgi verir. Kodu çağırma özelliği, null yapılabilir etkin bir bağlamda derlenirse, derleyici bu kuralları ihlal ettiklerinde çağıranları uyarır. Bu öznitelikler, uygulamanızda daha fazla denetim etkinleştirmez.

## <a name="specify-preconditions-allownull-and-disallownull"></a>Önkoşulları belirtin: `AllowNull` ve `DisallowNull`

`null`Makul bir varsayılan değere sahip olduğu için hiçbir süre döndürülmediği bir okuma/yazma özelliği düşünün. Çağıranlar `null` , bu varsayılan değere ayarlarken ayarlanan erişimciye geçer. Örneğin, bir sohbet odasında ekran adı isteyen bir mesajlaşma sistemi düşünün. Hiçbiri sağlanmazsa, sistem rastgele bir ad üretir:

```csharp
public string ScreenName
{
   get => _screenName;
   set => _screenName = value ?? GenerateRandomScreenName();
}
private string _screenName;
```

Önceki kodu null olabilir bir zorunluluvou bağlamında derlerken her şey iyidir. Null yapılabilir başvuru türlerini etkinleştirdikten sonra, `ScreenName` özelliği null yapılamayan bir başvuru haline gelir. Bu, erişimci için doğrudur `get` : hiçbir şekilde döndürmez `null` . Çağıranlar için döndürülen özelliği denetmek zorunda değildir `null` . Ancak şimdi özelliği `null` bir uyarı oluşturacak şekilde ayarlanıyor. Bu tür bir kodu desteklemek için, <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute?displayProperty=nameWithType> aşağıdaki kodda gösterildiği gibi özniteliğini özelliği ekleyin:

```csharp
[AllowNull]
public string ScreenName
{
   get => _screenName;
   set => _screenName = value ?? GenerateRandomScreenName();
}
private string _screenName = GenerateRandomScreenName();
```

Bu `using` <xref:System.Diagnostics.CodeAnalysis> makalede ele alınan bu ve diğer özniteliklerin kullanılması için bir yönerge eklemeniz gerekebilir. Özniteliği, erişimciye değil, özelliğine uygulanır `set` . `AllowNull`Öznitelik, *ön koşulları* belirtir ve yalnızca girişler için geçerlidir. `get`Erişimcinin dönüş değeri var, ancak giriş bağımsız değişkeni yok. Bu nedenle, `AllowNull` öznitelik yalnızca erişimci için geçerlidir `set` .

Yukarıdaki örnekte, `AllowNull` bir bağımsız değişkende özniteliği eklenirken ne aranacağı gösterilmektedir:

1. Bu değişken için genel sözleşme bunun olmaması `null` , bu nedenle null atanamaz bir başvuru türü istemeniz gerekir.
1. Giriş değişkeninin en yaygın kullanımları olmadıkları halde olması için senaryolar vardır `null` .

Çoğu kez bu özniteliğe özellikler, veya `in` , `out` ve bağımsız değişkenler için ihtiyaç duyarsınız `ref` . `AllowNull`Özniteliği genellikle null olmayan ancak önkoşul olarak izin vermeniz gereken en iyi seçenektir `null` .

Kullanma senaryolarıyla karşıtlık `DisallowNull` : Bu özniteliği, null atanabilir bir başvuru türünün giriş değişkeninin olmaması gerektiğini belirtmek için kullanırsınız `null` . `null`Varsayılan değer olan, ancak istemciler yalnızca null olmayan bir değere ayarlayabileceği bir özelliği düşünün. Aşağıdaki kodu inceleyin:

```csharp
public string ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string _comment;
```

Önceki kod, tasarımınızı ifade etmenin en iyi yoludur `ReviewComment` `null` , ancak olarak ayarlanamaz `null` . Bu kod null yapılabilir olduğunda, bu kavramı kullanarak çağıranlara daha net bir şekilde ifade edebilirsiniz <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute?displayProperty=nameWithType> :

```csharp
[DisallowNull]
public string? ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string? _comment;
```

Null yapılabilir bir bağlamda, `ReviewComment` `get` erişimci varsayılan değerini döndürebilir `null` . Derleyici, erişim öncesinde denetlenmesi gerektiğini uyarır. Buna ek olarak, arayanlara açıkça ayarlanmaması durumunda bile arayanlara uyarır `null` `null` . `DisallowNull`Öznitelik bir *ön koşul* da belirtir, `get` erişimciyi etkilemez. `DisallowNull`Aşağıdaki özellikleri gözlemlediğiniz zaman özniteliğini kullanabilirsiniz:

1. Değişken `null` , genellikle ilk örneği oluşturulduğunda temel senaryolarda olabilir.
1. Değişken açıkça olarak ayarlanmamalıdır `null` .

Bu durumlar, başlangıçta *null yükümlülüğü* oluşturulan kodda ortaktır. Nesne özelliklerinin iki ayrı başlatma işlemi olarak ayarlanmış olması olabilir. Bazı özelliklerin bazı zaman uyumsuz çalışma tamamlandıktan sonra ayarlanmış olması olabilir.

`AllowNull`Ve `DisallowNull` öznitelikleri, değişkenlerde önkoşulların Bu değişkenlerde null yapılabilir ek açıklamalarıyla eşleşmeyebilir belirtmenize olanak tanır. Bunlar, API 'nizin özellikleri hakkında daha ayrıntılı bilgi sağlar. Bu ek bilgiler, arayanların API 'nizi doğru şekilde kullanmasına yardımcı olur. Aşağıdaki öznitelikleri kullanarak önkoşulları belirtdüğünü unutmayın:

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): null yapılamayan bir giriş bağımsız değişkeni null olabilir.
- [Disallownull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): null olabilen bir giriş bağımsız değişkeni hiçbir şekilde null olmamalıdır.

## <a name="specify-post-conditions-maybenull-and-notnull"></a>Son koşulları belirtin: `MaybeNull` ve `NotNull`

Aşağıdaki imzaya sahip bir yönteminiz olduğunu varsayalım:

```csharp
public Customer FindCustomer(string lastName, string firstName)
```

Aranan ad bulunamadığı zaman döndürmek için bunun gibi bir yöntem yazmış oluk `null` . `null`Açıkça kaydın bulunamadığını gösterir. Bu örnekte, büyük olasılıkla ' dan ' a dönüş türünü değiştirirsiniz `Customer` `Customer?` . Dönüş değerinin null yapılabilir bir başvuru türü olarak bildirilmesi, bu API 'nin amacını açıkça belirtir.

[Genel tanımlar ve null değer alabilme](../../nullable-migration-strategies.md#generic-definitions-and-nullability) bölümünde ele alınan nedenler için, tekniği genel yöntemlerle çalışmaz. Benzer bir kalıbı izleyen genel bir yönteminiz olabilir:

```csharp
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> predicate)
```

Dönüş değerinin olduğunu belirtemezsiniz `T?` . Yöntemi, `null` Aranan öğe bulunamadığında döndürür. Bir dönüş türü bildirebileceğinizden `T?` , `MaybeNull` ek açıklamayı Yöntem döndürecek şekilde eklersiniz:

```csharp
[return: MaybeNull]
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> predicate)
```

Yukarıdaki kod, arayanlara sözleşmenin null yapılamayan bir tür gösterdiği anlamına gelir, ancak *dönüş değeri gerçekten null olabilir.*  `MaybeNull`API 'niz null yapılamayan bir tür olması gerektiği zaman, genellikle genel bir tür parametresi olması durumunda özniteliği kullanın, ancak döndürülecek örnekler olabilir `null` .

Bir dönüş değeri veya `out` ya da `ref` bağımsız değişkenin tür, null değer atanabilir bir başvuru türü olmasına rağmen null olmadığını belirtebilirsiniz. Bir dizinin birçok öğe tutabilecek kadar büyük olmasını sağlayan bir yöntemi düşünün. Giriş bağımsız değişkeninin kapasitesi yoksa, yordam yeni bir dizi ayırır ve var olan tüm öğeleri buna kopyalar. Giriş bağımsız değişkeni ise `null` , yordam yeni depolama alanı ayırır. Yeterli kapasite varsa, yordam hiçbir şey yapmaz:

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

Null başvuru türlerini etkinleştirdikten sonra, önceki kodun uyarı olmadan derlendiğinden emin olmak istersiniz. Yöntemi döndürüldüğünde `storage` bağımsız değişkenin null olmaması garanti edilir. Ancak, `EnsureCapacity` bir null başvurusuyla çağırmak kabul edilebilir. `storage`Null yapılabilir bir başvuru türü yapabilir ve `NotNull` parametre bildirimine son koşulu ekleyebilirsiniz:

```csharp
public void EnsureCapacity<T>([NotNull] ref T[]? storage, int size)
```

Yukarıdaki kod, mevcut sözleşmeyi açık bir şekilde ifade eder: çağıranlar değer ile bir değişken geçirebilir `null` , ancak dönüş değeri hiçbir şekilde null olmamalıdır. `NotNull`Özniteliği ve bağımsız değişken olarak geçirilebilecek bağımsız değişkenler için en yararlı seçenektir `ref` `out` `null` , ancak yöntemin döndürdüğü zaman değişkenin null olmaması garanti edilir.

Aşağıdaki öznitelikleri kullanarak koşulsuz Sonkoşulları belirtirsiniz:

- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): null yapılamayan bir dönüş değeri null olabilir.
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): null olabilen bir dönüş değeri hiçbir şekilde null olmaz.

## <a name="specify-conditional-post-conditions-notnullwhen-maybenullwhen-and-notnullifnotnull"></a>Koşullu koşulları belirtin: `NotNullWhen` , `MaybeNullWhen` , ve `NotNullIfNotNull`

Büyük olasılıkla yöntemiyle ilgili bilgi sahibisiniz `string` <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType> . Bu yöntem `true` , bağımsız değişken null veya boş bir dize olduğunda döndürür. Bu bir null denetim biçimidir: çağıranların null olması gerekmez; yöntemin döndürdüğü bağımsız değişkeni kontrol edin `false` . Bu null yapılabilir bir yöntemi gibi bir yöntem oluşturmak için bağımsız değişkenini null atanabilir bir başvuru türüne ayarlarsınız ve `NotNullWhen` özniteliği ekleyebilirsiniz:

```csharp
bool IsNullOrEmpty([NotNullWhen(false)] string? value);
```

Bu, derleyiciye dönüş değerinin null denetimleri gerektirmeyen herhangi bir kod olduğunu bildirir `false` . Özniteliğin eklenmesi, derleyicinin statik analizini, `IsNullOrEmpty` gerekli null denetimini yerine getiren bildirir: döndüğünde `false` , giriş bağımsız değişkeni değildir `null` .

```csharp
string? userInput = GetUserInput();
if (!string.IsNullOrEmpty(userInput))
{
   int messageLength = userInput.Length; // no null check needed.
}
// null check needed on userInput here.
```

<xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType>Yöntemi, .NET Core 3,0 için yukarıda gösterildiği gibi açıklanacaktır. Kod tabanınızda, null değerler için nesnelerin durumunu kontrol eden benzer yöntemlere sahip olabilirsiniz. Derleyici özel null denetim yöntemlerini tanımaz ve ek açıklamaları kendiniz eklemeniz gerekir. Özniteliğini eklediğinizde, derleyicinin statik analizi, sınanan değişkenin null olarak işaretli olduğunu bilir.

Bu öznitelikler için başka bir kullanım de modeldir `Try*` . Ve değişkenleri için Sonkoşulları, `ref` `out` dönüş değeri üzerinden iletilir. Daha önce gösterilen bu yöntemi göz önünde bulundurun:

```csharp
bool TryGetMessage(string key, out string message)
```

Yukarıdaki yöntem tipik bir .NET deyimidir OM: dönüş değeri, `message` bulunan değer olarak ayarlanmış olup olmadığını veya hiçbir ileti bulunamazsa varsayılan değere ayarlandığını gösterir. Yöntemi döndürürse `true` , değeri `message` null değildir; Aksi takdirde, yöntemi `message` null olarak ayarlanır.

Özniteliği kullanarak bu deyimden iletişim kurabilirsiniz `NotNullWhen` . Null yapılabilir başvuru türleri için imzayı güncelleştirdiğinizde `message` bir `string?` özniteliği oluşturun ve ekleyin:

```csharp
bool TryGetMessage(string key, [NotNullWhen(true)] out string? message)
```

Önceki örnekte, değeri `message` döndüğünde null değil olarak bilinir `TryGetMessage` `true` . Kod tabanınızda benzer yöntemlere aynı şekilde açıklama eklenmelidir: bağımsız değişkenler olabilir `null` ve yöntem döndürüldüğünde null olmadığı bilinmektedir `true` .

Ayrıca ihtiyacınız olabilecek bir son öznitelik vardır. Bazen bir dönüş değerinin null durumu, bir veya daha fazla giriş bağımsız değişkenlerinin null durumuna bağlıdır. Bu yöntemler, belirli giriş bağımsız değişkenleri olmadığında null olmayan bir değer döndürür `null` . Bu yöntemlere doğru şekilde açıklama eklemek için özniteliğini kullanırsınız `NotNullIfNotNull` . Aşağıdaki yöntemi göz önünde bulundurun:

```csharp
string GetTopLevelDomainFromFullUrl(string url);
```

`url`Bağımsız değişken null değilse, çıktı değildir `null` . Null yapılabilir başvurular etkinleştirildikten sonra, bu imza doğru şekilde çalışarak API 'niz hiçbir şekilde null girişi kabul etmez. Ancak, giriş null ise, dönüş değeri de null olabilir. İmzayı şu kodla değiştirebilirsiniz:

```csharp
string? GetTopLevelDomainFromFullUrl(string? url);
```

Bu da çalışır, ancak arayanlara çok fazla denetim uygulamak için zorlayacaktır `null` . Sözleşmenin dönüş değeri `null` yalnızca giriş bağımsız değişkeni olduğunda olacaktır `url` `null` . Bu sözleşmeyi ifade etmek için, aşağıdaki kodda gösterildiği gibi bu yönteme açıklama ekleyebilirsiniz:

```csharp
[return: NotNullIfNotNull("url")]
string? GetTopLevelDomainFromFullUrl(string? url);
```

Dönüş değerine ve bağımsız değişkenine, her iki durumda da olabilecek şekilde açıklama eklenmiş `?` `null` . Özniteliği, bağımsız değişken olmadığında dönüş değerinin null olmaması gerektiğini açıklığa kavuşturulur `url` `null` .

Şu öznitelikleri kullanarak koşullu Sonkoşulları belirtirsiniz:

- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): yöntem belirtilen değeri döndürdüğünde null yapılamayan bir giriş bağımsız değişkeni null olabilir `bool` .
- [Notnullne zaman](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): yöntem belirtilen değeri döndürdüğünde null yapılabilir giriş bağımsız değişkeni null olmaz `bool` .
- [Notnullifnotnull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): belirtilen parametrenin giriş bağımsız değişkeni null değilse, dönüş değeri null olamaz.

## <a name="constructor-helper-methods-membernotnull-and-membernotnullwhen"></a>Oluşturucu yardımcı yöntemleri: `MemberNotNull` ve `MemberNotNullWhen`

Bu öznitelikler, oluşturuculardan yardımcı yöntemlere ortak kod yeniden düzenlenmiş sahip olduğunuzda amacınızı belirler. C# derleyicisi, her bir Oluşturucu döndürülmeden önce null yapılamayan tüm başvuru alanlarının başlatıldığından emin olmak için oluşturucuları ve alan başlatıcıları analiz eder. Ancak, C# derleyicisi tüm yardımcı yöntemler aracılığıyla alan atamalarını izlemez. Derleyici, `CS8618` alanlar doğrudan oluşturucuda başlatılmadığında, ancak bir yardımcı yönteminde değil, uyarı verir. <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute>Yöntemini bir yöntem bildirimine eklersiniz ve yöntemdeki null olmayan bir değere başlatılan alanları belirtirsiniz. Örneğin, aşağıdaki örneği göz önünde bulundurun:

:::code language="csharp" source="snippets/InitializeMembers.cs" ID="MemberNotNullExample":::

Öznitelik oluşturucusunda bağımsız değişken olarak birden çok alan adı belirtebilirsiniz `MemberNotNull` .

, <xref:System.Diagnostics.CodeAnalysis.MemberNotNullWhenAttribute> Bir `bool` bağımsız değişkenine sahiptir. `MemberNotNullWhen`Yardımcı yönteminizin, `bool` Yardım yönteminizin alanları başlattığını belirten bir durum olduğu durumlarda kullanırsınız.

## <a name="verify-unreachable-code"></a>Erişilemeyen kodu doğrula

Bazı yöntemler, genellikle özel durum yardımcıları veya diğer yardımcı yöntemler, her zaman bir özel durum oluşturarak çıkış yapılır. Ya da bir yardımcı, Boole bağımsız değişkeninin değerine göre bir özel durum oluşturabilir.

İlk durumda, `DoesNotReturn` metot bildirimine özniteliğini ekleyebilirsiniz. Derleyici üç şekilde size yardımcı olur. İlk olarak, yöntemin bir özel durum oluşturmadan çıkabileceği bir yol varsa derleyici bir uyarı verir. İkinci olarak, *derleyici, uygun* bir yan tümce bulunana kadar bu yönteme bir çağrıdan sonra kodu işaretler `catch` . Üçüncü olarak, erişilemeyen kod hiçbir null durumu etkilemez. Şu yöntemi göz önünde bulundurun:

```csharp
[DoesNotReturn]
private void FailFast()
{
    throw new InvalidOperationException();
}

public void SetState(object containedField)
{
    if (!isInitialized)
    {
        FailFast();
    }

    // unreachable code:
    _field = containedField;
}
```

İkinci durumda, `DoesNotReturnIf` özniteliğini yönteminin bir Boolean parametresine eklersiniz. Önceki örneği aşağıdaki gibi değiştirebilirsiniz:

```csharp
private void FailFast([DoesNotReturnIf(false)] bool isValid)
{
    if (!isValid)
    {
        throw new InvalidOperationException();
    }
}

public void SetState(object containedField)
{
    FailFast(isInitialized);

    // unreachable code when "isInitialized" is false:
    _field = containedField;
}
```

## <a name="summary"></a>Özet

[!INCLUDE [C# version alert](../../includes/csharp-version-alert.md)]

Null yapılabilir başvuru türleri eklemek, olabilecek değişkenlere yönelik API beklentilerinizi tanımlayan bir başlangıç sözlüğü sağlar `null` . Öznitelikleri, değişkenlerin, ön koşullar ve Postconditions olarak null durumunu açıklamaya yönelik daha zengin bir sözlük sağlar. Bu öznitelikler beklentilerinizi daha net bir şekilde anlatır ve API 'lerinizi kullanan geliştiriciler için daha iyi bir deneyim sağlar.

Bir null yapılabilir bağlam için kitaplıkları güncelleştirdiğinizde, API 'lerinizi kullanıcılarına doğru kullanım için bu öznitelikleri ekleyin. Bu öznitelikler, giriş bağımsız değişkenlerinin ve dönüş değerlerinin Null durumunu tam olarak açıklamanıza yardımcı olur:

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): null yapılamayan bir giriş bağımsız değişkeni null olabilir.
- [Disallownull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): null olabilen bir giriş bağımsız değişkeni hiçbir şekilde null olmamalıdır.
- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): null yapılamayan bir dönüş değeri null olabilir.
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): null olabilen bir dönüş değeri hiçbir şekilde null olmaz.
- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): yöntem belirtilen değeri döndürdüğünde null yapılamayan bir giriş bağımsız değişkeni null olabilir `bool` .
- [Notnullne zaman](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): yöntem belirtilen değeri döndürdüğünde null yapılabilir giriş bağımsız değişkeni null olmaz `bool` .
- [Notnullifnotnull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): belirtilen parametrenin giriş bağımsız değişkeni null değilse, dönüş değeri null olamaz.
- Hayır: bir yöntem hiçbir [şekilde döndürmez.](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute) Diğer bir deyişle, her zaman bir özel durum oluşturur.
- Yok [: ilişkili](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute) `bool` parametre belirtilen değere sahipse, bu yöntem hiçbir şekilde döndürmez.
