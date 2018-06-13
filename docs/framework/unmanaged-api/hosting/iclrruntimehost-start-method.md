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
ms.openlocfilehash: df2747b7cce112e61c6fb99cdb91dc0d56047b9e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432566"
---
# <a name="iclrruntimehoststart-method"></a><span data-ttu-id="f5360-102">ICLRRuntimeHost::Start Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f5360-102">ICLRRuntimeHost::Start Method</span></span>
<span data-ttu-id="f5360-103">Ortak dil çalışma zamanı (CLR) süreç içine başlatır.</span><span class="sxs-lookup"><span data-stu-id="f5360-103">Initializes the common language runtime (CLR) into a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5360-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f5360-104">Syntax</span></span>  
  
```  
HRESULT Start();  
```  
  
## <a name="return-value"></a><span data-ttu-id="f5360-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f5360-105">Return Value</span></span>  
  
|<span data-ttu-id="f5360-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f5360-106">HRESULT</span></span>|<span data-ttu-id="f5360-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f5360-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f5360-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="f5360-108">S_OK</span></span>|<span data-ttu-id="f5360-109">`Start` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="f5360-109">`Start` returned successfully.</span></span>|  
|<span data-ttu-id="f5360-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f5360-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f5360-111">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="f5360-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f5360-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f5360-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f5360-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="f5360-113">The call timed out.</span></span>|  
|<span data-ttu-id="f5360-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f5360-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f5360-115">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="f5360-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f5360-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f5360-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f5360-117">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="f5360-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f5360-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f5360-118">E_FAIL</span></span>|<span data-ttu-id="f5360-119">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="f5360-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f5360-120">Bir yöntem E_FAIL döndürürse, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f5360-120">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f5360-121">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="f5360-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5360-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f5360-122">Remarks</span></span>  
 <span data-ttu-id="f5360-123">Birçok senaryoda çağırmak ise gerekli değildir `Start`, çalışma zamanı kendisini otomatik olarak yönetilen kodu çalıştırmak için ilk istek üzerine başlatılır.</span><span class="sxs-lookup"><span data-stu-id="f5360-123">In many scenarios it is not necessary to call `Start`, because the runtime will initialize itself automatically upon the first request to run managed code.</span></span> <span data-ttu-id="f5360-124">Ancak, kullanabilirsiniz `Start` tam olarak ne zaman çalışma zamanı başlatılması belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="f5360-124">You can, however, use `Start` to specify exactly when the runtime should be initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5360-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f5360-125">Requirements</span></span>  
 <span data-ttu-id="f5360-126">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5360-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5360-127">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f5360-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f5360-128">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="f5360-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f5360-129">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5360-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5360-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f5360-130">See Also</span></span>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="f5360-131">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f5360-131">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
