---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo8 Interface'
title: ICorProfilerInfo8 Arabirimi
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 4538c9d314283c67ab0bfe6af3f3768062cffda4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646549"
---
# <a name="icorprofilerinfo8-interface"></a><span data-ttu-id="a597a-103">ICorProfilerInfo8 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a597a-103">ICorProfilerInfo8 Interface</span></span>

<span data-ttu-id="a597a-104">Dinamik yöntemlerle ilgili bilgileri sorgulamak için yöntemler sağlayan [ICorProfilerInfo7](icorprofilerinfo7-interface.md) öğesinin bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a597a-104">A subclass of [ICorProfilerInfo7](icorprofilerinfo7-interface.md) that provides methods to query information about dynamic methods.</span></span>

## <a name="methods"></a><span data-ttu-id="a597a-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a597a-105">Methods</span></span>  

| <span data-ttu-id="a597a-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a597a-106">Method</span></span>|<span data-ttu-id="a597a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a597a-107">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="a597a-108">IsFunctionDynamic Metodu</span><span class="sxs-lookup"><span data-stu-id="a597a-108">IsFunctionDynamic Method</span></span>](icorprofilerinfo8-isfunctiondynamic-method.md)| <span data-ttu-id="a597a-109">Bir işlevin ilişkili meta veriye sahip olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="a597a-109">Determines if a function does not have associated metadata.</span></span>|
|[<span data-ttu-id="a597a-110">GetFunctionFromIP3 Metodu</span><span class="sxs-lookup"><span data-stu-id="a597a-110">GetFunctionFromIP3 Method</span></span>](icorprofilerinfo8-getfunctionfromip3-method.md)| <span data-ttu-id="a597a-111">Yönetilen bir kod yönerge işaretçisini FunctionID 'ye eşler.</span><span class="sxs-lookup"><span data-stu-id="a597a-111">Maps a managed code instruction pointer to a FunctionID.</span></span> <span data-ttu-id="a597a-112">Bu yöntem hem dinamik hem de dinamik olmayan yöntemler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a597a-112">This method works for both dynamic and non-dynamic methods.</span></span> |
|[<span data-ttu-id="a597a-113">GetDynamicFunctionInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="a597a-113">GetDynamicFunctionInfo Method</span></span>](icorprofilerinfo8-getdynamicfunctioninfo-method.md)| <span data-ttu-id="a597a-114">Dinamik yöntemler hakkında bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="a597a-114">Retrieves information about dynamic methods.</span></span> |

## <a name="requirements"></a><span data-ttu-id="a597a-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a597a-115">Requirements</span></span>  

<span data-ttu-id="a597a-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a597a-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="a597a-117">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a597a-117">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="a597a-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a597a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="a597a-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a597a-119">See also</span></span>

- [<span data-ttu-id="a597a-120">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a597a-120">Profiling Interfaces</span></span>](profiling-interfaces.md)
