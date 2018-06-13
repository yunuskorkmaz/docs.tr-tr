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
ms.openlocfilehash: 0529dee17469018e872951740a5899ef8664300a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421008"
---
# <a name="icordebugthread4getcurrentcustomdebuggernotification-method"></a><span data-ttu-id="79a4f-102">ICorDebugThread4::GetCurrentCustomDebuggerNotification Metodu</span><span class="sxs-lookup"><span data-stu-id="79a4f-102">ICorDebugThread4::GetCurrentCustomDebuggerNotification Method</span></span>
<span data-ttu-id="79a4f-103">Geçerli alır [Icordebugmanagedcallback3::customnotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) nesne geçerli iş parçacığı üzerinde.</span><span class="sxs-lookup"><span data-stu-id="79a4f-103">Gets the current [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79a4f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="79a4f-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentCustomDebuggerNotification(  
    [out] ICorDebugValue **ppNotificationObject  
    );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="79a4f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="79a4f-105">Parameters</span></span>  
 `ppNOtificationObject`  
 <span data-ttu-id="79a4f-106">[out] Geçerli bir işaretçi `ICorDebugManagedCallback3::CustomNotification` nesne geçerli iş parçacığı üzerinde.</span><span class="sxs-lookup"><span data-stu-id="79a4f-106">[out] A pointer to the current `ICorDebugManagedCallback3::CustomNotification` object on the current thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79a4f-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="79a4f-107">Remarks</span></span>  
 <span data-ttu-id="79a4f-108">Değeri `ppNotificationObject` yöntemi içinden çağrılmazsa null bir `ICorDebugManagedCallback3::CustomNotification` geri veya geçerli bir bildirim nesne varsa.</span><span class="sxs-lookup"><span data-stu-id="79a4f-108">The value of `ppNotificationObject` is null if the method is not called from within a `ICorDebugManagedCallback3::CustomNotification` callback, or if no current notification object exists.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79a4f-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="79a4f-109">Requirements</span></span>  
 <span data-ttu-id="79a4f-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79a4f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79a4f-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="79a4f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="79a4f-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="79a4f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79a4f-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79a4f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79a4f-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="79a4f-114">See Also</span></span>  
 [<span data-ttu-id="79a4f-115">ICorDebugThread4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="79a4f-115">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 [<span data-ttu-id="79a4f-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="79a4f-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="79a4f-117">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="79a4f-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
