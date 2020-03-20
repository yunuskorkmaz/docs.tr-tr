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
# <a name="how-to-debug-clr-activation-issues"></a><span data-ttu-id="2b184-102">CLR etkinleştirme sorunlarını hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="2b184-102">How to debug CLR activation issues</span></span>

<span data-ttu-id="2b184-103">Uygulamanızın ortak dil çalışma zamanının (CLR) doğru sürümüyle çalıştırılmasında sorunlarla karşılaşırsanız, CLR etkinleştirme günlüklerini görüntüleyebilir ve hata ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b184-103">If you encounter problems in getting your application to run with the correct version of the common language runtime (CLR), you can view and debug CLR activation logs.</span></span> <span data-ttu-id="2b184-104">Bu günlükler, uygulamanız beklenenden farklı bir CLR sürümü yüklediğinde veya CLR'yi hiç yüklemediğinde, etkinleştirme sorununun temel nedenini belirlemede çok yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="2b184-104">These logs can be very useful in determining the root cause of an activation issue, when your application either loads a different CLR version than expected or doesn't load the CLR at all.</span></span> <span data-ttu-id="2b184-105">[.NET Framework Initialization Errors: Kullanıcı Deneyimini yönetme,](initialization-errors-managing-the-user-experience.md) bir uygulama için CLR bulunmadığında deneyimi tartışır.</span><span class="sxs-lookup"><span data-stu-id="2b184-105">The [.NET Framework Initialization Errors: Managing the User Experience](initialization-errors-managing-the-user-experience.md) discusses the experience when no CLR is found for an application.</span></span>

<span data-ttu-id="2b184-106">CLR etkinleştirme günlüğü, HKEY_LOCAL_MACHINE kayıt defteri anahtarı veya sistem ortamı değişkeni kullanılarak sistem genelinde etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="2b184-106">CLR activation logging can be enabled system-wide by using an HKEY_LOCAL_MACHINE registry key or a system environment variable.</span></span> <span data-ttu-id="2b184-107">Kayıt defteri girişi veya ortam değişkeni kaldırılana kadar günlük oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2b184-107">The log will be generated until the registry entry or the environment variable is removed.</span></span> <span data-ttu-id="2b184-108">Alternatif olarak, farklı bir kapsam ve süre ile günlüğe kaydetmeyi etkinleştirmek için bir kullanıcı veya işlem yerel ortam değişkeni kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b184-108">Alternatively, you can use a user or process-local environment variable to enable logging with a different scope and duration.</span></span>

<span data-ttu-id="2b184-109">CLR etkinleştirme günlükleri tamamen farklı [derleme bağlama günlükleri](../tools/fuslogvw-exe-assembly-binding-log-viewer.md)ile karıştırılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="2b184-109">CLR activation logs shouldn't be confused with [assembly binding logs](../tools/fuslogvw-exe-assembly-binding-log-viewer.md), which are entirely different.</span></span>

## <a name="to-enable-clr-activation-logging"></a><span data-ttu-id="2b184-110">CLR etkinleştirme günlüğe kaydetmeyi etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="2b184-110">To enable CLR activation logging</span></span>

### <a name="using-the-registry"></a><span data-ttu-id="2b184-111">Kayıt defterini kullanma</span><span class="sxs-lookup"><span data-stu-id="2b184-111">Using the registry</span></span>

1. <span data-ttu-id="2b184-112">Kayıt Defteri Düzenleyicisi'nde HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft'a\\gidin. NETFramework (32 bit bilgisayarda) veya HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework klasörü (64 bit bilgisayarda).</span><span class="sxs-lookup"><span data-stu-id="2b184-112">In the Registry Editor, navigate to HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework (on a 32-bit computer) or HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework folder (on a 64-bit computer).</span></span>

2. <span data-ttu-id="2b184-113">Adlandırılmış `CLRLoadLogDir`bir dize değeri ekleyin ve CLR etkinleştirme günlüklerini depolamak istediğiniz varolan bir dizinin tam yoluna ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2b184-113">Add a string value named `CLRLoadLogDir`, and set it to the full path of an existing directory where you'd like to store CLR activation logs.</span></span>

<span data-ttu-id="2b184-114">Etkinleştirme günlüğe kaydetme, dize değerini kaldırana kadar etkin kalır.</span><span class="sxs-lookup"><span data-stu-id="2b184-114">Activation logging remains enabled until you remove the string value.</span></span>

### <a name="using-an-environment-variable"></a><span data-ttu-id="2b184-115">Bir ortam değişkenini kullanma</span><span class="sxs-lookup"><span data-stu-id="2b184-115">Using an environment variable</span></span>

- <span data-ttu-id="2b184-116">Çevre `COMPLUS_CLRLoadLogDir` değişkenini, CLR etkinleştirme günlüklerini depolamak istediğiniz varolan bir dizinin tam yolunu temsil eden bir dize ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2b184-116">Set the `COMPLUS_CLRLoadLogDir` environment variable to a string that represents the full path of an existing directory where you'd like to store CLR activation logs.</span></span>

    <span data-ttu-id="2b184-117">Ortam değişkenini nasıl ayarladığınız kapsamını belirler:</span><span class="sxs-lookup"><span data-stu-id="2b184-117">How you set the environment variable determines its scope:</span></span>

  - <span data-ttu-id="2b184-118">Sistem düzeyinde ayarlarsanız, ortam değişkeni kaldırılıncaya kadar o bilgisayardaki tüm .NET Framework uygulamaları için etkinleştirme günlüğe kaydetme etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="2b184-118">If you set it at the system level, activation logging is enabled for all .NET Framework applications on that computer until the environment variable is removed.</span></span>

  - <span data-ttu-id="2b184-119">Kullanıcı düzeyinde ayarlarsanız, etkinleştirme günlüğe kaydetme yalnızca geçerli kullanıcı hesabı için etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="2b184-119">If you set it at the user level, activation logging is enabled only for the current user account.</span></span> <span data-ttu-id="2b184-120">Günlüğe kaydetme, ortam değişkeni kaldırılana kadar devam eder.</span><span class="sxs-lookup"><span data-stu-id="2b184-120">Logging continues until the environment variable is removed.</span></span>

  - <span data-ttu-id="2b184-121">CLR'yi yüklemeden önce işlem içinden ayarlarsanız, işlem sona erene kadar etkinleştirme günlüğe kaydetme etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="2b184-121">If you set it from within the process before loading the CLR, activation logging is enabled until the process terminates.</span></span>

  - <span data-ttu-id="2b184-122">Bir uygulamayı çalıştırmadan önce komut isteminde ayarlarsanız, bu komut isteminden çalıştırılabilen herhangi bir uygulama için etkinleştirme günlüğe kaydetme etkindir.</span><span class="sxs-lookup"><span data-stu-id="2b184-122">If you set it at a command prompt before you run an application, activation logging is enabled for any application that is run from that command prompt.</span></span>

    <span data-ttu-id="2b184-123">Örneğin, etkinleştirme günlüklerini işlem düzeyi kapsamıyla c:\clrloadlogs dizininde depolamak için, bir Komut İstem penceresi açın ve uygulamayı çalıştırmadan önce aşağıdakileri yazın:</span><span class="sxs-lookup"><span data-stu-id="2b184-123">For example, to store activation logs in the c:\clrloadlogs directory with process-level scope, open a Command Prompt window and type the following before you run the application:</span></span>

    ```console
    set COMPLUS_CLRLoadLogDir=c:\clrloadlogs
    ```

## <a name="example"></a><span data-ttu-id="2b184-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="2b184-124">Example</span></span>

<span data-ttu-id="2b184-125">CLR etkinleştirme günlükleri, CLR etkinleştirme ve CLR barındırma API'lerinin kullanımı hakkında büyük miktarda veri sağlar.</span><span class="sxs-lookup"><span data-stu-id="2b184-125">CLR activation logs provide a large amount of data about CLR activation and the use of the CLR hosting APIs.</span></span> <span data-ttu-id="2b184-126">Bu verilerin çoğu Microsoft tarafından dahili olarak kullanılır, ancak bu makalede açıklandığı gibi bazı veriler geliştiriciler için de yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="2b184-126">Most of this data is used internally by Microsoft, but some of the data can also be useful to developers, as described in this article.</span></span>

<span data-ttu-id="2b184-127">Günlük, API barındırma CLR çağrıldığı sırasını yansıtır.</span><span class="sxs-lookup"><span data-stu-id="2b184-127">The log reflects the order in which the CLR hosting APIs were called.</span></span> <span data-ttu-id="2b184-128">Ayrıca, bilgisayarda algılanan yüklü çalışma süreleri kümesi hakkında yararlı veriler de içerir.</span><span class="sxs-lookup"><span data-stu-id="2b184-128">It also includes useful data about the set of installed runtimes detected on the computer.</span></span> <span data-ttu-id="2b184-129">CLR etkinleştirme günlüğü biçimi kendisi belgelenmiş değildir, ancak CLR etkinleştirme sorunlarını çözmesi gereken geliştiricilere yardımcı olmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2b184-129">The CLR activation log format is not itself documented, but can be used to aid developers who need to resolve CLR activation issues.</span></span>

> [!NOTE]
> <span data-ttu-id="2b184-130">CLR kullanan işlem sonlandırılmadan bir etkinleştirme günlüğü açamazsınız.</span><span class="sxs-lookup"><span data-stu-id="2b184-130">You cannot open an activation log until the process that uses the CLR has terminated.</span></span>

> [!NOTE]
> <span data-ttu-id="2b184-131">CLR etkinleştirme günlükleri yerelleştirilmiş değil; her zaman İngilizce üretilir.</span><span class="sxs-lookup"><span data-stu-id="2b184-131">CLR activation logs are not localized; they are always generated in the English language.</span></span>

<span data-ttu-id="2b184-132">Etkinleştirme günlüğünün aşağıdaki örneğinde, en yararlı bilgiler vurgulanır ve günlükten sonra açıklanır.</span><span class="sxs-lookup"><span data-stu-id="2b184-132">In the following example of an activation log, the most useful information is highlighted and described after the log.</span></span>

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

- <span data-ttu-id="2b184-133">**CLR Yükleme günlüğü,** yönetilen kodu yükleyen işlemi başlatan yürütülebilir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="2b184-133">**CLR Loading log** provides the path to the executable that started the process that loaded managed code.</span></span> <span data-ttu-id="2b184-134">Bunun yerel bir ana bilgisayar olabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2b184-134">Note that this could be a native host.</span></span>

    ```output
    532,205950.367,CLR Loading log for C:\Tests\myapp.exe
    ```

- <span data-ttu-id="2b184-135">**Yüklü Runtime,** etkinleştirme isteği için aday olan bilgisayarda yüklü CLR sürümleri kümesidir.</span><span class="sxs-lookup"><span data-stu-id="2b184-135">**Installed Runtime** is the set of CLR versions installed on the computer that are candidates for the activation request.</span></span>

    ```output
    532,205950.382,Installed Runtime: v4.0.30319. VERSION_ARCHITECTURE: 0
    ```

- <span data-ttu-id="2b184-136">**sürümü ile inşa** ICLRMetaHostPolicy gibi bir yöntem için sağlanan ikili oluşturmak için kullanılan [CLR sürümü::GetRequestedRuntime](../unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="2b184-136">**built with version** is the version of the CLR that was used to build the binary that was provided to a method such as [ICLRMetaHostPolicy::GetRequestedRuntime](../unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md).</span></span>

    ```output
    532,205950.382,C:\Tests\myapp.exe was built with version: v2.0.50727
    ```

- <span data-ttu-id="2b184-137">**isteğe bağlı özellik yüklemesi,** Windows 8'de .NET Framework 3.5'i etkinleştirmek anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="2b184-137">**feature-on-demand installation** refers to enabling the .NET Framework 3.5 on Windows 8.</span></span> <span data-ttu-id="2b184-138">Bkz. [.NET Framework Initialization Errors:](initialization-errors-managing-the-user-experience.md) Bu senaryo hakkında daha fazla bilgi için Kullanıcı Deneyimini Yönetme.</span><span class="sxs-lookup"><span data-stu-id="2b184-138">See [.NET Framework Initialization Errors: Managing the User Experience](initialization-errors-managing-the-user-experience.md) for more information about this scenario.</span></span>

    ```output
    532,205950.398,Launching feature-on-demand installation. CmdLine: C:\Windows\system32\fondue.exe /enable-feature:NetFx3
    ```

## <a name="see-also"></a><span data-ttu-id="2b184-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b184-139">See also</span></span>

- [<span data-ttu-id="2b184-140">Dağıtım</span><span class="sxs-lookup"><span data-stu-id="2b184-140">Deployment</span></span>](index.md)
- [<span data-ttu-id="2b184-141">Nasıl yapilir: Bir uygulamayı .NET Framework 4 veya sonraki sürümlerini destekleyecek şekilde yapılandırın</span><span class="sxs-lookup"><span data-stu-id="2b184-141">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
