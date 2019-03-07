---
title: ICLRRuntimeInfo::LoadErrorString Yöntemi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a565c19285b00c807ef6fbfc018a40467139638e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466355"
---
# <a name="iclrruntimeinfoloaderrorstring-method"></a><span data-ttu-id="1437e-102">ICLRRuntimeInfo::LoadErrorString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1437e-102">ICLRRuntimeInfo::LoadErrorString Method</span></span>
<span data-ttu-id="1437e-103">HRESULT değerini belirtilen kültür için bir uygun hata iletisine çevirir.</span><span class="sxs-lookup"><span data-stu-id="1437e-103">Translates an HRESULT value into an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="1437e-104">Bu yöntem, aşağıdaki işlevleri yerine geçer:</span><span class="sxs-lookup"><span data-stu-id="1437e-104">This method supersedes the following functions:</span></span>  
  
-   [<span data-ttu-id="1437e-105">LoadStringRC</span><span class="sxs-lookup"><span data-stu-id="1437e-105">LoadStringRC</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
  
-   [<span data-ttu-id="1437e-106">LoadStringRCEx</span><span class="sxs-lookup"><span data-stu-id="1437e-106">LoadStringRCEx</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="1437e-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1437e-107">Syntax</span></span>  
  
```  
HRESULT LoadErrorString(  
     [in] UINT iResourceID,  
     [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
     [in, out]  DWORD *pcchBuffer,  
     [in, lcid] LONG iLocaleID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1437e-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1437e-108">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="1437e-109">[in] Çevrilecek HRESULT.</span><span class="sxs-lookup"><span data-stu-id="1437e-109">[in] The HRESULT to translate.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="1437e-110">[out] Verilen HRESULT ile ilişkili ileti dizesi.</span><span class="sxs-lookup"><span data-stu-id="1437e-110">[out] The message string associated with the given HRESULT.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="1437e-111">[out içinde] Boyutu `pwzbuffer` arabellek taşması önlemek için.</span><span class="sxs-lookup"><span data-stu-id="1437e-111">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="1437e-112">Varsa `pwzbuffer` boş `pcchBuffer` beklenen boyutu sağlar `pwzbuffer` serilerindeki izin vermek için.</span><span class="sxs-lookup"><span data-stu-id="1437e-112">If `pwzbuffer` is null, `pcchBuffer` provides the expected size of `pwzbuffer` to allow preallocation.</span></span>  
  
 `iLocaleID`  
 <span data-ttu-id="1437e-113">[in] Kültür tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="1437e-113">[in] The culture identifier.</span></span> <span data-ttu-id="1437e-114">Varsayılan kültürü kullanmak için -1 belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1437e-114">To use the default culture, you must specify -1.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1437e-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1437e-115">Return Value</span></span>  
 <span data-ttu-id="1437e-116">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="1437e-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="1437e-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1437e-117">HRESULT</span></span>|<span data-ttu-id="1437e-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1437e-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1437e-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="1437e-119">S_OK</span></span>|<span data-ttu-id="1437e-120">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="1437e-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="1437e-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="1437e-121">E_POINTER</span></span>|<span data-ttu-id="1437e-122">`pcchBuffer` NULL olur.</span><span class="sxs-lookup"><span data-stu-id="1437e-122">`pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="1437e-123">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="1437e-123">E_INVALIDARG</span></span>|<span data-ttu-id="1437e-124">`pwzBuffer` NULL olur.</span><span class="sxs-lookup"><span data-stu-id="1437e-124">`pwzBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1437e-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1437e-125">Requirements</span></span>  
 <span data-ttu-id="1437e-126">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1437e-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1437e-127">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="1437e-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="1437e-128">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="1437e-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1437e-129">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1437e-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1437e-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1437e-130">See also</span></span>
- [<span data-ttu-id="1437e-131">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1437e-131">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="1437e-132">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1437e-132">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="1437e-133">Barındırma</span><span class="sxs-lookup"><span data-stu-id="1437e-133">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
