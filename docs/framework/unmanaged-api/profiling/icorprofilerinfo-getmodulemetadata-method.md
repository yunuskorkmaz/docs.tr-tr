---
title: ICorProfilerInfo::GetModuleMetaData Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerInfo.GetModuleMetaData
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetModuleMetaData
helpviewer_keywords:
- GetModuleMetaData method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleMetaData method [.NET Framework profiling]
ms.assetid: 7a439d92-348a-44dd-b60f-cad7cba56379
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6ad52460bcd6eb320e970cd0ce2078f2e93df353
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetmodulemetadata-method"></a><span data-ttu-id="64b8d-102">ICorProfilerInfo::GetModuleMetaData Metodu</span><span class="sxs-lookup"><span data-stu-id="64b8d-102">ICorProfilerInfo::GetModuleMetaData Method</span></span>
<span data-ttu-id="64b8d-103">Belirtilen modül eşleyen bir meta veri arabirimi örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="64b8d-103">Gets a metadata interface instance that maps to the specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64b8d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="64b8d-104">Syntax</span></span>  
  
```  
HRESULT GetModuleMetaData(  
    [in]  ModuleID moduleId,  
    [in]  DWORD    dwOpenFlags,  
    [in]  REFIID   riid,  
    [out] IUnknown **ppOut);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="64b8d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="64b8d-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="64b8d-106">[in] Arabirim örneğinin eşlenecek modül kimliği.</span><span class="sxs-lookup"><span data-stu-id="64b8d-106">[in] The ID of the module to which the interface instance will be mapped.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="64b8d-107">[in] Değerini [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) bildirim dosyalarını açmak için modu belirtir numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="64b8d-107">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration that specifies the mode for opening manifest files.</span></span> <span data-ttu-id="64b8d-108">Yalnızca `ofRead`, `ofWrite` ve `ofNoTransform` BITS geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="64b8d-108">Only the `ofRead`, `ofWrite` and `ofNoTransform` bits are valid.</span></span>  
  
 `riid`  
 <span data-ttu-id="64b8d-109">[in] Başvuru Kimliği (GUID) meta veri arabiriminin örneği alınır.</span><span class="sxs-lookup"><span data-stu-id="64b8d-109">[in] The reference ID (GUID) of the metadata interface whose instance will be retrieved.</span></span> <span data-ttu-id="64b8d-110">Bkz: [meta veri arabirimleri](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) arabirimler listesi.</span><span class="sxs-lookup"><span data-stu-id="64b8d-110">See [Metadata Interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) for a list of the interfaces.</span></span>  
  
 `ppOut`  
 <span data-ttu-id="64b8d-111">[out] Meta veri arabirim örneğinin adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="64b8d-111">[out] A pointer to the address of the metadata interface instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64b8d-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="64b8d-112">Remarks</span></span>  
 <span data-ttu-id="64b8d-113">Okuma/yazma modunda açılması meta veriler için isteyebilir, ancak bu programın daha yavaş meta veri yürütme neden olacak, derleyiciden oldukları gibi yapılan değişiklikler için meta veriler iyileştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="64b8d-113">You may ask for the metadata to be opened in read/write mode, but this will result in slower metadata execution of the program, because changes made to the metadata cannot be optimized as they were from the compiler.</span></span>  
  
 <span data-ttu-id="64b8d-114">Bazı modüller (örneğin, kaynak modüller) hiçbir meta verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="64b8d-114">Some modules (such as resource modules) have no metadata.</span></span> <span data-ttu-id="64b8d-115">Bu durumlarda, `GetModuleMetaData` S_FALSE ve null olarak HRESULT değerini döndürür \*`ppOut`.</span><span class="sxs-lookup"><span data-stu-id="64b8d-115">In those cases, `GetModuleMetaData` will return an HRESULT value of S_FALSE, and a null in \*`ppOut`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64b8d-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="64b8d-116">Requirements</span></span>  
 <span data-ttu-id="64b8d-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64b8d-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64b8d-118">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="64b8d-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="64b8d-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="64b8d-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64b8d-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64b8d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64b8d-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="64b8d-121">See Also</span></span>  
 [<span data-ttu-id="64b8d-122">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="64b8d-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
