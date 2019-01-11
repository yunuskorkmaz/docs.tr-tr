---
title: CLR etkinleştirme sorunlarında hata ayıklama
ms.date: 03/30/2017
helpviewer_keywords:
- CLR activation, debugging issues
ms.assetid: 4fe17546-d56e-4344-a930-6d8e4a545914
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5e552f7014c21e2ead61b83ca9909655def6333b
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54221082"
---
# <a name="how-to-debug-clr-activation-issues"></a>CLR etkinleştirme sorunlarında hata ayıklama

Uygulamanızın doğru sürümü ortak dil çalışma zamanı (CLR) ile çalışmaya başlama sorunlarla karşılaşırsanız, görüntüleyebilir ve hata ayıklama CLR etkinleştirme günlüklerini. Bu günlükler bir etkinleştirme sorunun kök nedenini belirlerken uygulamanızın beklenenden farklı bir CLR sürümü yükler veya CLR hiç yüklenmiyor çok kullanışlı olabilir. [.NET Framework başlatma hataları: Kullanıcı deneyimini yönetme](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md) bir uygulama için hiçbir CLR bulunduğunda deneyimi açıklanır.

CLR etkinleştirme günlük bir HKEY_LOCAL_MACHINE kayıt defteri anahtarı veya bir sistem ortam değişkeni kullanarak etkin sistem genelinde olabilir. Kayıt defteri girişini kadar günlük oluşturulur veya ortam değişkenini kaldırılır. Alternatif olarak, farklı kapsam ve süresi ile günlüğe kaydetmeyi etkinleştirmek için bir kullanıcı veya işlem yerel ortam değişkenini kullanabilirsiniz.

CLR etkinleştirme günlükleri olmamalıdır yanıltıcı ile [derleme bağlama günlüklerini](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md), tamamen farklı olan.

## <a name="to-enable-clr-activation-logging"></a>CLR etkinleştirme günlüğe kaydetmeyi etkinleştirmek için

### <a name="using-the-registry"></a>Kayıt defterini kullanma

1. Kayıt Defteri Düzenleyicisi'nde HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft için gidin\\. NETFramework (32 bit bilgisayarda) veya HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework klasörü (64 bit bilgisayarda).

2. Adlı bir dize değeri ekleyin `CLRLoadLogDir`, CLR etkinleştirme günlüklerini depolamak istediğiniz varolan bir dizinin tam yolunu ayarlayın.

Dize değeri kaldırana kadar etkinleştirme günlük kaydı etkin olarak kalır.

### <a name="using-an-environment-variable"></a>Bir ortam değişkeni kullanarak

- Ayarlama `COMPLUS_CLRLoadLogDir` ortam değişkenine istediğiniz CLR etkinleştirme günlüklerini depolamak için mevcut bir dizinin tam yolu temsil eden bir dize.

     Ortam değişkenini nasıl kapsamı belirler:

    - Sistem düzeyinde ayarlarsanız, ortam değişkenini kaldırılana kadar etkinleştirme günlük kaydı o bilgisayardaki tüm .NET Framework uygulamaları için etkindir.

    - Kullanıcı düzeyinde ayarlarsanız, etkinleştirme günlüğü yalnızca geçerli kullanıcı hesabı için etkinleştirilir. Ortam değişkenini kaldırılana kadar günlüğe kaydetmeye devam eder.

    - Gelen işlem dahilinde CLR yüklemeden önce ayarlarsanız, işlem sonlanana kadar etkinleştirme günlük kaydı etkindir.

    - Bir uygulamayı çalıştırmadan önce bir komut isteminde ayarlarsanız, bu komut istemi'nden çalıştırmak herhangi bir uygulama için etkinleştirme günlük kaydı etkindir.

     Örneğin, işlem düzeyinde kapsamlı c:\clrloadlogs dizinde etkinleştirme günlüklerini depolamak için bir komut istemi penceresi açın ve uygulamayı çalıştırmadan önce aşağıdaki komutu yazın:

    ```
    set COMPLUS_CLRLoadLogDir=c:\clrloadlogs
    ```

## <a name="example"></a>Örnek

CLR etkinleştirme günlükleri, barındırma API'leri, çok miktarda CLR etkinleştirme hakkında daha fazla veri ve CLR kullanımını sağlar. Bu verilerin çoğu Microsoft tarafından dahili olarak kullanılır, ancak bazı veri da bu makalede anlatıldığı gibi geliştiriciler için yararlı olabilir.

Günlük barındırma API'leri CLR sırayı yansıtır adı veriliyordu. Ayrıca, bu bilgisayarda algılanan çalışma zamanı kümesini hakkında yararlı bilgiler içerir. CLR etkinleştirme günlük biçimi, kendisini belgelenen değildir, ancak CLR etkinleştirme sorunlarında çözmek için gereken geliştiriciler yardımcı olmak için kullanılabilir.

> [!NOTE]
> CLR kullandığı işlemi sona erdi kadar etkinleştirme oturum açılamıyor.

> [!NOTE]
> CLR etkinleştirme günlükleri yerelleştirilmedi; Bunlar, her zaman İngilizce olarak oluşturulur.

Etkinleştirme günlüğünün aşağıdaki örnekte, en yararlı bilgiler vurgulanır ve sonra günlük açıklanmaktadır.

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

- **CLR yükleme günlüğü** yönetilen kod yüklenen işlemi başlatıldı yürütülebilir dosyanın yolunu sağlar. Bu yerel bir konak olabilir unutmayın.

    ```
    532,205950.367,CLR Loading log for C:\Tests\myapp.exe
    ```

- **Çalışma zamanı yüklü** etkinleştirme isteği için aday niteliği taşıyan CLR sürümleri bilgisayarda yüklü kümesidir.

    ```
    532,205950.382,Installed Runtime: v4.0.30319. VERSION_ARCHITECTURE: 0
    ```

- **sürümü ile oluşturulmuş** gibi bir yöntem için sağlanan ikili oluşturmak için kullanılan CLR sürümüdür [Iclrmetahostpolicy::getrequestedruntime](../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md).

    ```
    532,205950.382,C:\Tests\myapp.exe was built with version: v2.0.50727
    ```

- **İsteğe bağlı özellik Kurulum** Windows 8'de .NET Framework 3.5 etkinleştirme için ifade eder. Bkz: [.NET Framework başlatma hataları: Kullanıcı deneyimini yönetme](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md) bu senaryo hakkında daha fazla bilgi için.

    ```
    532,205950.398,Launching feature-on-demand installation. CmdLine: C:\Windows\system32\fondue.exe /enable-feature:NetFx3
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [Dağıtım](../../../docs/framework/deployment/index.md)
- [Nasıl yapılır: Bir uygulamayı .NET Framework 4 veya sonraki sürümler destekleyecek şekilde yapılandırma](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)