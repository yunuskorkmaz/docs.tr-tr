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
ms.openlocfilehash: 6c85888e9d29e7b3ae6ad76d1e534e08a4603ed2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54499031"
---
# <a name="iclrruntimeinfobindaslegacyv2runtime-method"></a><span data-ttu-id="9606f-102">ICLRRuntimeInfo::BindAsLegacyV2Runtime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9606f-102">ICLRRuntimeInfo::BindAsLegacyV2Runtime Method</span></span>
<span data-ttu-id="9606f-103">Geçerli çalışma zamanının tüm eski ortak dil çalışma zamanı (CLR) sürüm 2 etkinleştirme İlkesi kararları için bağlar.</span><span class="sxs-lookup"><span data-stu-id="9606f-103">Binds the current runtime for all legacy common language runtime (CLR) version 2 activation policy decisions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9606f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9606f-104">Syntax</span></span>  
  
```  
HRESULT BindAsLegacyV2Runtime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="9606f-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9606f-105">Return Value</span></span>  
 <span data-ttu-id="9606f-106">Bu yöntem aşağıdaki özel HRESULT'ları döndürür:</span><span class="sxs-lookup"><span data-stu-id="9606f-106">This method returns the following specific HRESULTs:</span></span>  
  
|<span data-ttu-id="9606f-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9606f-107">HRESULT</span></span>|<span data-ttu-id="9606f-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9606f-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9606f-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="9606f-109">S_OK</span></span>|<span data-ttu-id="9606f-110">Bağlama başarılı ya da bu çalışma zamanı, eski CLR sürüm 2 etkinleştirme İlkesi çalışma zamanı zaten bağlıydı.</span><span class="sxs-lookup"><span data-stu-id="9606f-110">Either binding succeeded, or this runtime was already bound as the legacy CLR version 2 activation policy runtime.</span></span>|  
|<span data-ttu-id="9606f-111">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="9606f-111">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="9606f-112">Farklı bir çalışma zamanı, eski CLR sürüm 2 etkinleştirme ilkesi zaten bağlıydı.</span><span class="sxs-lookup"><span data-stu-id="9606f-112">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9606f-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9606f-113">Remarks</span></span>  
 <span data-ttu-id="9606f-114">Geçerli çalışma zamanının tüm eski CLR sürüm 2 etkinleştirme İlkesi kararları için zaten bağlıysa (kullanarak örneğin, `useLegacyV2RuntimeActivationPolicy` özniteliği [ \<başlangıç > öğesi](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) yapılandırma dosyasında), bu yöntemi bir hata sonucu döndürmeyen; Bunun yerine, yalnızca bu yöntem eski etkinleştirme ilkesini başarıyla bağlı olmadığını olduğu gibi sonuç S_OK, olur.</span><span class="sxs-lookup"><span data-stu-id="9606f-114">If the current runtime is already bound for all legacy CLR version 2 activation policy decisions (for example, by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) in the configuration file), this method does not return an error result; instead, the result is S_OK, just as it would be if the method had successfully bound legacy activation policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9606f-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9606f-115">Requirements</span></span>  
 <span data-ttu-id="9606f-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9606f-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9606f-117">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="9606f-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9606f-118">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="9606f-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9606f-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9606f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9606f-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9606f-120">See also</span></span>
- [<span data-ttu-id="9606f-121">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9606f-121">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="9606f-122">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9606f-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="9606f-123">Barındırma</span><span class="sxs-lookup"><span data-stu-id="9606f-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [<span data-ttu-id="9606f-124">\<Başlangıç > öğesi</span><span class="sxs-lookup"><span data-stu-id="9606f-124">\<startup> Element</span></span>](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
