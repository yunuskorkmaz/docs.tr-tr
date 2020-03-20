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
ms.openlocfilehash: db721e1ef774c87de0fa7da178463d832a3da756
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178149"
---
# <a name="getrequestedruntimeinfo-function"></a><span data-ttu-id="a4375-102">GetRequestedRuntimeInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="a4375-102">GetRequestedRuntimeInfo Function</span></span>
<span data-ttu-id="a4375-103">Bir uygulama tarafından istenen ortak dil çalışma süresi (CLR) hakkında sürüm ve dizin bilgileri alır.</span><span class="sxs-lookup"><span data-stu-id="a4375-103">Gets version and directory information about the common language runtime (CLR) requested by an application.</span></span>  
  
 <span data-ttu-id="a4375-104">Bu işlev .NET Framework 4'te amortismana hazırlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a4375-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4375-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a4375-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="a4375-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a4375-106">Parameters</span></span>  
 `pExe`  
 <span data-ttu-id="a4375-107">[içinde] Uygulamanın adı.</span><span class="sxs-lookup"><span data-stu-id="a4375-107">[in] The name of the application.</span></span>  
  
 `pwszVersion`  
 <span data-ttu-id="a4375-108">[içinde] Çalışma zamanının sürüm numarasını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="a4375-108">[in] A string specifying the version number of the runtime.</span></span>  
  
 `pConfigurationFile`  
 <span data-ttu-id="a4375-109">[içinde] `pExe`' ile ilişkili yapılandırma dosyasının adı</span><span class="sxs-lookup"><span data-stu-id="a4375-109">[in] The name of the configuration file that is associated with `pExe`.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="a4375-110">[içinde] numaralandırma değerlerinden biri veya birkaçı [STARTUP_FLAGS.](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="a4375-110">[in] One or more of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration values.</span></span>  
  
 `runtimeInfoFlags`  
 <span data-ttu-id="a4375-111">[içinde] [Numaralandırma değerlerinden](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md) biri veya birkaçı RUNTIME_INFO_FLAGS.</span><span class="sxs-lookup"><span data-stu-id="a4375-111">[in] One or more of the [RUNTIME_INFO_FLAGS](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md) enumeration values.</span></span>  
  
 `pDirectory`  
 <span data-ttu-id="a4375-112">[çıkış] Başarılı bir şekilde tamamlandığında çalışma zamanına giden dizin yolunu içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="a4375-112">[out] A buffer that contains the directory path to the runtime upon successful completion.</span></span>  
  
 `dwDirectory`  
 <span data-ttu-id="a4375-113">[içinde] Dizin arabelleği uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="a4375-113">[in] The length of the directory buffer.</span></span>  
  
 `dwDirectoryLength`  
 <span data-ttu-id="a4375-114">[çıkış] Dizin yolu dizesinin uzunluğuna işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a4375-114">[out] A pointer to the length of the directory path string.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="a4375-115">[çıkış] Başarılı bir şekilde tamamlandığında çalışma zamanının sürüm numarasını içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="a4375-115">[out] A buffer that contains the version number of the runtime upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="a4375-116">[içinde] Sürüm dize arabelleği uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="a4375-116">[in] The length of the version string buffer.</span></span>  
  
 `dwlength`  
 <span data-ttu-id="a4375-117">[çıkış] Sürüm dizesinin uzunluğuna işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a4375-117">[out] A pointer to the length of the version string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a4375-118">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a4375-118">Return Value</span></span>  
 <span data-ttu-id="a4375-119">Bu yöntem, aşağıdaki değerlere ek olarak WinError.h'de tanımlandığı şekilde standart Bileşen Nesne Modeli (COM) hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="a4375-119">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="a4375-120">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="a4375-120">Return code</span></span>|<span data-ttu-id="a4375-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4375-121">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="a4375-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="a4375-122">S_OK</span></span>|<span data-ttu-id="a4375-123">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="a4375-123">The method completed successfully.</span></span>|  
|<span data-ttu-id="a4375-124">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="a4375-124">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="a4375-125">Dizin arabelleği dizin yolunu depolamak için yeterince büyük değil.</span><span class="sxs-lookup"><span data-stu-id="a4375-125">The directory buffer is not large enough to store the directory path.</span></span><br /><br /> <span data-ttu-id="a4375-126">- veya -</span><span class="sxs-lookup"><span data-stu-id="a4375-126">- or -</span></span><br /><br /> <span data-ttu-id="a4375-127">Sürüm arabelleği sürüm dizesini depolamak için yeterince büyük değildir.</span><span class="sxs-lookup"><span data-stu-id="a4375-127">The version buffer is not large enough to store the version string.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4375-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a4375-128">Remarks</span></span>  
 <span data-ttu-id="a4375-129">Yöntem, `GetRequestedRuntimeInfo` işleme yüklenen sürüm le ilgili çalışma zamanı bilgilerini döndürür ve bu da bilgisayarda yüklü olan en son sürüm değildir.</span><span class="sxs-lookup"><span data-stu-id="a4375-129">The `GetRequestedRuntimeInfo` method returns run-time information about the version loaded into the process, which is not necessarily the latest version installed on the computer.</span></span>  
  
 <span data-ttu-id="a4375-130">.NET Framework sürüm 2.0'da, `GetRequestedRuntimeInfo` yöntemi aşağıdaki şekilde kullanarak en son yüklenen sürüm hakkında bilgi alabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a4375-130">In the .NET Framework version 2.0, you can get information about the latest installed version by using the `GetRequestedRuntimeInfo` method as follows:</span></span>  
  
- <span data-ttu-id="a4375-131">, `pExe` `pwszVersion`ve `pConfigurationFile` parametreleri null olarak belirtin.</span><span class="sxs-lookup"><span data-stu-id="a4375-131">Specify the `pExe`, `pwszVersion`, and `pConfigurationFile` parameters as null.</span></span>  
  
- <span data-ttu-id="a4375-132">Parametre için sayısallaştırmalarda `RUNTIME_INFO_FLAGS` RUNTIME_INFO_UPGRADE_VERSION bayrağı `runtimeInfoFlags` belirtin.</span><span class="sxs-lookup"><span data-stu-id="a4375-132">Specify the RUNTIME_INFO_UPGRADE_VERSION flag in the `RUNTIME_INFO_FLAGS` enumerations for the `runtimeInfoFlags` parameter.</span></span>  
  
 <span data-ttu-id="a4375-133">Yöntem, `GetRequestedRuntimeInfo` aşağıdaki durumlarda en son CLR sürümünü döndürmez:</span><span class="sxs-lookup"><span data-stu-id="a4375-133">The `GetRequestedRuntimeInfo` method does not return the latest CLR version in the following circumstances:</span></span>  
  
- <span data-ttu-id="a4375-134">Belirli bir CLR sürümünün yüklendiğini belirten bir uygulama yapılandırma dosyası vardır.</span><span class="sxs-lookup"><span data-stu-id="a4375-134">An application configuration file that specifies loading a particular CLR version exists.</span></span> <span data-ttu-id="a4375-135">.NET Framework'ün, parametre için null belirtseniz `pConfigurationFile` bile yapılandırma dosyasını kullanacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a4375-135">Note that the .NET Framework will use the configuration file even if you specify null for the `pConfigurationFile` parameter.</span></span>  
  
- <span data-ttu-id="a4375-136">[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) yöntemi daha önceki bir CLR sürümünü belirterek çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="a4375-136">The [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) method was called specifying an earlier CLR version.</span></span>  
  
- <span data-ttu-id="a4375-137">Önceki bir CLR sürümü için derlenen bir uygulama şu anda çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="a4375-137">An application that was compiled for an earlier CLR version is currently running.</span></span>  
  
 <span data-ttu-id="a4375-138">Parametre `runtimeInfoFlags` için, numaralandırmanın `RUNTIME_INFO_FLAGS` mimari sabitlerinden yalnızca birini bir defada belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a4375-138">For the `runtimeInfoFlags` parameter, you can specify only one of the architecture constants of the `RUNTIME_INFO_FLAGS` enumeration at a time:</span></span>  
  
- <span data-ttu-id="a4375-139">RUNTIME_INFO_REQUEST_IA64</span><span class="sxs-lookup"><span data-stu-id="a4375-139">RUNTIME_INFO_REQUEST_IA64</span></span>  
  
- <span data-ttu-id="a4375-140">RUNTIME_INFO_REQUEST_AMD64</span><span class="sxs-lookup"><span data-stu-id="a4375-140">RUNTIME_INFO_REQUEST_AMD64</span></span>  
  
- <span data-ttu-id="a4375-141">RUNTIME_INFO_REQUEST_X86</span><span class="sxs-lookup"><span data-stu-id="a4375-141">RUNTIME_INFO_REQUEST_X86</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4375-142">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a4375-142">Requirements</span></span>  
 <span data-ttu-id="a4375-143">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4375-143">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4375-144">**Üstbilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a4375-144">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a4375-145">**Kütüphane:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="a4375-145">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a4375-146">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4375-146">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4375-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4375-147">See also</span></span>

- [<span data-ttu-id="a4375-148">GetRequestedRuntimeVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="a4375-148">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [<span data-ttu-id="a4375-149">GetVersionFromProcess İşlevi</span><span class="sxs-lookup"><span data-stu-id="a4375-149">GetVersionFromProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [<span data-ttu-id="a4375-150">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="a4375-150">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
