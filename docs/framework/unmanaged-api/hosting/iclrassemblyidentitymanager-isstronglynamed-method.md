---
description: ': ICLRAssemblyIdentityManager:: IsStronglyNamed yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: f6f1715513fba56e10b10c14c298d3c553fd4652
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716854"
---
# <a name="iclrassemblyidentitymanagerisstronglynamed-method"></a><span data-ttu-id="a46e6-103">ICLRAssemblyIdentityManager::IsStronglyNamed Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a46e6-103">ICLRAssemblyIdentityManager::IsStronglyNamed Method</span></span>

<span data-ttu-id="a46e6-104">Belirtilen derlemenin kesin olarak adlandırılmış olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="a46e6-104">Gets a value that indicates whether the specified assembly is strongly named.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a46e6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a46e6-105">Syntax</span></span>  
  
```cpp  
RESULT IsStronglyNamed (  
    [in]  LPCWSTR  pwzAssemblyIdentity,  
    [out] BOOL    *pbIsStronglyNamed  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a46e6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a46e6-106">Parameters</span></span>  

 `pwzAssemblyIdentity`  
 <span data-ttu-id="a46e6-107">'ndaki Değerlendirilecek derlemenin donuk kurallı derleme kimlik verileri.</span><span class="sxs-lookup"><span data-stu-id="a46e6-107">[in] The opaque canonical assembly identity data of the assembly to be evaluated.</span></span>  
  
 `pbIsStronglyNamed`  
 <span data-ttu-id="a46e6-108">[out] `true` parametre tarafından başvurulan derleme `pwzAssemblyIdentity` kesin olarak adlandırılmışsa, tersi durumda `false` .</span><span class="sxs-lookup"><span data-stu-id="a46e6-108">[out] `true`, if the assembly referenced by the `pwzAssemblyIdentity` parameter is strongly named; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a46e6-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a46e6-109">Return Value</span></span>  
  
|<span data-ttu-id="a46e6-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a46e6-110">HRESULT</span></span>|<span data-ttu-id="a46e6-111">Description</span><span class="sxs-lookup"><span data-stu-id="a46e6-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a46e6-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="a46e6-112">S_OK</span></span>|<span data-ttu-id="a46e6-113">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="a46e6-113">The method returned successfully.</span></span>|  
|<span data-ttu-id="a46e6-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a46e6-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a46e6-115">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="a46e6-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a46e6-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a46e6-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a46e6-117">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="a46e6-117">The call timed out.</span></span>|  
|<span data-ttu-id="a46e6-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a46e6-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a46e6-119">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="a46e6-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a46e6-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a46e6-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a46e6-121">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="a46e6-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a46e6-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a46e6-122">E_FAIL</span></span>|<span data-ttu-id="a46e6-123">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="a46e6-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a46e6-124">Bir yöntem E_FAIL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a46e6-124">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a46e6-125">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="a46e6-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a46e6-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a46e6-126">Requirements</span></span>  

 <span data-ttu-id="a46e6-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a46e6-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a46e6-128">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a46e6-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a46e6-129">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="a46e6-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a46e6-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a46e6-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a46e6-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a46e6-131">See also</span></span>

- [<span data-ttu-id="a46e6-132">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a46e6-132">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
