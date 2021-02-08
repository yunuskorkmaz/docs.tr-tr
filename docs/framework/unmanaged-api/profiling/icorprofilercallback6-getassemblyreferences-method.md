---
description: 'Şu konuda daha fazla bilgi edinin: ICorProfilerCallback6:: GetAssemblyReferences Yöntemi'
title: ICorProfilerCallback6::GetAssemblyReferences Yöntemi
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerCallback6.GetAssemblyReferences
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: 8b391afb-d79f-41bd-94ce-43ce62c6b5fc
topic_type:
- apiref
ms.openlocfilehash: 27c2b5e0ed935501de551bac32b6d229d5c59f79
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788650"
---
# <a name="icorprofilercallback6getassemblyreferences-method"></a><span data-ttu-id="6f3de-103">ICorProfilerCallback6::GetAssemblyReferences Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6f3de-103">ICorProfilerCallback6::GetAssemblyReferences Method</span></span>

<span data-ttu-id="6f3de-104">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="6f3de-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="6f3de-105">Profil oluşturucuyu bir derlemenin çok erken yükleme aşamasında olduğunu, ortak dil çalışma zamanı bir derleme başvurusu kapatma ilerlemesi gerçekleştirdiğinde bildirir.</span><span class="sxs-lookup"><span data-stu-id="6f3de-105">Notifies the profiler that an assembly is in a very early loading stage, when the common language runtime performs an assembly reference closure walk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f3de-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6f3de-106">Syntax</span></span>  
  
```cpp
HRESULT GetAssemblyReferences(        [in, string] const WCHAR* wszAssemblyPath,  
        [in] ICorProfilerAssemblyReferenceProvider* pAsmRefProvider  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f3de-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6f3de-107">Parameters</span></span>  

 `wszAssemblyPath`  
 <span data-ttu-id="6f3de-108">'ndaki Meta verileri değiştirilecek olan derlemenin yolu ve adı.</span><span class="sxs-lookup"><span data-stu-id="6f3de-108">[in] The path and name of the assembly whose metadata will be modified.</span></span>  
  
 `pAsmRefProvider`  
 <span data-ttu-id="6f3de-109">'ndaki Eklenecek derleme başvurularını belirten [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) arabiriminin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6f3de-109">[in] A pointer to the address of an [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) interface that specifies the assembly references to add.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6f3de-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6f3de-110">Return Value</span></span>  

 <span data-ttu-id="6f3de-111">Bu geri aramadan döndürülen değerler yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="6f3de-111">Return values from this callback are ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f3de-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6f3de-112">Remarks</span></span>  

 <span data-ttu-id="6f3de-113">Bu geri çağırma, [ICorProfilerCallback5:: SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) yöntemi çağrılırken [COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES](cor-prf-high-monitor-enumeration.md) Event Mask bayrağı ayarlanarak denetlenir.</span><span class="sxs-lookup"><span data-stu-id="6f3de-113">This callback is controlled by setting the [COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES](cor-prf-high-monitor-enumeration.md) event mask flag when calling the [ICorProfilerCallback5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method.</span></span> <span data-ttu-id="6f3de-114">Profil Oluşturucu [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) geri çağırma metoduna kaydolduktan sonra, çalışma zamanı yüklenecek derlemenin yolunu ve adını, bu yönteme bir [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) arabirim nesnesine yönelik bir işaretçi ile geçirir.</span><span class="sxs-lookup"><span data-stu-id="6f3de-114">If the profiler registers for the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback method, the runtime passes the path and name of the assembly to be loaded, along with a pointer to an [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) interface object to that method.</span></span> <span data-ttu-id="6f3de-115">Profil Oluşturucu daha sonra [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) metodunu, `COR_PRF_ASSEMBLY_REFERENCE_INFO` `GetAssemblyReferences` geri çağırmada belirtilen derlemeden başvuruyu planlıyor olan her hedef derleme için bir nesneyle çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="6f3de-115">The profiler can then call the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method with a `COR_PRF_ASSEMBLY_REFERENCE_INFO` object for each target assembly it plans to reference from the assembly specified in the `GetAssemblyReferences` callback.</span></span>  
  
 <span data-ttu-id="6f3de-116">`GetAssemblyReferences`Geri çağırma işlemini yalnızca profil oluşturucunun derleme başvurularını eklemek için bir derlemenin meta verilerini değiştirmesi gerekiyorsa kullanın.</span><span class="sxs-lookup"><span data-stu-id="6f3de-116">Use the `GetAssemblyReferences` callback only if the profiler has to modify an assembly's metadata to add assembly references.</span></span> <span data-ttu-id="6f3de-117">(Ancak, bir derlemenin meta verisinin gerçek değişiminin [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md)geri çağırma yönteminde yapıldığını unutmayın.) Profil Oluşturucu, `GetAssemblyReferences` Modül yüklendiğinde derleme başvurularının ekleneceği ortak dil çalışma zamanını (CLR) bilgilendirmek için geri çağırma yöntemini uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="6f3de-117">(But note that the actual modification of an assembly's metadata is done in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md)callback method.) The profiler should implement the `GetAssemblyReferences` callback method to inform the common language runtime (CLR) that assembly references will be added when the module has been loaded.</span></span>  <span data-ttu-id="6f3de-118">Bu, bu erken aşamada CLR tarafından yapılan derleme paylaşımı kararlarının, daha sonra meta veri derleme başvurularını değiştirme planları olmasına rağmen geçerli olmaya devam etmesine yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="6f3de-118">This helps ensure that assembly sharing decisions made by the CLR during this early stage remain valid although the profiler plans to modify the metadata assembly references later.</span></span>  <span data-ttu-id="6f3de-119">Bu, Profil Oluşturucu meta verileri değişikliklerinin hataya neden olduğu bazı örneklerden kaçınabilir `SECURITY_E_INCOMPATIBLE_SHARE` .</span><span class="sxs-lookup"><span data-stu-id="6f3de-119">This can avoid some instances in which profiler metadata modifications cause an `SECURITY_E_INCOMPATIBLE_SHARE` error.</span></span>  
  
 <span data-ttu-id="6f3de-120">Profil Oluşturucu, CLR derleme başvuru kapanışı denetçisi 'ne derleme başvuruları eklemek için bu yöntem tarafından sunulan [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) nesnesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="6f3de-120">The profiler uses the [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) object provided by this method to add assembly references to the CLR assembly reference closure walker.</span></span>  <span data-ttu-id="6f3de-121">[ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) nesnesi yalnızca bu geri çağırma içinden kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6f3de-121">The [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) object should be used only from within this callback.</span></span> <span data-ttu-id="6f3de-122">Bu geri aramadan [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) metoduna yapılan çağrılar, değiştirilen meta veriler ile sonuçlanmaz, ancak yalnızca değiştirilmiş bir derleme başvurusu kapatma ilerinde.</span><span class="sxs-lookup"><span data-stu-id="6f3de-122">Calls to the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method from this callback don't result in modified metadata, but only in a modified assembly reference closure walk.</span></span> <span data-ttu-id="6f3de-123">Profil oluşturucunun, geri çağırma işlemini uyguladığından bile, başvurulan derleme için [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) geri çağrısının içinden derleme başvurularını açıkça eklemesi Için bir [IMetaDataAssemblyEmit](../metadata/imetadataassemblyemit-interface.md) nesnesi kullanması gerekecektir `GetAssemblyReferences` .</span><span class="sxs-lookup"><span data-stu-id="6f3de-123">The profiler will still have to use an [IMetaDataAssemblyEmit](../metadata/imetadataassemblyemit-interface.md) object to explicitly add assembly references from within the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback for the referencing assembly, even if it implements the `GetAssemblyReferences` callback.</span></span>  
  
 <span data-ttu-id="6f3de-124">Profil Oluşturucu aynı derleme için bu geri çağrıya yinelenen çağrılar alacak şekilde hazırlanmalı ve her bir yinelenen çağrı için aynı şekilde yanıt vermelidir (aynı [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) çağrılarının kümesini yaparak).</span><span class="sxs-lookup"><span data-stu-id="6f3de-124">The profiler should be prepared to receive duplicate calls to this callback for the same assembly, and should respond identically for each such duplicate call (by making the same set of [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) calls).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f3de-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6f3de-125">Requirements</span></span>  

 <span data-ttu-id="6f3de-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f3de-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f3de-127">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="6f3de-127">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6f3de-128">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6f3de-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f3de-129">**.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f3de-129">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f3de-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f3de-130">See also</span></span>

- [<span data-ttu-id="6f3de-131">ICorProfilerCallback6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6f3de-131">ICorProfilerCallback6 Interface</span></span>](icorprofilercallback6-interface.md)
- [<span data-ttu-id="6f3de-132">ModuleLoadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6f3de-132">ModuleLoadFinished Method</span></span>](icorprofilercallback-moduleloadfinished-method.md)
- [<span data-ttu-id="6f3de-133">COR_PRF_ASSEMBLY_REFERENCE_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="6f3de-133">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>](cor-prf-assembly-reference-info-structure.md)
- [<span data-ttu-id="6f3de-134">ICorProfilerAssemblyReferenceProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6f3de-134">ICorProfilerAssemblyReferenceProvider Interface</span></span>](icorprofilerassemblyreferenceprovider-interface.md)
