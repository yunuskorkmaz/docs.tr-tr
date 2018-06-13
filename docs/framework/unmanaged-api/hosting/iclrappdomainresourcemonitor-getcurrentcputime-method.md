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
ms.openlocfilehash: 53deeab574716a426c1c4617abe279e72f27c04e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433527"
---
# <a name="iclrappdomainresourcemonitorgetcurrentcputime-method"></a><span data-ttu-id="b387c-102">ICLRAppDomainResourceMonitor::GetCurrentCpuTime Metodu</span><span class="sxs-lookup"><span data-stu-id="b387c-102">ICLRAppDomainResourceMonitor::GetCurrentCpuTime Method</span></span>
<span data-ttu-id="b387c-103">Uygulama etki alanı oluşturulduktan sonra geçerli uygulama etki alanında yürütülürken tüm iş parçacıkları tarafından kullanılmış olan toplam işlemci zamanı alır.</span><span class="sxs-lookup"><span data-stu-id="b387c-103">Gets the total processor time that has been used by all threads while executing in the current application domain, since the application domain was created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b387c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b387c-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentCpuTime([in]  DWORD dwAppDomainId,  
                          [out] ULONGLONG* pMilliseconds);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b387c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b387c-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="b387c-106">[in] İstenen uygulama etki alanı kimliği.</span><span class="sxs-lookup"><span data-stu-id="b387c-106">[in] The ID of the requested application domain.</span></span>  
  
 `pMilliseconds`  
 <span data-ttu-id="b387c-107">[out] Uygulama etki alanı oluşturulduktan sonra geçerli uygulama etki alanında yürütülürken tüm iş parçacıkları tarafından kullanılmış olan toplam işlemci zamanı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b387c-107">[out] A pointer to the total processor time that has been used by all threads while executing in the current application domain since the application domain was created.</span></span> <span data-ttu-id="b387c-108">Bu parametre olabilir `null`.</span><span class="sxs-lookup"><span data-stu-id="b387c-108">This parameter can be `null`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b387c-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b387c-109">Return Value</span></span>  
  
|<span data-ttu-id="b387c-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b387c-110">HRESULT</span></span>|<span data-ttu-id="b387c-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b387c-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b387c-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="b387c-112">S_OK</span></span>|<span data-ttu-id="b387c-113">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="b387c-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="b387c-114">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="b387c-114">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="b387c-115">Uygulama etki alanı kaldırıldı veya yok.</span><span class="sxs-lookup"><span data-stu-id="b387c-115">The application domain has been unloaded or does not exist.</span></span>|  
|<span data-ttu-id="b387c-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b387c-116">E_FAIL</span></span>|<span data-ttu-id="b387c-117">Uygulama etki alanı kaynak izleme etkin değil.</span><span class="sxs-lookup"><span data-stu-id="b387c-117">Application domain resource monitoring is not enabled.</span></span><br /><br /> <span data-ttu-id="b387c-118">-veya-</span><span class="sxs-lookup"><span data-stu-id="b387c-118">-or-</span></span><br /><br /> <span data-ttu-id="b387c-119">Tüm diğer hataları.</span><span class="sxs-lookup"><span data-stu-id="b387c-119">All other failures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b387c-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b387c-120">Remarks</span></span>  
 <span data-ttu-id="b387c-121">Bu yöntem yönetilmeyen yönetilen eşdeğerdir <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="b387c-121">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b387c-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b387c-122">Requirements</span></span>  
 <span data-ttu-id="b387c-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b387c-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b387c-124">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="b387c-124">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="b387c-125">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="b387c-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b387c-126">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b387c-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b387c-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b387c-127">See Also</span></span>  
 [<span data-ttu-id="b387c-128">ICLRAppDomainResourceMonitor Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b387c-128">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 [<span data-ttu-id="b387c-129">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b387c-129">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="b387c-130">Uygulama Etki Alanı Kaynak İzleme</span><span class="sxs-lookup"><span data-stu-id="b387c-130">Application Domain Resource Monitoring</span></span>](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)  
 [<span data-ttu-id="b387c-131">Barındırma</span><span class="sxs-lookup"><span data-stu-id="b387c-131">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
