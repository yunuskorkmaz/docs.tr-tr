---
title: Profil Oluşturma Ortamını Ayarlama
ms.date: 03/30/2017
helpviewer_keywords:
- environment variables, profiling API
- profiling API [.NET Framework], setting up environment
- COR_PROFILER environment variable
- Windows Service applications, profiling
- profiling API [.NET Framework], Windows Service applications
- COR_ENABLE_PROFILING environment variable
- profiling API [.NET Framework], enabling
ms.assetid: fefca07f-7555-4e77-be86-3c542e928312
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bfa11083fad7a3ccc6a208f5f0e4b68e9e1bc18c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59098188"
---
# <a name="setting-up-a-profiling-environment"></a>Profil Oluşturma Ortamını Ayarlama
> [!NOTE]
>  Da profillere önemli değişiklikler olmuştur [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
 Yönetilen bir işlem (uygulama veya hizmet) başlatıldığında, ortak dil çalışma zamanı (CLR) yükler. CLR başlatılırken, işlemin bir profil oluşturucuya bağlanması gerekip gerekmediğine karar vermek için aşağıdaki iki ortam değişkenini değerlendirir:  
  
-   COR_ENABLE_PROFILING: Bu ortam değişkeni varsa ve 1 olarak ayarlanmış CLR Profil oluşturucuya bağlanır.  
  
-   COR_PROFILER: Cor_enable_profılıng geçişleri işaretlerseniz, CLR, bu CLSID veya önceden kayıt defterinde depolanmış olması gereken ProgID sahip profil oluşturucuya bağlanır. Cor_profıler ortam değişkeni, aşağıdaki iki örnekte gösterildiği gibi bir dize olarak tanımlanır.  
  
    ```  
    set COR_PROFILER={32E2F4DA-1BEA-47ea-88F9-C5DAF691C94A}  
    set COR_PROFILER="MyProfiler"  
    ```  
  
 Bir CLR uygulamasının profilini çıkarmak için uygulamayı çalıştırmadan önce cor_enable_profılıng ve cor_profıler ortam değişkenleri ayarlamanız gerekir. Ayrıca Profil Oluşturucu DLL'SİNİN kayıtlı olduğundan emin olmanız gerekir.  
  
> [!NOTE]
>  İle başlayarak [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], profil oluşturucular kaydedilmesi gerekmez.  
  
> [!NOTE]
>  .NET Framework 2.0, 3.0 ve 3.5 sürümlerini kullanmak için [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] ve sonraki sürümlerinde, complus_profapı_profilercompatibilitysetting ortam değişkenini ayarlamanız gerekir.  
  
## <a name="environment-variable-scope"></a>Ortam değişken kapsamı  
 Cor_enable_profılıng ve cor_profıler ortam değişkenlerini nasıl ayarladığınız etki kapsamlarını belirler. Bu değişkenleri aşağıdaki yollardan biriyle ayarlayabilirsiniz:  
  
-   Değişkenleri ayarlarsanız bir [Icordebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) çağrı, bunlar geçerli anda çalışmakta olan uygulama. (Ayrıca ortamı devralan bu uygulama tarafından başlatılmış diğer uygulamalara uygulanacaklardır.)  
  
-   Değişkenleri komut istemi penceresinde ayarlarsanız, bu pencereden başlatılan tüm uygulamalara uygulanacaklardır.  
  
-   Değişkenleri kullanıcı düzeyinde ayarlarsanız, dosya Gezgini ile başlattığınız tüm uygulamalara uygulanacaklardır. Bir komut istemi penceresi bu ortam ayarlarını değişkenleri ayarladıktan sonra açtığınız sahiptir ve bu pencereden başlayacağınız uygulamaları içerecektir. Kullanıcı düzeyinde ortam değişkenlerini ayarlamak için sağ **Bilgisayarım**, tıklayın **özellikleri**, tıklayın **Gelişmiş** sekmesini tıklatın, **ortamı Değişkenleri**ve değişkenleri ekleyip **kullanıcı değişkenleri** listesi.  
  
-   Değişkenleri bilgisayar düzeyinde ayarlarsanız, bu bilgisayarda başlatılan tüm uygulamalara uygulanacaklardır. Bu bilgisayarda açtığınız komut istemi penceresi bu ortam ayarlarını ve bu pencereden başlayacağınız uygulamaları içerecektir. Bu, o bilgisayardaki her yönetilen her işlemin oluşturucunuz ile başlayacağı anlamına gelir. Bilgisayar düzeyinde ortam değişkenlerini ayarlamak için sağ **Bilgisayarım**, tıklayın **özellikleri**, tıklayın **Gelişmiş** sekmesini tıklatın, **ortamı Değişkenleri**, değişkenleri ekleyip **sistem değişkenlerini** listelemek ve bilgisayarınızı yeniden başlatın. Yeniden başlattıktan sonra değişkenler sistem çapında olacaktır.  
  
 Bir Windows hizmeti profili oluşturuyorsanız, ortam değişkenlerini ayarladıktan ve profil oluşturucu DLL'yi kaydettikten sonra bilgisayarınızı yeniden başlatmanız gerekir. Bu değerlendirmeler hakkında daha fazla bilgi için bkz [bir Windows hizmeti profili](#windows_service).  
  
## <a name="additional-considerations"></a>Dikkat edilecek diğer noktalar  
  
-   Profil Oluşturucu sınıfının Implements [Icorprofilercallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) ve [Icorprofilercallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) arabirimleri. .NET Framework sürüm 2. 0'da, bir profil oluşturucu uygulamalıdır `ICorProfilerCallback2`. Bu, eğer okumuyorsa `ICorProfilerCallback2` yüklenmeyecek.  
  
-   İşlem verili bir ortamda tek seferde yalnızca bir profil oluşturucu profil oluşturabilirsiniz. İki farklı profil oluşturucuyu farklı ortamlarda kaydedebilirsiniz, ancak her ayrı işlemlerin profilini oluşturmalıdır. Profil Oluşturucu, işlemde COM sunucusu, profili oluşturulan işlem olarak aynı adres alanına eşlenmiş bir DLL olarak uygulanmalıdır. Bu, profil oluşturucunun işlemde çalıştığı anlamına gelir. .NET Framework, herhangi bir COM sunucusu türünü desteklemez. Örneğin, bir profil oluşturucu uzak bir bilgisayardan uygulamaları izlemek isterse, bunu her bilgisayarda Toplayıcı aracılarını uygulamalıdır. Bu aracılar, sonuçları toplar ve onları merkezi veri toplama bilgisayarına iletir.  
  
-   Profil Oluşturucu, işlemde oluşturulan bir COM nesnesi olduğundan, profilli her uygulama kendi profil oluşturucu kopyasına sahip. Bu nedenle, birden çok uygulamadan veri işlemek tek bir profil oluşturucu örneği yok. Ancak, günlük dosyası önlemek için profil oluşturucu günlüğe kaydetme koduna mantık diğer profilli uygulamalardan üzerine yazmasını eklemeniz gerekir.  
  
## <a name="initializing-the-profiler"></a>Profiler'ı başlatma  
 Her iki ortam değişkeni denetimi başarılı olduğunda, CLR Profil Oluşturucu bir örneğini com benzer şekilde oluşturur. `CoCreateInstance` işlevi. Profil Oluşturucu doğrudan çağrı aracılığıyla yüklenmediğinden `CoCreateInstance`. Bu nedenle, bir çağrı `CoInitialize`, iş parçacığı modelinin ayarlanmasını gerektiren engellenir. CLR sonra çağıran [Icorprofilercallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) yönteminde profil oluşturucu. Bu yöntemin imzası aşağıdaki gibidir.  
  
```  
HRESULT Initialize(IUnknown *pICorProfilerInfoUnk)  
```  
  
 Profil Oluşturucu faydalanacaksa `pICorProfilerInfoUnk` için bir [Icorprofilerınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) veya [Icorprofilerınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md) arabirim işaretçisi ve böylece daha sonra profil oluşturma sırasında daha fazla bilgi talep edebilir.  
  
## <a name="setting-event-notifications"></a>Olay bildirimlerini ayarlama  
 Daha sonra profil oluşturucuyu çağırır [Icorprofilerınfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) , ilgileniyor olan hangi bildirim kategorilerini belirlemek için yöntemi. Örneğin, profil oluşturucu yalnızca işlev girişi ve bildirim ve çöp toplama bildirimleri bırakın, aşağıdakileri belirtir.  
  
```  
ICorProfilerInfo* pInfo;  
pICorProfilerInfoUnk->QueryInterface(IID_ICorProfilerInfo, (void**)&pInfo);  
pInfo->SetEventMask(COR_PRF_MONITOR_ENTERLEAVE | COR_PRF_MONITOR_GC)  
```  
  
 Bu şekilde bildirim maskesini ayarlayarak, profil oluşturucu hangi bildirimlerin alınacağını sınırlandırabilir. Bu yaklaşım, kullanıcının basit ya da özel amaçlı profil oluşturucu oluşturmasına yardımcı olur. Ayrıca, profil oluşturucu yok bildirimleri gönderme boşa gidecektir CPU süresini azaltır.  
  
 Belirli profil oluşturucu olayları sabittir. Bu olaylar kümesinde hemen sonra buna `ICorProfilerCallback::Initialize` geri çağırma, bunlar devre dışı bırakılamaz ve yeni olayların açılamayacağı. Değişmez bir olayı değiştirme girişimleri sonuçlanır `ICorProfilerInfo::SetEventMask` başarısız HRESULT döndüren bir.  
  
<a name="windows_service"></a>   
## <a name="profiling-a-windows-service"></a>Bir Windows hizmeti profili oluşturma  
 Bir Windows hizmeti profili, bir ortak dil çalışma zamanı uygulamasının profilini oluşturmaya benzer olur. Her iki profil oluşturma işlemi ortam değişkenleri ile etkinleştirilir. İşletim sistemi başlatıldığında, bu konuda daha önce tartışılan ortam değişikliklerinin zaten olmalıdır, bir Windows hizmeti de başlatıldığı için sunmak ve sistem başlatılmadan önce gereken değerlere ayarlayın. Ayrıca, profil oluşturma DLL'SİNİN sistemde zaten kayıtlı olmalıdır.  
  
 Cor_enable_profılıng ve cor_profıler ortam değişkenlerini ayarladıktan ve profil oluşturucu DLL'yi kaydettikten sonra Windows hizmeti bu değişiklikleri algılayabilmesi hedef bilgisayarı yeniden başlatmanız gerekir.  
  
 Bu değişikliklerin sistem genelinde profil oluşturmayı unutmayın. Profili oluşturulan daha sonra çalışan her yönetilen uygulamanın önlemek için hedef bilgisayarı yeniden başlattıktan sonra sistem ortam değişkenlerini silmeniz gerekir.  
  
 Bu teknik, her CLR işleminin profilinin oluşturulmasına da yol açar. Profil Oluşturucu mantık eklemelidir kendi [Icorprofilercallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) geçerli işlemin ilgili olup olmadığını algılamak için geri çağırma. Yüklü değilse, profil oluşturucu başlatmayı gerçekleştirmeden geri çağırma başarısız olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturmaya Genel Bakış](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)
