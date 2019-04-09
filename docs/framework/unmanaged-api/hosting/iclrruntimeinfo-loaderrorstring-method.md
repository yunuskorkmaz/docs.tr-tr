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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59154693"
---
# <a name="iclrruntimeinfoloaderrorstring-method"></a><span data-ttu-id="68beb-102">ICLRRuntimeInfo::LoadErrorString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="68beb-102">ICLRRuntimeInfo::LoadErrorString Method</span></span>
<span data-ttu-id="68beb-103">HRESULT değerini belirtilen kültür için bir uygun hata iletisine çevirir.</span><span class="sxs-lookup"><span data-stu-id="68beb-103">Translates an HRESULT value into an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="68beb-104">Bu yöntem, aşağıdaki işlevleri yerine geçer:</span><span class="sxs-lookup"><span data-stu-id="68beb-104">This method supersedes the following functions:</span></span>  
  
-   [<span data-ttu-id="68beb-105">LoadStringRC</span><span class="sxs-lookup"><span data-stu-id="68beb-105">LoadStringRC</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
  
-   [<span data-ttu-id="68beb-106">LoadStringRCEx</span><span class="sxs-lookup"><span data-stu-id="68beb-106">LoadStringRCEx</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="68beb-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="68beb-107">Syntax</span></span>  
  
```  
HRESULT LoadErrorString(  
     [in] UINT iResourceID,  
     [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
     [in, out]  DWORD *pcchBuffer,  
     [in, lcid] LONG iLocaleID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68beb-108">Parametreler</span><span class="sxs-lookup"><span data-stu-id="68beb-108">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="68beb-109">[in] Çevrilecek HRESULT.</span><span class="sxs-lookup"><span data-stu-id="68beb-109">[in] The HRESULT to translate.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="68beb-110">[out] Verilen HRESULT ile ilişkili ileti dizesi.</span><span class="sxs-lookup"><span data-stu-id="68beb-110">[out] The message string associated with the given HRESULT.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="68beb-111">[out içinde] Boyutu `pwzbuffer` arabellek taşması önlemek için.</span><span class="sxs-lookup"><span data-stu-id="68beb-111">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="68beb-112">Varsa `pwzbuffer` boş `pcchBuffer` beklenen boyutu sağlar `pwzbuffer` serilerindeki izin vermek için.</span><span class="sxs-lookup"><span data-stu-id="68beb-112">If `pwzbuffer` is null, `pcchBuffer` provides the expected size of `pwzbuffer` to allow preallocation.</span></span>  
  
 `iLocaleID`  
 <span data-ttu-id="68beb-113">[in] Kültür tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="68beb-113">[in] The culture identifier.</span></span> <span data-ttu-id="68beb-114">Varsayılan kültürü kullanmak için -1 belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="68beb-114">To use the default culture, you must specify -1.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="68beb-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="68beb-115">Return Value</span></span>  
 <span data-ttu-id="68beb-116">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="68beb-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="68beb-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="68beb-117">HRESULT</span></span>|<span data-ttu-id="68beb-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="68beb-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="68beb-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="68beb-119">S_OK</span></span>|<span data-ttu-id="68beb-120">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="68beb-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="68beb-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="68beb-121">E_POINTER</span></span>|`pcchBuffer` <span data-ttu-id="68beb-122">NULL olur.</span><span class="sxs-lookup"><span data-stu-id="68beb-122">is null.</span></span>|  
|<span data-ttu-id="68beb-123">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="68beb-123">E_INVALIDARG</span></span>|`pwzBuffer` <span data-ttu-id="68beb-124">NULL olur.</span><span class="sxs-lookup"><span data-stu-id="68beb-124">is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="68beb-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="68beb-125">Requirements</span></span>  
 <span data-ttu-id="68beb-126">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68beb-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68beb-127">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="68beb-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="68beb-128">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="68beb-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="68beb-129">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="68beb-129">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="68beb-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68beb-130">See also</span></span>

- [<span data-ttu-id="68beb-131">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="68beb-131">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="68beb-132">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="68beb-132">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="68beb-133">Barındırma</span><span class="sxs-lookup"><span data-stu-id="68beb-133">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
