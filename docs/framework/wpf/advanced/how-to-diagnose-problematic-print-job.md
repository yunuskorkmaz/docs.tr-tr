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
ms.openlocfilehash: 181248f69684860fd43648952ef4eb3cced1c0ba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944629"
---
# <a name="how-to-diagnose-problematic-print-job"></a>Nasıl yapılır: Sorunlu Yazdırma İşini Tanımlama
Ağ yöneticileri çoğunlukla, yavaş yazdırılmayan veya yazdırmayan yazdırma işleri hakkında kullanıcılardan şikayetlerden kaynaklanır. Microsoft .NET Framework API 'Lerinde kullanıma sunulan zengin yazdırma işi özellikleri, yazdırma işlerinin hızlı uzaktan tanılamasını gerçekleştirmek için bir yol sağlar.  
  
## <a name="example"></a>Örnek  
 Bu tür bir yardımcı program oluşturmak için önemli adımlar aşağıda verilmiştir.  
  
1. Kullanıcının hakkında şikayetçi olduğu yazdırma işini belirler. Kullanıcılar genellikle bu işlemleri kesinlikle yapamazlar. Yazdırma sunucularının veya yazıcıların adlarını bilmiyor olabilir. Bu kişiler, kendi <xref:System.Printing.PrintQueue.Location%2A> özelliğini ayarlarken kullanılandan farklı terminolojisinde yazıcının konumunu açıklayabilir. Buna uygun olarak, kullanıcının şu anda gönderdiği işlerin bir listesini oluşturmak iyi bir fikirdir. Birden fazla varsa, Kullanıcı ve yazıcı sistemi Yöneticisi arasındaki iletişim, sorun yaşayan işi saptamak için kullanılabilir. Alt adımlar aşağıdaki gibidir.  
  
    1. Tüm yazdırma sunucularının bir listesini alın.  
  
    2. Yazdırma kuyruklarını sorgulamak için sunucular aracılığıyla döngü gerçekleştirin.  
  
    3. Sunucu döngüsünün her geçişinde, işlerini sorgulamak için tüm sunucu kuyruklarında döngü gerçekleştirin  
  
    4. Sıra döngüsünün her bir geçişinde, işleri boyunca ilerleyin ve şikayetçi Kullanıcı tarafından gönderilen olanlarla ilgili tanımlama bilgilerini toplayın.  
  
2. Sorunlu yazdırma işi tanımlandığında, sorunun ne olabileceğini görmek için ilgili özellikleri inceleyin. Örneğin, iş bir hata durumunda ya da iş yazdıramadan önce kuyruğun hizmet verdiği yazıcı çevrimdışı duruma mi çalışıyor?  
  
 Aşağıdaki kod, kod örnekleri dizisidir. İlk kod örneği, yazdırma kuyrukları aracılığıyla döngüyü içerir. (Yukarıdaki adım 1C.) `myPrintQueues` Değişkeni<xref:System.Printing.PrintQueueCollection> , geçerli yazdırma sunucusunun nesnesidir.  
  
 Kod örneği, geçerli yazdırma kuyruğu nesnesinin ile <xref:System.Printing.PrintQueue.Refresh%2A?displayProperty=nameWithType>yenilenerek başlar. Bu, nesnenin özelliklerinin temsil ettiği fiziksel yazıcının durumunu doğru şekilde temsil etmesini sağlar. Ardından uygulama, şu anda yazdırma sırasındaki yazdırma işlerinin koleksiyonunu kullanarak <xref:System.Printing.PrintQueue.GetPrintJobInfoCollection%2A>alır.  
  
 Daha sonra uygulama, <xref:System.Printing.PrintSystemJobInfo> koleksiyon aracılığıyla geçer ve her <xref:System.Printing.PrintSystemJobInfo.Submitter%2A> bir özelliği şikayetçi kullanıcısının diğer adıyla karşılaştırır. Eşleşiyorsa, uygulama, sunulacak dizeye iş hakkında tanımlama bilgilerini ekler. `userName` (Ve `jobList` değişkenleri uygulamada daha önce başlatılır.)  
  
 [!code-cpp[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#enumeratejobsinqueues)]
 [!code-csharp[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#enumeratejobsinqueues)]
 [!code-vb[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#enumeratejobsinqueues)]  
  
 Sonraki kod örneği, 2. adımdaki uygulamayı seçer. (Yukarıya bakın.) Sorunlu iş tanımlanmıştır ve uygulama onu tanımlayacak bilgileri sorar. Bu bilgilerden, <xref:System.Printing.PrintServer> <xref:System.Printing.PrintQueue>ve <xref:System.Printing.PrintSystemJobInfo> nesneleri oluşturur.  
  
 Bu noktada, uygulama bir yazdırma işinin durumunu denetlemenin iki yolu ile eşleşen bir dallanma yapısı içerir:  
  
- <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> Türünde<xref:System.Printing.PrintJobStatus>olan özelliğinin bayraklarını okuyabilirsiniz.  
  
- <xref:System.Printing.PrintSystemJobInfo.IsBlocked%2A> Ve<xref:System.Printing.PrintSystemJobInfo.IsInError%2A>gibi ilgili her özelliği okuyabilirsiniz.  
  
 Bu örnekte her iki yöntem de gösterilmektedir. bu nedenle, Kullanıcı daha önce hangi yöntemin kullanılacağı ve <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> özelliğin bayraklarını kullanmak istiyorlarsa "Y" ile yanıt veren bir yöntem olarak istenir. İki yöntemin ayrıntıları için aşağıya bakın. Son olarak, uygulama, işin bu saatte yazdırılıp yazdırılamayacağını raporlamak için **ReportQueueAndJobAvailability** adlı bir yöntem kullanır. Bu yöntem, [günde bir yazdırma Işinin yazdırılıp yazdırılmadığını bulma](how-to-discover-whether-a-print-job-can-be-printed-at-this-time-of-day.md)bölümünde ele alınmıştır.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#identifyanddiagnoseproblematicjob)]
 [!code-csharp[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#identifyanddiagnoseproblematicjob)]
 [!code-vb[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#identifyanddiagnoseproblematicjob)]  
  
 <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> Özelliğin bayraklarını kullanarak yazdırma işi durumunu denetlemek için, ayarlanmış olup olmadığını görmek için ilgili her bayrağı kontrol edersiniz. Bir bit bayrakları kümesinde bir bit ayarlanmış olup olmadığını görmenin standart yolu, bir işlenen olarak bayrak kümesi ve diğerinin kendisi olarak bir mantıksal ve işlem gerçekleştirmesidir. Bayrağın kendisi yalnızca bir bit kümesine sahip olduğundan, mantıksal ve bu, en çok, aynı bitin ayarlandığı bir sonucudur. Olup olmadığını öğrenmek için, mantıksal ve yalnızca bayrağın sonucunu karşılaştırın. Daha fazla bilgi için bkz <xref:System.Printing.PrintJobStatus>. [& işleci (C# başvuru)](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)ve. <xref:System.FlagsAttribute>  
  
 Biti ayarlanan her öznitelik için, kod bunu konsol ekranına bildirir ve bazen yanıt vermek için bir yol önerir. (İş veya sıra duraklatıldığında çağrılan **HandlePausedJob** yöntemi aşağıda ele alınmıştır.)  
  
 [!code-cpp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#spottroubleusingjobattributes)]
 [!code-csharp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#spottroubleusingjobattributes)]
 [!code-vb[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#spottroubleusingjobattributes)]  
  
 Ayrı özellikler kullanarak yazdırma işi durumunu denetlemek için, her bir özelliği okuyun ve özellik ise `true`, konsol ekranına rapor verir ve muhtemelen yanıt vermek için bir yol önerebilir. (İş veya sıra duraklatıldığında çağrılan **HandlePausedJob** yöntemi aşağıda ele alınmıştır.)  
  
 [!code-cpp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#spottroubleusingjobproperties)]
 [!code-csharp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#spottroubleusingjobproperties)]
 [!code-vb[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#spottroubleusingjobproperties)]  
  
 **HandlePausedJob** yöntemi, uygulamanın kullanıcının duraklatılmış işleri uzaktan sürdürmesini sağlar. Yazdırma sırasının duraklatılmasının iyi bir nedeni olabileceğinden, yöntemi, sürdürülip sürdürülmediği konusunda bir Kullanıcı kararı isteyerek başlar. Yanıt "Y" <xref:System.Printing.PrintQueue.Resume%2A?displayProperty=nameWithType> ise, yöntemi çağrılır.  
  
 Daha sonra, kullanıcının, yazdırma sırasından bağımsız olarak duraklatıldığı durumda, işin kendisinin devam etmesi gerekip gerekmediğine karar vermesini istenir. (Karşılaştır <xref:System.Printing.PrintQueue.IsPaused%2A?displayProperty=nameWithType> ve <xref:System.Printing.PrintSystemJobInfo.IsPaused%2A?displayProperty=nameWithType>.) Yanıt "Y" <xref:System.Printing.PrintSystemJobInfo.Resume%2A?displayProperty=nameWithType> ise çağrılır; Aksi takdirde <xref:System.Printing.PrintSystemJobInfo.Cancel%2A> çağrılır.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#HandlePausedJob](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#handlepausedjob)]
 [!code-csharp[DiagnoseProblematicPrintJob#HandlePausedJob](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#handlepausedjob)]
 [!code-vb[DiagnoseProblematicPrintJob#HandlePausedJob](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#handlepausedjob)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Printing.PrintJobStatus>
- <xref:System.Printing.PrintSystemJobInfo>
- <xref:System.FlagsAttribute>
- <xref:System.Printing.PrintQueue>
- [& Işleci (C# başvuru)](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)
- [WPF'deki Belgeler](documents-in-wpf.md)
- [Yazdırmaya Genel Bakış](printing-overview.md)
