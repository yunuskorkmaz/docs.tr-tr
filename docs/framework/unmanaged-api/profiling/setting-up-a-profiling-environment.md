---
title: "Profil Oluşturma Ortamını Ayarlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- environment variables, profiling API
- profiling API [.NET Framework], setting up environment
- COR_PROFILER environment variable
- Windows Service applications, profiling
- profiling API [.NET Framework], Windows Service applications
- COR_ENABLE_PROFILING environment variable
- profiling API [.NET Framework], enabling
ms.assetid: fefca07f-7555-4e77-be86-3c542e928312
caps.latest.revision: "29"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dc3d490284e371aefb2de712cb5721b0246caa6a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="setting-up-a-profiling-environment"></a>Profil Oluşturma Ortamını Ayarlama
> [!NOTE]
>  İçinde profil oluşturma için önemli değişiklikler olmuştur [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
 (Uygulama veya hizmet) yönetilen bir işlemi başladığında, ortak dil çalışma zamanı (CLR) yükler. CLR başlatıldığında işlemi için profil oluşturucu bağlanıp bağlanmadığını karar vermek için aşağıdaki iki ortam değişkenleri değerlendirir:  
  
-   Cor_enable_profılıng: Bu ortam değişkenini varsa ve 1 olarak ayarlanmış bir profil oluşturucu CLR bağlanır.  
  
-   Cor_profıler: cor_enable_profılıng onay geçerse, CLR bu CLSID ya da daha önce kayıt defterinde depolandı gerekir ProgID sahip profil oluşturucu bağlanır. Cor_profıler ortam değişkeni, aşağıdaki iki örnekte gösterildiği gibi bir dize olarak tanımlanır.  
  
    ```  
    set COR_PROFILER={32E2F4DA-1BEA-47ea-88F9-C5DAF691C94A}  
    set COR_PROFILER="MyProfiler"  
    ```  
  
 Bir CLR uygulama profili için uygulamayı çalıştırmadan önce cor_enable_profılıng ve cor_profıler ortam değişkenleri ayarlamanız gerekir. Profil Oluşturucu DLL kayıtlı olduğundan emin olmalısınız.  
  
> [!NOTE]
>  İle başlayarak [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], profil oluşturucular kayıtlı olması gerekmez.  
  
> [!NOTE]
>  .NET Framework sürüm 2.0, 3.0 ve 3.5 profil oluşturucular içinde kullanmak için [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] ve sonraki sürümlerinde COMPLUS_ProfAPI_ProfilerCompatibilitySetting ortam değişkeni ayarlamanız gerekir.  
  
## <a name="environment-variable-scope"></a>Ortam değişken kapsamı  
 Cor_enable_profılıng ve cor_profıler ortam değişkenlerini ayarlama nasıl kendi kapsamı belirler. Bu değişkenleri aşağıdaki yollardan biriyle ayarlayabilirsiniz:  
  
-   Değişkenleri ayarlarsanız bir [Icordebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) çağrısı, bunlar uygulanacak aynı anda çalışmakta olan uygulama. (Bunlar da ortam devralan bir uygulama tarafından başlatılan başka uygulamalar için uygulanır.)  
  
-   Bir komut istemi penceresinde değişkenleri ayarladıysanız, o penceresinden başlatılan tüm uygulamalar için geçerli olur.  
  
-   Kullanıcı düzeyinde değişkenleri ayarlarsanız, dosya Gezgini ile başlayan tüm uygulamalar için geçerli olur. Bir komut istemi penceresi değişkenleri ayarladıktan sonra açtığınız bu ortam ayarlarına sahip olur ve bu nedenle bu penceresinden başlatmak herhangi bir uygulama olur. Ortam değişkenleri kullanıcı düzeyinde ayarlamak için sağ tıklatın **Bilgisayarım**, tıklatın **özellikleri**, tıklatın **Gelişmiş** sekmesini tıklatın, **ortamı Değişkenleri**ve değişkenleri ekleyip **kullanıcı değişkenleri** listesi.  
  
-   Bilgisayar düzeyinde değişkenleri ayarlarsanız, bu bilgisayar üzerinde başlatılan tüm uygulamalar için geçerli olur. Bu bilgisayarda açık bir komut istemi penceresi bu ortam ayarları varsa ve bu nedenle bu penceresinden başlatmak herhangi bir uygulama olur. Başka bir deyişle, bu bilgisayarda yönetilen her işlem, Profil Oluşturucu ile başlar. Ortam değişkenleri bilgisayar düzeyinde ayarlamak için sağ tıklatın **Bilgisayarım**, tıklatın **özellikleri**, tıklatın **Gelişmiş** sekmesini tıklatın, **ortamı Değişkenleri**, değişkenleri ekleyip **sistem değişkenleri** listesinde ve bilgisayarınızı yeniden başlatın. Yeniden başlattıktan sonra değişkenleri sistem genelinde kullanılabilir olacaktır.  
  
 Bir Windows hizmeti profil, ortam değişkenlerini ayarlama ve profil oluşturucu DLL kaydetme sonra bilgisayarınızı yeniden başlatmanız gerekir. Bu konuları hakkında daha fazla bilgi için bkz [bir Windows hizmeti profil](#windows_service).  
  
## <a name="additional-considerations"></a>Ek hususlar  
  
-   Profil Oluşturucu sınıfı uygulayan [Icorprofilercallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) ve [Icorprofilercallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) arabirimleri. .NET Framework sürüm 2. 0'da, bir profil oluşturucu uygulamalıdır `ICorProfilerCallback2`. Yoksa `ICorProfilerCallback2` yüklenmeyecek.  
  
-   Yalnızca bir profil oluşturucu bir işlemde aynı anda belirli bir ortam profil. İki farklı profil oluşturucular farklı ortamlarda kaydedebilirsiniz, ancak her ayrı işlemler profil gerekir. Profil Oluşturucu, işlem içi COM sunucusu profili oluşturuluyor bir işlem olarak aynı adres alanına eşlenen DLL olarak uygulanmalıdır. Bu profil oluşturucu işlemdeki çalıştığını anlamına gelir. .NET Framework başka türde bir COM sunucusu desteklemez. Örneğin, uzak bir bilgisayardan uygulamaları izlemek bir profil oluşturucu istiyorsa, her bilgisayarda Toplayıcı aracıları uyguladıktan gerekir. Bu aracıları sonuçları toplu ve bunları merkezi veri toplama bilgisayara iletişim kurabilirsiniz.  
  
-   Profil Oluşturucu başlatılan işlem bir COM nesnesi olduğundan, her profili uygulamaya profil oluşturucu kopyasını sahip olacaksınız. Bu nedenle, birden çok uygulama verileri işlemek bir tek profil oluşturucu örneği yok. Ancak, günlük dosyası önlemek için Profil Oluşturucu'nın günlük kodu mantığı profili diğer uygulamalardan üzerine yazar eklemeniz gerekir.  
  
## <a name="initializing-the-profiler"></a>Profil oluşturucu başlatma  
 Her iki ortam değişkeni denetimleri geçirdiğinizde, CLR benzer şekilde COM için profil oluşturucu örneği oluşturur `CoCreateInstance` işlevi. Profil Oluşturucu doğrudan çağrısıyla yüklü değil `CoCreateInstance`. Bu nedenle, yapılan bir çağrı `CoInitialize`, iş parçacığı modelini ayarlama gerektiren engellenir. CLR sonra çağırır [Icorprofilercallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) profil oluşturucu yöntemi. Bu yöntem imzası aşağıdaki gibidir.  
  
```  
HRESULT Initialize(IUnknown *pICorProfilerInfoUnk)  
```  
  
 Profil Oluşturucu sorgulaması gerekir `pICorProfilerInfoUnk` için bir [Icorprofilerınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) veya [Icorprofilerınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md) arabirimi işaretçisi ve böylece profil oluşturma sırasında daha sonra daha fazla bilgi isteyebilir kaydedin.  
  
## <a name="setting-event-notifications"></a>Olay bildirimlerini ayarlama  
 Profil Oluşturucu sonra çağırır [Icorprofilerınfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) yöntemi içinde ilgileniyor kategorilerini bildirimler belirtin. Örneğin, yalnızca profil oluşturucu ilgilenmektedir işlevi girin ve bildirimleri ve çöp toplama bildirimleri bırakın, aşağıdaki belirtir.  
  
```  
ICorProfilerInfo* pInfo;  
pICorProfilerInfoUnk->QueryInterface(IID_ICorProfilerInfo, (void**)&pInfo);  
pInfo->SetEventMask(COR_PRF_MONITOR_ENTERLEAVE | COR_PRF_MONITOR_GC)  
```  
  
 Bu şekilde bildirimleri maskesi ayarlayarak, profil oluşturucu aldığı hangi bildirimleri sınırlayabilir. Bu yaklaşım basit veya özel amaçlı profil oluşturucu derleme kullanıcı yardımcı olur. Ayrıca, profil oluşturucu yalnızca yoksay bildirimleri gönderme küçülttüğü iyi bir şekilde CPU zamanı azaltır.  
  
 Belirli profil oluşturucu olayları değişmez. Bu olaylar kümesinde hemen buna `ICorProfilerCallback::Initialize` geri arama, bunlar devre dışı bırakılamaz ve yeni olaylar açılamaz. Değişmez olaya değiştirme girişimleri neden olur `ICorProfilerInfo::SetEventMask` başarısız HRESULT döndürüyor.  
  
<a name="windows_service"></a>   
## <a name="profiling-a-windows-service"></a>Bir Windows hizmeti profil oluşturma  
 Bir Windows hizmeti profil, bir ortak dil çalışma zamanı uygulama profili oluşturma gibi olur. Her iki profil oluşturma işlemlerini ortam değişkenleri etkinleştirilir. İşletim sistemi başlar, bu konuda daha önce tartışılan ortam değişkenleri zaten olması gerektiğinde bir Windows hizmeti başlatıldığı için sunmak ve sistem başlamadan önce gerekli değerleri ayarlayın. Ayrıca, profil DLL sistemde zaten kaydedilmesi gerekir.  
  
 Cor_enable_profılıng ve cor_profıler ortam değişkenlerini ayarlama ve profil oluşturucu DLL kaydetme sonra Windows hizmeti bu değişiklikleri algılayabilmesi hedef bilgisayarı yeniden başlatmanız gerekir.  
  
 Bu değişiklikler sistem genelinde profil etkinleştirecek unutmayın. Daha sonra profili oluşturuluyor çalıştıran her yönetilen uygulamayı önlemek için hedef bilgisayar yeniden başlatıldıktan sonra sistem ortam değişkenleri silmeniz gerekir.  
  
 Bu teknik de profili her bir CLR işleme yol açar. Profil Oluşturucu mantığı eklemeniz gerekir, [Icorprofilercallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) geçerli işlem ilgi olup olmadığını saptamak için geri çağırma. Değilse, profil oluşturucu başlatma yapmadan geri arama başarısız olabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Profil Oluşturmaya Genel Bakış](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)
