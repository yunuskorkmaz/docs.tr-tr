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
ms.openlocfilehash: b46c74ec0bfc1fc44bcaca07439c472b0fd8393f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59113769"
---
# <a name="icordebugilframe3-interface"></a><span data-ttu-id="adb65-102">ICorDebugILFrame3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="adb65-102">ICorDebugILFrame3 Interface</span></span>
<span data-ttu-id="adb65-103">İşlevin dönüş değerini içeren bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="adb65-103">Provides a method that encapsulates the return value of a function.</span></span> <span data-ttu-id="adb65-104">`ICorDebugILFrame3` Icordebugılframe ve Icordebugılframe2 arabirimlerinin mantıksal uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="adb65-104">`ICorDebugILFrame3` is a logical extension of the ICorDebugILFrame and ICorDebugILFrame2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="adb65-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="adb65-105">Methods</span></span>  
  
|<span data-ttu-id="adb65-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="adb65-106">Method</span></span>|<span data-ttu-id="adb65-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="adb65-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="adb65-108">GetReturnValueForILOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="adb65-108">GetReturnValueForILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)|<span data-ttu-id="adb65-109">Bir işlevin dönüş değeri bir Icordebugvalue nesnesini alır.</span><span class="sxs-lookup"><span data-stu-id="adb65-109">Gets an ICorDebugValue object that encapsulates the return value of a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="adb65-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="adb65-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="adb65-111">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="adb65-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="adb65-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="adb65-112">Requirements</span></span>  
 <span data-ttu-id="adb65-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="adb65-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="adb65-114">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="adb65-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="adb65-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="adb65-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="adb65-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="adb65-116">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adb65-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="adb65-117">See also</span></span>

- [<span data-ttu-id="adb65-118">ICorDebugCode3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="adb65-118">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [<span data-ttu-id="adb65-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="adb65-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
