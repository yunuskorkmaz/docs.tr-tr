---
title: "ICLRRuntimeInfo::LoadErrorString Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRRuntimeInfo.LoadErrorString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::LoadErrorString
helpviewer_keywords:
- ICLRRuntimeInfo::LoadErrorString method [.NET Framework hosting]
- LoadErrorString method [.NET Framework hosting]
ms.assetid: 52c543ab-9ef5-4ee7-b836-c0ffc35cd45b
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d6253844e931b7b9126b2df28c7977eaa1d92d70
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimeinfoloaderrorstring-method"></a><span data-ttu-id="1557c-102">ICLRRuntimeInfo::LoadErrorString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1557c-102">ICLRRuntimeInfo::LoadErrorString Method</span></span>
<span data-ttu-id="1557c-103">Uygun bir hata iletisi belirtilen kültür için bir HRESULT değeri çevirir.</span><span class="sxs-lookup"><span data-stu-id="1557c-103">Translates an HRESULT value into an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="1557c-104">Bu yöntem, aşağıdaki işlevleri yerine geçiyor:</span><span class="sxs-lookup"><span data-stu-id="1557c-104">This method supersedes the following functions:</span></span>  
  
-   [<span data-ttu-id="1557c-105">LoadStringRC</span><span class="sxs-lookup"><span data-stu-id="1557c-105">LoadStringRC</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
  
-   [<span data-ttu-id="1557c-106">LoadStringRCEx</span><span class="sxs-lookup"><span data-stu-id="1557c-106">LoadStringRCEx</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="1557c-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1557c-107">Syntax</span></span>  
  
```  
HRESULT LoadErrorString(  
     [in] UINT iResourceID,  
     [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
     [in, out]  DWORD *pcchBuffer,  
     [in, lcid] LONG iLocaleID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1557c-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1557c-108">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="1557c-109">[in] Çevir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="1557c-109">[in] The HRESULT to translate.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="1557c-110">[out] Verilen HRESULT ile ilişkili ileti dizesi.</span><span class="sxs-lookup"><span data-stu-id="1557c-110">[out] The message string associated with the given HRESULT.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="1557c-111">[içinde out] Boyutunu `pwzbuffer` arabellek taşmaları önlemek için.</span><span class="sxs-lookup"><span data-stu-id="1557c-111">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="1557c-112">Varsa `pwzbuffer` null, `pcchBuffer` beklenen boyutu sağlar `pwzbuffer` ön tahsis izin vermek için.</span><span class="sxs-lookup"><span data-stu-id="1557c-112">If `pwzbuffer` is null, `pcchBuffer` provides the expected size of `pwzbuffer` to allow preallocation.</span></span>  
  
 `iLocaleID`  
 <span data-ttu-id="1557c-113">[in] Bir kültür tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="1557c-113">[in] The culture identifier.</span></span> <span data-ttu-id="1557c-114">Varsayılan kültürü kullanmak için -1 belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1557c-114">To use the default culture, you must specify -1.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1557c-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1557c-115">Return Value</span></span>  
 <span data-ttu-id="1557c-116">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="1557c-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="1557c-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1557c-117">HRESULT</span></span>|<span data-ttu-id="1557c-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1557c-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1557c-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="1557c-119">S_OK</span></span>|<span data-ttu-id="1557c-120">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="1557c-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="1557c-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="1557c-121">E_POINTER</span></span>|<span data-ttu-id="1557c-122">`pcchBuffer`null şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="1557c-122">`pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="1557c-123">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="1557c-123">E_INVALIDARG</span></span>|<span data-ttu-id="1557c-124">`pwzBuffer`null şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="1557c-124">`pwzBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1557c-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1557c-125">Requirements</span></span>  
 <span data-ttu-id="1557c-126">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1557c-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1557c-127">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="1557c-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="1557c-128">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="1557c-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1557c-129">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1557c-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1557c-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1557c-130">See Also</span></span>  
 [<span data-ttu-id="1557c-131">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1557c-131">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="1557c-132">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1557c-132">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="1557c-133">Barındırma</span><span class="sxs-lookup"><span data-stu-id="1557c-133">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
