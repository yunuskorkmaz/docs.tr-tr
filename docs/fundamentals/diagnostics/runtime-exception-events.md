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
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96590033"
---
# <a name="net-runtime-exception-events"></a><span data-ttu-id="6ec09-103">.NET çalışma zamanı özel durum olayları</span><span class="sxs-lookup"><span data-stu-id="6ec09-103">.NET runtime exception events</span></span>

<span data-ttu-id="6ec09-104">Bu çalışma zamanı olayları, oluşturulan özel durumlarla ilgili bilgileri yakalar.</span><span class="sxs-lookup"><span data-stu-id="6ec09-104">These runtime events capture information about exceptions that are thrown.</span></span> <span data-ttu-id="6ec09-105">Bu olayların tanılama amacıyla nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [.NET uygulamalarını günlüğe kaydetme ve izleme](../../core/diagnostics/logging-tracing.md)</span><span class="sxs-lookup"><span data-stu-id="6ec09-105">For more information about how to use these events for diagnostic purposes, see [logging and tracing .NET applications](../../core/diagnostics/logging-tracing.md)</span></span>

## <a name="exceptionthrown_v1-event"></a><span data-ttu-id="6ec09-106">ExceptionThrown_V1 olayı</span><span class="sxs-lookup"><span data-stu-id="6ec09-106">ExceptionThrown_V1 event</span></span>

|<span data-ttu-id="6ec09-107">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="6ec09-107">Keyword for raising the event</span></span>|<span data-ttu-id="6ec09-108">Level</span><span class="sxs-lookup"><span data-stu-id="6ec09-108">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="6ec09-109">`ExceptionKeyword` 0x8000</span><span class="sxs-lookup"><span data-stu-id="6ec09-109">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="6ec09-110">Hata (1)</span><span class="sxs-lookup"><span data-stu-id="6ec09-110">Error (1)</span></span>|

 <span data-ttu-id="6ec09-111">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6ec09-111">The following table shows event information.</span></span>

|<span data-ttu-id="6ec09-112">Olay</span><span class="sxs-lookup"><span data-stu-id="6ec09-112">Event</span></span>|<span data-ttu-id="6ec09-113">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="6ec09-113">Event ID</span></span>|<span data-ttu-id="6ec09-114">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="6ec09-114">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionThrown_V1`|<span data-ttu-id="6ec09-115">80</span><span class="sxs-lookup"><span data-stu-id="6ec09-115">80</span></span>|<span data-ttu-id="6ec09-116">Yönetilen bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6ec09-116">A managed exception is thrown.</span></span>|

|<span data-ttu-id="6ec09-117">Alan adı</span><span class="sxs-lookup"><span data-stu-id="6ec09-117">Field name</span></span>|<span data-ttu-id="6ec09-118">Veri türü</span><span class="sxs-lookup"><span data-stu-id="6ec09-118">Data type</span></span>|<span data-ttu-id="6ec09-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6ec09-119">Description</span></span>|
|----------------|---------------|-----------------|
|`ExceptionType`|`win:UnicodeString`|<span data-ttu-id="6ec09-120">Özel durumun türü; Örneğin, `System.NullReferenceException` .</span><span class="sxs-lookup"><span data-stu-id="6ec09-120">Type of the exception; for example, `System.NullReferenceException`.</span></span>|
|`ExceptionMessage`|`win:UnicodeString`|<span data-ttu-id="6ec09-121">Gerçek özel durum iletisi.</span><span class="sxs-lookup"><span data-stu-id="6ec09-121">Actual exception message.</span></span>|
|`EIPCodeThrow`|`win:Pointer`|<span data-ttu-id="6ec09-122">Özel durumun oluştuğu yönerge işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="6ec09-122">Instruction pointer where exception occurred.</span></span>|
|`ExceptionHR`|`win:UInt32`|<span data-ttu-id="6ec09-123">Özel durum [HRESULT](/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).</span><span class="sxs-lookup"><span data-stu-id="6ec09-123">Exception [HRESULT](/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).</span></span>|
|`ExceptionFlags`|`win:UInt16`|<span data-ttu-id="6ec09-124">`0x01`: HasInnerException.</span><span class="sxs-lookup"><span data-stu-id="6ec09-124">`0x01`: HasInnerException.</span></span><br /><br /> <span data-ttu-id="6ec09-125">`0x02`: IsNestedException.</span><span class="sxs-lookup"><span data-stu-id="6ec09-125">`0x02`: IsNestedException.</span></span><br /><br /> <span data-ttu-id="6ec09-126">`0x04`: IsRethrownException.</span><span class="sxs-lookup"><span data-stu-id="6ec09-126">`0x04`: IsRethrownException.</span></span><br /><br /> <span data-ttu-id="6ec09-127">`0x08`: Ibozulan Tedstateexception (işlem durumunun bozuk olduğunu gösterir; bkz. [bozuk durum özel durumlarını işleme](/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).</span><span class="sxs-lookup"><span data-stu-id="6ec09-127">`0x08`: IsCorruptedStateException (indicates that the process state is corrupt; see [Handling Corrupted State Exceptions](/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).</span></span><br /><br /> <span data-ttu-id="6ec09-128">`0x10`: Isclscompliant (öğesinden türetilen özel durum <xref:System.Exception> CLS uyumludur; Aksi takdirde, CLS uyumlu değildir).</span><span class="sxs-lookup"><span data-stu-id="6ec09-128">`0x10`: IsCLSCompliant (an exception that derives from <xref:System.Exception> is CLS-compliant; otherwise, it is not CLS-compliant).</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="6ec09-129">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="6ec09-129">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="exceptioncatchstart-event"></a><span data-ttu-id="6ec09-130">Exceptioncatch başlangıç olayı</span><span class="sxs-lookup"><span data-stu-id="6ec09-130">ExceptionCatchStart event</span></span>

<span data-ttu-id="6ec09-131">Bu olay, yönetilen bir özel durum catch işleyicisi başladığında yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="6ec09-131">This event is emitted when a managed exception catch handler begins.</span></span>

|<span data-ttu-id="6ec09-132">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="6ec09-132">Keyword for raising the event</span></span>|<span data-ttu-id="6ec09-133">Level</span><span class="sxs-lookup"><span data-stu-id="6ec09-133">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="6ec09-134">`ExceptionKeyword` 0x8000</span><span class="sxs-lookup"><span data-stu-id="6ec09-134">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="6ec09-135">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="6ec09-135">Informational (4)</span></span>|

 <span data-ttu-id="6ec09-136">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6ec09-136">The following table shows event information.</span></span>

|<span data-ttu-id="6ec09-137">Olay</span><span class="sxs-lookup"><span data-stu-id="6ec09-137">Event</span></span>|<span data-ttu-id="6ec09-138">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="6ec09-138">Event ID</span></span>|<span data-ttu-id="6ec09-139">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="6ec09-139">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionCatchStart`|<span data-ttu-id="6ec09-140">250</span><span class="sxs-lookup"><span data-stu-id="6ec09-140">250</span></span>|<span data-ttu-id="6ec09-141">Yönetilen bir özel durum, çalışma zamanı tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="6ec09-141">A managed exception is handled by the runtime.</span></span>|

|<span data-ttu-id="6ec09-142">Alan adı</span><span class="sxs-lookup"><span data-stu-id="6ec09-142">Field name</span></span>|<span data-ttu-id="6ec09-143">Veri türü</span><span class="sxs-lookup"><span data-stu-id="6ec09-143">Data type</span></span>|<span data-ttu-id="6ec09-144">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6ec09-144">Description</span></span>|
|----------------|---------------|-----------------|
|`EIPCodeThrow`|`win:Pointer`|<span data-ttu-id="6ec09-145">Özel durumun oluştuğu yönerge işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="6ec09-145">Instruction pointer where exception occurred.</span></span>|
|`MethodID`|`win:Pointer`|<span data-ttu-id="6ec09-146">Özel durumun oluştuğu yöntemde Yöntem tanımlayıcısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6ec09-146">Pointer to the method descriptor on the method where exception occurred.</span></span>|
|`MethodName`|`win:UnicodeString`|<span data-ttu-id="6ec09-147">Özel durumun oluştuğu yöntemin adı.</span><span class="sxs-lookup"><span data-stu-id="6ec09-147">Name of the method where exception occurred.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="6ec09-148">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="6ec09-148">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="exceptioncatchstop-event"></a><span data-ttu-id="6ec09-149">Exceptioncatch durdurma olayı</span><span class="sxs-lookup"><span data-stu-id="6ec09-149">ExceptionCatchStop event</span></span>

<span data-ttu-id="6ec09-150">Bu olay, yönetilen bir özel durum catch işleyicisi sona erdiğinde yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="6ec09-150">This event is emitted when a managed exception catch handler ends.</span></span>

|<span data-ttu-id="6ec09-151">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="6ec09-151">Keyword for raising the event</span></span>|<span data-ttu-id="6ec09-152">Level</span><span class="sxs-lookup"><span data-stu-id="6ec09-152">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="6ec09-153">`ExceptionKeyword` 0x8000</span><span class="sxs-lookup"><span data-stu-id="6ec09-153">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="6ec09-154">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="6ec09-154">Informational (4)</span></span>|

 <span data-ttu-id="6ec09-155">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6ec09-155">The following table shows event information.</span></span>

|<span data-ttu-id="6ec09-156">Olay</span><span class="sxs-lookup"><span data-stu-id="6ec09-156">Event</span></span>|<span data-ttu-id="6ec09-157">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="6ec09-157">Event ID</span></span>|<span data-ttu-id="6ec09-158">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="6ec09-158">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionCatchStop`|<span data-ttu-id="6ec09-159">251</span><span class="sxs-lookup"><span data-stu-id="6ec09-159">251</span></span>|<span data-ttu-id="6ec09-160">Yönetilen bir özel durum yakalama işleyicisi bitti.</span><span class="sxs-lookup"><span data-stu-id="6ec09-160">A managed exception catch handler is done.</span></span>|

## <a name="exceptionfinallystart-event"></a><span data-ttu-id="6ec09-161">ExceptionFinallyStart olayı</span><span class="sxs-lookup"><span data-stu-id="6ec09-161">ExceptionFinallyStart event</span></span>

<span data-ttu-id="6ec09-162">Bu olay yönetilen bir özel durum finally işleyicisi başladığında yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="6ec09-162">This event is emitted when a managed exception finally handler begins.</span></span>

|<span data-ttu-id="6ec09-163">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="6ec09-163">Keyword for raising the event</span></span>|<span data-ttu-id="6ec09-164">Level</span><span class="sxs-lookup"><span data-stu-id="6ec09-164">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="6ec09-165">`ExceptionKeyword` 0x8000</span><span class="sxs-lookup"><span data-stu-id="6ec09-165">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="6ec09-166">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="6ec09-166">Informational (4)</span></span>|

 <span data-ttu-id="6ec09-167">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6ec09-167">The following table shows event information.</span></span>

|<span data-ttu-id="6ec09-168">Olay</span><span class="sxs-lookup"><span data-stu-id="6ec09-168">Event</span></span>|<span data-ttu-id="6ec09-169">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="6ec09-169">Event ID</span></span>|<span data-ttu-id="6ec09-170">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="6ec09-170">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionFinallyStart`|<span data-ttu-id="6ec09-171">252</span><span class="sxs-lookup"><span data-stu-id="6ec09-171">252</span></span>|<span data-ttu-id="6ec09-172">Yönetilen bir özel durum, çalışma zamanı tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="6ec09-172">A managed exception is handled by the runtime.</span></span>|

|<span data-ttu-id="6ec09-173">Alan adı</span><span class="sxs-lookup"><span data-stu-id="6ec09-173">Field name</span></span>|<span data-ttu-id="6ec09-174">Veri türü</span><span class="sxs-lookup"><span data-stu-id="6ec09-174">Data type</span></span>|<span data-ttu-id="6ec09-175">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6ec09-175">Description</span></span>|
|----------------|---------------|-----------------|
|`EIPCodeThrow`|`win:Pointer`|<span data-ttu-id="6ec09-176">Özel durumun oluştuğu yönerge işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="6ec09-176">Instruction pointer where exception occurred.</span></span>|
|`MethodID`|`win:Pointer`|<span data-ttu-id="6ec09-177">Özel durumun oluştuğu yöntemde Yöntem tanımlayıcısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6ec09-177">Pointer to the method descriptor on the method where exception occurred.</span></span>|
|`MethodName`|`win:UnicodeString`|<span data-ttu-id="6ec09-178">Özel durumun oluştuğu yöntemin adı.</span><span class="sxs-lookup"><span data-stu-id="6ec09-178">Name of the method where exception occurred.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="6ec09-179">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="6ec09-179">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="exceptionfinallystop-event"></a><span data-ttu-id="6ec09-180">ExceptionFinallyStop olayı</span><span class="sxs-lookup"><span data-stu-id="6ec09-180">ExceptionFinallyStop event</span></span>

<span data-ttu-id="6ec09-181">Bu olay, yönetilen bir özel durum catch işleyicisi sona erdiğinde yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="6ec09-181">This event is emitted when a managed exception catch handler ends.</span></span>

|<span data-ttu-id="6ec09-182">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="6ec09-182">Keyword for raising the event</span></span>|<span data-ttu-id="6ec09-183">Level</span><span class="sxs-lookup"><span data-stu-id="6ec09-183">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="6ec09-184">`ExceptionKeyword` 0x8000</span><span class="sxs-lookup"><span data-stu-id="6ec09-184">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="6ec09-185">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="6ec09-185">Informational (4)</span></span>|

 <span data-ttu-id="6ec09-186">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6ec09-186">The following table shows event information.</span></span>

|<span data-ttu-id="6ec09-187">Olay</span><span class="sxs-lookup"><span data-stu-id="6ec09-187">Event</span></span>|<span data-ttu-id="6ec09-188">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="6ec09-188">Event ID</span></span>|<span data-ttu-id="6ec09-189">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="6ec09-189">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionFinallyStop`|<span data-ttu-id="6ec09-190">253</span><span class="sxs-lookup"><span data-stu-id="6ec09-190">253</span></span>|<span data-ttu-id="6ec09-191">Yönetilen bir özel durum finally işleyicisi bitti.</span><span class="sxs-lookup"><span data-stu-id="6ec09-191">A managed exception finally handler is done.</span></span>|

## <a name="exceptionfilterstart-event"></a><span data-ttu-id="6ec09-192">ExceptionFilterStart olayı</span><span class="sxs-lookup"><span data-stu-id="6ec09-192">ExceptionFilterStart event</span></span>

<span data-ttu-id="6ec09-193">Bu olay, yönetilen bir özel durum filtrelemesi başladığında yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="6ec09-193">This event is emitted when a managed exception filtering begins.</span></span>

|<span data-ttu-id="6ec09-194">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="6ec09-194">Keyword for raising the event</span></span>|<span data-ttu-id="6ec09-195">Level</span><span class="sxs-lookup"><span data-stu-id="6ec09-195">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="6ec09-196">`ExceptionKeyword` 0x8000</span><span class="sxs-lookup"><span data-stu-id="6ec09-196">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="6ec09-197">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="6ec09-197">Informational (4)</span></span>|

 <span data-ttu-id="6ec09-198">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6ec09-198">The following table shows event information.</span></span>

|<span data-ttu-id="6ec09-199">Olay</span><span class="sxs-lookup"><span data-stu-id="6ec09-199">Event</span></span>|<span data-ttu-id="6ec09-200">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="6ec09-200">Event ID</span></span>|<span data-ttu-id="6ec09-201">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="6ec09-201">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionFilterStart`|<span data-ttu-id="6ec09-202">254</span><span class="sxs-lookup"><span data-stu-id="6ec09-202">254</span></span>|<span data-ttu-id="6ec09-203">Yönetilen özel durum filtrelemesi başlar.</span><span class="sxs-lookup"><span data-stu-id="6ec09-203">A managed exception filtering begins.</span></span>|

|<span data-ttu-id="6ec09-204">Alan adı</span><span class="sxs-lookup"><span data-stu-id="6ec09-204">Field name</span></span>|<span data-ttu-id="6ec09-205">Veri türü</span><span class="sxs-lookup"><span data-stu-id="6ec09-205">Data type</span></span>|<span data-ttu-id="6ec09-206">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6ec09-206">Description</span></span>|
|----------------|---------------|-----------------|
|`EIPCodeThrow`|`win:Pointer`|<span data-ttu-id="6ec09-207">Özel durumun oluştuğu yönerge işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="6ec09-207">Instruction pointer where exception occurred.</span></span>|
|`MethodID`|`win:Pointer`|<span data-ttu-id="6ec09-208">Özel durumun oluştuğu yöntemde Yöntem tanımlayıcısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6ec09-208">Pointer to the method descriptor on the method where exception occurred.</span></span>|
|`MethodName`|`win:UnicodeString`|<span data-ttu-id="6ec09-209">Özel durumun oluştuğu yöntemin adı.</span><span class="sxs-lookup"><span data-stu-id="6ec09-209">Name of the method where exception occurred.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="6ec09-210">CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="6ec09-210">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="exceptionfilterstop-event"></a><span data-ttu-id="6ec09-211">ExceptionFilterStop olayı</span><span class="sxs-lookup"><span data-stu-id="6ec09-211">ExceptionFilterStop event</span></span>

<span data-ttu-id="6ec09-212">Yönetilen özel durum filtrelemesi sona erdiğinde bu olay yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="6ec09-212">This event is emitted when a managed exception filtering ends.</span></span>

|<span data-ttu-id="6ec09-213">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="6ec09-213">Keyword for raising the event</span></span>|<span data-ttu-id="6ec09-214">Level</span><span class="sxs-lookup"><span data-stu-id="6ec09-214">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="6ec09-215">`ExceptionKeyword` 0x8000</span><span class="sxs-lookup"><span data-stu-id="6ec09-215">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="6ec09-216">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="6ec09-216">Informational (4)</span></span>|

 <span data-ttu-id="6ec09-217">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6ec09-217">The following table shows event information.</span></span>

|<span data-ttu-id="6ec09-218">Olay</span><span class="sxs-lookup"><span data-stu-id="6ec09-218">Event</span></span>|<span data-ttu-id="6ec09-219">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="6ec09-219">Event ID</span></span>|<span data-ttu-id="6ec09-220">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="6ec09-220">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionFilteringStart`|<span data-ttu-id="6ec09-221">255</span><span class="sxs-lookup"><span data-stu-id="6ec09-221">255</span></span>|<span data-ttu-id="6ec09-222">Yönetilen özel durum filtreleme sona erer.</span><span class="sxs-lookup"><span data-stu-id="6ec09-222">A managed exception filtering ends.</span></span>|

## <a name="exceptionthrownstop-event"></a><span data-ttu-id="6ec09-223">ExceptionThrownStop olayı</span><span class="sxs-lookup"><span data-stu-id="6ec09-223">ExceptionThrownStop event</span></span>

<span data-ttu-id="6ec09-224">Bu olay, çalışma zamanı oluşturulan yönetilen bir özel durumu işlemeye çalışırken yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="6ec09-224">This event is emitted when the runtime is done handling a managed exception that was thrown.</span></span>

|<span data-ttu-id="6ec09-225">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="6ec09-225">Keyword for raising the event</span></span>|<span data-ttu-id="6ec09-226">Level</span><span class="sxs-lookup"><span data-stu-id="6ec09-226">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="6ec09-227">`ExceptionKeyword` 0x8000</span><span class="sxs-lookup"><span data-stu-id="6ec09-227">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="6ec09-228">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="6ec09-228">Informational (4)</span></span>|
  
 <span data-ttu-id="6ec09-229">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6ec09-229">The following table shows event information.</span></span>

|<span data-ttu-id="6ec09-230">Olay</span><span class="sxs-lookup"><span data-stu-id="6ec09-230">Event</span></span>|<span data-ttu-id="6ec09-231">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="6ec09-231">Event ID</span></span>|<span data-ttu-id="6ec09-232">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="6ec09-232">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionThrownStop`|<span data-ttu-id="6ec09-233">256</span><span class="sxs-lookup"><span data-stu-id="6ec09-233">256</span></span>|<span data-ttu-id="6ec09-234">Yönetilen özel durum filtreleme sona erer.</span><span class="sxs-lookup"><span data-stu-id="6ec09-234">A managed exception filtering ends.</span></span>|
