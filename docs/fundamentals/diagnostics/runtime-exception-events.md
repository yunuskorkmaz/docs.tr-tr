---
title: Özel durum çalışma zamanı olayları
description: Özel durumlara ve özel durum işlemeye özgü tanılama bilgilerini toplayıp .NET çalışma zamanı olaylarına bakın.
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- exception events (CoreCLR)
- exception handling events (CoreCLR)
- ETW, EventPipe, LTTng exception events (CoreCLR)
ms.openlocfilehash: f4f63c8469f9c734b872ddaec8d1d7f7f0427576
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2021
ms.locfileid: "96590033"
---
# <a name="net-runtime-exception-events"></a><span data-ttu-id="6bd2d-103">.NET çalışma zamanı özel durum olayları</span><span class="sxs-lookup"><span data-stu-id="6bd2d-103">.NET runtime exception events</span></span>

<span data-ttu-id="6bd2d-104">Bu çalışma zamanı olayları, oluşturulan özel durumlarla ilgili bilgileri yakalar.</span><span class="sxs-lookup"><span data-stu-id="6bd2d-104">These runtime events capture information about exceptions that are thrown.</span></span> <span data-ttu-id="6bd2d-105">Bu olayların tanılama amacıyla nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [.NET uygulamalarını günlüğe kaydetme ve izleme](../../core/diagnostics/logging-tracing.md)</span><span class="sxs-lookup"><span data-stu-id="6bd2d-105">For more information about how to use these events for diagnostic purposes, see [logging and tracing .NET applications](../../core/diagnostics/logging-tracing.md)</span></span>

## <a name="exceptionthrown_v1-event"></a><span data-ttu-id="6bd2d-106">ExceptionThrown_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="6bd2d-106">ExceptionThrown_V1 event</span></span>

|<span data-ttu-id="6bd2d-107">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="6bd2d-107">Keyword for raising the event</span></span>|<span data-ttu-id="6bd2d-108">Level</span><span class="sxs-lookup"><span data-stu-id="6bd2d-108">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="6bd2d-109">`ExceptionKeyword` 0x8000</span><span class="sxs-lookup"><span data-stu-id="6bd2d-109">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="6bd2d-110">Hata (1)</span><span class="sxs-lookup"><span data-stu-id="6bd2d-110">Error (1)</span></span>|

 <span data-ttu-id="6bd2d-111">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6bd2d-111">The following table shows event information.</span></span>

|<span data-ttu-id="6bd2d-112">Olay</span><span class="sxs-lookup"><span data-stu-id="6bd2d-112">Event</span></span>|<span data-ttu-id="6bd2d-113">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="6bd2d-113">Event ID</span></span>|<span data-ttu-id="6bd2d-114">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="6bd2d-114">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionThrown_V1`|<span data-ttu-id="6bd2d-115">80</span><span class="sxs-lookup"><span data-stu-id="6bd2d-115">80</span></span>|<span data-ttu-id="6bd2d-116">Yönetilen bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6bd2d-116">A managed exception is thrown.</span></span>|

|<span data-ttu-id="6bd2d-117">Alan adı</span><span class="sxs-lookup"><span data-stu-id="6bd2d-117">Field name</span></span>|<span data-ttu-id="6bd2d-118">Veri türü</span><span class="sxs-lookup"><span data-stu-id="6bd2d-118">Data type</span></span>|<span data-ttu-id="6bd2d-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6bd2d-119">Description</span></span>|
|----------------|---------------|-----------------|
|`ExceptionType`|`win:UnicodeString`|<span data-ttu-id="6bd2d-120">Özel durumun türü; Örneğin, `System.NullReferenceException` .</span><span class="sxs-lookup"><span data-stu-id="6bd2d-120">Type of the exception; for example, `System.NullReferenceException`.</span></span>|
|`ExceptionMessage`|`win:UnicodeString`|<span data-ttu-id="6bd2d-121">Gerçek özel durum iletisi.</span><span class="sxs-lookup"><span data-stu-id="6bd2d-121">Actual exception message.</span></span>|
|`EIPCodeThrow`|`win:Pointer`|<span data-ttu-id="6bd2d-122">Özel durumun oluştuğu yönerge işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="6bd2d-122">Instruction pointer where exception occurred.</span></span>|
|`ExceptionHR`|`win:UInt32`|<span data-ttu-id="6bd2d-123">Özel durum [HRESULT](/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).</span><span class="sxs-lookup"><span data-stu-id="6bd2d-123">Exception [HRESULT](/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).</span></span>|
|`ExceptionFlags`|`win:UInt16`|<span data-ttu-id="6bd2d-124">`0x01`: HasInnerException.</span><span class="sxs-lookup"><span data-stu-id="6bd2d-124">`0x01`: HasInnerException.</span></span><br /><br /> <span data-ttu-id="6bd2d-125">`0x02`: IsNestedException.</span><span class="sxs-lookup"><span data-stu-id="6bd2d-125">`0x02`: IsNestedException.</span></span><br /><br /> <span data-ttu-id="6bd2d-126">`0x04`: IsRethrownException.</span><span class="sxs-lookup"><span data-stu-id="6bd2d-126">`0x04`: IsRethrownException.</span></span><br /><br /> <span data-ttu-id="6bd2d-127">`0x08`: Ibozulan Tedstateexception (işlem durumunun bozuk olduğunu gösterir; bkz. [bozuk durum özel durumlarını işleme](/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).</span><span class="sxs-lookup"><span data-stu-id="6bd2d-127">`0x08`: IsCorruptedStateException (indicates that the process state is corrupt; see [Handling Corrupted State Exceptions](/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).</span></span><br /><br /> <span data-ttu-id="6bd2d-128">`0x10`: Isclscompliant (öğesinden türetilen özel durum <xref:System.Exception> CLS uyumludur; Aksi takdirde, CLS uyumlu değildir).</span><span class="sxs-lookup"><span data-stu-id="6bd2d-128">`0x10`: IsCLSCompliant (an exception that derives from <xref:System.Exception> is CLS-compliant; otherwise, it is not CLS-compliant).</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="6bd2d-129">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="6bd2d-129">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="exceptioncatchstart-event"></a><span data-ttu-id="6bd2d-130">Exceptioncatch başlangıç olayı</span><span class="sxs-lookup"><span data-stu-id="6bd2d-130">ExceptionCatchStart event</span></span>

<span data-ttu-id="6bd2d-131">Bu olay, yönetilen bir özel durum catch işleyicisi başladığında yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="6bd2d-131">This event is emitted when a managed exception catch handler begins.</span></span>

|<span data-ttu-id="6bd2d-132">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="6bd2d-132">Keyword for raising the event</span></span>|<span data-ttu-id="6bd2d-133">Level</span><span class="sxs-lookup"><span data-stu-id="6bd2d-133">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="6bd2d-134">`ExceptionKeyword` 0x8000</span><span class="sxs-lookup"><span data-stu-id="6bd2d-134">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="6bd2d-135">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="6bd2d-135">Informational (4)</span></span>|

 <span data-ttu-id="6bd2d-136">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6bd2d-136">The following table shows event information.</span></span>

|<span data-ttu-id="6bd2d-137">Olay</span><span class="sxs-lookup"><span data-stu-id="6bd2d-137">Event</span></span>|<span data-ttu-id="6bd2d-138">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="6bd2d-138">Event ID</span></span>|<span data-ttu-id="6bd2d-139">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="6bd2d-139">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionCatchStart`|<span data-ttu-id="6bd2d-140">250</span><span class="sxs-lookup"><span data-stu-id="6bd2d-140">250</span></span>|<span data-ttu-id="6bd2d-141">Yönetilen bir özel durum, çalışma zamanı tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="6bd2d-141">A managed exception is handled by the runtime.</span></span>|

|<span data-ttu-id="6bd2d-142">Alan adı</span><span class="sxs-lookup"><span data-stu-id="6bd2d-142">Field name</span></span>|<span data-ttu-id="6bd2d-143">Veri türü</span><span class="sxs-lookup"><span data-stu-id="6bd2d-143">Data type</span></span>|<span data-ttu-id="6bd2d-144">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6bd2d-144">Description</span></span>|
|----------------|---------------|-----------------|
|`EIPCodeThrow`|`win:Pointer`|<span data-ttu-id="6bd2d-145">Özel durumun oluştuğu yönerge işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="6bd2d-145">Instruction pointer where exception occurred.</span></span>|
|`MethodID`|`win:Pointer`|<span data-ttu-id="6bd2d-146">Özel durumun oluştuğu yöntemde Yöntem tanımlayıcısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6bd2d-146">Pointer to the method descriptor on the method where exception occurred.</span></span>|
|`MethodName`|`win:UnicodeString`|<span data-ttu-id="6bd2d-147">Özel durumun oluştuğu yöntemin adı.</span><span class="sxs-lookup"><span data-stu-id="6bd2d-147">Name of the method where exception occurred.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="6bd2d-148">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="6bd2d-148">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="exceptioncatchstop-event"></a><span data-ttu-id="6bd2d-149">Exceptioncatch durdurma olayı</span><span class="sxs-lookup"><span data-stu-id="6bd2d-149">ExceptionCatchStop event</span></span>

<span data-ttu-id="6bd2d-150">Bu olay, yönetilen bir özel durum catch işleyicisi sona erdiğinde yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="6bd2d-150">This event is emitted when a managed exception catch handler ends.</span></span>

|<span data-ttu-id="6bd2d-151">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="6bd2d-151">Keyword for raising the event</span></span>|<span data-ttu-id="6bd2d-152">Level</span><span class="sxs-lookup"><span data-stu-id="6bd2d-152">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="6bd2d-153">`ExceptionKeyword` 0x8000</span><span class="sxs-lookup"><span data-stu-id="6bd2d-153">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="6bd2d-154">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="6bd2d-154">Informational (4)</span></span>|

 <span data-ttu-id="6bd2d-155">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6bd2d-155">The following table shows event information.</span></span>

|<span data-ttu-id="6bd2d-156">Olay</span><span class="sxs-lookup"><span data-stu-id="6bd2d-156">Event</span></span>|<span data-ttu-id="6bd2d-157">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="6bd2d-157">Event ID</span></span>|<span data-ttu-id="6bd2d-158">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="6bd2d-158">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionCatchStop`|<span data-ttu-id="6bd2d-159">251</span><span class="sxs-lookup"><span data-stu-id="6bd2d-159">251</span></span>|<span data-ttu-id="6bd2d-160">Yönetilen bir özel durum yakalama işleyicisi bitti.</span><span class="sxs-lookup"><span data-stu-id="6bd2d-160">A managed exception catch handler is done.</span></span>|

## <a name="exceptionfinallystart-event"></a><span data-ttu-id="6bd2d-161">ExceptionFinallyStart olayı</span><span class="sxs-lookup"><span data-stu-id="6bd2d-161">ExceptionFinallyStart event</span></span>

<span data-ttu-id="6bd2d-162">Bu olay yönetilen bir özel durum finally işleyicisi başladığında yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="6bd2d-162">This event is emitted when a managed exception finally handler begins.</span></span>

|<span data-ttu-id="6bd2d-163">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="6bd2d-163">Keyword for raising the event</span></span>|<span data-ttu-id="6bd2d-164">Level</span><span class="sxs-lookup"><span data-stu-id="6bd2d-164">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="6bd2d-165">`ExceptionKeyword` 0x8000</span><span class="sxs-lookup"><span data-stu-id="6bd2d-165">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="6bd2d-166">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="6bd2d-166">Informational (4)</span></span>|

 <span data-ttu-id="6bd2d-167">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6bd2d-167">The following table shows event information.</span></span>

|<span data-ttu-id="6bd2d-168">Olay</span><span class="sxs-lookup"><span data-stu-id="6bd2d-168">Event</span></span>|<span data-ttu-id="6bd2d-169">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="6bd2d-169">Event ID</span></span>|<span data-ttu-id="6bd2d-170">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="6bd2d-170">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionFinallyStart`|<span data-ttu-id="6bd2d-171">252</span><span class="sxs-lookup"><span data-stu-id="6bd2d-171">252</span></span>|<span data-ttu-id="6bd2d-172">Yönetilen bir özel durum, çalışma zamanı tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="6bd2d-172">A managed exception is handled by the runtime.</span></span>|

|<span data-ttu-id="6bd2d-173">Alan adı</span><span class="sxs-lookup"><span data-stu-id="6bd2d-173">Field name</span></span>|<span data-ttu-id="6bd2d-174">Veri türü</span><span class="sxs-lookup"><span data-stu-id="6bd2d-174">Data type</span></span>|<span data-ttu-id="6bd2d-175">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6bd2d-175">Description</span></span>|
|----------------|---------------|-----------------|
|`EIPCodeThrow`|`win:Pointer`|<span data-ttu-id="6bd2d-176">Özel durumun oluştuğu yönerge işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="6bd2d-176">Instruction pointer where exception occurred.</span></span>|
|`MethodID`|`win:Pointer`|<span data-ttu-id="6bd2d-177">Özel durumun oluştuğu yöntemde Yöntem tanımlayıcısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6bd2d-177">Pointer to the method descriptor on the method where exception occurred.</span></span>|
|`MethodName`|`win:UnicodeString`|<span data-ttu-id="6bd2d-178">Özel durumun oluştuğu yöntemin adı.</span><span class="sxs-lookup"><span data-stu-id="6bd2d-178">Name of the method where exception occurred.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="6bd2d-179">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="6bd2d-179">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="exceptionfinallystop-event"></a><span data-ttu-id="6bd2d-180">ExceptionFinallyStop olayı</span><span class="sxs-lookup"><span data-stu-id="6bd2d-180">ExceptionFinallyStop event</span></span>

<span data-ttu-id="6bd2d-181">Bu olay, yönetilen bir özel durum catch işleyicisi sona erdiğinde yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="6bd2d-181">This event is emitted when a managed exception catch handler ends.</span></span>

|<span data-ttu-id="6bd2d-182">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="6bd2d-182">Keyword for raising the event</span></span>|<span data-ttu-id="6bd2d-183">Level</span><span class="sxs-lookup"><span data-stu-id="6bd2d-183">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="6bd2d-184">`ExceptionKeyword` 0x8000</span><span class="sxs-lookup"><span data-stu-id="6bd2d-184">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="6bd2d-185">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="6bd2d-185">Informational (4)</span></span>|

 <span data-ttu-id="6bd2d-186">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6bd2d-186">The following table shows event information.</span></span>

|<span data-ttu-id="6bd2d-187">Olay</span><span class="sxs-lookup"><span data-stu-id="6bd2d-187">Event</span></span>|<span data-ttu-id="6bd2d-188">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="6bd2d-188">Event ID</span></span>|<span data-ttu-id="6bd2d-189">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="6bd2d-189">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionFinallyStop`|<span data-ttu-id="6bd2d-190">253</span><span class="sxs-lookup"><span data-stu-id="6bd2d-190">253</span></span>|<span data-ttu-id="6bd2d-191">Yönetilen bir özel durum finally işleyicisi bitti.</span><span class="sxs-lookup"><span data-stu-id="6bd2d-191">A managed exception finally handler is done.</span></span>|

## <a name="exceptionfilterstart-event"></a><span data-ttu-id="6bd2d-192">ExceptionFilterStart olayı</span><span class="sxs-lookup"><span data-stu-id="6bd2d-192">ExceptionFilterStart event</span></span>

<span data-ttu-id="6bd2d-193">Bu olay, yönetilen bir özel durum filtrelemesi başladığında yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="6bd2d-193">This event is emitted when a managed exception filtering begins.</span></span>

|<span data-ttu-id="6bd2d-194">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="6bd2d-194">Keyword for raising the event</span></span>|<span data-ttu-id="6bd2d-195">Level</span><span class="sxs-lookup"><span data-stu-id="6bd2d-195">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="6bd2d-196">`ExceptionKeyword` 0x8000</span><span class="sxs-lookup"><span data-stu-id="6bd2d-196">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="6bd2d-197">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="6bd2d-197">Informational (4)</span></span>|

 <span data-ttu-id="6bd2d-198">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6bd2d-198">The following table shows event information.</span></span>

|<span data-ttu-id="6bd2d-199">Olay</span><span class="sxs-lookup"><span data-stu-id="6bd2d-199">Event</span></span>|<span data-ttu-id="6bd2d-200">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="6bd2d-200">Event ID</span></span>|<span data-ttu-id="6bd2d-201">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="6bd2d-201">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionFilterStart`|<span data-ttu-id="6bd2d-202">254</span><span class="sxs-lookup"><span data-stu-id="6bd2d-202">254</span></span>|<span data-ttu-id="6bd2d-203">Yönetilen özel durum filtrelemesi başlar.</span><span class="sxs-lookup"><span data-stu-id="6bd2d-203">A managed exception filtering begins.</span></span>|

|<span data-ttu-id="6bd2d-204">Alan adı</span><span class="sxs-lookup"><span data-stu-id="6bd2d-204">Field name</span></span>|<span data-ttu-id="6bd2d-205">Veri türü</span><span class="sxs-lookup"><span data-stu-id="6bd2d-205">Data type</span></span>|<span data-ttu-id="6bd2d-206">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6bd2d-206">Description</span></span>|
|----------------|---------------|-----------------|
|`EIPCodeThrow`|`win:Pointer`|<span data-ttu-id="6bd2d-207">Özel durumun oluştuğu yönerge işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="6bd2d-207">Instruction pointer where exception occurred.</span></span>|
|`MethodID`|`win:Pointer`|<span data-ttu-id="6bd2d-208">Özel durumun oluştuğu yöntemde Yöntem tanımlayıcısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6bd2d-208">Pointer to the method descriptor on the method where exception occurred.</span></span>|
|`MethodName`|`win:UnicodeString`|<span data-ttu-id="6bd2d-209">Özel durumun oluştuğu yöntemin adı.</span><span class="sxs-lookup"><span data-stu-id="6bd2d-209">Name of the method where exception occurred.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="6bd2d-210">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="6bd2d-210">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="exceptionfilterstop-event"></a><span data-ttu-id="6bd2d-211">ExceptionFilterStop olayı</span><span class="sxs-lookup"><span data-stu-id="6bd2d-211">ExceptionFilterStop event</span></span>

<span data-ttu-id="6bd2d-212">Yönetilen özel durum filtrelemesi sona erdiğinde bu olay yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="6bd2d-212">This event is emitted when a managed exception filtering ends.</span></span>

|<span data-ttu-id="6bd2d-213">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="6bd2d-213">Keyword for raising the event</span></span>|<span data-ttu-id="6bd2d-214">Level</span><span class="sxs-lookup"><span data-stu-id="6bd2d-214">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="6bd2d-215">`ExceptionKeyword` 0x8000</span><span class="sxs-lookup"><span data-stu-id="6bd2d-215">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="6bd2d-216">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="6bd2d-216">Informational (4)</span></span>|

 <span data-ttu-id="6bd2d-217">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6bd2d-217">The following table shows event information.</span></span>

|<span data-ttu-id="6bd2d-218">Olay</span><span class="sxs-lookup"><span data-stu-id="6bd2d-218">Event</span></span>|<span data-ttu-id="6bd2d-219">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="6bd2d-219">Event ID</span></span>|<span data-ttu-id="6bd2d-220">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="6bd2d-220">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionFilteringStart`|<span data-ttu-id="6bd2d-221">255</span><span class="sxs-lookup"><span data-stu-id="6bd2d-221">255</span></span>|<span data-ttu-id="6bd2d-222">Yönetilen özel durum filtreleme sona erer.</span><span class="sxs-lookup"><span data-stu-id="6bd2d-222">A managed exception filtering ends.</span></span>|

## <a name="exceptionthrownstop-event"></a><span data-ttu-id="6bd2d-223">ExceptionThrownStop olayı</span><span class="sxs-lookup"><span data-stu-id="6bd2d-223">ExceptionThrownStop event</span></span>

<span data-ttu-id="6bd2d-224">Bu olay, çalışma zamanı oluşturulan yönetilen bir özel durumu işlemeye çalışırken yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="6bd2d-224">This event is emitted when the runtime is done handling a managed exception that was thrown.</span></span>

|<span data-ttu-id="6bd2d-225">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="6bd2d-225">Keyword for raising the event</span></span>|<span data-ttu-id="6bd2d-226">Level</span><span class="sxs-lookup"><span data-stu-id="6bd2d-226">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="6bd2d-227">`ExceptionKeyword` 0x8000</span><span class="sxs-lookup"><span data-stu-id="6bd2d-227">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="6bd2d-228">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="6bd2d-228">Informational (4)</span></span>|
  
 <span data-ttu-id="6bd2d-229">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6bd2d-229">The following table shows event information.</span></span>

|<span data-ttu-id="6bd2d-230">Olay</span><span class="sxs-lookup"><span data-stu-id="6bd2d-230">Event</span></span>|<span data-ttu-id="6bd2d-231">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="6bd2d-231">Event ID</span></span>|<span data-ttu-id="6bd2d-232">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="6bd2d-232">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionThrownStop`|<span data-ttu-id="6bd2d-233">256</span><span class="sxs-lookup"><span data-stu-id="6bd2d-233">256</span></span>|<span data-ttu-id="6bd2d-234">Yönetilen özel durum filtreleme sona erer.</span><span class="sxs-lookup"><span data-stu-id="6bd2d-234">A managed exception filtering ends.</span></span>|
