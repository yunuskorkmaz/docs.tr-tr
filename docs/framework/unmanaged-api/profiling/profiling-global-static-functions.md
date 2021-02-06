---
description: 'Daha fazla bilgi edinin: profil oluşturma genel statik Işlevleri'
title: Profil Oluşturma Genel Statik İşlevleri
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework profiling]
- profiling global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], profiling
ms.assetid: 08a13a57-dc49-488d-b937-31e3051fda97
ms.openlocfilehash: 86e4b6bda73b0783f5f95e4e7dbc24f1ccccb130
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646380"
---
# <a name="profiling-global-static-functions"></a><span data-ttu-id="00a6e-103">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="00a6e-103">Profiling Global Static Functions</span></span>

<span data-ttu-id="00a6e-104">Bu bölümde profil oluşturma API 'sinin kullandığı yönetilmeyen API işlevleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="00a6e-104">This section describes the unmanaged API functions that the profiling API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="00a6e-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="00a6e-105">In This Section</span></span>  
  
## <a name="net-framework-version-1-profiling-functions"></a><span data-ttu-id="00a6e-106">.NET Framework sürüm 1 profil oluşturma Işlevleri</span><span class="sxs-lookup"><span data-stu-id="00a6e-106">.NET Framework version 1 Profiling Functions</span></span>  

 [<span data-ttu-id="00a6e-107">FunctionEnter İşlevi</span><span class="sxs-lookup"><span data-stu-id="00a6e-107">FunctionEnter Function</span></span>](functionenter-function.md)  
 <span data-ttu-id="00a6e-108">Profil oluşturucuya denetimin bir işleve geçtiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="00a6e-108">Notifies the profiler that control is being passed to a function.</span></span> <span data-ttu-id="00a6e-109">.NET Framework 2,0 ' de kullanımdan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="00a6e-109">Deprecated in the .NET Framework 2.0.</span></span>  
  
 [<span data-ttu-id="00a6e-110">FunctionLeave İşlevi</span><span class="sxs-lookup"><span data-stu-id="00a6e-110">FunctionLeave Function</span></span>](functionleave-function.md)  
 <span data-ttu-id="00a6e-111">Profiler öğesine bir işlevin çağırana dönmek üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="00a6e-111">Notifies the profiler that a function is about to return to the caller.</span></span> <span data-ttu-id="00a6e-112">.NET Framework 2,0 ' de kullanımdan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="00a6e-112">Deprecated in the .NET Framework 2.0.</span></span>  
  
 [<span data-ttu-id="00a6e-113">FunctionTailcall İşlevi</span><span class="sxs-lookup"><span data-stu-id="00a6e-113">FunctionTailcall Function</span></span>](functiontailcall-function.md)  
 <span data-ttu-id="00a6e-114">Profil oluşturucuyu Şu anda yürütülmekte olan işlevin başka bir işleve tail çağrısı gerçekleştirmek üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="00a6e-114">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span> <span data-ttu-id="00a6e-115">.NET Framework 2,0 ' de kullanımdan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="00a6e-115">Deprecated in the .NET Framework 2.0.</span></span>  
  
## <a name="net-framework-version-2-profiling-functions"></a><span data-ttu-id="00a6e-116">.NET Framework sürüm 2 profil oluşturma Işlevleri</span><span class="sxs-lookup"><span data-stu-id="00a6e-116">.NET Framework version 2 Profiling Functions</span></span>  

 [<span data-ttu-id="00a6e-117">FunctionIDMapper İşlevi</span><span class="sxs-lookup"><span data-stu-id="00a6e-117">FunctionIDMapper Function</span></span>](functionidmapper-function.md)  
 <span data-ttu-id="00a6e-118">Profil oluşturucuyu, bir işlevin verilen tanımlayıcısının, bu işlev için [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md)ve [FunctionTailcall2](functiontailcall2-function.md) geri ÇAĞıRMALAR içinde kullanılacak alternatif bir kimliğe yeniden eşlenilebileceği konusunda bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="00a6e-118">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md), and [FunctionTailcall2](functiontailcall2-function.md) callbacks for that function.</span></span> <span data-ttu-id="00a6e-119">Ayrıca, profil oluşturucunun bu işlev için geri çağırmaları almak isteyip istemediğini belirtmek için izin sağlar</span><span class="sxs-lookup"><span data-stu-id="00a6e-119">Also enables the profiler to indicate whether it wants to receive callbacks for that function</span></span>  
  
 [<span data-ttu-id="00a6e-120">FunctionEnter2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="00a6e-120">FunctionEnter2 Function</span></span>](functionenter2-function.md)  
 <span data-ttu-id="00a6e-121">Profil oluşturucuyu denetimin bir işleve geçtiğini ve yığın çerçevesi ve işlev bağımsız değişkenleri hakkında bilgi sağladığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="00a6e-121">Notifies the profiler that control is being passed to a function and provides information about the stack frame and function arguments.</span></span> <span data-ttu-id="00a6e-122">.NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="00a6e-122">Deprecated in the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="00a6e-123">FunctionLeave2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="00a6e-123">FunctionLeave2 Function</span></span>](functionleave2-function.md)  
 <span data-ttu-id="00a6e-124">Profil oluşturucuya bir işlevin çağırana dönmek üzere olduğunu bildirir ve yığın çerçevesi ve işlev dönüş değeri hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="00a6e-124">Notifies the profiler that a function is about to return to the caller and provides information about the stack frame and function return value.</span></span> <span data-ttu-id="00a6e-125">.NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="00a6e-125">Deprecated in the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="00a6e-126">FunctionTailcall2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="00a6e-126">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)  
 <span data-ttu-id="00a6e-127">Şu anda yürütülmekte olan işlevin başka bir işleve bir tail çağrısı gerçekleştirmek üzere olduğunu ve yığın çerçevesi hakkında bilgi sağladığını bildiren Profiler öğesine bildirir.</span><span class="sxs-lookup"><span data-stu-id="00a6e-127">Notifies the profiler that the currently executing function is about to perform a tail call to another function and provides information about the stack frame.</span></span> <span data-ttu-id="00a6e-128">.NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="00a6e-128">Deprecated in the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="00a6e-129">StackSnapshotCallback İşlevi</span><span class="sxs-lookup"><span data-stu-id="00a6e-129">StackSnapshotCallback Function</span></span>](stacksnapshotcallback-function.md)  
 <span data-ttu-id="00a6e-130">, Profil oluşturucuyu her yönetilen çerçeve ve yığın üzerinde her yönetilmeyen çerçeve, [ICorProfilerInfo2::D oStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) yöntemi tarafından başlatılan bir yığın ilerleme durumuyla ilgili bilgilerle birlikte sağlar.</span><span class="sxs-lookup"><span data-stu-id="00a6e-130">Provides the profiler with information about each managed frame and each run of unmanaged frames on the stack during a stack walk, which is initiated by the [ICorProfilerInfo2::DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="net-framework-version-4-profiling-functions"></a><span data-ttu-id="00a6e-131">.NET Framework sürüm 4 profil oluşturma Işlevleri</span><span class="sxs-lookup"><span data-stu-id="00a6e-131">.NET Framework version 4 Profiling Functions</span></span>  

 [<span data-ttu-id="00a6e-132">FunctionIDMapper2 İşlevi</span><span class="sxs-lookup"><span data-stu-id="00a6e-132">FunctionIDMapper2 Function</span></span>](functionidmapper2-function.md)  
 <span data-ttu-id="00a6e-133">Profil oluşturucuyu, bir işlevin verilen tanımlayıcısının, bu işlev için [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md)ve [FunctionTailcall3](functiontailcall3-function.md)veya[FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md)ve [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) geri çağırmalar içinde kullanılacak alternatif bir kimliğe yeniden eşlenilebileceği konusunda bilgilendirir.</span><span class="sxs-lookup"><span data-stu-id="00a6e-133">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md), and [FunctionTailcall3](functiontailcall3-function.md), or[FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) callbacks for that function.</span></span> <span data-ttu-id="00a6e-134">Ayrıca, profil oluşturucunun bu işlev için geri çağırmaları almak isteyip istemediğini belirtmek için de olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="00a6e-134">Also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
 <span data-ttu-id="00a6e-135">`FunctionIDMapper2`[FunctionIDMapper](functionidmapper-function.md) işlevini, çalışma `clientData` zamanları arasında belirsizliği ortadan kaldırmak için profil oluşturucular kullanılabilecek bir parametresiyle genişletir.</span><span class="sxs-lookup"><span data-stu-id="00a6e-135">`FunctionIDMapper2` extends the [FunctionIDMapper](functionidmapper-function.md) function with a `clientData` parameter, which profilers may use to disambiguate among runtimes.</span></span>  
  
 [<span data-ttu-id="00a6e-136">FunctionEnter3 İşlevi</span><span class="sxs-lookup"><span data-stu-id="00a6e-136">FunctionEnter3 Function</span></span>](functionenter3-function.md)  
 <span data-ttu-id="00a6e-137">Profil oluşturucuya denetimin bir işleve geçtiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="00a6e-137">Notifies the profiler that control is being passed to a function.</span></span>  
  
 [<span data-ttu-id="00a6e-138">FunctionEnter3WithInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="00a6e-138">FunctionEnter3WithInfo Function</span></span>](functionenter3withinfo-function.md)  
 <span data-ttu-id="00a6e-139">Denetim oluşturucuyu denetimin bir işleve geçtiğini bildirir ve yığın çerçevesini ve işlev bağımsız değişkenlerini almak için [ICorProfilerInfo3:: GetFunctionEnter3Info](icorprofilerinfo3-getfunctionenter3info-method.md) öğesine geçirilebilecek bir tanıtıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="00a6e-139">Notifies the profiler that control is being passed to a function, and provides a handle that can be passed to [ICorProfilerInfo3::GetFunctionEnter3Info](icorprofilerinfo3-getfunctionenter3info-method.md) to retrieve the stack frame and function arguments.</span></span>  
  
 [<span data-ttu-id="00a6e-140">FunctionLeave3 İşlevi</span><span class="sxs-lookup"><span data-stu-id="00a6e-140">FunctionLeave3 Function</span></span>](functionleave3-function.md)  
 <span data-ttu-id="00a6e-141">Denetim oluşturucuyu, denetimin bir işlevden döndürülmekte olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="00a6e-141">Notifies the profiler that control is being returned from a function.</span></span>  
  
 [<span data-ttu-id="00a6e-142">FunctionLeave3WithInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="00a6e-142">FunctionLeave3WithInfo Function</span></span>](functionleave3withinfo-function.md)  
 <span data-ttu-id="00a6e-143">Denetim oluşturucuyu denetimin bir işlevden döndürülmekte olduğunu bildirir ve yığın çerçevesini ve dönüş değerini almak için [ICorProfilerInfo3:: GetFunctionLeave3Info](icorprofilerinfo3-getfunctionleave3info-method.md) öğesine geçirilebilecek bir tanıtıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="00a6e-143">Notifies the profiler that control is being returned from a function, and provides a handle that can be passed to [ICorProfilerInfo3::GetFunctionLeave3Info](icorprofilerinfo3-getfunctionleave3info-method.md) to retrieve the stack frame and the return value.</span></span>  
  
 [<span data-ttu-id="00a6e-144">FunctionTailcall3 İşlevi</span><span class="sxs-lookup"><span data-stu-id="00a6e-144">FunctionTailcall3 Function</span></span>](functiontailcall3-function.md)  
 <span data-ttu-id="00a6e-145">Profil oluşturucuyu Şu anda yürütülmekte olan işlevin başka bir işleve tail çağrısı gerçekleştirmek üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="00a6e-145">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
 [<span data-ttu-id="00a6e-146">FunctionTailcall3WithInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="00a6e-146">FunctionTailcall3WithInfo Function</span></span>](functiontailcall3withinfo-function.md)  
 <span data-ttu-id="00a6e-147">Profiler 'ın Şu anda yürütülmekte olan işlevin başka bir işleve tail çağrısı gerçekleştirmek üzere olduğunu bildirir ve yığın çerçevesini almak için [ICorProfilerInfo3:: GetFunctionTailcall3Info](icorprofilerinfo3-getfunctiontailcall3info-method.md) öğesine geçirilebilecek bir tanıtıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="00a6e-147">Notifies the profiler that the currently executing function is about to perform a tail call to another function, and provides a handle that can be passed to [ICorProfilerInfo3::GetFunctionTailcall3Info](icorprofilerinfo3-getfunctiontailcall3info-method.md) to retrieve the stack frame.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="00a6e-148">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="00a6e-148">Related Sections</span></span>  

 [<span data-ttu-id="00a6e-149">Profil Oluşturmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="00a6e-149">Profiling Overview</span></span>](profiling-overview.md)  
  
 [<span data-ttu-id="00a6e-150">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="00a6e-150">Profiling Interfaces</span></span>](profiling-interfaces.md)  
  
 [<span data-ttu-id="00a6e-151">Profil Oluşturma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="00a6e-151">Profiling Enumerations</span></span>](profiling-enumerations.md)  
  
 [<span data-ttu-id="00a6e-152">Profil Oluşturma Yapıları</span><span class="sxs-lookup"><span data-stu-id="00a6e-152">Profiling Structures</span></span>](profiling-structures.md)
