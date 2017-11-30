---
title: "ICLRRuntimeInfo::LoadErrorString Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.LoadErrorString
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::LoadErrorString
helpviewer_keywords:
- ICLRRuntimeInfo::LoadErrorString method [.NET Framework hosting]
- LoadErrorString method [.NET Framework hosting]
ms.assetid: 52c543ab-9ef5-4ee7-b836-c0ffc35cd45b
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 26fa051e5c4735307edbb443e6615a57190c0ae5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimeinfoloaderrorstring-method"></a><span data-ttu-id="0a2d4-102">ICLRRuntimeInfo::LoadErrorString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0a2d4-102">ICLRRuntimeInfo::LoadErrorString Method</span></span>
<span data-ttu-id="0a2d4-103">Uygun bir hata iletisi belirtilen kültür için bir HRESULT değeri çevirir.</span><span class="sxs-lookup"><span data-stu-id="0a2d4-103">Translates an HRESULT value into an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="0a2d4-104">Bu yöntem, aşağıdaki işlevleri yerine geçiyor:</span><span class="sxs-lookup"><span data-stu-id="0a2d4-104">This method supersedes the following functions:</span></span>  
  
-   [<span data-ttu-id="0a2d4-105">LoadStringRC</span><span class="sxs-lookup"><span data-stu-id="0a2d4-105">LoadStringRC</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
  
-   [<span data-ttu-id="0a2d4-106">LoadStringRCEx</span><span class="sxs-lookup"><span data-stu-id="0a2d4-106">LoadStringRCEx</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="0a2d4-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0a2d4-107">Syntax</span></span>  
  
```  
HRESULT LoadErrorString(  
     [in] UINT iResourceID,  
     [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
     [in, out]  DWORD *pcchBuffer,  
     [in, lcid] LONG iLocaleID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0a2d4-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0a2d4-108">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="0a2d4-109">[in] Çevir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="0a2d4-109">[in] The HRESULT to translate.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="0a2d4-110">[out] Verilen HRESULT ile ilişkili ileti dizesi.</span><span class="sxs-lookup"><span data-stu-id="0a2d4-110">[out] The message string associated with the given HRESULT.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="0a2d4-111">[içinde out] Boyutunu `pwzbuffer` arabellek taşmaları önlemek için.</span><span class="sxs-lookup"><span data-stu-id="0a2d4-111">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="0a2d4-112">Varsa `pwzbuffer` null, `pcchBuffer` beklenen boyutu sağlar `pwzbuffer` ön tahsis izin vermek için.</span><span class="sxs-lookup"><span data-stu-id="0a2d4-112">If `pwzbuffer` is null, `pcchBuffer` provides the expected size of `pwzbuffer` to allow preallocation.</span></span>  
  
 `iLocaleID`  
 <span data-ttu-id="0a2d4-113">[in] Bir kültür tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="0a2d4-113">[in] The culture identifier.</span></span> <span data-ttu-id="0a2d4-114">Varsayılan kültürü kullanmak için -1 belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0a2d4-114">To use the default culture, you must specify -1.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0a2d4-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0a2d4-115">Return Value</span></span>  
 <span data-ttu-id="0a2d4-116">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="0a2d4-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="0a2d4-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0a2d4-117">HRESULT</span></span>|<span data-ttu-id="0a2d4-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0a2d4-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0a2d4-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="0a2d4-119">S_OK</span></span>|<span data-ttu-id="0a2d4-120">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="0a2d4-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="0a2d4-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="0a2d4-121">E_POINTER</span></span>|<span data-ttu-id="0a2d4-122">`pcchBuffer`null şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="0a2d4-122">`pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="0a2d4-123">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="0a2d4-123">E_INVALIDARG</span></span>|<span data-ttu-id="0a2d4-124">`pwzBuffer`null şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="0a2d4-124">`pwzBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0a2d4-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0a2d4-125">Requirements</span></span>  
 <span data-ttu-id="0a2d4-126">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a2d4-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a2d4-127">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="0a2d4-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="0a2d4-128">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="0a2d4-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0a2d4-129">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a2d4-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a2d4-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0a2d4-130">See Also</span></span>  
 [<span data-ttu-id="0a2d4-131">Iclrruntimeınfo arabirimi</span><span class="sxs-lookup"><span data-stu-id="0a2d4-131">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="0a2d4-132">Barındırma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0a2d4-132">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="0a2d4-133">Barındırma</span><span class="sxs-lookup"><span data-stu-id="0a2d4-133">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
