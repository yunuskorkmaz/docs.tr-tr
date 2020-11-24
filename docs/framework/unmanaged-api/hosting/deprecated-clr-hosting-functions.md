---
title: Kullanım Dışı CLR Barındırma İşlevleri
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 1.1, hosting global static functions
- global static functions [.NET Framework hosting], version 2.0
- .NET Framework 2.0, hosting global static functions
- hosting global static functions [.NET Framework], version 2.0
ms.assetid: 91fbbb35-e543-4814-b806-371cebae8c5a
ms.openlocfilehash: 9e19502672973f292991b72c7ea9b4fdc17f5707
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673130"
---
# <a name="deprecated-clr-hosting-functions"></a><span data-ttu-id="50fe5-102">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="50fe5-102">Deprecated CLR Hosting Functions</span></span>

<span data-ttu-id="50fe5-103">Bu bölümde, barındırma API 'sinin önceki sürümlerinin kullanıldığı yönetilmeyen genel statik işlevler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="50fe5-103">This section describes the unmanaged global static functions that earlier versions of the hosting API used.</span></span>  
  
 <span data-ttu-id="50fe5-104">`_Cor*`Yalnızca .NET Framework tarafından kullanılan altyapı işlevleri (işlevler) dışında, bu işlevler .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="50fe5-104">With the exception of the infrastructure functions (`_Cor*` functions), which are used only by the .NET Framework, these functions have been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="activation-functions"></a><span data-ttu-id="50fe5-105">Etkinleştirme işlevleri</span><span class="sxs-lookup"><span data-stu-id="50fe5-105">Activation functions</span></span>  

 [<span data-ttu-id="50fe5-106">ClrCreateManagedInstance İşlevi</span><span class="sxs-lookup"><span data-stu-id="50fe5-106">ClrCreateManagedInstance Function</span></span>](clrcreatemanagedinstance-function.md)  
 <span data-ttu-id="50fe5-107">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="50fe5-107">Deprecated.</span></span> <span data-ttu-id="50fe5-108">Belirtilen yönetilen türün bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="50fe5-108">Creates an instance of the specified managed type.</span></span>  
  
 [<span data-ttu-id="50fe5-109">CoInitializeCor İşlevi</span><span class="sxs-lookup"><span data-stu-id="50fe5-109">CoInitializeCor Function</span></span>](coinitializecor-function.md)  
 <span data-ttu-id="50fe5-110">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="50fe5-110">Obsolete.</span></span> <span data-ttu-id="50fe5-111">Ortak dil çalışma zamanını (CLR) başlatmak için [CorBindToRuntimeEx](corbindtoruntimeex-function.md) veya [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md)kullanın.</span><span class="sxs-lookup"><span data-stu-id="50fe5-111">To initialize the common language runtime (CLR), use either [CorBindToRuntimeEx](corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span></span>  
  
 [<span data-ttu-id="50fe5-112">CoInitializeEE İşlevi</span><span class="sxs-lookup"><span data-stu-id="50fe5-112">CoInitializeEE Function</span></span>](coinitializeee-function.md)  
 <span data-ttu-id="50fe5-113">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="50fe5-113">Deprecated.</span></span> <span data-ttu-id="50fe5-114">CLR yürütme altyapısının bir işleme yüklenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="50fe5-114">Ensures that the CLR execution engine is loaded into a process.</span></span> <span data-ttu-id="50fe5-115">Bunun yerine [ICLRRuntimeHost:: Start](iclrruntimehost-start-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="50fe5-115">Use the [ICLRRuntimeHost::Start](iclrruntimehost-start-method.md) method instead.</span></span>  
  
 [<span data-ttu-id="50fe5-116">CorBindToCurrentRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="50fe5-116">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)  
 <span data-ttu-id="50fe5-117">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="50fe5-117">Deprecated.</span></span> <span data-ttu-id="50fe5-118">Bir XML dosyasında depolanan sürüm bilgilerini kullanarak ortak dil çalışma zamanını (CLR) bir işleme yükler.</span><span class="sxs-lookup"><span data-stu-id="50fe5-118">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span>  
  
 [<span data-ttu-id="50fe5-119">CorBindToRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="50fe5-119">CorBindToRuntime Function</span></span>](corbindtoruntime-function.md)  
 <span data-ttu-id="50fe5-120">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="50fe5-120">Deprecated.</span></span> <span data-ttu-id="50fe5-121">Yönetilmeyen ana bilgisayarların CLR 'yi bir işleme yüklemesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="50fe5-121">Enables unmanaged hosts to load the CLR into a process.</span></span>  
  
 [<span data-ttu-id="50fe5-122">CorBindToRuntimeByCfg İşlevi</span><span class="sxs-lookup"><span data-stu-id="50fe5-122">CorBindToRuntimeByCfg Function</span></span>](corbindtoruntimebycfg-function.md)  
 <span data-ttu-id="50fe5-123">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="50fe5-123">Deprecated.</span></span> <span data-ttu-id="50fe5-124">XML dosyasından okunan sürüm bilgilerini kullanarak CLR 'yi bir işleme yükler.</span><span class="sxs-lookup"><span data-stu-id="50fe5-124">Loads the CLR into a process by using version information that is read from an XML file.</span></span>  
  
 [<span data-ttu-id="50fe5-125">CorBindToRuntimeEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="50fe5-125">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)  
 <span data-ttu-id="50fe5-126">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="50fe5-126">Deprecated.</span></span> <span data-ttu-id="50fe5-127">Yönetilmeyen ana bilgisayarların CLR 'yi bir işleme yüklemesine olanak tanır ve CLR 'nin davranışını belirtmek için bayraklar ayarlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="50fe5-127">Enables unmanaged hosts to load the CLR into a process, and allows you to set flags to specify the behavior of the CLR.</span></span>  
  
 [<span data-ttu-id="50fe5-128">CorBindToRuntimeHost İşlevi</span><span class="sxs-lookup"><span data-stu-id="50fe5-128">CorBindToRuntimeHost Function</span></span>](corbindtoruntimehost-function.md)  
 <span data-ttu-id="50fe5-129">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="50fe5-129">Deprecated.</span></span> <span data-ttu-id="50fe5-130">Ana bilgisayarların belirli bir CLR sürümünü bir işleme yüklemesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="50fe5-130">Enables hosts to load a specified version of the CLR into a process.</span></span>  
  
 [<span data-ttu-id="50fe5-131">GetCORRequiredVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="50fe5-131">GetCORRequiredVersion Function</span></span>](getcorrequiredversion-function.md)  
 <span data-ttu-id="50fe5-132">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="50fe5-132">Deprecated.</span></span> <span data-ttu-id="50fe5-133">Gereken CLR sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="50fe5-133">Gets the required CLR version number.</span></span>  
  
 [<span data-ttu-id="50fe5-134">GetCORSystemDirectory İşlevi</span><span class="sxs-lookup"><span data-stu-id="50fe5-134">GetCORSystemDirectory Function</span></span>](getcorsystemdirectory-function.md)  
 <span data-ttu-id="50fe5-135">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="50fe5-135">Deprecated.</span></span> <span data-ttu-id="50fe5-136">İşleme yüklenen CLR 'nin yükleme dizinini döndürür.</span><span class="sxs-lookup"><span data-stu-id="50fe5-136">Returns the installation directory of the CLR that is loaded into the process.</span></span>  
  
 [<span data-ttu-id="50fe5-137">GetRealProcAddress İşlevi</span><span class="sxs-lookup"><span data-stu-id="50fe5-137">GetRealProcAddress Function</span></span>](getrealprocaddress-function.md)  
 <span data-ttu-id="50fe5-138">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="50fe5-138">Deprecated.</span></span> <span data-ttu-id="50fe5-139">CLR 'nin en son yüklenen sürümünden aktarılmış olan belirtilen işlevin adresini alır.</span><span class="sxs-lookup"><span data-stu-id="50fe5-139">Gets the address of the specified function that is exported from the latest installed version of the CLR.</span></span>  
  
 [<span data-ttu-id="50fe5-140">GetRequestedRuntimeInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="50fe5-140">GetRequestedRuntimeInfo Function</span></span>](getrequestedruntimeinfo-function.md)  
 <span data-ttu-id="50fe5-141">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="50fe5-141">Deprecated.</span></span> <span data-ttu-id="50fe5-142">Bir uygulama tarafından istenen CLR ile ilgili sürüm ve dizin bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="50fe5-142">Gets version and directory information about the CLR requested by an application.</span></span>  
  
## <a name="clr-version-functions"></a><span data-ttu-id="50fe5-143">CLR sürüm işlevleri</span><span class="sxs-lookup"><span data-stu-id="50fe5-143">CLR version functions</span></span>  

 <span data-ttu-id="50fe5-144">Bu bölümdeki işlevler bir CLR sürümü döndürür; CLR 'yi etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="50fe5-144">The functions in this section return a CLR version; they do not activate the CLR.</span></span>  
  
 [<span data-ttu-id="50fe5-145">GetCORVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="50fe5-145">GetCORVersion Function</span></span>](getcorversion-function.md)  
 <span data-ttu-id="50fe5-146">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="50fe5-146">Deprecated.</span></span> <span data-ttu-id="50fe5-147">Geçerli işlemde çalışan CLR 'nin sürüm numarasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="50fe5-147">Returns the version number of the CLR that is running in the current process.</span></span>  
  
 [<span data-ttu-id="50fe5-148">GetFileVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="50fe5-148">GetFileVersion Function</span></span>](getfileversion-function.md)  
 <span data-ttu-id="50fe5-149">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="50fe5-149">Deprecated.</span></span> <span data-ttu-id="50fe5-150">Belirtilen arabelleği kullanarak belirtilen dosyanın CLR sürüm bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="50fe5-150">Gets the CLR version information of the specified file, using the specified buffer.</span></span>  
  
 [<span data-ttu-id="50fe5-151">GetRequestedRuntimeVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="50fe5-151">GetRequestedRuntimeVersion Function</span></span>](getrequestedruntimeversion-function.md)  
 <span data-ttu-id="50fe5-152">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="50fe5-152">Deprecated.</span></span> <span data-ttu-id="50fe5-153">Belirtilen uygulama tarafından istenen CLR 'nin sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="50fe5-153">Gets the version number of the CLR requested by the specified application.</span></span> <span data-ttu-id="50fe5-154">Bu sürüm yüklü değilse, istenen sürümden önce yüklenen en son sürümü alır.</span><span class="sxs-lookup"><span data-stu-id="50fe5-154">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 [<span data-ttu-id="50fe5-155">GetRequestedRuntimeVersionForCLSID İşlevi</span><span class="sxs-lookup"><span data-stu-id="50fe5-155">GetRequestedRuntimeVersionForCLSID Function</span></span>](getrequestedruntimeversionforclsid-function.md)  
 <span data-ttu-id="50fe5-156">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="50fe5-156">Deprecated.</span></span> <span data-ttu-id="50fe5-157">Belirtilen CLSID ile sınıf için uygun CLR sürüm bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="50fe5-157">Gets the appropriate CLR version information for the class with the specified CLSID.</span></span>  
  
 [<span data-ttu-id="50fe5-158">GetVersionFromProcess İşlevi</span><span class="sxs-lookup"><span data-stu-id="50fe5-158">GetVersionFromProcess Function</span></span>](getversionfromprocess-function.md)  
 <span data-ttu-id="50fe5-159">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="50fe5-159">Deprecated.</span></span> <span data-ttu-id="50fe5-160">Belirtilen işlem tanıtıcısından ilişkilendirilen CLR 'nin sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="50fe5-160">Gets the version number of the CLR that is associated with the specified process handle.</span></span>  
  
 [<span data-ttu-id="50fe5-161">LockClrVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="50fe5-161">LockClrVersion Function</span></span>](lockclrversion-function.md)  
 <span data-ttu-id="50fe5-162">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="50fe5-162">Deprecated.</span></span> <span data-ttu-id="50fe5-163">Konağın clr 'yi açıkça başlatmadan önce işlem içinde hangi CLR sürümünün kullanılacağını belirlemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="50fe5-163">Allows the host to determine which version of the CLR will be used within the process before explicitly initializing the CLR.</span></span>  
  
## <a name="hosting-functions"></a><span data-ttu-id="50fe5-164">Barındırma işlevleri</span><span class="sxs-lookup"><span data-stu-id="50fe5-164">Hosting functions</span></span>  

 [<span data-ttu-id="50fe5-165">CallFunctionShim İşlevi</span><span class="sxs-lookup"><span data-stu-id="50fe5-165">CallFunctionShim Function</span></span>](callfunctionshim-function.md)  
 <span data-ttu-id="50fe5-166">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="50fe5-166">Deprecated.</span></span> <span data-ttu-id="50fe5-167">Belirtilen kitaplıkta belirtilen ad ve parametrelere sahip işleve bir çağrı yapar.</span><span class="sxs-lookup"><span data-stu-id="50fe5-167">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 [<span data-ttu-id="50fe5-168">CoEEShutDownCOM İşlevi</span><span class="sxs-lookup"><span data-stu-id="50fe5-168">CoEEShutDownCOM Function</span></span>](coeeshutdowncom-function.md)  
 <span data-ttu-id="50fe5-169">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="50fe5-169">Deprecated.</span></span> <span data-ttu-id="50fe5-170">İşlemden bir COM derlemesini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="50fe5-170">Unloads a COM assembly from the process.</span></span>  
  
 [<span data-ttu-id="50fe5-171">CorExitProcess İşlevi</span><span class="sxs-lookup"><span data-stu-id="50fe5-171">CorExitProcess Function</span></span>](corexitprocess-function.md)  
 <span data-ttu-id="50fe5-172">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="50fe5-172">Deprecated.</span></span> <span data-ttu-id="50fe5-173">Geçerli yönetilmeyen işlemi kapatır.</span><span class="sxs-lookup"><span data-stu-id="50fe5-173">Shuts down the current unmanaged process.</span></span>  
  
 [<span data-ttu-id="50fe5-174">CorLaunchApplication İşlevi</span><span class="sxs-lookup"><span data-stu-id="50fe5-174">CorLaunchApplication Function</span></span>](corlaunchapplication-function.md)  
 <span data-ttu-id="50fe5-175">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="50fe5-175">Deprecated.</span></span> <span data-ttu-id="50fe5-176">Belirtilen bildirimleri ve diğer uygulama verilerini kullanarak belirtilen ağ yolundaki uygulamayı başlatır.</span><span class="sxs-lookup"><span data-stu-id="50fe5-176">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 [<span data-ttu-id="50fe5-177">CorMarkThreadInThreadPool İşlevi</span><span class="sxs-lookup"><span data-stu-id="50fe5-177">CorMarkThreadInThreadPool Function</span></span>](cormarkthreadinthreadpool-function.md)  
 <span data-ttu-id="50fe5-178">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="50fe5-178">Deprecated.</span></span> <span data-ttu-id="50fe5-179">Yönetilen kodun yürütülmesi için şu anda yürütülmekte olan iş parçacığı havuzu iş parçacığını işaretler.</span><span class="sxs-lookup"><span data-stu-id="50fe5-179">Marks the currently executing thread-pool thread for the execution of managed code.</span></span> <span data-ttu-id="50fe5-180">.NET Framework sürüm 2,0 ' den başlayarak, bu işlevin etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="50fe5-180">Starting with the .NET Framework version 2.0, this function has no effect.</span></span> <span data-ttu-id="50fe5-181">Gerekli değildir ve kodınızdan kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="50fe5-181">It is not required, and can be removed from your code.</span></span>  
  
 [<span data-ttu-id="50fe5-182">CoUninitializeCor İşlevi</span><span class="sxs-lookup"><span data-stu-id="50fe5-182">CoUninitializeCor Function</span></span>](couninitializecor-function.md)  
 <span data-ttu-id="50fe5-183">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="50fe5-183">Obsolete.</span></span> <span data-ttu-id="50fe5-184">CLR bir işlemden kaldırılamıyor.</span><span class="sxs-lookup"><span data-stu-id="50fe5-184">The CLR cannot be unloaded from a process.</span></span>  
  
 [<span data-ttu-id="50fe5-185">CoUninitializeEE İşlevi</span><span class="sxs-lookup"><span data-stu-id="50fe5-185">CoUninitializeEE Function</span></span>](couninitializeee-function.md)  
 <span data-ttu-id="50fe5-186">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="50fe5-186">Obsolete.</span></span>  
  
 [<span data-ttu-id="50fe5-187">CreateDebuggingInterfaceFromVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="50fe5-187">CreateDebuggingInterfaceFromVersion Function</span></span>](createdebugginginterfacefromversion-function.md)  
 <span data-ttu-id="50fe5-188">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="50fe5-188">Deprecated.</span></span> <span data-ttu-id="50fe5-189">Belirtilen sürüm bilgilerini temel alan bir [ICorDebug](../debugging/icordebug-interface.md) nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="50fe5-189">Creates an [ICorDebug](../debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 [<span data-ttu-id="50fe5-190">CreateICeeFileGen İşlevi</span><span class="sxs-lookup"><span data-stu-id="50fe5-190">CreateICeeFileGen Function</span></span>](createiceefilegen-function.md)  
 <span data-ttu-id="50fe5-191">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="50fe5-191">Deprecated.</span></span> <span data-ttu-id="50fe5-192">Bir [ICeeFileGen](iceefilegen-class.md) nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="50fe5-192">Creates an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 [<span data-ttu-id="50fe5-193">DestroyICeeFileGen İşlevi</span><span class="sxs-lookup"><span data-stu-id="50fe5-193">DestroyICeeFileGen Function</span></span>](destroyiceefilegen-function.md)  
 <span data-ttu-id="50fe5-194">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="50fe5-194">Deprecated.</span></span> <span data-ttu-id="50fe5-195">Bir [ICeeFileGen](iceefilegen-class.md) nesnesini yok eder.</span><span class="sxs-lookup"><span data-stu-id="50fe5-195">Destroys an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 [<span data-ttu-id="50fe5-196">FExecuteInAppDomainCallback İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="50fe5-196">FExecuteInAppDomainCallback Function Pointer</span></span>](fexecuteinappdomaincallback-function-pointer.md)  
 <span data-ttu-id="50fe5-197">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="50fe5-197">Deprecated.</span></span> <span data-ttu-id="50fe5-198">CLR 'nin yönetilen kodu yürütmek için çağırdığı bir işleve işaret eder.</span><span class="sxs-lookup"><span data-stu-id="50fe5-198">Points to a function that the CLR calls to execute managed code.</span></span>  
  
 [<span data-ttu-id="50fe5-199">FLockClrVersionCallback İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="50fe5-199">FLockClrVersionCallback Function Pointer</span></span>](flockclrversioncallback-function-pointer.md)  
 <span data-ttu-id="50fe5-200">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="50fe5-200">Deprecated.</span></span> <span data-ttu-id="50fe5-201">CLR 'nin, başlatmanın başlatıldığını ya da tamamlandığını bildirmek için çağırdığı bir işleve işaret eder.</span><span class="sxs-lookup"><span data-stu-id="50fe5-201">Points to a function that the CLR calls to notify the host that initialization has either started or completed.</span></span>  
  
 [<span data-ttu-id="50fe5-202">GetCLRIdentityManager İşlevi</span><span class="sxs-lookup"><span data-stu-id="50fe5-202">GetCLRIdentityManager Function</span></span>](getclridentitymanager-function.md)  
 <span data-ttu-id="50fe5-203">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="50fe5-203">Deprecated.</span></span> <span data-ttu-id="50fe5-204">CLR 'nin kimlikleri yönetmesine izin veren bir arabirime yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="50fe5-204">Gets a pointer to an interface that allows the CLR to manage identities.</span></span>  
  
 [<span data-ttu-id="50fe5-205">LoadLibraryShim İşlevi</span><span class="sxs-lookup"><span data-stu-id="50fe5-205">LoadLibraryShim Function</span></span>](loadlibraryshim-function.md)  
 <span data-ttu-id="50fe5-206">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="50fe5-206">Deprecated.</span></span> <span data-ttu-id="50fe5-207">.NET Framework DLL 'nin belirtilen bir sürümünü yükler.</span><span class="sxs-lookup"><span data-stu-id="50fe5-207">Loads a specified version of a .NET Framework DLL.</span></span>  
  
 [<span data-ttu-id="50fe5-208">LoadStringRC İşlevi</span><span class="sxs-lookup"><span data-stu-id="50fe5-208">LoadStringRC Function</span></span>](loadstringrc-function.md)  
 <span data-ttu-id="50fe5-209">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="50fe5-209">Deprecated.</span></span> <span data-ttu-id="50fe5-210">Geçerli iş parçacığının varsayılan kültürünü kullanarak bir HRESULT değerini bir hata iletisine çevirir.</span><span class="sxs-lookup"><span data-stu-id="50fe5-210">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 [<span data-ttu-id="50fe5-211">LoadStringRCEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="50fe5-211">LoadStringRCEx Function</span></span>](loadstringrcex-function.md)  
 <span data-ttu-id="50fe5-212">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="50fe5-212">Deprecated.</span></span> <span data-ttu-id="50fe5-213">Belirtilen kültür için bir HRESULT değerini uygun bir hata iletisine çevirir.</span><span class="sxs-lookup"><span data-stu-id="50fe5-213">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 [<span data-ttu-id="50fe5-214">LPOVERLAPPED_COMPLETION_ROUTINE İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="50fe5-214">LPOVERLAPPED_COMPLETION_ROUTINE Function Pointer</span></span>](lpoverlapped-completion-routine-function-pointer.md)  
 <span data-ttu-id="50fe5-215">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="50fe5-215">Deprecated.</span></span> <span data-ttu-id="50fe5-216">Bir cihaza çakışan (yani zaman uyumsuz) g/ç tamamlandığında konağa bildiren bir işleve işaret eder.</span><span class="sxs-lookup"><span data-stu-id="50fe5-216">Points to a function that notifies the host when an overlapped (that is, asynchronous) I/O to a device has completed.</span></span>  
  
 [<span data-ttu-id="50fe5-217">LPTHREAD_START_ROUTINE İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="50fe5-217">LPTHREAD_START_ROUTINE Function Pointer</span></span>](lpthread-start-routine-function-pointer.md)  
 <span data-ttu-id="50fe5-218">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="50fe5-218">Deprecated.</span></span> <span data-ttu-id="50fe5-219">Bir iş parçacığının yürütülmeye başlatıldığını konağa bildiren bir işleve işaret eder.</span><span class="sxs-lookup"><span data-stu-id="50fe5-219">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 [<span data-ttu-id="50fe5-220">RunDll32ShimW İşlevi</span><span class="sxs-lookup"><span data-stu-id="50fe5-220">RunDll32ShimW Function</span></span>](rundll32shimw-function.md)  
 <span data-ttu-id="50fe5-221">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="50fe5-221">Deprecated.</span></span> <span data-ttu-id="50fe5-222">Belirtilen komutu yürütür.</span><span class="sxs-lookup"><span data-stu-id="50fe5-222">Executes the specified command.</span></span>  
  
 [<span data-ttu-id="50fe5-223">WAITORTIMERCALLBACK İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="50fe5-223">WAITORTIMERCALLBACK Function Pointer</span></span>](waitortimercallback-function-pointer.md)  
 <span data-ttu-id="50fe5-224">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="50fe5-224">Deprecated.</span></span> <span data-ttu-id="50fe5-225">Ana bilgisayarı bir bekleme tutamacının sinyal ettiğini veya zaman aşımına uğradığını bildiren bir işleve işaret eder.</span><span class="sxs-lookup"><span data-stu-id="50fe5-225">Points to a function that notifies the host that a wait handle has either been signaled or timed out.</span></span>  
  
## <a name="infrastructure-functions"></a><span data-ttu-id="50fe5-226">Altyapı işlevleri</span><span class="sxs-lookup"><span data-stu-id="50fe5-226">Infrastructure functions</span></span>  

 <span data-ttu-id="50fe5-227">Bu bölümdeki işlevler yalnızca .NET Framework tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="50fe5-227">The functions in this section are for use by the .NET Framework only.</span></span>  
  
 [<span data-ttu-id="50fe5-228">_CorDllMain İşlevi</span><span class="sxs-lookup"><span data-stu-id="50fe5-228">_CorDllMain Function</span></span>](cordllmain-function.md)  
 <span data-ttu-id="50fe5-229">CLR 'yi başlatır, DLL derlemesinin CLR üst bilgisinde yönetilen giriş noktasını bulur ve yürütmeyi başlatır.</span><span class="sxs-lookup"><span data-stu-id="50fe5-229">Initializes the CLR, locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
 [<span data-ttu-id="50fe5-230">_CorExeMain İşlevi</span><span class="sxs-lookup"><span data-stu-id="50fe5-230">_CorExeMain Function</span></span>](corexemain-function.md)  
 <span data-ttu-id="50fe5-231">CLR 'yi başlatır, çalıştırılabilir derlemenin CLR üst bilgisinde yönetilen giriş noktasını bulur ve yürütmeyi başlatır.</span><span class="sxs-lookup"><span data-stu-id="50fe5-231">Initializes the CLR, locates the managed entry point in the executable assembly's CLR header, and begins execution.</span></span>  
  
 [<span data-ttu-id="50fe5-232">_CorExeMain2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="50fe5-232">_CorExeMain2 Function</span></span>](corexemain2-function.md)  
 <span data-ttu-id="50fe5-233">Giriş noktasını belirtilen bellek eşlemeli kodda yürütür.</span><span class="sxs-lookup"><span data-stu-id="50fe5-233">Executes the entry point in the specified memory-mapped code.</span></span> <span data-ttu-id="50fe5-234">Bu işlev, işletim sistemi yükleyicisi tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="50fe5-234">This function is called by the operating system loader.</span></span>  
  
 [<span data-ttu-id="50fe5-235">_CorImageUnloading İşlevi</span><span class="sxs-lookup"><span data-stu-id="50fe5-235">_CorImageUnloading Function</span></span>](corimageunloading-function.md)  
 <span data-ttu-id="50fe5-236">Yönetilen modül görüntüleri kaldırıldığında yükleyiciyi bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="50fe5-236">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 [<span data-ttu-id="50fe5-237">_CorValidateImage İşlevi</span><span class="sxs-lookup"><span data-stu-id="50fe5-237">_CorValidateImage Function</span></span>](corvalidateimage-function.md)  
 <span data-ttu-id="50fe5-238">Yönetilen modül görüntülerini doğrular ve yüklendikten sonra işletim sistemi yükleyicisini bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="50fe5-238">Validates managed module images, and notifies the operating system loader after they have been loaded.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50fe5-239">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50fe5-239">See also</span></span>

- [<span data-ttu-id="50fe5-240">.NET Framework 4 Barındırma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="50fe5-240">.NET Framework 4 Hosting Global Static Functions</span></span>](net-framework-4-hosting-global-static-functions.md)
