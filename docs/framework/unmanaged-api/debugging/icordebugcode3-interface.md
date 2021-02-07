---
description: 'Daha fazla bilgi edinin: ICorDebugCode3 Interface'
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
ms.openlocfilehash: 378141395ab4d23e3e33a84c3b14ca4a75d847dc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764846"
---
# <a name="icordebugcode3-interface"></a><span data-ttu-id="4a5f8-103">ICorDebugCode3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4a5f8-103">ICorDebugCode3 Interface</span></span>

<span data-ttu-id="4a5f8-104">Yönetilen bir dönüş değeri hakkında bilgi sağlamak için "ICorDebugCode" ve "ICorDebugCode2" değerlerini genişleten bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="4a5f8-104">Provides a method that extends "ICorDebugCode" and "ICorDebugCode2" to provide information about a managed return value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4a5f8-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4a5f8-105">Methods</span></span>  
  
|<span data-ttu-id="4a5f8-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4a5f8-106">Method</span></span>|<span data-ttu-id="4a5f8-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4a5f8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4a5f8-108">GetReturnValueLiveOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4a5f8-108">GetReturnValueLiveOffset Method</span></span>](icordebugcode3-getreturnvalueliveoffset-method.md)|<span data-ttu-id="4a5f8-109">Belirtilen bir Il ofseti için, hata ayıklayıcının bir işlevden dönüş değeri alabileceği şekilde, bir kesme noktasının yerleştirilmesi gereken yerel uzaklıkları alır.</span><span class="sxs-lookup"><span data-stu-id="4a5f8-109">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a5f8-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4a5f8-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4a5f8-111">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="4a5f8-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a5f8-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4a5f8-112">Requirements</span></span>  

 <span data-ttu-id="4a5f8-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a5f8-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a5f8-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4a5f8-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4a5f8-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4a5f8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a5f8-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a5f8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a5f8-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a5f8-117">See also</span></span>

- [<span data-ttu-id="4a5f8-118">ICorDebugILFrame3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4a5f8-118">ICorDebugILFrame3 Interface</span></span>](icordebugilframe3-interface.md)
- [<span data-ttu-id="4a5f8-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4a5f8-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
