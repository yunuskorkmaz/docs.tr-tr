---
description: 'Daha fazla bilgi edinin: ICorDebugFunction3 Interface'
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
ms.openlocfilehash: f6f3ce78fbb0ca7efb6ba6a95da20f8c698b923c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692075"
---
# <a name="icordebugfunction3-interface"></a><span data-ttu-id="96578-103">ICorDebugFunction3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="96578-103">ICorDebugFunction3 Interface</span></span>

<span data-ttu-id="96578-104">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="96578-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="96578-105">Bir ReJIT isteğinden koda erişim sağlamak için ICorDebugFunction arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="96578-105">Logically extends the ICorDebugFunction interface to provide access to code from a ReJIT request.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="96578-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="96578-106">Methods</span></span>  
  
|<span data-ttu-id="96578-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="96578-107">Method</span></span>|<span data-ttu-id="96578-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="96578-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="96578-109">GetActiveReJitRequestILCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="96578-109">GetActiveReJitRequestILCode Method</span></span>](icordebugfunction3-getactiverejitrequestilcode-method.md)|<span data-ttu-id="96578-110">Etkin bir ReJIT isteğinden Il 'yi içeren bir [ICorDebugILCode](icordebugilcode-interface.md) için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="96578-110">Gets an interface pointer to an [ICorDebugILCode](icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96578-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="96578-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96578-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="96578-112">Requirements</span></span>  

 <span data-ttu-id="96578-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96578-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96578-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="96578-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="96578-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="96578-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96578-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96578-116">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96578-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96578-117">See also</span></span>

- [<span data-ttu-id="96578-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="96578-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="96578-119">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="96578-119">Debugging</span></span>](index.md)
- [<span data-ttu-id="96578-120">ReJIT: A How-To Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="96578-120">ReJIT: A How-To Guide</span></span>](/archive/blogs/davbr/rejit-a-how-to-guide)
