---
title: İzleme Türü Özeti
ms.date: 03/30/2017
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
ms.openlocfilehash: 44446b58510e58758934a5eb964efc8643854879
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647183"
---
# <a name="trace-type-summary"></a><span data-ttu-id="3388f-102">İzleme Türü Özeti</span><span class="sxs-lookup"><span data-stu-id="3388f-102">Trace Type Summary</span></span>
<span data-ttu-id="3388f-103">[Kaynak düzeylerini](https://go.microsoft.com/fwlink/?LinkID=94943) çeşitli izleme düzeylerini tanımlar: Kritik, hata, uyarı, bilgi ve ayrıntı, sağlar açıklamasını `ActivityTracing` çıktısını değiştirir bayrak sınır ve etkinlik aktarım olayları izleme.</span><span class="sxs-lookup"><span data-stu-id="3388f-103">[Source Levels](https://go.microsoft.com/fwlink/?LinkID=94943) defines various trace levels: Critical, Error, Warning, Information, and Verbose, as well as provides description of the `ActivityTracing` flag, which toggles the output of trace boundary and activity transfer events.</span></span>  
  
 <span data-ttu-id="3388f-104">Ayrıca inceleyebilirsiniz [TraceEventType](https://go.microsoft.com/fwlink/?LinkId=95169) , gelen yayılan izlemeleri türde <xref:System.Diagnostics>.</span><span class="sxs-lookup"><span data-stu-id="3388f-104">You can also review [TraceEventType](https://go.microsoft.com/fwlink/?LinkId=95169) for the types of traces which can be emitted from <xref:System.Diagnostics>.</span></span>  
  
 <span data-ttu-id="3388f-105">Aşağıdaki tabloda, en önemli olanları listeler.</span><span class="sxs-lookup"><span data-stu-id="3388f-105">The following table lists the most important ones.</span></span>  
  
|<span data-ttu-id="3388f-106">İzleme türü</span><span class="sxs-lookup"><span data-stu-id="3388f-106">Trace Type</span></span>|<span data-ttu-id="3388f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3388f-107">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="3388f-108">Kritik</span><span class="sxs-lookup"><span data-stu-id="3388f-108">Critical</span></span>|<span data-ttu-id="3388f-109">Önemli hata veya uygulama kilitlenme.</span><span class="sxs-lookup"><span data-stu-id="3388f-109">Fatal error or application crash.</span></span>|  
|<span data-ttu-id="3388f-110">Hata</span><span class="sxs-lookup"><span data-stu-id="3388f-110">Error</span></span>|<span data-ttu-id="3388f-111">Kurtarılabilir bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="3388f-111">Recoverable error.</span></span>|  
|<span data-ttu-id="3388f-112">Uyarı</span><span class="sxs-lookup"><span data-stu-id="3388f-112">Warning</span></span>|<span data-ttu-id="3388f-113">Bilgi iletisi.</span><span class="sxs-lookup"><span data-stu-id="3388f-113">Informational message.</span></span>|  
|<span data-ttu-id="3388f-114">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="3388f-114">Information</span></span>|<span data-ttu-id="3388f-115">Kritik olmayan sorun oluştu.</span><span class="sxs-lookup"><span data-stu-id="3388f-115">Non-critical problem.</span></span>|  
|<span data-ttu-id="3388f-116">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="3388f-116">Verbose</span></span>|<span data-ttu-id="3388f-117">İzleme hata ayıklama.</span><span class="sxs-lookup"><span data-stu-id="3388f-117">Debugging trace.</span></span>|  
|<span data-ttu-id="3388f-118">Başlat</span><span class="sxs-lookup"><span data-stu-id="3388f-118">Start</span></span>|<span data-ttu-id="3388f-119">Mantıksal birimi işleme başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="3388f-119">Starting of a logical unit of processing.</span></span>|  
|<span data-ttu-id="3388f-120">Askıya alma</span><span class="sxs-lookup"><span data-stu-id="3388f-120">Suspend</span></span>|<span data-ttu-id="3388f-121">İşleme bir mantıksal birimin askıya alma.</span><span class="sxs-lookup"><span data-stu-id="3388f-121">Suspension of a logical unit of processing.</span></span>|  
|<span data-ttu-id="3388f-122">Devam etme</span><span class="sxs-lookup"><span data-stu-id="3388f-122">Resume</span></span>|<span data-ttu-id="3388f-123">İşleme bir mantıksal birim sürdürme.</span><span class="sxs-lookup"><span data-stu-id="3388f-123">Resumption of a logical unit of processing.</span></span>|  
|<span data-ttu-id="3388f-124">Durdur</span><span class="sxs-lookup"><span data-stu-id="3388f-124">Stop</span></span>|<span data-ttu-id="3388f-125">İşleme bir mantıksal birim durduruluyor.</span><span class="sxs-lookup"><span data-stu-id="3388f-125">Stopping of a logical unit of processing.</span></span>|  
|<span data-ttu-id="3388f-126">Aktarma</span><span class="sxs-lookup"><span data-stu-id="3388f-126">Transfer</span></span>|<span data-ttu-id="3388f-127">Bağıntı kimliği değiştiriliyor.</span><span class="sxs-lookup"><span data-stu-id="3388f-127">Changing of correlation identity.</span></span>|  
  
 <span data-ttu-id="3388f-128">Bir etkinlik, yukarıdaki izleme türleri bir birleşimi olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="3388f-128">An activity is defined as a combination of the trace types above.</span></span>  
  
 <span data-ttu-id="3388f-129">Bir yerel (izleme kaynak) kapsamındaki ideal aktiviteye tanımlayan bir normal ifade verilmiştir,</span><span class="sxs-lookup"><span data-stu-id="3388f-129">The following is a regular expression that defines an ideal activity in a local (trace source) scope,</span></span>  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 <span data-ttu-id="3388f-130">Başka bir deyişle, etkinlik aşağıdaki koşulları karşılaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3388f-130">This means that an activity must satisfy the following conditions.</span></span>  
  
- <span data-ttu-id="3388f-131">Başlamalı ve bir başlatma ve durdurma izlemeleri tarafından durdurur</span><span class="sxs-lookup"><span data-stu-id="3388f-131">It must start and stop respectively by a Start and Stop traces</span></span>  
  
- <span data-ttu-id="3388f-132">Hemen bir askıya alma veya sürdürme izleme önceki bir aktarım izleme olmalıdır</span><span class="sxs-lookup"><span data-stu-id="3388f-132">It must have a Transfer trace immediately preceding a Suspend or Resume trace</span></span>  
  
- <span data-ttu-id="3388f-133">Bu tür izleme varsa askıya alma ve sürdürme izlemeler arasında tüm izlemeleri olmamalıdır</span><span class="sxs-lookup"><span data-stu-id="3388f-133">It must not have any traces between the Suspend and Resume traces if such traces exist</span></span>  
  
- <span data-ttu-id="3388f-134">Önceki koşullar gözlemlenen sürece her ve Kritik/hata/uyarı/bilgi/Verbose/aktarım izleme sayıda olabilir</span><span class="sxs-lookup"><span data-stu-id="3388f-134">It can have any and as many of critical/Error/Warning/Information/Verbose/Transfer traces as long as the previous conditions are observed</span></span>  
  
 <span data-ttu-id="3388f-135">Aşağıdaki genel kapsamda ideal aktiviteye tanımlayan bir düzenli ifadedir,</span><span class="sxs-lookup"><span data-stu-id="3388f-135">The following is a regular expression that defines an ideal activity in the global scope,</span></span>  
  
```  
R+   
```  
  
 <span data-ttu-id="3388f-136">R ile yerel kapsama bir etkinlik için normal ifade edilen.</span><span class="sxs-lookup"><span data-stu-id="3388f-136">with R being the regular expression for an activity in the local scope.</span></span> <span data-ttu-id="3388f-137">Bu şekilde dönüşür,</span><span class="sxs-lookup"><span data-stu-id="3388f-137">This translates to,</span></span>  
  
```  
[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+  
```
