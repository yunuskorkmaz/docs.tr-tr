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
ms.openlocfilehash: f1a30c197373928ec10c2b84de4e805b94ea2384
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724513"
---
# <a name="icordebugprocess2-interface"></a><span data-ttu-id="f7de9-102">ICorDebugProcess2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f7de9-102">ICorDebugProcess2 Interface</span></span>

<span data-ttu-id="f7de9-103">Yönetilen kodu çalıştıran bir işlemi temsil eden ICorDebugProcess arabiriminin mantıksal uzantısı.</span><span class="sxs-lookup"><span data-stu-id="f7de9-103">A logical extension of the ICorDebugProcess interface, which represents a process running managed code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f7de9-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f7de9-104">Methods</span></span>  
  
|<span data-ttu-id="f7de9-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f7de9-105">Method</span></span>|<span data-ttu-id="f7de9-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f7de9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f7de9-107">ClearUnmanagedBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f7de9-107">ClearUnmanagedBreakpoint Method</span></span>](icordebugprocess2-clearunmanagedbreakpoint-method.md)|<span data-ttu-id="f7de9-108">Daha önceki bir çağrısıyla ayarlanan belirtilen uzaklığında bir kesme noktasını kaldırır `ICorDebugProcess2::SetUnmanagedBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="f7de9-108">Removes a breakpoint at the specified offset that was set by an earlier call to `ICorDebugProcess2::SetUnmanagedBreakpoint`.</span></span>|  
|[<span data-ttu-id="f7de9-109">GetDesiredNGENCompilerFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f7de9-109">GetDesiredNGENCompilerFlags Method</span></span>](icordebugprocess2-getdesiredngencompilerflags-method.md)|<span data-ttu-id="f7de9-110">Görüntüyü bunun başvurduğu işleme yüklemek için ortak dil çalışma zamanı (CLR) için ayarlanması gereken bayrakları alır `ICorDebugProcess2` .</span><span class="sxs-lookup"><span data-stu-id="f7de9-110">Gets the flags that must be set for the common language runtime (CLR) to load the image into the process referenced by this `ICorDebugProcess2`.</span></span>|  
|[<span data-ttu-id="f7de9-111">GetReferenceValueFromGCHandle Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f7de9-111">GetReferenceValueFromGCHandle Method</span></span>](icordebugprocess2-getreferencevaluefromgchandle-method.md)|<span data-ttu-id="f7de9-112">Bir atık toplama tanıtıcısına sahip olan, belirtilen yönetilen nesneye bir başvuru işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="f7de9-112">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>|  
|[<span data-ttu-id="f7de9-113">GetThreadForTaskID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f7de9-113">GetThreadForTaskID Method</span></span>](icordebugprocess2-getthreadfortaskid-method.md)|<span data-ttu-id="f7de9-114">Belirtilen tanımlayıcıya sahip görevin yürütüldüğü iş parçacığını alır.</span><span class="sxs-lookup"><span data-stu-id="f7de9-114">Gets the thread upon which the task with the specified identifier is executing.</span></span>|  
|[<span data-ttu-id="f7de9-115">GetVersion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f7de9-115">GetVersion Method</span></span>](icordebugprocess2-getversion-method.md)|<span data-ttu-id="f7de9-116">Hata ayıklamakta olan işlemin üzerinde çalıştığı CLR sürümünü alır.</span><span class="sxs-lookup"><span data-stu-id="f7de9-116">Gets the version of the CLR upon which the process being debugged is running.</span></span>|  
|[<span data-ttu-id="f7de9-117">SetDesiredNGENCompilerFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f7de9-117">SetDesiredNGENCompilerFlags Method</span></span>](icordebugprocess2-setdesiredngencompilerflags-method.md)|<span data-ttu-id="f7de9-118">Just-In-Time (JıT) derleyicisi için gereken bayrakları, hata ayıklanan işleme bir görüntü yükleyecek şekilde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f7de9-118">Sets the flags that are required for the just-in-time (JIT) compiler to load an image into the process being debugged.</span></span>|  
|[<span data-ttu-id="f7de9-119">SetUnmanagedBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f7de9-119">SetUnmanagedBreakpoint Method</span></span>](icordebugprocess2-setunmanagedbreakpoint-method.md)|<span data-ttu-id="f7de9-120">Belirtilen yerel görüntü uzaklığında yönetilmeyen bir kesme noktası ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f7de9-120">Sets an unmanaged breakpoint at the specified native image offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7de9-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f7de9-121">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f7de9-122">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="f7de9-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7de9-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f7de9-123">Requirements</span></span>  

 <span data-ttu-id="f7de9-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7de9-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7de9-125">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f7de9-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f7de9-126">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f7de9-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7de9-127">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7de9-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7de9-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7de9-128">See also</span></span>

- [<span data-ttu-id="f7de9-129">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f7de9-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
