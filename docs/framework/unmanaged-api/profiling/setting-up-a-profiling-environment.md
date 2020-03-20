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
ms.openlocfilehash: 32ebb868ea64a24fba80133b1a0eb539f51cb411
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176974"
---
# <a name="setting-up-a-profiling-environment"></a>Profil Oluşturma Ortamını Ayarlama
> [!NOTE]
> .NET Framework 4'te profil çıkarmada önemli değişiklikler olmuştur.  
  
 Yönetilen bir işlem (uygulama veya hizmet) başladığında, ortak dil çalışma zamanını (CLR) yükler. CLR başlatıldığı zaman, işlemin bir profiloluşturucuya bağlanıp bağlanmayacağına karar vermek için aşağıdaki iki çevresel değişkeni değerlendirir:  
  
- COR_ENABLE_PROFILING: CLR bir profilciye yalnızca bu ortam değişkeni varsa ve 1 olarak ayarlanmışsa bağlanır.  
  
- COR_PROFILER: COR_ENABLE_PROFILING denetimi geçerse, CLR bu CLSID veya ProgID olan ve daha önce kayıt defterinde depolanmış olması gereken profil oluşturucuya bağlanır. COR_PROFILER ortam değişkeni, aşağıdaki iki örnekte gösterildiği gibi bir dize olarak tanımlanır.  
  
    ```cpp  
    set COR_PROFILER={32E2F4DA-1BEA-47ea-88F9-C5DAF691C94A}  
    set COR_PROFILER="MyProfiler"  
    ```  
  
 Bir CLR uygulamasının profilini çıkarmak için, uygulamayı çalıştırmadan önce COR_ENABLE_PROFILING ve COR_PROFILER ortam değişkenlerini ayarlamanız gerekir. Ayrıca profil oluşturucu DLL'nin kayıtlı olduğundan da emin olmalısınız.  
  
> [!NOTE]
> .NET Framework 4'ten başlayarak profilcilerin kaydedilmesi gerekmez.  
  
> [!NOTE]
> .NET Framework 4 ve sonraki sürümlerde .NET Framework 2.0, 3.0 ve 3.5 profilcileri kullanmak için COMPLUS_ProfAPI_ProfilerCompatibilitySetting ortam değişkenini ayarlamanız gerekir.  
  
## <a name="environment-variable-scope"></a>Çevre Değişken Kapsamı  
 COR_ENABLE_PROFILING ve COR_PROFILER ortam değişkenlerini nasıl ayarladığınız, bunların etki kapsamını belirleyecektir. Bu değişkenleri aşağıdaki yollardan biriyle ayarlayabilirsiniz:  
  
- Değişkenleri [Bir ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) çağrısında ayarlarsanız, bunlar yalnızca o anda çalıştırdığınız uygulama için geçerli dir. (Ayrıca, ortamı miras alan bu uygulama tarafından başlatılan diğer uygulamalar için de geçerlidir.)  
  
- Değişkenleri Komut İstem penceresinde ayarlarsanız, bu değişkenler bu pencereden başlatılan tüm uygulamalara uygulanır.  
  
- Değişkenleri kullanıcı düzeyinde ayarlarsanız, Dosya Gezgini ile başlattığınız tüm uygulamalar için geçerlidir. Değişkenleri ayarladıktan sonra açtığınız Komut İstemi penceresi bu ortam ayarlarına sahip olur ve bu pencereden başlattığınız herhangi bir uygulama da olur. Ortam değişkenlerini kullanıcı düzeyinde ayarlamak için **Bilgisayarım'ı**tıklatın, **Özellikler'i**tıklatın, **Gelişmiş** sekmesini tıklatın, **Çevre Değişkenleri'ni**tıklatın ve değişkenleri **Kullanıcı değişkenleri** listesine ekleyin.  
  
- Değişkenleri bilgisayar düzeyinde ayarlarsanız, bu değişkenler o bilgisayarda başlatılan tüm uygulamalar için geçerli dir. Bu bilgisayarda açtığınız Komut İstemi penceresi bu ortam ayarlarına sahip olacak ve bu pencereden başlattığınız herhangi bir uygulama da olacaktır. Bu, o bilgisayardaki her yönetilen işlemin profil oluşturucunuzla başlayacağı anlamına gelir. Bilgisayar düzeyinde ortam değişkenlerini ayarlamak için **Bilgisayarım'ı**tıklatın, **Özellikler'i**tıklatın, **Gelişmiş** sekmesini tıklatın, **Çevre Değişkenleri'ni**tıklatın, Değişkenleri **Sistem değişkenleri** listesine ekleyin ve ardından bilgisayarınızı yeniden başlatın. Yeniden başladıktan sonra, değişkenler sistem çapında kullanılabilir olacaktır.  
  
 Bir Windows Hizmetinin profilini çıkarıyorsanız, ortam değişkenlerini ayarladıktan ve profil oluşturucu DLL'yi kaydettikten sonra bilgisayarınızı yeniden başlatmanız gerekir. Bu hususlar hakkında daha fazla bilgi için [Windows Hizmeti Profil Oluşturma](#windows_service)bölümüne bakın.  
  
## <a name="additional-considerations"></a>Ek Hususlar  
  
- Profiler sınıfı [ICorProfilerCallback ve ICorProfilerCallback2](icorprofilercallback-interface.md) arayüzlerini uygular. [ICorProfilerCallback2](icorprofilercallback2-interface.md) .NET Framework sürüm 2.0'da bir `ICorProfilerCallback2`profil oluşturucu. Yoksa, `ICorProfilerCallback2` yüklenmez.  
  
- Yalnızca bir profil oluşturucu, belirli bir ortamda bir işlemin profilini aynı anda verebilir. Farklı ortamlarda iki farklı profil oluşturabilirsiniz, ancak her birinin ayrı işlemlerin profilini çıkarmanız gerekir. Profil oluşturucu, profillenen işlemle aynı adres alanına eşlenen işlem içi COM sunucusu DLL olarak uygulanmalıdır. Bu, profil oluşturucunun işlem içinde çalıştığı anlamına gelir. .NET Framework, başka bir TÜR COM sunucusunu desteklemez. Örneğin, bir profil oluşturucu uygulamaları uzak bir bilgisayardan izlemek istiyorsa, her bilgisayarda toplayıcı aracıları uygulaması gerekir. Bu aracılar sonuçları toplu olarak toplayacak ve bunları merkezi veri toplama bilgisayarına iletir.  
  
- Profil oluşturucu, anında işlem sırasında bulunan bir COM nesnesi olduğundan, her profilli uygulama nın kendi profil oluşturucu kopyasına sahip olacaktır. Bu nedenle, tek bir profiloluşturucu örneği birden çok uygulamadan verileri işlemek zorunda değildir. Ancak, diğer profilli uygulamalardan günlük dosyası üzerine yazmasını önlemek için profiloluşturucugünlük koduna mantık eklemeniz gerekir.  
  
## <a name="initializing-the-profiler"></a>Profil oluşturma başlatma  
 Her iki ortam değişkeni denetimi de geçtiğinde, CLR profiloluşturucunun bir `CoCreateInstance` örneğini COM işlevine benzer bir şekilde oluşturur. Profiloluşturucu doğrudan bir çağrı ile `CoCreateInstance`yüklenmez. Bu nedenle, `CoInitialize`iş parçacığı modelinin ayarlanması gereken bir çağrı önlenir. CLR daha sonra [iCorProfilerCallback çağırır::Profiloluşturda](icorprofilercallback-initialize-method.md) başlatma yöntemi. Bu yöntemin imzası aşağıdaki gibidir.  
  
```cpp  
HRESULT Initialize(IUnknown *pICorProfilerInfoUnk)  
```  
  
 Profil oluşturucu `pICorProfilerInfoUnk` bir [ICorProfilerInfo](icorprofilerinfo-interface.md) veya [ICorProfilerInfo2](icorprofilerinfo2-interface.md) arayüz işaretçisi için sorgulama yapmalı ve profil oluşturma sırasında daha fazla bilgi isteyebilmeleri için bunu kaydetmelidir.  
  
## <a name="setting-event-notifications"></a>Olay Bildirimlerini Ayarlama  
 Profil oluşturucu daha sonra hangi bildirim kategorileriyle ilgilendiğini belirtmek için [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) yöntemini çağırır. Örneğin, profil oluşturucu yalnızca işlevle ilgileniyorsa bildirimleri ve çöp toplama bildirimlerini girin ve bırakın, aşağıdakileri belirtir.  
  
```cpp  
ICorProfilerInfo* pInfo;  
pICorProfilerInfoUnk->QueryInterface(IID_ICorProfilerInfo, (void**)&pInfo);  
pInfo->SetEventMask(COR_PRF_MONITOR_ENTERLEAVE | COR_PRF_MONITOR_GC)  
```  
  
 Bildirim maskesini bu şekilde ayarlayarak, profil oluşturucu hangi bildirimleri aldığını sınırlayabilir. Bu yaklaşım, kullanıcının basit veya özel amaçlı bir profil oluşturabına yardımcı olur. Ayrıca, profil oluşturucunun yalnızca yok sayacağı bildirimleri göndererek boşa harcanan CPU süresini de azaltır.  
  
 Bazı profil oluşturucu olaylar değişmezdir. Bu, bu olaylar `ICorProfilerCallback::Initialize` geri aramada ayarlanır ayarlanır ayarlanmaz kapatılamaz ve yeni olaylar açılamaz anlamına gelir. Değişmez bir olayı değiştirme girişimleri, `ICorProfilerInfo::SetEventMask` başarısız bir HRESULT'ı döndürmeye neden olur.  
  
<a name="windows_service"></a>
## <a name="profiling-a-windows-service"></a>Windows Hizmeti Profil Oluşturma  
 Windows Hizmeti profil oluşturma, ortak bir dil çalışma zamanı uygulaması profil oluşturma gibidir. Her iki profil oluşturma işlemi de ortam değişkenleri aracılığıyla etkinleştirilir. İşletim sistemi başlatıldığında bir Windows Hizmeti başlatıldığından, bu konuda daha önce tartışılan ortam değişkenlerinin zaten mevcut olması ve sistem başlamadan önce gerekli değerlere ayarlanması gerekir. Buna ek olarak, profil oluşturma DLL zaten sistemde kayıtlı olmalıdır.  
  
 COR_ENABLE_PROFILING ve COR_PROFILER ortam değişkenlerini ayarladıktan ve profil oluşturucu DLL'yi kaydettikten sonra, Windows Hizmeti'nin bu değişiklikleri algılayabilmesi için hedef bilgisayarı yeniden başlatmanız gerekir.  
  
 Bu değişikliklerin sistem genelinde profil oluşturmayı sağlayacağını unutmayın. Daha sonra çalışan her yönetilen uygulamanın profilinin çıkarOlmasını önlemek için, hedef bilgisayarı yeniden başlattıktan sonra sistem ortamı değişkenlerini silmeniz gerekir.  
  
 Bu teknik aynı zamanda her CLR işleminin profilinin atLayabına yol açar. Profil oluşturucu, [iCorProfilerCallback'ine mantık eklemelidir::Geçerli](icorprofilercallback-initialize-method.md) işlemin ilgi çekici olup olmadığını algılamak için geri aramayı başlatmayı başlatma. Değilse, profil oluşturucu başlatma gerçekleştirmeden geri arama başarısız olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Genel Bakış](profiling-overview.md)
