---
title: ICorDebugManagedCallback3::CustomNotification Yöntemi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b086c27d73324b4d834c9afa9e7aea20bf6d9148
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59193583"
---
# <a name="icordebugmanagedcallback3customnotification-method"></a><span data-ttu-id="b73f8-102">ICorDebugManagedCallback3::CustomNotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b73f8-102">ICorDebugManagedCallback3::CustomNotification Method</span></span>
<span data-ttu-id="b73f8-103">Bir özel hata ayıklayıcı bildiriminin tetiklendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b73f8-103">Indicates that a custom debugger notification has been raised.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b73f8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b73f8-104">Syntax</span></span>  
  
```  
HRESULT CustomNotification(ICorDebugThread *    pThread,  
                           ICorDebugAppDomain * pAppDomain);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b73f8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b73f8-105">Parameters</span></span>  
 `pThread`  
 <span data-ttu-id="b73f8-106">[in] Bildirim oluşturulan iş parçacığına bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b73f8-106">[in] A pointer to the thread that raised the notification.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="b73f8-107">[in] Bildirim harekete geçirilen iş parçacığı içeren uygulama etki alanı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b73f8-107">[in] A pointer to the application domain that contains the thread that raised the notification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b73f8-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b73f8-108">Return Value</span></span>  
 <span data-ttu-id="b73f8-109">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="b73f8-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="b73f8-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b73f8-110">HRESULT</span></span>|<span data-ttu-id="b73f8-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b73f8-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b73f8-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="b73f8-112">S_OK</span></span>|<span data-ttu-id="b73f8-113">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="b73f8-113">The method completed successfully.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="b73f8-114">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="b73f8-114">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b73f8-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b73f8-115">Remarks</span></span>  
 <span data-ttu-id="b73f8-116">Bir sonraki çağrı [Icordebugthread4::getcurrentcustomdebuggernotification](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md) yöntemi geçildi iş parçacığı nesnesi alır <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b73f8-116">A subsequent call to the [ICorDebugThread4::GetCurrentCustomDebuggerNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md) method retrieves the thread object that was passed to the <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b73f8-117">İş parçacığı nesnesinin türü daha önce çağırarak etkinleştirilmiş olmalıdır [Icordebugprocess3::setenablecustomnotification](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b73f8-117">The thread object's type must have been previously enabled by calling the [ICorDebugProcess3::SetEnableCustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md) method.</span></span> <span data-ttu-id="b73f8-118">Hata ayıklayıcı, türe özgü parametreler iş parçacığı nesnesinin alanları okuyabilir ve yanıtları alanlarına depolayabilir.</span><span class="sxs-lookup"><span data-stu-id="b73f8-118">The debugger can read type-specific parameters from the fields of the thread object, and can store responses into fields.</span></span>  
  
 <span data-ttu-id="b73f8-119">[Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) arabirimi ilkesiz bildirimleri veya içeriklerinin türlerini getirir ve bildirimleri semantiği kesinlikle hata ayıklayıcılar, uygulamaları ve .NET Framework arasında bir sözleşme olan.</span><span class="sxs-lookup"><span data-stu-id="b73f8-119">The [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface imposes no policy on the types of notifications or their contents, and the semantics of the notifications are strictly a contract between debuggers, applications, and the .NET Framework.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b73f8-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b73f8-120">Requirements</span></span>  
 <span data-ttu-id="b73f8-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b73f8-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b73f8-122">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b73f8-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b73f8-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b73f8-123">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b73f8-124">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="b73f8-124">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b73f8-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b73f8-125">See also</span></span>

- [<span data-ttu-id="b73f8-126">ICorDebugManagedCallback3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b73f8-126">ICorDebugManagedCallback3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-interface.md)
- [<span data-ttu-id="b73f8-127">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b73f8-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="b73f8-128">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="b73f8-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
