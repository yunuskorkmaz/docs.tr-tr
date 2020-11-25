---
title: ICLRAppDomainResourceMonitor::GetCurrentAllocated Metodu
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentAllocated
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentAllocated
helpviewer_keywords:
- GetCurrentAllocated method [.NET Framework hosting]
- ICLRAppDomainResourceMonitor::GetCurrentAllocated method [.NET Framework hosting]
ms.assetid: 7bab209c-efd4-44c2-af30-61abab0ae2fc
topic_type:
- apiref
ms.openlocfilehash: d3bd948dfe4a5cf97e3e3e430f551e7bc6404690
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700801"
---
# <a name="iclrappdomainresourcemonitorgetcurrentallocated-method"></a><span data-ttu-id="6269e-102">ICLRAppDomainResourceMonitor::GetCurrentAllocated Metodu</span><span class="sxs-lookup"><span data-stu-id="6269e-102">ICLRAppDomainResourceMonitor::GetCurrentAllocated Method</span></span>

<span data-ttu-id="6269e-103">, Atık olarak toplanmış olan belleği çıkarmadan, uygulama etki alanı tarafından yapılan tüm bellek ayırmalarının bayt cinsinden toplam boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="6269e-103">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6269e-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="6269e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentAllocated([in]  DWORD dwAppDomainId,  
                            [out] ULONGLONG* pBytesAllocated);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6269e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6269e-105">Parameters</span></span>  

 `dwAppDomainId`  
 <span data-ttu-id="6269e-106">'ndaki İstenen uygulama etki alanının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="6269e-106">[in] The ID of the requested application domain.</span></span>  
  
 `pBytesAllocated`  
 <span data-ttu-id="6269e-107">dışı Tüm bellek ayırmalarının toplam boyutuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6269e-107">[out] A pointer to the total size of all memory allocations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6269e-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6269e-108">Return Value</span></span>  

 <span data-ttu-id="6269e-109">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="6269e-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="6269e-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6269e-110">HRESULT</span></span>|<span data-ttu-id="6269e-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6269e-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6269e-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="6269e-112">S_OK</span></span>|<span data-ttu-id="6269e-113">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="6269e-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="6269e-114">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="6269e-114">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="6269e-115">Uygulama etki alanı kaldırıldı veya yok.</span><span class="sxs-lookup"><span data-stu-id="6269e-115">The application domain has been unloaded or does not exist.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6269e-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6269e-116">Remarks</span></span>  

 <span data-ttu-id="6269e-117">Bu yöntem, yönetilen özelliğin yönetilmeyen eşdeğeridir <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="6269e-117">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6269e-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6269e-118">Requirements</span></span>  

 <span data-ttu-id="6269e-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6269e-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6269e-120">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="6269e-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="6269e-121">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="6269e-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6269e-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6269e-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6269e-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6269e-123">See also</span></span>

- [<span data-ttu-id="6269e-124">ICLRAppDomainResourceMonitor Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6269e-124">ICLRAppDomainResourceMonitor Interface</span></span>](iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="6269e-125">Uygulama etki alanı kaynak Izleme</span><span class="sxs-lookup"><span data-stu-id="6269e-125">Application Domain Resource Monitoring</span></span>](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="6269e-126">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6269e-126">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="6269e-127">Hosting</span><span class="sxs-lookup"><span data-stu-id="6269e-127">Hosting</span></span>](index.md)
