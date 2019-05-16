---
title: ICorDebugProcess4::ProcessStateChanged yöntemi
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
ms.openlocfilehash: 5e3a6714489e2051a09b5855ab9f911ef2f57450
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632294"
---
# <a name="icordebugprocess4processstatechanged-method"></a><span data-ttu-id="018db-102">ICorDebugProcess4::ProcessStateChanged yöntemi</span><span class="sxs-lookup"><span data-stu-id="018db-102">ICorDebugProcess4::ProcessStateChanged Method</span></span>

<span data-ttu-id="018db-103">Icordebug ardışık düzen işlemi hata ayıklayıcı dışı debugee'nın yürütülmesine devam etmesini bildirir.</span><span class="sxs-lookup"><span data-stu-id="018db-103">Notifies the ICorDebug pipeline that the out of process debugger is continuing the debugee's execution.</span></span>

## <a name="syntax"></a><span data-ttu-id="018db-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="018db-104">Syntax</span></span>

```
HRESULT ProcessStateChanged(
    [in] CorDebugStateChange change
);
```

## <a name="parameters"></a><span data-ttu-id="018db-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="018db-105">Parameters</span></span>

 `eChange`\
<span data-ttu-id="018db-106">[in] Üye [CorDebugStateChange numaralandırması](cordebugstatechange-enumeration.md) işlem yürütme durumundaki bir değişikliği açıklayan.</span><span class="sxs-lookup"><span data-stu-id="018db-106">[in] A member of the [CorDebugStateChange enumeration](cordebugstatechange-enumeration.md) describing a change in the process's execution state.</span></span>

## <a name="remarks"></a><span data-ttu-id="018db-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="018db-107">Remarks</span></span>

<span data-ttu-id="018db-108">Sağlanan yöntem parçasıdır `ICorDebugProcess4` arabirim ve sanal yöntem tablosunun dördüncü yuvaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="018db-108">The provided method is part of the `ICorDebugProcess4` interface and corresponds to the fourth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="018db-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="018db-109">Requirements</span></span>

 <span data-ttu-id="018db-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="018db-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="018db-111">**Üst bilgi:** None</span><span class="sxs-lookup"><span data-stu-id="018db-111">**Header:** None</span></span>

 <span data-ttu-id="018db-112">**Kitaplığı:** Yok.</span><span class="sxs-lookup"><span data-stu-id="018db-112">**Library:** None</span></span>
 
 <span data-ttu-id="018db-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="018db-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="018db-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="018db-114">See also</span></span>

- [<span data-ttu-id="018db-115">ICorDebugProcess4 arabirimi</span><span class="sxs-lookup"><span data-stu-id="018db-115">ICorDebugProcess4 Interface</span></span>](icordebugprocess4-interface.md)
- [<span data-ttu-id="018db-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="018db-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="018db-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="018db-117">Debugging</span></span>](index.md)
