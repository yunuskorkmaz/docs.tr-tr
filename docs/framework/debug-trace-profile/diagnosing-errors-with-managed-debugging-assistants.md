---
title: Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama
description: Yönetilen hata ayıklama yardımcıları ile .NET 'teki hataları tanılayın. Mdalar, çalışma zamanı durum bilgilerini sağlamak için CLR ile birlikte çalışan hata ayıklama yardımlardır.
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
ms.openlocfilehash: ac6fdc09fb057cc55659ce076d37ab96fe2354d1
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416102"
---
# <a name="diagnose-errors-with-managed-debugging-assistants"></a><span data-ttu-id="46e38-104">Yönetilen hata ayıklama yardımcıları ile hataları tanılama</span><span class="sxs-lookup"><span data-stu-id="46e38-104">Diagnose Errors with Managed Debugging Assistants</span></span>

<span data-ttu-id="46e38-105">Yönetilen hata ayıklama yardımcıları (MDAs), çalışma zamanı durum bilgilerini sağlamak için ortak dil çalışma zamanı (CLR) ile birlikte çalışan yardımlarda hata ayıklar.</span><span class="sxs-lookup"><span data-stu-id="46e38-105">Managed debugging assistants (MDAs) are debugging aids that work in conjunction with the common language runtime (CLR) to provide information on runtime state.</span></span> <span data-ttu-id="46e38-106">Yardımcılar, aksi takdirde yakalayamayacağınız çalışma zamanı olayları hakkında bilgi iletileri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="46e38-106">The assistants generate informational messages about runtime events that you cannot otherwise trap.</span></span> <span data-ttu-id="46e38-107">Yönetilen ve yönetilmeyen kod arasında geçiş yaparken ortaya çıkan bulması zor uygulama hatalarını yalıtmak için MDA'leri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46e38-107">You can use MDAs to isolate hard-to-find application bugs that occur when transitioning between managed and unmanaged code.</span></span>

<span data-ttu-id="46e38-108">Windows kayıt defterine bir anahtar ekleyerek veya bir ortam değişkenini ayarlayarak tüm Mdaları [etkinleştirebilir veya devre dışı](#enable-and-disable-mdas) bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46e38-108">You can [enable or disable](#enable-and-disable-mdas) all MDAs by adding a key to the Windows registry or by setting an environment variable.</span></span> <span data-ttu-id="46e38-109">Uygulama yapılandırma ayarlarını kullanarak belirli MDA'leri etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46e38-109">You can enable specific MDAs by using application configuration settings.</span></span> <span data-ttu-id="46e38-110">Uygulamanın yapılandırma dosyasındaki bazı tek MDA'ler için ek yapılandırma ayarları ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46e38-110">You can set additional configuration settings for some individual MDAs in the application's configuration file.</span></span> <span data-ttu-id="46e38-111">Çalışma zamanı yüklendiğinde bu yapılandırma dosyaları ayrıştırıldığı için yönetilen uygulama başlamadan önce MDA'i etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="46e38-111">Because these configuration files are parsed when the runtime is loaded, you must enable the MDA before the managed application starts.</span></span> <span data-ttu-id="46e38-112">Zaten başlatılmış uygulamalar için MDA'i etkinleştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="46e38-112">You cannot enable it for applications that have already started.</span></span>

<span data-ttu-id="46e38-113">Aşağıdaki tabloda .NET Framework ile birlikte gelen Mdalar listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="46e38-113">The following table lists the MDAs that ship with the .NET Framework:</span></span>

|||
|-|-|
|[<span data-ttu-id="46e38-114">asynchronousThreadAbort</span><span class="sxs-lookup"><span data-stu-id="46e38-114">asynchronousThreadAbort</span></span>](asynchronousthreadabort-mda.md)|[<span data-ttu-id="46e38-115">bindingFailure</span><span class="sxs-lookup"><span data-stu-id="46e38-115">bindingFailure</span></span>](bindingfailure-mda.md)|
|[<span data-ttu-id="46e38-116">callbackOnCollectedDelegate</span><span class="sxs-lookup"><span data-stu-id="46e38-116">callbackOnCollectedDelegate</span></span>](callbackoncollecteddelegate-mda.md)|[<span data-ttu-id="46e38-117">contextSwitchDeadlock</span><span class="sxs-lookup"><span data-stu-id="46e38-117">contextSwitchDeadlock</span></span>](contextswitchdeadlock-mda.md)|
|[<span data-ttu-id="46e38-118">dangerousThreadingAPI</span><span class="sxs-lookup"><span data-stu-id="46e38-118">dangerousThreadingAPI</span></span>](dangerousthreadingapi-mda.md)|[<span data-ttu-id="46e38-119">dateTimeInvalidLocalFormat</span><span class="sxs-lookup"><span data-stu-id="46e38-119">dateTimeInvalidLocalFormat</span></span>](datetimeinvalidlocalformat-mda.md)|
|[<span data-ttu-id="46e38-120">dirtyCastAndCallOnInterface</span><span class="sxs-lookup"><span data-stu-id="46e38-120">dirtyCastAndCallOnInterface</span></span>](dirtycastandcalloninterface-mda.md)|[<span data-ttu-id="46e38-121">disconnectedContext</span><span class="sxs-lookup"><span data-stu-id="46e38-121">disconnectedContext</span></span>](disconnectedcontext-mda.md)|
|[<span data-ttu-id="46e38-122">dllMainReturnsFalse</span><span class="sxs-lookup"><span data-stu-id="46e38-122">dllMainReturnsFalse</span></span>](dllmainreturnsfalse-mda.md)|[<span data-ttu-id="46e38-123">exceptionSwallowedOnCallFromCom</span><span class="sxs-lookup"><span data-stu-id="46e38-123">exceptionSwallowedOnCallFromCom</span></span>](exceptionswallowedoncallfromcom-mda.md)|
|[<span data-ttu-id="46e38-124">failedQI</span><span class="sxs-lookup"><span data-stu-id="46e38-124">failedQI</span></span>](failedqi-mda.md)|[<span data-ttu-id="46e38-125">fatalExecutionEngineError</span><span class="sxs-lookup"><span data-stu-id="46e38-125">fatalExecutionEngineError</span></span>](fatalexecutionengineerror-mda.md)|
|[<span data-ttu-id="46e38-126">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="46e38-126">gcManagedToUnmanaged</span></span>](gcmanagedtounmanaged-mda.md)|[<span data-ttu-id="46e38-127">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="46e38-127">gcUnmanagedToManaged</span></span>](gcunmanagedtomanaged-mda.md)|
|[<span data-ttu-id="46e38-128">illegalPrepareConstrainedRegion</span><span class="sxs-lookup"><span data-stu-id="46e38-128">illegalPrepareConstrainedRegion</span></span>](illegalprepareconstrainedregion-mda.md)|[<span data-ttu-id="46e38-129">invalidApartmentStateChange</span><span class="sxs-lookup"><span data-stu-id="46e38-129">invalidApartmentStateChange</span></span>](invalidapartmentstatechange-mda.md)|
|[<span data-ttu-id="46e38-130">invalidCERCall</span><span class="sxs-lookup"><span data-stu-id="46e38-130">invalidCERCall</span></span>](invalidcercall-mda.md)|[<span data-ttu-id="46e38-131">invalidFunctionPointerInDelegate</span><span class="sxs-lookup"><span data-stu-id="46e38-131">invalidFunctionPointerInDelegate</span></span>](invalidfunctionpointerindelegate-mda.md)|
|[<span data-ttu-id="46e38-132">invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="46e38-132">invalidGCHandleCookie</span></span>](invalidgchandlecookie-mda.md)|[<span data-ttu-id="46e38-133">invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="46e38-133">invalidIUnknown</span></span>](invalidiunknown-mda.md)|
|[<span data-ttu-id="46e38-134">invalidMemberDeclaration</span><span class="sxs-lookup"><span data-stu-id="46e38-134">invalidMemberDeclaration</span></span>](invalidmemberdeclaration-mda.md)|[<span data-ttu-id="46e38-135">invalidOverlappedToPinvoke</span><span class="sxs-lookup"><span data-stu-id="46e38-135">invalidOverlappedToPinvoke</span></span>](invalidoverlappedtopinvoke-mda.md)|
|[<span data-ttu-id="46e38-136">invalidVariant</span><span class="sxs-lookup"><span data-stu-id="46e38-136">invalidVariant</span></span>](invalidvariant-mda.md)|[<span data-ttu-id="46e38-137">jitCompilationStart</span><span class="sxs-lookup"><span data-stu-id="46e38-137">jitCompilationStart</span></span>](jitcompilationstart-mda.md)|
|[<span data-ttu-id="46e38-138">loaderLock</span><span class="sxs-lookup"><span data-stu-id="46e38-138">loaderLock</span></span>](loaderlock-mda.md)|[<span data-ttu-id="46e38-139">loadFromContext</span><span class="sxs-lookup"><span data-stu-id="46e38-139">loadFromContext</span></span>](loadfromcontext-mda.md)|
|[<span data-ttu-id="46e38-140">marshalCleanupError</span><span class="sxs-lookup"><span data-stu-id="46e38-140">marshalCleanupError</span></span>](marshalcleanuperror-mda.md)|[<span data-ttu-id="46e38-141">sıralama</span><span class="sxs-lookup"><span data-stu-id="46e38-141">marshaling</span></span>](marshaling-mda.md)|
|[<span data-ttu-id="46e38-142">memberInfoCacheCreation</span><span class="sxs-lookup"><span data-stu-id="46e38-142">memberInfoCacheCreation</span></span>](memberinfocachecreation-mda.md)|[<span data-ttu-id="46e38-143">moduloObjectHashcode</span><span class="sxs-lookup"><span data-stu-id="46e38-143">moduloObjectHashcode</span></span>](moduloobjecthashcode-mda.md)|
|[<span data-ttu-id="46e38-144">nonComVisibleBaseClass</span><span class="sxs-lookup"><span data-stu-id="46e38-144">nonComVisibleBaseClass</span></span>](noncomvisiblebaseclass-mda.md)|[<span data-ttu-id="46e38-145">notMarshalable</span><span class="sxs-lookup"><span data-stu-id="46e38-145">notMarshalable</span></span>](notmarshalable-mda.md)|
|[<span data-ttu-id="46e38-146">openGenericCERCall</span><span class="sxs-lookup"><span data-stu-id="46e38-146">openGenericCERCall</span></span>](opengenericcercall-mda.md)|[<span data-ttu-id="46e38-147">overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="46e38-147">overlappedFreeError</span></span>](overlappedfreeerror-mda.md)|
|[<span data-ttu-id="46e38-148">pInvokeLog</span><span class="sxs-lookup"><span data-stu-id="46e38-148">pInvokeLog</span></span>](pinvokelog-mda.md)|[<span data-ttu-id="46e38-149">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="46e38-149">pInvokeStackImbalance</span></span>](pinvokestackimbalance-mda.md)|
|[<span data-ttu-id="46e38-150">raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="46e38-150">raceOnRCWCleanup</span></span>](raceonrcwcleanup-mda.md)|[<span data-ttu-id="46e38-151">yeniden giriş</span><span class="sxs-lookup"><span data-stu-id="46e38-151">reentrancy</span></span>](reentrancy-mda.md)|
|[<span data-ttu-id="46e38-152">releaseHandleFailed</span><span class="sxs-lookup"><span data-stu-id="46e38-152">releaseHandleFailed</span></span>](releasehandlefailed-mda.md)|[<span data-ttu-id="46e38-153">reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="46e38-153">reportAvOnComRelease</span></span>](reportavoncomrelease-mda.md)|
|[<span data-ttu-id="46e38-154">streamWriterBufferedDataLost</span><span class="sxs-lookup"><span data-stu-id="46e38-154">streamWriterBufferedDataLost</span></span>](streamwriterbuffereddatalost-mda.md)|[<span data-ttu-id="46e38-155">virtualCERCall</span><span class="sxs-lookup"><span data-stu-id="46e38-155">virtualCERCall</span></span>](virtualcercall-mda.md)|

<span data-ttu-id="46e38-156">Varsayılan olarak, .NET Framework yönetilen tüm hata ayıklayıcıları için bir MDA alt kümesini etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="46e38-156">By default, the .NET Framework activates a subset of MDAs for all managed debuggers.</span></span> <span data-ttu-id="46e38-157">Visual Studio 'da varsayılan kümeyi **Windows**  >  **Hata Ayıkla** menüsündeki Windows**özel durum ayarları** ' nı seçerek ve ardından **yönetilen hata ayıklama yardımcıları** listesini genişleterek görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46e38-157">You can view the default set in Visual Studio by choosing **Windows** > **Exception Settings** on the **Debug** menu, and then expanding the **Managed Debugging Assistants** list.</span></span>

![Visual Studio 'da özel durum ayarları penceresi](./media/diagnosing-errors-with-managed-debugging-assistants/exception-settings-mdas.png)

## <a name="enable-and-disable-mdas"></a><span data-ttu-id="46e38-159">Mdaları etkinleştirme ve devre dışı bırakma</span><span class="sxs-lookup"><span data-stu-id="46e38-159">Enable and Disable MDAs</span></span>

<span data-ttu-id="46e38-160">Bir kayıt defteri anahtarını, bir ortam değişkenini ve uygulama yapılandırma ayarlarını kullanarak MDA'leri etkinleştirebilir ve devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46e38-160">You can enable and disable MDAs by using a registry key, an environment variable, and application configuration settings.</span></span> <span data-ttu-id="46e38-161">Uygulama yapılandırma ayarlarını kullanmak için kayıt defteri anahtarını veya ortam değişkenini etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="46e38-161">You must enable either the registry key or the environment variable to use the application configuration settings.</span></span>

> [!TIP]
> <span data-ttu-id="46e38-162">MDAs 'yi devre dışı bırakmak yerine, bir MDA bildirimi alındığında Visual Studio 'Nun MDA iletişim kutusunu görüntülemesini engelleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46e38-162">Instead of disabling MDAs, you can prevent Visual Studio from displaying the MDA dialog box whenever an MDA notification is received.</span></span> <span data-ttu-id="46e38-163">Bunu yapmak için, **Windows**  >  **hata ayıklama** menüsünde Windows**özel durum ayarları** ' nı seçin, **yönetilen hata ayıklama yardımcıları** listesini genişletin ve sonra tek bir mda için **oluşturulduğunda kes** onay kutusunu seçin veya temizleyin.</span><span class="sxs-lookup"><span data-stu-id="46e38-163">To do that, choose **Windows** > **Exception Settings** on the **Debug** menu, expand the **Managed Debugging Assistants** list, and then select or clear the **Break When Thrown** check box for the individual MDA.</span></span>

### <a name="registry-key"></a><span data-ttu-id="46e38-164">Kayıt Defteri Anahtarı</span><span class="sxs-lookup"><span data-stu-id="46e38-164">Registry Key</span></span>

<span data-ttu-id="46e38-165">MDAs 'yi etkinleştirmek için, **\ Software\microsoft HKEY_LOCAL_MACHINE ekleyin \\ . Windows kayıt defteri 'nde NETFramework\MDA** AltAnahtar (tür REG_SZ, değer 1).</span><span class="sxs-lookup"><span data-stu-id="46e38-165">To enable MDAs, add the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\MDA** subkey (type REG_SZ, value 1) in the Windows registry.</span></span> <span data-ttu-id="46e38-166">Aşağıdaki örneği *Mdadenable. reg*adlı bir metin dosyasına kopyalayın. Windows kayıt defteri Düzenleyicisi 'Ni (RegEdit.exe) açın ve **Dosya** menüsünden **içeri aktar**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="46e38-166">Copy the following example into a text file named *MDAEnable.reg*. Open the Windows Registry Editor (RegEdit.exe), and from the **File** menu choose **Import**.</span></span> <span data-ttu-id="46e38-167">Bu bilgisayarda MDAs 'yi etkinleştirmek için *MDAEnable. reg* dosyasını seçin.</span><span class="sxs-lookup"><span data-stu-id="46e38-167">Select the *MDAEnable.reg* file to enable MDAs on that computer.</span></span> <span data-ttu-id="46e38-168">Alt anahtarı, **1** ' in dize DEĞERINE (DWORD değeri **1**değil) ayarlamak, ' nin *APPLICATIONNAME. suffix*.mda.config dosyasından MDA ayarlarının okunmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="46e38-168">Setting the subkey to string value of **1** (not DWORD value of **1**) enables the reading of MDA settings from the *ApplicationName.suffix*.mda.config file.</span></span> <span data-ttu-id="46e38-169">Örneğin, Notepad için MDA yapılandırma dosyası notepad.exe.mda.config olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="46e38-169">For example, the MDA configuration file for Notepad would be named notepad.exe.mda.config.</span></span>

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework]
"MDA"="1"
```

<span data-ttu-id="46e38-170">Bilgisayar 64 bit işletim sisteminde 32 bitlik bir uygulama çalıştırıyorsa, MDA anahtarı aşağıdaki gibi ayarlanmalıdır:</span><span class="sxs-lookup"><span data-stu-id="46e38-170">If the computer is running a 32-bit application on a 64-bit operating system, then the MDA key should be set like the following:</span></span>

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework]
"MDA"="1"
```

<span data-ttu-id="46e38-171">Daha fazla bilgi için [uygulamaya özgü yapılandırma ayarlarına](#application-specific-configuration-settings) bakın.</span><span class="sxs-lookup"><span data-stu-id="46e38-171">See [Application-Specific Configuration Settings](#application-specific-configuration-settings) for more information.</span></span> <span data-ttu-id="46e38-172">Kayıt defteri ayarı, COMPLUS_MDA ortam değişkeni tarafından geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="46e38-172">The registry setting can be overridden by the COMPLUS_MDA environment variable.</span></span> <span data-ttu-id="46e38-173">Daha fazla bilgi için bkz. [ortam değişkeni](#environment-variable) .</span><span class="sxs-lookup"><span data-stu-id="46e38-173">See [Environment Variable](#environment-variable) for more information.</span></span>

<span data-ttu-id="46e38-174">MDAs 'yi devre dışı bırakmak için, Windows kayıt defteri düzenleyicisini kullanarak MDA alt anahtarını **0** (sıfır) olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="46e38-174">To disable MDAs, set the MDA subkey to **0** (zero) using the Windows Registry Editor.</span></span>

<span data-ttu-id="46e38-175">Bir hata ayıklayıcıya bağlı bir uygulamayı çalıştırdığınızda kayıt defteri anahtarı bile eklemeden bazı MDA'ler varsayılan olarak etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="46e38-175">By default, some MDAs are enabled when you run an application that is attached to a debugger, even without adding the registry key.</span></span> <span data-ttu-id="46e38-176">Bu bölümün önceki kısımlarında açıklandığı gibi *Mdaddisable. reg* dosyasını çalıştırarak bu yardımcıları devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46e38-176">You can disable these assistants by running the *MDADisable.reg* file as described earlier in this section.</span></span>

### <a name="environment-variable"></a><span data-ttu-id="46e38-177">Ortam değişkeni</span><span class="sxs-lookup"><span data-stu-id="46e38-177">Environment Variable</span></span>

<span data-ttu-id="46e38-178">MDA etkinleştirmesi aynı zamanda, kayıt defteri anahtarını geçersiz kılan COMPLUS_MDA ortam değişkeni tarafından da kontrol edilebilir.</span><span class="sxs-lookup"><span data-stu-id="46e38-178">MDA activation can also controlled by the environment variable COMPLUS_MDA, which overrides the registry key.</span></span> <span data-ttu-id="46e38-179">COMPLUS_MDA dizesi, MDA adlarının veya başka özel denetim dizelerinin büyük/küçük harf duyarlı, noktalı virgülle ayrılmış listesidir.</span><span class="sxs-lookup"><span data-stu-id="46e38-179">The COMPLUS_MDA string is a case-insensitive, semicolon-delimited list of MDA names or other special control strings.</span></span> <span data-ttu-id="46e38-180">Yönetilen veya yönetilmeyen hata ayıklayıcı altında başlamak varsayılan olarak bir MDA kümesini etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="46e38-180">Starting under a managed or unmanaged debugger enables a set of MDAs by default.</span></span> <span data-ttu-id="46e38-181">Bu, varsayılan olarak hata ayıklayıcılarda etkinleştirilen, noktalı virgülle ayrılmış MDA listesini ortam değişkeninin veya kayıt defteri anahtarının değerine açıkça ekleyerek yapılır.</span><span class="sxs-lookup"><span data-stu-id="46e38-181">This is done by implicitly prepending the semicolon-delimited list of MDAs enabled by default under debuggers to the value of the environment variable or registry key.</span></span> <span data-ttu-id="46e38-182">Özel denetim dizeleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="46e38-182">The special control strings are the following:</span></span>

- <span data-ttu-id="46e38-183">`0` - Tüm MDA'leri devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="46e38-183">`0` - Deactivates all MDAs.</span></span>

- <span data-ttu-id="46e38-184">`1`- *ApplicationName*.mda.config 'den MDA ayarlarını okur.</span><span class="sxs-lookup"><span data-stu-id="46e38-184">`1` - Reads MDA settings from *ApplicationName*.mda.config.</span></span>

- <span data-ttu-id="46e38-185">`managedDebugger` - Yönetilen bir yürütülebilir dosya hata ayıklayıcı altında başlatıldığında dolaylı olarak etkinleştirilmiş tüm MDA'leri açıkça etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="46e38-185">`managedDebugger` - Explicitly activates all MDAs that are implicitly activated when a managed executable is started under a debugger.</span></span>

- <span data-ttu-id="46e38-186">`unmanagedDebugger` - Yönetilmeyen bir yürütülebilir dosya hata ayıklayıcı altında başlatıldığında dolaylı olarak etkinleştirilmiş tüm MDA'leri açıkça etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="46e38-186">`unmanagedDebugger` - Explicitly activates all MDAs that are implicitly activated when an unmanaged executable is started under a debugger.</span></span>

<span data-ttu-id="46e38-187">Çakışan ayarlar varsa, en son ayarlar önceki ayarları geçersiz kılar:</span><span class="sxs-lookup"><span data-stu-id="46e38-187">If there are conflicting settings, the most recent settings override previous settings:</span></span>

- <span data-ttu-id="46e38-188">`COMPLUS_MDA=0`, dolaylı olarak bir hata ayıklayıcıda etkinleştirilmiş olanlar dahil olmak üzere tüm MDA'leri devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="46e38-188">`COMPLUS_MDA=0` disables all MDAs, including those implicitly enabled under a debugger.</span></span>

- <span data-ttu-id="46e38-189">`COMPLUS_MDA=gcUnmanagedToManaged`, bir hata ayıklayıcıda dolaylı olarak etkinleştirilen MDA'lere ek olarak `gcUnmanagedToManaged` öğesini etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="46e38-189">`COMPLUS_MDA=gcUnmanagedToManaged` enables `gcUnmanagedToManaged` in addition to any MDAs that are implicitly enabled under a debugger.</span></span>

- <span data-ttu-id="46e38-190">`COMPLUS_MDA=0;gcUnmanagedToManaged`, `gcUnmanagedToManaged` öğesini etkinleştirir, ancak aksi takdirde dolaylı olarak bir hata ayıklayıcıda etkinleştirilecek olan MDA'leri devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="46e38-190">`COMPLUS_MDA=0;gcUnmanagedToManaged` enables `gcUnmanagedToManaged` but disables MDAs that would otherwise be implicitly enabled under a debugger.</span></span>

### <a name="application-specific-configuration-settings"></a><span data-ttu-id="46e38-191">Uygulamaya özgü yapılandırma ayarları</span><span class="sxs-lookup"><span data-stu-id="46e38-191">Application-Specific Configuration Settings</span></span>

<span data-ttu-id="46e38-192">Uygulamaya ait MDA yapılandırma dosyası içinde bazı yardımcıları etkinleştirebilir, devre dışı bırakabilir ve ayrı ayrı yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46e38-192">You can enable, disable, and configure some assistants individually in the MDA configuration file for the application.</span></span> <span data-ttu-id="46e38-193">MDA'leri yapılandırmak üzere bir uygulama yapılandırma dosyasının kullanımını etkinleştirmek için MDA kayıt defteri anahtarının veya COMPLUS_MDA ortam değişkeni ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="46e38-193">To enable the use of an application configuration file for configuring MDAs, either the MDA registry key or the COMPLUS_MDA environment variable must be set.</span></span> <span data-ttu-id="46e38-194">Uygulama yapılandırma dosyası, genellikle uygulamanın yürütülebilir (.exe) dosyası ile aynı dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="46e38-194">The application configuration file is typically located in the same directory as the application's executable (.exe) file.</span></span> <span data-ttu-id="46e38-195">Dosya adı, *ApplicationName*.mda.config. Örneğin, notepad.exe.mda.config. Uygulama yapılandırma dosyasında etkinleştirilen yardımcılar, bu yardımcının davranışını denetlemek için özel olarak tasarlanmış özniteliklere veya öğelere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="46e38-195">The file name takes the form *ApplicationName*.mda.config; for example, notepad.exe.mda.config. Assistants that are enabled in the application configuration file may have attributes or elements specifically designed to control that assistant's behavior.</span></span>

<span data-ttu-id="46e38-196">Aşağıdaki örnek, [hazırlamayı](marshaling-mda.md)nasıl etkinleştireceğinizi ve yapılandıracağınızı göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="46e38-196">The following example shows how to enable and configure the [marshaling](marshaling-mda.md):</span></span>

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

<span data-ttu-id="46e38-197">`Marshaling` MDA, uygulamadaki her yönetilenden yönetilmeyene geçiş için bir yönetilmeyen türe sıraya koyulan yönetilen tür hakkında bilgiler verir.</span><span class="sxs-lookup"><span data-stu-id="46e38-197">The `Marshaling` MDA emits information about the managed type that is being marshaled to an unmanaged type for each managed-to-unmanaged transition in the application.</span></span> <span data-ttu-id="46e38-198">`Marshaling`MDA, sırasıyla **methodFilter** ve **FieldFilter** alt öğelerinde sağlanan yöntem ve yapı alanlarının adlarını da filtreleyebilirler.</span><span class="sxs-lookup"><span data-stu-id="46e38-198">The `Marshaling` MDA can also filter the names of the method and structure fields supplied in the **methodFilter** and **fieldFilter** child elements, respectively.</span></span>

<span data-ttu-id="46e38-199">Aşağıdaki örnek, varsayılan ayarlarını kullanarak birden çok Mdayı nasıl etkinleştireceğinizi göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="46e38-199">The following example shows how to enable multiple MDAs by using their default settings:</span></span>

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
> <span data-ttu-id="46e38-200">Bir yapılandırma dosyasında birden fazla yardımcı belirttiğinizde, bunları alfabetik olarak listelemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="46e38-200">When you specify more than one assistant in a configuration file, you must list them in alphabetical order.</span></span> <span data-ttu-id="46e38-201">Örneğin, `virtualCERCall` ve `invalidCERCall` MDA'lerinin her ikisini de etkinleştirmek istiyorsanız `<invalidCERCall />` girdisinden önce `<virtualCERCall />` girdisini eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="46e38-201">For example, if you want to enable both the `virtualCERCall` and the `invalidCERCall` MDAs, you must add the `<invalidCERCall />` entry before the `<virtualCERCall />` entry.</span></span> <span data-ttu-id="46e38-202">Girdiler alfabetik sırada değilse, işlenmemiş bir geçersiz yapılandırma dosyası özel durum iletisi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="46e38-202">If the entries are not in alphabetical order, an unhandled invalid configuration file exception message is displayed.</span></span>

## <a name="mda-exceptions"></a><span data-ttu-id="46e38-203">MDA özel durumlar</span><span class="sxs-lookup"><span data-stu-id="46e38-203">MDA exceptions</span></span>

<span data-ttu-id="46e38-204">Bir MDA etkinleştirildiğinde, kodunuz bir hata ayıklayıcı altında yürütülmediğinde bile etkin olur.</span><span class="sxs-lookup"><span data-stu-id="46e38-204">When an MDA is enabled, it's active even when your code is not executing under a debugger.</span></span> <span data-ttu-id="46e38-205">Bir hata ayıklayıcı olmadığında bir MDA olayı oluşturulursa, işlenmemiş özel bir durum olmasa bile olay iletisi, işlenmemiş özel durum iletişim kutusunda sunulur.</span><span class="sxs-lookup"><span data-stu-id="46e38-205">If an MDA event is raised when a debugger is not present, the event message is presented in an unhandled exception dialog box, although it is not an unhandled exception.</span></span> <span data-ttu-id="46e38-206">İletişim kutusunu önlemek için kodunuz hata ayıklama ortamında çalışmıyorken MDA etkinleştirme ayarlarını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="46e38-206">To avoid the dialog box, remove the MDA-enabling settings when your code is not executing in a debugging environment.</span></span>

<span data-ttu-id="46e38-207">Kodunuz Visual Studio tümleşik geliştirme ortamında (IDE) yürütüldüğünde, belirli MDA olayları için görüntülenen özel durum iletişim kutusunu önleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46e38-207">When your code executes in the Visual Studio integrated development environment (IDE), you can avoid the exception dialog box that appears for specific MDA events.</span></span> <span data-ttu-id="46e38-208">Bunu yapmak için, **Hata Ayıkla** menüsünde **Windows**  >  **özel durum ayarları**' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="46e38-208">To do that, on the **Debug** menu, choose **Windows** > **Exception Settings**.</span></span> <span data-ttu-id="46e38-209">**Özel durum ayarları** penceresinde, **yönetilen hata ayıklama yardımcıları** listesini genişletin ve sonra tek bir mda için **oluşturulan** onay kutusunu temizleyin.</span><span class="sxs-lookup"><span data-stu-id="46e38-209">In the **Exception Settings** window, expand the **Managed Debugging Assistants** list, and then clear the **Break When Thrown** check box for the individual MDA.</span></span> <span data-ttu-id="46e38-210">Bu iletişim kutusunu, MDA özel durum iletişim kutularının görüntülenmesini *sağlamak* için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46e38-210">You can also use this dialog box to *enable* the display of MDA exception dialog boxes.</span></span>

## <a name="mda-output"></a><span data-ttu-id="46e38-211">MDA Çıktısı</span><span class="sxs-lookup"><span data-stu-id="46e38-211">MDA Output</span></span>

<span data-ttu-id="46e38-212">MDA çıktısı, MDA ' dan çıktıyı gösteren aşağıdaki örneğe benzer `PInvokeStackImbalance` .</span><span class="sxs-lookup"><span data-stu-id="46e38-212">MDA output is similar to the following example, which shows the output from the `PInvokeStackImbalance` MDA:</span></span>

<span data-ttu-id="46e38-213">**PInvoke işlevi ' Mdadtest! ' çağrısı Mdadtest. Program:: StdCall ', yığına dengesiz. Bu, yönetilen PInvoke imzasının yönetilmeyen hedef imzasıyla eşleşmemesi nedeniyle olasıdır. PInvoke imzasının çağırma kuralı ve parametrelerinin hedef yönetilmeyen imzayla eşleşip eşleştiğinden emin olun.**</span><span class="sxs-lookup"><span data-stu-id="46e38-213">**A call to PInvoke function 'MDATest!MDATest.Program::StdCall' has unbalanced the stack. This is likely because the managed PInvoke signature does not match the unmanaged target signature. Check that the calling convention and parameters of the PInvoke signature match the target unmanaged signature.**</span></span>

## <a name="see-also"></a><span data-ttu-id="46e38-214">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46e38-214">See also</span></span>

- [<span data-ttu-id="46e38-215">Hata ayıklama, Izleme ve profil oluşturma</span><span class="sxs-lookup"><span data-stu-id="46e38-215">Debugging, Tracing, and Profiling</span></span>](index.md)
