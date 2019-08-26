---
title: .NET 'teki normal Ifadeler için en iyi uygulamalar
description: .NET ' te verimli, etkili normal ifadeler oluşturmayı öğrenin.
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
ms.openlocfilehash: 8d887bb32d1bdd398353d00aba16c2cc8adfcacb
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988820"
---
# <a name="best-practices-for-regular-expressions-in-net"></a>.NET 'teki normal Ifadeler için en iyi uygulamalar
<a name="top"></a>.NET 'teki normal ifade altyapısı, metni karşılaştırma ve eşleştirme yerine, metin işleme ve eşleme yapmak yerine, metni işleyen güçlü, tam özellikli bir araçtır. Çoğu durumda desen eşleme işlemini hızlı ve verimli şekilde yapar. Ancak bazı durumlarda normal ifade motoru çok yavaş görünebilir. Aşırı durumlarda saatler ve hatta günler boyunca görece küçük bir girişi işlerken yanıt vermeyi durdurmuş gibi bile görünebilir.  
  
 Bu konu, normal ifadelerinin en iyi performansa ulaşabilmesi için geliştiricilerin benimseyebileceği en iyi yöntemlerden bazılarını özetlemektedir. Aşağıdaki bölümleri içerir:  
  
- [Giriş kaynağını göz önünde bulundurun](#InputSource)  
  
- [Nesne örneğini oluşturmayı uygun şekilde işleyin](#ObjectInstantiation)  
  
- [Geri Izleme için ücret alın](#Backtracking)  
  
- [Zaman aşımı değerlerini kullanma](#Timeouts)  
  
- [Yalnızca gerekli olduğunda yakala](#Capture)  
  
- [İlgili konular](#RelatedTopics)  
  
<a name="InputSource"></a>   
## <a name="consider-the-input-source"></a>Giriş Kaynağını düşünün  
 Genelde normal ifadeler iki tür giriş kabul edebilir: sınırlandırılmış ya da sınırlandırılmamış. Kısıtlı giriş, bilinen ya da güvenilir bir kaynaktan geldiği bilinen ve ön tanımlı bir biçim izleyen metindir. Sınırlandırılmamış girdi, bir web kullanıcısı gibi güvenilir olmayan bir kaynaktan gelen ve önceden tanımlı veya beklenen bir biçime uymayabilecek bir metindir.  
  
 Normal ifade desenleri genelde geçerli girişi eşlemek için yazılır. Diğer bir deyişle, geliştiriciler eşleştirmek istedikleri metni inceler ve bu metinle eşleşen normal bir ifade deseni yazarlar. Geliştiriciler daha sonra bu desenin düzeltme ya da daha fazla ayrıntı gerektirip gerektirmediğini, birden çok geçerli giriş öğesini test ederek belirler. Desen gereçli olduğu kabul edilen tüm girdilerle eşleştiğinde, üretime hazır kabul edilir ve çıkacak uygulamaya dahil edilebilir. Bu, normal bir ifade desenini, kısıtlanmış girdiyle eşleşme için uygun hale getirir. Ancak sınırlandırılmamış girişin eşlenmesi uygun hale getirmez.  
  
 Sınırlandırılmamış girdide eşlemek yapmak için, normal bir ifade üç tür metni verimli olarak işleyebilmelidir:  
  
- Normal ifade deseniyle eşleşen metin.  
  
- Normal ifade deseniyle eşleşmeyen metin.  
  
- Normal ifade deseniyle neredeyse eşleşen metin.  
  
 Son metin türü, sınırlandırılmış girdi işlemek üzere yazılmış bir normal ifade için özellikle sorunludur. Bu normal ifade Ayrıca kapsamlı [geri izleme](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)özelliği de kullanıyorsa, normal ifade altyapısı, görünen bir süre (bazı durumlarda, birkaç saat veya gün), görünüşzararsız metnini işleme harcayabilir.  
  
> [!WARNING]
> Aşağıdaki örnek, aşırı miktarda geri dönüş kullanma eğiliminde olan ve geçerli e-posta adreslerini reddetmesi olası bir normal ifadeyi kullanmaktadır. Bir e-posta doğrulama yordamında kullanmamalısınız. E-posta adreslerini doğrulayan bir normal ifade isterseniz, bkz [. nasıl yapılır: Dizelerin geçerli e-posta biçiminde](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md)olduğunu doğrulayın.  
  
 Örneğin bir e-posta adresinin takma adını onaylamak için çok yaygın kullanılan ama son derece sorunlu normal ifade düşünün. Normal ifade `^[0-9A-Z]([-.\w]*[0-9A-Z])*$` , alfasayısal bir karakterden oluşan ve sonra alfasayısal, nokta veya kısa çizgi olabilen sıfır veya daha fazla karakterle oluşan geçerli bir e-posta adresi olarak değerlendirilme işlemini işleyecek şekilde yazılmıştır. Normal ifade, alfasayısal bir karakterle bitmelidir. Ancak aşağıdaki örnekte gösterildiği gibi, bu normal ifade geçerli girişi kolayca yönetmesine rağmen performansı neredeyse geçerli girişi işlerken çok yetersizdir.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/design2.cs#1)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/design2.vb#1)]  
  
 Örneğin çıktısında gösterildiği üzere normal ifade motoru geçerli e-posta takma adlarını, uzunluğundan bağımsız olarak yaklaşık aynı zaman aralığında işler. Diğer taraftan, yakın geçerli e-posta adresi beşten fazla karakter içeriyorsa, işlem zamanı dizedeki ek her karakter için yaklaşık iki kat olacaktır. Bunun anlamı, neredeyse geçerli 28-karakter dizesi işlemek için bir saatten fazla götürecek ve neredeyse geçerli 33-karakter dizesi işlemek için neredeyse bir gün sürecektir.  
  
 Bu düzenli ifade yalnızca eşlenecek girişin biçimi düşünülerek geliştirildiğinden desen ile eşleşmeyen girişi hesaba katamaz. Bu da normal ifade deseniyle neredeyse eşleşen sınırlandırılmamış girdinin performansı önemli ölçüde düşürmesine neden olabilir.  
  
 Bu sorunu çözmek için, şunları yapabilirsiniz:  
  
- Bir desen geliştirirken, özellikle de normal ifadeniz sınırlandırılmamış girdiyi işlemek üzere tasarlandıysa, geri dönüşün normal ifade altyapısının performansını nasıl etkileyeceğini düşünmelisiniz. Daha fazla bilgi için [geri Izlemeyi alma](#Backtracking) bölümüne bakın.  
  
- Normal ifadenizi geçerli girdilerin yanı sıra gereçsiz ve neredeyse geçerli girdiler de kullanarak baştan aşağı test edin. Belirli bir normal ifadeye yönelik girişi rastgele oluşturmak için, Microsoft Research 'tan normal ifade araştırma aracı olan [Rex](https://www.microsoft.com/en-us/research/project/rex-regular-expression-exploration/)'i kullanabilirsiniz.  
  
 [Başa dön](#top)  
  
<a name="ObjectInstantiation"></a>   
## <a name="handle-object-instantiation-appropriately"></a>Nesne Örneklemesini Uygun Şekilde Yönetme  
 . NET ' in normal ifade nesne modeli <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> , normal ifade altyapısını temsil eden sınıftır. Genellikle, normal ifade performansını etkileyen tek en büyük faktör, <xref:System.Text.RegularExpressions.Regex> altyapının kullanıldığı yoldur. Normal bir ifadeyi tanımlama, normal ifade motorunu bir normal ifade deseni ile sıkı şekilde eşlemeyi içerir. Bu, oluşturucusunu bir normal ifade deseninin geçişine veya <xref:System.Text.RegularExpressions.Regex> bir statik yöntemi çağırarak bir nesnenin örneğini oluşturma işleminin, çözümlenecek dizeyle birlikte zorunludur a pahalı bir.  
  
> [!NOTE]
> Yorumlanan ve derlenmiş normal ifadelerin kullanımıyla ilgili performans etkilerine ilişkin daha ayrıntılı bir açıklama için bkz [. normal ifade performansını iyileştirme, Bölüm II: BCL ekibi bloguna geri](https://blogs.msdn.microsoft.com/bclteam/2010/08/03/optimizing-regular-expression-performance-part-ii-taking-charge-of-backtracking-ron-petrusha/) izleme alma.  
  
 Normal ifade altyapısını belirli bir normal ifade deseniyle birleştirebilir, sonra altyapıyı birkaç şekilde metin eşlemesi yapmak üzere kullanabilirsiniz:  
  
- Gibi bir statik kalıp eşleme yöntemini <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%29?displayProperty=nameWithType>çağırabilirsiniz. Bu, bir normal ifade nesnesine öndeğer atanmasını gerektirmez.  
  
- Bir <xref:System.Text.RegularExpressions.Regex> nesne örneği oluşturabilir ve yorumlanan bir normal ifadenin örnek örüntü eşleme yöntemini çağırabilirsiniz. Bu, normal ifade altyapısını bir normal ifade desenine bağlamak için varsayılan yöntemdir. Bir <xref:System.Text.RegularExpressions.Regex> nesne, <xref:System.Text.RegularExpressions.RegexOptions.Compiled> bayrağını içeren bir `options` bağımsız değişken olmadan oluşturulduğunda oluşur.  
  
- Bir <xref:System.Text.RegularExpressions.Regex> nesne örneği oluşturabilir ve derlenmiş bir normal ifadenin örnek desenler eşleme yöntemini çağırabilirsiniz. Normal ifade nesneleri, <xref:System.Text.RegularExpressions.Regex> <xref:System.Text.RegularExpressions.RegexOptions.Compiled> bayrağını içeren bir `options` bağımsız değişkenle bir nesne örneği oluşturulduğunda derlenmiş desenleri temsil eder.  
  
- Belirli bir normal ifade düzeniyle sıkı bir <xref:System.Text.RegularExpressions.Regex> şekilde bağlanmış özel amaçlı bir nesne oluşturabilir, derleyebilir ve tek başına bir derlemeye kaydedebilirsiniz. Bunu <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> yöntemini çağırarak yapabilirsiniz.  
  
 Normal ifade eşleme yöntemlerini çağırma biçiminizin uygulamanız üzerinde önemli bir etkisi olabilir. Aşağıdaki bölümler, uygulamanızın performansını iyileştirmek için statik yöntem çağrılarının, yorumlanan normal ifadelerin ve derlenmiş normal ifadelerin ne zaman kullanılacağını tartışmaktadır.  
  
> [!IMPORTANT]
> Yöntem çağrılarında aynı normal ifade tekrar tekrar kullanılıyorsa veya uygulama normal ifade nesnelerini yoğun olarak kullanıyorsa, yöntem çağrısının biçimi (statik, yorumlanan, derlenmiş) performansı etkiler.  
  
### <a name="static-regular-expressions"></a>Statik Normal İfadeler  
 Statik normal ifade yöntemleri, bir normal ifade nesnesine aynı normal ifadeyi tekrar tekrar ön değer olarak atamaya alternatif olarak önerilir. Normal ifade nesneleri tarafından kullanılan normal ifade desenlerinden farklı olarak örnek yöntemi çağrılarında kullanılan desenlerin işlem kodları veya derlenmiş Microsoft ara dili (MSIL), normal ifade motoru tarafından dahili olarak önbelleğe alınır.  
  
 Örneğin bir olay işleyicisi, kullanıcı girişini onaylamak için sık sık başka bir yöntem çağırır. Bu, bir <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Click> denetimin olayının adlı `IsValidCurrency`bir yöntemi çağırmak için kullanıldığı, bu, kullanıcının bir para birimi simgesi ve ardından en az bir ondalık basamak yazıp girmediğini denetleyen aşağıdaki kodda yansıtılır.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/static1.cs#2)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/static1.vb#2)]  
  
 `IsValidCurrency` Yönteminin çok verimsiz bir uygulanması aşağıdaki örnekte gösterilmiştir. Her yöntem çağrısının aynı düzene sahip bir <xref:System.Text.RegularExpressions.Regex> nesneyi yeniden örnekdiğini unutmayın. Bu ise normal ifade deseninin yöntem her çağrıldığında tekrar derlenmesi gerektiği anlamına gelir.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/static1.cs#3)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/static1.vb#3)]  
  
 Bu verimsiz kodu statik <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> yöntem çağrısıyla değiştirmelisiniz. Bu, her bir model eşleme yöntemini <xref:System.Text.RegularExpressions.Regex> her çağırmak istediğinizde bir nesne örneği oluşturma gereksinimini ortadan kaldırır ve normal ifade altyapısının, normal ifadenin derlenmiş bir sürümünü önbelleğinden almasını sağlar.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/static2.cs#4)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/static2.vb#4)]  
  
 Varsayılan olarak, en son kullanılan 15 statik normal ifade deseni önbelleğe alınır. Daha fazla sayıda önbelleğe alınmış statik normal ifade gerektiren uygulamalarda, önbellek boyutu <xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=nameWithType> özelliği ayarlanarak ayarlanabilir.  
  
 Bu örnekte kullanılan `\p{Sc}+\s*\d+` normal ifade, giriş dizesinin bir para birimi simgesinden ve en az bir ondalık basamağından oluştuğunu doğrular. Desen aşağıdaki tabloda gösterildiği gibi tanımlanır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\p{Sc}+`|Unicode Sembolü, Para Birimi kategorisinde bir ya da daha fazla karakter eşleyin.|  
|`\s*`|Sıfır veya daha fazla boşluk karakteriyle eşleş.|  
|`\d+`|Bir veya daha fazla ondalık basamağı eşleştirin.|  
  
<a name="Interpreted"></a>   
### <a name="interpreted-vs-compiled-regular-expressions"></a>Yorumlanan vs. Derlenmiş normal Ifadeler  
 Normal ifade motoruna <xref:System.Text.RegularExpressions.RegexOptions.Compiled> seçeneğinin belirtimi aracılığıyla bağlanmamış olan normal ifade desenleri yorumlanır. Bir normal ifade nesnesi örneği oluşturulduğunda, normal ifade altyapısı normal ifadeyi bir dizi işlem koduna dönüştürür. Bir örnek yöntemi çağrıldığında, işlem kodları MSIL'ye dönüştürülür ve JIT derleyicisi tarafından yürütülür. Benzer şekilde, statik bir normal ifade yöntemi çağrıldığı ve normal ifade önbellekte bulunamadığı zaman, normal ifade altyapısı normal ifadeyi bir dizi işlem koduna dönüştürür ve bunları önbellekte depolar. Daha sonra işlem kodlarını MSIL'ye dönüştürür, bu sayede JIT derleyicisi bunları yürütebilir. Yorumlanmış normal ifadeler, daha yavaş yürütme sürelerine karşın açılış süresini azaltır. Bundan dolayı bunlar, normal ifade az sayıda yöntem çağrısında kullanıldığında ya da normal ifade yöntemine yapılan kesin çağrı sayısı bilinmiyor ancak küçük olması bekleniyorsa en iyi şekilde kullanılır. Yöntem çağrıları arttıkça performans kazancı daha az başlangıç saatinden sayısı daha yavaş yürütme hızını outstripped gibi.  
  
 Normal ifade motoruna <xref:System.Text.RegularExpressions.RegexOptions.Compiled> seçeneğinin belirtimi aracılığıyla bağlanan normal ifade desenleri derlenir. Bu, bir normal ifade nesnesi örneği oluşturulduğunda veya statik bir normal ifade yöntemi çağrıldığında ve normal ifade önbellekte bulunamadığında, normal ifade altyapısının normal ifadeyi ara bir işlem kodu kümesine, sonra da bunu MSIL'ye dönüştürdüğü anlamına gelir. Bir yöntem çağrıldığında, JIT derleyici MSIL'yi yürütür. Yorumlanmış normal ifadelerin aksine, derlenmiş normal ifadeler açılış süresini artırır ancak ayrı desen eşleme yöntemlerini daha hızlı yürütür. Sonuç olarak normal ifade derlemekten kaynaklanan sonuçlardan yararlanan performans çağrılan normal ifade yöntemlerinin sayısı oranında artar.  
  
 Özetlemek gerekirse, normal ifade yöntemlerini belirli bir normal ifadeyle nispeten ender olarak çağırıyorsanız, yorumlanan normal ifadeler kullanmanızı öneririz. Normal ifade yöntemlerinizi oldukça sık olarak belirli bir normal ifadeyle çağırıyorsanız, derlenmiş normal ifadeler kullanmalısınız. Yorumlanan normal ifadelerin yürütülme hızlarındaki yavaşlığın bunların başlama süresinin kısa olmasından elde edilen avantajı ortadan kaldırmaya başladığı eşiği veya derlenmiş normal ifadelerin başlama süresinin uzunluğunun bunların yürütülme hızından elde edilen avantajı ortadan kaldırmaya başladığı eşiği belirlemek güçtür. Normal ifadenin karmaşıklığı ve bunun işlediği özel veri gibi çeşitli faktörlere bağlıdır. Yorumlanan veya derlenmiş normal ifadelerin, belirli uygulama senaryonuz için en iyi performansı sunmadığını öğrenmek için, bu <xref:System.Diagnostics.Stopwatch> sınıfı, yürütme sürelerini karşılaştırmak için kullanabilirsiniz.  
  
 Aşağıdaki örnek, ilk on cümleleri okurken ve Theodore Dreiser 'ın *Mali*metninde bulunan tüm tümceleri okurken derlenen ve yorumlanan normal ifadelerin performansını karşılaştırır. Örneğin çıktısında gösterildiği üzere normal ifade eşleme yöntemlerine yalnızca on çağrı yapıldığında, yorumlanan bir normal ifade derlenmiş bir normal ifadeden daha iyi performans sergiler. Ancak derlenmiş bir normal ifade, daha fazla sayıda çağrı yapıldığında (bu örnekte 13.000'den fazla) daha iyi performans gösterir.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/compare1.cs#5)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/compare1.vb#5)]  
  
 Örnekte `\b(\w+((\r?\n)|,?\s))*\w+[.?:;!]`kullanılan normal ifade deseninin, aşağıdaki tabloda gösterildiği gibi tanımlanmıştır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`\w+`|Bir veya daha fazla sözcük karakteri eşleştir.|  
|<code>(\r?\n)&#124;,?\s)</code>|Arkasından bir yeni satır karakteri gelen sıfır ya da bir satır başı veya arkasından bir boşluk karakteri gelen sıfır ya da bir virgül eşleyin.|  
|<code>(\w+((\r?\n)&#124;,?\s))*</code>|Arkasından sıfır ya da bir satır başı ve bir yeni satır karakteri veya sıfır ya da bir virgül ve sonra boşluk karakteri gelen bir ya da daha fazla sözcük karakterinin sıfır ya da daha fazla oluşumunu eşleyin.|  
|`\w+`|Bir veya daha fazla sözcük karakteri eşleştir.|  
|`[.?:;!]`|Bir nokta, soru işareti, iki nokta üst üste, noktalı virgül ya da ünlem işareti eşleyin.|  
  
### <a name="regular-expressions-compiled-to-an-assembly"></a>Normal Ifadeler: Derleme için derlenmiş  
 .NET ayrıca derlenmiş normal ifadeler içeren bir derleme oluşturmanıza olanak sağlar. Bu, normal ifade derlemesinin uğradığı performans düşüşünü çalışma zamanından tasarım zamanına taşır. Bununla birlikte, ek iş de içerir: Normal ifadeleri önceden tanımlamanız ve bunları bir derlemeye derlemeniz gerekir. Derleyici daha sonra, derlemenin normal ifadelerini kullanan kaynak kodunu derlerken bu derlemeye başvurabilir. Derlemedeki her derlenmiş normal ifade, öğesinden <xref:System.Text.RegularExpressions.Regex>türetilen bir sınıf tarafından temsil edilir.  
  
 Normal ifadeleri bir derlemeye derlemek için, <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%28System.Text.RegularExpressions.RegexCompilationInfo%5B%5D%2CSystem.Reflection.AssemblyName%29?displayProperty=nameWithType> yöntemini çağırır ve bunu derlenecek normal ifadeleri temsil eden bir nesne <xref:System.Text.RegularExpressions.RegexCompilationInfo> dizisi ve derleme hakkında bilgi içeren bir nesne <xref:System.Reflection.AssemblyName> yaratıl.  
  
 Aşağıdaki durumlarda normal ifadeleri bütünleşik bir dosyaya derlemenizi öneririz:  
  
- Yeniden kullanılabilir normal ifadeler üretmek isteyen yetkin bir geliştiriciyseniz.  
  
- Normal ifadenizin desen eşleme yöntemlerinizin belirsiz kere (bir ya da iki kezden binlerce ya da on binlerce defa) çağrılmasını bekliyorsanız. Derlenmiş veya yorumlanan normal ifadelerden farklı olarak, ayrı derlemelere derlenen normal ifadeler, yöntem çağrısı sayısından bağımsız olarak tutarlı bir performans sunar.  
  
 Performansı en iyi hale getirmek için derlenmiş normal ifadeler kullanıyorsanız, derlemeyi oluşturmak, normal ifade motorunu yüklemek ve bunun desen eşleyen yöntemlerini yürütmek için yansıtma kullanmamanız gerekir. Bu, normal ifade desenlerini dinamik olarak oluşturmaktan kaçınmanızı ve desen eşleme seçeneklerini (örneğin harf büyüklüğüne duyarlı eşleme) derleme oluşturulurken belirtmenizi gerekli kılar. Ayrıca derlemeyi, normal ifadeyi kullanan koddan oluşturan kodu ayırmanızı gerektirir.  
  
 Aşağıdaki örnek, derlenmiş bir normal ifade içeren bir derlemenin nasıl oluşturulacağını göstermektedir. Yorumlanan vs 'de kullanılan cümle `RegexLib.dll` ile eşleşen normal `SentencePattern`ifade deseninin bulunduğu tek bir normal ifade sınıfıyla adlı bir derleme oluşturur. [ Derlenmiş normal ifadeler](#Interpreted) bölümü.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/compile1.cs#6)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/compile1.vb#6)]  
  
 Örnek bir yürütülebilir dosyaya derlenirse ve çalıştırıldığında adlı `RegexLib.dll`bir derleme oluşturur. Normal ifade, öğesinden `Utilities.RegularExpressions.SentencePattern` <xref:System.Text.RegularExpressions.Regex>türetilmiş adlı bir sınıf tarafından temsil edilir. Aşağıdaki örnek daha sonra derlenmiş normal ifadeyi kullanarak Theodore Dreiser 'ın *Finano*'nun metindeki tümceleri ayıklar.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/compile2.cs#7)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/compile2.vb#7)]  
  
 [Başa dön](#top)  
  
<a name="Backtracking"></a>   
## <a name="take-charge-of-backtracking"></a>Geriye Dönüşü Denetimini El Alma  
 Sıradan şekilde, normal ifade motoru bir giriş dizsi içinde ilerlemek ve bunu bir normal ifade deseni ile karşılaştırmak için doğrusal ilerlemeyi kullanır. Ancak,, ve `*` `?` gibi belirsiz nicelik `+`belirteçleri normal ifade düzeninde kullanıldığında, normal ifade motoru başarılı kısmi eşleşmelerin bir kısmını verebilir ve daha önce kaydedilen bir duruma geri dönebilir tüm düzen için başarılı bir eşleşme aramak amacıyla. Bu işlem geri dönüş olarak bilinir.  
  
> [!NOTE]
> Geri izleme hakkında daha fazla bilgi için bkz. [normal Ifade davranışı](../../../docs/standard/base-types/details-of-regular-expression-behavior.md) ve [geri izleme](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)ayrıntıları. Geri izlemenin ayrıntılı bir açıklaması için bkz [. normal ifade performansını iyileştirme, Bölüm II: BCL ekibi bloguna geri](https://blogs.msdn.microsoft.com/bclteam/2010/08/03/optimizing-regular-expression-performance-part-ii-taking-charge-of-backtracking-ron-petrusha/) izleme alma.  
  
 Geri dönüş için destek, normal ifadelere güç ve esneklik kazandırır. Ayrıca normal ifade motorunun çalışmasının denetlenmesini sorumluluğunu normal ifade geliştiricisine teslim eder. Geliştiriciler genelde bu sorumluluğun farkında olmadığından, geri dönüşü yanlış kullanmaları ya da aşırı geri dönüşe bağımlılıkları genelde normal ifade performansının düşmesinde önemli bir rol oynar. En kötü senaryoda yürütme süresi girdi dizesinde her ek karakter ile iki katına çıkar. Aslında geri izlemeyi aşırı şekilde kullanarak, girişin normal ifade desenini yakın eşlemesi halinde sonsuz bir döngünün program eşdeğerini oluşturmak kolaydır; normal ifade motorunun görece kısa bir giriş dizesini işlemesi saatler ve hatta günler alabilir.  
  
 Genelde, geri izlemenin bir eşleme için gerekli olmadığı gerçeğine rağmen uygulamalar geri izleme kullandıkları için bir ceza öder. Örneğin, normal ifade `\b\p{Lu}\w*\b` , aşağıdaki tabloda gösterildiği gibi, büyük bir karakterle başlayan tüm sözcüklerle eşleşir.  
  
|Desen|Açıklama|  
|-|-|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`\p{Lu}`|Bir büyük harfli karakter eşleyin.|  
|`\w*`|Sıfır veya daha fazla sözcük karakteriyle eşleş.|  
|`\b`|Eşlemeyi bir sözcük sınırında sonlandır.|  
  
 Bir kelime sınırı bir kelime karakteri ile aynı ya da bunu bir alt kümesi olmadığından, normal ifade motorunun kelime karakterlerini eşlerken bir kelime sınırı geçirmesi mümkün değildir. Bunun anlamı şudur: bu normal ifadede geri dönüş, herhangi bir eşleşmenin genel başarısına hiçbir zaman katkıda bulunamaz; olsa olsa performansı düşürebilir, çünkü normal ifade altyapısı başarılı her sözcük karakteri eşleşmesindeki durumunu kaydetmeye zorlanır.  
  
 Geri izlemenin gerekli olmadığını belirlerseniz, `(?>subexpression)` dil öğesini kullanarak bunu devre dışı bırakabilirsiniz. Aşağıdaki örnek, bir girdi dizesini iki normal ifade kullanarak ayrıştırmaktadır. İlki `\b\p{Lu}\w*\b`, geri izlemeyi temel alır. İkincisi `\b\p{Lu}(?>\w*)\b`, geri izlemeyi devre dışı bırakır. Örneğin çıktısında gösterildiği üzere bunların her ikisi de aynı sonucu üretir.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/backtrack2.cs#10)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/backtrack2.vb#10)]  
  
 Birçok durumda, geri izleme bir normal ifade desenini giriş metnine eşlemek için gereklidir. Ancak aşırı geri izleme performansı ciddi şekilde azaltabilir ve uygulamanın yanıt vermediği izlenimine yol açabilir. Bu durum, özellikle, miktar niceleyiciler yuvalandığında ve metin dış alt ifadeyle eşleşen metin, dış alt ifadeyle eşleşen metnin bir alt kümesi olduğunda gerçekleşir.  
  
> [!WARNING]
> Aşırı geri izlemeyi önlemeye ek olarak, aşırı geri izlemenin normal ifade performansını ciddi şekilde bozmayacağından emin olmak için zaman aşımı özelliğini de kullanmalısınız. Daha fazla bilgi için bkz. [zaman aşımı değerlerini kullanma](#Timeouts) bölümü.  
  
 Örneğin, normal ifade deseninin `^[0-9A-Z]([-.\w]*[0-9A-Z])*\$$` en az bir alfasayısal karakterden oluşan bir bölüm numarasıyla eşleşmesi amaçlanmıştır. Bir ek karakter bir alfasayısal karakter, bir ayırma çizgisi, bir alt çizgi ya da bir nokta olabilir, ancak son karakter alfasayısal olmalıdır. Bir dolar işareti parça numarasını sonlandırır. Bazı durumlarda, bu normal ifade, nicelik belirteçleri iç içe yerleştirilmiş olduğundan ve alt ifade `[0-9A-Z]` alt ifadenin bir alt kümesi `[-.\w]*`olduğundan, bu normal ifade deseninin son derece kötü performans sergilemesinde.  
  
 Bu durumlarda, yuvalanan miktar niceleyicileri kaldırarak ve dış alt ifadeyi sıfır genişliğinde bir ileriye dönük ya da geriye dönük onay ile değiştirerek normal ifade performansını en iyi hale getireceksiniz. İleriye dönük ve geriye dönük onaylar tutturuculardır; bunlar giriş dizesindeki işaretçiyi kaydırmaz, bunun yerine belirtilen koşulun sağlanıp sağlanmadığını kontrol etmek için ileriye ya da geriye bakar. Örneğin, bölüm numarası normal ifadesi olarak `^[0-9A-Z][-.\w]*(?<=[0-9A-Z])\$$`yeniden yazılabilir. Bu normal ifade deseni aşağıdaki tabloda gösterildiği gibi tanımlanmaktadır.  
  
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
  
 .NET 'teki normal ifade dili, iç içe nicelik belirteçleri ortadan kaldırmak için kullanabileceğiniz aşağıdaki dil öğelerini içerir. Daha fazla bilgi için bkz. [Gruplandırma Yapıları](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
|Dil öğesi|Açıklama|  
|----------------------|-----------------|  
|`(?=` `subexpression` `)`|Sıfır genişlikli pozitif ileriye yönelik onay. Giriş dizesiyle `subexpression` eşleşip eşleşmediğini öğrenmek için geçerli konumun önüne bakın.|  
|`(?!` `subexpression` `)`|Sıfır genişlikli negatif ileriye yönelik onay. Giriş dizesiyle eşleşip engellenmeyeceğini `subexpression` öğrenmek için geçerli konumun önüne bakın.|  
|`(?<=` `subexpression` `)`|Sıfır genişlikli pozitif geriye yönelik onay. Giriş dizesiyle `subexpression` eşleşip eşleşmediğini öğrenmek için geçerli konumun arkasına bakın.|  
|`(?<!` `subexpression` `)`|Sıfır genişlikli negatif geriye yönelik onay. Giriş dizesiyle eşleşip engellenmeyeceğini `subexpression` öğrenmek için geçerli konumun arkasına bakın.|  
  
 [Başa dön](#top)  
  
<a name="Timeouts"></a>   
## <a name="use-time-out-values"></a>Zaman Aşımı Değerlerini Kullanma  
 Normal ifadeleriniz, normal ifade deseniyle neredeyse eşleşen girişleri işleme alıyorsa, sıkça aşırı geri izlemeye dayanıyor olabilir, bu da performansı önemli ölçüde etkiler. Normal ifadenin yakın eşleme girişine karşı geri izlemesi ve testine ilişkin kullanımınızı dikkatle düşünmeye ek olarak, gerçekleşmesi halinde aşırı geri izleme etkisinin en aza indirilmesini sağlamak için mutlaka bir zaman aşımı değeri belirlemelisiniz.  
  
 Normal ifade zaman aşımı aralığı, normal ifade altyapısının zaman aşımına uğramadan önce tek bir eşleşen arayacağı süreyi tanımlar. Varsayılan zaman aşımı aralığı olur <xref:System.Text.RegularExpressions.Regex.InfiniteMatchTimeout?displayProperty=nameWithType>, yani normal ifade zaman aşımına uğrar. Aşağıdaki şekilde bu değeri geçersiz kılabilir ve bir zaman aşımı aralığı tanımlayabilirsiniz:  
  
- Oluşturucuyu çağırarak bir <xref:System.Text.RegularExpressions.Regex> nesneyi örneklediğinizde bir zaman aşımı değeri sağlar. <xref:System.Text.RegularExpressions.Regex.%23ctor%28System.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29?displayProperty=nameWithType>  
  
- Bir <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%2CSystem.TimeSpan%29?displayProperty=nameWithType> parametresiiçeren,veyagibibirstatikmodeleşleştirmeyönteminiçağırarak.`matchTimeout`  
  
- <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> Yöntemi çağırarak oluşturulan derlenmiş normal ifadeler için türünde <xref:System.TimeSpan>bir parametreye sahip Oluşturucu çağırarak.  
  
 Bir zaman aşımı aralığı tanımladıysanız ve bu aralığın sonunda bir eşleşme bulunamazsa, normal ifade yöntemi bir <xref:System.Text.RegularExpressions.RegexMatchTimeoutException> özel durum oluşturur. Özel durum işleyicinizde, eşlemeyi daha uzun bir zaman aralığı ile yeniden denemeyi, eşleme denemesinden vazgeçip bir eşleme olmadığını varsaymayı ya da eşleme denemesinden vazgeçip özel durum bilgisini gelecekteki analizler için kaydetmeyi seçebilirsiniz.  
  
 Aşağıdaki örnek, bir metin `GetWordData` belgesindeki sözcük sayısını ve ortalama karakter sayısını hesaplamak için 350 milisaniyelik zaman aşımı aralığı ile düzenli bir ifade sunan bir yöntemi tanımlar. Eşleştirme işlemi zaman aşımına uğrarsa, zaman aşımı aralığı 350 milisaniyelik artar ve <xref:System.Text.RegularExpressions.Regex> nesne yeniden oluşturulur. Yeni zaman aşımı aralığı 1 saniyeden uzunsa, yöntem yeniden çağırıcıya özel durum atar.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/timeout1.cs#12)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/timeout1.vb#12)]  
  
 [Başa dön](#top)  
  
<a name="Capture"></a>   
## <a name="capture-only-when-necessary"></a>Yalnızca Gerekli Olduğunda Yakala  
 .NET 'teki normal ifadeler bir veya daha fazla alt ifadeye normal ifade deseninin gruplandırılmasına olanak sağlayan bir dizi gruplama yapısını destekler. .Net normal ifade dilinde en yaygın olarak kullanılan gruplandırma yapıları, numaralandırılmış `(`bir yakalama grubunu ve `(?<` *ad*`>`alt ifadesini tanımlayan alt *ifade*`)`' dir., adlandırılmış bir yakalama grubunu tanımlar. `)` Yapı birimlerini gruplamak geri başvuruları oluşturmak ve bir miktar niteleyicinin uygulandığı bir alt ifade tanımlamak için gereklidir.  
  
 Ancak bu dil öğelerinin kullanılmasının bir maliyeti vardır. Bu, <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> özelliğin <xref:System.Text.RegularExpressions.GroupCollection> döndürdüğü nesnenin en son adlandırılmamış veya adlandırılmış yakalamalarla doldurulmasına neden olur ve tek bir gruplama yapısı giriş dizesinde birden çok alt dizeyi yakalamışsa, ayrıca <xref:System.Text.RegularExpressions.CaptureCollection>birden çok <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> nesneiçerenbelirlibiryakalamagrubununözelliğitarafındandöndürülennesne.<xref:System.Text.RegularExpressions.Capture>  
  
 Genelde oluşturma birimlerini gruplama, miktar niceleyicilerin yalnızca bunlara uygulanacağı şekilde bir normal ifadede kullanılır ve bu alt ifadeler tarafından yakalanan gruplar daha sonra kullanılmaz. Örneğin, normal ifade `\b(\w+[;,]?\s?)+[.?!]` bir tümcenin tamamını yakalamak için tasarlanmıştır. Aşağıdaki tabloda, bu normal ifade deseninin dil öğeleri ve bunların <xref:System.Text.RegularExpressions.Match> <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> nesne ve <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> koleksiyonları üzerindeki etkileri açıklanmaktadır.  
  
|Desen|Açıklama|  
|-------------|-----------------|  
|`\b`|Bir sözcük sınırında eşleşmeye başla.|  
|`\w+`|Bir veya daha fazla sözcük karakteri eşleştir.|  
|`[;,]?`|Sıfır ya da bir virgül ya da noktalı virgülü eşleyin.|  
|`\s?`|Sıfır veya bir beyaz boşluk karakterini eşleştirin.|  
|`(\w+[;,]?\s?)+`|Arkasından isteğe bağlı bir boşluk karakteri gelen isteğe bağlı bir virgül ya da noktalı virgül tarafından izlenen bir ya da daha fazla sözcük karakterinin bir ya da daha fazla oluşumunu eşleyin. Bu, birkaç sözcük karakteri (yani sözcüğün) ve ardından isteğe bağlı bir noktalama işaretinin, normal ifade altyapısı cümlenin sonuna ulaşıncaya kadar tekrarlanması için gerekli olan ilk tutma grubunu tanımlar.|  
|`[.?!]`|Bir nokta, soru işareti ya da ünlem işareti eşleyin.|  
  
 Aşağıdaki örnekte gösterildiği gibi, bir eşleşme bulunduğunda, hem <xref:System.Text.RegularExpressions.GroupCollection> hem <xref:System.Text.RegularExpressions.CaptureCollection> de nesneleri eşleşenlerin yakalamalarla doldurulur. Bu durumda, yakalama grubu `(\w+[;,]?\s?)` , `+` nicelik düzeninin uygulanabilmesi için bulunur, bu da normal ifade deseninin bir tümcedeki her sözcükle eşleşmesini sağlar. Aksi halde bir cümledeki son sözcüğü eşleyebilir.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/group1.cs#8)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/group1.vb#8)]  
  
 Alt ifadeleri yalnızca bunlara niceleyiciler uygulamak için kullanırken ve tutulan metinle ilgilenmediğinizde, grup tutmalarını devre dışı bırakmanız gerekir. Örneğin, `(?:subexpression)` Language öğesi, eşleşen alt dizeleri yakalamaya uyguladığı grubu engeller. Aşağıdaki örnekte, önceki örnekteki normal ifade deseninin olarak `\b(?:\w+[;,]?\s?)+[.?!]`değiştirilmiştir. Çıktıda gösterildiği gibi, normal ifade altyapısının <xref:System.Text.RegularExpressions.GroupCollection> ve <xref:System.Text.RegularExpressions.CaptureCollection> koleksiyonlarını doldurmasının engel olur.  
  
 [!code-csharp[Conceptual.RegularExpressions.BestPractices#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/cs/group2.cs#9)]
 [!code-vb[Conceptual.RegularExpressions.BestPractices#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.bestpractices/vb/group2.vb#9)]  
  
 Tutmayı, şu yöntemlerden biriyle devre dışı bırakabilirsiniz:  
  
- `(?:subexpression)` Language öğesini kullanın. Bu öğe, geçerli olduğu gruptaki eşleşen alt dizelerin tutulmasını engeller. Herhangi bir yuvalanmış grupta alt dize yakalamalarını devre dışı bırakmaz.  
  
- <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture> Seçeneğini kullanın. Normal ifade deseninde tüm adlandırılmamış ya da örtük yakalamaları devre dışı bırakır. Bu seçeneği kullandığınızda, yalnızca `(?<name>subexpression)` Language öğesiyle tanımlanan adlandırılmış gruplarla eşleşen alt dizeler yakalanabilir. `options` `options` Bayrak, bir<xref:System.Text.RegularExpressions.Regex>sınıfoluşturucusunun parametresine veya Statikeşleştirmeyöntemininparametresinegeçirilebilir.<xref:System.Text.RegularExpressions.Regex> <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture>  
  
- `(?imnsx)` Language öğesindeki `n` seçeneğini kullanın. Bu seçenek, tutulan tüm adlandırılmamış veya örtük öğeleri, öğenin normal ifade deseninde ortaya çıktığı noktadan başlayarak devre dışı bırakır. Yakalamaları, düzenin sonuna kadar veya `(-n)` seçeneği adlandırılmamış ya da örtük yakalamaları etkinleştirene kadar devre dışı bırakılır. Daha fazla bilgi için bkz. [Çeşitli Yapılar](../../../docs/standard/base-types/miscellaneous-constructs-in-regular-expressions.md).  
  
- `(?imnsx:subexpression)` Language öğesindeki `n` seçeneğini kullanın. Bu seçenek içindeki `subexpression`tüm adlandırılmamış veya örtük yakalamaları devre dışı bırakır. Yakalamalar adlandırılmamış ya da örtük yuvalı yakalama grupları tarafından devre dışı bırakılır.  
  
 [Başa dön](#top)  
  
<a name="RelatedTopics"></a>   
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Normal İfade Davranışının Ayrıntıları](../../../docs/standard/base-types/details-of-regular-expression-behavior.md)|.NET 'teki normal ifade altyapısının uygulanmasını inceler. Konu normal ifadelerin esnekliği üzerine yoğunlaşmakta ve geliştiricinin normal ifade altyapısının verimli ve sorunsuz çalışmasını sağlamadaki sorumluluğunu açıklamaktadır.|  
|[Geri Dönüş](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)|Geri izlemenin ne olduğunu ve bunun normal ifade performansını nasıl etkilediği açıklar ve geri izlemeye alternatifler sağlayan dil öğelerini inceler.|  
|[Normal İfade Dili - Hızlı Başvuru](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)|.NET 'teki normal ifade dilinin öğelerini açıklar ve her dil öğesi için ayrıntılı belgelere bağlantılar sağlar.|
