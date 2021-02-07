---
description: ': Iclartppdomainresourcemonitor:: GetCurrentCpuTime yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: ce36bf4ab88f953834d3ff12404bcaadcb42812d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753935"
---
# <a name="iclrappdomainresourcemonitorgetcurrentcputime-method"></a><span data-ttu-id="d609a-103">ICLRAppDomainResourceMonitor::GetCurrentCpuTime Metodu</span><span class="sxs-lookup"><span data-stu-id="d609a-103">ICLRAppDomainResourceMonitor::GetCurrentCpuTime Method</span></span>

<span data-ttu-id="d609a-104">Uygulama etki alanı oluşturulduğundan bu yana geçerli uygulama etki alanında yürütme sırasında tüm iş parçacıkları tarafından kullanılan toplam işlemci süresini alır.</span><span class="sxs-lookup"><span data-stu-id="d609a-104">Gets the total processor time that has been used by all threads while executing in the current application domain, since the application domain was created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d609a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d609a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentCpuTime([in]  DWORD dwAppDomainId,  
                          [out] ULONGLONG* pMilliseconds);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d609a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d609a-106">Parameters</span></span>  

 `dwAppDomainId`  
 <span data-ttu-id="d609a-107">'ndaki İstenen uygulama etki alanının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="d609a-107">[in] The ID of the requested application domain.</span></span>  
  
 `pMilliseconds`  
 <span data-ttu-id="d609a-108">dışı Uygulama etki alanı oluşturulduktan sonra geçerli uygulama etki alanında yürütülürken tüm iş parçacıkları tarafından kullanılan toplam işlemci zamanı işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="d609a-108">[out] A pointer to the total processor time that has been used by all threads while executing in the current application domain since the application domain was created.</span></span> <span data-ttu-id="d609a-109">Bu parametre olabilir `null` .</span><span class="sxs-lookup"><span data-stu-id="d609a-109">This parameter can be `null`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d609a-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d609a-110">Return Value</span></span>  
  
|<span data-ttu-id="d609a-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d609a-111">HRESULT</span></span>|<span data-ttu-id="d609a-112">Description</span><span class="sxs-lookup"><span data-stu-id="d609a-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d609a-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="d609a-113">S_OK</span></span>|<span data-ttu-id="d609a-114">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="d609a-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="d609a-115">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="d609a-115">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="d609a-116">Uygulama etki alanı kaldırıldı veya yok.</span><span class="sxs-lookup"><span data-stu-id="d609a-116">The application domain has been unloaded or does not exist.</span></span>|  
|<span data-ttu-id="d609a-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d609a-117">E_FAIL</span></span>|<span data-ttu-id="d609a-118">Uygulama etki alanı kaynak izleme etkin değil.</span><span class="sxs-lookup"><span data-stu-id="d609a-118">Application domain resource monitoring is not enabled.</span></span><br /><br /> <span data-ttu-id="d609a-119">-veya-</span><span class="sxs-lookup"><span data-stu-id="d609a-119">-or-</span></span><br /><br /> <span data-ttu-id="d609a-120">Diğer tüm arızalar.</span><span class="sxs-lookup"><span data-stu-id="d609a-120">All other failures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d609a-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d609a-121">Remarks</span></span>  

 <span data-ttu-id="d609a-122">Bu yöntem, yönetilen özelliğin yönetilmeyen eşdeğeridir <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="d609a-122">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d609a-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d609a-123">Requirements</span></span>  

 <span data-ttu-id="d609a-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d609a-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d609a-125">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="d609a-125">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d609a-126">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="d609a-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d609a-127">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d609a-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d609a-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d609a-128">See also</span></span>

- [<span data-ttu-id="d609a-129">ICLRAppDomainResourceMonitor Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d609a-129">ICLRAppDomainResourceMonitor Interface</span></span>](iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="d609a-130">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d609a-130">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="d609a-131">Uygulama etki alanı kaynak Izleme</span><span class="sxs-lookup"><span data-stu-id="d609a-131">Application Domain Resource Monitoring</span></span>](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="d609a-132">Hosting</span><span class="sxs-lookup"><span data-stu-id="d609a-132">Hosting</span></span>](index.md)
