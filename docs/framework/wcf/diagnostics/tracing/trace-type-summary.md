---
title: İzleme Türü Özeti
ms.date: 03/30/2017
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
ms.openlocfilehash: 8ed6dceb19caa52f928f285064c60337e3f15a87
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674835"
---
# <a name="trace-type-summary"></a><span data-ttu-id="2ae3d-102">İzleme Türü Özeti</span><span class="sxs-lookup"><span data-stu-id="2ae3d-102">Trace Type Summary</span></span>
<span data-ttu-id="2ae3d-103">[Kaynak Düzeyleri](xref:System.Diagnostics.SourceLevels) çeşitli izleme düzeyleri tanımlar: Kritik, Hata, Uyarı, Bilgi ve Verbose, yanı sıra izleme sınır ve etkinlik aktarım olayları çıktısını geçişbayrak, bir açıklama `ActivityTracing` sağlar.</span><span class="sxs-lookup"><span data-stu-id="2ae3d-103">[Source Levels](xref:System.Diagnostics.SourceLevels) defines various trace levels: Critical, Error, Warning, Information, and Verbose, as well as provides a description of the `ActivityTracing` flag, which toggles the output of trace boundary and activity transfer events.</span></span>  
  
 <span data-ttu-id="2ae3d-104">Ayrıca, 'den <xref:System.Diagnostics.TraceEventType> <xref:System.Diagnostics>çıkarılabilen izleme türleri için de gözden geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2ae3d-104">You can also review <xref:System.Diagnostics.TraceEventType> for the types of traces which can be emitted from <xref:System.Diagnostics>.</span></span>  
  
 <span data-ttu-id="2ae3d-105">Aşağıdaki tabloda en önemli olanları listeleyiş.</span><span class="sxs-lookup"><span data-stu-id="2ae3d-105">The following table lists the most important ones.</span></span>  
  
|<span data-ttu-id="2ae3d-106">İzleme Türü</span><span class="sxs-lookup"><span data-stu-id="2ae3d-106">Trace Type</span></span>|<span data-ttu-id="2ae3d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2ae3d-107">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="2ae3d-108">Kritik</span><span class="sxs-lookup"><span data-stu-id="2ae3d-108">Critical</span></span>|<span data-ttu-id="2ae3d-109">Önemli hata veya uygulama çökmesi.</span><span class="sxs-lookup"><span data-stu-id="2ae3d-109">Fatal error or application crash.</span></span>|  
|<span data-ttu-id="2ae3d-110">Hata</span><span class="sxs-lookup"><span data-stu-id="2ae3d-110">Error</span></span>|<span data-ttu-id="2ae3d-111">Kurtarılabilir hata.</span><span class="sxs-lookup"><span data-stu-id="2ae3d-111">Recoverable error.</span></span>|  
|<span data-ttu-id="2ae3d-112">Uyarı</span><span class="sxs-lookup"><span data-stu-id="2ae3d-112">Warning</span></span>|<span data-ttu-id="2ae3d-113">Bilgilendirme iletisi.</span><span class="sxs-lookup"><span data-stu-id="2ae3d-113">Informational message.</span></span>|  
|<span data-ttu-id="2ae3d-114">Bilgi</span><span class="sxs-lookup"><span data-stu-id="2ae3d-114">Information</span></span>|<span data-ttu-id="2ae3d-115">Kritik olmayan bir sorun.</span><span class="sxs-lookup"><span data-stu-id="2ae3d-115">Non-critical problem.</span></span>|  
|<span data-ttu-id="2ae3d-116">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="2ae3d-116">Verbose</span></span>|<span data-ttu-id="2ae3d-117">Hata ayıklama izi.</span><span class="sxs-lookup"><span data-stu-id="2ae3d-117">Debugging trace.</span></span>|  
|<span data-ttu-id="2ae3d-118">Başlangıç</span><span class="sxs-lookup"><span data-stu-id="2ae3d-118">Start</span></span>|<span data-ttu-id="2ae3d-119">Mantıksal bir işlem biriminin başlatılması.</span><span class="sxs-lookup"><span data-stu-id="2ae3d-119">Starting of a logical unit of processing.</span></span>|  
|<span data-ttu-id="2ae3d-120">Askıya Alma</span><span class="sxs-lookup"><span data-stu-id="2ae3d-120">Suspend</span></span>|<span data-ttu-id="2ae3d-121">Mantıksal bir işlem biriminin askıya alınması.</span><span class="sxs-lookup"><span data-stu-id="2ae3d-121">Suspension of a logical unit of processing.</span></span>|  
|<span data-ttu-id="2ae3d-122">Sürdür</span><span class="sxs-lookup"><span data-stu-id="2ae3d-122">Resume</span></span>|<span data-ttu-id="2ae3d-123">Mantıksal bir işlem biriminin devamı.</span><span class="sxs-lookup"><span data-stu-id="2ae3d-123">Resumption of a logical unit of processing.</span></span>|  
|<span data-ttu-id="2ae3d-124">Durdur</span><span class="sxs-lookup"><span data-stu-id="2ae3d-124">Stop</span></span>|<span data-ttu-id="2ae3d-125">Mantıksal bir işlem biriminin durdurulması.</span><span class="sxs-lookup"><span data-stu-id="2ae3d-125">Stopping of a logical unit of processing.</span></span>|  
|<span data-ttu-id="2ae3d-126">Aktarma</span><span class="sxs-lookup"><span data-stu-id="2ae3d-126">Transfer</span></span>|<span data-ttu-id="2ae3d-127">Korelasyon kimliğinin değiştirilmesi.</span><span class="sxs-lookup"><span data-stu-id="2ae3d-127">Changing of correlation identity.</span></span>|  
  
 <span data-ttu-id="2ae3d-128">Bir etkinlik yukarıdaki izleme türlerinin bir leşimi olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="2ae3d-128">An activity is defined as a combination of the trace types above.</span></span>  
  
 <span data-ttu-id="2ae3d-129">Aşağıda, yerel (izleme kaynağı) kapsamda ideal bir etkinliği tanımlayan normal bir ifade,</span><span class="sxs-lookup"><span data-stu-id="2ae3d-129">The following is a regular expression that defines an ideal activity in a local (trace source) scope,</span></span>  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 <span data-ttu-id="2ae3d-130">Bu, bir etkinliğin aşağıdaki koşulları karşılaması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="2ae3d-130">This means that an activity must satisfy the following conditions.</span></span>  
  
- <span data-ttu-id="2ae3d-131">Başlangıç ve Durdurma izlerine göre sırasıyla başlatmalı ve durdurmalı</span><span class="sxs-lookup"><span data-stu-id="2ae3d-131">It must start and stop respectively by a Start and Stop traces</span></span>  
  
- <span data-ttu-id="2ae3d-132">Askıya Alma veya Devam takibinden hemen önce bir Aktarım izleme olmalıdır</span><span class="sxs-lookup"><span data-stu-id="2ae3d-132">It must have a Transfer trace immediately preceding a Suspend or Resume trace</span></span>  
  
- <span data-ttu-id="2ae3d-133">Bu tür izler varsa Askıya Alma ve Devam İzleri arasında herhangi bir iz olmamalıdır</span><span class="sxs-lookup"><span data-stu-id="2ae3d-133">It must not have any traces between the Suspend and Resume traces if such traces exist</span></span>  
  
- <span data-ttu-id="2ae3d-134">Önceki koşullar gözlendiği sürece kritik/Hata/Uyarı/Bilgi/Verbose/Transfer izlerinin herhangi bir ve çok sayıda olabilir</span><span class="sxs-lookup"><span data-stu-id="2ae3d-134">It can have any and as many of critical/Error/Warning/Information/Verbose/Transfer traces as long as the previous conditions are observed</span></span>  
  
 <span data-ttu-id="2ae3d-135">Aşağıda, genel kapsamda ideal bir etkinliği tanımlayan düzenli bir ifade</span><span class="sxs-lookup"><span data-stu-id="2ae3d-135">The following is a regular expression that defines an ideal activity in the global scope,</span></span>  
  
`R+`  
  
 <span data-ttu-id="2ae3d-136">R yerel kapsamdabir etkinlik için düzenli ifade olmak.</span><span class="sxs-lookup"><span data-stu-id="2ae3d-136">with R being the regular expression for an activity in the local scope.</span></span> <span data-ttu-id="2ae3d-137">Bu, çevirir</span><span class="sxs-lookup"><span data-stu-id="2ae3d-137">This translates to,</span></span>  
  
`[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+`
