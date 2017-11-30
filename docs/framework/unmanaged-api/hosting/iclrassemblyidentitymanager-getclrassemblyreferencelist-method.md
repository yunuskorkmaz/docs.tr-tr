---
title: ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyIdentityManager.GetCLRAssemblyReferenceList
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList
helpviewer_keywords:
- GetClrAssemblyReferenceList method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList method [.NET Framework hosting]
ms.assetid: cb5ffae5-287b-4a87-9ca8-7ce3ae0601b7
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5456d725f5bb1c11308b72fdb72f6f60d57ea6b3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrassemblyidentitymanagergetclrassemblyreferencelist-method"></a><span data-ttu-id="6c263-102">ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList Metodu</span><span class="sxs-lookup"><span data-stu-id="6c263-102">ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList Method</span></span>
<span data-ttu-id="6c263-103">Bir arabirim işaretçisi alır bir [Iclrassemblyreferencelist](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) kısmi derleme kimlikleri sağlanan listeden örneği.</span><span class="sxs-lookup"><span data-stu-id="6c263-103">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c263-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6c263-104">Syntax</span></span>  
  
```  
HRESULT  GetCLRAssemblyReferenceList (  
    [in] LPCWSTR *ppwzAssemblyReferences,  
    [in] DWORD    dwNumOfReferences,  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6c263-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6c263-105">Parameters</span></span>  
 `ppwzAssemblyReferences`  
 <span data-ttu-id="6c263-106">[in] Null ile sonlandırılmış dizeler biçiminde bir dizi "adı, özellik değeri... =" kısmi derleme kimlikleri listesini belirtin.</span><span class="sxs-lookup"><span data-stu-id="6c263-106">[in] An array of null-terminated strings in the form "name, property=value..." that specify a list of partial assembly identities.</span></span>  
  
 `dwNumOfReferences`  
 <span data-ttu-id="6c263-107">[in] Öğelerin sayısı `ppwzAssemblyReferences`.</span><span class="sxs-lookup"><span data-stu-id="6c263-107">[in] The number of items in `ppwzAssemblyReferences`.</span></span>  
  
 `ppReferenceList`  
 <span data-ttu-id="6c263-108">[out] Bir arabirim işaretçisi bir `ICLRAssemblyReferenceList` belirtilen derleme listesi için derleme kimlik verilerini içeren nesne `ppwzAssemblyReferences`.</span><span class="sxs-lookup"><span data-stu-id="6c263-108">[out] An interface pointer to an `ICLRAssemblyReferenceList` object that contains the assembly identity data for the list of assemblies specified in `ppwzAssemblyReferences`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6c263-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6c263-109">Return Value</span></span>  
  
|<span data-ttu-id="6c263-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6c263-110">HRESULT</span></span>|<span data-ttu-id="6c263-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6c263-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6c263-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="6c263-112">S_OK</span></span>|<span data-ttu-id="6c263-113">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="6c263-113">The method returned successfully.</span></span>|  
|<span data-ttu-id="6c263-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6c263-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6c263-115">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="6c263-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6c263-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6c263-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6c263-117">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="6c263-117">The call timed out.</span></span>|  
|<span data-ttu-id="6c263-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6c263-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6c263-119">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="6c263-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6c263-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6c263-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6c263-121">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="6c263-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6c263-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6c263-122">E_FAIL</span></span>|<span data-ttu-id="6c263-123">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="6c263-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6c263-124">Bir yöntem E_FAIL döndürürse, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6c263-124">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6c263-125">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="6c263-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6c263-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6c263-126">Requirements</span></span>  
 <span data-ttu-id="6c263-127">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c263-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c263-128">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6c263-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6c263-129">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="6c263-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6c263-130">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c263-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c263-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6c263-131">See Also</span></span>  
 [<span data-ttu-id="6c263-132">Iclrassemblyıdentitymanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="6c263-132">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="6c263-133">Iclrassemblyreferencelist arabirimi</span><span class="sxs-lookup"><span data-stu-id="6c263-133">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
