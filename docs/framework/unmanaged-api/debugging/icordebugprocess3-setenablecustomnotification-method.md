---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugProcess3:: SetEnableCustomNotification yöntemi'
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
ms.openlocfilehash: 71d1d23b1fa4ba16b26b7c9bacf7fb5cec5e5074
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746481"
---
# <a name="icordebugprocess3setenablecustomnotification-method"></a><span data-ttu-id="583a4-103">ICorDebugProcess3::SetEnableCustomNotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="583a4-103">ICorDebugProcess3::SetEnableCustomNotification Method</span></span>

<span data-ttu-id="583a4-104">Belirtilen türdeki özel hata ayıklayıcı bildirimlerini etkinleştir ve devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="583a4-104">Enables and disables custom debugger notifications of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="583a4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="583a4-105">Syntax</span></span>  
  
```cpp  
HRESULT SetEnableCustomNotification(ICorDebugClass * pClass,  
                                    BOOL fEnable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="583a4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="583a4-106">Parameters</span></span>  

 `pClass`  
 <span data-ttu-id="583a4-107">'ndaki Özel hata ayıklayıcı bildirimlerini belirten tür.</span><span class="sxs-lookup"><span data-stu-id="583a4-107">[in] The type that specifies custom debugger notifications.</span></span>  
  
 `fEnable`  
 <span data-ttu-id="583a4-108">[in] `true` özel hata ayıklayıcı bildirimlerini etkinleştirmek için; `false` bildirimleri devre dışı bırakmak için.</span><span class="sxs-lookup"><span data-stu-id="583a4-108">[in] `true` to enable custom debugger notifications; `false` to disable notifications.</span></span> <span data-ttu-id="583a4-109">`false` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="583a4-109">The default value is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="583a4-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="583a4-110">Remarks</span></span>  

 <span data-ttu-id="583a4-111">Ne zaman `fEnable` ayarlandığında `true` , yöntemine yapılan çağrılar <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> bir [ICorDebugManagedCallback3:: CustomNotification](icordebugmanagedcallback3-customnotification-method.md) geri çağırması tetikler.</span><span class="sxs-lookup"><span data-stu-id="583a4-111">When `fEnable` is set to `true`, calls to the <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> method trigger an [ICorDebugManagedCallback3::CustomNotification](icordebugmanagedcallback3-customnotification-method.md) callback.</span></span> <span data-ttu-id="583a4-112">Bildirimler varsayılan olarak devre dışıdır; Bu nedenle, hata ayıklayıcı, bildiği ve işlemek istediği herhangi bir bildirim türü belirtmelidir.</span><span class="sxs-lookup"><span data-stu-id="583a4-112">Notifications are disabled by default; therefore, the debugger must specify any notification types it knows about and wants to handle.</span></span> <span data-ttu-id="583a4-113">[ICorDebugClass](icordebug-interface.md) sınıfı, uygulama etki alanı tarafından kapsamlandırdığı için, hata ayıklayıcının `SetEnableCustomNotification` tüm işlem genelinde bildirimi almasını istemesi durumunda, işlemdeki her uygulama etki alanı için çağrı yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="583a4-113">Because the [ICorDebugClass](icordebug-interface.md) class is scoped by application domain, the debugger must call `SetEnableCustomNotification` for every application domain in the process if it wants to receive the notification across the entire process.</span></span>  
  
 <span data-ttu-id="583a4-114">.NET Framework 4 ' te başlayarak, tek desteklenen bildirim bir çapraz iş parçacığı bağımlılığı bildirimidir.</span><span class="sxs-lookup"><span data-stu-id="583a4-114">Starting with the .NET Framework 4, the only supported notification is a cross-thread dependency notification.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="583a4-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="583a4-115">Requirements</span></span>  

 <span data-ttu-id="583a4-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="583a4-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="583a4-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="583a4-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="583a4-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="583a4-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="583a4-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="583a4-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="583a4-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="583a4-120">See also</span></span>

- [<span data-ttu-id="583a4-121">ICorDebugProcess3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="583a4-121">ICorDebugProcess3 Interface</span></span>](icordebugprocess3-interface.md)
- [<span data-ttu-id="583a4-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="583a4-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="583a4-123">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="583a4-123">Debugging</span></span>](index.md)
