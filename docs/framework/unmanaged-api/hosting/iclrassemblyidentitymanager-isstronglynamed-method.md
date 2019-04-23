---
title: ICLRAssemblyIdentityManager::IsStronglyNamed Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.IsStronglyNamed
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::IsStronglyNamed
helpviewer_keywords:
- IsStronglyNamed method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::IsStronglyNamed method [.NET Framework hosting]
ms.assetid: 954bd386-2076-4d00-9d46-38c728aa9cab
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 166583f690fc7ed80f80cf2cf5cd5b0348708cc3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59159724"
---
# <a name="iclrassemblyidentitymanagerisstronglynamed-method"></a><span data-ttu-id="ae167-102">ICLRAssemblyIdentityManager::IsStronglyNamed Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ae167-102">ICLRAssemblyIdentityManager::IsStronglyNamed Method</span></span>
<span data-ttu-id="ae167-103">Belirtilen derleme kesin şekilde adlandırıldığında olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="ae167-103">Gets a value that indicates whether the specified assembly is strongly named.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae167-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ae167-104">Syntax</span></span>  
  
```  
RESULT IsStronglyNamed (  
    [in]  LPCWSTR  pwzAssemblyIdentity,  
    [out] BOOL    *pbIsStronglyNamed  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae167-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ae167-105">Parameters</span></span>  
 `pwzAssemblyIdentity`  
 <span data-ttu-id="ae167-106">[in] Donuk kurallı derleme kimlik verilerini derlemenin değerlendirilecek.</span><span class="sxs-lookup"><span data-stu-id="ae167-106">[in] The opaque canonical assembly identity data of the assembly to be evaluated.</span></span>  
  
 `pbIsStronglyNamed`  
 <span data-ttu-id="ae167-107">[out] `true`, derlemenin başvurduğu `pwzAssemblyIdentity` parametredir kesin adlandırılmış; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="ae167-107">[out] `true`, if the assembly referenced by the `pwzAssemblyIdentity` parameter is strongly named; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ae167-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ae167-108">Return Value</span></span>  
  
|<span data-ttu-id="ae167-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ae167-109">HRESULT</span></span>|<span data-ttu-id="ae167-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ae167-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ae167-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ae167-111">S_OK</span></span>|<span data-ttu-id="ae167-112">Yöntemi başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="ae167-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="ae167-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ae167-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ae167-114">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="ae167-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ae167-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ae167-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ae167-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="ae167-116">The call timed out.</span></span>|  
|<span data-ttu-id="ae167-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ae167-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ae167-118">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="ae167-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ae167-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ae167-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ae167-120">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="ae167-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ae167-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ae167-121">E_FAIL</span></span>|<span data-ttu-id="ae167-122">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="ae167-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ae167-123">CLR, artık bir yöntem E_FAIL döndürürse, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ae167-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ae167-124">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="ae167-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ae167-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ae167-125">Requirements</span></span>  
 <span data-ttu-id="ae167-126">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae167-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae167-127">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ae167-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ae167-128">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="ae167-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ae167-129">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae167-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae167-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae167-130">See also</span></span>

- [<span data-ttu-id="ae167-131">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ae167-131">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
