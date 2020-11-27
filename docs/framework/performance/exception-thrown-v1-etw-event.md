---
title: Özel Durum Thrown_V1 ETW Olayı
description: ExceptionThrown_V1 ETW olayı hakkında ayrıntılı bilgileri görüntüleyin. Oluşturulan özel durumlar için alan adları, veri türleri ve açıklamalar gibi olay verileri verilir.
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
ms.openlocfilehash: c1ba994b291bd278a95e34beb0b02ed6581786e8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263483"
---
# <a name="exception-thrown_v1-etw-event"></a><span data-ttu-id="1ebd3-104">Özel Durum Thrown_V1 ETW Olayı</span><span class="sxs-lookup"><span data-stu-id="1ebd3-104">Exception Thrown_V1 ETW Event</span></span>

<span data-ttu-id="1ebd3-105">Bu olay, oluşturulan özel durumlarla ilgili bilgileri yakalar.</span><span class="sxs-lookup"><span data-stu-id="1ebd3-105">This event captures information about the exceptions that are thrown.</span></span>  
  
 <span data-ttu-id="1ebd3-106">Aşağıdaki tabloda, olayın oluşturulduğu anahtar sözcük ve olay düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1ebd3-106">The following table shows the keyword under which the event is raised, and the level of the event.</span></span> <span data-ttu-id="1ebd3-107">(Daha fazla bilgi için bkz. [CLR ETW anahtar sözcükleri ve düzeyleri](clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="1ebd3-107">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="1ebd3-108">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="1ebd3-108">Keyword for raising the event</span></span>|<span data-ttu-id="1ebd3-109">Düzey</span><span class="sxs-lookup"><span data-stu-id="1ebd3-109">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="1ebd3-110">`ExceptionKeyword` 0x8000</span><span class="sxs-lookup"><span data-stu-id="1ebd3-110">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="1ebd3-111">Uyarı (2)</span><span class="sxs-lookup"><span data-stu-id="1ebd3-111">Warning (2)</span></span>|  
  
 <span data-ttu-id="1ebd3-112">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1ebd3-112">The following table shows event information.</span></span>  
  
|<span data-ttu-id="1ebd3-113">Olay</span><span class="sxs-lookup"><span data-stu-id="1ebd3-113">Event</span></span>|<span data-ttu-id="1ebd3-114">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="1ebd3-114">Event ID</span></span>|<span data-ttu-id="1ebd3-115">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="1ebd3-115">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|<span data-ttu-id="1ebd3-116">80</span><span class="sxs-lookup"><span data-stu-id="1ebd3-116">80</span></span>|<span data-ttu-id="1ebd3-117">Yönetilen bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1ebd3-117">A managed exception is thrown.</span></span>|  
  
 <span data-ttu-id="1ebd3-118">Aşağıdaki tabloda olay verileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1ebd3-118">The following table shows event data.</span></span>  
  
|<span data-ttu-id="1ebd3-119">Alan adı</span><span class="sxs-lookup"><span data-stu-id="1ebd3-119">Field name</span></span>|<span data-ttu-id="1ebd3-120">Veri türü</span><span class="sxs-lookup"><span data-stu-id="1ebd3-120">Data type</span></span>|<span data-ttu-id="1ebd3-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1ebd3-121">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="1ebd3-122">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="1ebd3-122">Exception Type</span></span>|<span data-ttu-id="1ebd3-123">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="1ebd3-123">win:UnicodeString</span></span>|<span data-ttu-id="1ebd3-124">Özel durumun türü; Örneğin, `System.NullReferenceException` .</span><span class="sxs-lookup"><span data-stu-id="1ebd3-124">Type of the exception; for example, `System.NullReferenceException`.</span></span>|  
|<span data-ttu-id="1ebd3-125">Özel durum Iletisi</span><span class="sxs-lookup"><span data-stu-id="1ebd3-125">Exception Message</span></span>|<span data-ttu-id="1ebd3-126">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="1ebd3-126">win:UnicodeString</span></span>|<span data-ttu-id="1ebd3-127">Gerçek özel durum iletisi.</span><span class="sxs-lookup"><span data-stu-id="1ebd3-127">Actual exception message.</span></span>|  
|<span data-ttu-id="1ebd3-128">EIPCodeThrow</span><span class="sxs-lookup"><span data-stu-id="1ebd3-128">EIPCodeThrow</span></span>|<span data-ttu-id="1ebd3-129">Win: Işaretçi</span><span class="sxs-lookup"><span data-stu-id="1ebd3-129">win:Pointer</span></span>|<span data-ttu-id="1ebd3-130">Özel durumun oluştuğu yönerge işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="1ebd3-130">Instruction pointer where exception occurred.</span></span>|  
|<span data-ttu-id="1ebd3-131">ExceptionHR</span><span class="sxs-lookup"><span data-stu-id="1ebd3-131">ExceptionHR</span></span>|<span data-ttu-id="1ebd3-132">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="1ebd3-132">win:UInt32</span></span>|<span data-ttu-id="1ebd3-133">Özel durum [HRESULT](/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).</span><span class="sxs-lookup"><span data-stu-id="1ebd3-133">Exception [HRESULT](/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).</span></span>|  
|<span data-ttu-id="1ebd3-134">ExceptionFlags</span><span class="sxs-lookup"><span data-stu-id="1ebd3-134">ExceptionFlags</span></span>|<span data-ttu-id="1ebd3-135">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="1ebd3-135">win:UInt16</span></span>|<span data-ttu-id="1ebd3-136">0x01: HasInnerException (Visual Basic belgelerinde [CLR ETW olaylarını](clr-etw-events.md) görün).</span><span class="sxs-lookup"><span data-stu-id="1ebd3-136">0x01: HasInnerException (see [CLR ETW Events](clr-etw-events.md) in the Visual Basic documentation).</span></span><br /><br /> <span data-ttu-id="1ebd3-137">0x02: ısnestedexception.</span><span class="sxs-lookup"><span data-stu-id="1ebd3-137">0x02: IsNestedException.</span></span><br /><br /> <span data-ttu-id="1ebd3-138">0x04: IsRethrownException.</span><span class="sxs-lookup"><span data-stu-id="1ebd3-138">0x04: IsRethrownException.</span></span><br /><br /> <span data-ttu-id="1ebd3-139">0x08: ıbozulan Tedstateexception (işlem durumunun bozuk olduğunu gösterir; bkz. [bozuk durum özel durumlarını işleme](/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).</span><span class="sxs-lookup"><span data-stu-id="1ebd3-139">0x08: IsCorruptedStateException (indicates that the process state is corrupt; see [Handling Corrupted State Exceptions](/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).</span></span><br /><br /> <span data-ttu-id="1ebd3-140">0x10: ısclscompliant (öğesinden türetilen özel durum <xref:System.Exception> CLS uyumludur; Aksi takdirde, CLS uyumlu değildir).</span><span class="sxs-lookup"><span data-stu-id="1ebd3-140">0x10: IsCLSCompliant (an exception that derives from <xref:System.Exception> is CLS-compliant; otherwise, it is not CLS-compliant).</span></span>|  
|<span data-ttu-id="1ebd3-141">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="1ebd3-141">ClrInstanceID</span></span>|<span data-ttu-id="1ebd3-142">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="1ebd3-142">win:UInt16</span></span>|<span data-ttu-id="1ebd3-143">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="1ebd3-143">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1ebd3-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ebd3-144">See also</span></span>

- [<span data-ttu-id="1ebd3-145">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="1ebd3-145">CLR ETW Events</span></span>](clr-etw-events.md)
