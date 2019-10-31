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
ms.openlocfilehash: cd1d9e768698115bee22e35699b044e0c3526d2d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136317"
---
# <a name="getrequestedruntimeinfo-function"></a><span data-ttu-id="f3aef-102">GetRequestedRuntimeInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="f3aef-102">GetRequestedRuntimeInfo Function</span></span>
<span data-ttu-id="f3aef-103">Bir uygulama tarafından istenen ortak dil çalışma zamanı (CLR) hakkındaki sürüm ve dizin bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="f3aef-103">Gets version and directory information about the common language runtime (CLR) requested by an application.</span></span>  
  
 <span data-ttu-id="f3aef-104">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="f3aef-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3aef-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f3aef-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="f3aef-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f3aef-106">Parameters</span></span>  
 `pExe`  
 <span data-ttu-id="f3aef-107">'ndaki Uygulamanın adı.</span><span class="sxs-lookup"><span data-stu-id="f3aef-107">[in] The name of the application.</span></span>  
  
 `pwszVersion`  
 <span data-ttu-id="f3aef-108">'ndaki Çalışma zamanının sürüm numarasını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="f3aef-108">[in] A string specifying the version number of the runtime.</span></span>  
  
 `pConfigurationFile`  
 <span data-ttu-id="f3aef-109">'ndaki `pExe`ilişkili yapılandırma dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="f3aef-109">[in] The name of the configuration file that is associated with `pExe`.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="f3aef-110">'ndaki Bir veya daha fazla [startup_flags](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="f3aef-110">[in] One or more of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration values.</span></span>  
  
 `runtimeInfoFlags`  
 <span data-ttu-id="f3aef-111">'ndaki Bir veya daha fazla [RUNTIME_INFO_FLAGS](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md) numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="f3aef-111">[in] One or more of the [RUNTIME_INFO_FLAGS](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md) enumeration values.</span></span>  
  
 `pDirectory`  
 <span data-ttu-id="f3aef-112">dışı Başarılı bir şekilde tamamlandıktan sonra çalışma zamanına ait dizin yolunu içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="f3aef-112">[out] A buffer that contains the directory path to the runtime upon successful completion.</span></span>  
  
 `dwDirectory`  
 <span data-ttu-id="f3aef-113">'ndaki Dizin arabelleğinin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="f3aef-113">[in] The length of the directory buffer.</span></span>  
  
 `dwDirectoryLength`  
 <span data-ttu-id="f3aef-114">dışı Dizin yolu dizesinin uzunluğuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f3aef-114">[out] A pointer to the length of the directory path string.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="f3aef-115">dışı Başarılı bir şekilde tamamlandıktan sonra çalışma zamanının sürüm numarasını içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="f3aef-115">[out] A buffer that contains the version number of the runtime upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="f3aef-116">'ndaki Sürüm dizesi arabelleğinin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="f3aef-116">[in] The length of the version string buffer.</span></span>  
  
 `dwlength`  
 <span data-ttu-id="f3aef-117">dışı Sürüm dizesinin uzunluğuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f3aef-117">[out] A pointer to the length of the version string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f3aef-118">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f3aef-118">Return Value</span></span>  
 <span data-ttu-id="f3aef-119">Bu yöntem, aşağıdaki değerlere ek olarak, WinError. h içinde tanımlanan standart bileşen nesne modeli (COM) hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="f3aef-119">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="f3aef-120">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="f3aef-120">Return code</span></span>|<span data-ttu-id="f3aef-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f3aef-121">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="f3aef-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="f3aef-122">S_OK</span></span>|<span data-ttu-id="f3aef-123">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="f3aef-123">The method completed successfully.</span></span>|  
|<span data-ttu-id="f3aef-124">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="f3aef-124">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="f3aef-125">Dizin arabelleği, dizin yolunu depolamaya yetecek kadar büyük değil.</span><span class="sxs-lookup"><span data-stu-id="f3aef-125">The directory buffer is not large enough to store the directory path.</span></span><br /><br /> <span data-ttu-id="f3aef-126">veya</span><span class="sxs-lookup"><span data-stu-id="f3aef-126">- or -</span></span><br /><br /> <span data-ttu-id="f3aef-127">Sürüm arabelleği, sürüm dizesini depolamak için yeterince büyük değil.</span><span class="sxs-lookup"><span data-stu-id="f3aef-127">The version buffer is not large enough to store the version string.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3aef-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f3aef-128">Remarks</span></span>  
 <span data-ttu-id="f3aef-129">`GetRequestedRuntimeInfo` yöntemi, işleme yüklenen sürüm hakkında, bilgisayarda yüklü en son sürüm olması gereken çalışma zamanı bilgilerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="f3aef-129">The `GetRequestedRuntimeInfo` method returns run-time information about the version loaded into the process, which is not necessarily the latest version installed on the computer.</span></span>  
  
 <span data-ttu-id="f3aef-130">.NET Framework sürüm 2,0 ' de, aşağıdaki gibi `GetRequestedRuntimeInfo` metodunu kullanarak en son yüklenen sürüm hakkında bilgi edinebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f3aef-130">In the .NET Framework version 2.0, you can get information about the latest installed version by using the `GetRequestedRuntimeInfo` method as follows:</span></span>  
  
- <span data-ttu-id="f3aef-131">`pExe`, `pwszVersion`ve `pConfigurationFile` parametrelerini null olarak belirtin.</span><span class="sxs-lookup"><span data-stu-id="f3aef-131">Specify the `pExe`, `pwszVersion`, and `pConfigurationFile` parameters as null.</span></span>  
  
- <span data-ttu-id="f3aef-132">`runtimeInfoFlags` parametresi için `RUNTIME_INFO_FLAGS` numaralandırmalar içinde RUNTIME_INFO_UPGRADE_VERSION bayrağını belirtin.</span><span class="sxs-lookup"><span data-stu-id="f3aef-132">Specify the RUNTIME_INFO_UPGRADE_VERSION flag in the `RUNTIME_INFO_FLAGS` enumerations for the `runtimeInfoFlags` parameter.</span></span>  
  
 <span data-ttu-id="f3aef-133">`GetRequestedRuntimeInfo` yöntemi, aşağıdaki durumlarda en son CLR sürümünü döndürmez:</span><span class="sxs-lookup"><span data-stu-id="f3aef-133">The `GetRequestedRuntimeInfo` method does not return the latest CLR version in the following circumstances:</span></span>  
  
- <span data-ttu-id="f3aef-134">Belirli bir CLR sürümünü yüklemeyi belirten bir uygulama yapılandırma dosyası var.</span><span class="sxs-lookup"><span data-stu-id="f3aef-134">An application configuration file that specifies loading a particular CLR version exists.</span></span> <span data-ttu-id="f3aef-135">`pConfigurationFile` parametresi için null belirtseniz bile .NET Framework yapılandırma dosyasını kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="f3aef-135">Note that the .NET Framework will use the configuration file even if you specify null for the `pConfigurationFile` parameter.</span></span>  
  
- <span data-ttu-id="f3aef-136">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) yöntemi, ÖNCEKI bir clr sürümü belirtilerek çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="f3aef-136">The [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) method was called specifying an earlier CLR version.</span></span>  
  
- <span data-ttu-id="f3aef-137">Daha önceki bir CLR sürümü için derlenen bir uygulama şu anda çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="f3aef-137">An application that was compiled for an earlier CLR version is currently running.</span></span>  
  
 <span data-ttu-id="f3aef-138">`runtimeInfoFlags` parametresi için aynı anda `RUNTIME_INFO_FLAGS` numaralandırmanın mimari sabitlerinden yalnızca birini belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f3aef-138">For the `runtimeInfoFlags` parameter, you can specify only one of the architecture constants of the `RUNTIME_INFO_FLAGS` enumeration at a time:</span></span>  
  
- <span data-ttu-id="f3aef-139">RUNTIME_INFO_REQUEST_IA64</span><span class="sxs-lookup"><span data-stu-id="f3aef-139">RUNTIME_INFO_REQUEST_IA64</span></span>  
  
- <span data-ttu-id="f3aef-140">RUNTIME_INFO_REQUEST_AMD64</span><span class="sxs-lookup"><span data-stu-id="f3aef-140">RUNTIME_INFO_REQUEST_AMD64</span></span>  
  
- <span data-ttu-id="f3aef-141">RUNTIME_INFO_REQUEST_X86</span><span class="sxs-lookup"><span data-stu-id="f3aef-141">RUNTIME_INFO_REQUEST_X86</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3aef-142">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f3aef-142">Requirements</span></span>  
 <span data-ttu-id="f3aef-143">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3aef-143">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3aef-144">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f3aef-144">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f3aef-145">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f3aef-145">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f3aef-146">**.NET Framework sürümleri:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3aef-146">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3aef-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f3aef-147">See also</span></span>

- [<span data-ttu-id="f3aef-148">GetRequestedRuntimeVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="f3aef-148">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [<span data-ttu-id="f3aef-149">GetVersionFromProcess İşlevi</span><span class="sxs-lookup"><span data-stu-id="f3aef-149">GetVersionFromProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [<span data-ttu-id="f3aef-150">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="f3aef-150">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
