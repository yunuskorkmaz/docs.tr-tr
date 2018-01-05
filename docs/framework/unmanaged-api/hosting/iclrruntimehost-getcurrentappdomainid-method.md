---
title: ICLRRuntimeHost::GetCurrentAppDomainId Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeHost.GetCurrentAppDomainId
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeHost::GetCurrentAppDomainId
helpviewer_keywords:
- ICLRRuntimeHost::GetCurrentAppDomainId method [.NET Framework hosting]
- GetCurrentAppDomainId method [.NET Framework hosting]
ms.assetid: 33800475-7815-4976-8aca-a1038761a2ef
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5e4e682ae71512e24d91ea7e4e12a8a2dd70f1de
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimehostgetcurrentappdomainid-method"></a><span data-ttu-id="32e4c-102">ICLRRuntimeHost::GetCurrentAppDomainId Metodu</span><span class="sxs-lookup"><span data-stu-id="32e4c-102">ICLRRuntimeHost::GetCurrentAppDomainId Method</span></span>
<span data-ttu-id="32e4c-103">Sayısal tanımlayıcısını alır <xref:System.AppDomain> , şu anda yürütülüyor.</span><span class="sxs-lookup"><span data-stu-id="32e4c-103">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32e4c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="32e4c-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentAppDomainId(  
    [out] DWORD* pdwAppDomainId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="32e4c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="32e4c-105">Parameters</span></span>  
 `pdwAppDomainId`  
 <span data-ttu-id="32e4c-106">[out] Sayısal tanıtıcısı <xref:System.AppDomain> , şu anda yürütülüyor.</span><span class="sxs-lookup"><span data-stu-id="32e4c-106">[out] The numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="32e4c-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="32e4c-107">Return Value</span></span>  
  
|<span data-ttu-id="32e4c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="32e4c-108">HRESULT</span></span>|<span data-ttu-id="32e4c-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="32e4c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="32e4c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="32e4c-110">S_OK</span></span>|<span data-ttu-id="32e4c-111">`GetCurrentAppDomainId`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="32e4c-111">`GetCurrentAppDomainId` returned successfully.</span></span>|  
|<span data-ttu-id="32e4c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="32e4c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="32e4c-113">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="32e4c-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="32e4c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="32e4c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="32e4c-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="32e4c-115">The call timed out.</span></span>|  
|<span data-ttu-id="32e4c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="32e4c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="32e4c-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="32e4c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="32e4c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="32e4c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="32e4c-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="32e4c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="32e4c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="32e4c-120">E_FAIL</span></span>|<span data-ttu-id="32e4c-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="32e4c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="32e4c-122">Bir yöntem E_FAIL döndürürse, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="32e4c-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="32e4c-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="32e4c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="32e4c-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="32e4c-124">Remarks</span></span>  
 <span data-ttu-id="32e4c-125">`pdwAppDomainId` Parametre değerine ayarlanmış <xref:System.AppDomain.Id%2A> özelliği <xref:System.AppDomain> , geçerli iş parçacığının yürütürken.</span><span class="sxs-lookup"><span data-stu-id="32e4c-125">The `pdwAppDomainId` parameter is set to the value of the <xref:System.AppDomain.Id%2A> property of the <xref:System.AppDomain> in which the current thread is executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32e4c-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="32e4c-126">Requirements</span></span>  
 <span data-ttu-id="32e4c-127">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32e4c-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32e4c-128">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="32e4c-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="32e4c-129">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="32e4c-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="32e4c-130">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32e4c-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32e4c-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="32e4c-131">See Also</span></span>  
 <xref:System.AppDomain>  
 <xref:System.AppDomainManager>  
 [<span data-ttu-id="32e4c-132">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="32e4c-132">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
