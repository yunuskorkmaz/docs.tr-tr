---
title: "Profil Oluşturmaya Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: "27"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6d7918a369b5a5656fa2e059bdaaf6c211bd022c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="profiling-overview"></a>Profil Oluşturmaya Genel Bakış
<a name="top"></a>Bir profil oluşturucu başka bir uygulamanın yürütülmesini izleyen bir araçtır. Ortak dil çalışma zamanı (CLR) profil oluşturucu ileti almak ve profil oluşturma API kullanarak için CLR iletileri göndermek işlevler oluşan bir dinamik bağlantı kitaplığı (DLL) olur. Profil Oluşturucu DLL çalışma zamanında CLR tarafından yüklenir.  
  
 Geleneksel profil oluşturma araçları, uygulamanın yürütülmesini ölçmeye odaklanın. Diğer bir deyişle, her işlev veya uygulama zamanla bellek kullanımını harcanan süreyi ölçer. Profil oluşturma API kod kapsamı yardımcı programları gibi tanılama araçları daha geniş bir sınıfı hedefler ve hatta yardımları hata ayıklama Gelişmiş. Bu kullanımları doğası gereği tüm tanılama. Profil oluşturma API yalnızca ölçer ancak bir uygulamanın yürütmesini de izler. Bu nedenle, profil oluşturma API hiçbir zaman uygulama tarafından kullanılmamalıdır ve uygulamanın yürütme üzerinde bağımlı olmamalıdır (veya tarafından etkilenen) profil oluşturucu.  
  
 Bir CLR uygulaması profil işleme, genel profil makine kodu derlenmiş olandan daha fazla destek gerektirir. Uygulama etki alanları, atık toplama, özel durum işleme yönetilen gibi CLR kavramları tanıtır. Bunun nedeni tam zamanında (JIT) derleme (Microsoft Ara dili veya MSIL, yerel makine kod koda dönüştürme), kod ve benzer Özellikler. Geleneksel profil mekanizmaları tanımlamak veya bu özellikler hakkında yararlı bilgiler sağlar. Profil oluşturma API bu bilgileri eksik CLR ve profili uygulama performansına etkisi en düşük düzeydedir ile verimli bir şekilde sağlar.  
  
 JIT derleme zamanında profil oluşturma için iyi fırsatı sağlar. Profil oluşturma API'si JIT derlenmiş önce bir yordam için bellek içi MSIL kod akış değiştirmek profil oluşturucu sağlar. Bu şekilde, profil oluşturucu izleme kodu daha kapsamlı bir araştırma gereken belirli yordamları dinamik olarak ekleyebilirsiniz. Bu yaklaşım geleneksel senaryolarda mümkün olsa da, CLR için profil oluşturma API kullanarak uygulama çok daha kolaydır.  
  
 Bu genel bakışta, aşağıdaki bölümlerden oluşur:  
  
-   [Profil oluşturma API'si](#profiling_api)  
  
-   [Desteklenen özellikler](#support)  
  
-   [Bildirim iş parçacıkları](#notification_threads)  
  
-   [Güvenlik](#security)  
  
-   [Yönetilen ve yönetilmeyen kod profil oluşturucu kodu birleştirme](#combining_managed_unmanaged)  
  
-   [Yönetilmeyen kod profili oluşturma](#unmanaged)  
  
-   [COM kullanma](#com)  
  
-   [Çağrı yığınları](#call_stacks)  
  
-   [Geri aramalar ve yığın derinliği](#callbacks)  
  
-   [İlgili Konular](#related_topics)  
  
<a name="profiling_api"></a>   
## <a name="the-profiling-api"></a>Profil oluşturma API'si  
 Genellikle, profil oluşturma API yazmak için kullanılan bir *profil oluşturucu kodu*, hangi yönetilen bir uygulamanın yürütülmesini izleyen bir programdır.  
  
 Profil oluşturma API profil oluşturucu profili oluşturuluyor uygulama aynı süreci yüklenen DLL tarafından kullanılır. Profil Oluşturucu DLL bir geri çağırma arabirimi uygulayan ([Icorprofilercallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) .NET Framework sürüm 1.0 ve 1.1, [Icorprofilercallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) sürüm 2.0 ve üzeri). CLR Profil Oluşturucu profili işlemindeki olayların bildirmek için bu arabiriminde yöntemleri çağırır. Profil Oluşturucu geri çalışma zamanı tarafından yöntemleri kullanma çağırabilirsiniz [Icorprofilerınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) ve [Icorprofilerınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md) profili uygulamasının durumu hakkında bilgi edinmek için arabirim.  
  
> [!NOTE]
>  Profil Oluşturucu çözümü, yalnızca veri toplama bölümünü profili uygulama olarak aynı işlemde çalıştırıyor olması gerekir. Tüm kullanıcı arabirimi ve veri analizi ayrı bir işlemde gerçekleştirilmesi gerekir.  
  
 Aşağıdaki resimde, profil oluşturucu DLL profili oluşturuluyor uygulama ve CLR ile nasıl etkileşim kurduğu gösterilmektedir.  
  
 ![Profil Mimarisi](../../../../docs/framework/unmanaged-api/profiling/media/profilingarch.png "ProfilingArch")  
Profil oluşturma mimarisi  
  
### <a name="the-notification-interfaces"></a>Bildirim arabirimleri  
 [Icorprofilercallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) ve [Icorprofilercallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) bildirimi arabirimleri kabul edilebilir. Bu arabirim yöntemleri gibi oluşur [ClassLoadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md), [ClassLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md), ve [Jıtcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md). CLR yükler veya bir sınıf kaldırılırken her zaman bir işlev derler ve vb. karşılık gelen yöntemini Profil Oluşturucusu'nda 's çağırır `ICorProfilerCallback` veya `ICorProfilerCallback2` arabirimi.  
  
 Örneğin, bir profil oluşturucu kod performansı iki bildirim işlevler aracılığıyla ölçü: [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) ve [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md). Zaman damgaları her bir bildirim sonuçları toplanır ve hangi işlevleri gösteren bir liste çıkarır yalnızca, en fazla CPU veya duvar saati süresi uygulama yürütülmesi sırasında tüketilen.  
  
### <a name="the-information-retrieval-interfaces"></a>Bilgi alma arabirimleri  
 Diğer ana profil söz konusu arabirimlerdir [Icorprofilerınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) ve [Icorprofilerınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md). Profil Oluşturucu bu arabirimleri kendi çözümlemesine yardımcı olmak üzere daha fazla bilgi edinmek için gerekli olarak çağırır. Örneğin, her CLR çağırır [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) işlevi, bir işlev tanımlayıcı sağlar. Profil Oluşturucu çağırarak bu işlevi hakkında daha fazla bilgi edinebilirsiniz [Icorprofilerınfo2::getfunctionınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) işlevin üst sınıfı ', adı ve benzeri bulma yöntemi.  
  
 [Başa dön](#top)  
  
<a name="support"></a>   
## <a name="supported-features"></a>Desteklenen Özellikler  
 Profil oluşturma API'si, çeşitli olayları ve ortak dil çalışma zamanı'nda gerçekleşen eylemler hakkında bilgi sağlar. Çalışmalar işlemleri izlemek ve .NET Framework uygulamanızın performansını çözümlemek için bu bilgileri kullanabilirsiniz.  
  
 Profil oluşturma API'si aşağıdaki eylemler ve CLR oluşan olaylar hakkında bilgi alır:  
  
-   CLR başlatma ve kapatma olayları.  
  
-   Uygulama etki alanı oluşturma ve kapatma olayları.  
  
-   Yükleme ve yüklemeyi kaldırma olaylarını derleme.  
  
-   Yükleme ve yüklemeyi kaldırma olaylarını modül.  
  
-   COM vtable olaylar oluşturma ve yok etme.  
  
-   Tam zamanında (JIT) derleme ve kod pitching olaylar.  
  
-   Yükleme ve kaldırma olaylarını sınıfı.  
  
-   İş parçacığı oluşturma ve yok etme olayları.  
  
-   İşlev giriş ve çıkış olaylar.  
  
-   Özel durumlar.  
  
-   Yönetilen ve yönetilmeyen kod yürütmeyi arasında geçişler.  
  
-   Farklı çalışma zamanı bağlamları arasında geçişler.  
  
-   Çalışma zamanı suspensions hakkında bilgi sağlar.  
  
-   Çalışma zamanı bellek öbek ve atık toplama etkinliği hakkında bilgi.  
  
 Profil oluşturma API herhangi (yönetilmeyen) COM uyumlu bir dilden çağrılabilir.  
  
 API, CPU ve bellek tüketimi açısından verimlidir. Profil oluşturma yanıltıcı sonuçlara neden önemli değişiklikler profili uygulamaya gerektirmez.  
  
 Profil oluşturma API örnekleme ve örnekleme olmayan profil oluşturucuları için yararlıdır. A *profil oluşturucu örnekleme* normal saat vuruşlarını profilde söyleyin, birbirinden 5 milisaniye inceler. A *profil oluşturucu örnekleme olmayan* bir olayın zaman uyumlu olarak olaya neden iş parçacığı ile bilgilendirilir.  
  
### <a name="unsupported-functionality"></a>Desteklenmeyen işlevi  
 Profil oluşturma API'si aşağıdaki işlevselliği desteklemez:  
  
-   Yönetilmeyen kod, geleneksel Win32 yöntemleri kullanarak profili gerekir. Ancak, CLR Profil Oluşturucu yönetilen ve yönetilmeyen kodu arasındaki sınırların belirlemek için geçiş olaylarını içerir.  
  
-   En boy odaklı programlama gibi amaçlarla kendi kodlarını değiştirme uygulamaları otomatik olarak değiştiriliyor.  
  
-   Profil oluşturma API bu bilgileri sağlanmadığı için denetimi sınırları. CLR iç destek sınırları tüm yönetilen kodu denetimi sağlar.  
  
-   Aşağıdaki nedenlerden dolayı desteklenmeyen profil, uzaktan:  
  
    -   Uzaktan profil oluşturmayı yürütme süresini uzatır. Profil oluşturma arabirimleri kullandığınızda, böylece sonuçları profil unduly etkilenmeyecek yürütme süresini en aza gerekir. Yürütme performans izlenmekte olan durumlarda özellikle geçerlidir. Profil oluşturma arabirimleri bellek kullanımı izlemek veya yığın çerçeveleri, nesneleri ve benzeri ilişkin çalışma zamanı bilgi almak için kullanıldığında, ancak uzaktan profil oluşturmayı bir sınırlama değil.  
  
    -   CLR kod profil oluşturucu çalışma zamanı profili uygulamanın çalıştığı yerel bilgisayardaki bir veya daha fazla geri çağırma arabirimleri kaydetmeniz gerekir. Bu, bir uzaktan kod profil oluşturucu oluşturma olanağı sınırlar.  
  
-   Üretim ortamlarında yüksek oranda kullanılabilirlik gereksinimleri olan profil oluşturma. Profil oluşturma API geliştirme zamanı tanılama desteklemek için oluşturuldu. Üretim ortamlarında desteklemek için gereken ciddi testler geçmemiştir.  
  
 [Başa dön](#top)  
  
<a name="notification_threads"></a>   
## <a name="notification-threads"></a>Bildirim iş parçacıkları  
 Çoğu durumda, bir olay oluşturur iş parçacığı bildirimleri de yürütür. Bu tür bildirimleri (örneğin, [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) ve [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md)) açık sağlamanız gerekmez `ThreadID`. Ayrıca, profil oluşturucu depolamak ve genel depolama, temel analiz bloklarında dizin oluşturma yerine kendi analiz blokları güncelleştirmek için iş parçacığı yerel depolama kullanmaya karar verebilir `ThreadID` etkilenen iş parçacığının.  
  
 Bu geri aramalar sıralanmamış unutmayın. Kullanıcılar kendi kod parçacığı veri yapıları oluşturma ve birden çok iş parçacığından paralel erişimi engellemek gerekli olması durumunda profil oluşturucu kodu kilitleme korumanız gerekir. Bu nedenle, bazı durumlarda geri aramalar olağan dışı bir dizi alabilir. Örneğin, yönetilen bir uygulamaya aynı kodu yürütme iki iş parçacığı oluşturma olduğunu varsayın. Bu durumda, almak olası bir [Icorprofilercallback::jıtcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) bir iş parçacığından diğerine bazı işlevi için olay ve `FunctionEnter` geri alma önce başka bir iş parçacığı aramasından [ Icorprofilercallback::jıtcompilationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) geri çağırma. Bu durumda, kullanıcı alacak bir `FunctionEnter` tam olarak yalnızca henüz derlenmiş zamanında (JIT) olmayabilen bir işlev için geri çağırma.  
  
 [Başa dön](#top)  
  
<a name="security"></a>   
## <a name="security"></a>Güvenlik  
 Bir profil oluşturucu ortak dil çalışma zamanı yürütme altyapısı bir parçası olarak çalışan bir yönetilmeyen DLL DLL'dir. Sonuç olarak, DLL kısıtlamalarını tabi değil profil oluşturucu kodda kod erişim güvenliği yönetilen. Profil Oluşturucu yalnızca sınırlamalar DLL bilgilerdir işletim sistemi profili uygulama çalıştıran kullanıcı tarafından uygulanmaz.  
  
 Profil Oluşturucu yazarlar güvenlikle ilgili sorunları önlemek için uygun önlemleri almanız gerekir. Kötü niyetli bir kullanıcı onu değiştiremezsiniz, örneğin, yükleme sırasında bir erişim denetim listesi (ACL) profil oluşturucu DLL eklenmelidir.  
  
 [Başa dön](#top)  
  
<a name="combining_managed_unmanaged"></a>   
## <a name="combining-managed-and-unmanaged-code-in-a-code-profiler"></a>Yönetilen ve yönetilmeyen kod profil oluşturucu kodu birleştirme  
 Yanlış yazılmış bir profil oluşturucu kendisi, döngüsel başvurulara kaynaklanan beklenmeyen davranışlara neden olabilir.  
  
 Profil oluşturma API'si CLR gözden birbirine COM birlikte çalışma ya da dolaylı çağrılarına yönetilen ve yönetilmeyen bileşenlerini içeren bir profil oluşturucu yazma izlenim oluşturabilir.  
  
 Bu tasarım açısından mümkün olsa da, profil oluşturma API yönetilen bileşenleri desteklemez. CLR Profil Oluşturucu tamamen yönetilmeyen olması gerekir. CLR Profil Oluşturucu yönetilen ve yönetilmeyen kodunda birleştirmek için deneme erişim ihlalleri, program hatası veya kilitlenmeleri neden olabilir. Profil Oluşturucu yönetilen bileşenleri, yönetilen bileşenleri içinde döngüsel başvurulara kaynaklanan yeniden sonradan çağırırdı geri yönetilmeyen bileşenleri, olayları ateşlenir.  
  
 Burada bir CLR Profil Oluşturucu yönetilen kod güvenle çağırabilirsiniz tek bir yöntemin Microsoft Ara dili (MSIL) gövdesi konumdur. MSIL gövde değiştirmek için önerilen uygulama JIT derleme yöntemlere kullanmaktır [Icorprofilercallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) arabirimi.  
  
 MSIL değiştirmek için eski izleme yöntemleri kullanmak da mümkündür. Bir işlevin tam zamanında (JIT) derleme tamamlanmadan önce Profil Oluşturucu yöntemi ve ardından JIT derleme MSIL gövdesinde yönetilen çağrılar ekleyebilirsiniz, (bkz [Icorprofilerınfo::getılfunctionbody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbody-method.md) yöntemi). Bu teknik başarıyla seçmeli araçları yönetilen kodun ya da JIT hakkında istatistikler ve performans verilerini toplamak için kullanılabilir.  
  
 Alternatif olarak, bir kod profil oluşturucu yerel kancaları yönetilmeyen koda çağıran her Yönetilen işlev MSIL gövdesi ekleyebilirsiniz. Bu yöntem, araçları ve kapsamı için kullanılabilir. Örneğin, kod profil oluşturucu izleme kancaları blok yürütüldüğü emin olmak için her MSIL bloğundan sonra ekleyebilirsiniz. Bir yöntemin MSIL gövdesi değiştirilmesini çok delicate bir işlemdir ve dikkate alınması gereken birçok Faktörden vardır.  
  
 [Başa dön](#top)  
  
<a name="unmanaged"></a>   
## <a name="profiling-unmanaged-code"></a>Yönetilmeyen kod profili oluşturma  
 Profil oluşturma API'si ortak dil çalışma zamanı (CLR), yönetilmeyen kod profili oluşturma için en az destek sağlar. Aşağıdaki işlevsellik sağlanır:  
  
-   Yığın zincirleri numaralandırması. Bu özellik, yönetilmeyen kod ile yönetilen kod arasındaki sınır belirlemek Kod Oluşturucu sağlar.  
  
-   Belirleme yönetilen kod veya yerel kod olup olmadığını karşılık gelen bir yığın zinciri.  
  
 .NET Framework sürüm 1.0 ve 1.1, bu yöntemleri hata ayıklama API'si CLR işlemdeki alt kullanılabilir. Bunlar CorDebug.idl dosyasında tanımlanır.  
  
 .NET Framework 2.0 ve daha sonra kullanabileceğiniz [Icorprofilerınfo2::dostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) bu işlev için yöntem.  
  
 [Başa dön](#top)  
  
<a name="com"></a>   
## <a name="using-com"></a>COM kullanma  
 Profil oluşturma arabirimleri COM arabirimleri tanımlanmasına rağmen ortak dil çalışma zamanı (CLR) bu arabirimleri kullanılacak COM gerçekte Başlatmıyor. Bir iş parçacığı modelini kullanarak ayarlama yapmak zorunda kalmamak için nedeni [CoInitialize](http://msdn.microsoft.com/library/windows/desktop/ms678543\(v=vs.85\).aspx) yönetilen uygulama, istenen iş parçacığı modelini belirtmek için bir fırsat dolmadığı önce işlev. Benzer şekilde, profil oluşturucu kendisini değil çağırmalıdır `CoInitialize`, çünkü profili oluşturuluyor uygulama ile uyumlu olmayan bir iş parçacığı modelini çekme ve uygulamanın başarısız olmasına neden olabilir.  
  
 [Başa dön](#top)  
  
<a name="call_stacks"></a>   
## <a name="call-stacks"></a>Çağrı yığınları  
 Profil oluşturma API'si çağrı yığınları elde etmek için iki yöntem sunar: çağrı yığınları, seyrek toplamayı etkinleştirir, yığın anlık görüntü yöntemi ve her anlık çağrı yığını izler gölge yığını yöntemi.  
  
### <a name="stack-snapshot"></a>Yığın anlık görüntü  
 Yığın anlık bir iş parçacığı yığın izlemesi zamanında anlık görüntüsüdür. Profil oluşturma API yığında yönetilen işlevler izlenmesini destekler ancak için Profil Oluşturucu'nın kendi yığını walker yönetilmeyen işlevleri izleme durumda bırakır.  
  
 Yönetilen yığın yürütmek için profil oluşturucu programı hakkında daha fazla bilgi için bkz [Icorprofilerınfo2::dostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) bu belge kümesindeki yöntemi ve [profil oluşturucu yığınının taramasını, .NET Framework 2.0: Temel kavramları ve ötesine](http://go.microsoft.com/fwlink/?LinkId=73638).
  
### <a name="shadow-stack"></a>Gölge yığını  
 Anlık görüntü yöntemi çok sık kullanarak hızlı bir performans sorunu oluşturabilirsiniz. Yığın izlemeleri sık almak istiyorsanız, oluşturucunuz bunun yerine bir gölge yığını kullanarak oluşturup [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md), ve [Icorprofilercallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) özel durum geri aramalar. Gölge yığın her zaman güncel olduğundan ve depolama birimine, yığın anlık görüntü gerektiğinde hızlı bir şekilde kopyalanabilir.  
  
 Gölge yığını işlev bağımsız değişkenleri, dönüş değerleri ve genel örneklemesi hakkında bilgi edinebilirsiniz. Bu bilgiler yalnızca gölge yığınından kullanılabilir ve denetim için bir işlev karmalayan zaman elde edilebilir. Ancak, bu bilgiler daha sonra işlevi çalışması sırasında kullanılamayabilir.  
  
 [Başa dön](#top)  
  
<a name="callbacks"></a>   
## <a name="callbacks-and-stack-depth"></a>Geri aramalar ve yığın derinliği  
 Profil Oluşturucu geri aramalar çok yığını kısıtlı durumlarda verilebilir ve hemen işlem çıkmak için profil oluşturucu geri çağırma bir yığın taşması götürür. Bir profil oluşturucu yanıt geri aramalar için mümkün olduğunca az yığın olarak kullandığınızdan emin olmalısınız. Profil Oluşturucu yığın taşması karşı güçlü işlemler karşı kullanıma yöneliktir, profil oluşturucu kendisi de yığın taşması tetikleme kaçınmalısınız.  
  
 [Başa dön](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Profil oluşturma ortamını ayarlama](../../../../docs/framework/unmanaged-api/profiling/setting-up-a-profiling-environment.md)|Bir profil oluşturucu başlatmak, olay bildirimlerini ayarlamak ve bir Windows hizmeti profil açıklanmaktadır.|  
|[Profil oluşturma arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)|Profil oluşturma API'si kullanan yönetilmeyen arabirimler açıklanmaktadır.|  
|[Profil oluşturma genel statik işlevleri](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)|Profil oluşturma API'si kullanan yönetilmeyen genel statik işlevleri açıklanmaktadır.|  
|[Profil oluşturma numaralandırmaları](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)|Profil oluşturma API'si kullanan yönetilmeyen numaralandırmalar açıklar.|  
|[Profil oluşturma yapıları](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)|Profil oluşturma API'si kullanan yönetilmeyen yapılar açıklar.|
