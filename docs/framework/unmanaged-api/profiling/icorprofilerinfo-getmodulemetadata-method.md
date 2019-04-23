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
ms.openlocfilehash: 89a2424548bb577e3580d6eaa72f61e5cf9ccc7d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59111221"
---
# <a name="icorprofilerinfogetmodulemetadata-method"></a><span data-ttu-id="5d895-102">ICorProfilerInfo::GetModuleMetaData Metodu</span><span class="sxs-lookup"><span data-stu-id="5d895-102">ICorProfilerInfo::GetModuleMetaData Method</span></span>
<span data-ttu-id="5d895-103">Belirtilen modül için eşleşen bir meta veri arabirimi örneği alır.</span><span class="sxs-lookup"><span data-stu-id="5d895-103">Gets a metadata interface instance that maps to the specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d895-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5d895-104">Syntax</span></span>  
  
```  
HRESULT GetModuleMetaData(  
    [in]  ModuleID moduleId,  
    [in]  DWORD    dwOpenFlags,  
    [in]  REFIID   riid,  
    [out] IUnknown **ppOut);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d895-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5d895-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="5d895-106">[in] Arabirim örneğinin eşleştirilecek modül kimliği.</span><span class="sxs-lookup"><span data-stu-id="5d895-106">[in] The ID of the module to which the interface instance will be mapped.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="5d895-107">[in] Değerini [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) bildirim dosyalarını açmak için modu belirten sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="5d895-107">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration that specifies the mode for opening manifest files.</span></span> <span data-ttu-id="5d895-108">Yalnızca `ofRead`, `ofWrite` ve `ofNoTransform` BITS geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5d895-108">Only the `ofRead`, `ofWrite` and `ofNoTransform` bits are valid.</span></span>  
  
 `riid`  
 <span data-ttu-id="5d895-109">[in] Başvuru Kimliği (GUID), örnek alınan meta verileri arabirimi.</span><span class="sxs-lookup"><span data-stu-id="5d895-109">[in] The reference ID (GUID) of the metadata interface whose instance will be retrieved.</span></span> <span data-ttu-id="5d895-110">Bkz: [meta veri arabirimleri](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) arabirimlerin listesi.</span><span class="sxs-lookup"><span data-stu-id="5d895-110">See [Metadata Interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) for a list of the interfaces.</span></span>  
  
 `ppOut`  
 <span data-ttu-id="5d895-111">[out] Meta veri arabirimi örneği adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5d895-111">[out] A pointer to the address of the metadata interface instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d895-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5d895-112">Remarks</span></span>  
 <span data-ttu-id="5d895-113">Meta veriler okuma/yazma modunda açılması için sorun, ancak bu programın daha yavaş meta verileri yürütülmesine neden olur, yapılan değişiklikler için derleyicinin oldukları gibi meta veriler iyileştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="5d895-113">You may ask for the metadata to be opened in read/write mode, but this will result in slower metadata execution of the program, because changes made to the metadata cannot be optimized as they were from the compiler.</span></span>  
  
 <span data-ttu-id="5d895-114">Bazı modüller (gibi kaynak Modülü) hiçbir meta veriler bulunur.</span><span class="sxs-lookup"><span data-stu-id="5d895-114">Some modules (such as resource modules) have no metadata.</span></span> <span data-ttu-id="5d895-115">Bu durumlarda `GetModuleMetaData` S_FALSE yanı sıra, bir null HRESULT değerini döndürecektir \*`ppOut`.</span><span class="sxs-lookup"><span data-stu-id="5d895-115">In those cases, `GetModuleMetaData` will return an HRESULT value of S_FALSE, and a null in \*`ppOut`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d895-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5d895-116">Requirements</span></span>  
 <span data-ttu-id="5d895-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d895-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d895-118">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5d895-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5d895-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5d895-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d895-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d895-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d895-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d895-121">See also</span></span>

- [<span data-ttu-id="5d895-122">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5d895-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
