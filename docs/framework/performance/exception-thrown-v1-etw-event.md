---
title: Özel Durum Thrown_V1 ETW Olayı
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
ms.openlocfilehash: 80faf6e607755ee79c7ec17f2d7d3d5bdce822b7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716061"
---
# <a name="exception-thrown_v1-etw-event"></a><span data-ttu-id="6b6f3-102">Özel Durum Thrown_V1 ETW Olayı</span><span class="sxs-lookup"><span data-stu-id="6b6f3-102">Exception Thrown_V1 ETW Event</span></span>
<span data-ttu-id="6b6f3-103">Bu olay, oluşturulan özel durumlarla ilgili bilgileri yakalar.</span><span class="sxs-lookup"><span data-stu-id="6b6f3-103">This event captures information about the exceptions that are thrown.</span></span>  
  
 <span data-ttu-id="6b6f3-104">Aşağıdaki tabloda, olayın oluşturulduğu anahtar sözcük ve olay düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6b6f3-104">The following table shows the keyword under which the event is raised, and the level of the event.</span></span> <span data-ttu-id="6b6f3-105">(Daha fazla bilgi için bkz. [CLR ETW anahtar sözcükleri ve düzeyleri](clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="6b6f3-105">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="6b6f3-106">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="6b6f3-106">Keyword for raising the event</span></span>|<span data-ttu-id="6b6f3-107">Düzey</span><span class="sxs-lookup"><span data-stu-id="6b6f3-107">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="6b6f3-108">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="6b6f3-108">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="6b6f3-109">Uyarı (2)</span><span class="sxs-lookup"><span data-stu-id="6b6f3-109">Warning (2)</span></span>|  
  
 <span data-ttu-id="6b6f3-110">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6b6f3-110">The following table shows event information.</span></span>  
  
|<span data-ttu-id="6b6f3-111">Olay</span><span class="sxs-lookup"><span data-stu-id="6b6f3-111">Event</span></span>|<span data-ttu-id="6b6f3-112">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="6b6f3-112">Event ID</span></span>|<span data-ttu-id="6b6f3-113">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="6b6f3-113">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|<span data-ttu-id="6b6f3-114">80</span><span class="sxs-lookup"><span data-stu-id="6b6f3-114">80</span></span>|<span data-ttu-id="6b6f3-115">Yönetilen bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6b6f3-115">A managed exception is thrown.</span></span>|  
  
 <span data-ttu-id="6b6f3-116">Aşağıdaki tabloda olay verileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6b6f3-116">The following table shows event data.</span></span>  
  
|<span data-ttu-id="6b6f3-117">Alan adı</span><span class="sxs-lookup"><span data-stu-id="6b6f3-117">Field name</span></span>|<span data-ttu-id="6b6f3-118">Veri türü</span><span class="sxs-lookup"><span data-stu-id="6b6f3-118">Data type</span></span>|<span data-ttu-id="6b6f3-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6b6f3-119">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="6b6f3-120">Özel Durum Türü</span><span class="sxs-lookup"><span data-stu-id="6b6f3-120">Exception Type</span></span>|<span data-ttu-id="6b6f3-121">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="6b6f3-121">win:UnicodeString</span></span>|<span data-ttu-id="6b6f3-122">Özel durumun türü; Örneğin, `System.NullReferenceException`.</span><span class="sxs-lookup"><span data-stu-id="6b6f3-122">Type of the exception; for example, `System.NullReferenceException`.</span></span>|  
|<span data-ttu-id="6b6f3-123">Özel durum Iletisi</span><span class="sxs-lookup"><span data-stu-id="6b6f3-123">Exception Message</span></span>|<span data-ttu-id="6b6f3-124">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="6b6f3-124">win:UnicodeString</span></span>|<span data-ttu-id="6b6f3-125">Gerçek özel durum iletisi.</span><span class="sxs-lookup"><span data-stu-id="6b6f3-125">Actual exception message.</span></span>|  
|<span data-ttu-id="6b6f3-126">EIPCodeThrow</span><span class="sxs-lookup"><span data-stu-id="6b6f3-126">EIPCodeThrow</span></span>|<span data-ttu-id="6b6f3-127">Win: Işaretçi</span><span class="sxs-lookup"><span data-stu-id="6b6f3-127">win:Pointer</span></span>|<span data-ttu-id="6b6f3-128">Özel durumun oluştuğu yönerge işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="6b6f3-128">Instruction pointer where exception occurred.</span></span>|  
|<span data-ttu-id="6b6f3-129">ExceptionHR</span><span class="sxs-lookup"><span data-stu-id="6b6f3-129">ExceptionHR</span></span>|<span data-ttu-id="6b6f3-130">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="6b6f3-130">win:UInt32</span></span>|<span data-ttu-id="6b6f3-131">Özel durum [HRESULT](https://docs.microsoft.com/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).</span><span class="sxs-lookup"><span data-stu-id="6b6f3-131">Exception [HRESULT](https://docs.microsoft.com/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).</span></span>|  
|<span data-ttu-id="6b6f3-132">ExceptionFlags</span><span class="sxs-lookup"><span data-stu-id="6b6f3-132">ExceptionFlags</span></span>|<span data-ttu-id="6b6f3-133">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="6b6f3-133">win:UInt16</span></span>|<span data-ttu-id="6b6f3-134">0x01: HasInnerException (Visual Basic belgelerinde [CLR ETW olaylarını](clr-etw-events.md) görün).</span><span class="sxs-lookup"><span data-stu-id="6b6f3-134">0x01: HasInnerException (see [CLR ETW Events](clr-etw-events.md) in the Visual Basic documentation).</span></span><br /><br /> <span data-ttu-id="6b6f3-135">0x02: ısnestedexception.</span><span class="sxs-lookup"><span data-stu-id="6b6f3-135">0x02: IsNestedException.</span></span><br /><br /> <span data-ttu-id="6b6f3-136">0x04: IsRethrownException.</span><span class="sxs-lookup"><span data-stu-id="6b6f3-136">0x04: IsRethrownException.</span></span><br /><br /> <span data-ttu-id="6b6f3-137">0x08: ıbozulan Tedstateexception (işlem durumunun bozuk olduğunu gösterir; bkz. [bozuk durum özel durumlarını işleme](https://docs.microsoft.com/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).</span><span class="sxs-lookup"><span data-stu-id="6b6f3-137">0x08: IsCorruptedStateException (indicates that the process state is corrupt; see [Handling Corrupted State Exceptions](https://docs.microsoft.com/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).</span></span><br /><br /> <span data-ttu-id="6b6f3-138">0x10: ısclscompliant (<xref:System.Exception> türetilen bir özel durum CLS uyumludur; Aksi takdirde, CLS uyumlu değildir).</span><span class="sxs-lookup"><span data-stu-id="6b6f3-138">0x10: IsCLSCompliant (an exception that derives from <xref:System.Exception> is CLS-compliant; otherwise, it is not CLS-compliant).</span></span>|  
|<span data-ttu-id="6b6f3-139">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="6b6f3-139">ClrInstanceID</span></span>|<span data-ttu-id="6b6f3-140">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="6b6f3-140">win:UInt16</span></span>|<span data-ttu-id="6b6f3-141">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="6b6f3-141">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6b6f3-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b6f3-142">See also</span></span>

- [<span data-ttu-id="6b6f3-143">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="6b6f3-143">CLR ETW Events</span></span>](clr-etw-events.md)
