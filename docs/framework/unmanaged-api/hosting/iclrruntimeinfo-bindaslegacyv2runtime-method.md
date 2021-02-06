---
description: ': ICLRRuntimeInfo:: BindAsLegacyV2Runtime Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 77b340cba18ea86546e1a8f4a17933f09289b1de
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637189"
---
# <a name="iclrruntimeinfobindaslegacyv2runtime-method"></a><span data-ttu-id="69a68-103">ICLRRuntimeInfo::BindAsLegacyV2Runtime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="69a68-103">ICLRRuntimeInfo::BindAsLegacyV2Runtime Method</span></span>

<span data-ttu-id="69a68-104">Tüm eski ortak dil çalışma zamanı (CLR) sürüm 2 etkinleştirme ilkesi kararlarının geçerli çalışma zamanını bağlar.</span><span class="sxs-lookup"><span data-stu-id="69a68-104">Binds the current runtime for all legacy common language runtime (CLR) version 2 activation policy decisions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69a68-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="69a68-105">Syntax</span></span>  
  
```cpp  
HRESULT BindAsLegacyV2Runtime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="69a68-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="69a68-106">Return Value</span></span>  

 <span data-ttu-id="69a68-107">Bu yöntem, aşağıdaki belirli HRESULTs 'leri döndürür:</span><span class="sxs-lookup"><span data-stu-id="69a68-107">This method returns the following specific HRESULTs:</span></span>  
  
|<span data-ttu-id="69a68-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="69a68-108">HRESULT</span></span>|<span data-ttu-id="69a68-109">Description</span><span class="sxs-lookup"><span data-stu-id="69a68-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="69a68-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="69a68-110">S_OK</span></span>|<span data-ttu-id="69a68-111">Bağlama başarılı ya da bu çalışma zamanı eski CLR sürüm 2 etkinleştirme ilkesi çalışma zamanı olarak zaten bağlandı.</span><span class="sxs-lookup"><span data-stu-id="69a68-111">Either binding succeeded, or this runtime was already bound as the legacy CLR version 2 activation policy runtime.</span></span>|  
|<span data-ttu-id="69a68-112">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="69a68-112">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="69a68-113">Farklı bir çalışma zamanı eski CLR sürüm 2 etkinleştirme ilkesine zaten bağlıydı.</span><span class="sxs-lookup"><span data-stu-id="69a68-113">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69a68-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="69a68-114">Remarks</span></span>  

 <span data-ttu-id="69a68-115">Geçerli çalışma zamanı tüm eski CLR sürüm 2 etkinleştirme ilkesi kararlarında zaten bağlıysa (örneğin, `useLegacyV2RuntimeActivationPolicy` yapılandırma dosyasındaki [ \<startup> öğesindeki](../../configure-apps/file-schema/startup/startup-element.md) özniteliğini kullanarak), bu yöntem bir hata sonucu döndürmez; bunun yerine, yöntemin eski etkinleştirme ilkesini başarıyla bağlamış olduğu gibi, sonuç S_OK.</span><span class="sxs-lookup"><span data-stu-id="69a68-115">If the current runtime is already bound for all legacy CLR version 2 activation policy decisions (for example, by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> element](../../configure-apps/file-schema/startup/startup-element.md) in the configuration file), this method does not return an error result; instead, the result is S_OK, just as it would be if the method had successfully bound legacy activation policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69a68-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="69a68-116">Requirements</span></span>  

 <span data-ttu-id="69a68-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69a68-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69a68-118">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="69a68-118">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="69a68-119">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="69a68-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="69a68-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69a68-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69a68-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="69a68-121">See also</span></span>

- [<span data-ttu-id="69a68-122">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="69a68-122">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="69a68-123">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="69a68-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="69a68-124">Hosting</span><span class="sxs-lookup"><span data-stu-id="69a68-124">Hosting</span></span>](index.md)
- [<span data-ttu-id="69a68-125">\<startup> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="69a68-125">\<startup> Element</span></span>](../../configure-apps/file-schema/startup/startup-element.md)
