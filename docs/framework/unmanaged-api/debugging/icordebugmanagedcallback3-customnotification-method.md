---
description: 'Daha fazla bilgi edinin: ICorDebugManagedCallback3:: CustomNotification Yöntemi'
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
ms.openlocfilehash: 18210e9c65afa0655374fb038d30516cfed02052
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691724"
---
# <a name="icordebugmanagedcallback3customnotification-method"></a><span data-ttu-id="3acd4-103">ICorDebugManagedCallback3::CustomNotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3acd4-103">ICorDebugManagedCallback3::CustomNotification Method</span></span>

<span data-ttu-id="3acd4-104">Özel bir hata ayıklayıcı bildiriminin yapıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3acd4-104">Indicates that a custom debugger notification has been raised.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3acd4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3acd4-105">Syntax</span></span>  
  
```cpp  
HRESULT CustomNotification(ICorDebugThread *    pThread,  
                           ICorDebugAppDomain * pAppDomain);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3acd4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3acd4-106">Parameters</span></span>  

 `pThread`  
 <span data-ttu-id="3acd4-107">'ndaki Bildirimi oluşturan iş parçacığına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3acd4-107">[in] A pointer to the thread that raised the notification.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="3acd4-108">'ndaki Bildirimi oluşturan iş parçacığını içeren uygulama etki alanına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3acd4-108">[in] A pointer to the application domain that contains the thread that raised the notification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3acd4-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3acd4-109">Return Value</span></span>  

 <span data-ttu-id="3acd4-110">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="3acd4-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="3acd4-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3acd4-111">HRESULT</span></span>|<span data-ttu-id="3acd4-112">Description</span><span class="sxs-lookup"><span data-stu-id="3acd4-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3acd4-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="3acd4-113">S_OK</span></span>|<span data-ttu-id="3acd4-114">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="3acd4-114">The method completed successfully.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="3acd4-115">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="3acd4-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3acd4-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3acd4-116">Remarks</span></span>  

 <span data-ttu-id="3acd4-117">[ICorDebugThread4:: GetCurrentCustomDebuggerNotification](icordebugthread4-getcurrentcustomdebuggernotification-method.md) yöntemine sonraki bir çağrı, metoduna geçirilen iş parçacığı nesnesini alır <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="3acd4-117">A subsequent call to the [ICorDebugThread4::GetCurrentCustomDebuggerNotification](icordebugthread4-getcurrentcustomdebuggernotification-method.md) method retrieves the thread object that was passed to the <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="3acd4-118">İş parçacığı nesnesinin türü, [ICorDebugProcess3:: SetEnableCustomNotification](icordebugprocess3-setenablecustomnotification-method.md) yöntemi çağırarak önceden etkinleştirilmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3acd4-118">The thread object's type must have been previously enabled by calling the [ICorDebugProcess3::SetEnableCustomNotification](icordebugprocess3-setenablecustomnotification-method.md) method.</span></span> <span data-ttu-id="3acd4-119">Hata ayıklayıcı, iş parçacığı nesnesi alanlarından türe özgü parametreleri okuyabilir ve yanıtları alanlara depolayabilirler.</span><span class="sxs-lookup"><span data-stu-id="3acd4-119">The debugger can read type-specific parameters from the fields of the thread object, and can store responses into fields.</span></span>  
  
 <span data-ttu-id="3acd4-120">[ICorDebug](icordebug-interface.md) arabirimi, bildirim türleri veya içerikleri üzerinde hiçbir ilke vermez ve bildirimlerin semantiği, hata ayıklayıcılar, uygulamalar ve .NET Framework arasındaki bir anlaşmada yer alır.</span><span class="sxs-lookup"><span data-stu-id="3acd4-120">The [ICorDebug](icordebug-interface.md) interface imposes no policy on the types of notifications or their contents, and the semantics of the notifications are strictly a contract between debuggers, applications, and the .NET Framework.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3acd4-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3acd4-121">Requirements</span></span>  

 <span data-ttu-id="3acd4-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3acd4-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3acd4-123">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3acd4-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3acd4-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3acd4-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3acd4-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3acd4-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3acd4-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3acd4-126">See also</span></span>

- [<span data-ttu-id="3acd4-127">ICorDebugManagedCallback3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3acd4-127">ICorDebugManagedCallback3 Interface</span></span>](icordebugmanagedcallback3-interface.md)
- [<span data-ttu-id="3acd4-128">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3acd4-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="3acd4-129">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="3acd4-129">Debugging</span></span>](index.md)
