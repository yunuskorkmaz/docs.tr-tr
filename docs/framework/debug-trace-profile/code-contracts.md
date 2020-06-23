---
title: Kod Sözleşmeleri
description: .NET kodunuzda önkoşulları, Postconditions ve nesne ıntürevlerini belirtmenin bir yolunu sağlayan kod sözleşmelerini keşfet.
ms.date: 09/05/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Code contracts
ms.assetid: 84526045-496f-489d-8517-a258cf76f040
ms.openlocfilehash: 60f794373af75bd3f745c224e0a8c7a84192e4c4
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904149"
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

Anlaşma sınıfındaki yöntemlerin çoğu koşullu olarak derlenir; diğer bir deyişle, derleyici bu yöntemlere yalnızca özel bir sembol tanımladığınızda, CONTRACTS_FULL, yönergesini kullanarak çağrı yayar `#define` . CONTRACTS_FULL, yönergeleri kullanmadan kodunuzda sözleşmeleri yazmanızı sağlar `#ifdef` ; farklı yapılar, bazı sözleşmelerle ve bazıları olmadan oluşturabilirsiniz.

Kod sözleşmelerini kullanmaya yönelik araçlar ve ayrıntılı yönergeler için bkz. Visual Studio marketi sitesindeki [Kod sözleşmeleri](https://marketplace.visualstudio.com/items?itemName=RiSEResearchinSoftwareEngineering.CodeContractsforNET) .

## <a name="preconditions"></a>Üstbilgisinde

Yöntemini kullanarak önkoşulları ifade edebilirsiniz <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType> . Ön koşullar bir yöntem çağrıldığında durumu belirtir. Bunlar genellikle geçerli parametre değerlerini belirtmek için kullanılır. Ön koşullarda bahsedilen tüm Üyeler en azından yöntemin kendisi olarak erişilebilir olmalıdır; Aksi takdirde, önkoşul bir yöntemin tüm çağıranları tarafından anlaşılmayabilir. Koşulun yan etkileri olmaması gerekir. Başarısız önkoşulların çalışma zamanı davranışı, çalışma zamanı Çözümleyicisi tarafından belirlenir.

Örneğin, aşağıdaki önkoşul parametrenin `x` null olmayan bir değer olması gerektiğini ifade eder.

```csharp
Contract.Requires(x != null);
```

Kodunuzun bir önkoşulun hata durumunda belirli bir özel durum oluşturması gerekiyorsa, genel aşırı yüklemesini <xref:System.Diagnostics.Contracts.Contract.Requires%2A> aşağıdaki gibi kullanabilirsiniz.

```csharp
Contract.Requires<ArgumentNullException>(x != null, "x");
```

### <a name="legacy-requires-statements"></a>Eski deyimleri gerektiriyor

Çoğu kod, kod biçiminde bazı parametre doğrulamasını içerir `if` - `then` - `throw` . Sözleşme araçları, aşağıdaki durumlarda bu deyimleri ön koşullar olarak tanır:

- Deyimler bir yöntemde diğer deyimlerden önce görüntülenir.

- Bu tür deyimler kümesinin tamamı,,, <xref:System.Diagnostics.Contracts.Contract> <xref:System.Diagnostics.Contracts.Contract.Requires%2A> <xref:System.Diagnostics.Contracts.Contract.Ensures%2A> <xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A> veya yöntemine yapılan çağrı gibi açık bir yöntem çağrısıyla izlenir <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A> .

`if` - `then` - `throw` Bu formda deyimler görüntülendiğinde, Araçlar bunları eski deyimler olarak tanır `requires` . Sırayı takip eden başka sözleşmeler yoksa `if` - `then` - `throw` , kodu <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A?displayProperty=nameWithType> yöntemiyle sonlandırın.

```csharp
if (x == null) throw new ...
Contract.EndContractBlock(); // All previous "if" checks are preconditions
```

Önceki testteki koşulun bir geçişli önkoşul olduğunu unutmayın. (Gerçek önkoşul olacaktır `x != null` .) Bir geçişli önkoşul yüksek oranda kısıtlıdır: önceki örnekte gösterildiği gibi yazılmalıdır. Yani, hiçbir yan tümce içermemelidir `else` ve `then` yan tümcesinin gövdesi tek bir `throw` ifade olmalıdır. `if`Test, hem önemli hem de görünürlük kurallarına tabidir (bkz. [Kullanım yönergeleri](#usage_guidelines)), ancak `throw` ifade yalnızca önemli kurallara tabidir. Ancak, oluşturulan özel durumun türü, sözleşmenin gerçekleştiği Yöntem olarak görünür olmalıdır.

## <a name="postconditions"></a>Sonkoşulları

Postconditions, bir yöntemin sonlandırıldığında bir yöntemin durumu için sözleşmelerdir. Sonkoşul, bir yöntemden çıkmadan hemen önce denetlenir. Başarısız Sonkoşulları çalışma zamanı davranışı, çalışma zamanı Çözümleyicisi tarafından belirlenir.

Önkoşullardan farklı olarak, Sonkoşulları daha az görünürlük içeren üyelere başvurabilir. İstemci özel durum kullanan bir Sonkoşul tarafından ifade edilen bilgilerden bazılarını anlayamayabilir veya kullanamaz, ancak bu, istemcinin yöntemi doğru bir şekilde kullanma yeteneğini etkilemez.

### <a name="standard-postconditions"></a>Standart Postconditions

Yöntemini kullanarak standart Sonkoşulları getirebilirsiniz <xref:System.Diagnostics.Contracts.Contract.Ensures%2A> . Postconditions `true` , yöntemin normal sonlandırmasından sonra olması gereken bir koşul ifade etmelidir.

```csharp
Contract.Ensures(this.F > 0);
```

### <a name="exceptional-postconditions"></a>Olağanüstü Postconditions

Olağanüstü Sonkoşullar, `true` bir yöntem tarafından belirli bir özel durum oluşturulduğunda olması gereken Sonkoşullar olur. <xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A?displayProperty=nameWithType>Aşağıdaki örnekte gösterildiği gibi, yöntemini kullanarak bu Sonkoşulları belirtebilirsiniz.

```csharp
Contract.EnsuresOnThrow<T>(this.F > 0);
```

Bağımsız değişkeni, `true` öğesinin bir alt türü olan her bir özel durum oluştuğunda olması gereken durumdur `T` .

Olağanüstü bir Sonkoşul içinde kullanılması zor olan bazı özel durum türleri vardır. Örneğin, için türünün kullanılması, <xref:System.Exception> `T` bir yığın taşması veya diğer imkansız-denetim özel durumu olsa bile, oluşturulan özel durum türünden bağımsız olarak koşulu güvence altına almak için yöntemini gerektirir. Yalnızca bir üye çağrıldığında, örneğin, bir <xref:System.InvalidTimeZoneException> Yöntem çağrısı için oluşturulduğunda, özel durumlar için, yalnızca bir üye çağrıldığında oluşturulan özel durumlar için olağanüstü Sonkoşulları kullanmanız gerekir <xref:System.TimeZoneInfo> .

### <a name="special-postconditions"></a>Özel Postconditions

Aşağıdaki yöntemler yalnızca Postconditions içinde kullanılabilir:

- Yöntemini kullanarak Sonkoşulları içindeki değer dönüş değerlerini ifade eder; `Contract.Result<T>()` burada, `T` yönteminin dönüş türü ile değiştirilmiştir. Derleyici türü çıkarsanamıyor, açıkça sağlamanız gerekir. Örneğin, C# derleyicisi herhangi bir bağımsız değişken kullanmayan yöntemler için türleri çıkarmıyor, bu nedenle aşağıdaki Sonkoşul gerektirir: `Contract.Ensures(0 <Contract.Result<int>())` dönüş türü olan Yöntemler, `void` `Contract.Result<T>()` kendi iade koşullarına başvuramaz.

- Sonkoşul içindeki bir prestate değeri, bir yöntemin veya özelliğin başlangıcında bir ifadenin değerine başvurur. Bu, türü olan ifadesini kullanır `Contract.OldValue<T>(e)` `T` `e` . Derleyici türünü çıkarsdığı zaman genel tür bağımsız değişkenini atlayabilirsiniz. (Örneğin, C# derleyicisi her zaman bir bağımsız değişken aldığı için türü kullanır.) ' De neler olabileceği `e` ve eski bir ifadenin görünebileceği bağlamlarda çeşitli kısıtlamalar vardır. Eski bir ifade başka bir eski ifade içeremez. En önemlisi, eski bir ifade yöntemin önkoşul durumunda varolan bir değere başvurmalıdır. Diğer bir deyişle, yöntemin önkoşulunu olduğu sürece değerlendirilebilecek bir ifade olmalıdır `true` . Bu kuralın birkaç örneği aşağıda verilmiştir.

  - Değer, yöntemin önkoşul durumunda bulunmalıdır. Bir nesne üzerindeki bir alana başvurmak için, önkoşulların nesnenin her zaman null olmadığından emin olması gerekir.

  - Eski bir ifadede yöntemin dönüş değerine başvuramaz:

      ```csharp
      Contract.OldValue(Contract.Result<int>() + x) // ERROR
      ```

  - `out`Eski bir ifadede parametrelere başvurulamaz.

  - Belirleyici aralığı, yöntemin dönüş değerine bağımlıysa, eski bir ifade bir nicelik sayısının bağlı değişkenine bağlı olamaz:

      ```csharp
      Contract.ForAll(0, Contract.Result<int>(), i => Contract.OldValue(xs[i]) > 3); // ERROR
      ```

  - Bir <xref:System.Diagnostics.Contracts.Contract.ForAll%2A> <xref:System.Diagnostics.Contracts.Contract.Exists%2A> Yöntem çağrısında bir Dizin Oluşturucu veya bağımsız değişken olarak kullanılmadığı sürece, eski bir ifade bir veya çağrısındaki anonim temsilcinin parametresine başvuramaz:

      ```csharp
      Contract.ForAll(0, xs.Length, i => Contract.OldValue(xs[i]) > 3); // OK
      Contract.ForAll(0, xs.Length, i => Contract.OldValue(i) > 3); // ERROR
      ```

  - Eski ifadenin değeri, veya yöntemine ait bir bağımsız değişken olmadığı müddetçe, anonim temsilcinin gövdesinde anonim temsilcinin herhangi birine bağımlıysa, eski bir ifade bulunamaz <xref:System.Diagnostics.Contracts.Contract.ForAll%2A> <xref:System.Diagnostics.Contracts.Contract.Exists%2A> :

      ```csharp
      Method(... (T t) => Contract.OldValue(... t ...) ...); // ERROR
      ```

  - `Out`sözleşmeler metodun gövdesinden önce göründüğünden ve çoğu derleyiciler, Postconditions içindeki parametrelere başvuruya izin vermediğinden, bir sorun oluşur `out` . Bu sorunu çözmek için, <xref:System.Diagnostics.Contracts.Contract> sınıfı bir <xref:System.Diagnostics.Contracts.Contract.ValueAtReturn%2A> parametreye dayalı bir Sonkoşul sağlayan yöntemini sağlar `out` .

      ```csharp
      public void OutParam(out int x)
      {
          Contract.Ensures(Contract.ValueAtReturn(out x) == 3);
          x = 3;
      }
      ```

      Yönteminde olduğu gibi <xref:System.Diagnostics.Contracts.Contract.OldValue%2A> , derleyici türünü çıkarsdığı zaman genel tür parametresini atlayabilirsiniz. Sözleşme yeniden yazıcı, yöntem çağrısını parametrenin değeriyle değiştirir `out` . <xref:System.Diagnostics.Contracts.Contract.ValueAtReturn%2A>Yöntemi yalnızca Postconditions içinde görünebilir. Metodun bağımsız değişkeni bir `out` parametre veya bir yapı parametresinin alanı olmalıdır `out` . İkincisi, bir yapı oluşturucusunun sonkoşulun içindeki alanlara başvururken da yararlıdır.

      > [!NOTE]
      > Şu anda, kod sözleşmesi analiz araçları `out` parametrelerin doğru başlatılıp başlatılmayacağını denetleyip sonkoşulun ne olduğunu göz ardı etmez. Bu nedenle, önceki örnekte, sözleşmenin sonraki satırı, `x` bir tamsayı atamak yerine değerini kullansaydı, bir derleyici doğru hatayı veremez. Bununla birlikte, CONTRACTS_FULL Önişlemci simgesinin tanımlanmadığı bir derlemede (Bu tür asa yayın derlemesi), derleyici bir hata oluşturur.

## <a name="invariants"></a>Invaryantlar

Nesne ınvaryantları, her nesnenin bir istemciye her görünmesinin her bir sınıf örneği için doğru olması gereken koşullardır. Nesnenin doğru olduğu kabul edildiği koşulları ifade ederler.

Sabit Yöntemler, özniteliğiyle işaretlenerek tanımlanır <xref:System.Diagnostics.Contracts.ContractInvariantMethodAttribute> . <xref:System.Diagnostics.Contracts.Contract.Invariant%2A>Aşağıdaki örnekte gösterildiği gibi, sabit metotlar, her biri tek bir sabiti belirten yöntemine yapılan çağrı dizisi haricinde hiçbir kod içermemelidir.

```csharp
[ContractInvariantMethod]
protected void ObjectInvariant ()
{
    Contract.Invariant(this.y >= 0);
    Contract.Invariant(this.x > this.y);
    ...
}
```

Invaryantlar CONTRACTS_FULL Önişlemci simgesiyle koşullu olarak tanımlanır. Çalışma zamanı denetimi sırasında, ınvaryantlar her genel yöntemin sonunda denetlenir. Bir sabit, aynı sınıftaki ortak bir yönteme bahsetiyorsa, normalde bu genel yöntemin sonunda gerçekleşen sabit denetim devre dışıdır. Bunun yerine, denetim yalnızca o sınıfa en dıştaki yöntem çağrısının sonunda gerçekleşir. Bu aynı zamanda, başka bir sınıftaki bir yönteme çağrı nedeniyle sınıf yeniden girilirse de olur. Invaryantlar, bir nesne Sonlandırıcı ve bir uygulama için denetlenmez <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> .

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
|<xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A>|`if` - `then` - `throw` Başka sözleşmeler olmadan stil önkoşulları kullanıyorsanız, <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A> tüm önceki denetimlerin ön koşullar olduğunu göstermek için öğesine bir çağrısı koyun.|

<a name="purity"></a>

### <a name="purity"></a>Takip

Bir sözleşme içinde çağrılan tüm yöntemler saf olmalıdır; diğer bir deyişle, önceden var olan bir durumu güncelleştirmemelidir. Saf yönteme giriş yapıldıktan sonra oluşturulan nesneleri değiştirmeye izin verilir.

Kod sözleşmesi araçları şu anda aşağıdaki kod öğelerinin saf olduğunu varsayar:

- İle işaretlenen Yöntemler <xref:System.Diagnostics.Contracts.PureAttribute> .

- İle işaretlenen türler <xref:System.Diagnostics.Contracts.PureAttribute> (özniteliği tüm tür yöntemlerine uygulanır).

- Özellik Al erişimcileri.

- İşleçler (adları "op" ile başlayan ve bir veya iki parametresi ve void olmayan bir dönüş türü olan statik yöntemler).

- Tam adı "System. Diagnostics. sözleşmeleri. Sözleşmesi", "System. String", "System. ıO. Path" veya "System. Type" ile başlayan tüm yöntemler.

- Temsilci türünün kendisi ile ilişkilendirilebildiği tüm çağrılan temsilciler <xref:System.Diagnostics.Contracts.PureAttribute> . Temsilci türleri <xref:System.Predicate%601?displayProperty=nameWithType> ve <xref:System.Comparison%601?displayProperty=nameWithType> saf olarak değerlendirilir.

<a name="visibility"></a>

### <a name="visibility"></a>Görünürlük

Bir sözleşmede bahsedilen tüm üyelerin en az göründükleri Yöntem olarak görünür olması gerekir. Örneğin, bir özel alan, bir genel yöntemin önkoşulunu içinde belirtilemez; istemciler, yöntemi çağırmadan önce böyle bir sözleşmeyi doğrulayamaz. Ancak, alanı ile işaretlenmişse, <xref:System.Diagnostics.Contracts.ContractPublicPropertyNameAttribute> Bu kurallardan muaf tutulur.

## <a name="example"></a>Örnek

Aşağıdaki örnek, kod sözleşmelerinin kullanımını gösterir.

[!code-csharp[ContractExample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/contractexample/cs/program.cs#1)]
[!code-vb[ContractExample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/contractexample/vb/program.vb#1)]
