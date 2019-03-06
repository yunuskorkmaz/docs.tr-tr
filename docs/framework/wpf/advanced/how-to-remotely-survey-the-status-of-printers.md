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
ms.openlocfilehash: 6eba3c5edd9095a25c0a387a3b37f68e3799d1c3
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57359711"
---
# <a name="how-to-remotely-survey-the-status-of-printers"></a><span data-ttu-id="ed12a-102">Nasıl yapılır: Uzaktan Yazıcıların Durumunu Araştırma</span><span class="sxs-lookup"><span data-stu-id="ed12a-102">How to: Remotely Survey the Status of Printers</span></span>
<span data-ttu-id="ed12a-103">Orta ve büyük şirketler belirli bir zamanda en nedeniyle bir kağıt sıkıştı çalışma veya kağıt veya diğer bazı sorunlu durum dışında olan birden çok yazıcılar olabilir.</span><span class="sxs-lookup"><span data-stu-id="ed12a-103">At any given time at medium and large companies there may be multiple printers that are not working due to a paper jam or being out of paper or some other problematic situation.</span></span> <span data-ttu-id="ed12a-104">Zengin, kullanıma sunulan yazıcı Özellikler [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] hızlı yazıcıların durumunu araştırma gerçekleştirmek için Microsoft .NET Framework'ü bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="ed12a-104">The rich set of printer properties exposed in the [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] of Microsoft .NET Framework provide a means for performing a rapid survey of the states of printers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed12a-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="ed12a-105">Example</span></span>  
 <span data-ttu-id="ed12a-106">Bu tür bir yardımcı programı oluşturmak için önemli adımlar aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="ed12a-106">The major steps for creating this kind of utility are as follows.</span></span>  
  
1.  <span data-ttu-id="ed12a-107">Tüm yazdırma sunucularının bir listesini alın.</span><span class="sxs-lookup"><span data-stu-id="ed12a-107">Obtain a list of all print servers.</span></span>  
  
2.  <span data-ttu-id="ed12a-108">Kendi yazdırma sorgulamak için sunucular üzerinden döngü.</span><span class="sxs-lookup"><span data-stu-id="ed12a-108">Loop through the servers to query their print queues.</span></span>  
  
3.  <span data-ttu-id="ed12a-109">Sunucu döngüsünün her geçişinde sunucunun tüm kuyruklar üzerinden döngü ve kuyruk şu anda çalışmadığını gösterebilir her bir özellik okuyun.</span><span class="sxs-lookup"><span data-stu-id="ed12a-109">Within each pass of the server loop, loop through all the server's queues and read each property that might indicate that the queue is not currently working.</span></span>  
  
 <span data-ttu-id="ed12a-110">Aşağıdaki kod parçacıkları dizisidir.</span><span class="sxs-lookup"><span data-stu-id="ed12a-110">The code below is a series of snippets.</span></span> <span data-ttu-id="ed12a-111">Kolaylık olması için bu örnek, yazdırma sunucularını CRLF ayrılmış bir listesi olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="ed12a-111">For simplicity, this example assumes that there is a CRLF-delimited list of print servers.</span></span> <span data-ttu-id="ed12a-112">Değişken `fileOfPrintServers` olduğu bir <xref:System.IO.StreamReader> bu dosya için nesne.</span><span class="sxs-lookup"><span data-stu-id="ed12a-112">The variable `fileOfPrintServers` is a <xref:System.IO.StreamReader> object for this file.</span></span> <span data-ttu-id="ed12a-113">Her bir sunucu adı, kendi satırında olduğundan, tüm çağrısı <xref:System.IO.StreamReader.ReadLine%2A> sonraki sunucunun adını alır ve taşır <xref:System.IO.StreamReader>'s imleci sonraki satırın başlangıcına.</span><span class="sxs-lookup"><span data-stu-id="ed12a-113">Since each server name is on its own line, any call of <xref:System.IO.StreamReader.ReadLine%2A> gets the name of the next server and moves the <xref:System.IO.StreamReader>'s cursor to the beginning of the next line.</span></span>  
  
 <span data-ttu-id="ed12a-114">Dış döngü içinde kod oluşturur bir <xref:System.Printing.PrintServer> nesne en yeni yazdırma sunucusunu ve uygulama sunucusuna yönetici haklarına sahip olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="ed12a-114">Within the outer loop, the code creates a <xref:System.Printing.PrintServer> object for the latest print server and specifies that the application is to have administrative rights to the server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ed12a-115">Çok sunucu varsa, kullanarak performansı artırabilirsiniz <xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> oluşturucular yalnızca gerek seçeceğiz özelliklerini başlatır.</span><span class="sxs-lookup"><span data-stu-id="ed12a-115">If there are a lot of servers, you can improve performance by using the <xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> constructors that only initialize the properties you are going to need.</span></span>  
  
 <span data-ttu-id="ed12a-116">Ardından örnekte <xref:System.Printing.PrintServer.GetPrintQueues%2A> tüm sunucuların bir koleksiyonunu oluşturmak üzere kuyruğa alır ve bu bloblarda döngü başlatır günceller.</span><span class="sxs-lookup"><span data-stu-id="ed12a-116">The example then uses <xref:System.Printing.PrintServer.GetPrintQueues%2A> to create a collection of all of the server's queues and begins to loop through them.</span></span> <span data-ttu-id="ed12a-117">Bu iç döngü, iki yolla yazıcının durumu denetleme, karşılık gelen bir dallandırma yapısını içerir:</span><span class="sxs-lookup"><span data-stu-id="ed12a-117">This inner loop contains a branching structure corresponding to the two ways of checking a printer's status:</span></span>  
  
-   <span data-ttu-id="ed12a-118">Bayraklarını edinebilirsiniz <xref:System.Printing.PrintQueue.QueueStatus%2A> tür özelliği <xref:System.Printing.PrintQueueStatus>.</span><span class="sxs-lookup"><span data-stu-id="ed12a-118">You can read the flags of the <xref:System.Printing.PrintQueue.QueueStatus%2A> property which is of type <xref:System.Printing.PrintQueueStatus>.</span></span>  
  
-   <span data-ttu-id="ed12a-119">Her bir ilgili özellik gibi edinebilirsiniz <xref:System.Printing.PrintQueue.IsOutOfPaper%2A>, ve <xref:System.Printing.PrintQueue.IsPaperJammed%2A>.</span><span class="sxs-lookup"><span data-stu-id="ed12a-119">You can read each relevant property such as <xref:System.Printing.PrintQueue.IsOutOfPaper%2A>, and <xref:System.Printing.PrintQueue.IsPaperJammed%2A>.</span></span>  
  
 <span data-ttu-id="ed12a-120">Bu örnekte, her iki yöntem gösterir, böylece kullanıcı daha önce hangi metodu kullanmak için istenir ve bayraklarını kullanmak istiyordu, "y" ile yanıt verdi <xref:System.Printing.PrintQueue.QueueStatus%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="ed12a-120">This example demonstrates both methods, so the user was previously prompted as to which method to use and responded with "y" if he or she wanted to use the flags of the <xref:System.Printing.PrintQueue.QueueStatus%2A> property.</span></span> <span data-ttu-id="ed12a-121">İki yöntemden biriyle ayrıntıları için aşağıya bakın.</span><span class="sxs-lookup"><span data-stu-id="ed12a-121">See below for the details of the two methods.</span></span>  
  
 <span data-ttu-id="ed12a-122">Son olarak, sonuçları kullanıcıya gösterilir.</span><span class="sxs-lookup"><span data-stu-id="ed12a-122">Finally, the results are presented to the user.</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#surveyqueues)]
 [!code-csharp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#surveyqueues)]
 [!code-vb[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#surveyqueues)]  
  
 <span data-ttu-id="ed12a-123">Bayraklarını kullanarak yazıcı durumunu denetlemek için <xref:System.Printing.PrintQueue.QueueStatus%2A> özelliği, ilgili her bayrağı ayarlanmış olup olmadığını görmek için denetleyin.</span><span class="sxs-lookup"><span data-stu-id="ed12a-123">To check printer status using the flags of the <xref:System.Printing.PrintQueue.QueueStatus%2A> property, you check each relevant flag to see if it is set.</span></span> <span data-ttu-id="ed12a-124">Bir bit bit bayrakları kümesi içinde ayarlanmış olup olmadığını görmek için standart bayrakları kümesini tek bir işlenen ve diğer bayrağını kendisini olarak bir mantıksal AND işlemini gerçekleştirmek için yoludur.</span><span class="sxs-lookup"><span data-stu-id="ed12a-124">The standard way to see if one bit is set in a set of bit flags is to perform a logical AND operation with the set of flags as one operand and the flag itself as the other.</span></span> <span data-ttu-id="ed12a-125">En fazla bayrağı ayarlayın, mantıksal sonucunu bir bit varsa ve bu yana aynı söz konusu bit ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="ed12a-125">Since the flag itself has only one bit set, the result of the logical AND is that, at most, that same bit is set.</span></span> <span data-ttu-id="ed12a-126">Bunu veya olduğunu bulmak için yalnızca sonuç mantıksal AND bayrağı ile karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="ed12a-126">To find out whether it is or not, just compare the result of the logical AND with the flag itself.</span></span> <span data-ttu-id="ed12a-127">Daha fazla bilgi için <xref:System.Printing.PrintQueueStatus>, [& işleci (C# başvuru)](~/docs/csharp/language-reference/operators/and-operator.md), ve <xref:System.FlagsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="ed12a-127">For more information, see <xref:System.Printing.PrintQueueStatus>, the [& Operator (C# Reference)](~/docs/csharp/language-reference/operators/and-operator.md), and <xref:System.FlagsAttribute>.</span></span>  
  
 <span data-ttu-id="ed12a-128">Kod biti ayarlanmış her öznitelik için bir bildirim kullanıcıya sunulan raporun son hali ekler.</span><span class="sxs-lookup"><span data-stu-id="ed12a-128">For each attribute whose bit is set, the code adds a notice to the final report that will be presented to the user.</span></span> <span data-ttu-id="ed12a-129">( **ReportAvailabilityAtThisTime** kod sonunda çağrılan yöntem aşağıda ele alınmıştır.)</span><span class="sxs-lookup"><span data-stu-id="ed12a-129">(The **ReportAvailabilityAtThisTime** method that is called at the end of the code is discussed below.)</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueattributes)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueattributes)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueattributes)]  
  
 <span data-ttu-id="ed12a-130">Her bir özellik kullanarak yazıcı durumunu denetlemek için yalnızca her bir özellik okuma ve özellik ise, kullanıcıya sunulan son rapora Not ekleme `true`.</span><span class="sxs-lookup"><span data-stu-id="ed12a-130">To check printer status using each property, you simply read each property and add a note to the final report that will be presented to the user if the property is `true`.</span></span> <span data-ttu-id="ed12a-131">( **ReportAvailabilityAtThisTime** kod sonunda çağrılan yöntem aşağıda ele alınmıştır.)</span><span class="sxs-lookup"><span data-stu-id="ed12a-131">(The **ReportAvailabilityAtThisTime** method that is called at the end of the code is discussed below.)</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueproperties)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueproperties)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueproperties)]  
  
 <span data-ttu-id="ed12a-132">**ReportAvailabilityAtThisTime** durumda kuyruğun geçerli günün saatini kullanılabilir olup olmadığını belirlemek gereken yöntemini oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="ed12a-132">The **ReportAvailabilityAtThisTime** method was created in case you need to determine if the queue is available at the current time of day.</span></span>  
  
 <span data-ttu-id="ed12a-133">Yöntemi, hiçbir şey yapmaz, <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> ve <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> özellikleri eşit; çünkü bu durumda yazıcıyı her zaman kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ed12a-133">The method will do nothing if the <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> and <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> properties are equal; because in that case the printer is available at all times.</span></span> <span data-ttu-id="ed12a-134">Farklı olmaları durumunda yöntemi olduğundan toplam dakika son gece yarısı dönüştürülmesi gereken geçerli saati alır <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> ve <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> özellikleri <xref:System.Int32>dakika-sonra-gece yarısı temsil eden değil s <xref:System.DateTime> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="ed12a-134">If they are different, the method gets the current time which then has to be converted into total minutes past midnight because the <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> and <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> properties are <xref:System.Int32>s representing minutes-after-midnight, not <xref:System.DateTime> objects.</span></span> <span data-ttu-id="ed12a-135">Son olarak, yöntem geçerli saati "kadar" kez başlangıç arasında olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="ed12a-135">Finally, the method checks to see if the current time is between the start and "until" times.</span></span>  
  
 [!code-cpp[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#usingstartanduntiltimes)]
 [!code-csharp[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#usingstartanduntiltimes)]
 [!code-vb[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#usingstartanduntiltimes)]  
  
## <a name="see-also"></a><span data-ttu-id="ed12a-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed12a-136">See also</span></span>
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
- [<span data-ttu-id="ed12a-137">& İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="ed12a-137">& Operator (C# Reference)</span></span>](~/docs/csharp/language-reference/operators/and-operator.md)
- [<span data-ttu-id="ed12a-138">WPF'deki Belgeler</span><span class="sxs-lookup"><span data-stu-id="ed12a-138">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="ed12a-139">Yazdırmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ed12a-139">Printing Overview</span></span>](printing-overview.md)
