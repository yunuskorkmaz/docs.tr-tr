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
ms.openlocfilehash: 1ef6af11851acbe0f7e9469c9432ff09f9228608
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792500"
---
# <a name="icordebugprocess2-interface"></a><span data-ttu-id="2e289-102">ICorDebugProcess2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2e289-102">ICorDebugProcess2 Interface</span></span>
<span data-ttu-id="2e289-103">Yönetilen kodu çalıştıran bir işlemi temsil eden ICorDebugProcess arabiriminin mantıksal uzantısı.</span><span class="sxs-lookup"><span data-stu-id="2e289-103">A logical extension of the ICorDebugProcess interface, which represents a process running managed code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2e289-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2e289-104">Methods</span></span>  
  
|<span data-ttu-id="2e289-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="2e289-105">Method</span></span>|<span data-ttu-id="2e289-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2e289-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2e289-107">ClearUnmanagedBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2e289-107">ClearUnmanagedBreakpoint Method</span></span>](icordebugprocess2-clearunmanagedbreakpoint-method.md)|<span data-ttu-id="2e289-108">Daha önceki bir `ICorDebugProcess2::SetUnmanagedBreakpoint`çağrısıyla ayarlanan belirtilen uzaklığında bir kesme noktasını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="2e289-108">Removes a breakpoint at the specified offset that was set by an earlier call to `ICorDebugProcess2::SetUnmanagedBreakpoint`.</span></span>|  
|[<span data-ttu-id="2e289-109">GetDesiredNGENCompilerFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2e289-109">GetDesiredNGENCompilerFlags Method</span></span>](icordebugprocess2-getdesiredngencompilerflags-method.md)|<span data-ttu-id="2e289-110">Görüntüyü bu `ICorDebugProcess2`başvurduğu işleme yüklemek için ortak dil çalışma zamanı (CLR) için ayarlanması gereken bayrakları alır.</span><span class="sxs-lookup"><span data-stu-id="2e289-110">Gets the flags that must be set for the common language runtime (CLR) to load the image into the process referenced by this `ICorDebugProcess2`.</span></span>|  
|[<span data-ttu-id="2e289-111">GetReferenceValueFromGCHandle Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2e289-111">GetReferenceValueFromGCHandle Method</span></span>](icordebugprocess2-getreferencevaluefromgchandle-method.md)|<span data-ttu-id="2e289-112">Bir atık toplama tanıtıcısına sahip olan, belirtilen yönetilen nesneye bir başvuru işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="2e289-112">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>|  
|[<span data-ttu-id="2e289-113">GetThreadForTaskID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2e289-113">GetThreadForTaskID Method</span></span>](icordebugprocess2-getthreadfortaskid-method.md)|<span data-ttu-id="2e289-114">Belirtilen tanımlayıcıya sahip görevin yürütüldüğü iş parçacığını alır.</span><span class="sxs-lookup"><span data-stu-id="2e289-114">Gets the thread upon which the task with the specified identifier is executing.</span></span>|  
|[<span data-ttu-id="2e289-115">GetVersion Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2e289-115">GetVersion Method</span></span>](icordebugprocess2-getversion-method.md)|<span data-ttu-id="2e289-116">Hata ayıklamakta olan işlemin üzerinde çalıştığı CLR sürümünü alır.</span><span class="sxs-lookup"><span data-stu-id="2e289-116">Gets the version of the CLR upon which the process being debugged is running.</span></span>|  
|[<span data-ttu-id="2e289-117">SetDesiredNGENCompilerFlags Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2e289-117">SetDesiredNGENCompilerFlags Method</span></span>](icordebugprocess2-setdesiredngencompilerflags-method.md)|<span data-ttu-id="2e289-118">Just-In-Time (JıT) derleyicisi için gereken bayrakları, hata ayıklanan işleme bir görüntü yükleyecek şekilde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2e289-118">Sets the flags that are required for the just-in-time (JIT) compiler to load an image into the process being debugged.</span></span>|  
|[<span data-ttu-id="2e289-119">SetUnmanagedBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2e289-119">SetUnmanagedBreakpoint Method</span></span>](icordebugprocess2-setunmanagedbreakpoint-method.md)|<span data-ttu-id="2e289-120">Belirtilen yerel görüntü uzaklığında yönetilmeyen bir kesme noktası ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2e289-120">Sets an unmanaged breakpoint at the specified native image offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2e289-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2e289-121">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2e289-122">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="2e289-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e289-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2e289-123">Requirements</span></span>  
 <span data-ttu-id="2e289-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e289-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e289-125">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2e289-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2e289-126">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2e289-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e289-127">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e289-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e289-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e289-128">See also</span></span>

- [<span data-ttu-id="2e289-129">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2e289-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
