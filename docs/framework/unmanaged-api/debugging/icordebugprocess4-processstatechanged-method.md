---
description: 'Hakkında daha fazla bilgi edinin: ICorDebugProcess4::P rocessStateChanged yöntemi'
title: ICorDebugProcess4::P rocessStateChanged yöntemi
ms.date: 02/07/2019
api_name:
- ICorDebugProcess4::ProcessStateChanged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess4::ProcessStateChanged
helpviewer_keywords:
- ICorDebugProcess4::ProcessStateChanged method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 35a76b3c6dd9b37d3f06f23bc2ffea82f125a29e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746483"
---
# <a name="icordebugprocess4processstatechanged-method"></a><span data-ttu-id="6f103-103">ICorDebugProcess4::P rocessStateChanged yöntemi</span><span class="sxs-lookup"><span data-stu-id="6f103-103">ICorDebugProcess4::ProcessStateChanged Method</span></span>

<span data-ttu-id="6f103-104">ICorDebug ardışık düzenine, işlem hata ayıklamanın dışına ayıklandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="6f103-104">Notifies the ICorDebug pipeline that the out of process debugger is continuing the debugee's execution.</span></span>

## <a name="syntax"></a><span data-ttu-id="6f103-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6f103-105">Syntax</span></span>

```cpp
HRESULT ProcessStateChanged(
    [in] CorDebugStateChange change
);
```

## <a name="parameters"></a><span data-ttu-id="6f103-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6f103-106">Parameters</span></span>

 `eChange`\
<span data-ttu-id="6f103-107">'ndaki İşlemin yürütme durumundaki bir değişikliği açıklayan [Cordebugstatechange numaralandırmasının](cordebugstatechange-enumeration.md) bir üyesi.</span><span class="sxs-lookup"><span data-stu-id="6f103-107">[in] A member of the [CorDebugStateChange enumeration](cordebugstatechange-enumeration.md) describing a change in the process's execution state.</span></span>

## <a name="remarks"></a><span data-ttu-id="6f103-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6f103-108">Remarks</span></span>

<span data-ttu-id="6f103-109">Belirtilen yöntem arabirimin bir parçasıdır `ICorDebugProcess4` ve sanal yöntem tablosunun dördüncü yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="6f103-109">The provided method is part of the `ICorDebugProcess4` interface and corresponds to the fourth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="6f103-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6f103-110">Requirements</span></span>

 <span data-ttu-id="6f103-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f103-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="6f103-112">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="6f103-112">**Header:** None</span></span>

 <span data-ttu-id="6f103-113">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="6f103-113">**Library:** None</span></span>

 <span data-ttu-id="6f103-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f103-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="6f103-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f103-115">See also</span></span>

- [<span data-ttu-id="6f103-116">ICorDebugProcess4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6f103-116">ICorDebugProcess4 Interface</span></span>](icordebugprocess4-interface.md)
- [<span data-ttu-id="6f103-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6f103-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="6f103-118">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="6f103-118">Debugging</span></span>](index.md)
