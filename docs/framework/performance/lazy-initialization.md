---
title: Yavaş Başlatma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lazy initialization in .NET, introduction
ms.assetid: 56b4ae5c-4745-44ff-ad78-ffe4fcde6b9b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fac921bbe6250b039aba8527a1b9b5203af0972e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54492955"
---
# <a name="lazy-initialization"></a>Yavaş Başlatma
*Yavaş başlatma* nesnenin anlamına gelir oluşturulduktan önce kullanılana kadar ertelenir. (Bu konu için koşulları *yavaş başlatma* ve *yavaş oluşturmada* eşanlamlıdır.) Yavaş başlatma, öncelikle performansı iyileştirmek için kısıp hesaplama önlemek ve program bellek gereksinimlerini azaltmak için kullanılır. En yaygın senaryolar şunlardır:  
  
-   Oluşturmak pahalı bir nesnesinin yüklü ve program kullanamayabilir. Örneğin, bellekte olduğunu varsayalım. bir `Customer` nesnesi bir `Orders` içeren büyük bir dizi özelliği `Order` nesneleri başlatılması için bir veritabanı bağlantısı gerektirir. Kullanıcı, siparişleri görüntülemek veya bir hesaplamanın verileri kullanmak hiçbir zaman isterse, sistem belleği veya döngüleri bilgi işlem oluşturmak için kullanılacak bir neden yoktur. Kullanarak `Lazy<Orders>` bildirmek için `Orders` kaçınırsınız İsraf sistem kaynaklarının olmadığında nesne yavaş başlatma için nesne.  
  
-   Ne zaman oluşturulacağı pahalı bir nesneye sahip ve diğer pahalı işlemler tamamlandıktan sonra oluşturulduktan kadar erteleme istiyorsunuz. Örneğin, programınız başlar, ancak bazı yalnızca hemen gerekli olan birden fazla nesne örneklerini yükler varsayalım. Gerekli nesnelerden oluşturulan kadar gerekli olmayan nesnelerin başlatılması erteleyerek program başlangıç performansını artırabilir.  
  
 Yavaş başlatma gerçekleştirmek için kendi kodunuzu yazabilirsiniz olmasa da kullanmanızı öneririz <xref:System.Lazy%601> yerine. <xref:System.Lazy%601> ve ilgili türlerinden de iş parçacığı güvenliği destek ve tutarlı bir özel durum yayma İlkesi belirtin.  
  
 Aşağıdaki tabloda farklı senaryolarda yavaş başlatma etkinleştirmek için .NET Framework sürüm 4 sağlayan türleri listelenmektedir.  
  
|Tür|Açıklama|  
|----------|-----------------|  
|<xref:System.Lazy%601>|Sarmalayıcı sınıf herhangi bir sınıf kitaplığı veya kullanıcı tanımlı tür için yavaş başlatma semantikler sağlar.|  
|<xref:System.Threading.ThreadLocal%601>|Benzer <xref:System.Lazy%601> dışında bir iş parçacığı-yerel olarak yavaş başlatma semantiği sağlar. Her iş parçacığı kendi benzersiz bir değer erişebilir.|  
|<xref:System.Threading.LazyInitializer>|Sağlayan gelişmiş `static` (`Shared` Visual Basic'te) bir sınıf yükü olmadan nesnelerin geç başlatılmasını için yöntemleri.|  
  
## <a name="basic-lazy-initialization"></a>Temel yavaş başlatma  
 Geç başlatılan tür, örneğin, tanımlama için `MyType`, kullanın `Lazy<MyType>` (`Lazy(Of MyType)` Visual Basic'te), aşağıdaki örnekte gösterildiği gibi. Hiçbir temsilci geçtiyse <xref:System.Lazy%601> oluşturucusu, kaydırılmış tür oluşturulur kullanarak <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> zaman value özelliği ilk erişilen. Türü varsayılan bir oluşturucuya sahip değilse, bir çalışma zamanı özel durum oluşturulur.  
  
 Aşağıdaki örnekte, varsayımında `Orders` bir dizi içeren bir sınıf `Order` nesnelerini bir veritabanından alınır. A `Customer` nesne örneğini içeren `Orders`, ancak kullanıcı eylemlerini, verilerden bağlı olarak `Orders` nesne gerekli olmayabilir.  
  
 [!code-csharp[Lazy#1](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#1)]
 [!code-vb[Lazy#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#1)]  
  
 Bir temsilci de geçirebilirsiniz <xref:System.Lazy%601> belirli bir oluşturucu çağırır oluşturucu aşırı Sarmalanan tür üzerinde oluşturma zamanında ve aşağıdaki örnekte gösterildiği gibi gerekli olan tüm diğer başlatma adımlarını gerçekleştirin.  
  
 [!code-csharp[Lazy#2](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#2)]
 [!code-vb[Lazy#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#2)]  
  
 Yavaş nesnesi oluşturulur sonra hiçbir örneği `Orders` kadar oluşturulan <xref:System.Lazy%601.Value%2A> yavaş değişkeninin özelliği ilk kez erişilebilir. İlk erişimde kaydırılmış tür oluşturulur ve döndürülen ve herhangi bir gelecek erişimi için depolanır.  
  
 [!code-csharp[Lazy#3](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#3)]
 [!code-vb[Lazy#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#3)]  
  
 A <xref:System.Lazy%601> nesne her zaman aynı nesne veya ile başlatıldı değeri döndürür. Bu nedenle, <xref:System.Lazy%601.Value%2A> özelliği salt okunur. Varsa <xref:System.Lazy%601.Value%2A> depoları başvuru türü, yeni bir nesne kendisine atayamazsınız. (Ancak ayarlanabilir genel alanlar ve Özellikler değerini değiştirebilirsiniz.) Varsa <xref:System.Lazy%601.Value%2A> depoları bir değer türü, değerini değiştiremezsiniz. Bununla birlikte, değişken Oluşturucu yeniden yeni bağımsız değişkenler kullanarak harekete geçirerek yeni bir değişken oluşturabilirsiniz.  
  
 [!code-csharp[Lazy#4](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#4)]
 [!code-vb[Lazy#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#4)]  
  
 Yeni yavaş, önceki bir gibi değil örneğini `Orders` kadar kendi <xref:System.Lazy%601.Value%2A> özelliği ilk kez erişilebilir.  
  
### <a name="thread-safe-initialization"></a>İş parçacığı açısından güvenli başlatma  
 Varsayılan olarak, <xref:System.Lazy%601> iş parçacığı açısından güvenli nesneleridir. Diğer bir deyişle, oluşturucu iş parçacığı güvenliği türü belirtmezse <xref:System.Lazy%601> oluşturduğu iş parçacığı açısından güvenli nesneleridir. Çok iş parçacıklı senaryolarda erişmek için ilk iş parçacığında <xref:System.Lazy%601.Value%2A> iş parçacığı açısından güvenli özelliği <xref:System.Lazy%601> nesne için tüm iş parçacıklarının sonraki tüm erişimlerde onu başlatır ve tüm iş parçacıkları aynı verileri paylaşın. Bu nedenle, hangi iş parçacığı nesnesi başlatan bir önemi yoktur ve yarış durumları zararsızdır.  
  
> [!NOTE]
>  Bu tutarlılık hata koşulları için özel durum Önbelleği'ni kullanarak genişletebilirsiniz. Daha fazla bilgi için sonraki bölüme bakın [yavaş nesneleri durumlar](../../../docs/framework/performance/lazy-initialization.md#ExceptionsInLazyObjects).  
  
 Aşağıdaki örnek aynı gösteren `Lazy<int>` örneği için üç ayrı iş parçacığı aynı değere sahiptir.  
  
 [!code-csharp[Lazy#8](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#8)]
 [!code-vb[Lazy#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#8)]  
  
 Her iş parçacığı üzerinde ayrı veri gerekiyorsa kullanın <xref:System.Threading.ThreadLocal%601> , bu konunun ilerleyen bölümlerinde açıklandığı şekilde yazın.  
  
 Bazı <xref:System.Lazy%601> oluşturuculara sahip adlı bir Boole parametresi `isThreadSafe` belirtmek için kullanılan olmadığını <xref:System.Lazy%601.Value%2A> özelliği birden çok iş parçacığı tarafından erişilebilir. Özelliği yalnızca bir iş parçacığından erişmek istiyorsanız, geçirin `false` büyüklükteki performans avantajı elde edilir. Özellik birden fazla iş parçacığından erişmek istiyorsanız, geçirin `true` istemek için <xref:System.Lazy%601> tek bir iş parçacığı başlatma sırasında bir özel durum oluşturduğunda yarış durumlarını doğru bir şekilde işlemek için örneği.  
  
 Bazı <xref:System.Lazy%601> oluşturuculara sahip bir <xref:System.Threading.LazyThreadSafetyMode> adlı parametre `mode`. Bu oluşturucular bir ek iş parçacığı güvenlik modu sağlar. Aşağıdaki tabloda nasıl, iş parçacığı güvenliği bir <xref:System.Lazy%601> nesne iş parçacığı güvenliği belirtin Oluşturucusu parametrelerin etkilenir. Her Oluşturucu en fazla bir tür parametresi vardır.  
  
|Nesne iş parçacığı güvenliği|`LazyThreadSafetyMode` `mode` Parametre|Boole `isThreadSafe` parametresi|İş parçacığı güvenliği parametre yok|  
|---------------------------------|---------------------------------------------|--------------------------------------|---------------------------------|  
|Tam iş parçacığı açısından güvenli; aynı anda yalnızca tek bir iş parçacığı değeriyle dener.|<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>|`true`|Evet.|  
|İş parçacığı-güvenli değildir.|<xref:System.Threading.LazyThreadSafetyMode.None>|`false`|Uygulanamaz.|  
|Tam iş parçacığı açısından güvenli; iş parçacıkları yarış'değeri başlatılamadı.|<xref:System.Threading.LazyThreadSafetyMode.PublicationOnly>|Uygulanamaz.|Uygulanamaz.|  
  
 Tablonun gösterdiği gibi belirtme <xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication?displayProperty=nameWithType> için `mode` parametre belirtmekle aynı olan `true` için `isThreadSafe` parametresi ve belirterek <xref:System.Threading.LazyThreadSafetyMode.None?displayProperty=nameWithType> belirtmekle aynı `false`.  
  
 Belirtme <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly?displayProperty=nameWithType> birden çok iş parçacığı başlatmaya sağlayan <xref:System.Lazy%601> örneği. Yalnızca bir iş parçacığı bu yarışını kazanmak ve diğer tüm iş başarılı bir iş parçacığı tarafından başlatıldı değerini alır. Başlatma sırasında bir iş parçacığında bir özel durum, iş parçacığı başarılı bir iş parçacığı tarafından ayarlanan değer almaz. Özel durumlar önbelleğe alınmaz, bu nedenle erişmek için sonraki bir girişimi <xref:System.Lazy%601.Value%2A> özelliği içinde başarıyla başlatılmasına neden olur. Bu, aşağıdaki bölümde anlatılan diğer modlarda özel durumları kabul edilir şekilde farklıdır. Daha fazla bilgi için <xref:System.Threading.LazyThreadSafetyMode> sabit listesi.  
  
<a name="ExceptionsInLazyObjects"></a>   
## <a name="exceptions-in-lazy-objects"></a>Yavaş nesneleri özel durumları  
 Daha önce belirtildiği gibi bir <xref:System.Lazy%601> nesne her zaman aynı nesne veya birlikte başlatıldı değerini döndürür ve bu nedenle <xref:System.Lazy%601.Value%2A> özelliği salt okunur. Özel durum önbelleğe almayı etkinleştirirseniz, bu değiştirilemezlik ayrıca özel durum davranışını genişletir. Geç başlatılan bir nesne özel durum önbelleği etkinleştirildi ve kendi başlatma yöntemden bir özel durum oluşturur, <xref:System.Lazy%601.Value%2A> özelliğine önce erişilirse, o aynı erişmek için sonraki her denemede özel durum <xref:System.Lazy%601.Value%2A> özelliği . Diğer bir deyişle, kaydırılmış Tür oluşturucu hiçbir zaman, hatta çok iş parçacıklı senaryolarda yeniden çağrılır. Bu nedenle, <xref:System.Lazy%601> nesne üzerinde bir erişim bir özel durum ve bir sonraki erişimi bir değer döndürür.  
  
 Özel önbelleğe alma etkin kullandığınızda <xref:System.Lazy%601?displayProperty=nameWithType> başlatma yöntemini alan oluşturucu (`valueFactory` parametresi); Örneğin, kullandığınız zaman etkin `Lazy(T)(Func(T))`Oluşturucusu. Oluşturucu ayrıca uzun sürerse bir <xref:System.Threading.LazyThreadSafetyMode> değeri (`mode` parametresi), belirtin <xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication?displayProperty=nameWithType> veya <xref:System.Threading.LazyThreadSafetyMode.None?displayProperty=nameWithType>. Başlatma yöntemini belirleme, özel durum, bu iki mod için önbelleğe alınmasını etkinleştirir. Başlatma yöntemi çok basit olabilir. Örneğin, varsayılan oluşturucusu çağırabilirsiniz `T`: `new Lazy<Contents>(() => new Contents(), mode)` C# veya `New Lazy(Of Contents)(Function() New Contents())` Visual Basic'te. Kullanıyorsanız bir <xref:System.Lazy%601?displayProperty=nameWithType> başlatma yöntemini belirtmeyen bir kurucu, için varsayılan oluşturucu tarafından oluşturulan özel durumları `T` önbelleğe alınmaz. Daha fazla bilgi için <xref:System.Threading.LazyThreadSafetyMode> sabit listesi.  
  
> [!NOTE]
>  Oluşturursanız, bir <xref:System.Lazy%601> nesnesi ile `isThreadSafe` kümesine Oluşturucu parametresi `false` veya `mode` kümesine Oluşturucu parametresi <xref:System.Threading.LazyThreadSafetyMode.None?displayProperty=nameWithType>, erişmesi gereken <xref:System.Lazy%601> nesne tek bir iş parçacığından veya kendi sağlayın Eşitleme. Bu, özel durum önbelleğe alma dahil olmak üzere nesnenin tüm yönleri için geçerlidir.  
  
 Önceki bölümde belirtildiği gibi <xref:System.Lazy%601> belirterek oluşturulan nesneleri <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly?displayProperty=nameWithType> özel durumlar farklı şekilde ele. İle <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly>, birden çok iş parçacığı başlatılamadı yarışabileceğiniz <xref:System.Lazy%601> örneği. Bu durumda, özel durumlar önbelleğe alınmaz ve erişmeye <xref:System.Lazy%601.Value%2A> özellik başlatma başarılı olana kadar devam edebilir.  
  
 Aşağıdaki tabloda özetlenmiştir biçimini <xref:System.Lazy%601> oluşturucular denetim özel önbelleğe alma.  
  
|Oluşturucu|İş parçacığı güvenlik modu|Başlatma yöntemi kullanır.|Özel durumlar önbelleğe alınır|  
|-----------------|------------------------|--------------------------------|---------------------------|  
|Lazy(T)()|(<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>)|Hayır|Hayır|  
|Lazy(T)(FUNC(T))|(<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>)|Evet|Evet|  
|Lazy(T)(Boolean)|`True` (<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>) veya `false` (<xref:System.Threading.LazyThreadSafetyMode.None>)|Hayır|Hayır|  
|Lazy(T)(FUNC(T), Boolean)|`True` (<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>) veya `false` (<xref:System.Threading.LazyThreadSafetyMode.None>)|Evet|Evet|  
|Lazy(T)(LazyThreadSafetyMode)|Kullanıcı tarafından belirtilen|Hayır|Hayır|  
|Lazy(T)(FUNC(T), LazyThreadSafetyMode)|Kullanıcı tarafından belirtilen|Evet|Kullanıcının belirttiği Hayır <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly>; tersi durumda, Evet.|  
  
## <a name="implementing-a-lazy-initialized-property"></a>Geç başlatılan bir özelliği uygulama  
 Geç Başlatma kullanarak ortak özelliği uygulamak için olarak özelliğinin destek alanı tanımlar. bir <xref:System.Lazy%601>ve dönüş <xref:System.Lazy%601.Value%2A> özelliğinden `get` özellik erişimcisi.  
  
 [!code-csharp[Lazy#5](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#5)]
 [!code-vb[Lazy#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#5)]  
  
 <xref:System.Lazy%601.Value%2A> Özelliği salt okunur; bu nedenle, kullanıma sunduğu özellik yoktur `set` erişimcisi. Tarafından desteklenen bir okuma/yazma özelliği gerekliyse bir <xref:System.Lazy%601> nesnesi `set` erişimci yeni oluşturmalısınız <xref:System.Lazy%601> nesne ve yedekleme deposu için atayın. `set` Erişimci geçildi yeni özellik değeri döndüren bir lambda ifadesi oluşturmalısınız `set` erişimci ve oluşturucuya, lambda ifadesi için yeni geçirin <xref:System.Lazy%601> nesne. Sonraki erişim <xref:System.Lazy%601.Value%2A> özelliği yeni başlatma neden olacak <xref:System.Lazy%601>ve onun <xref:System.Lazy%601.Value%2A> özelliği bundan sonra özelliğine atanan yeni değer döndürür. Bu yaşar düzenleme için yerleşik çoklu iş parçacığı kullanımı korumaları korumak için nedeni <xref:System.Lazy%601>. Aksi takdirde, özellik erişimcileri tarafından döndürülen değerin ilk önbellek zorunda <xref:System.Lazy%601.Value%2A> özelliği yalnızca önbelleğe alınan değeri değiştirmek ve bunu yapmak için kendi iş parçacığı açısından güvenli kod yazma gerekir. Tarafından desteklenen bir okuma/yazma özelliği gerektirdiği ek başlatmalar nedeniyle bir <xref:System.Lazy%601> nesnesi, performansı kabul edilebilir olmayabilir. Ayrıca, belirli bir senaryoya bağlı olarak, ek koordinasyon yarış ayarlayıcılar alıcıları arasındaki önlemek için gerekli olabilir.  
  
## <a name="thread-local-lazy-initialization"></a>İş parçacığı-yerel yavaş başlatma  
 Çok iş parçacıklı bazı senaryolarda, her iş parçacığının kendi özel veri vermek isteyebilirsiniz. Bu tür veriler denir *iş parçacığı-yerel veri*. .NET Framework sürüm 3.5 ve önceki sürümlerinde, geçerli olabilir `ThreadStatic` özniteliği iş parçacığı-yerel yapmak için bir statik değişken. Ancak, `ThreadStatic` özniteliği Zarif hatalarına neden olabilir. Örneğin, aşağıdaki örnekte gösterildiği gibi erişen yalnızca ilk iş parçacığında başlatılacak değişkeni bile temel başlatma deyimleri neden olur.  
  
 [!code-csharp[Lazy#6](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#6)]
 [!code-vb[Lazy#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#6)]  
  
 Tüm diğer iş parçacıkları üzerinde varsayılan değerine (sıfır) kullanarak değişkeni başlatılır. .NET Framework sürüm 4 alternatif olarak, kullandığınız <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> tüm iş parçacıkları tarafından başlatılan bir örnek tabanlı, iş parçacığı yerel değişkeni oluşturmak için tür <xref:System.Action%601> sağladığınız temsilci. Aşağıdaki örnekte, tüm iş parçacıkları, erişim `counter` başlangıç değeri 1 görürsünüz.  
  
 [!code-csharp[Lazy#7](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#7)]
 [!code-vb[Lazy#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#7)]  
  
 <xref:System.Threading.ThreadLocal%601> aynı şekilde çok nesne sarmalar <xref:System.Lazy%601>, temel farklar:  
  
-   Her iş parçacığı, diğer iş parçacığı tarafından erişilebilir değil, kendi özel verileri kullanarak iş parçacığı yerel değişkenini ayarlar.  
  
-   <xref:System.Threading.ThreadLocal%601.Value%2A?displayProperty=nameWithType> Özelliği okuma-yazma ve bir kez herhangi bir sayıda değiştirilebilir. Bu örneğin, bir özel durum yayma etkileyebilir `get` işlemi, bir özel durum yükseltme, ancak bir sonraki başarılı bir şekilde değer başlatabilirsiniz.  
  
-   Hiçbir başlatma temsilci sağlanırsa <xref:System.Threading.ThreadLocal%601> Sarmalanan türünü türünün varsayılan değerini kullanarak başlatın. Bu bağlamda <xref:System.Threading.ThreadLocal%601> tutarlıdır <xref:System.ThreadStaticAttribute> özniteliği.  
  
 Aşağıdaki örnek, her iş parçacığı erişen gösterir `ThreadLocal<int>` örneğini benzersiz kendi veri kopyasını alır.  
  
 [!code-csharp[Lazy#9](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#9)]
 [!code-vb[Lazy#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#9)]  
  
## <a name="thread-local-variables-in-parallelfor-and-foreach"></a>Thread-Local değişkenleri Parallel.For ve ForEach  
 Kullanırken <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> yöntemi veya <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> yöntemi yinelemek için paralel olarak veri kaynakları üzerinde iş parçacığı-yerel veri için yerleşik desteğe sahip aşırı kullanabilirsiniz. Bu yöntemleri, iş parçacığı-yerel konumu oluşturmanıza, erişmek ve ve verileri temizlemek için yerel temsilciler kullanılarak elde edilir. Daha fazla bilgi için [nasıl yapılır: İş parçacığı yerel değişkenleriyle bir Parallel.For döngüsü yazma](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md) ve [nasıl yapılır: Bölüm yerel değişkenleriyle bir Parallel.ForEach döngüsü yazma](../../../docs/standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-partition-local-variables.md).  
  
## <a name="using-lazy-initialization-for-low-overhead-scenarios"></a>Geç Başlatma kullanarak düşük ek yük senaryoları için  
 Çok sayıda nesnelerin geç başlatma için sahip olduğu senaryolarda, sarmalama, her bir nesnenin karar verebilirsiniz bir <xref:System.Lazy%601> çok fazla bellek veya çok sayıda bilgi işlem kaynakları gerektirir. Veya katı gereksinimlere sahip olabileceğiniz hakkında nasıl yavaş başlatma sunulur. Bu gibi durumlarda, kullandığınız `static` (`Shared` Visual Basic'te) yöntemleri <xref:System.Threading.LazyInitializer?displayProperty=nameWithType> yavaş-her bir nesne örneğinde sarmalama olmadan başlatma için sınıf <xref:System.Lazy%601>.  
  
 Aşağıdaki örnekte, tüm sarmalama yerine varsayalım. `Orders` bir nesne <xref:System.Lazy%601> geç başlatılan tek sahip nesne `Order` yalnızca gerekli olup olmadığını nesneleri.  
  
 [!code-csharp[Lazy#10](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#10)]
 [!code-vb[Lazy#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#10)]  
  
 Bu örnekte, başlatma yordamı döngünün her yinelenişinde çağrılan dikkat edin. Çok iş parçacıklı senaryolarda başlatma yordamı çağırmak için ilk iş parçacığında değeri tüm iş parçacıkları tarafından görülen bir bileşendir. Sonraki iş parçacığı da başlatma yordamı çağırmak, ancak sonuçları kullanılmaz. Bu tür bir yarış durumu olası kabul edilebilir değilse, aşırı yüklemesini kullanın <xref:System.Threading.LazyInitializer.EnsureInitialized%2A?displayProperty=nameWithType> bir Boole bağımsız değişkeni ve bir eşitleme nesnesi alır.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Yönetilen İş Parçacığı Oluşturma Temelleri](../../../docs/standard/threading/managed-threading-basics.md)
- [İş Parçacıkları ve İş Parçacığı Oluşturma](../../../docs/standard/threading/threads-and-threading.md)
- [Görev Paralel Kitaplığı (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
- [Nasıl yapılır: Nesnelerin geç başlatılmasını gerçekleştirme](../../../docs/framework/performance/how-to-perform-lazy-initialization-of-objects.md)
