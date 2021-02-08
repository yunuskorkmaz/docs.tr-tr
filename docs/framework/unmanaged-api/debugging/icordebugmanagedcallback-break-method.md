---
description: ': ICorDebugManagedCallback:: Break yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugManagedCallback::Break Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.Break
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::Break
helpviewer_keywords:
- Break method [.NET Framework debugging]
- ICorDebugManagedCallback::Break method [.NET Framework debugging]
ms.assetid: 7d78a301-82b3-43b2-9d65-3cda3285ae97
topic_type:
- apiref
ms.openlocfilehash: 2ef273a693291685c4c3a0ce2b20ed45613e3376
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801221"
---
# <a name="icordebugmanagedcallbackbreak-method"></a><span data-ttu-id="5633c-103">ICorDebugManagedCallback::Break Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5633c-103">ICorDebugManagedCallback::Break Method</span></span>

<span data-ttu-id="5633c-104">Kod akışındaki bir yönerge yürütüldüğünde hata ayıklayıcıya bildirir <xref:System.Reflection.Emit.OpCodes.Break> .</span><span class="sxs-lookup"><span data-stu-id="5633c-104">Notifies the debugger when a <xref:System.Reflection.Emit.OpCodes.Break> instruction in the code stream is executed.</span></span>

## <a name="syntax"></a><span data-ttu-id="5633c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5633c-105">Syntax</span></span>

```cpp
HRESULT Break (
    [in] ICorDebugAppDomain *pAppDomain,
    [in] ICorDebugThread    *thread
);
```

## <a name="parameters"></a><span data-ttu-id="5633c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5633c-106">Parameters</span></span>

`pAppDomain`\
<span data-ttu-id="5633c-107">'ndaki Break yönergesini içeren uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5633c-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the break instruction.</span></span>

`thread`\
<span data-ttu-id="5633c-108">'ndaki Break yönergesini içeren iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5633c-108">[in] A pointer to an ICorDebugThread object that represents the thread that contains the break instruction.</span></span>

## <a name="requirements"></a><span data-ttu-id="5633c-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5633c-109">Requirements</span></span>

<span data-ttu-id="5633c-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5633c-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="5633c-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5633c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="5633c-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5633c-112">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="5633c-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5633c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="5633c-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5633c-114">See also</span></span>

- [<span data-ttu-id="5633c-115">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5633c-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
