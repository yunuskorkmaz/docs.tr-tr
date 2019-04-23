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
ms.openlocfilehash: b485811b0e7d2f657ff2d2c1d7a2aa135e48a335
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59154693"
---
# <a name="iclrruntimeinfoloaderrorstring-method"></a><span data-ttu-id="17407-102">ICLRRuntimeInfo::LoadErrorString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="17407-102">ICLRRuntimeInfo::LoadErrorString Method</span></span>
<span data-ttu-id="17407-103">HRESULT değerini belirtilen kültür için bir uygun hata iletisine çevirir.</span><span class="sxs-lookup"><span data-stu-id="17407-103">Translates an HRESULT value into an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="17407-104">Bu yöntem, aşağıdaki işlevleri yerine geçer:</span><span class="sxs-lookup"><span data-stu-id="17407-104">This method supersedes the following functions:</span></span>  
  
-   [<span data-ttu-id="17407-105">LoadStringRC</span><span class="sxs-lookup"><span data-stu-id="17407-105">LoadStringRC</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
  
-   [<span data-ttu-id="17407-106">LoadStringRCEx</span><span class="sxs-lookup"><span data-stu-id="17407-106">LoadStringRCEx</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="17407-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="17407-107">Syntax</span></span>  
  
```  
HRESULT LoadErrorString(  
     [in] UINT iResourceID,  
     [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
     [in, out]  DWORD *pcchBuffer,  
     [in, lcid] LONG iLocaleID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17407-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="17407-108">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="17407-109">[in] Çevrilecek HRESULT.</span><span class="sxs-lookup"><span data-stu-id="17407-109">[in] The HRESULT to translate.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="17407-110">[out] Verilen HRESULT ile ilişkili ileti dizesi.</span><span class="sxs-lookup"><span data-stu-id="17407-110">[out] The message string associated with the given HRESULT.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="17407-111">[out içinde] Boyutu `pwzbuffer` arabellek taşması önlemek için.</span><span class="sxs-lookup"><span data-stu-id="17407-111">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="17407-112">Varsa `pwzbuffer` boş `pcchBuffer` beklenen boyutu sağlar `pwzbuffer` serilerindeki izin vermek için.</span><span class="sxs-lookup"><span data-stu-id="17407-112">If `pwzbuffer` is null, `pcchBuffer` provides the expected size of `pwzbuffer` to allow preallocation.</span></span>  
  
 `iLocaleID`  
 <span data-ttu-id="17407-113">[in] Kültür tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="17407-113">[in] The culture identifier.</span></span> <span data-ttu-id="17407-114">Varsayılan kültürü kullanmak için -1 belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="17407-114">To use the default culture, you must specify -1.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="17407-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="17407-115">Return Value</span></span>  
 <span data-ttu-id="17407-116">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="17407-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="17407-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="17407-117">HRESULT</span></span>|<span data-ttu-id="17407-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="17407-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="17407-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="17407-119">S_OK</span></span>|<span data-ttu-id="17407-120">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="17407-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="17407-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="17407-121">E_POINTER</span></span>|<span data-ttu-id="17407-122">`pcchBuffer` NULL olur.</span><span class="sxs-lookup"><span data-stu-id="17407-122">`pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="17407-123">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="17407-123">E_INVALIDARG</span></span>|<span data-ttu-id="17407-124">`pwzBuffer` NULL olur.</span><span class="sxs-lookup"><span data-stu-id="17407-124">`pwzBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="17407-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="17407-125">Requirements</span></span>  
 <span data-ttu-id="17407-126">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17407-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17407-127">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="17407-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="17407-128">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="17407-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="17407-129">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17407-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17407-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17407-130">See also</span></span>

- [<span data-ttu-id="17407-131">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17407-131">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="17407-132">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="17407-132">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="17407-133">Barındırma</span><span class="sxs-lookup"><span data-stu-id="17407-133">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
