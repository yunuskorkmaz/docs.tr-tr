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
ms.openlocfilehash: 3a24f51884b5dc55e45d22f33735fe07db770d06
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466927"
---
# <a name="iclrappdomainresourcemonitorgetcurrentsurvived-method"></a><span data-ttu-id="431e6-102">ICLRAppDomainResourceMonitor::GetCurrentSurvived Metodu</span><span class="sxs-lookup"><span data-stu-id="431e6-102">ICLRAppDomainResourceMonitor::GetCurrentSurvived Method</span></span>
<span data-ttu-id="431e6-103">Atık toplamayı engelleme son tam kurtulan ve geçerli uygulama etki alanı tarafından başvurulan bayt sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="431e6-103">Gets the number of bytes that survived the last full, blocking garbage collection and that are referenced by the current application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="431e6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="431e6-104">Syntax</span></span>  
  
```  
HRESULT STDMETHODCALLTYPE GetCurrentSurvived(  
             [in]  DWORD dwAppDomainId,  
             [out] ULONGLONG *pAppDomainBytesSurvived,  
             [out] ULONGLONG *pTotalBytesSurvived);  
```  
  
## <a name="parameters"></a><span data-ttu-id="431e6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="431e6-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="431e6-106">[in] İstenen uygulama etki alanı kimliği.</span><span class="sxs-lookup"><span data-stu-id="431e6-106">[in] The ID of the requested application domain.</span></span>  
  
 `pAppDomainBytesSurvived`  
 <span data-ttu-id="431e6-107">[out] Bu uygulama etki alanı tarafından tutulan sonra son çöp toplamadan kurtulan bayt sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="431e6-107">[out] A pointer to the number of bytes that survived after the last garbage collection that are held by this application domain.</span></span> <span data-ttu-id="431e6-108">Tam bir koleksiyon sonra bu sayı, doğru ve eksiksiz olması.</span><span class="sxs-lookup"><span data-stu-id="431e6-108">After a full collection, this number is accurate and complete.</span></span> <span data-ttu-id="431e6-109">Kısa ömürlü bir toplamanın ardından bu sayı olası eksik.</span><span class="sxs-lookup"><span data-stu-id="431e6-109">After an ephemeral collection, this number is potentially incomplete.</span></span> <span data-ttu-id="431e6-110">Bu parametre olabilir `null`.</span><span class="sxs-lookup"><span data-stu-id="431e6-110">This parameter can be `null`.</span></span>  
  
 `pRuntimeBytesSurvived`  
 <span data-ttu-id="431e6-111">[out] Toplam son çöp toplamadan kurtulan bayt sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="431e6-111">[out] A pointer to the total number of bytes that survived from the last garbage collection.</span></span> <span data-ttu-id="431e6-112">Tam bir koleksiyon sonra bu sayı, yönetilen yığın içinde tutulan bayt sayısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="431e6-112">After a full collection, this number represents the number of the bytes that are held in managed heaps.</span></span> <span data-ttu-id="431e6-113">Kısa ömürlü bir toplamanın ardından bu sayı, kısa ömürlü nesillerde Canlı tutulan bayt sayısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="431e6-113">After an ephemeral collection, this number represents the number of bytes that are held live in ephemeral generations.</span></span> <span data-ttu-id="431e6-114">Bu parametre olabilir `null`.</span><span class="sxs-lookup"><span data-stu-id="431e6-114">This parameter can be `null`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="431e6-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="431e6-115">Return Value</span></span>  
 <span data-ttu-id="431e6-116">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="431e6-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="431e6-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="431e6-117">HRESULT</span></span>|<span data-ttu-id="431e6-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="431e6-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="431e6-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="431e6-119">S_OK</span></span>|<span data-ttu-id="431e6-120">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="431e6-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="431e6-121">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="431e6-121">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="431e6-122">Uygulama etki alanı kaldırıldı veya yok.</span><span class="sxs-lookup"><span data-stu-id="431e6-122">The application domain has been unloaded or does not exist.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="431e6-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="431e6-123">Remarks</span></span>  
 <span data-ttu-id="431e6-124">Atık toplamayı engelleme yalnızca tam sonra İstatistikler güncelleştirilir. diğer bir deyişle, uygulama çalışırken koleksiyonu durdurur ve tüm nesiller içeren bir koleksiyon gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="431e6-124">Statistics are updated only after a full, blocking garbage collection; that is, a collection that includes all generations and that stops the application while collection occurs.</span></span> <span data-ttu-id="431e6-125">Örneğin, <xref:System.GC.Collect?displayProperty=nameWithType> yöntemi aşırı yüklemesi, tam toplamayı engelleme, gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="431e6-125">For example, the <xref:System.GC.Collect?displayProperty=nameWithType> method overload performs a full, blocking collection.</span></span> <span data-ttu-id="431e6-126">Eş zamanlı çöp toplama, arka planda gerçekleşir ve uygulamayı engellemez.</span><span class="sxs-lookup"><span data-stu-id="431e6-126">Concurrent garbage collection occurs in the background and does not block the application.</span></span>  
  
 <span data-ttu-id="431e6-127">`GetCurrentSurvived` Yöntemdir yönetilen yönetilmeyen eşdeğerini <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="431e6-127">The `GetCurrentSurvived` method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="431e6-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="431e6-128">Requirements</span></span>  
 <span data-ttu-id="431e6-129">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="431e6-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="431e6-130">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="431e6-130">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="431e6-131">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="431e6-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="431e6-132">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="431e6-132">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="431e6-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="431e6-133">See also</span></span>
- [<span data-ttu-id="431e6-134">ICLRAppDomainResourceMonitor Arabirimi</span><span class="sxs-lookup"><span data-stu-id="431e6-134">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="431e6-135">Uygulama Etki Alanı Kaynak İzleme</span><span class="sxs-lookup"><span data-stu-id="431e6-135">Application Domain Resource Monitoring</span></span>](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="431e6-136">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="431e6-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="431e6-137">Barındırma</span><span class="sxs-lookup"><span data-stu-id="431e6-137">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
