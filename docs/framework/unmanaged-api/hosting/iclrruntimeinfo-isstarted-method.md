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
ms.openlocfilehash: b09c509c3e0ba941a34f60ff522117ff30d83caf
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2019
ms.locfileid: "66457387"
---
# <a name="iclrruntimeinfoisstarted-method"></a><span data-ttu-id="08088-102">ICLRRuntimeInfo::IsStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="08088-102">ICLRRuntimeInfo::IsStarted Method</span></span>
<span data-ttu-id="08088-103">Çalışma zamanı başlayıp başlamadığını gösterir (diğer bir deyişle, olmadığını [Iclrruntimehost::Start yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) çağrıldığında ve başarılı oldu).</span><span class="sxs-lookup"><span data-stu-id="08088-103">Indicates whether the runtime has been started (that is, whether the [ICLRRuntimeHost::Start method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) has been called and has succeeded).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08088-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="08088-104">Syntax</span></span>  
  
```  
HRESULT IsStarted(  
        [out] BOOL     *pbStarted,  
        [out] DWORD    *pdwStartupFlags);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08088-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="08088-105">Parameters</span></span>  
 `pbStarted`  
 <span data-ttu-id="08088-106">[out] `true` bu çalışma zamanı varsa başlatıldı; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="08088-106">[out] `true` if this runtime is started; otherwise, `false`.</span></span>  
  
 `pdwStartupFlags`  
 <span data-ttu-id="08088-107">[out] Çalışma zamanı'nı başlatmak için kullanılan bayraklar döndürür.</span><span class="sxs-lookup"><span data-stu-id="08088-107">[out] Returns the flags that were used to start the runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="08088-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="08088-108">Return Value</span></span>  
 <span data-ttu-id="08088-109">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="08088-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="08088-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="08088-110">HRESULT</span></span>|<span data-ttu-id="08088-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="08088-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="08088-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="08088-112">S_OK</span></span>|<span data-ttu-id="08088-113">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="08088-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="08088-114">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="08088-114">E_NOTIMPL</span></span>|<span data-ttu-id="08088-115">Ortak dil çalışma zamanı (CLR) sürümünü CLR sürümünü daha eski [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="08088-115">The common language runtime (CLR) version is earlier than the CLR version in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08088-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="08088-116">Remarks</span></span>  
 <span data-ttu-id="08088-117">Bu yöntem .NET Framework 4'te CLR sürümü'den önceki CLR sürümleriyle çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="08088-117">This method does not work with CLR versions earlier than the CLR version in the .NET Framework 4.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08088-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="08088-118">Requirements</span></span>  
 <span data-ttu-id="08088-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08088-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08088-120">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="08088-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="08088-121">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="08088-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="08088-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08088-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08088-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08088-123">See also</span></span>

- [<span data-ttu-id="08088-124">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="08088-124">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="08088-125">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="08088-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="08088-126">Barındırma</span><span class="sxs-lookup"><span data-stu-id="08088-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
