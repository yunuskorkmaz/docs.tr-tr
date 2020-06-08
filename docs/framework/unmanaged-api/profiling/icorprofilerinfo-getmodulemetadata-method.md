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
ms.openlocfilehash: 62b34128be99ce7750d45e6c19e26bef7fcc98c5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502957"
---
# <a name="icorprofilerinfogetmodulemetadata-method"></a><span data-ttu-id="df996-102">ICorProfilerInfo::GetModuleMetaData Metodu</span><span class="sxs-lookup"><span data-stu-id="df996-102">ICorProfilerInfo::GetModuleMetaData Method</span></span>
<span data-ttu-id="df996-103">Belirtilen modülle eşlenen meta veri arabirimi örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="df996-103">Gets a metadata interface instance that maps to the specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df996-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="df996-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleMetaData(  
    [in]  ModuleID moduleId,  
    [in]  DWORD    dwOpenFlags,  
    [in]  REFIID   riid,  
    [out] IUnknown **ppOut);  
```  
  
## <a name="parameters"></a><span data-ttu-id="df996-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="df996-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="df996-106">'ndaki Arabirim örneğinin eşleştirilabileceği modülün KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="df996-106">[in] The ID of the module to which the interface instance will be mapped.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="df996-107">'ndaki Bildirim dosyalarını açma modunu belirten [CorOpenFlags](../metadata/coropenflags-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="df996-107">[in] A value of the [CorOpenFlags](../metadata/coropenflags-enumeration.md) enumeration that specifies the mode for opening manifest files.</span></span> <span data-ttu-id="df996-108">Yalnızca `ofRead` `ofWrite` ve `ofNoTransform` bitleri geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="df996-108">Only the `ofRead`, `ofWrite` and `ofNoTransform` bits are valid.</span></span>  
  
 `riid`  
 <span data-ttu-id="df996-109">'ndaki Örneği alınacak olan meta veri arabiriminin başvuru KIMLIĞI (GUID).</span><span class="sxs-lookup"><span data-stu-id="df996-109">[in] The reference ID (GUID) of the metadata interface whose instance will be retrieved.</span></span> <span data-ttu-id="df996-110">Arabirimlerin listesi için bkz. [meta veri arabirimleri](../metadata/metadata-interfaces.md) .</span><span class="sxs-lookup"><span data-stu-id="df996-110">See [Metadata Interfaces](../metadata/metadata-interfaces.md) for a list of the interfaces.</span></span>  
  
 `ppOut`  
 <span data-ttu-id="df996-111">dışı Meta veri arabirimi örneğinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="df996-111">[out] A pointer to the address of the metadata interface instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df996-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="df996-112">Remarks</span></span>  
 <span data-ttu-id="df996-113">Meta verilerin okuma/yazma modunda açılmasını isteyebilirsiniz, ancak meta verilerde yapılan değişiklikler derleyicisinden oldukları için en iyi duruma getirilmediğinden, bu, programın daha yavaş yürütülmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="df996-113">You may ask for the metadata to be opened in read/write mode, but this will result in slower metadata execution of the program, because changes made to the metadata cannot be optimized as they were from the compiler.</span></span>  
  
 <span data-ttu-id="df996-114">Bazı modüller (örneğin, kaynak modülleri) meta veri içermez.</span><span class="sxs-lookup"><span data-stu-id="df996-114">Some modules (such as resource modules) have no metadata.</span></span> <span data-ttu-id="df996-115">Bu durumlarda, bir `GetModuleMetaData` HRESULT değeri olan S_FALSE döndürür ve \* içinde null değeri döndürülür `ppOut` .</span><span class="sxs-lookup"><span data-stu-id="df996-115">In those cases, `GetModuleMetaData` will return an HRESULT value of S_FALSE, and a null in \*`ppOut`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df996-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="df996-116">Requirements</span></span>  
 <span data-ttu-id="df996-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df996-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df996-118">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="df996-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="df996-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="df996-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df996-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df996-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df996-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="df996-121">See also</span></span>

- [<span data-ttu-id="df996-122">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="df996-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
