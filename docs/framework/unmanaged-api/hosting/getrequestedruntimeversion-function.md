---
title: GetRequestedRuntimeVersion İşlevi
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeVersion
helpviewer_keywords:
- GetRequestedRuntimeVersion function [.NET Framework hosting]
ms.assetid: 82f596a4-483d-4509-b0c5-a84c53c3da1b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4083440903e6147ae645f2d6420f19160471841c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779582"
---
# <a name="getrequestedruntimeversion-function"></a><span data-ttu-id="05da6-102">GetRequestedRuntimeVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="05da6-102">GetRequestedRuntimeVersion Function</span></span>
<span data-ttu-id="05da6-103">Belirtilen uygulamanın istediği ortak dil çalışma zamanı (CLR) sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="05da6-103">Gets the version number of the common language runtime (CLR) requested by the specified application.</span></span> <span data-ttu-id="05da6-104">Bu sürüm yüklü değilse istenen sürümden önce yüklenen en son sürümü alır.</span><span class="sxs-lookup"><span data-stu-id="05da6-104">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 <span data-ttu-id="05da6-105">Bu işlev .NET Framework 4'te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="05da6-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05da6-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="05da6-106">Syntax</span></span>  
  
```cpp  
HRESULT GetRequestedRuntimeVersion (  
    [in]  LPWSTR  pExe,   
    [out] LPWSTR  pVersion,   
    [in]  DWORD   cchBuffer,   
    [out] DWORD  *pdwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05da6-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="05da6-107">Parameters</span></span>  
 `pExe`  
 <span data-ttu-id="05da6-108">[in] Uygulamanın adı.</span><span class="sxs-lookup"><span data-stu-id="05da6-108">[in] The name of the application.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="05da6-109">[out] Başarıyla tamamlandıktan sonra sürüm numarası dizesi içeren bir arabelleği.</span><span class="sxs-lookup"><span data-stu-id="05da6-109">[out] A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="05da6-110">[in] Sürüm arabellek uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="05da6-110">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="05da6-111">[out] Sürüm numarası dizenin uzunluğu bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="05da6-111">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="05da6-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="05da6-112">Return Value</span></span>  
 <span data-ttu-id="05da6-113">Bu yöntem standart Bileşen Nesne Modeli (COM) hata kodları, ek olarak aşağıdaki değerleri Wınerror içinde tanımlanan döndürür.</span><span class="sxs-lookup"><span data-stu-id="05da6-113">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="05da6-114">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="05da6-114">Return code</span></span>|<span data-ttu-id="05da6-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="05da6-115">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="05da6-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="05da6-116">S_OK</span></span>|<span data-ttu-id="05da6-117">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="05da6-117">The method completed successfully.</span></span>|  
|<span data-ttu-id="05da6-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="05da6-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="05da6-119">Sürüm arabellek sürüm dizesi depolamak için yeterli büyüklükte değil.</span><span class="sxs-lookup"><span data-stu-id="05da6-119">The version buffer is not large enough to store the version string.</span></span>|  
|<span data-ttu-id="05da6-120">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="05da6-120">E_POINTER</span></span>|<span data-ttu-id="05da6-121">`pdwLength` NULL olur.</span><span class="sxs-lookup"><span data-stu-id="05da6-121">`pdwLength` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="05da6-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="05da6-122">Requirements</span></span>  
 <span data-ttu-id="05da6-123">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05da6-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05da6-124">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="05da6-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="05da6-125">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="05da6-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="05da6-126">**.NET framework sürümleri:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05da6-126">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05da6-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05da6-127">See also</span></span>

- [<span data-ttu-id="05da6-128">GetRequestedRuntimeInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="05da6-128">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="05da6-129">GetVersionFromProcess İşlevi</span><span class="sxs-lookup"><span data-stu-id="05da6-129">GetVersionFromProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [<span data-ttu-id="05da6-130">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="05da6-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
