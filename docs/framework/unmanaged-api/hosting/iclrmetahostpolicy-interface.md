---
title: ICLRMetaHostPolicy Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHostPolicy
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHostPolicy
helpviewer_keywords: ICLRMetaHostPolicy interface [.NET Framework hosting]
ms.assetid: 1bdeccb6-0698-4c97-ad69-eae2b69e59f1
topic_type: apiref
caps.latest.revision: "23"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cd9b8d6aef2289833a0bd192b838e6f70ea8c0ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrmetahostpolicy-interface"></a><span data-ttu-id="34a35-102">ICLRMetaHostPolicy Arabirimi</span><span class="sxs-lookup"><span data-stu-id="34a35-102">ICLRMetaHostPolicy Interface</span></span>
<span data-ttu-id="34a35-103">Sağlar [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) döndüren bir işaretçi bir ilke ölçütlere göre bir ortak dil çalışma zamanı (CLR) arabirimi, yöntem, yönetilen derleme, sürüm ve yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="34a35-103">Provides the [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method, which returns a pointer to a common language runtime (CLR) interface based on a policy criteria, managed assembly, version and configuration file.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="34a35-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="34a35-104">Methods</span></span>  
  
|<span data-ttu-id="34a35-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="34a35-105">Method</span></span>|<span data-ttu-id="34a35-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="34a35-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="34a35-107">GetRequestedRuntime Yöntemi</span><span class="sxs-lookup"><span data-stu-id="34a35-107">GetRequestedRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)|<span data-ttu-id="34a35-108">Tercih edilen bir CLR arabirimi ilke ölçütleri temel alarak, derleme, sürüm ve yapılandırma dosyası yönetilen sağlar.</span><span class="sxs-lookup"><span data-stu-id="34a35-108">Provides a preferred CLR interface based on a policy criteria, managed assembly, version, and configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34a35-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="34a35-109">Remarks</span></span>  
 <span data-ttu-id="34a35-110">Bu arabirim başvuru çağırarak alabilirsiniz [Clrcreateınstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) işlev aşağıdaki kodda gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="34a35-110">You can get a reference to this interface by calling the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function as shown in the following code:</span></span>  
  
```  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHostPolicy,  
                   IID_ICLRMetaHostPolicy, (LPVOID*)&pMetaHostPolicy);  
```  
  
> [!NOTE]
>  <span data-ttu-id="34a35-111">Bu arabirim gerçekten yük veya CLR, ancak yalnızca tercih edilen CLR sürümü yüklü ya da yüklenen kullanılabilir sürümlerine bağlı döndürür etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="34a35-111">This interface does not actually load or activate the CLR, but simply returns the preferred CLR version based on the available versions that are installed or loaded.</span></span>  
  
 <span data-ttu-id="34a35-112">[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] API barındırma birleştirir ilkeleri böylece ihtiyacınıza konaklarla temel işlevleri istenmeyen cezaları yansıtılmasını olmadan kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="34a35-112">The [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] hosting API consolidates policies so that hosts with specific needs may use basic functionality without incurring unintended penalties.</span></span> <span data-ttu-id="34a35-113">Örneğin, bunu bir yöntem mantıksal olarak gerektirmeyebilecek ancak birçok MSCorEE.dll dışarı aktarmaları için belirli bir CLR, bağlarsınız.</span><span class="sxs-lookup"><span data-stu-id="34a35-113">For example, many of the MSCorEE.dll exports will bind to a specific CLR, although a method might not logically require it.</span></span> <span data-ttu-id="34a35-114">[Metahost_polıcy_flags](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) numaralandırması konakları çoğunluğu için ortak olan bağlama ilkeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="34a35-114">The [METAHOST_POLICY_FLAGS](../../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) enumeration provides binding policies that are common to the majority of hosts.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34a35-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="34a35-115">Requirements</span></span>  
 <span data-ttu-id="34a35-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34a35-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34a35-117">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="34a35-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="34a35-118">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="34a35-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="34a35-119">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34a35-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34a35-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="34a35-120">See Also</span></span>  
 [<span data-ttu-id="34a35-121">.NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="34a35-121">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 [<span data-ttu-id="34a35-122">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="34a35-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="34a35-123">Barındırma</span><span class="sxs-lookup"><span data-stu-id="34a35-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
