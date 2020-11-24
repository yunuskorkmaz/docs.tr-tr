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
ms.openlocfilehash: 9ac3b2ae349a696ba0cea1bad3e3484bb1c113fa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679253"
---
# <a name="iclrassemblyidentitymanagerisstronglynamed-method"></a><span data-ttu-id="043b7-102">ICLRAssemblyIdentityManager::IsStronglyNamed Yöntemi</span><span class="sxs-lookup"><span data-stu-id="043b7-102">ICLRAssemblyIdentityManager::IsStronglyNamed Method</span></span>

<span data-ttu-id="043b7-103">Belirtilen derlemenin kesin olarak adlandırılmış olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="043b7-103">Gets a value that indicates whether the specified assembly is strongly named.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="043b7-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="043b7-104">Syntax</span></span>  
  
```cpp  
RESULT IsStronglyNamed (  
    [in]  LPCWSTR  pwzAssemblyIdentity,  
    [out] BOOL    *pbIsStronglyNamed  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="043b7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="043b7-105">Parameters</span></span>  

 `pwzAssemblyIdentity`  
 <span data-ttu-id="043b7-106">'ndaki Değerlendirilecek derlemenin donuk kurallı derleme kimlik verileri.</span><span class="sxs-lookup"><span data-stu-id="043b7-106">[in] The opaque canonical assembly identity data of the assembly to be evaluated.</span></span>  
  
 `pbIsStronglyNamed`  
 <span data-ttu-id="043b7-107">[out] `true` parametre tarafından başvurulan derleme `pwzAssemblyIdentity` kesin olarak adlandırılmışsa, tersi durumda `false` .</span><span class="sxs-lookup"><span data-stu-id="043b7-107">[out] `true`, if the assembly referenced by the `pwzAssemblyIdentity` parameter is strongly named; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="043b7-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="043b7-108">Return Value</span></span>  
  
|<span data-ttu-id="043b7-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="043b7-109">HRESULT</span></span>|<span data-ttu-id="043b7-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="043b7-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="043b7-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="043b7-111">S_OK</span></span>|<span data-ttu-id="043b7-112">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="043b7-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="043b7-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="043b7-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="043b7-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="043b7-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="043b7-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="043b7-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="043b7-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="043b7-116">The call timed out.</span></span>|  
|<span data-ttu-id="043b7-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="043b7-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="043b7-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="043b7-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="043b7-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="043b7-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="043b7-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="043b7-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="043b7-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="043b7-121">E_FAIL</span></span>|<span data-ttu-id="043b7-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="043b7-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="043b7-123">Bir yöntem E_FAIL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="043b7-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="043b7-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="043b7-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="043b7-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="043b7-125">Requirements</span></span>  

 <span data-ttu-id="043b7-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="043b7-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="043b7-127">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="043b7-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="043b7-128">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="043b7-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="043b7-129">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="043b7-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="043b7-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="043b7-130">See also</span></span>

- [<span data-ttu-id="043b7-131">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="043b7-131">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
