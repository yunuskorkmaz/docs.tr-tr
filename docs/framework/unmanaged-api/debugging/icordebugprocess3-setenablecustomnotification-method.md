---
title: ICorDebugProcess3::SetEnableCustomNotification Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess3.SetEnableCustomNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess3::SetEnableCustomNotification
helpviewer_keywords:
- ICorDebugProcess3::SetEnableCustomNotification method [.NET Framework debugging]
- SetEnableCustomNotification method [.NET Framework debugging]
ms.assetid: afd88ee9-2589-4461-a75a-9b6fe55a2525
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7501a8a0f8368049c87b3c90e1e707e12773a853
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54531648"
---
# <a name="icordebugprocess3setenablecustomnotification-method"></a><span data-ttu-id="2407d-102">ICorDebugProcess3::SetEnableCustomNotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2407d-102">ICorDebugProcess3::SetEnableCustomNotification Method</span></span>
<span data-ttu-id="2407d-103">Sağlar ve belirtilen türün özel hata ayıklayıcı bildirimlerini devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="2407d-103">Enables and disables custom debugger notifications of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2407d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2407d-104">Syntax</span></span>  
  
```  
HRESULT SetEnableCustomNotification(ICorDebugClass * pClass,  
                                    BOOL fEnable);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2407d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2407d-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="2407d-106">[in] Özel hata ayıklayıcı bildirimlerini belirten türü.</span><span class="sxs-lookup"><span data-stu-id="2407d-106">[in] The type that specifies custom debugger notifications.</span></span>  
  
 `fEnable`  
 <span data-ttu-id="2407d-107">[in] `true` ; özel hata ayıklayıcı bildirimlerini etkinleştirmek için `false` bildirimlerini devre dışı.</span><span class="sxs-lookup"><span data-stu-id="2407d-107">[in] `true` to enable custom debugger notifications; `false` to disable notifications.</span></span> <span data-ttu-id="2407d-108">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="2407d-108">The default value is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2407d-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2407d-109">Remarks</span></span>  
 <span data-ttu-id="2407d-110">Zaman `fEnable` ayarlanır `true`, çağrılar <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> yöntemi tetikleyici bir [Icordebugmanagedcallback3::customnotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="2407d-110">When `fEnable` is set to `true`, calls to the <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> method trigger an [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) callback.</span></span> <span data-ttu-id="2407d-111">Bildirimleri varsayılan olarak devre dışıdır; Bu nedenle, hata ayıklayıcı bildiği ve işlemek istediği herhangi bir bildirim türü belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2407d-111">Notifications are disabled by default; therefore, the debugger must specify any notification types it knows about and wants to handle.</span></span> <span data-ttu-id="2407d-112">Çünkü [Icordebugclass](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) sınıfı uygulama etki alanına göre kapsamlı, hata ayıklayıcı çağırmalıdır `SetEnableCustomNotification` tüm işlem bildirimi almak istiyorsa, işlemdeki her bir uygulama etki alanı.</span><span class="sxs-lookup"><span data-stu-id="2407d-112">Because the [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) class is scoped by application domain, the debugger must call `SetEnableCustomNotification` for every application domain in the process if it wants to receive the notification across the entire process.</span></span>  
  
 <span data-ttu-id="2407d-113">İle başlayarak [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], yalnızca desteklenen bildirim iş parçacıkları arası bağımlılık bildirimi.</span><span class="sxs-lookup"><span data-stu-id="2407d-113">Starting with the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], the only supported notification is a cross-thread dependency notification.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2407d-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2407d-114">Requirements</span></span>  
 <span data-ttu-id="2407d-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2407d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2407d-116">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2407d-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2407d-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2407d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2407d-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2407d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2407d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2407d-119">See also</span></span>
- [<span data-ttu-id="2407d-120">ICorDebugProcess3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2407d-120">ICorDebugProcess3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)
- [<span data-ttu-id="2407d-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2407d-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="2407d-122">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="2407d-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
