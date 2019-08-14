---
title: ICorProfilerInfo8 arabirimi
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 210029ed1b1c7d780f3895f975f7a72227bbea80
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973695"
---
# <a name="icorprofilerinfo8-interface"></a><span data-ttu-id="7ef08-102">ICorProfilerInfo8 arabirimi</span><span class="sxs-lookup"><span data-stu-id="7ef08-102">ICorProfilerInfo8 Interface</span></span>

<span data-ttu-id="7ef08-103">Dinamik yöntemlerle ilgili bilgileri sorgulamak için yöntemler sağlayan [ICorProfilerInfo7](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md) öğesinin bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7ef08-103">A subclass of [ICorProfilerInfo7](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md) that provides methods to query information about dynamic methods.</span></span>

## <a name="methods"></a><span data-ttu-id="7ef08-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7ef08-104">Methods</span></span>  

| <span data-ttu-id="7ef08-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7ef08-105">Method</span></span>|<span data-ttu-id="7ef08-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7ef08-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="7ef08-107">Ifunctiondynamic yöntemi</span><span class="sxs-lookup"><span data-stu-id="7ef08-107">IsFunctionDynamic Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-isfunctiondynamic-method.md)| <span data-ttu-id="7ef08-108">Bir işlevin ilişkili meta veriye sahip olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="7ef08-108">Determines if a function does not have associated metadata.</span></span>|
|[<span data-ttu-id="7ef08-109">GetFunctionFromIP3 yöntemi</span><span class="sxs-lookup"><span data-stu-id="7ef08-109">GetFunctionFromIP3 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-getfunctionfromip3-method.md)| <span data-ttu-id="7ef08-110">Yönetilen bir kod yönerge işaretçisini FunctionID 'ye eşler.</span><span class="sxs-lookup"><span data-stu-id="7ef08-110">Maps a managed code instruction pointer to a FunctionID.</span></span> <span data-ttu-id="7ef08-111">Bu yöntem hem dinamik hem de dinamik olmayan yöntemler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="7ef08-111">This method works for both dynamic and non-dynamic methods.</span></span> |
|[<span data-ttu-id="7ef08-112">Getdynamicfunctionınfo yöntemi</span><span class="sxs-lookup"><span data-stu-id="7ef08-112">GetDynamicFunctionInfo Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-getdynamicfunctioninfo-method.md)| <span data-ttu-id="7ef08-113">Dinamik yöntemler hakkında bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="7ef08-113">Retrieves information about dynamic methods.</span></span> |

## <a name="requirements"></a><span data-ttu-id="7ef08-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7ef08-114">Requirements</span></span>  
<span data-ttu-id="7ef08-115">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ef08-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="7ef08-116">**Üst bilgi** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7ef08-116">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="7ef08-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7ef08-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
## <a name="see-also"></a><span data-ttu-id="7ef08-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ef08-118">See also</span></span>
- [<span data-ttu-id="7ef08-119">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7ef08-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
