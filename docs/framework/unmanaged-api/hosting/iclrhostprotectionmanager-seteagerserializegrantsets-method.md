---
title: ICLRHostProtectionManager::SetEagerSerializeGrantSets Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRHostProtectionManager.SetEagerSerializeGrantSets
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostProtectionManager::SetEagerSerializeGrantSets
helpviewer_keywords:
- SetEagerSerializeGrantSets method [.NET Framework hosting]
- ICLRHostProtectionManager::SetEagerSerializeGrantSets method [.NET Framework hosting]
ms.assetid: d6158360-22b1-4ace-ad85-d830b9964783
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 160e31859e3d58812861d4462e77d68fa18d6186
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61944683"
---
# <a name="iclrhostprotectionmanagerseteagerserializegrantsets-method"></a><span data-ttu-id="60db9-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets Yöntemi</span><span class="sxs-lookup"><span data-stu-id="60db9-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets Method</span></span>
<span data-ttu-id="60db9-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="60db9-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60db9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="60db9-104">Syntax</span></span>  
  
```  
HRESULT SetEagerSerializeGrantSets ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="60db9-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="60db9-105">Return Value</span></span>  
  
|<span data-ttu-id="60db9-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="60db9-106">HRESULT</span></span>|<span data-ttu-id="60db9-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="60db9-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="60db9-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="60db9-108">S_OK</span></span>|<span data-ttu-id="60db9-109">`SetEagerSerializeGrantSets` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="60db9-109">`SetEagerSerializeGrantSets` returned successfully.</span></span>|  
|<span data-ttu-id="60db9-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="60db9-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="60db9-111">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="60db9-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="60db9-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="60db9-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="60db9-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="60db9-113">The call timed out.</span></span>|  
|<span data-ttu-id="60db9-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="60db9-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="60db9-115">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="60db9-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="60db9-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="60db9-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="60db9-117">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="60db9-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="60db9-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="60db9-118">E_FAIL</span></span>|<span data-ttu-id="60db9-119">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="60db9-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="60db9-120">CLR, artık E_FAIL bir yöntemin dönüşünün ardından, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="60db9-120">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="60db9-121">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="60db9-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="60db9-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="60db9-122">Requirements</span></span>  
 <span data-ttu-id="60db9-123">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60db9-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60db9-124">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="60db9-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="60db9-125">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="60db9-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="60db9-126">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60db9-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60db9-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="60db9-127">See also</span></span>

- [<span data-ttu-id="60db9-128">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="60db9-128">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="60db9-129">ICLRHostProtectionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="60db9-129">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
