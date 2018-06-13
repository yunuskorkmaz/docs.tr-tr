---
title: Özel Durum Thrown_V1 ETW Olayı
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dafa5846f779276ab81e8e30e7c7a50b9fbff853
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33393861"
---
# <a name="exception-thrownv1-etw-event"></a><span data-ttu-id="a2e6b-102">Özel Durum Thrown_V1 ETW Olayı</span><span class="sxs-lookup"><span data-stu-id="a2e6b-102">Exception Thrown_V1 ETW Event</span></span>
<span data-ttu-id="a2e6b-103">Bu olay, oluşturulan özel durumlar hakkında bilgi yakalar.</span><span class="sxs-lookup"><span data-stu-id="a2e6b-103">This event captures information about the exceptions that are thrown.</span></span>  
  
 <span data-ttu-id="a2e6b-104">Aşağıdaki tabloda, altında olay tetiklenir anahtar sözcüğü ve olay düzeyini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a2e6b-104">The following table shows the keyword under which the event is raised, and the level of the event.</span></span> <span data-ttu-id="a2e6b-105">(Daha fazla bilgi için bkz: [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="a2e6b-105">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="a2e6b-106">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="a2e6b-106">Keyword for raising the event</span></span>|<span data-ttu-id="a2e6b-107">Düzey</span><span class="sxs-lookup"><span data-stu-id="a2e6b-107">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="a2e6b-108">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="a2e6b-108">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="a2e6b-109">Uyarı (2)</span><span class="sxs-lookup"><span data-stu-id="a2e6b-109">Warning (2)</span></span>|  
  
 <span data-ttu-id="a2e6b-110">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a2e6b-110">The following table shows event information.</span></span>  
  
|<span data-ttu-id="a2e6b-111">Olay</span><span class="sxs-lookup"><span data-stu-id="a2e6b-111">Event</span></span>|<span data-ttu-id="a2e6b-112">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="a2e6b-112">Event ID</span></span>|<span data-ttu-id="a2e6b-113">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="a2e6b-113">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|<span data-ttu-id="a2e6b-114">80</span><span class="sxs-lookup"><span data-stu-id="a2e6b-114">80</span></span>|<span data-ttu-id="a2e6b-115">Yönetilen bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="a2e6b-115">A managed exception is thrown.</span></span>|  
  
 <span data-ttu-id="a2e6b-116">Aşağıdaki tabloda olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a2e6b-116">The following table shows event data.</span></span>  
  
|<span data-ttu-id="a2e6b-117">Alan adı</span><span class="sxs-lookup"><span data-stu-id="a2e6b-117">Field name</span></span>|<span data-ttu-id="a2e6b-118">Veri türü</span><span class="sxs-lookup"><span data-stu-id="a2e6b-118">Data type</span></span>|<span data-ttu-id="a2e6b-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a2e6b-119">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="a2e6b-120">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="a2e6b-120">Exception Type</span></span>|<span data-ttu-id="a2e6b-121">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="a2e6b-121">win:UnicodeString</span></span>|<span data-ttu-id="a2e6b-122">Özel durum türünü; Örneğin, `System.NullReferenceException`.</span><span class="sxs-lookup"><span data-stu-id="a2e6b-122">Type of the exception; for example, `System.NullReferenceException`.</span></span>|  
|<span data-ttu-id="a2e6b-123">Özel durum iletisi</span><span class="sxs-lookup"><span data-stu-id="a2e6b-123">Exception Message</span></span>|<span data-ttu-id="a2e6b-124">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="a2e6b-124">win:UnicodeString</span></span>|<span data-ttu-id="a2e6b-125">Gerçek özel durum iletisi.</span><span class="sxs-lookup"><span data-stu-id="a2e6b-125">Actual exception message.</span></span>|  
|<span data-ttu-id="a2e6b-126">EIPCodeThrow</span><span class="sxs-lookup"><span data-stu-id="a2e6b-126">EIPCodeThrow</span></span>|<span data-ttu-id="a2e6b-127">Win: işaretçi</span><span class="sxs-lookup"><span data-stu-id="a2e6b-127">win:Pointer</span></span>|<span data-ttu-id="a2e6b-128">Yönerge işaretçisi burada özel durum oluştu.</span><span class="sxs-lookup"><span data-stu-id="a2e6b-128">Instruction pointer where exception occurred.</span></span>|  
|<span data-ttu-id="a2e6b-129">ExceptionHR</span><span class="sxs-lookup"><span data-stu-id="a2e6b-129">ExceptionHR</span></span>|<span data-ttu-id="a2e6b-130">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="a2e6b-130">win:UInt32</span></span>|<span data-ttu-id="a2e6b-131">Özel durum [HRESULT](http://go.microsoft.com/fwlink/?LinkId=179679).</span><span class="sxs-lookup"><span data-stu-id="a2e6b-131">Exception [HRESULT](http://go.microsoft.com/fwlink/?LinkId=179679).</span></span>|  
|<span data-ttu-id="a2e6b-132">ExceptionFlags</span><span class="sxs-lookup"><span data-stu-id="a2e6b-132">ExceptionFlags</span></span>|<span data-ttu-id="a2e6b-133">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="a2e6b-133">win:UInt16</span></span>|<span data-ttu-id="a2e6b-134">0x01: HasInnerException (bkz [CLR ETW olayları](../../../docs/framework/performance/clr-etw-events.md) Visual Basic belgelerinde).</span><span class="sxs-lookup"><span data-stu-id="a2e6b-134">0x01: HasInnerException (see [CLR ETW Events](../../../docs/framework/performance/clr-etw-events.md) in the Visual Basic documentation).</span></span><br /><br /> <span data-ttu-id="a2e6b-135">0x02: IsNestedException.</span><span class="sxs-lookup"><span data-stu-id="a2e6b-135">0x02: IsNestedException.</span></span><br /><br /> <span data-ttu-id="a2e6b-136">0x04: IsRethrownException.</span><span class="sxs-lookup"><span data-stu-id="a2e6b-136">0x04: IsRethrownException.</span></span><br /><br /> <span data-ttu-id="a2e6b-137">0x08: IsCorruptedStateException (işlem durumu bozuk olduğunu gösteriyor; bkz [işleme bozuk durumu özel durumları](http://go.microsoft.com/fwlink/?LinkId=179681) MSDN'de).</span><span class="sxs-lookup"><span data-stu-id="a2e6b-137">0x08: IsCorruptedStateException (indicates that the process state is corrupt; see [Handling Corrupted State Exceptions](http://go.microsoft.com/fwlink/?LinkId=179681) on MSDN).</span></span><br /><br /> <span data-ttu-id="a2e6b-138">0x10: IsCLSCompliant (türeyen bir özel durum <xref:System.Exception> CLS uyumlu; Aksi takdirde, CLS uyumlu değil).</span><span class="sxs-lookup"><span data-stu-id="a2e6b-138">0x10: IsCLSCompliant (an exception that derives from <xref:System.Exception> is CLS-compliant; otherwise, it is not CLS-compliant).</span></span>|  
|<span data-ttu-id="a2e6b-139">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="a2e6b-139">ClrInstanceID</span></span>|<span data-ttu-id="a2e6b-140">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="a2e6b-140">win:UInt16</span></span>|<span data-ttu-id="a2e6b-141">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="a2e6b-141">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a2e6b-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a2e6b-142">See Also</span></span>  
 [<span data-ttu-id="a2e6b-143">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="a2e6b-143">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
