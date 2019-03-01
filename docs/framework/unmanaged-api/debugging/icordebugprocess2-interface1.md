---
title: ICorDebugProcess2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2
helpviewer_keywords:
- ICorDebugProcess2 interface [.NET Framework debugging]
ms.assetid: 73332138-5fea-441f-b893-61af87d45a42
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3009ee6a2ba22771a2132032744f76ca527c422
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965689"
---
# <a name="icordebugprocess2-interface"></a><span data-ttu-id="c051f-102">ICorDebugProcess2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c051f-102">ICorDebugProcess2 Interface</span></span>
<span data-ttu-id="c051f-103">Temsil eden bir işlem çalışan yönetilen kod Icordebugprocess arabirimi öğesinin mantıksal uzantısı.</span><span class="sxs-lookup"><span data-stu-id="c051f-103">A logical extension of the ICorDebugProcess interface, which represents a process running managed code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c051f-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c051f-104">Methods</span></span>  
  
|<span data-ttu-id="c051f-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c051f-105">Method</span></span>|<span data-ttu-id="c051f-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c051f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c051f-107">ClearUnmanagedBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c051f-107">ClearUnmanagedBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md)|<span data-ttu-id="c051f-108">Belirtilen uzaklık daha önceki bir çağrı tarafından ayarlanan bir kesme noktasında kaldırır `ICorDebugProcess2::SetUnmanagedBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="c051f-108">Removes a breakpoint at the specified offset that was set by an earlier call to `ICorDebugProcess2::SetUnmanagedBreakpoint`.</span></span>|  
|[<span data-ttu-id="c051f-109">GetDesiredNGENCompilerFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c051f-109">GetDesiredNGENCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getdesiredngencompilerflags-method.md)|<span data-ttu-id="c051f-110">Bu tarafından başvurulan işlemine görüntüyü yüklemek için ortak dil çalışma zamanı Modülü (CLR) ayarlanmalıdır bayrakları alır `ICorDebugProcess2`.</span><span class="sxs-lookup"><span data-stu-id="c051f-110">Gets the flags that must be set for the common language runtime (CLR) to load the image into the process referenced by this `ICorDebugProcess2`.</span></span>|  
|[<span data-ttu-id="c051f-111">GetReferenceValueFromGCHandle Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c051f-111">GetReferenceValueFromGCHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getreferencevaluefromgchandle-method.md)|<span data-ttu-id="c051f-112">Bir başvuru işaretçi, tanıtıcı bir çöp toplama olan belirtilen yönetilen nesneyi alır.</span><span class="sxs-lookup"><span data-stu-id="c051f-112">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>|  
|[<span data-ttu-id="c051f-113">GetThreadForTaskID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c051f-113">GetThreadForTaskID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getthreadfortaskid-method.md)|<span data-ttu-id="c051f-114">Bağlı belirtilen tanımlayıcıya sahip bir görevi yürüten iş parçacığının alır.</span><span class="sxs-lookup"><span data-stu-id="c051f-114">Gets the thread upon which the task with the specified identifier is executing.</span></span>|  
|[<span data-ttu-id="c051f-115">GetVersion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c051f-115">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getversion-method.md)|<span data-ttu-id="c051f-116">Ayıklanan işlemin çalıştığı CLR sürümünü alır.</span><span class="sxs-lookup"><span data-stu-id="c051f-116">Gets the version of the CLR upon which the process being debugged is running.</span></span>|  
|[<span data-ttu-id="c051f-117">SetDesiredNGENCompilerFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c051f-117">SetDesiredNGENCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md)|<span data-ttu-id="c051f-118">Just-ın-time (JIT) derleyicinin ayıklanan işleme görüntüyü yüklemek için gerekli olan bayraklarını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c051f-118">Sets the flags that are required for the just-in-time (JIT) compiler to load an image into the process being debugged.</span></span>|  
|[<span data-ttu-id="c051f-119">SetUnmanagedBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c051f-119">SetUnmanagedBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)|<span data-ttu-id="c051f-120">Belirtilen yerel görüntü uzaklığında yönetilmeyen bir kesme noktası ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c051f-120">Sets an unmanaged breakpoint at the specified native image offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c051f-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c051f-121">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c051f-122">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="c051f-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c051f-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c051f-123">Requirements</span></span>  
 <span data-ttu-id="c051f-124">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c051f-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c051f-125">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c051f-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c051f-126">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c051f-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c051f-127">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c051f-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c051f-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c051f-128">See also</span></span>
- [<span data-ttu-id="c051f-129">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c051f-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
