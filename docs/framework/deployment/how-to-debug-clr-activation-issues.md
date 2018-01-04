---
title: "Nasıl Yapılır: CLR Etkinleştirme Sorunlarında Hata Ayıklama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: CLR activation, debugging issues
ms.assetid: 4fe17546-d56e-4344-a930-6d8e4a545914
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fa8153fe680a8848ad19f32a2246d0f350c73c66
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-debug-clr-activation-issues"></a>Nasıl Yapılır: CLR Etkinleştirme Sorunlarında Hata Ayıklama
Ortak dil çalışma zamanı (CLR) doğru sürümü ile çalışacak şekilde uygulamanızı alınırken sorunlarla karşılaşırsanız, görüntüleyin ve hata ayıklama CLR etkinleştirme günlüklerini. Bu günlükler, uygulamanızın beklenenden farklı bir CLR sürümü yükler veya CLR hiç yüklenmiyor bir etkinleştirme sorunun kök nedenini belirlerken çok kullanışlı olabilir. [.NET Framework başlatma hataları: kullanıcı deneyimi yönetme](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md) bir uygulama için hiçbir CLR bulunduğunda deneyimi açıklanır.  
  
 CLR etkinleştirme günlük kaydı etkin sistem genelinde bir HKEY_LOCAL_MACHINE kayıt defteri anahtarını veya bir sistem ortam değişkeni kullanarak olabilir. Günlük kayıt defteri girişini kadar oluşturulur veya ortam değişkeni kaldırılır. Alternatif olarak, farklı bir kapsam ve süre ile günlük kaydını etkinleştirmek için bir kullanıcı veya işlem yerel ortam değişkeni kullanabilirsiniz.  
  
 CLR etkinleştirme günlükleri döndürmemelidir kafası ile [derleme günlükleri bağlama](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md), tamamen farklı olduğu.  
  
## <a name="to-enable-clr-activation-logging"></a>CLR etkinleştirme günlük kaydını etkinleştirmek için  
  
#### <a name="using-the-registry"></a>Kayıt defterini kullanma  
  
1.  Kayıt Defteri Düzenleyicisi'nde HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft için gidin\\. NETFramework (32-bit bilgisayarda) veya HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework klasörü (64 bit bilgisayarda).  
  
2.  Adlı bir dize değeri ekleyin `CLRLoadLogDir`ve burada CLR etkinleştirme günlükleri depolamak istediğiniz varolan bir dizin tam yolunu ayarlayın.  
  
 Dize değeri kaldırana kadar etkinleştirme günlük kaydı etkin halde kalır.  
  
#### <a name="using-an-environment-variable"></a>Bir ortam değişkeni kullanarak  
  
-   Ayarlama `COMPLUS_CLRLoadLogDir` ortam değişkenine olduğu gibi CLR etkinleştirme günlükleri depolamak için varolan bir dizinin tam yolu temsil eden bir dize.  
  
     Ortam değişkenini nasıl kapsamı belirler:  
  
    -   Sistem düzeyinde ayarlanan, ortam değişkeni kaldırılana kadar etkinleştirme günlük bu bilgisayardaki tüm .NET Framework uygulamaları için etkinleştirilir.  
  
    -   Kullanıcı düzeyinde ayarlanan etkinleştirme günlüğü yalnızca geçerli kullanıcı hesabı için etkinleştirilir. Ortam değişkeni kaldırılana kadar günlük devam eder.  
  
    -   Buradan işlemi içinde CLR'yi yüklemeden önce ayarlarsanız, işlem sonlanana kadar etkinleştirme günlük kaydı etkindir.  
  
    -   Bir uygulamayı çalıştırmadan önce bir komut isteminde ayarlarsanız, bu komut isteminden çalıştırın herhangi bir uygulama için etkinleştirme günlük kaydı etkin.  
  
     Örneğin, işlem düzeyinde kapsamlı c:\clrloadlogs dizininde etkinleştirme günlükleri depolamak için bir komut istemi penceresi açın ve uygulamayı çalıştırmadan önce aşağıdaki komutu yazın:  
  
    ```  
    set COMPLUS_CLRLoadLogDir=c:\clrloadlogs  
    ```  
  
## <a name="example"></a>Örnek  
 CLR etkinleştirme günlükleri API'leri barındırma büyük miktarda veri CLR etkinleştirme hakkında ve CLR kullanılmasını sağlar. Bu verilerin çoğu Microsoft tarafından dahili olarak kullanılır, ancak bazı veriler Ayrıca bu makalede açıklanan geliştiricileri için faydalı olabilir.  
  
 API'leri barındırma CLR hangi sırayla günlük yansıtır adı veriliyordu. Ayrıca bilgisayarda algılanan yüklü çalışma zamanları kümesi hakkında yararlı verileri içerir. CLR etkinleştirme günlük biçimini kendisi belgelenen değildir, ancak CLR etkinleştirme sorunlarını çözmek için gereken geliştiriciler yardımcı olmak için kullanılabilir.  
  
> [!NOTE]
>  CLR kullandığı işlem sonlandırıldı kadar etkinleştirme oturum açamıyor.  
  
> [!NOTE]
>  CLR etkinleştirme günlükleri yerelleştirilmiş değil; Bunlar her zaman İngilizce dilinde üretilir.  
  
 Bir etkinleştirme günlüğü aşağıdaki örnekte en faydalı bilgileri vurgulanmış ve sonra günlük açıklanır.  
  
```  
532,205950.367,CLR Loading log for C:\Tests\myapp.exe   
532,205950.367,Log started at 4:26:12 PM on 10/6/2011   
532,205950.367,-----------------------------------   
532,205950.382,FunctionCall: _CorExeMain   
532,205950.382,FunctionCall: ClrCreateInstance, Clsid: {2EBCD49A-1B47-4A61-B13A-4A03701E594B}, Iid: {E2190695-77B2-492E-8E14-C4B3A7FDD593}   
532,205950.382,MethodCall: ICLRMetaHostPolicy::GetRequestedRuntime. Version: (null), Metahost Policy Flags: 0x168, Binary: (null), Iid: {BD39D1D2-BA2F-486A-89B0-B4B0CB466891}   
532,205950.382,Installed Runtime: v4.0.30319. VERSION_ARCHITECTURE: 0   
532,205950.382,Input values for ComputeVersionString follow this line   
532,205950.382,-----------------------------------   
532,205950.382,Default Application Name: C:\Tests\myapp.exe   
532,205950.382,IsLegacyBind is: 0   
532,205950.382,IsCapped is 0   
532,205950.382,SkuCheckFlags are 0   
532,205950.382,ShouldEmulateExeLaunch is 0   
532,205950.382,LegacyBindRequired is 0   
532,205950.382,-----------------------------------   
532,205950.382,Parsing config file: C:\Tests\myapp.exe   
532,205950.382,UseLegacyV2RuntimeActivationPolicy is set to 0   
532,205950.382,LegacyFunctionCall: GetFileVersion. Filename: C:\Tests\myapp.exe   
532,205950.382,LegacyFunctionCall: GetFileVersion. Filename: C:\Tests\myapp.exe   
532,205950.382,C:\Tests\myapp.exe was built with version: v2.0.50727   
532,205950.382,ERROR: Version v2.0.50727 is not present on the machine.   
532,205950.398,SEM_FAILCRITICALERRORS is set to 0   
532,205950.398,Launching feature-on-demand installation. CmdLine: C:\Windows\system32\fondue.exe /enable-feature:NetFx3   
532,205950.398,FunctionCall: RealDllMain. Reason: 0   
532,205950.398,FunctionCall: OnShimDllMainCalled. Reason: 0  
```  
  
-   **CLR yükleme günlüğü** yönetilen kod yüklenen işlemi başlatıldı yürütülebilir dosya yolunu sağlar. Bu yerel bir konak olabilir unutmayın.  
  
    ```  
    532,205950.367,CLR Loading log for C:\Tests\myapp.exe  
    ```  
  
-   **Çalışma zamanı yüklü** etkinleştirme isteği adaylar bilgisayarda yüklü CLR sürümleri kümesidir.  
  
    ```  
    532,205950.382,Installed Runtime: v4.0.30319. VERSION_ARCHITECTURE: 0  
    ```  
  
-   **sürümüyle oluşturulmuş** bir yönteme gibi sağlanan ikili oluşturmak için kullanılan CLR sürümü [Iclrmetahostpolicy::getrequestedruntime](../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md).  
  
    ```  
    532,205950.382,C:\Tests\myapp.exe was built with version: v2.0.50727  
    ```  
  
-   **İsteğe bağlı özellik Kurulum** .NET Framework 3.5 Windows 8 etkinleştirmekle başvuruyor. Bkz: [.NET Framework başlatma hataları: kullanıcı deneyimini yönetme](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md) bu senaryo hakkında daha fazla bilgi için.  
  
    ```  
    532,205950.398,Launching feature-on-demand installation. CmdLine: C:\Windows\system32\fondue.exe /enable-feature:NetFx3  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dağıtım](../../../docs/framework/deployment/index.md)  
 [Nasıl yapılır: Bir Uygulamayı .NET Framework 4 veya 4.5'i Destekleyecek Şekilde Yapılandırma](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
