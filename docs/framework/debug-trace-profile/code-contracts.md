---
title: "Kod Sözleşmeleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Code contracts
ms.assetid: 84526045-496f-489d-8517-a258cf76f040
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4a7f6dd2f97f7d57cdaa59d1420a34409804f9dd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="code-contracts"></a>Kod Sözleşmeleri
Kod sözleşmeleri önkoşulları, Sonkoşullar ve nesne invariants kodunuzda belirtmek için bir yol sağlar. Önkoşulları yöntemi veya özelliği girerken karşılanması gereken gereksinimleri verilmiştir. Sonkoşullar beklentilerini yöntemi veya özelliği kod çıkar aynı anda açıklanmaktadır. Nesne invariants iyi bir durumda bir sınıfı için beklenen durumu açıklanmaktadır.  
  
 Kod sözleşmeleri kodunuzu, derleme zamanı çözümleme için statik bir Çözümleyicisi ve bir çalışma zamanı Çözümleyicisi işaretlemek için sınıflar içerir. Kod sözleşmeleri sınıflarını bulunabilir <xref:System.Diagnostics.Contracts> ad alanı.  
  
 Kod sözleşmeleri avantajları şunlardır:  
  
-   Sınama geliştirilmiş: kod sözleşmeleri statik sözleşme doğrulama, çalışma zamanı denetleniyor ve belgeleri oluşturma sağlar.  
  
-   Otomatik test araçları: kod sözleşmeleri önkoşulları karşılamadığı anlamsız test bağımsız değişkenleri filtreleyerek daha anlamlı birim testleri oluşturmak için kullanabilirsiniz.  
  
-   Statik doğrulama: statik denetleyicisi programı çalıştırmadan herhangi bir sözleşme ihlal olup olmadığına karar verebilirsiniz. Null gibi örtük sözleşmeleri denetler dereferences ve dizi sınırları ve açık sözleşmeleri.  
  
-   Başvuru belgelerini: Sözleşme bilgilerle varolan XML belge dosyalarını belgelerine Oluşturucu artırmaktadır. Ayrıca ile kullanılan stil sayfaları vardır [Sandcastle](https://github.com/EWSoftware/SHFB) böylece oluşturulan belge sayfalarının sözleşme bölümler.  
  
 Tüm .NET Framework diller hemen sözleşmeleri yararlanabilir; bir özel ayrıştırıcı veya derleyici yazmak zorunda değildir. Visual Studio eklentisi gerçekleştirilecek kod sözleşme çözümleme düzeyini belirtmenize olanak sağlar. Çözümleyiciler sözleşmeleri doğru biçimlendirilmiş olduğunu doğrulayın (tür denetimini gerçekleştireceğini ve ad çözümlemesi) ve Microsoft Ara dili (MSIL) biçiminde sözleşmelerin derlenmiş bir formu üretebilir. Sözleşmeleri Visual Studio geliştirme, IntelliSense aracı tarafından sağlanan standart yararlanmanızı sağlar.  
  
 Sözleşme sınıfı çoğu yöntemleri koşullu derlenen; diğer bir deyişle, yalnızca CONTRACTS_FULL, özel bir simge kullanarak tanımlarken bu yöntemlere çağrılar derleyici yayar `#define` yönergesi. CONTRACTS_FULL kullanmadan kodunuzda sözleşmeleri yazmanıza olanak tanır `#ifdef` yönergeleri; farklı derlemeleri, bazı Sözleşmelerle ve bazı olmadan üretebilir.  
  
 Araçlar ve kod sözleşmeleri kullanmaya yönelik ayrıntılı yönergeler için bkz: [kod sözleşmeleri](http://go.microsoft.com/fwlink/?LinkId=152461) MSDN DevLabs Web sitesinde.  
  
## <a name="preconditions"></a>Önkoşulları  
 Kullanarak önkoşulları açıklayabilir <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType> yöntemi. Bir yöntem çağrıldığında önkoşulları durumunu belirtin. Bunlar genellikle geçerli parametre değerleri belirtmek için kullanılır. Önkoşulları içinde açıklanan tüm üyeleri en az yöntemi olarak olarak erişilebilir olmalıdır; Aksi takdirde önkoşulu tüm bir yöntemini arayanlar tarafından anlaşılmayan. Koşul hiçbir yan etkisi olması gerekir. Başarısız önkoşulları çalışma zamanı davranışını çalışma zamanı Çözümleyicisi tarafından belirlenir.  
  
 Örneğin, bu parametre aşağıdaki önkoşulu ifade `x` null olmayan olması gerekir.  
  
 `Contract.Requires( x != null );`  
  
 Kodunuzu belirli bir özel durum, bir önkoşul hatası durumunda throw gerekir, genel aşırı yüklemesini kullanabilirsiniz <xref:System.Diagnostics.Contracts.Contract.Requires%2A> gibi.  
  
 `Contract.Requires<ArgumentNullException>( x != null, "x" );`  
  
### <a name="legacy-requires-statements"></a>Eski deyimleri gerektirir  
 Bazı parametre doğrulaması biçiminde çoğu kod içeren `if` - `then` - `throw` kodu. Sözleşme araçları bu deyimleri önkoşulları aşağıdaki durumlarda olarak algılar:  
  
-   Diğer herhangi bir yöntem deyimlerinde önce deyimleri görünür.  
  
-   Bu tür ifadeleri kümesinin tamamını açık bir tarafından izlenir <xref:System.Diagnostics.Contracts.Contract> yapılan bir çağrı gibi yöntem çağrısı <xref:System.Diagnostics.Contracts.Contract.Requires%2A>, <xref:System.Diagnostics.Contracts.Contract.Ensures%2A>, <xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>, veya <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A> yöntemi.  
  
 Zaman `if` - `then` - `throw` deyimleri araçları tanıması bunları eski bu formda görünen `requires` deyimleri. Diğer bir sözleşmeleri izlerseniz `if` - `then` - `throw` serisi, kodla end <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A?displayProperty=nameWithType> yöntemi.  
  
```  
if ( x == null ) throw new ...  
Contract.EndContractBlock(); // All previous "if" checks are preconditions  
```  
  
 Önceki test koşulunda çevrilerek önkoşulu olduğuna dikkat edin. (Gerçek önkoşulu olacaktır `x != null`.) Çevrilerek önkoşulu ileri derecede kısıtlı: önceki örnekte; gösterildiği gibi yazılmalıdır diğer bir deyişle, Hayır içermelidir `else` yan tümceleri ve gövdesini `then` yan tümcesi, tek bir olmalıdır `throw` deyimi. `if` Test olmak üzere ve görünürlük kuralları tabi olur (bkz [kullanım yönergeleri](#usage_guidelines)), ancak `throw` ifadesidir yalnızca olmak üzere kuralları konu. Ancak, özel durum türünü sözleşme oluştuğu yöntemi olarak olarak görünür olması gerekir.  
  
## <a name="postconditions"></a>Sonkoşullar  
 Sonkoşullar durumuna yönelik bir yöntem sözleşmeleri alındığında sonlandırır. Sonkoşul bir yöntem çıkmadan önce denetlenir. Başarısız Sonkoşullar çalışma zamanı davranışını çalışma zamanı Çözümleyicisi tarafından belirlenir.  
  
 Önkoşulları, daha az görünürlük üyeleriyle Sonkoşullar başvurabilir. Bir istemci anlamak veya yapmak mümkün olmayabilir bazı özel durumu kullanarak Sonkoşul ifade edilen bilgileri kullanır, ancak bu istemcinin yöntemi doğru bir şekilde kullanma yeteneğini etkilemez.  
  
### <a name="standard-postconditions"></a>Standart Sonkoşullar  
 Kullanarak standart Sonkoşullar açıklayabilir <xref:System.Diagnostics.Contracts.Contract.Ensures%2A> yöntemi. Sonkoşullar express olmalıdır bir koşul `true` yönteminin normal sonlandırmada.  
  
 `Contract.Ensures( this.F > 0 );`  
  
### <a name="exceptional-postconditions"></a>Olağanüstü Sonkoşullar  
 Olağanüstü Sonkoşullar olan olmalıdır Sonkoşullar `true` belirli bir özel durum bir yöntemle oluşur zaman. Kullanarak bu Sonkoşullar belirtebilirsiniz <xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A?displayProperty=nameWithType> aşağıdaki örnekte gösterildiği gibi yöntemi.  
  
 `Contract.EnsuresOnThrow<T>( this.F > 0 );`  
  
 Bağımsız değişken olmalıdır durumdur `true` alt türü olan bir özel durum her `T` atılır.  
  
 Bir olağanüstü Sonkoşul içinde kullanmak zordur bazı özel durum türü vardır. Örneğin, türü kullanılarak <xref:System.Exception> için `T` bir yığın taşması veya diğer denetim imkansız özel durum olsa bile, koşul oluşturulur, özel durum türü ne olursa olsun güvence altına almak için bir yöntem gerektirir. Olağanüstü Sonkoşullar üyesi, örneğin, ne zaman çağrıldığında oluşturulan yalnızca belirli durumlar için kullanması gereken bir <xref:System.InvalidTimeZoneException> için oluşturulan bir <xref:System.TimeZoneInfo> yöntem çağrısı.  
  
### <a name="special-postconditions"></a>Özel Sonkoşullar  
 Aşağıdaki yöntemlerden yalnızca Sonkoşullar içinde kullanılabilir:  
  
-   Dönüş değerleri Sonkoşullar yöntemi ifade kullanarak başvurabilirsiniz `Contract.Result<T>()`, burada `T` yönteminin dönüş türü tarafından değiştirilir. Derleyici türü Infer başlatılamadığında açıkça sağlamanız gerekir. Örneğin, C# Derleyici türleri aşağıdaki Sonkoşul gerekir, böylece tüm bağımsız değişkenler almayan yöntemleri için Infer alamıyor: `Contract.Ensures(0 <Contract.Result<int>())` dönüş türüne sahip yöntemleri `void` başvuramıyor `Contract.Result<T>()` kendi Sonkoşullar içinde.  
  
-   Sonkoşul prestate değerinde bir ifadenin başlangıcında bir yöntemi veya özelliği değerini gösterir. Deyim kullanan `Contract.OldValue<T>(e)`, burada `T` türü `e`. Derleyici türünü Infer mümkün olduğunda genel tür bağımsız değişkeni atlayabilirsiniz. (Bir bağımsız değişken aldığından Örneğin, C# Derleyici her zaman türü oluşturur.) Ne de oluşabilir bazı kısıtlamalar vardır `e` ve eski deyim görünebilir bağlamı. Eski deyim başka bir eski ifade içeremez. En önemlisi, eski deyim yöntemin önkoşulu durumunda var olan bir değer başvurmalıdır. Diğer bir deyişle, bu yöntemin önkoşulu olduğu sürece sonucu verebilen bir ifade olmalıdır `true`. Bu kural için birkaç örneği aşağıda verilmiştir.  
  
    -   Değer yöntemin önkoşulu durumda olması gerekir. Bir nesne üzerinde bir alana başvuru için önkoşulları söz konusu nesne her zaman null olmayan olduğunu güvence altına almalıdır.  
  
    -   Eski bir ifadede yöntemin dönüş değerine başvuruda bulunamaz:  
  
        ```  
        Contract.OldValue(Contract.Result<int>() + x) // ERROR  
        ```  
  
    -   İçin başvuramaz `out` eski deyimde parametreleri.  
  
    -   Niceleyici aralığını yöntemin dönüş değeri temel alıyorsa eski deyim bir niceleyici ilişkili değişkenine bağlı olamaz:  
  
        ```  
        Contract. ForAll (0,Contract. Result<int>(),  
        i => Contract.OldValue(xs[i]) > 3); // ERROR  
        ```  
  
    -   Eski deyim anonim temsilci parametresinin başvuramıyor bir <xref:System.Diagnostics.Contracts.Contract.ForAll%2A> veya <xref:System.Diagnostics.Contracts.Contract.Exists%2A> bir dizin oluşturucu veya yöntem çağrısı için bağımsız değişken olarak kullanılmadıkça çağırın:  
  
        ```  
        Contract. ForAll (0, xs .Length, i => Contract.OldValue(xs[i]) > 3); // OK  
        Contract. ForAll (0, xs .Length, i => Contract.OldValue(i) > 3); // ERROR  
        ```  
  
    -   Eski ifadesinin değerini anonim temsilci parametrelerinin hiçbirinde bağımlıysa anonim temsilci bağımsız değişken olmadıkça eski deyim anonim bir temsilci gövdesinde gerçekleşemez <xref:System.Diagnostics.Contracts.Contract.ForAll%2A> veya <xref:System.Diagnostics.Contracts.Contract.Exists%2A> yöntemi:  
  
        ```  
        Method( ... (T t) => Contract.OldValue(... t ...) ... ); // ERROR  
        ```  
  
    -   `Out`parametreleri mevcut bir sorun sözleşmeleri yönteminin gövdesi önce görünür ve çoğu derleyicileri başvurular izin verme çünkü `out` Sonkoşullar parametreleri. Bu sorunu çözmek için <xref:System.Diagnostics.Contracts.Contract> SAX <xref:System.Diagnostics.Contracts.Contract.ValueAtReturn%2A> göre Sonkoşul sağlayan yöntemi bir `out` parametresi.  
  
        ```  
        public void OutParam(out int x) f  
        Contract.Ensures(Contract.ValueAtReturn(out x) == 3);  
        x = 3;  
        ```  
  
         İle <xref:System.Diagnostics.Contracts.Contract.OldValue%2A> yöntemi kullanmayabilir genel tür parametresi derleyici türünü Infer mümkün olduğunda. Sözleşme yeniden yazan yöntem çağrısının değeri ile değiştirir. `out` parametresi. <xref:System.Diagnostics.Contracts.Contract.ValueAtReturn%2A> Yöntemi yalnızca Sonkoşullar içinde görünebilir. Yöntemin bağımsız değişkeni olmalıdır bir `out` parametresi ya da alan bir yapısının `out` parametresi. İkincisi de yapısı Oluşturucusu Sonkoşul alanlara söz konusu olduğunda yararlıdır.  
  
        > [!NOTE]
        >  Şu anda, kod sözleşme çözümleme araçları denetleme olup olmadığını `out` parametreleri düzgün şekilde başlatılmadı ve bunların Bahsetme Sonkoşul içinde göz ardı. Sözleşme satırdan değeri kullanılırsa bu nedenle, önceki örnekte, `x` tamsayı kendisine atamak yerine, bir derleyici doğru hatası sorunu değil. Ancak, üzerinde CONTRACTS_FULL önişlemci sembolü olduğu bir yapı (böyle asa yayın derlemesi) tanımlı değil, derleyici hata verecek.  
  
## <a name="invariants"></a>İnvariants  
 Nesne invariants bu nesne için bir istemci görünür olduğunda, bir sınıfın her örneği için doğru olması gereken koşullardır. Bunlar, altında nesne doğru olarak değerlendirilir koşullar express.  
  
 Değişmez yöntemleri ile işaretlenen tarafından tanımlanan <xref:System.Diagnostics.Contracts.ContractInvariantMethodAttribute> özniteliği. Değişmez yöntemleri yapılan çağrıların bir sıra dışında hiçbir kod içermelidir <xref:System.Diagnostics.Contracts.Contract.Invariant%2A> yöntemi, her biri belirtir tek tek bir değişmez değer aşağıdaki örnekte gösterildiği gibi.  
  
```  
[ContractInvariantMethod]  
protected void ObjectInvariant ()   
{  
Contract.Invariant(this.y >= 0);  
Contract.Invariant(this.x > this.y);  
...  
}  
```  
  
 İnvariants koşullu CONTRACTS_FULL önişlemci sembolü tarafından tanımlanır. Çalışma zamanı denetimi sırasında invariants her genel yöntem sonunda denetlenir. Genel yöntem aynı sınıfta bir değişmez değer değinmektedir, normal olarak bu genel yöntem sonunda olacağını değişmez denetimi devre dışı bırakılır. Bunun yerine, yalnızca o sınıfın en dıştaki yöntemi çağrısı sonunda onay oluşur. Bu durum, aynı zamanda sınıfın başka bir sınıf bir yöntem çağrısı nedeniyle yeniden girilirse gerçekleşir. Nesne sonlandırıcılar veya uygulayan herhangi bir yöntem, invariants işaretli değil <xref:System.IDisposable.Dispose%2A> yöntemi.  
  
<a name="usage_guidelines"></a>   
## <a name="usage-guidelines"></a>Kullanım yönergeleri  
  
### <a name="contract-ordering"></a>Sözleşme sıralama  
 Aşağıdaki tabloda yöntemi sözleşmeleri yazdığınızda kullanması gereken öğelerin sırasını gösterir.  
  
|`If-then-throw statements`|Geriye dönük olarak uyumlu ortak önkoşulları|  
|-|-|  
|<xref:System.Diagnostics.Contracts.Contract.Requires%2A>|Tüm ortak önkoşulları.|  
|<xref:System.Diagnostics.Contracts.Contract.Ensures%2A>|Tüm ortak (normal) Sonkoşullar.|  
|<xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>|Tüm genel olağanüstü Sonkoşullar.|  
|<xref:System.Diagnostics.Contracts.Contract.Ensures%2A>|Tüm özel/iç (normal) Sonkoşullar.|  
|<xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>|Tüm özel/iç olağanüstü Sonkoşullar.|  
|<xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A>|Kullanıyorsanız `if` - `then` - `throw` stil önkoşulları diğer sözleşmeleri olmadan, bir çağrı için <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A> göstermek için denetimleri önkoşulları varsa tüm önceki.|  
  
<a name="purity"></a>   
### <a name="purity"></a>Olmak üzere  
 İçinde bir sözleşme adında tüm yöntemleri saf olmalıdır; diğer bir deyişle, bunlar önceden var olan herhangi bir durum güncelleştirmelisiniz değil. Saf yönteminde, saf yöntemi giriş sonra oluşturulan nesneleri değiştirmek için izin verilir.  
  
 Aşağıdaki kod öğeleri saf kod sözleşme araçları şu anda varsayın:  
  
-   İle işaretlenen yöntemleri <xref:System.Diagnostics.Contracts.PureAttribute>.  
  
-   İle işaretlenen türleri <xref:System.Diagnostics.Contracts.PureAttribute> (öznitelik tipinin tüm yöntemleri için geçerlidir).  
  
-   Özellik get erişimcisi.  
  
-   İşleçler (bir veya iki parametreleri ve void olmayan dönüş türüne sahip statik yöntemler adları "Aç" ve, ile başlayan).  
  
-   Tam adı "System.Diagnostics.Contracts.Contract", "System.String", "System.IO.Path" veya "System.Type" ile başlayan herhangi bir yöntem.  
  
-   Temsilci türü ile öznitelikli koşuluyla herhangi bir temsilci çağrılır <xref:System.Diagnostics.Contracts.PureAttribute>. Temsilci türleri <xref:System.Predicate%601?displayProperty=nameWithType> ve <xref:System.Comparison%601?displayProperty=nameWithType> saf olarak kabul edilir.  
  
<a name="visibility"></a>   
### <a name="visibility"></a>Görünürlük  
 Bir sözleşmede belirtilen tüm üyeleri en az göründükleri yöntemi olarak olarak görünür olması gerekir. Örneğin, özel bir alan bir public yöntemi için bir önkoşulu bölümünde belirtildiği olamaz; Bunlar yöntemi çağırmadan önce istemcileri böyle bir sözleşme doğrulanamıyor. Ancak, alanın işaretlenmişse <xref:System.Diagnostics.Contracts.ContractPublicPropertyNameAttribute>, bu kurallardan tutulur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kod sözleşmeleri kullanımını göstermektedir.  
  
 [!code-csharp[ContractExample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/contractexample/cs/program.cs#1)]
 [!code-vb[ContractExample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/contractexample/vb/program.vb#1)]
