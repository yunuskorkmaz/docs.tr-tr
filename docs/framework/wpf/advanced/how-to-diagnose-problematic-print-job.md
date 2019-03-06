---
title: 'Nasıl yapılır: Sorunlu Yazdırma İşini Tanımlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- troubleshooting print job problems [WPF]
- print jobs [WPF], troubleshooting
- print jobs [WPF], diagnosing problems
ms.assetid: b081a170-84c6-48f9-a487-5766a8d58a82
ms.openlocfilehash: babd601bb29fc2aa9c906921082a18942f6649c0
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369714"
---
# <a name="how-to-diagnose-problematic-print-job"></a>Nasıl yapılır: Sorunlu Yazdırma İşini Tanımlama
Ağ yöneticileri genellikle şikayetlerinin değil veya yavaş yazdırma, yazdırma işlerini ilgili olarak kullanıcılardan alan. Zengin, kullanıma sunulan yazdırma işi Özellikler [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] hızlı bir uzaktan tanılama yazdırma işi gerçekleştirmek için Microsoft .NET Framework'ü bir yol sağlar.  
  
## <a name="example"></a>Örnek  
 Bu tür bir yardımcı programı oluşturmak için önemli adımlar aşağıdaki gibidir.  
  
1.  Kullanıcı hakkında şikayetçi yazdırma işi tanımlayın. Kullanıcılar genellikle tam olarak bunu yapamaz. Yazıcı ve yazdırma sunucularının adlarını bilemeyebilirsiniz. Ayarında kullanılandan farklı bir terminoloji yazıcıya konumunu açıklayabilir kendi <xref:System.Printing.PrintQueue.Location%2A> özelliği. Buna göre bu kullanıcının listesi şu anda oluşturmak iyi bir fikir gönderilen olur. Varsa birden fazla kullanıcı ve yazdırma sistemi yönetici arasındaki iletişimi sorunları ortaya çıktığında iş saptamak için kullanılabilir. Alt adımlar aşağıdaki gibidir.  
  
    1.  Tüm yazdırma sunucularının bir listesini alın.  
  
    2.  Kendi yazdırma sorgulamak için sunucular üzerinden döngü.  
  
    3.  Sunucu döngüsünün her geçişinde işlerini sorgulamak için sunucunun tüm kuyruklar üzerinden döngü  
  
    4.  Kuyruk döngünün her geçişinde döngü, işlerini ve şikayetçi kullanıcı tarafından gönderilen bu hakkında tanımlayıcı bilgileri toplayın.  
  
2.  Sorunlu yazdırma işini tanımlandığı zaman hangi sorunu olabileceğini görmek için ilgili özelliklerini inceleyin. Örneğin, bir hata durumunda iş veya yazıcı sırası işi yazdırmadan önce çevrimdışı hizmet verme muydunuz?  
  
 Aşağıdaki kod, kod örnekleri bir dizisidir. İlk örnek kod, yazdırma sıralarını döngü içerir. (1 c yukarıdaki adım.) Değişken `myPrintQueues` olduğu <xref:System.Printing.PrintQueueCollection> geçerli yazdırma sunucusu için nesne.  
  
 Kod örneği geçerli bir yazdırma sırasını nesneyle yenileyerek başlar <xref:System.Printing.PrintQueue.Refresh%2A?displayProperty=nameWithType>. Bu, nesnenin özelliklerini temsil ettiği fiziksel yazıcı durumunu doğru şekilde temsil sağlar. Uygulama yazdırma işlerini koleksiyonu şu anda yazdırma kuyruğunda kullanarak alır, ardından <xref:System.Printing.PrintQueue.GetPrintJobInfoCollection%2A>.  
  
 Uygulamayı sonraki döngü <xref:System.Printing.PrintSystemJobInfo> toplama ve karşılaştırır <xref:System.Printing.PrintSystemJobInfo.Submitter%2A> şikayetçi olan kullanıcı diğer adı ile özelliği. Eşleşiyorlarsa uygulama işi hakkında tanıtıcı bilgi sunulacak dizesine ekler. ( `userName` Ve `jobList` değişkenleri, uygulamada daha önce başlatılır.)  
  
 [!code-cpp[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#enumeratejobsinqueues)]
 [!code-csharp[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#enumeratejobsinqueues)]
 [!code-vb[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#enumeratejobsinqueues)]  
  
 2. adım uygulamayı sonraki kod örneğinde seçer. (Yukarıya bakın.) Sorunlu iş belirlenmiştir ve uygulamayı tanımlayacak bilgileri ister. Bu bilgiyi oluşturduğu <xref:System.Printing.PrintServer>, <xref:System.Printing.PrintQueue>, ve <xref:System.Printing.PrintSystemJobInfo> nesneleri.  
  
 Bu noktada uygulama, karşılık gelen bir yazdırma işin durumunu denetleme için iki yol bir dallandırma yapısını içerir:  
  
-   Bayraklarını edinebilirsiniz <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> tür özelliği <xref:System.Printing.PrintJobStatus>.  
  
-   Her bir ilgili özellik gibi edinebilirsiniz <xref:System.Printing.PrintSystemJobInfo.IsBlocked%2A> ve <xref:System.Printing.PrintSystemJobInfo.IsInError%2A>.  
  
 Bu örnekte, her iki yöntem gösterir, böylece kullanıcı daha önce hangi metodu kullanmak için istenir ve bayraklarını kullanmak istiyordu, "Y" ile yanıt verdi <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> özelliği. İki yöntemden biriyle ayrıntıları için aşağıya bakın. Son olarak, uygulama adında bir yöntem kullanır **ReportQueueAndJobAvailability** iş günün bu saatinde yazdırılabilir olup olmadığını bildirmek için. Bu yöntem içinde ele alınmıştır [keşfedin olup olmadığını bir yazdırma işi yapabilirsiniz olması yazdırılan sırasında bu günün saati](how-to-discover-whether-a-print-job-can-be-printed-at-this-time-of-day.md).  
  
 [!code-cpp[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#identifyanddiagnoseproblematicjob)]
 [!code-csharp[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#identifyanddiagnoseproblematicjob)]
 [!code-vb[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#identifyanddiagnoseproblematicjob)]  
  
 Bayraklarını kullanarak yazdırma işinin durumunu denetlemek için <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> özelliği, ilgili her bayrağı ayarlanmış olup olmadığını görmek için denetleyin. Bir bit bit bayrakları kümesi içinde ayarlanmış olup olmadığını görmek için standart bayrakları kümesini tek bir işlenen ve diğer bayrağını kendisini olarak bir mantıksal AND işlemini gerçekleştirmek için yoludur. En fazla bayrağı ayarlayın, mantıksal sonucunu bir bit varsa ve bu yana aynı söz konusu bit ayarlanır. Bunu veya olduğunu bulmak için yalnızca sonuç mantıksal AND bayrağı ile karşılaştırın. Daha fazla bilgi için <xref:System.Printing.PrintJobStatus>, [& işleci (C# başvuru)](~/docs/csharp/language-reference/operators/and-operator.md), ve <xref:System.FlagsAttribute>.  
  
 Biti ayarlanmış, her bir öznitelik için kod, bu rapor, konsol ekranına ve bazen yanıt için bir yol önerir. ( **HandlePausedJob** iş veya sıra duraklatılmışsa çağrılan yöntem aşağıda ele alınmıştır.)  
  
 [!code-cpp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#spottroubleusingjobattributes)]
 [!code-csharp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#spottroubleusingjobattributes)]
 [!code-vb[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#spottroubleusingjobattributes)]  
  
 Ayrı özellikleri kullanarak yazdırma işinin durumunu denetlemek için yalnızca her bir özellik okuyun ve özellik ise `true`, rapor konsol ekranına ve büyük olasılıkla yanıt için bir yol önerin. ( **HandlePausedJob** iş veya sıra duraklatılmışsa çağrılan yöntem aşağıda ele alınmıştır.)  
  
 [!code-cpp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#spottroubleusingjobproperties)]
 [!code-csharp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#spottroubleusingjobproperties)]
 [!code-vb[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#spottroubleusingjobproperties)]  
  
 **HandlePausedJob** uzaktan duraklatılmış işler devam etmek uygulamanın kullanıcı yöntemi sağlar. Yazdırma sırasını neden duraklatıldı geçerli bir nedeniniz olabileceğinden yöntem bunu sürdürmek konusunda bir kullanıcı karar isteyerek başlar. "Y" ise sonra <xref:System.Printing.PrintQueue.Resume%2A?displayProperty=nameWithType> yöntemi çağrılır.  
  
 Sonraki kullanıcı işi sürdürülemiyor varsa, bağımsız olarak yazdırma sırasını duraklatıldı durumunda karar vermeniz istenir. (Karşılaştırma <xref:System.Printing.PrintQueue.IsPaused%2A?displayProperty=nameWithType> ve <xref:System.Printing.PrintSystemJobInfo.IsPaused%2A?displayProperty=nameWithType>.) Yanıt "Y", ardından ise <xref:System.Printing.PrintSystemJobInfo.Resume%2A?displayProperty=nameWithType> çağrılan; Aksi takdirde <xref:System.Printing.PrintSystemJobInfo.Cancel%2A> çağrılır.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#HandlePausedJob](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#handlepausedjob)]
 [!code-csharp[DiagnoseProblematicPrintJob#HandlePausedJob](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#handlepausedjob)]
 [!code-vb[DiagnoseProblematicPrintJob#HandlePausedJob](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#handlepausedjob)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Printing.PrintJobStatus>
- <xref:System.Printing.PrintSystemJobInfo>
- <xref:System.FlagsAttribute>
- <xref:System.Printing.PrintQueue>
- [& İşleci (C# Başvurusu)](~/docs/csharp/language-reference/operators/and-operator.md)
- [WPF'deki Belgeler](documents-in-wpf.md)
- [Yazdırmaya Genel Bakış](printing-overview.md)
