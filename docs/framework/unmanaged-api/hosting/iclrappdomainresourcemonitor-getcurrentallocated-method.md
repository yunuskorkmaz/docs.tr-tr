---
title: ICLRAppDomainResourceMonitor::GetCurrentAllocated Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d2b69f2f8e8273c07d277ff7460ad977fade89ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrappdomainresourcemonitorgetcurrentallocated-method"></a><span data-ttu-id="c1bb9-102">ICLRAppDomainResourceMonitor::GetCurrentAllocated Metodu</span><span class="sxs-lookup"><span data-stu-id="c1bb9-102">ICLRAppDomainResourceMonitor::GetCurrentAllocated Method</span></span>
<span data-ttu-id="c1bb9-103">Atık olarak toplanmış bellek çıkarılmasıyla olmadan oluşturulduktan sonra uygulama etki alanı tarafından yapılan tüm bellek ayırmaları bayt cinsinden toplam boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="c1bb9-103">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1bb9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c1bb9-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentAllocated([in]  DWORD dwAppDomainId,  
                            [out] ULONGLONG* pBytesAllocated);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c1bb9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c1bb9-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="c1bb9-106">[in] İstenen uygulama etki alanı kimliği.</span><span class="sxs-lookup"><span data-stu-id="c1bb9-106">[in] The ID of the requested application domain.</span></span>  
  
 `pBytesAllocated`  
 <span data-ttu-id="c1bb9-107">[out] Tüm bellek ayırmaları toplam boyutu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c1bb9-107">[out] A pointer to the total size of all memory allocations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c1bb9-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c1bb9-108">Return Value</span></span>  
 <span data-ttu-id="c1bb9-109">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="c1bb9-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="c1bb9-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c1bb9-110">HRESULT</span></span>|<span data-ttu-id="c1bb9-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c1bb9-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c1bb9-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="c1bb9-112">S_OK</span></span>|<span data-ttu-id="c1bb9-113">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="c1bb9-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="c1bb9-114">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="c1bb9-114">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="c1bb9-115">Uygulama etki alanı kaldırıldı veya yok.</span><span class="sxs-lookup"><span data-stu-id="c1bb9-115">The application domain has been unloaded or does not exist.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1bb9-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c1bb9-116">Remarks</span></span>  
 <span data-ttu-id="c1bb9-117">Bu yöntem yönetilmeyen yönetilen eşdeğerdir <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="c1bb9-117">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1bb9-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c1bb9-118">Requirements</span></span>  
 <span data-ttu-id="c1bb9-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1bb9-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1bb9-120">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="c1bb9-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c1bb9-121">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="c1bb9-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c1bb9-122">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1bb9-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1bb9-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c1bb9-123">See Also</span></span>  
 [<span data-ttu-id="c1bb9-124">ICLRAppDomainResourceMonitor Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c1bb9-124">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 [<span data-ttu-id="c1bb9-125">Uygulama Etki Alanı Kaynak İzleme</span><span class="sxs-lookup"><span data-stu-id="c1bb9-125">Application Domain Resource Monitoring</span></span>](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)  
 [<span data-ttu-id="c1bb9-126">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c1bb9-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="c1bb9-127">Barındırma</span><span class="sxs-lookup"><span data-stu-id="c1bb9-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
