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
ms.openlocfilehash: e5ed1cbb640e760d75e1722871453a0bec283bde
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703906"
---
# <a name="iclrruntimehoststart-method"></a><span data-ttu-id="8b751-102">ICLRRuntimeHost::Start Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8b751-102">ICLRRuntimeHost::Start Method</span></span>
<span data-ttu-id="8b751-103">Ortak dil çalışma zamanını (CLR) bir işleme başlatır.</span><span class="sxs-lookup"><span data-stu-id="8b751-103">Initializes the common language runtime (CLR) into a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b751-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="8b751-104">Syntax</span></span>  
  
```cpp  
HRESULT Start();  
```  
  
## <a name="return-value"></a><span data-ttu-id="8b751-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8b751-105">Return Value</span></span>  
  
|<span data-ttu-id="8b751-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8b751-106">HRESULT</span></span>|<span data-ttu-id="8b751-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8b751-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8b751-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="8b751-108">S_OK</span></span>|<span data-ttu-id="8b751-109">`Start`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="8b751-109">`Start` returned successfully.</span></span>|  
|<span data-ttu-id="8b751-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8b751-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8b751-111">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="8b751-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8b751-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8b751-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8b751-113">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="8b751-113">The call timed out.</span></span>|  
|<span data-ttu-id="8b751-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8b751-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8b751-115">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="8b751-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8b751-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8b751-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8b751-117">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="8b751-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8b751-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8b751-118">E_FAIL</span></span>|<span data-ttu-id="8b751-119">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="8b751-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8b751-120">Bir yöntem E_FAIL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="8b751-120">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8b751-121">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="8b751-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b751-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8b751-122">Remarks</span></span>  
 <span data-ttu-id="8b751-123">Birçok senaryoda `Start` , çalışma zamanı, yönetilen kodu çalıştırmak için ilk istek üzerine otomatik olarak başlatılacak olduğundan, bu çağrı için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="8b751-123">In many scenarios it is not necessary to call `Start`, because the runtime will initialize itself automatically upon the first request to run managed code.</span></span> <span data-ttu-id="8b751-124">Bununla birlikte, yalnızca `Start` çalışma zamanının başlatılması gerektiğinde tam olarak belirtmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b751-124">You can, however, use `Start` to specify exactly when the runtime should be initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b751-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8b751-125">Requirements</span></span>  
 <span data-ttu-id="8b751-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b751-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b751-127">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8b751-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8b751-128">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="8b751-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8b751-129">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b751-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b751-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b751-130">See also</span></span>

- <xref:System.AppDomain>
- [<span data-ttu-id="8b751-131">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8b751-131">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
