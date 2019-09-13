---
title: ICorProfilerInfo8 Arabirimi
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 2baa33a7a3527392d8095b5d0ec7ad6af8a71a8e
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928931"
---
# <a name="icorprofilerinfo8-interface"></a><span data-ttu-id="dc4db-102">ICorProfilerInfo8 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dc4db-102">ICorProfilerInfo8 Interface</span></span>

<span data-ttu-id="dc4db-103">Dinamik yöntemlerle ilgili bilgileri sorgulamak için yöntemler sağlayan [ICorProfilerInfo7](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md) öğesinin bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="dc4db-103">A subclass of [ICorProfilerInfo7](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md) that provides methods to query information about dynamic methods.</span></span>

## <a name="methods"></a><span data-ttu-id="dc4db-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="dc4db-104">Methods</span></span>  

| <span data-ttu-id="dc4db-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="dc4db-105">Method</span></span>|<span data-ttu-id="dc4db-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dc4db-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="dc4db-107">Ifunctiondynamic yöntemi</span><span class="sxs-lookup"><span data-stu-id="dc4db-107">IsFunctionDynamic Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-isfunctiondynamic-method.md)| <span data-ttu-id="dc4db-108">Bir işlevin ilişkili meta veriye sahip olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="dc4db-108">Determines if a function does not have associated metadata.</span></span>|
|[<span data-ttu-id="dc4db-109">GetFunctionFromIP3 yöntemi</span><span class="sxs-lookup"><span data-stu-id="dc4db-109">GetFunctionFromIP3 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-getfunctionfromip3-method.md)| <span data-ttu-id="dc4db-110">Yönetilen bir kod yönerge işaretçisini FunctionID 'ye eşler.</span><span class="sxs-lookup"><span data-stu-id="dc4db-110">Maps a managed code instruction pointer to a FunctionID.</span></span> <span data-ttu-id="dc4db-111">Bu yöntem hem dinamik hem de dinamik olmayan yöntemler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="dc4db-111">This method works for both dynamic and non-dynamic methods.</span></span> |
|[<span data-ttu-id="dc4db-112">Getdynamicfunctionınfo yöntemi</span><span class="sxs-lookup"><span data-stu-id="dc4db-112">GetDynamicFunctionInfo Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-getdynamicfunctioninfo-method.md)| <span data-ttu-id="dc4db-113">Dinamik yöntemler hakkında bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="dc4db-113">Retrieves information about dynamic methods.</span></span> |

## <a name="requirements"></a><span data-ttu-id="dc4db-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dc4db-114">Requirements</span></span>  
<span data-ttu-id="dc4db-115">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc4db-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="dc4db-116">**Üst bilgi** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="dc4db-116">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="dc4db-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="dc4db-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="dc4db-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dc4db-118">See also</span></span>

- [<span data-ttu-id="dc4db-119">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="dc4db-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
