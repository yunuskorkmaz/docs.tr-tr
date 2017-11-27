---
title: "Kullanım Dışı CLR Barındırma İşlevleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- .NET Framework 1.1, hosting global static functions
- global static functions [.NET Framework hosting], version 2.0
- .NET Framework 2.0, hosting global static functions
- hosting global static functions [.NET Framework], version 2.0
ms.assetid: 91fbbb35-e543-4814-b806-371cebae8c5a
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9530fecb4f2ca6f59d165e49c282320966fd2fa8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="deprecated-clr-hosting-functions"></a><span data-ttu-id="61cab-102">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="61cab-102">Deprecated CLR Hosting Functions</span></span>
<span data-ttu-id="61cab-103">Bu bölümde barındırma API önceki sürümlerinde kullanılan yönetilmeyen genel statik işlevler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="61cab-103">This section describes the unmanaged global static functions that earlier versions of the hosting API used.</span></span>  
  
 <span data-ttu-id="61cab-104">Altyapı işlevleri (`_Cor*` işlevler), yalnızca .NET Framework tarafından kullanılır, bu işlevler de kullanım dışı bırakıldı [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="61cab-104">With the exception of the infrastructure functions (`_Cor*` functions), which are used only by the .NET Framework, these functions have been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="activation-functions"></a><span data-ttu-id="61cab-105">Etkinleştirme işlevleri</span><span class="sxs-lookup"><span data-stu-id="61cab-105">Activation functions</span></span>  
 [<span data-ttu-id="61cab-106">Clrcreatemanagedınstance işlevi</span><span class="sxs-lookup"><span data-stu-id="61cab-106">ClrCreateManagedInstance Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/clrcreatemanagedinstance-function.md)  
 <span data-ttu-id="61cab-107">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="61cab-107">Deprecated.</span></span> <span data-ttu-id="61cab-108">Belirtilen yönetilen türü örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="61cab-108">Creates an instance of the specified managed type.</span></span>  
  
 [<span data-ttu-id="61cab-109">Coınitializecor işlevi</span><span class="sxs-lookup"><span data-stu-id="61cab-109">CoInitializeCor Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coinitializecor-function.md)  
 <span data-ttu-id="61cab-110">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="61cab-110">Obsolete.</span></span> <span data-ttu-id="61cab-111">Ortak dil çalışma zamanı (CLR) başlatmak için kullanın ya da [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) veya [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="61cab-111">To initialize the common language runtime (CLR), use either [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span></span>  
  
 [<span data-ttu-id="61cab-112">Coınitializeee işlevi</span><span class="sxs-lookup"><span data-stu-id="61cab-112">CoInitializeEE Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)  
 <span data-ttu-id="61cab-113">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="61cab-113">Deprecated.</span></span> <span data-ttu-id="61cab-114">CLR yürütme altyapısı bir işlemine yüklendi sağlar.</span><span class="sxs-lookup"><span data-stu-id="61cab-114">Ensures that the CLR execution engine is loaded into a process.</span></span> <span data-ttu-id="61cab-115">Kullanım [Iclrruntimehost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="61cab-115">Use the [ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method instead.</span></span>  
  
 [<span data-ttu-id="61cab-116">CorBindToCurrentRuntime işlevi</span><span class="sxs-lookup"><span data-stu-id="61cab-116">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 <span data-ttu-id="61cab-117">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="61cab-117">Deprecated.</span></span> <span data-ttu-id="61cab-118">Ortak dil çalışma zamanı (CLR), bir XML dosyasında depolanan sürüm bilgileri kullanarak bir sürecine yükler.</span><span class="sxs-lookup"><span data-stu-id="61cab-118">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span>  
  
 [<span data-ttu-id="61cab-119">CorBindToRuntime işlevi</span><span class="sxs-lookup"><span data-stu-id="61cab-119">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 <span data-ttu-id="61cab-120">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="61cab-120">Deprecated.</span></span> <span data-ttu-id="61cab-121">CLR süreç içine yüklemek için yönetilmeyen konakları etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="61cab-121">Enables unmanaged hosts to load the CLR into a process.</span></span>  
  
 [<span data-ttu-id="61cab-122">CorBindToRuntimeByCfg işlevi</span><span class="sxs-lookup"><span data-stu-id="61cab-122">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 <span data-ttu-id="61cab-123">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="61cab-123">Deprecated.</span></span> <span data-ttu-id="61cab-124">CLR bir XML dosyasından okuma sürüm bilgilerini kullanarak bir sürecine yükler.</span><span class="sxs-lookup"><span data-stu-id="61cab-124">Loads the CLR into a process by using version information that is read from an XML file.</span></span>  
  
 [<span data-ttu-id="61cab-125">CorBindToRuntimeEx işlevi</span><span class="sxs-lookup"><span data-stu-id="61cab-125">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 <span data-ttu-id="61cab-126">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="61cab-126">Deprecated.</span></span> <span data-ttu-id="61cab-127">CLR süreç içine yüklemek yönetilmeyen ana bilgisayarları etkinleştirir ve CLR davranışını belirtmek için bayrakları ayarlamanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="61cab-127">Enables unmanaged hosts to load the CLR into a process, and allows you to set flags to specify the behavior of the CLR.</span></span>  
  
 [<span data-ttu-id="61cab-128">CorBindToRuntimeHost işlevi</span><span class="sxs-lookup"><span data-stu-id="61cab-128">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 <span data-ttu-id="61cab-129">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="61cab-129">Deprecated.</span></span> <span data-ttu-id="61cab-130">Süreç içine CLR belirtilen bir sürümünü yüklemek ana bilgisayarları sağlar.</span><span class="sxs-lookup"><span data-stu-id="61cab-130">Enables hosts to load a specified version of the CLR into a process.</span></span>  
  
 [<span data-ttu-id="61cab-131">GetCORRequiredVersion işlevi</span><span class="sxs-lookup"><span data-stu-id="61cab-131">GetCORRequiredVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getcorrequiredversion-function.md)  
 <span data-ttu-id="61cab-132">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="61cab-132">Deprecated.</span></span> <span data-ttu-id="61cab-133">Gerekli CLR sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="61cab-133">Gets the required CLR version number.</span></span>  
  
 [<span data-ttu-id="61cab-134">GetCORSystemDirectory işlevi</span><span class="sxs-lookup"><span data-stu-id="61cab-134">GetCORSystemDirectory Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md)  
 <span data-ttu-id="61cab-135">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="61cab-135">Deprecated.</span></span> <span data-ttu-id="61cab-136">İşlem içine yüklenmiş CLR yükleme dizinini döndürür.</span><span class="sxs-lookup"><span data-stu-id="61cab-136">Returns the installation directory of the CLR that is loaded into the process.</span></span>  
  
 [<span data-ttu-id="61cab-137">GetRealProcAddress işlevi</span><span class="sxs-lookup"><span data-stu-id="61cab-137">GetRealProcAddress Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md)  
 <span data-ttu-id="61cab-138">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="61cab-138">Deprecated.</span></span> <span data-ttu-id="61cab-139">Son yüklenen sürümünden CLR dışarı belirtilen işlev adresi alır.</span><span class="sxs-lookup"><span data-stu-id="61cab-139">Gets the address of the specified function that is exported from the latest installed version of the CLR.</span></span>  
  
 [<span data-ttu-id="61cab-140">Getrequestedruntimeınfo işlevi</span><span class="sxs-lookup"><span data-stu-id="61cab-140">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
 <span data-ttu-id="61cab-141">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="61cab-141">Deprecated.</span></span> <span data-ttu-id="61cab-142">Bir uygulama tarafından istenen CLR sürümü ve dizin bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="61cab-142">Gets version and directory information about the CLR requested by an application.</span></span>  
  
## <a name="clr-version-functions"></a><span data-ttu-id="61cab-143">CLR sürüm işlevleri</span><span class="sxs-lookup"><span data-stu-id="61cab-143">CLR version functions</span></span>  
 <span data-ttu-id="61cab-144">Bu bölümdeki işlevler CLR sürümü döndürür; CLR etkinleştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="61cab-144">The functions in this section return a CLR version; they do not activate the CLR.</span></span>  
  
 [<span data-ttu-id="61cab-145">GetCORVersion işlevi</span><span class="sxs-lookup"><span data-stu-id="61cab-145">GetCORVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getcorversion-function.md)  
 <span data-ttu-id="61cab-146">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="61cab-146">Deprecated.</span></span> <span data-ttu-id="61cab-147">Geçerli işlemde çalışan CLR sürüm numarasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="61cab-147">Returns the version number of the CLR that is running in the current process.</span></span>  
  
 [<span data-ttu-id="61cab-148">GetFileVersion işlevi</span><span class="sxs-lookup"><span data-stu-id="61cab-148">GetFileVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md)  
 <span data-ttu-id="61cab-149">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="61cab-149">Deprecated.</span></span> <span data-ttu-id="61cab-150">Belirtilen arabellek kullanarak dosyanın belirtilen CLR sürüm bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="61cab-150">Gets the CLR version information of the specified file, using the specified buffer.</span></span>  
  
 [<span data-ttu-id="61cab-151">GetRequestedRuntimeVersion işlevi</span><span class="sxs-lookup"><span data-stu-id="61cab-151">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
 <span data-ttu-id="61cab-152">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="61cab-152">Deprecated.</span></span> <span data-ttu-id="61cab-153">Belirtilen uygulama tarafından istenen CLR sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="61cab-153">Gets the version number of the CLR requested by the specified application.</span></span> <span data-ttu-id="61cab-154">Bu sürümü yüklü değilse, önce istenen sürümü yüklü en son sürümünü alır.</span><span class="sxs-lookup"><span data-stu-id="61cab-154">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 [<span data-ttu-id="61cab-155">Getrequestedruntimeversionforclsıd işlevi</span><span class="sxs-lookup"><span data-stu-id="61cab-155">GetRequestedRuntimeVersionForCLSID Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversionforclsid-function.md)  
 <span data-ttu-id="61cab-156">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="61cab-156">Deprecated.</span></span> <span data-ttu-id="61cab-157">Belirtilen CLSID sınıfı için uygun CLR sürüm bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="61cab-157">Gets the appropriate CLR version information for the class with the specified CLSID.</span></span>  
  
 [<span data-ttu-id="61cab-158">GetVersionFromProcess işlevi</span><span class="sxs-lookup"><span data-stu-id="61cab-158">GetVersionFromProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)  
 <span data-ttu-id="61cab-159">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="61cab-159">Deprecated.</span></span> <span data-ttu-id="61cab-160">Belirtilen işlem tanıtıcı ile ilişkili CLR sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="61cab-160">Gets the version number of the CLR that is associated with the specified process handle.</span></span>  
  
 [<span data-ttu-id="61cab-161">LockClrVersion işlevi</span><span class="sxs-lookup"><span data-stu-id="61cab-161">LockClrVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)  
 <span data-ttu-id="61cab-162">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="61cab-162">Deprecated.</span></span> <span data-ttu-id="61cab-163">CLR açıkça başlatmadan önce işlemi içinde CLR hangi sürümünün kullanılacağını belirlemek için ana sağlar.</span><span class="sxs-lookup"><span data-stu-id="61cab-163">Allows the host to determine which version of the CLR will be used within the process before explicitly initializing the CLR.</span></span>  
  
## <a name="hosting-functions"></a><span data-ttu-id="61cab-164">Barındırma işlevleri</span><span class="sxs-lookup"><span data-stu-id="61cab-164">Hosting functions</span></span>  
 [<span data-ttu-id="61cab-165">CallFunctionShim işlevi</span><span class="sxs-lookup"><span data-stu-id="61cab-165">CallFunctionShim Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/callfunctionshim-function.md)  
 <span data-ttu-id="61cab-166">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="61cab-166">Deprecated.</span></span> <span data-ttu-id="61cab-167">Belirtilen ada ve parametreleri belirtilen Kitaplığı'nda sahip işlevine bir çağrı yapar.</span><span class="sxs-lookup"><span data-stu-id="61cab-167">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 [<span data-ttu-id="61cab-168">CoEEShutDownCOM işlevi</span><span class="sxs-lookup"><span data-stu-id="61cab-168">CoEEShutDownCOM Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coeeshutdowncom-function.md)  
 <span data-ttu-id="61cab-169">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="61cab-169">Deprecated.</span></span> <span data-ttu-id="61cab-170">Bir COM derlemesine işleminden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="61cab-170">Unloads a COM assembly from the process.</span></span>  
  
 [<span data-ttu-id="61cab-171">CorExitProcess işlevi</span><span class="sxs-lookup"><span data-stu-id="61cab-171">CorExitProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md)  
 <span data-ttu-id="61cab-172">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="61cab-172">Deprecated.</span></span> <span data-ttu-id="61cab-173">Geçerli yönetilmeyen işlemi kapatır.</span><span class="sxs-lookup"><span data-stu-id="61cab-173">Shuts down the current unmanaged process.</span></span>  
  
 [<span data-ttu-id="61cab-174">CorLaunchApplication işlevi</span><span class="sxs-lookup"><span data-stu-id="61cab-174">CorLaunchApplication Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corlaunchapplication-function.md)  
 <span data-ttu-id="61cab-175">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="61cab-175">Deprecated.</span></span> <span data-ttu-id="61cab-176">Belirtilen bildirimleri ve diğer uygulama verilerini kullanarak belirtilen ağ yolundaki uygulamayı başlatır.</span><span class="sxs-lookup"><span data-stu-id="61cab-176">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 [<span data-ttu-id="61cab-177">Cormarkthreadınthreadpool işlevi</span><span class="sxs-lookup"><span data-stu-id="61cab-177">CorMarkThreadInThreadPool Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/cormarkthreadinthreadpool-function.md)  
 <span data-ttu-id="61cab-178">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="61cab-178">Deprecated.</span></span> <span data-ttu-id="61cab-179">Yönetilen kod yürütülmesi için şu anda yürütülen iş parçacığı havuzu iş parçacığı işaretler.</span><span class="sxs-lookup"><span data-stu-id="61cab-179">Marks the currently executing thread-pool thread for the execution of managed code.</span></span> <span data-ttu-id="61cab-180">.NET Framework sürüm 2.0 ile başlayarak, bu işlev hiçbir etkisi olmaz.</span><span class="sxs-lookup"><span data-stu-id="61cab-180">Starting with the .NET Framework version 2.0, this function has no effect.</span></span> <span data-ttu-id="61cab-181">Gerekli değildir ve kodunuzdan kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="61cab-181">It is not required, and can be removed from your code.</span></span>  
  
 [<span data-ttu-id="61cab-182">CoUninitializeCor işlevi</span><span class="sxs-lookup"><span data-stu-id="61cab-182">CoUninitializeCor Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md)  
 <span data-ttu-id="61cab-183">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="61cab-183">Obsolete.</span></span> <span data-ttu-id="61cab-184">CLR bir işlemden kaldırılamıyor.</span><span class="sxs-lookup"><span data-stu-id="61cab-184">The CLR cannot be unloaded from a process.</span></span>  
  
 [<span data-ttu-id="61cab-185">CoUninitializeEE işlevi</span><span class="sxs-lookup"><span data-stu-id="61cab-185">CoUninitializeEE Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md)  
 <span data-ttu-id="61cab-186">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="61cab-186">Obsolete.</span></span>  
  
 [<span data-ttu-id="61cab-187">Createdebuggingınterfacefromversion işlevi</span><span class="sxs-lookup"><span data-stu-id="61cab-187">CreateDebuggingInterfaceFromVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md)  
 <span data-ttu-id="61cab-188">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="61cab-188">Deprecated.</span></span> <span data-ttu-id="61cab-189">Oluşturur bir [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) nesne tabanlı belirtilen sürüm bilgileri.</span><span class="sxs-lookup"><span data-stu-id="61cab-189">Creates an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 [<span data-ttu-id="61cab-190">Createıceefilegen işlevi</span><span class="sxs-lookup"><span data-stu-id="61cab-190">CreateICeeFileGen Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md)  
 <span data-ttu-id="61cab-191">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="61cab-191">Deprecated.</span></span> <span data-ttu-id="61cab-192">Oluşturur bir [Iceefilegen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) nesnesi.</span><span class="sxs-lookup"><span data-stu-id="61cab-192">Creates an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 [<span data-ttu-id="61cab-193">Destroyıceefilegen işlevi</span><span class="sxs-lookup"><span data-stu-id="61cab-193">DestroyICeeFileGen Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md)  
 <span data-ttu-id="61cab-194">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="61cab-194">Deprecated.</span></span> <span data-ttu-id="61cab-195">Bozar bir [Iceefilegen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) nesnesi.</span><span class="sxs-lookup"><span data-stu-id="61cab-195">Destroys an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 [<span data-ttu-id="61cab-196">Fexecuteınappdomaincallback işlev işaretçisi</span><span class="sxs-lookup"><span data-stu-id="61cab-196">FExecuteInAppDomainCallback Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/hosting/fexecuteinappdomaincallback-function-pointer.md)  
 <span data-ttu-id="61cab-197">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="61cab-197">Deprecated.</span></span> <span data-ttu-id="61cab-198">Yönetilen kod yürütmek için CLR çağıran bir işlev noktalarına.</span><span class="sxs-lookup"><span data-stu-id="61cab-198">Points to a function that the CLR calls to execute managed code.</span></span>  
  
 [<span data-ttu-id="61cab-199">FLockClrVersionCallback işlev işaretçisi</span><span class="sxs-lookup"><span data-stu-id="61cab-199">FLockClrVersionCallback Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md)  
 <span data-ttu-id="61cab-200">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="61cab-200">Deprecated.</span></span> <span data-ttu-id="61cab-201">Konak bildirmek için CLR çağıran bir işlev noktalarına başlatmanın başlatılan tamamlandı ya da.</span><span class="sxs-lookup"><span data-stu-id="61cab-201">Points to a function that the CLR calls to notify the host that initialization has either started or completed.</span></span>  
  
 [<span data-ttu-id="61cab-202">Getclrıdentitymanager işlevi</span><span class="sxs-lookup"><span data-stu-id="61cab-202">GetCLRIdentityManager Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getclridentitymanager-function.md)  
 <span data-ttu-id="61cab-203">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="61cab-203">Deprecated.</span></span> <span data-ttu-id="61cab-204">Bir işaretçi kimlikleri yönetmek CLR sağlayan bir arabirim alır.</span><span class="sxs-lookup"><span data-stu-id="61cab-204">Gets a pointer to an interface that allows the CLR to manage identities.</span></span>  
  
 [<span data-ttu-id="61cab-205">LoadLibraryShim işlevi</span><span class="sxs-lookup"><span data-stu-id="61cab-205">LoadLibraryShim Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md)  
 <span data-ttu-id="61cab-206">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="61cab-206">Deprecated.</span></span> <span data-ttu-id="61cab-207">.NET Framework DLL belirtilen sürümünü yükler.</span><span class="sxs-lookup"><span data-stu-id="61cab-207">Loads a specified version of a .NET Framework DLL.</span></span>  
  
 [<span data-ttu-id="61cab-208">LoadStringRC işlevi</span><span class="sxs-lookup"><span data-stu-id="61cab-208">LoadStringRC Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
 <span data-ttu-id="61cab-209">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="61cab-209">Deprecated.</span></span> <span data-ttu-id="61cab-210">Bir HRESULT değeri, geçerli iş parçacığının varsayılan kültürü kullanarak hata iletisine çevirir.</span><span class="sxs-lookup"><span data-stu-id="61cab-210">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 [<span data-ttu-id="61cab-211">LoadStringRCEx işlevi</span><span class="sxs-lookup"><span data-stu-id="61cab-211">LoadStringRCEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
 <span data-ttu-id="61cab-212">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="61cab-212">Deprecated.</span></span> <span data-ttu-id="61cab-213">Uygun bir hata iletisi belirtilen kültür için HRESULT değerine dönüşür.</span><span class="sxs-lookup"><span data-stu-id="61cab-213">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 [<span data-ttu-id="61cab-214">Lpoverlapped_completıon_routıne işlev işaretçisi</span><span class="sxs-lookup"><span data-stu-id="61cab-214">LPOVERLAPPED_COMPLETION_ROUTINE Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/hosting/lpoverlapped-completion-routine-function-pointer.md)  
 <span data-ttu-id="61cab-215">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="61cab-215">Deprecated.</span></span> <span data-ttu-id="61cab-216">İşaret eden bir çakışan olduğunda ana bilgisayar bildiren bir işlev (diğer bir deyişle, zaman uyumsuz) bir aygıt g/ç işlemi tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="61cab-216">Points to a function that notifies the host when an overlapped (that is, asynchronous) I/O to a device has completed.</span></span>  
  
 [<span data-ttu-id="61cab-217">Lpthread_start_routıne işlev işaretçisi</span><span class="sxs-lookup"><span data-stu-id="61cab-217">LPTHREAD_START_ROUTINE Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/hosting/lpthread-start-routine-function-pointer.md)  
 <span data-ttu-id="61cab-218">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="61cab-218">Deprecated.</span></span> <span data-ttu-id="61cab-219">Bir iş parçacığını yürütmek için başlatıldı konak bildiren bir işlev noktalarına.</span><span class="sxs-lookup"><span data-stu-id="61cab-219">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 [<span data-ttu-id="61cab-220">RunDll32ShimW işlevi</span><span class="sxs-lookup"><span data-stu-id="61cab-220">RunDll32ShimW Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/rundll32shimw-function.md)  
 <span data-ttu-id="61cab-221">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="61cab-221">Deprecated.</span></span> <span data-ttu-id="61cab-222">Belirtilen komut yürütür.</span><span class="sxs-lookup"><span data-stu-id="61cab-222">Executes the specified command.</span></span>  
  
 [<span data-ttu-id="61cab-223">WAITORTIMERCALLBACK işlev işaretçisi</span><span class="sxs-lookup"><span data-stu-id="61cab-223">WAITORTIMERCALLBACK Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/hosting/waitortimercallback-function-pointer.md)  
 <span data-ttu-id="61cab-224">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="61cab-224">Deprecated.</span></span> <span data-ttu-id="61cab-225">Ana bilgisayar bekleme tanıtıcısı da işaret veya bırakıldığı zaman aşımına uğradı olduğunu bildiren bir işlev noktalarına.</span><span class="sxs-lookup"><span data-stu-id="61cab-225">Points to a function that notifies the host that a wait handle has either been signaled or timed out.</span></span>  
  
## <a name="infrastructure-functions"></a><span data-ttu-id="61cab-226">Altyapı işlevleri</span><span class="sxs-lookup"><span data-stu-id="61cab-226">Infrastructure functions</span></span>  
 <span data-ttu-id="61cab-227">Bu bölümde yalnızca .NET Framework tarafından kullanılmak üzere işlevlerdir.</span><span class="sxs-lookup"><span data-stu-id="61cab-227">The functions in this section are for use by the .NET Framework only.</span></span>  
  
 [<span data-ttu-id="61cab-228">_CorDllMain işlevi</span><span class="sxs-lookup"><span data-stu-id="61cab-228">_CorDllMain Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md)  
 <span data-ttu-id="61cab-229">CLR başlatır, DLL derlemenin CLR üstbilgisinde yönetilen giriş noktasını bulur ve yürütmeye başlar.</span><span class="sxs-lookup"><span data-stu-id="61cab-229">Initializes the CLR, locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
 [<span data-ttu-id="61cab-230">_CorExeMain işlevi</span><span class="sxs-lookup"><span data-stu-id="61cab-230">_CorExeMain Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md)  
 <span data-ttu-id="61cab-231">CLR başlatır, yürütülebilir derlemenin CLR üstbilgisinde yönetilen giriş noktasını bulur ve yürütmeye başlar.</span><span class="sxs-lookup"><span data-stu-id="61cab-231">Initializes the CLR, locates the managed entry point in the executable assembly's CLR header, and begins execution.</span></span>  
  
 [<span data-ttu-id="61cab-232">_CorExeMain2 işlevi</span><span class="sxs-lookup"><span data-stu-id="61cab-232">_CorExeMain2 Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corexemain2-function.md)  
 <span data-ttu-id="61cab-233">Giriş noktası belirtilen bellekle eşlenen kodu yürütür.</span><span class="sxs-lookup"><span data-stu-id="61cab-233">Executes the entry point in the specified memory-mapped code.</span></span> <span data-ttu-id="61cab-234">Bu işlev, işletim sistemi yükleyicisi tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="61cab-234">This function is called by the operating system loader.</span></span>  
  
 [<span data-ttu-id="61cab-235">_Corımageunloading işlevi</span><span class="sxs-lookup"><span data-stu-id="61cab-235">_CorImageUnloading Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md)  
 <span data-ttu-id="61cab-236">Yönetilen modül görüntüleri kaldırılır, yükleyici size bildirir.</span><span class="sxs-lookup"><span data-stu-id="61cab-236">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 [<span data-ttu-id="61cab-237">_Corvalidateımage işlevi</span><span class="sxs-lookup"><span data-stu-id="61cab-237">_CorValidateImage Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md)  
 <span data-ttu-id="61cab-238">Yönetilen modül görüntüleri doğrular ve bunlar yüklendikten sonra işletim sistemi yükleyicisi bildirir.</span><span class="sxs-lookup"><span data-stu-id="61cab-238">Validates managed module images, and notifies the operating system loader after they have been loaded.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61cab-239">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="61cab-239">See Also</span></span>  
 [<span data-ttu-id="61cab-240">.NET framework 4 barındırma genel statik işlevleri</span><span class="sxs-lookup"><span data-stu-id="61cab-240">.NET Framework 4 Hosting Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/net-framework-4-hosting-global-static-functions.md) 
