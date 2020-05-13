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
ms.openlocfilehash: fc4f4b56552c4db265d2ea123a84c7792ad53094
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213640"
---
# <a name="icordebugprocessgethelperthreadid-method"></a><span data-ttu-id="f3e7e-102">ICorDebugProcess::GetHelperThreadID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f3e7e-102">ICorDebugProcess::GetHelperThreadID Method</span></span>
<span data-ttu-id="f3e7e-103">Hata ayıklayıcının iç yardımcı iş parçacığının işletim sistemi (OS) iş parçacığı KIMLIĞINI alır.</span><span class="sxs-lookup"><span data-stu-id="f3e7e-103">Gets the operating system (OS) thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3e7e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f3e7e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHelperThreadID (  
    [out] DWORD *pThreadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3e7e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f3e7e-105">Parameters</span></span>  
 `pThreadID`  
 <span data-ttu-id="f3e7e-106">dışı Hata ayıklayıcının iç yardımcı iş parçacığının işletim sistemi iş parçacığı KIMLIĞINE yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f3e7e-106">[out] A pointer to the OS thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3e7e-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f3e7e-107">Remarks</span></span>  
 <span data-ttu-id="f3e7e-108">Yönetilen ve yönetilmeyen hata ayıklama sırasında, belirtilen KIMLIĞE sahip iş parçacığının, hata ayıklayıcı tarafından verilen bir kesme noktasına isabet ettiği durumlarda çalışmaya devam ettiğinden emin olmak için hata ayıklayıcının sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="f3e7e-108">During managed and unmanaged debugging, it is the debugger's responsibility to ensure that the thread with the specified ID remains running if it hits a breakpoint placed by the debugger.</span></span> <span data-ttu-id="f3e7e-109">Bir hata ayıklayıcı, bu iş parçacığını kullanıcıdan gizlemek de isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="f3e7e-109">A debugger may also wish to hide this thread from the user.</span></span> <span data-ttu-id="f3e7e-110">İşlemde henüz bir yardımcı iş parçacığı yoksa, `GetHelperThreadID` Yöntem \* içinde 0 döndürür `pThreadID` .</span><span class="sxs-lookup"><span data-stu-id="f3e7e-110">If no helper thread exists in the process yet, the `GetHelperThreadID` method returns zero in \*`pThreadID`.</span></span>  
  
 <span data-ttu-id="f3e7e-111">Zamanla değiştirebileceğinden, yardımcı iş parçacığının iş parçacığı KIMLIĞINI önbelleğe alamaz.</span><span class="sxs-lookup"><span data-stu-id="f3e7e-111">You cannot cache the thread ID of the helper thread, because it may change over time.</span></span> <span data-ttu-id="f3e7e-112">Her durdurma olayında iş parçacığı KIMLIĞINI yeniden sorgulamalısınız.</span><span class="sxs-lookup"><span data-stu-id="f3e7e-112">You must re-query the thread ID at every stopping event.</span></span>  
  
 <span data-ttu-id="f3e7e-113">Hata ayıklayıcının yardımcı iş parçacığının iş parçacığı KIMLIĞI, her yönetilmeyen [ICorDebugManagedCallback:: CreateThread](icordebugmanagedcallback-createthread-method.md) olayında doğru olacaktır, böylece bir hata ayıklayıcının yardımcı iş parçacığının Iş parçacığı kimliğini belirlemesine ve kullanıcıdan gizlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="f3e7e-113">The thread ID of the debugger's helper thread will be correct on every unmanaged [ICorDebugManagedCallback::CreateThread](icordebugmanagedcallback-createthread-method.md) event, thus allowing a debugger to determine the thread ID of its helper thread and hide it from the user.</span></span> <span data-ttu-id="f3e7e-114">Yönetilmeyen bir olay sırasında yardımcı iş parçacığı olarak tanımlanan bir iş parçacığı `ICorDebugManagedCallback::CreateThread` , yönetilen Kullanıcı kodunu hiçbir şekilde çalıştırmaz.</span><span class="sxs-lookup"><span data-stu-id="f3e7e-114">A thread that is identified as a helper thread during an unmanaged `ICorDebugManagedCallback::CreateThread` event will never run managed user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3e7e-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f3e7e-115">Requirements</span></span>  
 <span data-ttu-id="f3e7e-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3e7e-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3e7e-117">**Üst bilgi:** CorDebug. IDL.</span><span class="sxs-lookup"><span data-stu-id="f3e7e-117">**Header:** CorDebug.idl.</span></span> <span data-ttu-id="f3e7e-118">CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f3e7e-118">CorDebug.h</span></span>  
  
 <span data-ttu-id="f3e7e-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f3e7e-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3e7e-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3e7e-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
