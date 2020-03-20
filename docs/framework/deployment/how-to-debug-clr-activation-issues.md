---
title: CLR etkinleştirme sorunlarını hata ayıklama
ms.date: 03/30/2017
helpviewer_keywords:
- CLR activation, debugging issues
ms.assetid: 4fe17546-d56e-4344-a930-6d8e4a545914
ms.openlocfilehash: 602ee3c88237a902d48339836fbe25f636ae9705
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75716503"
---
# <a name="how-to-debug-clr-activation-issues"></a>CLR etkinleştirme sorunlarını hata ayıklama

Uygulamanızın ortak dil çalışma zamanının (CLR) doğru sürümüyle çalıştırılmasında sorunlarla karşılaşırsanız, CLR etkinleştirme günlüklerini görüntüleyebilir ve hata ayıklayabilirsiniz. Bu günlükler, uygulamanız beklenenden farklı bir CLR sürümü yüklediğinde veya CLR'yi hiç yüklemediğinde, etkinleştirme sorununun temel nedenini belirlemede çok yararlı olabilir. [.NET Framework Initialization Errors: Kullanıcı Deneyimini yönetme,](initialization-errors-managing-the-user-experience.md) bir uygulama için CLR bulunmadığında deneyimi tartışır.

CLR etkinleştirme günlüğü, HKEY_LOCAL_MACHINE kayıt defteri anahtarı veya sistem ortamı değişkeni kullanılarak sistem genelinde etkinleştirilebilir. Kayıt defteri girişi veya ortam değişkeni kaldırılana kadar günlük oluşturulur. Alternatif olarak, farklı bir kapsam ve süre ile günlüğe kaydetmeyi etkinleştirmek için bir kullanıcı veya işlem yerel ortam değişkeni kullanabilirsiniz.

CLR etkinleştirme günlükleri tamamen farklı [derleme bağlama günlükleri](../tools/fuslogvw-exe-assembly-binding-log-viewer.md)ile karıştırılmamalıdır.

## <a name="to-enable-clr-activation-logging"></a>CLR etkinleştirme günlüğe kaydetmeyi etkinleştirmek için

### <a name="using-the-registry"></a>Kayıt defterini kullanma

1. Kayıt Defteri Düzenleyicisi'nde HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft'a\\gidin. NETFramework (32 bit bilgisayarda) veya HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework klasörü (64 bit bilgisayarda).

2. Adlandırılmış `CLRLoadLogDir`bir dize değeri ekleyin ve CLR etkinleştirme günlüklerini depolamak istediğiniz varolan bir dizinin tam yoluna ayarlayın.

Etkinleştirme günlüğe kaydetme, dize değerini kaldırana kadar etkin kalır.

### <a name="using-an-environment-variable"></a>Bir ortam değişkenini kullanma

- Çevre `COMPLUS_CLRLoadLogDir` değişkenini, CLR etkinleştirme günlüklerini depolamak istediğiniz varolan bir dizinin tam yolunu temsil eden bir dize ayarlayın.

    Ortam değişkenini nasıl ayarladığınız kapsamını belirler:

  - Sistem düzeyinde ayarlarsanız, ortam değişkeni kaldırılıncaya kadar o bilgisayardaki tüm .NET Framework uygulamaları için etkinleştirme günlüğe kaydetme etkinleştirilir.

  - Kullanıcı düzeyinde ayarlarsanız, etkinleştirme günlüğe kaydetme yalnızca geçerli kullanıcı hesabı için etkinleştirilir. Günlüğe kaydetme, ortam değişkeni kaldırılana kadar devam eder.

  - CLR'yi yüklemeden önce işlem içinden ayarlarsanız, işlem sona erene kadar etkinleştirme günlüğe kaydetme etkinleştirilir.

  - Bir uygulamayı çalıştırmadan önce komut isteminde ayarlarsanız, bu komut isteminden çalıştırılabilen herhangi bir uygulama için etkinleştirme günlüğe kaydetme etkindir.

    Örneğin, etkinleştirme günlüklerini işlem düzeyi kapsamıyla c:\clrloadlogs dizininde depolamak için, bir Komut İstem penceresi açın ve uygulamayı çalıştırmadan önce aşağıdakileri yazın:

    ```console
    set COMPLUS_CLRLoadLogDir=c:\clrloadlogs
    ```

## <a name="example"></a>Örnek

CLR etkinleştirme günlükleri, CLR etkinleştirme ve CLR barındırma API'lerinin kullanımı hakkında büyük miktarda veri sağlar. Bu verilerin çoğu Microsoft tarafından dahili olarak kullanılır, ancak bu makalede açıklandığı gibi bazı veriler geliştiriciler için de yararlı olabilir.

Günlük, API barındırma CLR çağrıldığı sırasını yansıtır. Ayrıca, bilgisayarda algılanan yüklü çalışma süreleri kümesi hakkında yararlı veriler de içerir. CLR etkinleştirme günlüğü biçimi kendisi belgelenmiş değildir, ancak CLR etkinleştirme sorunlarını çözmesi gereken geliştiricilere yardımcı olmak için kullanılabilir.

> [!NOTE]
> CLR kullanan işlem sonlandırılmadan bir etkinleştirme günlüğü açamazsınız.

> [!NOTE]
> CLR etkinleştirme günlükleri yerelleştirilmiş değil; her zaman İngilizce üretilir.

Etkinleştirme günlüğünün aşağıdaki örneğinde, en yararlı bilgiler vurgulanır ve günlükten sonra açıklanır.

```output
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

- **CLR Yükleme günlüğü,** yönetilen kodu yükleyen işlemi başlatan yürütülebilir yol sağlar. Bunun yerel bir ana bilgisayar olabileceğini unutmayın.

    ```output
    532,205950.367,CLR Loading log for C:\Tests\myapp.exe
    ```

- **Yüklü Runtime,** etkinleştirme isteği için aday olan bilgisayarda yüklü CLR sürümleri kümesidir.

    ```output
    532,205950.382,Installed Runtime: v4.0.30319. VERSION_ARCHITECTURE: 0
    ```

- **sürümü ile inşa** ICLRMetaHostPolicy gibi bir yöntem için sağlanan ikili oluşturmak için kullanılan [CLR sürümü::GetRequestedRuntime](../unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md).

    ```output
    532,205950.382,C:\Tests\myapp.exe was built with version: v2.0.50727
    ```

- **isteğe bağlı özellik yüklemesi,** Windows 8'de .NET Framework 3.5'i etkinleştirmek anlamına gelir. Bkz. [.NET Framework Initialization Errors:](initialization-errors-managing-the-user-experience.md) Bu senaryo hakkında daha fazla bilgi için Kullanıcı Deneyimini Yönetme.

    ```output
    532,205950.398,Launching feature-on-demand installation. CmdLine: C:\Windows\system32\fondue.exe /enable-feature:NetFx3
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [Dağıtım](index.md)
- [Nasıl yapilir: Bir uygulamayı .NET Framework 4 veya sonraki sürümlerini destekleyecek şekilde yapılandırın](../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
