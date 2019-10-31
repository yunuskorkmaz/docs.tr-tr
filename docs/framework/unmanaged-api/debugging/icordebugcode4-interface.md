---
title: ICorDebugCode4 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugCode4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode4
helpviewer_keywords:
- ICorDebugCode4 interface [.NET Framework debugging]
ms.assetid: a3fdf523-274a-449c-920b-9fcb0aed1d97
topic_type:
- apiref
ms.openlocfilehash: 6c74a6c371ababb21bfda9b8dd2910d6a7881e6a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125535"
---
# <a name="icordebugcode4-interface"></a><span data-ttu-id="4a534-102">ICorDebugCode4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4a534-102">ICorDebugCode4 Interface</span></span>
<span data-ttu-id="4a534-103">Bir işlevdeki yerel değişkenleri ve bağımsız değişkenleri numaralandırmak için hata ayıklayıcı sağlayan bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="4a534-103">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4a534-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4a534-104">Methods</span></span>  
  
|<span data-ttu-id="4a534-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4a534-105">Method</span></span>|<span data-ttu-id="4a534-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4a534-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4a534-107">EnumerateVariableHomes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4a534-107">EnumerateVariableHomes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md)|<span data-ttu-id="4a534-108">Bir işlevdeki yerel değişkenlere ve bağımsız değişkenlere bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="4a534-108">Gets an enumerator to the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a534-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4a534-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4a534-110">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="4a534-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a534-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4a534-111">Requirements</span></span>  
 <span data-ttu-id="4a534-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a534-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a534-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4a534-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4a534-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4a534-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a534-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a534-115">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a534-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a534-116">See also</span></span>

- [<span data-ttu-id="4a534-117">ICorDebugCode3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4a534-117">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [<span data-ttu-id="4a534-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4a534-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
