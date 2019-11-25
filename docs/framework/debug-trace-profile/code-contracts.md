---
title: Kod Sözleşmeleri
ms.date: 09/05/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Code contracts
ms.assetid: 84526045-496f-489d-8517-a258cf76f040
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 103d668dd7a7436fd1acdccdc0afc2431ed8372a
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975005"
---
# <a name="code-contracts"></a>Kod Sözleşmeleri

Kod sözleşmeleri, kodunuzda önkoşulları, Postconditions ve nesne ınvaryantları belirtmek için bir yol sağlar. Önkoşullar, bir yöntem veya özellik girilirken karşılanması gereken gereksinimlerdir. Postconditions, yöntem veya özellik kodunun çıkış sırasında beklentileri anlatmaktadır. Nesne ınvaryantları, iyi durumda olan bir sınıf için beklenen durumu tanımlıyor.

Kod sözleşmeleri, kodunuzu işaretlemek için sınıflar, derleme zamanı analizi için bir statik çözümleyici ve bir çalışma zamanı Çözümleyicisi içerir. Kod sözleşmeleri sınıfları <xref:System.Diagnostics.Contracts> ad alanında bulunabilir.

Kod sözleşmelerinin avantajları şunlardır:

- İyileştirilmiş test: kod sözleşmeleri statik sözleşme doğrulaması, çalışma zamanı denetimi ve belge oluşturma sağlar.

- Otomatik test araçları: önkoşulları karşılamayan anlamlı test bağımsız değişkenlerini filtreleyerek daha anlamlı birim testleri oluşturmak için kod sözleşmelerini kullanabilirsiniz.

- Statik doğrulama: statik denetleyici, programı çalıştırmadan herhangi bir sözleşme ihlali olup olmadığına karar verebilir. Null başvuru ve dizi sınırları ve açık sözleşmeler gibi örtük sözleşmeleri denetler.

- Başvuru belgeleri: belge Oluşturucu, mevcut XML belge dosyalarını sözleşme bilgileriyle genişlettiğini. Ayrıca, üretilen belge sayfalarında sözleşme bölümleri olması için [sanderle](https://github.com/EWSoftware/SHFB) ile kullanılabilen stil sayfaları vardır.

Tüm .NET Framework diller, sözleşmelerin avantajlarından hemen faydalanabilir; özel bir Ayrıştırıcı veya derleyici yazmak zorunda değilsiniz. Visual Studio eklentisi, gerçekleştirilecek kod sözleşmesi analizinin düzeyini belirtmenize olanak tanır. Çözümleyiciler, sözleşmelerin doğru biçimlendirildiğini (tür denetimi ve ad çözümlemesi) ve Microsoft ara dili (MSIL) biçiminde sözleşmelerin derlenmiş bir formunu oluşturabildiğini doğrulayabilirler. Visual Studio 'da sözleşme yazma, araç tarafından sunulan standart IntelliSense 'den yararlanmanızı sağlar.

Anlaşma sınıfındaki yöntemlerin çoğu koşullu olarak derlenir; diğer bir deyişle, derleyici bu yöntemlere yalnızca özel bir sembol tanımladığınızda, CONTRACTS_FULL `#define` yönergesini kullanarak çağrı yayar. CONTRACTS_FULL, `#ifdef` yönergeleri kullanmadan kodunuzda sözleşmeleri yazmanızı sağlar; farklı yapılar, bazıları sözleşmelerle ve bazıları olmadan oluşturabilirsiniz.

Kod sözleşmelerini kullanmaya yönelik araçlar ve ayrıntılı yönergeler için bkz. Visual Studio marketi sitesindeki [Kod sözleşmeleri](https://marketplace.visualstudio.com/items?itemName=RiSEResearchinSoftwareEngineering.CodeContractsforNET) .

## <a name="preconditions"></a>Üstbilgisinde

<xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType> yöntemini kullanarak önkoşulları Express yapabilirsiniz. Ön koşullar bir yöntem çağrıldığında durumu belirtir. Bunlar genellikle geçerli parametre değerlerini belirtmek için kullanılır. Ön koşullarda bahsedilen tüm Üyeler en azından yöntemin kendisi olarak erişilebilir olmalıdır; Aksi takdirde, önkoşul bir yöntemin tüm çağıranları tarafından anlaşılmayabilir. Koşulun yan etkileri olmaması gerekir. Başarısız önkoşulların çalışma zamanı davranışı, çalışma zamanı Çözümleyicisi tarafından belirlenir.

Örneğin, aşağıdaki önkoşul parametre `x` null olmayan bir değer olması gerektiğini ifade eder.

```csharp
Contract.Requires(x != null);
```

Kodunuzun bir önkoşulun hata durumunda belirli bir özel durum oluşturması gerekiyorsa, <xref:System.Diagnostics.Contracts.Contract.Requires%2A> genel aşırı yüklemesini aşağıdaki gibi kullanabilirsiniz.

```csharp
Contract.Requires<ArgumentNullException>(x != null, "x");
```

### <a name="legacy-requires-statements"></a>Eski deyimleri gerektiriyor

Çoğu kod, `if`-`then`-`throw` kod biçiminde bazı parametre doğrulamasını içerir. Sözleşme araçları, aşağıdaki durumlarda bu deyimleri ön koşullar olarak tanır:

- Deyimler bir yöntemde diğer deyimlerden önce görüntülenir.

- Bu tür deyimler kümesinin tamamı, <xref:System.Diagnostics.Contracts.Contract.Requires%2A>, <xref:System.Diagnostics.Contracts.Contract.Ensures%2A>, <xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>veya <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A> yöntemine yapılan çağrı gibi açık bir <xref:System.Diagnostics.Contracts.Contract> yöntemi çağrısıyla izlenir.

`if`-`then`-`throw` deyimleri bu formda görüntülendiğinde, Araçlar bunları eski `requires` deyimler olarak tanır. Başka hiçbir sözleşme `if`-`then`-`throw` sıra, kodu <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A?displayProperty=nameWithType> yöntemiyle sonlandırın.

```csharp
if (x == null) throw new ...
Contract.EndContractBlock(); // All previous "if" checks are preconditions
```

Önceki testteki koşulun bir geçişli önkoşul olduğunu unutmayın. (Gerçek önkoşul `x != null`.) Bir geçişli önkoşul yüksek oranda kısıtlıdır: önceki örnekte gösterildiği gibi yazılmalıdır. diğer bir deyişle, `else` yan tümceleri içermemelidir ve `then` yan tümcesinin gövdesi tek bir `throw` deyimi olmalıdır. `if` testi hem özne hem de görünürlük kurallarına tabidir (bkz. [Kullanım yönergeleri](#usage_guidelines)), ancak `throw` ifadesi yalnızca önemli kurallara tabidir. Ancak, oluşturulan özel durumun türü, sözleşmenin gerçekleştiği Yöntem olarak görünür olmalıdır.

## <a name="postconditions"></a>Sonkoşulları

Postconditions, bir yöntemin sonlandırıldığında bir yöntemin durumu için sözleşmelerdir. Sonkoşul, bir yöntemden çıkmadan hemen önce denetlenir. Başarısız Sonkoşulları çalışma zamanı davranışı, çalışma zamanı Çözümleyicisi tarafından belirlenir.

Önkoşullardan farklı olarak, Sonkoşulları daha az görünürlük içeren üyelere başvurabilir. İstemci özel durum kullanan bir Sonkoşul tarafından ifade edilen bilgilerden bazılarını anlayamayabilir veya kullanamaz, ancak bu, istemcinin yöntemi doğru bir şekilde kullanma yeteneğini etkilemez.

### <a name="standard-postconditions"></a>Standart Postconditions

Standart Sonkoşulları <xref:System.Diagnostics.Contracts.Contract.Ensures%2A> yöntemini kullanarak ifade edebilirsiniz. Postconditions, yöntemin normal sonlandırmasından sonra `true` olması gereken bir koşul ifade etmelidir.

```csharp
Contract.Ensures(this.F > 0);
```

### <a name="exceptional-postconditions"></a>Olağanüstü Postconditions

Olağanüstü Sonkoşullar, bir yöntem tarafından belirli bir özel durum oluştuğunda `true` olması gereken Sonkoşullar olur. Aşağıdaki örnekte gösterildiği gibi, bu Sonkoşulları <xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A?displayProperty=nameWithType> yöntemini kullanarak belirtebilirsiniz.

```csharp
Contract.EnsuresOnThrow<T>(this.F > 0);
```

Bağımsız değişkeni, `T` alt türü olan bir özel durum oluştuğunda `true` olması gereken koşuldur.

Olağanüstü bir Sonkoşul içinde kullanılması zor olan bazı özel durum türleri vardır. Örneğin, `T` için <xref:System.Exception> türü kullanıldığında, bir yığın taşması veya diğer imkansız-Control özel durumu olsa bile, oluşturulan özel durum türünden bağımsız olarak koşulu garanti etmek için yöntemi gerekir. Yalnızca bir üye çağrıldığında, örneğin bir <xref:System.TimeZoneInfo> Yöntem çağrısı için <xref:System.InvalidTimeZoneException> oluşturulduğunda, özel durumlar için, olağanüstü Sonkoşulları kullanmanız gerekir.

### <a name="special-postconditions"></a>Özel Postconditions

Aşağıdaki yöntemler yalnızca Postconditions içinde kullanılabilir:

- Yöntemi, `T` yönteminin dönüş türü ile değiştirildiği `Contract.Result<T>()`Expression ' ı kullanarak Sonkoşulları içindeki değer dönüş değerlerini ifade edebilirsiniz. Derleyici türü çıkarsanamıyor, açıkça sağlamanız gerekir. Örneğin, C# derleyici herhangi bir bağımsız değişken kullanmayan yöntemler için türleri çıkarmıyor, bu nedenle aşağıdaki Sonkoşul gerektirir: `void` dönüş türü olan `Contract.Ensures(0 <Contract.Result<int>())` yöntemler, `Contract.Result<T>()` kendi gelen koşullarında başvuramaz.

- Sonkoşul içindeki bir prestate değeri, bir yöntemin veya özelliğin başlangıcında bir ifadenin değerine başvurur. `Contract.OldValue<T>(e)`ifadesi kullanır, burada `T` `e`türüdür. Derleyici türünü çıkarsdığı zaman genel tür bağımsız değişkenini atlayabilirsiniz. (Örneğin, C# derleyici bir bağımsız değişken aldığı için türü her zaman alır.) `e` ve eski bir ifadenin görünebileceği bağlamlarda oluşabilecek çeşitli kısıtlamalar vardır. Eski bir ifade başka bir eski ifade içeremez. En önemlisi, eski bir ifade yöntemin önkoşul durumunda varolan bir değere başvurmalıdır. Diğer bir deyişle, yöntemin önkoşulunu `true`olduğu sürece değerlendirilebilecek bir ifade olmalıdır. Bu kuralın birkaç örneği aşağıda verilmiştir.

  - Değer, yöntemin önkoşul durumunda bulunmalıdır. Bir nesne üzerindeki bir alana başvurmak için, önkoşulların nesnenin her zaman null olmadığından emin olması gerekir.

  - Eski bir ifadede yöntemin dönüş değerine başvuramaz:

      ```csharp
      Contract.OldValue(Contract.Result<int>() + x) // ERROR
      ```

  - Eski bir ifadede `out` parametrelere başvuramaz.

  - Belirleyici aralığı, yöntemin dönüş değerine bağımlıysa, eski bir ifade bir nicelik sayısının bağlı değişkenine bağlı olamaz:

      ```csharp
      Contract.ForAll(0, Contract.Result<int>(), i => Contract.OldValue(xs[i]) > 3); // ERROR
      ```

  - Bir yöntem çağrısında bir Dizin Oluşturucu veya bağımsız değişken olarak kullanılmadığı sürece eski bir ifade bir <xref:System.Diagnostics.Contracts.Contract.ForAll%2A> veya <xref:System.Diagnostics.Contracts.Contract.Exists%2A> çağrısı içindeki anonim temsilcinin parametresine başvuramaz:

      ```csharp
      Contract.ForAll(0, xs.Length, i => Contract.OldValue(xs[i]) > 3); // OK
      Contract.ForAll(0, xs.Length, i => Contract.OldValue(i) > 3); // ERROR
      ```

  - Anonim temsilci <xref:System.Diagnostics.Contracts.Contract.ForAll%2A> veya <xref:System.Diagnostics.Contracts.Contract.Exists%2A> yöntemine bir bağımsız değişken olmadığı müddetçe, eski ifadenin değeri anonim temsilcinin herhangi birine bağımlıysa, eski bir ifade, anonim temsilcinin gövdesinde gerçekleşemez:

      ```csharp
      Method(... (T t) => Contract.OldValue(... t ...) ...); // ERROR
      ```

  - `Out` parametreler, sözleşme metodun gövdesinden önce göründüğünden ve çoğu derleyiciler, Postconditions içindeki `out` parametrelere yönelik başvurulara izin vermediğinden bir sorun sunar. Bu sorunu çözmek için <xref:System.Diagnostics.Contracts.Contract> sınıfı, bir `out` parametresine dayalı bir sonkoşulun izin verdiği <xref:System.Diagnostics.Contracts.Contract.ValueAtReturn%2A> yöntemini sağlar.

      ```csharp
      public void OutParam(out int x)
      {
          Contract.Ensures(Contract.ValueAtReturn(out x) == 3);
          x = 3;
      }
      ```

      <xref:System.Diagnostics.Contracts.Contract.OldValue%2A> yönteminde olduğu gibi, derleyici türünü çıkarsdığı zaman genel tür parametresini atlayabilirsiniz. Sözleşme yeniden yazıcı, yöntem çağrısını `out` parametresi değeriyle değiştirir. <xref:System.Diagnostics.Contracts.Contract.ValueAtReturn%2A> yöntemi yalnızca Postconditions içinde görünebilir. Metodun bağımsız değişkeni bir `out` parametresi veya bir yapı `out` parametresinin alanı olmalıdır. İkincisi, bir yapı oluşturucusunun sonkoşulun içindeki alanlara başvururken da yararlıdır.

      > [!NOTE]
      > Şu anda, kod sözleşmesi analiz araçları `out` parametrelerinin düzgün başlatılıp başlatılmayacağını ve sonkoşulun bahsetmediğini kontrol etmez. Bu nedenle, önceki örnekte, sözleşmenin sonraki satırı, bir tamsayı atamak yerine `x` değerini kullansaydı, derleyici doğru hatayı vermez. Bununla birlikte, CONTRACTS_FULL Önişlemci simgesinin tanımlanmadığı bir derlemede (Bu tür asa yayın derlemesi), derleyici bir hata oluşturur.

## <a name="invariants"></a>Invaryantlar

Nesne ınvaryantları, her nesnenin bir istemciye her görünmesinin her bir sınıf örneği için doğru olması gereken koşullardır. Nesnenin doğru olduğu kabul edildiği koşulları ifade ederler.

Sabit Yöntemler <xref:System.Diagnostics.Contracts.ContractInvariantMethodAttribute> özniteliğiyle işaretlenerek tanımlanır. Sabit metotlar, her biri aşağıdaki örnekte gösterildiği gibi tek bir sabiti belirten <xref:System.Diagnostics.Contracts.Contract.Invariant%2A> yöntemine yapılan çağrılar dizisi dışında hiçbir kod içermemelidir.

```csharp
[ContractInvariantMethod]
protected void ObjectInvariant ()
{
    Contract.Invariant(this.y >= 0);
    Contract.Invariant(this.x > this.y);
    ...
}
```

Invaryantlar CONTRACTS_FULL Önişlemci simgesiyle koşullu olarak tanımlanır. Çalışma zamanı denetimi sırasında, ınvaryantlar her genel yöntemin sonunda denetlenir. Bir sabit, aynı sınıftaki ortak bir yönteme bahsetiyorsa, normalde bu genel yöntemin sonunda gerçekleşen sabit denetim devre dışıdır. Bunun yerine, denetim yalnızca o sınıfa en dıştaki yöntem çağrısının sonunda gerçekleşir. Bu aynı zamanda, başka bir sınıftaki bir yönteme çağrı nedeniyle sınıf yeniden girilirse de olur. Invaryantlar, bir nesne Sonlandırıcı ve bir <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> uygulama için denetlenmez.

<a name="usage_guidelines"></a>

## <a name="usage-guidelines"></a>Kullanım Yönergeleri

### <a name="contract-ordering"></a>Sözleşme sıralaması

Aşağıdaki tabloda, yöntem sözleşmeleri yazarken kullanmanız gereken öğelerin sırası gösterilmektedir.

|`If-then-throw statements`|Geriye dönük olarak uyumlu genel Önkoşullar|
|-|-|
|<xref:System.Diagnostics.Contracts.Contract.Requires%2A>|Tüm genel Önkoşullar.|
|<xref:System.Diagnostics.Contracts.Contract.Ensures%2A>|Tüm genel (normal) Postconditions.|
|<xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>|Tüm genel sıradışı Postconditions.|
|<xref:System.Diagnostics.Contracts.Contract.Ensures%2A>|Tüm özel/iç (normal) Postconditions.|
|<xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>|Tüm özel/iç olağanüstü Postconditions.|
|<xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A>|Başka sözleşmeler olmadan `throw` stili önkoşulları -`if`-`then`kullanıyorsanız, tüm önceki denetimlerin ön koşullar olduğunu göstermek için <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A> için bir çağrı koyun.|

<a name="purity"></a>

### <a name="purity"></a>Takip

Bir sözleşme içinde çağrılan tüm yöntemler saf olmalıdır; diğer bir deyişle, önceden var olan bir durumu güncelleştirmemelidir. Saf yönteme giriş yapıldıktan sonra oluşturulan nesneleri değiştirmeye izin verilir.

Kod sözleşmesi araçları şu anda aşağıdaki kod öğelerinin saf olduğunu varsayar:

- <xref:System.Diagnostics.Contracts.PureAttribute>işaretlenen Yöntemler.

- <xref:System.Diagnostics.Contracts.PureAttribute> işaretli olan türler (öznitelik tüm tür yöntemleri için geçerlidir).

- Özellik Al erişimcileri.

- İşleçler (adları "op" ile başlayan ve bir veya iki parametresi ve void olmayan bir dönüş türü olan statik yöntemler).

- Tam adı "System. Diagnostics. sözleşmeleri. Sözleşmesi", "System. String", "System. ıO. Path" veya "System. Type" ile başlayan tüm yöntemler.

- Temsilci türünün kendisi <xref:System.Diagnostics.Contracts.PureAttribute>ilişkilendirilebildiği tüm çağrılan temsilciler. <xref:System.Predicate%601?displayProperty=nameWithType> ve <xref:System.Comparison%601?displayProperty=nameWithType> temsilci türleri saf olarak değerlendirilir.

<a name="visibility"></a>

### <a name="visibility"></a>Görünürlük

Bir sözleşmede bahsedilen tüm üyelerin en az göründükleri Yöntem olarak görünür olması gerekir. Örneğin, bir özel alan, bir genel yöntemin önkoşulunu içinde belirtilemez; istemciler, yöntemi çağırmadan önce böyle bir sözleşmeyi doğrulayamaz. Ancak, alan <xref:System.Diagnostics.Contracts.ContractPublicPropertyNameAttribute>işaretlenmişse, bu kurallardan muaf tutulur.

## <a name="example"></a>Örnek

Aşağıdaki örnek, kod sözleşmelerinin kullanımını gösterir.

[!code-csharp[ContractExample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/contractexample/cs/program.cs#1)]
[!code-vb[ContractExample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/contractexample/vb/program.vb#1)]
