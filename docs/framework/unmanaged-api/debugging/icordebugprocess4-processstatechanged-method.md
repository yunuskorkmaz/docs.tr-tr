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
ms.openlocfilehash: b434f30fc187af8b118ac926fec96d28182b0bfc
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56221382"
---
# <a name="icordebugprocess4processstatechanged-method"></a><span data-ttu-id="f0562-102">ICorDebugProcess4::ProcessStateChanged yöntemi</span><span class="sxs-lookup"><span data-stu-id="f0562-102">ICorDebugProcess4::ProcessStateChanged Method</span></span>

<span data-ttu-id="f0562-103">Icordebug ardışık düzen işlemi hata ayıklayıcı dışı debugee'nın yürütülmesine devam etmesini bildirir.</span><span class="sxs-lookup"><span data-stu-id="f0562-103">Notifies the ICorDebug pipeline that the out of process debugger is continuing the debugee's execution.</span></span>

## <a name="syntax"></a><span data-ttu-id="f0562-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f0562-104">Syntax</span></span>

```
HRESULT ProcessStateChanged(
    [in] CorDebugStateChange change
);
```

#### <a name="parameters"></a><span data-ttu-id="f0562-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f0562-105">Parameters</span></span>

 `eChange`

 <span data-ttu-id="f0562-106">[in] Üye [CorDebugStateChange numaralandırması](cordebugstatechange-enumeration.md) işlem yürütme durumundaki bir değişikliği açıklayan.</span><span class="sxs-lookup"><span data-stu-id="f0562-106">[in] A member of the [CorDebugStateChange enumeration](cordebugstatechange-enumeration.md) describing a change in the process's execution state.</span></span>

## <a name="remarks"></a><span data-ttu-id="f0562-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f0562-107">Remarks</span></span>

<span data-ttu-id="f0562-108">Sağlanan yöntem parçasıdır `ICorDebugProcess4` arabirim ve sanal yöntem tablosunun dördüncü yuvaya karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="f0562-108">The provided method is part of the `ICorDebugProcess4` interface and corresponds to the fourth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="f0562-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f0562-109">Requirements</span></span>

 <span data-ttu-id="f0562-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0562-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="f0562-111">**Üst bilgi:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="f0562-111">**Header:** None</span></span>

 <span data-ttu-id="f0562-112">**Kitaplığı:** Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="f0562-112">**Library:** None</span></span>
 
 <span data-ttu-id="f0562-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0562-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="f0562-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0562-114">See also</span></span>

- [<span data-ttu-id="f0562-115">ICorDebugProcess4 arabirimi</span><span class="sxs-lookup"><span data-stu-id="f0562-115">ICorDebugProcess4 Interface</span></span>](icordebugprocess4-interface.md)
- [<span data-ttu-id="f0562-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f0562-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="f0562-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="f0562-117">Debugging</span></span>](index.md)
