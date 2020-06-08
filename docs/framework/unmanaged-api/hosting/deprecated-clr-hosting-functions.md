---
title: Kullanım Dışı CLR Barındırma İşlevleri
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 1.1, hosting global static functions
- global static functions [.NET Framework hosting], version 2.0
- .NET Framework 2.0, hosting global static functions
- hosting global static functions [.NET Framework], version 2.0
ms.assetid: 91fbbb35-e543-4814-b806-371cebae8c5a
ms.openlocfilehash: 083d0ff285abb4a99ad05c791bc504ff7f282c6a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504374"
---
# <a name="deprecated-clr-hosting-functions"></a><span data-ttu-id="083e3-102">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="083e3-102">Deprecated CLR Hosting Functions</span></span>
<span data-ttu-id="083e3-103">Bu bölümde, barındırma API 'sinin önceki sürümlerinin kullanıldığı yönetilmeyen genel statik işlevler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="083e3-103">This section describes the unmanaged global static functions that earlier versions of the hosting API used.</span></span>  
  
 <span data-ttu-id="083e3-104">`_Cor*`Yalnızca .NET Framework tarafından kullanılan altyapı işlevleri (işlevler) dışında, bu işlevler .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="083e3-104">With the exception of the infrastructure functions (`_Cor*` functions), which are used only by the .NET Framework, these functions have been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="activation-functions"></a><span data-ttu-id="083e3-105">Etkinleştirme işlevleri</span><span class="sxs-lookup"><span data-stu-id="083e3-105">Activation functions</span></span>  
 [<span data-ttu-id="083e3-106">ClrCreateManagedInstance İşlevi</span><span class="sxs-lookup"><span data-stu-id="083e3-106">ClrCreateManagedInstance Function</span></span>](clrcreatemanagedinstance-function.md)  
 <span data-ttu-id="083e3-107">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="083e3-107">Deprecated.</span></span> <span data-ttu-id="083e3-108">Belirtilen yönetilen türün bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="083e3-108">Creates an instance of the specified managed type.</span></span>  
  
 [<span data-ttu-id="083e3-109">CoInitializeCor İşlevi</span><span class="sxs-lookup"><span data-stu-id="083e3-109">CoInitializeCor Function</span></span>](coinitializecor-function.md)  
 <span data-ttu-id="083e3-110">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="083e3-110">Obsolete.</span></span> <span data-ttu-id="083e3-111">Ortak dil çalışma zamanını (CLR) başlatmak için [CorBindToRuntimeEx](corbindtoruntimeex-function.md) veya [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md)kullanın.</span><span class="sxs-lookup"><span data-stu-id="083e3-111">To initialize the common language runtime (CLR), use either [CorBindToRuntimeEx](corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span></span>  
  
 [<span data-ttu-id="083e3-112">CoInitializeEE İşlevi</span><span class="sxs-lookup"><span data-stu-id="083e3-112">CoInitializeEE Function</span></span>](coinitializeee-function.md)  
 <span data-ttu-id="083e3-113">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="083e3-113">Deprecated.</span></span> <span data-ttu-id="083e3-114">CLR yürütme altyapısının bir işleme yüklenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="083e3-114">Ensures that the CLR execution engine is loaded into a process.</span></span> <span data-ttu-id="083e3-115">Bunun yerine [ICLRRuntimeHost:: Start](iclrruntimehost-start-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="083e3-115">Use the [ICLRRuntimeHost::Start](iclrruntimehost-start-method.md) method instead.</span></span>  
  
 [<span data-ttu-id="083e3-116">CorBindToCurrentRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="083e3-116">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)  
 <span data-ttu-id="083e3-117">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="083e3-117">Deprecated.</span></span> <span data-ttu-id="083e3-118">Bir XML dosyasında depolanan sürüm bilgilerini kullanarak ortak dil çalışma zamanını (CLR) bir işleme yükler.</span><span class="sxs-lookup"><span data-stu-id="083e3-118">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span>  
  
 [<span data-ttu-id="083e3-119">CorBindToRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="083e3-119">CorBindToRuntime Function</span></span>](corbindtoruntime-function.md)  
 <span data-ttu-id="083e3-120">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="083e3-120">Deprecated.</span></span> <span data-ttu-id="083e3-121">Yönetilmeyen ana bilgisayarların CLR 'yi bir işleme yüklemesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="083e3-121">Enables unmanaged hosts to load the CLR into a process.</span></span>  
  
 [<span data-ttu-id="083e3-122">CorBindToRuntimeByCfg İşlevi</span><span class="sxs-lookup"><span data-stu-id="083e3-122">CorBindToRuntimeByCfg Function</span></span>](corbindtoruntimebycfg-function.md)  
 <span data-ttu-id="083e3-123">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="083e3-123">Deprecated.</span></span> <span data-ttu-id="083e3-124">XML dosyasından okunan sürüm bilgilerini kullanarak CLR 'yi bir işleme yükler.</span><span class="sxs-lookup"><span data-stu-id="083e3-124">Loads the CLR into a process by using version information that is read from an XML file.</span></span>  
  
 [<span data-ttu-id="083e3-125">CorBindToRuntimeEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="083e3-125">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)  
 <span data-ttu-id="083e3-126">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="083e3-126">Deprecated.</span></span> <span data-ttu-id="083e3-127">Yönetilmeyen ana bilgisayarların CLR 'yi bir işleme yüklemesine olanak tanır ve CLR 'nin davranışını belirtmek için bayraklar ayarlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="083e3-127">Enables unmanaged hosts to load the CLR into a process, and allows you to set flags to specify the behavior of the CLR.</span></span>  
  
 [<span data-ttu-id="083e3-128">CorBindToRuntimeHost İşlevi</span><span class="sxs-lookup"><span data-stu-id="083e3-128">CorBindToRuntimeHost Function</span></span>](corbindtoruntimehost-function.md)  
 <span data-ttu-id="083e3-129">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="083e3-129">Deprecated.</span></span> <span data-ttu-id="083e3-130">Ana bilgisayarların belirli bir CLR sürümünü bir işleme yüklemesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="083e3-130">Enables hosts to load a specified version of the CLR into a process.</span></span>  
  
 [<span data-ttu-id="083e3-131">GetCORRequiredVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="083e3-131">GetCORRequiredVersion Function</span></span>](getcorrequiredversion-function.md)  
 <span data-ttu-id="083e3-132">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="083e3-132">Deprecated.</span></span> <span data-ttu-id="083e3-133">Gereken CLR sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="083e3-133">Gets the required CLR version number.</span></span>  
  
 [<span data-ttu-id="083e3-134">GetCORSystemDirectory İşlevi</span><span class="sxs-lookup"><span data-stu-id="083e3-134">GetCORSystemDirectory Function</span></span>](getcorsystemdirectory-function.md)  
 <span data-ttu-id="083e3-135">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="083e3-135">Deprecated.</span></span> <span data-ttu-id="083e3-136">İşleme yüklenen CLR 'nin yükleme dizinini döndürür.</span><span class="sxs-lookup"><span data-stu-id="083e3-136">Returns the installation directory of the CLR that is loaded into the process.</span></span>  
  
 [<span data-ttu-id="083e3-137">GetRealProcAddress İşlevi</span><span class="sxs-lookup"><span data-stu-id="083e3-137">GetRealProcAddress Function</span></span>](getrealprocaddress-function.md)  
 <span data-ttu-id="083e3-138">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="083e3-138">Deprecated.</span></span> <span data-ttu-id="083e3-139">CLR 'nin en son yüklenen sürümünden aktarılmış olan belirtilen işlevin adresini alır.</span><span class="sxs-lookup"><span data-stu-id="083e3-139">Gets the address of the specified function that is exported from the latest installed version of the CLR.</span></span>  
  
 [<span data-ttu-id="083e3-140">GetRequestedRuntimeInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="083e3-140">GetRequestedRuntimeInfo Function</span></span>](getrequestedruntimeinfo-function.md)  
 <span data-ttu-id="083e3-141">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="083e3-141">Deprecated.</span></span> <span data-ttu-id="083e3-142">Bir uygulama tarafından istenen CLR ile ilgili sürüm ve dizin bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="083e3-142">Gets version and directory information about the CLR requested by an application.</span></span>  
  
## <a name="clr-version-functions"></a><span data-ttu-id="083e3-143">CLR sürüm işlevleri</span><span class="sxs-lookup"><span data-stu-id="083e3-143">CLR version functions</span></span>  
 <span data-ttu-id="083e3-144">Bu bölümdeki işlevler bir CLR sürümü döndürür; CLR 'yi etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="083e3-144">The functions in this section return a CLR version; they do not activate the CLR.</span></span>  
  
 [<span data-ttu-id="083e3-145">GetCORVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="083e3-145">GetCORVersion Function</span></span>](getcorversion-function.md)  
 <span data-ttu-id="083e3-146">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="083e3-146">Deprecated.</span></span> <span data-ttu-id="083e3-147">Geçerli işlemde çalışan CLR 'nin sürüm numarasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="083e3-147">Returns the version number of the CLR that is running in the current process.</span></span>  
  
 [<span data-ttu-id="083e3-148">GetFileVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="083e3-148">GetFileVersion Function</span></span>](getfileversion-function.md)  
 <span data-ttu-id="083e3-149">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="083e3-149">Deprecated.</span></span> <span data-ttu-id="083e3-150">Belirtilen arabelleği kullanarak belirtilen dosyanın CLR sürüm bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="083e3-150">Gets the CLR version information of the specified file, using the specified buffer.</span></span>  
  
 [<span data-ttu-id="083e3-151">GetRequestedRuntimeVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="083e3-151">GetRequestedRuntimeVersion Function</span></span>](getrequestedruntimeversion-function.md)  
 <span data-ttu-id="083e3-152">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="083e3-152">Deprecated.</span></span> <span data-ttu-id="083e3-153">Belirtilen uygulama tarafından istenen CLR 'nin sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="083e3-153">Gets the version number of the CLR requested by the specified application.</span></span> <span data-ttu-id="083e3-154">Bu sürüm yüklü değilse, istenen sürümden önce yüklenen en son sürümü alır.</span><span class="sxs-lookup"><span data-stu-id="083e3-154">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 [<span data-ttu-id="083e3-155">GetRequestedRuntimeVersionForCLSID İşlevi</span><span class="sxs-lookup"><span data-stu-id="083e3-155">GetRequestedRuntimeVersionForCLSID Function</span></span>](getrequestedruntimeversionforclsid-function.md)  
 <span data-ttu-id="083e3-156">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="083e3-156">Deprecated.</span></span> <span data-ttu-id="083e3-157">Belirtilen CLSID ile sınıf için uygun CLR sürüm bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="083e3-157">Gets the appropriate CLR version information for the class with the specified CLSID.</span></span>  
  
 [<span data-ttu-id="083e3-158">GetVersionFromProcess İşlevi</span><span class="sxs-lookup"><span data-stu-id="083e3-158">GetVersionFromProcess Function</span></span>](getversionfromprocess-function.md)  
 <span data-ttu-id="083e3-159">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="083e3-159">Deprecated.</span></span> <span data-ttu-id="083e3-160">Belirtilen işlem tanıtıcısından ilişkilendirilen CLR 'nin sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="083e3-160">Gets the version number of the CLR that is associated with the specified process handle.</span></span>  
  
 [<span data-ttu-id="083e3-161">LockClrVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="083e3-161">LockClrVersion Function</span></span>](lockclrversion-function.md)  
 <span data-ttu-id="083e3-162">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="083e3-162">Deprecated.</span></span> <span data-ttu-id="083e3-163">Konağın clr 'yi açıkça başlatmadan önce işlem içinde hangi CLR sürümünün kullanılacağını belirlemesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="083e3-163">Allows the host to determine which version of the CLR will be used within the process before explicitly initializing the CLR.</span></span>  
  
## <a name="hosting-functions"></a><span data-ttu-id="083e3-164">Barındırma işlevleri</span><span class="sxs-lookup"><span data-stu-id="083e3-164">Hosting functions</span></span>  
 [<span data-ttu-id="083e3-165">CallFunctionShim İşlevi</span><span class="sxs-lookup"><span data-stu-id="083e3-165">CallFunctionShim Function</span></span>](callfunctionshim-function.md)  
 <span data-ttu-id="083e3-166">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="083e3-166">Deprecated.</span></span> <span data-ttu-id="083e3-167">Belirtilen kitaplıkta belirtilen ad ve parametrelere sahip işleve bir çağrı yapar.</span><span class="sxs-lookup"><span data-stu-id="083e3-167">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 [<span data-ttu-id="083e3-168">CoEEShutDownCOM İşlevi</span><span class="sxs-lookup"><span data-stu-id="083e3-168">CoEEShutDownCOM Function</span></span>](coeeshutdowncom-function.md)  
 <span data-ttu-id="083e3-169">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="083e3-169">Deprecated.</span></span> <span data-ttu-id="083e3-170">İşlemden bir COM derlemesini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="083e3-170">Unloads a COM assembly from the process.</span></span>  
  
 [<span data-ttu-id="083e3-171">CorExitProcess İşlevi</span><span class="sxs-lookup"><span data-stu-id="083e3-171">CorExitProcess Function</span></span>](corexitprocess-function.md)  
 <span data-ttu-id="083e3-172">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="083e3-172">Deprecated.</span></span> <span data-ttu-id="083e3-173">Geçerli yönetilmeyen işlemi kapatır.</span><span class="sxs-lookup"><span data-stu-id="083e3-173">Shuts down the current unmanaged process.</span></span>  
  
 [<span data-ttu-id="083e3-174">CorLaunchApplication İşlevi</span><span class="sxs-lookup"><span data-stu-id="083e3-174">CorLaunchApplication Function</span></span>](corlaunchapplication-function.md)  
 <span data-ttu-id="083e3-175">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="083e3-175">Deprecated.</span></span> <span data-ttu-id="083e3-176">Belirtilen bildirimleri ve diğer uygulama verilerini kullanarak belirtilen ağ yolundaki uygulamayı başlatır.</span><span class="sxs-lookup"><span data-stu-id="083e3-176">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 [<span data-ttu-id="083e3-177">CorMarkThreadInThreadPool İşlevi</span><span class="sxs-lookup"><span data-stu-id="083e3-177">CorMarkThreadInThreadPool Function</span></span>](cormarkthreadinthreadpool-function.md)  
 <span data-ttu-id="083e3-178">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="083e3-178">Deprecated.</span></span> <span data-ttu-id="083e3-179">Yönetilen kodun yürütülmesi için şu anda yürütülmekte olan iş parçacığı havuzu iş parçacığını işaretler.</span><span class="sxs-lookup"><span data-stu-id="083e3-179">Marks the currently executing thread-pool thread for the execution of managed code.</span></span> <span data-ttu-id="083e3-180">.NET Framework sürüm 2,0 ' den başlayarak, bu işlevin etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="083e3-180">Starting with the .NET Framework version 2.0, this function has no effect.</span></span> <span data-ttu-id="083e3-181">Gerekli değildir ve kodınızdan kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="083e3-181">It is not required, and can be removed from your code.</span></span>  
  
 [<span data-ttu-id="083e3-182">CoUninitializeCor İşlevi</span><span class="sxs-lookup"><span data-stu-id="083e3-182">CoUninitializeCor Function</span></span>](couninitializecor-function.md)  
 <span data-ttu-id="083e3-183">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="083e3-183">Obsolete.</span></span> <span data-ttu-id="083e3-184">CLR bir işlemden kaldırılamıyor.</span><span class="sxs-lookup"><span data-stu-id="083e3-184">The CLR cannot be unloaded from a process.</span></span>  
  
 [<span data-ttu-id="083e3-185">CoUninitializeEE İşlevi</span><span class="sxs-lookup"><span data-stu-id="083e3-185">CoUninitializeEE Function</span></span>](couninitializeee-function.md)  
 <span data-ttu-id="083e3-186">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="083e3-186">Obsolete.</span></span>  
  
 [<span data-ttu-id="083e3-187">CreateDebuggingInterfaceFromVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="083e3-187">CreateDebuggingInterfaceFromVersion Function</span></span>](createdebugginginterfacefromversion-function.md)  
 <span data-ttu-id="083e3-188">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="083e3-188">Deprecated.</span></span> <span data-ttu-id="083e3-189">Belirtilen sürüm bilgilerini temel alan bir [ICorDebug](../debugging/icordebug-interface.md) nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="083e3-189">Creates an [ICorDebug](../debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 [<span data-ttu-id="083e3-190">CreateICeeFileGen İşlevi</span><span class="sxs-lookup"><span data-stu-id="083e3-190">CreateICeeFileGen Function</span></span>](createiceefilegen-function.md)  
 <span data-ttu-id="083e3-191">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="083e3-191">Deprecated.</span></span> <span data-ttu-id="083e3-192">Bir [ICeeFileGen](iceefilegen-class.md) nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="083e3-192">Creates an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 [<span data-ttu-id="083e3-193">DestroyICeeFileGen İşlevi</span><span class="sxs-lookup"><span data-stu-id="083e3-193">DestroyICeeFileGen Function</span></span>](destroyiceefilegen-function.md)  
 <span data-ttu-id="083e3-194">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="083e3-194">Deprecated.</span></span> <span data-ttu-id="083e3-195">Bir [ICeeFileGen](iceefilegen-class.md) nesnesini yok eder.</span><span class="sxs-lookup"><span data-stu-id="083e3-195">Destroys an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 [<span data-ttu-id="083e3-196">FExecuteInAppDomainCallback İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="083e3-196">FExecuteInAppDomainCallback Function Pointer</span></span>](fexecuteinappdomaincallback-function-pointer.md)  
 <span data-ttu-id="083e3-197">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="083e3-197">Deprecated.</span></span> <span data-ttu-id="083e3-198">CLR 'nin yönetilen kodu yürütmek için çağırdığı bir işleve işaret eder.</span><span class="sxs-lookup"><span data-stu-id="083e3-198">Points to a function that the CLR calls to execute managed code.</span></span>  
  
 [<span data-ttu-id="083e3-199">FLockClrVersionCallback İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="083e3-199">FLockClrVersionCallback Function Pointer</span></span>](flockclrversioncallback-function-pointer.md)  
 <span data-ttu-id="083e3-200">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="083e3-200">Deprecated.</span></span> <span data-ttu-id="083e3-201">CLR 'nin, başlatmanın başlatıldığını ya da tamamlandığını bildirmek için çağırdığı bir işleve işaret eder.</span><span class="sxs-lookup"><span data-stu-id="083e3-201">Points to a function that the CLR calls to notify the host that initialization has either started or completed.</span></span>  
  
 [<span data-ttu-id="083e3-202">GetCLRIdentityManager İşlevi</span><span class="sxs-lookup"><span data-stu-id="083e3-202">GetCLRIdentityManager Function</span></span>](getclridentitymanager-function.md)  
 <span data-ttu-id="083e3-203">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="083e3-203">Deprecated.</span></span> <span data-ttu-id="083e3-204">CLR 'nin kimlikleri yönetmesine izin veren bir arabirime yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="083e3-204">Gets a pointer to an interface that allows the CLR to manage identities.</span></span>  
  
 [<span data-ttu-id="083e3-205">LoadLibraryShim İşlevi</span><span class="sxs-lookup"><span data-stu-id="083e3-205">LoadLibraryShim Function</span></span>](loadlibraryshim-function.md)  
 <span data-ttu-id="083e3-206">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="083e3-206">Deprecated.</span></span> <span data-ttu-id="083e3-207">.NET Framework DLL 'nin belirtilen bir sürümünü yükler.</span><span class="sxs-lookup"><span data-stu-id="083e3-207">Loads a specified version of a .NET Framework DLL.</span></span>  
  
 [<span data-ttu-id="083e3-208">LoadStringRC İşlevi</span><span class="sxs-lookup"><span data-stu-id="083e3-208">LoadStringRC Function</span></span>](loadstringrc-function.md)  
 <span data-ttu-id="083e3-209">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="083e3-209">Deprecated.</span></span> <span data-ttu-id="083e3-210">Geçerli iş parçacığının varsayılan kültürünü kullanarak bir HRESULT değerini bir hata iletisine çevirir.</span><span class="sxs-lookup"><span data-stu-id="083e3-210">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 [<span data-ttu-id="083e3-211">LoadStringRCEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="083e3-211">LoadStringRCEx Function</span></span>](loadstringrcex-function.md)  
 <span data-ttu-id="083e3-212">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="083e3-212">Deprecated.</span></span> <span data-ttu-id="083e3-213">Belirtilen kültür için bir HRESULT değerini uygun bir hata iletisine çevirir.</span><span class="sxs-lookup"><span data-stu-id="083e3-213">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 [<span data-ttu-id="083e3-214">LPOVERLAPPED_COMPLETION_ROUTINE İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="083e3-214">LPOVERLAPPED_COMPLETION_ROUTINE Function Pointer</span></span>](lpoverlapped-completion-routine-function-pointer.md)  
 <span data-ttu-id="083e3-215">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="083e3-215">Deprecated.</span></span> <span data-ttu-id="083e3-216">Bir cihaza çakışan (yani zaman uyumsuz) g/ç tamamlandığında konağa bildiren bir işleve işaret eder.</span><span class="sxs-lookup"><span data-stu-id="083e3-216">Points to a function that notifies the host when an overlapped (that is, asynchronous) I/O to a device has completed.</span></span>  
  
 [<span data-ttu-id="083e3-217">LPTHREAD_START_ROUTINE İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="083e3-217">LPTHREAD_START_ROUTINE Function Pointer</span></span>](lpthread-start-routine-function-pointer.md)  
 <span data-ttu-id="083e3-218">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="083e3-218">Deprecated.</span></span> <span data-ttu-id="083e3-219">Bir iş parçacığının yürütülmeye başlatıldığını konağa bildiren bir işleve işaret eder.</span><span class="sxs-lookup"><span data-stu-id="083e3-219">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 [<span data-ttu-id="083e3-220">RunDll32ShimW İşlevi</span><span class="sxs-lookup"><span data-stu-id="083e3-220">RunDll32ShimW Function</span></span>](rundll32shimw-function.md)  
 <span data-ttu-id="083e3-221">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="083e3-221">Deprecated.</span></span> <span data-ttu-id="083e3-222">Belirtilen komutu yürütür.</span><span class="sxs-lookup"><span data-stu-id="083e3-222">Executes the specified command.</span></span>  
  
 [<span data-ttu-id="083e3-223">WAITORTIMERCALLBACK İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="083e3-223">WAITORTIMERCALLBACK Function Pointer</span></span>](waitortimercallback-function-pointer.md)  
 <span data-ttu-id="083e3-224">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="083e3-224">Deprecated.</span></span> <span data-ttu-id="083e3-225">Ana bilgisayarı bir bekleme tutamacının sinyal ettiğini veya zaman aşımına uğradığını bildiren bir işleve işaret eder.</span><span class="sxs-lookup"><span data-stu-id="083e3-225">Points to a function that notifies the host that a wait handle has either been signaled or timed out.</span></span>  
  
## <a name="infrastructure-functions"></a><span data-ttu-id="083e3-226">Altyapı işlevleri</span><span class="sxs-lookup"><span data-stu-id="083e3-226">Infrastructure functions</span></span>  
 <span data-ttu-id="083e3-227">Bu bölümdeki işlevler yalnızca .NET Framework tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="083e3-227">The functions in this section are for use by the .NET Framework only.</span></span>  
  
 [<span data-ttu-id="083e3-228">_CorDllMain İşlevi</span><span class="sxs-lookup"><span data-stu-id="083e3-228">_CorDllMain Function</span></span>](cordllmain-function.md)  
 <span data-ttu-id="083e3-229">CLR 'yi başlatır, DLL derlemesinin CLR üst bilgisinde yönetilen giriş noktasını bulur ve yürütmeyi başlatır.</span><span class="sxs-lookup"><span data-stu-id="083e3-229">Initializes the CLR, locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
 [<span data-ttu-id="083e3-230">_CorExeMain İşlevi</span><span class="sxs-lookup"><span data-stu-id="083e3-230">_CorExeMain Function</span></span>](corexemain-function.md)  
 <span data-ttu-id="083e3-231">CLR 'yi başlatır, çalıştırılabilir derlemenin CLR üst bilgisinde yönetilen giriş noktasını bulur ve yürütmeyi başlatır.</span><span class="sxs-lookup"><span data-stu-id="083e3-231">Initializes the CLR, locates the managed entry point in the executable assembly's CLR header, and begins execution.</span></span>  
  
 [<span data-ttu-id="083e3-232">_CorExeMain2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="083e3-232">_CorExeMain2 Function</span></span>](corexemain2-function.md)  
 <span data-ttu-id="083e3-233">Giriş noktasını belirtilen bellek eşlemeli kodda yürütür.</span><span class="sxs-lookup"><span data-stu-id="083e3-233">Executes the entry point in the specified memory-mapped code.</span></span> <span data-ttu-id="083e3-234">Bu işlev, işletim sistemi yükleyicisi tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="083e3-234">This function is called by the operating system loader.</span></span>  
  
 [<span data-ttu-id="083e3-235">_CorImageUnloading İşlevi</span><span class="sxs-lookup"><span data-stu-id="083e3-235">_CorImageUnloading Function</span></span>](corimageunloading-function.md)  
 <span data-ttu-id="083e3-236">Yönetilen modül görüntüleri kaldırıldığında yükleyiciyi bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="083e3-236">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 [<span data-ttu-id="083e3-237">_CorValidateImage İşlevi</span><span class="sxs-lookup"><span data-stu-id="083e3-237">_CorValidateImage Function</span></span>](corvalidateimage-function.md)  
 <span data-ttu-id="083e3-238">Yönetilen modül görüntülerini doğrular ve yüklendikten sonra işletim sistemi yükleyicisini bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="083e3-238">Validates managed module images, and notifies the operating system loader after they have been loaded.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="083e3-239">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="083e3-239">See also</span></span>

- [<span data-ttu-id="083e3-240">.NET Framework 4 Barındırma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="083e3-240">.NET Framework 4 Hosting Global Static Functions</span></span>](net-framework-4-hosting-global-static-functions.md)
