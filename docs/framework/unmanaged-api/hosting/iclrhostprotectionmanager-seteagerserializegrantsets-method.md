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
ms.openlocfilehash: f14368956ee2ffd3ae875710e1e73e2bdbee8dd7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779659"
---
# <a name="iclrhostprotectionmanagerseteagerserializegrantsets-method"></a><span data-ttu-id="c7b67-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c7b67-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets Method</span></span>
<span data-ttu-id="c7b67-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="c7b67-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7b67-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c7b67-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEagerSerializeGrantSets ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="c7b67-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c7b67-105">Return Value</span></span>  
  
|<span data-ttu-id="c7b67-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c7b67-106">HRESULT</span></span>|<span data-ttu-id="c7b67-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c7b67-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c7b67-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="c7b67-108">S_OK</span></span>|<span data-ttu-id="c7b67-109">`SetEagerSerializeGrantSets` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="c7b67-109">`SetEagerSerializeGrantSets` returned successfully.</span></span>|  
|<span data-ttu-id="c7b67-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c7b67-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c7b67-111">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="c7b67-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c7b67-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c7b67-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c7b67-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="c7b67-113">The call timed out.</span></span>|  
|<span data-ttu-id="c7b67-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c7b67-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c7b67-115">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="c7b67-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c7b67-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c7b67-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c7b67-117">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="c7b67-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c7b67-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c7b67-118">E_FAIL</span></span>|<span data-ttu-id="c7b67-119">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="c7b67-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c7b67-120">CLR, artık E_FAIL bir yöntemin dönüşünün ardından, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c7b67-120">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c7b67-121">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="c7b67-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c7b67-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c7b67-122">Requirements</span></span>  
 <span data-ttu-id="c7b67-123">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7b67-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7b67-124">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c7b67-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c7b67-125">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="c7b67-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c7b67-126">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7b67-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7b67-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7b67-127">See also</span></span>

- [<span data-ttu-id="c7b67-128">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c7b67-128">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="c7b67-129">ICLRHostProtectionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c7b67-129">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
