---
title: ICorProfilerInfo8 Arabirimi
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 2cca915eda44d73aea7469e5f752c57309c2300d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495170"
---
# <a name="icorprofilerinfo8-interface"></a><span data-ttu-id="8c1ff-102">ICorProfilerInfo8 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8c1ff-102">ICorProfilerInfo8 Interface</span></span>

<span data-ttu-id="8c1ff-103">Dinamik yöntemlerle ilgili bilgileri sorgulamak için yöntemler sağlayan [ICorProfilerInfo7](icorprofilerinfo7-interface.md) öğesinin bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8c1ff-103">A subclass of [ICorProfilerInfo7](icorprofilerinfo7-interface.md) that provides methods to query information about dynamic methods.</span></span>

## <a name="methods"></a><span data-ttu-id="8c1ff-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8c1ff-104">Methods</span></span>  

| <span data-ttu-id="8c1ff-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="8c1ff-105">Method</span></span>|<span data-ttu-id="8c1ff-106">Description</span><span class="sxs-lookup"><span data-stu-id="8c1ff-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="8c1ff-107">IsFunctionDynamic Metodu</span><span class="sxs-lookup"><span data-stu-id="8c1ff-107">IsFunctionDynamic Method</span></span>](icorprofilerinfo8-isfunctiondynamic-method.md)| <span data-ttu-id="8c1ff-108">Bir işlevin ilişkili meta veriye sahip olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="8c1ff-108">Determines if a function does not have associated metadata.</span></span>|
|[<span data-ttu-id="8c1ff-109">GetFunctionFromIP3 Metodu</span><span class="sxs-lookup"><span data-stu-id="8c1ff-109">GetFunctionFromIP3 Method</span></span>](icorprofilerinfo8-getfunctionfromip3-method.md)| <span data-ttu-id="8c1ff-110">Yönetilen bir kod yönerge işaretçisini FunctionID 'ye eşler.</span><span class="sxs-lookup"><span data-stu-id="8c1ff-110">Maps a managed code instruction pointer to a FunctionID.</span></span> <span data-ttu-id="8c1ff-111">Bu yöntem hem dinamik hem de dinamik olmayan yöntemler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="8c1ff-111">This method works for both dynamic and non-dynamic methods.</span></span> |
|[<span data-ttu-id="8c1ff-112">GetDynamicFunctionInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="8c1ff-112">GetDynamicFunctionInfo Method</span></span>](icorprofilerinfo8-getdynamicfunctioninfo-method.md)| <span data-ttu-id="8c1ff-113">Dinamik yöntemler hakkında bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="8c1ff-113">Retrieves information about dynamic methods.</span></span> |

## <a name="requirements"></a><span data-ttu-id="8c1ff-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8c1ff-114">Requirements</span></span>  
<span data-ttu-id="8c1ff-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c1ff-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="8c1ff-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="8c1ff-116">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="8c1ff-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8c1ff-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="8c1ff-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8c1ff-118">See also</span></span>

- [<span data-ttu-id="8c1ff-119">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8c1ff-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
