---
title: ICLRRuntimeInfo::IsStarted Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsStarted
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsStarted
helpviewer_keywords:
- IsStarted method [.NET Framework hosting]
- ICLRRuntimeInfo::IsStarted method [.NET Framework hosting]
ms.assetid: ef6f2662-323b-4534-aa82-6d1afb7b9309
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1297c84acadf0a53b418b06afe806237d374ee25
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073903"
---
# <a name="iclrruntimeinfoisstarted-method"></a><span data-ttu-id="9d40d-102">ICLRRuntimeInfo::IsStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9d40d-102">ICLRRuntimeInfo::IsStarted Method</span></span>
<span data-ttu-id="9d40d-103">Çalışma zamanı başlayıp başlamadığını gösterir (diğer bir deyişle, olmadığını [Iclrruntimehost::Start yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) çağrıldığında ve başarılı oldu).</span><span class="sxs-lookup"><span data-stu-id="9d40d-103">Indicates whether the runtime has been started (that is, whether the [ICLRRuntimeHost::Start method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) has been called and has succeeded).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d40d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9d40d-104">Syntax</span></span>  
  
```  
HRESULT IsStarted(  
        [out] BOOL     *pbStarted,  
        [out] DWORD    *pdwStartupFlags);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d40d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9d40d-105">Parameters</span></span>  
 `pbStarted`  
 <span data-ttu-id="9d40d-106">[out] `true` bu çalışma zamanı varsa başlatıldı; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="9d40d-106">[out] `true` if this runtime is started; otherwise, `false`.</span></span>  
  
 `pdwStartupFlags`  
 <span data-ttu-id="9d40d-107">[out] Çalışma zamanı'nı başlatmak için kullanılan bayraklar döndürür.</span><span class="sxs-lookup"><span data-stu-id="9d40d-107">[out] Returns the flags that were used to start the runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9d40d-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9d40d-108">Return Value</span></span>  
 <span data-ttu-id="9d40d-109">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="9d40d-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="9d40d-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9d40d-110">HRESULT</span></span>|<span data-ttu-id="9d40d-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9d40d-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9d40d-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="9d40d-112">S_OK</span></span>|<span data-ttu-id="9d40d-113">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="9d40d-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="9d40d-114">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="9d40d-114">E_NOTIMPL</span></span>|<span data-ttu-id="9d40d-115">Ortak dil çalışma zamanı (CLR) sürümünü CLR sürümünü daha eski [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9d40d-115">The common language runtime (CLR) version is earlier than the CLR version in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d40d-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9d40d-116">Remarks</span></span>  
 <span data-ttu-id="9d40d-117">Bu yöntem CLR sürümleri ile kullanılan CLR sürümü'den önceki çalışmaz [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9d40d-117">This method does not work with CLR versions earlier than the CLR version in the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d40d-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9d40d-118">Requirements</span></span>  
 <span data-ttu-id="9d40d-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d40d-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d40d-120">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="9d40d-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9d40d-121">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="9d40d-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="9d40d-122">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="9d40d-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9d40d-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d40d-123">See also</span></span>

- [<span data-ttu-id="9d40d-124">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d40d-124">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="9d40d-125">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9d40d-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="9d40d-126">Barındırma</span><span class="sxs-lookup"><span data-stu-id="9d40d-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
