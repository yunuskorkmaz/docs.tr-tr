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
# <a name="how-to-debug-clr-activation-issues"></a><span data-ttu-id="601b0-102">CLR etkinleştirme sorunlarında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="601b0-102">How to debug CLR activation issues</span></span>

<span data-ttu-id="601b0-103">Uygulamanızın doğru sürümü ortak dil çalışma zamanı (CLR) ile çalışmaya başlama sorunlarla karşılaşırsanız, görüntüleyebilir ve hata ayıklama CLR etkinleştirme günlüklerini.</span><span class="sxs-lookup"><span data-stu-id="601b0-103">If you encounter problems in getting your application to run with the correct version of the common language runtime (CLR), you can view and debug CLR activation logs.</span></span> <span data-ttu-id="601b0-104">Bu günlükler bir etkinleştirme sorunun kök nedenini belirlerken uygulamanızın beklenenden farklı bir CLR sürümü yükler veya CLR hiç yüklenmiyor çok kullanışlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="601b0-104">These logs can be very useful in determining the root cause of an activation issue, when your application either loads a different CLR version than expected or doesn't load the CLR at all.</span></span> <span data-ttu-id="601b0-105">[.NET Framework başlatma hataları: Kullanıcı deneyimini yönetme](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md) bir uygulama için hiçbir CLR bulunduğunda deneyimi açıklanır.</span><span class="sxs-lookup"><span data-stu-id="601b0-105">The [.NET Framework Initialization Errors: Managing the User Experience](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md) discusses the experience when no CLR is found for an application.</span></span>

<span data-ttu-id="601b0-106">CLR etkinleştirme günlük bir HKEY_LOCAL_MACHINE kayıt defteri anahtarı veya bir sistem ortam değişkeni kullanarak etkin sistem genelinde olabilir.</span><span class="sxs-lookup"><span data-stu-id="601b0-106">CLR activation logging can be enabled system-wide by using an HKEY_LOCAL_MACHINE registry key or a system environment variable.</span></span> <span data-ttu-id="601b0-107">Kayıt defteri girişini kadar günlük oluşturulur veya ortam değişkenini kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="601b0-107">The log will be generated until the registry entry or the environment variable is removed.</span></span> <span data-ttu-id="601b0-108">Alternatif olarak, farklı kapsam ve süresi ile günlüğe kaydetmeyi etkinleştirmek için bir kullanıcı veya işlem yerel ortam değişkenini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="601b0-108">Alternatively, you can use a user or process-local environment variable to enable logging with a different scope and duration.</span></span>

<span data-ttu-id="601b0-109">CLR etkinleştirme günlükleri olmamalıdır yanıltıcı ile [derleme bağlama günlüklerini](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md), tamamen farklı olan.</span><span class="sxs-lookup"><span data-stu-id="601b0-109">CLR activation logs shouldn't be confused with [assembly binding logs](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md), which are entirely different.</span></span>

## <a name="to-enable-clr-activation-logging"></a><span data-ttu-id="601b0-110">CLR etkinleştirme günlüğe kaydetmeyi etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="601b0-110">To enable CLR activation logging</span></span>

### <a name="using-the-registry"></a><span data-ttu-id="601b0-111">Kayıt defterini kullanma</span><span class="sxs-lookup"><span data-stu-id="601b0-111">Using the registry</span></span>

1. <span data-ttu-id="601b0-112">Kayıt Defteri Düzenleyicisi'nde HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft için gidin\\. NETFramework (32 bit bilgisayarda) veya HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework klasörü (64 bit bilgisayarda).</span><span class="sxs-lookup"><span data-stu-id="601b0-112">In the Registry Editor, navigate to HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework (on a 32-bit computer) or HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework folder (on a 64-bit computer).</span></span>

2. <span data-ttu-id="601b0-113">Adlı bir dize değeri ekleyin `CLRLoadLogDir`, CLR etkinleştirme günlüklerini depolamak istediğiniz varolan bir dizinin tam yolunu ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="601b0-113">Add a string value named `CLRLoadLogDir`, and set it to the full path of an existing directory where you'd like to store CLR activation logs.</span></span>

<span data-ttu-id="601b0-114">Dize değeri kaldırana kadar etkinleştirme günlük kaydı etkin olarak kalır.</span><span class="sxs-lookup"><span data-stu-id="601b0-114">Activation logging remains enabled until you remove the string value.</span></span>

### <a name="using-an-environment-variable"></a><span data-ttu-id="601b0-115">Bir ortam değişkeni kullanarak</span><span class="sxs-lookup"><span data-stu-id="601b0-115">Using an environment variable</span></span>

- <span data-ttu-id="601b0-116">Ayarlama `COMPLUS_CLRLoadLogDir` ortam değişkenine istediğiniz CLR etkinleştirme günlüklerini depolamak için mevcut bir dizinin tam yolu temsil eden bir dize.</span><span class="sxs-lookup"><span data-stu-id="601b0-116">Set the `COMPLUS_CLRLoadLogDir` environment variable to a string that represents the full path of an existing directory where you'd like to store CLR activation logs.</span></span>

     <span data-ttu-id="601b0-117">Ortam değişkenini nasıl kapsamı belirler:</span><span class="sxs-lookup"><span data-stu-id="601b0-117">How you set the environment variable determines its scope:</span></span>

    - <span data-ttu-id="601b0-118">Sistem düzeyinde ayarlarsanız, ortam değişkenini kaldırılana kadar etkinleştirme günlük kaydı o bilgisayardaki tüm .NET Framework uygulamaları için etkindir.</span><span class="sxs-lookup"><span data-stu-id="601b0-118">If you set it at the system level, activation logging is enabled for all .NET Framework applications on that computer until the environment variable is removed.</span></span>

    - <span data-ttu-id="601b0-119">Kullanıcı düzeyinde ayarlarsanız, etkinleştirme günlüğü yalnızca geçerli kullanıcı hesabı için etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="601b0-119">If you set it at the user level, activation logging is enabled only for the current user account.</span></span> <span data-ttu-id="601b0-120">Ortam değişkenini kaldırılana kadar günlüğe kaydetmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="601b0-120">Logging continues until the environment variable is removed.</span></span>

    - <span data-ttu-id="601b0-121">Gelen işlem dahilinde CLR yüklemeden önce ayarlarsanız, işlem sonlanana kadar etkinleştirme günlük kaydı etkindir.</span><span class="sxs-lookup"><span data-stu-id="601b0-121">If you set it from within the process before loading the CLR, activation logging is enabled until the process terminates.</span></span>

    - <span data-ttu-id="601b0-122">Bir uygulamayı çalıştırmadan önce bir komut isteminde ayarlarsanız, bu komut istemi'nden çalıştırmak herhangi bir uygulama için etkinleştirme günlük kaydı etkindir.</span><span class="sxs-lookup"><span data-stu-id="601b0-122">If you set it at a command prompt before you run an application, activation logging is enabled for any application that is run from that command prompt.</span></span>

     <span data-ttu-id="601b0-123">Örneğin, işlem düzeyinde kapsamlı c:\clrloadlogs dizinde etkinleştirme günlüklerini depolamak için bir komut istemi penceresi açın ve uygulamayı çalıştırmadan önce aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="601b0-123">For example, to store activation logs in the c:\clrloadlogs directory with process-level scope, open a Command Prompt window and type the following before you run the application:</span></span>

    ```
    set COMPLUS_CLRLoadLogDir=c:\clrloadlogs
    ```

## <a name="example"></a><span data-ttu-id="601b0-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="601b0-124">Example</span></span>

<span data-ttu-id="601b0-125">CLR etkinleştirme günlükleri, barındırma API'leri, çok miktarda CLR etkinleştirme hakkında daha fazla veri ve CLR kullanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="601b0-125">CLR activation logs provide a large amount of data about CLR activation and the use of the CLR hosting APIs.</span></span> <span data-ttu-id="601b0-126">Bu verilerin çoğu Microsoft tarafından dahili olarak kullanılır, ancak bazı veri da bu makalede anlatıldığı gibi geliştiriciler için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="601b0-126">Most of this data is used internally by Microsoft, but some of the data can also be useful to developers, as described in this article.</span></span>

<span data-ttu-id="601b0-127">Günlük barındırma API'leri CLR sırayı yansıtır adı veriliyordu.</span><span class="sxs-lookup"><span data-stu-id="601b0-127">The log reflects the order in which the CLR hosting APIs were called.</span></span> <span data-ttu-id="601b0-128">Ayrıca, bu bilgisayarda algılanan çalışma zamanı kümesini hakkında yararlı bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="601b0-128">It also includes useful data about the set of installed runtimes detected on the computer.</span></span> <span data-ttu-id="601b0-129">CLR etkinleştirme günlük biçimi, kendisini belgelenen değildir, ancak CLR etkinleştirme sorunlarında çözmek için gereken geliştiriciler yardımcı olmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="601b0-129">The CLR activation log format is not itself documented, but can be used to aid developers who need to resolve CLR activation issues.</span></span>

> [!NOTE]
> <span data-ttu-id="601b0-130">CLR kullandığı işlemi sona erdi kadar etkinleştirme oturum açılamıyor.</span><span class="sxs-lookup"><span data-stu-id="601b0-130">You cannot open an activation log until the process that uses the CLR has terminated.</span></span>

> [!NOTE]
> <span data-ttu-id="601b0-131">CLR etkinleştirme günlükleri yerelleştirilmedi; Bunlar, her zaman İngilizce olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="601b0-131">CLR activation logs are not localized; they are always generated in the English language.</span></span>

<span data-ttu-id="601b0-132">Etkinleştirme günlüğünün aşağıdaki örnekte, en yararlı bilgiler vurgulanır ve sonra günlük açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="601b0-132">In the following example of an activation log, the most useful information is highlighted and described after the log.</span></span>

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

- <span data-ttu-id="601b0-133">**CLR yükleme günlüğü** yönetilen kod yüklenen işlemi başlatıldı yürütülebilir dosyanın yolunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="601b0-133">**CLR Loading log** provides the path to the executable that started the process that loaded managed code.</span></span> <span data-ttu-id="601b0-134">Bu yerel bir konak olabilir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="601b0-134">Note that this could be a native host.</span></span>

    ```
    532,205950.367,CLR Loading log for C:\Tests\myapp.exe
    ```

- <span data-ttu-id="601b0-135">**Çalışma zamanı yüklü** etkinleştirme isteği için aday niteliği taşıyan CLR sürümleri bilgisayarda yüklü kümesidir.</span><span class="sxs-lookup"><span data-stu-id="601b0-135">**Installed Runtime** is the set of CLR versions installed on the computer that are candidates for the activation request.</span></span>

    ```
    532,205950.382,Installed Runtime: v4.0.30319. VERSION_ARCHITECTURE: 0
    ```

- <span data-ttu-id="601b0-136">**sürümü ile oluşturulmuş** gibi bir yöntem için sağlanan ikili oluşturmak için kullanılan CLR sürümüdür [Iclrmetahostpolicy::getrequestedruntime](../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="601b0-136">**built with version** is the version of the CLR that was used to build the binary that was provided to a method such as [ICLRMetaHostPolicy::GetRequestedRuntime](../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md).</span></span>

    ```
    532,205950.382,C:\Tests\myapp.exe was built with version: v2.0.50727
    ```

- <span data-ttu-id="601b0-137">**İsteğe bağlı özellik Kurulum** Windows 8'de .NET Framework 3.5 etkinleştirme için ifade eder.</span><span class="sxs-lookup"><span data-stu-id="601b0-137">**feature-on-demand installation** refers to enabling the .NET Framework 3.5 on Windows 8.</span></span> <span data-ttu-id="601b0-138">Bkz: [.NET Framework başlatma hataları: Kullanıcı deneyimini yönetme](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md) bu senaryo hakkında daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="601b0-138">See [.NET Framework Initialization Errors: Managing the User Experience](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md) for more information about this scenario.</span></span>

    ```
    532,205950.398,Launching feature-on-demand installation. CmdLine: C:\Windows\system32\fondue.exe /enable-feature:NetFx3
    ```

## <a name="see-also"></a><span data-ttu-id="601b0-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="601b0-139">See also</span></span>

- [<span data-ttu-id="601b0-140">Dağıtım</span><span class="sxs-lookup"><span data-stu-id="601b0-140">Deployment</span></span>](../../../docs/framework/deployment/index.md)
- [<span data-ttu-id="601b0-141">Nasıl yapılır: Bir uygulamayı .NET Framework 4 veya sonraki sürümler destekleyecek şekilde yapılandırma</span><span class="sxs-lookup"><span data-stu-id="601b0-141">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)