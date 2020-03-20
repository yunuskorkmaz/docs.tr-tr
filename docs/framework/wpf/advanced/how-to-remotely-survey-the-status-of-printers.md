---
title: 'Nasıl yapılır: Uzaktan Yazıcıların Durumunu Araştırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- surveying printer status remotely [WPF]
- printer status [WPF], surveying remotely
- remotely surveying printer status [WPF]
- status [WPF], printers [WPF], surveying remotely
ms.assetid: d6324759-8292-4c23-9584-9c708887dc94
ms.openlocfilehash: 859ccb703c6c54c66d6ea7b433c67d156627e25b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187033"
---
# <a name="how-to-remotely-survey-the-status-of-printers"></a><span data-ttu-id="dd53a-102">Nasıl yapılır: Uzaktan Yazıcıların Durumunu Araştırma</span><span class="sxs-lookup"><span data-stu-id="dd53a-102">How to: Remotely Survey the Status of Printers</span></span>
<span data-ttu-id="dd53a-103">Orta ve büyük şirketlerde herhangi bir zamanda bir kağıt sıkışması veya kağıt veya başka bir sorunlu durum dışında olması nedeniyle çalışmıyor birden fazla yazıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="dd53a-103">At any given time at medium and large companies there may be multiple printers that are not working due to a paper jam or being out of paper or some other problematic situation.</span></span> <span data-ttu-id="dd53a-104">Microsoft .NET Framework API'lerinde ortaya çıkarılan zengin yazıcı özellikleri kümesi, yazıcıların durumları hakkında hızlı bir anket yapmak için bir araç sağlar.</span><span class="sxs-lookup"><span data-stu-id="dd53a-104">The rich set of printer properties exposed in the APIs of Microsoft .NET Framework provide a means for performing a rapid survey of the states of printers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd53a-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="dd53a-105">Example</span></span>  
 <span data-ttu-id="dd53a-106">Bu tür bir yardımcı program oluşturmak için önemli adımlar aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="dd53a-106">The major steps for creating this kind of utility are as follows.</span></span>  
  
1. <span data-ttu-id="dd53a-107">Tüm yazdırma sunucularının listesini alın.</span><span class="sxs-lookup"><span data-stu-id="dd53a-107">Obtain a list of all print servers.</span></span>  
  
2. <span data-ttu-id="dd53a-108">Yazdırma kuyruklarını sorgulamak için sunucular arasında geçiş yapmayı niçin.</span><span class="sxs-lookup"><span data-stu-id="dd53a-108">Loop through the servers to query their print queues.</span></span>  
  
3. <span data-ttu-id="dd53a-109">Sunucu döngüsünün her geçişinde, sunucunun tüm kuyruklarını iletin ve sıranın şu anda çalışmadığını gösteren her özelliği okuyun.</span><span class="sxs-lookup"><span data-stu-id="dd53a-109">Within each pass of the server loop, loop through all the server's queues and read each property that might indicate that the queue is not currently working.</span></span>  
  
 <span data-ttu-id="dd53a-110">Aşağıdaki kod bir dizi parçacıktır.</span><span class="sxs-lookup"><span data-stu-id="dd53a-110">The code below is a series of snippets.</span></span> <span data-ttu-id="dd53a-111">Basitlik için, bu örnek, yazdırma sunucularının CRLF'ye bağlı bir listesi olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="dd53a-111">For simplicity, this example assumes that there is a CRLF-delimited list of print servers.</span></span> <span data-ttu-id="dd53a-112">Değişken `fileOfPrintServers` bu <xref:System.IO.StreamReader> dosya için bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="dd53a-112">The variable `fileOfPrintServers` is a <xref:System.IO.StreamReader> object for this file.</span></span> <span data-ttu-id="dd53a-113">Her sunucu adı kendi satırında olduğundan, <xref:System.IO.StreamReader.ReadLine%2A> herhangi bir çağrı sonraki sunucunun adını alır ve <xref:System.IO.StreamReader>'imleci bir sonraki satırın başına taşır.</span><span class="sxs-lookup"><span data-stu-id="dd53a-113">Since each server name is on its own line, any call of <xref:System.IO.StreamReader.ReadLine%2A> gets the name of the next server and moves the <xref:System.IO.StreamReader>'s cursor to the beginning of the next line.</span></span>  
  
 <span data-ttu-id="dd53a-114">Dış döngü içinde, kod en <xref:System.Printing.PrintServer> son yazdırma sunucusu için bir nesne oluşturur ve uygulamanın sunucuya yönetim haklarına sahip olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="dd53a-114">Within the outer loop, the code creates a <xref:System.Printing.PrintServer> object for the latest print server and specifies that the application is to have administrative rights to the server.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dd53a-115">Çok sayıda sunucu varsa, yalnızca gereksinim duyduğunuz <xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> özellikleri ilke açan oluşturucuları kullanarak performansı artırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dd53a-115">If there are a lot of servers, you can improve performance by using the <xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> constructors that only initialize the properties you are going to need.</span></span>  
  
 <span data-ttu-id="dd53a-116">Örnek daha <xref:System.Printing.PrintServer.GetPrintQueues%2A> sonra sunucunun tüm kuyrukları bir koleksiyon oluşturmak için kullanır ve bunların üzerinden döngü başlar.</span><span class="sxs-lookup"><span data-stu-id="dd53a-116">The example then uses <xref:System.Printing.PrintServer.GetPrintQueues%2A> to create a collection of all of the server's queues and begins to loop through them.</span></span> <span data-ttu-id="dd53a-117">Bu iç döngü, yazıcının durumunu denetlemenin iki yoluna karşılık gelen bir dallanma yapısı içerir:</span><span class="sxs-lookup"><span data-stu-id="dd53a-117">This inner loop contains a branching structure corresponding to the two ways of checking a printer's status:</span></span>  
  
- <span data-ttu-id="dd53a-118">Türünde olan özelliğin <xref:System.Printing.PrintQueue.QueueStatus%2A> bayraklarını <xref:System.Printing.PrintQueueStatus>okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dd53a-118">You can read the flags of the <xref:System.Printing.PrintQueue.QueueStatus%2A> property which is of type <xref:System.Printing.PrintQueueStatus>.</span></span>  
  
- <span data-ttu-id="dd53a-119">Gibi her ilgili özelliği <xref:System.Printing.PrintQueue.IsOutOfPaper%2A>okuyabilirsiniz <xref:System.Printing.PrintQueue.IsPaperJammed%2A>ve .</span><span class="sxs-lookup"><span data-stu-id="dd53a-119">You can read each relevant property such as <xref:System.Printing.PrintQueue.IsOutOfPaper%2A>, and <xref:System.Printing.PrintQueue.IsPaperJammed%2A>.</span></span>  
  
 <span data-ttu-id="dd53a-120">Bu örnek, her iki yöntemi de gösterdiğinden, kullanıcıya daha önce hangi yöntemin kullanılacağı sorulmuş ve <xref:System.Printing.PrintQueue.QueueStatus%2A> özelliğin bayraklarını kullanmak isterse "y" ile yanıt verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="dd53a-120">This example demonstrates both methods, so the user was previously prompted as to which method to use and responded with "y" if they wanted to use the flags of the <xref:System.Printing.PrintQueue.QueueStatus%2A> property.</span></span> <span data-ttu-id="dd53a-121">İki yöntemin ayrıntıları için aşağıya bakın.</span><span class="sxs-lookup"><span data-stu-id="dd53a-121">See below for the details of the two methods.</span></span>  
  
 <span data-ttu-id="dd53a-122">Son olarak, sonuçlar kullanıcıya sunulur.</span><span class="sxs-lookup"><span data-stu-id="dd53a-122">Finally, the results are presented to the user.</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#surveyqueues)]
 [!code-csharp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#surveyqueues)]
 [!code-vb[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#surveyqueues)]  
  
 <span data-ttu-id="dd53a-123"><xref:System.Printing.PrintQueue.QueueStatus%2A> Özelliğin bayraklarını kullanarak yazıcı durumunu denetlemek için, ayarlı olup olmadığını görmek için ilgili her bayrağı denetlersiniz.</span><span class="sxs-lookup"><span data-stu-id="dd53a-123">To check printer status using the flags of the <xref:System.Printing.PrintQueue.QueueStatus%2A> property, you check each relevant flag to see if it is set.</span></span> <span data-ttu-id="dd53a-124">Bir bit bit bayrakları kümesi nde ayarlanmış olup olmadığını görmek için standart yolu bir operand ve diğer olarak bayrak kendisi olarak bayrak kümesi ile mantıksal ve işlem gerçekleştirmektir.</span><span class="sxs-lookup"><span data-stu-id="dd53a-124">The standard way to see if one bit is set in a set of bit flags is to perform a logical AND operation with the set of flags as one operand and the flag itself as the other.</span></span> <span data-ttu-id="dd53a-125">Bayrağın kendisi yalnızca bir bit kümesine sahip olduğundan, mantıksal VE sonucu, en fazla, aynı bit ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="dd53a-125">Since the flag itself has only one bit set, the result of the logical AND is that, at most, that same bit is set.</span></span> <span data-ttu-id="dd53a-126">Olup olmadığını öğrenmek için, sadece mantıksal ve bayrağın kendisi ile sonucu karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="dd53a-126">To find out whether it is or not, just compare the result of the logical AND with the flag itself.</span></span> <span data-ttu-id="dd53a-127">Daha fazla bilgi <xref:System.Printing.PrintQueueStatus>için bkz:& [Operatörü (C# Reference)](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)ve <xref:System.FlagsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="dd53a-127">For more information, see <xref:System.Printing.PrintQueueStatus>, the [& Operator (C# Reference)](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-), and <xref:System.FlagsAttribute>.</span></span>  
  
 <span data-ttu-id="dd53a-128">Biti ayarlanmış her öznitelik için kod, kullanıcıya sunulacak son rapora bir bildirim ekler.</span><span class="sxs-lookup"><span data-stu-id="dd53a-128">For each attribute whose bit is set, the code adds a notice to the final report that will be presented to the user.</span></span> <span data-ttu-id="dd53a-129">(Kodun sonunda çağrılan **ReportAvailabilityAtThisTime** yöntemi aşağıda tartışılmıştır.)</span><span class="sxs-lookup"><span data-stu-id="dd53a-129">(The **ReportAvailabilityAtThisTime** method that is called at the end of the code is discussed below.)</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueattributes)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueattributes)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueattributes)]  
  
 <span data-ttu-id="dd53a-130">Her özelliği kullanarak yazıcı durumunu denetlemek için, her özelliği okumanız ve son rapora, özellik. `true`</span><span class="sxs-lookup"><span data-stu-id="dd53a-130">To check printer status using each property, you simply read each property and add a note to the final report that will be presented to the user if the property is `true`.</span></span> <span data-ttu-id="dd53a-131">(Kodun sonunda çağrılan **ReportAvailabilityAtThisTime** yöntemi aşağıda tartışılmıştır.)</span><span class="sxs-lookup"><span data-stu-id="dd53a-131">(The **ReportAvailabilityAtThisTime** method that is called at the end of the code is discussed below.)</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueproperties)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueproperties)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueproperties)]  
  
 <span data-ttu-id="dd53a-132">Sıranın günün geçerli saatinde kullanılabilir olup olmadığını belirlemeniz gerektiğinde **ReportAvailabilityAtThisTime** yöntemi oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="dd53a-132">The **ReportAvailabilityAtThisTime** method was created in case you need to determine if the queue is available at the current time of day.</span></span>  
  
 <span data-ttu-id="dd53a-133">Yöntem <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> ve <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> özellikleri eşit ise hiçbir şey yapmaz; çünkü bu durumda yazıcı her zaman kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dd53a-133">The method will do nothing if the <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> and <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> properties are equal; because in that case the printer is available at all times.</span></span> <span data-ttu-id="dd53a-134">Farklıysalar, yöntem geçerli zamanı alır ve bu süre gece yarısını geçen <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> toplam <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> dakikaya dönüştürülür, çünkü ve <xref:System.Int32> <xref:System.DateTime> özellikler nesneleri değil, gece yarısından sonra dakikaları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="dd53a-134">If they are different, the method gets the current time which then has to be converted into total minutes past midnight because the <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> and <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> properties are <xref:System.Int32>s representing minutes-after-midnight, not <xref:System.DateTime> objects.</span></span> <span data-ttu-id="dd53a-135">Son olarak, yöntem geçerli saatin başlangıç ve "kadar" saatleri arasında olup olmadığını görmek için denetler.</span><span class="sxs-lookup"><span data-stu-id="dd53a-135">Finally, the method checks to see if the current time is between the start and "until" times.</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#usingstartanduntiltimes)]
 [!code-csharp[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#usingstartanduntiltimes)]
 [!code-vb[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#usingstartanduntiltimes)]  
  
## <a name="see-also"></a><span data-ttu-id="dd53a-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd53a-136">See also</span></span>

- <xref:System.Printing.PrintQueue.StartTimeOfDay%2A>
- <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A>
- <xref:System.DateTime>
- <xref:System.Printing.PrintQueueStatus>
- <xref:System.FlagsAttribute>
- <xref:System.Printing.PrintServer.GetPrintQueues%2A>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.LocalPrintServer>
- <xref:System.Printing.EnumeratedPrintQueueTypes>
- <xref:System.Printing.PrintQueue>
- [<span data-ttu-id="dd53a-137">& Operatörü (C# Referans)</span><span class="sxs-lookup"><span data-stu-id="dd53a-137">& Operator (C# Reference)</span></span>](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)
- [<span data-ttu-id="dd53a-138">WPF'deki Belgeler</span><span class="sxs-lookup"><span data-stu-id="dd53a-138">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="dd53a-139">Yazdırmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="dd53a-139">Printing Overview</span></span>](printing-overview.md)
