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
ms.openlocfilehash: c7bf8e3ebedb17a4536b604909434c3e004fc828
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439831"
---
# <a name="icorprofilerinfogetmodulemetadata-method"></a><span data-ttu-id="d9408-102">ICorProfilerInfo::GetModuleMetaData Metodu</span><span class="sxs-lookup"><span data-stu-id="d9408-102">ICorProfilerInfo::GetModuleMetaData Method</span></span>
<span data-ttu-id="d9408-103">Belirtilen modülle eşlenen meta veri arabirimi örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="d9408-103">Gets a metadata interface instance that maps to the specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9408-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d9408-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleMetaData(  
    [in]  ModuleID moduleId,  
    [in]  DWORD    dwOpenFlags,  
    [in]  REFIID   riid,  
    [out] IUnknown **ppOut);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9408-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d9408-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="d9408-106">'ndaki Arabirim örneğinin eşleştirilabileceği modülün KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="d9408-106">[in] The ID of the module to which the interface instance will be mapped.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="d9408-107">'ndaki Bildirim dosyalarını açma modunu belirten [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="d9408-107">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration that specifies the mode for opening manifest files.</span></span> <span data-ttu-id="d9408-108">Yalnızca `ofRead`, `ofWrite` ve `ofNoTransform` bitleri geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d9408-108">Only the `ofRead`, `ofWrite` and `ofNoTransform` bits are valid.</span></span>  
  
 `riid`  
 <span data-ttu-id="d9408-109">'ndaki Örneği alınacak olan meta veri arabiriminin başvuru KIMLIĞI (GUID).</span><span class="sxs-lookup"><span data-stu-id="d9408-109">[in] The reference ID (GUID) of the metadata interface whose instance will be retrieved.</span></span> <span data-ttu-id="d9408-110">Arabirimlerin listesi için bkz. [meta veri arabirimleri](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) .</span><span class="sxs-lookup"><span data-stu-id="d9408-110">See [Metadata Interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) for a list of the interfaces.</span></span>  
  
 `ppOut`  
 <span data-ttu-id="d9408-111">dışı Meta veri arabirimi örneğinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d9408-111">[out] A pointer to the address of the metadata interface instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9408-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d9408-112">Remarks</span></span>  
 <span data-ttu-id="d9408-113">Meta verilerin okuma/yazma modunda açılmasını isteyebilirsiniz, ancak meta verilerde yapılan değişiklikler derleyicisinden oldukları için en iyi duruma getirilmediğinden, bu, programın daha yavaş yürütülmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="d9408-113">You may ask for the metadata to be opened in read/write mode, but this will result in slower metadata execution of the program, because changes made to the metadata cannot be optimized as they were from the compiler.</span></span>  
  
 <span data-ttu-id="d9408-114">Bazı modüller (örneğin, kaynak modülleri) meta veri içermez.</span><span class="sxs-lookup"><span data-stu-id="d9408-114">Some modules (such as resource modules) have no metadata.</span></span> <span data-ttu-id="d9408-115">Bu durumlarda `GetModuleMetaData` bir HRESULT değeri S_FALSE ve \*`ppOut`null değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="d9408-115">In those cases, `GetModuleMetaData` will return an HRESULT value of S_FALSE, and a null in \*`ppOut`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9408-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d9408-116">Requirements</span></span>  
 <span data-ttu-id="d9408-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9408-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9408-118">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d9408-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d9408-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d9408-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d9408-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9408-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9408-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9408-121">See also</span></span>

- [<span data-ttu-id="d9408-122">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d9408-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
