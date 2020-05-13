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
ms.openlocfilehash: 76ad1c0ac421f05cf30f6d3d1f3e65848796a0c7
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378692"
---
# <a name="icordebugthread4getcurrentcustomdebuggernotification-method"></a><span data-ttu-id="865b4-102">ICorDebugThread4::GetCurrentCustomDebuggerNotification Metodu</span><span class="sxs-lookup"><span data-stu-id="865b4-102">ICorDebugThread4::GetCurrentCustomDebuggerNotification Method</span></span>

<span data-ttu-id="865b4-103">Geçerli iş parçacığında geçerli [ICorDebugManagedCallback3:: CustomNotification](icordebugmanagedcallback3-customnotification-method.md) nesnesini alır.</span><span class="sxs-lookup"><span data-stu-id="865b4-103">Gets the current [ICorDebugManagedCallback3::CustomNotification](icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>

## <a name="syntax"></a><span data-ttu-id="865b4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="865b4-104">Syntax</span></span>

```cpp
HRESULT GetCurrentCustomDebuggerNotification(
    [out] ICorDebugValue **ppNotificationObject
    );
```

## <a name="parameters"></a><span data-ttu-id="865b4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="865b4-105">Parameters</span></span>

`ppNotificationObject`\
<span data-ttu-id="865b4-106">dışı `ICorDebugManagedCallback3::CustomNotification`Geçerli iş parçacığındaki geçerli nesneye yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="865b4-106">[out] A pointer to the current `ICorDebugManagedCallback3::CustomNotification` object on the current thread.</span></span>

## <a name="remarks"></a><span data-ttu-id="865b4-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="865b4-107">Remarks</span></span>

<span data-ttu-id="865b4-108">`ppNotificationObject`Yöntemi bir geri çağırma içinden çağrılmaması `ICorDebugManagedCallback3::CustomNotification` veya geçerli bir bildirim nesnesi yoksa değeri null olur.</span><span class="sxs-lookup"><span data-stu-id="865b4-108">The value of `ppNotificationObject` is null if the method is not called from within a `ICorDebugManagedCallback3::CustomNotification` callback, or if no current notification object exists.</span></span>

## <a name="requirements"></a><span data-ttu-id="865b4-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="865b4-109">Requirements</span></span>

<span data-ttu-id="865b4-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="865b4-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="865b4-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="865b4-111">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="865b4-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="865b4-112">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="865b4-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="865b4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="865b4-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="865b4-114">See also</span></span>

- [<span data-ttu-id="865b4-115">ICorDebugThread4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="865b4-115">ICorDebugThread4 Interface</span></span>](icordebugthread4-interface.md)
- [<span data-ttu-id="865b4-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="865b4-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="865b4-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="865b4-117">Debugging</span></span>](index.md)
