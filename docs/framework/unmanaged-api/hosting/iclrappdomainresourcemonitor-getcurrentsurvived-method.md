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
ms.openlocfilehash: a73c0731c79dea3a0c411fe27a864ec9ac4e20b2
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616027"
---
# <a name="iclrappdomainresourcemonitorgetcurrentsurvived-method"></a><span data-ttu-id="ab0fd-102">ICLRAppDomainResourceMonitor::GetCurrentSurvived Metodu</span><span class="sxs-lookup"><span data-stu-id="ab0fd-102">ICLRAppDomainResourceMonitor::GetCurrentSurvived Method</span></span>
<span data-ttu-id="ab0fd-103">Son tam ve çöp toplamayı engelleyen ve geçerli uygulama etki alanı tarafından başvurulan bayt sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="ab0fd-103">Gets the number of bytes that survived the last full, blocking garbage collection and that are referenced by the current application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab0fd-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ab0fd-104">Syntax</span></span>  
  
```cpp  
HRESULT STDMETHODCALLTYPE GetCurrentSurvived(  
             [in]  DWORD dwAppDomainId,  
             [out] ULONGLONG *pAppDomainBytesSurvived,  
             [out] ULONGLONG *pTotalBytesSurvived);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab0fd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ab0fd-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="ab0fd-106">'ndaki İstenen uygulama etki alanının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="ab0fd-106">[in] The ID of the requested application domain.</span></span>  
  
 `pAppDomainBytesSurvived`  
 <span data-ttu-id="ab0fd-107">dışı Bu uygulama etki alanı tarafından tutulan son çöp toplamadan sonra kalan bayt sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ab0fd-107">[out] A pointer to the number of bytes that survived after the last garbage collection that are held by this application domain.</span></span> <span data-ttu-id="ab0fd-108">Tam bir koleksiyon sonrasında bu sayı doğru ve tamamlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="ab0fd-108">After a full collection, this number is accurate and complete.</span></span> <span data-ttu-id="ab0fd-109">Kısa ömürlü bir koleksiyon sonrasında bu sayı muhtemelen tamamlanmamış olur.</span><span class="sxs-lookup"><span data-stu-id="ab0fd-109">After an ephemeral collection, this number is potentially incomplete.</span></span> <span data-ttu-id="ab0fd-110">Bu parametre olabilir `null` .</span><span class="sxs-lookup"><span data-stu-id="ab0fd-110">This parameter can be `null`.</span></span>  
  
 `pRuntimeBytesSurvived`  
 <span data-ttu-id="ab0fd-111">dışı Son çöp toplamadan kalan toplam bayt sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ab0fd-111">[out] A pointer to the total number of bytes that survived from the last garbage collection.</span></span> <span data-ttu-id="ab0fd-112">Tam bir koleksiyon sonrasında bu sayı, yönetilen yığınlardaki tutulan baytların sayısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ab0fd-112">After a full collection, this number represents the number of the bytes that are held in managed heaps.</span></span> <span data-ttu-id="ab0fd-113">Kısa ömürlü bir koleksiyon sonrasında bu sayı, kısa ömürlü neslerde canlı tutulan bayt sayısını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ab0fd-113">After an ephemeral collection, this number represents the number of bytes that are held live in ephemeral generations.</span></span> <span data-ttu-id="ab0fd-114">Bu parametre olabilir `null` .</span><span class="sxs-lookup"><span data-stu-id="ab0fd-114">This parameter can be `null`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ab0fd-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ab0fd-115">Return Value</span></span>  
 <span data-ttu-id="ab0fd-116">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="ab0fd-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ab0fd-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ab0fd-117">HRESULT</span></span>|<span data-ttu-id="ab0fd-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ab0fd-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ab0fd-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="ab0fd-119">S_OK</span></span>|<span data-ttu-id="ab0fd-120">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="ab0fd-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="ab0fd-121">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="ab0fd-121">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="ab0fd-122">Uygulama etki alanı kaldırıldı veya yok.</span><span class="sxs-lookup"><span data-stu-id="ab0fd-122">The application domain has been unloaded or does not exist.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab0fd-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ab0fd-123">Remarks</span></span>  
 <span data-ttu-id="ab0fd-124">İstatistikler, yalnızca tam ve çöp toplama işlemleri engellendikten sonra güncelleştirilir; diğer bir deyişle, koleksiyon gerçekleştiğinde uygulamayı durduran tüm nesilleri içeren bir koleksiyon.</span><span class="sxs-lookup"><span data-stu-id="ab0fd-124">Statistics are updated only after a full, blocking garbage collection; that is, a collection that includes all generations and that stops the application while collection occurs.</span></span> <span data-ttu-id="ab0fd-125">Örneğin, <xref:System.GC.Collect?displayProperty=nameWithType> yöntem aşırı yüklemesi tam, engelleyici bir koleksiyon gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="ab0fd-125">For example, the <xref:System.GC.Collect?displayProperty=nameWithType> method overload performs a full, blocking collection.</span></span> <span data-ttu-id="ab0fd-126">Eşzamanlı çöp toplama, arka planda gerçekleşir ve uygulamayı engellemez.</span><span class="sxs-lookup"><span data-stu-id="ab0fd-126">Concurrent garbage collection occurs in the background and does not block the application.</span></span>  
  
 <span data-ttu-id="ab0fd-127">`GetCurrentSurvived`Yöntemi, yönetilen özelliğin yönetilmeyen eşdeğeridir <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="ab0fd-127">The `GetCurrentSurvived` method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab0fd-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ab0fd-128">Requirements</span></span>  
 <span data-ttu-id="ab0fd-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab0fd-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab0fd-130">**Üst bilgi:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="ab0fd-130">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ab0fd-131">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="ab0fd-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ab0fd-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab0fd-132">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab0fd-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab0fd-133">See also</span></span>

- [<span data-ttu-id="ab0fd-134">ICLRAppDomainResourceMonitor Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ab0fd-134">ICLRAppDomainResourceMonitor Interface</span></span>](iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="ab0fd-135">Uygulama etki alanı kaynak Izleme</span><span class="sxs-lookup"><span data-stu-id="ab0fd-135">Application Domain Resource Monitoring</span></span>](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="ab0fd-136">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ab0fd-136">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="ab0fd-137">Barındırma</span><span class="sxs-lookup"><span data-stu-id="ab0fd-137">Hosting</span></span>](index.md)
