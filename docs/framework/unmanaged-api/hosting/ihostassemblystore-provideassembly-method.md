---
title: IHostAssemblyStore::ProvideAssembly Yöntemi
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore.ProvideAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore::ProvideAssembly
helpviewer_keywords:
- ProvideAssembly method [.NET Framework hosting]
- IHostAssemblyStore::ProvideAssembly method [.NET Framework hosting]
ms.assetid: 625c3dd5-a3f0-442c-adde-310dadbb5054
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 62a8be1e330338043df50bd80576b5aa65447b9c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61951781"
---
# <a name="ihostassemblystoreprovideassembly-method"></a><span data-ttu-id="9fa5f-102">IHostAssemblyStore::ProvideAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9fa5f-102">IHostAssemblyStore::ProvideAssembly Method</span></span>
<span data-ttu-id="9fa5f-103">Tarafından başvurulmuyor bir derlemeye bir başvuru alır [Iclrassemblyreferencelist](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) sağlayıcıdan döndürülen [Ihostassemblymanager::getnonhoststoreassemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span><span class="sxs-lookup"><span data-stu-id="9fa5f-103">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that is returned from [IHostAssemblyManager::GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span> <span data-ttu-id="9fa5f-104">Ortak dil çalışma zamanı (CLR) çağıran `ProvideAssembly` listesinde görünmüyor her derleme için.</span><span class="sxs-lookup"><span data-stu-id="9fa5f-104">The common language runtime (CLR) calls `ProvideAssembly` for each assembly that does not appear in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fa5f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9fa5f-105">Syntax</span></span>  
  
```  
HRESULT ProvideAssembly (  
    [in]  AssemblyBindInfo *pBindInfo,  
    [out] UINT64           *pAssemblyId,  
    [out] UINT64           *pHostContext,  
    [out] IStream          **ppStmAssemblyImage,  
    [out] IStream          **ppStmPDB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9fa5f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9fa5f-106">Parameters</span></span>  
 `pBindInfo`  
 <span data-ttu-id="9fa5f-107">[in] Bir işaretçi bir [Assemblybindınfo](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md) varlığı veya yokluğu herhangi bir sürüm oluşturma ilkesine dahil olmak üzere, belirli bir bağlama özellikleri belirlemek için konağın kullandığı örneği ve bağlamak için hangi derleme.</span><span class="sxs-lookup"><span data-stu-id="9fa5f-107">[in] A pointer to an [AssemblyBindInfo](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md) instance that the host uses to determine certain bind characteristics, including the presence or absence of any versioning policy, and which assembly to bind to.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="9fa5f-108">[out] Bunun için istenen derleme için benzersiz bir tanımlayıcı için bir işaretçi `IStream`.</span><span class="sxs-lookup"><span data-stu-id="9fa5f-108">[out] A pointer to a unique identifier for the requested assembly for this `IStream`.</span></span>  
  
 `pHostContext`  
 <span data-ttu-id="9fa5f-109">[out] Bir platform gerek olmadan istenen derleme kanıtı belirlemek için kullanılan ana bilgisayara özgü veri işaretçisi çağrısı çağırın.</span><span class="sxs-lookup"><span data-stu-id="9fa5f-109">[out] A pointer to host-specific data that is used to determine the evidence of the requested assembly without the need of a platform invoke call.</span></span> <span data-ttu-id="9fa5f-110">`pHostContext` karşılık gelen <xref:System.Reflection.Assembly.HostContext%2A> yönetilen özellik <xref:System.Reflection.Assembly> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9fa5f-110">`pHostContext` corresponds to the <xref:System.Reflection.Assembly.HostContext%2A> property of the managed <xref:System.Reflection.Assembly> class.</span></span>  
  
 `ppStmAssemblyImage`  
 <span data-ttu-id="9fa5f-111">[out] Adresine bir işaretçi bir `IStream` yüklenmesi veya bütünleştirilmiş kod bulunamadı, null için taşınabilir yürütülebilir (PE) görüntüsünü içerir.</span><span class="sxs-lookup"><span data-stu-id="9fa5f-111">[out] A pointer to the address of an `IStream` that contains the portable executable (PE) image to be loaded, or null if the assembly could not be found.</span></span>  
  
 `ppStmPDB`  
 <span data-ttu-id="9fa5f-112">[out] Adresine bir işaretçi bir `IStream` varsa program hata ayıklama (PDB) bilgileri veya null .pdb dosyası bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="9fa5f-112">[out] A pointer to the address of an `IStream` that contains the program debug (PDB) information, or null if the .pdb file could not be found.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9fa5f-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9fa5f-113">Return Value</span></span>  
  
|<span data-ttu-id="9fa5f-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9fa5f-114">HRESULT</span></span>|<span data-ttu-id="9fa5f-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9fa5f-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9fa5f-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="9fa5f-116">S_OK</span></span>|<span data-ttu-id="9fa5f-117">`ProvideAssembly` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="9fa5f-117">`ProvideAssembly` returned successfully.</span></span>|  
|<span data-ttu-id="9fa5f-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9fa5f-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9fa5f-119">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="9fa5f-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9fa5f-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9fa5f-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9fa5f-121">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="9fa5f-121">The call timed out.</span></span>|  
|<span data-ttu-id="9fa5f-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9fa5f-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9fa5f-123">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="9fa5f-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9fa5f-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9fa5f-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9fa5f-125">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="9fa5f-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9fa5f-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9fa5f-126">E_FAIL</span></span>|<span data-ttu-id="9fa5f-127">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="9fa5f-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9fa5f-128">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9fa5f-128">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9fa5f-129">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="9fa5f-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9fa5f-130">COR_E_FILENOTFOUND (0x80070002)</span><span class="sxs-lookup"><span data-stu-id="9fa5f-130">COR_E_FILENOTFOUND (0x80070002)</span></span>|<span data-ttu-id="9fa5f-131">İstenen derleme bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="9fa5f-131">The requested assembly could not be located.</span></span>|  
|<span data-ttu-id="9fa5f-132">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="9fa5f-132">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="9fa5f-133">Tarafından belirtilen arabellek boyutu `pAssemblyId` döndürülecek konak istediği tanımlayıcısı tutabilecek kadar büyük değil.</span><span class="sxs-lookup"><span data-stu-id="9fa5f-133">The buffer size specified by `pAssemblyId` is not large enough to hold the identifier that the host wants to return.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9fa5f-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9fa5f-134">Remarks</span></span>  
 <span data-ttu-id="9fa5f-135">Kimlik değeri için döndürülen `pAssemblyId` ana bilgisayar tarafından belirtilir.</span><span class="sxs-lookup"><span data-stu-id="9fa5f-135">The identity value returned for `pAssemblyId` is specified by the host.</span></span> <span data-ttu-id="9fa5f-136">Tanımlayıcılar bir işlem yaşam süresi içinde benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9fa5f-136">Identifiers must be unique within the lifetime of a process.</span></span> <span data-ttu-id="9fa5f-137">CLR, akışı için benzersiz bir tanımlayıcı olarak bu değeri kullanır.</span><span class="sxs-lookup"><span data-stu-id="9fa5f-137">The CLR uses this value as a unique identifier for the stream.</span></span> <span data-ttu-id="9fa5f-138">Her değer değerlerini karşı denetler `pAssemblyId` yapılan diğer çağrılar tarafından döndürülen `ProvideAssembly`.</span><span class="sxs-lookup"><span data-stu-id="9fa5f-138">It checks each value against the values for `pAssemblyId` returned by other calls to `ProvideAssembly`.</span></span> <span data-ttu-id="9fa5f-139">Konak aynı döndürürse `pAssemblyId` başka bir değer `IStream`, CLR, akış içeriğini zaten eşlendi olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="9fa5f-139">If the host returns the same `pAssemblyId` value for another `IStream`, the CLR checks whether the contents of that stream have already been mapped.</span></span> <span data-ttu-id="9fa5f-140">Bu durumda, çalışma zamanı yerine yeni bir eşleme görüntü kopyasının yükler.</span><span class="sxs-lookup"><span data-stu-id="9fa5f-140">If so, the runtime loads the existing copy of the image instead of mapping a new one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fa5f-141">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9fa5f-141">Requirements</span></span>  
 <span data-ttu-id="9fa5f-142">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9fa5f-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fa5f-143">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9fa5f-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9fa5f-144">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="9fa5f-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9fa5f-145">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fa5f-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fa5f-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9fa5f-146">See also</span></span>

- [<span data-ttu-id="9fa5f-147">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9fa5f-147">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="9fa5f-148">IHostAssemblyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9fa5f-148">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [<span data-ttu-id="9fa5f-149">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9fa5f-149">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
