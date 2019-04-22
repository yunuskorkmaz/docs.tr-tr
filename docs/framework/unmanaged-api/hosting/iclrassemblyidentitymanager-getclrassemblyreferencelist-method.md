---
title: ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList Metodu
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetCLRAssemblyReferenceList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList
helpviewer_keywords:
- GetClrAssemblyReferenceList method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList method [.NET Framework hosting]
ms.assetid: cb5ffae5-287b-4a87-9ca8-7ce3ae0601b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: de166a22350e49197ff6a5b5d6dc956cdcc2d1ac
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59089516"
---
# <a name="iclrassemblyidentitymanagergetclrassemblyreferencelist-method"></a><span data-ttu-id="3bca9-102">ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList Metodu</span><span class="sxs-lookup"><span data-stu-id="3bca9-102">ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList Method</span></span>
<span data-ttu-id="3bca9-103">Bir arabirim işaretçisi alır bir [Iclrassemblyreferencelist](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) kısmi derleme kimlikleri sağlanan listeden örneği.</span><span class="sxs-lookup"><span data-stu-id="3bca9-103">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bca9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3bca9-104">Syntax</span></span>  
  
```  
HRESULT  GetCLRAssemblyReferenceList (  
    [in] LPCWSTR *ppwzAssemblyReferences,  
    [in] DWORD    dwNumOfReferences,  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3bca9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3bca9-105">Parameters</span></span>  
 `ppwzAssemblyReferences`  
 <span data-ttu-id="3bca9-106">[in] Null ile sonlandırılmış dize biçiminde dizisi "adı, özellik = değer..." Bu, kısmi derleme kimlikleri listesini belirtin.</span><span class="sxs-lookup"><span data-stu-id="3bca9-106">[in] An array of null-terminated strings in the form "name, property=value..." that specify a list of partial assembly identities.</span></span>  
  
 `dwNumOfReferences`  
 <span data-ttu-id="3bca9-107">[in] Öğe sayısını `ppwzAssemblyReferences`.</span><span class="sxs-lookup"><span data-stu-id="3bca9-107">[in] The number of items in `ppwzAssemblyReferences`.</span></span>  
  
 `ppReferenceList`  
 <span data-ttu-id="3bca9-108">[out] Bir arabirim işaretçisi için bir `ICLRAssemblyReferenceList` listesi içinde belirtilen derlemeler için derleme kimlik verilerini içeren nesne `ppwzAssemblyReferences`.</span><span class="sxs-lookup"><span data-stu-id="3bca9-108">[out] An interface pointer to an `ICLRAssemblyReferenceList` object that contains the assembly identity data for the list of assemblies specified in `ppwzAssemblyReferences`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3bca9-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3bca9-109">Return Value</span></span>  
  
|<span data-ttu-id="3bca9-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3bca9-110">HRESULT</span></span>|<span data-ttu-id="3bca9-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3bca9-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3bca9-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="3bca9-112">S_OK</span></span>|<span data-ttu-id="3bca9-113">Yöntemi başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="3bca9-113">The method returned successfully.</span></span>|  
|<span data-ttu-id="3bca9-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3bca9-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3bca9-115">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="3bca9-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3bca9-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3bca9-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3bca9-117">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="3bca9-117">The call timed out.</span></span>|  
|<span data-ttu-id="3bca9-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3bca9-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3bca9-119">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="3bca9-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3bca9-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3bca9-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3bca9-121">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="3bca9-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3bca9-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3bca9-122">E_FAIL</span></span>|<span data-ttu-id="3bca9-123">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="3bca9-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3bca9-124">CLR, artık bir yöntem E_FAIL döndürürse, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="3bca9-124">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3bca9-125">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="3bca9-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3bca9-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3bca9-126">Requirements</span></span>  
 <span data-ttu-id="3bca9-127">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3bca9-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3bca9-128">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3bca9-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3bca9-129">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="3bca9-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3bca9-130">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3bca9-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bca9-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3bca9-131">See also</span></span>

- [<span data-ttu-id="3bca9-132">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3bca9-132">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="3bca9-133">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3bca9-133">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
