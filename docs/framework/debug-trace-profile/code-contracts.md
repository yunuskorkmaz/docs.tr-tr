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
ms.openlocfilehash: f7f7a779cc10b32d66a184107359b502cf094979
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44277672"
---
# <a name="code-contracts"></a>Kod Sözleşmeleri
Kod sözleşmeleri, önkoşulları ve koşul sonralarına nesne okuduğunuzda kodunuzda belirtmek için bir yol sağlar. Önkoşulları, bir metot veya özellik girerken karşılanması gereken gereksinimleri verilmiştir. Koşul sonralarına beklentileri metot veya özellik kod çıkar zaman açıklanmaktadır. Beklenen durum iyi durumda olan bir sınıf için nesne okuduğunuzda açıklanmaktadır.  
  
 Kod sözleşmeleri kodunuzu, derleme zamanı analiz için statik bir Çözümleyicisi ve çalışma zamanı Çözümleyicisi işaretlemek için sınıflar içerir. Kod sözleşmeleri sınıflarını bulunabilir <xref:System.Diagnostics.Contracts> ad alanı.  
  
 Kod sözleşmeleri avantajları şunları içerir:  
  
-   Testi: kod sözleşmeleri statik sözleşme doğrulama, çalışma zamanı denetimi ve belgeleri oluşturma sağlar.  
  
-   Otomatik test araçları: kod sözleşmeleri önkoşulları karşılayan değil anlamsız test değişkenlerinin filtreleyerek daha anlamlı birim testleri oluşturmak için kullanabilirsiniz.  
  
-   Statik doğrulama: statik denetleyicisi programı çalıştırmadan herhangi bir sözleşme ihlali olup olmadığına karar verebilirsiniz. Null gibi örtük sözleşmeleri denetler başvurusunu kaldırır ve dizi sınırları ve açık anlaşmaları.  
  
-   Başvuru belgeleri: Sözleşme bilgileriniz ile varolan bir XML belgesi dosyalarının belgeleri Oluşturucu artırmaktadır. Kullanılabilir stil sayfaları da vardır [Sandcastle](https://github.com/EWSoftware/SHFB) oluşturulan belge sayfalarına sözleşme bölümleri edinecek olmanızdır.  
  
 Tüm .NET Framework dillerinde sözleşmeleri hemen yararlanabilirsiniz; Özel ayrıştırıcı veya derleyici yazmanız gerekmez. Bir Visual Studio eklentisi gerçekleştirilecek kod sözleşme analizi düzeyini belirtmenize olanak tanır. Çözümleyicileri anlaşmalar doğru oluşturulduğunu onaylayın (tür denetimini ve ad çözümlemesi) ve Microsoft Ara dili (MSIL) biçimde sözleşmelerinin derlenmiş form üretebilir. Visual Studio'da sözleşmeleri yazma IntelliSense araç tarafından sağlanan standart avantajlarından yararlanmanıza imkan sağlar.  
  
 Çoğu sözleşme sınıfı yöntemleri koşullu olarak derlenir; diğer bir deyişle, yalnızca CONTRACTS_FULL, özel bir simge kullanarak tanımlarken bu yöntemlere yapılan çağrılar derleyici yayar `#define` yönergesi. CONTRACTS_FULL sözleşmeleri olmadan kodunuzu yazmanıza olanak tanır `#ifdef` yönergeleri; farklı yapılar, bazı sözleşmeler ve bazı olmadan üretebilir.  
  
 Araçlar ve kod sözleşmeleri kullanmaya yönelik ayrıntılı yönergeler için bkz. [kod sözleşmeleri](https://go.microsoft.com/fwlink/?LinkId=152461) MSDN DevLabs Web sitesinde.  
  
## <a name="preconditions"></a>Önkoşulları  
 Kullanarak önkoşulları ifade edebilirsiniz <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType> yöntemi. Bir yöntem çağrıldığında önkoşulları durumunu belirtin. Bunlar, genellikle geçerli parametre değerleri belirtmek için kullanılır. Önkoşullarda belirtildiği tüm üyeleri en az yöntemi olarak olarak erişilebilir olması gerekir; Aksi takdirde, önkoşuluna tüm bir yöntemi çağıranlar tarafından anlaşılabilir değil. Koşul herhangi bir yan etkisi olması gerekir. Başarısız önkoşulları çalışma zamanı davranışını çalışma zamanı çözümleyici tarafından belirlenir.  
  
 Örneğin, bu parametre aşağıdaki önkoşul ifade `x` null olmayan olmalıdır.  
  
 `Contract.Requires( x != null );`  
  
 Kodunuz, bir önkoşul hatası belirli bir özel durum throw gerekir, genel aşırı yüklemesini kullanabilirsiniz <xref:System.Diagnostics.Contracts.Contract.Requires%2A> gibi.  
  
 `Contract.Requires<ArgumentNullException>( x != null, "x" );`  
  
### <a name="legacy-requires-statements"></a>Eski #requires  
 Bazı parametre doğrulaması biçiminde çoğu kod içeren `if` - `then` - `throw` kod. Sözleşme araçları bu deyimler önkoşulları aşağıdaki durumlarda olarak tanır:  
  
-   Önce bir yöntem içinde herhangi bir deyim deyimlerinizin.  
  
-   Bu tür ifadeleri kümesinin tamamını açık bir tarafından izlenir <xref:System.Diagnostics.Contracts.Contract> gibi bir çağrı, yöntem çağrısının <xref:System.Diagnostics.Contracts.Contract.Requires%2A>, <xref:System.Diagnostics.Contracts.Contract.Ensures%2A>, <xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>, veya <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A> yöntemi.  
  
 Zaman `if` - `then` - `throw` deyimleri araçları tanıması bunları bilinen bu formda görünen `requires` deyimleri. Diğer bir sözleşme izlerseniz `if` - `then` - `throw` sıra, kod ile bitiş <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A?displayProperty=nameWithType> yöntemi.  
  
```  
if ( x == null ) throw new ...  
Contract.EndContractBlock(); // All previous "if" checks are preconditions  
```  
  
 Önceki test koşulu çevrilerek önkoşul olduğunu unutmayın. (Gerçek önkoşuluna olacaktır `x != null`.) Çevrilerek önkoşulu ileri derecede kısıtlı:; önceki örnekte de gösterildiği gibi yazılmalıdır diğer bir deyişle, Hayır içermelidir `else` yan tümceleri ve gövdesini `then` yan tümcesi olmalıdır tek bir `throw` deyimi. `if` Sınamadır tabi olmak üzere hem görünürlük kuralları (bkz [kullanım yönergeleri](#usage_guidelines)), ancak `throw` ifadesidir yalnızca saflığa kurallarına tabidir. Ancak, oluşturulan özel durum türü olarak sözleşme oluştuğu yöntemi olarak görünür olması gerekir.  
  
## <a name="postconditions"></a>Koşul sonralarına  
 Koşul sonralarına sonlandırmasına sözleşmeler için bir yöntem durumunu olur. Bir yöntem çıkmadan önce Sonkoşul denetlenir. Başarısız bir koşul sonralarına çalışma zamanı davranışını çalışma zamanı çözümleyici tarafından belirlenir.  
  
 Önkoşulları, daha az görünürlük üyeleriyle koşul sonralarına başvurabilir. Bir istemci anlamak veya mümkün olmayabilir, bazı özel durumu kullanarak Sonkoşul tarafından gösterilen bilgiler kullanır, ancak bu istemcinin yöntemi doğru şekilde kullanma yeteneğini etkilemez.  
  
### <a name="standard-postconditions"></a>Standart koşul Sonralarına  
 Kullanarak standart koşul sonralarına ifade edebilirsiniz <xref:System.Diagnostics.Contracts.Contract.Ensures%2A> yöntemi. Koşul sonralarına express olması gereken bir koşul `true` normal sonlandırmada yöntemi.  
  
 `Contract.Ensures( this.F > 0 );`  
  
### <a name="exceptional-postconditions"></a>Olağanüstü bir koşul Sonralarına  
 Olağanüstü bir koşul sonralarına olan olmalıdır koşul sonralarına `true` belirli bir özel durumun yöntemi tarafından harekete geçirildiğinde. Bu koşul sonralarına kullanarak belirtebilirsiniz <xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A?displayProperty=nameWithType> yöntemi, aşağıdaki örnekte gösterildiği gibi.  
  
 `Contract.EnsuresOnThrow<T>( this.F > 0 );`  
  
 Bağımsız değişken olmalıdır durumdur `true` bir alt türünde bir özel durum olduğunda `T` oluşturulur.  
  
 Olağanüstü bir Sonkoşul içinde kullanılacak zor olan bazı özel durum türü vardır. Örneğin, türü kullanılarak <xref:System.Exception> için `T` bir yığın taşması veya diğer denetim imkansız özel durumu olsa bile oluşturulan, özel durum türü ne olursa olsun koşul güvence altına almak için bir yöntem gerektirir. Olağanüstü bir koşul sonralarına üyesi, örneğin, ne zaman çağrıldığında oluşturulabilecek özel durum için kullanması gereken bir <xref:System.InvalidTimeZoneException> için oluşturulan bir <xref:System.TimeZoneInfo> yöntem çağrısı.  
  
### <a name="special-postconditions"></a>Özel koşul Sonralarına  
 Aşağıdaki yöntemlerden yalnızca koşul sonralarına içinde kullanılabilir:  
  
-   İfade kullanarak koşul sonralarına yöntem dönüş değerlerine başvurabilir `Contract.Result<T>()`burada `T` yöntemin dönüş türü tarafından değiştirilir. Derleyicinin türü çıkarımı işlenemediğinde açıkça sağlamanız gerekir. Örneğin, C# derleyici aşağıdaki Sonkoşul gerektirir böylece herhangi bir bağımsız değişken almayan yöntemleri için türlerini çıkarması oluşturulamıyor: `Contract.Ensures(0 <Contract.Result<int>())` dönüş türüne sahip yöntemleri `void` başvurulamaz `Contract.Result<T>()` kendi koşul sonralarına içinde.  
  
-   Sonkoşul prestate değeri bir ifade başlatma sırasında bir yöntem veya özellik değerini ifade eder. İfade kullanır `Contract.OldValue<T>(e)`burada `T` türü `e`. Derleyici, türü çıkarımı mümkün olduğunda genel tür bağımsız değişkeni atlayabilirsiniz. (Bağımsız değişken aldığından Örneğin, C# Derleyici her zaman türü çıkarır.) Ne ortaya çıkabilir bazı kısıtlamalar vardır `e` ve eski deyim görünebilir bağlamı. Eski bir ifade başka bir eski ifadesi içeremez. En önemlisi, eski bir ifade yöntemin önkoşulu durumunda var olan bir değer başvurmalıdır. Diğer bir deyişle, yöntemin önkoşulu olduğu sürece değerlendirilebilen bir ifade olmalıdır `true`. Bu kural için birkaç örneği aşağıda verilmiştir.  
  
    -   Değer yöntemin önkoşulu durumda mevcut olması gerekir. Bir alan bir nesne üzerinde başvurmak için önkoşulları söz konusu nesne her zaman null olmayan olduğunu garanti gerekir.  
  
    -   Eski bir ifade yöntemin dönüş değeri başvuruda bulunamaz:  
  
        ```  
        Contract.OldValue(Contract.Result<int>() + x) // ERROR  
        ```  
  
    -   Başvuruda bulunamaz `out` eski bir ifadede parametreleri.  
  
    -   Nicelik aralığı yöntemin dönüş değerini temel bağlıysa, eski bir ifade bağlı bir miktar belirleyiciyi değişkenin üzerine bağımlı olamaz:  
  
        ```  
        Contract. ForAll (0,Contract. Result<int>(),  
        i => Contract.OldValue(xs[i]) > 3); // ERROR  
        ```  
  
    -   Eski bir ifade anonim temsilci parametresine başvuramaz bir <xref:System.Diagnostics.Contracts.Contract.ForAll%2A> veya <xref:System.Diagnostics.Contracts.Contract.Exists%2A> bir dizin oluşturucu veya yöntem çağrısı için bağımsız değişkeni olarak kullanılmadığı sürece çağırın:  
  
        ```  
        Contract. ForAll (0, xs .Length, i => Contract.OldValue(xs[i]) > 3); // OK  
        Contract. ForAll (0, xs .Length, i => Contract.OldValue(i) > 3); // ERROR  
        ```  
  
    -   Eski ifadenin değerini herhangi bir anonim metot temsilcisinin parametre bağlıysa anonim temsilci bağımsız değişken olmadığı sürece eski bir ifade anonim bir temsilci gövdesinde gerçekleşemez <xref:System.Diagnostics.Contracts.Contract.ForAll%2A> veya <xref:System.Diagnostics.Contracts.Contract.Exists%2A> yöntemi:  
  
        ```  
        Method( ... (T t) => Contract.OldValue(... t ...) ... ); // ERROR  
        ```  
  
    -   `Out` parametreleri mevcut bir sorun sözleşmeleri Yöntemin gövdesi önce görünür ve derleyicilerin çoğu başvuruları izin vermez çünkü `out` koşul sonralarına parametreleri. Bu sorunu çözmek için <xref:System.Diagnostics.Contracts.Contract> sağlar sınıfını <xref:System.Diagnostics.Contracts.Contract.ValueAtReturn%2A> göre Sonkoşul sağlayan yöntemi bir `out` parametresi.  
  
        ```  
        public void OutParam(out int x) f  
        Contract.Ensures(Contract.ValueAtReturn(out x) == 3);  
        x = 3;  
        ```  
  
         Olduğu gibi <xref:System.Diagnostics.Contracts.Contract.OldValue%2A> yöntemi çıkarabilirsiniz genel tür parametresi derleyici türünü çıkarsamak mümkün olduğunda. Sözleşme rewriter yöntem çağrısında değeri ile değiştirir. `out` parametresi. <xref:System.Diagnostics.Contracts.Contract.ValueAtReturn%2A> Yöntemi yalnızca koşul sonralarına görünebilir. Yöntem bağımsız değişkeni olmalıdır bir `out` parametresi veya bir yapının bir alan `out` parametresi. İkincisi de yapısı oluşturucunun Sonkoşul alanları söz konusu olduğunda yararlıdır.  
  
        > [!NOTE]
        >  Şu anda, kod sözleşme çözümleme araçları işaretlemeyin olmadığını `out` parametreleri düzgün başlatılmadı ve bunların Bahsetme Sonkoşul içinde göz ardı. Sözleşme satırdan değerini kullanmışsınız bu nedenle, önceki örnekte, `x` tamsayı kendisine atamak yerine, derleyici doğru hatası sorunu değil. Ancak, CONTRACTS_FULL önişlemci sembolü olduğu bir derleme (Bu tür asa yayın derleme) tanımlı değil, derleyici bir hata verir.  
  
## <a name="invariants"></a>Okuduğunuzda  
 Nesne okuduğunuzda o nesnenin bir istemci tarafından görünür olduğunda, bir sınıfın her örneği için true olması gereken koşullardır. Bunlar, nesnenin altında doğru olarak kabul edilir koşullar express.  
  
 Sabit yöntemleri ile işaretlenen tarafından tanımlanan <xref:System.Diagnostics.Contracts.ContractInvariantMethodAttribute> özniteliği. Sabit yöntem çağrıları bir dizi dışında hiçbir kod içermelidir <xref:System.Diagnostics.Contracts.Contract.Invariant%2A> yöntemi, her biri belirten tek bir değişmez değer aşağıdaki örnekte gösterildiği gibi.  
  
```  
[ContractInvariantMethod]  
protected void ObjectInvariant ()   
{  
Contract.Invariant(this.y >= 0);  
Contract.Invariant(this.x > this.y);  
...  
}  
```  
  
 Okuduğunuzda koşullu CONTRACTS_FULL önişlemci sembolü tarafından tanımlanır. Çalışma zamanı denetimi sırasında her bir genel yöntem sonunda okuduğunuzda denetlenir. Değişmez değer aynı sınıftaki bir genel yöntem bahsetmeleri normalde, genel yönteminin sonunda olacağını sabit denetimi devre dışı bırakılır. Bunun yerine, yalnızca o sınıfın en dıştaki yöntem çağrısına sonunda onay gerçekleşir. Bu durum, aynı zamanda sınıfın başka bir sınıftaki bir yönteme bir çağrı nedeniyle yeniden girilirse gerçekleşir. Okuduğunuzda bir nesnenin Sonlandırıcısı için onaylanmamış ve <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> uygulaması.  
  
<a name="usage_guidelines"></a>   
## <a name="usage-guidelines"></a>Kullanım yönergeleri  
  
### <a name="contract-ordering"></a>Sözleşme sıralama  
 Aşağıdaki tabloda yöntemi sözleşmeleri yazdığınızda kullanması gereken öğelerin sırasını gösterir.  
  
|`If-then-throw statements`|Geriye dönük olarak uyumlu genel Önkoşullar|  
|-|-|  
|<xref:System.Diagnostics.Contracts.Contract.Requires%2A>|Tüm genel önkoşulları.|  
|<xref:System.Diagnostics.Contracts.Contract.Ensures%2A>|Tüm genel (normal) koşul sonralarına.|  
|<xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>|Tüm genel olağanüstü koşul sonralarına.|  
|<xref:System.Diagnostics.Contracts.Contract.Ensures%2A>|Tüm özel/iç (normal) koşul sonralarına.|  
|<xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>|Tüm özel/iç olağanüstü koşul sonralarına.|  
|<xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A>|Kullanıyorsanız `if` - `then` - `throw` stil önkoşulları diğer tüm sözleşmeleri olmadan, bir çağrı yapmak <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A> göstermek için önceki tüm denetimleri önkoşulları varsa.|  
  
<a name="purity"></a>   
### <a name="purity"></a>Saflığa  
 Bir sözleşme içinde çağrılan tüm yöntemlere saf olmalıdır; diğer bir deyişle, bunlar önceden var olan herhangi bir durum güncelleştirmeyi gerekir. Saf yönteminin saf yönteminin girişine sonra oluşturulan nesneleri değiştirme izin verilmez.  
  
 Kod sözleşme araçları, şu anda aşağıdaki kod öğelerinden saf olduğunu varsayar:  
  
-   İle işaretlenmiş yöntemler <xref:System.Diagnostics.Contracts.PureAttribute>.  
  
-   İle işaretlenmiş türler <xref:System.Diagnostics.Contracts.PureAttribute> (öznitelik türün tüm yöntemleri için geçerlidir).  
  
-   Özellik get erişimcileri.  
  
-   İşleçler (bir veya iki parametre ve void olmayan dönüş türüne sahip adları "op" ve, ile başlayan statik yöntemleri).  
  
-   Tam adı "System.Diagnostics.Contracts.Contract", "System.String", "System.IO.Path" veya "System.Type" ile başlayan herhangi bir yöntem.  
  
-   Temsilci türü ile öznitelendirilen şartıyla tüm temsilci çağrılır <xref:System.Diagnostics.Contracts.PureAttribute>. Temsilci türleriyle <xref:System.Predicate%601?displayProperty=nameWithType> ve <xref:System.Comparison%601?displayProperty=nameWithType> saf olarak kabul edilir.  
  
<a name="visibility"></a>   
### <a name="visibility"></a>Görünürlük  
 Tüm üyeleri bir sözleşmede belirtilen en az göründükleri yöntemi olarak olarak görünür olmalıdır. Örneğin, özel bir alan genel bir yöntem için bir önkoşul olarak belirtilen olamaz; Bunlar yöntemi çağırmadan önce istemcileri böyle bir sözleşme doğrulanamıyor. Ancak, alan ile işaretlenmişse <xref:System.Diagnostics.Contracts.ContractPublicPropertyNameAttribute>, bu kurallardan muaf.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, kod sözleşmeleri kullanımını gösterir.  
  
 [!code-csharp[ContractExample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/contractexample/cs/program.cs#1)]
 [!code-vb[ContractExample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/contractexample/vb/program.vb#1)]
