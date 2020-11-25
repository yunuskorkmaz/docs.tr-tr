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
ms.openlocfilehash: 17eda7470e5f2e4b41d1f2ed164843eaeeedea93
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695876"
---
# <a name="icordebugfunction3-interface"></a><span data-ttu-id="0b6c4-102">ICorDebugFunction3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b6c4-102">ICorDebugFunction3 Interface</span></span>

<span data-ttu-id="0b6c4-103">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="0b6c4-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="0b6c4-104">Bir ReJIT isteğinden koda erişim sağlamak için ICorDebugFunction arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="0b6c4-104">Logically extends the ICorDebugFunction interface to provide access to code from a ReJIT request.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0b6c4-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0b6c4-105">Methods</span></span>  
  
|<span data-ttu-id="0b6c4-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="0b6c4-106">Method</span></span>|<span data-ttu-id="0b6c4-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b6c4-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0b6c4-108">GetActiveReJitRequestILCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0b6c4-108">GetActiveReJitRequestILCode Method</span></span>](icordebugfunction3-getactiverejitrequestilcode-method.md)|<span data-ttu-id="0b6c4-109">Etkin bir ReJIT isteğinden Il 'yi içeren bir [ICorDebugILCode](icordebugilcode-interface.md) için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="0b6c4-109">Gets an interface pointer to an [ICorDebugILCode](icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b6c4-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0b6c4-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b6c4-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0b6c4-111">Requirements</span></span>  

 <span data-ttu-id="0b6c4-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b6c4-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b6c4-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0b6c4-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0b6c4-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0b6c4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b6c4-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b6c4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b6c4-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b6c4-116">See also</span></span>

- [<span data-ttu-id="0b6c4-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0b6c4-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="0b6c4-118">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="0b6c4-118">Debugging</span></span>](index.md)
- [<span data-ttu-id="0b6c4-119">ReJIT: A How-To Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0b6c4-119">ReJIT: A How-To Guide</span></span>](/archive/blogs/davbr/rejit-a-how-to-guide)
