---
description: ': GetRequestedRuntimeInfo Işlevi hakkında daha fazla bilgi'
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
ms.openlocfilehash: 63d0bdcd07be5727cddc0acc352e8358b5ff0090
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785295"
---
# <a name="getrequestedruntimeinfo-function"></a><span data-ttu-id="2946d-103">GetRequestedRuntimeInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="2946d-103">GetRequestedRuntimeInfo Function</span></span>

<span data-ttu-id="2946d-104">Bir uygulama tarafından istenen ortak dil çalışma zamanı (CLR) hakkındaki sürüm ve dizin bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="2946d-104">Gets version and directory information about the common language runtime (CLR) requested by an application.</span></span>  
  
 <span data-ttu-id="2946d-105">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="2946d-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2946d-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2946d-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="2946d-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2946d-107">Parameters</span></span>  

 `pExe`  
 <span data-ttu-id="2946d-108">'ndaki Uygulamanın adı.</span><span class="sxs-lookup"><span data-stu-id="2946d-108">[in] The name of the application.</span></span>  
  
 `pwszVersion`  
 <span data-ttu-id="2946d-109">'ndaki Çalışma zamanının sürüm numarasını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="2946d-109">[in] A string specifying the version number of the runtime.</span></span>  
  
 `pConfigurationFile`  
 <span data-ttu-id="2946d-110">'ndaki İle ilişkili yapılandırma dosyasının adı `pExe` .</span><span class="sxs-lookup"><span data-stu-id="2946d-110">[in] The name of the configuration file that is associated with `pExe`.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="2946d-111">'ndaki Bir veya daha fazla [startup_flags](startup-flags-enumeration.md) numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="2946d-111">[in] One or more of the [STARTUP_FLAGS](startup-flags-enumeration.md) enumeration values.</span></span>  
  
 `runtimeInfoFlags`  
 <span data-ttu-id="2946d-112">'ndaki Bir veya daha fazla [RUNTIME_INFO_FLAGS](runtime-info-flags-enumeration.md) numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="2946d-112">[in] One or more of the [RUNTIME_INFO_FLAGS](runtime-info-flags-enumeration.md) enumeration values.</span></span>  
  
 `pDirectory`  
 <span data-ttu-id="2946d-113">dışı Başarılı bir şekilde tamamlandıktan sonra çalışma zamanına ait dizin yolunu içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="2946d-113">[out] A buffer that contains the directory path to the runtime upon successful completion.</span></span>  
  
 `dwDirectory`  
 <span data-ttu-id="2946d-114">'ndaki Dizin arabelleğinin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="2946d-114">[in] The length of the directory buffer.</span></span>  
  
 `dwDirectoryLength`  
 <span data-ttu-id="2946d-115">dışı Dizin yolu dizesinin uzunluğuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2946d-115">[out] A pointer to the length of the directory path string.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="2946d-116">dışı Başarılı bir şekilde tamamlandıktan sonra çalışma zamanının sürüm numarasını içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="2946d-116">[out] A buffer that contains the version number of the runtime upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="2946d-117">'ndaki Sürüm dizesi arabelleğinin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="2946d-117">[in] The length of the version string buffer.</span></span>  
  
 `dwlength`  
 <span data-ttu-id="2946d-118">dışı Sürüm dizesinin uzunluğuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2946d-118">[out] A pointer to the length of the version string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2946d-119">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2946d-119">Return Value</span></span>  

 <span data-ttu-id="2946d-120">Bu yöntem, aşağıdaki değerlere ek olarak, WinError. h içinde tanımlanan standart bileşen nesne modeli (COM) hata kodlarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="2946d-120">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="2946d-121">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="2946d-121">Return code</span></span>|<span data-ttu-id="2946d-122">Description</span><span class="sxs-lookup"><span data-stu-id="2946d-122">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="2946d-123">S_OK</span><span class="sxs-lookup"><span data-stu-id="2946d-123">S_OK</span></span>|<span data-ttu-id="2946d-124">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="2946d-124">The method completed successfully.</span></span>|  
|<span data-ttu-id="2946d-125">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="2946d-125">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="2946d-126">Dizin arabelleği, dizin yolunu depolamaya yetecek kadar büyük değil.</span><span class="sxs-lookup"><span data-stu-id="2946d-126">The directory buffer is not large enough to store the directory path.</span></span><br /><br /> <span data-ttu-id="2946d-127">- veya -</span><span class="sxs-lookup"><span data-stu-id="2946d-127">- or -</span></span><br /><br /> <span data-ttu-id="2946d-128">Sürüm arabelleği, sürüm dizesini depolamak için yeterince büyük değil.</span><span class="sxs-lookup"><span data-stu-id="2946d-128">The version buffer is not large enough to store the version string.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2946d-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2946d-129">Remarks</span></span>  

 <span data-ttu-id="2946d-130">`GetRequestedRuntimeInfo`Yöntemi, işleme yüklenen sürüm hakkında, bilgisayarda yüklü en son sürüm olması gereken çalışma zamanı bilgilerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="2946d-130">The `GetRequestedRuntimeInfo` method returns run-time information about the version loaded into the process, which is not necessarily the latest version installed on the computer.</span></span>  
  
 <span data-ttu-id="2946d-131">.NET Framework sürüm 2,0 ' de, aşağıdaki gibi yöntemi kullanarak en son yüklenen sürüm hakkında bilgi edinebilirsiniz `GetRequestedRuntimeInfo` :</span><span class="sxs-lookup"><span data-stu-id="2946d-131">In the .NET Framework version 2.0, you can get information about the latest installed version by using the `GetRequestedRuntimeInfo` method as follows:</span></span>  
  
- <span data-ttu-id="2946d-132">`pExe`, `pwszVersion` Ve `pConfigurationFile` parametrelerini null olarak belirtin.</span><span class="sxs-lookup"><span data-stu-id="2946d-132">Specify the `pExe`, `pwszVersion`, and `pConfigurationFile` parameters as null.</span></span>  
  
- <span data-ttu-id="2946d-133">`RUNTIME_INFO_FLAGS`Parametre için numaralandırmalar RUNTIME_INFO_UPGRADE_VERSION bayrağını belirtin `runtimeInfoFlags` .</span><span class="sxs-lookup"><span data-stu-id="2946d-133">Specify the RUNTIME_INFO_UPGRADE_VERSION flag in the `RUNTIME_INFO_FLAGS` enumerations for the `runtimeInfoFlags` parameter.</span></span>  
  
 <span data-ttu-id="2946d-134">`GetRequestedRuntimeInfo`Yöntemi aşağıdaki koşullarda en son CLR sürümünü döndürmez:</span><span class="sxs-lookup"><span data-stu-id="2946d-134">The `GetRequestedRuntimeInfo` method does not return the latest CLR version in the following circumstances:</span></span>  
  
- <span data-ttu-id="2946d-135">Belirli bir CLR sürümünü yüklemeyi belirten bir uygulama yapılandırma dosyası var.</span><span class="sxs-lookup"><span data-stu-id="2946d-135">An application configuration file that specifies loading a particular CLR version exists.</span></span> <span data-ttu-id="2946d-136">Parametresi için null belirtseniz bile .NET Framework yapılandırma dosyasını kullanacaktır `pConfigurationFile` .</span><span class="sxs-lookup"><span data-stu-id="2946d-136">Note that the .NET Framework will use the configuration file even if you specify null for the `pConfigurationFile` parameter.</span></span>  
  
- <span data-ttu-id="2946d-137">[CorBindToRuntimeEx](corbindtoruntimeex-function.md) yöntemi, ÖNCEKI bir clr sürümü belirtilerek çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="2946d-137">The [CorBindToRuntimeEx](corbindtoruntimeex-function.md) method was called specifying an earlier CLR version.</span></span>  
  
- <span data-ttu-id="2946d-138">Daha önceki bir CLR sürümü için derlenen bir uygulama şu anda çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="2946d-138">An application that was compiled for an earlier CLR version is currently running.</span></span>  
  
 <span data-ttu-id="2946d-139">Parametresi için `runtimeInfoFlags` , tek seferde numaralandırmanın mimari sabitlerinden yalnızca birini belirtebilirsiniz `RUNTIME_INFO_FLAGS` :</span><span class="sxs-lookup"><span data-stu-id="2946d-139">For the `runtimeInfoFlags` parameter, you can specify only one of the architecture constants of the `RUNTIME_INFO_FLAGS` enumeration at a time:</span></span>  
  
- <span data-ttu-id="2946d-140">RUNTIME_INFO_REQUEST_IA64</span><span class="sxs-lookup"><span data-stu-id="2946d-140">RUNTIME_INFO_REQUEST_IA64</span></span>  
  
- <span data-ttu-id="2946d-141">RUNTIME_INFO_REQUEST_AMD64</span><span class="sxs-lookup"><span data-stu-id="2946d-141">RUNTIME_INFO_REQUEST_AMD64</span></span>  
  
- <span data-ttu-id="2946d-142">RUNTIME_INFO_REQUEST_X86</span><span class="sxs-lookup"><span data-stu-id="2946d-142">RUNTIME_INFO_REQUEST_X86</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2946d-143">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2946d-143">Requirements</span></span>  

 <span data-ttu-id="2946d-144">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2946d-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2946d-145">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2946d-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2946d-146">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2946d-146">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2946d-147">**.NET Framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2946d-147">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2946d-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2946d-148">See also</span></span>

- [<span data-ttu-id="2946d-149">GetRequestedRuntimeVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="2946d-149">GetRequestedRuntimeVersion Function</span></span>](getrequestedruntimeversion-function.md)
- [<span data-ttu-id="2946d-150">GetVersionFromProcess İşlevi</span><span class="sxs-lookup"><span data-stu-id="2946d-150">GetVersionFromProcess Function</span></span>](getversionfromprocess-function.md)
- [<span data-ttu-id="2946d-151">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="2946d-151">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
