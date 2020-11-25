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
ms.openlocfilehash: 2358af3dff97dbe648da924bc929dd2f83b12df0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728816"
---
# <a name="iclrruntimehoststart-method"></a><span data-ttu-id="a59a2-102">ICLRRuntimeHost::Start Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a59a2-102">ICLRRuntimeHost::Start Method</span></span>

<span data-ttu-id="a59a2-103">Ortak dil çalışma zamanını (CLR) bir işleme başlatır.</span><span class="sxs-lookup"><span data-stu-id="a59a2-103">Initializes the common language runtime (CLR) into a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a59a2-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="a59a2-104">Syntax</span></span>  
  
```cpp  
HRESULT Start();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a59a2-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a59a2-105">Return Value</span></span>  
  
|<span data-ttu-id="a59a2-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a59a2-106">HRESULT</span></span>|<span data-ttu-id="a59a2-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a59a2-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a59a2-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="a59a2-108">S_OK</span></span>|<span data-ttu-id="a59a2-109">`Start` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="a59a2-109">`Start` returned successfully.</span></span>|  
|<span data-ttu-id="a59a2-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a59a2-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a59a2-111">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="a59a2-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a59a2-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a59a2-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a59a2-113">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="a59a2-113">The call timed out.</span></span>|  
|<span data-ttu-id="a59a2-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a59a2-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a59a2-115">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="a59a2-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a59a2-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a59a2-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a59a2-117">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="a59a2-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a59a2-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a59a2-118">E_FAIL</span></span>|<span data-ttu-id="a59a2-119">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="a59a2-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a59a2-120">Bir yöntem E_FAIL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a59a2-120">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a59a2-121">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="a59a2-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a59a2-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a59a2-122">Remarks</span></span>  

 <span data-ttu-id="a59a2-123">Birçok senaryoda `Start` , çalışma zamanı, yönetilen kodu çalıştırmak için ilk istek üzerine otomatik olarak başlatılacak olduğundan, bu çağrı için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="a59a2-123">In many scenarios it is not necessary to call `Start`, because the runtime will initialize itself automatically upon the first request to run managed code.</span></span> <span data-ttu-id="a59a2-124">Bununla birlikte, yalnızca `Start` çalışma zamanının başlatılması gerektiğinde tam olarak belirtmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a59a2-124">You can, however, use `Start` to specify exactly when the runtime should be initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a59a2-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a59a2-125">Requirements</span></span>  

 <span data-ttu-id="a59a2-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a59a2-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a59a2-127">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a59a2-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a59a2-128">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="a59a2-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a59a2-129">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a59a2-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a59a2-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a59a2-130">See also</span></span>

- <xref:System.AppDomain>
- [<span data-ttu-id="a59a2-131">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a59a2-131">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
