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
ms.openlocfilehash: d388f366671f50c3dcb3bd9d387300dd1bbb168f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615910"
---
# <a name="iclrassemblyidentitymanagerisstronglynamed-method"></a><span data-ttu-id="3ef54-102">ICLRAssemblyIdentityManager::IsStronglyNamed Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3ef54-102">ICLRAssemblyIdentityManager::IsStronglyNamed Method</span></span>
<span data-ttu-id="3ef54-103">Belirtilen derlemenin kesin olarak adlandırılmış olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="3ef54-103">Gets a value that indicates whether the specified assembly is strongly named.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ef54-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="3ef54-104">Syntax</span></span>  
  
```cpp  
RESULT IsStronglyNamed (  
    [in]  LPCWSTR  pwzAssemblyIdentity,  
    [out] BOOL    *pbIsStronglyNamed  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3ef54-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3ef54-105">Parameters</span></span>  
 `pwzAssemblyIdentity`  
 <span data-ttu-id="3ef54-106">'ndaki Değerlendirilecek derlemenin donuk kurallı derleme kimlik verileri.</span><span class="sxs-lookup"><span data-stu-id="3ef54-106">[in] The opaque canonical assembly identity data of the assembly to be evaluated.</span></span>  
  
 `pbIsStronglyNamed`  
 <span data-ttu-id="3ef54-107">[out] `true` parametre tarafından başvurulan derleme `pwzAssemblyIdentity` kesin olarak adlandırılmışsa, tersi durumda `false` .</span><span class="sxs-lookup"><span data-stu-id="3ef54-107">[out] `true`, if the assembly referenced by the `pwzAssemblyIdentity` parameter is strongly named; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3ef54-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3ef54-108">Return Value</span></span>  
  
|<span data-ttu-id="3ef54-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3ef54-109">HRESULT</span></span>|<span data-ttu-id="3ef54-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3ef54-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3ef54-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="3ef54-111">S_OK</span></span>|<span data-ttu-id="3ef54-112">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="3ef54-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="3ef54-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3ef54-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3ef54-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="3ef54-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3ef54-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3ef54-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3ef54-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="3ef54-116">The call timed out.</span></span>|  
|<span data-ttu-id="3ef54-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3ef54-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3ef54-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="3ef54-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3ef54-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3ef54-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3ef54-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="3ef54-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3ef54-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3ef54-121">E_FAIL</span></span>|<span data-ttu-id="3ef54-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="3ef54-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3ef54-123">Bir yöntem E_FAIL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="3ef54-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3ef54-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="3ef54-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3ef54-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3ef54-125">Requirements</span></span>  
 <span data-ttu-id="3ef54-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ef54-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ef54-127">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3ef54-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3ef54-128">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="3ef54-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3ef54-129">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ef54-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ef54-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3ef54-130">See also</span></span>

- [<span data-ttu-id="3ef54-131">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3ef54-131">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
