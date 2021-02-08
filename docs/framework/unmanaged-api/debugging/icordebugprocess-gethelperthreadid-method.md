---
description: ': ICorDebugProcess:: GetHelperThreadID yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: ee7bd2106a37c5c67df48a54ff9ab7fa49a03f80
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801026"
---
# <a name="icordebugprocessgethelperthreadid-method"></a><span data-ttu-id="3d284-103">ICorDebugProcess::GetHelperThreadID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3d284-103">ICorDebugProcess::GetHelperThreadID Method</span></span>

<span data-ttu-id="3d284-104">Hata ayıklayıcının iç yardımcı iş parçacığının işletim sistemi (OS) iş parçacığı KIMLIĞINI alır.</span><span class="sxs-lookup"><span data-stu-id="3d284-104">Gets the operating system (OS) thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d284-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3d284-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHelperThreadID (  
    [out] DWORD *pThreadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d284-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3d284-106">Parameters</span></span>  

 `pThreadID`  
 <span data-ttu-id="3d284-107">dışı Hata ayıklayıcının iç yardımcı iş parçacığının işletim sistemi iş parçacığı KIMLIĞINE yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3d284-107">[out] A pointer to the OS thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d284-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3d284-108">Remarks</span></span>  

 <span data-ttu-id="3d284-109">Yönetilen ve yönetilmeyen hata ayıklama sırasında, belirtilen KIMLIĞE sahip iş parçacığının, hata ayıklayıcı tarafından verilen bir kesme noktasına isabet ettiği durumlarda çalışmaya devam ettiğinden emin olmak için hata ayıklayıcının sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="3d284-109">During managed and unmanaged debugging, it is the debugger's responsibility to ensure that the thread with the specified ID remains running if it hits a breakpoint placed by the debugger.</span></span> <span data-ttu-id="3d284-110">Bir hata ayıklayıcı, bu iş parçacığını kullanıcıdan gizlemek de isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="3d284-110">A debugger may also wish to hide this thread from the user.</span></span> <span data-ttu-id="3d284-111">İşlemde henüz bir yardımcı iş parçacığı yoksa, `GetHelperThreadID` Yöntem \* içinde 0 döndürür `pThreadID` .</span><span class="sxs-lookup"><span data-stu-id="3d284-111">If no helper thread exists in the process yet, the `GetHelperThreadID` method returns zero in \*`pThreadID`.</span></span>  
  
 <span data-ttu-id="3d284-112">Zamanla değiştirebileceğinden, yardımcı iş parçacığının iş parçacığı KIMLIĞINI önbelleğe alamaz.</span><span class="sxs-lookup"><span data-stu-id="3d284-112">You cannot cache the thread ID of the helper thread, because it may change over time.</span></span> <span data-ttu-id="3d284-113">Her durdurma olayında iş parçacığı KIMLIĞINI yeniden sorgulamalısınız.</span><span class="sxs-lookup"><span data-stu-id="3d284-113">You must re-query the thread ID at every stopping event.</span></span>  
  
 <span data-ttu-id="3d284-114">Hata ayıklayıcının yardımcı iş parçacığının iş parçacığı KIMLIĞI, her yönetilmeyen [ICorDebugManagedCallback:: CreateThread](icordebugmanagedcallback-createthread-method.md) olayında doğru olacaktır, böylece bir hata ayıklayıcının yardımcı iş parçacığının Iş parçacığı kimliğini belirlemesine ve kullanıcıdan gizlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="3d284-114">The thread ID of the debugger's helper thread will be correct on every unmanaged [ICorDebugManagedCallback::CreateThread](icordebugmanagedcallback-createthread-method.md) event, thus allowing a debugger to determine the thread ID of its helper thread and hide it from the user.</span></span> <span data-ttu-id="3d284-115">Yönetilmeyen bir olay sırasında yardımcı iş parçacığı olarak tanımlanan bir iş parçacığı `ICorDebugManagedCallback::CreateThread` , yönetilen Kullanıcı kodunu hiçbir şekilde çalıştırmaz.</span><span class="sxs-lookup"><span data-stu-id="3d284-115">A thread that is identified as a helper thread during an unmanaged `ICorDebugManagedCallback::CreateThread` event will never run managed user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d284-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3d284-116">Requirements</span></span>  

 <span data-ttu-id="3d284-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d284-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d284-118">**Üst bilgi:** CorDebug. IDL.</span><span class="sxs-lookup"><span data-stu-id="3d284-118">**Header:** CorDebug.idl.</span></span> <span data-ttu-id="3d284-119">CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3d284-119">CorDebug.h</span></span>  
  
 <span data-ttu-id="3d284-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3d284-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d284-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d284-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
