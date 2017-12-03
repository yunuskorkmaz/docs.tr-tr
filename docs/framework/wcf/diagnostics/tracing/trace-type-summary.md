---
title: "İzleme Türü Özeti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c1570832e5f179b6d2685ad33fad743c9530bb16
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="trace-type-summary"></a><span data-ttu-id="b840c-102">İzleme Türü Özeti</span><span class="sxs-lookup"><span data-stu-id="b840c-102">Trace Type Summary</span></span>
<span data-ttu-id="b840c-103">[Kaynak düzeyleri](http://go.microsoft.com/fwlink/?LinkID=94943) çeşitli izleme düzeyleri tanımlar: Kritik hata, uyarı, bilgi ve ayrıntılı, sağlar açıklaması `ActivityTracing` çıktısını değiştirir bayrağı sınır ve etkinlik aktarım olayları izleme.</span><span class="sxs-lookup"><span data-stu-id="b840c-103">[Source Levels](http://go.microsoft.com/fwlink/?LinkID=94943) defines various trace levels: Critical, Error, Warning, Information, and Verbose, as well as provides description of the `ActivityTracing` flag, which toggles the output of trace boundary and activity transfer events.</span></span>  
  
 <span data-ttu-id="b840c-104">Ayrıca gözden geçirebilirsiniz [TraceEventType](http://go.microsoft.com/fwlink/?LinkId=95169) gelen yayılan izlerini türleri için <xref:System.Diagnostics>.</span><span class="sxs-lookup"><span data-stu-id="b840c-104">You can also review [TraceEventType](http://go.microsoft.com/fwlink/?LinkId=95169) for the types of traces which can be emitted from <xref:System.Diagnostics>.</span></span>  
  
 <span data-ttu-id="b840c-105">Aşağıdaki tabloda en önemlileri listeler.</span><span class="sxs-lookup"><span data-stu-id="b840c-105">The following table lists the most important ones.</span></span>  
  
|<span data-ttu-id="b840c-106">İzleme türü</span><span class="sxs-lookup"><span data-stu-id="b840c-106">Trace Type</span></span>|<span data-ttu-id="b840c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b840c-107">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="b840c-108">Kritik</span><span class="sxs-lookup"><span data-stu-id="b840c-108">Critical</span></span>|<span data-ttu-id="b840c-109">Önemli hata veya uygulama kilitlenme.</span><span class="sxs-lookup"><span data-stu-id="b840c-109">Fatal error or application crash.</span></span>|  
|<span data-ttu-id="b840c-110">Hata</span><span class="sxs-lookup"><span data-stu-id="b840c-110">Error</span></span>|<span data-ttu-id="b840c-111">Kurtarılamaz bir hata.</span><span class="sxs-lookup"><span data-stu-id="b840c-111">Recoverable error.</span></span>|  
|<span data-ttu-id="b840c-112">Uyarı</span><span class="sxs-lookup"><span data-stu-id="b840c-112">Warning</span></span>|<span data-ttu-id="b840c-113">Bilgi iletisi.</span><span class="sxs-lookup"><span data-stu-id="b840c-113">Informational message.</span></span>|  
|<span data-ttu-id="b840c-114">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="b840c-114">Information</span></span>|<span data-ttu-id="b840c-115">Kritik olmayan sorun.</span><span class="sxs-lookup"><span data-stu-id="b840c-115">Non-critical problem.</span></span>|  
|<span data-ttu-id="b840c-116">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="b840c-116">Verbose</span></span>|<span data-ttu-id="b840c-117">Hata ayıklama izleme.</span><span class="sxs-lookup"><span data-stu-id="b840c-117">Debugging trace.</span></span>|  
|<span data-ttu-id="b840c-118">Başlat</span><span class="sxs-lookup"><span data-stu-id="b840c-118">Start</span></span>|<span data-ttu-id="b840c-119">İşlem bir mantıksal birim başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="b840c-119">Starting of a logical unit of processing.</span></span>|  
|<span data-ttu-id="b840c-120">Askıya alma</span><span class="sxs-lookup"><span data-stu-id="b840c-120">Suspend</span></span>|<span data-ttu-id="b840c-121">İşleme bir mantıksal birim ertelenmesi.</span><span class="sxs-lookup"><span data-stu-id="b840c-121">Suspension of a logical unit of processing.</span></span>|  
|<span data-ttu-id="b840c-122">Devam etme</span><span class="sxs-lookup"><span data-stu-id="b840c-122">Resume</span></span>|<span data-ttu-id="b840c-123">İşleme bir mantıksal birim sürdürme.</span><span class="sxs-lookup"><span data-stu-id="b840c-123">Resumption of a logical unit of processing.</span></span>|  
|<span data-ttu-id="b840c-124">Durdur</span><span class="sxs-lookup"><span data-stu-id="b840c-124">Stop</span></span>|<span data-ttu-id="b840c-125">İşleme bir mantıksal birim durduruluyor.</span><span class="sxs-lookup"><span data-stu-id="b840c-125">Stopping of a logical unit of processing.</span></span>|  
|<span data-ttu-id="b840c-126">Aktarma</span><span class="sxs-lookup"><span data-stu-id="b840c-126">Transfer</span></span>|<span data-ttu-id="b840c-127">Bağıntı kimliğini değiştirme.</span><span class="sxs-lookup"><span data-stu-id="b840c-127">Changing of correlation identity.</span></span>|  
  
 <span data-ttu-id="b840c-128">Bir etkinlik izleme türleri yukarıdaki bileşimi tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="b840c-128">An activity is defined as a combination of the trace types above.</span></span>  
  
 <span data-ttu-id="b840c-129">Yerel (izleme kaynak) kapsamda ideal bir etkinlik tanımlayan normal bir ifade değil,</span><span class="sxs-lookup"><span data-stu-id="b840c-129">The following is a regular expression that defines an ideal activity in a local (trace source) scope,</span></span>  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 <span data-ttu-id="b840c-130">Başka bir deyişle, bir etkinlik aşağıdaki koşulları karşılaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b840c-130">This means that an activity must satisfy the following conditions.</span></span>  
  
-   <span data-ttu-id="b840c-131">Başlamalı ve sırasıyla Başlat ve Durdur izlemeler tarafından Durdur</span><span class="sxs-lookup"><span data-stu-id="b840c-131">It must start and stop respectively by a Start and Stop traces</span></span>  
  
-   <span data-ttu-id="b840c-132">Askıya alma veya sürdürme izleme hemen önceki bir aktarım izleme olmalıdır</span><span class="sxs-lookup"><span data-stu-id="b840c-132">It must have a Transfer trace immediately preceding a Suspend or Resume trace</span></span>  
  
-   <span data-ttu-id="b840c-133">Böyle izlemeleri varsa askıya alma ve sürdürme izlemeleri arasındaki tüm izlemeleri olmamalıdır</span><span class="sxs-lookup"><span data-stu-id="b840c-133">It must not have any traces between the Suspend and Resume traces if such traces exist</span></span>  
  
-   <span data-ttu-id="b840c-134">Önceki koşullar gözlenen sürece herhangi ve birçok Kritik/hata/uyarı/bilgi/Verbose/aktarım izlemeleri olarak olabilir</span><span class="sxs-lookup"><span data-stu-id="b840c-134">It can have any and as many of critical/Error/Warning/Information/Verbose/Transfer traces as long as the previous conditions are observed</span></span>  
  
 <span data-ttu-id="b840c-135">Genel kapsamda ideal bir etkinlik tanımlayan normal bir ifade değil,</span><span class="sxs-lookup"><span data-stu-id="b840c-135">The following is a regular expression that defines an ideal activity in the global scope,</span></span>  
  
```  
R+   
```  
  
 <span data-ttu-id="b840c-136">yerel kapsam içinde bir etkinlik için normal ifade edilen R ile.</span><span class="sxs-lookup"><span data-stu-id="b840c-136">with R being the regular expression for an activity in the local scope.</span></span> <span data-ttu-id="b840c-137">Bu şekilde çevirir,</span><span class="sxs-lookup"><span data-stu-id="b840c-137">This translates to,</span></span>  
  
```  
[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+  
```
