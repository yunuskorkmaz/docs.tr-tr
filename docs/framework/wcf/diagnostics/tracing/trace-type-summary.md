---
description: 'Daha fazla bilgi edinin: Izleme türü Özeti'
title: İzleme Türü Özeti
ms.date: 03/30/2017
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
ms.openlocfilehash: ebfe9de16766494a6aebe0a8d2501954855dc4df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803223"
---
# <a name="trace-type-summary"></a><span data-ttu-id="2611f-103">İzleme Türü Özeti</span><span class="sxs-lookup"><span data-stu-id="2611f-103">Trace Type Summary</span></span>

<span data-ttu-id="2611f-104">[Kaynak düzeyleri](xref:System.Diagnostics.SourceLevels) çeşitli izleme düzeylerini tanımlar: kritik, hata, uyarı, bilgi ve ayrıntılı, Ayrıca, `ActivityTracing` izleme sınırının ve etkinlik aktarım olaylarının çıktısına geçiş yapmak için bayrağın bir açıklamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="2611f-104">[Source Levels](xref:System.Diagnostics.SourceLevels) defines various trace levels: Critical, Error, Warning, Information, and Verbose, as well as provides a description of the `ActivityTracing` flag, which toggles the output of trace boundary and activity transfer events.</span></span>  
  
 <span data-ttu-id="2611f-105">Ayrıca, ' <xref:System.Diagnostics.TraceEventType> den yayınlanbilen izleme türlerini gözden geçirebilirsiniz <xref:System.Diagnostics> .</span><span class="sxs-lookup"><span data-stu-id="2611f-105">You can also review <xref:System.Diagnostics.TraceEventType> for the types of traces which can be emitted from <xref:System.Diagnostics>.</span></span>  
  
 <span data-ttu-id="2611f-106">Aşağıdaki tabloda en önemli olanlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="2611f-106">The following table lists the most important ones.</span></span>  
  
|<span data-ttu-id="2611f-107">İzleme türü</span><span class="sxs-lookup"><span data-stu-id="2611f-107">Trace Type</span></span>|<span data-ttu-id="2611f-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2611f-108">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="2611f-109">Kritik</span><span class="sxs-lookup"><span data-stu-id="2611f-109">Critical</span></span>|<span data-ttu-id="2611f-110">Önemli hata veya uygulama kilitlenmesi.</span><span class="sxs-lookup"><span data-stu-id="2611f-110">Fatal error or application crash.</span></span>|  
|<span data-ttu-id="2611f-111">Hata</span><span class="sxs-lookup"><span data-stu-id="2611f-111">Error</span></span>|<span data-ttu-id="2611f-112">Kurtarılabilir hata.</span><span class="sxs-lookup"><span data-stu-id="2611f-112">Recoverable error.</span></span>|  
|<span data-ttu-id="2611f-113">Uyarı</span><span class="sxs-lookup"><span data-stu-id="2611f-113">Warning</span></span>|<span data-ttu-id="2611f-114">Bilgi iletisi.</span><span class="sxs-lookup"><span data-stu-id="2611f-114">Informational message.</span></span>|  
|<span data-ttu-id="2611f-115">Bilgi</span><span class="sxs-lookup"><span data-stu-id="2611f-115">Information</span></span>|<span data-ttu-id="2611f-116">Kritik olmayan sorun.</span><span class="sxs-lookup"><span data-stu-id="2611f-116">Non-critical problem.</span></span>|  
|<span data-ttu-id="2611f-117">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="2611f-117">Verbose</span></span>|<span data-ttu-id="2611f-118">Hata ayıklama izleme.</span><span class="sxs-lookup"><span data-stu-id="2611f-118">Debugging trace.</span></span>|  
|<span data-ttu-id="2611f-119">Başlangıç</span><span class="sxs-lookup"><span data-stu-id="2611f-119">Start</span></span>|<span data-ttu-id="2611f-120">Mantıksal bir işlem birimi başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="2611f-120">Starting of a logical unit of processing.</span></span>|  
|<span data-ttu-id="2611f-121">Askıya Alma</span><span class="sxs-lookup"><span data-stu-id="2611f-121">Suspend</span></span>|<span data-ttu-id="2611f-122">Mantıksal bir işlem birimini askıya alma.</span><span class="sxs-lookup"><span data-stu-id="2611f-122">Suspension of a logical unit of processing.</span></span>|  
|<span data-ttu-id="2611f-123">Sürdür</span><span class="sxs-lookup"><span data-stu-id="2611f-123">Resume</span></span>|<span data-ttu-id="2611f-124">Sürdürme mantıksal bir işlem birimi.</span><span class="sxs-lookup"><span data-stu-id="2611f-124">Resumption of a logical unit of processing.</span></span>|  
|<span data-ttu-id="2611f-125">Durdur</span><span class="sxs-lookup"><span data-stu-id="2611f-125">Stop</span></span>|<span data-ttu-id="2611f-126">Mantıksal bir işleme birimi durduruluyor.</span><span class="sxs-lookup"><span data-stu-id="2611f-126">Stopping of a logical unit of processing.</span></span>|  
|<span data-ttu-id="2611f-127">Aktarma</span><span class="sxs-lookup"><span data-stu-id="2611f-127">Transfer</span></span>|<span data-ttu-id="2611f-128">Bağıntı kimliğini değiştirme.</span><span class="sxs-lookup"><span data-stu-id="2611f-128">Changing of correlation identity.</span></span>|  
  
 <span data-ttu-id="2611f-129">Etkinlik, yukarıdaki izleme türlerinin birleşimi olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="2611f-129">An activity is defined as a combination of the trace types above.</span></span>  
  
 <span data-ttu-id="2611f-130">Aşağıda, yerel (izleme kaynağı) kapsamında ideal bir etkinliği tanımlayan bir normal ifade verilmiştir,</span><span class="sxs-lookup"><span data-stu-id="2611f-130">The following is a regular expression that defines an ideal activity in a local (trace source) scope,</span></span>  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 <span data-ttu-id="2611f-131">Bu, bir etkinliğin aşağıdaki koşulları karşılaması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="2611f-131">This means that an activity must satisfy the following conditions.</span></span>  
  
- <span data-ttu-id="2611f-132">Başlatma ve durdurma izlemelerinin sırasıyla başlaması ve durdurulması gerekir</span><span class="sxs-lookup"><span data-stu-id="2611f-132">It must start and stop respectively by a Start and Stop traces</span></span>  
  
- <span data-ttu-id="2611f-133">Bir askıya alma veya yeniden başlatma izlemesinin hemen öncesinde bir aktarım izlemesi olmalıdır</span><span class="sxs-lookup"><span data-stu-id="2611f-133">It must have a Transfer trace immediately preceding a Suspend or Resume trace</span></span>  
  
- <span data-ttu-id="2611f-134">Bu tür izlemeler varsa askıya al ve Duraklat izlemeleri arasında izleme içermemelidir</span><span class="sxs-lookup"><span data-stu-id="2611f-134">It must not have any traces between the Suspend and Resume traces if such traces exist</span></span>  
  
- <span data-ttu-id="2611f-135">Önceki koşullar gözlemlendiği sürece bir veya daha fazla kritik/hata/uyarı/bilgi/ayrıntılı/aktarım izlerinden oluşabilir</span><span class="sxs-lookup"><span data-stu-id="2611f-135">It can have any and as many of critical/Error/Warning/Information/Verbose/Transfer traces as long as the previous conditions are observed</span></span>  
  
 <span data-ttu-id="2611f-136">Aşağıda genel kapsamda ideal bir etkinliği tanımlayan bir normal ifade verilmiştir,</span><span class="sxs-lookup"><span data-stu-id="2611f-136">The following is a regular expression that defines an ideal activity in the global scope,</span></span>  
  
`R+`  
  
 <span data-ttu-id="2611f-137">yerel kapsamdaki bir etkinliğin normal ifadesi olan R.</span><span class="sxs-lookup"><span data-stu-id="2611f-137">with R being the regular expression for an activity in the local scope.</span></span> <span data-ttu-id="2611f-138">Bu,</span><span class="sxs-lookup"><span data-stu-id="2611f-138">This translates to,</span></span>  
  
`[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+`
