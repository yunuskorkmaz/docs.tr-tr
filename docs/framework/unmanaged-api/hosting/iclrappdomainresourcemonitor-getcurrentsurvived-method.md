---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bf285b6e1f703c8776937fa33c7ab5801f04f80f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950152"
---
# <a name="iclrappdomainresourcemonitorgetcurrentsurvived-method"></a><span data-ttu-id="7ffcf-102">ICLRAppDomainResourceMonitor::GetCurrentSurvived Metodu</span><span class="sxs-lookup"><span data-stu-id="7ffcf-102">ICLRAppDomainResourceMonitor::GetCurrentSurvived Method</span></span>
<span data-ttu-id="7ffcf-103">Son tam ve çöp toplamayı engelleyen ve geçerli uygulama etki alanı tarafından başvurulan bayt sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="7ffcf-103">Gets the number of bytes that survived the last full, blocking garbage collection and that are referenced by the current application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ffcf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7ffcf-104">Syntax</span></span>  
  
```cpp  
HRESULT STDMETHODCALLTYPE GetCurrentSurvived(  
             [in]  DWORD dwAppDomainId,  
             [out] ULONGLONG *pAppDomainBytesSurvived,  
             [out] ULONGLONG *pTotalBytesSurvived);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ffcf-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7ffcf-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="7ffcf-106">'ndaki İstenen uygulama etki alanının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="7ffcf-106">[in] The ID of the requested application domain.</span></span>  
  
 `pAppDomainBytesSurvived`  
 <span data-ttu-id="7ffcf-107">dışı Bu uygulama etki alanı tarafından tutulan son çöp toplamadan sonra kalan bayt sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7ffcf-107">[out] A pointer to the number of bytes that survived after the last garbage collection that are held by this application domain.</span></span> <span data-ttu-id="7ffcf-108">Tam bir koleksiyon sonrasında bu sayı doğru ve tamamlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="7ffcf-108">After a full collection, this number is accurate and complete.</span></span> <span data-ttu-id="7ffcf-109">Kısa ömürlü bir koleksiyon sonrasında bu sayı muhtemelen tamamlanmamış olur.</span><span class="sxs-lookup"><span data-stu-id="7ffcf-109">After an ephemeral collection, this number is potentially incomplete.</span></span> <span data-ttu-id="7ffcf-110">Bu parametre `null`olabilir.</span><span class="sxs-lookup"><span data-stu-id="7ffcf-110">This parameter can be `null`.</span></span>  
  
 `pRuntimeBytesSurvived`  
 <span data-ttu-id="7ffcf-111">dışı Son çöp toplamadan kalan toplam bayt sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7ffcf-111">[out] A pointer to the total number of bytes that survived from the last garbage collection.</span></span> <span data-ttu-id="7ffcf-112">Tam bir koleksiyon sonrasında bu sayı, yönetilen yığınlardaki tutulan baytların sayısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7ffcf-112">After a full collection, this number represents the number of the bytes that are held in managed heaps.</span></span> <span data-ttu-id="7ffcf-113">Kısa ömürlü bir koleksiyon sonrasında bu sayı, kısa ömürlü neslerde canlı tutulan bayt sayısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7ffcf-113">After an ephemeral collection, this number represents the number of bytes that are held live in ephemeral generations.</span></span> <span data-ttu-id="7ffcf-114">Bu parametre `null`olabilir.</span><span class="sxs-lookup"><span data-stu-id="7ffcf-114">This parameter can be `null`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7ffcf-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7ffcf-115">Return Value</span></span>  
 <span data-ttu-id="7ffcf-116">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="7ffcf-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="7ffcf-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7ffcf-117">HRESULT</span></span>|<span data-ttu-id="7ffcf-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7ffcf-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7ffcf-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="7ffcf-119">S_OK</span></span>|<span data-ttu-id="7ffcf-120">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="7ffcf-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="7ffcf-121">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="7ffcf-121">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="7ffcf-122">Uygulama etki alanı kaldırıldı veya yok.</span><span class="sxs-lookup"><span data-stu-id="7ffcf-122">The application domain has been unloaded or does not exist.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ffcf-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7ffcf-123">Remarks</span></span>  
 <span data-ttu-id="7ffcf-124">İstatistikler, yalnızca tam ve çöp toplama işlemleri engellendikten sonra güncelleştirilir; diğer bir deyişle, koleksiyon gerçekleştiğinde uygulamayı durduran tüm nesilleri içeren bir koleksiyon.</span><span class="sxs-lookup"><span data-stu-id="7ffcf-124">Statistics are updated only after a full, blocking garbage collection; that is, a collection that includes all generations and that stops the application while collection occurs.</span></span> <span data-ttu-id="7ffcf-125">Örneğin, <xref:System.GC.Collect?displayProperty=nameWithType> yöntem aşırı yüklemesi tam, engelleyici bir koleksiyon gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="7ffcf-125">For example, the <xref:System.GC.Collect?displayProperty=nameWithType> method overload performs a full, blocking collection.</span></span> <span data-ttu-id="7ffcf-126">Eşzamanlı çöp toplama, arka planda gerçekleşir ve uygulamayı engellemez.</span><span class="sxs-lookup"><span data-stu-id="7ffcf-126">Concurrent garbage collection occurs in the background and does not block the application.</span></span>  
  
 <span data-ttu-id="7ffcf-127">Yöntemi, yönetilen <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> özelliğin yönetilmeyen eşdeğeridir. `GetCurrentSurvived`</span><span class="sxs-lookup"><span data-stu-id="7ffcf-127">The `GetCurrentSurvived` method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ffcf-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7ffcf-128">Requirements</span></span>  
 <span data-ttu-id="7ffcf-129">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ffcf-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ffcf-130">**Üst bilgi** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="7ffcf-130">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7ffcf-131">**Kitaplığı** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="7ffcf-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7ffcf-132">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ffcf-132">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ffcf-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ffcf-133">See also</span></span>

- [<span data-ttu-id="7ffcf-134">ICLRAppDomainResourceMonitor Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7ffcf-134">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="7ffcf-135">Uygulama Etki Alanı Kaynak İzleme</span><span class="sxs-lookup"><span data-stu-id="7ffcf-135">Application Domain Resource Monitoring</span></span>](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="7ffcf-136">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7ffcf-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="7ffcf-137">Barındırma</span><span class="sxs-lookup"><span data-stu-id="7ffcf-137">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
