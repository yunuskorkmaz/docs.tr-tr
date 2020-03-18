---
title: .NET'te Normal İfadeler İçin En İyi Uygulamalar
description: .NET'te etkili ve etkili düzenli ifadeler oluşturmayı öğrenin.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- .NET Framework regular expressions, best practices
- regular expressions, best practices
ms.assetid: 618e5afb-3a97-440d-831a-70e4c526a51c
ms.openlocfilehash: 9b09f5a2505888c6154a58a3512c94c51f89295b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77124428"
---
# <a name="best-practices-for-regular-expressions-in-net"></a>.NET'te normal ifadeler için en iyi uygulamalar

.NET'teki normal ifade altyapısı, metni karşılaştırmave eşleştirme yerine desen eşleşmelerine göre işleyen güçlü ve tam özellikli bir araçtır. Çoğu durumda desen eşleme işlemini hızlı ve verimli şekilde yapar. Ancak bazı durumlarda normal ifade motoru çok yavaş görünebilir. Aşırı durumlarda saatler ve hatta günler boyunca görece küçük bir girişi işlerken yanıt vermeyi durdurmuş gibi bile görünebilir.

Bu konu, normal ifadelerinin en iyi performansa ulaşabilmesi için geliştiricilerin benimseyebileceği en iyi yöntemlerden bazılarını özetlemektedir.

## <a name="consider-the-input-source"></a>Giriş kaynağını göz önünde bulundurun

Genelde normal ifadeler iki tür giriş kabul edebilir: sınırlandırılmış ya da sınırlandırılmamış. Kısıtlı giriş, bilinen ya da güvenilir bir kaynaktan geldiği bilinen ve ön tanımlı bir biçim izleyen metindir. Sınırlandırılmamış girdi, bir web kullanıcısı gibi güvenilir olmayan bir kaynaktan gelen ve önceden tanımlı veya beklenen bir biçime uymayabilecek bir metindir.

Normal ifade desenleri genelde geçerli girişi eşlemek için yazılır. Diğer bir deyişle, geliştiriciler eşleştirmek istedikleri metni inceler ve bu metinle eşleşen normal bir ifade deseni yazarlar. Geliştiriciler daha sonra bu desenin düzeltme ya da daha fazla ayrıntı gerektirip gerektirmediğini, birden çok geçerli giriş öğesini test ederek belirler. Desen gereçli olduğu kabul edilen tüm girdilerle eşleştiğinde, üretime hazır kabul edilir ve çıkacak uygulamaya dahil edilebilir. Bu, normal bir ifade desenini, kısıtlanmış girdiyle eşleşme için uygun hale getirir. Ancak sınırlandırılmamış girişin eşlenmesi uygun hale getirmez.

Sınırlandırılmamış girdide eşlemek yapmak için, normal bir ifade üç tür metni verimli olarak işleyebilmelidir:

- Normal ifade deseniyle eşleşen metin.

- Normal ifade deseniyle eşleşmeyen metin.

- Normal ifade deseniyle neredeyse eşleşen metin.

Son metin türü, sınırlandırılmış girdi işlemek üzere yazılmış bir normal ifade için özellikle sorunludur. Bu normal ifade aynı zamanda kapsamlı [geri izleme](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)dayanıyorsa, normal ifade altyapısı görünüşte zararsız metin işleme zaman (bazı durumlarda, birçok saat veya gün) aşırı miktarda geçirebilirsiniz.

> [!WARNING]
> Aşağıdaki örnek, aşırı miktarda geri dönüş kullanma eğiliminde olan ve geçerli e-posta adreslerini reddetmesi olası bir normal ifadeyi kullanmaktadır. Bir e-posta doğrulama yordamında kullanmamalısınız. E-posta adreslerini doğrulayan normal bir ifade istiyorsanız, [bkz.](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md)

Örneğin bir e-posta adresinin takma adını onaylamak için çok yaygın kullanılan ama son derece sorunlu normal ifade düşünün. Normal ifade, `^[0-9A-Z]([-.\w]*[0-9A-Z])*$` alfasayısal bir karakterden oluşan ve ardından alfasayısal, dönemler veya tireler olabilecek sıfır veya daha fazla karakterden oluşan geçerli bir e-posta adresi olarak kabul edilen şeyi işlemek için yazılır. Normal ifade, alfasayısal bir karakterle bitmelidir. Ancak aşağıdaki örnekte gösterildiği gibi, bu normal ifade geçerli girişi kolayca yönetmesine rağmen performansı neredeyse geçerli girişi işlerken çok yetersizdir.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/design2.cs#1)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/design2.vb#1)]

Örneğin çıktısında gösterildiği üzere normal ifade motoru geçerli e-posta takma adlarını, uzunluğundan bağımsız olarak yaklaşık aynı zaman aralığında işler. Diğer taraftan, yakın geçerli e-posta adresi beşten fazla karakter içeriyorsa, işlem zamanı dizedeki ek her karakter için yaklaşık iki kat olacaktır. Bunun anlamı, neredeyse geçerli 28-karakter dizesi işlemek için bir saatten fazla götürecek ve neredeyse geçerli 33-karakter dizesi işlemek için neredeyse bir gün sürecektir.

Bu düzenli ifade yalnızca eşlenecek girişin biçimi düşünülerek geliştirildiğinden desen ile eşleşmeyen girişi hesaba katamaz. Bu da normal ifade deseniyle neredeyse eşleşen sınırlandırılmamış girdinin performansı önemli ölçüde düşürmesine neden olabilir.

Bu sorunu çözmek için, şunları yapabilirsiniz:

- Bir desen geliştirirken, özellikle de normal ifadeniz sınırlandırılmamış girdiyi işlemek üzere tasarlandıysa, geri dönüşün normal ifade altyapısının performansını nasıl etkileyeceğini düşünmelisiniz. Daha fazla bilgi için, [Geri İzlemeden Ücret Al](#take-charge-of-backtracking) bölümüne bakın.

- Normal ifadenizi geçerli girdilerin yanı sıra gereçsiz ve neredeyse geçerli girdiler de kullanarak baştan aşağı test edin. Belirli bir normal ifade için rasgele giriş oluşturmak için, Microsoft Research'ün düzenli bir ifade arama aracı olan [Rex'i](https://www.microsoft.com/research/project/rex-regular-expression-exploration/)kullanabilirsiniz.

## <a name="handle-object-instantiation-appropriately"></a>Nesne nin anlık noktalarını uygun şekilde işleme

Kalbinde. NET'in normal ifade nesnesi modeli, normal ifade altyapısını temsil eden <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> sınıftır. Genellikle, normal ifade performansını etkileyen tek büyük faktör, <xref:System.Text.RegularExpressions.Regex> motorun kullanılma şeklidir. Normal bir ifadeyi tanımlama, normal ifade motorunu bir normal ifade deseni ile sıkı şekilde eşlemeyi içerir. Bu bağlantı süreci, ister bir <xref:System.Text.RegularExpressions.Regex> nesneyi, oluşturucusu düzenli bir ifade deseni geçirerek ister analiz edilecek dize ile birlikte normal ifade deseni ile birlikte geçirerek statik bir metodu çağırarak anlık olarak bir araya getirerek, zorunlu olarak pahalı bir işlemdir.

> [!NOTE]
> Yorumlanmış ve derlenmiş normal ifadeleri kullanmanın performans etkilerihakkında daha ayrıntılı bir tartışma için [bkz.](https://docs.microsoft.com/archive/blogs/bclteam/optimizing-regular-expression-performance-part-ii-taking-charge-of-backtracking-ron-petrusha)

Normal ifade altyapısını belirli bir normal ifade deseniyle birleştirebilir, sonra altyapıyı birkaç şekilde metin eşlemesi yapmak üzere kullanabilirsiniz:

- Statik desen eşleştirme yöntemini çağırabilirsiniz, <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%29?displayProperty=nameWithType>örneğin. Bu, bir normal ifade nesnesine öndeğer atanmasını gerektirmez.

- Bir <xref:System.Text.RegularExpressions.Regex> nesneyi anında anlayabilir ve yorumlanmış normal ifadenin örnek desen eşleştirme yöntemini çağırabilirsiniz. Bu, normal ifade altyapısını bir normal ifade desenine bağlamak için varsayılan yöntemdir. Bir <xref:System.Text.RegularExpressions.Regex> `options` <xref:System.Text.RegularExpressions.RegexOptions.Compiled> nesne, bayrağı içeren bir bağımsız değişken olmadan anında elde edildiğinde sonuçlanır.

- Bir <xref:System.Text.RegularExpressions.Regex> nesneyi anında anlayabilir ve derlenmiş normal ifadenin örnek desen eşleştirme yöntemini çağırabilirsiniz. Normal ifade nesneleri, bir <xref:System.Text.RegularExpressions.Regex> nesne bayrağı içeren bir `options` bağımsız değişkenle <xref:System.Text.RegularExpressions.RegexOptions.Compiled> anında işaretlendiğinde derlenmiş desenleri temsil eder.

- Belirli bir normal ifade <xref:System.Text.RegularExpressions.Regex> deseniyle sıkıca birleşen özel amaçlı bir nesne oluşturabilir, derleyebilir ve bağımsız bir derlemeye kaydedebilirsiniz. Yöntemi arayarak <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> bunu yaparsınız.

Normal ifade eşleme yöntemlerini çağırma biçiminizin uygulamanız üzerinde önemli bir etkisi olabilir. Aşağıdaki bölümler, uygulamanızın performansını iyileştirmek için statik yöntem çağrılarının, yorumlanan normal ifadelerin ve derlenmiş normal ifadelerin ne zaman kullanılacağını tartışmaktadır.

> [!IMPORTANT]
> Yöntem çağrılarında aynı normal ifade tekrar tekrar kullanılıyorsa veya uygulama normal ifade nesnelerini yoğun olarak kullanıyorsa, yöntem çağrısının biçimi (statik, yorumlanan, derlenmiş) performansı etkiler.

### <a name="static-regular-expressions"></a>Statik düzenli ifadeler

Statik normal ifade yöntemleri, bir normal ifade nesnesine aynı normal ifadeyi tekrar tekrar ön değer olarak atamaya alternatif olarak önerilir. Normal ifade nesneleri tarafından kullanılan normal ifade desenlerinden farklı olarak, statik yöntem çağrılarında kullanılan desenlerden işlem kodları veya derlenmiş Microsoft ara dili (MSIL) normal ifade altyapısı tarafından dahili olarak önbelleğe alır.

Örneğin bir olay işleyicisi, kullanıcı girişini onaylamak için sık sık başka bir yöntem çağırır. Bu, bir <xref:System.Windows.Forms.Button> denetim <xref:System.Windows.Forms.Control.Click> olayının `IsValidCurrency`, kullanıcının bir para birimi simgesine girip girmediğini ve ardından en az bir ondalık basamak girdiğini denetleyen bir yöntemi çağırmak için kullanıldığı aşağıdaki koda yansıtılır.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/static1.cs#2)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/static1.vb#2)]

Yöntemin `IsValidCurrency` çok verimsiz bir uygulama aşağıdaki örnekte gösterilmiştir. Her yöntem çağrısının aynı desene <xref:System.Text.RegularExpressions.Regex> sahip bir nesneyi yeniden yeniden instantiates olduğunu unutmayın. Bu ise normal ifade deseninin yöntem her çağrıldığında tekrar derlenmesi gerektiği anlamına gelir.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/static1.cs#3)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/static1.vb#3)]

Bu verimsiz kodu statik <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> yönteme yapılan bir çağrıyla değiştirmeniz gerekir. Bu, bir <xref:System.Text.RegularExpressions.Regex> nesneyi her desen eşleştirme yöntemini çağırmak istediğinizde anında çevirme gereksinimini ortadan kaldırır ve normal ifade altyapısının önbelleğinden normal ifadenin derlenmiş bir sürümünü almasına olanak tanır.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/static2.cs#4)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/static2.vb#4)]

Varsayılan olarak, en son kullanılan 15 statik normal ifade deseni önbelleğe alınır. Daha fazla sayıda önbelleğe alınmış statik normal ifade gerektiren uygulamalariçin, önbelleğin boyutu <xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=nameWithType> özelliği ayarlayarak ayarlanabilir.

Bu örnekte kullanılan normal ifade, `\p{Sc}+\s*\d+` giriş dizesinin bir para birimi simgesi ve en az bir ondalık basamaktan oluştuğunu doğrular. Desen aşağıdaki tabloda gösterildiği gibi tanımlanır.

|Desen|Açıklama|
|-------------|-----------------|
|`\p{Sc}+`|Unicode Sembolü, Para Birimi kategorisinde bir ya da daha fazla karakter eşleyin.|
|`\s*`|Sıfır veya daha fazla boşluk karakteriyle eşleş.|
|`\d+`|Bir veya daha fazla ondalık basamağı eşleştirin.|

### <a name="interpreted-vs-compiled-regular-expressions"></a>Yorumlanan vs derlenmiş düzenli ifadeler

<xref:System.Text.RegularExpressions.RegexOptions.Compiled> Opsiyonun belirtimi ile normal ifade motoruna bağlı olmayan normal ifade desenleri yorumlanır. Bir normal ifade nesnesi örneği oluşturulduğunda, normal ifade altyapısı normal ifadeyi bir dizi işlem koduna dönüştürür. Bir örnek yöntemi çağrıldığında, işlem kodları MSIL'ye dönüştürülür ve JIT derleyicisi tarafından yürütülür. Benzer şekilde, statik bir normal ifade yöntemi çağrıldığı ve normal ifade önbellekte bulunamadığı zaman, normal ifade altyapısı normal ifadeyi bir dizi işlem koduna dönüştürür ve bunları önbellekte depolar. Daha sonra işlem kodlarını MSIL'ye dönüştürür, bu sayede JIT derleyicisi bunları yürütebilir. Yorumlanmış normal ifadeler, daha yavaş yürütme sürelerine karşın açılış süresini azaltır. Bundan dolayı bunlar, normal ifade az sayıda yöntem çağrısında kullanıldığında ya da normal ifade yöntemine yapılan kesin çağrı sayısı bilinmiyor ancak küçük olması bekleniyorsa en iyi şekilde kullanılır. Yöntem çağrıları arttıkça performans kazancı daha az başlangıç saatinden sayısı daha yavaş yürütme hızını outstripped gibi.

<xref:System.Text.RegularExpressions.RegexOptions.Compiled> Opsiyonun belirtimi ile normal ifade motoruna bağlanan normal ifade desenleri derlenir. Bu, bir normal ifade nesnesi örneği oluşturulduğunda veya statik bir normal ifade yöntemi çağrıldığında ve normal ifade önbellekte bulunamadığında, normal ifade altyapısının normal ifadeyi ara bir işlem kodu kümesine, sonra da bunu MSIL'ye dönüştürdüğü anlamına gelir. Bir yöntem çağrıldığında, JIT derleyici MSIL'yi yürütür. Yorumlanmış normal ifadelerin aksine, derlenmiş normal ifadeler açılış süresini artırır ancak ayrı desen eşleme yöntemlerini daha hızlı yürütür. Sonuç olarak normal ifade derlemekten kaynaklanan sonuçlardan yararlanan performans çağrılan normal ifade yöntemlerinin sayısı oranında artar.

Özetlemek gerekirse, normal ifade yöntemlerini belirli bir normal ifadeyle nispeten ender olarak çağırıyorsanız, yorumlanan normal ifadeler kullanmanızı öneririz. Normal ifade yöntemlerinizi oldukça sık olarak belirli bir normal ifadeyle çağırıyorsanız, derlenmiş normal ifadeler kullanmalısınız. Yorumlanan normal ifadelerin yürütülme hızlarındaki yavaşlığın bunların başlama süresinin kısa olmasından elde edilen avantajı ortadan kaldırmaya başladığı eşiği veya derlenmiş normal ifadelerin başlama süresinin uzunluğunun bunların yürütülme hızından elde edilen avantajı ortadan kaldırmaya başladığı eşiği belirlemek güçtür. Normal ifadenin karmaşıklığı ve bunun işlediği özel veri gibi çeşitli faktörlere bağlıdır. Yorumlanan veya derlenen normal ifadelerin belirli uygulama senaryonuz için en iyi <xref:System.Diagnostics.Stopwatch> performansı gösterip sunmadığını belirlemek için, sınıfı yürütme sürelerini karşılaştırmak için kullanabilirsiniz.

Aşağıdaki örnek, ilk on cümleyi okurken ve Theodore Dreiser'ın *The Financier*'inin metnindeki tüm cümleleri okurken derlenmiş ve yorumlanmış normal ifadelerin performansını karşılaştırır. Örneğin çıktısında gösterildiği üzere normal ifade eşleme yöntemlerine yalnızca on çağrı yapıldığında, yorumlanan bir normal ifade derlenmiş bir normal ifadeden daha iyi performans sergiler. Ancak derlenmiş bir normal ifade, daha fazla sayıda çağrı yapıldığında (bu örnekte 13.000'den fazla) daha iyi performans gösterir.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/compare1.cs#5)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/compare1.vb#5)]

Örnekte kullanılan normal ifade `\b(\w+((\r?\n)|,?\s))*\w+[.?:;!]`deseni, aşağıdaki tabloda gösterildiği gibi tanımlanır.

|Desen|Açıklama|
|-------------|-----------------|
|`\b`|Bir sözcük sınırında eşleşmeye başla.|
|`\w+`|Bir veya daha fazla sözcük karakteri eşleştir.|
|<code>(\r?\n)&#124;,?\s)</code>|Arkasından bir yeni satır karakteri gelen sıfır ya da bir satır başı veya arkasından bir boşluk karakteri gelen sıfır ya da bir virgül eşleyin.|
|<code>(\w+((\r?\n)&#124;,?\s))*</code>|Arkasından sıfır ya da bir satır başı ve bir yeni satır karakteri veya sıfır ya da bir virgül ve sonra boşluk karakteri gelen bir ya da daha fazla sözcük karakterinin sıfır ya da daha fazla oluşumunu eşleyin.|
|`\w+`|Bir veya daha fazla sözcük karakteri eşleştir.|
|`[.?:;!]`|Bir nokta, soru işareti, iki nokta üst üste, noktalı virgül ya da ünlem işareti eşleyin.|

### <a name="regular-expressions-compiled-to-an-assembly"></a>Normal ifadeler: Derlemeye derlenmiş

.NET ayrıca derlenmiş düzenli ifadeler içeren bir derleme oluşturmanıza da olanak tanır. Bu, normal ifade derlemesinin uğradığı performans düşüşünü çalışma zamanından tasarım zamanına taşır. Ancak ayrıca bazı ek işleri de içerir: Normal ifadeleri önceden tanımlamanız ve bunları bir derleme içinde derlemeniz gerekir. Derleyici daha sonra, derlemenin normal ifadelerini kullanan kaynak kodunu derlerken bu derlemeye başvurabilir. Derlemede derlenen her derlenmiş normal ifade, 'den <xref:System.Text.RegularExpressions.Regex>türeyen bir sınıf tarafından temsil edilir.

Bir derlemeye normal ifadeleri derlemek <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%28System.Text.RegularExpressions.RegexCompilationInfo%5B%5D%2CSystem.Reflection.AssemblyName%29?displayProperty=nameWithType> için, yöntemi çağırır ve <xref:System.Text.RegularExpressions.RegexCompilationInfo> derlenecek normal ifadeleri temsil eden bir nesne <xref:System.Reflection.AssemblyName> dizisi ve oluşturulacak derleme hakkında bilgi içeren bir nesne geçirirsiniz.

Aşağıdaki durumlarda normal ifadeleri bütünleşik bir dosyaya derlemenizi öneririz:

- Yeniden kullanılabilir normal ifadeler üretmek isteyen yetkin bir geliştiriciyseniz.

- Normal ifadenizin desen eşleme yöntemlerinizin belirsiz kere (bir ya da iki kezden binlerce ya da on binlerce defa) çağrılmasını bekliyorsanız. Derlenmiş veya yorumlanan normal ifadelerden farklı olarak, ayrı derlemelere derlenen normal ifadeler, yöntem çağrısı sayısından bağımsız olarak tutarlı bir performans sunar.

Performansı en iyi hale getirmek için derlenmiş normal ifadeler kullanıyorsanız, derlemeyi oluşturmak, normal ifade motorunu yüklemek ve bunun desen eşleyen yöntemlerini yürütmek için yansıtma kullanmamanız gerekir. Bu, normal ifade desenlerini dinamik olarak oluşturmaktan kaçınmanızı ve desen eşleme seçeneklerini (örneğin harf büyüklüğüne duyarlı eşleme) derleme oluşturulurken belirtmenizi gerekli kılar. Ayrıca derlemeyi, normal ifadeyi kullanan koddan oluşturan kodu ayırmanızı gerektirir.

Aşağıdaki örnek, derlenmiş bir normal ifade içeren bir derlemenin nasıl oluşturulacağını göstermektedir. [Yorumlanan ve Derlenen Düzenli İfadeler](#interpreted-vs-compiled-regular-expressions) `SentencePattern`bölümünde kullanılan cümle eşleştirme li normal ifade deseni içeren, tek bir normal ifade sınıfıyla adlandırılan `RegexLib.dll` bir derleme oluşturur.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/compile1.cs#6)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/compile1.vb#6)]

Örnek yürütülebilir ve çalıştırılabilen bir derlendiğinde, `RegexLib.dll`'. adlı bir derleme oluşturur. Normal ifade, `Utilities.RegularExpressions.SentencePattern` <xref:System.Text.RegularExpressions.Regex>türetilen bir sınıf tarafından temsil edilir. Aşağıdaki örnek teodore Dreiser's *Financier*metninden cümleleri ayıklamak için derlenmiş düzenli ifade kullanır.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/compile2.cs#7)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/compile2.vb#7)]

## <a name="take-charge-of-backtracking"></a>Geri izleme sorumluluğunu alın

Sıradan şekilde, normal ifade motoru bir giriş dizsi içinde ilerlemek ve bunu bir normal ifade deseni ile karşılaştırmak için doğrusal ilerlemeyi kullanır. Ancak, , `*`, `+`, gibi belirsiz niceleyiciler ve `?` normal bir ifade deseni kullanıldığında, normal ifade altyapısı başarılı kısmi eşleşmelerin bir kısmını vazgeçebilir ve tüm desen için başarılı bir eşleşme aramak için önceden kaydedilmiş bir duruma dönebilir. Bu işlem geri dönüş olarak bilinir.

> [!NOTE]
> Geri izleme hakkında daha fazla bilgi için Düzenli İfade Davranışı ve [Geri İzleme](../../../docs/standard/base-types/backtracking-in-regular-expressions.md) [Ayrıntıları'na](../../../docs/standard/base-types/details-of-regular-expression-behavior.md) bakın. Geri izleme hakkında ayrıntılı bir tartışma için bkz: [Normal İfade Performansını Optimize Etme, Bölüm II:](https://docs.microsoft.com/archive/blogs/bclteam/optimizing-regular-expression-performance-part-ii-taking-charge-of-backtracking-ron-petrusha) BCL Team blogunda Geri İzlemenin Ücretlendirmesi.

Geri dönüş için destek, normal ifadelere güç ve esneklik kazandırır. Ayrıca normal ifade motorunun çalışmasının denetlenmesini sorumluluğunu normal ifade geliştiricisine teslim eder. Geliştiriciler genelde bu sorumluluğun farkında olmadığından, geri dönüşü yanlış kullanmaları ya da aşırı geri dönüşe bağımlılıkları genelde normal ifade performansının düşmesinde önemli bir rol oynar. En kötü senaryoda yürütme süresi girdi dizesinde her ek karakter ile iki katına çıkar. Aslında geri izlemeyi aşırı şekilde kullanarak, girişin normal ifade desenini yakın eşlemesi halinde sonsuz bir döngünün program eşdeğerini oluşturmak kolaydır; normal ifade motorunun görece kısa bir giriş dizesini işlemesi saatler ve hatta günler alabilir.

Genelde, geri izlemenin bir eşleme için gerekli olmadığı gerçeğine rağmen uygulamalar geri izleme kullandıkları için bir ceza öder. Örneğin, normal ifade, `\b\p{Lu}\w*\b` aşağıdaki tabloda görüldüğü gibi, büyük harfli bir karakterle başlayan tüm sözcüklerle eşleşir.

|Desen|Açıklama|
|-|-|
|`\b`|Bir sözcük sınırında eşleşmeye başla.|
|`\p{Lu}`|Bir büyük harfli karakter eşleyin.|
|`\w*`|Sıfır veya daha fazla sözcük karakteriyle eşleş.|
|`\b`|Eşlemeyi bir sözcük sınırında sonlandır.|

Bir kelime sınırı bir kelime karakteri ile aynı ya da bunu bir alt kümesi olmadığından, normal ifade motorunun kelime karakterlerini eşlerken bir kelime sınırı geçirmesi mümkün değildir. Bunun anlamı şudur: bu normal ifadede geri dönüş, herhangi bir eşleşmenin genel başarısına hiçbir zaman katkıda bulunamaz; olsa olsa performansı düşürebilir, çünkü normal ifade altyapısı başarılı her sözcük karakteri eşleşmesindeki durumunu kaydetmeye zorlanır.

Geri izlemenin gerekli olmadığını belirlerseniz, atomik grup olarak `(?>subexpression)` bilinen dil öğesini kullanarak onu devre dışı kullanabilirsiniz. Aşağıdaki örnek, bir girdi dizesini iki normal ifade kullanarak ayrıştırmaktadır. İlki, `\b\p{Lu}\w*\b`geri izleme üzerine dayanır. İkincisi, `\b\p{Lu}(?>\w*)\b`geri izlemeyi devre dışı kılabilir. Örneğin çıktısında gösterildiği üzere bunların her ikisi de aynı sonucu üretir.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/backtrack2.cs#10)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/backtrack2.vb#10)]

Birçok durumda, geri izleme bir normal ifade desenini giriş metnine eşlemek için gereklidir. Ancak aşırı geri izleme performansı ciddi şekilde azaltabilir ve uygulamanın yanıt vermediği izlenimine yol açabilir. Bu durum, özellikle, miktar niceleyiciler yuvalandığında ve metin dış alt ifadeyle eşleşen metin, dış alt ifadeyle eşleşen metnin bir alt kümesi olduğunda gerçekleşir.

> [!WARNING]
> Aşırı geri izlemeyi önlemeye ek olarak, aşırı geri izlemenin normal ifade performansını ciddi şekilde bozmayacağından emin olmak için zaman aşımı özelliğini de kullanmalısınız. Daha fazla bilgi için [Zaman Çıkış Değerlerini Kullan](#use-time-out-values) bölümüne bakın.

Örneğin, normal ifade `^[0-9A-Z]([-.\w]*[0-9A-Z])*\$$` deseni en az bir alfasayısal karakterden oluşan bir parça numarasıyla eşleşmek için tasarlanmıştır. Bir ek karakter bir alfasayısal karakter, bir ayırma çizgisi, bir alt çizgi ya da bir nokta olabilir, ancak son karakter alfasayısal olmalıdır. Bir dolar işareti parça numarasını sonlandırır. Bazı durumlarda, niceleyiciler iç içe olduğundan ve alt ifade `[0-9A-Z]` alt ifadenin `[-.\w]*`bir alt kümesi olduğundan, bu normal ifade deseni son derece düşük performans gösterebilir.

Bu durumlarda, yuvalanan miktar niceleyicileri kaldırarak ve dış alt ifadeyi sıfır genişliğinde bir ileriye dönük ya da geriye dönük onay ile değiştirerek normal ifade performansını en iyi hale getireceksiniz. İleriye dönük ve geriye dönük onaylar tutturuculardır; bunlar giriş dizesindeki işaretçiyi kaydırmaz, bunun yerine belirtilen koşulun sağlanıp sağlanmadığını kontrol etmek için ileriye ya da geriye bakar. Örneğin, parça numarası normal ifade olarak `^[0-9A-Z][-.\w]*(?<=[0-9A-Z])\$$`yeniden yazılabilir. Bu normal ifade deseni aşağıdaki tabloda gösterildiği gibi tanımlanmaktadır.

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

.NET'teki normal ifade dili, iç içe bulunan niceleyicileri ortadan kaldırmak için kullanabileceğiniz aşağıdaki dil öğelerini içerir. Daha fazla bilgi için [yapıyı gruplandırma](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md)ya da gruplandırma'ya bakın.

|Dil öğesi|Açıklama|
|----------------------|-----------------|
|`(?=` `subexpression` `)`|Sıfır genişlikli pozitif ileriye yönelik onay. Giriş dizesine uygun olup `subexpression` olmadığını belirlemek için geçerli konumun önüne bakın.|
|`(?!` `subexpression` `)`|Sıfır genişlikli negatif ileriye yönelik onay. Giriş dizesi ile eşleşip `subexpression` eşleşmediğini belirlemek için geçerli konumun önüne bakın.|
|`(?<=` `subexpression` `)`|Sıfır genişlikli pozitif geriye yönelik onay. Giriş dizesine uygun `subexpression` olup olmadığını belirlemek için geçerli konumun arkasına bakın.|
|`(?<!` `subexpression` `)`|Sıfır genişlikli negatif geriye yönelik onay. Giriş dizesinin eşleşip `subexpression` eşleşmediğini belirlemek için geçerli konumun arkasına bakın.|

## <a name="use-time-out-values"></a>Zaman dışarı değerlerini kullanma

Normal ifadeleriniz, normal ifade deseniyle neredeyse eşleşen girişleri işleme alıyorsa, sıkça aşırı geri izlemeye dayanıyor olabilir, bu da performansı önemli ölçüde etkiler. Normal ifadenin yakın eşleme girişine karşı geri izlemesi ve testine ilişkin kullanımınızı dikkatle düşünmeye ek olarak, gerçekleşmesi halinde aşırı geri izleme etkisinin en aza indirilmesini sağlamak için mutlaka bir zaman aşımı değeri belirlemelisiniz.

Normal ifade zaman ayırma aralığı, normal ifade altyapısının zaman dışarı çıkmadan önce tek bir eşleşme arayacağı süreyi tanımlar. Varsayılan zaman zaman aralığı, <xref:System.Text.RegularExpressions.Regex.InfiniteMatchTimeout?displayProperty=nameWithType>normal ifadenin zaman dışarı çıkmayacağı anlamına gelir. Bu değeri geçersiz kılabilir ve zaman aralığını aşağıdaki gibi tanımlayabilirsiniz:

- Oluşturucuyu arayarak bir <xref:System.Text.RegularExpressions.Regex> nesneyi anında aldığınızda bir zaman kaybı değeri sağlayarak. <xref:System.Text.RegularExpressions.Regex.%23ctor%28System.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29?displayProperty=nameWithType>

- Parametre içeren <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29?displayProperty=nameWithType> `matchTimeout` statik desen eşleştirme <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29?displayProperty=nameWithType>yöntemini çağırarak.

- <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> Yöntem çağırılarak oluşturulan düzenli ifadeleri derleyen, türü <xref:System.TimeSpan>bir parametresi olan oluşturucuyu arayarak.

Bir zaman aralığı tanımladıysanız ve bu aralığın sonunda eşleşme bulunamazsa, normal ifade <xref:System.Text.RegularExpressions.RegexMatchTimeoutException> yöntemi bir özel durum oluşturur. Özel durum işleyicinizde, eşlemeyi daha uzun bir zaman aralığı ile yeniden denemeyi, eşleme denemesinden vazgeçip bir eşleme olmadığını varsaymayı ya da eşleme denemesinden vazgeçip özel durum bilgisini gelecekteki analizler için kaydetmeyi seçebilirsiniz.

Aşağıdaki örnek, metin `GetWordData` belgesindeki sözcük teki sözcük sayısını ve ortalama karakter sayısını hesaplamak için normal bir ifadeyi 350 milisaniye aralıkla anında ifade eden bir yöntem tanımlar. Eşleştirme işlemi zaman dilimi dolursa, zaman aralığı 350 milisaniye <xref:System.Text.RegularExpressions.Regex> artırılır ve nesne yeniden anında gerçekleşir. Yeni zaman aşımı aralığı 1 saniyeden uzunsa, yöntem yeniden çağırıcıya özel durum atar.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/timeout1.cs#12)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/timeout1.vb#12)]

## <a name="capture-only-when-necessary"></a>Yalnızca gerektiğinde yakalama

.NET'teki normal ifadeler, normal bir ifade deseni bir veya daha fazla alt ifadede gruplandırmanızı sağlayan bir dizi gruplandırma yapısını destekler. .NET normal ifade dilinde en sık kullanılan gruplandırma yapıları, sayılı yakalama grubunu tanımlayan `(` *alt ifade*`)`ve `(?<`adlandırılmış yakalama grubunu tanımlayan *ad*`>`*alt ifadesidir.*`)` Yapı birimlerini gruplamak geri başvuruları oluşturmak ve bir miktar niceleyicinin uygulandığı bir alt ifade tanımlamak için gereklidir.

Ancak bu dil öğelerinin kullanılmasının bir maliyeti vardır. Bunlar, <xref:System.Text.RegularExpressions.GroupCollection> özellik tarafından <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> döndürülen nesnenin en son adlandırılmış veya adlandırılmış yakalamalarla doldurulmasını neden olurlar ve tek bir gruplama yapısı <xref:System.Text.RegularExpressions.CaptureCollection> giriş dizesinde birden çok alt dize yakalamışsa, belirli bir yakalama grubunun <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> özelliği tarafından döndürülen nesneyi birden çok <xref:System.Text.RegularExpressions.Capture> nesneyle doldururlar.

Genelde oluşturma birimlerini gruplama, miktar niceleyicilerin yalnızca bunlara uygulanacağı şekilde bir normal ifadede kullanılır ve bu alt ifadeler tarafından yakalanan gruplar daha sonra kullanılmaz. Örneğin, normal ifade `\b(\w+[;,]?\s?)+[.?!]` tüm cümlenin tamamını yakalamak için tasarlanmıştır. Aşağıdaki tabloda, bu normal ifade desenindeki dil <xref:System.Text.RegularExpressions.Match> öğeleri <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> ve <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> bunların nesnenin ve koleksiyonları üzerindeki etkileri açıklanmaktadır.

|Desen|Açıklama|
|-------------|-----------------|
|`\b`|Bir sözcük sınırında eşleşmeye başla.|
|`\w+`|Bir veya daha fazla sözcük karakteri eşleştir.|
|`[;,]?`|Sıfır ya da bir virgül ya da noktalı virgülü eşleyin.|
|`\s?`|Sıfır veya bir beyaz boşluk karakterini eşleştirin.|
|`(\w+[;,]?\s?)+`|Arkasından isteğe bağlı bir boşluk karakteri gelen isteğe bağlı bir virgül ya da noktalı virgül tarafından izlenen bir ya da daha fazla sözcük karakterinin bir ya da daha fazla oluşumunu eşleyin. Bu, birkaç sözcük karakteri (yani sözcüğün) ve ardından isteğe bağlı bir noktalama işaretinin, normal ifade altyapısı cümlenin sonuna ulaşıncaya kadar tekrarlanması için gerekli olan ilk tutma grubunu tanımlar.|
|`[.?!]`|Bir nokta, soru işareti ya da ünlem işareti eşleyin.|

Aşağıdaki örnekte de görüldüğü gibi, bir <xref:System.Text.RegularExpressions.GroupCollection> eşleşme <xref:System.Text.RegularExpressions.CaptureCollection> bulunduğunda, hem nesneler hem de nesneler eşleşmeden yakalamalarla doldurulur. Bu durumda, yakalama grubu, `(\w+[;,]?\s?)` `+` niceleyicinin ona uygulanabilmesi için vardır ve bu da normal ifade deseninin bir tümcedeki her sözcüğü eşleştirmesini sağlar. Aksi halde bir cümledeki son sözcüğü eşleyebilir.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/group1.cs#8)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/group1.vb#8)]

Alt ifadeleri yalnızca bunlara niceleyiciler uygulamak için kullanırken ve tutulan metinle ilgilenmediğinizde, grup tutmalarını devre dışı bırakmanız gerekir. Örneğin, `(?:subexpression)` dil öğesi, uygulandığı grubun eşleşen alt dizeleri yakalamasını engeller. Aşağıdaki örnekte, önceki örnekteki normal ifade deseni ' olarak `\b(?:\w+[;,]?\s?)+[.?!]`değiştirilir. Çıktının gösterdiği gibi, normal ifade altyapısının koleksiyonları <xref:System.Text.RegularExpressions.GroupCollection> <xref:System.Text.RegularExpressions.CaptureCollection> doldurmasını engeller.

[!code-csharp[Conceptual.RegularExpressions.BestPractices#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/group2.cs#9)]
[!code-vb[Conceptual.RegularExpressions.BestPractices#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/group2.vb#9)]

Tutmayı, şu yöntemlerden biriyle devre dışı bırakabilirsiniz:

- Dil `(?:subexpression)` öğesini kullanın. Bu öğe, geçerli olduğu gruptaki eşleşen alt dizelerin tutulmasını engeller. Herhangi bir yuvalanmış grupta alt dize yakalamalarını devre dışı bırakmaz.

- <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture> Seçeneği kullanın. Normal ifade deseninde tüm adlandırılmamış ya da örtük yakalamaları devre dışı bırakır. Bu seçeneği kullandığınızda, yalnızca dil öğesiile tanımlanan `(?<name>subexpression)` adlandırılmış grupları eşleştirebilen alt dizeleri yakalanabilir. Bayrak, <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture> `options` bir <xref:System.Text.RegularExpressions.Regex> sınıf oluşturucuparametresine veya statik `options` eşleştirme <xref:System.Text.RegularExpressions.Regex> yönteminin parametresine geçirilebilir.

- Dil `n` öğesindeki `(?imnsx)` seçeneği kullanın. Bu seçenek, tutulan tüm adlandırılmamış veya örtük öğeleri, öğenin normal ifade deseninde ortaya çıktığı noktadan başlayarak devre dışı bırakır. Yakalamalar, desenin sonuna kadar veya `(-n)` seçenek adsız veya örtülü yakalamalara izin gelene kadar devre dışı bırakılır. Daha fazla bilgi için [bkz.](../../../docs/standard/base-types/miscellaneous-constructs-in-regular-expressions.md)

- Dil `n` öğesindeki `(?imnsx:subexpression)` seçeneği kullanın. Bu seçenek, `subexpression`tüm adsız veya örtülü yakalamaları devre dışı kılabilir. Yakalamalar adlandırılmamış ya da örtük yuvalı yakalama grupları tarafından devre dışı bırakılır.

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Normal İfade Davranışının Ayrıntıları](../../../docs/standard/base-types/details-of-regular-expression-behavior.md)|.NET'te normal ifade altyapısının uygulanmasını inceler. Konu normal ifadelerin esnekliği üzerine yoğunlaşmakta ve geliştiricinin normal ifade altyapısının verimli ve sorunsuz çalışmasını sağlamadaki sorumluluğunu açıklamaktadır.|
|[Geri Dönüş](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)|Geri izlemenin ne olduğunu ve bunun normal ifade performansını nasıl etkilediği açıklar ve geri izlemeye alternatifler sağlayan dil öğelerini inceler.|
|[Normal İfade Dili - Hızlı Başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)|.NET'teki normal ifade dilinin öğelerini açıklar ve her dil öğesi için ayrıntılı belgelere bağlantılar sağlar.|
