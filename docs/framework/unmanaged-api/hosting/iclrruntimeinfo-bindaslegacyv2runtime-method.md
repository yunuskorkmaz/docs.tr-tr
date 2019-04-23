---
title: ICLRRuntimeInfo::BindAsLegacyV2Runtime Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.BindAsLegacyV2Runtime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime
helpviewer_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime method [.NET Framework hosting]
- BindAsLegacyV2Runtime method [.NET Framework hosting]
ms.assetid: 65fd55ac-4a24-4479-9384-a2e8013bfb2b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 647c87b6f42b01922a385d502d72410af3140cd2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59095353"
---
# <a name="iclrruntimeinfobindaslegacyv2runtime-method"></a><span data-ttu-id="b5c57-102">ICLRRuntimeInfo::BindAsLegacyV2Runtime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b5c57-102">ICLRRuntimeInfo::BindAsLegacyV2Runtime Method</span></span>
<span data-ttu-id="b5c57-103">Geçerli çalışma zamanının tüm eski ortak dil çalışma zamanı (CLR) sürüm 2 etkinleştirme İlkesi kararları için bağlar.</span><span class="sxs-lookup"><span data-stu-id="b5c57-103">Binds the current runtime for all legacy common language runtime (CLR) version 2 activation policy decisions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5c57-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b5c57-104">Syntax</span></span>  
  
```  
HRESULT BindAsLegacyV2Runtime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="b5c57-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b5c57-105">Return Value</span></span>  
 <span data-ttu-id="b5c57-106">Bu yöntem aşağıdaki özel HRESULT'ları döndürür:</span><span class="sxs-lookup"><span data-stu-id="b5c57-106">This method returns the following specific HRESULTs:</span></span>  
  
|<span data-ttu-id="b5c57-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b5c57-107">HRESULT</span></span>|<span data-ttu-id="b5c57-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b5c57-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b5c57-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="b5c57-109">S_OK</span></span>|<span data-ttu-id="b5c57-110">Bağlama başarılı ya da bu çalışma zamanı, eski CLR sürüm 2 etkinleştirme İlkesi çalışma zamanı zaten bağlıydı.</span><span class="sxs-lookup"><span data-stu-id="b5c57-110">Either binding succeeded, or this runtime was already bound as the legacy CLR version 2 activation policy runtime.</span></span>|  
|<span data-ttu-id="b5c57-111">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="b5c57-111">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="b5c57-112">Farklı bir çalışma zamanı, eski CLR sürüm 2 etkinleştirme ilkesi zaten bağlıydı.</span><span class="sxs-lookup"><span data-stu-id="b5c57-112">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5c57-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b5c57-113">Remarks</span></span>  
 <span data-ttu-id="b5c57-114">Geçerli çalışma zamanının tüm eski CLR sürüm 2 etkinleştirme İlkesi kararları için zaten bağlıysa (kullanarak örneğin, `useLegacyV2RuntimeActivationPolicy` özniteliği [ \<başlangıç > öğesi](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) yapılandırma dosyasında), bu yöntemi bir hata sonucu döndürmeyen; Bunun yerine, yalnızca bu yöntem eski etkinleştirme ilkesini başarıyla bağlı olmadığını olduğu gibi sonuç S_OK, olur.</span><span class="sxs-lookup"><span data-stu-id="b5c57-114">If the current runtime is already bound for all legacy CLR version 2 activation policy decisions (for example, by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) in the configuration file), this method does not return an error result; instead, the result is S_OK, just as it would be if the method had successfully bound legacy activation policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5c57-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b5c57-115">Requirements</span></span>  
 <span data-ttu-id="b5c57-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5c57-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5c57-117">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="b5c57-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="b5c57-118">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="b5c57-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b5c57-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5c57-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5c57-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5c57-120">See also</span></span>

- [<span data-ttu-id="b5c57-121">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b5c57-121">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="b5c57-122">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b5c57-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="b5c57-123">Barındırma</span><span class="sxs-lookup"><span data-stu-id="b5c57-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [<span data-ttu-id="b5c57-124">\<Başlangıç > öğesi</span><span class="sxs-lookup"><span data-stu-id="b5c57-124">\<startup> Element</span></span>](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
