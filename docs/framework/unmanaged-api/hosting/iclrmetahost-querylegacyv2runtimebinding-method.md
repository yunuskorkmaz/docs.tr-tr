---
title: ICLRMetaHost::QueryLegacyV2RuntimeBinding Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.RequestRuntimeLoadedNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::QueryLegacyV2RuntimeBinding
helpviewer_keywords:
- QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
- ICLRMetaHost::QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
ms.assetid: 9929817e-acc9-40b7-960c-598664e04b60
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0252f27f30c3ce8abe349a2ddc45b20692fbb5ea
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59186413"
---
# <a name="iclrmetahostquerylegacyv2runtimebinding-method"></a><span data-ttu-id="13c1e-102">ICLRMetaHost::QueryLegacyV2RuntimeBinding Yöntemi</span><span class="sxs-lookup"><span data-stu-id="13c1e-102">ICLRMetaHost::QueryLegacyV2RuntimeBinding Method</span></span>
<span data-ttu-id="13c1e-103">Eski etkinleştirme İlkesi bağlı, örneğin, kullanarak bir çalışma zamanı temsil eden bir arabirim döndürür `useLegacyV2RuntimeActivationPolicy` özniteliği [ \<başlangıç > öğesi](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) doğrudan kullanılarak yapılandırma dosyası girdisi eski etkinleştirme API'leri veya çağırarak [Iclrruntimeınfo::bindaslegacyv2runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="13c1e-103">Returns an interface that represents a runtime to which legacy activation policy has been bound, for example, by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) configuration file entry, by direct use of the legacy activation APIs, or by calling the [ICLRRuntimeInfo::BindAsLegacyV2Runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13c1e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="13c1e-104">Syntax</span></span>  
  
```  
HRESULT QueryLegacyV2RuntimeBinding (  
    [in] REFIID riid,  
    [out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13c1e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="13c1e-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="13c1e-106">[in] Bu parametre için geçerli tek değer Required.Currently `IID_ICLRRuntimeInfo`.</span><span class="sxs-lookup"><span data-stu-id="13c1e-106">[in] Required.Currently the only valid value for this parameter is `IID_ICLRRuntimeInfo`.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="13c1e-107">[out] Gerekli.</span><span class="sxs-lookup"><span data-stu-id="13c1e-107">[out] Required.</span></span> <span data-ttu-id="13c1e-108">Bu yöntem döndürüldüğünde, bir işaretçi içeren [Iclrruntimeınfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) eski etkinleştirme ilkesi için bağlı bir çalışma zamanı temsil eden arabirim.</span><span class="sxs-lookup"><span data-stu-id="13c1e-108">When this method returns, contains a pointer to the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that represents a runtime that has been bound to legacy activation policy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="13c1e-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="13c1e-109">Return Value</span></span>  
 <span data-ttu-id="13c1e-110">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="13c1e-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="13c1e-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="13c1e-111">HRESULT</span></span>|<span data-ttu-id="13c1e-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="13c1e-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="13c1e-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="13c1e-113">S_OK</span></span>|<span data-ttu-id="13c1e-114">Yöntem başarıyla tamamlandı ve eski etkinleştirme ilkesi için sınırlı bir çalışma zamanı döndürdü.</span><span class="sxs-lookup"><span data-stu-id="13c1e-114">The method completed successfully and returned a runtime that was bound to legacy activation policy.</span></span>|  
|<span data-ttu-id="13c1e-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="13c1e-115">S_FALSE</span></span>|<span data-ttu-id="13c1e-116">Yöntemin başarıyla tamamlandı, ancak eski bir çalışma zamanı henüz bağlı değil.</span><span class="sxs-lookup"><span data-stu-id="13c1e-116">The method completed successfully, but a legacy runtime has not yet been bound.</span></span>|  
|<span data-ttu-id="13c1e-117">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="13c1e-117">E_NOINTERFACE</span></span>|<span data-ttu-id="13c1e-118">Yöntemi, eski etkinleştirme İlkesi bağlanan bir çalışma zamanı bulunamadı ancak `riid` , çalışma zamanı tarafından desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="13c1e-118">The method found a runtime that was bound to legacy activation policy, but `riid` is not supported by that runtime.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13c1e-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="13c1e-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13c1e-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="13c1e-120">Requirements</span></span>  
 <span data-ttu-id="13c1e-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13c1e-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13c1e-122">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="13c1e-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="13c1e-123">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="13c1e-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="13c1e-124">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13c1e-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13c1e-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13c1e-125">See also</span></span>

- [<span data-ttu-id="13c1e-126">ICLRMetaHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="13c1e-126">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="13c1e-127">Barındırma</span><span class="sxs-lookup"><span data-stu-id="13c1e-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
