---
title: ICLRAppDomainResourceMonitor::GetCurrentCpuTime Metodu
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentCpuTime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentCpuTime
helpviewer_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentCpuTime method [.NET Framework hosting]
- GetCurrentCpuTime method [.NET Framework hosting]
ms.assetid: ebc9cc33-fcd6-4cae-9ecb-ea21c51874e6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 63f5687787a9b0cdb30790b7e80e4160cdf413f4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54737250"
---
# <a name="iclrappdomainresourcemonitorgetcurrentcputime-method"></a><span data-ttu-id="e24a9-102">ICLRAppDomainResourceMonitor::GetCurrentCpuTime Metodu</span><span class="sxs-lookup"><span data-stu-id="e24a9-102">ICLRAppDomainResourceMonitor::GetCurrentCpuTime Method</span></span>
<span data-ttu-id="e24a9-103">Geçerli uygulama etki alanında, uygulama etki alanı oluşturulmasından bu yana yürütülürken tüm iş parçacıkları tarafından kullanılmış olan toplam işlemci zamanı alır.</span><span class="sxs-lookup"><span data-stu-id="e24a9-103">Gets the total processor time that has been used by all threads while executing in the current application domain, since the application domain was created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e24a9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e24a9-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentCpuTime([in]  DWORD dwAppDomainId,  
                          [out] ULONGLONG* pMilliseconds);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e24a9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e24a9-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="e24a9-106">[in] İstenen uygulama etki alanı kimliği.</span><span class="sxs-lookup"><span data-stu-id="e24a9-106">[in] The ID of the requested application domain.</span></span>  
  
 `pMilliseconds`  
 <span data-ttu-id="e24a9-107">[out] Uygulama etki alanı oluşturulduktan sonra geçerli uygulama etki alanında yürütülürken tüm iş parçacıkları tarafından kullanılmış olan toplam işlemci zamanı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e24a9-107">[out] A pointer to the total processor time that has been used by all threads while executing in the current application domain since the application domain was created.</span></span> <span data-ttu-id="e24a9-108">Bu parametre olabilir `null`.</span><span class="sxs-lookup"><span data-stu-id="e24a9-108">This parameter can be `null`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e24a9-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e24a9-109">Return Value</span></span>  
  
|<span data-ttu-id="e24a9-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e24a9-110">HRESULT</span></span>|<span data-ttu-id="e24a9-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e24a9-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e24a9-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="e24a9-112">S_OK</span></span>|<span data-ttu-id="e24a9-113">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="e24a9-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="e24a9-114">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="e24a9-114">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="e24a9-115">Uygulama etki alanı kaldırıldı veya yok.</span><span class="sxs-lookup"><span data-stu-id="e24a9-115">The application domain has been unloaded or does not exist.</span></span>|  
|<span data-ttu-id="e24a9-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e24a9-116">E_FAIL</span></span>|<span data-ttu-id="e24a9-117">Uygulama etki alanı kaynak izlemesinin etkin değil.</span><span class="sxs-lookup"><span data-stu-id="e24a9-117">Application domain resource monitoring is not enabled.</span></span><br /><br /> <span data-ttu-id="e24a9-118">-veya-</span><span class="sxs-lookup"><span data-stu-id="e24a9-118">-or-</span></span><br /><br /> <span data-ttu-id="e24a9-119">Tüm diğer hataları.</span><span class="sxs-lookup"><span data-stu-id="e24a9-119">All other failures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e24a9-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e24a9-120">Remarks</span></span>  
 <span data-ttu-id="e24a9-121">Bu yöntem yönetilmeyen yönetilen eşdeğerdir <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="e24a9-121">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e24a9-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e24a9-122">Requirements</span></span>  
 <span data-ttu-id="e24a9-123">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e24a9-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e24a9-124">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="e24a9-124">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e24a9-125">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e24a9-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e24a9-126">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e24a9-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e24a9-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e24a9-127">See also</span></span>
- [<span data-ttu-id="e24a9-128">ICLRAppDomainResourceMonitor Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e24a9-128">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="e24a9-129">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e24a9-129">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="e24a9-130">Uygulama Etki Alanı Kaynak İzleme</span><span class="sxs-lookup"><span data-stu-id="e24a9-130">Application Domain Resource Monitoring</span></span>](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="e24a9-131">Barındırma</span><span class="sxs-lookup"><span data-stu-id="e24a9-131">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
