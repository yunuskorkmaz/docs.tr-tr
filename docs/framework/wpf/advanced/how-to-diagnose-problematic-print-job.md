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
ms.openlocfilehash: 15de5d9ec8dc4016753b9d4cbed6fb0c64571774
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186038"
---
# <a name="how-to-diagnose-problematic-print-job"></a>Nasıl yapılır: Sorunlu Yazdırma İşini Tanımlama
Ağ yöneticileri genellikle kullanıcılardan yavaş yazdırılmayan veya yazdırılmayan yazdırma işleri hakkında şikayetler alır. Microsoft .NET Framework'ün API'lerinde ortaya çıkarılan zengin yazdırma iş özellikleri kümesi, yazdırma işlerinin hızlı bir uzaktan tanısını gerçekleştirmek için bir araç sağlar.  
  
## <a name="example"></a>Örnek  
 Bu tür bir yardımcı program oluşturmak için önemli adımlar aşağıdaki gibidir.  
  
1. Kullanıcının şikayet ettiği yazdırma işini tanımlayın. Kullanıcılar genellikle bunu tam olarak yapamaz. Yazdırma sunucularının veya yazıcıların adlarını bilmiyor olabilirler. Yazıcının konumunu, <xref:System.Printing.PrintQueue.Location%2A> özelliğini ayarlamada kullanılandan farklı terminolojide tanımlayabilirler. Buna göre, kullanıcının şu anda gönderilen işlerinin bir listesini oluşturmak iyi bir fikirdir. Birden fazla varsa, kullanıcı ile yazdırma sistemi yöneticisi arasındaki iletişim, sorun olan işi saptamak için kullanılabilir. Alt adımlar aşağıdaki gibidir.  
  
    1. Tüm yazdırma sunucularının listesini alın.  
  
    2. Yazdırma kuyruklarını sorgulamak için sunucular arasında geçiş yapmayı niçin.  
  
    3. Sunucu döngüher geçiş içinde, işlerini sorgulamak için tüm sunucu kuyrukları üzerinden döngü  
  
    4. Sıra döngüsünün her geçişinde, işleri arasında döngü ve şikayet eden kullanıcı tarafından gönderilenler hakkında tanımlayıcı bilgiler toplayın.  
  
2. Sorunlu yazdırma işi tanımlandığında, sorunun ne olabileceğini görmek için ilgili özellikleri inceleyin. Örneğin, iş bir hata durumunda mı yoksa iş yazdırılmadan önce sıraya hizmet veren yazıcı çevrimdışı mı oldu?  
  
 Aşağıdaki kod kod örnekleri dizisidir. İlk kod örneği, yazdırma kuyrukları üzerinden döngü içerir. (Adım 1c yukarıda.) Değişken, `myPrintQueues` geçerli <xref:System.Printing.PrintQueueCollection> yazdırma sunucusunun nesnesidir.  
  
 Kod örneği, geçerli yazdırma sırası nesnesini ' ile <xref:System.Printing.PrintQueue.Refresh%2A?displayProperty=nameWithType>yenileyerek başlar. Bu, nesnenin özelliklerinin temsil ettiği fiziksel yazıcının durumunu doğru bir şekilde temsil edilmesini sağlar. Daha sonra uygulama kullanarak <xref:System.Printing.PrintQueue.GetPrintJobInfoCollection%2A>yazdırma kuyruğunda şu anda yazdırma işleri koleksiyonunu alır.  
  
 Sonraki uygulama <xref:System.Printing.PrintSystemJobInfo> toplama yoluyla döngüler ve <xref:System.Printing.PrintSystemJobInfo.Submitter%2A> şikayetçi kullanıcının takma ile her özelliği karşılaştırır. Eşleşirse, uygulama sunulacak dize için iş hakkında tanımlayıcı bilgiler ekler. (Ve `userName` `jobList` değişkenler uygulamada daha erken başharfe işlenir.)  
  
 [!code-cpp[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#enumeratejobsinqueues)]
 [!code-csharp[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#enumeratejobsinqueues)]
 [!code-vb[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#enumeratejobsinqueues)]  
  
 Sonraki kod örneği, uygulamayı Adım 2'de alır. (Yukarıya bakınız.) Sorunlu iş tanımlandı ve uygulama onu tanımlayacak bilgiler için istenir. Bu bilgilerden oluşturur <xref:System.Printing.PrintServer> <xref:System.Printing.PrintQueue>, <xref:System.Printing.PrintSystemJobInfo> , ve nesneler.  
  
 Bu noktada uygulama, yazdırma işinin durumunu denetlemenin iki yoluna karşılık gelen bir dallanma yapısı içerir:  
  
- Türünde olan özelliğin <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> bayraklarını <xref:System.Printing.PrintJobStatus>okuyabilirsiniz.  
  
- Gibi her ilgili özelliği <xref:System.Printing.PrintSystemJobInfo.IsBlocked%2A> okuyabilirsiniz ve. <xref:System.Printing.PrintSystemJobInfo.IsInError%2A>  
  
 Bu örnek, her iki yöntemi de gösterdiğinden, kullanıcıya daha önce hangi yöntemin kullanılacağı sorulmuş ve <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> özelliğin bayraklarını kullanmak isterse "Y" ile yanıt verilmiştir. İki yöntemin ayrıntıları için aşağıya bakın. Son olarak, uygulama, işin günün bu saatinde yazdırılıp yazdırılamadığını bildirmek için **ReportQueueAndJobAvailability** adlı bir yöntem kullanır. Bu yöntem, [Yazdırma Işinin Günün Bu Saatinde Yazdırılıp Yazdırılamadığını Bulma'da](how-to-discover-whether-a-print-job-can-be-printed-at-this-time-of-day.md)açıklanır.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#identifyanddiagnoseproblematicjob)]
 [!code-csharp[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#identifyanddiagnoseproblematicjob)]
 [!code-vb[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#identifyanddiagnoseproblematicjob)]  
  
 <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> Özelliğin bayraklarını kullanarak yazdırma iş durumunu denetlemek için, ayarlı olup olmadığını görmek için ilgili her bayrağı denetlersiniz. Bir bit bit bayrakları kümesi nde ayarlanmış olup olmadığını görmek için standart yolu bir operand ve diğer olarak bayrak kendisi olarak bayrak kümesi ile mantıksal ve işlem gerçekleştirmektir. Bayrağın kendisi yalnızca bir bit kümesine sahip olduğundan, mantıksal VE sonucu, en fazla, aynı bit ayarlanır. Olup olmadığını öğrenmek için, sadece mantıksal ve bayrağın kendisi ile sonucu karşılaştırın. Daha fazla bilgi <xref:System.Printing.PrintJobStatus>için bkz:& [Operatörü (C# Reference)](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)ve <xref:System.FlagsAttribute>.  
  
 Biti ayarlanmış her öznitelik için, kod bunu konsol ekranına bildirir ve bazen yanıt vermek için bir yol önerir. (İş veya sıra duraklatılırsa çağrılan **İş Lezİzİş** yöntemi aşağıda açıklanmıştır.)  
  
 [!code-cpp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#spottroubleusingjobattributes)]
 [!code-csharp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#spottroubleusingjobattributes)]
 [!code-vb[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#spottroubleusingjobattributes)]  
  
 Ayrı özellikleri kullanarak yazdırma iş durumunu denetlemek için, her özelliği `true`okumanız ve özellik varsa konsol ekranına rapor verin ve büyük olasılıkla yanıt vermek için bir yol önerin. (İş veya sıra duraklatılırsa çağrılan **İş Lezİzİş** yöntemi aşağıda açıklanmıştır.)  
  
 [!code-cpp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#spottroubleusingjobproperties)]
 [!code-csharp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#spottroubleusingjobproperties)]
 [!code-vb[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#spottroubleusingjobproperties)]  
  
 **HandlePausedJob** yöntemi, uygulamanın kullanıcısının duraklatılmış işleri uzaktan devam ettirmesini sağlar. Yazdırma sırasının duraklatılmasının iyi bir nedeni olabileceğinden, yöntem devam edip etmeme konusunda kullanıcı kararı isteyerek başlar. Yanıt "Y" ise, <xref:System.Printing.PrintQueue.Resume%2A?displayProperty=nameWithType> yöntem çağrılır.  
  
 Daha sonra, yazdırma kuyruğundan bağımsız olarak duraklatılmış olması durumunda, kullanıcıdan işin kendisinin devam edip edileceğine karar vermesi istenir. (Karşılaştır <xref:System.Printing.PrintQueue.IsPaused%2A?displayProperty=nameWithType> <xref:System.Printing.PrintSystemJobInfo.IsPaused%2A?displayProperty=nameWithType>ve .) Cevap "Y" ise, <xref:System.Printing.PrintSystemJobInfo.Resume%2A?displayProperty=nameWithType> o zaman denir; aksi <xref:System.Printing.PrintSystemJobInfo.Cancel%2A> takdirde denir.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#HandlePausedJob](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#handlepausedjob)]
 [!code-csharp[DiagnoseProblematicPrintJob#HandlePausedJob](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#handlepausedjob)]
 [!code-vb[DiagnoseProblematicPrintJob#HandlePausedJob](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#handlepausedjob)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Printing.PrintJobStatus>
- <xref:System.Printing.PrintSystemJobInfo>
- <xref:System.FlagsAttribute>
- <xref:System.Printing.PrintQueue>
- [& Operatörü (C# Referans)](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)
- [WPF'deki Belgeler](documents-in-wpf.md)
- [Yazdırmaya Genel Bakış](printing-overview.md)
