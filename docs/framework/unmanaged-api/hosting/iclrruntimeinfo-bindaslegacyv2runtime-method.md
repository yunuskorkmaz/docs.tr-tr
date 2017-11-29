---
title: "ICLRRuntimeInfo::BindAsLegacyV2Runtime Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.BindAsLegacyV2Runtime
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::BindAsLegacyV2Runtime
helpviewer_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime method [.NET Framework hosting]
- BindAsLegacyV2Runtime method [.NET Framework hosting]
ms.assetid: 65fd55ac-4a24-4479-9384-a2e8013bfb2b
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 229c5483c02357054f3d2821d8e024c78887e839
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimeinfobindaslegacyv2runtime-method"></a><span data-ttu-id="53ab0-102">ICLRRuntimeInfo::BindAsLegacyV2Runtime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="53ab0-102">ICLRRuntimeInfo::BindAsLegacyV2Runtime Method</span></span>
<span data-ttu-id="53ab0-103">Tüm eski ortak dil çalışma zamanı (CLR) sürüm 2 etkinleştirme ilke kararları için geçerli çalışma zamanı bağlar.</span><span class="sxs-lookup"><span data-stu-id="53ab0-103">Binds the current runtime for all legacy common language runtime (CLR) version 2 activation policy decisions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53ab0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="53ab0-104">Syntax</span></span>  
  
```  
HRESULT BindAsLegacyV2Runtime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="53ab0-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="53ab0-105">Return Value</span></span>  
 <span data-ttu-id="53ab0-106">Bu yöntem aşağıdaki belirli HRESULTs döndürür:</span><span class="sxs-lookup"><span data-stu-id="53ab0-106">This method returns the following specific HRESULTs:</span></span>  
  
|<span data-ttu-id="53ab0-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="53ab0-107">HRESULT</span></span>|<span data-ttu-id="53ab0-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="53ab0-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="53ab0-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="53ab0-109">S_OK</span></span>|<span data-ttu-id="53ab0-110">Bağlama başarılı ya da bu çalışma zamanı eski CLR sürüm 2 etkinleştirme İlkesi çalışma zamanı zaten bağlıydı.</span><span class="sxs-lookup"><span data-stu-id="53ab0-110">Either binding succeeded, or this runtime was already bound as the legacy CLR version 2 activation policy runtime.</span></span>|  
|<span data-ttu-id="53ab0-111">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="53ab0-111">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="53ab0-112">Farklı bir çalışma zamanı eski CLR sürüm 2 etkinleştirme ilkesi zaten bağlıydı.</span><span class="sxs-lookup"><span data-stu-id="53ab0-112">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53ab0-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="53ab0-113">Remarks</span></span>  
 <span data-ttu-id="53ab0-114">Geçerli çalışma zamanının tüm eski CLR sürüm 2 etkinleştirme ilke kararları için zaten bağlıysa (kullanarak örneğin, `useLegacyV2RuntimeActivationPolicy` özniteliği [ \<başlangıç > öğesi](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) yapılandırma dosyası), bu yöntemi bir hata sonucu döndürmüyor; Bunun yerine, yalnızca bu yöntem eski etkinleştirme ilkesi başarıyla bağlı, olduğu gibi sonuç S_OK, olur.</span><span class="sxs-lookup"><span data-stu-id="53ab0-114">If the current runtime is already bound for all legacy CLR version 2 activation policy decisions (for example, by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) in the configuration file), this method does not return an error result; instead, the result is S_OK, just as it would be if the method had successfully bound legacy activation policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53ab0-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="53ab0-115">Requirements</span></span>  
 <span data-ttu-id="53ab0-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53ab0-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53ab0-117">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="53ab0-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="53ab0-118">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="53ab0-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="53ab0-119">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53ab0-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53ab0-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="53ab0-120">See Also</span></span>  
 [<span data-ttu-id="53ab0-121">Iclrruntimeınfo arabirimi</span><span class="sxs-lookup"><span data-stu-id="53ab0-121">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="53ab0-122">Barındırma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="53ab0-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="53ab0-123">Barındırma</span><span class="sxs-lookup"><span data-stu-id="53ab0-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 [<span data-ttu-id="53ab0-124">\<Başlangıç > öğesi</span><span class="sxs-lookup"><span data-stu-id="53ab0-124">\<startup> Element</span></span>](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
