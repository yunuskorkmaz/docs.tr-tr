---
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
ms.openlocfilehash: f70a88df00d15729a6bde06b49417b6439f7c0ec
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212483"
---
# <a name="icordebugmanagedcallbackbreak-method"></a><span data-ttu-id="ae22f-102">ICorDebugManagedCallback::Break Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ae22f-102">ICorDebugManagedCallback::Break Method</span></span>

<span data-ttu-id="ae22f-103">Kod akışındaki bir yönerge yürütüldüğünde hata ayıklayıcıya bildirir <xref:System.Reflection.Emit.OpCodes.Break> .</span><span class="sxs-lookup"><span data-stu-id="ae22f-103">Notifies the debugger when a <xref:System.Reflection.Emit.OpCodes.Break> instruction in the code stream is executed.</span></span>

## <a name="syntax"></a><span data-ttu-id="ae22f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ae22f-104">Syntax</span></span>

```cpp
HRESULT Break (
    [in] ICorDebugAppDomain *pAppDomain,
    [in] ICorDebugThread    *thread
);
```

## <a name="parameters"></a><span data-ttu-id="ae22f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ae22f-105">Parameters</span></span>

`pAppDomain`\
<span data-ttu-id="ae22f-106">'ndaki Break yönergesini içeren uygulama etki alanını temsil eden ICorDebugAppDomain nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ae22f-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the break instruction.</span></span>

`thread`\
<span data-ttu-id="ae22f-107">'ndaki Break yönergesini içeren iş parçacığını temsil eden ICorDebugThread nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ae22f-107">[in] A pointer to an ICorDebugThread object that represents the thread that contains the break instruction.</span></span>

## <a name="requirements"></a><span data-ttu-id="ae22f-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ae22f-108">Requirements</span></span>

<span data-ttu-id="ae22f-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae22f-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="ae22f-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ae22f-110">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="ae22f-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ae22f-111">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="ae22f-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae22f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="ae22f-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae22f-113">See also</span></span>

- [<span data-ttu-id="ae22f-114">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ae22f-114">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
