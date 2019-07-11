---
title: ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetReferencedAssembliesFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetReferenceAssembliesFromFile method [.NET Framework hosting]
- GetReferenceAssembliesFromFile method [.NET Framework hosting]
ms.assetid: eed63d31-d977-4c7d-9443-f9d37a2a7d81
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bb7500c1c9d09cffd0c1f3365b2a7cf939f78531
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773421"
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromfile-method"></a><span data-ttu-id="8f178-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8f178-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile Method</span></span>
<span data-ttu-id="8f178-103">Alır bir [Iclrreferenceassemblyenum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) belirtilen dosya yolunda derlemesi tarafından başvurulan derlemelerin bir listesini içeren örneği.</span><span class="sxs-lookup"><span data-stu-id="8f178-103">Gets an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f178-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8f178-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReferencedAssembliesFromFile (  
    [in]  LPCWSTR pwzFilePath,  
    [in]  DWORD   dwFlags,  
    [in]  ICLRAssemblyReferenceList   *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum  **ppReferenceEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f178-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8f178-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="8f178-106">[in] Değerlendirilecek derleme yolu.</span><span class="sxs-lookup"><span data-stu-id="8f178-106">[in] The path to the assembly to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="8f178-107">[in] Sonra genişletilebilmek için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="8f178-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="8f178-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT geçerli ortak dil çalışma zamanı (CLR) sürümünü destekleyen tek bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="8f178-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pExcludeAssembliesList`  
 <span data-ttu-id="8f178-109">[in] Bir işaretçi bir [Iclrassemblyreferencelist](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) dışında tutulacak derlemeleri temsil eden nesne `ppReferenceEnum`.</span><span class="sxs-lookup"><span data-stu-id="8f178-109">[in] A pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) object that represents assemblies that should be excluded from `ppReferenceEnum`.</span></span>  
  
 `ppReferenceEnum`  
 <span data-ttu-id="8f178-110">[out] Adresine bir işaretçi bir `ICLRReferenceAssemblyEnum` konumunda derlemesi tarafından başvurulan derlemeler için derleme kimlik verilerini içeren nesne `pwzFilePath`, tarafından temsil edilen derlemeleri hariç `pExcludeAssembliesList`.</span><span class="sxs-lookup"><span data-stu-id="8f178-110">[out] A pointer to the address of an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly at `pwzFilePath`, excluding the assemblies represented by `pExcludeAssembliesList`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8f178-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8f178-111">Return Value</span></span>  
  
|<span data-ttu-id="8f178-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8f178-112">HRESULT</span></span>|<span data-ttu-id="8f178-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8f178-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8f178-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="8f178-114">S_OK</span></span>|<span data-ttu-id="8f178-115">Yöntemi başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="8f178-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="8f178-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8f178-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8f178-117">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="8f178-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8f178-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8f178-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8f178-119">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="8f178-119">The call timed out.</span></span>|  
|<span data-ttu-id="8f178-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8f178-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8f178-121">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="8f178-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8f178-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8f178-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8f178-123">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="8f178-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8f178-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8f178-124">E_FAIL</span></span>|<span data-ttu-id="8f178-125">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="8f178-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8f178-126">CLR, artık bir yöntem E_FAIL döndürürse, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="8f178-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8f178-127">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="8f178-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f178-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8f178-128">Remarks</span></span>  
 <span data-ttu-id="8f178-129">Arayan, döndürülen listeden bir dizi bilinen bütünleştirilmiş kod başvuruları dışlanacak seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f178-129">The caller can choose to exclude a set of known assembly references from the returned list.</span></span> <span data-ttu-id="8f178-130">Bu tarafından tanımlanan `pExcludeAssembliesList` parametresi.</span><span class="sxs-lookup"><span data-stu-id="8f178-130">This set is defined by the `pExcludeAssembliesList` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f178-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8f178-131">Requirements</span></span>  
 <span data-ttu-id="8f178-132">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f178-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f178-133">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8f178-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8f178-134">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="8f178-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8f178-135">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f178-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f178-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f178-136">See also</span></span>

- [<span data-ttu-id="8f178-137">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8f178-137">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="8f178-138">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8f178-138">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="8f178-139">ICLRReferenceAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8f178-139">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
