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
ms.openlocfilehash: 6f66e4a903be2e9b12a573f74638a62c58005689
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893463"
---
# <a name="icordebugcode3-interface"></a><span data-ttu-id="4578d-102">ICorDebugCode3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4578d-102">ICorDebugCode3 Interface</span></span>
<span data-ttu-id="4578d-103">Yönetilen bir dönüş değeri hakkında bilgi sağlamak için "ICorDebugCode" ve "ICorDebugCode2" değerlerini genişleten bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="4578d-103">Provides a method that extends "ICorDebugCode" and "ICorDebugCode2" to provide information about a managed return value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4578d-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4578d-104">Methods</span></span>  
  
|<span data-ttu-id="4578d-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4578d-105">Method</span></span>|<span data-ttu-id="4578d-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4578d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4578d-107">GetReturnValueLiveOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4578d-107">GetReturnValueLiveOffset Method</span></span>](icordebugcode3-getreturnvalueliveoffset-method.md)|<span data-ttu-id="4578d-108">Belirtilen bir Il ofseti için, hata ayıklayıcının bir işlevden dönüş değeri alabileceği şekilde, bir kesme noktasının yerleştirilmesi gereken yerel uzaklıkları alır.</span><span class="sxs-lookup"><span data-stu-id="4578d-108">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4578d-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4578d-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4578d-110">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="4578d-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4578d-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4578d-111">Requirements</span></span>  
 <span data-ttu-id="4578d-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4578d-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4578d-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4578d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4578d-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4578d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4578d-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4578d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4578d-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4578d-116">See also</span></span>

- [<span data-ttu-id="4578d-117">ICorDebugILFrame3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4578d-117">ICorDebugILFrame3 Interface</span></span>](icordebugilframe3-interface.md)
- [<span data-ttu-id="4578d-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4578d-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
