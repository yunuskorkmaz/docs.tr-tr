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
ms.openlocfilehash: 8f262c416a6998ed182d0c42d7f00ea7dcb3f898
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768686"
---
# <a name="iclrruntimehostgetcurrentappdomainid-method"></a><span data-ttu-id="bccb8-102">ICLRRuntimeHost::GetCurrentAppDomainId Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bccb8-102">ICLRRuntimeHost::GetCurrentAppDomainId Method</span></span>
<span data-ttu-id="bccb8-103">Sayısal tanımlayıcısını alır <xref:System.AppDomain> , şu anda yürütülüyor.</span><span class="sxs-lookup"><span data-stu-id="bccb8-103">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bccb8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bccb8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentAppDomainId(  
    [out] DWORD* pdwAppDomainId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bccb8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bccb8-105">Parameters</span></span>  
 `pdwAppDomainId`  
 <span data-ttu-id="bccb8-106">[out] Sayısal tanımlayıcısını <xref:System.AppDomain> , şu anda yürütülüyor.</span><span class="sxs-lookup"><span data-stu-id="bccb8-106">[out] The numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bccb8-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bccb8-107">Return Value</span></span>  
  
|<span data-ttu-id="bccb8-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bccb8-108">HRESULT</span></span>|<span data-ttu-id="bccb8-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bccb8-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bccb8-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="bccb8-110">S_OK</span></span>|<span data-ttu-id="bccb8-111">`GetCurrentAppDomainId` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="bccb8-111">`GetCurrentAppDomainId` returned successfully.</span></span>|  
|<span data-ttu-id="bccb8-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bccb8-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bccb8-113">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="bccb8-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bccb8-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bccb8-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bccb8-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="bccb8-115">The call timed out.</span></span>|  
|<span data-ttu-id="bccb8-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bccb8-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bccb8-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="bccb8-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bccb8-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bccb8-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bccb8-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="bccb8-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bccb8-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bccb8-120">E_FAIL</span></span>|<span data-ttu-id="bccb8-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="bccb8-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bccb8-122">CLR, artık bir yöntem E_FAIL döndürürse, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="bccb8-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bccb8-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="bccb8-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bccb8-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bccb8-124">Remarks</span></span>  
 <span data-ttu-id="bccb8-125">`pdwAppDomainId` Parametresi değeri olarak ayarlanırsa <xref:System.AppDomain.Id%2A> özelliği <xref:System.AppDomain> geçerli iş parçacığının yürütülmekte olan içinde.</span><span class="sxs-lookup"><span data-stu-id="bccb8-125">The `pdwAppDomainId` parameter is set to the value of the <xref:System.AppDomain.Id%2A> property of the <xref:System.AppDomain> in which the current thread is executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bccb8-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bccb8-126">Requirements</span></span>  
 <span data-ttu-id="bccb8-127">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bccb8-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bccb8-128">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bccb8-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bccb8-129">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="bccb8-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bccb8-130">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bccb8-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bccb8-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bccb8-131">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainManager>
- [<span data-ttu-id="bccb8-132">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bccb8-132">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
