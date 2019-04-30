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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 598722c44d8d20adab9ce7d624edb820f67c0fa4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757564"
---
# <a name="profiling-overview"></a>Profil Oluşturmaya Genel Bakış
<a name="top"></a> Bir profil oluşturucu başka bir uygulamanın yürütülmesini izleyen bir araçtır. Ortak dil çalışma zamanı (CLR) Profil Oluşturucu, ileti almak ve CLR Profil oluşturma API'ı kullanarak göndermek işlevlerini içeren bir dinamik bağlantı kitaplığı (DLL) ' dir. Profil Oluşturucu DLL çalışma zamanında CLR tarafından yüklenir.  
  
 Geleneksel profil oluşturma araçları, uygulamanın yürütülmesini ölçmeye odaklanır. Diğer bir deyişle, her bir işlevin veya uygulamanın zaman bellek kullanımını harcanan süreyi ölçer. Profil oluşturma API'SİNİN daha geniş bir kod kapsama araçları gibi tanılama araç sınıfı hedefler ve Gelişmiş hata ayıklama yardımları bile. Doğası gereği tüm tanılama bu kullanır. Profil oluşturma API ölçmekle kalmaz aynı zamanda bir uygulamanın yürütülmesini izler. Bu nedenle, profil oluşturma API'si asla uygulamanın kendisi tarafından kullanılmamalıdır ve uygulamanın yürütülmesi bağlı olmamalıdır (veya ondan etkilenmemelidir) profil oluşturucu.  
  
 CLR uygulamasının profilini derlenmiş makine kodu gerekenden çok daha fazla desteği gerektirir. Uygulama etki alanları, çöp toplama, yönetilen özel durum işleme gibi CLR kavramlar tanıtılmaktadır olmasıdır (Microsoft Ara dili veya MSIL kodunu yerel makine koda dönüştürme), kod just-in-time (JIT) derleme ve benzer Özellikler. Geleneksel profil oluşturma mekanizmaları tanımlayamaz ya da bu özellikler hakkında yararlı bilgiler sağlar. Profil oluşturma API CLR ile profili oluşturulan uygulamanın performansı üzerinde çok az etkisi olan bu eksik bilgiyi verimli bir şekilde sağlar.  
  
 Çalışma zamanında JIT derlemesi profil oluşturma için iyi fırsatlar sağlar. Profil oluşturma API JIT olarak derlenmiş silinmeden önce bir yordam için bellek içi MSIL kod akışını değiştirmek bir profil oluşturucunun sağlar. Bu şekilde, profil oluşturucu izleme kodu daha derin araştırma gerektiren belirli yordamlara dinamik olarak ekleyebilirsiniz. Bu yaklaşım geleneksel senaryolarda mümkün olsa da, CLR Profil oluşturma API'ı kullanarak uygulama çok daha kolaydır.  
  
 Bu genel bakış aşağıdaki bölümlerden oluşur:  
  
- [Profil oluşturma API'si](#profiling_api)  
  
- [Desteklenen özellikler](#support)  
  
- [Bildirim iş parçacıkları](#notification_threads)  
  
- [Güvenlik](#security)  
  
- [Yönetilen ve yönetilmeyen kod Profiler kodu birleştirme](#combining_managed_unmanaged)  
  
- [Yönetilmeyen kod profili oluşturma](#unmanaged)  
  
- [COM kullanma](#com)  
  
- [Çağrı yığınları](#call_stacks)  
  
- [Geri çağrılar ve yığın derinliği](#callbacks)  
  
- [İlgili Konular](#related_topics)  
  
<a name="profiling_api"></a>   
## <a name="the-profiling-api"></a>Profil oluşturma API'si  
 Genellikle, profil oluşturma API yazmak için kullanılan bir *kod profil oluşturucu*, hangi yönetilen bir uygulamanın yürütülmesini izleyen bir programdır.  
  
 Profil oluşturma API, bir profil oluşturucu ile profili oluşturulan uygulamayla aynı işleme yüklenen DLL tarafından kullanılır. Profil Oluşturucu DLL bir geri arama arayüzü uygular ([Icorprofilercallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) .NET Framework sürüm 1.0 ve 1.1 [Icorprofilercallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) sürüm 2.0 ve üzeri). CLR, profili oluşturulan işlemdeki olayların profil oluşturucusuna bildirim için bu arabirimdeki yöntemleri çağırır. Profil Oluşturucu geri çalışma zamanı tarafından bulunan yöntemleri kullanarak çağırabilirsiniz [Icorprofilerınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) ve [Icorprofilerınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md) oluşturulan uygulamanın durumu hakkında bilgi edinmek için arabirim.  
  
> [!NOTE]
>  Profili oluşturulan uygulamayla aynı işlemde profil oluşturucu çözümünün yalnızca veri toplama bölümü çalışmalıdır. Tüm kullanıcı arabirimi ve veri analizi ayrı bir işlemde gerçekleştirilmelidir.  
  
 Aşağıdaki resimde, profil oluşturucu DLL'nin profili oluşturulan uygulama ve CLR ile nasıl etkileşim kurduğu gösterilmektedir.  
  
 ![Profil oluşturma mimarisi gösteren ekran görüntüsü.](./media/profiling-overview/profiling-architecture.png)  
  
### <a name="the-notification-interfaces"></a>Bildirim arabirimleri  
 [Icorprofilercallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) ve [Icorprofilercallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) bildirim arabirimleri olarak düşünülebilir. Bu arabirimler yöntemleri gibi oluşur [ClassLoadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md), [ClassLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md), ve [Jıtcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md). Her zaman CLR yükler veya bir sınıf yüklemesini kaldırdığında, bir işlev derler ve bu şekilde karşılık gelen yöntemini profil oluşturucunun çağırır `ICorProfilerCallback` veya `ICorProfilerCallback2` arabirimi.  
  
 Örneğin, bir profil oluşturucu iki bildirim işlevi ile kod performansını ölçebilir: [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) ve [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md). Bu zaman damgaları her bir bildirim, sonuçları toplar ve hangi işlevleri gösteren bir liste çıkışı oluşturur yalnızca en çok CPU ya da duvar saati zaman uygulama yürütmesi sırasında kullanılan.  
  
### <a name="the-information-retrieval-interfaces"></a>Bilgi alım arabirimleri  
 Diğer ana profil oluşturma dahil arabirimdir [Icorprofilerınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) ve [Icorprofilerınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md). Profil Oluşturucu Analizine yardımcı olmak için daha fazla bilgi edinmek için gerektiği gibi bu arabirimler çağırır. Örneğin, her CLR çağırır [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) işlevi, bir işlev tanımlayıcı sağlar. Profil Oluşturucu çağırarak o işlev ile ilgili daha fazla bilgi edinebilirsiniz [Icorprofilerınfo2::getfunctionınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) işlevin üst sınıfı, adı ve benzeri bulmak için yöntemi.  
  
 [Başa dön](#top)  
  
<a name="support"></a>   
## <a name="supported-features"></a>Desteklenen Özellikler  
 Profil oluşturma API çeşitli olayları ve ortak dil çalışma zamanı'nda gerçekleşen eylemler hakkında bilgi sağlar. Bu bilgileri, işlemlerin iç işleyişini izlemek ve .NET Framework uygulamanızın performansını çözümlemek için kullanabilirsiniz.  
  
 Profil oluşturma API'si aşağıdaki eylemler ve CLR içerisinde gerçekleşen olayları hakkında bilgi alır:  
  
- CLR başlatma ve kapatma olayları.  
  
- Uygulama etki alanı oluşturma ve kapatma olayları.  
  
- Derleme yükleme ve kaldırma olayları.  
  
- Modül yükleme ve kaldırma olayları.  
  
- COM vtable oluşturma ve yok etme olayları.  
  
- Just-in-time (JIT) derlemeyi ve kod atışlı olaylar.  
  
- Yükleme ve kaldırma olayları sınıfı.  
  
- İş parçacığı oluşturma ve yok etme olayları'nı tıklatın.  
  
- İşlev giriş ve çıkış olayları.  
  
- Özel durumlar.  
  
- Yönetilen ve yönetilmeyen kod yürütülmesi arasında geçişler.  
  
- Farklı çalışma zamanı bağlamları arasında geçişler.  
  
- Çalışma zamanını askıya alma hakkında bilgi sağlar.  
  
- Çalışma zamanı bellek yığını ve çöp toplama etkinliği hakkında bilgiler.  
  
 Profil oluşturma API tüm (yönetilmeyen) COM uyumlu dil üzerinden çağrılabilir.  
  
 API, CPU ve bellek tüketimi açısından verimlidir. Profil oluşturma profili oluşturulan uygulamada yanıltıcı sonuçlara neden olabilecek kadar önemli bir değişiklik gerektirmez.  
  
 Profil oluşturma API hem örnekleme hem de örnekleme yapmayan profil oluşturucuları için yararlıdır. A *örnekleme profil oluşturucu* profili normal saat vuruşlarında, örneğin 5 mili saniye inceler. A *örnekleme olmayan profil oluşturucu* bir olayın zaman uyumlu olarak olayına neden olmadan iş parçacığı ile bilgilendirilir.  
  
### <a name="unsupported-functionality"></a>Desteklenmeyen İşlev  
 Profil oluşturma API'si aşağıdaki işlevleri desteklemez:  
  
- Geleneksel Win32 yöntemleri kullanılarak profili oluşturulması gereken yönetilmeyen kod. Ancak, CLR Profil Oluşturucu yönetilen ve yönetilmeyen kod arasındaki sınırları belirlemek için geçiş olaylarını içerir.  
  
- Kendi kendini değiştiren açı yönelimli programlama gibi amaçlarla kendi kodunu değiştiren uygulamalar.  
  
- Profil oluşturma API'si bu bilgileri sağlamaz sağlamadığı için sınır denetimi. CLR sınırlarının tüm yönetilen kod denetimi desteği sağlar.  
  
- Aşağıdaki nedenlerden dolayı desteklenmeyen uzaktan profil oluşturma:  
  
    - Uzaktan profil oluşturma, yürütme süresini uzatır. Profil oluşturma arabirimlerini kullandığınızda, böylece profil oluşturma sonuçlarının unduly etkilenmez, yürütme süresi en aza indirmeniz gerekir. Bu, yürütme performansını izlendiğinde özellikle doğrudur. Profil oluşturma arabirimleri bellek kullanımını izlemek veya yığın çerçeveleri, nesneleri vb. hakkında çalışma zamanı bilgileri almak için kullanıldığında, ancak uzak profil oluşturma bir kısıtlaması değil.  
  
    - CLR kod Profilcisi bir veya daha fazla geri çağrı arabirimini, profili oluşturulan uygulamanın üzerinde çalıştığı yerel bilgisayardaki çalışma zamanı ile kaydetmelisiniz. Bu, bir uzaktan kod profil oluşturucu oluşturma özelliğini sınırlar.  
  
- Yüksek kullanılabilirlik gereksinimleri olan üretim ortamlarında profil oluşturma. Profil oluşturma API'si, geliştirme zamanı tanılamalarını desteklemek üzere oluşturulmuştur. Üretim ortamlarını desteklemek için gereken ciddi testleri gerçekleştirmedi.  
  
 [Başa dön](#top)  
  
<a name="notification_threads"></a>   
## <a name="notification-threads"></a>Bildirim iş parçacıkları  
 Çoğu durumda, olay oluşturan iş parçacığı da bildirimleri yürütür. Bu tür bildirimleri (örneğin, [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) ve [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md)) açık sağlamanız gerekmez `ThreadID`. Ayrıca, profil oluşturucu depolamak ve analiz bloklarıyla dizin göre genel depoda analiz bloklarında yerine güncelleştirmek için iş parçacığı yerel depolama kullanmaya karar verebilir `ThreadID` etkilenen iş parçacığının.  
  
 Bu geri aramaların seri halde olmadığını unutmayın. Kullanıcılar, iş parçacığı açısından güvenli veri yapıları oluşturarak ve birden çok iş parçacığından paralel erişimi önlemek gerektiğinde profil oluşturucu kodu kilitleme kodlarını korumanız gerekir. Bu nedenle, bazı durumlarda alışılmadık geri çağırmalar dizisi alabilirsiniz. Örneğin, yönetilen bir uygulama aynı kodu yürüten iki iş parçacığı ürettiğini varsayalım. Bu durumda, almak olası bir [Icorprofilercallback::jıtcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) olay bir iş parçacığından bazı işlevlere ait ve bir `FunctionEnter` geri alma önce diğer iş parçacığından [ Icorprofilercallback::jıtcompilationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) geri çağırma. Bu durumda, kullanıcı alacak bir `FunctionEnter` tam olarak yalnızca henüz derlenmiş zamanında (JIT) olmayabilen bir işlev için geri çağırma.  
  
 [Başa dön](#top)  
  
<a name="security"></a>   
## <a name="security"></a>Güvenlik  
 Bir profil oluşturucu DLL'si, ortak dil çalışma zamanı yürütme altyapısının bir parçası olarak çalışan yönetilmeyen bir DLL'dir. Yönetilen kod erişimi güvenliği sonuç olarak, kod profil oluşturucu DLL sınırlamalarına tabi değildir. Profil Oluşturucu üzerindeki tek sınırlamalar DLL aittir uygulamasını çalıştıran kullanıcının işletim sistemi tarafından uygulanmaz.  
  
 Profiler yazarları, güvenlikle ilgili sorunlardan kaçınmak için uygun önlemleri almalıdır. Kötü niyetli bir kullanıcı değiştirememeleri Örneğin, yükleme sırasında bir erişim denetim listesine (ACL) bir profil oluşturucu DLL'si eklenmelidir.  
  
 [Başa dön](#top)  
  
<a name="combining_managed_unmanaged"></a>   
## <a name="combining-managed-and-unmanaged-code-in-a-code-profiler"></a>Yönetilen ve yönetilmeyen kod Profiler kodu birleştirme  
 Yanlış yazılmış bir profil oluşturucusu, beklenmeyen davranışla sonuçlanarak kendisine, döngüsel başvurulara neden olabilir.  
  
 CLR Profil oluşturma API'si bir gözden geçirme, COM birlikte çalışması veya dolaylı aramalar birbirini çağıran yönetilen ve yönetilmeyen bileşenler içeren bir profil oluşturucu yazabileceğiniz izlenimini oluşturabilir.  
  
 Bu tasarım açısından mümkün olsa da, profil oluşturma API'si yönetilen bileşenleri desteklemez. Bir CLR Profil Oluşturucu bütünüyle yönetilmemelidir. Yönetilen ve yönetilmeyen kodu bir CLR Profil Oluşturucusu'nda birleştirme girişimleri, erişim ihlallerine, program hatalarına veya kilitlenmelere neden olabilir. Profil oluşturucunun yönetilen bileşenleri, sonradan döngüsel başvurulara da yönetilen bileşenleri tekrar çağıracak geri yönetilmeyen bileşenlerine olayları ateşlenir.  
  
 Burada bir CLR Profil Oluşturucu yönetilen kodu güvenle çağırabilirsiniz tek bir yöntemin Microsoft Ara dili (MSIL) gövdesi konumdur. MSIL gövdesinin değiştirilmesi için önerilen uygulama, JIT yeniden derleme yöntemlerini kullanmaktır [Icorprofilercallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) arabirimi.  
  
 MSIL değiştirmek amacıyla eski araç yöntemleri kullanmak da mümkündür. Just-in-time (JIT) derleme işlev tamamlanmadan önce profiler MSIL gövdesinde bir yöntem ve sonra JIT derleme yönetilen çağrı ekleyebilirsiniz, (bkz [Icorprofilerınfo::getılfunctionbody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbody-method.md) yöntemi). Bu teknik, yönetilen kod veya JIT hakkında istatistik ve performans verilerini toplamak için seçmeli araç başarıyla kullanılabilir.  
  
 Alternatif olarak, kod profil oluşturucusu yönetilmeyen koda çağıran her yönetilen işlevin MSIL gövdesine yerel kancalar ekleyebilirsiniz. Bu teknik, Araçlar ve kapsam için kullanılabilir. Örneğin, bir kod profil oluşturucu bloğun yürütülmesini emin olmak için her MSIL bloğundan sonra araç kancaları ekleyebilirsiniz. Bir yöntemin MSIL gövdesinin değiştirilmesi çok hassas bir işlemdir ve dikkate alınması gereken birçok faktör vardır.  
  
 [Başa dön](#top)  
  
<a name="unmanaged"></a>   
## <a name="profiling-unmanaged-code"></a>Yönetilmeyen kod profili oluşturma  
 Profil oluşturma API'si ortak dil çalışma zamanı (CLR), yönetilmeyen kodun profilini çıkarmaya çok az destek sağlar. Aşağıdaki işlev sağlanır:  
  
- Yığın zincirlerini numaralandırma. Bu özellik, yönetilen kod ve yönetimsiz kod arasındaki sınırları belirlemek bir kod profil oluşturucusu sağlar.  
  
- Belirleme olup bir yığın zincirinin yönetilen koda veya yerel koda karşılık gelir.  
  
 .NET Framework sürüm 1.0 ve 1.1, bu yöntemler API hata ayıklama CLR'nin işlemdeki alt kullanılabilir. Bunlar CorDebug.idl dosyasında tanımlanır.  
  
 .NET Framework 2.0 ve sonraki sürümlerinde, kullanabileceğiniz [Icorprofilerınfo2::dostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) bu işlevselliği için yöntemi.  
  
 [Başa dön](#top)  
  
<a name="com"></a>   
## <a name="using-com"></a>COM kullanma  
 Profil oluşturan arabirimler COM arabirimleri olarak tanımlansa da, ortak dil çalışma zamanı (CLR) aslında bu arabirimleri kullanması için com'i başlatmaz. İş parçacığı modeli kullanarak ayarlamak zorunda kalmamak için nedeni [CoInitialize](/windows/desktop/api/objbase/nf-objbase-coinitialize) önce yönetilen uygulamanın kendi istenen iş parçacığı oluşturma modelini belirlemesine izin işlev. Benzer şekilde, profil oluşturucunun kendisi çağırmamalıdır `CoInitialize`, profili oluşturulan uygulamayla uyumsuz bir iş parçacığı modeli seçebileceği ve uygulamanın başarısız olmasına neden olabilir.  
  
 [Başa dön](#top)  
  
<a name="call_stacks"></a>   
## <a name="call-stacks"></a>Çağrı yığınları  
 Profil oluşturma API çağrı yığınlarının alınması için iki yol sunar: çağrı yığınlarının seyrek toplama toplanmasını sağlayan yığın anlık görüntüsü yöntemi ve her anında çağrı yığınını izleyen gölge yığın yöntemi.  
  
### <a name="stack-snapshot"></a>Yığın anlık görüntüsü  
 Yığın anlık görüntüsü bir iş parçacığı yığınının bir izleme anlık saattir. Profil oluşturma API yığın üzerinde yönetilen işlevlerin izlenmesini destekler ancak Yönetilmeyen işlevlerin izlenmesini profil oluşturucunun kendi yığın değişkenine bırakır.  
  
 Profil oluşturucuyu yönetilen yığınları ilerletmek hakkında daha fazla bilgi için bkz. [Icorprofilerınfo2::dostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) yöntemi bu belge kümesindeki ve [.NET Framework 2.0 Profiler Programlayacağınız yığını: Temeller ve ötesi](https://go.microsoft.com/fwlink/?LinkId=73638).
  
### <a name="shadow-stack"></a>Gölge yığını  
 Anlık görüntü yönteminin çok sık kullanılması, hızlı bir performans sorunu oluşturabilir. Yığın izlemelerini sık sık almak istiyorsanız, profil oluşturucu, bunun yerine bir gölge yığını kullanarak Sysprep.inf'in [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md), ve [Icorprofilercallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) özel durum geri aramalarını. Gölge yığını her zaman günceldir ve bir yığın anlık görüntüsü gerektiğinde hızla depoya kopyalanabilir.  
  
 Gölge yığını, işlev bağımsız değişkenleri ve dönüş değerleri genel örnek oluşturma hakkında bilgi edinebilirsiniz. Bu bilgiler, yalnızca gölge yığın içinde kullanılabilir ve denetim bir işleve aktarıldığında elde edilebilir. Ancak, bu bilgiler daha sonra işlevin çalışması sırasında kullanılabilir olmayabilir.  
  
 [Başa dön](#top)  
  
<a name="callbacks"></a>   
## <a name="callbacks-and-stack-depth"></a>Geri çağrılar ve yığın derinliği  
 Profiler geri aramaları fazlasıyla yığın kısıtlaması olan durumlarda verilebilir ve oluşturucu geri aramasında bir yığın taşması bir işlemden hemen çıkılmasına yol açar. Bir profil oluşturucu geri çağırmalara yanıt olarak olabildiğince küçük yığın kullandığınızdan emin olmanız gerekir. Profil Oluşturucu yığın taşmasına karşı güçlü olan işlemlere karşı kullanılmak üzere tasarlanmışsa profil oluşturucunun kendisi de yığın taşmasını tetiklemekten kaçınmalıdır.  
  
 [Başa dön](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Profil Oluşturma Ortamını Ayarlama](../../../../docs/framework/unmanaged-api/profiling/setting-up-a-profiling-environment.md)|Profil oluşturucuyu başlatmayı, olay bildirimlerini ayarlamayı ve bir Windows hizmeti profili açıklanmaktadır.|  
|[Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)|Profil oluşturma API'SİNİN kullandığı yönetilmeyen arabirimleri açıklar.|  
|[Profil Oluşturma Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)|Profil oluşturma API'SİNİN kullandığı yönetilmeyen genel statik işlevleri açıklar.|  
|[Profil Oluşturma Sabit Listeleri](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)|Profil oluşturma API'SİNİN kullandığı yönetilmeyen numaralandırmaları açıklar.|  
|[Profil Oluşturma Yapıları](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)|Profil oluşturma API'SİNİN kullandığı yönetilmeyen yapıları açıklar.|
