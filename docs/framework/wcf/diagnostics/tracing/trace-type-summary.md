---
title: İzleme Türü Özeti
ms.date: 03/30/2017
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
ms.openlocfilehash: e8d222d6f093f5db3bd620194bfde7edd4b998a8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96259251"
---
# <a name="trace-type-summary"></a><span data-ttu-id="ff271-102">İzleme Türü Özeti</span><span class="sxs-lookup"><span data-stu-id="ff271-102">Trace Type Summary</span></span>

<span data-ttu-id="ff271-103">[Kaynak düzeyleri](xref:System.Diagnostics.SourceLevels) çeşitli izleme düzeylerini tanımlar: kritik, hata, uyarı, bilgi ve ayrıntılı, Ayrıca, `ActivityTracing` izleme sınırının ve etkinlik aktarım olaylarının çıktısına geçiş yapmak için bayrağın bir açıklamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="ff271-103">[Source Levels](xref:System.Diagnostics.SourceLevels) defines various trace levels: Critical, Error, Warning, Information, and Verbose, as well as provides a description of the `ActivityTracing` flag, which toggles the output of trace boundary and activity transfer events.</span></span>  
  
 <span data-ttu-id="ff271-104">Ayrıca, ' <xref:System.Diagnostics.TraceEventType> den yayınlanbilen izleme türlerini gözden geçirebilirsiniz <xref:System.Diagnostics> .</span><span class="sxs-lookup"><span data-stu-id="ff271-104">You can also review <xref:System.Diagnostics.TraceEventType> for the types of traces which can be emitted from <xref:System.Diagnostics>.</span></span>  
  
 <span data-ttu-id="ff271-105">Aşağıdaki tabloda en önemli olanlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="ff271-105">The following table lists the most important ones.</span></span>  
  
|<span data-ttu-id="ff271-106">İzleme türü</span><span class="sxs-lookup"><span data-stu-id="ff271-106">Trace Type</span></span>|<span data-ttu-id="ff271-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ff271-107">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="ff271-108">Kritik</span><span class="sxs-lookup"><span data-stu-id="ff271-108">Critical</span></span>|<span data-ttu-id="ff271-109">Önemli hata veya uygulama kilitlenmesi.</span><span class="sxs-lookup"><span data-stu-id="ff271-109">Fatal error or application crash.</span></span>|  
|<span data-ttu-id="ff271-110">Hata</span><span class="sxs-lookup"><span data-stu-id="ff271-110">Error</span></span>|<span data-ttu-id="ff271-111">Kurtarılabilir hata.</span><span class="sxs-lookup"><span data-stu-id="ff271-111">Recoverable error.</span></span>|  
|<span data-ttu-id="ff271-112">Uyarı</span><span class="sxs-lookup"><span data-stu-id="ff271-112">Warning</span></span>|<span data-ttu-id="ff271-113">Bilgi iletisi.</span><span class="sxs-lookup"><span data-stu-id="ff271-113">Informational message.</span></span>|  
|<span data-ttu-id="ff271-114">Bilgi</span><span class="sxs-lookup"><span data-stu-id="ff271-114">Information</span></span>|<span data-ttu-id="ff271-115">Kritik olmayan sorun.</span><span class="sxs-lookup"><span data-stu-id="ff271-115">Non-critical problem.</span></span>|  
|<span data-ttu-id="ff271-116">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="ff271-116">Verbose</span></span>|<span data-ttu-id="ff271-117">Hata ayıklama izleme.</span><span class="sxs-lookup"><span data-stu-id="ff271-117">Debugging trace.</span></span>|  
|<span data-ttu-id="ff271-118">Başlangıç</span><span class="sxs-lookup"><span data-stu-id="ff271-118">Start</span></span>|<span data-ttu-id="ff271-119">Mantıksal bir işlem birimi başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="ff271-119">Starting of a logical unit of processing.</span></span>|  
|<span data-ttu-id="ff271-120">Askıya Alma</span><span class="sxs-lookup"><span data-stu-id="ff271-120">Suspend</span></span>|<span data-ttu-id="ff271-121">Mantıksal bir işlem birimini askıya alma.</span><span class="sxs-lookup"><span data-stu-id="ff271-121">Suspension of a logical unit of processing.</span></span>|  
|<span data-ttu-id="ff271-122">Sürdür</span><span class="sxs-lookup"><span data-stu-id="ff271-122">Resume</span></span>|<span data-ttu-id="ff271-123">Sürdürme mantıksal bir işlem birimi.</span><span class="sxs-lookup"><span data-stu-id="ff271-123">Resumption of a logical unit of processing.</span></span>|  
|<span data-ttu-id="ff271-124">Durdur</span><span class="sxs-lookup"><span data-stu-id="ff271-124">Stop</span></span>|<span data-ttu-id="ff271-125">Mantıksal bir işleme birimi durduruluyor.</span><span class="sxs-lookup"><span data-stu-id="ff271-125">Stopping of a logical unit of processing.</span></span>|  
|<span data-ttu-id="ff271-126">Aktarma</span><span class="sxs-lookup"><span data-stu-id="ff271-126">Transfer</span></span>|<span data-ttu-id="ff271-127">Bağıntı kimliğini değiştirme.</span><span class="sxs-lookup"><span data-stu-id="ff271-127">Changing of correlation identity.</span></span>|  
  
 <span data-ttu-id="ff271-128">Etkinlik, yukarıdaki izleme türlerinin birleşimi olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="ff271-128">An activity is defined as a combination of the trace types above.</span></span>  
  
 <span data-ttu-id="ff271-129">Aşağıda, yerel (izleme kaynağı) kapsamında ideal bir etkinliği tanımlayan bir normal ifade verilmiştir,</span><span class="sxs-lookup"><span data-stu-id="ff271-129">The following is a regular expression that defines an ideal activity in a local (trace source) scope,</span></span>  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 <span data-ttu-id="ff271-130">Bu, bir etkinliğin aşağıdaki koşulları karşılaması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ff271-130">This means that an activity must satisfy the following conditions.</span></span>  
  
- <span data-ttu-id="ff271-131">Başlatma ve durdurma izlemelerinin sırasıyla başlaması ve durdurulması gerekir</span><span class="sxs-lookup"><span data-stu-id="ff271-131">It must start and stop respectively by a Start and Stop traces</span></span>  
  
- <span data-ttu-id="ff271-132">Bir askıya alma veya yeniden başlatma izlemesinin hemen öncesinde bir aktarım izlemesi olmalıdır</span><span class="sxs-lookup"><span data-stu-id="ff271-132">It must have a Transfer trace immediately preceding a Suspend or Resume trace</span></span>  
  
- <span data-ttu-id="ff271-133">Bu tür izlemeler varsa askıya al ve Duraklat izlemeleri arasında izleme içermemelidir</span><span class="sxs-lookup"><span data-stu-id="ff271-133">It must not have any traces between the Suspend and Resume traces if such traces exist</span></span>  
  
- <span data-ttu-id="ff271-134">Önceki koşullar gözlemlendiği sürece bir veya daha fazla kritik/hata/uyarı/bilgi/ayrıntılı/aktarım izlerinden oluşabilir</span><span class="sxs-lookup"><span data-stu-id="ff271-134">It can have any and as many of critical/Error/Warning/Information/Verbose/Transfer traces as long as the previous conditions are observed</span></span>  
  
 <span data-ttu-id="ff271-135">Aşağıda genel kapsamda ideal bir etkinliği tanımlayan bir normal ifade verilmiştir,</span><span class="sxs-lookup"><span data-stu-id="ff271-135">The following is a regular expression that defines an ideal activity in the global scope,</span></span>  
  
`R+`  
  
 <span data-ttu-id="ff271-136">yerel kapsamdaki bir etkinliğin normal ifadesi olan R.</span><span class="sxs-lookup"><span data-stu-id="ff271-136">with R being the regular expression for an activity in the local scope.</span></span> <span data-ttu-id="ff271-137">Bu,</span><span class="sxs-lookup"><span data-stu-id="ff271-137">This translates to,</span></span>  
  
`[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+`
