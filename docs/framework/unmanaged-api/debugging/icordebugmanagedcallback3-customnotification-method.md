---
title: "ICorDebugManagedCallback3::CustomNotification Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugManagedCallback3.CustomNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback3::CustomNotification
helpviewer_keywords:
- ICorDebugManagedCallback3::CustomNotification method [.NET Framework debugging]
- CustomNotification method [.NET Framework debugging]
ms.assetid: 5e5422ac-afa1-403d-a894-2d7348673e38
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9c42443b0d1e355d4233909357c341763298160e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback3customnotification-method"></a><span data-ttu-id="9a0c0-102">ICorDebugManagedCallback3::CustomNotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9a0c0-102">ICorDebugManagedCallback3::CustomNotification Method</span></span>
<span data-ttu-id="9a0c0-103">Bir özel hata ayıklayıcı bildirim yükseltildiğinde gösterir.</span><span class="sxs-lookup"><span data-stu-id="9a0c0-103">Indicates that a custom debugger notification has been raised.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a0c0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9a0c0-104">Syntax</span></span>  
  
```  
HRESULT CustomNotification(ICorDebugThread *    pThread,  
                           ICorDebugAppDomain * pAppDomain);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9a0c0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9a0c0-105">Parameters</span></span>  
 `pThread`  
 <span data-ttu-id="9a0c0-106">[in] Bildirim gerçekleştirilen iş parçacığı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9a0c0-106">[in] A pointer to the thread that raised the notification.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="9a0c0-107">[in] Bildirim gerçekleştirilen iş parçacığı içeren uygulama etki alanı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9a0c0-107">[in] A pointer to the application domain that contains the thread that raised the notification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9a0c0-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9a0c0-108">Return Value</span></span>  
 <span data-ttu-id="9a0c0-109">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="9a0c0-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="9a0c0-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9a0c0-110">HRESULT</span></span>|<span data-ttu-id="9a0c0-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9a0c0-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9a0c0-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="9a0c0-112">S_OK</span></span>|<span data-ttu-id="9a0c0-113">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="9a0c0-113">The method completed successfully.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="9a0c0-114">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="9a0c0-114">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a0c0-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9a0c0-115">Remarks</span></span>  
 <span data-ttu-id="9a0c0-116">Sonraki çağrı [Icordebugthread4::getcurrentcustomdebuggernotification](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md) yöntemi alır geçirilmedi iş parçacığı nesnesi <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9a0c0-116">A subsequent call to the [ICorDebugThread4::GetCurrentCustomDebuggerNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md) method retrieves the thread object that was passed to the <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="9a0c0-117">İş parçacığı nesnenin türü daha önce çağırarak etkinleştirilmiş olmalıdır [Icordebugprocess3::setenablecustomnotification](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9a0c0-117">The thread object's type must have been previously enabled by calling the [ICorDebugProcess3::SetEnableCustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md) method.</span></span> <span data-ttu-id="9a0c0-118">Hata ayıklayıcı türüne özgü parametreler iş parçacığı nesnesi alanlardan okuyabilir ve yanıtları alanlarına depolayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a0c0-118">The debugger can read type-specific parameters from the fields of the thread object, and can store responses into fields.</span></span>  
  
 <span data-ttu-id="9a0c0-119">[Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) arabirimi bildirimleri veya içeriklerini türleri üzerinde hiçbir ilke uygular ve bildirimleri semantiği kesinlikle hata ayıklayıcıları, uygulamaları ve .NET Framework arasında bir sözleşme şunlardır.</span><span class="sxs-lookup"><span data-stu-id="9a0c0-119">The [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface imposes no policy on the types of notifications or their contents, and the semantics of the notifications are strictly a contract between debuggers, applications, and the .NET Framework.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a0c0-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9a0c0-120">Requirements</span></span>  
 <span data-ttu-id="9a0c0-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a0c0-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a0c0-122">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9a0c0-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9a0c0-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a0c0-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a0c0-124">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a0c0-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a0c0-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9a0c0-125">See Also</span></span>  
 [<span data-ttu-id="9a0c0-126">ICorDebugManagedCallback3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9a0c0-126">ICorDebugManagedCallback3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-interface.md)  
 [<span data-ttu-id="9a0c0-127">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9a0c0-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="9a0c0-128">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="9a0c0-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
