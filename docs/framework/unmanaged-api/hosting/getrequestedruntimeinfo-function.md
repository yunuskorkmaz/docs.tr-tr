---
title: GetRequestedRuntimeInfo İşlevi
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeInfo
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeInfo
helpviewer_keywords:
- GetRequestedRuntimeInfo function [.NET Framework hosting]
ms.assetid: 0dfd7cdc-c116-4e25-b56a-ac7b0378c942
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 62a6f6d6e73ce42c8c86d4e458322e5bd361f412
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778130"
---
# <a name="getrequestedruntimeinfo-function"></a><span data-ttu-id="ac2fd-102">GetRequestedRuntimeInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="ac2fd-102">GetRequestedRuntimeInfo Function</span></span>
<span data-ttu-id="ac2fd-103">Bir uygulama tarafından istenen ortak dil çalışma zamanı (CLR) sürümünü ve dizin bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="ac2fd-103">Gets version and directory information about the common language runtime (CLR) requested by an application.</span></span>  
  
 <span data-ttu-id="ac2fd-104">Bu işlev .NET Framework 4'te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="ac2fd-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac2fd-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ac2fd-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRequestedRuntimeInfo (  
    [in]  LPCWSTR  pExe,   
    [in]  LPCWSTR  pwszVersion,   
    [in]  LPCWSTR  pConfigurationFile,   
    [in]  DWORD    startupFlags,   
    [in]  DWORD    runtimeInfoFlags,   
    [out] LPWSTR   pDirectory,   
    [in]  DWORD    dwDirectory,   
    [out] DWORD   *dwDirectoryLength,   
    [out] LPWSTR   pVersion,   
    [in]  DWORD    cchBuffer,   
    [out] DWORD   *dwlength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac2fd-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ac2fd-106">Parameters</span></span>  
 `pExe`  
 <span data-ttu-id="ac2fd-107">[in] Uygulamanın adı.</span><span class="sxs-lookup"><span data-stu-id="ac2fd-107">[in] The name of the application.</span></span>  
  
 `pwszVersion`  
 <span data-ttu-id="ac2fd-108">[in] Çalışma zamanı sürüm numarasını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="ac2fd-108">[in] A string specifying the version number of the runtime.</span></span>  
  
 `pConfigurationFile`  
 <span data-ttu-id="ac2fd-109">[in] İle ilişkili yapılandırma dosyasının adını `pExe`.</span><span class="sxs-lookup"><span data-stu-id="ac2fd-109">[in] The name of the configuration file that is associated with `pExe`.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="ac2fd-110">[in] Bir veya daha fazla [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) sabit listesi değerleri.</span><span class="sxs-lookup"><span data-stu-id="ac2fd-110">[in] One or more of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration values.</span></span>  
  
 `runtimeInfoFlags`  
 <span data-ttu-id="ac2fd-111">[in] Bir veya daha fazla [runtıme_ınfo_flags](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md) sabit listesi değerleri.</span><span class="sxs-lookup"><span data-stu-id="ac2fd-111">[in] One or more of the [RUNTIME_INFO_FLAGS](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md) enumeration values.</span></span>  
  
 `pDirectory`  
 <span data-ttu-id="ac2fd-112">[out] Çalışma zamanı başarıyla tamamlandıktan sonra dizin yolu içeren arabellek.</span><span class="sxs-lookup"><span data-stu-id="ac2fd-112">[out] A buffer that contains the directory path to the runtime upon successful completion.</span></span>  
  
 `dwDirectory`  
 <span data-ttu-id="ac2fd-113">[in] Dizin arabelleği uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="ac2fd-113">[in] The length of the directory buffer.</span></span>  
  
 `dwDirectoryLength`  
 <span data-ttu-id="ac2fd-114">[out] Dizin yolu dizenin uzunluğu bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ac2fd-114">[out] A pointer to the length of the directory path string.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="ac2fd-115">[out] Çalışma zamanı başarıyla tamamlandığında uygulamanın sürüm sayısını içeren bir arabelleği.</span><span class="sxs-lookup"><span data-stu-id="ac2fd-115">[out] A buffer that contains the version number of the runtime upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="ac2fd-116">[in] Sürüm dizesi arabelleği uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="ac2fd-116">[in] The length of the version string buffer.</span></span>  
  
 `dwlength`  
 <span data-ttu-id="ac2fd-117">[out] Sürüm dizesinin uzunluğunu işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="ac2fd-117">[out] A pointer to the length of the version string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ac2fd-118">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ac2fd-118">Return Value</span></span>  
 <span data-ttu-id="ac2fd-119">Bu yöntem standart Bileşen Nesne Modeli (COM) hata kodları, ek olarak aşağıdaki değerleri Wınerror içinde tanımlanan döndürür.</span><span class="sxs-lookup"><span data-stu-id="ac2fd-119">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="ac2fd-120">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="ac2fd-120">Return code</span></span>|<span data-ttu-id="ac2fd-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ac2fd-121">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="ac2fd-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="ac2fd-122">S_OK</span></span>|<span data-ttu-id="ac2fd-123">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="ac2fd-123">The method completed successfully.</span></span>|  
|<span data-ttu-id="ac2fd-124">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="ac2fd-124">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="ac2fd-125">Dizin arabelleği dizin yolu depolamak için yeterli büyüklükte değil.</span><span class="sxs-lookup"><span data-stu-id="ac2fd-125">The directory buffer is not large enough to store the directory path.</span></span><br /><br /> <span data-ttu-id="ac2fd-126">- veya -</span><span class="sxs-lookup"><span data-stu-id="ac2fd-126">- or -</span></span><br /><br /> <span data-ttu-id="ac2fd-127">Sürüm arabellek sürüm dizesi depolamak için yeterli büyüklükte değil.</span><span class="sxs-lookup"><span data-stu-id="ac2fd-127">The version buffer is not large enough to store the version string.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac2fd-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ac2fd-128">Remarks</span></span>  
 <span data-ttu-id="ac2fd-129">`GetRequestedRuntimeInfo` Yöntemi mutlaka en son sürümü bilgisayarda yüklü değil işlem yüklenen sürümü çalışma zamanı bilgilerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="ac2fd-129">The `GetRequestedRuntimeInfo` method returns run-time information about the version loaded into the process, which is not necessarily the latest version installed on the computer.</span></span>  
  
 <span data-ttu-id="ac2fd-130">.NET Framework sürüm 2. 0'da, en son yüklenen sürüm bilgilerini kullanarak alabilirsiniz `GetRequestedRuntimeInfo` yöntemini aşağıdaki şekilde:</span><span class="sxs-lookup"><span data-stu-id="ac2fd-130">In the .NET Framework version 2.0, you can get information about the latest installed version by using the `GetRequestedRuntimeInfo` method as follows:</span></span>  
  
- <span data-ttu-id="ac2fd-131">Belirtin `pExe`, `pwszVersion`, ve `pConfigurationFile` parametreleri null olarak.</span><span class="sxs-lookup"><span data-stu-id="ac2fd-131">Specify the `pExe`, `pwszVersion`, and `pConfigurationFile` parameters as null.</span></span>  
  
- <span data-ttu-id="ac2fd-132">RUNTIME_INFO_UPGRADE_VERSION bayrağını belirtin `RUNTIME_INFO_FLAGS` sabit listeleri için `runtimeInfoFlags` parametresi.</span><span class="sxs-lookup"><span data-stu-id="ac2fd-132">Specify the RUNTIME_INFO_UPGRADE_VERSION flag in the `RUNTIME_INFO_FLAGS` enumerations for the `runtimeInfoFlags` parameter.</span></span>  
  
 <span data-ttu-id="ac2fd-133">`GetRequestedRuntimeInfo` Yöntemi en son CLR sürümünü aşağıdaki durumlarda döndürmüyor:</span><span class="sxs-lookup"><span data-stu-id="ac2fd-133">The `GetRequestedRuntimeInfo` method does not return the latest CLR version in the following circumstances:</span></span>  
  
- <span data-ttu-id="ac2fd-134">Belirli bir CLR sürümü belirten bir uygulama yapılandırma dosyası yok.</span><span class="sxs-lookup"><span data-stu-id="ac2fd-134">An application configuration file that specifies loading a particular CLR version exists.</span></span> <span data-ttu-id="ac2fd-135">İçin null belirtin bile .NET Framework yapılandırma dosyası kullanacağını Not `pConfigurationFile` parametresi.</span><span class="sxs-lookup"><span data-stu-id="ac2fd-135">Note that the .NET Framework will use the configuration file even if you specify null for the `pConfigurationFile` parameter.</span></span>  
  
- <span data-ttu-id="ac2fd-136">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) önceki bir CLR sürümünü belirtme yöntemi çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="ac2fd-136">The [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) method was called specifying an earlier CLR version.</span></span>  
  
- <span data-ttu-id="ac2fd-137">Önceki bir CLR sürümü için derlenmiş bir uygulama şu anda çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="ac2fd-137">An application that was compiled for an earlier CLR version is currently running.</span></span>  
  
 <span data-ttu-id="ac2fd-138">İçin `runtimeInfoFlags` parametresini belirtebilirsiniz mimarisi sabitlerini yalnızca biri `RUNTIME_INFO_FLAGS` birer birer sabit listesi:</span><span class="sxs-lookup"><span data-stu-id="ac2fd-138">For the `runtimeInfoFlags` parameter, you can specify only one of the architecture constants of the `RUNTIME_INFO_FLAGS` enumeration at a time:</span></span>  
  
- <span data-ttu-id="ac2fd-139">RUNTIME_INFO_REQUEST_IA64</span><span class="sxs-lookup"><span data-stu-id="ac2fd-139">RUNTIME_INFO_REQUEST_IA64</span></span>  
  
- <span data-ttu-id="ac2fd-140">RUNTIME_INFO_REQUEST_AMD64</span><span class="sxs-lookup"><span data-stu-id="ac2fd-140">RUNTIME_INFO_REQUEST_AMD64</span></span>  
  
- <span data-ttu-id="ac2fd-141">RUNTIME_INFO_REQUEST_X86</span><span class="sxs-lookup"><span data-stu-id="ac2fd-141">RUNTIME_INFO_REQUEST_X86</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac2fd-142">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ac2fd-142">Requirements</span></span>  
 <span data-ttu-id="ac2fd-143">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac2fd-143">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac2fd-144">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ac2fd-144">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ac2fd-145">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ac2fd-145">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ac2fd-146">**.NET framework sürümleri:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac2fd-146">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac2fd-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac2fd-147">See also</span></span>

- [<span data-ttu-id="ac2fd-148">GetRequestedRuntimeVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="ac2fd-148">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [<span data-ttu-id="ac2fd-149">GetVersionFromProcess İşlevi</span><span class="sxs-lookup"><span data-stu-id="ac2fd-149">GetVersionFromProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [<span data-ttu-id="ac2fd-150">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="ac2fd-150">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
