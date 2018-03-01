---
title: "CLRCreateInstance İşlevi"
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
- CLRCreateInstance
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- COM
f1_keywords:
- CLRCreateInstance
helpviewer_keywords:
- CLRCreateInstance function [.NET Framework hosting]
ms.assetid: 5de13327-96c6-4697-a89e-b8bf40717855
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4d95815dd0b2a1cdbddcb28a2e176bc12d3270ed
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="clrcreateinstance-function"></a><span data-ttu-id="db79b-102">CLRCreateInstance İşlevi</span><span class="sxs-lookup"><span data-stu-id="db79b-102">CLRCreateInstance Function</span></span>
<span data-ttu-id="db79b-103">Üç arabirimi birini sağlar: [Iclrmetahost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [Iclrmetahostpolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), veya [Iclrdebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).</span><span class="sxs-lookup"><span data-stu-id="db79b-103">Provides one of three interfaces: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), or [ICLRDebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db79b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="db79b-104">Syntax</span></span>  
  
```  
HRESULT CLRCreateInstance(  
    [in]  REFCLSID  clsid,  
    [in]  REFIID     riid,  
    [out] LPVOID  * ppInterface  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="db79b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="db79b-105">Parameters</span></span>  
 `clsid`  
 <span data-ttu-id="db79b-106">[in] Üç sınıf tanımlayıcıları birini: CLSID_CLRMetaHost, CLSID_CLRMetaHostPolicy veya CLSID_CLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="db79b-106">[in] One of three class identifiers: CLSID_CLRMetaHost, CLSID_CLRMetaHostPolicy, or CLSID_CLRDebugging.</span></span>  
  
 `riid`  
 <span data-ttu-id="db79b-107">[in] Üç arabirim tanımlayıcıları (IID'leri) birini: IID_ICLRMetaHost, IID_ICLRMetaHostPolicy veya IID_ICLRDebugging.</span><span class="sxs-lookup"><span data-stu-id="db79b-107">[in] One of three interface identifiers (IIDs): IID_ICLRMetaHost, IID_ICLRMetaHostPolicy, or IID_ICLRDebugging.</span></span>  
  
 `ppInterface`  
 <span data-ttu-id="db79b-108">[out] Üç arabirimi birini: [Iclrmetahost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [Iclrmetahostpolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), veya [Iclrdebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).</span><span class="sxs-lookup"><span data-stu-id="db79b-108">[out] One of three interfaces: [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md), [ICLRMetaHostPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md), or [ICLRDebugging](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="db79b-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="db79b-109">Return Value</span></span>  
 <span data-ttu-id="db79b-110">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="db79b-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="db79b-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="db79b-111">HRESULT</span></span>|<span data-ttu-id="db79b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="db79b-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="db79b-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="db79b-113">S_OK</span></span>|<span data-ttu-id="db79b-114">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="db79b-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="db79b-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="db79b-115">E_POINTER</span></span>|<span data-ttu-id="db79b-116">`ppInterface`null şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="db79b-116">`ppInterface` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db79b-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="db79b-117">Remarks</span></span>  
 <span data-ttu-id="db79b-118">Aşağıdaki tablo için desteklenen birleşimlerin gösterir `clsid` ve `riid`.</span><span class="sxs-lookup"><span data-stu-id="db79b-118">The following table shows the supported combinations for `clsid` and `riid`.</span></span>  
  
|`rclsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="db79b-119">CLSID_CLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="db79b-119">CLSID_CLRMetaHost</span></span>|<span data-ttu-id="db79b-120">IID_ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="db79b-120">IID_ICLRMetaHost</span></span>|  
|<span data-ttu-id="db79b-121">CLSID_CLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="db79b-121">CLSID_CLRMetaHostPolicy</span></span>|<span data-ttu-id="db79b-122">IID_ICLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="db79b-122">IID_ICLRMetaHostPolicy</span></span>|  
|<span data-ttu-id="db79b-123">CLSID_CLRDebugging</span><span class="sxs-lookup"><span data-stu-id="db79b-123">CLSID_CLRDebugging</span></span>|<span data-ttu-id="db79b-124">IID_ICLRDebugging</span><span class="sxs-lookup"><span data-stu-id="db79b-124">IID_ICLRDebugging</span></span>|  
  
 <span data-ttu-id="db79b-125">Aşağıdaki kodu nasıl kullanılacağını gösterir `CLRCreateInstance` tüm üç arabirimi almak için:</span><span class="sxs-lookup"><span data-stu-id="db79b-125">The following code shows how to use `CLRCreateInstance` to get all three interfaces:</span></span>  
  
```  
#include <metahost.h>  
#pragma comment(lib, "mscoree.lib")  
  
ICLRMetaHost       *pMetaHost       = NULL;  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
ICLRDebugging      *pCLRDebugging   = NULL;  
HRESULT hr;  
hr = CLRCreateInstance(CLSID_CLRMetaHost, IID_ICLRMetaHost,  
                    (LPVOID*)&pMetaHost);  
hr = CLRCreateInstance (CLSID_CLRMetaHostPolicy, IID_ICLRMetaHostPolicy,  
                    (LPVOID*)&pMetaHostPolicy);  
hr = CLRCreateInstance (CLSID_CLRDebugging, IID_ICLRDebugging,  
                    (LPVOID*)&pCLRDebugging);  
```  
  
## <a name="requirements"></a><span data-ttu-id="db79b-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="db79b-126">Requirements</span></span>  
 <span data-ttu-id="db79b-127">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db79b-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db79b-128">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="db79b-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="db79b-129">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="db79b-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="db79b-130">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db79b-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db79b-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="db79b-131">See Also</span></span>  
 [<span data-ttu-id="db79b-132">Barındırma</span><span class="sxs-lookup"><span data-stu-id="db79b-132">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
