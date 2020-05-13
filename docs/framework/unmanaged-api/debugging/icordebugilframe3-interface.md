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
ms.openlocfilehash: 59221b09cc1c5d2d01c1007b649a4bb01de57f04
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213770"
---
# <a name="icordebugilframe3-interface"></a><span data-ttu-id="be042-102">ICorDebugILFrame3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="be042-102">ICorDebugILFrame3 Interface</span></span>
<span data-ttu-id="be042-103">İşlevin dönüş değerini içeren bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="be042-103">Provides a method that encapsulates the return value of a function.</span></span> <span data-ttu-id="be042-104">`ICorDebugILFrame3`, ICorDebugILFrame ve ICorDebugILFrame2 arabirimlerinin mantıksal bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="be042-104">`ICorDebugILFrame3` is a logical extension of the ICorDebugILFrame and ICorDebugILFrame2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="be042-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="be042-105">Methods</span></span>  
  
|<span data-ttu-id="be042-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="be042-106">Method</span></span>|<span data-ttu-id="be042-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="be042-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="be042-108">GetReturnValueForILOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="be042-108">GetReturnValueForILOffset Method</span></span>](icordebugilframe3-getreturnvalueforiloffset-method.md)|<span data-ttu-id="be042-109">Bir işlevin dönüş değerini kapsülleyen bir ICorDebugValue nesnesi alır.</span><span class="sxs-lookup"><span data-stu-id="be042-109">Gets an ICorDebugValue object that encapsulates the return value of a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="be042-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="be042-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="be042-111">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="be042-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be042-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="be042-112">Requirements</span></span>  
 <span data-ttu-id="be042-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be042-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be042-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="be042-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="be042-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="be042-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be042-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be042-116">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be042-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be042-117">See also</span></span>

- [<span data-ttu-id="be042-118">ICorDebugCode3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="be042-118">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
- [<span data-ttu-id="be042-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="be042-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
