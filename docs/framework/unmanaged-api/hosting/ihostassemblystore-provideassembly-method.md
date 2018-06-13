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
ms.openlocfilehash: e32d48931177a42dd14092b4052370764a217abe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440369"
---
# <a name="ihostassemblystoreprovideassembly-method"></a><span data-ttu-id="e4051-102">IHostAssemblyStore::ProvideAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e4051-102">IHostAssemblyStore::ProvideAssembly Method</span></span>
<span data-ttu-id="e4051-103">Tarafından başvurulmuyor bir derlemesine başvuru alır [Iclrassemblyreferencelist](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) sağlayıcıdan döndürülen [Ihostassemblymanager::getnonhoststoreassemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span><span class="sxs-lookup"><span data-stu-id="e4051-103">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that is returned from [IHostAssemblyManager::GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span> <span data-ttu-id="e4051-104">Ortak dil çalışma zamanı (CLR) çağırır `ProvideAssembly` listede görünmeyen her derleme için.</span><span class="sxs-lookup"><span data-stu-id="e4051-104">The common language runtime (CLR) calls `ProvideAssembly` for each assembly that does not appear in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4051-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e4051-105">Syntax</span></span>  
  
```  
HRESULT ProvideAssembly (  
    [in]  AssemblyBindInfo *pBindInfo,  
    [out] UINT64           *pAssemblyId,  
    [out] UINT64           *pHostContext,  
    [out] IStream          **ppStmAssemblyImage,  
    [out] IStream          **ppStmPDB  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e4051-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e4051-106">Parameters</span></span>  
 `pBindInfo`  
 <span data-ttu-id="e4051-107">[in] Bir işaretçi bir [Assemblybindınfo](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md) ana bilgisayar varlığı veya yokluğuna göre herhangi bir sürüm oluşturma ilkesi de dahil olmak üzere, belirli bir bağlama özellikleri belirlemek için kullanır örneği ve bağlamak için hangi derleme.</span><span class="sxs-lookup"><span data-stu-id="e4051-107">[in] A pointer to an [AssemblyBindInfo](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md) instance that the host uses to determine certain bind characteristics, including the presence or absence of any versioning policy, and which assembly to bind to.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="e4051-108">[out] Bunun için istenen derlemesi için benzersiz bir tanımlayıcı için bir işaretçi `IStream`.</span><span class="sxs-lookup"><span data-stu-id="e4051-108">[out] A pointer to a unique identifier for the requested assembly for this `IStream`.</span></span>  
  
 `pHostContext`  
 <span data-ttu-id="e4051-109">[out] Bir platform gerek kalmadan istenen derleme kanıtı belirlemek için kullanılan konak özgü veriler için bir işaretçi çağrısı çağırır.</span><span class="sxs-lookup"><span data-stu-id="e4051-109">[out] A pointer to host-specific data that is used to determine the evidence of the requested assembly without the need of a platform invoke call.</span></span> <span data-ttu-id="e4051-110">`pHostContext` karşılık gelen <xref:System.Reflection.Assembly.HostContext%2A> yönetilen özelliği <xref:System.Reflection.Assembly> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e4051-110">`pHostContext` corresponds to the <xref:System.Reflection.Assembly.HostContext%2A> property of the managed <xref:System.Reflection.Assembly> class.</span></span>  
  
 `ppStmAssemblyImage`  
 <span data-ttu-id="e4051-111">[out] Adresine bir işaretçi bir `IStream` yüklenmesi veya derlemenin bulunamamış olması, boş için taşınabilir yürütülebilir (PE) görüntüsünü içerir.</span><span class="sxs-lookup"><span data-stu-id="e4051-111">[out] A pointer to the address of an `IStream` that contains the portable executable (PE) image to be loaded, or null if the assembly could not be found.</span></span>  
  
 `ppStmPDB`  
 <span data-ttu-id="e4051-112">[out] Adresine bir işaretçi bir `IStream` , içeriyorsa program hata ayıklama (PDB) bilgileri ya da null .pdb dosyası bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="e4051-112">[out] A pointer to the address of an `IStream` that contains the program debug (PDB) information, or null if the .pdb file could not be found.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e4051-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e4051-113">Return Value</span></span>  
  
|<span data-ttu-id="e4051-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e4051-114">HRESULT</span></span>|<span data-ttu-id="e4051-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e4051-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e4051-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="e4051-116">S_OK</span></span>|<span data-ttu-id="e4051-117">`ProvideAssembly` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e4051-117">`ProvideAssembly` returned successfully.</span></span>|  
|<span data-ttu-id="e4051-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e4051-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e4051-119">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="e4051-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e4051-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e4051-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e4051-121">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="e4051-121">The call timed out.</span></span>|  
|<span data-ttu-id="e4051-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e4051-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e4051-123">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="e4051-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e4051-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e4051-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e4051-125">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="e4051-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e4051-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e4051-126">E_FAIL</span></span>|<span data-ttu-id="e4051-127">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e4051-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e4051-128">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e4051-128">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e4051-129">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="e4051-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e4051-130">COR_E_FILENOTFOUND (0X80070002)</span><span class="sxs-lookup"><span data-stu-id="e4051-130">COR_E_FILENOTFOUND (0x80070002)</span></span>|<span data-ttu-id="e4051-131">İstenen derlemesi bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="e4051-131">The requested assembly could not be located.</span></span>|  
|<span data-ttu-id="e4051-132">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="e4051-132">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="e4051-133">Belirtilen arabellek boyutu `pAssemblyId` döndürmek için konak istediği tanımlayıcı tutmak için yeterince büyük değil.</span><span class="sxs-lookup"><span data-stu-id="e4051-133">The buffer size specified by `pAssemblyId` is not large enough to hold the identifier that the host wants to return.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4051-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e4051-134">Remarks</span></span>  
 <span data-ttu-id="e4051-135">İçin kimlik değeri döndürülen `pAssemblyId` ana bilgisayar tarafından belirtilir.</span><span class="sxs-lookup"><span data-stu-id="e4051-135">The identity value returned for `pAssemblyId` is specified by the host.</span></span> <span data-ttu-id="e4051-136">Tanımlayıcıları bir işlem yaşam süresi içinde benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e4051-136">Identifiers must be unique within the lifetime of a process.</span></span> <span data-ttu-id="e4051-137">CLR akış için benzersiz bir tanımlayıcı olarak bu değeri kullanır.</span><span class="sxs-lookup"><span data-stu-id="e4051-137">The CLR uses this value as a unique identifier for the stream.</span></span> <span data-ttu-id="e4051-138">Her değer için değerleri karşı denetler `pAssemblyId` diğer çağrı tarafından döndürülen `ProvideAssembly`.</span><span class="sxs-lookup"><span data-stu-id="e4051-138">It checks each value against the values for `pAssemblyId` returned by other calls to `ProvideAssembly`.</span></span> <span data-ttu-id="e4051-139">Ana bilgisayar aynı döndürürse `pAssemblyId` için başka bir değer `IStream`, CLR, akış içeriğini zaten eşlenmiş olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="e4051-139">If the host returns the same `pAssemblyId` value for another `IStream`, the CLR checks whether the contents of that stream have already been mapped.</span></span> <span data-ttu-id="e4051-140">Bu durumda, var olan kopyasını yeni bir eşleme yerine görüntü çalışma zamanı yükler.</span><span class="sxs-lookup"><span data-stu-id="e4051-140">If so, the runtime loads the existing copy of the image instead of mapping a new one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4051-141">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e4051-141">Requirements</span></span>  
 <span data-ttu-id="e4051-142">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4051-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4051-143">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e4051-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e4051-144">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e4051-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e4051-145">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4051-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4051-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e4051-146">See Also</span></span>  
 [<span data-ttu-id="e4051-147">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e4051-147">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="e4051-148">IHostAssemblyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e4051-148">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="e4051-149">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e4051-149">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
