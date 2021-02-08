---
description: 'Daha fazla bilgi edinin: ICorDebugThread4:: GetCurrentCustomDebuggerNotification yöntemi'
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
ms.openlocfilehash: 20d9449e98b9ab91dbdec84ba026e91514d5b3cc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800948"
---
# <a name="icordebugthread4getcurrentcustomdebuggernotification-method"></a><span data-ttu-id="a9a9b-103">ICorDebugThread4::GetCurrentCustomDebuggerNotification Metodu</span><span class="sxs-lookup"><span data-stu-id="a9a9b-103">ICorDebugThread4::GetCurrentCustomDebuggerNotification Method</span></span>

<span data-ttu-id="a9a9b-104">Geçerli iş parçacığında geçerli [ICorDebugManagedCallback3:: CustomNotification](icordebugmanagedcallback3-customnotification-method.md) nesnesini alır.</span><span class="sxs-lookup"><span data-stu-id="a9a9b-104">Gets the current [ICorDebugManagedCallback3::CustomNotification](icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>

## <a name="syntax"></a><span data-ttu-id="a9a9b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a9a9b-105">Syntax</span></span>

```cpp
HRESULT GetCurrentCustomDebuggerNotification(
    [out] ICorDebugValue **ppNotificationObject
    );
```

## <a name="parameters"></a><span data-ttu-id="a9a9b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a9a9b-106">Parameters</span></span>

`ppNotificationObject`\
<span data-ttu-id="a9a9b-107">dışı `ICorDebugManagedCallback3::CustomNotification` Geçerli iş parçacığındaki geçerli nesneye yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a9a9b-107">[out] A pointer to the current `ICorDebugManagedCallback3::CustomNotification` object on the current thread.</span></span>

## <a name="remarks"></a><span data-ttu-id="a9a9b-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a9a9b-108">Remarks</span></span>

<span data-ttu-id="a9a9b-109">`ppNotificationObject`Yöntemi bir geri çağırma içinden çağrılmaması `ICorDebugManagedCallback3::CustomNotification` veya geçerli bir bildirim nesnesi yoksa değeri null olur.</span><span class="sxs-lookup"><span data-stu-id="a9a9b-109">The value of `ppNotificationObject` is null if the method is not called from within a `ICorDebugManagedCallback3::CustomNotification` callback, or if no current notification object exists.</span></span>

## <a name="requirements"></a><span data-ttu-id="a9a9b-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a9a9b-110">Requirements</span></span>

<span data-ttu-id="a9a9b-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9a9b-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="a9a9b-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a9a9b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="a9a9b-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a9a9b-113">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="a9a9b-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9a9b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="a9a9b-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9a9b-115">See also</span></span>

- [<span data-ttu-id="a9a9b-116">ICorDebugThread4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a9a9b-116">ICorDebugThread4 Interface</span></span>](icordebugthread4-interface.md)
- [<span data-ttu-id="a9a9b-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a9a9b-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="a9a9b-118">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="a9a9b-118">Debugging</span></span>](index.md)
