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
ms.openlocfilehash: d37ec8e17e62f58212a5f79f4d6b6aa75f57bf7c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120266"
---
# <a name="iclrruntimeinfobindaslegacyv2runtime-method"></a><span data-ttu-id="fa590-102">ICLRRuntimeInfo::BindAsLegacyV2Runtime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fa590-102">ICLRRuntimeInfo::BindAsLegacyV2Runtime Method</span></span>
<span data-ttu-id="fa590-103">Tüm eski ortak dil çalışma zamanı (CLR) sürüm 2 etkinleştirme ilkesi kararlarının geçerli çalışma zamanını bağlar.</span><span class="sxs-lookup"><span data-stu-id="fa590-103">Binds the current runtime for all legacy common language runtime (CLR) version 2 activation policy decisions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa590-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fa590-104">Syntax</span></span>  
  
```cpp  
HRESULT BindAsLegacyV2Runtime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="fa590-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fa590-105">Return Value</span></span>  
 <span data-ttu-id="fa590-106">Bu yöntem, aşağıdaki belirli HRESULTs 'leri döndürür:</span><span class="sxs-lookup"><span data-stu-id="fa590-106">This method returns the following specific HRESULTs:</span></span>  
  
|<span data-ttu-id="fa590-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fa590-107">HRESULT</span></span>|<span data-ttu-id="fa590-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa590-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fa590-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="fa590-109">S_OK</span></span>|<span data-ttu-id="fa590-110">Bağlama başarılı ya da bu çalışma zamanı eski CLR sürüm 2 etkinleştirme ilkesi çalışma zamanı olarak zaten bağlandı.</span><span class="sxs-lookup"><span data-stu-id="fa590-110">Either binding succeeded, or this runtime was already bound as the legacy CLR version 2 activation policy runtime.</span></span>|  
|<span data-ttu-id="fa590-111">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="fa590-111">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="fa590-112">Farklı bir çalışma zamanı eski CLR sürüm 2 etkinleştirme ilkesine zaten bağlıydı.</span><span class="sxs-lookup"><span data-stu-id="fa590-112">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa590-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fa590-113">Remarks</span></span>  
 <span data-ttu-id="fa590-114">Geçerli çalışma zamanı tüm eski CLR sürüm 2 etkinleştirme ilkesi kararlarında zaten bağlıysa (örneğin, yapılandırma dosyasındaki [\<startup > öğesinde](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) `useLegacyV2RuntimeActivationPolicy` özniteliğini kullanarak), bu yöntem bir hata sonucu döndürmez; Bunun yerine, yöntemin eski etkinleştirme ilkesini başarıyla bağladığından olduğu gibi, sonuç S_OK olur.</span><span class="sxs-lookup"><span data-stu-id="fa590-114">If the current runtime is already bound for all legacy CLR version 2 activation policy decisions (for example, by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) in the configuration file), this method does not return an error result; instead, the result is S_OK, just as it would be if the method had successfully bound legacy activation policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa590-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fa590-115">Requirements</span></span>  
 <span data-ttu-id="fa590-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa590-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa590-117">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="fa590-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="fa590-118">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="fa590-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fa590-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa590-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa590-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa590-120">See also</span></span>

- [<span data-ttu-id="fa590-121">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fa590-121">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="fa590-122">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fa590-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="fa590-123">Barındırma</span><span class="sxs-lookup"><span data-stu-id="fa590-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [<span data-ttu-id="fa590-124">\<Başlangıç > öğesi</span><span class="sxs-lookup"><span data-stu-id="fa590-124">\<startup> Element</span></span>](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
