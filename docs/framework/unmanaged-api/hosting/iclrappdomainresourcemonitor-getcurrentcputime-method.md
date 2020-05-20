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
ms.openlocfilehash: b411190ff36410c1d293f1e48b31975be8a13aee
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616040"
---
# <a name="iclrappdomainresourcemonitorgetcurrentcputime-method"></a><span data-ttu-id="bb49f-102">ICLRAppDomainResourceMonitor::GetCurrentCpuTime Metodu</span><span class="sxs-lookup"><span data-stu-id="bb49f-102">ICLRAppDomainResourceMonitor::GetCurrentCpuTime Method</span></span>
<span data-ttu-id="bb49f-103">Uygulama etki alanı oluşturulduğundan bu yana geçerli uygulama etki alanında yürütme sırasında tüm iş parçacıkları tarafından kullanılan toplam işlemci süresini alır.</span><span class="sxs-lookup"><span data-stu-id="bb49f-103">Gets the total processor time that has been used by all threads while executing in the current application domain, since the application domain was created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb49f-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="bb49f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentCpuTime([in]  DWORD dwAppDomainId,  
                          [out] ULONGLONG* pMilliseconds);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb49f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bb49f-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="bb49f-106">'ndaki İstenen uygulama etki alanının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="bb49f-106">[in] The ID of the requested application domain.</span></span>  
  
 `pMilliseconds`  
 <span data-ttu-id="bb49f-107">dışı Uygulama etki alanı oluşturulduktan sonra geçerli uygulama etki alanında yürütülürken tüm iş parçacıkları tarafından kullanılan toplam işlemci zamanı işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="bb49f-107">[out] A pointer to the total processor time that has been used by all threads while executing in the current application domain since the application domain was created.</span></span> <span data-ttu-id="bb49f-108">Bu parametre olabilir `null` .</span><span class="sxs-lookup"><span data-stu-id="bb49f-108">This parameter can be `null`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bb49f-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bb49f-109">Return Value</span></span>  
  
|<span data-ttu-id="bb49f-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bb49f-110">HRESULT</span></span>|<span data-ttu-id="bb49f-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bb49f-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bb49f-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="bb49f-112">S_OK</span></span>|<span data-ttu-id="bb49f-113">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="bb49f-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="bb49f-114">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="bb49f-114">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="bb49f-115">Uygulama etki alanı kaldırıldı veya yok.</span><span class="sxs-lookup"><span data-stu-id="bb49f-115">The application domain has been unloaded or does not exist.</span></span>|  
|<span data-ttu-id="bb49f-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bb49f-116">E_FAIL</span></span>|<span data-ttu-id="bb49f-117">Uygulama etki alanı kaynak izleme etkin değil.</span><span class="sxs-lookup"><span data-stu-id="bb49f-117">Application domain resource monitoring is not enabled.</span></span><br /><br /> <span data-ttu-id="bb49f-118">-veya-</span><span class="sxs-lookup"><span data-stu-id="bb49f-118">-or-</span></span><br /><br /> <span data-ttu-id="bb49f-119">Diğer tüm arızalar.</span><span class="sxs-lookup"><span data-stu-id="bb49f-119">All other failures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb49f-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bb49f-120">Remarks</span></span>  
 <span data-ttu-id="bb49f-121">Bu yöntem, yönetilen özelliğin yönetilmeyen eşdeğeridir <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="bb49f-121">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb49f-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bb49f-122">Requirements</span></span>  
 <span data-ttu-id="bb49f-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb49f-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb49f-124">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="bb49f-124">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="bb49f-125">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="bb49f-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bb49f-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb49f-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb49f-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb49f-127">See also</span></span>

- [<span data-ttu-id="bb49f-128">ICLRAppDomainResourceMonitor Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bb49f-128">ICLRAppDomainResourceMonitor Interface</span></span>](iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="bb49f-129">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="bb49f-129">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="bb49f-130">Uygulama etki alanı kaynak Izleme</span><span class="sxs-lookup"><span data-stu-id="bb49f-130">Application Domain Resource Monitoring</span></span>](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="bb49f-131">Barındırma</span><span class="sxs-lookup"><span data-stu-id="bb49f-131">Hosting</span></span>](index.md)
