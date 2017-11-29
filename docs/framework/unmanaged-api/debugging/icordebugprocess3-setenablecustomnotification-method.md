---
title: "ICorDebugProcess3::SetEnableCustomNotification Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess3.SetEnableCustomNotification Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess3::SetEnableCustomNotification
helpviewer_keywords:
- ICorDebugProcess3::SetEnableCustomNotification method [.NET Framework debugging]
- SetEnableCustomNotification method [.NET Framework debugging]
ms.assetid: afd88ee9-2589-4461-a75a-9b6fe55a2525
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6d4c6604d57b28cca33007b9d72d4b4c06e6d062
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess3setenablecustomnotification-method"></a><span data-ttu-id="fc305-102">ICorDebugProcess3::SetEnableCustomNotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fc305-102">ICorDebugProcess3::SetEnableCustomNotification Method</span></span>
<span data-ttu-id="fc305-103">Belirtilen türün özel hata ayıklayıcı bildirimleri devre dışı bırakır ve sağlar.</span><span class="sxs-lookup"><span data-stu-id="fc305-103">Enables and disables custom debugger notifications of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc305-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fc305-104">Syntax</span></span>  
  
```  
HRESULT SetEnableCustomNotification(ICorDebugClass * pClass,  
                                    BOOL fEnable);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fc305-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fc305-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="fc305-106">[in] Özel hata ayıklayıcı bildirimleri belirtir türü.</span><span class="sxs-lookup"><span data-stu-id="fc305-106">[in] The type that specifies custom debugger notifications.</span></span>  
  
 `fEnable`  
 <span data-ttu-id="fc305-107">[in] `true` özel hata ayıklayıcı bildirimlerini; etkinleştirmek için `false` bildirimleri devre dışı bırakmak için.</span><span class="sxs-lookup"><span data-stu-id="fc305-107">[in] `true` to enable custom debugger notifications; `false` to disable notifications.</span></span> <span data-ttu-id="fc305-108">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="fc305-108">The default value is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc305-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fc305-109">Remarks</span></span>  
 <span data-ttu-id="fc305-110">Zaman `fEnable` ayarlanır `true`, çağrılar <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> yöntemi tetikleyici bir [Icordebugmanagedcallback3::customnotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="fc305-110">When `fEnable` is set to `true`, calls to the <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> method trigger an [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) callback.</span></span> <span data-ttu-id="fc305-111">Bildirimler, varsayılan olarak devre dışıdır; Bu nedenle, hata ayıklayıcı bildiği ve işlemek istediği her bildirim türünü belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fc305-111">Notifications are disabled by default; therefore, the debugger must specify any notification types it knows about and wants to handle.</span></span> <span data-ttu-id="fc305-112">Çünkü [Icordebugclass](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) sınıfı uygulama etki alanı tarafından kapsamlı, hata ayıklayıcı çağırmalısınız `SetEnableCustomNotification` sürecinin tamamı bildirim almak istiyorsa, işlemdeki her uygulama etki alanı için.</span><span class="sxs-lookup"><span data-stu-id="fc305-112">Because the [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) class is scoped by application domain, the debugger must call `SetEnableCustomNotification` for every application domain in the process if it wants to receive the notification across the entire process.</span></span>  
  
 <span data-ttu-id="fc305-113">İle başlayarak [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], yalnızca desteklenen bildirim iş parçacıkları arası bağımlılık bildirimi.</span><span class="sxs-lookup"><span data-stu-id="fc305-113">Starting with the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], the only supported notification is a cross-thread dependency notification.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc305-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fc305-114">Requirements</span></span>  
 <span data-ttu-id="fc305-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc305-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc305-116">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fc305-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fc305-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc305-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc305-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc305-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc305-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fc305-119">See Also</span></span>  
 [<span data-ttu-id="fc305-120">Icordebugprocess3 arabirimi</span><span class="sxs-lookup"><span data-stu-id="fc305-120">ICorDebugProcess3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)  
 [<span data-ttu-id="fc305-121">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fc305-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="fc305-122">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="fc305-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
