---
title: ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile Metodu
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
ms.openlocfilehash: 9b3c727b49b7df48baa4f5084106f0586419133e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54625707"
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromfile-method"></a><span data-ttu-id="3644d-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile Metodu</span><span class="sxs-lookup"><span data-stu-id="3644d-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile Method</span></span>
<span data-ttu-id="3644d-103">Alır bir [Iclrreferenceassemblyenum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) belirtilen dosya yolunda derlemesi tarafından başvurulan derlemelerin bir listesini içeren örneği.</span><span class="sxs-lookup"><span data-stu-id="3644d-103">Gets an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3644d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3644d-104">Syntax</span></span>  
  
```  
HRESULT GetReferencedAssembliesFromFile (  
    [in]  LPCWSTR pwzFilePath,  
    [in]  DWORD   dwFlags,  
    [in]  ICLRAssemblyReferenceList   *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum  **ppReferenceEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3644d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3644d-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="3644d-106">[in] Değerlendirilecek derleme yolu.</span><span class="sxs-lookup"><span data-stu-id="3644d-106">[in] The path to the assembly to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="3644d-107">[in] Sonra genişletilebilmek için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="3644d-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="3644d-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT geçerli ortak dil çalışma zamanı (CLR) sürümünü destekleyen tek bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="3644d-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pExcludeAssembliesList`  
 <span data-ttu-id="3644d-109">[in] Bir işaretçi bir [Iclrassemblyreferencelist](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) dışında tutulacak derlemeleri temsil eden nesne `ppReferenceEnum`.</span><span class="sxs-lookup"><span data-stu-id="3644d-109">[in] A pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) object that represents assemblies that should be excluded from `ppReferenceEnum`.</span></span>  
  
 `ppReferenceEnum`  
 <span data-ttu-id="3644d-110">[out] Adresine bir işaretçi bir `ICLRReferenceAssemblyEnum` konumunda derlemesi tarafından başvurulan derlemeler için derleme kimlik verilerini içeren nesne `pwzFilePath`, tarafından temsil edilen derlemeleri hariç `pExcludeAssembliesList`.</span><span class="sxs-lookup"><span data-stu-id="3644d-110">[out] A pointer to the address of an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly at `pwzFilePath`, excluding the assemblies represented by `pExcludeAssembliesList`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3644d-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3644d-111">Return Value</span></span>  
  
|<span data-ttu-id="3644d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3644d-112">HRESULT</span></span>|<span data-ttu-id="3644d-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3644d-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3644d-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="3644d-114">S_OK</span></span>|<span data-ttu-id="3644d-115">Yöntemi başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="3644d-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="3644d-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3644d-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3644d-117">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="3644d-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3644d-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3644d-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3644d-119">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="3644d-119">The call timed out.</span></span>|  
|<span data-ttu-id="3644d-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3644d-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3644d-121">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="3644d-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3644d-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3644d-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3644d-123">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="3644d-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3644d-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3644d-124">E_FAIL</span></span>|<span data-ttu-id="3644d-125">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="3644d-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3644d-126">CLR, artık bir yöntem E_FAIL döndürürse, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="3644d-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3644d-127">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="3644d-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3644d-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3644d-128">Remarks</span></span>  
 <span data-ttu-id="3644d-129">Arayan, döndürülen listeden bir dizi bilinen bütünleştirilmiş kod başvuruları dışlanacak seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3644d-129">The caller can choose to exclude a set of known assembly references from the returned list.</span></span> <span data-ttu-id="3644d-130">Bu tarafından tanımlanan `pExcludeAssembliesList` parametresi.</span><span class="sxs-lookup"><span data-stu-id="3644d-130">This set is defined by the `pExcludeAssembliesList` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3644d-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3644d-131">Requirements</span></span>  
 <span data-ttu-id="3644d-132">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3644d-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3644d-133">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3644d-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3644d-134">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="3644d-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3644d-135">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3644d-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3644d-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3644d-136">See also</span></span>
- [<span data-ttu-id="3644d-137">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3644d-137">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="3644d-138">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3644d-138">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="3644d-139">ICLRReferenceAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3644d-139">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
