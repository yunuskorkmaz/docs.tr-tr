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
ms.openlocfilehash: 9f37be8e3d2e92147e9f13954ab64396062ade2d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434987"
---
# <a name="getrequestedruntimeinfo-function"></a><span data-ttu-id="f1c8f-102">GetRequestedRuntimeInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="f1c8f-102">GetRequestedRuntimeInfo Function</span></span>
<span data-ttu-id="f1c8f-103">Bir uygulama tarafından istenen ortak dil çalışma zamanı (CLR) sürümü ve dizin bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="f1c8f-103">Gets version and directory information about the common language runtime (CLR) requested by an application.</span></span>  
  
 <span data-ttu-id="f1c8f-104">Bu işlev kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f1c8f-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1c8f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f1c8f-105">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="f1c8f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f1c8f-106">Parameters</span></span>  
 `pExe`  
 <span data-ttu-id="f1c8f-107">[in] Uygulamanın adı.</span><span class="sxs-lookup"><span data-stu-id="f1c8f-107">[in] The name of the application.</span></span>  
  
 `pwszVersion`  
 <span data-ttu-id="f1c8f-108">[in] Çalışma zamanı sürüm sayısını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="f1c8f-108">[in] A string specifying the version number of the runtime.</span></span>  
  
 `pConfigurationFile`  
 <span data-ttu-id="f1c8f-109">[in] İle ilişkili yapılandırma dosyasının adını `pExe`.</span><span class="sxs-lookup"><span data-stu-id="f1c8f-109">[in] The name of the configuration file that is associated with `pExe`.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="f1c8f-110">[in] Bir veya daha fazlasının [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) numaralandırma değerleri.</span><span class="sxs-lookup"><span data-stu-id="f1c8f-110">[in] One or more of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration values.</span></span>  
  
 `runtimeInfoFlags`  
 <span data-ttu-id="f1c8f-111">[in] Bir veya daha fazlasının [runtıme_ınfo_flags](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md) numaralandırma değerleri.</span><span class="sxs-lookup"><span data-stu-id="f1c8f-111">[in] One or more of the [RUNTIME_INFO_FLAGS](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md) enumeration values.</span></span>  
  
 `pDirectory`  
 <span data-ttu-id="f1c8f-112">[out] Çalışma zamanı başarıyla tamamlandıktan sonra dizin yolunu içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="f1c8f-112">[out] A buffer that contains the directory path to the runtime upon successful completion.</span></span>  
  
 `dwDirectory`  
 <span data-ttu-id="f1c8f-113">[in] Dizin arabellek uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="f1c8f-113">[in] The length of the directory buffer.</span></span>  
  
 `dwDirectoryLength`  
 <span data-ttu-id="f1c8f-114">[out] Dizin yolu dizesi uzunluğu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f1c8f-114">[out] A pointer to the length of the directory path string.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="f1c8f-115">[out] İşlem başarıyla tamamlandıktan sonra çalışma zamanının sürüm numarasını içerir arabelleği.</span><span class="sxs-lookup"><span data-stu-id="f1c8f-115">[out] A buffer that contains the version number of the runtime upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="f1c8f-116">[in] Sürüm dizesi arabellek uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="f1c8f-116">[in] The length of the version string buffer.</span></span>  
  
 `dwlength`  
 <span data-ttu-id="f1c8f-117">[out] Sürüm dizesi uzunluğu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f1c8f-117">[out] A pointer to the length of the version string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f1c8f-118">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f1c8f-118">Return Value</span></span>  
 <span data-ttu-id="f1c8f-119">Bu yöntem standart Bileşen Nesne Modeli (COM) hata kodları, ek olarak aşağıdaki değerleri Winerror.h'de içinde tanımlandığı şekilde döndürür.</span><span class="sxs-lookup"><span data-stu-id="f1c8f-119">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="f1c8f-120">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="f1c8f-120">Return code</span></span>|<span data-ttu-id="f1c8f-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f1c8f-121">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="f1c8f-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="f1c8f-122">S_OK</span></span>|<span data-ttu-id="f1c8f-123">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="f1c8f-123">The method completed successfully.</span></span>|  
|<span data-ttu-id="f1c8f-124">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="f1c8f-124">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="f1c8f-125">Dizin arabelleği dizin yolu depolamak için yeterli büyüklükte değil.</span><span class="sxs-lookup"><span data-stu-id="f1c8f-125">The directory buffer is not large enough to store the directory path.</span></span><br /><br /> <span data-ttu-id="f1c8f-126">- veya -</span><span class="sxs-lookup"><span data-stu-id="f1c8f-126">- or -</span></span><br /><br /> <span data-ttu-id="f1c8f-127">Sürüm arabellek sürüm dizesi depolamak için yeterli büyüklükte değil.</span><span class="sxs-lookup"><span data-stu-id="f1c8f-127">The version buffer is not large enough to store the version string.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1c8f-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f1c8f-128">Remarks</span></span>  
 <span data-ttu-id="f1c8f-129">`GetRequestedRuntimeInfo` Yöntemi mutlaka en son sürümü bilgisayarda yüklü değil işlemine yüklenen sürümüyle ilgili çalışma zamanı bilgilerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="f1c8f-129">The `GetRequestedRuntimeInfo` method returns run-time information about the version loaded into the process, which is not necessarily the latest version installed on the computer.</span></span>  
  
 <span data-ttu-id="f1c8f-130">.NET Framework sürüm 2. 0'da, kullanarak en son yüklenen sürümü hakkında bilgi alabilirsiniz `GetRequestedRuntimeInfo` yöntemini aşağıdaki şekilde:</span><span class="sxs-lookup"><span data-stu-id="f1c8f-130">In the .NET Framework version 2.0, you can get information about the latest installed version by using the `GetRequestedRuntimeInfo` method as follows:</span></span>  
  
-   <span data-ttu-id="f1c8f-131">Belirtin `pExe`, `pwszVersion`, ve `pConfigurationFile` parametre null olarak.</span><span class="sxs-lookup"><span data-stu-id="f1c8f-131">Specify the `pExe`, `pwszVersion`, and `pConfigurationFile` parameters as null.</span></span>  
  
-   <span data-ttu-id="f1c8f-132">RUNTIME_INFO_UPGRADE_VERSION bayrağı belirtin `RUNTIME_INFO_FLAGS` sabit listeleri için `runtimeInfoFlags` parametresi.</span><span class="sxs-lookup"><span data-stu-id="f1c8f-132">Specify the RUNTIME_INFO_UPGRADE_VERSION flag in the `RUNTIME_INFO_FLAGS` enumerations for the `runtimeInfoFlags` parameter.</span></span>  
  
 <span data-ttu-id="f1c8f-133">`GetRequestedRuntimeInfo` Yöntemi, aşağıdaki durumlarda en son CLR sürümü dönmez:</span><span class="sxs-lookup"><span data-stu-id="f1c8f-133">The `GetRequestedRuntimeInfo` method does not return the latest CLR version in the following circumstances:</span></span>  
  
-   <span data-ttu-id="f1c8f-134">Belirli bir CLR sürümü belirten bir uygulama yapılandırma dosyası yok.</span><span class="sxs-lookup"><span data-stu-id="f1c8f-134">An application configuration file that specifies loading a particular CLR version exists.</span></span> <span data-ttu-id="f1c8f-135">.NET Framework için null belirtin olsa bile yapılandırma dosyasını kullanacak Not `pConfigurationFile` parametresi.</span><span class="sxs-lookup"><span data-stu-id="f1c8f-135">Note that the .NET Framework will use the configuration file even if you specify null for the `pConfigurationFile` parameter.</span></span>  
  
-   <span data-ttu-id="f1c8f-136">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) yöntemi, daha önce bir CLR sürüm belirtme çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="f1c8f-136">The [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) method was called specifying an earlier CLR version.</span></span>  
  
-   <span data-ttu-id="f1c8f-137">Önceki bir CLR sürümü için derlenmiş bir uygulama şu anda çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="f1c8f-137">An application that was compiled for an earlier CLR version is currently running.</span></span>  
  
 <span data-ttu-id="f1c8f-138">İçin `runtimeInfoFlags` parametresi, yalnızca birini belirtebilir mimarisi sabitleri `RUNTIME_INFO_FLAGS` sabit bir zaman:</span><span class="sxs-lookup"><span data-stu-id="f1c8f-138">For the `runtimeInfoFlags` parameter, you can specify only one of the architecture constants of the `RUNTIME_INFO_FLAGS` enumeration at a time:</span></span>  
  
-   <span data-ttu-id="f1c8f-139">RUNTIME_INFO_REQUEST_IA64</span><span class="sxs-lookup"><span data-stu-id="f1c8f-139">RUNTIME_INFO_REQUEST_IA64</span></span>  
  
-   <span data-ttu-id="f1c8f-140">RUNTIME_INFO_REQUEST_AMD64</span><span class="sxs-lookup"><span data-stu-id="f1c8f-140">RUNTIME_INFO_REQUEST_AMD64</span></span>  
  
-   <span data-ttu-id="f1c8f-141">RUNTIME_INFO_REQUEST_X86</span><span class="sxs-lookup"><span data-stu-id="f1c8f-141">RUNTIME_INFO_REQUEST_X86</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1c8f-142">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f1c8f-142">Requirements</span></span>  
 <span data-ttu-id="f1c8f-143">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1c8f-143">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1c8f-144">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f1c8f-144">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f1c8f-145">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f1c8f-145">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f1c8f-146">**.NET framework sürümleri:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1c8f-146">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1c8f-147">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f1c8f-147">See Also</span></span>  
 [<span data-ttu-id="f1c8f-148">GetRequestedRuntimeVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="f1c8f-148">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
 [<span data-ttu-id="f1c8f-149">GetVersionFromProcess İşlevi</span><span class="sxs-lookup"><span data-stu-id="f1c8f-149">GetVersionFromProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)  
 [<span data-ttu-id="f1c8f-150">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="f1c8f-150">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
