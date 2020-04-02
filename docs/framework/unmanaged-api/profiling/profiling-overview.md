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
ms.openlocfilehash: 3836b562d969726a6587d702d3edf45abb147d10
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588499"
---
# <a name="profiling-overview"></a>Profil Oluşturmaya Genel Bakış

Profil oluşturucu, başka bir uygulamanın yürütülmesini izleyen bir araçtır. Ortak bir dil çalışma zamanı (CLR) profil oluşturucusu profil oluşturma API'sini kullanarak CLR'den ileti alan ve CLR'ye ileti gönderen işlevlerden oluşan dinamik bir bağlantı kitaplığıdır (DLL). Profil oluşturucu DLL, clr tarafından çalışma zamanında yüklenir.

Geleneksel profil oluşturma araçları, uygulamanın yürütülmesini ölçmeye odaklanır. Diğer bir deyişle, her işlevde harcanan zamanı veya uygulamanın bellek kullanımını zaman içinde ölçerler. Profil oluşturma API' si, kod kapsama yardımcı programları ve hatta gelişmiş hata ayıklama yardımcıları gibi daha geniş bir tanı araçları sınıfını hedefler. Bu kullanımların hepsi doğada tanısaldır. Profil oluşturma API'si yalnızca bir uygulamanın yürütülmesini de ölçer. Bu nedenle, profil oluşturma API'si hiçbir zaman uygulamanın kendisi tarafından kullanılmamalıdır ve uygulamanın yürütülmesi profil oluşturucuya bağlı olmamalıdır (veya bundan etkilenmemelidir).

CLR uygulamasının profilini çıkarmak, geleneksel olarak derlenen makine kodunu profillemekten daha fazla destek gerektirir. Bunun nedeni, CLR'nin uygulama etki alanları, çöp toplama, yönetilen özel durum işleme, kodun tam zamanında (JIT) derlemesi (Microsoft ara dilini veya MSIL kodu yerel makine koduna dönüştürme) ve benzeri özellikler gibi kavramları tanıtmasıdır. Geleneksel profil oluşturma mekanizmaları bu özellikleri tanımlayamaz veya bu özellikler hakkında yararlı bilgiler sağlayamaz. Profil oluşturma API'si, CLR'nin ve profilli uygulamanın performansı üzerinde en az etkiye sahip, bu eksik bilgileri verimli bir şekilde sağlar.

Çalışma zamanında JIT derleme profil oluşturma için iyi fırsatlar sağlar. Profil oluşturma API'si, bir profil oluşturucunun JIT derlenmeden önce bir yordam için bellek teki MSIL kod akışını değiştirmesini sağlar. Bu şekilde, profil oluşturucu daha derin bir araştırma gerektiren belirli yordamlara dinamik olarak enstrümantasyon kodu ekleyebilir. Bu yaklaşım geleneksel senaryolarda mümkün olsa da, profil oluşturma API'sini kullanarak CLR için uygulanması çok daha kolaydır.

## <a name="the-profiling-api"></a>Profil Oluşturma API'si

Genellikle, profil oluşturma API yönetilen bir uygulamanın yürütülmesini izleyen bir program dır bir *kod profil oluşturucu*yazmak için kullanılır.

Profil oluşturma API profili olan uygulama ile aynı işleme yüklenir bir profil dll tarafından kullanılır. Profil oluşturucu DLL bir geri arama arabirimi uygular[(ICorProfilerCallback.NET](icorprofilercallback-interface.md) Framework sürüm 1.0 ve 1.1, [ICorProfilerCallback2](icorprofilercallback2-interface.md) sürüm 2.0 ve sonrası). CLR, profil işlemindeki olayların profiloluşturucuya bildirilmesi için bu arabirimdeki yöntemleri çağırır. Profil oluşturucu, profilli uygulamanın durumu hakkında bilgi edinmek için [ICorProfilerInfo](icorprofilerinfo-interface.md) ve [ICorProfilerInfo2](icorprofilerinfo2-interface.md) arayüzlerinde kullanılan yöntemleri kullanarak çalışma süresine geri çağrıyapabilir.

> [!NOTE]
> Yalnızca profil oluşturucu çözümünün veri toplama bölümü profilli uygulamayla aynı işlemde çalışıyor olmalıdır. Tüm kullanıcı arabirimi ve veri analizi ayrı bir işlemle yapılmalıdır.

Aşağıdaki resimde profil oluşturucu DLL'nin profil yapılan uygulama ve CLR ile nasıl etkileşimde bulunduğu gösterilmektedir.

![Profil oluşturma mimarisini gösteren ekran görüntüsü.](./media/profiling-overview/profiling-architecture.png)

### <a name="the-notification-interfaces"></a>Bildirim Arayüzleri

[ICorProfilerCallback](icorprofilercallback-interface.md) ve [ICorProfilerCallback2](icorprofilercallback2-interface.md) bildirim arabirimleri olarak kabul edilebilir. Bu arabirimler [ClassLoadStarted](icorprofilercallback-classloadstarted-method.md), [ClassLoadFinished](icorprofilercallback-classloadfinished-method.md)ve [JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md)gibi yöntemlerden oluşur. CLR bir sınıfı her yüklese veya boşaltsa, bir işlev derlesin ve `ICorProfilerCallback` saire, profiloluşturcunun veya `ICorProfilerCallback2` arabirimindeki ilgili yöntemi çağırır.

Örneğin, bir profil oluşturucu kod performansını iki bildirim işlevi yle ölçebilir: [FunctionEnter2](functionenter2-function.md) ve [FunctionLeave2](functionleave2-function.md). Her bildirimi yalnızca zaman damgaları, sonuçları birikir ve uygulamanın yürütülmesi sırasında hangi işlevlerin en çok CPU veya duvar saati süresini tükettiğini gösteren bir liste çıkarır.

### <a name="the-information-retrieval-interfaces"></a>Bilgi Alma Arayüzleri

Profil leme ile ilgili diğer ana arayüzler [ICorProfilerInfo](icorprofilerinfo-interface.md) ve [ICorProfilerInfo2'dir.](icorprofilerinfo2-interface.md) Profil oluşturucu, çözümlemesi için daha fazla bilgi elde etmek için bu arabirimleri gerektiği gibi çağırır. Örneğin, CLR [FunctionEnter2](functionenter2-function.md) işlevini aradığında, bir işlev tanımlayıcısı sağlar. Profil oluşturucu, işlevin üst sınıfını, adını ve benzeri bilgileri keşfetmek için [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) yöntemini arayarak bu işlev hakkında daha fazla bilgi edinebilir.

## <a name="supported-features"></a>Desteklenen Özellikler

Profil oluşturma API'si, ortak dil çalışma zamanında gerçekleşen çeşitli olaylar ve eylemler hakkında bilgi sağlar. Bu bilgileri, süreçlerin iç işleyişini izlemek ve .NET Framework uygulamanızın performansını analiz etmek için kullanabilirsiniz.

Profil oluşturma API' si, CLR' de meydana gelen aşağıdaki eylemler ve olaylar hakkında bilgi alır:

- CLR başlatma ve kapatma olayları.

- Uygulama etki alanı oluşturma ve kapatma olayları.

- Montaj yükleme ve boşaltma olayları.

- Modül yükleme ve boşaltma olayları.

- COM vtable oluşturma ve imha olayları.

- Tam zamanında (JIT) derleme ve kod pitching olaylar.

- Sınıf yükleme ve boşaltma olayları.

- İş parçacığı oluşturma ve imha olayları.

- İşlev giriş ve çıkış olayları.

- Özel durum.

- Yönetilen ve yönetilmeyen kod yürütme arasındaki geçişler.

- Farklı çalışma zamanı bağlamları arasında geçişler.

- Çalışma zamanı askıya almalar hakkında bilgi.

- Çalışma zamanı bellek yığını ve çöp toplama etkinliği hakkında bilgi.

Profil oluşturma API'si, COM uyumlu herhangi bir dilden çağrılabilir.

API, CPU ve bellek tüketimi açısından etkilidir. Profil oluşturma, yanıltıcı sonuçlara neden olacak kadar önemli olan profilli uygulamada değişiklikler içermez.

Profil oluşturma API'si hem örnekleme hem de örnekleme yapmayan profilciler için yararlıdır. Örnekleme *profiloluşturucusu* profili normal saat işaretlerinde inceler, örneğin, 5 milisaniye arayla. Örnekleme olmayan bir *profil oluşturucu,* olaya neden olan iş parçacığıyla eşzamanlı olarak bir olay hakkında bilgilendirilir.

### <a name="unsupported-functionality"></a>Desteklenmeyen İşlev

Profil oluşturma API'si aşağıdaki işlevselliği desteklemez:

- Geleneksel Win32 yöntemleri kullanılarak profillenilmesi gereken yönetilmeyen kod. Ancak, CLR profil oluşturucu, yönetilen ve yönetilmeyen kod arasındaki sınırları belirlemek için geçiş olayları içerir.

- Kendi kodlarını boy odaklı programlama gibi amaçlarla değiştiren kendi kendini değiştiren uygulamalar.

- Profil oluşturma API'si bu bilgileri sağlamadığından, sınır denetimi. CLR, yönetilen tüm kodların sınır denetimi için içsel destek sağlar.

- Aşağıdaki nedenlerle desteklenmeyen uzaktan profil oluşturma:

  - Uzaktan profil oluşturma yürütme süresini uzalar. Profil oluşturma arabirimlerini kullandığınızda, profil oluşturma sonuçlarının gereksiz yere etkilenmemesi için yürütme süresini en aza indirmeniz gerekir. Yürütme performansı izlenirken bu özellikle doğrudur. Ancak, profil oluşturma arabirimleri bellek kullanımını izlemek veya yığın çerçeveleri, nesneler ve benzeri hakkında çalışma zamanı bilgileri elde etmek için kullanıldığında uzaktan profil oluşturma bir sınırlama değildir.

  - CLR kod profillayıcısı, profilli uygulamanın çalıştırıldığı yerel bilgisayarda çalışma süresiyle birlikte bir veya daha fazla geri arama arabirimi kaydetmelidir. Bu, uzak kod profiloluşturabilme yeteneğini sınırlar.

## <a name="notification-threads"></a>Bildirim Konuları

Çoğu durumda, bir olay oluşturan iş parçacığı da bildirimleri yürütür. Bu tür bildirimlerin (örneğin, [FunctionEnter](functionenter-function.md) ve [FunctionLeave)](functionleave-function.md) `ThreadID`açık bir şekilde sağlanmasıgerekmez. Ayrıca, profil oluşturucu, etkilenen iş parçacığına dayalı `ThreadID` olarak çözümleme bloklarını küresel depolamada dizine ekinyapmak yerine çözüm leme bloklarını depolamak ve güncelleştirmek için iş parçacığı yerel depolamasını kullanmaya karar verebilir.

Bu geri aramaların seri hale getirilemediğini unutmayın. Kullanıcılar, iş parçacığı namına veri yapıları oluşturarak ve birden çok iş parçacığından paralel erişimi önlemek için gerektiğinde profil oluşturucu kodunu kilitleyerek kodlarını korumalıdır. Bu nedenle, bazı durumlarda alışılmadık bir geri arama dizisi alabilirsiniz. Örneğin, yönetilen bir uygulamanın aynı kodu çalıştıran iki iş parçacığı yumurtladığını varsayalım. Bu durumda, [iCorProfilerCallback almak mümkündür::JITCompilationBir](icorprofilercallback-jitcompilationstarted-method.md) iş parçacığı bazı işlev `FunctionEnter` ve ICorProfilerCallback almadan önce diğer iş parçacığı bir geri arama için olay [başladı::JITCompilationFinished](icorprofilercallback-jitcompilationfinished-method.md) geri arama. Bu durumda, kullanıcı henüz `FunctionEnter` tam olarak tam zamanında (JIT) derlenmiş olmayan bir işlev için bir geri arama alır.

## <a name="security"></a>Güvenlik

Profil oluşturucu DLL, ortak dil çalışma zamanı yürütme altyapısının bir parçası olarak çalışan yönetilmeyen bir DLL'dir. Sonuç olarak, profil oluşturucu DLL'deki kod yönetilen kod erişim güvenliği kısıtlamalarına tabi değildir. Profil oluşturucu DLL üzerindeki tek sınırlamalar, işletim sistemi tarafından profilli uygulamayı çalıştıran kullanıcıya uygulanan sınırlamalardır.

Profiler yazarları güvenlikle ilgili sorunları önlemek için uygun önlemleri almalıdır. Örneğin, yükleme sırasında, kötü amaçlı bir kullanıcının değiştirememesi için bir profil oluşturucu DLL'nin bir erişim denetim listesine (ACL) eklenmesi gerekir.

## <a name="combining-managed-and-unmanaged-code-in-a-code-profiler"></a>Yönetilen ve Yönetilmeyen Kodu Kod Profilleyicisinde Birleştirme

Yanlış yazılmış bir profil oluşturucu, kendisine dairesel başvurular alabildiği gibi öngörülemeyen davranışlara neden olabilir.

CLR profil oluşturma API'sinin gözden geçirilmesi, COM interop veya dolaylı aramalar aracılığıyla birbirini çağıran yönetilen ve yönetilmeyen bileşenler içeren bir profil oluşturabileceğiniz izlenimini oluşturabilir.

Bu, tasarım açısından mümkün olsa da, profil oluşturma API'si yönetilen bileşenleri desteklemez. Bir CLR profiloluşturucu tamamen yönetilmemiş olmalıdır. Yönetilen ve yönetilmeyen kodu clr profiloluşturcayında birleştirme girişimleri erişim ihlallerine, program hatasına veya kilitlenmelere neden olabilir. Profil oluşturucunun yönetilen bileşenleri olayları yönetilmeyen bileşenlerine geri döndürecek ve bu da yönetilen bileşenleri yeniden çağırarak dairesel başvurulara yol açacaktır.

Bir CLR profiloluşturucunun yönetilen kodu güvenli bir şekilde arayabildiği tek konum, bir yöntemin Microsoft ara dili (MSIL) gövdesindedir. MSIL gövdesini değiştirmek için önerilen [uygulama, ICorProfilerCallback4](icorprofilercallback4-interface.md) arabirimindeki JIT yeniden derleme yöntemlerini kullanmaktır.

MSIL'i değiştirmek için eski enstrümantasyon yöntemlerini kullanmak da mümkündür. Bir işlevin tam zamanında (JIT) derlemesi tamamlanmadan önce, profil oluşturucu bir yöntemin MSIL gövdesine yönetilen çağrıları ekleyebilir ve ardından JIT-derleme yapabilir [(Bkz. ICorProfilerInfo::GetILFunctionBody](icorprofilerinfo-getilfunctionbody-method.md) yöntemi). Bu teknik, yönetilen kodun seçici araçları için veya JIT hakkında istatistik ve performans verileri toplamak için başarıyla kullanılabilir.

Alternatif olarak, bir kod profilleyicisi, yönetilmeyen koda çağıran her yönetilen işlevin MSIL gövdesine yerel kancalar ekleyebilir. Bu teknik enstrümantasyon ve kapsama için kullanılabilir. Örneğin, bir kod profilleyicisi, bloğun yürütüldünlü olduğundan emin olmak için her MSIL bloğundan sonra enstrümantasyon kancaları ekleyebilir. Bir yöntemin MSIL gövdesinin modifikasyonu çok hassas bir işlemdir ve dikkate alınması gereken birçok faktör vardır.

## <a name="profiling-unmanaged-code"></a>Yönetilmeyen Kodu Profil Oluşturma

Ortak dil çalışma zamanı (CLR) profil oluşturma API, yönetilmeyen kodu profil oluşturma için en az destek sağlar. Aşağıdaki işlevsellik sağlanır:

- Yığın zincirlerinin numaralandırması. Bu özellik, yönetilen kod ve yönetilmeyen kod arasındaki sınırı belirlemek için bir kod profiloluşturucu sağlar.

- Yığın zincirinin yönetilen koda mı yoksa yerel koda mı karşılık olduğunu belirleme.

.NET Framework sürümleri 1.0 ve 1.1'de, bu yöntemler CLR hata ayıklama API'sinin işlem içi alt kümesi aracılığıyla kullanılabilir. Bunlar CorDebug.idl dosyasında tanımlanır.

.NET Framework 2.0 ve sonraki durumlarda, bu işlevsellik için [ICorProfilerInfo2::DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) yöntemini kullanabilirsiniz.

## <a name="using-com"></a>COM'u kullanma

Profil oluşturma arabirimleri COM arabirimleri olarak tanımlansa da, ortak dil çalışma süresi (CLR) aslında bu arabirimleri kullanmak için COM'u başlatmaz. Bunun nedeni, yönetilen uygulama nın istenen iş parçacığı modelini belirtme şansı elde etmeden önce [CoInitialize](/windows/desktop/api/objbase/nf-objbase-coinitialize) işlevini kullanarak iş parçacığı modelini ayarlamak zorunda kalmamaktır. Benzer şekilde, profil oluşturucunun `CoInitialize`kendisi aramamalıdır, çünkü profillegösterilen uygulamayla uyumsuz bir iş parçacığı modeli seçebilir ve uygulamanın başarısız olmasına neden olabilir.

## <a name="call-stacks"></a>Çağrı Yığınları

Profil oluşturma API'si çağrı yığınları elde etmek için iki yol sağlar: çağrı yığınlarının seyrek bir şekilde toplanmasını sağlayan bir yığın anlık görüntü yöntemi ve her anda çağrı yığınını izleyen bir gölge yığını yöntemi.

### <a name="stack-snapshot"></a>Anlık Görüntü Yığını

Yığın anlık görüntüsü, bir iş parçacığı yığınının bir anda zaman içinde izlenmesidir. Profil oluşturma API yığını üzerinde yönetilen işlevlerin izlenmesini destekler, ancak profillenmemiş işlevlerin izlenmesini profiloluşturcunun kendi yığın yürütücüse bırakır.

Yönetilen yığınları yürümek için profiloluşturucu program hakkında daha fazla bilgi için, bu dokümantasyon kümesinde [ICorProfilerInfo2::DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) yöntemi ve [Profiler Stack Yürüyüş .NET Framework 2.0: Temelleri ve Ötesi](https://docs.microsoft.com/previous-versions/dotnet/articles/bb264782(v=msdn.10)).

### <a name="shadow-stack"></a>Gölge Yığını

Anlık görüntü yöntemini çok sık kullanmak hızlı bir performans sorunu oluşturabilir. Yığın izlerini sık sık almak istiyorsanız, profilciniz bunun yerine [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md), [FunctionTailcall2](functiontailcall2-function.md)ve [ICorProfilerCallback2](icorprofilercallback2-interface.md) özel durum geri aramaları kullanarak bir gölge yığını oluşturmalıdır. Gölge yığını her zaman geçerlidir ve yığın anlık görüntüsü gerektiğinde hızla depolama alanına kopyalanabilir.

Gölge yığını işlev bağımsız değişkenleri, döndürme değerleri ve genel anlık bilgiler edinebilir. Bu bilgiler yalnızca gölge yığını aracılığıyla kullanılabilir ve denetim bir işleve verildiğinde elde edilebilir. Ancak, bu bilgiler daha sonra işlevin çalıştırılması sırasında kullanılamayabilir.

## <a name="callbacks-and-stack-depth"></a>Geri Aramalar ve Yığın Derinliği

Profiler geri aramaları çok yığın kısıtlı durumlarda verilebilir ve profilci geri aramasında yığın taşma hemen bir işlem çıkışına yol açar. Bir profil oluşturucu, geri aramalara yanıt olarak mümkün olduğunca az yığın kullandığınızdan emin olmalıdır. Profil oluşturucu, yığın taşmasına karşı sağlam olan işlemlere karşı kullanılmak üzere tasarlanmıştırsa, profilcinin kendisi de yığın taşmasını tetiklemekten kaçınmalıdır.

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Profil Oluşturma Ortamını Ayarlama](setting-up-a-profiling-environment.md)|Profil oluşturucunun nasıl başharfe atılabildiğini, olay bildirimlerini nasıl ayarladığını ve bir Windows Hizmetinin profilini nasıl oluşturup oluşturup oluşturup oluşturup oluşturup oluşturup oluşturup oluşturup oluşturup oluşturup oluşturup oluşturup oluşturup oluşturup oluşturup oluşturup oluşturup oluşturup|
|[Profil Oluşturma Arabirimleri](profiling-interfaces.md)|Profil oluşturma API'sinin kullandığı yönetilmeyen arabirimleri açıklar.|
|[Profil Oluşturma Genel Statik İşlevleri](profiling-global-static-functions.md)|Profil oluşturma API'sinin kullandığı yönetilmeyen genel statik işlevleri açıklar.|
|[Profil Oluşturma Sabit Listeleri](profiling-enumerations.md)|Profil oluşturma API'sinin kullandığı yönetilmeyen sayısallaştırmaları açıklar.|
|[Profil Oluşturma Yapıları](profiling-structures.md)|Profil oluşturma API'sinin kullandığı yönetilmeyen yapıları açıklar.|
