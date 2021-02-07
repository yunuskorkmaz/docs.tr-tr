---
description: 'Daha fazla bilgi edinin: ICorDebugCode4 Interface'
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
ms.openlocfilehash: 1276db5c55c3d98e5ffa379f6126f700d93c1670
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764729"
---
# <a name="icordebugcode4-interface"></a><span data-ttu-id="c285c-103">ICorDebugCode4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c285c-103">ICorDebugCode4 Interface</span></span>

<span data-ttu-id="c285c-104">Bir işlevdeki yerel değişkenleri ve bağımsız değişkenleri numaralandırmak için hata ayıklayıcı sağlayan bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="c285c-104">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c285c-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c285c-105">Methods</span></span>  
  
|<span data-ttu-id="c285c-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c285c-106">Method</span></span>|<span data-ttu-id="c285c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c285c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c285c-108">EnumerateVariableHomes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c285c-108">EnumerateVariableHomes Method</span></span>](icordebugcode4-enumeratevariablehomes-method.md)|<span data-ttu-id="c285c-109">Bir işlevdeki yerel değişkenlere ve bağımsız değişkenlere bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="c285c-109">Gets an enumerator to the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c285c-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c285c-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c285c-111">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="c285c-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c285c-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c285c-112">Requirements</span></span>  

 <span data-ttu-id="c285c-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c285c-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c285c-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c285c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c285c-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c285c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c285c-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c285c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c285c-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c285c-117">See also</span></span>

- [<span data-ttu-id="c285c-118">ICorDebugCode3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c285c-118">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
- [<span data-ttu-id="c285c-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c285c-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
