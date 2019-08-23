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
ms.openlocfilehash: 10245541718fd5e5f30ef6bba4ab289bcef767fc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950214"
---
# <a name="iclrappdomainresourcemonitorgetcurrentcputime-method"></a><span data-ttu-id="89a92-102">ICLRAppDomainResourceMonitor::GetCurrentCpuTime Metodu</span><span class="sxs-lookup"><span data-stu-id="89a92-102">ICLRAppDomainResourceMonitor::GetCurrentCpuTime Method</span></span>
<span data-ttu-id="89a92-103">Uygulama etki alanı oluşturulduğundan bu yana geçerli uygulama etki alanında yürütme sırasında tüm iş parçacıkları tarafından kullanılan toplam işlemci süresini alır.</span><span class="sxs-lookup"><span data-stu-id="89a92-103">Gets the total processor time that has been used by all threads while executing in the current application domain, since the application domain was created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89a92-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="89a92-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentCpuTime([in]  DWORD dwAppDomainId,  
                          [out] ULONGLONG* pMilliseconds);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89a92-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="89a92-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="89a92-106">'ndaki İstenen uygulama etki alanının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="89a92-106">[in] The ID of the requested application domain.</span></span>  
  
 `pMilliseconds`  
 <span data-ttu-id="89a92-107">dışı Uygulama etki alanı oluşturulduktan sonra geçerli uygulama etki alanında yürütülürken tüm iş parçacıkları tarafından kullanılan toplam işlemci zamanı işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="89a92-107">[out] A pointer to the total processor time that has been used by all threads while executing in the current application domain since the application domain was created.</span></span> <span data-ttu-id="89a92-108">Bu parametre `null`olabilir.</span><span class="sxs-lookup"><span data-stu-id="89a92-108">This parameter can be `null`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="89a92-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="89a92-109">Return Value</span></span>  
  
|<span data-ttu-id="89a92-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="89a92-110">HRESULT</span></span>|<span data-ttu-id="89a92-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89a92-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="89a92-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="89a92-112">S_OK</span></span>|<span data-ttu-id="89a92-113">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="89a92-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="89a92-114">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="89a92-114">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="89a92-115">Uygulama etki alanı kaldırıldı veya yok.</span><span class="sxs-lookup"><span data-stu-id="89a92-115">The application domain has been unloaded or does not exist.</span></span>|  
|<span data-ttu-id="89a92-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="89a92-116">E_FAIL</span></span>|<span data-ttu-id="89a92-117">Uygulama etki alanı kaynak izleme etkin değil.</span><span class="sxs-lookup"><span data-stu-id="89a92-117">Application domain resource monitoring is not enabled.</span></span><br /><br /> <span data-ttu-id="89a92-118">-veya-</span><span class="sxs-lookup"><span data-stu-id="89a92-118">-or-</span></span><br /><br /> <span data-ttu-id="89a92-119">Diğer tüm arızalar.</span><span class="sxs-lookup"><span data-stu-id="89a92-119">All other failures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89a92-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="89a92-120">Remarks</span></span>  
 <span data-ttu-id="89a92-121">Bu yöntem, yönetilen <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> özelliğin yönetilmeyen eşdeğeridir.</span><span class="sxs-lookup"><span data-stu-id="89a92-121">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89a92-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="89a92-122">Requirements</span></span>  
 <span data-ttu-id="89a92-123">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89a92-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89a92-124">**Üst bilgi** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="89a92-124">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="89a92-125">**Kitaplığı** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="89a92-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="89a92-126">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89a92-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89a92-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="89a92-127">See also</span></span>

- [<span data-ttu-id="89a92-128">ICLRAppDomainResourceMonitor Arabirimi</span><span class="sxs-lookup"><span data-stu-id="89a92-128">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="89a92-129">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="89a92-129">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="89a92-130">Uygulama Etki Alanı Kaynak İzleme</span><span class="sxs-lookup"><span data-stu-id="89a92-130">Application Domain Resource Monitoring</span></span>](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="89a92-131">Barındırma</span><span class="sxs-lookup"><span data-stu-id="89a92-131">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
