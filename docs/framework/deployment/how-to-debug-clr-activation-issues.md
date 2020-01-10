---
title: CLR etkinleştirme sorunlarını ayıklama
ms.date: 03/30/2017
helpviewer_keywords:
- CLR activation, debugging issues
ms.assetid: 4fe17546-d56e-4344-a930-6d8e4a545914
ms.openlocfilehash: 602ee3c88237a902d48339836fbe25f636ae9705
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716503"
---
# <a name="how-to-debug-clr-activation-issues"></a>CLR etkinleştirme sorunlarını ayıklama

Uygulamanızı ortak dil çalışma zamanının (CLR) doğru sürümü ile çalışacak şekilde almaya yönelik sorunlarla karşılaşırsanız, CLR etkinleştirme günlüklerini görüntüleyebilir ve hata ayıklaması yapabilirsiniz. Bu Günlükler, uygulamanız beklenenden farklı bir CLR sürümü yüklediğinde veya CLR 'yi hiç yüklemediğinde, bir etkinleştirme sorununun kök nedenini belirlemede çok yararlı olabilir. [.NET Framework başlatma hataları: Kullanıcı deneyimini yönetmek](initialization-errors-managing-the-user-experience.md) , bir uygulama için clr bulunamadığı zaman deneyimi ele alır.

CLR etkinleştirme günlüğü, bir HKEY_LOCAL_MACHINE kayıt defteri anahtarı veya bir sistem ortam değişkeni kullanılarak sistem genelinde etkinleştirilebilir. Günlük kaydı, kayıt defteri girişi veya ortam değişkeni kaldırılana kadar oluşturulur. Alternatif olarak, farklı bir kapsam ve süre ile günlüğe kaydetmeyi etkinleştirmek için bir kullanıcı veya işlem yerel ortam değişkeni kullanabilirsiniz.

CLR etkinleştirme günlükleri, tamamen farklı olan [bütünleştirilmiş kod bağlama günlükleriyle](../tools/fuslogvw-exe-assembly-binding-log-viewer.md)karıştırılmamalıdır.

## <a name="to-enable-clr-activation-logging"></a>CLR etkinleştirme günlük kaydını etkinleştirmek için

### <a name="using-the-registry"></a>Kayıt defterini kullanma

1. Kayıt Defteri Düzenleyicisi 'nde, HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\\adresine gidin. NETFramework (32 bitlik bir bilgisayarda) veya \SOFTWARE\Wow6432Node\Microsoft\\HKEY_LOCAL_MACHINE. NETFramework klasörü (64 bitlik bir bilgisayarda).

2. `CLRLoadLogDir`adlı bir dize değeri ekleyin ve CLR etkinleştirme günlüklerini depolamak istediğiniz mevcut bir dizinin tam yolu olarak ayarlayın.

Etkinleştirme günlüğü, dize değerini kaldırana kadar etkin kalır.

### <a name="using-an-environment-variable"></a>Ortam değişkeni kullanma

- `COMPLUS_CLRLoadLogDir` ortam değişkenini, CLR etkinleştirme günlüklerini depolamak istediğiniz mevcut bir dizinin tam yolunu temsil eden bir dizeye ayarlayın.

    Ortam değişkenini nasıl ayarlarsanız kapsamını belirler:

  - Bunu sistem düzeyinde ayarlarsanız, ortam değişkeni kaldırılana kadar, bu bilgisayardaki tüm .NET Framework uygulamaları için etkinleştirme günlüğü etkinleştirilir.

  - Bunu Kullanıcı düzeyinde ayarlarsanız, etkinleştirme günlüğü yalnızca geçerli kullanıcı hesabı için etkinleştirilir. Ortam değişkeni kaldırılana kadar günlüğe kaydetme devam eder.

  - CLR yüklemeden önce işlemin içinden ayarlarsanız, işlem sonlanana kadar etkinleştirme günlüğü etkinleştirilir.

  - Uygulamayı çalıştırmadan önce bir komut isteminde ayarlarsanız, bu komut isteminden çalıştırılan herhangi bir uygulama için etkinleştirme günlüğü etkinleştirilir.

    Örneğin, etkinleştirme günlüklerini işlem düzeyi kapsama sahip c:\clrloadlogs dizininde depolamak için, uygulamayı çalıştırmadan önce bir komut Istemi penceresi açın ve aşağıdakini yazın:

    ```console
    set COMPLUS_CLRLoadLogDir=c:\clrloadlogs
    ```

## <a name="example"></a>Örnek

CLR etkinleştirme günlükleri CLR etkinleştirme ve CLR barındırma API 'lerinin kullanımı hakkında büyük miktarda veri sağlar. Bu verilerin çoğu Microsoft tarafından dahili olarak kullanılır, ancak bazı veriler bu makalede açıklandığı gibi geliştiriciler için de yararlı olabilir.

Günlük, CLR barındırma API 'Lerinin çağrıldığı sırayı yansıtır. Ayrıca, bilgisayarda algılanan yüklü çalışma zamanları kümesiyle ilgili yararlı verileri de içerir. CLR etkinleştirme günlük biçimi kendisini belgelenmemiş, ancak CLR etkinleştirme sorunlarını çözmesi gereken geliştiricilere yardımcı olmak için kullanılabilir.

> [!NOTE]
> CLR kullanan işlem sonlandırılana kadar bir etkinleştirme günlüğü açamazsınız.

> [!NOTE]
> CLR etkinleştirme günlükleri yerelleştirilmemiş; Bunlar her zaman Ingilizce dilinde oluşturulur.

Aşağıdaki bir etkinleştirme günlüğü örneğinde, en yararlı bilgiler vurgulanır ve günlüğün ardından açıklanır.

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

- **Clr yükleme günlüğü** , yönetilen kodu yükleyen işlemi başlatan yürütülebilir dosyanın yolunu sağlar. Bunun yerel bir konak olabileceğini unutmayın.

    ```output
    532,205950.367,CLR Loading log for C:\Tests\myapp.exe
    ```

- **Yüklü çalışma zamanı** , etkinleştirme isteği için aday olan bilgisayarda yüklü olan CLR sürümleri kümesidir.

    ```output
    532,205950.382,Installed Runtime: v4.0.30319. VERSION_ARCHITECTURE: 0
    ```

- **sürümü ile birlikte inşa** edilen, [ICLRMetaHostPolicy:: GetRequestedRuntime](../unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)gibi bir yönteme sağlanmış ikiliyi oluşturmak için kullanılan CLR 'nin sürümüdür.

    ```output
    532,205950.382,C:\Tests\myapp.exe was built with version: v2.0.50727
    ```

- **isteğe bağlı özellik yüklemesi** , Windows 8 ' de .NET Framework 3,5 ' i etkinleştirmeyi belirtir. Bu senaryo hakkında daha fazla bilgi için bkz. [.NET Framework başlatma hataları: Kullanıcı deneyimini yönetme](initialization-errors-managing-the-user-experience.md) .

    ```output
    532,205950.398,Launching feature-on-demand installation. CmdLine: C:\Windows\system32\fondue.exe /enable-feature:NetFx3
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [Dağıtım](index.md)
- [Nasıl yapılır: .NET Framework 4 veya sonraki sürümleri desteklemek için uygulama yapılandırma](../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
