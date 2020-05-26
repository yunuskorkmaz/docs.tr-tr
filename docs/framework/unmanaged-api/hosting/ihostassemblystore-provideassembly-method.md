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
ms.openlocfilehash: f97490e89e835716911072dbad5f70d8e55e76e6
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805022"
---
# <a name="ihostassemblystoreprovideassembly-method"></a><span data-ttu-id="3dab9-102">IHostAssemblyStore::ProvideAssembly Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3dab9-102">IHostAssemblyStore::ProvideAssembly Method</span></span>
<span data-ttu-id="3dab9-103">[IHostAssemblyManager:: GetNonHostStoreAssemblies](ihostassemblymanager-getnonhoststoreassemblies-method.md)öğesinden döndürülen [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) tarafından başvurulmayan bir derlemeye başvuru alır.</span><span class="sxs-lookup"><span data-stu-id="3dab9-103">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) that is returned from [IHostAssemblyManager::GetNonHostStoreAssemblies](ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span> <span data-ttu-id="3dab9-104">Ortak dil çalışma zamanı (CLR), `ProvideAssembly` Listede görünmeyen her derleme için çağırır.</span><span class="sxs-lookup"><span data-stu-id="3dab9-104">The common language runtime (CLR) calls `ProvideAssembly` for each assembly that does not appear in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dab9-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="3dab9-105">Syntax</span></span>  
  
```cpp  
HRESULT ProvideAssembly (  
    [in]  AssemblyBindInfo *pBindInfo,  
    [out] UINT64           *pAssemblyId,  
    [out] UINT64           *pHostContext,  
    [out] IStream          **ppStmAssemblyImage,  
    [out] IStream          **ppStmPDB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3dab9-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3dab9-106">Parameters</span></span>  
 `pBindInfo`  
 <span data-ttu-id="3dab9-107">'ndaki Herhangi bir sürüm oluşturma ilkesinin varlığı veya yokluğu ve hangi derlemenin bağlanacağı dahil olmak üzere, konağın belirli bağlama özelliklerini belirlemede kullandığı bir [AssemblyBindInfo](assemblybindinfo-structure.md) örneği işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="3dab9-107">[in] A pointer to an [AssemblyBindInfo](assemblybindinfo-structure.md) instance that the host uses to determine certain bind characteristics, including the presence or absence of any versioning policy, and which assembly to bind to.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="3dab9-108">dışı Bunun için istenen derleme için benzersiz bir tanımlayıcı işaretçisi `IStream` .</span><span class="sxs-lookup"><span data-stu-id="3dab9-108">[out] A pointer to a unique identifier for the requested assembly for this `IStream`.</span></span>  
  
 `pHostContext`  
 <span data-ttu-id="3dab9-109">dışı Platform çağırma çağrısına gerek olmadan istenen derlemenin kanıtını belirlemede kullanılan, konağa özgü verilere yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3dab9-109">[out] A pointer to host-specific data that is used to determine the evidence of the requested assembly without the need of a platform invoke call.</span></span> <span data-ttu-id="3dab9-110">`pHostContext`<xref:System.Reflection.Assembly.HostContext%2A>yönetilen sınıfın özelliğine karşılık gelir <xref:System.Reflection.Assembly> .</span><span class="sxs-lookup"><span data-stu-id="3dab9-110">`pHostContext` corresponds to the <xref:System.Reflection.Assembly.HostContext%2A> property of the managed <xref:System.Reflection.Assembly> class.</span></span>  
  
 `ppStmAssemblyImage`  
 <span data-ttu-id="3dab9-111">dışı `IStream`Yüklenecek Taşınabilir çalıştırılabilir (PE) görüntüsünü içeren bir adresine yönelik bir işaretçi veya derleme bulunamazsa null.</span><span class="sxs-lookup"><span data-stu-id="3dab9-111">[out] A pointer to the address of an `IStream` that contains the portable executable (PE) image to be loaded, or null if the assembly could not be found.</span></span>  
  
 `ppStmPDB`  
 <span data-ttu-id="3dab9-112">dışı `IStream`Program hata ayıklama (pdb) bilgilerini içeren bir adresine yönelik bir işaretçi veya. pdb dosyası bulunamazsa null.</span><span class="sxs-lookup"><span data-stu-id="3dab9-112">[out] A pointer to the address of an `IStream` that contains the program debug (PDB) information, or null if the .pdb file could not be found.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3dab9-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3dab9-113">Return Value</span></span>  
  
|<span data-ttu-id="3dab9-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3dab9-114">HRESULT</span></span>|<span data-ttu-id="3dab9-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3dab9-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3dab9-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="3dab9-116">S_OK</span></span>|<span data-ttu-id="3dab9-117">`ProvideAssembly`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="3dab9-117">`ProvideAssembly` returned successfully.</span></span>|  
|<span data-ttu-id="3dab9-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3dab9-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3dab9-119">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="3dab9-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3dab9-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3dab9-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3dab9-121">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="3dab9-121">The call timed out.</span></span>|  
|<span data-ttu-id="3dab9-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3dab9-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3dab9-123">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="3dab9-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3dab9-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3dab9-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3dab9-125">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="3dab9-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3dab9-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3dab9-126">E_FAIL</span></span>|<span data-ttu-id="3dab9-127">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="3dab9-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3dab9-128">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="3dab9-128">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3dab9-129">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="3dab9-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3dab9-130">COR_E_FILENOTFOUND (0x80070002)</span><span class="sxs-lookup"><span data-stu-id="3dab9-130">COR_E_FILENOTFOUND (0x80070002)</span></span>|<span data-ttu-id="3dab9-131">İstenen derleme bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="3dab9-131">The requested assembly could not be located.</span></span>|  
|<span data-ttu-id="3dab9-132">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="3dab9-132">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="3dab9-133">Tarafından belirtilen arabellek boyutu, `pAssemblyId` konağın döndürmek istediği tanımlayıcıyı tutabilecek kadar büyük değil.</span><span class="sxs-lookup"><span data-stu-id="3dab9-133">The buffer size specified by `pAssemblyId` is not large enough to hold the identifier that the host wants to return.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3dab9-134">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3dab9-134">Remarks</span></span>  
 <span data-ttu-id="3dab9-135">İçin döndürülen kimlik değeri `pAssemblyId` ana bilgisayar tarafından belirtilir.</span><span class="sxs-lookup"><span data-stu-id="3dab9-135">The identity value returned for `pAssemblyId` is specified by the host.</span></span> <span data-ttu-id="3dab9-136">Tanımlayıcılar bir işlemin ömrü içinde benzersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3dab9-136">Identifiers must be unique within the lifetime of a process.</span></span> <span data-ttu-id="3dab9-137">CLR bu değeri akış için benzersiz bir tanımlayıcı olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="3dab9-137">The CLR uses this value as a unique identifier for the stream.</span></span> <span data-ttu-id="3dab9-138">Her değeri, `pAssemblyId` için diğer çağrılar tarafından döndürülen değerlere karşı denetler `ProvideAssembly` .</span><span class="sxs-lookup"><span data-stu-id="3dab9-138">It checks each value against the values for `pAssemblyId` returned by other calls to `ProvideAssembly`.</span></span> <span data-ttu-id="3dab9-139">Konak `pAssemblyId` diğeri için aynı değeri döndürürse `IStream` , clr bu akışın içeriğinin zaten eşlenmiş olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="3dab9-139">If the host returns the same `pAssemblyId` value for another `IStream`, the CLR checks whether the contents of that stream have already been mapped.</span></span> <span data-ttu-id="3dab9-140">Öyleyse, çalışma zamanı yeni bir tane eşlemek yerine görüntünün var olan kopyasını yükler.</span><span class="sxs-lookup"><span data-stu-id="3dab9-140">If so, the runtime loads the existing copy of the image instead of mapping a new one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3dab9-141">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3dab9-141">Requirements</span></span>  
 <span data-ttu-id="3dab9-142">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3dab9-142">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3dab9-143">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3dab9-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3dab9-144">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="3dab9-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3dab9-145">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3dab9-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dab9-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3dab9-146">See also</span></span>

- [<span data-ttu-id="3dab9-147">ICLRAssemblyReferenceList Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3dab9-147">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="3dab9-148">IHostAssemblyManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3dab9-148">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="3dab9-149">IHostAssemblyStore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3dab9-149">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
