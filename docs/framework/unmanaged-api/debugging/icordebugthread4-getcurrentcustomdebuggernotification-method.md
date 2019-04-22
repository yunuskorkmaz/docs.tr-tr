---
title: ICorDebugThread4::GetCurrentCustomDebuggerNotification Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.GetCurrentCustomDebuggerNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::GetCurrentCustomDebuggerNotification
helpviewer_keywords:
- GetCurrentCustomDebuggerNotification method [.NET Framework debugging]
- ICorDebugThread4::GetCurrentCustomDebuggerNotification method [.NET Framework debugging]
ms.assetid: 57e0f2d2-5f0e-4e2d-99ec-3f26632eb693
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f626ff6e562bd9bc94440f31e9470a45cc32cfbd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59216333"
---
# <a name="icordebugthread4getcurrentcustomdebuggernotification-method"></a><span data-ttu-id="b8452-102">ICorDebugThread4::GetCurrentCustomDebuggerNotification Metodu</span><span class="sxs-lookup"><span data-stu-id="b8452-102">ICorDebugThread4::GetCurrentCustomDebuggerNotification Method</span></span>

<span data-ttu-id="b8452-103">Geçerli alır [Icordebugmanagedcallback3::customnotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) nesne geçerli iş parçacığı üzerinde.</span><span class="sxs-lookup"><span data-stu-id="b8452-103">Gets the current [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>

## <a name="syntax"></a><span data-ttu-id="b8452-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b8452-104">Syntax</span></span>

```cpp
HRESULT GetCurrentCustomDebuggerNotification(
    [out] ICorDebugValue **ppNotificationObject
    );
```

## <a name="parameters"></a><span data-ttu-id="b8452-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b8452-105">Parameters</span></span>

`ppNotificationObject`\
<span data-ttu-id="b8452-106">[out] Geçerli bir işaretçi `ICorDebugManagedCallback3::CustomNotification` nesne geçerli iş parçacığı üzerinde.</span><span class="sxs-lookup"><span data-stu-id="b8452-106">[out] A pointer to the current `ICorDebugManagedCallback3::CustomNotification` object on the current thread.</span></span>

## <a name="remarks"></a><span data-ttu-id="b8452-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b8452-107">Remarks</span></span>

<span data-ttu-id="b8452-108">Değerini `ppNotificationObject` yöntemi içinden çağrılmazsa null bir `ICorDebugManagedCallback3::CustomNotification` geri arama veya geçerli hiçbir bildirim nesne varsa.</span><span class="sxs-lookup"><span data-stu-id="b8452-108">The value of `ppNotificationObject` is null if the method is not called from within a `ICorDebugManagedCallback3::CustomNotification` callback, or if no current notification object exists.</span></span>

## <a name="requirements"></a><span data-ttu-id="b8452-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b8452-109">Requirements</span></span>

<span data-ttu-id="b8452-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8452-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="b8452-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b8452-111">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="b8452-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8452-112">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="b8452-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8452-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="b8452-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8452-114">See also</span></span>

- [<span data-ttu-id="b8452-115">ICorDebugThread4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b8452-115">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)
- [<span data-ttu-id="b8452-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b8452-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="b8452-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="b8452-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
