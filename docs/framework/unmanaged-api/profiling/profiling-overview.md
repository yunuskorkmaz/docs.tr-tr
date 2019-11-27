---
title: Profil Oluşturmaya Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- managed code, profiling API support
- unmanaged code, combining with managed code in profiling
- notification threads [.NET Framework profiling]
- unmanaged code, profiling
- profiling API [.NET Framework], and COM
- profiling API [.NET Framework], unmanaged code profiling
- profilers, writing
- profiling API [.NET Framework], call stacks
- code profilers, writing
- profiling API [.NET Framework], security considerations
- profiling API [.NET Framework], managed code support
- common language runtime, profiling
- profiling API [.NET Framework], notification threads
- call stacks [.NET Framework profiling]
- profiling API [.NET Framework], stack depth
- common language runtime, writing a profiler
- profiling API [.NET Framework], information retrieval interfaces
- shadow stacks [.NET Framework profiling]
- COM, using in the profiling API
- stack snapshots [.NET Framework profiling]
- profiling API [.NET Framework], supported features
- profiling API [.NET Framework], overview
- security, profiling API considerations
- stack depth [.NET Framework profiling]
ms.assetid: 864c2344-71dc-46f9-96b2-ed59fb6427a8
ms.openlocfilehash: 08015e2e5918ca64f601ec912a906cfb6319ed6c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427093"
---
# <a name="profiling-overview"></a>Profil Oluşturmaya Genel Bakış

Profil Oluşturucu, başka bir uygulamanın yürütülmesini izleyen bir araçtır. Ortak dil çalışma zamanı (CLR) profil oluşturucu, profil oluşturma API 'sini kullanarak, CLR 'ye ileti alan ve iletileri gönderen işlevlerden oluşan bir dinamik bağlantı kitaplığıdır (DLL). Profil oluşturucu DLL, çalışma zamanında CLR tarafından yüklenir.

Geleneksel profil oluşturma araçları, uygulamanın yürütülmesini ölçmeye odaklanmaktadır. Yani, her işlevde harcanan süreyi veya zaman içinde uygulamanın bellek kullanımını ölçirler. Profil oluşturma API 'SI, kod kapsamı yardımcı programları ve hatta gelişmiş hata ayıklama yardımları gibi daha geniş bir tanılama araçları sınıfını hedefler. Bu kullanımlar doğası gereği tüm tanılardır. Profil oluşturma API 'SI yalnızca ölçülere sahip olmakla kalmaz, ayrıca bir uygulamanın yürütülmesini de izler. Bu nedenle, profil oluşturma API 'SI asla uygulamanın kendisi tarafından kullanılmamalıdır ve uygulamanın yürütülmesi profil oluşturucunun, (veya tarafından etkilenmemelidir) bağlı olmamalıdır.

CLR uygulamasının profilini oluşturmak, profil oluşturma genel olarak derlenmiş makine kodundan daha fazla destek gerektirir. Bunun nedeni, CLR 'nin uygulama etki alanları, çöp toplama, yönetilen özel durum işleme, tam zamanında (JıT) kod derlemesi (Microsoft ara dili veya MSIL, kod yerel makine koduna dönüştürme) ve benzer şekilde kavram sağlaması özelliklerinde. Geleneksel profil oluşturma mekanizmaları, bu özelliklerle ilgili yararlı bilgileri tanımlayamıyor veya sağlamıyor. Profil oluşturma API 'SI bu eksik bilgileri, CLR ve profili oluşturulmuş uygulamanın performansı üzerinde en az etkiyle verimli bir şekilde sağlar.

Çalışma zamanında JıT derlemesi, profil oluşturma için iyi fırsatlar sağlar. Profil oluşturma API 'SI, bir profil oluşturucunun JıT derlenmesinden önce bir yordam için bellek içi MSIL kod akışını değiştirmesini sağlar. Bu şekilde, Profil Oluşturucu daha derin araştırma gerektiren belirli yordamlara dinamik olarak izleme kodu ekleyebilir. Bu yaklaşım geleneksel senaryolarda mümkün olsa da, profil oluşturma API 'SI kullanılarak CLR için uygulanması çok daha kolaydır.

## <a name="the-profiling-api"></a>Profil oluşturma API 'SI

Genellikle, profil oluşturma API 'SI, yönetilen bir uygulamanın yürütülmesini izleyen bir program olan *kod profil oluşturucu*yazmak için kullanılır.

Profil oluşturma API 'si, profili oluşturulan uygulamayla aynı işleme yüklenen bir profil oluşturucu DLL tarafından kullanılır. Profil oluşturucu DLL, .NET Framework sürüm 1,0 ve 1,1 ' de bir[geri çağırma arabirimi (](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) sürüm 2,0 ve üzeri) uygular. CLR, profili oluşturulan işlemdeki olayların profil oluşturucuyu bilgilendirmek için bu arabirimdeki yöntemleri çağırır. Profil Oluşturucu, profili oluşturulmuş uygulamanın durumu hakkında bilgi almak için [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) ve [ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md) arabirimlerindeki yöntemleri kullanarak çalışma zamanına geri çağırabilir.

> [!NOTE]
> Profil Oluşturucu çözümünün yalnızca veri toplama bölümü, profili oluşturulmuş uygulamayla aynı işlemde çalışmalıdır. Tüm Kullanıcı arabirimi ve veri analizi ayrı bir işlemde gerçekleştirilmelidir.

Aşağıdaki çizimde profil oluşturucu DLL 'nin profili oluşturulan uygulamayla ve CLR ile nasıl etkileşimde bulunduğu gösterilmektedir.

![Profil oluşturma mimarisini gösteren ekran görüntüsü.](./media/profiling-overview/profiling-architecture.png)

### <a name="the-notification-interfaces"></a>Bildirim arabirimleri

[ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) ve [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) , bildirim arabirimleri olarak düşünülebilir. Bu arabirimler [ClassLoadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md), [ClassLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)ve [JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)gibi yöntemlerden oluşur. CLR bir sınıfı yüklediğinde veya kaldırdığında, bir işlevi derlediğinde ve bu durumda, profil oluşturucunun `ICorProfilerCallback` veya `ICorProfilerCallback2` arabiriminde karşılık gelen yöntemi çağırır.

Örneğin, bir profil oluşturucu iki bildirim işlevi aracılığıyla kod performansını ölçebilir: [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) ve [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md). Her bildirime yalnızca zaman damgası oluşturur, sonuçları birikir ve uygulamanın yürütülmesi sırasında en fazla CPU veya duvar saati zamanını hangi işlevlerin tükettiğini belirten bir liste verir.

### <a name="the-information-retrieval-interfaces"></a>Bilgi alma arabirimleri

Profil oluşturma ile ilgili diğer ana arabirimler [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) ve [ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md). Profil Oluşturucu, analizine yardımcı olmak üzere daha fazla bilgi edinmek için bu arabirimleri gerektiği şekilde çağırır. Örneğin, CLR [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) işlevini her çağırdığında, bir işlev tanımlayıcısı sağlar. Profil Oluşturucu, işlevin üst sınıfını, adını ve benzerlerini saptamak için [ICorProfilerInfo2:: GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) metodunu çağırarak, bu işlev hakkında daha fazla bilgi alabilir.

## <a name="supported-features"></a>Desteklenen Özellikler

Profil oluşturma API 'SI, ortak dil çalışma zamanında oluşan çeşitli olaylar ve eylemler hakkında bilgi sağlar. Bu bilgileri, işlemlerin iç işleyişini izlemek ve .NET Framework uygulamanızın performansını analiz etmek için kullanabilirsiniz.

Profil oluşturma API 'SI, CLR 'de oluşan aşağıdaki eylemler ve olaylar hakkında bilgi alır:

- CLR başlatma ve başlatma olayları.

- Uygulama etki alanı oluşturma ve kapanıyor olayları.

- Derleme yükleme ve kaldırma olayları.

- Modül yükleme ve kaldırma olayları.

- COM vtable oluşturma ve yok etme olayları.

- Tam zamanında (JıT) derleme ve kod temelli olaylar.

- Sınıf yükleme ve kaldırma olayları.

- İş parçacığı oluşturma ve yok etme olayları.

- İşlev girdisi ve çıkış olayları.

- Özel durumlar.

- Yönetilen ve yönetilmeyen kod yürütme arasındaki geçişler.

- Farklı çalışma zamanı bağlamları arasındaki geçişler.

- Çalışma zamanı getirilmesi hakkında bilgi.

- Çalışma zamanı bellek yığını ve çöp toplama etkinliği hakkında bilgi.

Profil oluşturma API 'SI (yönetilen olmayan) COM uyumlu dillerden çağrılabilir.

API, CPU ve bellek tüketimine göre etkilidir. Profil oluşturma, profili oluşturulmuş uygulamada yanıltıcı sonuçlara neden olacak kadar önemli değişiklikler içermez.

Profil oluşturma API 'SI hem örnekleme hem de örnekleme olmayan profil oluşturucular için faydalıdır. Bir *örnekleme profil oluşturucu* , profili düzenli saat işaretleri, yani 5 milisaniyelik olarak inceler. *Örneklemesi olmayan bir profil oluşturucu* , olaya neden olan iş parçacığı ile eşzamanlı olarak bir olay hakkında bilgilendirilir.

### <a name="unsupported-functionality"></a>Desteklenmeyen İşlev

Profil oluşturma API 'SI aşağıdaki işlevleri desteklemez:

- Geleneksel Win32 yöntemleri kullanılarak profili oluşturulmuş olması gereken yönetilmeyen kod. Ancak, CLR Profiler yönetilen ve yönetilmeyen kod arasındaki sınırları belirleyecek geçiş olaylarını içerir.

- En boy odaklı programlama gibi amaçlar için kendi kodlarını değiştiren uygulamaları kendi kendine değiştirme.

- Sınır denetlemesi, profil oluşturma API 'SI bu bilgileri sağlamadığı için. CLR, tüm yönetilen kodların sınır denetlemesi için iç destek sağlar.

- Aşağıdaki nedenlerden dolayı desteklenmeyen uzak profil oluşturma:

  - Uzaktan profil oluşturma, yürütme süresini uzatır. Profil oluşturma arabirimlerini kullanırken, profil oluşturma sonuçlarının etkilenmemesi etkilenmemesi için yürütme süresini en aza indirmiş olmanız gerekir. Bu özellikle, yürütme performansı izlendiğinde geçerlidir. Ancak, profil oluşturma arabirimleri bellek kullanımını izlemek veya yığın çerçeveleri, nesneleri vb. hakkında çalışma zamanı bilgileri elde etmek için kullanıldığında uzak profil oluşturma bir sınırlama değildir.

  - CLR kodu profil oluşturucu, profili oluşturulan uygulamanın çalıştığı yerel bilgisayardaki çalışma zamanına sahip bir veya daha fazla geri çağırma arabirimi kaydetmelidir. Bu, uzak kod profil Oluşturucu oluşturma özelliğini kısıtlar.

- Yüksek kullanılabilirlik gereksinimlerine sahip üretim ortamlarında profil oluşturma. Profil oluşturma API 'SI, geliştirme zamanı tanılamayı destekleyecek şekilde oluşturulmuştur. Üretim ortamlarını desteklemek için gereken kapsamlı testi henüz yapılmamıştır.

## <a name="notification-threads"></a>Bildirim Iş parçacıkları

Çoğu durumda, bir olayı oluşturan iş parçacığı de bildirimleri yürütür. Bu tür bildirimlerin (örneğin, [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) ve [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md)) açık `ThreadID`sağlaması gerekmez. Ayrıca, profil oluşturucu, etkilenen iş parçacığının `ThreadID` bağlı olarak genel depolamada analiz bloklarını dizinlemek yerine çözümleme bloklarını depolamak ve güncelleştirmek için iş parçacığı yerel depolama 'yı kullanmaya karar verebilir.

Bu geri çağırmaların serileştirilmediğini unutmayın. Kullanıcılar, iş parçacığı açısından güvenli veri yapıları oluşturarak ve birden çok iş parçacığından paralel erişimi engellemek için gerektiğinde profil oluşturucu kodunu kilitleyerek kendi kodlarını korumalıdır. Bu nedenle, bazı durumlarda olağan dışı bir geri çağırma sırası alabilirsiniz. Örneğin, yönetilen bir uygulamanın özdeş kodu yürüten iki iş parçacığını sağladığını varsayalım. Bu durumda, bir iş parçacığından bazı işlevleri için [ICorProfilerCallback:: JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) olayını ve [ICorProfilerCallback:: JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) geri aramasını almadan önce diğer iş parçacığından bir `FunctionEnter` geri aramasını almak mümkündür. Bu durumda, Kullanıcı henüz derlenmiş tam zamanında (JıT) olmayan bir işlev için `FunctionEnter` geri araması alacaktır.

## <a name="security"></a>Güvenlik

Profil oluşturucu DLL, ortak dil çalışma zamanı yürütme altyapısının bir parçası olarak çalışan yönetilmeyen bir DLL 'dir. Sonuç olarak, profil oluşturucu DLL 'deki kod, yönetilen kod erişim güvenliği kısıtlamalarına tabi değildir. Profil oluşturucu DLL 'deki tek sınırlamalar, profili oluşturulmuş uygulamayı çalıştıran kullanıcının işletim sistemi tarafından uygulanan olanlardır.

Profil Oluşturucu yazarları güvenlikle ilgili sorunlardan kaçınmak için uygun önlemleri almalıdır. Örneğin, yükleme sırasında, kötü niyetli bir kullanıcının değiştirememesi için bir erişim denetim listesine (ACL) bir profil oluşturucu DLL 'SI eklenmelidir.

## <a name="combining-managed-and-unmanaged-code-in-a-code-profiler"></a>Yönetilen ve yönetilmeyen kodu bir kod Profilcisi ile birleştirme

Yanlış yazılmış bir profil oluşturucu kendi kendine döngüsel başvurulara neden olabilir ve bu da öngörülemeyen davranışa yol açabilir.

CLR profil oluşturma API 'SI gözden geçirmesi, COM birlikte çalışma veya dolaylı çağrılar aracılığıyla birbirlerine çağrı yapan yönetilen ve yönetilmeyen bileşenleri içeren bir profil oluşturucu yazabileceğiniz izlenime yol açabilir.

Bu bir tasarım perspektifinden mümkün olsa da, profil oluşturma API 'SI yönetilen bileşenleri desteklemez. CLR profiler tamamen yönetilmeyen olmalıdır. Yönetilen ve yönetilmeyen kodu bir CLR Profiler 'da birleştirme girişimleri, erişim ihlallerine, program hatasına veya kilitlenmelere neden olabilir. Profil oluşturucunun yönetilen bileşenleri, olayları yönetilmeyen bileşenlerine geri tetikleyecektir. Bu, daha sonra yönetilen bileşenleri yeniden çağırıp döngüsel başvurular oluşmasına neden olur.

Bir CLR Profiler 'ın yönetilen kodu güvenli bir şekilde çağırabildiği tek konum bir yöntemin Microsoft ara dili (MSIL) gövdesinden oluşur. MSIL gövdesini değiştirmek için önerilen yöntem, [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) arabirimindeki JIT yeniden derleme yöntemlerini kullanmaktır.

Ayrıca, MSIL 'yi değiştirmek için eski izleme yöntemlerini kullanmak da mümkündür. Bir işlevin tam zamanında (JıT) derlenmesi tamamlanmadan önce, profil oluşturucu bir yöntemin MSIL gövdesine yönetilen çağrılar ekleyebilir ve ardından bunu JıT-derle (bkz. [ICorProfilerInfo:: GetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbody-method.md) yöntemi). Bu teknik, yönetilen kodun seçmeli araçları için veya JıT hakkında istatistik ve performans verileri toplamak için başarılı bir şekilde kullanılabilir.

Alternatif olarak, bir kod Profilleyicisi, yönetilmeyen koda çağıran her yönetilen işlevin MSIL gövdesine yerel kancalar ekleyebilir. Bu teknik, izleme ve kapsam için kullanılabilir. Örneğin, bir kod Profilcisi, bloğun yürütüldüğünü sağlamak için her MSIL bloğundan sonra izleme kancaları ekleyebilir. Bir yöntemin MSIL gövdesinin değiştirilmesi çok önemli bir işlemdir ve dikkate alınması gereken birçok etken vardır.

## <a name="profiling-unmanaged-code"></a>Yönetilmeyen kod profili oluşturma

Ortak dil çalışma zamanı (CLR) profil oluşturma API 'SI, yönetilmeyen kod profili oluşturma için en düşük desteği sağlar Aşağıdaki işlevsellik verilmiştir:

- Yığın zincirlerinin numaralandırılması. Bu özellik, yönetilen kod ve yönetilmeyen kod arasındaki sınırı belirlemede kod Profilcisi sağlar.

- Yığın zincirinin yönetilen koda mı yoksa yerel koda mı karşılık geldiğini belirleme.

1,0 ve 1,1 .NET Framework sürümlerinde, bu yöntemler CLR hata ayıklama API 'sinin işlem içi alt kümesi aracılığıyla kullanılabilir. CorDebug. IDL dosyasında tanımlanmıştır.

.NET Framework 2,0 ve sonrasında, bu işlevsellik için [ICorProfilerInfo2::D oStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) yöntemini kullanabilirsiniz.

## <a name="using-com"></a>COM kullanarak

Profil oluşturma arabirimleri COM arabirimleri olarak tanımlansa da, ortak dil çalışma zamanı (CLR) bu arabirimleri kullanmak için gerçekte COM 'u başlatılmaz. Bunun nedeni, yönetilen uygulama, istenen iş parçacığı modelini belirtmek için bir şansına sahip olmadan önce [CoInitialize](/windows/desktop/api/objbase/nf-objbase-coinitialize) işlevini kullanarak iş parçacığı modelini ayarlamayı kullanmaktan kaçınmaktır. Benzer şekilde, profil oluşturucunun kendisi de `CoInitialize`çağırmamalıdır, çünkü profili oluşturulan uygulamayla uyumsuz bir iş parçacığı modeli seçip uygulamanın başarısız olmasına neden olabilir.

## <a name="call-stacks"></a>Çağrı yığınları

Profil oluşturma API 'SI, çağrı yığınlarının alınması için iki yol sunar: çağrı yığınlarının seyrek toplanmaya olanak tanıyan bir yığın anlık görüntüsü yöntemi ve her anında çağrı yığınını izleyen bir gölge yığın yöntemi.

### <a name="stack-snapshot"></a>Yığın anlık görüntüsü

Yığın anlık görüntüsü, zaman içinde anlık bir iş parçacığı yığınının bir izlemesinde. Profil oluşturma API 'SI yığında yönetilen işlevlerin izlenmesini destekler, ancak yönetilmeyen işlevlerin izlenmesini profil oluşturucunun kendi yığın Denetçisi ' ne bırakır.

Profil oluşturucunun yönetilen yığınları izlenecek şekilde programlamanın nasıl yapılacağı hakkında daha fazla bilgi için, bu belge kümesindeki [ICorProfilerInfo2::D oStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) yöntemine ve [profiler Stack .NET Framework 2,0: temelleri ve ötesinde](https://go.microsoft.com/fwlink/?LinkId=73638)inceleyin.

### <a name="shadow-stack"></a>Gölge yığını

Snapshot yönteminin çok sık kullanılması, hızlı bir şekilde performans sorunu oluşturabilir. Yığın izlemelerini sık sık almak istiyorsanız, profil oluşturucunun bunun yerine [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)ve [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) özel durum geri çağırmaları kullanarak bir gölge yığını oluşturması gerekir. Gölge yığını her zaman geçerli olur ve yığın anlık görüntüsü gerektiğinde hızlı bir şekilde depolamaya kopyalanabilir.

Bir gölge yığın, işlev bağımsız değişkenlerini, dönüş değerlerini ve genel örneklemeler hakkında bilgileri alabilir. Bu bilgiler yalnızca gölge yığın aracılığıyla kullanılabilir ve denetim bir işleve geldiğinde elde edilebilir. Ancak, bu bilgiler işlevin çalıştırılması sırasında daha sonra kullanılamayabilir.

## <a name="callbacks-and-stack-depth"></a>Geri çağrılar ve yığın derinliği

Profiler geri çağırmaları çok yığın kısıtlı koşullarda verilebilir ve bir profil oluşturucu geri aramasında yığın taşması anında işlem çıkışı oluşmasına neden olur. Bir profil oluşturucunun geri çağırmaları yanıtlamak için olabildiğince az yığın olarak kullanılması gerekir. Profil oluşturucunun yığın taşmasına karşı dayanıklı işlemlere karşı kullanılması amaçlanıyorsa, profil oluşturucunun kendisi de yığın taşmasını tetiklememelidir.

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Profil Oluşturma Ortamını Ayarlama](../../../../docs/framework/unmanaged-api/profiling/setting-up-a-profiling-environment.md)|Profil oluşturucuyu başlatma, olay bildirimlerini ayarlama ve bir Windows hizmeti profili oluşturma hakkında bilgiler sağlar.|
|[Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)|Profil oluşturma API 'sinin kullandığı yönetilmeyen arabirimleri açıklar.|
|[Profil Oluşturma Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)|Profil oluşturma API 'sinin kullandığı yönetilmeyen genel statik işlevleri açıklar.|
|[Profil Oluşturma Sabit Listeleri](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)|Profil oluşturma API 'sinin kullandığı yönetilmeyen numaralandırmaları açıklar.|
|[Profil Oluşturma Yapıları](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)|Profil oluşturma API 'sinin kullandığı yönetilmeyen yapıları açıklar.|
