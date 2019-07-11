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
ms.openlocfilehash: f9d201c3753a8e71ea3da0b0f4f8a3a47e5bcee2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773378"
---
# <a name="iclrassemblyidentitymanagerisstronglynamed-method"></a><span data-ttu-id="96c75-102">ICLRAssemblyIdentityManager::IsStronglyNamed Yöntemi</span><span class="sxs-lookup"><span data-stu-id="96c75-102">ICLRAssemblyIdentityManager::IsStronglyNamed Method</span></span>
<span data-ttu-id="96c75-103">Belirtilen derleme kesin şekilde adlandırıldığında olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="96c75-103">Gets a value that indicates whether the specified assembly is strongly named.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96c75-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="96c75-104">Syntax</span></span>  
  
```cpp  
RESULT IsStronglyNamed (  
    [in]  LPCWSTR  pwzAssemblyIdentity,  
    [out] BOOL    *pbIsStronglyNamed  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96c75-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="96c75-105">Parameters</span></span>  
 `pwzAssemblyIdentity`  
 <span data-ttu-id="96c75-106">[in] Donuk kurallı derleme kimlik verilerini derlemenin değerlendirilecek.</span><span class="sxs-lookup"><span data-stu-id="96c75-106">[in] The opaque canonical assembly identity data of the assembly to be evaluated.</span></span>  
  
 `pbIsStronglyNamed`  
 <span data-ttu-id="96c75-107">[out] `true`, derlemenin başvurduğu `pwzAssemblyIdentity` parametredir kesin adlandırılmış; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="96c75-107">[out] `true`, if the assembly referenced by the `pwzAssemblyIdentity` parameter is strongly named; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="96c75-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="96c75-108">Return Value</span></span>  
  
|<span data-ttu-id="96c75-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="96c75-109">HRESULT</span></span>|<span data-ttu-id="96c75-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="96c75-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="96c75-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="96c75-111">S_OK</span></span>|<span data-ttu-id="96c75-112">Yöntemi başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="96c75-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="96c75-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="96c75-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="96c75-114">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="96c75-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="96c75-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="96c75-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="96c75-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="96c75-116">The call timed out.</span></span>|  
|<span data-ttu-id="96c75-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="96c75-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="96c75-118">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="96c75-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="96c75-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="96c75-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="96c75-120">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="96c75-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="96c75-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="96c75-121">E_FAIL</span></span>|<span data-ttu-id="96c75-122">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="96c75-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="96c75-123">CLR, artık bir yöntem E_FAIL döndürürse, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="96c75-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="96c75-124">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="96c75-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="96c75-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="96c75-125">Requirements</span></span>  
 <span data-ttu-id="96c75-126">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96c75-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96c75-127">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="96c75-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="96c75-128">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="96c75-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="96c75-129">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96c75-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96c75-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96c75-130">See also</span></span>

- [<span data-ttu-id="96c75-131">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="96c75-131">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
