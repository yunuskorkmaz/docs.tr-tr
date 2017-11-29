---
title: "ICLRHostProtectionManager::SetEagerSerializeGrantSets Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRHostProtectionManager.SetEagerSerializeGrantSets
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRHostProtectionManager::SetEagerSerializeGrantSets
helpviewer_keywords:
- SetEagerSerializeGrantSets method [.NET Framework hosting]
- ICLRHostProtectionManager::SetEagerSerializeGrantSets method [.NET Framework hosting]
ms.assetid: d6158360-22b1-4ace-ad85-d830b9964783
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a9b1e314f7af6edf3d8db00780105dff95868a6c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrhostprotectionmanagerseteagerserializegrantsets-method"></a><span data-ttu-id="cd6f3-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cd6f3-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets Method</span></span>
<span data-ttu-id="cd6f3-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="cd6f3-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd6f3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cd6f3-104">Syntax</span></span>  
  
```  
HRESULT SetEagerSerializeGrantSets ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="cd6f3-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cd6f3-105">Return Value</span></span>  
  
|<span data-ttu-id="cd6f3-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cd6f3-106">HRESULT</span></span>|<span data-ttu-id="cd6f3-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cd6f3-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cd6f3-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="cd6f3-108">S_OK</span></span>|<span data-ttu-id="cd6f3-109">`SetEagerSerializeGrantSets`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="cd6f3-109">`SetEagerSerializeGrantSets` returned successfully.</span></span>|  
|<span data-ttu-id="cd6f3-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cd6f3-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cd6f3-111">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="cd6f3-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cd6f3-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cd6f3-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cd6f3-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="cd6f3-113">The call timed out.</span></span>|  
|<span data-ttu-id="cd6f3-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cd6f3-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cd6f3-115">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="cd6f3-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cd6f3-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cd6f3-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cd6f3-117">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="cd6f3-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cd6f3-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cd6f3-118">E_FAIL</span></span>|<span data-ttu-id="cd6f3-119">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="cd6f3-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cd6f3-120">CLR, artık bir yöntem E_FAIL döndükten sonra işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="cd6f3-120">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cd6f3-121">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="cd6f3-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cd6f3-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cd6f3-122">Requirements</span></span>  
 <span data-ttu-id="cd6f3-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd6f3-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd6f3-124">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cd6f3-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cd6f3-125">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="cd6f3-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cd6f3-126">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd6f3-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd6f3-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cd6f3-127">See Also</span></span>  
 [<span data-ttu-id="cd6f3-128">Iclrcontrol arabirimi</span><span class="sxs-lookup"><span data-stu-id="cd6f3-128">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="cd6f3-129">Iclrhostprotectionmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="cd6f3-129">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
