---
title: Icordebugprocess2 Interface1
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
ms.openlocfilehash: 6a1588a37891d6a73c49cb1b9ccbc81d9dcdb7e2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420423"
---
# <a name="icordebugprocess2-interface1"></a><span data-ttu-id="e5c72-102">Icordebugprocess2 Interface1</span><span class="sxs-lookup"><span data-stu-id="e5c72-102">ICorDebugProcess2 Interface1</span></span>
<span data-ttu-id="e5c72-103">Bir işlem çalışan yönetilen kodu temsil eden Icordebugprocess arabirimi mantıksal bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="e5c72-103">A logical extension of the ICorDebugProcess interface, which represents a process running managed code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e5c72-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e5c72-104">Methods</span></span>  
  
|<span data-ttu-id="e5c72-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e5c72-105">Method</span></span>|<span data-ttu-id="e5c72-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5c72-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e5c72-107">ClearUnmanagedBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e5c72-107">ClearUnmanagedBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md)|<span data-ttu-id="e5c72-108">Önceki bir çağrı tarafından ayarlanan belirtilen uzaklığında bir kesme noktası kaldırır `ICorDebugProcess2::SetUnmanagedBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="e5c72-108">Removes a breakpoint at the specified offset that was set by an earlier call to `ICorDebugProcess2::SetUnmanagedBreakpoint`.</span></span>|  
|[<span data-ttu-id="e5c72-109">GetDesiredNGENCompilerFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e5c72-109">GetDesiredNGENCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getdesiredngencompilerflags-method.md)|<span data-ttu-id="e5c72-110">Ortak Dil Çalışma Zamanı Modülü (CLR) bu tarafından başvurulan işlemine resmi yüklemek için ayarlanmalıdır bayraklarını alır `ICorDebugProcess2`.</span><span class="sxs-lookup"><span data-stu-id="e5c72-110">Gets the flags that must be set for the common language runtime (CLR) to load the image into the process referenced by this `ICorDebugProcess2`.</span></span>|  
|[<span data-ttu-id="e5c72-111">GetReferenceValueFromGCHandle Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e5c72-111">GetReferenceValueFromGCHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getreferencevaluefromgchandle-method.md)|<span data-ttu-id="e5c72-112">Bir başvuru işaretçi işlemek çöp toplama sahip belirtilen yönetilen nesneyi alır.</span><span class="sxs-lookup"><span data-stu-id="e5c72-112">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>|  
|[<span data-ttu-id="e5c72-113">GetThreadForTaskID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e5c72-113">GetThreadForTaskID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getthreadfortaskid-method.md)|<span data-ttu-id="e5c72-114">Belirtilen tanımlayıcıya sahip görev dosyanızın çalıştığı iş parçacığı alır.</span><span class="sxs-lookup"><span data-stu-id="e5c72-114">Gets the thread upon which the task with the specified identifier is executing.</span></span>|  
|[<span data-ttu-id="e5c72-115">GetVersion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e5c72-115">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getversion-method.md)|<span data-ttu-id="e5c72-116">Ayıklanacak işlem üzerinde çalıştığı CLR sürümünü alır.</span><span class="sxs-lookup"><span data-stu-id="e5c72-116">Gets the version of the CLR upon which the process being debugged is running.</span></span>|  
|[<span data-ttu-id="e5c72-117">SetDesiredNGENCompilerFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e5c72-117">SetDesiredNGENCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md)|<span data-ttu-id="e5c72-118">Ayıklanacak işlemine bir görüntü yüklemek tam zamanında (JIT) derleyici için gerekli olan bayrakları ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e5c72-118">Sets the flags that are required for the just-in-time (JIT) compiler to load an image into the process being debugged.</span></span>|  
|[<span data-ttu-id="e5c72-119">SetUnmanagedBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e5c72-119">SetUnmanagedBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)|<span data-ttu-id="e5c72-120">Yönetilmeyen bir kesme noktası belirtilen yerel görüntü uzaklığı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e5c72-120">Sets an unmanaged breakpoint at the specified native image offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5c72-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e5c72-121">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5c72-122">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="e5c72-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5c72-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e5c72-123">Requirements</span></span>  
 <span data-ttu-id="e5c72-124">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5c72-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5c72-125">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e5c72-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e5c72-126">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e5c72-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5c72-127">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5c72-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5c72-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e5c72-128">See Also</span></span>  
 [<span data-ttu-id="e5c72-129">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e5c72-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
