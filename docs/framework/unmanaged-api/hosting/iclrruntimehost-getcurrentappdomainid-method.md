---
title: ICLRRuntimeHost::GetCurrentAppDomainId Metodu
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
ms.openlocfilehash: cbe6ac3c9f03de2224f933a7e44325f578ded48b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433917"
---
# <a name="iclrruntimehostgetcurrentappdomainid-method"></a><span data-ttu-id="79264-102">ICLRRuntimeHost::GetCurrentAppDomainId Metodu</span><span class="sxs-lookup"><span data-stu-id="79264-102">ICLRRuntimeHost::GetCurrentAppDomainId Method</span></span>
<span data-ttu-id="79264-103">Sayısal tanımlayıcısını alır <xref:System.AppDomain> , şu anda yürütülüyor.</span><span class="sxs-lookup"><span data-stu-id="79264-103">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79264-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="79264-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentAppDomainId(  
    [out] DWORD* pdwAppDomainId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="79264-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="79264-105">Parameters</span></span>  
 `pdwAppDomainId`  
 <span data-ttu-id="79264-106">[out] Sayısal tanıtıcısı <xref:System.AppDomain> , şu anda yürütülüyor.</span><span class="sxs-lookup"><span data-stu-id="79264-106">[out] The numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="79264-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="79264-107">Return Value</span></span>  
  
|<span data-ttu-id="79264-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="79264-108">HRESULT</span></span>|<span data-ttu-id="79264-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="79264-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="79264-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="79264-110">S_OK</span></span>|<span data-ttu-id="79264-111">`GetCurrentAppDomainId` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="79264-111">`GetCurrentAppDomainId` returned successfully.</span></span>|  
|<span data-ttu-id="79264-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="79264-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="79264-113">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="79264-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="79264-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="79264-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="79264-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="79264-115">The call timed out.</span></span>|  
|<span data-ttu-id="79264-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="79264-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="79264-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="79264-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="79264-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="79264-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="79264-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="79264-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="79264-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="79264-120">E_FAIL</span></span>|<span data-ttu-id="79264-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="79264-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="79264-122">Bir yöntem E_FAIL döndürürse, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="79264-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="79264-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="79264-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79264-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="79264-124">Remarks</span></span>  
 <span data-ttu-id="79264-125">`pdwAppDomainId` Parametre değerine ayarlanmış <xref:System.AppDomain.Id%2A> özelliği <xref:System.AppDomain> , geçerli iş parçacığının yürütürken.</span><span class="sxs-lookup"><span data-stu-id="79264-125">The `pdwAppDomainId` parameter is set to the value of the <xref:System.AppDomain.Id%2A> property of the <xref:System.AppDomain> in which the current thread is executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79264-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="79264-126">Requirements</span></span>  
 <span data-ttu-id="79264-127">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79264-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79264-128">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="79264-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="79264-129">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="79264-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="79264-130">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79264-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79264-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="79264-131">See Also</span></span>  
 <xref:System.AppDomain>  
 <xref:System.AppDomainManager>  
 [<span data-ttu-id="79264-132">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="79264-132">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
