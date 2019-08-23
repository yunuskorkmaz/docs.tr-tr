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
ms.openlocfilehash: 0a7756684d5a133fa9cb014f109d14e413223ea9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945220"
---
# <a name="how-to-remotely-survey-the-status-of-printers"></a><span data-ttu-id="0968c-102">Nasıl yapılır: Uzaktan Yazıcıların Durumunu Araştırma</span><span class="sxs-lookup"><span data-stu-id="0968c-102">How to: Remotely Survey the Status of Printers</span></span>
<span data-ttu-id="0968c-103">Orta ve büyük şirketlerde herhangi bir zamanda, kağıt sıkıştı veya kağıt kalmadı ya da başka bir sorun olması nedeniyle çalışmayan birden çok yazıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="0968c-103">At any given time at medium and large companies there may be multiple printers that are not working due to a paper jam or being out of paper or some other problematic situation.</span></span> <span data-ttu-id="0968c-104">Microsoft .NET Framework API 'Lerinde kullanıma sunulan zengin yazıcı özellikleri kümesi, yazıcıların durumlarının hızlı bir anketini gerçekleştirmek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="0968c-104">The rich set of printer properties exposed in the APIs of Microsoft .NET Framework provide a means for performing a rapid survey of the states of printers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0968c-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="0968c-105">Example</span></span>  
 <span data-ttu-id="0968c-106">Bu tür bir yardımcı program oluşturmak için önemli adımlar aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0968c-106">The major steps for creating this kind of utility are as follows.</span></span>  
  
1. <span data-ttu-id="0968c-107">Tüm yazdırma sunucularının bir listesini alın.</span><span class="sxs-lookup"><span data-stu-id="0968c-107">Obtain a list of all print servers.</span></span>  
  
2. <span data-ttu-id="0968c-108">Yazdırma kuyruklarını sorgulamak için sunucular aracılığıyla döngü gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="0968c-108">Loop through the servers to query their print queues.</span></span>  
  
3. <span data-ttu-id="0968c-109">Sunucu döngüsünün her geçişinde, tüm sunucu kuyrukları boyunca ilerleyin ve kuyruğun Şu anda çalışmadığını gösterebilen her bir özelliği okuyun.</span><span class="sxs-lookup"><span data-stu-id="0968c-109">Within each pass of the server loop, loop through all the server's queues and read each property that might indicate that the queue is not currently working.</span></span>  
  
 <span data-ttu-id="0968c-110">Aşağıdaki kod bir dizi kod parçacıdır.</span><span class="sxs-lookup"><span data-stu-id="0968c-110">The code below is a series of snippets.</span></span> <span data-ttu-id="0968c-111">Kolaylık olması için bu örnek, yazdırma sunucularının CRLF ile ayrılmış bir listesi olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="0968c-111">For simplicity, this example assumes that there is a CRLF-delimited list of print servers.</span></span> <span data-ttu-id="0968c-112">Değişken `fileOfPrintServers` , bu dosya <xref:System.IO.StreamReader> için bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="0968c-112">The variable `fileOfPrintServers` is a <xref:System.IO.StreamReader> object for this file.</span></span> <span data-ttu-id="0968c-113">Her sunucu adı kendi satırında olduğundan, herhangi bir çağrısı <xref:System.IO.StreamReader.ReadLine%2A> sonraki sunucunun adını alır ve imleci sonraki satırın başlangıcına <xref:System.IO.StreamReader>taşıdır.</span><span class="sxs-lookup"><span data-stu-id="0968c-113">Since each server name is on its own line, any call of <xref:System.IO.StreamReader.ReadLine%2A> gets the name of the next server and moves the <xref:System.IO.StreamReader>'s cursor to the beginning of the next line.</span></span>  
  
 <span data-ttu-id="0968c-114">Dış döngü içinde, kod en son yazdırma sunucusu <xref:System.Printing.PrintServer> için bir nesne oluşturur ve uygulamanın sunucuda yönetici haklarına sahip olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="0968c-114">Within the outer loop, the code creates a <xref:System.Printing.PrintServer> object for the latest print server and specifies that the application is to have administrative rights to the server.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0968c-115">Çok sayıda sunucu varsa, yalnızca ihtiyacınız olan özellikleri başlatacak <xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> oluşturucuları kullanarak performansı artırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0968c-115">If there are a lot of servers, you can improve performance by using the <xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> constructors that only initialize the properties you are going to need.</span></span>  
  
 <span data-ttu-id="0968c-116">Örnek daha sonra tüm <xref:System.Printing.PrintServer.GetPrintQueues%2A> sunucu sıralarının bir koleksiyonunu oluşturmak için kullanır ve bunlar üzerinden döngüye geçer.</span><span class="sxs-lookup"><span data-stu-id="0968c-116">The example then uses <xref:System.Printing.PrintServer.GetPrintQueues%2A> to create a collection of all of the server's queues and begins to loop through them.</span></span> <span data-ttu-id="0968c-117">Bu iç döngüde, bir yazıcının durumunu denetlemenin iki yolu ile ilgili bir dallanma yapısı bulunur:</span><span class="sxs-lookup"><span data-stu-id="0968c-117">This inner loop contains a branching structure corresponding to the two ways of checking a printer's status:</span></span>  
  
- <span data-ttu-id="0968c-118"><xref:System.Printing.PrintQueue.QueueStatus%2A> Türünde<xref:System.Printing.PrintQueueStatus>olan özelliğinin bayraklarını okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0968c-118">You can read the flags of the <xref:System.Printing.PrintQueue.QueueStatus%2A> property which is of type <xref:System.Printing.PrintQueueStatus>.</span></span>  
  
- <span data-ttu-id="0968c-119"><xref:System.Printing.PrintQueue.IsOutOfPaper%2A> Ve<xref:System.Printing.PrintQueue.IsPaperJammed%2A>gibi ilgili her özelliği okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0968c-119">You can read each relevant property such as <xref:System.Printing.PrintQueue.IsOutOfPaper%2A>, and <xref:System.Printing.PrintQueue.IsPaperJammed%2A>.</span></span>  
  
 <span data-ttu-id="0968c-120">Bu örnekte her iki yöntem de gösterilmektedir. bu nedenle, Kullanıcı daha önce hangi yöntemin kullanılacağı ve <xref:System.Printing.PrintQueue.QueueStatus%2A> özelliğin bayraklarını kullanmak istiyorlarsa "y" ile yanıt veren bir yöntem olarak istenir.</span><span class="sxs-lookup"><span data-stu-id="0968c-120">This example demonstrates both methods, so the user was previously prompted as to which method to use and responded with "y" if he or she wanted to use the flags of the <xref:System.Printing.PrintQueue.QueueStatus%2A> property.</span></span> <span data-ttu-id="0968c-121">İki yöntemin ayrıntıları için aşağıya bakın.</span><span class="sxs-lookup"><span data-stu-id="0968c-121">See below for the details of the two methods.</span></span>  
  
 <span data-ttu-id="0968c-122">Son olarak, sonuçlar kullanıcıya sunulur.</span><span class="sxs-lookup"><span data-stu-id="0968c-122">Finally, the results are presented to the user.</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#surveyqueues)]
 [!code-csharp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#surveyqueues)]
 [!code-vb[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#surveyqueues)]  
  
 <span data-ttu-id="0968c-123"><xref:System.Printing.PrintQueue.QueueStatus%2A> Özelliğin bayraklarını kullanarak yazıcı durumunu denetlemek için, ayarlanmış olup olmadığını görmek için ilgili her bayrağı kontrol edersiniz.</span><span class="sxs-lookup"><span data-stu-id="0968c-123">To check printer status using the flags of the <xref:System.Printing.PrintQueue.QueueStatus%2A> property, you check each relevant flag to see if it is set.</span></span> <span data-ttu-id="0968c-124">Bir bit bayrakları kümesinde bir bit ayarlanmış olup olmadığını görmenin standart yolu, bir işlenen olarak bayrak kümesi ve diğerinin kendisi olarak bir mantıksal ve işlem gerçekleştirmesidir.</span><span class="sxs-lookup"><span data-stu-id="0968c-124">The standard way to see if one bit is set in a set of bit flags is to perform a logical AND operation with the set of flags as one operand and the flag itself as the other.</span></span> <span data-ttu-id="0968c-125">Bayrağın kendisi yalnızca bir bit kümesine sahip olduğundan, mantıksal ve bu, en çok, aynı bitin ayarlandığı bir sonucudur.</span><span class="sxs-lookup"><span data-stu-id="0968c-125">Since the flag itself has only one bit set, the result of the logical AND is that, at most, that same bit is set.</span></span> <span data-ttu-id="0968c-126">Olup olmadığını öğrenmek için, mantıksal ve yalnızca bayrağın sonucunu karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="0968c-126">To find out whether it is or not, just compare the result of the logical AND with the flag itself.</span></span> <span data-ttu-id="0968c-127">Daha fazla bilgi için bkz <xref:System.Printing.PrintQueueStatus>. [& işleci (C# başvuru)](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)ve. <xref:System.FlagsAttribute></span><span class="sxs-lookup"><span data-stu-id="0968c-127">For more information, see <xref:System.Printing.PrintQueueStatus>, the [& Operator (C# Reference)](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-), and <xref:System.FlagsAttribute>.</span></span>  
  
 <span data-ttu-id="0968c-128">Biti ayarlanan her öznitelik için, kod kullanıcıya sunulacak son rapora bir bildirim ekler.</span><span class="sxs-lookup"><span data-stu-id="0968c-128">For each attribute whose bit is set, the code adds a notice to the final report that will be presented to the user.</span></span> <span data-ttu-id="0968c-129">(Kodun sonunda çağrılan **ReportAvailabilityAtThisTime** yöntemi aşağıda ele alınmıştır.)</span><span class="sxs-lookup"><span data-stu-id="0968c-129">(The **ReportAvailabilityAtThisTime** method that is called at the end of the code is discussed below.)</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueattributes)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueattributes)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueattributes)]  
  
 <span data-ttu-id="0968c-130">Her bir özelliği kullanarak yazıcı durumunu denetlemek için, her bir özelliği okumanız ve son rapora, özelliği ise `true`kullanıcıya sunulacak bir Note eklemeniz yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="0968c-130">To check printer status using each property, you simply read each property and add a note to the final report that will be presented to the user if the property is `true`.</span></span> <span data-ttu-id="0968c-131">(Kodun sonunda çağrılan **ReportAvailabilityAtThisTime** yöntemi aşağıda ele alınmıştır.)</span><span class="sxs-lookup"><span data-stu-id="0968c-131">(The **ReportAvailabilityAtThisTime** method that is called at the end of the code is discussed below.)</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueproperties)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueproperties)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueproperties)]  
  
 <span data-ttu-id="0968c-132">**ReportAvailabilityAtThisTime** yöntemi, kuyruğun günün geçerli saatinde kullanılabilir olup olmadığını belirlemeniz gereken durumlarda oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="0968c-132">The **ReportAvailabilityAtThisTime** method was created in case you need to determine if the queue is available at the current time of day.</span></span>  
  
 <span data-ttu-id="0968c-133">, <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> Ve<xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> özellikleri eşitse yöntem hiçbir şey yapmaz; çünkü bu durumda yazıcı her zaman kullanılabilir durumda olur.</span><span class="sxs-lookup"><span data-stu-id="0968c-133">The method will do nothing if the <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> and <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> properties are equal; because in that case the printer is available at all times.</span></span> <span data-ttu-id="0968c-134">Bu değerler farklıysa, yöntemi son gece yarısı geçen süreyi <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> alır, çünkü ve <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> özellikleri <xref:System.Int32>, hafta içi <xref:System.DateTime> dakikaları temsil ettiğinden nesneyi.</span><span class="sxs-lookup"><span data-stu-id="0968c-134">If they are different, the method gets the current time which then has to be converted into total minutes past midnight because the <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> and <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> properties are <xref:System.Int32>s representing minutes-after-midnight, not <xref:System.DateTime> objects.</span></span> <span data-ttu-id="0968c-135">Son olarak yöntemi, geçerli saatin başlangıç ve "Until" zamanları arasında olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="0968c-135">Finally, the method checks to see if the current time is between the start and "until" times.</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#usingstartanduntiltimes)]
 [!code-csharp[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#usingstartanduntiltimes)]
 [!code-vb[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#usingstartanduntiltimes)]  
  
## <a name="see-also"></a><span data-ttu-id="0968c-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0968c-136">See also</span></span>

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
- [<span data-ttu-id="0968c-137">& Işleci (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="0968c-137">& Operator (C# Reference)</span></span>](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)
- [<span data-ttu-id="0968c-138">WPF'deki Belgeler</span><span class="sxs-lookup"><span data-stu-id="0968c-138">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="0968c-139">Yazdırmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0968c-139">Printing Overview</span></span>](printing-overview.md)
