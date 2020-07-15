---
title: Özel Durum Thrown_V1 ETW Olayı
description: ExceptionThrown_V1 ETW olayı hakkında ayrıntılı bilgileri görüntüleyin. Oluşturulan özel durumlar için alan adları, veri türleri ve açıklamalar gibi olay verileri verilir.
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
ms.openlocfilehash: f800a43d0ed2a82bc51a5e3a028b5fa1870df3fb
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309462"
---
# <a name="exception-thrown_v1-etw-event"></a><span data-ttu-id="0410d-104">Özel Durum Thrown_V1 ETW Olayı</span><span class="sxs-lookup"><span data-stu-id="0410d-104">Exception Thrown_V1 ETW Event</span></span>
<span data-ttu-id="0410d-105">Bu olay, oluşturulan özel durumlarla ilgili bilgileri yakalar.</span><span class="sxs-lookup"><span data-stu-id="0410d-105">This event captures information about the exceptions that are thrown.</span></span>  
  
 <span data-ttu-id="0410d-106">Aşağıdaki tabloda, olayın oluşturulduğu anahtar sözcük ve olay düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0410d-106">The following table shows the keyword under which the event is raised, and the level of the event.</span></span> <span data-ttu-id="0410d-107">(Daha fazla bilgi için bkz. [CLR ETW anahtar sözcükleri ve düzeyleri](clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="0410d-107">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="0410d-108">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="0410d-108">Keyword for raising the event</span></span>|<span data-ttu-id="0410d-109">Düzey</span><span class="sxs-lookup"><span data-stu-id="0410d-109">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="0410d-110">`ExceptionKeyword`0x8000</span><span class="sxs-lookup"><span data-stu-id="0410d-110">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="0410d-111">Uyarı (2)</span><span class="sxs-lookup"><span data-stu-id="0410d-111">Warning (2)</span></span>|  
  
 <span data-ttu-id="0410d-112">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0410d-112">The following table shows event information.</span></span>  
  
|<span data-ttu-id="0410d-113">Olay</span><span class="sxs-lookup"><span data-stu-id="0410d-113">Event</span></span>|<span data-ttu-id="0410d-114">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="0410d-114">Event ID</span></span>|<span data-ttu-id="0410d-115">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="0410d-115">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|<span data-ttu-id="0410d-116">80</span><span class="sxs-lookup"><span data-stu-id="0410d-116">80</span></span>|<span data-ttu-id="0410d-117">Yönetilen bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0410d-117">A managed exception is thrown.</span></span>|  
  
 <span data-ttu-id="0410d-118">Aşağıdaki tabloda olay verileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0410d-118">The following table shows event data.</span></span>  
  
|<span data-ttu-id="0410d-119">Alan adı</span><span class="sxs-lookup"><span data-stu-id="0410d-119">Field name</span></span>|<span data-ttu-id="0410d-120">Veri türü</span><span class="sxs-lookup"><span data-stu-id="0410d-120">Data type</span></span>|<span data-ttu-id="0410d-121">Description</span><span class="sxs-lookup"><span data-stu-id="0410d-121">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="0410d-122">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="0410d-122">Exception Type</span></span>|<span data-ttu-id="0410d-123">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="0410d-123">win:UnicodeString</span></span>|<span data-ttu-id="0410d-124">Özel durumun türü; Örneğin, `System.NullReferenceException` .</span><span class="sxs-lookup"><span data-stu-id="0410d-124">Type of the exception; for example, `System.NullReferenceException`.</span></span>|  
|<span data-ttu-id="0410d-125">Özel durum Iletisi</span><span class="sxs-lookup"><span data-stu-id="0410d-125">Exception Message</span></span>|<span data-ttu-id="0410d-126">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="0410d-126">win:UnicodeString</span></span>|<span data-ttu-id="0410d-127">Gerçek özel durum iletisi.</span><span class="sxs-lookup"><span data-stu-id="0410d-127">Actual exception message.</span></span>|  
|<span data-ttu-id="0410d-128">EIPCodeThrow</span><span class="sxs-lookup"><span data-stu-id="0410d-128">EIPCodeThrow</span></span>|<span data-ttu-id="0410d-129">Win: Işaretçi</span><span class="sxs-lookup"><span data-stu-id="0410d-129">win:Pointer</span></span>|<span data-ttu-id="0410d-130">Özel durumun oluştuğu yönerge işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="0410d-130">Instruction pointer where exception occurred.</span></span>|  
|<span data-ttu-id="0410d-131">ExceptionHR</span><span class="sxs-lookup"><span data-stu-id="0410d-131">ExceptionHR</span></span>|<span data-ttu-id="0410d-132">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="0410d-132">win:UInt32</span></span>|<span data-ttu-id="0410d-133">Özel durum [HRESULT](https://docs.microsoft.com/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).</span><span class="sxs-lookup"><span data-stu-id="0410d-133">Exception [HRESULT](https://docs.microsoft.com/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).</span></span>|  
|<span data-ttu-id="0410d-134">ExceptionFlags</span><span class="sxs-lookup"><span data-stu-id="0410d-134">ExceptionFlags</span></span>|<span data-ttu-id="0410d-135">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="0410d-135">win:UInt16</span></span>|<span data-ttu-id="0410d-136">0x01: HasInnerException (Visual Basic belgelerinde [CLR ETW olaylarını](clr-etw-events.md) görün).</span><span class="sxs-lookup"><span data-stu-id="0410d-136">0x01: HasInnerException (see [CLR ETW Events](clr-etw-events.md) in the Visual Basic documentation).</span></span><br /><br /> <span data-ttu-id="0410d-137">0x02: ısnestedexception.</span><span class="sxs-lookup"><span data-stu-id="0410d-137">0x02: IsNestedException.</span></span><br /><br /> <span data-ttu-id="0410d-138">0x04: IsRethrownException.</span><span class="sxs-lookup"><span data-stu-id="0410d-138">0x04: IsRethrownException.</span></span><br /><br /> <span data-ttu-id="0410d-139">0x08: ıbozulan Tedstateexception (işlem durumunun bozuk olduğunu gösterir; bkz. [bozuk durum özel durumlarını işleme](https://docs.microsoft.com/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).</span><span class="sxs-lookup"><span data-stu-id="0410d-139">0x08: IsCorruptedStateException (indicates that the process state is corrupt; see [Handling Corrupted State Exceptions](https://docs.microsoft.com/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).</span></span><br /><br /> <span data-ttu-id="0410d-140">0x10: ısclscompliant (öğesinden türetilen özel durum <xref:System.Exception> CLS uyumludur; Aksi takdirde, CLS uyumlu değildir).</span><span class="sxs-lookup"><span data-stu-id="0410d-140">0x10: IsCLSCompliant (an exception that derives from <xref:System.Exception> is CLS-compliant; otherwise, it is not CLS-compliant).</span></span>|  
|<span data-ttu-id="0410d-141">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0410d-141">ClrInstanceID</span></span>|<span data-ttu-id="0410d-142">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="0410d-142">win:UInt16</span></span>|<span data-ttu-id="0410d-143">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="0410d-143">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0410d-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0410d-144">See also</span></span>

- [<span data-ttu-id="0410d-145">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="0410d-145">CLR ETW Events</span></span>](clr-etw-events.md)
