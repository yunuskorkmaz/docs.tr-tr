---
title: ICorDebugProcess::GetHelperThreadID Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetHelperThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetHelperThreadID
helpviewer_keywords:
- GetHelperThreadID method [.NET Framework debugging]
- ICorDebugProcess::GetHelperThreadID method [.NET Framework debugging]
ms.assetid: 84e1e605-37c1-49a5-8e12-35db85654622
topic_type:
- apiref
ms.openlocfilehash: d38a59b23d47cbaf57dc21e121d56530a514d354
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128856"
---
# <a name="icordebugprocessgethelperthreadid-method"></a><span data-ttu-id="85e4a-102">ICorDebugProcess::GetHelperThreadID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="85e4a-102">ICorDebugProcess::GetHelperThreadID Method</span></span>
<span data-ttu-id="85e4a-103">Hata ayıklayıcının iç yardımcı iş parçacığının işletim sistemi (OS) iş parçacığı KIMLIĞINI alır.</span><span class="sxs-lookup"><span data-stu-id="85e4a-103">Gets the operating system (OS) thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85e4a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="85e4a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHelperThreadID (  
    [out] DWORD *pThreadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85e4a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="85e4a-105">Parameters</span></span>  
 `pThreadID`  
 <span data-ttu-id="85e4a-106">dışı Hata ayıklayıcının iç yardımcı iş parçacığının işletim sistemi iş parçacığı KIMLIĞINE yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="85e4a-106">[out] A pointer to the OS thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85e4a-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="85e4a-107">Remarks</span></span>  
 <span data-ttu-id="85e4a-108">Yönetilen ve yönetilmeyen hata ayıklama sırasında, belirtilen KIMLIĞE sahip iş parçacığının, hata ayıklayıcı tarafından verilen bir kesme noktasına isabet ettiği durumlarda çalışmaya devam ettiğinden emin olmak için hata ayıklayıcının sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="85e4a-108">During managed and unmanaged debugging, it is the debugger's responsibility to ensure that the thread with the specified ID remains running if it hits a breakpoint placed by the debugger.</span></span> <span data-ttu-id="85e4a-109">Bir hata ayıklayıcı, bu iş parçacığını kullanıcıdan gizlemek de isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="85e4a-109">A debugger may also wish to hide this thread from the user.</span></span> <span data-ttu-id="85e4a-110">İşlemde henüz bir yardımcı iş parçacığı yoksa, `GetHelperThreadID` yöntemi \*`pThreadID`sıfır döndürür.</span><span class="sxs-lookup"><span data-stu-id="85e4a-110">If no helper thread exists in the process yet, the `GetHelperThreadID` method returns zero in \*`pThreadID`.</span></span>  
  
 <span data-ttu-id="85e4a-111">Zamanla değiştirebileceğinden, yardımcı iş parçacığının iş parçacığı KIMLIĞINI önbelleğe alamaz.</span><span class="sxs-lookup"><span data-stu-id="85e4a-111">You cannot cache the thread ID of the helper thread, because it may change over time.</span></span> <span data-ttu-id="85e4a-112">Her durdurma olayında iş parçacığı KIMLIĞINI yeniden sorgulamalısınız.</span><span class="sxs-lookup"><span data-stu-id="85e4a-112">You must re-query the thread ID at every stopping event.</span></span>  
  
 <span data-ttu-id="85e4a-113">Hata ayıklayıcının yardımcı iş parçacığının iş parçacığı KIMLIĞI, her yönetilmeyen [ICorDebugManagedCallback:: CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) olayında doğru olacaktır, böylece bir hata ayıklayıcının yardımcı iş parçacığının Iş parçacığı kimliğini belirlemesine ve kullanıcıdan gizlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="85e4a-113">The thread ID of the debugger's helper thread will be correct on every unmanaged [ICorDebugManagedCallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) event, thus allowing a debugger to determine the thread ID of its helper thread and hide it from the user.</span></span> <span data-ttu-id="85e4a-114">Yönetilmeyen `ICorDebugManagedCallback::CreateThread` bir olay sırasında yardımcı iş parçacığı olarak tanımlanan bir iş parçacığı, yönetilen Kullanıcı kodunu hiçbir şekilde çalıştırmaz.</span><span class="sxs-lookup"><span data-stu-id="85e4a-114">A thread that is identified as a helper thread during an unmanaged `ICorDebugManagedCallback::CreateThread` event will never run managed user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85e4a-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="85e4a-115">Requirements</span></span>  
 <span data-ttu-id="85e4a-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85e4a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85e4a-117">**Üst bilgi:** CorDebug. IDL.</span><span class="sxs-lookup"><span data-stu-id="85e4a-117">**Header:** CorDebug.idl.</span></span> <span data-ttu-id="85e4a-118">CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="85e4a-118">CorDebug.h</span></span>  
  
 <span data-ttu-id="85e4a-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="85e4a-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85e4a-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85e4a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
