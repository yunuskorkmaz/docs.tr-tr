---
title: İzleme Türü Özeti
ms.date: 03/30/2017
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
ms.openlocfilehash: 8f54f71ef63338708a29fac5557c7c7e8f257f58
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856004"
---
# <a name="trace-type-summary"></a><span data-ttu-id="cc888-102">İzleme Türü Özeti</span><span class="sxs-lookup"><span data-stu-id="cc888-102">Trace Type Summary</span></span>
<span data-ttu-id="cc888-103">[Kaynak düzeyleri](https://go.microsoft.com/fwlink/?LinkID=94943) çeşitli izleme düzeylerini tanımlar: Kritik, hata, uyarı, bilgi ve ayrıntılı bilgilerin yanı sıra, izleme sınırının ve etkinlik aktarım `ActivityTracing` olaylarının çıktısına geçiş yapmak için bayrağın açıklaması sağlanır.</span><span class="sxs-lookup"><span data-stu-id="cc888-103">[Source Levels](https://go.microsoft.com/fwlink/?LinkID=94943) defines various trace levels: Critical, Error, Warning, Information, and Verbose, as well as provides description of the `ActivityTracing` flag, which toggles the output of trace boundary and activity transfer events.</span></span>  
  
 <span data-ttu-id="cc888-104">Ayrıca, ' den <xref:System.Diagnostics>yayılan Izleme türleri için [TraceEventType](https://go.microsoft.com/fwlink/?LinkId=95169) ' i gözden geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc888-104">You can also review [TraceEventType](https://go.microsoft.com/fwlink/?LinkId=95169) for the types of traces which can be emitted from <xref:System.Diagnostics>.</span></span>  
  
 <span data-ttu-id="cc888-105">Aşağıdaki tabloda en önemli olanlar listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="cc888-105">The following table lists the most important ones.</span></span>  
  
|<span data-ttu-id="cc888-106">İzleme türü</span><span class="sxs-lookup"><span data-stu-id="cc888-106">Trace Type</span></span>|<span data-ttu-id="cc888-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cc888-107">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="cc888-108">Kritik</span><span class="sxs-lookup"><span data-stu-id="cc888-108">Critical</span></span>|<span data-ttu-id="cc888-109">Önemli hata veya uygulama kilitlenmesi.</span><span class="sxs-lookup"><span data-stu-id="cc888-109">Fatal error or application crash.</span></span>|  
|<span data-ttu-id="cc888-110">Hata</span><span class="sxs-lookup"><span data-stu-id="cc888-110">Error</span></span>|<span data-ttu-id="cc888-111">Kurtarılabilir hata.</span><span class="sxs-lookup"><span data-stu-id="cc888-111">Recoverable error.</span></span>|  
|<span data-ttu-id="cc888-112">Uyarı</span><span class="sxs-lookup"><span data-stu-id="cc888-112">Warning</span></span>|<span data-ttu-id="cc888-113">Bilgi iletisi.</span><span class="sxs-lookup"><span data-stu-id="cc888-113">Informational message.</span></span>|  
|<span data-ttu-id="cc888-114">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="cc888-114">Information</span></span>|<span data-ttu-id="cc888-115">Kritik olmayan sorun.</span><span class="sxs-lookup"><span data-stu-id="cc888-115">Non-critical problem.</span></span>|  
|<span data-ttu-id="cc888-116">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="cc888-116">Verbose</span></span>|<span data-ttu-id="cc888-117">Hata ayıklama izleme.</span><span class="sxs-lookup"><span data-stu-id="cc888-117">Debugging trace.</span></span>|  
|<span data-ttu-id="cc888-118">Başlat</span><span class="sxs-lookup"><span data-stu-id="cc888-118">Start</span></span>|<span data-ttu-id="cc888-119">Mantıksal bir işlem birimi başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="cc888-119">Starting of a logical unit of processing.</span></span>|  
|<span data-ttu-id="cc888-120">Askıya alma</span><span class="sxs-lookup"><span data-stu-id="cc888-120">Suspend</span></span>|<span data-ttu-id="cc888-121">Mantıksal bir işlem birimini askıya alma.</span><span class="sxs-lookup"><span data-stu-id="cc888-121">Suspension of a logical unit of processing.</span></span>|  
|<span data-ttu-id="cc888-122">Devam etme</span><span class="sxs-lookup"><span data-stu-id="cc888-122">Resume</span></span>|<span data-ttu-id="cc888-123">Sürdürme mantıksal bir işlem birimi.</span><span class="sxs-lookup"><span data-stu-id="cc888-123">Resumption of a logical unit of processing.</span></span>|  
|<span data-ttu-id="cc888-124">Durdur</span><span class="sxs-lookup"><span data-stu-id="cc888-124">Stop</span></span>|<span data-ttu-id="cc888-125">Mantıksal bir işleme birimi durduruluyor.</span><span class="sxs-lookup"><span data-stu-id="cc888-125">Stopping of a logical unit of processing.</span></span>|  
|<span data-ttu-id="cc888-126">Aktarma</span><span class="sxs-lookup"><span data-stu-id="cc888-126">Transfer</span></span>|<span data-ttu-id="cc888-127">Bağıntı kimliğini değiştirme.</span><span class="sxs-lookup"><span data-stu-id="cc888-127">Changing of correlation identity.</span></span>|  
  
 <span data-ttu-id="cc888-128">Etkinlik, yukarıdaki izleme türlerinin birleşimi olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="cc888-128">An activity is defined as a combination of the trace types above.</span></span>  
  
 <span data-ttu-id="cc888-129">Aşağıda, yerel (izleme kaynağı) kapsamında ideal bir etkinliği tanımlayan bir normal ifade verilmiştir,</span><span class="sxs-lookup"><span data-stu-id="cc888-129">The following is a regular expression that defines an ideal activity in a local (trace source) scope,</span></span>  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 <span data-ttu-id="cc888-130">Bu, bir etkinliğin aşağıdaki koşulları karşılaması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="cc888-130">This means that an activity must satisfy the following conditions.</span></span>  
  
- <span data-ttu-id="cc888-131">Başlatma ve durdurma izlemelerinin sırasıyla başlaması ve durdurulması gerekir</span><span class="sxs-lookup"><span data-stu-id="cc888-131">It must start and stop respectively by a Start and Stop traces</span></span>  
  
- <span data-ttu-id="cc888-132">Bir askıya alma veya yeniden başlatma izlemesinin hemen öncesinde bir aktarım izlemesi olmalıdır</span><span class="sxs-lookup"><span data-stu-id="cc888-132">It must have a Transfer trace immediately preceding a Suspend or Resume trace</span></span>  
  
- <span data-ttu-id="cc888-133">Bu tür izlemeler varsa askıya al ve Duraklat izlemeleri arasında izleme içermemelidir</span><span class="sxs-lookup"><span data-stu-id="cc888-133">It must not have any traces between the Suspend and Resume traces if such traces exist</span></span>  
  
- <span data-ttu-id="cc888-134">Önceki koşullar gözlemlendiği sürece bir veya daha fazla kritik/hata/uyarı/bilgi/ayrıntılı/aktarım izlerinden oluşabilir</span><span class="sxs-lookup"><span data-stu-id="cc888-134">It can have any and as many of critical/Error/Warning/Information/Verbose/Transfer traces as long as the previous conditions are observed</span></span>  
  
 <span data-ttu-id="cc888-135">Aşağıda genel kapsamda ideal bir etkinliği tanımlayan bir normal ifade verilmiştir,</span><span class="sxs-lookup"><span data-stu-id="cc888-135">The following is a regular expression that defines an ideal activity in the global scope,</span></span>  
  
`R+`  
  
 <span data-ttu-id="cc888-136">yerel kapsamdaki bir etkinliğin normal ifadesi olan R.</span><span class="sxs-lookup"><span data-stu-id="cc888-136">with R being the regular expression for an activity in the local scope.</span></span> <span data-ttu-id="cc888-137">Bu,</span><span class="sxs-lookup"><span data-stu-id="cc888-137">This translates to,</span></span>  
  
`[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+`
