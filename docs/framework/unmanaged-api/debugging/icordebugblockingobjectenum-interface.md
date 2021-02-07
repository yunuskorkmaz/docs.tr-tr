---
description: ': ICorDebugBlockingObjectEnum arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 4f28039cb8a9bdcb376a9acf22572d29e41a2adf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754075"
---
# <a name="icordebugblockingobjectenum-interface"></a><span data-ttu-id="fee92-103">ICorDebugBlockingObjectEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fee92-103">ICorDebugBlockingObjectEnum Interface</span></span>

<span data-ttu-id="fee92-104">[CorDebugBlockingObject](cordebugblockingobject-structure.md) yapılarının listesi için bir Numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="fee92-104">Provides an enumerator for a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span> <span data-ttu-id="fee92-105">Bu arabirim, ıcordebuggenum arabiriminin bir alt sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="fee92-105">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fee92-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="fee92-106">Methods</span></span>  
  
|<span data-ttu-id="fee92-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="fee92-107">Method</span></span>|<span data-ttu-id="fee92-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fee92-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fee92-109">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fee92-109">Next Method</span></span>](icordebugblockingobjectenum-next-method.md)|<span data-ttu-id="fee92-110">[CorDebugBlockingObject](cordebugblockingobject-structure.md) yapılarının listesini sıralar.</span><span class="sxs-lookup"><span data-stu-id="fee92-110">Enumerates through a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fee92-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fee92-111">Remarks</span></span>  

 <span data-ttu-id="fee92-112">Her `CorDebugBlockingObject` Yapı, bir iş parçacığını engelleyen bir nesneyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fee92-112">Each `CorDebugBlockingObject` structure represents an object that is blocking a thread.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fee92-113">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="fee92-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fee92-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fee92-114">Requirements</span></span>  

 <span data-ttu-id="fee92-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fee92-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fee92-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fee92-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fee92-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="fee92-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fee92-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fee92-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fee92-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fee92-119">See also</span></span>

- [<span data-ttu-id="fee92-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fee92-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="fee92-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="fee92-121">Debugging</span></span>](index.md)
