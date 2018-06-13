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
ms.openlocfilehash: e9bddaa25ba83570389a9d70ac1a9f60357f533c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432228"
---
# <a name="iclrhostprotectionmanagerseteagerserializegrantsets-method"></a><span data-ttu-id="e39a6-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e39a6-102">ICLRHostProtectionManager::SetEagerSerializeGrantSets Method</span></span>
<span data-ttu-id="e39a6-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="e39a6-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e39a6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e39a6-104">Syntax</span></span>  
  
```  
HRESULT SetEagerSerializeGrantSets ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="e39a6-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e39a6-105">Return Value</span></span>  
  
|<span data-ttu-id="e39a6-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e39a6-106">HRESULT</span></span>|<span data-ttu-id="e39a6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e39a6-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e39a6-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="e39a6-108">S_OK</span></span>|<span data-ttu-id="e39a6-109">`SetEagerSerializeGrantSets` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e39a6-109">`SetEagerSerializeGrantSets` returned successfully.</span></span>|  
|<span data-ttu-id="e39a6-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e39a6-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e39a6-111">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="e39a6-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e39a6-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e39a6-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e39a6-113">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="e39a6-113">The call timed out.</span></span>|  
|<span data-ttu-id="e39a6-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e39a6-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e39a6-115">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="e39a6-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e39a6-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e39a6-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e39a6-117">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="e39a6-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e39a6-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e39a6-118">E_FAIL</span></span>|<span data-ttu-id="e39a6-119">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e39a6-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e39a6-120">CLR, artık bir yöntem E_FAIL döndükten sonra işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e39a6-120">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e39a6-121">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="e39a6-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e39a6-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e39a6-122">Requirements</span></span>  
 <span data-ttu-id="e39a6-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e39a6-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e39a6-124">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e39a6-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e39a6-125">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e39a6-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e39a6-126">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e39a6-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e39a6-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e39a6-127">See Also</span></span>  
 [<span data-ttu-id="e39a6-128">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e39a6-128">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="e39a6-129">ICLRHostProtectionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e39a6-129">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
