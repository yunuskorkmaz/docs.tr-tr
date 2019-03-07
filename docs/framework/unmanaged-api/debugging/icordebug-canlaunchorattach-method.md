---
title: ICorDebug::CanLaunchOrAttach Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebug.CanLaunchOrAttach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::CanLaunchOrAttach
helpviewer_keywords:
- ICorDebug::CanLaunchOrAttach method [.NET Framework debugging]
- CanLaunchOrAttach method [.NET Framework debugging]
ms.assetid: ca7723db-7c07-4cdd-bd92-fba34928b623
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c29859a54b89956e017f06b8eeb97a6171eabbb
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57476223"
---
# <a name="icordebugcanlaunchorattach-method"></a><span data-ttu-id="692fb-102">ICorDebug::CanLaunchOrAttach Yöntemi</span><span class="sxs-lookup"><span data-stu-id="692fb-102">ICorDebug::CanLaunchOrAttach Method</span></span>
<span data-ttu-id="692fb-103">Yeni bir işlem başlatılıyor veya belirtilen mevcut işleme iliştirdikten geçerli makine ve çalışma zamanı yapılandırma bağlamında mümkün olup olmadığını belirten bir HRESULT döndürür.</span><span class="sxs-lookup"><span data-stu-id="692fb-103">Returns an HRESULT that indicates whether launching a new process or attaching to the specified existing process is possible within the context of the current machine and runtime configuration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="692fb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="692fb-104">Syntax</span></span>  
  
```  
HRESULT CanLaunchOrAttach (  
    [in] DWORD      dwProcessId,  
    [in] BOOL       win32DebuggingEnabled  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="692fb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="692fb-105">Parameters</span></span>  
 `dwProcessId`  
 <span data-ttu-id="692fb-106">[in] Var olan bir işlem kimliği.</span><span class="sxs-lookup"><span data-stu-id="692fb-106">[in] The ID of an existing process.</span></span>  
  
 `win32DebuggingEnabled`  
 <span data-ttu-id="692fb-107">[in] Geçirin `true` , Win32 ile hata ayıklama etkin oluşturmayı planlıyoruz veya Win32 hata ayıklamaya etkin; Aksi takdirde eklemek için geçirmek `false`.</span><span class="sxs-lookup"><span data-stu-id="692fb-107">[in] Pass in `true` if you plan to launch with Win32 debugging enabled, or to attach with Win32 debugging enabled; otherwise, pass `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="692fb-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="692fb-108">Return Value</span></span>  
 <span data-ttu-id="692fb-109">Hata Ayıklama Hizmetleri yeni bir işlem başlatılıyor veya belirtilen işleme iliştirdikten belirlerseniz S_OK geçerli makine ve çalışma zamanı yapılandırma hakkında bilgi verilen mümkündür.</span><span class="sxs-lookup"><span data-stu-id="692fb-109">S_OK if the debugging services determine that launching a new process or attaching to the given process is possible, given the information about the current machine and runtime configuration.</span></span> <span data-ttu-id="692fb-110">HRESULT olası değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="692fb-110">Possible HRESULT values are:</span></span>  
  
-   <span data-ttu-id="692fb-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="692fb-111">S_OK</span></span>  
  
-   <span data-ttu-id="692fb-112">CORDBG_E_DEBUGGING_NOT_POSSIBLE</span><span class="sxs-lookup"><span data-stu-id="692fb-112">CORDBG_E_DEBUGGING_NOT_POSSIBLE</span></span>  
  
-   <span data-ttu-id="692fb-113">CORDBG_E_KERNEL_DEBUGGER_PRESENT</span><span class="sxs-lookup"><span data-stu-id="692fb-113">CORDBG_E_KERNEL_DEBUGGER_PRESENT</span></span>  
  
-   <span data-ttu-id="692fb-114">CORDBG_E_KERNEL_DEBUGGER_ENABLED</span><span class="sxs-lookup"><span data-stu-id="692fb-114">CORDBG_E_KERNEL_DEBUGGER_ENABLED</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="692fb-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="692fb-115">Remarks</span></span>  
 <span data-ttu-id="692fb-116">Bu yöntem, yalnızca bilgilendirme amaçlıdır.</span><span class="sxs-lookup"><span data-stu-id="692fb-116">This method is purely informational.</span></span> <span data-ttu-id="692fb-117">Arabirimi, başlatılmasını durdurmaz ya da tarafından döndürülen değerinden bağımsız olarak bir işleme ekleme `CanLaunchOrAttach`.</span><span class="sxs-lookup"><span data-stu-id="692fb-117">The interface will not stop you from launching or attaching to a process, regardless of the value returned by `CanLaunchOrAttach`.</span></span>  
  
 <span data-ttu-id="692fb-118">Planlıyorsanız Win32 ile hata ayıklama etkin başlatma veya ekleme Win32 ile hata ayıklamayı etkin geçirmek `true` için `win32DebuggingEnabled`.</span><span class="sxs-lookup"><span data-stu-id="692fb-118">If you plan to launch with Win32 debugging enabled or attach with Win32 debugging enabled, pass `true` for `win32DebuggingEnabled`.</span></span> <span data-ttu-id="692fb-119">Tarafından döndürülen HRESULT `CanLaunchOrAttach` bu seçeneği kullanırsanız farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="692fb-119">The HRESULT returned by `CanLaunchOrAttach` might differ if you use this option.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="692fb-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="692fb-120">Requirements</span></span>  
 <span data-ttu-id="692fb-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="692fb-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="692fb-122">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="692fb-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="692fb-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="692fb-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="692fb-124">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="692fb-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="692fb-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="692fb-125">See also</span></span>
- [<span data-ttu-id="692fb-126">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="692fb-126">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
