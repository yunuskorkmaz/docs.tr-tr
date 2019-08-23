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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8ec40de7fe9e12315987e65e48f1727f5d5b80ef
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960724"
---
# <a name="icordebugcode4-interface"></a><span data-ttu-id="a3484-102">ICorDebugCode4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a3484-102">ICorDebugCode4 Interface</span></span>
<span data-ttu-id="a3484-103">Bir işlevdeki yerel değişkenleri ve bağımsız değişkenleri numaralandırmak için hata ayıklayıcı sağlayan bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="a3484-103">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a3484-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a3484-104">Methods</span></span>  
  
|<span data-ttu-id="a3484-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a3484-105">Method</span></span>|<span data-ttu-id="a3484-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a3484-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a3484-107">EnumerateVariableHomes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a3484-107">EnumerateVariableHomes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md)|<span data-ttu-id="a3484-108">Bir işlevdeki yerel değişkenlere ve bağımsız değişkenlere bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="a3484-108">Gets an enumerator to the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3484-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a3484-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a3484-110">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="a3484-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3484-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a3484-111">Requirements</span></span>  
 <span data-ttu-id="a3484-112">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3484-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3484-113">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a3484-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a3484-114">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a3484-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3484-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3484-115">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3484-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a3484-116">See also</span></span>

- [<span data-ttu-id="a3484-117">ICorDebugCode3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a3484-117">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [<span data-ttu-id="a3484-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a3484-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
