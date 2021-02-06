---
description: ': ICorProfilerInfo:: GetModuleMetaData metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: ff0fb0563b041fcb3cf63438874724c8236d6081
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647186"
---
# <a name="icorprofilerinfogetmodulemetadata-method"></a><span data-ttu-id="9cb3f-103">ICorProfilerInfo::GetModuleMetaData Metodu</span><span class="sxs-lookup"><span data-stu-id="9cb3f-103">ICorProfilerInfo::GetModuleMetaData Method</span></span>

<span data-ttu-id="9cb3f-104">Belirtilen modülle eşlenen meta veri arabirimi örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="9cb3f-104">Gets a metadata interface instance that maps to the specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cb3f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9cb3f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleMetaData(  
    [in]  ModuleID moduleId,  
    [in]  DWORD    dwOpenFlags,  
    [in]  REFIID   riid,  
    [out] IUnknown **ppOut);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9cb3f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9cb3f-106">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="9cb3f-107">'ndaki Arabirim örneğinin eşleştirilabileceği modülün KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="9cb3f-107">[in] The ID of the module to which the interface instance will be mapped.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="9cb3f-108">'ndaki Bildirim dosyalarını açma modunu belirten [CorOpenFlags](../metadata/coropenflags-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="9cb3f-108">[in] A value of the [CorOpenFlags](../metadata/coropenflags-enumeration.md) enumeration that specifies the mode for opening manifest files.</span></span> <span data-ttu-id="9cb3f-109">Yalnızca `ofRead` `ofWrite` ve `ofNoTransform` bitleri geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="9cb3f-109">Only the `ofRead`, `ofWrite` and `ofNoTransform` bits are valid.</span></span>  
  
 `riid`  
 <span data-ttu-id="9cb3f-110">'ndaki Örneği alınacak olan meta veri arabiriminin başvuru KIMLIĞI (GUID).</span><span class="sxs-lookup"><span data-stu-id="9cb3f-110">[in] The reference ID (GUID) of the metadata interface whose instance will be retrieved.</span></span> <span data-ttu-id="9cb3f-111">Arabirimlerin listesi için bkz. [meta veri arabirimleri](../metadata/metadata-interfaces.md) .</span><span class="sxs-lookup"><span data-stu-id="9cb3f-111">See [Metadata Interfaces](../metadata/metadata-interfaces.md) for a list of the interfaces.</span></span>  
  
 `ppOut`  
 <span data-ttu-id="9cb3f-112">dışı Meta veri arabirimi örneğinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9cb3f-112">[out] A pointer to the address of the metadata interface instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9cb3f-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9cb3f-113">Remarks</span></span>  

 <span data-ttu-id="9cb3f-114">Meta verilerin okuma/yazma modunda açılmasını isteyebilirsiniz, ancak meta verilerde yapılan değişiklikler derleyicisinden oldukları için en iyi duruma getirilmediğinden, bu, programın daha yavaş yürütülmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="9cb3f-114">You may ask for the metadata to be opened in read/write mode, but this will result in slower metadata execution of the program, because changes made to the metadata cannot be optimized as they were from the compiler.</span></span>  
  
 <span data-ttu-id="9cb3f-115">Bazı modüller (örneğin, kaynak modülleri) meta veri içermez.</span><span class="sxs-lookup"><span data-stu-id="9cb3f-115">Some modules (such as resource modules) have no metadata.</span></span> <span data-ttu-id="9cb3f-116">Bu durumlarda, bir `GetModuleMetaData` HRESULT değeri olan S_FALSE döndürür ve \* içinde null değeri döndürülür `ppOut` .</span><span class="sxs-lookup"><span data-stu-id="9cb3f-116">In those cases, `GetModuleMetaData` will return an HRESULT value of S_FALSE, and a null in \*`ppOut`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9cb3f-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9cb3f-117">Requirements</span></span>  

 <span data-ttu-id="9cb3f-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9cb3f-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9cb3f-119">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="9cb3f-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9cb3f-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9cb3f-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9cb3f-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9cb3f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cb3f-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9cb3f-122">See also</span></span>

- [<span data-ttu-id="9cb3f-123">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9cb3f-123">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
