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
ms.openlocfilehash: 408ef5419fbc2081d25ad442986ec8155bcb4c62
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59141550"
---
# <a name="iclrappdomainresourcemonitorgetcurrentsurvived-method"></a><span data-ttu-id="701cc-102">ICLRAppDomainResourceMonitor::GetCurrentSurvived Metodu</span><span class="sxs-lookup"><span data-stu-id="701cc-102">ICLRAppDomainResourceMonitor::GetCurrentSurvived Method</span></span>
<span data-ttu-id="701cc-103">Atık toplamayı engelleme son tam kurtulan ve geçerli uygulama etki alanı tarafından başvurulan bayt sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="701cc-103">Gets the number of bytes that survived the last full, blocking garbage collection and that are referenced by the current application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="701cc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="701cc-104">Syntax</span></span>  
  
```  
HRESULT STDMETHODCALLTYPE GetCurrentSurvived(  
             [in]  DWORD dwAppDomainId,  
             [out] ULONGLONG *pAppDomainBytesSurvived,  
             [out] ULONGLONG *pTotalBytesSurvived);  
```  
  
## <a name="parameters"></a><span data-ttu-id="701cc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="701cc-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="701cc-106">[in] İstenen uygulama etki alanı kimliği.</span><span class="sxs-lookup"><span data-stu-id="701cc-106">[in] The ID of the requested application domain.</span></span>  
  
 `pAppDomainBytesSurvived`  
 <span data-ttu-id="701cc-107">[out] Bu uygulama etki alanı tarafından tutulan sonra son çöp toplamadan kurtulan bayt sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="701cc-107">[out] A pointer to the number of bytes that survived after the last garbage collection that are held by this application domain.</span></span> <span data-ttu-id="701cc-108">Tam bir koleksiyon sonra bu sayı, doğru ve eksiksiz olması.</span><span class="sxs-lookup"><span data-stu-id="701cc-108">After a full collection, this number is accurate and complete.</span></span> <span data-ttu-id="701cc-109">Kısa ömürlü bir toplamanın ardından bu sayı olası eksik.</span><span class="sxs-lookup"><span data-stu-id="701cc-109">After an ephemeral collection, this number is potentially incomplete.</span></span> <span data-ttu-id="701cc-110">Bu parametre olabilir `null`.</span><span class="sxs-lookup"><span data-stu-id="701cc-110">This parameter can be `null`.</span></span>  
  
 `pRuntimeBytesSurvived`  
 <span data-ttu-id="701cc-111">[out] Toplam son çöp toplamadan kurtulan bayt sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="701cc-111">[out] A pointer to the total number of bytes that survived from the last garbage collection.</span></span> <span data-ttu-id="701cc-112">Tam bir koleksiyon sonra bu sayı, yönetilen yığın içinde tutulan bayt sayısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="701cc-112">After a full collection, this number represents the number of the bytes that are held in managed heaps.</span></span> <span data-ttu-id="701cc-113">Kısa ömürlü bir toplamanın ardından bu sayı, kısa ömürlü nesillerde Canlı tutulan bayt sayısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="701cc-113">After an ephemeral collection, this number represents the number of bytes that are held live in ephemeral generations.</span></span> <span data-ttu-id="701cc-114">Bu parametre olabilir `null`.</span><span class="sxs-lookup"><span data-stu-id="701cc-114">This parameter can be `null`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="701cc-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="701cc-115">Return Value</span></span>  
 <span data-ttu-id="701cc-116">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="701cc-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="701cc-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="701cc-117">HRESULT</span></span>|<span data-ttu-id="701cc-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="701cc-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="701cc-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="701cc-119">S_OK</span></span>|<span data-ttu-id="701cc-120">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="701cc-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="701cc-121">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="701cc-121">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="701cc-122">Uygulama etki alanı kaldırıldı veya yok.</span><span class="sxs-lookup"><span data-stu-id="701cc-122">The application domain has been unloaded or does not exist.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="701cc-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="701cc-123">Remarks</span></span>  
 <span data-ttu-id="701cc-124">Atık toplamayı engelleme yalnızca tam sonra İstatistikler güncelleştirilir. diğer bir deyişle, uygulama çalışırken koleksiyonu durdurur ve tüm nesiller içeren bir koleksiyon gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="701cc-124">Statistics are updated only after a full, blocking garbage collection; that is, a collection that includes all generations and that stops the application while collection occurs.</span></span> <span data-ttu-id="701cc-125">Örneğin, <xref:System.GC.Collect?displayProperty=nameWithType> yöntemi aşırı yüklemesi, tam toplamayı engelleme, gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="701cc-125">For example, the <xref:System.GC.Collect?displayProperty=nameWithType> method overload performs a full, blocking collection.</span></span> <span data-ttu-id="701cc-126">Eş zamanlı çöp toplama, arka planda gerçekleşir ve uygulamayı engellemez.</span><span class="sxs-lookup"><span data-stu-id="701cc-126">Concurrent garbage collection occurs in the background and does not block the application.</span></span>  
  
 <span data-ttu-id="701cc-127">`GetCurrentSurvived` Yöntemdir yönetilen yönetilmeyen eşdeğerini <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="701cc-127">The `GetCurrentSurvived` method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="701cc-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="701cc-128">Requirements</span></span>  
 <span data-ttu-id="701cc-129">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="701cc-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="701cc-130">**Üst bilgi:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="701cc-130">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="701cc-131">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="701cc-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="701cc-132">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="701cc-132">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="701cc-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="701cc-133">See also</span></span>

- [<span data-ttu-id="701cc-134">ICLRAppDomainResourceMonitor Arabirimi</span><span class="sxs-lookup"><span data-stu-id="701cc-134">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="701cc-135">Uygulama Etki Alanı Kaynak İzleme</span><span class="sxs-lookup"><span data-stu-id="701cc-135">Application Domain Resource Monitoring</span></span>](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="701cc-136">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="701cc-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="701cc-137">Barındırma</span><span class="sxs-lookup"><span data-stu-id="701cc-137">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
