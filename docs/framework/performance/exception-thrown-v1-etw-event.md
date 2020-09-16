---
title: Özel Durum Thrown_V1 ETW Olayı
description: ExceptionThrown_V1 ETW olayı hakkında ayrıntılı bilgileri görüntüleyin. Oluşturulan özel durumlar için alan adları, veri türleri ve açıklamalar gibi olay verileri verilir.
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
ms.openlocfilehash: f4ae277b5dfb09d2676755fec2208b63906ead84
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554677"
---
# <a name="exception-thrown_v1-etw-event"></a><span data-ttu-id="b9085-104">Özel Durum Thrown_V1 ETW Olayı</span><span class="sxs-lookup"><span data-stu-id="b9085-104">Exception Thrown_V1 ETW Event</span></span>
<span data-ttu-id="b9085-105">Bu olay, oluşturulan özel durumlarla ilgili bilgileri yakalar.</span><span class="sxs-lookup"><span data-stu-id="b9085-105">This event captures information about the exceptions that are thrown.</span></span>  
  
 <span data-ttu-id="b9085-106">Aşağıdaki tabloda, olayın oluşturulduğu anahtar sözcük ve olay düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b9085-106">The following table shows the keyword under which the event is raised, and the level of the event.</span></span> <span data-ttu-id="b9085-107">(Daha fazla bilgi için bkz. [CLR ETW anahtar sözcükleri ve düzeyleri](clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="b9085-107">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="b9085-108">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="b9085-108">Keyword for raising the event</span></span>|<span data-ttu-id="b9085-109">Düzey</span><span class="sxs-lookup"><span data-stu-id="b9085-109">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="b9085-110">`ExceptionKeyword` 0x8000</span><span class="sxs-lookup"><span data-stu-id="b9085-110">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="b9085-111">Uyarı (2)</span><span class="sxs-lookup"><span data-stu-id="b9085-111">Warning (2)</span></span>|  
  
 <span data-ttu-id="b9085-112">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b9085-112">The following table shows event information.</span></span>  
  
|<span data-ttu-id="b9085-113">Olay</span><span class="sxs-lookup"><span data-stu-id="b9085-113">Event</span></span>|<span data-ttu-id="b9085-114">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="b9085-114">Event ID</span></span>|<span data-ttu-id="b9085-115">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="b9085-115">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|<span data-ttu-id="b9085-116">80</span><span class="sxs-lookup"><span data-stu-id="b9085-116">80</span></span>|<span data-ttu-id="b9085-117">Yönetilen bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b9085-117">A managed exception is thrown.</span></span>|  
  
 <span data-ttu-id="b9085-118">Aşağıdaki tabloda olay verileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b9085-118">The following table shows event data.</span></span>  
  
|<span data-ttu-id="b9085-119">Alan adı</span><span class="sxs-lookup"><span data-stu-id="b9085-119">Field name</span></span>|<span data-ttu-id="b9085-120">Veri türü</span><span class="sxs-lookup"><span data-stu-id="b9085-120">Data type</span></span>|<span data-ttu-id="b9085-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b9085-121">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="b9085-122">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="b9085-122">Exception Type</span></span>|<span data-ttu-id="b9085-123">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="b9085-123">win:UnicodeString</span></span>|<span data-ttu-id="b9085-124">Özel durumun türü; Örneğin, `System.NullReferenceException` .</span><span class="sxs-lookup"><span data-stu-id="b9085-124">Type of the exception; for example, `System.NullReferenceException`.</span></span>|  
|<span data-ttu-id="b9085-125">Özel durum Iletisi</span><span class="sxs-lookup"><span data-stu-id="b9085-125">Exception Message</span></span>|<span data-ttu-id="b9085-126">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="b9085-126">win:UnicodeString</span></span>|<span data-ttu-id="b9085-127">Gerçek özel durum iletisi.</span><span class="sxs-lookup"><span data-stu-id="b9085-127">Actual exception message.</span></span>|  
|<span data-ttu-id="b9085-128">EIPCodeThrow</span><span class="sxs-lookup"><span data-stu-id="b9085-128">EIPCodeThrow</span></span>|<span data-ttu-id="b9085-129">Win: Işaretçi</span><span class="sxs-lookup"><span data-stu-id="b9085-129">win:Pointer</span></span>|<span data-ttu-id="b9085-130">Özel durumun oluştuğu yönerge işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="b9085-130">Instruction pointer where exception occurred.</span></span>|  
|<span data-ttu-id="b9085-131">ExceptionHR</span><span class="sxs-lookup"><span data-stu-id="b9085-131">ExceptionHR</span></span>|<span data-ttu-id="b9085-132">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="b9085-132">win:UInt32</span></span>|<span data-ttu-id="b9085-133">Özel durum [HRESULT](/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).</span><span class="sxs-lookup"><span data-stu-id="b9085-133">Exception [HRESULT](/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).</span></span>|  
|<span data-ttu-id="b9085-134">ExceptionFlags</span><span class="sxs-lookup"><span data-stu-id="b9085-134">ExceptionFlags</span></span>|<span data-ttu-id="b9085-135">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="b9085-135">win:UInt16</span></span>|<span data-ttu-id="b9085-136">0x01: HasInnerException (Visual Basic belgelerinde [CLR ETW olaylarını](clr-etw-events.md) görün).</span><span class="sxs-lookup"><span data-stu-id="b9085-136">0x01: HasInnerException (see [CLR ETW Events](clr-etw-events.md) in the Visual Basic documentation).</span></span><br /><br /> <span data-ttu-id="b9085-137">0x02: ısnestedexception.</span><span class="sxs-lookup"><span data-stu-id="b9085-137">0x02: IsNestedException.</span></span><br /><br /> <span data-ttu-id="b9085-138">0x04: IsRethrownException.</span><span class="sxs-lookup"><span data-stu-id="b9085-138">0x04: IsRethrownException.</span></span><br /><br /> <span data-ttu-id="b9085-139">0x08: ıbozulan Tedstateexception (işlem durumunun bozuk olduğunu gösterir; bkz. [bozuk durum özel durumlarını işleme](/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).</span><span class="sxs-lookup"><span data-stu-id="b9085-139">0x08: IsCorruptedStateException (indicates that the process state is corrupt; see [Handling Corrupted State Exceptions](/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).</span></span><br /><br /> <span data-ttu-id="b9085-140">0x10: ısclscompliant (öğesinden türetilen özel durum <xref:System.Exception> CLS uyumludur; Aksi takdirde, CLS uyumlu değildir).</span><span class="sxs-lookup"><span data-stu-id="b9085-140">0x10: IsCLSCompliant (an exception that derives from <xref:System.Exception> is CLS-compliant; otherwise, it is not CLS-compliant).</span></span>|  
|<span data-ttu-id="b9085-141">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="b9085-141">ClrInstanceID</span></span>|<span data-ttu-id="b9085-142">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="b9085-142">win:UInt16</span></span>|<span data-ttu-id="b9085-143">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="b9085-143">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b9085-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b9085-144">See also</span></span>

- [<span data-ttu-id="b9085-145">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="b9085-145">CLR ETW Events</span></span>](clr-etw-events.md)
