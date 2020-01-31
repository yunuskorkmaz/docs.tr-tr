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
ms.openlocfilehash: 04b9abd8ffe04a24c08ad89ff48b037c9b003359
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76860985"
---
# <a name="setting-up-a-profiling-environment"></a>Profil Oluşturma Ortamını Ayarlama
> [!NOTE]
> .NET Framework 4 ' te profil oluşturmak için önemli değişiklikler yapıldı.  
  
 Yönetilen bir işlem (uygulama veya hizmet) başlatıldığında, ortak dil çalışma zamanını (CLR) yükler. CLR başlatıldığında, işlemin bir profil oluşturucuya bağlanıp bağlanmayacağı konusunda karar vermek için aşağıdaki iki çevresel değişkeni değerlendirir:  
  
- COR_ENABLE_PROFILING: CLR yalnızca bu ortam değişkeni varsa ve 1 olarak ayarlandıysa bir profil oluşturucuya bağlanır.  
  
- COR_PROFILER: COR_ENABLE_PROFILING denetimi geçerse, CLR bu CLSID veya ProgID içeren PROFILER 'a bağlanır ve bu, önceden kayıt defterinde depolanmış olmalıdır. COR_PROFILER ortam değişkeni, aşağıdaki iki örnekte gösterildiği gibi bir dize olarak tanımlanır.  
  
    ```cpp  
    set COR_PROFILER={32E2F4DA-1BEA-47ea-88F9-C5DAF691C94A}  
    set COR_PROFILER="MyProfiler"  
    ```  
  
 Bir CLR uygulamasını profil oluşturma için, uygulamayı çalıştırmadan önce COR_ENABLE_PROFILING ve COR_PROFILER ortam değişkenlerini ayarlamanız gerekir. Ayrıca profil oluşturucu DLL 'inin kayıtlı olduğundan emin olmalısınız.  
  
> [!NOTE]
> .NET Framework 4 ' te başlayarak, profil oluşturucular kayıtlı olması gerekmez.  
  
> [!NOTE]
> .NET Framework 4 ve sonraki sürümlerde 2,0, 3,0 ve 3,5 .NET Framework sürümlerini kullanmak için COMPLUS_ProfAPI_ProfilerCompatibilitySetting ortam değişkenini ayarlamanız gerekir.  
  
## <a name="environment-variable-scope"></a>Ortam değişkeni kapsamı  
 COR_ENABLE_PROFILING nasıl ayarlarsınız ve COR_PROFILER ortam değişkenleri, etki alanının etki kapsamını tespit eder. Bu değişkenleri aşağıdaki yollarla ayarlayabilirsiniz:  
  
- Değişkenleri bir [ICorDebug:: CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) çağrısında ayarlarsanız, bunlar yalnızca sizin çalıştırdığınız uygulamaya uygulanır. (Bu uygulamalar, ortamı miras alan uygulama tarafından başlatılan diğer uygulamalar için de geçerlidir.)  
  
- Değişkenleri bir komut Istemi penceresinde ayarlarsanız, bu pencereden başlatılan tüm uygulamalara uygulanır.  
  
- Değişkenleri Kullanıcı düzeyinde ayarlarsanız, dosya Gezgini ile başlattığınız tüm uygulamalara uygulanır. Değişkenleri ayarladıktan sonra açtığınız bir komut Istemi penceresi bu ortam ayarlarına sahip olur, bu nedenle bu pencereden başlattığınız tüm uygulamalar olur. Kullanıcı düzeyinde ortam değişkenlerini ayarlamak için **, Bilgisayarım ' a sağ tıklayın,** **Özellikler**' e tıklayın, **Gelişmiş** sekmesine tıklayın, **ortam değişkenleri**' ne tıklayın ve değişkenleri **Kullanıcı değişkenleri** listesine ekleyin.  
  
- Değişkenleri bilgisayar düzeyinde ayarlarsanız, bu bilgisayarda başlatılan tüm uygulamalara uygulanır. Bu bilgisayarda açtığınız bir komut Istemi penceresi bu ortam ayarlarına sahip olur, bu nedenle bu pencereden başlattığınız tüm uygulamalar olur. Bu, bilgisayardaki her yönetilen işlemin Profil oluşturucunuz ile başlayacağı anlamına gelir. Bilgisayar düzeyinde ortam değişkenlerini ayarlamak için **, Bilgisayarım ' a sağ tıklayın,** **Özellikler**' e tıklayın, **Gelişmiş** sekmesine tıklayın, **ortam değişkenleri**' ne tıklayın, değişkenleri **Sistem değişkenleri** listesine ekleyin ve ardından bilgisayarınızı yeniden başlatın. Yeniden başlatıldıktan sonra, değişkenler sistem genelinde kullanılabilir olacaktır.  
  
 Bir Windows hizmeti profili oluşturuyorsanız, ortam değişkenlerini ayarladıktan ve profil oluşturucu DLL 'sini kaydettikten sonra bilgisayarınızı yeniden başlatmanız gerekir. Bu konular hakkında daha fazla bilgi için, [Windows hizmeti profili oluşturma](#windows_service)bölümüne bakın.  
  
## <a name="additional-considerations"></a>Ek konular  
  
- Profiler sınıfı [ICorProfilerCallback](icorprofilercallback-interface.md) ve [ICorProfilerCallback2](icorprofilercallback2-interface.md) arabirimlerini uygular. .NET Framework sürüm 2,0 ' de, bir profil oluşturucunun `ICorProfilerCallback2`uygulaması gerekir. Bu yoksa `ICorProfilerCallback2` yüklenmez.  
  
- Belirli bir ortamda aynı anda yalnızca bir profil oluşturucu bir işlem profili oluşturabilir. Farklı ortamlarda iki farklı profil oluşturucular kaydedebilirsiniz, ancak her birinin ayrı süreçler profili oluşturulmalıdır. Profil Oluşturucu, profili oluşturulan işlemle aynı adres alanına eşlenmiş işlem içi bir COM Server DLL 'SI olarak uygulanmalıdır. Bu, profil oluşturucunun işlem içinde çalıştığı anlamına gelir. .NET Framework diğer COM sunucusu türlerini desteklemez. Örneğin, bir profil oluşturucu uzak bir bilgisayardan uygulamaları izlemek isterse, her bilgisayarda toplayıcı aracıları uygulamalıdır. Bu aracılar toplu sonuçlara neden olur ve bunları merkezi veri koleksiyonu bilgisayarıyla iletişim kurar.  
  
- Profil Oluşturucu işlem içi örneği oluşturulan bir COM nesnesi olduğundan, profili oluşturulan her uygulama profil oluşturucunun kendi kopyasına sahip olur. Bu nedenle, tek bir profil oluşturucu örneği birden çok uygulamadan veri işlemek zorunda değildir. Ancak, profil oluşturucunun günlüğe kaydetme koduna, günlük dosyasının diğer profili oluşturulmuş uygulamalardan üzerine yazılmasına engel olmak için mantık eklemeniz gerekecektir.  
  
## <a name="initializing-the-profiler"></a>Profil oluşturucuyu başlatma  
 Her iki ortam değişkeni denetimi başarılı olduğunda, CLR, profil oluşturucunun bir örneğini COM `CoCreateInstance` işlevine benzer bir şekilde oluşturur. Profil Oluşturucu, `CoCreateInstance`doğrudan çağrısıyla yüklenmez. Bu nedenle, iş parçacığı modelini ayarlamayı gerektiren `CoInitialize`çağrısı önlenmiş olur. CLR daha sonra Profiler 'da [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) yöntemini çağırır. Bu yöntemin imzası aşağıdaki gibidir.  
  
```cpp  
HRESULT Initialize(IUnknown *pICorProfilerInfoUnk)  
```  
  
 Profiler bir [ICorProfilerInfo](icorprofilerinfo-interface.md) veya [ICorProfilerInfo2](icorprofilerinfo2-interface.md) arabirim işaretçisi için `pICorProfilerInfoUnk` sorgulayıp, daha sonra profil oluşturma sırasında daha fazla bilgi isteyebilmesi için onu kaydetmeniz gerekir.  
  
## <a name="setting-event-notifications"></a>Olay bildirimlerini ayarlama  
 Profil Oluşturucu daha sonra hangi bildirim kategorisini ilgilendiğinizi belirlemek için [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) yöntemini çağırır. Örneğin, Profil Oluşturucu yalnızca işlev girme ve bildirim ve çöp toplama bildirimleri ile ilgileniyorsanız, aşağıdakileri belirtir.  
  
```cpp  
ICorProfilerInfo* pInfo;  
pICorProfilerInfoUnk->QueryInterface(IID_ICorProfilerInfo, (void**)&pInfo);  
pInfo->SetEventMask(COR_PRF_MONITOR_ENTERLEAVE | COR_PRF_MONITOR_GC)  
```  
  
 Bildirim maskesini bu şekilde ayarlayarak profil oluşturucu hangi bildirimlerin alacağını sınırlayabilir. Bu yaklaşım, kullanıcının basit veya özel amaçlı bir profil oluşturucu oluşturmasına yardımcı olur. Ayrıca, profil oluşturucunun yalnızca yoksayması gereken bildirimleri göndermek için harcanan CPU süresini azaltır.  
  
 Bazı profil oluşturucu olayları sabittir. Diğer bir deyişle, bu olaylar `ICorProfilerCallback::Initialize` geri aramada ayarlandığı anda kapatılamaz ve yeni olaylar açılamaz. Değişmez bir olayı değiştirme girişimleri, başarısız bir HRESULT döndüren `ICorProfilerInfo::SetEventMask` neden olur.  
  
<a name="windows_service"></a>   
## <a name="profiling-a-windows-service"></a>Windows hizmeti profili oluşturma  
 Bir Windows hizmetinin profilini oluşturmak, ortak dil çalışma zamanı uygulamasının profilini oluşturmaya benzer. Her iki profil oluşturma işlemi de ortam değişkenleri aracılığıyla etkinleştirilir. İşletim sistemi başlatıldığında bir Windows hizmeti başlatıldığı için, bu konuda daha önce açıklanan ortam değişkenlerinin zaten mevcut olması ve sistem başlamadan önce gerekli değerlere ayarlanması gerekir. Ayrıca, profil oluşturma DLL 'sinin sistemde zaten kayıtlı olması gerekir.  
  
 COR_ENABLE_PROFILING ve COR_PROFILER ortam değişkenlerini ayarladıktan ve profil oluşturucu DLL 'sini kaydettikten sonra, Windows hizmetinin bu değişiklikleri algılayabilmesi için hedef bilgisayarı yeniden başlatmanız gerekir.  
  
 Bu değişikliklerin, sistem genelinde profil oluşturmayı etkinleştiğine unutmayın. Daha sonra çalıştırılan her yönetilen uygulamanın profili oluşturulmasını engellemek için, hedef bilgisayarı yeniden başlattıktan sonra sistem ortam değişkenlerini silmeniz gerekir.  
  
 Bu teknik, profili oluşturulan her CLR işlemine da yol açar. Profiler 'ın [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) geri çağırması için bir mantık eklemesi gerekir. Bu işlem, geçerli işlemin ilgi olup olmadığını algılar. Değilse, profil oluşturucu başlatmayı gerçekleştirmeden geri çağırma işlemini başarısız olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturmaya Genel Bakış](profiling-overview.md)
