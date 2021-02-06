---
description: ': ICLRMetaHostPolicy Interface hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: b14ad417617c32242f8a59844f7c1f1a8d05c78d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637423"
---
# <a name="iclrmetahostpolicy-interface"></a><span data-ttu-id="f1365-103">ICLRMetaHostPolicy Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f1365-103">ICLRMetaHostPolicy Interface</span></span>

<span data-ttu-id="f1365-104">Bir ilke ölçütlerine, yönetilen derlemeye, sürüme ve yapılandırma dosyasına dayalı ortak dil çalışma zamanı (CLR) arabirimine yönelik bir işaretçi döndüren [GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) yöntemini sağlar.</span><span class="sxs-lookup"><span data-stu-id="f1365-104">Provides the [GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) method, which returns a pointer to a common language runtime (CLR) interface based on a policy criteria, managed assembly, version and configuration file.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f1365-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f1365-105">Methods</span></span>  
  
|<span data-ttu-id="f1365-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f1365-106">Method</span></span>|<span data-ttu-id="f1365-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f1365-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f1365-108">GetRequestedRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f1365-108">GetRequestedRuntime Method</span></span>](iclrmetahostpolicy-getrequestedruntime-method.md)|<span data-ttu-id="f1365-109">İlke ölçütlerini, yönetilen derlemeyi, sürümü ve yapılandırma dosyasını temel alan tercih edilen bir CLR arabirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f1365-109">Provides a preferred CLR interface based on a policy criteria, managed assembly, version, and configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1365-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f1365-110">Remarks</span></span>  

 <span data-ttu-id="f1365-111">Aşağıdaki kodda gösterildiği gibi [CLRCreateInstance](clrcreateinstance-function.md) işlevini çağırarak, bu arabirime bir başvuru alabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f1365-111">You can get a reference to this interface by calling the [CLRCreateInstance](clrcreateinstance-function.md) function as shown in the following code:</span></span>  
  
```cpp  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHostPolicy,  
                   IID_ICLRMetaHostPolicy, (LPVOID*)&pMetaHostPolicy);  
```  
  
> [!NOTE]
> <span data-ttu-id="f1365-112">Bu arabirim gerçekte CLR 'yi yüklemez veya etkinleştirmez, ancak yalnızca yüklenmiş veya yüklenen kullanılabilir sürümlere göre tercih edilen CLR sürümünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="f1365-112">This interface does not actually load or activate the CLR, but simply returns the preferred CLR version based on the available versions that are installed or loaded.</span></span>  
  
 <span data-ttu-id="f1365-113">.NET Framework 4 barındırma API 'SI ilkeleri birleştirir, böylece belirli ihtiyaçları olan konaklar, istenmeyen yaptırımlara gerek kalmadan temel işlevleri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="f1365-113">The .NET Framework 4 hosting API consolidates policies so that hosts with specific needs may use basic functionality without incurring unintended penalties.</span></span> <span data-ttu-id="f1365-114">Örneğin, çoğu MSCorEE.dll dışarı aktarmalar belirli bir CLR 'ye bağlanır, ancak bir yöntem mantıksal olarak gerektirmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="f1365-114">For example, many of the MSCorEE.dll exports will bind to a specific CLR, although a method might not logically require it.</span></span> <span data-ttu-id="f1365-115">[METAHOST_POLICY_FLAGS](metahost-policy-flags-enumeration.md) numaralandırması, ana bilgisayarların çoğunluğu için ortak olan bağlama ilkeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="f1365-115">The [METAHOST_POLICY_FLAGS](metahost-policy-flags-enumeration.md) enumeration provides binding policies that are common to the majority of hosts.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1365-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f1365-116">Requirements</span></span>  

 <span data-ttu-id="f1365-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1365-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1365-118">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="f1365-118">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f1365-119">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="f1365-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f1365-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1365-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1365-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1365-121">See also</span></span>

- [<span data-ttu-id="f1365-122">.NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f1365-122">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="f1365-123">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f1365-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="f1365-124">Hosting</span><span class="sxs-lookup"><span data-stu-id="f1365-124">Hosting</span></span>](index.md)
