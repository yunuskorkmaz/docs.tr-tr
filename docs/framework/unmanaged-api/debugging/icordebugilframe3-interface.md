---
title: ICorDebugILFrame3 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 15212cb5-93d4-4025-bec9-d4b9919eb1fe
topic_type:
- apiref
ms.openlocfilehash: dab5329086971b9349deaf84535fa251744f3cf0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724994"
---
# <a name="icordebugilframe3-interface"></a><span data-ttu-id="4e3c9-102">ICorDebugILFrame3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4e3c9-102">ICorDebugILFrame3 Interface</span></span>

<span data-ttu-id="4e3c9-103">İşlevin dönüş değerini içeren bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e3c9-103">Provides a method that encapsulates the return value of a function.</span></span> <span data-ttu-id="4e3c9-104">`ICorDebugILFrame3` , ICorDebugILFrame ve ICorDebugILFrame2 arabirimlerinin mantıksal bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="4e3c9-104">`ICorDebugILFrame3` is a logical extension of the ICorDebugILFrame and ICorDebugILFrame2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4e3c9-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4e3c9-105">Methods</span></span>  
  
|<span data-ttu-id="4e3c9-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4e3c9-106">Method</span></span>|<span data-ttu-id="4e3c9-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4e3c9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4e3c9-108">GetReturnValueForILOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4e3c9-108">GetReturnValueForILOffset Method</span></span>](icordebugilframe3-getreturnvalueforiloffset-method.md)|<span data-ttu-id="4e3c9-109">Bir işlevin dönüş değerini kapsülleyen bir ICorDebugValue nesnesi alır.</span><span class="sxs-lookup"><span data-stu-id="4e3c9-109">Gets an ICorDebugValue object that encapsulates the return value of a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4e3c9-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4e3c9-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4e3c9-111">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="4e3c9-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e3c9-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4e3c9-112">Requirements</span></span>  

 <span data-ttu-id="4e3c9-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e3c9-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e3c9-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4e3c9-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4e3c9-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4e3c9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e3c9-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e3c9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e3c9-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e3c9-117">See also</span></span>

- [<span data-ttu-id="4e3c9-118">ICorDebugCode3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4e3c9-118">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
- [<span data-ttu-id="4e3c9-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4e3c9-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
