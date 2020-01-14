---
title: ICorDebugFunction3 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugFunction3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: b22717b9-ead5-4eea-887e-789b52d613dc
topic_type:
- apiref
ms.openlocfilehash: b74008e0a183d46d82c5262209d582537fd155c7
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75938079"
---
# <a name="icordebugfunction3-interface"></a><span data-ttu-id="c049b-102">ICorDebugFunction3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c049b-102">ICorDebugFunction3 Interface</span></span>
<span data-ttu-id="c049b-103">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="c049b-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="c049b-104">Bir ReJIT isteğinden koda erişim sağlamak için ICorDebugFunction arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="c049b-104">Logically extends the ICorDebugFunction interface to provide access to code from a ReJIT request.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c049b-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c049b-105">Methods</span></span>  
  
|<span data-ttu-id="c049b-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c049b-106">Method</span></span>|<span data-ttu-id="c049b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c049b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c049b-108">GetActiveReJitRequestILCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c049b-108">GetActiveReJitRequestILCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md)|<span data-ttu-id="c049b-109">Etkin bir ReJIT isteğinden Il 'yi içeren bir [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="c049b-109">Gets an interface pointer to an [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c049b-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c049b-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c049b-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c049b-111">Requirements</span></span>  
 <span data-ttu-id="c049b-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c049b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c049b-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c049b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c049b-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c049b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c049b-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c049b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c049b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c049b-116">See also</span></span>

- [<span data-ttu-id="c049b-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c049b-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="c049b-118">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="c049b-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="c049b-119">ReJIT: nasıl yapılır Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c049b-119">ReJIT: A How-To Guide</span></span>](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
