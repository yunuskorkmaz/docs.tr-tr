---
title: ICLRMetaHostPolicy Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRMetaHostPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHostPolicy
helpviewer_keywords:
- ICLRMetaHostPolicy interface [.NET Framework hosting]
ms.assetid: 1bdeccb6-0698-4c97-ad69-eae2b69e59f1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e2735d3e0bbcb6326ca8ea87a3358824bca81108
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951181"
---
# <a name="iclrmetahostpolicy-interface"></a><span data-ttu-id="94bd8-102">ICLRMetaHostPolicy Arabirimi</span><span class="sxs-lookup"><span data-stu-id="94bd8-102">ICLRMetaHostPolicy Interface</span></span>
<span data-ttu-id="94bd8-103">Bir ilke ölçütlerine, yönetilen derlemeye, sürüme ve yapılandırma dosyasına dayalı ortak dil çalışma zamanı (CLR) arabirimine yönelik bir işaretçi döndüren [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) yöntemini sağlar.</span><span class="sxs-lookup"><span data-stu-id="94bd8-103">Provides the [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method, which returns a pointer to a common language runtime (CLR) interface based on a policy criteria, managed assembly, version and configuration file.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="94bd8-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="94bd8-104">Methods</span></span>  
  
|<span data-ttu-id="94bd8-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="94bd8-105">Method</span></span>|<span data-ttu-id="94bd8-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="94bd8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="94bd8-107">GetRequestedRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="94bd8-107">GetRequestedRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)|<span data-ttu-id="94bd8-108">İlke ölçütlerini, yönetilen derlemeyi, sürümü ve yapılandırma dosyasını temel alan tercih edilen bir CLR arabirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="94bd8-108">Provides a preferred CLR interface based on a policy criteria, managed assembly, version, and configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94bd8-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="94bd8-109">Remarks</span></span>  
 <span data-ttu-id="94bd8-110">Aşağıdaki kodda gösterildiği gibi [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) işlevini çağırarak, bu arabirime bir başvuru alabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="94bd8-110">You can get a reference to this interface by calling the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function as shown in the following code:</span></span>  
  
```cpp  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHostPolicy,  
                   IID_ICLRMetaHostPolicy, (LPVOID*)&pMetaHostPolicy);  
```  
  
> [!NOTE]
> <span data-ttu-id="94bd8-111">Bu arabirim gerçekte CLR 'yi yüklemez veya etkinleştirmez, ancak yalnızca yüklenmiş veya yüklenen kullanılabilir sürümlere göre tercih edilen CLR sürümünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="94bd8-111">This interface does not actually load or activate the CLR, but simply returns the preferred CLR version based on the available versions that are installed or loaded.</span></span>  
  
 <span data-ttu-id="94bd8-112">.NET Framework 4 barındırma API 'SI ilkeleri birleştirir, böylece belirli ihtiyaçları olan konaklar, istenmeyen yaptırımlara gerek kalmadan temel işlevleri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="94bd8-112">The .NET Framework 4 hosting API consolidates policies so that hosts with specific needs may use basic functionality without incurring unintended penalties.</span></span> <span data-ttu-id="94bd8-113">Örneğin, bazı MSCorEE. dll dışarı aktarmaları belirli bir CLR 'ye bağlanır, ancak bir yöntem mantıksal olarak gerektirmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="94bd8-113">For example, many of the MSCorEE.dll exports will bind to a specific CLR, although a method might not logically require it.</span></span> <span data-ttu-id="94bd8-114">[METAHOST_POLICY_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) numaralandırması, ana bilgisayarların çoğunluğu için ortak olan bağlama ilkeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="94bd8-114">The [METAHOST_POLICY_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) enumeration provides binding policies that are common to the majority of hosts.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94bd8-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="94bd8-115">Requirements</span></span>  
 <span data-ttu-id="94bd8-116">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94bd8-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94bd8-117">**Üst bilgi** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="94bd8-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="94bd8-118">**Kitaplığı** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="94bd8-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="94bd8-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94bd8-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94bd8-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94bd8-120">See also</span></span>

- [<span data-ttu-id="94bd8-121">.NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="94bd8-121">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="94bd8-122">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="94bd8-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="94bd8-123">Barındırma</span><span class="sxs-lookup"><span data-stu-id="94bd8-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
