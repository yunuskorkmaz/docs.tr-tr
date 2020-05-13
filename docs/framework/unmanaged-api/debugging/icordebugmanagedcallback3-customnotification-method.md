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
ms.openlocfilehash: 8a4620e591cc80efb5c0fd53b0edf3a35849c421
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209766"
---
# <a name="icordebugmanagedcallback3customnotification-method"></a><span data-ttu-id="a9efb-102">ICorDebugManagedCallback3::CustomNotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a9efb-102">ICorDebugManagedCallback3::CustomNotification Method</span></span>
<span data-ttu-id="a9efb-103">Özel bir hata ayıklayıcı bildiriminin yapıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a9efb-103">Indicates that a custom debugger notification has been raised.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9efb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a9efb-104">Syntax</span></span>  
  
```cpp  
HRESULT CustomNotification(ICorDebugThread *    pThread,  
                           ICorDebugAppDomain * pAppDomain);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9efb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a9efb-105">Parameters</span></span>  
 `pThread`  
 <span data-ttu-id="a9efb-106">'ndaki Bildirimi oluşturan iş parçacığına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a9efb-106">[in] A pointer to the thread that raised the notification.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="a9efb-107">'ndaki Bildirimi oluşturan iş parçacığını içeren uygulama etki alanına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a9efb-107">[in] A pointer to the application domain that contains the thread that raised the notification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a9efb-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a9efb-108">Return Value</span></span>  
 <span data-ttu-id="a9efb-109">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="a9efb-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a9efb-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a9efb-110">HRESULT</span></span>|<span data-ttu-id="a9efb-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a9efb-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a9efb-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="a9efb-112">S_OK</span></span>|<span data-ttu-id="a9efb-113">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="a9efb-113">The method completed successfully.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="a9efb-114">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="a9efb-114">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9efb-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a9efb-115">Remarks</span></span>  
 <span data-ttu-id="a9efb-116">[ICorDebugThread4:: GetCurrentCustomDebuggerNotification](icordebugthread4-getcurrentcustomdebuggernotification-method.md) yöntemine sonraki bir çağrı, metoduna geçirilen iş parçacığı nesnesini alır <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="a9efb-116">A subsequent call to the [ICorDebugThread4::GetCurrentCustomDebuggerNotification](icordebugthread4-getcurrentcustomdebuggernotification-method.md) method retrieves the thread object that was passed to the <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a9efb-117">İş parçacığı nesnesinin türü, [ICorDebugProcess3:: SetEnableCustomNotification](icordebugprocess3-setenablecustomnotification-method.md) yöntemi çağırarak önceden etkinleştirilmiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a9efb-117">The thread object's type must have been previously enabled by calling the [ICorDebugProcess3::SetEnableCustomNotification](icordebugprocess3-setenablecustomnotification-method.md) method.</span></span> <span data-ttu-id="a9efb-118">Hata ayıklayıcı, iş parçacığı nesnesi alanlarından türe özgü parametreleri okuyabilir ve yanıtları alanlara depolayabilirler.</span><span class="sxs-lookup"><span data-stu-id="a9efb-118">The debugger can read type-specific parameters from the fields of the thread object, and can store responses into fields.</span></span>  
  
 <span data-ttu-id="a9efb-119">[ICorDebug](icordebug-interface.md) arabirimi, bildirim türleri veya içerikleri üzerinde hiçbir ilke vermez ve bildirimlerin semantiği, hata ayıklayıcılar, uygulamalar ve .NET Framework arasındaki bir anlaşmada yer alır.</span><span class="sxs-lookup"><span data-stu-id="a9efb-119">The [ICorDebug](icordebug-interface.md) interface imposes no policy on the types of notifications or their contents, and the semantics of the notifications are strictly a contract between debuggers, applications, and the .NET Framework.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9efb-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a9efb-120">Requirements</span></span>  
 <span data-ttu-id="a9efb-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9efb-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9efb-122">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a9efb-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a9efb-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a9efb-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a9efb-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9efb-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9efb-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9efb-125">See also</span></span>

- [<span data-ttu-id="a9efb-126">ICorDebugManagedCallback3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a9efb-126">ICorDebugManagedCallback3 Interface</span></span>](icordebugmanagedcallback3-interface.md)
- [<span data-ttu-id="a9efb-127">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a9efb-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="a9efb-128">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="a9efb-128">Debugging</span></span>](index.md)
