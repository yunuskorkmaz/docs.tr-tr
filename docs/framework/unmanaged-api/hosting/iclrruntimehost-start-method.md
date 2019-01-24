---
title: ICLRRuntimeHost::Start Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.Start
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::Start
helpviewer_keywords:
- ICLRRuntimeHost::Start method [.NET Framework hosting]
- Start method, ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: c0a6dce5-0a8d-42e8-808b-6ca14df9d289
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c36d1e4aea284db6111ae1b7df6a683e5d5d85c2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54561182"
---
# <a name="iclrruntimehoststart-method"></a><span data-ttu-id="b2ef6-102">ICLRRuntimeHost::Start Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b2ef6-102">ICLRRuntimeHost::Start Method</span></span>
<span data-ttu-id="b2ef6-103">Ortak dil çalışma zamanı (CLR) işlem içine başlatır.</span><span class="sxs-lookup"><span data-stu-id="b2ef6-103">Initializes the common language runtime (CLR) into a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2ef6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b2ef6-104">Syntax</span></span>  
  
```  
HRESULT Start();  
```  
  
## <a name="return-value"></a><span data-ttu-id="b2ef6-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b2ef6-105">Return Value</span></span>  
  
|<span data-ttu-id="b2ef6-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b2ef6-106">HRESULT</span></span>|<span data-ttu-id="b2ef6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b2ef6-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b2ef6-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="b2ef6-108">S_OK</span></span>|<span data-ttu-id="b2ef6-109">`Start` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="b2ef6-109">`Start` returned successfully.</span></span>|  
|<span data-ttu-id="b2ef6-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b2ef6-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b2ef6-111">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="b2ef6-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b2ef6-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b2ef6-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b2ef6-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="b2ef6-113">The call timed out.</span></span>|  
|<span data-ttu-id="b2ef6-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b2ef6-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b2ef6-115">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="b2ef6-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b2ef6-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b2ef6-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b2ef6-117">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="b2ef6-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b2ef6-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b2ef6-118">E_FAIL</span></span>|<span data-ttu-id="b2ef6-119">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="b2ef6-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b2ef6-120">CLR, artık bir yöntem E_FAIL döndürürse, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b2ef6-120">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b2ef6-121">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="b2ef6-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2ef6-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b2ef6-122">Remarks</span></span>  
 <span data-ttu-id="b2ef6-123">Birçok senaryoda bu çağrı gerekli değildir `Start`, çalışma zamanının kendisi otomatik olarak yönetilen kodu çalıştırmak için ilk istek üzerine başlatılır.</span><span class="sxs-lookup"><span data-stu-id="b2ef6-123">In many scenarios it is not necessary to call `Start`, because the runtime will initialize itself automatically upon the first request to run managed code.</span></span> <span data-ttu-id="b2ef6-124">Ancak, kullanabileceğiniz `Start` tam olarak ne zaman çalışma zamanı başlatılmalıdır belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="b2ef6-124">You can, however, use `Start` to specify exactly when the runtime should be initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2ef6-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b2ef6-125">Requirements</span></span>  
 <span data-ttu-id="b2ef6-126">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2ef6-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2ef6-127">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b2ef6-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b2ef6-128">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="b2ef6-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b2ef6-129">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2ef6-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2ef6-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2ef6-130">See also</span></span>
- <xref:System.AppDomain>
- [<span data-ttu-id="b2ef6-131">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b2ef6-131">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
