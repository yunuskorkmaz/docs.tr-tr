---
title: Kullanım Dışı CLR Barındırma İşlevleri
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 1.1, hosting global static functions
- global static functions [.NET Framework hosting], version 2.0
- .NET Framework 2.0, hosting global static functions
- hosting global static functions [.NET Framework], version 2.0
ms.assetid: 91fbbb35-e543-4814-b806-371cebae8c5a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dde711f2d626d88fd80009fa83f1198dd9d47810
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490487"
---
# <a name="deprecated-clr-hosting-functions"></a><span data-ttu-id="7bd1e-102">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="7bd1e-102">Deprecated CLR Hosting Functions</span></span>
<span data-ttu-id="7bd1e-103">Bu bölümde barındırma API'sinin önceki sürümlerinde kullanılan yönetilmeyen genel statik işlevler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-103">This section describes the unmanaged global static functions that earlier versions of the hosting API used.</span></span>  
  
 <span data-ttu-id="7bd1e-104">Altyapı işlevleri (`_Cor*` işlevler), yalnızca .NET Framework tarafından kullanılır, bu işlevler .NET Framework 4'te kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-104">With the exception of the infrastructure functions (`_Cor*` functions), which are used only by the .NET Framework, these functions have been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="activation-functions"></a><span data-ttu-id="7bd1e-105">Etkinleştirme işlevleri</span><span class="sxs-lookup"><span data-stu-id="7bd1e-105">Activation functions</span></span>  
 [<span data-ttu-id="7bd1e-106">ClrCreateManagedInstance İşlevi</span><span class="sxs-lookup"><span data-stu-id="7bd1e-106">ClrCreateManagedInstance Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/clrcreatemanagedinstance-function.md)  
 <span data-ttu-id="7bd1e-107">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-107">Deprecated.</span></span> <span data-ttu-id="7bd1e-108">Belirli bir yönetilen türün bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-108">Creates an instance of the specified managed type.</span></span>  
  
 [<span data-ttu-id="7bd1e-109">CoInitializeCor İşlevi</span><span class="sxs-lookup"><span data-stu-id="7bd1e-109">CoInitializeCor Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coinitializecor-function.md)  
 <span data-ttu-id="7bd1e-110">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-110">Obsolete.</span></span> <span data-ttu-id="7bd1e-111">Ortak dil çalışma zamanı (CLR) başlatmak için ya da kullanmak [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) veya [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="7bd1e-111">To initialize the common language runtime (CLR), use either [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span></span>  
  
 [<span data-ttu-id="7bd1e-112">CoInitializeEE İşlevi</span><span class="sxs-lookup"><span data-stu-id="7bd1e-112">CoInitializeEE Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)  
 <span data-ttu-id="7bd1e-113">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-113">Deprecated.</span></span> <span data-ttu-id="7bd1e-114">CLR yürütme motorunun bir işleme yüklenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-114">Ensures that the CLR execution engine is loaded into a process.</span></span> <span data-ttu-id="7bd1e-115">Kullanım [Iclrruntimehost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-115">Use the [ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method instead.</span></span>  
  
 [<span data-ttu-id="7bd1e-116">CorBindToCurrentRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="7bd1e-116">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 <span data-ttu-id="7bd1e-117">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-117">Deprecated.</span></span> <span data-ttu-id="7bd1e-118">Ortak dil çalışma zamanı (CLR), bir XML dosyasında depolanan sürüm bilgilerini kullanarak bir işlem içine yükler.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-118">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span>  
  
 [<span data-ttu-id="7bd1e-119">CorBindToRuntime İşlevi</span><span class="sxs-lookup"><span data-stu-id="7bd1e-119">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 <span data-ttu-id="7bd1e-120">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-120">Deprecated.</span></span> <span data-ttu-id="7bd1e-121">CLR'yi bir işleme yüklemek için yöneilmeyen ana bilgisayarları etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-121">Enables unmanaged hosts to load the CLR into a process.</span></span>  
  
 [<span data-ttu-id="7bd1e-122">CorBindToRuntimeByCfg İşlevi</span><span class="sxs-lookup"><span data-stu-id="7bd1e-122">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 <span data-ttu-id="7bd1e-123">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-123">Deprecated.</span></span> <span data-ttu-id="7bd1e-124">CLR, bir XML dosyasından okunan sürüm bilgilerini kullanarak bir işlem içine yükler.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-124">Loads the CLR into a process by using version information that is read from an XML file.</span></span>  
  
 [<span data-ttu-id="7bd1e-125">CorBindToRuntimeEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="7bd1e-125">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 <span data-ttu-id="7bd1e-126">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-126">Deprecated.</span></span> <span data-ttu-id="7bd1e-127">CLR'yi bir işleme yüklemek için yönetilmeyen ana bilgisayarları etkinleştirir ve CLR'nin davranışını belirtmek için bayrakları ayarlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-127">Enables unmanaged hosts to load the CLR into a process, and allows you to set flags to specify the behavior of the CLR.</span></span>  
  
 [<span data-ttu-id="7bd1e-128">CorBindToRuntimeHost İşlevi</span><span class="sxs-lookup"><span data-stu-id="7bd1e-128">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 <span data-ttu-id="7bd1e-129">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-129">Deprecated.</span></span> <span data-ttu-id="7bd1e-130">Bir işleme belirtilen bir CLR sürümü yüklemek için ana bilgisayarları etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-130">Enables hosts to load a specified version of the CLR into a process.</span></span>  
  
 [<span data-ttu-id="7bd1e-131">GetCORRequiredVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="7bd1e-131">GetCORRequiredVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getcorrequiredversion-function.md)  
 <span data-ttu-id="7bd1e-132">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-132">Deprecated.</span></span> <span data-ttu-id="7bd1e-133">Gerekli CLR sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-133">Gets the required CLR version number.</span></span>  
  
 [<span data-ttu-id="7bd1e-134">GetCORSystemDirectory İşlevi</span><span class="sxs-lookup"><span data-stu-id="7bd1e-134">GetCORSystemDirectory Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md)  
 <span data-ttu-id="7bd1e-135">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-135">Deprecated.</span></span> <span data-ttu-id="7bd1e-136">İşlem içine yüklenmiş CLR yükleme dizinini döndürür.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-136">Returns the installation directory of the CLR that is loaded into the process.</span></span>  
  
 [<span data-ttu-id="7bd1e-137">GetRealProcAddress İşlevi</span><span class="sxs-lookup"><span data-stu-id="7bd1e-137">GetRealProcAddress Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md)  
 <span data-ttu-id="7bd1e-138">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-138">Deprecated.</span></span> <span data-ttu-id="7bd1e-139">En son yüklenen sürümünden CLR dışa aktarılan belirtilen işlevin adresini alır.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-139">Gets the address of the specified function that is exported from the latest installed version of the CLR.</span></span>  
  
 [<span data-ttu-id="7bd1e-140">GetRequestedRuntimeInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="7bd1e-140">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
 <span data-ttu-id="7bd1e-141">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-141">Deprecated.</span></span> <span data-ttu-id="7bd1e-142">Bir uygulama tarafından istenen CLR hakkındaki sürüm ve dizin bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-142">Gets version and directory information about the CLR requested by an application.</span></span>  
  
## <a name="clr-version-functions"></a><span data-ttu-id="7bd1e-143">CLR sürüm işlevleri</span><span class="sxs-lookup"><span data-stu-id="7bd1e-143">CLR version functions</span></span>  
 <span data-ttu-id="7bd1e-144">Bu bölümdeki işlevler bir CLR sürümü döndürür; Bunlar, CLR'yi etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-144">The functions in this section return a CLR version; they do not activate the CLR.</span></span>  
  
 [<span data-ttu-id="7bd1e-145">GetCORVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="7bd1e-145">GetCORVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getcorversion-function.md)  
 <span data-ttu-id="7bd1e-146">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-146">Deprecated.</span></span> <span data-ttu-id="7bd1e-147">Geçerli işlemde çalışan CLR'nin sürüm numarasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-147">Returns the version number of the CLR that is running in the current process.</span></span>  
  
 [<span data-ttu-id="7bd1e-148">GetFileVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="7bd1e-148">GetFileVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md)  
 <span data-ttu-id="7bd1e-149">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-149">Deprecated.</span></span> <span data-ttu-id="7bd1e-150">Belirtilen arabelleği kullanarak belirtilen dosyanın CLR sürümü bilgisini alır.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-150">Gets the CLR version information of the specified file, using the specified buffer.</span></span>  
  
 [<span data-ttu-id="7bd1e-151">GetRequestedRuntimeVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="7bd1e-151">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
 <span data-ttu-id="7bd1e-152">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-152">Deprecated.</span></span> <span data-ttu-id="7bd1e-153">Belirtilen uygulamanın istediği CLR sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-153">Gets the version number of the CLR requested by the specified application.</span></span> <span data-ttu-id="7bd1e-154">Bu sürüm yüklü değilse istenen sürümden önce yüklenen en son sürümü alır.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-154">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 [<span data-ttu-id="7bd1e-155">GetRequestedRuntimeVersionForCLSID İşlevi</span><span class="sxs-lookup"><span data-stu-id="7bd1e-155">GetRequestedRuntimeVersionForCLSID Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversionforclsid-function.md)  
 <span data-ttu-id="7bd1e-156">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-156">Deprecated.</span></span> <span data-ttu-id="7bd1e-157">Belirtilen CLSID'yi içeren sınıf için uygun CLR sürümü bilgisini alır.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-157">Gets the appropriate CLR version information for the class with the specified CLSID.</span></span>  
  
 [<span data-ttu-id="7bd1e-158">GetVersionFromProcess İşlevi</span><span class="sxs-lookup"><span data-stu-id="7bd1e-158">GetVersionFromProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)  
 <span data-ttu-id="7bd1e-159">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-159">Deprecated.</span></span> <span data-ttu-id="7bd1e-160">Belirtilen işlem tanımlayıcısıyla ilişkili CLR sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-160">Gets the version number of the CLR that is associated with the specified process handle.</span></span>  
  
 [<span data-ttu-id="7bd1e-161">LockClrVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="7bd1e-161">LockClrVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)  
 <span data-ttu-id="7bd1e-162">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-162">Deprecated.</span></span> <span data-ttu-id="7bd1e-163">Hangi CLR sürümünün işlem dahilinde CLR açıkça başlatılmadan önce kullanılacak belirlemek konak sağlar.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-163">Allows the host to determine which version of the CLR will be used within the process before explicitly initializing the CLR.</span></span>  
  
## <a name="hosting-functions"></a><span data-ttu-id="7bd1e-164">Barındırma işlevleri</span><span class="sxs-lookup"><span data-stu-id="7bd1e-164">Hosting functions</span></span>  
 [<span data-ttu-id="7bd1e-165">CallFunctionShim İşlevi</span><span class="sxs-lookup"><span data-stu-id="7bd1e-165">CallFunctionShim Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/callfunctionshim-function.md)  
 <span data-ttu-id="7bd1e-166">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-166">Deprecated.</span></span> <span data-ttu-id="7bd1e-167">Belirtilen kitaplık içinde belirtilen ad ve parametreler içeren işleve bir çağrı yapar.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-167">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 [<span data-ttu-id="7bd1e-168">CoEEShutDownCOM İşlevi</span><span class="sxs-lookup"><span data-stu-id="7bd1e-168">CoEEShutDownCOM Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coeeshutdowncom-function.md)  
 <span data-ttu-id="7bd1e-169">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-169">Deprecated.</span></span> <span data-ttu-id="7bd1e-170">İşlemden COM derlemesini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-170">Unloads a COM assembly from the process.</span></span>  
  
 [<span data-ttu-id="7bd1e-171">CorExitProcess İşlevi</span><span class="sxs-lookup"><span data-stu-id="7bd1e-171">CorExitProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md)  
 <span data-ttu-id="7bd1e-172">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-172">Deprecated.</span></span> <span data-ttu-id="7bd1e-173">Yönetilmeyen geçerli işlemi kapatır.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-173">Shuts down the current unmanaged process.</span></span>  
  
 [<span data-ttu-id="7bd1e-174">CorLaunchApplication İşlevi</span><span class="sxs-lookup"><span data-stu-id="7bd1e-174">CorLaunchApplication Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corlaunchapplication-function.md)  
 <span data-ttu-id="7bd1e-175">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-175">Deprecated.</span></span> <span data-ttu-id="7bd1e-176">Belirtilen bildirimleri ve diğer uygulama verilerini kullanarak belirtilen ağ yolunda uygulamayı başlatır.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-176">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 [<span data-ttu-id="7bd1e-177">CorMarkThreadInThreadPool İşlevi</span><span class="sxs-lookup"><span data-stu-id="7bd1e-177">CorMarkThreadInThreadPool Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/cormarkthreadinthreadpool-function.md)  
 <span data-ttu-id="7bd1e-178">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-178">Deprecated.</span></span> <span data-ttu-id="7bd1e-179">Yürütülmekte olan iş parçacığı havuzu iş parçacığını yönetilen kodun yürütülmesi için işaretler.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-179">Marks the currently executing thread-pool thread for the execution of managed code.</span></span> <span data-ttu-id="7bd1e-180">Bu işlev, .NET Framework sürüm 2.0 ile başlayarak, hiçbir etkisi olmaz.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-180">Starting with the .NET Framework version 2.0, this function has no effect.</span></span> <span data-ttu-id="7bd1e-181">Gerekli değildir ve kodunuzdan kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-181">It is not required, and can be removed from your code.</span></span>  
  
 [<span data-ttu-id="7bd1e-182">CoUninitializeCor İşlevi</span><span class="sxs-lookup"><span data-stu-id="7bd1e-182">CoUninitializeCor Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md)  
 <span data-ttu-id="7bd1e-183">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-183">Obsolete.</span></span> <span data-ttu-id="7bd1e-184">CLR bir işlemden olamaz.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-184">The CLR cannot be unloaded from a process.</span></span>  
  
 [<span data-ttu-id="7bd1e-185">CoUninitializeEE İşlevi</span><span class="sxs-lookup"><span data-stu-id="7bd1e-185">CoUninitializeEE Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md)  
 <span data-ttu-id="7bd1e-186">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-186">Obsolete.</span></span>  
  
 [<span data-ttu-id="7bd1e-187">CreateDebuggingInterfaceFromVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="7bd1e-187">CreateDebuggingInterfaceFromVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md)  
 <span data-ttu-id="7bd1e-188">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-188">Deprecated.</span></span> <span data-ttu-id="7bd1e-189">Oluşturur bir [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) nesne belirtilen sürüm bilgisi esas alarak.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-189">Creates an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 [<span data-ttu-id="7bd1e-190">CreateICeeFileGen İşlevi</span><span class="sxs-lookup"><span data-stu-id="7bd1e-190">CreateICeeFileGen Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md)  
 <span data-ttu-id="7bd1e-191">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-191">Deprecated.</span></span> <span data-ttu-id="7bd1e-192">Oluşturur bir [Iceefilegen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) nesne.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-192">Creates an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 [<span data-ttu-id="7bd1e-193">DestroyICeeFileGen İşlevi</span><span class="sxs-lookup"><span data-stu-id="7bd1e-193">DestroyICeeFileGen Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md)  
 <span data-ttu-id="7bd1e-194">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-194">Deprecated.</span></span> <span data-ttu-id="7bd1e-195">Yok eder bir [Iceefilegen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) nesne.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-195">Destroys an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 [<span data-ttu-id="7bd1e-196">FExecuteInAppDomainCallback İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="7bd1e-196">FExecuteInAppDomainCallback Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/hosting/fexecuteinappdomaincallback-function-pointer.md)  
 <span data-ttu-id="7bd1e-197">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-197">Deprecated.</span></span> <span data-ttu-id="7bd1e-198">CLR'nin yönetilen kodu yürütmek için çağırdığı bir işleve işaret eder.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-198">Points to a function that the CLR calls to execute managed code.</span></span>  
  
 [<span data-ttu-id="7bd1e-199">FLockClrVersionCallback İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="7bd1e-199">FLockClrVersionCallback Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md)  
 <span data-ttu-id="7bd1e-200">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-200">Deprecated.</span></span> <span data-ttu-id="7bd1e-201">CLR ana bilgisayara bildirmek için çağırdığı bir işleve işaret başlatmanın çalışmaya tamamlandı ya da.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-201">Points to a function that the CLR calls to notify the host that initialization has either started or completed.</span></span>  
  
 [<span data-ttu-id="7bd1e-202">GetCLRIdentityManager İşlevi</span><span class="sxs-lookup"><span data-stu-id="7bd1e-202">GetCLRIdentityManager Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getclridentitymanager-function.md)  
 <span data-ttu-id="7bd1e-203">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-203">Deprecated.</span></span> <span data-ttu-id="7bd1e-204">CLR'nin kimlikleri yönetmenize izin veren bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-204">Gets a pointer to an interface that allows the CLR to manage identities.</span></span>  
  
 [<span data-ttu-id="7bd1e-205">LoadLibraryShim İşlevi</span><span class="sxs-lookup"><span data-stu-id="7bd1e-205">LoadLibraryShim Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md)  
 <span data-ttu-id="7bd1e-206">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-206">Deprecated.</span></span> <span data-ttu-id="7bd1e-207">Belirtilen bir .NET Framework DLL sürümünü yükler.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-207">Loads a specified version of a .NET Framework DLL.</span></span>  
  
 [<span data-ttu-id="7bd1e-208">LoadStringRC İşlevi</span><span class="sxs-lookup"><span data-stu-id="7bd1e-208">LoadStringRC Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
 <span data-ttu-id="7bd1e-209">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-209">Deprecated.</span></span> <span data-ttu-id="7bd1e-210">Geçerli iş parçacığının varsayılan kültürünü kullanarak, bir HRESULT değerini hata iletisine çevirir.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-210">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 [<span data-ttu-id="7bd1e-211">LoadStringRCEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="7bd1e-211">LoadStringRCEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
 <span data-ttu-id="7bd1e-212">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-212">Deprecated.</span></span> <span data-ttu-id="7bd1e-213">HRESULT değerini belirtilen kültür için uygun hata iletisine çevirir.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-213">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 [<span data-ttu-id="7bd1e-214">LPOVERLAPPED_COMPLETION_ROUTINE İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="7bd1e-214">LPOVERLAPPED_COMPLETION_ROUTINE Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/hosting/lpoverlapped-completion-routine-function-pointer.md)  
 <span data-ttu-id="7bd1e-215">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-215">Deprecated.</span></span> <span data-ttu-id="7bd1e-216">Tamamlandığı zaman ana bilgisayara bildiren bir işleve işaret eder (diğer bir deyişle, zaman uyumsuz) bir aygıt g/ç işlemi tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-216">Points to a function that notifies the host when an overlapped (that is, asynchronous) I/O to a device has completed.</span></span>  
  
 [<span data-ttu-id="7bd1e-217">LPTHREAD_START_ROUTINE İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="7bd1e-217">LPTHREAD_START_ROUTINE Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/hosting/lpthread-start-routine-function-pointer.md)  
 <span data-ttu-id="7bd1e-218">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-218">Deprecated.</span></span> <span data-ttu-id="7bd1e-219">Bir iş parçacığının yürütülmeye başlandığını ana bilgisayara bildiren bir işleve işaret eder.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-219">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 [<span data-ttu-id="7bd1e-220">RunDll32ShimW İşlevi</span><span class="sxs-lookup"><span data-stu-id="7bd1e-220">RunDll32ShimW Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/rundll32shimw-function.md)  
 <span data-ttu-id="7bd1e-221">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-221">Deprecated.</span></span> <span data-ttu-id="7bd1e-222">Belirtilen komutu yürütür.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-222">Executes the specified command.</span></span>  
  
 [<span data-ttu-id="7bd1e-223">WAITORTIMERCALLBACK İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="7bd1e-223">WAITORTIMERCALLBACK Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/hosting/waitortimercallback-function-pointer.md)  
 <span data-ttu-id="7bd1e-224">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-224">Deprecated.</span></span> <span data-ttu-id="7bd1e-225">Ana bilgisayar bekleme tanıtıcısı sinyal veya zaman aşımına uğradı olduğunu bildiren bir işleve işaret eder.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-225">Points to a function that notifies the host that a wait handle has either been signaled or timed out.</span></span>  
  
## <a name="infrastructure-functions"></a><span data-ttu-id="7bd1e-226">Altyapı işlevleri</span><span class="sxs-lookup"><span data-stu-id="7bd1e-226">Infrastructure functions</span></span>  
 <span data-ttu-id="7bd1e-227">Bu bölümdeki işlevler yalnızca .NET Framework tarafından içindir.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-227">The functions in this section are for use by the .NET Framework only.</span></span>  
  
 [<span data-ttu-id="7bd1e-228">_CorDllMain İşlevi</span><span class="sxs-lookup"><span data-stu-id="7bd1e-228">_CorDllMain Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md)  
 <span data-ttu-id="7bd1e-229">CLR'yi başlatır, DLL derlemesinin CLR başlığındaki yönetilen giriş noktasını bulur ve yürütmeyi başlatır.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-229">Initializes the CLR, locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
 [<span data-ttu-id="7bd1e-230">_CorExeMain İşlevi</span><span class="sxs-lookup"><span data-stu-id="7bd1e-230">_CorExeMain Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md)  
 <span data-ttu-id="7bd1e-231">CLR'yi başlatır, derlemesinin CLR başlığındaki yönetilen giriş noktasını bulur ve yürütmeyi başlatır.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-231">Initializes the CLR, locates the managed entry point in the executable assembly's CLR header, and begins execution.</span></span>  
  
 [<span data-ttu-id="7bd1e-232">_CorExeMain2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="7bd1e-232">_CorExeMain2 Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corexemain2-function.md)  
 <span data-ttu-id="7bd1e-233">Belirtilen bellek eşlemeli kod içinde giriş noktasını yürütür.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-233">Executes the entry point in the specified memory-mapped code.</span></span> <span data-ttu-id="7bd1e-234">Bu işlev, işletim sistemi yükleyicisi tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-234">This function is called by the operating system loader.</span></span>  
  
 [<span data-ttu-id="7bd1e-235">_CorImageUnloading İşlevi</span><span class="sxs-lookup"><span data-stu-id="7bd1e-235">_CorImageUnloading Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md)  
 <span data-ttu-id="7bd1e-236">Yönetilen modül görüntüleri yüklenmediği zaman yükleyiciye bildirir.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-236">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 [<span data-ttu-id="7bd1e-237">_CorValidateImage İşlevi</span><span class="sxs-lookup"><span data-stu-id="7bd1e-237">_CorValidateImage Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md)  
 <span data-ttu-id="7bd1e-238">Yönetilen modül görüntüleri doğrular ve bunlar yüklendikten sonra işletim sistemi yükleyicisi bildirir.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-238">Validates managed module images, and notifies the operating system loader after they have been loaded.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bd1e-239">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7bd1e-239">See also</span></span>

- [<span data-ttu-id="7bd1e-240">.NET Framework 4 Barındırma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="7bd1e-240">.NET Framework 4 Hosting Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/net-framework-4-hosting-global-static-functions.md)
