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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7fcd7a3aa1a6c034985099c24071429384563700
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61985302"
---
# <a name="iclrappdomainresourcemonitorgetcurrentallocated-method"></a><span data-ttu-id="96903-102">ICLRAppDomainResourceMonitor::GetCurrentAllocated Metodu</span><span class="sxs-lookup"><span data-stu-id="96903-102">ICLRAppDomainResourceMonitor::GetCurrentAllocated Method</span></span>
<span data-ttu-id="96903-103">Toplam boyutu bayt cinsinden, atık olarak toplanmış bellek çıkararak olmadan oluşturulduktan sonra uygulama etki alanı tarafından yapılan tüm bellek ayırmaları alır.</span><span class="sxs-lookup"><span data-stu-id="96903-103">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96903-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="96903-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentAllocated([in]  DWORD dwAppDomainId,  
                            [out] ULONGLONG* pBytesAllocated);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96903-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="96903-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="96903-106">[in] İstenen uygulama etki alanı kimliği.</span><span class="sxs-lookup"><span data-stu-id="96903-106">[in] The ID of the requested application domain.</span></span>  
  
 `pBytesAllocated`  
 <span data-ttu-id="96903-107">[out] Tüm bellek ayırmaları toplam boyutu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="96903-107">[out] A pointer to the total size of all memory allocations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="96903-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="96903-108">Return Value</span></span>  
 <span data-ttu-id="96903-109">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="96903-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="96903-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="96903-110">HRESULT</span></span>|<span data-ttu-id="96903-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="96903-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="96903-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="96903-112">S_OK</span></span>|<span data-ttu-id="96903-113">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="96903-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="96903-114">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="96903-114">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="96903-115">Uygulama etki alanı kaldırıldı veya yok.</span><span class="sxs-lookup"><span data-stu-id="96903-115">The application domain has been unloaded or does not exist.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96903-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="96903-116">Remarks</span></span>  
 <span data-ttu-id="96903-117">Bu yöntem yönetilmeyen yönetilen eşdeğerdir <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="96903-117">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96903-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="96903-118">Requirements</span></span>  
 <span data-ttu-id="96903-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96903-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96903-120">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="96903-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="96903-121">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="96903-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="96903-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96903-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96903-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96903-123">See also</span></span>

- [<span data-ttu-id="96903-124">ICLRAppDomainResourceMonitor Arabirimi</span><span class="sxs-lookup"><span data-stu-id="96903-124">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="96903-125">Uygulama Etki Alanı Kaynak İzleme</span><span class="sxs-lookup"><span data-stu-id="96903-125">Application Domain Resource Monitoring</span></span>](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="96903-126">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="96903-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="96903-127">Barındırma</span><span class="sxs-lookup"><span data-stu-id="96903-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
