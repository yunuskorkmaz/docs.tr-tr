---
title: Yavaş Başlatma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lazy initialization in .NET, introduction
ms.assetid: 56b4ae5c-4745-44ff-ad78-ffe4fcde6b9b
ms.openlocfilehash: 4f2b585dded6e20bb604f623217c6d1f1505c097
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180575"
---
# <a name="lazy-initialization"></a>Yavaş Başlatma
Bir nesnenin *tembel başlatılması,* oluşturmanın ilk kullanılana kadar ertelendiği anlamına gelir. (Bu konu için, *terimler tembel başlatma* ve tembel *anlık* eşanlamlıdır.) Tembel başlatma öncelikle performansı artırmak, savurgan hesaplamaönlemek ve program bellek gereksinimlerini azaltmak için kullanılır. Bunlar en yaygın senaryolar şunlardır:  
  
- Oluşturması pahalı bir nesneniz olduğunda ve program onu kullanmayabilir. Örneğin, bellekte, baş harflere başlatı lacak büyük `Order` bir nesne dizisi içeren bir `Customer` `Orders` nesneye sahip bir nesneniz olduğunu varsayalım. Kullanıcı siparişleri görüntülemek veya verileri bir hesaplamada kullanmak için hiçbir zaman İstemezse, bunu oluşturmak için sistem belleği veya bilgi işlem döngülerini kullanmak için bir neden yoktur. Sözcükte sözcük başlatma için nesneyi `Lazy<Orders>` `Orders` bildirmek için kullanarak, nesne kullanılmadığında sistem kaynaklarının boşa harcanmasını önleyebilirsiniz.  
  
- Oluşturması pahalı bir nesneniz olduğunda ve diğer pahalı işlemler tamamlanana kadar oluşturmasını ertelemek istediğinizde. Örneğin, programınız başladığında birkaç nesne örneği yüklediğini, ancak bunlardan yalnızca bazılarının hemen gerekli olduğunu varsayalım. Gerekli nesneler oluşturulana kadar gerekli olmayan nesnelerin başlatılmasını erteleyerek programın başlangıç performansını artırabilirsiniz.  
  
 Tembel başlatma gerçekleştirmek için kendi kodunuzu yazabiliyor olsanız da, bunun yerine kullanmanızı <xref:System.Lazy%601> öneririz. <xref:System.Lazy%601>ve ilgili türleri de iş parçacığı güvenliğini destekler ve tutarlı bir özel durum yayma ilkesi sağlar.  
  
 Aşağıdaki tabloda,.NET Framework sürüm 4'ün farklı senaryolarda tembel bir başlangıç sağlamak için sağladığı türleri listelemesi.  
  
|Tür|Açıklama|  
|----------|-----------------|  
|<xref:System.Lazy%601>|Herhangi bir sınıf kitaplığı veya kullanıcı tanımlı türü için tembel başlatma semantik sağlayan bir sarmalayıcı sınıfı.|  
|<xref:System.Threading.ThreadLocal%601>|Bir <xref:System.Lazy%601> iş parçacığı yerel olarak tembel başlatma semantik sağlar dışında benzer. Her iş parçacığının kendi benzersiz değerine erişimi vardır.|  
|<xref:System.Threading.LazyInitializer>|Bir `static` sınıfın`Shared` yükü olmadan nesnelerin tembel başlatılması için gelişmiş (Visual Basic) yöntemleri sağlar.|  
  
## <a name="basic-lazy-initialization"></a>Temel Tembel Başlatma  
 Aşağıdaki örnekte gösterildiği gibi, örneğin, `MyType` `Lazy<MyType>` (Visual`Lazy(Of MyType)` Basic'te) tembel-başharfe bürünen bir türü tanımlamak için. <xref:System.Lazy%601> Oluşturucuda temsilci geçirilirse, değer özelliğine ilk <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> erişildiğinde sarılmış tür kullanılarak oluşturulur. Türde parametresiz bir oluşturucu yoksa, çalışma zamanı özel bir durum atılır.  
  
 Aşağıdaki örnekte, veritabanından alınan bir `Orders` `Order` dizi nesne içeren bir sınıf olduğunu varsayalım. Bir `Customer` nesne `Orders`, ancak kullanıcı eylemlerine bağlı olarak, `Orders` nesneden veri gerekli olmayabilir bir örnek içerir.  
  
 [!code-csharp[Lazy#1](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#1)]
 [!code-vb[Lazy#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#1)]  
  
 Ayrıca, oluşturma zamanında sarılmış <xref:System.Lazy%601> türde belirli bir kurucu aşırı yükleme çağıran bir temsilciyi oluşturucuya geçirebilir ve aşağıdaki örnekte gösterildiği gibi gerekli olan diğer başlatma adımlarını gerçekleştirebilirsiniz.  
  
 [!code-csharp[Lazy#2](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#2)]
 [!code-vb[Lazy#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#2)]  
  
 Lazy nesnesi oluşturulduktan sonra, Lazy `Orders` <xref:System.Lazy%601.Value%2A> değişkeninin özelliğine ilk kez erişilene kadar hiçbir örnek oluşturulmaz. İlk erişimde, sarılmış tür oluşturulur ve döndürülür ve gelecekteki erişim için depolanır.  
  
 [!code-csharp[Lazy#3](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#3)]
 [!code-vb[Lazy#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#3)]  
  
 Bir <xref:System.Lazy%601> nesne her zaman başharfle başlandı aynı nesne veya değeri döndürür. Bu nedenle, <xref:System.Lazy%601.Value%2A> özellik salt okunur. Bir <xref:System.Lazy%601.Value%2A> başvuru türünü depolarsanız, ona yeni bir nesne atamazsınız. (Ancak, ayarlanabilir ortak alanların ve özelliklerinin değerini değiştirebilirsiniz.) Bir <xref:System.Lazy%601.Value%2A> değer türünü depolarsanız, değerini değiştiremezsiniz. Bununla birlikte, yeni bağımsız değişkenler kullanarak değişken oluşturucuyu yeniden çağırarak yeni bir değişken oluşturabilirsiniz.  
  
 [!code-csharp[Lazy#4](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#4)]
 [!code-vb[Lazy#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#4)]  
  
 Yeni tembel örnek, önceki gibi, özelliği ilk `Orders` erişilene <xref:System.Lazy%601.Value%2A> kadar anlık değildir.  
  
### <a name="thread-safe-initialization"></a>İş Parçacığı Güvenli Başlatma  
 Varsayılan olarak, <xref:System.Lazy%601> nesneler iş parçacığı güvenlidir. Diğer bir nokta, oluşturucu iş parçacığı nın türünü <xref:System.Lazy%601> belirtmezse, oluşturduğu nesneler iş parçacığı için güvenlidir. Çok iş parçacığı senaryolarında, iş parçacığı <xref:System.Lazy%601.Value%2A> güvenli <xref:System.Lazy%601> bir nesnenin özelliğine erişmek için ilk iş parçacığı tüm iş parçacıkları üzerinde sonraki tüm erişimler için başlatılan ve tüm iş parçacıkları aynı verileri paylaşır. Bu nedenle, hangi iş parçacığı nesneyi baş harfe doğru başlatmaktadır ve yarış koşulları iyi huyludur.  
  
> [!NOTE]
> Özel durum önbelleğe alma kullanarak bu tutarlılığı hata koşullarına genişletebilirsiniz. Daha fazla bilgi için, sonraki bölüme bakın, [Tembel Nesneler özel durumlar.](lazy-initialization.md#ExceptionsInLazyObjects)  
  
 Aşağıdaki örnek, aynı `Lazy<int>` örneğin üç ayrı iş parçacığı için aynı değere sahip olduğunu gösterir.  
  
 [!code-csharp[Lazy#8](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#8)]
 [!code-vb[Lazy#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#8)]  
  
 Her iş parçacığı için ayrı veri <xref:System.Threading.ThreadLocal%601> gerekiyorsa, bu konuda daha sonra açıklandığı gibi türü kullanın.  
  
 Bazı <xref:System.Lazy%601> oluşturucular, <xref:System.Lazy%601.Value%2A> özelliğin birden `isThreadSafe` çok iş parçacığından erişilip erişilmeyeceğini belirtmek için kullanılan boolean parametresi adlı bir parametreye sahiptir. Eğer sadece bir iş parçacığı özelliği erişmek `false` niyetinde iseniz, mütevazı bir performans avantajı elde etmek için geçmek. Özelliğe birden çok iş parçacığından erişmeye `true` yönelikseniz, bir iş parçacığının <xref:System.Lazy%601> başlatma zamanında özel bir durum attığı yarış koşullarını doğru şekilde işlemesi için örneği talimat vermek için geçiş edin.  
  
 Bazı <xref:System.Lazy%601> oluşturucuların <xref:System.Threading.LazyThreadSafetyMode> bir parametresi vardır. `mode` Bu oluşturucular ek bir iş parçacığı güvenlik modu sağlar. Aşağıdaki tablo, bir <xref:System.Lazy%601> nesnenin iş parçacığı güvenliğinin iş parçacığı güvenliğini belirten oluşturucu parametreleri tarafından nasıl etkilendiğini gösterir. Her oluşturucunun en fazla bir parametresi vardır.  
  
|Nesnenin iş parçacığı güvenliği|`LazyThreadSafetyMode``mode` parametre|Boolean `isThreadSafe` parametresi|İş parçacığı güvenlik parametreleri yok|  
|---------------------------------|---------------------------------------------|--------------------------------------|---------------------------------|  
|Tamamen iş parçacığı güvenli; değeri başlatmaya çalışır.|<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>|`true`|Evet.|  
|İş parçacığı güvenli değil.|<xref:System.Threading.LazyThreadSafetyMode.None>|`false`|Geçerli değildir.|  
|Tamamen iş parçacığı güvenli; konuları değeri başlatmaya yarış.|<xref:System.Threading.LazyThreadSafetyMode.PublicationOnly>|Geçerli değildir.|Geçerli değildir.|  
  
 Tablonun gösterdiği gibi, <xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication?displayProperty=nameWithType> `mode` parametre için `true` belirtme, `isThreadSafe` parametre için belirtme ile <xref:System.Threading.LazyThreadSafetyMode.None?displayProperty=nameWithType> aynıdır ve belirtme `false`de .  
  
 Belirtme, <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly?displayProperty=nameWithType> birden çok iş parçacığının <xref:System.Lazy%601> örneği başlatmaya çalışmasına olanak tanır. Bu yarışı yalnızca bir iş parçacığı kazanabilir ve diğer tüm iş parçacıkları başarılı iş parçacığı tarafından başlatı edilen değeri alır. Başlatma sırasında bir iş parçacığına bir özel durum atılırsa, bu iş parçacığı başarılı iş parçacığı tarafından ayarlanan değeri almaz. Özel durumlar önbelleğe alınmaz, bu nedenle <xref:System.Lazy%601.Value%2A> sonraki bir girişim özelliğine erişmek için başarılı bir başlatma neden olabilir. Bu, aşağıdaki bölümde açıklanan diğer modlarda özel durumlara işlenir şekilde farklıdır. Daha fazla bilgi <xref:System.Threading.LazyThreadSafetyMode> için numaralandırmaya bakın.  
  
<a name="ExceptionsInLazyObjects"></a>
## <a name="exceptions-in-lazy-objects"></a>Tembel Nesnelerdeki Özel Durumlar  
 Daha önce belirtildiği <xref:System.Lazy%601> gibi, bir nesne her zaman ile başharfe <xref:System.Lazy%601.Value%2A> başlandı aynı nesne veya değer döndürür ve bu nedenle özellik salt okunur. Özel durum önbelleğe alma özelliğini etkinleştirirseniz, bu değişmezlik özel durum davranışına da uzanır. Tembel olarak başlatılan bir nesne özel durum önbelleğe alma özelliğietkin ve <xref:System.Lazy%601.Value%2A> özelliği ilk erişildiğinde onun başlatma yönteminden bir özel <xref:System.Lazy%601.Value%2A> durum atıyorsa, aynı özel durum özelliği erişmek için sonraki her girişimde atılır. Başka bir deyişle, sarılmış tür oluşturucu, çok iş parçacığı senaryolarında bile hiçbir zaman yeniden çağrılmaz. Bu nedenle, <xref:System.Lazy%601> nesne bir erişim bir özel durum atamaz ve sonraki bir erişim bir değer döndüremez.  
  
 Bir başlatma yöntemi (parametre) <xref:System.Lazy%601?displayProperty=nameWithType> `valueFactory` alan herhangi bir oluşturucu kullandığınızda özel durum önbelleğe alma etkindir; örneğin, `Lazy(T)(Func(T))`oluşturucuyu kullandığınızda etkinleştirilir. Oluşturucu <xref:System.Threading.LazyThreadSafetyMode> da bir değer`mode` (parametre) <xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication?displayProperty=nameWithType> <xref:System.Threading.LazyThreadSafetyMode.None?displayProperty=nameWithType>alıyorsa, belirtin veya . Bir başlatma yöntemi belirtilmesi, bu iki mod için özel durum önbelleğe alınmasına olanak tanır. Başlatma yöntemi çok basit olabilir. Örneğin, parametresiz oluşturucu `T`: `new Lazy<Contents>(() => new Contents(), mode)` C#veya Visual Basic `New Lazy(Of Contents)(Function() New Contents())` olarak adlandırabilir. Bir başlatma <xref:System.Lazy%601?displayProperty=nameWithType> yöntemi belirtmeyen bir oluşturucu kullanıyorsanız, parametresiz oluşturucu `T` tarafından atılan özel durumlar önbelleğe alınmaz. Daha fazla bilgi <xref:System.Threading.LazyThreadSafetyMode> için numaralandırmaya bakın.  
  
> [!NOTE]
> `isThreadSafe` Kurucu parametresi ayarlı `false` bir `mode` <xref:System.Threading.LazyThreadSafetyMode.None?displayProperty=nameWithType> <xref:System.Lazy%601> <xref:System.Lazy%601> nesne veya kurucu parametre ayarlanmışsa, nesneye tek bir iş parçacığından erişmeniz veya kendi eşitlemenizi sağlamanız gerekir. Bu, özel durum önbelleğe alma da dahil olmak üzere nesnenin tüm yönleri için geçerlidir.  
  
 Önceki bölümde belirtildiği gibi, <xref:System.Lazy%601> özel durumları <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly?displayProperty=nameWithType> farklı şekilde ele alarak oluşturulan nesneler. Ile, <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly>birden çok iş parçacığı <xref:System.Lazy%601> örneği başlatmak için rekabet edebilir. Bu durumda, özel durumlar önbelleğe alınmaz ve <xref:System.Lazy%601.Value%2A> başlatma başarılı olana kadar özelliğe erişim girişimleri devam edebilir.  
  
 Aşağıdaki tablo, <xref:System.Lazy%601> oluşturucuların özel durum önbelleğe alma biçimini özetler.  
  
|Oluşturucu|İş parçacığı güvenlik modu|Başlatma yöntemini kullanır|Özel durumlar önbelleğe alınır|  
|-----------------|------------------------|--------------------------------|---------------------------|  
|Tembel(T)()|(<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>)|Hayır|Hayır|  
|Tembel(T)(Func(T))|(<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>)|Evet|Evet|  
|Tembel(T)(Boolean)|`True`(<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>) `false` <xref:System.Threading.LazyThreadSafetyMode.None>veya ( )|Hayır|Hayır|  
|Tembel(T)(Func(T), Boolean)|`True`(<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>) `false` <xref:System.Threading.LazyThreadSafetyMode.None>veya ( )|Evet|Evet|  
|Tembel(T)(LazyThreadSafetyMode)|Kullanıcı tarafından belirtilen|Hayır|Hayır|  
|Tembel(T)(Func(T), LazyThreadSafetyMode)|Kullanıcı tarafından belirtilen|Evet|Kullanıcı belirtirse <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly>hayır; Aksi takdirde, evet.|  
  
## <a name="implementing-a-lazy-initialized-property"></a>Tembel-Başharfe Bünyeyle Özellik Uygulama  
 Tembel başlatma kullanarak bir kamu malı uygulamak için, bir <xref:System.Lazy%601>olarak özelliğin <xref:System.Lazy%601.Value%2A> destek alanı `get` tanımlamak ve özelliği erişimci den geri.  
  
 [!code-csharp[Lazy#5](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#5)]
 [!code-vb[Lazy#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#5)]  
  
 Özellik <xref:System.Lazy%601.Value%2A> salt okunur; bu nedenle, onu ortaya çıkaran `set` özelliği hiçbir erişimci vardır. Bir nesne tarafından desteklenen bir <xref:System.Lazy%601> okuma/yazma özelliğine ihtiyacınız varsa, `set` erişimcinin yeni <xref:System.Lazy%601> bir nesne oluşturması ve bunu destek deposuna ataması gerekir. Erişimci, `set` `set` erişime geçen yeni özellik değerini döndüren bir lambda ifadesi oluşturmalı ve bu lambda <xref:System.Lazy%601> ifadesini yeni nesne için oluşturucuya geçirmelidir. <xref:System.Lazy%601.Value%2A> Özelliğin bir sonraki erişimi yeni <xref:System.Lazy%601>nin başlatılmasına neden olur ve özelliği <xref:System.Lazy%601.Value%2A> bundan sonra özelliğe atanan yeni değeri döndürecektir. Bu dolambaçlı düzenlemenin nedeni, yerleşik <xref:System.Lazy%601>çok iş parçacığı korumalarını korumaktır. Aksi takdirde, özellik erişimedenlerin <xref:System.Lazy%601.Value%2A> özellik tarafından döndürülen ilk değeri önbelleğe alması ve yalnızca önbelleğe alınmış değeri değiştirmesi ve bunu yapmak için kendi iş parçacığı güvenli kodunuzu yazmanız gerekir. Bir <xref:System.Lazy%601> nesne tarafından desteklenen okuma/yazma özelliği nin gerektirdiği ek başlatmalar nedeniyle, performans kabul edilemez olabilir. Ayrıca, belirli senaryoya bağlı olarak, ayarlayıcılar ve ayarlayıcılar arasındaki yarış koşullarını önlemek için ek koordinasyon gerekebilir.  
  
## <a name="thread-local-lazy-initialization"></a>Konu-Yerel Tembel Başlatma  
 Bazı çok iş parçacığı senaryolarında, her iş parçacığıkendi özel veri vermek isteyebilirsiniz. Bu tür verilere *iş parçacığı yerel verileri*denir. .NET Framework sürüm 3.5 ve daha önceki `ThreadStatic` sürümde, iş parçacığı yerel yapmak için statik bir değişkenöznitelik uygulayabilirsiniz. Ancak, öznitelik kullanarak `ThreadStatic` ince hatalara yol açabilir. Örneğin, temel başlatma deyimleri bile aşağıdaki örnekte gösterildiği gibi, değişkenin yalnızca ona erişen ilk iş parçacığında başlatılmasına neden olur.  
  
 [!code-csharp[Lazy#6](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#6)]
 [!code-vb[Lazy#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#6)]  
  
 Diğer tüm iş parçacıklarında, değişken varsayılan değeri (sıfır) kullanılarak başharfe çevrilir. .NET Framework sürüm 4'te alternatif olarak, <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> tür, sağladığınız <xref:System.Action%601> temsilci tarafından tüm iş parçacıklarında başharfe çevrilmiş örnek tabanlı, iş parçacığı yerel değişkeni oluşturmak için kullanabilirsiniz. Aşağıdaki örnekte, erişen `counter` tüm iş parçacıkları başlangıç değerini 1 olarak görür.  
  
 [!code-csharp[Lazy#7](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#7)]
 [!code-vb[Lazy#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#7)]  
  
 <xref:System.Threading.ThreadLocal%601><xref:System.Lazy%601>nesnesini, bu temel farklılıklarla aynı şekilde sarar:  
  
- Her iş parçacığı, diğer iş parçacıklarından erişilemeyen kendi özel verilerini kullanarak iş parçacığı yerel değişkenini başlangıç olarak kullanır.  
  
- Özellik <xref:System.Threading.ThreadLocal%601.Value%2A?displayProperty=nameWithType> okuma-yazma özelliğidir ve herhangi bir sayıda değiştirilebilir. Bu, özel durum yayılmasını etkileyebilir, `get` örneğin, bir işlem özel durum artırabilir, ancak bir sonraki değeri başarıyla başlatmaolabilir.  
  
- Hiçbir başlatma temsilcisi sağlanmazsa, <xref:System.Threading.ThreadLocal%601> türün varsayılan değerini kullanarak sarılmış türünü başolarak alacaktır. Bu bağlamda, <xref:System.Threading.ThreadLocal%601> öznitelik <xref:System.ThreadStaticAttribute> ile tutarlıdır.  
  
 Aşağıdaki örnek, örneğe `ThreadLocal<int>` erişen her iş parçacığının verilerin kendi benzersiz kopyasını aldığını göstermektedir.  
  
 [!code-csharp[Lazy#9](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#9)]
 [!code-vb[Lazy#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#9)]  
  
## <a name="thread-local-variables-in-parallelfor-and-foreach"></a>Paralel.For ve ForEach'de İş Parçacığı-Yerel Değişkenler  
 Veri kaynakları <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> üzerinde <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> paralel olarak yeniden doğrulamak için yöntem veya yöntemi kullandığınızda, iş parçacığı yerel verileri için yerleşik desteği olan aşırı yüklemeleri kullanabilirsiniz. Bu yöntemlerde, iş parçacığı yerelliği, verileri oluşturmak, erişmek ve temizlemek için yerel temsilciler kullanılarak elde edilir. Daha fazla bilgi için [bkz: Thread-Local Variables ile Parallel.For Loop yazın](../../standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md) ve [Nasıl: Partition-Local Variables ile Parallel.ForEach Loop yazın.](../../standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-partition-local-variables.md)  
  
## <a name="using-lazy-initialization-for-low-overhead-scenarios"></a>Düşük Tepeyle Senaryolar için Tembel Başlatma kullanma  
 Çok sayıda nesneyi tembelleştirmeniz gereken senaryolarda, her nesneyi çok <xref:System.Lazy%601> fazla bellek veya çok fazla bilgi işlem kaynağı na sarmanın gerektirdiğine karar verebilirsiniz. Veya, nasıl tembel başlatma maruz olduğu hakkında sıkı gereksinimleri olabilir. Bu gibi durumlarda, sınıfın `static` `Shared` (Visual Basic'te) <xref:System.Threading.LazyInitializer?displayProperty=nameWithType> yöntemlerini kullanarak her nesneyi bir örneğinde <xref:System.Lazy%601>sarmadan tembel-baş harfe bekleyebilirsiniz.  
  
 Aşağıdaki örnekte, bir nesnenin tamamını `Orders` tek <xref:System.Lazy%601> bir nesneye sarmak yerine, `Order` yalnızca gerekliyse, tek tek nesneleri tembelolarak başlatmanız gerektiğini varsayalım.  
  
 [!code-csharp[Lazy#10](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#10)]
 [!code-vb[Lazy#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#10)]  
  
 Bu örnekte, başlatma yordamı döngü her yineleme üzerinde çağrılır dikkat edin. Çok iş parçacığı senaryolarında, başlatma yordamını çağıran ilk iş parçacığı, değeri tüm iş parçacıkları tarafından görülen iş parçacığıdır. Daha sonraki iş parçacıkları da başlatma yordamını çağırır, ancak sonuçları kullanılmaz. Bu tür bir olası yarış koşulu kabul edilemezse, boolean bağımsız değişkeni ve eşitleme nesnesi <xref:System.Threading.LazyInitializer.EnsureInitialized%2A?displayProperty=nameWithType> gereken aşırı yük kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen İş Parçacığı Oluşturma Temelleri](../../standard/threading/managed-threading-basics.md)
- [İş Parçacıkları ve İş Parçacığı Oluşturma](../../standard/threading/threads-and-threading.md)
- [Görev Paralel Kitaplığı (TPL)](../../standard/parallel-programming/task-parallel-library-tpl.md)
- [Nasıl yapılır: Nesnelerin Yavaş Başlatılmasını Gerçekleştirme](how-to-perform-lazy-initialization-of-objects.md)
