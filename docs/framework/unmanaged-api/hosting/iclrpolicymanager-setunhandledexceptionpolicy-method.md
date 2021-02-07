---
description: ': ICLRPolicyManager:: SetUnhandledExceptionPolicy yöntemi hakkında daha fazla bilgi edinin'
title: ICLRPolicyManager::SetUnhandledExceptionPolicy Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetUnhandledExceptionPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetUnhandledExceptionPolicy
helpviewer_keywords:
- ICLRPolicyManager::SetUnhandledExceptionPolicy method [.NET Framework hosting]
- SetUnhandledExceptionPolicy method [.NET Framework hosting]
ms.assetid: 5268480e-280a-4931-b7a3-dc3ffdf7f78f
topic_type:
- apiref
ms.openlocfilehash: 489127bb00b2b65466460baa3cfd31439672cd1c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716555"
---
# <a name="iclrpolicymanagersetunhandledexceptionpolicy-method"></a><span data-ttu-id="4b2e3-103">ICLRPolicyManager::SetUnhandledExceptionPolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4b2e3-103">ICLRPolicyManager::SetUnhandledExceptionPolicy Method</span></span>

<span data-ttu-id="4b2e3-104">İşlenmeyen bir özel durum oluştuğunda ortak dil çalışma zamanının (CLR) davranışını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4b2e3-104">Specifies the behavior of the common language runtime (CLR) when an unhandled exception occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b2e3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4b2e3-105">Syntax</span></span>  
  
```cpp  
HRESULT SetUnhandledExceptionPolicy (  
    [in] EClrUnhandledExceptionPolicy policy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b2e3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4b2e3-106">Parameters</span></span>  

 `policy`  
 <span data-ttu-id="4b2e3-107">'ndaki Davranışın CLR veya konak tarafından ayarlanmış olup olmadığını gösteren [EClrUnhandledException](eclrunhandledexception-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="4b2e3-107">[in] One of the [EClrUnhandledException](eclrunhandledexception-enumeration.md) values, indicating whether the behavior is set by the CLR or the host.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4b2e3-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4b2e3-108">Return Value</span></span>  
  
|<span data-ttu-id="4b2e3-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4b2e3-109">HRESULT</span></span>|<span data-ttu-id="4b2e3-110">Description</span><span class="sxs-lookup"><span data-stu-id="4b2e3-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4b2e3-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="4b2e3-111">S_OK</span></span>|<span data-ttu-id="4b2e3-112">`SetUnhandledExceptionPolicy` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="4b2e3-112">`SetUnhandledExceptionPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="4b2e3-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4b2e3-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4b2e3-114">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="4b2e3-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4b2e3-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4b2e3-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4b2e3-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="4b2e3-116">The call timed out.</span></span>|  
|<span data-ttu-id="4b2e3-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4b2e3-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4b2e3-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="4b2e3-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4b2e3-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4b2e3-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4b2e3-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="4b2e3-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4b2e3-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4b2e3-121">E_FAIL</span></span>|<span data-ttu-id="4b2e3-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="4b2e3-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4b2e3-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="4b2e3-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4b2e3-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="4b2e3-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b2e3-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4b2e3-125">Remarks</span></span>  

 <span data-ttu-id="4b2e3-126">Varsayılan olarak, CLR işlenmeyen tüm özel durumlar için son işleyicidir ve varsayılan davranışı işlemi yavaşlatmak olur.</span><span class="sxs-lookup"><span data-stu-id="4b2e3-126">By default, the CLR is the final handler for all unhandled exceptions, and its default behavior is to tear down the process.</span></span> <span data-ttu-id="4b2e3-127">Konak, `policy` değeri eHostDeterminedPolicy olarak ayarlayarak bu davranışı değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="4b2e3-127">The host can change this behavior by setting the `policy` value to eHostDeterminedPolicy.</span></span> <span data-ttu-id="4b2e3-128">Bu değer, konağın, CLR 'nin önceki sürümlerinde olduğu gibi kendi varsayılan davranışını uygulamasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="4b2e3-128">This value allows the host to implement its own default behavior, as with earlier versions of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b2e3-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4b2e3-129">Requirements</span></span>  

 <span data-ttu-id="4b2e3-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b2e3-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b2e3-131">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4b2e3-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4b2e3-132">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="4b2e3-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4b2e3-133">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b2e3-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b2e3-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4b2e3-134">See also</span></span>

- [<span data-ttu-id="4b2e3-135">EClrUnhandledException Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="4b2e3-135">EClrUnhandledException Enumeration</span></span>](eclrunhandledexception-enumeration.md)
- [<span data-ttu-id="4b2e3-136">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4b2e3-136">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="4b2e3-137">ICLRPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4b2e3-137">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="4b2e3-138">IHostPolicyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4b2e3-138">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
