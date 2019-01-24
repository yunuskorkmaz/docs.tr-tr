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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9c87578c3a5e2bec9bbd754929308645f7862ee5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54701683"
---
# <a name="icordebugilframe3-interface"></a><span data-ttu-id="4b9b0-102">ICorDebugILFrame3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4b9b0-102">ICorDebugILFrame3 Interface</span></span>
<span data-ttu-id="4b9b0-103">İşlevin dönüş değerini içeren bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="4b9b0-103">Provides a method that encapsulates the return value of a function.</span></span> <span data-ttu-id="4b9b0-104">`ICorDebugILFrame3` Icordebugılframe ve Icordebugılframe2 arabirimlerinin mantıksal uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="4b9b0-104">`ICorDebugILFrame3` is a logical extension of the ICorDebugILFrame and ICorDebugILFrame2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4b9b0-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4b9b0-105">Methods</span></span>  
  
|<span data-ttu-id="4b9b0-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4b9b0-106">Method</span></span>|<span data-ttu-id="4b9b0-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4b9b0-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4b9b0-108">GetReturnValueForILOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4b9b0-108">GetReturnValueForILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)|<span data-ttu-id="4b9b0-109">Bir işlevin dönüş değeri bir Icordebugvalue nesnesini alır.</span><span class="sxs-lookup"><span data-stu-id="4b9b0-109">Gets an ICorDebugValue object that encapsulates the return value of a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b9b0-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4b9b0-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4b9b0-111">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="4b9b0-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b9b0-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4b9b0-112">Requirements</span></span>  
 <span data-ttu-id="4b9b0-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b9b0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b9b0-114">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4b9b0-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4b9b0-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4b9b0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b9b0-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b9b0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b9b0-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4b9b0-117">See also</span></span>
- [<span data-ttu-id="4b9b0-118">ICorDebugCode3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4b9b0-118">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [<span data-ttu-id="4b9b0-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4b9b0-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
