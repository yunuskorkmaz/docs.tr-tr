---
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
ms.openlocfilehash: 910c411d2c63ce2c6cf262e28e08546657dc2a4c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213575"
---
# <a name="icordebugprocess4processstatechanged-method"></a><span data-ttu-id="1b70c-102">ICorDebugProcess4::P rocessStateChanged yöntemi</span><span class="sxs-lookup"><span data-stu-id="1b70c-102">ICorDebugProcess4::ProcessStateChanged Method</span></span>

<span data-ttu-id="1b70c-103">ICorDebug ardışık düzenine, işlem hata ayıklamanın dışına ayıklandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="1b70c-103">Notifies the ICorDebug pipeline that the out of process debugger is continuing the debugee's execution.</span></span>

## <a name="syntax"></a><span data-ttu-id="1b70c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1b70c-104">Syntax</span></span>

```cpp
HRESULT ProcessStateChanged(
    [in] CorDebugStateChange change
);
```

## <a name="parameters"></a><span data-ttu-id="1b70c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1b70c-105">Parameters</span></span>

 `eChange`\
<span data-ttu-id="1b70c-106">'ndaki İşlemin yürütme durumundaki bir değişikliği açıklayan [Cordebugstatechange numaralandırmasının](cordebugstatechange-enumeration.md) bir üyesi.</span><span class="sxs-lookup"><span data-stu-id="1b70c-106">[in] A member of the [CorDebugStateChange enumeration](cordebugstatechange-enumeration.md) describing a change in the process's execution state.</span></span>

## <a name="remarks"></a><span data-ttu-id="1b70c-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1b70c-107">Remarks</span></span>

<span data-ttu-id="1b70c-108">Belirtilen yöntem arabirimin bir parçasıdır `ICorDebugProcess4` ve sanal yöntem tablosunun dördüncü yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="1b70c-108">The provided method is part of the `ICorDebugProcess4` interface and corresponds to the fourth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="1b70c-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1b70c-109">Requirements</span></span>

 <span data-ttu-id="1b70c-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b70c-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="1b70c-111">**Üst bilgi:** Seçim</span><span class="sxs-lookup"><span data-stu-id="1b70c-111">**Header:** None</span></span>

 <span data-ttu-id="1b70c-112">**Kitaplık:** Seçim</span><span class="sxs-lookup"><span data-stu-id="1b70c-112">**Library:** None</span></span>

 <span data-ttu-id="1b70c-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b70c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="1b70c-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1b70c-114">See also</span></span>

- [<span data-ttu-id="1b70c-115">ICorDebugProcess4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1b70c-115">ICorDebugProcess4 Interface</span></span>](icordebugprocess4-interface.md)
- [<span data-ttu-id="1b70c-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1b70c-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="1b70c-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="1b70c-117">Debugging</span></span>](index.md)
