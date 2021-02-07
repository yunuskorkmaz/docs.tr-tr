---
description: ': Iclartppdomainresourcemonitor:: GetCurrentSurvived yöntemi hakkında daha fazla bilgi edinin'
title: ICLRAppDomainResourceMonitor::GetCurrentSurvived Metodu
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentSurvived
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentSurvived
helpviewer_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentSurvived method [.NET Framework hosting]
- GetCurrentSurvived method [.NET Framework hosting]
ms.assetid: 392e9009-40ef-40e3-ad4d-7ce93a989e78
topic_type:
- apiref
ms.openlocfilehash: 20aea8583da207144aa0ffe29591a113da789fa8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753919"
---
# <a name="iclrappdomainresourcemonitorgetcurrentsurvived-method"></a><span data-ttu-id="4145c-103">ICLRAppDomainResourceMonitor::GetCurrentSurvived Metodu</span><span class="sxs-lookup"><span data-stu-id="4145c-103">ICLRAppDomainResourceMonitor::GetCurrentSurvived Method</span></span>

<span data-ttu-id="4145c-104">Son tam ve çöp toplamayı engelleyen ve geçerli uygulama etki alanı tarafından başvurulan bayt sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="4145c-104">Gets the number of bytes that survived the last full, blocking garbage collection and that are referenced by the current application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4145c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4145c-105">Syntax</span></span>  
  
```cpp  
HRESULT STDMETHODCALLTYPE GetCurrentSurvived(  
             [in]  DWORD dwAppDomainId,  
             [out] ULONGLONG *pAppDomainBytesSurvived,  
             [out] ULONGLONG *pTotalBytesSurvived);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4145c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4145c-106">Parameters</span></span>  

 `dwAppDomainId`  
 <span data-ttu-id="4145c-107">'ndaki İstenen uygulama etki alanının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="4145c-107">[in] The ID of the requested application domain.</span></span>  
  
 `pAppDomainBytesSurvived`  
 <span data-ttu-id="4145c-108">dışı Bu uygulama etki alanı tarafından tutulan son çöp toplamadan sonra kalan bayt sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4145c-108">[out] A pointer to the number of bytes that survived after the last garbage collection that are held by this application domain.</span></span> <span data-ttu-id="4145c-109">Tam bir koleksiyon sonrasında bu sayı doğru ve tamamlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="4145c-109">After a full collection, this number is accurate and complete.</span></span> <span data-ttu-id="4145c-110">Kısa ömürlü bir koleksiyon sonrasında bu sayı muhtemelen tamamlanmamış olur.</span><span class="sxs-lookup"><span data-stu-id="4145c-110">After an ephemeral collection, this number is potentially incomplete.</span></span> <span data-ttu-id="4145c-111">Bu parametre olabilir `null` .</span><span class="sxs-lookup"><span data-stu-id="4145c-111">This parameter can be `null`.</span></span>  
  
 `pRuntimeBytesSurvived`  
 <span data-ttu-id="4145c-112">dışı Son çöp toplamadan kalan toplam bayt sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4145c-112">[out] A pointer to the total number of bytes that survived from the last garbage collection.</span></span> <span data-ttu-id="4145c-113">Tam bir koleksiyon sonrasında bu sayı, yönetilen yığınlardaki tutulan baytların sayısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4145c-113">After a full collection, this number represents the number of the bytes that are held in managed heaps.</span></span> <span data-ttu-id="4145c-114">Kısa ömürlü bir koleksiyon sonrasında bu sayı, kısa ömürlü neslerde canlı tutulan bayt sayısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4145c-114">After an ephemeral collection, this number represents the number of bytes that are held live in ephemeral generations.</span></span> <span data-ttu-id="4145c-115">Bu parametre olabilir `null` .</span><span class="sxs-lookup"><span data-stu-id="4145c-115">This parameter can be `null`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4145c-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4145c-116">Return Value</span></span>  

 <span data-ttu-id="4145c-117">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="4145c-117">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="4145c-118">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4145c-118">HRESULT</span></span>|<span data-ttu-id="4145c-119">Description</span><span class="sxs-lookup"><span data-stu-id="4145c-119">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4145c-120">S_OK</span><span class="sxs-lookup"><span data-stu-id="4145c-120">S_OK</span></span>|<span data-ttu-id="4145c-121">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="4145c-121">The method completed successfully.</span></span>|  
|<span data-ttu-id="4145c-122">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="4145c-122">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="4145c-123">Uygulama etki alanı kaldırıldı veya yok.</span><span class="sxs-lookup"><span data-stu-id="4145c-123">The application domain has been unloaded or does not exist.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4145c-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4145c-124">Remarks</span></span>  

 <span data-ttu-id="4145c-125">İstatistikler, yalnızca tam ve çöp toplama işlemleri engellendikten sonra güncelleştirilir; diğer bir deyişle, koleksiyon gerçekleştiğinde uygulamayı durduran tüm nesilleri içeren bir koleksiyon.</span><span class="sxs-lookup"><span data-stu-id="4145c-125">Statistics are updated only after a full, blocking garbage collection; that is, a collection that includes all generations and that stops the application while collection occurs.</span></span> <span data-ttu-id="4145c-126">Örneğin, <xref:System.GC.Collect?displayProperty=nameWithType> yöntem aşırı yüklemesi tam, engelleyici bir koleksiyon gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="4145c-126">For example, the <xref:System.GC.Collect?displayProperty=nameWithType> method overload performs a full, blocking collection.</span></span> <span data-ttu-id="4145c-127">Eşzamanlı çöp toplama, arka planda gerçekleşir ve uygulamayı engellemez.</span><span class="sxs-lookup"><span data-stu-id="4145c-127">Concurrent garbage collection occurs in the background and does not block the application.</span></span>  
  
 <span data-ttu-id="4145c-128">`GetCurrentSurvived`Yöntemi, yönetilen özelliğin yönetilmeyen eşdeğeridir <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="4145c-128">The `GetCurrentSurvived` method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4145c-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4145c-129">Requirements</span></span>  

 <span data-ttu-id="4145c-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4145c-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4145c-131">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="4145c-131">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="4145c-132">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="4145c-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4145c-133">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4145c-133">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4145c-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4145c-134">See also</span></span>

- [<span data-ttu-id="4145c-135">ICLRAppDomainResourceMonitor Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4145c-135">ICLRAppDomainResourceMonitor Interface</span></span>](iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="4145c-136">Uygulama etki alanı kaynak Izleme</span><span class="sxs-lookup"><span data-stu-id="4145c-136">Application Domain Resource Monitoring</span></span>](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="4145c-137">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4145c-137">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="4145c-138">Hosting</span><span class="sxs-lookup"><span data-stu-id="4145c-138">Hosting</span></span>](index.md)
