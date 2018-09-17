---
title: Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama
ms.date: 08/14/2018
f1_keywords:
- EHMDA
helpviewer_keywords:
- run-time error debugging
- managed code, run-time debugging
- resource debugging
- registry, MDAs
- common language runtime, debugging
- MDAs (managed debugging assistants)
- configuration files [.NET Framework], debugging runtime events
- messages, managed debugging assistants
- application configuration files, managed debugging assistants
- debugging [.NET Framework], managed debugging assistants
- environment variables, MDAs
- access violation debugging [.NET Framework]
- diagnostics, managed debugging assistants
- unmanaged code, run-time debugging
- default debug output stream
- memory, debugging
- app.config files, managed debugging assistants
- managed debugging assistants (MDAs)
- debugging [.NET Framework], run-time errors
- trapping events
- runtime, error debugging
- disabling MDAs
- output, managed debugging assistants
- errors [.NET Framework], managed debugging assistants
ms.assetid: 76994ee6-9fa9-4059-b813-26578d24427c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b745fa6a78ab2a7ab0b3a94c9921883d3c56c1b7
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45750290"
---
# <a name="diagnose-errors-with-managed-debugging-assistants"></a><span data-ttu-id="e577d-102">Yönetilen hata ayıklama Yardımcıları ile hataları tanılama</span><span class="sxs-lookup"><span data-stu-id="e577d-102">Diagnose Errors with Managed Debugging Assistants</span></span>

<span data-ttu-id="e577d-103">Yönetilen hata ayıklama yardımcıları (MDAs), çalışma zamanı durum bilgilerini sağlamak için ortak dil çalışma zamanı (CLR) ile birlikte çalışan yardımlarda hata ayıklar.</span><span class="sxs-lookup"><span data-stu-id="e577d-103">Managed debugging assistants (MDAs) are debugging aids that work in conjunction with the common language runtime (CLR) to provide information on runtime state.</span></span> <span data-ttu-id="e577d-104">Yardımcılar, aksi takdirde yakalayamayacağınız çalışma zamanı olayları hakkında bilgi iletileri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e577d-104">The assistants generate informational messages about runtime events that you cannot otherwise trap.</span></span> <span data-ttu-id="e577d-105">Yönetilen ve yönetilmeyen kod arasında geçiş yaparken ortaya çıkan bulması zor uygulama hatalarını yalıtmak için MDA'leri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e577d-105">You can use MDAs to isolate hard-to-find application bugs that occur when transitioning between managed and unmanaged code.</span></span>

<span data-ttu-id="e577d-106">Yapabilecekleriniz [etkinleştirmek veya devre dışı](#enable-and-disable-mdas) tüm Mda'leri Windows kayıt defterine bir anahtar ekleyerek veya bir ortam değişkenini ayarlayarak.</span><span class="sxs-lookup"><span data-stu-id="e577d-106">You can [enable or disable](#enable-and-disable-mdas) all MDAs by adding a key to the Windows registry or by setting an environment variable.</span></span> <span data-ttu-id="e577d-107">Uygulama yapılandırma ayarlarını kullanarak belirli MDA'leri etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e577d-107">You can enable specific MDAs by using application configuration settings.</span></span> <span data-ttu-id="e577d-108">Uygulamanın yapılandırma dosyasındaki bazı tek MDA'ler için ek yapılandırma ayarları ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e577d-108">You can set additional configuration settings for some individual MDAs in the application's configuration file.</span></span> <span data-ttu-id="e577d-109">Çalışma zamanı yüklendiğinde bu yapılandırma dosyaları ayrıştırıldığı için yönetilen uygulama başlamadan önce MDA'i etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e577d-109">Because these configuration files are parsed when the runtime is loaded, you must enable the MDA before the managed application starts.</span></span> <span data-ttu-id="e577d-110">Zaten başlatılmış uygulamalar için MDA'i etkinleştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="e577d-110">You cannot enable it for applications that have already started.</span></span>

<span data-ttu-id="e577d-111">Aşağıdaki tablo, .NET Framework ile birlikte gelen Mda'leri listeler:</span><span class="sxs-lookup"><span data-stu-id="e577d-111">The following table lists the MDAs that ship with the .NET Framework:</span></span>

|||
|-|-|
|[<span data-ttu-id="e577d-112">asynchronousThreadAbort</span><span class="sxs-lookup"><span data-stu-id="e577d-112">asynchronousThreadAbort</span></span>](../../../docs/framework/debug-trace-profile/asynchronousthreadabort-mda.md)|[<span data-ttu-id="e577d-113">bindingFailure</span><span class="sxs-lookup"><span data-stu-id="e577d-113">bindingFailure</span></span>](../../../docs/framework/debug-trace-profile/bindingfailure-mda.md)|
|[<span data-ttu-id="e577d-114">callbackOnCollectedDelegate</span><span class="sxs-lookup"><span data-stu-id="e577d-114">callbackOnCollectedDelegate</span></span>](../../../docs/framework/debug-trace-profile/callbackoncollecteddelegate-mda.md)|[<span data-ttu-id="e577d-115">contextSwitchDeadlock</span><span class="sxs-lookup"><span data-stu-id="e577d-115">contextSwitchDeadlock</span></span>](../../../docs/framework/debug-trace-profile/contextswitchdeadlock-mda.md)|
|[<span data-ttu-id="e577d-116">dangerousThreadingAPI</span><span class="sxs-lookup"><span data-stu-id="e577d-116">dangerousThreadingAPI</span></span>](../../../docs/framework/debug-trace-profile/dangerousthreadingapi-mda.md)|[<span data-ttu-id="e577d-117">dateTimeInvalidLocalFormat</span><span class="sxs-lookup"><span data-stu-id="e577d-117">dateTimeInvalidLocalFormat</span></span>](../../../docs/framework/debug-trace-profile/datetimeinvalidlocalformat-mda.md)|
|[<span data-ttu-id="e577d-118">dirtyCastAndCallOnInterface</span><span class="sxs-lookup"><span data-stu-id="e577d-118">dirtyCastAndCallOnInterface</span></span>](../../../docs/framework/debug-trace-profile/dirtycastandcalloninterface-mda.md)|[<span data-ttu-id="e577d-119">disconnectedContext</span><span class="sxs-lookup"><span data-stu-id="e577d-119">disconnectedContext</span></span>](../../../docs/framework/debug-trace-profile/disconnectedcontext-mda.md)|
|[<span data-ttu-id="e577d-120">dllMainReturnsFalse</span><span class="sxs-lookup"><span data-stu-id="e577d-120">dllMainReturnsFalse</span></span>](../../../docs/framework/debug-trace-profile/dllmainreturnsfalse-mda.md)|[<span data-ttu-id="e577d-121">exceptionSwallowedOnCallFromCom</span><span class="sxs-lookup"><span data-stu-id="e577d-121">exceptionSwallowedOnCallFromCom</span></span>](../../../docs/framework/debug-trace-profile/exceptionswallowedoncallfromcom-mda.md)|
|[<span data-ttu-id="e577d-122">failedQI</span><span class="sxs-lookup"><span data-stu-id="e577d-122">failedQI</span></span>](../../../docs/framework/debug-trace-profile/failedqi-mda.md)|[<span data-ttu-id="e577d-123">fatalExecutionEngineError</span><span class="sxs-lookup"><span data-stu-id="e577d-123">fatalExecutionEngineError</span></span>](../../../docs/framework/debug-trace-profile/fatalexecutionengineerror-mda.md)|
|[<span data-ttu-id="e577d-124">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="e577d-124">gcManagedToUnmanaged</span></span>](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)|[<span data-ttu-id="e577d-125">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="e577d-125">gcUnmanagedToManaged</span></span>](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)|
|[<span data-ttu-id="e577d-126">illegalPrepareConstrainedRegion</span><span class="sxs-lookup"><span data-stu-id="e577d-126">illegalPrepareConstrainedRegion</span></span>](../../../docs/framework/debug-trace-profile/illegalprepareconstrainedregion-mda.md)|[<span data-ttu-id="e577d-127">invalidApartmentStateChange</span><span class="sxs-lookup"><span data-stu-id="e577d-127">invalidApartmentStateChange</span></span>](../../../docs/framework/debug-trace-profile/invalidapartmentstatechange-mda.md)|
|[<span data-ttu-id="e577d-128">invalidCERCall</span><span class="sxs-lookup"><span data-stu-id="e577d-128">invalidCERCall</span></span>](../../../docs/framework/debug-trace-profile/invalidcercall-mda.md)|[<span data-ttu-id="e577d-129">invalidFunctionPointerInDelegate</span><span class="sxs-lookup"><span data-stu-id="e577d-129">invalidFunctionPointerInDelegate</span></span>](../../../docs/framework/debug-trace-profile/invalidfunctionpointerindelegate-mda.md)|
|[<span data-ttu-id="e577d-130">invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="e577d-130">invalidGCHandleCookie</span></span>](../../../docs/framework/debug-trace-profile/invalidgchandlecookie-mda.md)|[<span data-ttu-id="e577d-131">invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="e577d-131">invalidIUnknown</span></span>](../../../docs/framework/debug-trace-profile/invalidiunknown-mda.md)|
|[<span data-ttu-id="e577d-132">invalidMemberDeclaration</span><span class="sxs-lookup"><span data-stu-id="e577d-132">invalidMemberDeclaration</span></span>](../../../docs/framework/debug-trace-profile/invalidmemberdeclaration-mda.md)|[<span data-ttu-id="e577d-133">invalidOverlappedToPinvoke</span><span class="sxs-lookup"><span data-stu-id="e577d-133">invalidOverlappedToPinvoke</span></span>](../../../docs/framework/debug-trace-profile/invalidoverlappedtopinvoke-mda.md)|
|[<span data-ttu-id="e577d-134">invalidVariant</span><span class="sxs-lookup"><span data-stu-id="e577d-134">invalidVariant</span></span>](../../../docs/framework/debug-trace-profile/invalidvariant-mda.md)|[<span data-ttu-id="e577d-135">jitCompilationStart</span><span class="sxs-lookup"><span data-stu-id="e577d-135">jitCompilationStart</span></span>](../../../docs/framework/debug-trace-profile/jitcompilationstart-mda.md)|
|[<span data-ttu-id="e577d-136">loaderLock</span><span class="sxs-lookup"><span data-stu-id="e577d-136">loaderLock</span></span>](../../../docs/framework/debug-trace-profile/loaderlock-mda.md)|[<span data-ttu-id="e577d-137">loadFromContext</span><span class="sxs-lookup"><span data-stu-id="e577d-137">loadFromContext</span></span>](../../../docs/framework/debug-trace-profile/loadfromcontext-mda.md)|
|[<span data-ttu-id="e577d-138">marshalCleanupError</span><span class="sxs-lookup"><span data-stu-id="e577d-138">marshalCleanupError</span></span>](../../../docs/framework/debug-trace-profile/marshalcleanuperror-mda.md)|[<span data-ttu-id="e577d-139">marshaling</span><span class="sxs-lookup"><span data-stu-id="e577d-139">marshaling</span></span>](../../../docs/framework/debug-trace-profile/marshaling-mda.md)|
|[<span data-ttu-id="e577d-140">memberInfoCacheCreation</span><span class="sxs-lookup"><span data-stu-id="e577d-140">memberInfoCacheCreation</span></span>](../../../docs/framework/debug-trace-profile/memberinfocachecreation-mda.md)|[<span data-ttu-id="e577d-141">moduloObjectHashcode</span><span class="sxs-lookup"><span data-stu-id="e577d-141">moduloObjectHashcode</span></span>](../../../docs/framework/debug-trace-profile/moduloobjecthashcode-mda.md)|
|[<span data-ttu-id="e577d-142">nonComVisibleBaseClass</span><span class="sxs-lookup"><span data-stu-id="e577d-142">nonComVisibleBaseClass</span></span>](../../../docs/framework/debug-trace-profile/noncomvisiblebaseclass-mda.md)|[<span data-ttu-id="e577d-143">notMarshalable</span><span class="sxs-lookup"><span data-stu-id="e577d-143">notMarshalable</span></span>](../../../docs/framework/debug-trace-profile/notmarshalable-mda.md)|
|[<span data-ttu-id="e577d-144">openGenericCERCall</span><span class="sxs-lookup"><span data-stu-id="e577d-144">openGenericCERCall</span></span>](../../../docs/framework/debug-trace-profile/opengenericcercall-mda.md)|[<span data-ttu-id="e577d-145">overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="e577d-145">overlappedFreeError</span></span>](../../../docs/framework/debug-trace-profile/overlappedfreeerror-mda.md)|
|[<span data-ttu-id="e577d-146">pInvokeLog</span><span class="sxs-lookup"><span data-stu-id="e577d-146">pInvokeLog</span></span>](../../../docs/framework/debug-trace-profile/pinvokelog-mda.md)|[<span data-ttu-id="e577d-147">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="e577d-147">pInvokeStackImbalance</span></span>](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)|
|[<span data-ttu-id="e577d-148">raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="e577d-148">raceOnRCWCleanup</span></span>](../../../docs/framework/debug-trace-profile/raceonrcwcleanup-mda.md)|[<span data-ttu-id="e577d-149">reentrancy</span><span class="sxs-lookup"><span data-stu-id="e577d-149">reentrancy</span></span>](../../../docs/framework/debug-trace-profile/reentrancy-mda.md)|
|[<span data-ttu-id="e577d-150">releaseHandleFailed</span><span class="sxs-lookup"><span data-stu-id="e577d-150">releaseHandleFailed</span></span>](../../../docs/framework/debug-trace-profile/releasehandlefailed-mda.md)|[<span data-ttu-id="e577d-151">reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="e577d-151">reportAvOnComRelease</span></span>](../../../docs/framework/debug-trace-profile/reportavoncomrelease-mda.md)|
|[<span data-ttu-id="e577d-152">streamWriterBufferedDataLost</span><span class="sxs-lookup"><span data-stu-id="e577d-152">streamWriterBufferedDataLost</span></span>](../../../docs/framework/debug-trace-profile/streamwriterbuffereddatalost-mda.md)|[<span data-ttu-id="e577d-153">virtualCERCall</span><span class="sxs-lookup"><span data-stu-id="e577d-153">virtualCERCall</span></span>](../../../docs/framework/debug-trace-profile/virtualcercall-mda.md)|

<span data-ttu-id="e577d-154">Varsayılan olarak, .NET Framework yönetilen tüm hata ayıklayıcıları için bir MDA alt kümesini etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="e577d-154">By default, the .NET Framework activates a subset of MDAs for all managed debuggers.</span></span> <span data-ttu-id="e577d-155">Visual Studio'da seçerek varsayılan görüntüleyebileceğiniz **Windows** > **özel durum ayarları** üzerinde **hata ayıklama** menüsüne ve ardından genişletme**Yönetilen hata ayıklama Yardımcıları** listesi.</span><span class="sxs-lookup"><span data-stu-id="e577d-155">You can view the default set in Visual Studio by choosing **Windows** > **Exception Settings** on the **Debug** menu, and then expanding the **Managed Debugging Assistants** list.</span></span>

![Visual Studio'da özel durum Ayarları penceresi](media/diagnosing-errors-with-managed-debugging-assistants/exception-settings-mdas.png)

## <a name="enable-and-disable-mdas"></a><span data-ttu-id="e577d-157">Etkinleştirme ve Mda'leri devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="e577d-157">Enable and Disable MDAs</span></span>

<span data-ttu-id="e577d-158">Bir kayıt defteri anahtarını, bir ortam değişkenini ve uygulama yapılandırma ayarlarını kullanarak MDA'leri etkinleştirebilir ve devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e577d-158">You can enable and disable MDAs by using a registry key, an environment variable, and application configuration settings.</span></span> <span data-ttu-id="e577d-159">Uygulama yapılandırma ayarlarını kullanmak için kayıt defteri anahtarını veya ortam değişkenini etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e577d-159">You must enable either the registry key or the environment variable to use the application configuration settings.</span></span>

> [!TIP]
> <span data-ttu-id="e577d-160">Mda'leri devre dışı bırakmak yerine Visual Studio bir MDA bildirimi alındığında MDA iletişim kutusunu görüntülemesini engelleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e577d-160">Instead of disabling MDAs, you can prevent Visual Studio from displaying the MDA dialog box whenever an MDA notification is received.</span></span> <span data-ttu-id="e577d-161">Bunu yapmak için seçin **Windows** > **özel durum ayarları** üzerinde **hata ayıklama** menüsünü genişletin **yönetilen hata ayıklama Yardımcıları**listesini ve ardından seçin veya temizleyin **Break When Thrown** tek mda'e onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="e577d-161">To do that, choose **Windows** > **Exception Settings** on the **Debug** menu, expand the **Managed Debugging Assistants** list, and then select or clear the **Break When Thrown** check box for the individual MDA.</span></span>

### <a name="registry-key"></a><span data-ttu-id="e577d-162">Kayıt Defteri Anahtarı</span><span class="sxs-lookup"><span data-stu-id="e577d-162">Registry Key</span></span>

<span data-ttu-id="e577d-163">Mda'leri etkinleştirmek için eklemeniz **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework\MDA** Windows kayıt defteri alt anahtarında (tür REG_SZ, değer 1).</span><span class="sxs-lookup"><span data-stu-id="e577d-163">To enable MDAs, add the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\MDA** subkey (type REG_SZ, value 1) in the Windows registry.</span></span> <span data-ttu-id="e577d-164">Aşağıdaki örnekte adlı bir metin dosyasına kopyalama *MDAEnable.reg*. Windows Kayıt Defteri Düzenleyicisi'ni (RegEdit.exe) açın ve **dosya** menüsünde **alma**.</span><span class="sxs-lookup"><span data-stu-id="e577d-164">Copy the following example into a text file named *MDAEnable.reg*. Open the Windows Registry Editor (RegEdit.exe), and from the **File** menu choose **Import**.</span></span> <span data-ttu-id="e577d-165">Seçin *MDAEnable.reg* o bilgisayardaki Mda'leri etkinleştirmek için dosya.</span><span class="sxs-lookup"><span data-stu-id="e577d-165">Select the *MDAEnable.reg* file to enable MDAs on that computer.</span></span> <span data-ttu-id="e577d-166">Alt dize değeri olarak ayarlama **1** (DWORD değerini değil **1**) MDA ayarlarının okunmasını etkinleştirir *ApplicationName.suffix*. mda.config dosyasından.</span><span class="sxs-lookup"><span data-stu-id="e577d-166">Setting the subkey to string value of **1** (not DWORD value of **1**) enables the reading of MDA settings from the *ApplicationName.suffix*.mda.config file.</span></span> <span data-ttu-id="e577d-167">Örneğin, Not Defteri ait MDA yapılandırma dosyası, notepad.exe.mda.config sayfadayken.</span><span class="sxs-lookup"><span data-stu-id="e577d-167">For example, the MDA configuration file for Notepad would be named notepad.exe.mda.config.</span></span>

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework]
"MDA"="1"
```

<span data-ttu-id="e577d-168">Ardından MDA anahtarı, bilgisayar, 64-bit işletim sisteminde 32 bit uygulama çalışıyorsa, aşağıdaki gibi ayarlanmalıdır:</span><span class="sxs-lookup"><span data-stu-id="e577d-168">If the computer is running a 32-bit application on a 64-bit operating system, then the MDA key should be set like the following:</span></span>

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework]
"MDA"="1"
```

<span data-ttu-id="e577d-169">Bkz: [uygulamaya özgü yapılandırma ayarlarını](#application-specific-configuration-settings) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="e577d-169">See [Application-Specific Configuration Settings](#application-specific-configuration-settings) for more information.</span></span> <span data-ttu-id="e577d-170">Kayıt defteri ayarı, COMPLUS_MDA ortam değişkeni tarafından geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="e577d-170">The registry setting can be overridden by the COMPLUS_MDA environment variable.</span></span> <span data-ttu-id="e577d-171">Bkz: [ortam değişkeni](#environment-variable) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="e577d-171">See [Environment Variable](#environment-variable) for more information.</span></span>

<span data-ttu-id="e577d-172">Mda'leri devre dışı bırakmak için MDA alt anahtarını ayarlamak **0** (Windows Kayıt Defteri Düzenleyicisi'ni kullanarak sıfır).</span><span class="sxs-lookup"><span data-stu-id="e577d-172">To disable MDAs, set the MDA subkey to **0** (zero) using the Windows Registry Editor.</span></span>

<span data-ttu-id="e577d-173">Bir hata ayıklayıcıya bağlı bir uygulamayı çalıştırdığınızda kayıt defteri anahtarı bile eklemeden bazı MDA'ler varsayılan olarak etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e577d-173">By default, some MDAs are enabled when you run an application that is attached to a debugger, even without adding the registry key.</span></span> <span data-ttu-id="e577d-174">Çalıştırarak bu Yardımcıları devre dışı bırakabilirsiniz *MDADisable.reg* dosya bu bölümde daha önce açıklandığı gibi.</span><span class="sxs-lookup"><span data-stu-id="e577d-174">You can disable these assistants by running the *MDADisable.reg* file as described earlier in this section.</span></span>

### <a name="environment-variable"></a><span data-ttu-id="e577d-175">Ortam değişkeni</span><span class="sxs-lookup"><span data-stu-id="e577d-175">Environment Variable</span></span>

<span data-ttu-id="e577d-176">MDA etkinleştirmesi aynı zamanda, kayıt defteri anahtarını geçersiz kılan COMPLUS_MDA ortam değişkeni tarafından da kontrol edilebilir.</span><span class="sxs-lookup"><span data-stu-id="e577d-176">MDA activation can also controlled by the environment variable COMPLUS_MDA, which overrides the registry key.</span></span> <span data-ttu-id="e577d-177">COMPLUS_MDA dizesi, MDA adlarının veya başka özel denetim dizelerinin büyük/küçük harf duyarlı, noktalı virgülle ayrılmış listesidir.</span><span class="sxs-lookup"><span data-stu-id="e577d-177">The COMPLUS_MDA string is a case-insensitive, semicolon-delimited list of MDA names or other special control strings.</span></span> <span data-ttu-id="e577d-178">Yönetilen veya yönetilmeyen hata ayıklayıcı altında başlamak varsayılan olarak bir MDA kümesini etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="e577d-178">Starting under a managed or unmanaged debugger enables a set of MDAs by default.</span></span> <span data-ttu-id="e577d-179">Bu, varsayılan olarak hata ayıklayıcılarda etkinleştirilen, noktalı virgülle ayrılmış MDA listesini ortam değişkeninin veya kayıt defteri anahtarının değerine açıkça ekleyerek yapılır.</span><span class="sxs-lookup"><span data-stu-id="e577d-179">This is done by implicitly prepending the semicolon-delimited list of MDAs enabled by default under debuggers to the value of the environment variable or registry key.</span></span> <span data-ttu-id="e577d-180">Özel denetim dizeleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e577d-180">The special control strings are the following:</span></span>

- <span data-ttu-id="e577d-181">`0` - Tüm MDA'leri devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="e577d-181">`0` - Deactivates all MDAs.</span></span>

- <span data-ttu-id="e577d-182">`1` -MDA ayarlarını okur *ApplicationName*. mda.config.</span><span class="sxs-lookup"><span data-stu-id="e577d-182">`1` - Reads MDA settings from *ApplicationName*.mda.config.</span></span>

- <span data-ttu-id="e577d-183">`managedDebugger` - Yönetilen bir yürütülebilir dosya hata ayıklayıcı altında başlatıldığında dolaylı olarak etkinleştirilmiş tüm MDA'leri açıkça etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="e577d-183">`managedDebugger` - Explicitly activates all MDAs that are implicitly activated when a managed executable is started under a debugger.</span></span>

- <span data-ttu-id="e577d-184">`unmanagedDebugger` - Yönetilmeyen bir yürütülebilir dosya hata ayıklayıcı altında başlatıldığında dolaylı olarak etkinleştirilmiş tüm MDA'leri açıkça etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="e577d-184">`unmanagedDebugger` - Explicitly activates all MDAs that are implicitly activated when an unmanaged executable is started under a debugger.</span></span>

<span data-ttu-id="e577d-185">Çakışan ayarlar varsa, en son ayarlar önceki ayarları geçersiz kılar:</span><span class="sxs-lookup"><span data-stu-id="e577d-185">If there are conflicting settings, the most recent settings override previous settings:</span></span>

- <span data-ttu-id="e577d-186">`COMPLUS_MDA=0`, dolaylı olarak bir hata ayıklayıcıda etkinleştirilmiş olanlar dahil olmak üzere tüm MDA'leri devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="e577d-186">`COMPLUS_MDA=0` disables all MDAs, including those implicitly enabled under a debugger.</span></span>

- <span data-ttu-id="e577d-187">`COMPLUS_MDA=gcUnmanagedToManaged`, bir hata ayıklayıcıda dolaylı olarak etkinleştirilen MDA'lere ek olarak `gcUnmanagedToManaged` öğesini etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="e577d-187">`COMPLUS_MDA=gcUnmanagedToManaged` enables `gcUnmanagedToManaged` in addition to any MDAs that are implicitly enabled under a debugger.</span></span>

- <span data-ttu-id="e577d-188">`COMPLUS_MDA=0;gcUnmanagedToManaged`, `gcUnmanagedToManaged` öğesini etkinleştirir, ancak aksi takdirde dolaylı olarak bir hata ayıklayıcıda etkinleştirilecek olan MDA'leri devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="e577d-188">`COMPLUS_MDA=0;gcUnmanagedToManaged` enables `gcUnmanagedToManaged` but disables MDAs that would otherwise be implicitly enabled under a debugger.</span></span>

### <a name="application-specific-configuration-settings"></a><span data-ttu-id="e577d-189">Uygulamaya özgü yapılandırma ayarları</span><span class="sxs-lookup"><span data-stu-id="e577d-189">Application-Specific Configuration Settings</span></span>

<span data-ttu-id="e577d-190">Uygulamaya ait MDA yapılandırma dosyası içinde bazı yardımcıları etkinleştirebilir, devre dışı bırakabilir ve ayrı ayrı yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e577d-190">You can enable, disable, and configure some assistants individually in the MDA configuration file for the application.</span></span> <span data-ttu-id="e577d-191">MDA'leri yapılandırmak üzere bir uygulama yapılandırma dosyasının kullanımını etkinleştirmek için MDA kayıt defteri anahtarının veya COMPLUS_MDA ortam değişkeni ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e577d-191">To enable the use of an application configuration file for configuring MDAs, either the MDA registry key or the COMPLUS_MDA environment variable must be set.</span></span> <span data-ttu-id="e577d-192">Uygulama yapılandırma dosyası, genellikle uygulamanın yürütülebilir (.exe) dosyası ile aynı dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="e577d-192">The application configuration file is typically located in the same directory as the application's executable (.exe) file.</span></span> <span data-ttu-id="e577d-193">Dosya adı biçimi alır *ApplicationName*. mda.config biçimini alır; Örneğin, notepad.exe.mda.config. Uygulama yapılandırma dosyasında etkinleştirilen yardımcılar, o yardımcının davranışını denetlemek için özel olarak tasarlanan özniteliklere veya öğelere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="e577d-193">The file name takes the form *ApplicationName*.mda.config; for example, notepad.exe.mda.config. Assistants that are enabled in the application configuration file may have attributes or elements specifically designed to control that assistant's behavior.</span></span>

<span data-ttu-id="e577d-194">Aşağıdaki örnek, etkinleştirme ve yapılandırma gösterilmektedir [hazırlama](../../../docs/framework/debug-trace-profile/marshaling-mda.md):</span><span class="sxs-lookup"><span data-stu-id="e577d-194">The following example shows how to enable and configure the [marshaling](../../../docs/framework/debug-trace-profile/marshaling-mda.md):</span></span>

```xml
<mdaConfig>
  <assistants>
    <marshaling>
      <methodFilter>
        <match name="*"/>
      </methodFilter>
      <fieldFilter>
        <match name="*"/>
      </fieldFilter>
    </marshaling>
  </assistants>
</mdaConfig>
```

<span data-ttu-id="e577d-195">`Marshaling` MDA, uygulamadaki her yönetilenden yönetilmeyene geçiş için bir yönetilmeyen türe sıraya koyulan yönetilen tür hakkında bilgiler verir.</span><span class="sxs-lookup"><span data-stu-id="e577d-195">The `Marshaling` MDA emits information about the managed type that is being marshaled to an unmanaged type for each managed-to-unmanaged transition in the application.</span></span> <span data-ttu-id="e577d-196">`Marshaling` MDA aynı zamanda yöntem adlarını filtrelemek ve yapı alanlarının sağlanan **methodFilter** ve **alan filtresi** alt öğeleri, sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="e577d-196">The `Marshaling` MDA can also filter the names of the method and structure fields supplied in the **methodFilter** and **fieldFilter** child elements, respectively.</span></span>

<span data-ttu-id="e577d-197">Aşağıdaki örnek, varsayılan ayarlarını kullanarak birden çok Mda'in etkinleştirmek gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="e577d-197">The following example shows how to enable multiple MDAs by using their default settings:</span></span>

```xml
<mdaConfig>
  <assistants>
    <illegalPrepareConstrainedRegion />
    <invalidCERCall />
    <openGenericCERCall />
    <virtualCERCall />
  </assistants>
</mdaConfig>
```

> [!IMPORTANT]
> <span data-ttu-id="e577d-198">Bir yapılandırma dosyasında birden fazla yardımcı belirttiğinizde, bunları alfabetik olarak listelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e577d-198">When you specify more than one assistant in a configuration file, you must list them in alphabetical order.</span></span> <span data-ttu-id="e577d-199">Örneğin, `virtualCERCall` ve `invalidCERCall` MDA'lerinin her ikisini de etkinleştirmek istiyorsanız `<invalidCERCall />` girdisinden önce `<virtualCERCall />` girdisini eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e577d-199">For example, if you want to enable both the `virtualCERCall` and the `invalidCERCall` MDAs, you must add the `<invalidCERCall />` entry before the `<virtualCERCall />` entry.</span></span> <span data-ttu-id="e577d-200">Girdiler alfabetik sırada değilse, işlenmemiş bir geçersiz yapılandırma dosyası özel durum iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e577d-200">If the entries are not in alphabetical order, an unhandled invalid configuration file exception message is displayed.</span></span>

## <a name="mda-exceptions"></a><span data-ttu-id="e577d-201">MDA özel durumları</span><span class="sxs-lookup"><span data-stu-id="e577d-201">MDA exceptions</span></span>

<span data-ttu-id="e577d-202">Bir MDA etkinleştirildiğinde, hatta zaman kodunuzu hata ayıklayıcı altında yürütülmüyor olduğunda etkin değil.</span><span class="sxs-lookup"><span data-stu-id="e577d-202">When an MDA is enabled, it's active even when your code is not executing under a debugger.</span></span> <span data-ttu-id="e577d-203">Bir hata ayıklayıcı olmadığında bir MDA olayı oluşturulursa, işlenmemiş özel bir durum olmasa bile olay iletisi, işlenmemiş özel durum iletişim kutusunda sunulur.</span><span class="sxs-lookup"><span data-stu-id="e577d-203">If an MDA event is raised when a debugger is not present, the event message is presented in an unhandled exception dialog box, although it is not an unhandled exception.</span></span> <span data-ttu-id="e577d-204">İletişim kutusunu önlemek için kodunuz hata ayıklama ortamında çalışmıyorken MDA etkinleştirme ayarlarını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="e577d-204">To avoid the dialog box, remove the MDA-enabling settings when your code is not executing in a debugging environment.</span></span>

<span data-ttu-id="e577d-205">Kodunuzu Visual Studio tümleşik geliştirme ortamında (IDE) yürütüldüğünde, belirli MDA olayları için görüntülenen özel durum iletişim kutusunu önleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e577d-205">When your code executes in the Visual Studio integrated development environment (IDE), you can avoid the exception dialog box that appears for specific MDA events.</span></span> <span data-ttu-id="e577d-206">Bunu yapmak için **hata ayıklama** menüsünde seçin **Windows** > **özel durum ayarları**.</span><span class="sxs-lookup"><span data-stu-id="e577d-206">To do that, on the **Debug** menu, choose **Windows** > **Exception Settings**.</span></span> <span data-ttu-id="e577d-207">İçinde **özel durum ayarları** penceresini genişletin **yönetilen hata ayıklama Yardımcıları** listeleyin ve ardından temizleyin **Break When Thrown** tek mda'e onay kutusu.</span><span class="sxs-lookup"><span data-stu-id="e577d-207">In the **Exception Settings** window, expand the **Managed Debugging Assistants** list, and then clear the **Break When Thrown** check box for the individual MDA.</span></span> <span data-ttu-id="e577d-208">Bu iletişim kutusu için de kullanabilirsiniz *etkinleştirme* MDA özel iletişim kutularının görüntülenmesini.</span><span class="sxs-lookup"><span data-stu-id="e577d-208">You can also use this dialog box to *enable* the display of MDA exception dialog boxes.</span></span>

## <a name="mda-output"></a><span data-ttu-id="e577d-209">MDA Çıktısı</span><span class="sxs-lookup"><span data-stu-id="e577d-209">MDA Output</span></span>

<span data-ttu-id="e577d-210">MDA çıktısı çıktısını gösteren aşağıdaki örneğe benzer `PInvokeStackImbalance` MDA:</span><span class="sxs-lookup"><span data-stu-id="e577d-210">MDA output is similar to the following example, which shows the output from the `PInvokeStackImbalance` MDA:</span></span>

<span data-ttu-id="e577d-211">**PInvoke işlevi çağrısı ' MDATest! MDATest.Program::StdCall' yığın dengesiz. Yönetilen PInvoke imza yönetilmeyen hedef imza eşleşmediği için büyük olasılıkla budur. Çağırma kuralı ve parametreleri PInvoke imza hedef yönetilmeyen imza eşleştiğinden emin olun.**</span><span class="sxs-lookup"><span data-stu-id="e577d-211">**A call to PInvoke function 'MDATest!MDATest.Program::StdCall' has unbalanced the stack. This is likely because the managed PInvoke signature does not match the unmanaged target signature. Check that the calling convention and parameters of the PInvoke signature match the target unmanaged signature.**</span></span>

## <a name="see-also"></a><span data-ttu-id="e577d-212">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e577d-212">See also</span></span>

- [<span data-ttu-id="e577d-213">Hata Ayıklama, İzleme ve Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e577d-213">Debugging, Tracing, and Profiling</span></span>](../../../docs/framework/debug-trace-profile/index.md)
