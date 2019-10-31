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
ms.openlocfilehash: ba4375511fe7f5aaee032c4e132de54808041111
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122441"
---
# <a name="icordebugthread4getcurrentcustomdebuggernotification-method"></a><span data-ttu-id="6bb85-102">ICorDebugThread4::GetCurrentCustomDebuggerNotification Metodu</span><span class="sxs-lookup"><span data-stu-id="6bb85-102">ICorDebugThread4::GetCurrentCustomDebuggerNotification Method</span></span>

<span data-ttu-id="6bb85-103">Geçerli iş parçacığında geçerli [ICorDebugManagedCallback3:: CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) nesnesini alır.</span><span class="sxs-lookup"><span data-stu-id="6bb85-103">Gets the current [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>

## <a name="syntax"></a><span data-ttu-id="6bb85-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6bb85-104">Syntax</span></span>

```cpp
HRESULT GetCurrentCustomDebuggerNotification(
    [out] ICorDebugValue **ppNotificationObject
    );
```

## <a name="parameters"></a><span data-ttu-id="6bb85-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6bb85-105">Parameters</span></span>

`ppNotificationObject`\
<span data-ttu-id="6bb85-106">dışı Geçerli iş parçacığında geçerli `ICorDebugManagedCallback3::CustomNotification` nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6bb85-106">[out] A pointer to the current `ICorDebugManagedCallback3::CustomNotification` object on the current thread.</span></span>

## <a name="remarks"></a><span data-ttu-id="6bb85-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6bb85-107">Remarks</span></span>

<span data-ttu-id="6bb85-108">Yöntem, `ICorDebugManagedCallback3::CustomNotification` bir geri çağırma içinden çağrılmaması veya geçerli bir bildirim nesnesi yoksa `ppNotificationObject` değeri null olur.</span><span class="sxs-lookup"><span data-stu-id="6bb85-108">The value of `ppNotificationObject` is null if the method is not called from within a `ICorDebugManagedCallback3::CustomNotification` callback, or if no current notification object exists.</span></span>

## <a name="requirements"></a><span data-ttu-id="6bb85-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6bb85-109">Requirements</span></span>

<span data-ttu-id="6bb85-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6bb85-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="6bb85-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6bb85-111">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="6bb85-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6bb85-112">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="6bb85-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bb85-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="6bb85-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6bb85-114">See also</span></span>

- [<span data-ttu-id="6bb85-115">ICorDebugThread4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6bb85-115">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)
- [<span data-ttu-id="6bb85-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6bb85-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="6bb85-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="6bb85-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
