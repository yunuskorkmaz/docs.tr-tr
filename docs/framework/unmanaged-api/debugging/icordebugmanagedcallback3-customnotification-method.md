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
ms.openlocfilehash: 098e140b7bffb7798a37b1881f2cb2ced36bcf1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416491"
---
# <a name="icordebugmanagedcallback3customnotification-method"></a><span data-ttu-id="40a46-102">ICorDebugManagedCallback3::CustomNotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="40a46-102">ICorDebugManagedCallback3::CustomNotification Method</span></span>
<span data-ttu-id="40a46-103">Bir özel hata ayıklayıcı bildirim yükseltildiğinde gösterir.</span><span class="sxs-lookup"><span data-stu-id="40a46-103">Indicates that a custom debugger notification has been raised.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40a46-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="40a46-104">Syntax</span></span>  
  
```  
HRESULT CustomNotification(ICorDebugThread *    pThread,  
                           ICorDebugAppDomain * pAppDomain);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="40a46-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="40a46-105">Parameters</span></span>  
 `pThread`  
 <span data-ttu-id="40a46-106">[in] Bildirim gerçekleştirilen iş parçacığı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="40a46-106">[in] A pointer to the thread that raised the notification.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="40a46-107">[in] Bildirim gerçekleştirilen iş parçacığı içeren uygulama etki alanı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="40a46-107">[in] A pointer to the application domain that contains the thread that raised the notification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="40a46-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="40a46-108">Return Value</span></span>  
 <span data-ttu-id="40a46-109">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="40a46-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="40a46-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="40a46-110">HRESULT</span></span>|<span data-ttu-id="40a46-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40a46-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="40a46-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="40a46-112">S_OK</span></span>|<span data-ttu-id="40a46-113">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="40a46-113">The method completed successfully.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="40a46-114">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="40a46-114">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40a46-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="40a46-115">Remarks</span></span>  
 <span data-ttu-id="40a46-116">Sonraki çağrı [Icordebugthread4::getcurrentcustomdebuggernotification](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md) yöntemi alır geçirilmedi iş parçacığı nesnesi <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="40a46-116">A subsequent call to the [ICorDebugThread4::GetCurrentCustomDebuggerNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md) method retrieves the thread object that was passed to the <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="40a46-117">İş parçacığı nesnenin türü daha önce çağırarak etkinleştirilmiş olmalıdır [Icordebugprocess3::setenablecustomnotification](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="40a46-117">The thread object's type must have been previously enabled by calling the [ICorDebugProcess3::SetEnableCustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md) method.</span></span> <span data-ttu-id="40a46-118">Hata ayıklayıcı türüne özgü parametreler iş parçacığı nesnesi alanlardan okuyabilir ve yanıtları alanlarına depolayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="40a46-118">The debugger can read type-specific parameters from the fields of the thread object, and can store responses into fields.</span></span>  
  
 <span data-ttu-id="40a46-119">[Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) arabirimi bildirimleri veya içeriklerini türleri üzerinde hiçbir ilke uygular ve bildirimleri semantiği kesinlikle hata ayıklayıcıları, uygulamaları ve .NET Framework arasında bir sözleşme şunlardır.</span><span class="sxs-lookup"><span data-stu-id="40a46-119">The [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface imposes no policy on the types of notifications or their contents, and the semantics of the notifications are strictly a contract between debuggers, applications, and the .NET Framework.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40a46-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="40a46-120">Requirements</span></span>  
 <span data-ttu-id="40a46-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40a46-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40a46-122">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="40a46-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="40a46-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="40a46-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40a46-124">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40a46-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40a46-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="40a46-125">See Also</span></span>  
 [<span data-ttu-id="40a46-126">ICorDebugManagedCallback3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="40a46-126">ICorDebugManagedCallback3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-interface.md)  
 [<span data-ttu-id="40a46-127">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="40a46-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="40a46-128">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="40a46-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
