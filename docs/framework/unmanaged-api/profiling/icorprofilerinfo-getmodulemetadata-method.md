---
title: ICorProfilerInfo::GetModuleMetaData Metodu
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2e63cf698e41e70084c9b71bdf58d7ac60723d53
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782786"
---
# <a name="icorprofilerinfogetmodulemetadata-method"></a><span data-ttu-id="feb83-102">ICorProfilerInfo::GetModuleMetaData Metodu</span><span class="sxs-lookup"><span data-stu-id="feb83-102">ICorProfilerInfo::GetModuleMetaData Method</span></span>
<span data-ttu-id="feb83-103">Belirtilen modül için eşleşen bir meta veri arabirimi örneği alır.</span><span class="sxs-lookup"><span data-stu-id="feb83-103">Gets a metadata interface instance that maps to the specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="feb83-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="feb83-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleMetaData(  
    [in]  ModuleID moduleId,  
    [in]  DWORD    dwOpenFlags,  
    [in]  REFIID   riid,  
    [out] IUnknown **ppOut);  
```  
  
## <a name="parameters"></a><span data-ttu-id="feb83-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="feb83-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="feb83-106">[in] Arabirim örneğinin eşleştirilecek modül kimliği.</span><span class="sxs-lookup"><span data-stu-id="feb83-106">[in] The ID of the module to which the interface instance will be mapped.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="feb83-107">[in] Değerini [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) bildirim dosyalarını açmak için modu belirten sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="feb83-107">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration that specifies the mode for opening manifest files.</span></span> <span data-ttu-id="feb83-108">Yalnızca `ofRead`, `ofWrite` ve `ofNoTransform` BITS geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="feb83-108">Only the `ofRead`, `ofWrite` and `ofNoTransform` bits are valid.</span></span>  
  
 `riid`  
 <span data-ttu-id="feb83-109">[in] Başvuru Kimliği (GUID), örnek alınan meta verileri arabirimi.</span><span class="sxs-lookup"><span data-stu-id="feb83-109">[in] The reference ID (GUID) of the metadata interface whose instance will be retrieved.</span></span> <span data-ttu-id="feb83-110">Bkz: [meta veri arabirimleri](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) arabirimlerin listesi.</span><span class="sxs-lookup"><span data-stu-id="feb83-110">See [Metadata Interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) for a list of the interfaces.</span></span>  
  
 `ppOut`  
 <span data-ttu-id="feb83-111">[out] Meta veri arabirimi örneği adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="feb83-111">[out] A pointer to the address of the metadata interface instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="feb83-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="feb83-112">Remarks</span></span>  
 <span data-ttu-id="feb83-113">Meta veriler okuma/yazma modunda açılması için sorun, ancak bu programın daha yavaş meta verileri yürütülmesine neden olur, yapılan değişiklikler için derleyicinin oldukları gibi meta veriler iyileştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="feb83-113">You may ask for the metadata to be opened in read/write mode, but this will result in slower metadata execution of the program, because changes made to the metadata cannot be optimized as they were from the compiler.</span></span>  
  
 <span data-ttu-id="feb83-114">Bazı modüller (gibi kaynak Modülü) hiçbir meta veriler bulunur.</span><span class="sxs-lookup"><span data-stu-id="feb83-114">Some modules (such as resource modules) have no metadata.</span></span> <span data-ttu-id="feb83-115">Bu durumlarda `GetModuleMetaData` S_FALSE yanı sıra, bir null HRESULT değerini döndürecektir \*`ppOut`.</span><span class="sxs-lookup"><span data-stu-id="feb83-115">In those cases, `GetModuleMetaData` will return an HRESULT value of S_FALSE, and a null in \*`ppOut`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="feb83-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="feb83-116">Requirements</span></span>  
 <span data-ttu-id="feb83-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="feb83-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="feb83-118">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="feb83-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="feb83-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="feb83-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="feb83-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="feb83-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="feb83-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="feb83-121">See also</span></span>

- [<span data-ttu-id="feb83-122">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="feb83-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
