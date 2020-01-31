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
ms.openlocfilehash: 28b9fb5a25981e5e37a5f1bbb797baeac45e0028
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793571"
---
# <a name="icordebugcanlaunchorattach-method"></a><span data-ttu-id="f5634-102">ICorDebug::CanLaunchOrAttach Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f5634-102">ICorDebug::CanLaunchOrAttach Method</span></span>
<span data-ttu-id="f5634-103">Geçerli makine ve çalışma zamanı yapılandırması bağlamında yeni bir işlemin başlatılıp başlatılmayacağını veya belirtilen mevcut işleme iliştirilip mümkün olup olmadığını belirten bir HRESULT döndürür.</span><span class="sxs-lookup"><span data-stu-id="f5634-103">Returns an HRESULT that indicates whether launching a new process or attaching to the specified existing process is possible within the context of the current machine and runtime configuration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5634-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f5634-104">Syntax</span></span>  
  
```cpp  
HRESULT CanLaunchOrAttach (  
    [in] DWORD      dwProcessId,  
    [in] BOOL       win32DebuggingEnabled  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5634-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f5634-105">Parameters</span></span>  
 `dwProcessId`  
 <span data-ttu-id="f5634-106">'ndaki Mevcut bir işlemin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="f5634-106">[in] The ID of an existing process.</span></span>  
  
 `win32DebuggingEnabled`  
 <span data-ttu-id="f5634-107">'ndaki Win32 hata ayıklaması etkinken başlatmayı planlıyorsanız veya Win32 hata ayıklaması etkin olarak eklemek istiyorsanız `true` geçirin; Aksi takdirde, `false`geçirin.</span><span class="sxs-lookup"><span data-stu-id="f5634-107">[in] Pass in `true` if you plan to launch with Win32 debugging enabled, or to attach with Win32 debugging enabled; otherwise, pass `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f5634-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f5634-108">Return Value</span></span>  
 <span data-ttu-id="f5634-109">Hata ayıklama Hizmetleri, yeni bir işlem başlatmayı veya belirli bir işleme eklemeyi saptarken, geçerli makine ve çalışma zamanı yapılandırmasıyla ilgili bilgiler verildiğinde S_OK.</span><span class="sxs-lookup"><span data-stu-id="f5634-109">S_OK if the debugging services determine that launching a new process or attaching to the given process is possible, given the information about the current machine and runtime configuration.</span></span> <span data-ttu-id="f5634-110">Olası HRESULT değerleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f5634-110">Possible HRESULT values are:</span></span>  
  
- <span data-ttu-id="f5634-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f5634-111">S_OK</span></span>  
  
- <span data-ttu-id="f5634-112">CORDBG_E_DEBUGGING_NOT_POSSIBLE</span><span class="sxs-lookup"><span data-stu-id="f5634-112">CORDBG_E_DEBUGGING_NOT_POSSIBLE</span></span>  
  
- <span data-ttu-id="f5634-113">CORDBG_E_KERNEL_DEBUGGER_PRESENT</span><span class="sxs-lookup"><span data-stu-id="f5634-113">CORDBG_E_KERNEL_DEBUGGER_PRESENT</span></span>  
  
- <span data-ttu-id="f5634-114">CORDBG_E_KERNEL_DEBUGGER_ENABLED</span><span class="sxs-lookup"><span data-stu-id="f5634-114">CORDBG_E_KERNEL_DEBUGGER_ENABLED</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5634-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f5634-115">Remarks</span></span>  
 <span data-ttu-id="f5634-116">Bu yöntem yalnızca bilgilendirme amaçlıdır.</span><span class="sxs-lookup"><span data-stu-id="f5634-116">This method is purely informational.</span></span> <span data-ttu-id="f5634-117">Arabirim, `CanLaunchOrAttach`tarafından döndürülen değerden bağımsız olarak, bir işlemden başlatma veya ekleme işlemini durdurmayacak.</span><span class="sxs-lookup"><span data-stu-id="f5634-117">The interface will not stop you from launching or attaching to a process, regardless of the value returned by `CanLaunchOrAttach`.</span></span>  
  
 <span data-ttu-id="f5634-118">Win32 hata ayıklaması etkinleştirilmiş veya Win32 hata ayıklama özelliği etkinken birlikte başlatmayı planlıyorsanız, `win32DebuggingEnabled`için `true` geçirin.</span><span class="sxs-lookup"><span data-stu-id="f5634-118">If you plan to launch with Win32 debugging enabled or attach with Win32 debugging enabled, pass `true` for `win32DebuggingEnabled`.</span></span> <span data-ttu-id="f5634-119">`CanLaunchOrAttach` tarafından döndürülen HRESULT, bu seçeneği kullanırsanız farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="f5634-119">The HRESULT returned by `CanLaunchOrAttach` might differ if you use this option.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5634-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f5634-120">Requirements</span></span>  
 <span data-ttu-id="f5634-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5634-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5634-122">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f5634-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f5634-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f5634-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5634-124">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5634-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5634-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f5634-125">See also</span></span>

- [<span data-ttu-id="f5634-126">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f5634-126">ICorDebug Interface</span></span>](icordebug-interface.md)
