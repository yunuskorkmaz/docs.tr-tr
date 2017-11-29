---
title: "ICLRMetaHost::QueryLegacyV2RuntimeBinding Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHost.RequestRuntimeLoadedNotification
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHost::QueryLegacyV2RuntimeBinding
helpviewer_keywords:
- QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
- ICLRMetaHost::QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
ms.assetid: 9929817e-acc9-40b7-960c-598664e04b60
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c273a1690828e37c8f7fcf5071e42e5bb2c58228
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrmetahostquerylegacyv2runtimebinding-method"></a><span data-ttu-id="e8c10-102">ICLRMetaHost::QueryLegacyV2RuntimeBinding Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e8c10-102">ICLRMetaHost::QueryLegacyV2RuntimeBinding Method</span></span>
<span data-ttu-id="e8c10-103">Eski etkinleştirme İlkesi bağlı, örneğin, kullanarak bir çalışma zamanı temsil eden bir arabirim döndürür `useLegacyV2RuntimeActivationPolicy` özniteliği [ \<başlangıç > öğesi](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) doğrudan kullanılarak yapılandırma dosyası girişi eski etkinleştirme API'leri veya çağırarak [Iclrruntimeınfo::bindaslegacyv2runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e8c10-103">Returns an interface that represents a runtime to which legacy activation policy has been bound, for example, by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) configuration file entry, by direct use of the legacy activation APIs, or by calling the [ICLRRuntimeInfo::BindAsLegacyV2Runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8c10-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e8c10-104">Syntax</span></span>  
  
```  
HRESULT QueryLegacyV2RuntimeBinding (  
    [in] REFIID riid,  
    [out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e8c10-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e8c10-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="e8c10-106">[in] Bu parametre için tek geçerli değer Required.Currently `IID_ICLRRuntimeInfo`.</span><span class="sxs-lookup"><span data-stu-id="e8c10-106">[in] Required.Currently the only valid value for this parameter is `IID_ICLRRuntimeInfo`.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="e8c10-107">[out] Gerekli.</span><span class="sxs-lookup"><span data-stu-id="e8c10-107">[out] Required.</span></span> <span data-ttu-id="e8c10-108">Bu yöntem döndürüldüğünde, bir işaretçi içeriyor [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) eski etkinleştirme ilkesine bağlı bir çalışma zamanı temsil eden arabirim.</span><span class="sxs-lookup"><span data-stu-id="e8c10-108">When this method returns, contains a pointer to the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that represents a runtime that has been bound to legacy activation policy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e8c10-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e8c10-109">Return Value</span></span>  
 <span data-ttu-id="e8c10-110">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="e8c10-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="e8c10-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e8c10-111">HRESULT</span></span>|<span data-ttu-id="e8c10-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e8c10-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e8c10-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="e8c10-113">S_OK</span></span>|<span data-ttu-id="e8c10-114">Bu yöntem başarıyla tamamlandı ve eski etkinleştirme ilkesine bağlı bir çalışma zamanı döndürdü.</span><span class="sxs-lookup"><span data-stu-id="e8c10-114">The method completed successfully and returned a runtime that was bound to legacy activation policy.</span></span>|  
|<span data-ttu-id="e8c10-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="e8c10-115">S_FALSE</span></span>|<span data-ttu-id="e8c10-116">Yöntemin başarıyla tamamlandı, ancak eski çalışma zamanı henüz bağlı.</span><span class="sxs-lookup"><span data-stu-id="e8c10-116">The method completed successfully, but a legacy runtime has not yet been bound.</span></span>|  
|<span data-ttu-id="e8c10-117">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="e8c10-117">E_NOINTERFACE</span></span>|<span data-ttu-id="e8c10-118">Yöntem eski etkinleştirme ilkesi için bağlı bir çalışma zamanı bulundu ancak `riid` , çalışma zamanı tarafından desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="e8c10-118">The method found a runtime that was bound to legacy activation policy, but `riid` is not supported by that runtime.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8c10-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e8c10-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8c10-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e8c10-120">Requirements</span></span>  
 <span data-ttu-id="e8c10-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8c10-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8c10-122">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="e8c10-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e8c10-123">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e8c10-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e8c10-124">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8c10-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8c10-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e8c10-125">See Also</span></span>  
 [<span data-ttu-id="e8c10-126">Iclrmetahost arabirimi</span><span class="sxs-lookup"><span data-stu-id="e8c10-126">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [<span data-ttu-id="e8c10-127">Barındırma</span><span class="sxs-lookup"><span data-stu-id="e8c10-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
