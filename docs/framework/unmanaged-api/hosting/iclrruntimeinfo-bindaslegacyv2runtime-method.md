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
ms.openlocfilehash: f0a03ecce49bbc3c1c03d037c9be31a8e994259d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732105"
---
# <a name="iclrruntimeinfobindaslegacyv2runtime-method"></a><span data-ttu-id="ef30b-102">ICLRRuntimeInfo::BindAsLegacyV2Runtime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ef30b-102">ICLRRuntimeInfo::BindAsLegacyV2Runtime Method</span></span>

<span data-ttu-id="ef30b-103">Tüm eski ortak dil çalışma zamanı (CLR) sürüm 2 etkinleştirme ilkesi kararlarının geçerli çalışma zamanını bağlar.</span><span class="sxs-lookup"><span data-stu-id="ef30b-103">Binds the current runtime for all legacy common language runtime (CLR) version 2 activation policy decisions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef30b-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="ef30b-104">Syntax</span></span>  
  
```cpp  
HRESULT BindAsLegacyV2Runtime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="ef30b-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ef30b-105">Return Value</span></span>  

 <span data-ttu-id="ef30b-106">Bu yöntem, aşağıdaki belirli HRESULTs 'leri döndürür:</span><span class="sxs-lookup"><span data-stu-id="ef30b-106">This method returns the following specific HRESULTs:</span></span>  
  
|<span data-ttu-id="ef30b-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ef30b-107">HRESULT</span></span>|<span data-ttu-id="ef30b-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ef30b-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ef30b-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="ef30b-109">S_OK</span></span>|<span data-ttu-id="ef30b-110">Bağlama başarılı ya da bu çalışma zamanı eski CLR sürüm 2 etkinleştirme ilkesi çalışma zamanı olarak zaten bağlandı.</span><span class="sxs-lookup"><span data-stu-id="ef30b-110">Either binding succeeded, or this runtime was already bound as the legacy CLR version 2 activation policy runtime.</span></span>|  
|<span data-ttu-id="ef30b-111">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="ef30b-111">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="ef30b-112">Farklı bir çalışma zamanı eski CLR sürüm 2 etkinleştirme ilkesine zaten bağlıydı.</span><span class="sxs-lookup"><span data-stu-id="ef30b-112">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ef30b-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ef30b-113">Remarks</span></span>  

 <span data-ttu-id="ef30b-114">Geçerli çalışma zamanı tüm eski CLR sürüm 2 etkinleştirme ilkesi kararlarında zaten bağlıysa (örneğin, `useLegacyV2RuntimeActivationPolicy` yapılandırma dosyasındaki [ \<startup> öğesindeki](../../configure-apps/file-schema/startup/startup-element.md) özniteliğini kullanarak), bu yöntem bir hata sonucu döndürmez; bunun yerine, yöntemin eski etkinleştirme ilkesini başarıyla bağlamış olduğu gibi, sonuç S_OK.</span><span class="sxs-lookup"><span data-stu-id="ef30b-114">If the current runtime is already bound for all legacy CLR version 2 activation policy decisions (for example, by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> element](../../configure-apps/file-schema/startup/startup-element.md) in the configuration file), this method does not return an error result; instead, the result is S_OK, just as it would be if the method had successfully bound legacy activation policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef30b-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ef30b-115">Requirements</span></span>  

 <span data-ttu-id="ef30b-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef30b-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef30b-117">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="ef30b-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ef30b-118">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="ef30b-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ef30b-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef30b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef30b-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef30b-120">See also</span></span>

- [<span data-ttu-id="ef30b-121">ICLRRuntimeInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ef30b-121">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="ef30b-122">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ef30b-122">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="ef30b-123">Hosting</span><span class="sxs-lookup"><span data-stu-id="ef30b-123">Hosting</span></span>](index.md)
- [<span data-ttu-id="ef30b-124">\<startup> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="ef30b-124">\<startup> Element</span></span>](../../configure-apps/file-schema/startup/startup-element.md)
