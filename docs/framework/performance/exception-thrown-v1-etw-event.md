---
title: "Özel Durum Thrown_V1 ETW Olayı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: dcf3390821c4210ced4c43dab5a94c93802d5f9d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="exception-thrownv1-etw-event"></a><span data-ttu-id="7c782-102">Özel Durum Thrown_V1 ETW Olayı</span><span class="sxs-lookup"><span data-stu-id="7c782-102">Exception Thrown_V1 ETW Event</span></span>
<span data-ttu-id="7c782-103">Bu olay, oluşturulan özel durumlar hakkında bilgi yakalar.</span><span class="sxs-lookup"><span data-stu-id="7c782-103">This event captures information about the exceptions that are thrown.</span></span>  
  
 <span data-ttu-id="7c782-104">Aşağıdaki tabloda, altında olay tetiklenir anahtar sözcüğü ve olay düzeyini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7c782-104">The following table shows the keyword under which the event is raised, and the level of the event.</span></span> <span data-ttu-id="7c782-105">(Daha fazla bilgi için bkz: [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="7c782-105">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="7c782-106">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="7c782-106">Keyword for raising the event</span></span>|<span data-ttu-id="7c782-107">Düzey</span><span class="sxs-lookup"><span data-stu-id="7c782-107">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="7c782-108">`ExceptionKeyword`(0x8000)</span><span class="sxs-lookup"><span data-stu-id="7c782-108">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="7c782-109">Uyarı (2)</span><span class="sxs-lookup"><span data-stu-id="7c782-109">Warning (2)</span></span>|  
  
 <span data-ttu-id="7c782-110">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7c782-110">The following table shows event information.</span></span>  
  
|<span data-ttu-id="7c782-111">Olay</span><span class="sxs-lookup"><span data-stu-id="7c782-111">Event</span></span>|<span data-ttu-id="7c782-112">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="7c782-112">Event ID</span></span>|<span data-ttu-id="7c782-113">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="7c782-113">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|<span data-ttu-id="7c782-114">80</span><span class="sxs-lookup"><span data-stu-id="7c782-114">80</span></span>|<span data-ttu-id="7c782-115">Yönetilen bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="7c782-115">A managed exception is thrown.</span></span>|  
  
 <span data-ttu-id="7c782-116">Aşağıdaki tabloda olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7c782-116">The following table shows event data.</span></span>  
  
|<span data-ttu-id="7c782-117">Alan adı</span><span class="sxs-lookup"><span data-stu-id="7c782-117">Field name</span></span>|<span data-ttu-id="7c782-118">Veri türü</span><span class="sxs-lookup"><span data-stu-id="7c782-118">Data type</span></span>|<span data-ttu-id="7c782-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7c782-119">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="7c782-120">Özel durum türü</span><span class="sxs-lookup"><span data-stu-id="7c782-120">Exception Type</span></span>|<span data-ttu-id="7c782-121">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="7c782-121">win:UnicodeString</span></span>|<span data-ttu-id="7c782-122">Özel durum türünü; Örneğin, `System.NullReferenceException`.</span><span class="sxs-lookup"><span data-stu-id="7c782-122">Type of the exception; for example, `System.NullReferenceException`.</span></span>|  
|<span data-ttu-id="7c782-123">Özel durum iletisi</span><span class="sxs-lookup"><span data-stu-id="7c782-123">Exception Message</span></span>|<span data-ttu-id="7c782-124">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="7c782-124">win:UnicodeString</span></span>|<span data-ttu-id="7c782-125">Gerçek özel durum iletisi.</span><span class="sxs-lookup"><span data-stu-id="7c782-125">Actual exception message.</span></span>|  
|<span data-ttu-id="7c782-126">EIPCodeThrow</span><span class="sxs-lookup"><span data-stu-id="7c782-126">EIPCodeThrow</span></span>|<span data-ttu-id="7c782-127">Win: işaretçi</span><span class="sxs-lookup"><span data-stu-id="7c782-127">win:Pointer</span></span>|<span data-ttu-id="7c782-128">Yönerge işaretçisi burada özel durum oluştu.</span><span class="sxs-lookup"><span data-stu-id="7c782-128">Instruction pointer where exception occurred.</span></span>|  
|<span data-ttu-id="7c782-129">ExceptionHR</span><span class="sxs-lookup"><span data-stu-id="7c782-129">ExceptionHR</span></span>|<span data-ttu-id="7c782-130">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="7c782-130">win:UInt32</span></span>|<span data-ttu-id="7c782-131">Özel durum [HRESULT](http://go.microsoft.com/fwlink/?LinkId=179679).</span><span class="sxs-lookup"><span data-stu-id="7c782-131">Exception [HRESULT](http://go.microsoft.com/fwlink/?LinkId=179679).</span></span>|  
|<span data-ttu-id="7c782-132">ExceptionFlags</span><span class="sxs-lookup"><span data-stu-id="7c782-132">ExceptionFlags</span></span>|<span data-ttu-id="7c782-133">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="7c782-133">win:UInt16</span></span>|<span data-ttu-id="7c782-134">0x01: HasInnerException (bkz [CLR ETW olayları](../../../docs/framework/performance/clr-etw-events.md) Visual Basic belgelerinde).</span><span class="sxs-lookup"><span data-stu-id="7c782-134">0x01: HasInnerException (see [CLR ETW Events](../../../docs/framework/performance/clr-etw-events.md) in the Visual Basic documentation).</span></span><br /><br /> <span data-ttu-id="7c782-135">0x02: IsNestedException.</span><span class="sxs-lookup"><span data-stu-id="7c782-135">0x02: IsNestedException.</span></span><br /><br /> <span data-ttu-id="7c782-136">0x04: IsRethrownException.</span><span class="sxs-lookup"><span data-stu-id="7c782-136">0x04: IsRethrownException.</span></span><br /><br /> <span data-ttu-id="7c782-137">0x08: IsCorruptedStateException (işlem durumu bozuk olduğunu gösteriyor; bkz [işleme bozuk durumu özel durumları](http://go.microsoft.com/fwlink/?LinkId=179681) MSDN'de).</span><span class="sxs-lookup"><span data-stu-id="7c782-137">0x08: IsCorruptedStateException (indicates that the process state is corrupt; see [Handling Corrupted State Exceptions](http://go.microsoft.com/fwlink/?LinkId=179681) on MSDN).</span></span><br /><br /> <span data-ttu-id="7c782-138">0x10: IsCLSCompliant (türeyen bir özel durum <xref:System.Exception> CLS uyumlu; Aksi takdirde, CLS uyumlu değil).</span><span class="sxs-lookup"><span data-stu-id="7c782-138">0x10: IsCLSCompliant (an exception that derives from <xref:System.Exception> is CLS-compliant; otherwise, it is not CLS-compliant).</span></span>|  
|<span data-ttu-id="7c782-139">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="7c782-139">ClrInstanceID</span></span>|<span data-ttu-id="7c782-140">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="7c782-140">win:UInt16</span></span>|<span data-ttu-id="7c782-141">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="7c782-141">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7c782-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7c782-142">See Also</span></span>  
 [<span data-ttu-id="7c782-143">CLR ETW olayları</span><span class="sxs-lookup"><span data-stu-id="7c782-143">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
