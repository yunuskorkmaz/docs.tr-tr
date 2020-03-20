---
title: ICorDebugProcess4::ProcessStateChanged Yöntemi
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
ms.openlocfilehash: a6f36f5b86b4fa58ce2a4ef4aa23d527f797a5a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178636"
---
# <a name="icordebugprocess4processstatechanged-method"></a><span data-ttu-id="51c6d-102">ICorDebugProcess4::ProcessStateChanged Yöntemi</span><span class="sxs-lookup"><span data-stu-id="51c6d-102">ICorDebugProcess4::ProcessStateChanged Method</span></span>

<span data-ttu-id="51c6d-103">ICorDebug boru hattına işlem hata ayıklayıcısının debugee'nin yürütmesini devam ettiğini bildirin.</span><span class="sxs-lookup"><span data-stu-id="51c6d-103">Notifies the ICorDebug pipeline that the out of process debugger is continuing the debugee's execution.</span></span>

## <a name="syntax"></a><span data-ttu-id="51c6d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="51c6d-104">Syntax</span></span>

```cpp
HRESULT ProcessStateChanged(
    [in] CorDebugStateChange change
);
```

## <a name="parameters"></a><span data-ttu-id="51c6d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="51c6d-105">Parameters</span></span>

 `eChange`\
<span data-ttu-id="51c6d-106">[içinde] İşlemin yürütme durumundaki bir değişikliği açıklayan [CorDebugStateChange numaralandırmasının](cordebugstatechange-enumeration.md) bir üyesi.</span><span class="sxs-lookup"><span data-stu-id="51c6d-106">[in] A member of the [CorDebugStateChange enumeration](cordebugstatechange-enumeration.md) describing a change in the process's execution state.</span></span>

## <a name="remarks"></a><span data-ttu-id="51c6d-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="51c6d-107">Remarks</span></span>

<span data-ttu-id="51c6d-108">Sağlanan yöntem `ICorDebugProcess4` arabirimin bir parçasıdır ve sanal yöntem tablosunun dördüncü yuvasına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="51c6d-108">The provided method is part of the `ICorDebugProcess4` interface and corresponds to the fourth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="51c6d-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="51c6d-109">Requirements</span></span>

 <span data-ttu-id="51c6d-110">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51c6d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="51c6d-111">**Üstbilgi:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="51c6d-111">**Header:** None</span></span>

 <span data-ttu-id="51c6d-112">**Kütüphane:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="51c6d-112">**Library:** None</span></span>

 <span data-ttu-id="51c6d-113">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51c6d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="51c6d-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51c6d-114">See also</span></span>

- [<span data-ttu-id="51c6d-115">ICorDebugProcess4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="51c6d-115">ICorDebugProcess4 Interface</span></span>](icordebugprocess4-interface.md)
- [<span data-ttu-id="51c6d-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="51c6d-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="51c6d-117">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="51c6d-117">Debugging</span></span>](index.md)
