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
ms.openlocfilehash: 79b62a5e2aad9cfcd14ba40c1abf0342bfe57a4b
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703537"
---
# <a name="iclrmetahostpolicy-interface"></a><span data-ttu-id="2289c-102">ICLRMetaHostPolicy Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2289c-102">ICLRMetaHostPolicy Interface</span></span>
<span data-ttu-id="2289c-103">Bir ilke ölçütlerine, yönetilen derlemeye, sürüme ve yapılandırma dosyasına dayalı ortak dil çalışma zamanı (CLR) arabirimine yönelik bir işaretçi döndüren [GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) yöntemini sağlar.</span><span class="sxs-lookup"><span data-stu-id="2289c-103">Provides the [GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) method, which returns a pointer to a common language runtime (CLR) interface based on a policy criteria, managed assembly, version and configuration file.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2289c-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2289c-104">Methods</span></span>  
  
|<span data-ttu-id="2289c-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="2289c-105">Method</span></span>|<span data-ttu-id="2289c-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2289c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2289c-107">GetRequestedRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2289c-107">GetRequestedRuntime Method</span></span>](iclrmetahostpolicy-getrequestedruntime-method.md)|<span data-ttu-id="2289c-108">İlke ölçütlerini, yönetilen derlemeyi, sürümü ve yapılandırma dosyasını temel alan tercih edilen bir CLR arabirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="2289c-108">Provides a preferred CLR interface based on a policy criteria, managed assembly, version, and configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2289c-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2289c-109">Remarks</span></span>  
 <span data-ttu-id="2289c-110">Aşağıdaki kodda gösterildiği gibi [CLRCreateInstance](clrcreateinstance-function.md) işlevini çağırarak, bu arabirime bir başvuru alabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2289c-110">You can get a reference to this interface by calling the [CLRCreateInstance](clrcreateinstance-function.md) function as shown in the following code:</span></span>  
  
```cpp  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHostPolicy,  
                   IID_ICLRMetaHostPolicy, (LPVOID*)&pMetaHostPolicy);  
```  
  
> [!NOTE]
> <span data-ttu-id="2289c-111">Bu arabirim gerçekte CLR 'yi yüklemez veya etkinleştirmez, ancak yalnızca yüklenmiş veya yüklenen kullanılabilir sürümlere göre tercih edilen CLR sürümünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="2289c-111">This interface does not actually load or activate the CLR, but simply returns the preferred CLR version based on the available versions that are installed or loaded.</span></span>  
  
 <span data-ttu-id="2289c-112">.NET Framework 4 barındırma API 'SI ilkeleri birleştirir, böylece belirli ihtiyaçları olan konaklar, istenmeyen yaptırımlara gerek kalmadan temel işlevleri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="2289c-112">The .NET Framework 4 hosting API consolidates policies so that hosts with specific needs may use basic functionality without incurring unintended penalties.</span></span> <span data-ttu-id="2289c-113">Örneğin, bazı MSCorEE. dll dışarı aktarmaları belirli bir CLR 'ye bağlanır, ancak bir yöntem mantıksal olarak gerektirmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="2289c-113">For example, many of the MSCorEE.dll exports will bind to a specific CLR, although a method might not logically require it.</span></span> <span data-ttu-id="2289c-114">[METAHOST_POLICY_FLAGS](metahost-policy-flags-enumeration.md) numaralandırması, ana bilgisayarların çoğunluğu için ortak olan bağlama ilkeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="2289c-114">The [METAHOST_POLICY_FLAGS](metahost-policy-flags-enumeration.md) enumeration provides binding policies that are common to the majority of hosts.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2289c-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2289c-115">Requirements</span></span>  
 <span data-ttu-id="2289c-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2289c-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2289c-117">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="2289c-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="2289c-118">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="2289c-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2289c-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2289c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2289c-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2289c-120">See also</span></span>

- [<span data-ttu-id="2289c-121">.NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2289c-121">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="2289c-122">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2289c-122">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="2289c-123">Barındırma</span><span class="sxs-lookup"><span data-stu-id="2289c-123">Hosting</span></span>](index.md)
