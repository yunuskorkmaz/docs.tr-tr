---
title: "Nasıl yapılır: Sorunlu Yazdırma İşini Tanımlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- troubleshooting print job problems [WPF]
- print jobs [WPF], troubleshooting
- print jobs [WPF], diagnosing problems
ms.assetid: b081a170-84c6-48f9-a487-5766a8d58a82
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: acc757d899da3ff737b2884131b77135265fd197
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-diagnose-problematic-print-job"></a>Nasıl yapılır: Sorunlu Yazdırma İşini Tanımlama
Ağ yöneticileri genellikle değil veya yavaş yazdırma yazdırma işleri hakkında kullanıcılardan şikayetlerinden alan. Yazdırma işi özellikleri de sağlanmaktadır zengin [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] , [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] yazdırma işlerinin hızlı uzaktan tanılamasını gerçekleştirmek için bir yol sağlar.  
  
## <a name="example"></a>Örnek  
 Bu tür bir yardımcı programı oluşturmak için önemli adımlar aşağıdaki gibidir.  
  
1.  Kullanıcı hakkında şikayetçi yazdırma işi tanımlayın. Kullanıcılar genellikle tam olarak bunu yapamaz. Yazdırma sunucuları veya yazıcıların adlarını bilemeyebilirsiniz. Ayarında kullanılandan farklı bir terminoloji yazıcıda konumunu açıklayabilir kendi <xref:System.Printing.PrintQueue.Location%2A> özelliği. Buna uygun olarak, şu anda kullanıcının listesini oluşturmak için iyi bir fikir işleri gönderilen olur. Varsa birden fazla, kullanıcı ve yazdırma Sistem Yöneticisi arasındaki iletişim sorunları var. iş saptamak için kullanılabilir. Alt adımlar aşağıdaki gibidir.  
  
    1.  Tüm yazdırma sunucularının bir listesini alın.  
  
    2.  Kendi yazdırma sorgulamak için sunucular üzerinden döngü.  
  
    3.  İşlerini sorgulamak için sunucunun tüm kuyruklar üzerinden içinde her geçişte sunucu döngüsünün döngüsü  
  
    4.  Sıra döngüsü her geçişinde kendi işlerinde döngü gerçekleştirin ve şikayetçi kullanıcı tarafından gönderilmiş o hakkında tanımlayıcı bilgileri toplayın.  
  
2.  Sorunlu yazdırma işi tanımlanan kullanırken ne sorun olabilir görmek için ilgili özelliklerini inceleyin. Örneğin, bir hata durumda iş veya sırası işi yazdırma önce çevrimdışı yazıcı bakım muydunuz?  
  
 Aşağıdaki kod, kod örnekleri bir dizisidir. İlk örnek kod, yazdırma sıralarını döngü içerir. (Yukarıdaki adım 1 c.) Değişkeni `myPrintQueues` olan <xref:System.Printing.PrintQueueCollection> geçerli yazdırma sunucusu için nesne.  
  
 Kod örneği geçerli yazdırma sırası nesneyle yenileyerek başlar <xref:System.Printing.PrintQueue.Refresh%2A?displayProperty=nameWithType>. Bu nesnenin özellikleri temsil ettiği fiziksel yazıcının durumunu doğru şekilde temsil sağlar. Uygulama yazdırma işlerini koleksiyon şu anda yazdırma kuyruğunda kullanarak alır sonra <xref:System.Printing.PrintQueue.GetPrintJobInfoCollection%2A>.  
  
 Sonraki uygulama döngü <xref:System.Printing.PrintSystemJobInfo> toplama ve karşılaştırır <xref:System.Printing.PrintSystemJobInfo.Submitter%2A> şikayetçi kullanıcı diğer adı özelliğiyle. Eşleşirlerse, uygulama iş hakkında tanımlayıcı bilgileri sunulacak dizesi olarak ekler. ( `userName` Ve `jobList` değişkenleri uygulamada daha önce başlatılmış.)  
  
 [!code-cpp[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#enumeratejobsinqueues)]
 [!code-csharp[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#enumeratejobsinqueues)]
 [!code-vb[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#enumeratejobsinqueues)]  
  
 2. adım uygulamayı sonraki kod örneği alır. (Yukarıya bakın.) Sorunlu iş tanımlanır ve uygulama tanımlayacak bilgileri ister. Bu bilgilerden oluşturduğu <xref:System.Printing.PrintServer>, <xref:System.Printing.PrintQueue>, ve <xref:System.Printing.PrintSystemJobInfo> nesneleri.  
  
 Bu noktada uygulamanın bir yazdırma işi durumunu denetleme, iki yolla karşılık gelen bir dallanma yapısını içerir:  
  
-   Bayraklarını okuyabilirsiniz <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> türü olan özelliği <xref:System.Printing.PrintJobStatus>.  
  
-   İlgili her özelliği gibi okuyabilirsiniz <xref:System.Printing.PrintSystemJobInfo.IsBlocked%2A> ve <xref:System.Printing.PrintSystemJobInfo.IsInError%2A>.  
  
 Bu örnekte, her iki yöntem gösterir, böylece kullanıcının daha önce hangi metodu istenir ve çözemiyorsa bayraklarını kullanmak isterse "Y" yanıt <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> özelliği. Aşağıda iki yöntem Ayrıntılar için bkz. Son olarak, uygulama adı verilen bir yöntem kullanır **ReportQueueAndJobAvailability** iş günü şu anda yazdırılabilir olup bildirilecek. Bu yöntem içinde ele alınmıştır [Bul olup olmadığını bir yazdırma işi yapabilirsiniz olması yazdırılan adresindeki bu saat, gün](../../../../docs/framework/wpf/advanced/how-to-discover-whether-a-print-job-can-be-printed-at-this-time-of-day.md).  
  
 [!code-cpp[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#identifyanddiagnoseproblematicjob)]
 [!code-csharp[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#identifyanddiagnoseproblematicjob)]
 [!code-vb[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#identifyanddiagnoseproblematicjob)]  
  
 Bayraklarını kullanarak yazdırma işinin durumunu denetlemek için <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> özelliği ayarlanmış olup olmadığını görmek için ilgili her bayrağı denetleyin. Bir bit bit bayrakları kümesinde ayarlanmış olup olmadığını görmek için standart bir mantıksal ve işlem bayrakları kümesiyle olarak bir işlenen ve diğer bayrağı kendisini gerçekleştirmek için yoludur. En fazla bayrağı ayarlayın, mantıksal sonucu yalnızca bir bit varsa ve bu yana o aynı bit ayarlanır. Bunu veya olup olmadığını öğrenmek için yalnızca mantıksal ve bayrağı sonucu karşılaştırın. Daha fazla bilgi için bkz: <xref:System.Printing.PrintJobStatus>, [& işleci (C# Başvurusu)](~/docs/csharp/language-reference/operators/and-operator.md), ve <xref:System.FlagsAttribute>.  
  
 Biti ayarlanmış olan her bir öznitelik için kod bunu konsol ekranına bildirir ve bazen yanıt için bir yol önerir. ( **HandlePausedJob** iş veya sıra duraklatıldığında çağrılan yöntem aşağıda ele alınmıştır.)  
  
 [!code-cpp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#spottroubleusingjobattributes)]
 [!code-csharp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#spottroubleusingjobattributes)]
 [!code-vb[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#spottroubleusingjobattributes)]  
  
 Ayrı özellikleri kullanarak yazdırma işinin durumunu denetlemek için yalnızca her özelliği okuyun ve özellik ise `true`, rapor konsol ekranına ve büyük olasılıkla yanıt için bir yol önerin. ( **HandlePausedJob** iş veya sıra duraklatıldığında çağrılan yöntem aşağıda ele alınmıştır.)  
  
 [!code-cpp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#spottroubleusingjobproperties)]
 [!code-csharp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#spottroubleusingjobproperties)]
 [!code-vb[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#spottroubleusingjobproperties)]  
  
 **HandlePausedJob** yöntemi uzaktan duraklatılmış işlerini sürdürmek uygulamanın kullanıcı sağlar. Yazdırma sırasını neden duraklatıldı iyi bir neden olabileceğinden yöntemi hakkında devam etmek bir kullanıcı kararını isteyerek başlar. Yanıt "Y" ise sonra <xref:System.Printing.PrintQueue.Resume%2A?displayProperty=nameWithType> yöntemi çağrılır.  
  
 Sonraki kullanıcı işi devam ettirilebilir varsa, bağımsız olarak yazdırma sırası duraklatıldı olasılığına karar istenir. (Karşılaştırma <xref:System.Printing.PrintQueue.IsPaused%2A?displayProperty=nameWithType> ve <xref:System.Printing.PrintSystemJobInfo.IsPaused%2A?displayProperty=nameWithType>.) Yanıt "Y" ise, <xref:System.Printing.PrintSystemJobInfo.Resume%2A?displayProperty=nameWithType> çağrılan; Aksi takdirde <xref:System.Printing.PrintSystemJobInfo.Cancel%2A> olarak adlandırılır.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#HandlePausedJob](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#handlepausedjob)]
 [!code-csharp[DiagnoseProblematicPrintJob#HandlePausedJob](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#handlepausedjob)]
 [!code-vb[DiagnoseProblematicPrintJob#HandlePausedJob](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#handlepausedjob)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Printing.PrintJobStatus>  
 <xref:System.Printing.PrintSystemJobInfo>  
 <xref:System.FlagsAttribute>  
 <xref:System.Printing.PrintQueue>  
 [& İşleci (C# Başvurusu)](~/docs/csharp/language-reference/operators/and-operator.md)  
 [WPF belgeleri](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Yazdırma genel bakış](../../../../docs/framework/wpf/advanced/printing-overview.md)
