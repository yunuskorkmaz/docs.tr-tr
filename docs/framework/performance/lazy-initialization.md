---
title: Yavaş Başlatma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lazy initialization in .NET, introduction
ms.assetid: 56b4ae5c-4745-44ff-ad78-ffe4fcde6b9b
ms.openlocfilehash: 54776304e484fc7f1db2c56b102034ed0e8650c0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130313"
---
# <a name="lazy-initialization"></a>Yavaş Başlatma
Bir nesnenin *geç başlatılması* , oluşturulması ilk kullanılana kadar ertelenmesi anlamına gelir. (Bu konu için, *yavaş başlatma* ve *yavaş örnekleme* terimleri eş anlamlı.) Yavaş başlatma öncelikle performansı artırmak, gereksiz hesaplama önlemek ve program belleği gereksinimlerini azaltmak için kullanılır. Bunlar en yaygın senaryolardır:  
  
- Oluşturmakta maliyetli bir nesneniz varsa ve program bunu kullanmayabilir. Örneğin, bellekte yer alan bir `Customer` nesnesi olduğunu varsayalım, bu, başlatılacak olan büyük bir `Order` nesneleri dizisi içeren bir `Orders` özelliğine sahiptir, bir veritabanı bağlantısı gerektirir. Kullanıcı hiçbir şekilde siparişleri görüntülemeyi veya verileri bir hesaplamada kullanmayı istemez, bu durumda sistem belleğini veya bilgi işlem döngülerini oluşturmak için bir neden yoktur. Yavaş başlatma için `Orders` nesnesini bildirmek üzere `Lazy<Orders>` kullanarak, nesne kullanılmazsa sistem kaynaklarından kaçınabilirsiniz.  
  
- Oluşturma maliyetli bir nesneniz varsa ve diğer maliyetli İşlemler tamamlanana kadar oluşturmayı erteleyin. Örneğin, programınızın başladığında birkaç nesne örneği yüklediğini varsayın, ancak yalnızca bir kısmı hemen gereklidir. Gerekli nesneler oluşturuluncaya kadar gerekli olmayan nesneleri başlatmayı erteleyerek programın başlangıç performansını artırabilirsiniz.  
  
 Yavaş başlatma gerçekleştirmek için kendi kodunuzu yazabilseniz de, bunun yerine <xref:System.Lazy%601> kullanmanızı öneririz. <xref:System.Lazy%601> ve ilgili türleri de iş parçacığı güvenliğini destekler ve tutarlı bir özel durum yayma ilkesi sağlar.  
  
 Aşağıdaki tabloda, farklı senaryolarda yavaş başlatmayı etkinleştirmek için .NET Framework sürüm 4 ' ün sağladığı türler listelenmektedir.  
  
|Tür|Açıklama|  
|----------|-----------------|  
|<xref:System.Lazy%601>|Herhangi bir sınıf kitaplığı veya Kullanıcı tanımlı tür için yavaş başlatma semantiğini sağlayan sarmalayıcı sınıf.|  
|<xref:System.Threading.ThreadLocal%601>|<xref:System.Lazy%601> benzer şekilde, iş parçacığı yerel temelinde yavaş başlatma semantiği sağlar. Her iş parçacığının kendi benzersiz değerine erişimi vardır.|  
|<xref:System.Threading.LazyInitializer>|, Bir sınıfın ek yükü olmadan nesnelerin yavaş başlatılmasına yönelik gelişmiş `static` (Visual Basic`Shared`) yöntemlerine sahiptir.|  
  
## <a name="basic-lazy-initialization"></a>Temel yavaş başlatma  
 Yavaş başlatılan bir tür tanımlamak için, örneğin `MyType`, aşağıdaki örnekte gösterildiği gibi, `Lazy<MyType>` (Visual Basic 'de`Lazy(Of MyType)`) kullanın. <xref:System.Lazy%601> oluşturucuda hiçbir temsilci geçirilmemişse, sarmalanmış tür, Value özelliğine ilk erişildiğinde <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> kullanılarak oluşturulur. Türün parametresiz bir Oluşturucusu yoksa, bir çalışma zamanı özel durumu oluşturulur.  
  
 Aşağıdaki örnekte, `Orders` bir veritabanından alınan `Order` nesneleri dizisini içeren bir sınıf olduğunu varsayalım. Bir `Customer` nesnesi `Orders`örneğini içerir, ancak kullanıcı eylemlerine bağlı olarak, `Orders` nesnesinden alınan veriler gerekli olmayabilir.  
  
 [!code-csharp[Lazy#1](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#1)]
 [!code-vb[Lazy#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#1)]  
  
 Ayrıca, oluşturma zamanında sarmalanmış tür üzerinde belirli bir Oluşturucu aşırı yüklemesini çağıran <xref:System.Lazy%601> oluşturucuda bir temsilci geçirebilir ve aşağıdaki örnekte gösterildiği gibi gereken diğer başlatma adımlarını gerçekleştirebilirsiniz.  
  
 [!code-csharp[Lazy#2](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#2)]
 [!code-vb[Lazy#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#2)]  
  
 Lazy nesnesi oluşturulduktan sonra, geç değişkeninin <xref:System.Lazy%601.Value%2A> özelliğine ilk kez erişilene kadar `Orders` örneği oluşturulmaz. İlk erişimde, Sarmalanan tür oluşturulur ve döndürülür ve gelecekte herhangi bir erişim için depolanır.  
  
 [!code-csharp[Lazy#3](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#3)]
 [!code-vb[Lazy#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#3)]  
  
 <xref:System.Lazy%601> nesnesi her zaman ile başlatıldığı nesne veya değeri döndürür. Bu nedenle, <xref:System.Lazy%601.Value%2A> özelliği salt okunurdur. <xref:System.Lazy%601.Value%2A> bir başvuru türü depoluyorsa, buna yeni bir nesne atayamazsınız. (Ancak, ayarlanabilir ortak alanları ve özellikleri değerini değiştirebilirsiniz.) <xref:System.Lazy%601.Value%2A> bir değer türünü depoluyorsa, değerini değiştiremezsiniz. Bununla birlikte, yeni bağımsız değişkenler kullanarak değişken oluşturucuyu yeniden çağırarak yeni bir değişken oluşturabilirsiniz.  
  
 [!code-csharp[Lazy#4](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#4)]
 [!code-vb[Lazy#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#4)]  
  
 Daha önceki bir gibi yeni bir geç örnek, <xref:System.Lazy%601.Value%2A> özelliğine erişilene kadar `Orders` örneklemez.  
  
### <a name="thread-safe-initialization"></a>İş parçacığı güvenli başlatma  
 Varsayılan olarak, <xref:System.Lazy%601> nesneleri iş parçacığı güvenlidir. Diğer bir deyişle, Oluşturucu iş parçacığı güvenliği türünü belirtmezse, oluşturduğu <xref:System.Lazy%601> nesneleri iş parçacığı güvenlidir. Çok iş parçacıklı senaryolarda, iş parçacığı güvenli <xref:System.Lazy%601> nesnesinin <xref:System.Lazy%601.Value%2A> özelliğine erişmek için ilk iş parçacığı bunu tüm iş parçacıklarında sonraki tüm erişimlerde başlatır ve tüm iş parçacıkları aynı verileri paylaşır. Bu nedenle, hangi iş parçacığının nesneyi başlattığında ve yarış durumlarının zararsız olması önemlidir.  
  
> [!NOTE]
> Özel durum önbelleğe alma özelliğini kullanarak bu tutarlılığı hata koşullarına genişletebilirsiniz. Daha fazla bilgi için, [yavaş nesnelerdeki özel durumlar](lazy-initialization.md#ExceptionsInLazyObjects)başlıklı sonraki bölüme bakın.  
  
 Aşağıdaki örnek, aynı `Lazy<int>` örneğinin üç ayrı iş parçacığı için aynı değere sahip olduğunu gösterir.  
  
 [!code-csharp[Lazy#8](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#8)]
 [!code-vb[Lazy#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#8)]  
  
 Her iş parçacığında ayrı veriye ihtiyacınız varsa, bu konunun ilerleyen kısımlarında açıklandığı gibi <xref:System.Threading.ThreadLocal%601> türünü kullanın.  
  
 Bazı <xref:System.Lazy%601> oluşturucular, <xref:System.Lazy%601.Value%2A> özelliğine birden çok iş parçacığından erişip erişmeyeceğini belirtmek için kullanılan `isThreadSafe` adlı bir Boole parametresine sahiptir. Özelliğe yalnızca bir iş parçacığından erişmeyi planlıyorsanız, bir ila büyüklükteki performans avantajı elde etmek için `false` geçirin. Özelliğe birden çok iş parçacığından erişmeyi düşünüyorsanız, bir iş parçacığının başlatma zamanında özel bir durum oluşturan yarış koşullarını doğru şekilde işlemesini <xref:System.Lazy%601> bildirmek için `true` geçirin.  
  
 Bazı <xref:System.Lazy%601> oluşturucuların `mode`adlı bir <xref:System.Threading.LazyThreadSafetyMode> parametresi vardır. Bu oluşturucular ek bir iş parçacığı güvenliği modu sağlar. Aşağıdaki tabloda, bir <xref:System.Lazy%601> nesnesinin iş parçacığı güvenliği, iş parçacığı güvenliğini belirten Oluşturucu parametrelerinden nasıl etkileneceği gösterilmektedir. Her oluşturucunun bu tür bir parametresi vardır.  
  
|Nesnenin iş parçacığı güvenliği|`LazyThreadSafetyMode` `mode` parametresi|Boole `isThreadSafe` parametresi|İş parçacığı güvenlik parametresi yok|  
|---------------------------------|---------------------------------------------|--------------------------------------|---------------------------------|  
|Tam iş parçacığı güvenli; tek seferde yalnızca bir iş parçacığı değeri başlatmaya çalışır.|<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>|`true`|Evet.|  
|İş parçacığı açısından güvenli değildir.|<xref:System.Threading.LazyThreadSafetyMode.None>|`false`|Yok.|  
|Tam iş parçacığı güvenli; değeri başlatmak için iş parçacıkları Race.|<xref:System.Threading.LazyThreadSafetyMode.PublicationOnly>|Yok.|Yok.|  
  
 Tabloda gösterildiği gibi, `mode` parametresi için <xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication?displayProperty=nameWithType> belirtmek, `isThreadSafe` parametresi için `true` belirtilerek aynı ve <xref:System.Threading.LazyThreadSafetyMode.None?displayProperty=nameWithType> belirtmenin `false`belirtilerek aynı olduğunu belirtmektir.  
  
 <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly?displayProperty=nameWithType> belirtmek, birden çok iş parçacığının <xref:System.Lazy%601> örneğini başlatmaya çalışmasına izin verir. Bu yarış 'i yalnızca bir iş parçacığı alabilir ve diğer tüm iş parçacıkları başarılı iş parçacığı tarafından başlatılan değeri alır. Başlatma sırasında bir iş parçacığında bir özel durum oluşturulursa, bu iş parçacığı başarılı iş parçacığı tarafından ayarlanan değeri almaz. Özel durumlar önbelleğe alınmaz, bu nedenle <xref:System.Lazy%601.Value%2A> özelliğine daha sonra erişme girişimi başarıyla başlatılmasına neden olabilir. Bu, özel durumların aşağıdaki bölümde açıklanan diğer modlarda ele alındığı yollardan farklıdır. Daha fazla bilgi için <xref:System.Threading.LazyThreadSafetyMode> sabit listesine bakın.  
  
<a name="ExceptionsInLazyObjects"></a>   
## <a name="exceptions-in-lazy-objects"></a>Yavaş nesnelerde özel durumlar  
 Daha önce belirtildiği gibi, bir <xref:System.Lazy%601> nesnesi her zaman ile başlatıldığı aynı nesne veya değeri döndürür ve bu nedenle <xref:System.Lazy%601.Value%2A> özelliği salt okunurdur. Özel durum önbelleğe almayı etkinleştirirseniz bu yaklaşım, özel durum davranışına de genişletilir. Geç başlatılmış bir nesnede özel durum önbelleğe alma etkinse ve <xref:System.Lazy%601.Value%2A> özelliğine ilk kez erişildiğinde, başlatma yönteminden bir özel durum oluşturursa, <xref:System.Lazy%601.Value%2A> özelliğine erişmek için sonraki her denemede aynı özel durum oluşturulur. Diğer bir deyişle, kaydırılmış türdeki Oluşturucu, çok iş parçacıklı senaryolarda bile hiçbir şekilde yeniden çağrılmaz. Bu nedenle, <xref:System.Lazy%601> nesnesi tek bir erişim üzerinde bir özel durum oluşturmaz ve sonraki erişimlerde bir değer döndürmez.  
  
 Bir başlatma yöntemi (`valueFactory` parametresi) alan <xref:System.Lazy%601?displayProperty=nameWithType> Oluşturucu kullandığınızda özel durum önbelleğe alma etkinleştirilir; Örneğin, `Lazy(T)(Func(T))`oluşturucusunu kullandığınızda etkinleştirilir. Oluşturucu aynı zamanda <xref:System.Threading.LazyThreadSafetyMode> bir değer (`mode` parametresi) alırsa, <xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication?displayProperty=nameWithType> veya <xref:System.Threading.LazyThreadSafetyMode.None?displayProperty=nameWithType>belirtin. Bir başlatma yöntemi belirtildiğinde, bu iki mod için özel durum önbelleğe alma etkinleştirilir. Başlatma yöntemi çok basit olabilir. Örneğin, `T`parametresiz oluşturucuyu çağırabilir, ' deki C#`new Lazy<Contents>(() => new Contents(), mode)` veya Visual Basic `New Lazy(Of Contents)(Function() New Contents())`. Başlatma yöntemi belirtmeyen bir <xref:System.Lazy%601?displayProperty=nameWithType> Oluşturucu kullanıyorsanız, `T` için parametresiz Oluşturucu tarafından oluşturulan özel durumlar önbelleğe alınmaz. Daha fazla bilgi için <xref:System.Threading.LazyThreadSafetyMode> sabit listesine bakın.  
  
> [!NOTE]
> `isThreadSafe` Oluşturucu parametresi `false` veya `mode` Oluşturucu parametresi <xref:System.Threading.LazyThreadSafetyMode.None?displayProperty=nameWithType>olarak ayarlanmış bir <xref:System.Lazy%601> nesnesi oluşturursanız, <xref:System.Lazy%601> nesnesine tek bir iş parçacığından erişmeniz veya kendi eşitlemesini sağlamanız gerekir. Bu, özel durum önbelleğe alma da dahil olmak üzere nesnenin tüm yönleri için geçerlidir.  
  
 Önceki bölümde belirtildiği gibi, özel durumları farklı değerlendir <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly?displayProperty=nameWithType> belirterek oluşturulan nesneler <xref:System.Lazy%601>. <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly>, <xref:System.Lazy%601> örneğini başlatmak için birden çok iş parçacığı rekabet edebilir. Bu durumda, özel durumlar önbelleğe alınmaz ve <xref:System.Lazy%601.Value%2A> özelliğine erişme girişimleri, başlatma başarılı olana kadar devam edebilir.  
  
 Aşağıdaki tabloda <xref:System.Lazy%601> oluşturucuların özel durum önbelleğe alma yöntemi özetlenmektedir.  
  
|Oluşturucu|İş parçacığı güvenlik modu|Başlatma yöntemini kullanır|Özel durumlar önbelleğe alındı|  
|-----------------|------------------------|--------------------------------|---------------------------|  
|Geç (T) ()|(<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>)|Hayır|Hayır|  
|Geç (T) (Func (T))|(<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>)|Evet|Evet|  
|Geç (T) (Boole)|`True` (<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>) veya `false` (<xref:System.Threading.LazyThreadSafetyMode.None>)|Hayır|Hayır|  
|Geç (T) (Func (T), Boolean)|`True` (<xref:System.Threading.LazyThreadSafetyMode.ExecutionAndPublication>) veya `false` (<xref:System.Threading.LazyThreadSafetyMode.None>)|Evet|Evet|  
|Geç (T) (LazyThreadSafetyMode)|Kullanıcı tarafından belirtilen|Hayır|Hayır|  
|Geç (T) (Func (T), LazyThreadSafetyMode)|Kullanıcı tarafından belirtilen|Evet|Kullanıcı <xref:System.Threading.LazyThreadSafetyMode.PublicationOnly>belirttiğinde Hayır; Aksi takdirde, evet.|  
  
## <a name="implementing-a-lazy-initialized-property"></a>Geç başlatılmış bir özellik uygulama  
 Yavaş başlatma kullanarak ortak bir özellik uygulamak için, özelliğinin yedekleme alanını bir <xref:System.Lazy%601>olarak tanımlayın ve özelliğin `get` erişimcisinde <xref:System.Lazy%601.Value%2A> özelliğini döndürün.  
  
 [!code-csharp[Lazy#5](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#5)]
 [!code-vb[Lazy#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#5)]  
  
 <xref:System.Lazy%601.Value%2A> özelliği salt okunurdur; Bu nedenle, bunu sunan özelliği `set` erişimcisine sahip değildir. Bir <xref:System.Lazy%601> nesnesi tarafından desteklenen bir okuma/yazma özelliğine ihtiyacınız varsa, `set` erişimci yeni bir <xref:System.Lazy%601> nesnesi oluşturmalı ve bunu yedekleme deposuna atamalıdır. `set` erişimcisi, `set` erişimcisine geçirilen yeni özellik değerini döndüren bir lambda ifadesi oluşturmalı ve bu lambda ifadesini yeni <xref:System.Lazy%601> nesnesi için oluşturucuya iletmelidir. <xref:System.Lazy%601.Value%2A> özelliğinin bir sonraki erişimi, yeni <xref:System.Lazy%601>başlatılmasına neden olur ve <xref:System.Lazy%601.Value%2A> özelliği daha sonra özelliğe atanmış olan yeni değeri döndürür. Bu, bu düzenlemenin nedeni <xref:System.Lazy%601>yerleşik çoklu iş parçacıklı korumaların korunmasının nedenidir. Aksi halde, özellik erişimcileri <xref:System.Lazy%601.Value%2A> özelliği tarafından döndürülen ilk değeri önbelleğe almak ve yalnızca önbelleğe alınmış değeri değiştirmek ve bunu yapmak için kendi iş parçacığı güvenli kodunuzu yazmanız gerekir. Bir <xref:System.Lazy%601> nesnesi tarafından desteklenen bir okuma/yazma özelliği için gereken ek başlatmalar nedeniyle, performans kabul edilemez olabilir. Ayrıca, belirli senaryoya bağlı olarak, ayarlayıcılar ve alıcılar arasında yarış durumlarının önüne geçmek için ek koordinasyon gerekebilir.  
  
## <a name="thread-local-lazy-initialization"></a>İş parçacığı yerel yavaş başlatma  
 Bazı çok iş parçacıklı senaryolarda, her iş parçacığına kendi özel verilerini vermek isteyebilirsiniz. Bu tür veriler, *iş parçacığı yerel verileri*olarak adlandırılır. .NET Framework sürüm 3,5 ve önceki sürümlerde, iş parçacığı yerel yapmak için `ThreadStatic` özniteliğini statik bir değişkene uygulayabilirsiniz. Ancak `ThreadStatic` özniteliği kullanmak, hafif hatalara neden olabilir. Örneğin, temel başlatma deyimleri bile, aşağıdaki örnekte gösterildiği gibi, değişkenin yalnızca ona erişen ilk iş parçacığında başlatılmasına neden olur.  
  
 [!code-csharp[Lazy#6](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#6)]
 [!code-vb[Lazy#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#6)]  
  
 Diğer tüm iş parçacıklarında, değişken varsayılan değeri (sıfır) kullanılarak başlatılır. .NET Framework sürüm 4 ' te bir alternatif olarak, sağladığınız <xref:System.Action%601> temsilcisi tarafından tüm iş parçacıklarında başlatılan örnek tabanlı, iş parçacığı yerel bir değişken oluşturmak için <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> türünü kullanabilirsiniz. Aşağıdaki örnekte, `counter` erişen tüm iş parçacıkları başlangıç değerini 1 olarak görür.  
  
 [!code-csharp[Lazy#7](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#7)]
 [!code-vb[Lazy#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#7)]  
  
 <xref:System.Threading.ThreadLocal%601> nesnesini, <xref:System.Lazy%601>ile aynı şekilde, bu temel farklılıklarla oldukça sarmalar:  
  
- Her iş parçacığı, iş parçacığı yerel değişkenini diğer iş parçacıklarından erişilemeyen kendi özel verilerini kullanarak başlatır.  
  
- <xref:System.Threading.ThreadLocal%601.Value%2A?displayProperty=nameWithType> özelliği okuma-yazma ' dır ve herhangi bir sayıda değişiklik yapılabilir. Bu, özel durum yaymayı etkileyebilir, örneğin bir `get` işlem özel durum oluşturabilir, ancak bir sonraki değer değeri başarıyla başlatabilir.  
  
- Başlatma temsilcisi sağlanmazsa <xref:System.Threading.ThreadLocal%601>, sarmalanmış türünü, türün varsayılan değerini kullanarak başlatır. Bu şekilde, <xref:System.Threading.ThreadLocal%601> <xref:System.ThreadStaticAttribute> özniteliğiyle tutarlıdır.  
  
 Aşağıdaki örnek, `ThreadLocal<int>` örneğine erişen her iş parçacığının, verilerin kendi benzersiz kopyasını aldığı gösterilmektedir.  
  
 [!code-csharp[Lazy#9](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#9)]
 [!code-vb[Lazy#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#9)]  
  
## <a name="thread-local-variables-in-parallelfor-and-foreach"></a>Parallel. for ve ForEach olarak iş parçacığı yerel değişkenleri  
 Paralel olarak veri kaynaklarını yinelemek için <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> yöntemini veya <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> yöntemini kullandığınızda, iş parçacığı yerel verileri için yerleşik desteğe sahip olan aşırı yüklemeleri kullanabilirsiniz. Bu yöntemlerde, iş parçacığı konum oluşturma, verileri oluşturmak, erişmek ve temizlemek için yerel temsilciler kullanılarak elde edilir. Daha fazla bilgi için bkz. [nasıl yapılır: Iş parçacığı yerel değişkenleriyle paralel. for döngüsü yazma](../../standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md) ve [nasıl yapılır: Bölüm Yerel Değişkenleriyle bir Parallel. foreach döngüsü yazma](../../standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-partition-local-variables.md).  
  
## <a name="using-lazy-initialization-for-low-overhead-scenarios"></a>Düşük iş yükü senaryolar için yavaş başlatma kullanma  
 Çok sayıda nesneyi daha yavaş başlatabilmeniz gereken senaryolarda, <xref:System.Lazy%601> her bir nesnenin çok fazla bellek veya çok fazla bilgi işlem kaynağı gerektirip gerektirdiğine karar verebilirsiniz. Ya da, yavaş başlatmanın nasıl açığa çıkmasıyla ilgili sıkı gereksinimlere sahip olabilirsiniz. Bu gibi durumlarda, her bir nesneyi bir <xref:System.Lazy%601>örneğine sarmalamadan yavaş başlatmak için <xref:System.Threading.LazyInitializer?displayProperty=nameWithType> sınıfının `static` (Visual Basic`Shared`) yöntemlerini kullanabilirsiniz.  
  
 Aşağıdaki örnekte, tek bir <xref:System.Lazy%601> nesnesinde bir `Orders` nesnesinin tamamını sarmalama yerine, yalnızca gerekli olmaları durumunda `Order` nesneleri için yavaş başlatılmış tek bir nesne olduğunu varsayalım.  
  
 [!code-csharp[Lazy#10](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#10)]
 [!code-vb[Lazy#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#10)]  
  
 Bu örnekte, başlatma yordamının döngünün her tekrarında çağrıldığına dikkat edin. Çok iş parçacıklı senaryolarda, başlatma yordamını çağırmak için ilk iş parçacığı değeri tüm iş parçacıkları tarafından görülen bir alandır. Sonraki iş parçacıkları da başlatma yordamını çağırır, ancak sonuçları kullanılmaz. Bu tür bir olası yarış durumu kabul edilemez ise, Boole bağımsız değişkeni ve eşitleme nesnesi alan <xref:System.Threading.LazyInitializer.EnsureInitialized%2A?displayProperty=nameWithType> aşırı yüklemesini kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen İş Parçacığı Oluşturma Temelleri](../../standard/threading/managed-threading-basics.md)
- [İş Parçacıkları ve İş Parçacığı Oluşturma](../../standard/threading/threads-and-threading.md)
- [Görev Paralel Kitaplığı (TPL)](../../standard/parallel-programming/task-parallel-library-tpl.md)
- [Nasıl yapılır: Nesnelerin Geç Başlatılmasını Gerçekleştirme](how-to-perform-lazy-initialization-of-objects.md)
