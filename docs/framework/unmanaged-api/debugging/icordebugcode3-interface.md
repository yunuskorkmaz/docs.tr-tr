---
title: ICorDebugCode3 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugCode3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode3
helpviewer_keywords:
- ICorDebugCode3 interface [.NET Framework debugging]
ms.assetid: 70f07c9e-0614-4bee-ac34-09fe6c51c5a9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4efcf6d477ab006e179e283ca4ce7b62c27018a6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960765"
---
# <a name="icordebugcode3-interface"></a><span data-ttu-id="8a028-102">ICorDebugCode3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8a028-102">ICorDebugCode3 Interface</span></span>
<span data-ttu-id="8a028-103">Yönetilen bir dönüş değeri hakkında bilgi sağlamak için "ICorDebugCode" ve "ICorDebugCode2" değerlerini genişleten bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="8a028-103">Provides a method that extends "ICorDebugCode" and "ICorDebugCode2" to provide information about a managed return value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8a028-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8a028-104">Methods</span></span>  
  
|<span data-ttu-id="8a028-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="8a028-105">Method</span></span>|<span data-ttu-id="8a028-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8a028-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8a028-107">GetReturnValueLiveOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8a028-107">GetReturnValueLiveOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)|<span data-ttu-id="8a028-108">Belirtilen bir Il ofseti için, hata ayıklayıcının bir işlevden dönüş değeri alabileceği şekilde, bir kesme noktasının yerleştirilmesi gereken yerel uzaklıkları alır.</span><span class="sxs-lookup"><span data-stu-id="8a028-108">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8a028-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8a028-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8a028-110">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="8a028-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a028-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8a028-111">Requirements</span></span>  
 <span data-ttu-id="8a028-112">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a028-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a028-113">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8a028-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8a028-114">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8a028-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a028-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a028-115">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a028-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a028-116">See also</span></span>

- [<span data-ttu-id="8a028-117">ICorDebugILFrame3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8a028-117">ICorDebugILFrame3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)
- [<span data-ttu-id="8a028-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8a028-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
