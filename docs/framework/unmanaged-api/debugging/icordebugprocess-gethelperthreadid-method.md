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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cd5e30d08e667dcd5a8be1f9502462f28290068e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494226"
---
# <a name="icordebugprocessgethelperthreadid-method"></a><span data-ttu-id="2ee9e-102">ICorDebugProcess::GetHelperThreadID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2ee9e-102">ICorDebugProcess::GetHelperThreadID Method</span></span>
<span data-ttu-id="2ee9e-103">Hata Ayıklayıcı'nın iç yardımcı iş parçacığı işletim sistemi (OS) iş parçacığı Kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="2ee9e-103">Gets the operating system (OS) thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ee9e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2ee9e-104">Syntax</span></span>  
  
```  
HRESULT GetHelperThreadID (  
    [out] DWORD *pThreadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ee9e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2ee9e-105">Parameters</span></span>  
 `pThreadID`  
 <span data-ttu-id="2ee9e-106">[out] Bir işaretçi işletim sistemi iş parçacığı Hata Ayıklayıcı'nın iç Yardımcısı iş parçacığının kimliği.</span><span class="sxs-lookup"><span data-stu-id="2ee9e-106">[out] A pointer to the OS thread ID of the debugger's internal helper thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ee9e-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2ee9e-107">Remarks</span></span>  
 <span data-ttu-id="2ee9e-108">Yönetilen ve yönetilmeyen hata ayıklama sırasında bu, hata ayıklayıcı tarafından yerleştirilen bir kesme noktasına denk gelir, belirtilen Kimliğe sahip bir iş parçacığı çalışan kalmasını sağlamak için hata ayıklayıcı'nın sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="2ee9e-108">During managed and unmanaged debugging, it is the debugger's responsibility to ensure that the thread with the specified ID remains running if it hits a breakpoint placed by the debugger.</span></span> <span data-ttu-id="2ee9e-109">Bir hata ayıklayıcı ayrıca kullanıcıdan bu iş parçacığı gizlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2ee9e-109">A debugger may also wish to hide this thread from the user.</span></span> <span data-ttu-id="2ee9e-110">Hiçbir yardımcı iş parçacığı henüz işlemde varsa `GetHelperThreadID` yöntemi sıfır döndürür \*`pThreadID`.</span><span class="sxs-lookup"><span data-stu-id="2ee9e-110">If no helper thread exists in the process yet, the `GetHelperThreadID` method returns zero in \*`pThreadID`.</span></span>  
  
 <span data-ttu-id="2ee9e-111">Zaman içinde değişebilir olduğundan yardımcı iş parçacığının iş parçacığı kimliği önbelleğe alamıyor.</span><span class="sxs-lookup"><span data-stu-id="2ee9e-111">You cannot cache the thread ID of the helper thread, because it may change over time.</span></span> <span data-ttu-id="2ee9e-112">İş parçacığı kimliği her durdurma etkinlikte yeniden sorgulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2ee9e-112">You must re-query the thread ID at every stopping event.</span></span>  
  
 <span data-ttu-id="2ee9e-113">Hata Ayıklayıcı'nın yardımcı iş parçacığının iş parçacığı kimliği doğru her yönetilmeyen [Icordebugmanagedcallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) olay, bu nedenle, yardımcı iş parçacığının iş parçacığı Kimliğini belirlemek ve kullanıcıdan gizlemek bir hata ayıklayıcı izin verme.</span><span class="sxs-lookup"><span data-stu-id="2ee9e-113">The thread ID of the debugger's helper thread will be correct on every unmanaged [ICorDebugManagedCallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) event, thus allowing a debugger to determine the thread ID of its helper thread and hide it from the user.</span></span> <span data-ttu-id="2ee9e-114">Bir yardımcı iş parçacığı yönetilmeyen sırasında tanımlanan bir iş parçacığı `ICorDebugManagedCallback::CreateThread` olay asla yönetilen kullanıcı kodu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="2ee9e-114">A thread that is identified as a helper thread during an unmanaged `ICorDebugManagedCallback::CreateThread` event will never run managed user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ee9e-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2ee9e-115">Requirements</span></span>  
 <span data-ttu-id="2ee9e-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ee9e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ee9e-117">**Üst bilgi:** CorDebug.idl.</span><span class="sxs-lookup"><span data-stu-id="2ee9e-117">**Header:** CorDebug.idl.</span></span> <span data-ttu-id="2ee9e-118">CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2ee9e-118">CorDebug.h</span></span>  
  
 <span data-ttu-id="2ee9e-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2ee9e-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ee9e-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ee9e-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
