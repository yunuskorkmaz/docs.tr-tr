---
title: "ICLRRuntimeInfo::IsStarted Yöntemi"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 991470ca0df3e0cf0470a8c40d3e8e4c40d96026
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimeinfoisstarted-method"></a><span data-ttu-id="a52ea-102">ICLRRuntimeInfo::IsStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a52ea-102">ICLRRuntimeInfo::IsStarted Method</span></span>
<span data-ttu-id="a52ea-103">Çalışma zamanı başlatılmış olup olmadığını gösterir (diğer bir deyişle, olup olmadığını [Iclrruntimehost::Start yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) çağrıldı ve başarılı oldu).</span><span class="sxs-lookup"><span data-stu-id="a52ea-103">Indicates whether the runtime has been started (that is, whether the [ICLRRuntimeHost::Start method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) has been called and has succeeded).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a52ea-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a52ea-104">Syntax</span></span>  
  
```  
HRESULT IsStarted(  
        [out] BOOL     *pbStarted,  
        [out] DWORD    *pdwStartupFlags);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a52ea-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a52ea-105">Parameters</span></span>  
 `pbStarted`  
 <span data-ttu-id="a52ea-106">[out] `true` bu çalışma zamanı, başlangıç Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="a52ea-106">[out] `true` if this runtime is started; otherwise, `false`.</span></span>  
  
 `pdwStartupFlags`  
 <span data-ttu-id="a52ea-107">[out] Çalışma zamanı başlatmak için kullanılan bayrakları döndürür.</span><span class="sxs-lookup"><span data-stu-id="a52ea-107">[out] Returns the flags that were used to start the runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a52ea-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a52ea-108">Return Value</span></span>  
 <span data-ttu-id="a52ea-109">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="a52ea-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a52ea-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a52ea-110">HRESULT</span></span>|<span data-ttu-id="a52ea-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a52ea-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a52ea-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="a52ea-112">S_OK</span></span>|<span data-ttu-id="a52ea-113">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="a52ea-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="a52ea-114">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="a52ea-114">E_NOTIMPL</span></span>|<span data-ttu-id="a52ea-115">Ortak dil çalışma zamanı (CLR) sürümü CLR sürümünü daha önceki [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a52ea-115">The common language runtime (CLR) version is earlier than the CLR version in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a52ea-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a52ea-116">Remarks</span></span>  
 <span data-ttu-id="a52ea-117">Bu yöntem CLR sürümleriyle CLR sürümü'den önceki çalışmaz [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a52ea-117">This method does not work with CLR versions earlier than the CLR version in the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a52ea-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a52ea-118">Requirements</span></span>  
 <span data-ttu-id="a52ea-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a52ea-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a52ea-120">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="a52ea-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a52ea-121">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="a52ea-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a52ea-122">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a52ea-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a52ea-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a52ea-123">See Also</span></span>  
 [<span data-ttu-id="a52ea-124">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a52ea-124">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="a52ea-125">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a52ea-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="a52ea-126">Barındırma</span><span class="sxs-lookup"><span data-stu-id="a52ea-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
