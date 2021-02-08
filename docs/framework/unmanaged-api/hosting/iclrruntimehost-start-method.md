---
description: ': ICLRRuntimeHost:: Start yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 0ada729c9a90b23fb1573a2101845028e5e2fe76
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785087"
---
# <a name="iclrruntimehoststart-method"></a><span data-ttu-id="17420-103">ICLRRuntimeHost::Start Yöntemi</span><span class="sxs-lookup"><span data-stu-id="17420-103">ICLRRuntimeHost::Start Method</span></span>

<span data-ttu-id="17420-104">Ortak dil çalışma zamanını (CLR) bir işleme başlatır.</span><span class="sxs-lookup"><span data-stu-id="17420-104">Initializes the common language runtime (CLR) into a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17420-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="17420-105">Syntax</span></span>  
  
```cpp  
HRESULT Start();  
```  
  
## <a name="return-value"></a><span data-ttu-id="17420-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="17420-106">Return Value</span></span>  
  
|<span data-ttu-id="17420-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="17420-107">HRESULT</span></span>|<span data-ttu-id="17420-108">Description</span><span class="sxs-lookup"><span data-stu-id="17420-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="17420-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="17420-109">S_OK</span></span>|<span data-ttu-id="17420-110">`Start` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="17420-110">`Start` returned successfully.</span></span>|  
|<span data-ttu-id="17420-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="17420-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="17420-112">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="17420-112">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="17420-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="17420-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="17420-114">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="17420-114">The call timed out.</span></span>|  
|<span data-ttu-id="17420-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="17420-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="17420-116">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="17420-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="17420-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="17420-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="17420-118">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="17420-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="17420-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="17420-119">E_FAIL</span></span>|<span data-ttu-id="17420-120">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="17420-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="17420-121">Bir yöntem E_FAIL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="17420-121">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="17420-122">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="17420-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17420-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="17420-123">Remarks</span></span>  

 <span data-ttu-id="17420-124">Birçok senaryoda `Start` , çalışma zamanı, yönetilen kodu çalıştırmak için ilk istek üzerine otomatik olarak başlatılacak olduğundan, bu çağrı için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="17420-124">In many scenarios it is not necessary to call `Start`, because the runtime will initialize itself automatically upon the first request to run managed code.</span></span> <span data-ttu-id="17420-125">Bununla birlikte, yalnızca `Start` çalışma zamanının başlatılması gerektiğinde tam olarak belirtmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="17420-125">You can, however, use `Start` to specify exactly when the runtime should be initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17420-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="17420-126">Requirements</span></span>  

 <span data-ttu-id="17420-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17420-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17420-128">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="17420-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="17420-129">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="17420-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="17420-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17420-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17420-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17420-131">See also</span></span>

- <xref:System.AppDomain>
- [<span data-ttu-id="17420-132">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17420-132">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
