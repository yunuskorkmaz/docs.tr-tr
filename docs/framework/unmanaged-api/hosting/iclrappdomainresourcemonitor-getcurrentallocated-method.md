---
description: ': Iclartppdomainresourcemonitor:: Getcurrentalkonumlandırılan yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: d7aaf31f775a9d6e2af95cf1a832c78587a85fe1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753958"
---
# <a name="iclrappdomainresourcemonitorgetcurrentallocated-method"></a><span data-ttu-id="5cc63-103">ICLRAppDomainResourceMonitor::GetCurrentAllocated Metodu</span><span class="sxs-lookup"><span data-stu-id="5cc63-103">ICLRAppDomainResourceMonitor::GetCurrentAllocated Method</span></span>

<span data-ttu-id="5cc63-104">, Atık olarak toplanmış olan belleği çıkarmadan, uygulama etki alanı tarafından yapılan tüm bellek ayırmalarının bayt cinsinden toplam boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="5cc63-104">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cc63-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5cc63-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentAllocated([in]  DWORD dwAppDomainId,  
                            [out] ULONGLONG* pBytesAllocated);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5cc63-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5cc63-106">Parameters</span></span>  

 `dwAppDomainId`  
 <span data-ttu-id="5cc63-107">'ndaki İstenen uygulama etki alanının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="5cc63-107">[in] The ID of the requested application domain.</span></span>  
  
 `pBytesAllocated`  
 <span data-ttu-id="5cc63-108">dışı Tüm bellek ayırmalarının toplam boyutuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5cc63-108">[out] A pointer to the total size of all memory allocations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5cc63-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5cc63-109">Return Value</span></span>  

 <span data-ttu-id="5cc63-110">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="5cc63-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="5cc63-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5cc63-111">HRESULT</span></span>|<span data-ttu-id="5cc63-112">Description</span><span class="sxs-lookup"><span data-stu-id="5cc63-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5cc63-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="5cc63-113">S_OK</span></span>|<span data-ttu-id="5cc63-114">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="5cc63-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="5cc63-115">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="5cc63-115">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="5cc63-116">Uygulama etki alanı kaldırıldı veya yok.</span><span class="sxs-lookup"><span data-stu-id="5cc63-116">The application domain has been unloaded or does not exist.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5cc63-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5cc63-117">Remarks</span></span>  

 <span data-ttu-id="5cc63-118">Bu yöntem, yönetilen özelliğin yönetilmeyen eşdeğeridir <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5cc63-118">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5cc63-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5cc63-119">Requirements</span></span>  

 <span data-ttu-id="5cc63-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5cc63-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cc63-121">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="5cc63-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="5cc63-122">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="5cc63-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5cc63-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5cc63-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cc63-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5cc63-124">See also</span></span>

- [<span data-ttu-id="5cc63-125">ICLRAppDomainResourceMonitor Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5cc63-125">ICLRAppDomainResourceMonitor Interface</span></span>](iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="5cc63-126">Uygulama etki alanı kaynak Izleme</span><span class="sxs-lookup"><span data-stu-id="5cc63-126">Application Domain Resource Monitoring</span></span>](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="5cc63-127">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5cc63-127">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="5cc63-128">Hosting</span><span class="sxs-lookup"><span data-stu-id="5cc63-128">Hosting</span></span>](index.md)
