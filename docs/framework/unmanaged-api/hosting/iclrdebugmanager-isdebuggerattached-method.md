---
description: ': ICLRDebugManager:: ısdebuggerekli yöntemi hakkında daha fazla bilgi edinin'
title: ICLRDebugManager::IsDebuggerAttached Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.IsDebuggerAttached
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::IsDebuggerAttached
helpviewer_keywords:
- IsDebuggerAttached method, ICLRDebugManager interface [.NET Framework hosting]
- ICLRDebugManager::IsDebuggerAttached method [.NET Framework hosting]
ms.assetid: 2f105fe0-f52d-49c5-bda5-583fb27e3aa6
topic_type:
- apiref
ms.openlocfilehash: 74305989797bcb553feb727a133e24bd308ac715
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772139"
---
# <a name="iclrdebugmanagerisdebuggerattached-method"></a><span data-ttu-id="cbc98-103">ICLRDebugManager::IsDebuggerAttached Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cbc98-103">ICLRDebugManager::IsDebuggerAttached Method</span></span>

<span data-ttu-id="cbc98-104">Bir hata ayıklayıcının işleme bağlı olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="cbc98-104">Gets a value that indicates whether a debugger is attached to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbc98-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cbc98-105">Syntax</span></span>  
  
```cpp  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cbc98-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cbc98-106">Parameters</span></span>  

 `pbAttached`  
 <span data-ttu-id="cbc98-107">[out] `true` bir hata ayıklayıcısı işleme eklenmişse; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="cbc98-107">[out] `true` if a debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cbc98-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cbc98-108">Return Value</span></span>  
  
|<span data-ttu-id="cbc98-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cbc98-109">HRESULT</span></span>|<span data-ttu-id="cbc98-110">Description</span><span class="sxs-lookup"><span data-stu-id="cbc98-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cbc98-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="cbc98-111">S_OK</span></span>|<span data-ttu-id="cbc98-112">`IsDebuggerAttached` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="cbc98-112">`IsDebuggerAttached` returned successfully.</span></span>|  
|<span data-ttu-id="cbc98-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cbc98-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cbc98-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="cbc98-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cbc98-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cbc98-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cbc98-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="cbc98-116">The call timed out.</span></span>|  
|<span data-ttu-id="cbc98-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cbc98-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cbc98-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="cbc98-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cbc98-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cbc98-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cbc98-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="cbc98-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cbc98-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cbc98-121">E_FAIL</span></span>|<span data-ttu-id="cbc98-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="cbc98-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cbc98-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="cbc98-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cbc98-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="cbc98-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cbc98-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cbc98-125">Remarks</span></span>  

 <span data-ttu-id="cbc98-126">`IsDebuggerAttached` bir hata ayıklayıcının işleme eklenip eklenmeyeceğini anlamak için konağın CLR 'yi sorgulamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="cbc98-126">`IsDebuggerAttached` allows the host to query the CLR to determine whether a debugger is attached to the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbc98-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cbc98-127">Requirements</span></span>  

 <span data-ttu-id="cbc98-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbc98-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbc98-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cbc98-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cbc98-130">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="cbc98-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cbc98-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbc98-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbc98-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cbc98-132">See also</span></span>

- [<span data-ttu-id="cbc98-133">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cbc98-133">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="cbc98-134">ICLRDebugManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cbc98-134">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="cbc98-135">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cbc98-135">IHostControl Interface</span></span>](ihostcontrol-interface.md)
