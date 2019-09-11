---
title: CLR etkinleştirme sorunlarını ayıklama
ms.date: 03/30/2017
helpviewer_keywords:
- CLR activation, debugging issues
ms.assetid: 4fe17546-d56e-4344-a930-6d8e4a545914
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7ab80cfbd0ae2130f465216ca77812bda0002c24
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854010"
---
# <a name="how-to-debug-clr-activation-issues"></a><span data-ttu-id="2c72b-102">CLR etkinleştirme sorunlarını ayıklama</span><span class="sxs-lookup"><span data-stu-id="2c72b-102">How to debug CLR activation issues</span></span>

<span data-ttu-id="2c72b-103">Uygulamanızı ortak dil çalışma zamanının (CLR) doğru sürümü ile çalışacak şekilde almaya yönelik sorunlarla karşılaşırsanız, CLR etkinleştirme günlüklerini görüntüleyebilir ve hata ayıklaması yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2c72b-103">If you encounter problems in getting your application to run with the correct version of the common language runtime (CLR), you can view and debug CLR activation logs.</span></span> <span data-ttu-id="2c72b-104">Bu Günlükler, uygulamanız beklenenden farklı bir CLR sürümü yüklediğinde veya CLR 'yi hiç yüklemediğinde, bir etkinleştirme sorununun kök nedenini belirlemede çok yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="2c72b-104">These logs can be very useful in determining the root cause of an activation issue, when your application either loads a different CLR version than expected or doesn't load the CLR at all.</span></span> <span data-ttu-id="2c72b-105">[.NET Framework başlatma hataları: Kullanıcı deneyimini](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md) yönetmek, bir uygulama için clr bulunamadığı zaman deneyimi ele alır.</span><span class="sxs-lookup"><span data-stu-id="2c72b-105">The [.NET Framework Initialization Errors: Managing the User Experience](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md) discusses the experience when no CLR is found for an application.</span></span>

<span data-ttu-id="2c72b-106">CLR etkinleştirme günlüğü, bir HKEY_LOCAL_MACHINE kayıt defteri anahtarı veya bir sistem ortam değişkeni kullanılarak sistem genelinde etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="2c72b-106">CLR activation logging can be enabled system-wide by using an HKEY_LOCAL_MACHINE registry key or a system environment variable.</span></span> <span data-ttu-id="2c72b-107">Günlük kaydı, kayıt defteri girişi veya ortam değişkeni kaldırılana kadar oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2c72b-107">The log will be generated until the registry entry or the environment variable is removed.</span></span> <span data-ttu-id="2c72b-108">Alternatif olarak, farklı bir kapsam ve süre ile günlüğe kaydetmeyi etkinleştirmek için bir kullanıcı veya işlem yerel ortam değişkeni kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2c72b-108">Alternatively, you can use a user or process-local environment variable to enable logging with a different scope and duration.</span></span>

<span data-ttu-id="2c72b-109">CLR etkinleştirme günlükleri, tamamen farklı olan [bütünleştirilmiş kod bağlama günlükleriyle](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md)karıştırılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="2c72b-109">CLR activation logs shouldn't be confused with [assembly binding logs](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md), which are entirely different.</span></span>

## <a name="to-enable-clr-activation-logging"></a><span data-ttu-id="2c72b-110">CLR etkinleştirme günlük kaydını etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="2c72b-110">To enable CLR activation logging</span></span>

### <a name="using-the-registry"></a><span data-ttu-id="2c72b-111">Kayıt defterini kullanma</span><span class="sxs-lookup"><span data-stu-id="2c72b-111">Using the registry</span></span>

1. <span data-ttu-id="2c72b-112">Kayıt Defteri Düzenleyicisi 'nde HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\adresine gidin. NETFramework (32 bitlik bir bilgisayarda) veya HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework klasörü (64 bitlik bir bilgisayarda).</span><span class="sxs-lookup"><span data-stu-id="2c72b-112">In the Registry Editor, navigate to HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework (on a 32-bit computer) or HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework folder (on a 64-bit computer).</span></span>

2. <span data-ttu-id="2c72b-113">Adlı `CLRLoadLogDir`bir dize değeri ekleyin ve CLR etkinleştirme günlüklerini depolamak istediğiniz mevcut bir dizinin tam yolu olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2c72b-113">Add a string value named `CLRLoadLogDir`, and set it to the full path of an existing directory where you'd like to store CLR activation logs.</span></span>

<span data-ttu-id="2c72b-114">Etkinleştirme günlüğü, dize değerini kaldırana kadar etkin kalır.</span><span class="sxs-lookup"><span data-stu-id="2c72b-114">Activation logging remains enabled until you remove the string value.</span></span>

### <a name="using-an-environment-variable"></a><span data-ttu-id="2c72b-115">Ortam değişkeni kullanma</span><span class="sxs-lookup"><span data-stu-id="2c72b-115">Using an environment variable</span></span>

- <span data-ttu-id="2c72b-116">`COMPLUS_CLRLoadLogDir` Ortam değişkenini, CLR etkinleştirme günlüklerini depolamak istediğiniz mevcut bir dizinin tam yolunu temsil eden bir dizeye ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2c72b-116">Set the `COMPLUS_CLRLoadLogDir` environment variable to a string that represents the full path of an existing directory where you'd like to store CLR activation logs.</span></span>

    <span data-ttu-id="2c72b-117">Ortam değişkenini nasıl ayarlarsanız kapsamını belirler:</span><span class="sxs-lookup"><span data-stu-id="2c72b-117">How you set the environment variable determines its scope:</span></span>

  - <span data-ttu-id="2c72b-118">Bunu sistem düzeyinde ayarlarsanız, ortam değişkeni kaldırılana kadar, bu bilgisayardaki tüm .NET Framework uygulamaları için etkinleştirme günlüğü etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="2c72b-118">If you set it at the system level, activation logging is enabled for all .NET Framework applications on that computer until the environment variable is removed.</span></span>

  - <span data-ttu-id="2c72b-119">Bunu Kullanıcı düzeyinde ayarlarsanız, etkinleştirme günlüğü yalnızca geçerli kullanıcı hesabı için etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="2c72b-119">If you set it at the user level, activation logging is enabled only for the current user account.</span></span> <span data-ttu-id="2c72b-120">Ortam değişkeni kaldırılana kadar günlüğe kaydetme devam eder.</span><span class="sxs-lookup"><span data-stu-id="2c72b-120">Logging continues until the environment variable is removed.</span></span>

  - <span data-ttu-id="2c72b-121">CLR yüklemeden önce işlemin içinden ayarlarsanız, işlem sonlanana kadar etkinleştirme günlüğü etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="2c72b-121">If you set it from within the process before loading the CLR, activation logging is enabled until the process terminates.</span></span>

  - <span data-ttu-id="2c72b-122">Uygulamayı çalıştırmadan önce bir komut isteminde ayarlarsanız, bu komut isteminden çalıştırılan herhangi bir uygulama için etkinleştirme günlüğü etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="2c72b-122">If you set it at a command prompt before you run an application, activation logging is enabled for any application that is run from that command prompt.</span></span>

    <span data-ttu-id="2c72b-123">Örneğin, etkinleştirme günlüklerini işlem düzeyi kapsama sahip c:\clrloadlogs dizininde depolamak için, uygulamayı çalıştırmadan önce bir komut Istemi penceresi açın ve aşağıdakini yazın:</span><span class="sxs-lookup"><span data-stu-id="2c72b-123">For example, to store activation logs in the c:\clrloadlogs directory with process-level scope, open a Command Prompt window and type the following before you run the application:</span></span>

    ```console
    set COMPLUS_CLRLoadLogDir=c:\clrloadlogs
    ```

## <a name="example"></a><span data-ttu-id="2c72b-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="2c72b-124">Example</span></span>

<span data-ttu-id="2c72b-125">CLR etkinleştirme günlükleri CLR etkinleştirme ve CLR barındırma API 'lerinin kullanımı hakkında büyük miktarda veri sağlar.</span><span class="sxs-lookup"><span data-stu-id="2c72b-125">CLR activation logs provide a large amount of data about CLR activation and the use of the CLR hosting APIs.</span></span> <span data-ttu-id="2c72b-126">Bu verilerin çoğu Microsoft tarafından dahili olarak kullanılır, ancak bazı veriler bu makalede açıklandığı gibi geliştiriciler için de yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="2c72b-126">Most of this data is used internally by Microsoft, but some of the data can also be useful to developers, as described in this article.</span></span>

<span data-ttu-id="2c72b-127">Günlük, CLR barındırma API 'Lerinin çağrıldığı sırayı yansıtır.</span><span class="sxs-lookup"><span data-stu-id="2c72b-127">The log reflects the order in which the CLR hosting APIs were called.</span></span> <span data-ttu-id="2c72b-128">Ayrıca, bilgisayarda algılanan yüklü çalışma zamanları kümesiyle ilgili yararlı verileri de içerir.</span><span class="sxs-lookup"><span data-stu-id="2c72b-128">It also includes useful data about the set of installed runtimes detected on the computer.</span></span> <span data-ttu-id="2c72b-129">CLR etkinleştirme günlük biçimi kendisini belgelenmemiş, ancak CLR etkinleştirme sorunlarını çözmesi gereken geliştiricilere yardımcı olmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2c72b-129">The CLR activation log format is not itself documented, but can be used to aid developers who need to resolve CLR activation issues.</span></span>

> [!NOTE]
> <span data-ttu-id="2c72b-130">CLR kullanan işlem sonlandırılana kadar bir etkinleştirme günlüğü açamazsınız.</span><span class="sxs-lookup"><span data-stu-id="2c72b-130">You cannot open an activation log until the process that uses the CLR has terminated.</span></span>

> [!NOTE]
> <span data-ttu-id="2c72b-131">CLR etkinleştirme günlükleri yerelleştirilmemiş; Bunlar her zaman Ingilizce dilinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2c72b-131">CLR activation logs are not localized; they are always generated in the English language.</span></span>

<span data-ttu-id="2c72b-132">Aşağıdaki bir etkinleştirme günlüğü örneğinde, en yararlı bilgiler vurgulanır ve günlüğün ardından açıklanır.</span><span class="sxs-lookup"><span data-stu-id="2c72b-132">In the following example of an activation log, the most useful information is highlighted and described after the log.</span></span>

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

- <span data-ttu-id="2c72b-133">**Clr yükleme günlüğü** , yönetilen kodu yükleyen işlemi başlatan yürütülebilir dosyanın yolunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="2c72b-133">**CLR Loading log** provides the path to the executable that started the process that loaded managed code.</span></span> <span data-ttu-id="2c72b-134">Bunun yerel bir konak olabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2c72b-134">Note that this could be a native host.</span></span>

    ```output
    532,205950.367,CLR Loading log for C:\Tests\myapp.exe
    ```

- <span data-ttu-id="2c72b-135">**Yüklü çalışma zamanı** , etkinleştirme isteği için aday olan bilgisayarda yüklü olan CLR sürümleri kümesidir.</span><span class="sxs-lookup"><span data-stu-id="2c72b-135">**Installed Runtime** is the set of CLR versions installed on the computer that are candidates for the activation request.</span></span>

    ```output
    532,205950.382,Installed Runtime: v4.0.30319. VERSION_ARCHITECTURE: 0
    ```

- <span data-ttu-id="2c72b-136">**sürümü ile birlikte inşa** edilen, [ICLRMetaHostPolicy:: GetRequestedRuntime](../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)gibi bir yönteme sağlanmış ikiliyi oluşturmak için kullanılan CLR 'nin sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="2c72b-136">**built with version** is the version of the CLR that was used to build the binary that was provided to a method such as [ICLRMetaHostPolicy::GetRequestedRuntime](../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md).</span></span>

    ```output
    532,205950.382,C:\Tests\myapp.exe was built with version: v2.0.50727
    ```

- <span data-ttu-id="2c72b-137">**isteğe bağlı özellik yüklemesi** , Windows 8 ' de .NET Framework 3,5 ' i etkinleştirmeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="2c72b-137">**feature-on-demand installation** refers to enabling the .NET Framework 3.5 on Windows 8.</span></span> <span data-ttu-id="2c72b-138">Bkz [. .NET Framework başlatma hataları: Bu senaryo hakkında daha](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md) fazla bilgi için Kullanıcı deneyimini yönetme.</span><span class="sxs-lookup"><span data-stu-id="2c72b-138">See [.NET Framework Initialization Errors: Managing the User Experience](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md) for more information about this scenario.</span></span>

    ```output
    532,205950.398,Launching feature-on-demand installation. CmdLine: C:\Windows\system32\fondue.exe /enable-feature:NetFx3
    ```

## <a name="see-also"></a><span data-ttu-id="2c72b-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c72b-139">See also</span></span>

- [<span data-ttu-id="2c72b-140">Dağıtım</span><span class="sxs-lookup"><span data-stu-id="2c72b-140">Deployment</span></span>](../../../docs/framework/deployment/index.md)
- [<span data-ttu-id="2c72b-141">Nasıl yapılır: .NET Framework 4 veya sonraki sürümleri desteklemek için bir uygulama yapılandırma</span><span class="sxs-lookup"><span data-stu-id="2c72b-141">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
