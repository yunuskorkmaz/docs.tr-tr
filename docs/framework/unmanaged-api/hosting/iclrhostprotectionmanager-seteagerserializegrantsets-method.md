---
description: ': ICLRHostProtectionManager:: SetEagerSerializeGrantSets Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 04eb00b1422523e8057c3a0fc27dfe7e49f98f08
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789924"
---
# <a name="iclrhostprotectionmanagerseteagerserializegrantsets-method"></a><span data-ttu-id="311da-103">ICLRHostProtectionManager::SetEagerSerializeGrantSets Yöntemi</span><span class="sxs-lookup"><span data-stu-id="311da-103">ICLRHostProtectionManager::SetEagerSerializeGrantSets Method</span></span>

<span data-ttu-id="311da-104">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="311da-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="311da-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="311da-105">Syntax</span></span>  
  
```cpp  
HRESULT SetEagerSerializeGrantSets ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="311da-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="311da-106">Return Value</span></span>  
  
|<span data-ttu-id="311da-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="311da-107">HRESULT</span></span>|<span data-ttu-id="311da-108">Description</span><span class="sxs-lookup"><span data-stu-id="311da-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="311da-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="311da-109">S_OK</span></span>|<span data-ttu-id="311da-110">`SetEagerSerializeGrantSets` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="311da-110">`SetEagerSerializeGrantSets` returned successfully.</span></span>|  
|<span data-ttu-id="311da-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="311da-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="311da-112">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="311da-112">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="311da-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="311da-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="311da-114">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="311da-114">The call timed out.</span></span>|  
|<span data-ttu-id="311da-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="311da-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="311da-116">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="311da-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="311da-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="311da-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="311da-118">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="311da-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="311da-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="311da-119">E_FAIL</span></span>|<span data-ttu-id="311da-120">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="311da-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="311da-121">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="311da-121">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="311da-122">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="311da-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="311da-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="311da-123">Requirements</span></span>  

 <span data-ttu-id="311da-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="311da-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="311da-125">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="311da-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="311da-126">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="311da-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="311da-127">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="311da-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="311da-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="311da-128">See also</span></span>

- [<span data-ttu-id="311da-129">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="311da-129">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="311da-130">ICLRHostProtectionManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="311da-130">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)
