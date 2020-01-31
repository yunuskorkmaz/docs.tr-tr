---
title: ICorDebugBlockingObjectEnum Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugBlockingObjectEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBlockingObjectEnum
helpviewer_keywords:
- ICorDebugBlockingObjectEnum interface [.NET Framework debugging]
ms.assetid: 208e5c2d-3f3f-404e-8b3c-7cccc14ddb16
topic_type:
- apiref
ms.openlocfilehash: be1e1cd0d38ad71de43478af5565bb1ac98a8c0d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76778009"
---
# <a name="icordebugblockingobjectenum-interface"></a><span data-ttu-id="4813c-102">ICorDebugBlockingObjectEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4813c-102">ICorDebugBlockingObjectEnum Interface</span></span>
<span data-ttu-id="4813c-103">[CorDebugBlockingObject](cordebugblockingobject-structure.md) yapılarının listesi için bir Numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="4813c-103">Provides an enumerator for a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span> <span data-ttu-id="4813c-104">Bu arabirim, ıcordebuggenum arabiriminin bir alt sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="4813c-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4813c-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4813c-105">Methods</span></span>  
  
|<span data-ttu-id="4813c-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4813c-106">Method</span></span>|<span data-ttu-id="4813c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4813c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4813c-108">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4813c-108">Next Method</span></span>](icordebugblockingobjectenum-next-method.md)|<span data-ttu-id="4813c-109">[CorDebugBlockingObject](cordebugblockingobject-structure.md) yapılarının listesini sıralar.</span><span class="sxs-lookup"><span data-stu-id="4813c-109">Enumerates through a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4813c-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4813c-110">Remarks</span></span>  
 <span data-ttu-id="4813c-111">Her `CorDebugBlockingObject` yapısı, bir iş parçacığını engelleyen bir nesneyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4813c-111">Each `CorDebugBlockingObject` structure represents an object that is blocking a thread.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4813c-112">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="4813c-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4813c-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4813c-113">Requirements</span></span>  
 <span data-ttu-id="4813c-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4813c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4813c-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4813c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4813c-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4813c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4813c-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4813c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4813c-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4813c-118">See also</span></span>

- [<span data-ttu-id="4813c-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4813c-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="4813c-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="4813c-120">Debugging</span></span>](index.md)
