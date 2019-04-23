---
title: ICLRRuntimeHost::GetCurrentAppDomainId Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.GetCurrentAppDomainId
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::GetCurrentAppDomainId
helpviewer_keywords:
- ICLRRuntimeHost::GetCurrentAppDomainId method [.NET Framework hosting]
- GetCurrentAppDomainId method [.NET Framework hosting]
ms.assetid: 33800475-7815-4976-8aca-a1038761a2ef
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 28d1655bdc3746dab87acef2e2aac6758883e74a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59096218"
---
# <a name="iclrruntimehostgetcurrentappdomainid-method"></a><span data-ttu-id="71d29-102">ICLRRuntimeHost::GetCurrentAppDomainId Yöntemi</span><span class="sxs-lookup"><span data-stu-id="71d29-102">ICLRRuntimeHost::GetCurrentAppDomainId Method</span></span>
<span data-ttu-id="71d29-103">Sayısal tanımlayıcısını alır <xref:System.AppDomain> , şu anda yürütülüyor.</span><span class="sxs-lookup"><span data-stu-id="71d29-103">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71d29-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="71d29-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentAppDomainId(  
    [out] DWORD* pdwAppDomainId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="71d29-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="71d29-105">Parameters</span></span>  
 `pdwAppDomainId`  
 <span data-ttu-id="71d29-106">[out] Sayısal tanımlayıcısını <xref:System.AppDomain> , şu anda yürütülüyor.</span><span class="sxs-lookup"><span data-stu-id="71d29-106">[out] The numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="71d29-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="71d29-107">Return Value</span></span>  
  
|<span data-ttu-id="71d29-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="71d29-108">HRESULT</span></span>|<span data-ttu-id="71d29-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="71d29-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="71d29-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="71d29-110">S_OK</span></span>|<span data-ttu-id="71d29-111">`GetCurrentAppDomainId` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="71d29-111">`GetCurrentAppDomainId` returned successfully.</span></span>|  
|<span data-ttu-id="71d29-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="71d29-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="71d29-113">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="71d29-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="71d29-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="71d29-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="71d29-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="71d29-115">The call timed out.</span></span>|  
|<span data-ttu-id="71d29-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="71d29-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="71d29-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="71d29-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="71d29-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="71d29-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="71d29-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="71d29-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="71d29-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="71d29-120">E_FAIL</span></span>|<span data-ttu-id="71d29-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="71d29-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="71d29-122">CLR, artık bir yöntem E_FAIL döndürürse, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="71d29-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="71d29-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="71d29-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71d29-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="71d29-124">Remarks</span></span>  
 <span data-ttu-id="71d29-125">`pdwAppDomainId` Parametresi değeri olarak ayarlanırsa <xref:System.AppDomain.Id%2A> özelliği <xref:System.AppDomain> geçerli iş parçacığının yürütülmekte olan içinde.</span><span class="sxs-lookup"><span data-stu-id="71d29-125">The `pdwAppDomainId` parameter is set to the value of the <xref:System.AppDomain.Id%2A> property of the <xref:System.AppDomain> in which the current thread is executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71d29-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="71d29-126">Requirements</span></span>  
 <span data-ttu-id="71d29-127">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71d29-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71d29-128">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="71d29-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="71d29-129">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="71d29-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="71d29-130">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71d29-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71d29-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71d29-131">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainManager>
- [<span data-ttu-id="71d29-132">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="71d29-132">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
