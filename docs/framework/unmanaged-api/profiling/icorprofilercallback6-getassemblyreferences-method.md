---
title: ICorProfilerCallback6::GetAssemblyReferences Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorProfilerCallback6.GetAssemblyReferences
api_location:
- mscorwks.dll
- corprof.idl
api_type: COM
ms.assetid: 8b391afb-d79f-41bd-94ce-43ce62c6b5fc
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bc2e80d6d8207a869d43beb46cc9448bdd86dfec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback6getassemblyreferences-method"></a><span data-ttu-id="48766-102">ICorProfilerCallback6::GetAssemblyReferences Metodu</span><span class="sxs-lookup"><span data-stu-id="48766-102">ICorProfilerCallback6::GetAssemblyReferences Method</span></span>
<span data-ttu-id="48766-103">[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="48766-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="48766-104">Profil Oluşturucu ortak dil çalışma zamanı bir derleme başvurusu kapatma ilerlemesi gerçekleştirdiğinde bütünleştirilmiş bir çok erkenden aşama, yüklüyor olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="48766-104">Notifies the profiler that an assembly is in a very early loading stage, when the common language runtime performs an assembly reference closure walk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48766-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="48766-105">Syntax</span></span>  
  
```cpp
HRESULT GetAssemblyReferences(        [in, string] const WCHAR* wszAssemblyPath,  
        [in] ICorProfilerAssemblyReferenceProvider* pAsmRefProvider  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="48766-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="48766-106">Parameters</span></span>  
 `wszAssemblyPath`  
 <span data-ttu-id="48766-107">[in] Meta veri değiştirilecek derlemenin adını ve yolunu.</span><span class="sxs-lookup"><span data-stu-id="48766-107">[in] The path and name of the assembly whose metadata will be modified.</span></span>  
  
 `pAsmRefProvider`  
 <span data-ttu-id="48766-108">[in] Adresine bir işaretçi bir [Icorprofilerassemblyreferenceprovider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) eklemek için derlemeyi belirtir arabirimi başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="48766-108">[in] A pointer to the address of an [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) interface that specifies the assembly references to add.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="48766-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="48766-109">Return Value</span></span>  
 <span data-ttu-id="48766-110">Bu geri dönüş değerleri yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="48766-110">Return values from this callback are ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48766-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="48766-111">Remarks</span></span>  
 <span data-ttu-id="48766-112">Bu geri çağırma ayarlanmasıyla denetlenir [COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) çağrılırken olay maskesi bayrağı [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="48766-112">This callback is controlled by setting the [COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) event mask flag when calling the [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method.</span></span> <span data-ttu-id="48766-113">Profil Oluşturucu için kaydettiğinde [Icorprofilercallback6::getassemblyreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) geri çağırma yöntemi, çalışma zamanı geçirir, bir işaretçi birlikte yüklenecek derlemenin adını ve yolunu bir [ Icorprofilerassemblyreferenceprovider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) bu yönteme arabirimi nesnesi.</span><span class="sxs-lookup"><span data-stu-id="48766-113">If the profiler registers for the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback method, the runtime passes the path and name of the assembly to be loaded, along with a pointer to an [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) interface object to that method.</span></span> <span data-ttu-id="48766-114">Profil Oluşturucu sonra çağırabilirsiniz [Icorprofilerassemblyreferenceprovider::addassemblyreference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) yöntemi ile bir `COR_PRF_ASSEMBLY_REFERENCE_INFO` nesne planları belirtilen derlemesinden başvurmak için her hedef derleme için `GetAssemblyReferences` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="48766-114">The profiler can then call the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method with a `COR_PRF_ASSEMBLY_REFERENCE_INFO` object for each target assembly it plans to reference from the assembly specified in the `GetAssemblyReferences` callback.</span></span>  
  
 <span data-ttu-id="48766-115">Kullanım `GetAssemblyReferences` yalnızca derleme başvurularını eklemek için bir derlemenin meta verilerini değiştirmek profil oluşturucu varsa, geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="48766-115">Use the `GetAssemblyReferences` callback only if the profiler has to modify an assembly's metadata to add assembly references.</span></span> <span data-ttu-id="48766-116">(Ancak gerçek bir derlemenin meta verilerini değiştirilmesini yapılır Not [Icorprofilercallback::moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)geri çağırma yöntemi.) Profil Oluşturucu uygulamalıdır `GetAssemblyReferences` modülü yüklendiğinde derleme başvurularını eklenecek ortak dil çalışma zamanı (CLR) bilgilendirmek için geri çağırma yöntemi.</span><span class="sxs-lookup"><span data-stu-id="48766-116">(But note that the actual modification of an assembly's metadata is done in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)callback method.) The profiler should implement the `GetAssemblyReferences` callback method to inform the common language runtime (CLR) that assembly references will be added when the module has been loaded.</span></span>  <span data-ttu-id="48766-117">Bu meta verileri derleme başvurularını daha sonra değiştirmek profil oluşturucu planları rağmen CLR tarafından bu erken aşamada derleme paylaşım kararlara geçerli kalmasını sağlamaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="48766-117">This helps ensure that assembly sharing decisions made by the CLR during this early stage remain valid although the profiler plans to modify the metadata assembly references later.</span></span>  <span data-ttu-id="48766-118">Bu meta veri değişiklikleri hangi Profil Oluşturucusu'nda neden bazı örnekleri önleyebilirsiniz bir `SECURITY_E_INCOMPATIBLE_SHARE` hata.</span><span class="sxs-lookup"><span data-stu-id="48766-118">This can avoid some instances in which profiler metadata modifications cause an `SECURITY_E_INCOMPATIBLE_SHARE` error.</span></span>  
  
 <span data-ttu-id="48766-119">Profil Oluşturucu kullanan [Icorprofilerassemblyreferenceprovider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) CLR derleme başvurusu kapatma walker derleme başvurularını eklemek için bu yöntem tarafından sağlanan nesne.</span><span class="sxs-lookup"><span data-stu-id="48766-119">The profiler uses the [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) object provided by this method to add assembly references to the CLR assembly reference closure walker.</span></span>  <span data-ttu-id="48766-120">[Icorprofilerassemblyreferenceprovider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) nesne kullanılmalıdır yalnızca içinde bu geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="48766-120">The [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) object should be used only from within this callback.</span></span> <span data-ttu-id="48766-121">Çağrılar [Icorprofilerassemblyreferenceprovider::addassemblyreference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) değiştirilmiş meta verilerde, ancak yalnızca değiştirilen derleme başvurusu kapatma ilerlemesi bu geri çağırma yöntemi neden yoktur.</span><span class="sxs-lookup"><span data-stu-id="48766-121">Calls to the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method from this callback don't result in modified metadata, but only in a modified assembly reference closure walk.</span></span> <span data-ttu-id="48766-122">Profil Oluşturucu hala kullanmak zorunda olacaksınız bir [Imetadataassemblyemit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) açıkça derleme başvurularını içinden eklemek için nesne [Icorprofilercallback::moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) başvuru için geri çağırma derleme, bunu uygulayan olsa bile `GetAssemblyReferences` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="48766-122">The profiler will still have to use an [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) object to explicitly add assembly references from within the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback for the referencing assembly, even if it implements the `GetAssemblyReferences` callback.</span></span>  
  
 <span data-ttu-id="48766-123">Profil Oluşturucu için aynı bütünleştirilmiş kodda bu geri çağırma yinelenen çağrılarını almak hazırlıklı olmalıdır ve her tür yinelenen çağrısı için aynı kullanmalıdır (aynı dizi yaparak [Icorprofilerassemblyreferenceprovider:: AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) çağrıları).</span><span class="sxs-lookup"><span data-stu-id="48766-123">The profiler should be prepared to receive duplicate calls to this callback for the same assembly, and should respond identically for each such duplicate call (by making the same set of [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) calls).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48766-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="48766-124">Requirements</span></span>  
 <span data-ttu-id="48766-125">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48766-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48766-126">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="48766-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="48766-127">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="48766-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48766-128">**.NET framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48766-128">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48766-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="48766-129">See Also</span></span>  
 [<span data-ttu-id="48766-130">ICorProfilerCallback6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="48766-130">ICorProfilerCallback6 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md)  
 [<span data-ttu-id="48766-131">ModuleLoadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="48766-131">ModuleLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)  
 [<span data-ttu-id="48766-132">COR_PRF_ASSEMBLY_REFERENCE_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="48766-132">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)  
 [<span data-ttu-id="48766-133">ICorProfilerAssemblyReferenceProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="48766-133">ICorProfilerAssemblyReferenceProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)
