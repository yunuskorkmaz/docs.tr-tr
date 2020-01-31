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
ms.openlocfilehash: f2f365f3fe1568f2dd3bad677dd77a13946002e1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792462"
---
# <a name="icordebugprocess3setenablecustomnotification-method"></a><span data-ttu-id="e9a29-102">ICorDebugProcess3::SetEnableCustomNotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e9a29-102">ICorDebugProcess3::SetEnableCustomNotification Method</span></span>
<span data-ttu-id="e9a29-103">Belirtilen türdeki özel hata ayıklayıcı bildirimlerini etkinleştir ve devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="e9a29-103">Enables and disables custom debugger notifications of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9a29-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e9a29-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnableCustomNotification(ICorDebugClass * pClass,  
                                    BOOL fEnable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9a29-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e9a29-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="e9a29-106">'ndaki Özel hata ayıklayıcı bildirimlerini belirten tür.</span><span class="sxs-lookup"><span data-stu-id="e9a29-106">[in] The type that specifies custom debugger notifications.</span></span>  
  
 `fEnable`  
 <span data-ttu-id="e9a29-107">[in] özel hata ayıklayıcı bildirimlerini etkinleştirmek için `true`; bildirimleri devre dışı bırakmak için `false`.</span><span class="sxs-lookup"><span data-stu-id="e9a29-107">[in] `true` to enable custom debugger notifications; `false` to disable notifications.</span></span> <span data-ttu-id="e9a29-108">Varsayılan değer `false` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="e9a29-108">The default value is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9a29-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e9a29-109">Remarks</span></span>  
 <span data-ttu-id="e9a29-110">`fEnable` `true`olarak ayarlandığında <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> yöntemine yapılan çağrılar bir [ICorDebugManagedCallback3:: CustomNotification](icordebugmanagedcallback3-customnotification-method.md) geri çağırması tetikler.</span><span class="sxs-lookup"><span data-stu-id="e9a29-110">When `fEnable` is set to `true`, calls to the <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> method trigger an [ICorDebugManagedCallback3::CustomNotification](icordebugmanagedcallback3-customnotification-method.md) callback.</span></span> <span data-ttu-id="e9a29-111">Bildirimler varsayılan olarak devre dışıdır; Bu nedenle, hata ayıklayıcı, bildiği ve işlemek istediği herhangi bir bildirim türü belirtmelidir.</span><span class="sxs-lookup"><span data-stu-id="e9a29-111">Notifications are disabled by default; therefore, the debugger must specify any notification types it knows about and wants to handle.</span></span> <span data-ttu-id="e9a29-112">[ICorDebugClass](icordebug-interface.md) sınıfı, uygulama etki alanı tarafından kapsamlandırdığı için, hata ayıklayıcının tüm işlem genelinde bildirimi almasını istiyorsa, işlemdeki her uygulama etki alanı için `SetEnableCustomNotification` çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e9a29-112">Because the [ICorDebugClass](icordebug-interface.md) class is scoped by application domain, the debugger must call `SetEnableCustomNotification` for every application domain in the process if it wants to receive the notification across the entire process.</span></span>  
  
 <span data-ttu-id="e9a29-113">.NET Framework 4 ' te başlayarak, tek desteklenen bildirim bir çapraz iş parçacığı bağımlılığı bildirimidir.</span><span class="sxs-lookup"><span data-stu-id="e9a29-113">Starting with the .NET Framework 4, the only supported notification is a cross-thread dependency notification.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9a29-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e9a29-114">Requirements</span></span>  
 <span data-ttu-id="e9a29-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9a29-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9a29-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e9a29-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e9a29-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e9a29-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9a29-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9a29-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9a29-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9a29-119">See also</span></span>

- [<span data-ttu-id="e9a29-120">ICorDebugProcess3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9a29-120">ICorDebugProcess3 Interface</span></span>](icordebugprocess3-interface.md)
- [<span data-ttu-id="e9a29-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e9a29-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="e9a29-122">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="e9a29-122">Debugging</span></span>](index.md)
