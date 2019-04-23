---
title: ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetProbingAssembliesFromReference
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference method [.NET Framework hosting]
- GetProbingAssembliesFromReference method [.NET Framework hosting]
ms.assetid: aec05744-e8d4-44c6-b4a8-e583229ac34e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e926fb2753367370e9aca726806eb8747e32048
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59153744"
---
# <a name="iclrassemblyidentitymanagergetprobingassembliesfromreference-method"></a><span data-ttu-id="bccb0-102">ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bccb0-102">ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference Method</span></span>
<span data-ttu-id="bccb0-103">Alır bir [Iclrprobingassemblyenum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) belirtilen kimlik türü ile derlemesi tarafından başvurulan derleme kimlikleri için Numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="bccb0-103">Gets an [ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bccb0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bccb0-104">Syntax</span></span>  
  
```  
HRESULT GetProbingAssembliesFromReference (  
    [in] DWORD   dwMachineType,  
    [in] DWORD   dwFlags,  
    [in] LPCWSTR pwzReferenceIdentity,  
    [out] ICLRProbingAssemblyEnum **ppProbingAssemblyEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bccb0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bccb0-105">Parameters</span></span>  
 `dwMachineType`  
 <span data-ttu-id="bccb0-106">[in] İşlemci mimarisi WinNT.h içinde tanımlanan belirtir. geçerli bir değer.</span><span class="sxs-lookup"><span data-stu-id="bccb0-106">[in] A valid value that specifies the processor architecture, as defined in WinNT.h.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="bccb0-107">[in] Sonra genişletilebilmek için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="bccb0-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="bccb0-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT geçerli ortak dil çalışma zamanı (CLR) sürümünü destekleyen tek bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="bccb0-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzReferenceIdentity`  
 <span data-ttu-id="bccb0-109">[in] Genellikle çağrısından döndürülen bir donuk derleme bağlama kimliği [Iclrassemblyıdentitymanager::getbindingıdentityfromfile](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md) veya [Iclrassemblyıdentitymanager::getbindingıdentityfromstream](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="bccb0-109">[in] An opaque assembly binding identity, typically returned from a call to the [ICLRAssemblyIdentityManager::GetBindingIdentityFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md) or [ICLRAssemblyIdentityManager::GetBindingIdentityFromStream](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md) method.</span></span>  
  
 `ppProbingAssemblyEnum`  
 <span data-ttu-id="bccb0-110">[out] Bir arabirim işaretçisi için bir `ICLRProbingAssemblyEnum` tarafından tanıtılan derlemenin başvurduğu derlemeleri başvurular içeren bir numaralandırıcı `pwzReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="bccb0-110">[out] An interface pointer to an `ICLRProbingAssemblyEnum` enumerator that contains references to the assemblies referenced by the assembly identified by `pwzReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bccb0-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bccb0-111">Return Value</span></span>  
  
|<span data-ttu-id="bccb0-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bccb0-112">HRESULT</span></span>|<span data-ttu-id="bccb0-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bccb0-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bccb0-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="bccb0-114">S_OK</span></span>|<span data-ttu-id="bccb0-115">Yöntemi başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="bccb0-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="bccb0-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bccb0-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bccb0-117">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="bccb0-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bccb0-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bccb0-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bccb0-119">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="bccb0-119">The call timed out.</span></span>|  
|<span data-ttu-id="bccb0-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bccb0-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bccb0-121">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="bccb0-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bccb0-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bccb0-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bccb0-123">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="bccb0-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bccb0-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bccb0-124">E_FAIL</span></span>|<span data-ttu-id="bccb0-125">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="bccb0-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bccb0-126">CLR, artık bir yöntem E_FAIL döndürürse, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="bccb0-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bccb0-127">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="bccb0-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bccb0-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bccb0-128">Requirements</span></span>  
 <span data-ttu-id="bccb0-129">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bccb0-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bccb0-130">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bccb0-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bccb0-131">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="bccb0-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bccb0-132">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bccb0-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bccb0-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bccb0-133">See also</span></span>

- [<span data-ttu-id="bccb0-134">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bccb0-134">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="bccb0-135">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bccb0-135">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="bccb0-136">ICLRProbingAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bccb0-136">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)
