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
ms.openlocfilehash: 0efda458d51677fcd16140cd0f0a835b76c20173
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617184"
---
# <a name="getrequestedruntimeinfo-function"></a><span data-ttu-id="49dd1-102">GetRequestedRuntimeInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="49dd1-102">GetRequestedRuntimeInfo Function</span></span>
<span data-ttu-id="49dd1-103">Bir uygulama tarafından istenen ortak dil çalışma zamanı (CLR) hakkındaki sürüm ve dizin bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="49dd1-103">Gets version and directory information about the common language runtime (CLR) requested by an application.</span></span>  
  
 <span data-ttu-id="49dd1-104">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="49dd1-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49dd1-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="49dd1-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="49dd1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="49dd1-106">Parameters</span></span>  
 `pExe`  
 <span data-ttu-id="49dd1-107">'ndaki Uygulamanın adı.</span><span class="sxs-lookup"><span data-stu-id="49dd1-107">[in] The name of the application.</span></span>  
  
 `pwszVersion`  
 <span data-ttu-id="49dd1-108">'ndaki Çalışma zamanının sürüm numarasını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="49dd1-108">[in] A string specifying the version number of the runtime.</span></span>  
  
 `pConfigurationFile`  
 <span data-ttu-id="49dd1-109">'ndaki İle ilişkili yapılandırma dosyasının adı `pExe` .</span><span class="sxs-lookup"><span data-stu-id="49dd1-109">[in] The name of the configuration file that is associated with `pExe`.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="49dd1-110">'ndaki Bir veya daha fazla [startup_flags](startup-flags-enumeration.md) numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="49dd1-110">[in] One or more of the [STARTUP_FLAGS](startup-flags-enumeration.md) enumeration values.</span></span>  
  
 `runtimeInfoFlags`  
 <span data-ttu-id="49dd1-111">'ndaki Bir veya daha fazla [RUNTIME_INFO_FLAGS](runtime-info-flags-enumeration.md) numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="49dd1-111">[in] One or more of the [RUNTIME_INFO_FLAGS](runtime-info-flags-enumeration.md) enumeration values.</span></span>  
  
 `pDirectory`  
 <span data-ttu-id="49dd1-112">dışı Başarılı bir şekilde tamamlandıktan sonra çalışma zamanına ait dizin yolunu içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="49dd1-112">[out] A buffer that contains the directory path to the runtime upon successful completion.</span></span>  
  
 `dwDirectory`  
 <span data-ttu-id="49dd1-113">'ndaki Dizin arabelleğinin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="49dd1-113">[in] The length of the directory buffer.</span></span>  
  
 `dwDirectoryLength`  
 <span data-ttu-id="49dd1-114">dışı Dizin yolu dizesinin uzunluğuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="49dd1-114">[out] A pointer to the length of the directory path string.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="49dd1-115">dışı Başarılı bir şekilde tamamlandıktan sonra çalışma zamanının sürüm numarasını içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="49dd1-115">[out] A buffer that contains the version number of the runtime upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="49dd1-116">'ndaki Sürüm dizesi arabelleğinin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="49dd1-116">[in] The length of the version string buffer.</span></span>  
  
 `dwlength`  
 <span data-ttu-id="49dd1-117">dışı Sürüm dizesinin uzunluğuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="49dd1-117">[out] A pointer to the length of the version string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="49dd1-118">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="49dd1-118">Return Value</span></span>  
 <span data-ttu-id="49dd1-119">Bu yöntem, aşağıdaki değerlere ek olarak, WinError. h içinde tanımlanan standart bileşen nesne modeli (COM) hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="49dd1-119">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="49dd1-120">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="49dd1-120">Return code</span></span>|<span data-ttu-id="49dd1-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="49dd1-121">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="49dd1-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="49dd1-122">S_OK</span></span>|<span data-ttu-id="49dd1-123">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="49dd1-123">The method completed successfully.</span></span>|  
|<span data-ttu-id="49dd1-124">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="49dd1-124">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="49dd1-125">Dizin arabelleği, dizin yolunu depolamaya yetecek kadar büyük değil.</span><span class="sxs-lookup"><span data-stu-id="49dd1-125">The directory buffer is not large enough to store the directory path.</span></span><br /><br /> <span data-ttu-id="49dd1-126">- veya -</span><span class="sxs-lookup"><span data-stu-id="49dd1-126">- or -</span></span><br /><br /> <span data-ttu-id="49dd1-127">Sürüm arabelleği, sürüm dizesini depolamak için yeterince büyük değil.</span><span class="sxs-lookup"><span data-stu-id="49dd1-127">The version buffer is not large enough to store the version string.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="49dd1-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="49dd1-128">Remarks</span></span>  
 <span data-ttu-id="49dd1-129">`GetRequestedRuntimeInfo`Yöntemi, işleme yüklenen sürüm hakkında, bilgisayarda yüklü en son sürüm olması gereken çalışma zamanı bilgilerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="49dd1-129">The `GetRequestedRuntimeInfo` method returns run-time information about the version loaded into the process, which is not necessarily the latest version installed on the computer.</span></span>  
  
 <span data-ttu-id="49dd1-130">.NET Framework sürüm 2,0 ' de, aşağıdaki gibi yöntemi kullanarak en son yüklenen sürüm hakkında bilgi edinebilirsiniz `GetRequestedRuntimeInfo` :</span><span class="sxs-lookup"><span data-stu-id="49dd1-130">In the .NET Framework version 2.0, you can get information about the latest installed version by using the `GetRequestedRuntimeInfo` method as follows:</span></span>  
  
- <span data-ttu-id="49dd1-131">`pExe`, `pwszVersion` Ve `pConfigurationFile` parametrelerini null olarak belirtin.</span><span class="sxs-lookup"><span data-stu-id="49dd1-131">Specify the `pExe`, `pwszVersion`, and `pConfigurationFile` parameters as null.</span></span>  
  
- <span data-ttu-id="49dd1-132">`RUNTIME_INFO_FLAGS`Parametre için numaralandırmalar RUNTIME_INFO_UPGRADE_VERSION bayrağını belirtin `runtimeInfoFlags` .</span><span class="sxs-lookup"><span data-stu-id="49dd1-132">Specify the RUNTIME_INFO_UPGRADE_VERSION flag in the `RUNTIME_INFO_FLAGS` enumerations for the `runtimeInfoFlags` parameter.</span></span>  
  
 <span data-ttu-id="49dd1-133">`GetRequestedRuntimeInfo`Yöntemi aşağıdaki koşullarda en son CLR sürümünü döndürmez:</span><span class="sxs-lookup"><span data-stu-id="49dd1-133">The `GetRequestedRuntimeInfo` method does not return the latest CLR version in the following circumstances:</span></span>  
  
- <span data-ttu-id="49dd1-134">Belirli bir CLR sürümünü yüklemeyi belirten bir uygulama yapılandırma dosyası var.</span><span class="sxs-lookup"><span data-stu-id="49dd1-134">An application configuration file that specifies loading a particular CLR version exists.</span></span> <span data-ttu-id="49dd1-135">Parametresi için null belirtseniz bile .NET Framework yapılandırma dosyasını kullanacaktır `pConfigurationFile` .</span><span class="sxs-lookup"><span data-stu-id="49dd1-135">Note that the .NET Framework will use the configuration file even if you specify null for the `pConfigurationFile` parameter.</span></span>  
  
- <span data-ttu-id="49dd1-136">[CorBindToRuntimeEx](corbindtoruntimeex-function.md) yöntemi, ÖNCEKI bir clr sürümü belirtilerek çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="49dd1-136">The [CorBindToRuntimeEx](corbindtoruntimeex-function.md) method was called specifying an earlier CLR version.</span></span>  
  
- <span data-ttu-id="49dd1-137">Daha önceki bir CLR sürümü için derlenen bir uygulama şu anda çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="49dd1-137">An application that was compiled for an earlier CLR version is currently running.</span></span>  
  
 <span data-ttu-id="49dd1-138">Parametresi için `runtimeInfoFlags` , tek seferde numaralandırmanın mimari sabitlerinden yalnızca birini belirtebilirsiniz `RUNTIME_INFO_FLAGS` :</span><span class="sxs-lookup"><span data-stu-id="49dd1-138">For the `runtimeInfoFlags` parameter, you can specify only one of the architecture constants of the `RUNTIME_INFO_FLAGS` enumeration at a time:</span></span>  
  
- <span data-ttu-id="49dd1-139">RUNTIME_INFO_REQUEST_IA64</span><span class="sxs-lookup"><span data-stu-id="49dd1-139">RUNTIME_INFO_REQUEST_IA64</span></span>  
  
- <span data-ttu-id="49dd1-140">RUNTIME_INFO_REQUEST_AMD64</span><span class="sxs-lookup"><span data-stu-id="49dd1-140">RUNTIME_INFO_REQUEST_AMD64</span></span>  
  
- <span data-ttu-id="49dd1-141">RUNTIME_INFO_REQUEST_X86</span><span class="sxs-lookup"><span data-stu-id="49dd1-141">RUNTIME_INFO_REQUEST_X86</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49dd1-142">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="49dd1-142">Requirements</span></span>  
 <span data-ttu-id="49dd1-143">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49dd1-143">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49dd1-144">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="49dd1-144">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="49dd1-145">**Kitaplık:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="49dd1-145">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="49dd1-146">**.NET Framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49dd1-146">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49dd1-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="49dd1-147">See also</span></span>

- [<span data-ttu-id="49dd1-148">GetRequestedRuntimeVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="49dd1-148">GetRequestedRuntimeVersion Function</span></span>](getrequestedruntimeversion-function.md)
- [<span data-ttu-id="49dd1-149">GetVersionFromProcess İşlevi</span><span class="sxs-lookup"><span data-stu-id="49dd1-149">GetVersionFromProcess Function</span></span>](getversionfromprocess-function.md)
- [<span data-ttu-id="49dd1-150">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="49dd1-150">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
