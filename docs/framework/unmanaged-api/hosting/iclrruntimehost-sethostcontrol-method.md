---
description: ': ICLRRuntimeHost:: SetHostControl yöntemi hakkında daha fazla bilgi edinin'
title: ICLRRuntimeHost::SetHostControl Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.SetHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::SetHostControl
helpviewer_keywords:
- SetHostControl method [.NET Framework hosting]
- ICLRRuntimeHost::SetHostControl method [.NET Framework hosting]
ms.assetid: 6136be87-e631-4756-81ed-74b66581bad4
topic_type:
- apiref
ms.openlocfilehash: e51c61666716badc7214f9a74ad11aa646f2316c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785120"
---
# <a name="iclrruntimehostsethostcontrol-method"></a><span data-ttu-id="f7dcc-103">ICLRRuntimeHost::SetHostControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f7dcc-103">ICLRRuntimeHost::SetHostControl Method</span></span>

<span data-ttu-id="f7dcc-104">Ortak dil çalışma zamanının (CLR), ana bilgisayarın [IHostControl arabirimi](ihostcontrol-interface.md)uygulamasını almak için kullanabileceği arabirim işaretçisini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f7dcc-104">Sets the interface pointer that the common language runtime (CLR) can use to get the host's implementation of [IHostControl Interface](ihostcontrol-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7dcc-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f7dcc-105">Syntax</span></span>  
  
```cpp  
HRESULT SetHostControl(  
    [in] IHostControl* pHostControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7dcc-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f7dcc-106">Parameters</span></span>  

 `pHostControl`  
 <span data-ttu-id="f7dcc-107">'ndaki Konağın [IHostControl arabirimi](ihostcontrol-interface.md)uygulamasına yönelik bir arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="f7dcc-107">[in] An interface pointer to the host's implementation of [IHostControl Interface](ihostcontrol-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f7dcc-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f7dcc-108">Return Value</span></span>  
  
|<span data-ttu-id="f7dcc-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f7dcc-109">HRESULT</span></span>|<span data-ttu-id="f7dcc-110">Description</span><span class="sxs-lookup"><span data-stu-id="f7dcc-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f7dcc-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f7dcc-111">S_OK</span></span>|<span data-ttu-id="f7dcc-112">`SetHostControl` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="f7dcc-112">`SetHostControl` returned successfully.</span></span>|  
|<span data-ttu-id="f7dcc-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f7dcc-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f7dcc-114">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="f7dcc-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f7dcc-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f7dcc-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f7dcc-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="f7dcc-116">The call timed out.</span></span>|  
|<span data-ttu-id="f7dcc-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f7dcc-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f7dcc-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="f7dcc-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f7dcc-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f7dcc-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f7dcc-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="f7dcc-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f7dcc-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f7dcc-121">E_FAIL</span></span>|<span data-ttu-id="f7dcc-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="f7dcc-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f7dcc-123">Bir yöntem E_FAIL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f7dcc-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f7dcc-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="f7dcc-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f7dcc-125">E_CLR_ALREADY_STARTED</span><span class="sxs-lookup"><span data-stu-id="f7dcc-125">E_CLR_ALREADY_STARTED</span></span>|<span data-ttu-id="f7dcc-126">CLR zaten başlatılmış.</span><span class="sxs-lookup"><span data-stu-id="f7dcc-126">The CLR has already been initialized.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7dcc-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f7dcc-127">Remarks</span></span>  

 <span data-ttu-id="f7dcc-128">`SetHostControl`Clr başlatılmadan önce, diğer bir deyişle, [başlangıç yöntemini](iclrruntimehost-start-method.md) çağırmadan veya [meta veri arabirimlerinden](../metadata/metadata-interfaces.md)herhangi birini kullanmadan önce ' i çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f7dcc-128">You must call `SetHostControl` before the CLR is initialized, that is, before you call [Start Method](iclrruntimehost-start-method.md) or use any of the [Metadata Interfaces](../metadata/metadata-interfaces.md).</span></span> <span data-ttu-id="f7dcc-129">`SetHostControl` [CorBindToCurrentRuntime Işlevini](corbindtocurrentruntime-function.md) veya [CorBindToRuntimeEx işlevini](corbindtoruntimeex-function.md)çağırdıktan hemen sonra çağırmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="f7dcc-129">It is recommended that you call `SetHostControl` immediately after calling [CorBindToCurrentRuntime Function](corbindtocurrentruntime-function.md) or [CorBindToRuntimeEx Function](corbindtoruntimeex-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7dcc-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f7dcc-130">Requirements</span></span>  

 <span data-ttu-id="f7dcc-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7dcc-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7dcc-132">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f7dcc-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f7dcc-133">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="f7dcc-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f7dcc-134">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7dcc-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7dcc-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7dcc-135">See also</span></span>

- [<span data-ttu-id="f7dcc-136">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f7dcc-136">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
- [<span data-ttu-id="f7dcc-137">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f7dcc-137">IHostControl Interface</span></span>](ihostcontrol-interface.md)
