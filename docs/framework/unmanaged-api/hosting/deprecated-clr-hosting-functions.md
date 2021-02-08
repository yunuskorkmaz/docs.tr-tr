---
description: 'Daha fazla bilgi edinin: kullanım dışı CLR Barındırma Işlevleri'
title: Kullanım Dışı CLR Barındırma İşlevleri
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 1.1, hosting global static functions
- global static functions [.NET Framework hosting], version 2.0
- .NET Framework 2.0, hosting global static functions
- hosting global static functions [.NET Framework], version 2.0
ms.assetid: 91fbbb35-e543-4814-b806-371cebae8c5a
ms.openlocfilehash: 3d16b5829e29c5c963f4790bbb3be7adcaeedbfc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785672"
---
# <a name="deprecated-clr-hosting-functions"></a><span data-ttu-id="6a0e4-103">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="6a0e4-103">Deprecated CLR Hosting Functions</span></span>

<span data-ttu-id="6a0e4-104">Bu bölümde, barındırma API 'sinin önceki sürümlerinin kullanıldığı yönetilmeyen genel statik işlevler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-104">This section describes the unmanaged global static functions that earlier versions of the hosting API used.</span></span>  
  
 <span data-ttu-id="6a0e4-105">`_Cor*`Yalnızca .NET Framework tarafından kullanılan altyapı işlevleri (işlevler) dışında, bu işlevler .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-105">With the exception of the infrastructure functions (`_Cor*` functions), which are used only by the .NET Framework, these functions have been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="activation-functions"></a><span data-ttu-id="6a0e4-106">Etkinleştirme işlevleri</span><span class="sxs-lookup"><span data-stu-id="6a0e4-106">Activation functions</span></span>  

 [<span data-ttu-id="6a0e4-107">ClrCreateManagedInstance İşlevi</span><span class="sxs-lookup"><span data-stu-id="6a0e4-107">ClrCreateManagedInstance Function</span></span>](clrcreatemanagedinstance-function.md)  
 <span data-ttu-id="6a0e4-108">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-108">Deprecated.</span></span> <span data-ttu-id="6a0e4-109">Belirtilen yönetilen türün bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-109">Creates an instance of the specified managed type.</span></span>  
  
 [<span data-ttu-id="6a0e4-110">CoInitializeCor İşlevi</span><span class="sxs-lookup"><span data-stu-id="6a0e4-110">CoInitializeCor Function</span></span>](coinitializecor-function.md)  
 <span data-ttu-id="6a0e4-111">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-111">Obsolete.</span></span> <span data-ttu-id="6a0e4-112">Ortak dil çalışma zamanını (CLR) başlatmak için [CorBindToRuntimeEx](corbindtoruntimeex-function.md) veya [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md)kullanın.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-112">To initialize the common language runtime (CLR), use either [CorBindToRuntimeEx](corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span></span>  
  
 [<span data-ttu-id="6a0e4-113">CoInitializeEE İşlevi</span><span class="sxs-lookup"><span data-stu-id="6a0e4-113">CoInitializeEE Function</span></span>](coinitializeee-function.md)  
 <span data-ttu-id="6a0e4-114">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-114">Deprecated.</span></span> <span data-ttu-id="6a0e4-115">CLR yürütme altyapısının bir işleme yüklenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-115">Ensures that the CLR execution engine is loaded into a process.</span></span> <span data-ttu-id="6a0e4-116">Bunun yerine [ICLRRuntimeHost:: Start](iclrruntimehost-start-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-116">Use the [ICLRRuntimeHost::Start](iclrruntimehost-start-method.md) method instead.</span></span>  
  
 [<span data-ttu-id="6a0e4-117">CorBindToCurrentRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="6a0e4-117">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)  
 <span data-ttu-id="6a0e4-118">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-118">Deprecated.</span></span> <span data-ttu-id="6a0e4-119">Bir XML dosyasında depolanan sürüm bilgilerini kullanarak ortak dil çalışma zamanını (CLR) bir işleme yükler.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-119">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span>  
  
 [<span data-ttu-id="6a0e4-120">CorBindToRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="6a0e4-120">CorBindToRuntime Function</span></span>](corbindtoruntime-function.md)  
 <span data-ttu-id="6a0e4-121">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-121">Deprecated.</span></span> <span data-ttu-id="6a0e4-122">Yönetilmeyen ana bilgisayarların CLR 'yi bir işleme yüklemesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-122">Enables unmanaged hosts to load the CLR into a process.</span></span>  
  
 [<span data-ttu-id="6a0e4-123">CorBindToRuntimeByCfg İşlevi</span><span class="sxs-lookup"><span data-stu-id="6a0e4-123">CorBindToRuntimeByCfg Function</span></span>](corbindtoruntimebycfg-function.md)  
 <span data-ttu-id="6a0e4-124">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-124">Deprecated.</span></span> <span data-ttu-id="6a0e4-125">XML dosyasından okunan sürüm bilgilerini kullanarak CLR 'yi bir işleme yükler.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-125">Loads the CLR into a process by using version information that is read from an XML file.</span></span>  
  
 [<span data-ttu-id="6a0e4-126">CorBindToRuntimeEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="6a0e4-126">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)  
 <span data-ttu-id="6a0e4-127">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-127">Deprecated.</span></span> <span data-ttu-id="6a0e4-128">Yönetilmeyen ana bilgisayarların CLR 'yi bir işleme yüklemesine olanak tanır ve CLR 'nin davranışını belirtmek için bayraklar ayarlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-128">Enables unmanaged hosts to load the CLR into a process, and allows you to set flags to specify the behavior of the CLR.</span></span>  
  
 [<span data-ttu-id="6a0e4-129">CorBindToRuntimeHost İşlevi</span><span class="sxs-lookup"><span data-stu-id="6a0e4-129">CorBindToRuntimeHost Function</span></span>](corbindtoruntimehost-function.md)  
 <span data-ttu-id="6a0e4-130">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-130">Deprecated.</span></span> <span data-ttu-id="6a0e4-131">Ana bilgisayarların belirli bir CLR sürümünü bir işleme yüklemesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-131">Enables hosts to load a specified version of the CLR into a process.</span></span>  
  
 [<span data-ttu-id="6a0e4-132">GetCORRequiredVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="6a0e4-132">GetCORRequiredVersion Function</span></span>](getcorrequiredversion-function.md)  
 <span data-ttu-id="6a0e4-133">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-133">Deprecated.</span></span> <span data-ttu-id="6a0e4-134">Gereken CLR sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-134">Gets the required CLR version number.</span></span>  
  
 [<span data-ttu-id="6a0e4-135">GetCORSystemDirectory İşlevi</span><span class="sxs-lookup"><span data-stu-id="6a0e4-135">GetCORSystemDirectory Function</span></span>](getcorsystemdirectory-function.md)  
 <span data-ttu-id="6a0e4-136">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-136">Deprecated.</span></span> <span data-ttu-id="6a0e4-137">İşleme yüklenen CLR 'nin yükleme dizinini döndürür.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-137">Returns the installation directory of the CLR that is loaded into the process.</span></span>  
  
 [<span data-ttu-id="6a0e4-138">GetRealProcAddress İşlevi</span><span class="sxs-lookup"><span data-stu-id="6a0e4-138">GetRealProcAddress Function</span></span>](getrealprocaddress-function.md)  
 <span data-ttu-id="6a0e4-139">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-139">Deprecated.</span></span> <span data-ttu-id="6a0e4-140">CLR 'nin en son yüklenen sürümünden aktarılmış olan belirtilen işlevin adresini alır.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-140">Gets the address of the specified function that is exported from the latest installed version of the CLR.</span></span>  
  
 [<span data-ttu-id="6a0e4-141">GetRequestedRuntimeInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="6a0e4-141">GetRequestedRuntimeInfo Function</span></span>](getrequestedruntimeinfo-function.md)  
 <span data-ttu-id="6a0e4-142">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-142">Deprecated.</span></span> <span data-ttu-id="6a0e4-143">Bir uygulama tarafından istenen CLR ile ilgili sürüm ve dizin bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-143">Gets version and directory information about the CLR requested by an application.</span></span>  
  
## <a name="clr-version-functions"></a><span data-ttu-id="6a0e4-144">CLR sürüm işlevleri</span><span class="sxs-lookup"><span data-stu-id="6a0e4-144">CLR version functions</span></span>  

 <span data-ttu-id="6a0e4-145">Bu bölümdeki işlevler bir CLR sürümü döndürür; CLR 'yi etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-145">The functions in this section return a CLR version; they do not activate the CLR.</span></span>  
  
 [<span data-ttu-id="6a0e4-146">GetCORVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="6a0e4-146">GetCORVersion Function</span></span>](getcorversion-function.md)  
 <span data-ttu-id="6a0e4-147">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-147">Deprecated.</span></span> <span data-ttu-id="6a0e4-148">Geçerli işlemde çalışan CLR 'nin sürüm numarasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-148">Returns the version number of the CLR that is running in the current process.</span></span>  
  
 [<span data-ttu-id="6a0e4-149">GetFileVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="6a0e4-149">GetFileVersion Function</span></span>](getfileversion-function.md)  
 <span data-ttu-id="6a0e4-150">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-150">Deprecated.</span></span> <span data-ttu-id="6a0e4-151">Belirtilen arabelleği kullanarak belirtilen dosyanın CLR sürüm bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-151">Gets the CLR version information of the specified file, using the specified buffer.</span></span>  
  
 [<span data-ttu-id="6a0e4-152">GetRequestedRuntimeVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="6a0e4-152">GetRequestedRuntimeVersion Function</span></span>](getrequestedruntimeversion-function.md)  
 <span data-ttu-id="6a0e4-153">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-153">Deprecated.</span></span> <span data-ttu-id="6a0e4-154">Belirtilen uygulama tarafından istenen CLR 'nin sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-154">Gets the version number of the CLR requested by the specified application.</span></span> <span data-ttu-id="6a0e4-155">Bu sürüm yüklü değilse, istenen sürümden önce yüklenen en son sürümü alır.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-155">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 [<span data-ttu-id="6a0e4-156">GetRequestedRuntimeVersionForCLSID İşlevi</span><span class="sxs-lookup"><span data-stu-id="6a0e4-156">GetRequestedRuntimeVersionForCLSID Function</span></span>](getrequestedruntimeversionforclsid-function.md)  
 <span data-ttu-id="6a0e4-157">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-157">Deprecated.</span></span> <span data-ttu-id="6a0e4-158">Belirtilen CLSID ile sınıf için uygun CLR sürüm bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-158">Gets the appropriate CLR version information for the class with the specified CLSID.</span></span>  
  
 [<span data-ttu-id="6a0e4-159">GetVersionFromProcess İşlevi</span><span class="sxs-lookup"><span data-stu-id="6a0e4-159">GetVersionFromProcess Function</span></span>](getversionfromprocess-function.md)  
 <span data-ttu-id="6a0e4-160">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-160">Deprecated.</span></span> <span data-ttu-id="6a0e4-161">Belirtilen işlem tanıtıcısından ilişkilendirilen CLR 'nin sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-161">Gets the version number of the CLR that is associated with the specified process handle.</span></span>  
  
 [<span data-ttu-id="6a0e4-162">LockClrVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="6a0e4-162">LockClrVersion Function</span></span>](lockclrversion-function.md)  
 <span data-ttu-id="6a0e4-163">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-163">Deprecated.</span></span> <span data-ttu-id="6a0e4-164">Konağın clr 'yi açıkça başlatmadan önce işlem içinde hangi CLR sürümünün kullanılacağını belirlemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-164">Allows the host to determine which version of the CLR will be used within the process before explicitly initializing the CLR.</span></span>  
  
## <a name="hosting-functions"></a><span data-ttu-id="6a0e4-165">Barındırma işlevleri</span><span class="sxs-lookup"><span data-stu-id="6a0e4-165">Hosting functions</span></span>  

 [<span data-ttu-id="6a0e4-166">CallFunctionShim İşlevi</span><span class="sxs-lookup"><span data-stu-id="6a0e4-166">CallFunctionShim Function</span></span>](callfunctionshim-function.md)  
 <span data-ttu-id="6a0e4-167">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-167">Deprecated.</span></span> <span data-ttu-id="6a0e4-168">Belirtilen kitaplıkta belirtilen ad ve parametrelere sahip işleve bir çağrı yapar.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-168">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 [<span data-ttu-id="6a0e4-169">CoEEShutDownCOM İşlevi</span><span class="sxs-lookup"><span data-stu-id="6a0e4-169">CoEEShutDownCOM Function</span></span>](coeeshutdowncom-function.md)  
 <span data-ttu-id="6a0e4-170">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-170">Deprecated.</span></span> <span data-ttu-id="6a0e4-171">İşlemden bir COM derlemesini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-171">Unloads a COM assembly from the process.</span></span>  
  
 [<span data-ttu-id="6a0e4-172">CorExitProcess İşlevi</span><span class="sxs-lookup"><span data-stu-id="6a0e4-172">CorExitProcess Function</span></span>](corexitprocess-function.md)  
 <span data-ttu-id="6a0e4-173">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-173">Deprecated.</span></span> <span data-ttu-id="6a0e4-174">Geçerli yönetilmeyen işlemi kapatır.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-174">Shuts down the current unmanaged process.</span></span>  
  
 [<span data-ttu-id="6a0e4-175">CorLaunchApplication İşlevi</span><span class="sxs-lookup"><span data-stu-id="6a0e4-175">CorLaunchApplication Function</span></span>](corlaunchapplication-function.md)  
 <span data-ttu-id="6a0e4-176">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-176">Deprecated.</span></span> <span data-ttu-id="6a0e4-177">Belirtilen bildirimleri ve diğer uygulama verilerini kullanarak belirtilen ağ yolundaki uygulamayı başlatır.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-177">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 [<span data-ttu-id="6a0e4-178">CorMarkThreadInThreadPool İşlevi</span><span class="sxs-lookup"><span data-stu-id="6a0e4-178">CorMarkThreadInThreadPool Function</span></span>](cormarkthreadinthreadpool-function.md)  
 <span data-ttu-id="6a0e4-179">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-179">Deprecated.</span></span> <span data-ttu-id="6a0e4-180">Yönetilen kodun yürütülmesi için şu anda yürütülmekte olan iş parçacığı havuzu iş parçacığını işaretler.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-180">Marks the currently executing thread-pool thread for the execution of managed code.</span></span> <span data-ttu-id="6a0e4-181">.NET Framework sürüm 2,0 ' den başlayarak, bu işlevin etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-181">Starting with the .NET Framework version 2.0, this function has no effect.</span></span> <span data-ttu-id="6a0e4-182">Gerekli değildir ve kodınızdan kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-182">It is not required, and can be removed from your code.</span></span>  
  
 [<span data-ttu-id="6a0e4-183">CoUninitializeCor İşlevi</span><span class="sxs-lookup"><span data-stu-id="6a0e4-183">CoUninitializeCor Function</span></span>](couninitializecor-function.md)  
 <span data-ttu-id="6a0e4-184">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-184">Obsolete.</span></span> <span data-ttu-id="6a0e4-185">CLR bir işlemden kaldırılamıyor.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-185">The CLR cannot be unloaded from a process.</span></span>  
  
 [<span data-ttu-id="6a0e4-186">CoUninitializeEE İşlevi</span><span class="sxs-lookup"><span data-stu-id="6a0e4-186">CoUninitializeEE Function</span></span>](couninitializeee-function.md)  
 <span data-ttu-id="6a0e4-187">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-187">Obsolete.</span></span>  
  
 [<span data-ttu-id="6a0e4-188">CreateDebuggingInterfaceFromVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="6a0e4-188">CreateDebuggingInterfaceFromVersion Function</span></span>](createdebugginginterfacefromversion-function.md)  
 <span data-ttu-id="6a0e4-189">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-189">Deprecated.</span></span> <span data-ttu-id="6a0e4-190">Belirtilen sürüm bilgilerini temel alan bir [ICorDebug](../debugging/icordebug-interface.md) nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-190">Creates an [ICorDebug](../debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 [<span data-ttu-id="6a0e4-191">CreateICeeFileGen İşlevi</span><span class="sxs-lookup"><span data-stu-id="6a0e4-191">CreateICeeFileGen Function</span></span>](createiceefilegen-function.md)  
 <span data-ttu-id="6a0e4-192">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-192">Deprecated.</span></span> <span data-ttu-id="6a0e4-193">Bir [ICeeFileGen](iceefilegen-class.md) nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-193">Creates an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 [<span data-ttu-id="6a0e4-194">DestroyICeeFileGen İşlevi</span><span class="sxs-lookup"><span data-stu-id="6a0e4-194">DestroyICeeFileGen Function</span></span>](destroyiceefilegen-function.md)  
 <span data-ttu-id="6a0e4-195">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-195">Deprecated.</span></span> <span data-ttu-id="6a0e4-196">Bir [ICeeFileGen](iceefilegen-class.md) nesnesini yok eder.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-196">Destroys an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 [<span data-ttu-id="6a0e4-197">FExecuteInAppDomainCallback İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="6a0e4-197">FExecuteInAppDomainCallback Function Pointer</span></span>](fexecuteinappdomaincallback-function-pointer.md)  
 <span data-ttu-id="6a0e4-198">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-198">Deprecated.</span></span> <span data-ttu-id="6a0e4-199">CLR 'nin yönetilen kodu yürütmek için çağırdığı bir işleve işaret eder.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-199">Points to a function that the CLR calls to execute managed code.</span></span>  
  
 [<span data-ttu-id="6a0e4-200">FLockClrVersionCallback İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="6a0e4-200">FLockClrVersionCallback Function Pointer</span></span>](flockclrversioncallback-function-pointer.md)  
 <span data-ttu-id="6a0e4-201">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-201">Deprecated.</span></span> <span data-ttu-id="6a0e4-202">CLR 'nin, başlatmanın başlatıldığını ya da tamamlandığını bildirmek için çağırdığı bir işleve işaret eder.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-202">Points to a function that the CLR calls to notify the host that initialization has either started or completed.</span></span>  
  
 [<span data-ttu-id="6a0e4-203">GetCLRIdentityManager İşlevi</span><span class="sxs-lookup"><span data-stu-id="6a0e4-203">GetCLRIdentityManager Function</span></span>](getclridentitymanager-function.md)  
 <span data-ttu-id="6a0e4-204">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-204">Deprecated.</span></span> <span data-ttu-id="6a0e4-205">CLR 'nin kimlikleri yönetmesine izin veren bir arabirime yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-205">Gets a pointer to an interface that allows the CLR to manage identities.</span></span>  
  
 [<span data-ttu-id="6a0e4-206">LoadLibraryShim İşlevi</span><span class="sxs-lookup"><span data-stu-id="6a0e4-206">LoadLibraryShim Function</span></span>](loadlibraryshim-function.md)  
 <span data-ttu-id="6a0e4-207">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-207">Deprecated.</span></span> <span data-ttu-id="6a0e4-208">.NET Framework DLL 'nin belirtilen bir sürümünü yükler.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-208">Loads a specified version of a .NET Framework DLL.</span></span>  
  
 [<span data-ttu-id="6a0e4-209">LoadStringRC İşlevi</span><span class="sxs-lookup"><span data-stu-id="6a0e4-209">LoadStringRC Function</span></span>](loadstringrc-function.md)  
 <span data-ttu-id="6a0e4-210">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-210">Deprecated.</span></span> <span data-ttu-id="6a0e4-211">Geçerli iş parçacığının varsayılan kültürünü kullanarak bir HRESULT değerini bir hata iletisine çevirir.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-211">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 [<span data-ttu-id="6a0e4-212">LoadStringRCEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="6a0e4-212">LoadStringRCEx Function</span></span>](loadstringrcex-function.md)  
 <span data-ttu-id="6a0e4-213">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-213">Deprecated.</span></span> <span data-ttu-id="6a0e4-214">Belirtilen kültür için bir HRESULT değerini uygun bir hata iletisine çevirir.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-214">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 [<span data-ttu-id="6a0e4-215">LPOVERLAPPED_COMPLETION_ROUTINE İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="6a0e4-215">LPOVERLAPPED_COMPLETION_ROUTINE Function Pointer</span></span>](lpoverlapped-completion-routine-function-pointer.md)  
 <span data-ttu-id="6a0e4-216">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-216">Deprecated.</span></span> <span data-ttu-id="6a0e4-217">Bir cihaza çakışan (yani zaman uyumsuz) g/ç tamamlandığında konağa bildiren bir işleve işaret eder.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-217">Points to a function that notifies the host when an overlapped (that is, asynchronous) I/O to a device has completed.</span></span>  
  
 [<span data-ttu-id="6a0e4-218">LPTHREAD_START_ROUTINE İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="6a0e4-218">LPTHREAD_START_ROUTINE Function Pointer</span></span>](lpthread-start-routine-function-pointer.md)  
 <span data-ttu-id="6a0e4-219">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-219">Deprecated.</span></span> <span data-ttu-id="6a0e4-220">Bir iş parçacığının yürütülmeye başlatıldığını konağa bildiren bir işleve işaret eder.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-220">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 [<span data-ttu-id="6a0e4-221">RunDll32ShimW İşlevi</span><span class="sxs-lookup"><span data-stu-id="6a0e4-221">RunDll32ShimW Function</span></span>](rundll32shimw-function.md)  
 <span data-ttu-id="6a0e4-222">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-222">Deprecated.</span></span> <span data-ttu-id="6a0e4-223">Belirtilen komutu yürütür.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-223">Executes the specified command.</span></span>  
  
 [<span data-ttu-id="6a0e4-224">WAITORTIMERCALLBACK İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="6a0e4-224">WAITORTIMERCALLBACK Function Pointer</span></span>](waitortimercallback-function-pointer.md)  
 <span data-ttu-id="6a0e4-225">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-225">Deprecated.</span></span> <span data-ttu-id="6a0e4-226">Ana bilgisayarı bir bekleme tutamacının sinyal ettiğini veya zaman aşımına uğradığını bildiren bir işleve işaret eder.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-226">Points to a function that notifies the host that a wait handle has either been signaled or timed out.</span></span>  
  
## <a name="infrastructure-functions"></a><span data-ttu-id="6a0e4-227">Altyapı işlevleri</span><span class="sxs-lookup"><span data-stu-id="6a0e4-227">Infrastructure functions</span></span>  

 <span data-ttu-id="6a0e4-228">Bu bölümdeki işlevler yalnızca .NET Framework tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-228">The functions in this section are for use by the .NET Framework only.</span></span>  
  
 [<span data-ttu-id="6a0e4-229">_CorDllMain İşlevi</span><span class="sxs-lookup"><span data-stu-id="6a0e4-229">_CorDllMain Function</span></span>](cordllmain-function.md)  
 <span data-ttu-id="6a0e4-230">CLR 'yi başlatır, DLL derlemesinin CLR üst bilgisinde yönetilen giriş noktasını bulur ve yürütmeyi başlatır.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-230">Initializes the CLR, locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
 [<span data-ttu-id="6a0e4-231">_CorExeMain İşlevi</span><span class="sxs-lookup"><span data-stu-id="6a0e4-231">_CorExeMain Function</span></span>](corexemain-function.md)  
 <span data-ttu-id="6a0e4-232">CLR 'yi başlatır, çalıştırılabilir derlemenin CLR üst bilgisinde yönetilen giriş noktasını bulur ve yürütmeyi başlatır.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-232">Initializes the CLR, locates the managed entry point in the executable assembly's CLR header, and begins execution.</span></span>  
  
 [<span data-ttu-id="6a0e4-233">_CorExeMain2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="6a0e4-233">_CorExeMain2 Function</span></span>](corexemain2-function.md)  
 <span data-ttu-id="6a0e4-234">Giriş noktasını belirtilen bellek eşlemeli kodda yürütür.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-234">Executes the entry point in the specified memory-mapped code.</span></span> <span data-ttu-id="6a0e4-235">Bu işlev, işletim sistemi yükleyicisi tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-235">This function is called by the operating system loader.</span></span>  
  
 [<span data-ttu-id="6a0e4-236">_CorImageUnloading İşlevi</span><span class="sxs-lookup"><span data-stu-id="6a0e4-236">_CorImageUnloading Function</span></span>](corimageunloading-function.md)  
 <span data-ttu-id="6a0e4-237">Yönetilen modül görüntüleri kaldırıldığında yükleyiciyi bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-237">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 [<span data-ttu-id="6a0e4-238">_CorValidateImage İşlevi</span><span class="sxs-lookup"><span data-stu-id="6a0e4-238">_CorValidateImage Function</span></span>](corvalidateimage-function.md)  
 <span data-ttu-id="6a0e4-239">Yönetilen modül görüntülerini doğrular ve yüklendikten sonra işletim sistemi yükleyicisini bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-239">Validates managed module images, and notifies the operating system loader after they have been loaded.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a0e4-240">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a0e4-240">See also</span></span>

- [<span data-ttu-id="6a0e4-241">.NET Framework 4 Barındırma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="6a0e4-241">.NET Framework 4 Hosting Global Static Functions</span></span>](net-framework-4-hosting-global-static-functions.md)
