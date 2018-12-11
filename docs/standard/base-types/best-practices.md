---
title: .NET içinde normal ifadeler için en iyi uygulamalar
description: . NET'te verimli ve etkili normal ifadeler oluşturmayı öğrenin.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- .NET Framework regular expressions, best practices
- regular expressions, best practices
ms.assetid: 618e5afb-3a97-440d-831a-70e4c526a51c
author: rpetrusha
ms.author: ronpet
ms.custom: serodec18
ms.openlocfilehash: 02847a813566c4675f7df2c88fa2e4e1f6138ecb
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152818"
---
# <a name="best-practices-for-regular-expressions-in-net"></a>.NET içinde normal ifadeler için en iyi uygulamalar
<a name="top"></a> .NET içinde normal ifade altyapısı yerine desen karşılaştırma ve metin eşleşen metni işleyen güçlü, tam özellikli bir araçtır. Çoğu durumda desen eşleme işlemini hızlı ve verimli şekilde yapar. Ancak bazı durumlarda normal ifade motoru çok yavaş görünebilir. Aşırı durumlarda saatler ve hatta günler boyunca görece küçük bir girişi işlerken yanıt vermeyi durdurmuş gibi bile görünebilir.  
  
 Bu konu, normal ifadelerinin en iyi performansa ulaşabilmesi için geliştiricilerin benimseyebileceği en iyi yöntemlerden bazılarını özetlemektedir. Aşağıdaki bölümleri içerir:  
  
-   [Giriş kaynağını düşünün](#InputSource)  
  
-   [Nesne örneklemesini uygun şekilde yönetme](#ObjectInstantiation)  
  
-   [Geri izlemenin alma](#Backtracking)  
  
-   [Zaman aşımı değerlerini kullanma](#Timeouts)  
  
-   [Yalnızca gerekli olduğunda yakala](#Capture)  
  
-   [İlgili Konular](#RelatedTopics)  
  
<a name="InputSource"></a>   
## <a name="consider-the-input-source"></a>Giriş Kaynağını düşünün  
 Genelde normal ifadeler iki tür giriş kabul edebilir: sınırlandırılmış ya da sınırlandırılmamış. Kısıtlı giriş, bilinen ya da güvenilir bir kaynaktan geldiği bilinen ve ön tanımlı bir biçim izleyen metindir. Sınırlandırılmamış girdi, bir web kullanıcısı gibi güvenilir olmayan bir kaynaktan gelen ve önceden tanımlı veya beklenen bir biçime uymayabilecek bir metindir.  
  
 Normal ifade desenleri genelde geçerli girişi eşlemek için yazılır. Diğer bir deyişle, geliştiriciler eşleştirmek istedikleri metni inceler ve bu metinle eşleşen normal bir ifade deseni yazarlar. Geliştiriciler daha sonra bu desenin düzeltme ya da daha fazla ayrıntı gerektirip gerektirmediğini, birden çok geçerli giriş öğesini test ederek belirler. Desen gereçli olduğu kabul edilen tüm girdilerle eşleştiğinde, üretime hazır kabul edilir ve çıkacak uygulamaya dahil edilebilir. Bu, normal bir ifade desenini, kısıtlanmış girdiyle eşleşme için uygun hale getirir. Ancak sınırlandırılmamış girişin eşlenmesi uygun hale getirmez.  
  
 Sınırlandırılmamış girdide eşlemek yapmak için, normal bir ifade üç tür metni verimli olarak işleyebilmelidir:  
  
-   Normal ifade deseniyle eşleşen metin.  
  
-   Normal ifade deseniyle eşleşmeyen metin.  
  
-   Normal ifade deseniyle neredeyse eşleşen metin.  
  
 Son metin türü, sınırlandırılmış girdi işlemek üzere yazılmış bir normal ifade için özellikle sorunludur. Bu normal ifade ayrıca kapsamlı dayanıyorsa [geri izlemenin](../../../docs/standard/base-types/backtracking-in-regular-expressions.md), normal ifade motoru normal dışı miktarda zamanı ayırabilirsiniz (bazı durumlarda saatler ya da günler) görünüşte zararsız bir metni işlemeye.  
  
> [!WARNING]
>  Aşağıdaki örnek, aşırı miktarda geri dönüş kullanma eğiliminde olan ve geçerli e-posta adreslerini reddetmesi olası bir normal ifadeyi kullanmaktadır. Bir e-posta doğrulama yordamında kullanmamalısınız. E-posta adreslerini onaylayan bir normal ifade isterseniz bkz [nasıl yapılır: Dizelerin geçerli e-posta biçiminde olduğunu doğrulama](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md).  
  
 Örneğin bir e-posta adresinin takma adını onaylamak için çok yaygın kullanılan ama son derece sorunlu normal ifade düşünün. Normal ifade `^[0-9A-Z]([-.\w]*[0-9A-Z])*$` ne ve ardından sıfır veya daha fazla alfasayısal karakter, nokta veya kısa çizgi, alfasayısal bir karakterle oluşan bir geçerli e-posta adresi olarak kabul edilir için yazılmıştır. Normal ifade, alfasayısal bir karakterle bitmelidir. Ancak aşağıdaki örnekte gösterildiği gibi, bu normal ifade geçerli girişi kolayca yönetmesine rağmen performansı neredeyse geçerli girişi işlerken çok yetersizdir.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/design2.cs#1)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/design2.vb#1)]  
  
 Örneğin çıktısında gösterildiği üzere normal ifade motoru geçerli e-posta takma adlarını, uzunluğundan bağımsız olarak yaklaşık aynı zaman aralığında işler. Diğer taraftan, yakın geçerli e-posta adresi beşten fazla karakter içeriyorsa, işlem zamanı dizedeki ek her karakter için yaklaşık iki kat olacaktır. Bunun anlamı, neredeyse geçerli 28-karakter dizesi işlemek için bir saatten fazla götürecek ve neredeyse geçerli 33-karakter dizesi işlemek için neredeyse bir gün sürecektir.  
  
 Bu düzenli ifade yalnızca eşlenecek girişin biçimi düşünülerek geliştirildiğinden desen ile eşleşmeyen girişi hesaba katamaz. Bu da normal ifade deseniyle neredeyse eşleşen sınırlandırılmamış girdinin performansı önemli ölçüde düşürmesine neden olabilir.  
  
 Bu sorunu çözmek için, şunları yapabilirsiniz:  
  
-   Bir desen geliştirirken, özellikle de normal ifadeniz sınırlandırılmamış girdiyi işlemek üzere tasarlandıysa, geri dönüşün normal ifade altyapısının performansını nasıl etkileyeceğini düşünmelisiniz. Daha fazla bilgi için [olması, ücretsiz olarak geri](#Backtracking) bölümü.  
  
-   Normal ifadenizi geçerli girdilerin yanı sıra gereçsiz ve neredeyse geçerli girdiler de kullanarak baştan aşağı test edin. Belirli bir normal ifadeye girdi üretmek için kullanabileceğiniz [Rex](https://www.microsoft.com/en-us/research/project/rex-regular-expression-exploration/), Microsoft Research'den bir normal ifade İnceleme aracı.  
  
 [Başa dön](#top)  
  
<a name="ObjectInstantiation"></a>   
## <a name="handle-object-instantiation-appropriately"></a>Nesne Örneklemesini Uygun Şekilde Yönetme  
 Yaklaşımının temelindeki. NET normal ifade nesnesi modeli <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> sınıfı, normal ifade motorunu temsil eder. Genellikle, normal ifade performansını etkileyen tekil en büyük faktör şeklidir <xref:System.Text.RegularExpressions.Regex> altyapısı kullanılır. Normal bir ifadeyi tanımlama, normal ifade motorunu bir normal ifade deseni ile sıkı şekilde eşlemeyi içerir. İşlem eşlenmesiyle, mi, örnekleme içerdiğini bir <xref:System.Text.RegularExpressions.Regex> nesnesine, yapıcısına bir normal ifade deseni geçerek veya statik bir yöntemi, normal ifade desenini çözümlenecek dizeyle birlikte geçirerek çağırmak, tarafından zorunluluktur bir pahalı bir.  
  
> [!NOTE]
>  Yorumlanmış ve derlenmiş normal ifadelerin kullanımının performans etkilerinin daha ayrıntılı bir açıklaması için bkz: [normal ifade performansını en iyi duruma getirme, Kısım II: Ücret, geri alma](https://blogs.msdn.microsoft.com/bclteam/2010/08/03/optimizing-regular-expression-performance-part-ii-taking-charge-of-backtracking-ron-petrusha/) bkz.BCL Ekibi blogunda.  
  
 Normal ifade altyapısını belirli bir normal ifade deseniyle birleştirebilir, sonra altyapıyı birkaç şekilde metin eşlemesi yapmak üzere kullanabilirsiniz:  
  
-   Gibi bir statik desen eşleme yöntemini çağırabilirsiniz <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%29?displayProperty=nameWithType>. Bu, bir normal ifade nesnesine öndeğer atanmasını gerektirmez.  
  
-   Örneği oluşturabilir bir <xref:System.Text.RegularExpressions.Regex> nesne ve yorumlanan normal ifade örneğinin desen eşleme yöntemini çağırabilirsiniz. Bu, normal ifade altyapısını bir normal ifade desenine bağlamak için varsayılan yöntemdir. Sonuç olduğunda bir <xref:System.Text.RegularExpressions.Regex> nesnesi örneği olmadan bir `options` içeren bağımsız değişken <xref:System.Text.RegularExpressions.RegexOptions.Compiled> bayrağı.  
  
-   Örneği oluşturabilir bir <xref:System.Text.RegularExpressions.Regex> nesne ve derlenmiş normal ifade örneğinin desen eşleme yöntemini çağırabilirsiniz. Normal ifade nesneleri derlenmiş desenleri temsil eder ne zaman bir <xref:System.Text.RegularExpressions.Regex> nesnesi örneği ile bir `options` içeren bağımsız değişken <xref:System.Text.RegularExpressions.RegexOptions.Compiled> bayrağı.  
  
-   Oluşturabileceğiniz özel amaçlı <xref:System.Text.RegularExpressions.Regex> bir belirli bir normal ifade deseniyle katı olarak birleştirilmiş sıkı bir şekilde nesne, derleyebilir ve tek başına bir derleme için kaydedin. Çağrı yaparak bunu <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> yöntemi.  
  
 Normal ifade eşleme yöntemlerini çağırma biçiminizin uygulamanız üzerinde önemli bir etkisi olabilir. Aşağıdaki bölümler, uygulamanızın performansını iyileştirmek için statik yöntem çağrılarının, yorumlanan normal ifadelerin ve derlenmiş normal ifadelerin ne zaman kullanılacağını tartışmaktadır.  
  
> [!IMPORTANT]
>  Yöntem çağrılarında aynı normal ifade tekrar tekrar kullanılıyorsa veya uygulama normal ifade nesnelerini yoğun olarak kullanıyorsa, yöntem çağrısının biçimi (statik, yorumlanan, derlenmiş) performansı etkiler.  
  
### <a name="static-regular-expressions"></a>Statik Normal İfadeler  
 Statik normal ifade yöntemleri, bir normal ifade nesnesine aynı normal ifadeyi tekrar tekrar ön değer olarak atamaya alternatif olarak önerilir. Normal ifade nesneleri tarafından kullanılan normal ifade desenlerinden farklı olarak örnek yöntemi çağrılarında kullanılan desenlerin işlem kodları veya derlenmiş Microsoft ara dili (MSIL), normal ifade motoru tarafından dahili olarak önbelleğe alınır.  
  
 Örneğin bir olay işleyicisi, kullanıcı girişini onaylamak için sık sık başka bir yöntem çağırır. Bunu aşağıdaki kodda yansıtılan bir <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Click> yöntemini çağırmak için kullanılan olay `IsValidCurrency`, kullanıcının bir para simgesi ve en az bir adet ondalık rakam ardından girdiği olup olmadığını denetler.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/static1.cs#2)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/static1.vb#2)]  
  
 Bir çok verimsiz bir uygulaması `IsValidCurrency` yöntemi, aşağıdaki örnekte gösterilmiştir. Her yöntem çağrısının yeniden başlattığına dikkat edin bir <xref:System.Text.RegularExpressions.Regex> aynı desene sahip bir nesne. Bu ise normal ifade deseninin yöntem her çağrıldığında tekrar derlenmesi gerektiği anlamına gelir.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/static1.cs#3)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/static1.vb#3)]  
  
 Bu Verimsiz kodu statik bir çağrıyla değiştirmelisiniz <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> yöntemi. Bu örneği oluşturmak için ihtiyacını ortadan kaldıran bir <xref:System.Text.RegularExpressions.Regex> nesne her zaman bir desen eşleme yöntemini çağırmak istediğinizde ve normal ifade altyapısının normal ifadenin derlenmiş bir sürümünü önbelleğinden almasını sağlar.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/static2.cs#4)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/static2.vb#4)]  
  
 Varsayılan olarak, en son kullanılan 15 statik normal ifade deseni önbelleğe alınır. Ayarlayarak, çok sayıda önbelleğe alınmış statik normal ifade gerektiren uygulamalarda, önbellek boyutu ayarlanabilir <xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=nameWithType> özelliği.  
  
 Normal ifade `\p{Sc}+\s*\d+` kullanılan bu örnek giriş dizesinde bir para birimi sembolü ve en az bir adet ondalık rakam olduğunu doğrulamaktır. Desen aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\p{Sc}+`|Unicode Sembolü, Para Birimi kategorisinde bir ya da daha fazla karakter eşleyin.|  
|`\s*`|Sıfır veya daha fazla boşluk karakteriyle eşleş.|  
|`\d+`|Bir veya daha fazla ondalık basamağı eşleştirin.|  
  
<a name="Interpreted"></a>   
### <a name="interpreted-vs-compiled-regular-expressions"></a>Yorumlanan vs. Derlenmiş normal ifadeler  
 Normal ifade motoruna belirtimi bağlı olmayan normal ifade desenleri <xref:System.Text.RegularExpressions.RegexOptions.Compiled> seçeneği yorumlanır. Bir normal ifade nesnesi örneği oluşturulduğunda, normal ifade altyapısı normal ifadeyi bir dizi işlem koduna dönüştürür. Bir örnek yöntemi çağrıldığında, işlem kodları MSIL'ye dönüştürülür ve JIT derleyicisi tarafından yürütülür. Benzer şekilde, statik bir normal ifade yöntemi çağrıldığı ve normal ifade önbellekte bulunamadığı zaman, normal ifade altyapısı normal ifadeyi bir dizi işlem koduna dönüştürür ve bunları önbellekte depolar. Daha sonra işlem kodlarını MSIL'ye dönüştürür, bu sayede JIT derleyicisi bunları yürütebilir. Yorumlanmış normal ifadeler, daha yavaş yürütme sürelerine karşın açılış süresini azaltır. Bundan dolayı bunlar, normal ifade az sayıda yöntem çağrısında kullanıldığında ya da normal ifade yöntemine yapılan kesin çağrı sayısı bilinmiyor ancak küçük olması bekleniyorsa en iyi şekilde kullanılır. Yöntem çağrıları arttıkça performans kazancı daha az başlangıç saatinden sayısı daha yavaş yürütme hızını outstripped gibi.  
  
 Normal ifade motoruna belirtimi normal ifade desenleri <xref:System.Text.RegularExpressions.RegexOptions.Compiled> seçeneği derlenir. Bu, bir normal ifade nesnesi örneği oluşturulduğunda veya statik bir normal ifade yöntemi çağrıldığında ve normal ifade önbellekte bulunamadığında, normal ifade altyapısının normal ifadeyi ara bir işlem kodu kümesine, sonra da bunu MSIL'ye dönüştürdüğü anlamına gelir. Bir yöntem çağrıldığında, JIT derleyici MSIL'yi yürütür. Yorumlanmış normal ifadelerin aksine, derlenmiş normal ifadeler açılış süresini artırır ancak ayrı desen eşleme yöntemlerini daha hızlı yürütür. Sonuç olarak normal ifade derlemekten kaynaklanan sonuçlardan yararlanan performans çağrılan normal ifade yöntemlerinin sayısı oranında artar.  
  
 Özetlemek gerekirse, normal ifade yöntemlerini belirli bir normal ifadeyle nispeten ender olarak çağırıyorsanız, yorumlanan normal ifadeler kullanmanızı öneririz. Normal ifade yöntemlerinizi oldukça sık olarak belirli bir normal ifadeyle çağırıyorsanız, derlenmiş normal ifadeler kullanmalısınız. Yorumlanan normal ifadelerin yürütülme hızlarındaki yavaşlığın bunların başlama süresinin kısa olmasından elde edilen avantajı ortadan kaldırmaya başladığı eşiği veya derlenmiş normal ifadelerin başlama süresinin uzunluğunun bunların yürütülme hızından elde edilen avantajı ortadan kaldırmaya başladığı eşiği belirlemek güçtür. Normal ifadenin karmaşıklığı ve bunun işlediği özel veri gibi çeşitli faktörlere bağlıdır. Yorumlanan mi, derlenmiş normal ifadeler, belirli uygulama senaryonuzda en iyi performansı sunan belirlemek için kullanabileceğiniz <xref:System.Diagnostics.Stopwatch> bunların yürütme sürelerini karşılaştırmak üzere sınıfı.  
  
 Aşağıdaki örnek metni Theodore Dreiser'ın tüm cümleleri okunurken ilk on okurken derlenmiş ve yorumlanan normal ifadelerin ve performansını karşılaştırır *The Financier*. Örneğin çıktısında gösterildiği üzere normal ifade eşleme yöntemlerine yalnızca on çağrı yapıldığında, yorumlanan bir normal ifade derlenmiş bir normal ifadeden daha iyi performans sergiler. Ancak derlenmiş bir normal ifade, daha fazla sayıda çağrı yapıldığında (bu örnekte 13.000'den fazla) daha iyi performans gösterir.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/compare1.cs#5)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/compare1.vb#5)]  
  
 Örnekte kullanılan normal ifade deseni `\b(\w+((\r?\n)|,?\s))*\w+[.?:;!]`, aşağıdaki tabloda gösterildiği gibi tanımlanmaktadır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`\w+`|Bir veya daha fazla sözcük karakteri eşleştir.|  
|<code>(\r?\n)&#124;,?\s)</code>|Arkasından bir yeni satır karakteri gelen sıfır ya da bir satır başı veya arkasından bir boşluk karakteri gelen sıfır ya da bir virgül eşleyin.|  
|<code>(\w+((\r?\n)&#124;,?\s))*</code>|Arkasından sıfır ya da bir satır başı ve bir yeni satır karakteri veya sıfır ya da bir virgül ve sonra boşluk karakteri gelen bir ya da daha fazla sözcük karakterinin sıfır ya da daha fazla oluşumunu eşleyin.|  
|`\w+`|Bir veya daha fazla sözcük karakteri eşleştir.|  
|`[.?:;!]`|Bir nokta, soru işareti, iki nokta üst üste, noktalı virgül ya da ünlem işareti eşleyin.|  
  
### <a name="regular-expressions-compiled-to-an-assembly"></a>Normal ifadeler: Bir derlemeye derlenen  
 .NET, derlenmiş normal ifadeler içeren bir bütünleştirilmiş kod oluşturmanızı sağlar. Bu, normal ifade derlemesinin uğradığı performans düşüşünü çalışma zamanından tasarım zamanına taşır. Ancak, bazı ek işleri de içerir: Normal ifadeleri önceden tanımlamanız ve bunları bir derlemeye derlemek gerekir. Derleyici daha sonra, derlemenin normal ifadelerini kullanan kaynak kodunu derlerken bu derlemeye başvurabilir. Derleme içinde derlenen her normal ifade, türetilen bir sınıf tarafından temsil edilen <xref:System.Text.RegularExpressions.Regex>.  
  
 Normal ifadeleri bir derleme olarak derlemek için çağrı <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%28System.Text.RegularExpressions.RegexCompilationInfo%5B%5D%2CSystem.Reflection.AssemblyName%29?displayProperty=nameWithType> yöntemi ve bir dizi geçirin <xref:System.Text.RegularExpressions.RegexCompilationInfo> derlenecek normal ifadeleri temsil eden nesneleri ve bir <xref:System.Reflection.AssemblyName> olmasını derleme hakkında bilgi içeren nesne oluşturuldu.  
  
 Aşağıdaki durumlarda normal ifadeleri bütünleşik bir dosyaya derlemenizi öneririz:  
  
-   Yeniden kullanılabilir normal ifadeler üretmek isteyen yetkin bir geliştiriciyseniz.  
  
-   Normal ifadenizin desen eşleme yöntemlerinizin belirsiz kere (bir ya da iki kezden binlerce ya da on binlerce defa) çağrılmasını bekliyorsanız. Derlenmiş veya yorumlanan normal ifadelerden farklı olarak, ayrı derlemelere derlenen normal ifadeler, yöntem çağrısı sayısından bağımsız olarak tutarlı bir performans sunar.  
  
 Performansı en iyi hale getirmek için derlenmiş normal ifadeler kullanıyorsanız, derlemeyi oluşturmak, normal ifade motorunu yüklemek ve bunun desen eşleyen yöntemlerini yürütmek için yansıtma kullanmamanız gerekir. Bu, normal ifade desenlerini dinamik olarak oluşturmaktan kaçınmanızı ve desen eşleme seçeneklerini (örneğin harf büyüklüğüne duyarlı eşleme) derleme oluşturulurken belirtmenizi gerekli kılar. Ayrıca derlemeyi, normal ifadeyi kullanan koddan oluşturan kodu ayırmanızı gerektirir.  
  
 Aşağıdaki örnek, derlenmiş bir normal ifade içeren bir derlemenin nasıl oluşturulacağını göstermektedir. Adlı bir derleme oluşturur `RegexLib.dll` bir tek normal ifade sınıfına sahip `SentencePattern`, cümle eşleşmeli normal ifade içeren kullanılan desen [vs yorumlanır. Derlenmiş normal ifadeler](#Interpreted) bölümü.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/compile1.cs#6)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/compile1.vb#6)]  
  
 Örnek bir yürütülebilir dosyayı ve çalışma derlendiğinde adlı bir derleme oluşturur. `RegexLib.dll`. Normal ifade adlı bir sınıf tarafından temsil edilen `Utilities.RegularExpressions.SentencePattern` sınıfından türetilen <xref:System.Text.RegularExpressions.Regex>. Aşağıdaki örnek, derlenmiş normal ifadeyi Theodore Dreiser'ın metni cümleler ayıklamak için ardından kullanır *The Financier*.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/compile2.cs#7)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/compile2.vb#7)]  
  
 [Başa dön](#top)  
  
<a name="Backtracking"></a>   
## <a name="take-charge-of-backtracking"></a>Geriye Dönüşü Denetimini El Alma  
 Sıradan şekilde, normal ifade motoru bir giriş dizsi içinde ilerlemek ve bunu bir normal ifade deseni ile karşılaştırmak için doğrusal ilerlemeyi kullanır. Ancak, gibi belirsiz miktar belirleyiciler `*`, `+`, ve `?` kullanılan normal ifade deseninde, normal ifade altyapısı başarılı kısmi eşleşmelerin bir kısmını verin ve önceden kaydedilmiş bir duruma geri dönebilir ve tüm desen için başarılı bir eşleşme aramak amacıyla. Bu işlem geri dönüş olarak bilinir.  
  
> [!NOTE]
>  Geri izleme hakkında daha fazla bilgi için bkz: [normal ifade davranışının ayrıntıları](../../../docs/standard/base-types/details-of-regular-expression-behavior.md) ve [Backtracking](../../../docs/standard/base-types/backtracking-in-regular-expressions.md). Geri izlemenin ayrıntılı bir açıklaması için bkz: [normal ifade performansını en iyi duruma getirme, Kısım II: Ücret, geri alma](https://blogs.msdn.microsoft.com/bclteam/2010/08/03/optimizing-regular-expression-performance-part-ii-taking-charge-of-backtracking-ron-petrusha/) bkz.BCL Ekibi blogunda.  
  
 Geri dönüş için destek, normal ifadelere güç ve esneklik kazandırır. Ayrıca normal ifade motorunun çalışmasının denetlenmesini sorumluluğunu normal ifade geliştiricisine teslim eder. Geliştiriciler genelde bu sorumluluğun farkında olmadığından, geri dönüşü yanlış kullanmaları ya da aşırı geri dönüşe bağımlılıkları genelde normal ifade performansının düşmesinde önemli bir rol oynar. En kötü senaryoda yürütme süresi girdi dizesinde her ek karakter ile iki katına çıkar. Aslında geri izlemeyi aşırı şekilde kullanarak, girişin normal ifade desenini yakın eşlemesi halinde sonsuz bir döngünün program eşdeğerini oluşturmak kolaydır; normal ifade motorunun görece kısa bir giriş dizesini işlemesi saatler ve hatta günler alabilir.  
  
 Genelde, geri izlemenin bir eşleme için gerekli olmadığı gerçeğine rağmen uygulamalar geri izleme kullandıkları için bir ceza öder. Örneğin, normal ifade `\b\p{Lu}\w*\b` aşağıdaki tabloda gösterildiği gibi bir büyük harf karakteri ile başlayan tüm sözcüklerle eşleşir.  
  
|Desen|Açıklama|  
|-|-|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`\p{Lu}`|Bir büyük harfli karakter eşleyin.|  
|`\w*`|Sıfır veya daha fazla sözcük karakteriyle eşleş.|  
|`\b`|Eşlemeyi bir sözcük sınırında sonlandır.|  
  
 Bir kelime sınırı bir kelime karakteri ile aynı ya da bunu bir alt kümesi olmadığından, normal ifade motorunun kelime karakterlerini eşlerken bir kelime sınırı geçirmesi mümkün değildir. Bunun anlamı şudur: bu normal ifadede geri dönüş, herhangi bir eşleşmenin genel başarısına hiçbir zaman katkıda bulunamaz; olsa olsa performansı düşürebilir, çünkü normal ifade altyapısı başarılı her sözcük karakteri eşleşmesindeki durumunu kaydetmeye zorlanır.  
  
 Geri izlemenin gerekli olmadığını belirlerseniz, onu kullanarak devre dışı bırakabilirsiniz `(?>subexpression)` dil öğesi. Aşağıdaki örnek, bir girdi dizesini iki normal ifade kullanarak ayrıştırmaktadır. Birincisi, `\b\p{Lu}\w*\b`, geri dönüş kullanır. İkinci `\b\p{Lu}(?>\w*)\b`, geri izlemeyi devre dışı bırakır. Örneğin çıktısında gösterildiği üzere bunların her ikisi de aynı sonucu üretir.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/backtrack2.cs#10)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/backtrack2.vb#10)]  
  
 Birçok durumda, geri izleme bir normal ifade desenini giriş metnine eşlemek için gereklidir. Ancak aşırı geri izleme performansı ciddi şekilde azaltabilir ve uygulamanın yanıt vermediği izlenimine yol açabilir. Bu durum, özellikle, miktar belirleyiciler yuvalandığında ve metin dış alt ifadeyle eşleşen metin, dış alt ifadeyle eşleşen metnin bir alt kümesi olduğunda gerçekleşir.  
  
> [!WARNING]
>  Aşırı geri izlemeyi önlemeye ek olarak, aşırı geri izlemenin normal ifade performansını ciddi şekilde bozmayacağından emin olmak için zaman aşımı özelliğini de kullanmalısınız. Daha fazla bilgi için [zaman aşımı değerlerini kullanma](#Timeouts) bölümü.  
  
 Örneğin, normal ifade deseni `^[0-9A-Z]([-.\w]*[0-9A-Z])*\$$` en az bir alfasayısal karakterden oluşan bir parça numarasını eşlemek içindir. Bir ek karakter bir alfasayısal karakter, bir ayırma çizgisi, bir alt çizgi ya da bir nokta olabilir, ancak son karakter alfasayısal olmalıdır. Bir dolar işareti parça numarasını sonlandırır. Bazı durumlarda, bu normal ifade deseni son derece düşük performans belirleyiciler olduğundan ve çünkü sergiler alt ifade `[0-9A-Z]` alt ifade bir alt kümesi `[-.\w]*`.  
  
 Bu durumlarda, yuvalanan miktar belirleyicileri kaldırarak ve dış alt ifadeyi sıfır genişliğinde bir ileriye dönük ya da geriye dönük onay ile değiştirerek normal ifade performansını en iyi hale getireceksiniz. İleriye dönük ve geriye dönük onaylar tutturuculardır; bunlar giriş dizesindeki işaretçiyi kaydırmaz, bunun yerine belirtilen koşulun sağlanıp sağlanmadığını kontrol etmek için ileriye ya da geriye bakar. Örneğin, parça numarası normal ifadesi şeklinde yeniden yazılabilir `^[0-9A-Z][-.\w]*(?<=[0-9A-Z])\$$`. Bu normal ifade deseni aşağıdaki tabloda gösterildiği gibi tanımlanmaktadır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`^`|Giriş dizesinin başında eşleşmeye başla.|  
|`[0-9A-Z]`|Alfasayısal bir karakterle eşleştirin Parça numarası en azından bu karakteri içermelidir.|  
|`[-.\w]*`|Herhangi bir sözcük karakteri, kesme ya da noktanın sıfır ya da daha fazla oluşumunu eşleyin.|  
|`\$`|Bir dolar işareti eşleyin.|  
|`(?<=[0-9A-Z])`|Önceki karakterin alfa sayısal olduğundan emin olmak için sonlandıran dolar işaretinin önüne bakın.|  
|`$`|Giriş dizesinin sonunda eşleşmeyi bitir.|  
  
 Aşağıdaki örnek, bu normal ifadenin parça numaraları içeriyor olabilecek bir diziyi eşleştirmek için kullanımını göstermektedir.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/backtrack4.cs#11)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/backtrack4.vb#11)]  
  
 .NET içinde normal ifade dili, iç içe niceleyicileri çıkarmak için kullanabileceğiniz aşağıdaki dil öğelerini içerir. Daha fazla bilgi için [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
|Dil öğesi|Açıklama|  
|----------------------|-----------------|  
|`(?=` `subexpression` `)`|Sıfır genişlikli pozitif ileriye yönelik onay. Belirlemek için geçerli konumun önüne bakın olmadığını `subexpression` giriş dizesi ile eşleştiğini.|  
|`(?!` `subexpression` `)`|Sıfır genişlikli negatif ileriye yönelik onay. Belirlemek için geçerli konumun önüne bakın olmadığını `subexpression` giriş dizesi ile eşleşmiyor.|  
|`(?<=` `subexpression` `)`|Sıfır genişlikli pozitif geriye yönelik onay. Belirlemek için geçerli konumun arkasına bakın olmadığını `subexpression` giriş dizesi ile eşleştiğini.|  
|`(?<!` `subexpression` `)`|Sıfır genişlikli negatif geriye yönelik onay. Belirlemek için geçerli konumun arkasına bakın olmadığını `subexpression` giriş dizesi ile eşleşmiyor.|  
  
 [Başa dön](#top)  
  
<a name="Timeouts"></a>   
## <a name="use-time-out-values"></a>Zaman Aşımı Değerlerini Kullanma  
 Normal ifadeleriniz, normal ifade deseniyle neredeyse eşleşen girişleri işleme alıyorsa, sıkça aşırı geri izlemeye dayanıyor olabilir, bu da performansı önemli ölçüde etkiler. Normal ifadenin yakın eşleme girişine karşı geri izlemesi ve testine ilişkin kullanımınızı dikkatle düşünmeye ek olarak, gerçekleşmesi halinde aşırı geri izleme etkisinin en aza indirilmesini sağlamak için mutlaka bir zaman aşımı değeri belirlemelisiniz.  
  
 Normal ifade zaman aşımı aralığı, normal ifade altyapısının zaman aşımına uğramadan önce tek bir eşleşen arayacağı süreyi tanımlar. Varsayılan zaman aşımı aralığı <xref:System.Text.RegularExpressions.Regex.InfiniteMatchTimeout?displayProperty=nameWithType>, normal ifade zaman aşımına olacağı anlamına gelir. Aşağıdaki şekilde bu değeri geçersiz kılabilir ve bir zaman aşımı aralığı tanımlayabilirsiniz:  
  
-   Başlattığınızda bir zaman aşımı değeri sağlayarak bir <xref:System.Text.RegularExpressions.Regex> çağırarak <xref:System.Text.RegularExpressions.Regex.%23ctor%28System.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29?displayProperty=nameWithType> Oluşturucusu.  
  
-   Yöntemi gibi bir statik desen çağırarak <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29?displayProperty=nameWithType> veya <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29?displayProperty=nameWithType>, içeren bir `matchTimeout` parametresi.  
  
-   Çağrılarak oluşturulmuş derlenmiş normal ifadeler <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> türünde bir parametresi olan yapılandırıcının çağrılmasıyla yöntemi, <xref:System.TimeSpan>.  
  
 Normal ifade yöntemi bir zaman aşımı aralığı belirlediyseniz ve bu aralığın sonunda bir eşleşme bulunamadı, oluşturur bir <xref:System.Text.RegularExpressions.RegexMatchTimeoutException> özel durum. Özel durum işleyicinizde, eşlemeyi daha uzun bir zaman aralığı ile yeniden denemeyi, eşleme denemesinden vazgeçip bir eşleme olmadığını varsaymayı ya da eşleme denemesinden vazgeçip özel durum bilgisini gelecekteki analizler için kaydetmeyi seçebilirsiniz.  
  
 Aşağıdaki örnekte tanımlayan bir `GetWordData` normal bir ifade ile bir zaman aşımı aralığı 350 milisaniye sayısını ve sözcük başına ortalama karakter sayısını bir metin belgesindeki sözcük hesaplamak için başlatan yöntem. Eşleme işlemi zaman aşımına uğrarsa, zaman aşımı aralığı 350 milisaniye artırılır ve <xref:System.Text.RegularExpressions.Regex> nesnesi yeniden oluşturulur. Yeni zaman aşımı aralığı 1 saniyeden uzunsa, yöntem yeniden çağırıcıya özel durum atar.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/timeout1.cs#12)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/timeout1.vb#12)]  
  
 [Başa dön](#top)  
  
<a name="Capture"></a>   
## <a name="capture-only-when-necessary"></a>Yalnızca Gerekli Olduğunda Yakala  
 .NET içinde normal ifadeler bir normal ifade desenini bir veya daha fazla gruplamanıza olanak veren gruplama yapıları sayısını destekler. .NET normal ifade dilindeki en sık kullanılan gruplama yapıları olan `(` *subexpression*`)`, numaralandırılmış bir tutma grubu tanımlayan ve `(?<` *adı* `>` *subexpression*`)`, adlandırılmış bir tutma grubu tanımlayan. Yapı birimlerini gruplamak; yeniden başvuruları oluşturmak ve bir miktar belirleyicinin uygulandığı bir alt ifade tanımlamak için gereklidir.  
  
 Ancak bu dil öğelerinin kullanılmasının bir maliyeti vardır. Bunlar neden <xref:System.Text.RegularExpressions.GroupCollection> tarafından döndürülen nesne <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> en son özelliğinin adlandırılmamış veya adlandırılmış ve tek bir gruplama kurgusu birden çok alt dizeleri giriş dizesinde yakalanan, bunlar da doldurmak<xref:System.Text.RegularExpressions.CaptureCollection>tarafından döndürülen nesne <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> özelliği birden çok belirli bir yakalama grubunun <xref:System.Text.RegularExpressions.Capture> nesneleri.  
  
 Genelde oluşturma birimlerini gruplama, miktar belirleyicilerin yalnızca bunlara uygulanacağı şekilde bir normal ifadede kullanılır ve bu alt ifadeler tarafından yakalanan gruplar daha sonra kullanılmaz. Örneğin, normal ifade `\b(\w+[;,]?\s?)+[.?!]` tamamını bir cümle yakalamak için tasarlanmıştır. Aşağıdaki tabloda bu normal ifade deseni ve etkilerini dil öğelerini açıklar <xref:System.Text.RegularExpressions.Match> nesnenin <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> ve <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> koleksiyonları.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`\w+`|Bir veya daha fazla sözcük karakteri eşleştir.|  
|`[;,]?`|Sıfır ya da bir virgül ya da noktalı virgülü eşleyin.|  
|`\s?`|Sıfır veya bir beyaz boşluk karakterini eşleştirin.|  
|`(\w+[;,]?\s?)+`|Arkasından isteğe bağlı bir boşluk karakteri gelen isteğe bağlı bir virgül ya da noktalı virgül tarafından izlenen bir ya da daha fazla sözcük karakterinin bir ya da daha fazla oluşumunu eşleyin. Bu, birkaç sözcük karakteri (yani sözcüğün) ve ardından isteğe bağlı bir noktalama işaretinin, normal ifade altyapısı cümlenin sonuna ulaşıncaya kadar tekrarlanması için gerekli olan ilk tutma grubunu tanımlar.|  
|`[.?!]`|Bir nokta, soru işareti ya da ünlem işareti eşleyin.|  
  
 Bir eşleşme bulunduğunda, her ikisi de aşağıdaki örnekte gösterildiği gibi <xref:System.Text.RegularExpressions.GroupCollection> ve <xref:System.Text.RegularExpressions.CaptureCollection> nesneleri gelen yakalamalarla doldurulur. Bu durumda, yakalama grubu `(\w+[;,]?\s?)` var. böylece `+` niceleyici uygulanabilir, her bir sözcüğün bir cümle eşleştirilecek normal ifade deseni sağlar. Aksi halde bir cümledeki son sözcüğü eşleyebilir.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/group1.cs#8)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/group1.vb#8)]  
  
 Alt ifadeleri yalnızca bunlara niceleyiciler uygulamak için kullanırken ve tutulan metinle ilgilenmediğinizde, grup tutmalarını devre dışı bırakmanız gerekir. Örneğin, `(?:subexpression)` dil öğesi engeller geçerli olduğu grubun eşlenen alt dizeleri yakalamasını önler. Aşağıdaki örnekte, önceki örnekteki normal ifade deseni olarak değiştirilir `\b(?:\w+[;,]?\s?)+[.?!]`. Çıktıda gösterildiği gibi normal ifade altyapısı doldurmasını önler <xref:System.Text.RegularExpressions.GroupCollection> ve <xref:System.Text.RegularExpressions.CaptureCollection> koleksiyonları.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/group2.cs#9)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/group2.vb#9)]  
  
 Tutmayı, şu yöntemlerden biriyle devre dışı bırakabilirsiniz:  
  
-   Kullanım `(?:subexpression)` dil öğesi. Bu öğe, geçerli olduğu gruptaki eşleşen alt dizelerin tutulmasını engeller. Herhangi bir yuvalanmış grupta alt dize yakalamalarını devre dışı bırakmaz.  
  
-   Kullanım <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture> seçeneği. Normal ifade deseninde tüm adlandırılmamış ya da örtük yakalamaları devre dışı bırakır. Bu seçeneği kullandığınızda yalnızca tanımlı adlandırılmış gruplarla eşleşen alt dizeler `(?<name>subexpression)` dil öğesi tutulabilir. <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture> Bayrağı geçilebilir `options` parametresinin bir <xref:System.Text.RegularExpressions.Regex> sınıf oluşturucusu veya `options` parametresinin bir <xref:System.Text.RegularExpressions.Regex> statik eşleme yönteminin.  
  
-   Kullanım `n` seçeneğini `(?imnsx)` dil öğesi. Bu seçenek, tutulan tüm adlandırılmamış veya örtük öğeleri, öğenin normal ifade deseninde ortaya çıktığı noktadan başlayarak devre dışı bırakır. Ya da kadar deseninin veya kadar yakalamaları devre dışı `(-n)` seçeneği adlandırılmamış veya örtük öğeleri sağlar. Daha fazla bilgi için [çeşitli yapıları](../../../docs/standard/base-types/miscellaneous-constructs-in-regular-expressions.md).  
  
-   Kullanım `n` seçeneğini `(?imnsx:subexpression)` dil öğesi. Bu seçenek tüm adlandırılmamış veya örtük öğeleri devre dışı bırakır. `subexpression`. Yakalamalar adlandırılmamış ya da örtük yuvalı yakalama grupları tarafından devre dışı bırakılır.  
  
 [Başa dön](#top)  
  
<a name="RelatedTopics"></a>   
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Normal İfade Davranışının Ayrıntıları](../../../docs/standard/base-types/details-of-regular-expression-behavior.md)|.NET normal ifade motorunun uygulanmasını inceler. Konu normal ifadelerin esnekliği üzerine yoğunlaşmakta ve geliştiricinin normal ifade altyapısının verimli ve sorunsuz çalışmasını sağlamadaki sorumluluğunu açıklamaktadır.|  
|[Geri Dönüş](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)|Geri izlemenin ne olduğunu ve bunun normal ifade performansını nasıl etkilediği açıklar ve geri izlemeye alternatifler sağlayan dil öğelerini inceler.|  
|[Normal İfade Dili - Hızlı Başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)|.NET içinde normal ifade dilinin öğelerini açıklar ve her dil öğesi için ayrıntılı belgelere bağlantılar sağlar.|
