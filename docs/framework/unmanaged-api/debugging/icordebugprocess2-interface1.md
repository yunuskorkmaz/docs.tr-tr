---
description: 'Daha fazla bilgi edinin: ICorDebugProcess2 Interface'
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
ms.openlocfilehash: 47e94ee8ee4f45e365fa9efe888cb706f8bb1dfd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746600"
---
# <a name="icordebugprocess2-interface"></a><span data-ttu-id="ef8c9-103">ICorDebugProcess2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ef8c9-103">ICorDebugProcess2 Interface</span></span>

<span data-ttu-id="ef8c9-104">Yönetilen kodu çalıştıran bir işlemi temsil eden ICorDebugProcess arabiriminin mantıksal uzantısı.</span><span class="sxs-lookup"><span data-stu-id="ef8c9-104">A logical extension of the ICorDebugProcess interface, which represents a process running managed code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ef8c9-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ef8c9-105">Methods</span></span>  
  
|<span data-ttu-id="ef8c9-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ef8c9-106">Method</span></span>|<span data-ttu-id="ef8c9-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ef8c9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ef8c9-108">ClearUnmanagedBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ef8c9-108">ClearUnmanagedBreakpoint Method</span></span>](icordebugprocess2-clearunmanagedbreakpoint-method.md)|<span data-ttu-id="ef8c9-109">Daha önceki bir çağrısıyla ayarlanan belirtilen uzaklığında bir kesme noktasını kaldırır `ICorDebugProcess2::SetUnmanagedBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="ef8c9-109">Removes a breakpoint at the specified offset that was set by an earlier call to `ICorDebugProcess2::SetUnmanagedBreakpoint`.</span></span>|  
|[<span data-ttu-id="ef8c9-110">GetDesiredNGENCompilerFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ef8c9-110">GetDesiredNGENCompilerFlags Method</span></span>](icordebugprocess2-getdesiredngencompilerflags-method.md)|<span data-ttu-id="ef8c9-111">Görüntüyü bunun başvurduğu işleme yüklemek için ortak dil çalışma zamanı (CLR) için ayarlanması gereken bayrakları alır `ICorDebugProcess2` .</span><span class="sxs-lookup"><span data-stu-id="ef8c9-111">Gets the flags that must be set for the common language runtime (CLR) to load the image into the process referenced by this `ICorDebugProcess2`.</span></span>|  
|[<span data-ttu-id="ef8c9-112">GetReferenceValueFromGCHandle Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ef8c9-112">GetReferenceValueFromGCHandle Method</span></span>](icordebugprocess2-getreferencevaluefromgchandle-method.md)|<span data-ttu-id="ef8c9-113">Bir atık toplama tanıtıcısına sahip olan, belirtilen yönetilen nesneye bir başvuru işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="ef8c9-113">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>|  
|[<span data-ttu-id="ef8c9-114">GetThreadForTaskID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ef8c9-114">GetThreadForTaskID Method</span></span>](icordebugprocess2-getthreadfortaskid-method.md)|<span data-ttu-id="ef8c9-115">Belirtilen tanımlayıcıya sahip görevin yürütüldüğü iş parçacığını alır.</span><span class="sxs-lookup"><span data-stu-id="ef8c9-115">Gets the thread upon which the task with the specified identifier is executing.</span></span>|  
|[<span data-ttu-id="ef8c9-116">GetVersion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ef8c9-116">GetVersion Method</span></span>](icordebugprocess2-getversion-method.md)|<span data-ttu-id="ef8c9-117">Hata ayıklamakta olan işlemin üzerinde çalıştığı CLR sürümünü alır.</span><span class="sxs-lookup"><span data-stu-id="ef8c9-117">Gets the version of the CLR upon which the process being debugged is running.</span></span>|  
|[<span data-ttu-id="ef8c9-118">SetDesiredNGENCompilerFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ef8c9-118">SetDesiredNGENCompilerFlags Method</span></span>](icordebugprocess2-setdesiredngencompilerflags-method.md)|<span data-ttu-id="ef8c9-119">Just-In-Time (JıT) derleyicisi için gereken bayrakları, hata ayıklanan işleme bir görüntü yükleyecek şekilde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ef8c9-119">Sets the flags that are required for the just-in-time (JIT) compiler to load an image into the process being debugged.</span></span>|  
|[<span data-ttu-id="ef8c9-120">SetUnmanagedBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ef8c9-120">SetUnmanagedBreakpoint Method</span></span>](icordebugprocess2-setunmanagedbreakpoint-method.md)|<span data-ttu-id="ef8c9-121">Belirtilen yerel görüntü uzaklığında yönetilmeyen bir kesme noktası ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ef8c9-121">Sets an unmanaged breakpoint at the specified native image offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ef8c9-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ef8c9-122">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ef8c9-123">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="ef8c9-123">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef8c9-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ef8c9-124">Requirements</span></span>  

 <span data-ttu-id="ef8c9-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef8c9-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef8c9-126">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ef8c9-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ef8c9-127">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ef8c9-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef8c9-128">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef8c9-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef8c9-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef8c9-129">See also</span></span>

- [<span data-ttu-id="ef8c9-130">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ef8c9-130">Debugging Interfaces</span></span>](debugging-interfaces.md)
