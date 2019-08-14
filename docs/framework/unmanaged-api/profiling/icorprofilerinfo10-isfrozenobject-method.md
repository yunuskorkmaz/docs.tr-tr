---
title: 'ICorProfilerInfo10:: ısfrozenobject'
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.IsFrozenObject
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 05f25d8fb61a16f41a82a987529017db6a687740
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973746"
---
# <a name="icorprofilerinfo10isfrozenobject-method"></a><span data-ttu-id="f33a7-102">ICorProfilerInfo10:: ısfrozenobject yöntemi</span><span class="sxs-lookup"><span data-stu-id="f33a7-102">ICorProfilerInfo10::IsFrozenObject Method</span></span>
  
 <span data-ttu-id="f33a7-103">ObjectID verildiğinde, nesnenin salt okunurdur bir kesimde olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="f33a7-103">Given an ObjectID, determines whether the object is in a read-only segment.</span></span>   
  
## <a name="syntax"></a><span data-ttu-id="f33a7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f33a7-104">Syntax</span></span>  
  
```cpp
HRESULT IsFrozenObject( [in]  ObjectID objectId,
                        [out] BOOL *pbFrozen);
```  
  
#### <a name="parameters"></a><span data-ttu-id="f33a7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f33a7-105">Parameters</span></span>  
 
 `objectId` \
 <span data-ttu-id="f33a7-106">'ndaki İncelenecek nesne.</span><span class="sxs-lookup"><span data-stu-id="f33a7-106">[in] The object to examine.</span></span>

 `pbFrozen` \
 <span data-ttu-id="f33a7-107">dışı Nesnenin salt okunurdur bir kesimde olup olmadığını gösterir.`BOOL`</span><span class="sxs-lookup"><span data-stu-id="f33a7-107">[out] A `BOOL` indicating if the object is in a read-only segment.</span></span>

## <a name="requirements"></a><span data-ttu-id="f33a7-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f33a7-108">Requirements</span></span>  
 <span data-ttu-id="f33a7-109">**Platform** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="f33a7-109">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>  
  
 <span data-ttu-id="f33a7-110">**Üst bilgi** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f33a7-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f33a7-111">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f33a7-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f33a7-112">**.NET sürümleri:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f33a7-112">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="f33a7-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f33a7-113">See also</span></span>
- [<span data-ttu-id="f33a7-114">ICorProfilerInfo10 arabirimi</span><span class="sxs-lookup"><span data-stu-id="f33a7-114">ICorProfilerInfo10 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)

