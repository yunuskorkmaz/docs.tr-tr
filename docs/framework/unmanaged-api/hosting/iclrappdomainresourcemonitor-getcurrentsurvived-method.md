---
title: ICLRAppDomainResourceMonitor::GetCurrentSurvived Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAppDomainResourceMonitor.GetCurrentSurvived
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAppDomainResourceMonitor::GetCurrentSurvived
helpviewer_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentSurvived method [.NET Framework hosting]
- GetCurrentSurvived method [.NET Framework hosting]
ms.assetid: 392e9009-40ef-40e3-ad4d-7ce93a989e78
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b9fe624c83be5dcf762f1c6036f8e4264f0e45c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrappdomainresourcemonitorgetcurrentsurvived-method"></a><span data-ttu-id="e3b4d-102">ICLRAppDomainResourceMonitor::GetCurrentSurvived Metodu</span><span class="sxs-lookup"><span data-stu-id="e3b4d-102">ICLRAppDomainResourceMonitor::GetCurrentSurvived Method</span></span>
<span data-ttu-id="e3b4d-103">Çöp toplama engelleme son tam, derdi bitti ve geçerli uygulama etki alanı tarafından başvurulan bayt sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="e3b4d-103">Gets the number of bytes that survived the last full, blocking garbage collection and that are referenced by the current application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3b4d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e3b4d-104">Syntax</span></span>  
  
```  
HRESULT STDMETHODCALLTYPE GetCurrentSurvived(  
             [in]  DWORD dwAppDomainId,  
             [out] ULONGLONG *pAppDomainBytesSurvived,  
             [out] ULONGLONG *pTotalBytesSurvived);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e3b4d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e3b4d-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="e3b4d-106">[in] İstenen uygulama etki alanı kimliği.</span><span class="sxs-lookup"><span data-stu-id="e3b4d-106">[in] The ID of the requested application domain.</span></span>  
  
 `pAppDomainBytesSurvived`  
 <span data-ttu-id="e3b4d-107">[out] Bu uygulama etki alanı tarafından tutulan son çöp toplamadan sonra derdi bitti bayt sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e3b4d-107">[out] A pointer to the number of bytes that survived after the last garbage collection that are held by this application domain.</span></span> <span data-ttu-id="e3b4d-108">Tam sonra bu sayı doğru ve eksiksiz koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="e3b4d-108">After a full collection, this number is accurate and complete.</span></span> <span data-ttu-id="e3b4d-109">Kısa ömürlü bir koleksiyon sonra bu sayı olası eksik.</span><span class="sxs-lookup"><span data-stu-id="e3b4d-109">After an ephemeral collection, this number is potentially incomplete.</span></span> <span data-ttu-id="e3b4d-110">Bu parametre olabilir `null`.</span><span class="sxs-lookup"><span data-stu-id="e3b4d-110">This parameter can be `null`.</span></span>  
  
 `pRuntimeBytesSurvived`  
 <span data-ttu-id="e3b4d-111">[out] Toplam son çöp koleksiyondan derdi bitti bayt sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e3b4d-111">[out] A pointer to the total number of bytes that survived from the last garbage collection.</span></span> <span data-ttu-id="e3b4d-112">Sonra tam bir koleksiyon, bu sayı Yönetilen yığın tutulan bayt sayısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e3b4d-112">After a full collection, this number represents the number of the bytes that are held in managed heaps.</span></span> <span data-ttu-id="e3b4d-113">Kısa ömürlü bir koleksiyon sonra bu sayı kısa ömürlü kuşakta Canlı tutulur bayt sayısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e3b4d-113">After an ephemeral collection, this number represents the number of bytes that are held live in ephemeral generations.</span></span> <span data-ttu-id="e3b4d-114">Bu parametre olabilir `null`.</span><span class="sxs-lookup"><span data-stu-id="e3b4d-114">This parameter can be `null`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e3b4d-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e3b4d-115">Return Value</span></span>  
 <span data-ttu-id="e3b4d-116">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="e3b4d-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="e3b4d-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e3b4d-117">HRESULT</span></span>|<span data-ttu-id="e3b4d-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e3b4d-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e3b4d-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="e3b4d-119">S_OK</span></span>|<span data-ttu-id="e3b4d-120">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="e3b4d-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="e3b4d-121">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="e3b4d-121">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="e3b4d-122">Uygulama etki alanı kaldırıldı veya yok.</span><span class="sxs-lookup"><span data-stu-id="e3b4d-122">The application domain has been unloaded or does not exist.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3b4d-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e3b4d-123">Remarks</span></span>  
 <span data-ttu-id="e3b4d-124">Çöp toplama engelleme yalnızca tam sonra İstatistikler güncelleştirilir; diğer bir deyişle, tüm nesli içerir ve uygulama koleksiyonunun çalışırken durdurur koleksiyonu oluşur.</span><span class="sxs-lookup"><span data-stu-id="e3b4d-124">Statistics are updated only after a full, blocking garbage collection; that is, a collection that includes all generations and that stops the application while collection occurs.</span></span> <span data-ttu-id="e3b4d-125">Örneğin, <xref:System.GC.Collect?displayProperty=nameWithType> yöntemi aşırı yüklemesini koleksiyon engelleme tam, gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="e3b4d-125">For example, the <xref:System.GC.Collect?displayProperty=nameWithType> method overload performs a full, blocking collection.</span></span> <span data-ttu-id="e3b4d-126">Eşzamanlı atık toplama arka planda gerçekleşir ve uygulamayı engellemez.</span><span class="sxs-lookup"><span data-stu-id="e3b4d-126">Concurrent garbage collection occurs in the background and does not block the application.</span></span>  
  
 <span data-ttu-id="e3b4d-127">`GetCurrentSurvived` Yöntemdir yönetilen yönetilmeyen eşdeğerini <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="e3b4d-127">The `GetCurrentSurvived` method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3b4d-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e3b4d-128">Requirements</span></span>  
 <span data-ttu-id="e3b4d-129">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3b4d-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3b4d-130">**Başlık:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="e3b4d-130">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e3b4d-131">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e3b4d-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e3b4d-132">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3b4d-132">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3b4d-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e3b4d-133">See Also</span></span>  
 [<span data-ttu-id="e3b4d-134">Iclrappdomainresourcemonitor arabirimi</span><span class="sxs-lookup"><span data-stu-id="e3b4d-134">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 [<span data-ttu-id="e3b4d-135">Uygulama etki alanı kaynak izleme</span><span class="sxs-lookup"><span data-stu-id="e3b4d-135">Application Domain Resource Monitoring</span></span>](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)  
 [<span data-ttu-id="e3b4d-136">Barındırma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e3b4d-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="e3b4d-137">Barındırma</span><span class="sxs-lookup"><span data-stu-id="e3b4d-137">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
