---
title: ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference Metodu
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
ms.openlocfilehash: 26423837c173b5f18282a8aa480ae92ecc452489
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435660"
---
# <a name="iclrassemblyidentitymanagergetprobingassembliesfromreference-method"></a><span data-ttu-id="62abf-102">ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference Metodu</span><span class="sxs-lookup"><span data-stu-id="62abf-102">ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference Method</span></span>
<span data-ttu-id="62abf-103">Alır bir [Iclrprobingassemblyenum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) belirli bir kimlik türüne sahip derlemesi tarafından başvurulan derleme kimlikleri için Numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="62abf-103">Gets an [ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62abf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="62abf-104">Syntax</span></span>  
  
```  
HRESULT GetProbingAssembliesFromReference (  
    [in] DWORD   dwMachineType,  
    [in] DWORD   dwFlags,  
    [in] LPCWSTR pwzReferenceIdentity,  
    [out] ICLRProbingAssemblyEnum **ppProbingAssemblyEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="62abf-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="62abf-105">Parameters</span></span>  
 `dwMachineType`  
 <span data-ttu-id="62abf-106">[in] İşlemci mimarisi WinNT.h içinde tanımlanan belirtir. geçerli bir değer.</span><span class="sxs-lookup"><span data-stu-id="62abf-106">[in] A valid value that specifies the processor architecture, as defined in WinNT.h.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="62abf-107">[in] Gelecekteki genişletilebilirliği için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="62abf-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="62abf-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT ortak dil çalışma zamanı (CLR) geçerli sürümünü destekleyen tek değerdir.</span><span class="sxs-lookup"><span data-stu-id="62abf-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzReferenceIdentity`  
 <span data-ttu-id="62abf-109">[in] Genellikle çağrısından döndürülen bir donuk derleme bağlama kimlik [Iclrassemblyıdentitymanager::getbindingıdentityfromfile](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md) veya [Iclrassemblyıdentitymanager::getbindingıdentityfromstream](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="62abf-109">[in] An opaque assembly binding identity, typically returned from a call to the [ICLRAssemblyIdentityManager::GetBindingIdentityFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md) or [ICLRAssemblyIdentityManager::GetBindingIdentityFromStream](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md) method.</span></span>  
  
 `ppProbingAssemblyEnum`  
 <span data-ttu-id="62abf-110">[out] Bir arabirim işaretçisi bir `ICLRProbingAssemblyEnum` tarafından tanımlanan derlemesi tarafından başvurulan derleme başvuruları içeren Numaralandırıcı `pwzReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="62abf-110">[out] An interface pointer to an `ICLRProbingAssemblyEnum` enumerator that contains references to the assemblies referenced by the assembly identified by `pwzReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="62abf-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="62abf-111">Return Value</span></span>  
  
|<span data-ttu-id="62abf-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="62abf-112">HRESULT</span></span>|<span data-ttu-id="62abf-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="62abf-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="62abf-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="62abf-114">S_OK</span></span>|<span data-ttu-id="62abf-115">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="62abf-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="62abf-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="62abf-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="62abf-117">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="62abf-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="62abf-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="62abf-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="62abf-119">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="62abf-119">The call timed out.</span></span>|  
|<span data-ttu-id="62abf-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="62abf-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="62abf-121">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="62abf-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="62abf-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="62abf-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="62abf-123">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="62abf-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="62abf-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="62abf-124">E_FAIL</span></span>|<span data-ttu-id="62abf-125">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="62abf-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="62abf-126">Bir yöntem E_FAIL döndürürse, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="62abf-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="62abf-127">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="62abf-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="62abf-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="62abf-128">Requirements</span></span>  
 <span data-ttu-id="62abf-129">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62abf-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62abf-130">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="62abf-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="62abf-131">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="62abf-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="62abf-132">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62abf-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62abf-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="62abf-133">See Also</span></span>  
 [<span data-ttu-id="62abf-134">ICLRAssemblyIdentityManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="62abf-134">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="62abf-135">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="62abf-135">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="62abf-136">ICLRProbingAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="62abf-136">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)
