---
description: ': ICorDebug:: CanLaunchOrAttach Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: cb813c4bae968941de731d9d5b74d8f804b3c8ac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723250"
---
# <a name="icordebugcanlaunchorattach-method"></a><span data-ttu-id="3a645-103">ICorDebug::CanLaunchOrAttach Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3a645-103">ICorDebug::CanLaunchOrAttach Method</span></span>

<span data-ttu-id="3a645-104">Geçerli makine ve çalışma zamanı yapılandırması bağlamında yeni bir işlemin başlatılıp başlatılmayacağını veya belirtilen mevcut işleme iliştirilip mümkün olup olmadığını belirten bir HRESULT döndürür.</span><span class="sxs-lookup"><span data-stu-id="3a645-104">Returns an HRESULT that indicates whether launching a new process or attaching to the specified existing process is possible within the context of the current machine and runtime configuration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a645-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3a645-105">Syntax</span></span>  
  
```cpp  
HRESULT CanLaunchOrAttach (  
    [in] DWORD      dwProcessId,  
    [in] BOOL       win32DebuggingEnabled  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a645-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3a645-106">Parameters</span></span>  

 `dwProcessId`  
 <span data-ttu-id="3a645-107">'ndaki Mevcut bir işlemin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="3a645-107">[in] The ID of an existing process.</span></span>  
  
 `win32DebuggingEnabled`  
 <span data-ttu-id="3a645-108">'ndaki `true` Win32 hata ayıklaması etkinken başlatmayı planlıyorsanız veya Win32 hata ayıklaması etkin olarak eklemek istiyorsanız, geçiş yapın; Aksi takdirde, pass `false` .</span><span class="sxs-lookup"><span data-stu-id="3a645-108">[in] Pass in `true` if you plan to launch with Win32 debugging enabled, or to attach with Win32 debugging enabled; otherwise, pass `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3a645-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3a645-109">Return Value</span></span>  

 <span data-ttu-id="3a645-110">Hata ayıklama Hizmetleri, yeni bir işlem başlatmayı veya belirli bir işleme eklemeyi saptarken, geçerli makine ve çalışma zamanı yapılandırmasıyla ilgili bilgiler verildiğinde S_OK.</span><span class="sxs-lookup"><span data-stu-id="3a645-110">S_OK if the debugging services determine that launching a new process or attaching to the given process is possible, given the information about the current machine and runtime configuration.</span></span> <span data-ttu-id="3a645-111">Olası HRESULT değerleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="3a645-111">Possible HRESULT values are:</span></span>  
  
- <span data-ttu-id="3a645-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="3a645-112">S_OK</span></span>  
  
- <span data-ttu-id="3a645-113">CORDBG_E_DEBUGGING_NOT_POSSIBLE</span><span class="sxs-lookup"><span data-stu-id="3a645-113">CORDBG_E_DEBUGGING_NOT_POSSIBLE</span></span>  
  
- <span data-ttu-id="3a645-114">CORDBG_E_KERNEL_DEBUGGER_PRESENT</span><span class="sxs-lookup"><span data-stu-id="3a645-114">CORDBG_E_KERNEL_DEBUGGER_PRESENT</span></span>  
  
- <span data-ttu-id="3a645-115">CORDBG_E_KERNEL_DEBUGGER_ENABLED</span><span class="sxs-lookup"><span data-stu-id="3a645-115">CORDBG_E_KERNEL_DEBUGGER_ENABLED</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3a645-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3a645-116">Remarks</span></span>  

 <span data-ttu-id="3a645-117">Bu yöntem yalnızca bilgilendirme amaçlıdır.</span><span class="sxs-lookup"><span data-stu-id="3a645-117">This method is purely informational.</span></span> <span data-ttu-id="3a645-118">Arabirim, tarafından döndürülen değerden bağımsız olarak, bir işleme veya ekleme işlemini durdurmayacak `CanLaunchOrAttach` .</span><span class="sxs-lookup"><span data-stu-id="3a645-118">The interface will not stop you from launching or attaching to a process, regardless of the value returned by `CanLaunchOrAttach`.</span></span>  
  
 <span data-ttu-id="3a645-119">Win32 hata ayıklaması etkinleştirilmiş veya Win32 hata ayıklaması etkinken birlikte başlatmaya çalışırsanız, için geçiş yapın `true` `win32DebuggingEnabled` .</span><span class="sxs-lookup"><span data-stu-id="3a645-119">If you plan to launch with Win32 debugging enabled or attach with Win32 debugging enabled, pass `true` for `win32DebuggingEnabled`.</span></span> <span data-ttu-id="3a645-120">Tarafından döndürülen HRESULT, `CanLaunchOrAttach` Bu seçeneği kullanırsanız farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="3a645-120">The HRESULT returned by `CanLaunchOrAttach` might differ if you use this option.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a645-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3a645-121">Requirements</span></span>  

 <span data-ttu-id="3a645-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a645-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a645-123">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3a645-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3a645-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3a645-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a645-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a645-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a645-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3a645-126">See also</span></span>

- [<span data-ttu-id="3a645-127">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3a645-127">ICorDebug Interface</span></span>](icordebug-interface.md)
