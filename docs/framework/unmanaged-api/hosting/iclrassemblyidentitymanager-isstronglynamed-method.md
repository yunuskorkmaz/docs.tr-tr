---
title: "ICLRAssemblyIdentityManager::IsStronglyNamed Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyIdentityManager.IsStronglyNamed
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyIdentityManager::IsStronglyNamed
helpviewer_keywords:
- IsStronglyNamed method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::IsStronglyNamed method [.NET Framework hosting]
ms.assetid: 954bd386-2076-4d00-9d46-38c728aa9cab
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1cb727d9144fc3364a04cd5b9064527c55f5ee79
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrassemblyidentitymanagerisstronglynamed-method"></a><span data-ttu-id="dfdaf-102">ICLRAssemblyIdentityManager::IsStronglyNamed Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dfdaf-102">ICLRAssemblyIdentityManager::IsStronglyNamed Method</span></span>
<span data-ttu-id="dfdaf-103">Belirtilen derleme güçlü olarak adlandırılmamış olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="dfdaf-103">Gets a value that indicates whether the specified assembly is strongly named.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfdaf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dfdaf-104">Syntax</span></span>  
  
```  
RESULT IsStronglyNamed (  
    [in]  LPCWSTR  pwzAssemblyIdentity,  
    [out] BOOL    *pbIsStronglyNamed  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dfdaf-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dfdaf-105">Parameters</span></span>  
 `pwzAssemblyIdentity`  
 <span data-ttu-id="dfdaf-106">[in] Değerlendirilecek derleme donuk kurallı derleme kimlik verileri.</span><span class="sxs-lookup"><span data-stu-id="dfdaf-106">[in] The opaque canonical assembly identity data of the assembly to be evaluated.</span></span>  
  
 `pbIsStronglyNamed`  
 <span data-ttu-id="dfdaf-107">[out] `true`derlemesi tarafından başvurulan, `pwzAssemblyIdentity` parametresi, kesin adlandırılmış Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="dfdaf-107">[out] `true`, if the assembly referenced by the `pwzAssemblyIdentity` parameter is strongly named; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dfdaf-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="dfdaf-108">Return Value</span></span>  
  
|<span data-ttu-id="dfdaf-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dfdaf-109">HRESULT</span></span>|<span data-ttu-id="dfdaf-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dfdaf-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dfdaf-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="dfdaf-111">S_OK</span></span>|<span data-ttu-id="dfdaf-112">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="dfdaf-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="dfdaf-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dfdaf-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dfdaf-114">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="dfdaf-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dfdaf-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dfdaf-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dfdaf-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="dfdaf-116">The call timed out.</span></span>|  
|<span data-ttu-id="dfdaf-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dfdaf-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dfdaf-118">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="dfdaf-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dfdaf-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dfdaf-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dfdaf-120">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="dfdaf-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dfdaf-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dfdaf-121">E_FAIL</span></span>|<span data-ttu-id="dfdaf-122">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="dfdaf-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dfdaf-123">Bir yöntem E_FAIL döndürürse, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="dfdaf-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dfdaf-124">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="dfdaf-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dfdaf-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dfdaf-125">Requirements</span></span>  
 <span data-ttu-id="dfdaf-126">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dfdaf-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfdaf-127">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dfdaf-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dfdaf-128">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="dfdaf-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dfdaf-129">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfdaf-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfdaf-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dfdaf-130">See Also</span></span>  
 [<span data-ttu-id="dfdaf-131">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dfdaf-131">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
