---
title: "Yavaş Başlatma"
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
- lazy initialization in .NET, introduction
ms.assetid: 56b4ae5c-4745-44ff-ad78-ffe4fcde6b9b
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f4998cc0c836cf46d79d854ad9a85e7eacf70d7f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="lazy-initialization"></a>Yavaş Başlatma
*Geç başlatma* bir nesnenin anlamına gelir oluşturulduktan ilk kullanılan kadar ertelenir. (Bu konu için koşulları *geç başlatma* ve *yavaş örneklemesi* eşanlamlıdır.) Geç Başlatma öncelikle performansı, kayıp hesaplama önlemek ve program bellek gereksinimlerini azaltmak için kullanılır. En yaygın senaryolar şunlardır:  
  
-   Ne zaman oluşturulacağını pahalı bir nesne varsa ve program kullanamayabilir. Örneğin, belleğe sahip olduğunuzu varsayın bir `Customer` olan nesneyi bir `Orders` içeren büyük bir dizi özelliği `Order` başlatılması için bir veritabanı bağlantısı gerektiren nesneleri. Kullanıcı hiçbir zaman siparişleri görüntülemek veya verileri bir hesaplama kullanmak isterse, sistem belleği veya döngüleri bilgisayar oluşturmak için kullanmak için bir neden yoktur. Kullanarak `Lazy<Orders>` bildirmek için `Orders` nesne geç başlatma için nesne kullanılmadığında İsraf sistem kaynaklarını özen gösterin.  
  
-   Ne zaman oluşturulacağını pahalı bir nesne varsa ve pahalı diğer işlemleri tamamlandıktan sonra oluşturulduktan kadar erteleme istiyorsanız. Örneğin, programınız başlar, ancak bazı yalnızca hemen gereken birkaç nesne örneklerini yükler varsayın. Gerekli nesnelerden oluşturana kadar gerekli olmayan nesnelerin başlatılması ertelemeyi tarafından program başlatma performansını artırabilir.  
  
 Geç Başlatma gerçekleştirmek için kendi kodunuzu yazabilirsiniz rağmen kullanmanız önerilir <xref:System.Lazy%601> yerine. <xref:System.Lazy%601>ve ilgili türlerinden de iş parçacığı güvenliği desteklemek ve tutarlı bir özel durum yayma İlkesi sağlayın.  
  
 Aşağıdaki tabloda farklı senaryolar yavaş başlatma etkinleştirmek için .NET Framework sürüm 4 sağlar türlerini listeler.  
  
|Tür|Açıklama|  
|----------|-----------------|  
|<xref:System.Lazy%601>|Geç Başlatma semantiği herhangi bir sınıf kitaplığı veya kullanıcı tanımlı tür için sağlayan bir sarmalayıcı sınıfı.|  
|<xref:System.Threading.ThreadLocal%601>|Benzer <xref:System.Lazy%601> bir iş parçacığı yerel temelinde geç başlatma semantiği sağlar ancak bu. Her iş parçacığı kendi benzersiz değer erişebilir.|  
|<xref:System.Threading.LazyInitializer>|Sağlayan gelişmiş `static` (`Shared` Visual Basic'te) için bir sınıf yükü olmadan nesnelerin yavaş başlatılmasını yöntemleri.|  
  
## <a name="basic-lazy-initialization"></a>Temel yavaş başlatma  
 Bir geç başlatılan türü, örneğin, tanımlamak için `MyType`, kullanın `Lazy<MyType>` (`Lazy(Of MyType)` Visual Basic'te), aşağıdaki örnekte gösterildiği gibi. Hiçbir temsilci geçtiyse <xref:System.Lazy%601> oluşturucusu, Sarmalanan türü kullanılarak oluşturulur tarafından <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> zaman değer özelliği ilk erişilir. Türü varsayılan bir oluşturucu yoksa, bir çalışma zamanı özel durum oluşur.  
  
 Aşağıdaki örnekte, varsayımında `Orders` bir dizi içeren bir sınıf `Order` nesnelerini bir veritabanından alınır. A `Customer` nesne örneği içeren `Orders`, ancak kullanıcı eylemlerini, verilerden bağlı olarak `Orders` nesne gerekli olabilir.  
  
 [!code-csharp[Lazy#1](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#1)]
 [!code-vb[Lazy#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#1)]  
  
 Bir temsilci geçebilen <xref:System.Lazy%601> belirli bir oluşturucu çağırır Oluşturucu oluşturma zamanında Sarmalanan türünde aşırı ve aşağıdaki örnekte gösterildiği gibi gerekli, diğer başlatma adımları gerçekleştirin.  
  
 [!code-csharp[Lazy#2](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#2)]
 [!code-vb[Lazy#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#2)]  
  
 Yavaş nesnesi oluşturulur sonra hiçbir örneği `Orders` kadar oluşturulan <xref:System.Lazy%601.Value%2A> yavaş değişkenin özelliği ilk kez erişilir. İlk erişimde Sarmalanan türü oluşturulur ve döndürülen ve gelecekteki tüm erişimi için depolanan.  
  
 [!code-csharp[Lazy#3](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#3)]
 [!code-vb[Lazy#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#3)]  
  
 A <xref:System.Lazy%601> nesne her zaman aynı nesne veya ile başlatıldı değeri döndürür. Bu nedenle, <xref:System.Lazy%601.Value%2A> özelliği salt okunur durumdadır. Varsa <xref:System.Lazy%601.Value%2A> başvuru depoları yazın, yeni bir nesne kendisine atadığınız olamaz. (Ancak, kendi ayarlanabilir genel alanlar ve Özellikler değeri değiştirebilirsiniz.) Varsa <xref:System.Lazy%601.Value%2A> depoları bir değer yazın, değeri değiştirilemez. Bununla birlikte, değişken Oluşturucusu yeniden yeni bağımsız değişkenleri kullanarak çağırarak yeni bir değişken oluşturabilirsiniz.  
  
 [!code-csharp[Lazy#4](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#4)]
 [!code-vb[Lazy#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#4)]  
  
 Yeni yavaş, önceki bir gibi değil örneği `Orders` kadar kendi <xref:System.Lazy%601.Value%2A> özelliği ilk erişilebilir.  
  
### <a name="thread-safe-initialization"></a>İş parçacığı başlatma  
 Varsayılan olarak, <xref:System.Lazy%601> iş parçacığı nesneleridir. Diğer bir deyişle, Oluşturucusu iş parçacığı güvenliği tür belirlemezse <xref:System.Lazy%601> oluşturduğu iş parçacığı nesneleridir. Çok iş parçacıklı senaryolarda erişmek için ilk iş parçacığı <xref:System.Lazy%601.Value%2A> bir iş parçacığı özelliğinin <xref:System.Lazy%601> nesnesi üzerinde tüm iş parçacıklarının tüm sonraki erişimler için bunu başlatır ve tüm iş parçacıkları aynı veri paylaşır. Bu nedenle, hangi iş parçacığı nesnesini başlatır önemli değildir ve yarış durumları zararsız.  
  
> [!NOTE]
>  Özel durum önbelleği kullanarak bu tutarlılık hata koşulları için genişletebilirsiniz. Daha fazla bilgi için sonraki bölüme bakın [yavaş nesneleri durumlar](../../../docs/framework/performance/lazy-initialization.md#ExceptionsInLazyObjects).  
  
 Aşağıdaki örnek, aynı gösterir `Lazy<int>` örneği üç ayrı iş parçacığı için aynı değere sahiptir.  
  
 [!code-csharp[Lazy#8](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#8)]
 [!code-vb[Lazy#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#8)]  
  
 Her iş parçacığı üzerinde ayrı veri gerekiyorsa kullanın <xref:System.Threading.ThreadLocal%601> , bu konunun ilerleyen bölümlerinde açıklandığı gibi yazın.  
  
 Bazı <xref:System.Lazy%601> oluşturucular sahip adlı bir Boolean parametresiyle `isThreadSafe` belirtmek için kullanılan olup olmadığını <xref:System.Lazy%601.Value%2A> özelliği birden çok iş parçacığı tarafından erişilen. Yalnızca bir iş parçacığından özelliğine erişmek istiyorsanız, geçirin `false` uygun performans avantajı elde edilir. Birden çok iş parçacığından özelliğine erişmek istiyorsanız, geçirin `true` istemek üzere <xref:System.Lazy%601> örneğinin düzgün bir şekilde bir iş parçacığı başlatma sırasında bir özel durum oluşturur yarış durumları işler.  
  
 Bazı <xref:System.Lazy%601> oluşturucular sahip bir <xref:System.Threading.LazyThreadSafetyMode> adlı parametre `mode`. Bu oluşturucu ek iş parçacığı güvenliği modu sağlar. Aşağıdaki tabloda nasıl, iş parçacığı güvenliği bir <xref:System.Lazy%601> nesnesi, iş parçacığı güvenliği belirtin Oluşturucu parametreleri tarafından etkilenir. Her Oluşturucusu en çok bir tür parametresi var.  
  
|Nesnenin iş parçacığı güvenliği|`LazyThreadSafetyMode``mode` parametresi|Boolean `isThreadSafe` parametresi|Hiçbir iş parçacığı güvenliği parametreleri|  
|---------------------------------|---------------------------------------------|--------------------------------------|---------------------------------|  
|Tam olarak iş parçacığı açısından güvenli; bir seferde yalnızca bir iş parçacığı değeriyle dener.|<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>|`true`|Evet.|  
|İş parçacığı-güvenli değil.|<xref:System.Threading.LazyThreadSafetyMode.None>|`false`|Yok.|  
|Tam olarak iş parçacığı açısından güvenli; iş parçacığı yarış'değeri başlatılamadı.|<xref:System.Threading.LazyThreadSafetyMode.PublicationOnly>|Yok.|Yok.|  
  
 Tabloda gösterildiği gibi belirtme <xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication?displayProperty=nameWithType> için `mode` parametresi aynıdır belirtme `true` için `isThreadSafe` parametre ve belirterek <xref:System.Threading.LazyThreadSafetyMode.None?displayProperty=nameWithType> belirtme aynı `false`.  
  
 Belirtme <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly?displayProperty=nameWithType> başlatma girişimi birden çok iş parçacığı sağlar <xref:System.Lazy%601> örneği. Yalnızca bir iş parçacığı bu yarış kazanabilirsiniz ve tüm diğer iş parçacıklarından başarılı iş parçacığı tarafından başlatıldı değeri alabilirsiniz. Başlatma sırasında bir iş parçacığında özel durum oluşur, o iş parçacığı başarılı iş parçacığı tarafından ayarlanan değer almaz. Özel durumlar önbelleğe alınmaz, bu nedenle bir sonraki erişim girişiminde <xref:System.Lazy%601.Value%2A> özelliği başarılı başlatma neden olur. Bu aşağıdaki bölümde açıklanan özel durumlar diğer modlarında nasıl işleneceğini farklıdır. Daha fazla bilgi için bkz: <xref:System.Threading.LazyThreadSafetyMode> numaralandırması.  
  
<a name="ExceptionsInLazyObjects"></a>   
## <a name="exceptions-in-lazy-objects"></a>Yavaş nesneleri özel durumları  
 Daha önce belirtildiği gibi bir <xref:System.Lazy%601> nesne her zaman döndürür aynı nesne veya, ile başlatıldı değeri ve bu nedenle <xref:System.Lazy%601.Value%2A> özelliği salt okunur durumdadır. Özel durum önbelleğe almayı etkinleştirirseniz bu girişi aynı zamanda özel durum davranışını genişletir. Geç başlatılan bir nesne özel durum etkinleştirildi ve onun başlatma yönteminden aykırı zaman <xref:System.Lazy%601.Value%2A> özelliği ilk erişilen, o aynı erişmeye sonraki her çalışırken özel durum <xref:System.Lazy%601.Value%2A> özelliği . Diğer bir deyişle, Sarmalanan türü Oluşturucusu hiçbir zaman, hatta birden çok iş parçacıklı senaryolarda yeniden çağrılır. Bu nedenle, <xref:System.Lazy%601> nesne üzerinde bir erişim bir özel durum ve bir sonraki erişimi bir değer döndürür.  
  
 Özel durum önbelleğe alma etkinse kullandığınızda <xref:System.Lazy%601?displayProperty=nameWithType> başlatma yöntemini alan oluşturucu (`valueFactory` parametresi); Örneğin, kullandığınızda etkin `Lazy(T)(Func(T))`Oluşturucusu. Oluşturucusu da uzun sürerse bir <xref:System.Threading.LazyThreadSafetyMode> değeri (`mode` parametresi), belirtin <xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication?displayProperty=nameWithType> veya <xref:System.Threading.LazyThreadSafetyMode.None?displayProperty=nameWithType>. Başlatma yöntemini belirtmek için bu iki moddan özel durum önbelleğe alınmasını etkinleştirir. Başlatma yöntemi çok basit olabilir. Örneğin, varsayılan oluşturucusu çağırabilirsiniz `T`: `new Lazy<Contents>(() => new Contents(), mode)` C# veya `New Lazy(Of Contents)(Function() New Contents())` Visual Basic'te. Kullanırsanız, bir <xref:System.Lazy%601?displayProperty=nameWithType> başlatma yöntemini belirtmiyor oluşturucusu, varsayılan oluşturucusu tarafından oluşturulan özel durumları `T` önbelleğe alınmaz. Daha fazla bilgi için bkz: <xref:System.Threading.LazyThreadSafetyMode> numaralandırması.  
  
> [!NOTE]
>  Oluşturursanız, bir <xref:System.Lazy%601> nesnesi ile `isThreadSafe` Oluşturucusu parametre kümesine `false` veya `mode` Oluşturucusu parametre kümesine <xref:System.Threading.LazyThreadSafetyMode.None?displayProperty=nameWithType>, erişmesi gereken <xref:System.Lazy%601> nesnesi tek bir iş parçacığından ya da kendi sağlayın Eşitleme. Bu, tüm yönlerini özel durumu önbelleğe alma dahil olmak üzere bu nesne için geçerlidir.  
  
 Önceki bölümünde belirtildiği gibi <xref:System.Lazy%601> belirterek oluşturulan nesneler <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly?displayProperty=nameWithType> özel durumlar farklı şekilde ele alın. İle <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly>, birden çok iş parçacığı başlatılamadı rekabet <xref:System.Lazy%601> örneği. Bu durumda, özel durumlar önbelleğe alınmaz ve erişmeyi denediği <xref:System.Lazy%601.Value%2A> özelliği başlatma başarılı olana kadar devam edebilir.  
  
 Yol aşağıdaki tabloda özetlenmiştir <xref:System.Lazy%601> oluşturucular denetim özel durumu önbelleğe alma.  
  
|Oluşturucu|İş parçacığı güvenliği modu|Başlatma yöntemini kullanır|Özel durumlar önbelleğe alınır|  
|-----------------|------------------------|--------------------------------|---------------------------|  
|Lazy(T)()|(<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>)|Hayır|Hayır|  
|Lazy(T)(FUNC(T))|(<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>)|Evet|Evet|  
|Lazy(T)(Boolean)|`True`(<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>) veya `false` (<xref:System.Threading.LazyThreadSafetyMode.None>)|Hayır|Hayır|  
|Lazy(T)(FUNC(T), Boolean)|`True`(<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>) veya `false` (<xref:System.Threading.LazyThreadSafetyMode.None>)|Evet|Evet|  
|Lazy(T)(LazyThreadSafetyMode)|Kullanıcı tanımlı|Hayır|Hayır|  
|Lazy(T)(FUNC(T), LazyThreadSafetyMode)|Kullanıcı tanımlı|Evet|Kullanıcı belirtiyorsa Hayır <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly>; Aksi halde, Evet.|  
  
## <a name="implementing-a-lazy-initialized-property"></a>Geç başlatılan bir özellik uygulama  
 Geç Başlatma kullanarak genel özelliği uygulamak için yedekleme alanı özelliğinin tanımlarsınız bir <xref:System.Lazy%601>ve geri dönüp <xref:System.Lazy%601.Value%2A> özelliğinden `get` özelliği erişimcisi.  
  
 [!code-csharp[Lazy#5](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#5)]
 [!code-vb[Lazy#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#5)]  
  
 <xref:System.Lazy%601.Value%2A> Özelliği salt okunur; bu nedenle, onu gösteren özelliği sahip olmayan `set` erişimcisi. Tarafından yedeklenen bir okuma/yazma özelliği gerekliyse bir <xref:System.Lazy%601> nesnesi `set` erişimci yeni oluşturmalısınız <xref:System.Lazy%601> nesne ve yedekleme deposu atayın. `set` Erişimci geçirilmedi yeni özellik değeri döndüren bir lambda ifadesi oluşturmalısınız `set` erişimci ve o lambda ifadesi oluşturucuya için yeni geçirin <xref:System.Lazy%601> nesnesi. Sonraki erişim <xref:System.Lazy%601.Value%2A> özelliği başlatma yeni neden olacak <xref:System.Lazy%601>ve kendi <xref:System.Lazy%601.Value%2A> özelliği bundan sonra özelliğine atanan yeni değerini döndür. Bu karışık düzenleme yerleşik çoklu iş parçacığı kullanımı korumaları korumak için nedeni <xref:System.Lazy%601>. Aksi takdirde, özellik erişimcisi tarafından döndürülen değerin ilk önbelleğe gerekirdi <xref:System.Lazy%601.Value%2A> özelliği yalnızca önbelleğe alınan değeri değiştirin ve bunu yapmak için kendi iş parçacığı kod yazmanız gerekir. Tarafından yedeklenen bir okuma/yazma özelliği gerektirdiği ek başlatmaları nedeniyle bir <xref:System.Lazy%601> nesnesi, performansı kabul edilebilir olabilir. Ayrıca, belirli bir senaryoyu bağlı olarak, ek koordinasyon ayarlayıcılar alıcılar arasındaki yarış durumları önlemek için gerekli olabilir.  
  
## <a name="thread-local-lazy-initialization"></a>İş parçacığı yerel yavaş başlatma  
 Birden çok iş parçacıklı bazı senaryolarda, her iş parçacığının kendi özel veri vermek isteyebilirsiniz. Bu tür veriler adlı *iş parçacığı yerel veri*. .NET Framework sürüm 3.5 ve önceki sürümlerde, uyguladığınız `ThreadStatic` iş parçacığı yerel yapmak için statik bir değişkene özniteliği. Ancak, kullanarak `ThreadStatic` özniteliği Zarif hatalarına yol açabilir. Örneğin, hatta temel başlatma ifadeleri, erişen yalnızca ilk iş parçacığı üzerinde aşağıdaki örnekte gösterildiği gibi başlatılması değişken neden olur.  
  
 [!code-csharp[Lazy#6](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#6)]
 [!code-vb[Lazy#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#6)]  
  
 Varsayılan değer (sıfır) kullanarak diğer tüm parçacıklarında değişkeni başlatılır. .NET Framework sürüm 4 alternatif olarak, kullandığınız <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> tüm iş parçacıkları tarafından başlatılan bir örnek tabanlı, iş parçacığı yerel değişken oluşturmak için türü <xref:System.Action%601> sağladığınız temsilci. Aşağıdaki örnekte, tüm iş parçacıklarının, erişim `counter` başlangıç değeri 1 olarak görürsünüz.  
  
 [!code-csharp[Lazy#7](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#7)]
 [!code-vb[Lazy#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#7)]  
  
 <xref:System.Threading.ThreadLocal%601>çok aynı şekilde kendi nesne sarmalar <xref:System.Lazy%601>, bu temel farklılıklar ile:  
  
-   Her iş parçacığı, diğer iş parçacığı tarafından erişilebilir durumda değil, kendi özel veri kullanarak iş parçacığı yerel değişken başlatır.  
  
-   <xref:System.Threading.ThreadLocal%601.Value%2A?displayProperty=nameWithType> Özelliği okuma-yazma ve bir kez herhangi bir sayıda değiştirilebilir. Bu örneğin, bir özel durum yayma etkileyebilir `get` işlemi özel durum Yükselt ancak bir sonraki başarılı bir şekilde değeri başlatabilirsiniz.  
  
-   Hiçbir başlatma temsilci sağlanırsa, <xref:System.Threading.ThreadLocal%601> Sarmalanan türü türünün varsayılan değerini kullanarak başlatılır. Bu bağlamda <xref:System.Threading.ThreadLocal%601> tutarlıdır <xref:System.ThreadStaticAttribute> özniteliği.  
  
 Aşağıdaki örnek, her iş parçacığı erişen gösterir `ThreadLocal<int>` örneğini kendi benzersiz verilerin kopyasını alır.  
  
 [!code-csharp[Lazy#9](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#9)]
 [!code-vb[Lazy#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#9)]  
  
## <a name="thread-local-variables-in-parallelfor-and-foreach"></a>Parallel.For ve ForEach iş parçacığı yerel değişkenler  
 Kullandığınızda <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> yöntemi veya <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> yöntemi yinelemek için veri kaynakları paralel olarak üzerinden iş parçacığı yerel verileri için yerleşik destek sahip aşırı kullanabilirsiniz. Bu yöntemler, yerleşim yeri iş parçacığı oluşturma, erişim ve veriyi temizlemek için yerel temsilciler kullanarak elde edilir. Daha fazla bilgi için bkz: [nasıl yapılır: iş parçacığı yerel değişkenleriyle bir Parallel.For döngüsü yazma](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md) ve [nasıl yapılır: iş parçacığı yerel değişkenleriyle bir Parallel.ForEach döngüsü yazma](../../../docs/standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-thread-local-variables.md).  
  
## <a name="using-lazy-initialization-for-low-overhead-scenarios"></a>Düşük yükünü senaryoları için geç başlatma kullanarak  
 Çok sayıda nesneleri geç başlatma için sahip olduğu senaryolarda, her nesne kaydırma karar verebilirsiniz bir <xref:System.Lazy%601> çok fazla bellek veya çok sayıda bilgi işlem kaynaklarını gerektirir. Veya, katı gereksinimlere sahip olabilir hakkında nasıl geç başlatma sunulur. Böyle durumlarda, kullandığınız `static` (`Shared` Visual Basic'te) yöntemlerinin <xref:System.Threading.LazyInitializer?displayProperty=nameWithType> yavaş-her nesne bir örnekte kaydırma olmadan başlatma için sınıf <xref:System.Lazy%601>.  
  
 Aşağıdaki örnekte, tüm kaydırma yerine varsayımında `Orders` bir nesne <xref:System.Lazy%601> nesnesi başlatılmadı yavaş tek sahip `Order` yalnızca gerekli olup olmadığını nesneleri.  
  
 [!code-csharp[Lazy#10](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#10)]
 [!code-vb[Lazy#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#10)]  
  
 Bu örnekte, başlatma yordamı her döngü tekrarında üzerinde çağrılan dikkat edin. Çok iş parçacıklı senaryolarda başlatma yordamı çağırmak için ilk değeri tüm iş parçacıkları tarafından görülen bir iş parçacığıdır. Sonraki iş parçacığı sayısı ayrıca başlatma yordamı çağırma ancak sonuçları kullanılmaz. Bu tür bir olası yarış durumu kabul edilebilir değilse kullanın <xref:System.Threading.LazyInitializer.EnsureInitialized%2A?displayProperty=nameWithType> Boolean bağımsız değişkeni ve eşitleme nesnesi alır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilen İş Parçacığı Oluşturma Temelleri](../../../docs/standard/threading/managed-threading-basics.md)  
 [İş Parçacıkları ve İş Parçacığı Oluşturma](../../../docs/standard/threading/threads-and-threading.md)  
 [Görev Paralel Kitaplığı (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 [Nasıl yapılır: Nesnelerin Geç Başlatılmasını Gerçekleştirme](../../../docs/framework/performance/how-to-perform-lazy-initialization-of-objects.md)
