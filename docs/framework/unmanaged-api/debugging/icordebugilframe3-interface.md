---
description: 'Daha fazla bilgi edinin: ICorDebugILFrame3 Interface'
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
ms.openlocfilehash: a34a3f0941871a2d0a63fb2d9f78ccb7ff455866
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791263"
---
# <a name="icordebugilframe3-interface"></a><span data-ttu-id="00a2c-103">ICorDebugILFrame3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00a2c-103">ICorDebugILFrame3 Interface</span></span>

<span data-ttu-id="00a2c-104">İşlevin dönüş değerini içeren bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="00a2c-104">Provides a method that encapsulates the return value of a function.</span></span> <span data-ttu-id="00a2c-105">`ICorDebugILFrame3` , ICorDebugILFrame ve ICorDebugILFrame2 arabirimlerinin mantıksal bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="00a2c-105">`ICorDebugILFrame3` is a logical extension of the ICorDebugILFrame and ICorDebugILFrame2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="00a2c-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="00a2c-106">Methods</span></span>  
  
|<span data-ttu-id="00a2c-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="00a2c-107">Method</span></span>|<span data-ttu-id="00a2c-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="00a2c-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="00a2c-109">GetReturnValueForILOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="00a2c-109">GetReturnValueForILOffset Method</span></span>](icordebugilframe3-getreturnvalueforiloffset-method.md)|<span data-ttu-id="00a2c-110">Bir işlevin dönüş değerini kapsülleyen bir ICorDebugValue nesnesi alır.</span><span class="sxs-lookup"><span data-stu-id="00a2c-110">Gets an ICorDebugValue object that encapsulates the return value of a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00a2c-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="00a2c-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="00a2c-112">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="00a2c-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00a2c-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="00a2c-113">Requirements</span></span>  

 <span data-ttu-id="00a2c-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00a2c-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00a2c-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="00a2c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="00a2c-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="00a2c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00a2c-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00a2c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00a2c-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00a2c-118">See also</span></span>

- [<span data-ttu-id="00a2c-119">ICorDebugCode3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="00a2c-119">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
- [<span data-ttu-id="00a2c-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="00a2c-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
