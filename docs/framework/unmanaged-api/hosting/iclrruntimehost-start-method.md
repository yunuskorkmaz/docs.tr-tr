---
title: "ICLRRuntimeHost::Start Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a9705e4449da3b485bef7e7250ca08473d51387b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimehoststart-method"></a><span data-ttu-id="767e1-102">ICLRRuntimeHost::Start Yöntemi</span><span class="sxs-lookup"><span data-stu-id="767e1-102">ICLRRuntimeHost::Start Method</span></span>
<span data-ttu-id="767e1-103">Ortak dil çalışma zamanı (CLR) süreç içine başlatır.</span><span class="sxs-lookup"><span data-stu-id="767e1-103">Initializes the common language runtime (CLR) into a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="767e1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="767e1-104">Syntax</span></span>  
  
```  
HRESULT Start();  
```  
  
## <a name="return-value"></a><span data-ttu-id="767e1-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="767e1-105">Return Value</span></span>  
  
|<span data-ttu-id="767e1-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="767e1-106">HRESULT</span></span>|<span data-ttu-id="767e1-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="767e1-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="767e1-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="767e1-108">S_OK</span></span>|<span data-ttu-id="767e1-109">`Start`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="767e1-109">`Start` returned successfully.</span></span>|  
|<span data-ttu-id="767e1-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="767e1-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="767e1-111">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="767e1-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="767e1-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="767e1-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="767e1-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="767e1-113">The call timed out.</span></span>|  
|<span data-ttu-id="767e1-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="767e1-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="767e1-115">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="767e1-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="767e1-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="767e1-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="767e1-117">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="767e1-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="767e1-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="767e1-118">E_FAIL</span></span>|<span data-ttu-id="767e1-119">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="767e1-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="767e1-120">Bir yöntem E_FAIL döndürürse, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="767e1-120">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="767e1-121">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="767e1-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="767e1-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="767e1-122">Remarks</span></span>  
 <span data-ttu-id="767e1-123">Birçok senaryoda çağırmak ise gerekli değildir `Start`, çalışma zamanı kendisini otomatik olarak yönetilen kodu çalıştırmak için ilk istek üzerine başlatılır.</span><span class="sxs-lookup"><span data-stu-id="767e1-123">In many scenarios it is not necessary to call `Start`, because the runtime will initialize itself automatically upon the first request to run managed code.</span></span> <span data-ttu-id="767e1-124">Ancak, kullanabilirsiniz `Start` tam olarak ne zaman çalışma zamanı başlatılması belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="767e1-124">You can, however, use `Start` to specify exactly when the runtime should be initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="767e1-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="767e1-125">Requirements</span></span>  
 <span data-ttu-id="767e1-126">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="767e1-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="767e1-127">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="767e1-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="767e1-128">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="767e1-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="767e1-129">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="767e1-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="767e1-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="767e1-130">See Also</span></span>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="767e1-131">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="767e1-131">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
