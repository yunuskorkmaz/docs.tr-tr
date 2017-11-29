---
title: "Nasıl yapılır: Uzaktan Yazıcıların Durumunu Araştırma"
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
- surveying printer status remotely [WPF]
- printer status [WPF], surveying remotely
- remotely surveying printer status [WPF]
- status [WPF], printers [WPF], surveying remotely
ms.assetid: d6324759-8292-4c23-9584-9c708887dc94
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ad824a1cef637edc99e6aaafc99d557167ea1f1f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-remotely-survey-the-status-of-printers"></a>Nasıl yapılır: Uzaktan Yazıcıların Durumunu Araştırma
Orta ve büyük şirketlerin belirli bir zamanda adresindeki kağıt sıkışması veya kağıt veya bazı sorunlu durumlar dışında olan birden çok yazıcı olabilir. Yazıcı özellikleri de sağlanmaktadır zengin [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] , [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] yazıcıların durumlarının hızlı araştırmasını gerçekleştirmek için bir yol sağlar.  
  
## <a name="example"></a>Örnek  
 Bu tür bir yardımcı programı oluşturmak için önemli adımlar aşağıdaki gibidir.  
  
1.  Tüm yazdırma sunucularının bir listesini alın.  
  
2.  Kendi yazdırma sorgulamak için sunucular üzerinden döngü.  
  
3.  Sunucu döngüsünün her geçişinde sunucunun tüm kuyruklar üzerinden döngü ve sıranın şu an çalışmadığını gösterebilir her bir özellik okuyun.  
  
 Aşağıdaki kod parçacıkları dizisidir. Kolaylık sağlamak için bu örnek, yazdırma sunucularını CRLF ayrılmış bir listesi olduğunu varsayar. Değişkeni `fileOfPrintServers` olan bir <xref:System.IO.StreamReader> bu dosya için nesne. Her sunucu adı kendi satırında olduğundan herhangi çağrısı <xref:System.IO.StreamReader.ReadLine%2A> sonraki sunucunun adını alır ve taşır <xref:System.IO.StreamReader>'s sonraki satırın başlangıcına imleç.  
  
 Dış döngü içinde kod oluşturur bir <xref:System.Printing.PrintServer> nesne için en son yazdırma sunucusu ve uygulama sunucusu için yönetici haklarına sahip olduğunu belirtir.  
  
> [!NOTE]
>  Çok sunucu varsa, kullanarak performansı artırabilirsiniz <xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> yalnızca bulacağınızı gerek özellikleri başlatma oluşturucular.  
  
 Bu örnek daha sonra kullanır <xref:System.Printing.PrintServer.GetPrintQueues%2A> tüm sunucuların bir koleksiyonunu oluşturmak üzere sıraya koyar ve bunlar üzerinde döngü başlar kullanıcının. İçteki döngü bir yazıcının durumunu denetleme iki yolla karşılık gelen bir dallanma yapısını içerir:  
  
-   Bayraklarını okuyabilirsiniz <xref:System.Printing.PrintQueue.QueueStatus%2A> türü olan özelliği <xref:System.Printing.PrintQueueStatus>.  
  
-   İlgili her özelliği gibi okuyabilirsiniz <xref:System.Printing.PrintQueue.IsOutOfPaper%2A>, ve <xref:System.Printing.PrintQueue.IsPaperJammed%2A>.  
  
 Bu örnekte, her iki yöntem gösterir, böylece kullanıcının daha önce hangi metodu istenir ve çözemiyorsa bayraklarını kullanmak isterse "y" yanıt <xref:System.Printing.PrintQueue.QueueStatus%2A> özelliği. Aşağıda iki yöntem Ayrıntılar için bkz.  
  
 Son olarak, sonuçların kullanıcıya sunulur.  
  
 [!code-cpp[PrinterStatusSurvey#SurveyQueues](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#surveyqueues)]
 [!code-csharp[PrinterStatusSurvey#SurveyQueues](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#surveyqueues)]
 [!code-vb[PrinterStatusSurvey#SurveyQueues](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#surveyqueues)]  
  
 Bayraklarını kullanarak yazıcı durumunu denetlemek için <xref:System.Printing.PrintQueue.QueueStatus%2A> özelliği ayarlanmış olup olmadığını görmek için ilgili her bayrağı denetleyin. Bir bit bit bayrakları kümesinde ayarlanmış olup olmadığını görmek için standart bir mantıksal ve işlem bayrakları kümesiyle olarak bir işlenen ve diğer bayrağı kendisini gerçekleştirmek için yoludur. En fazla bayrağı ayarlayın, mantıksal sonucu yalnızca bir bit varsa ve bu yana o aynı bit ayarlanır. Bunu veya olup olmadığını öğrenmek için yalnızca mantıksal ve bayrağı sonucu karşılaştırın. Daha fazla bilgi için bkz: <xref:System.Printing.PrintQueueStatus>, [& işleci (C# Başvurusu)](~/docs/csharp/language-reference/operators/and-operator.md), ve <xref:System.FlagsAttribute>.  
  
 Biti ayarlanmış olan her özniteliği için kod kullanıcıya sunulan son rapora bir bildirim ekler. ( **ReportAvailabilityAtThisTime** kodu sonunda çağrılan yöntem aşağıda ele alınmıştır.)  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueattributes)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueattributes)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueattributes)]  
  
 Her bir özellik kullanarak yazıcı durumunu denetlemek için yalnızca her özelliği okuyun ve Not özelliği olan ise, kullanıcıya sunulan son rapora eklemek `true`. ( **ReportAvailabilityAtThisTime** kodu sonunda çağrılan yöntem aşağıda ele alınmıştır.)  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueproperties)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueproperties)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueproperties)]  
  
 **ReportAvailabilityAtThisTime** yöntemi oluşturuldu durumunda günün geçerli saatinde sıranın kullanılabilir olup olmadığını belirlemeniz gerekir.  
  
 Yöntemi, hiçbir şey yapmaz varsa <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> ve <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> özelliklerdir eşit; bu durumda yazıcı her zaman kullanılabilir olduğundan. Bunlar farklıysa, çünkü toplam dakika son gece dönüştürülecek olan geçerli saati yöntemi alır <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> ve <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> özellikleri <xref:System.Int32>dakika sonra-dönüştürmemiz, temsil eden değil s <xref:System.DateTime> nesneleri. Son olarak, geçerli saati "kadar" kez başlangıç arasında olup olmadığını görmek için yöntem denetler.  
  
 [!code-cpp[PrinterStatusSurvey#UsingStartAndUntilTimes](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#usingstartanduntiltimes)]
 [!code-csharp[PrinterStatusSurvey#UsingStartAndUntilTimes](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#usingstartanduntiltimes)]
 [!code-vb[PrinterStatusSurvey#UsingStartAndUntilTimes](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#usingstartanduntiltimes)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Printing.PrintQueue.StartTimeOfDay%2A>  
 <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A>  
 <xref:System.DateTime>  
 <xref:System.Printing.PrintQueueStatus>  
 <xref:System.FlagsAttribute>  
 <xref:System.Printing.PrintServer.GetPrintQueues%2A>  
 <xref:System.Printing.PrintServer>  
 <xref:System.Printing.LocalPrintServer>  
 <xref:System.Printing.EnumeratedPrintQueueTypes>  
 <xref:System.Printing.PrintQueue>  
 [& İşleci (C# Başvurusu)](~/docs/csharp/language-reference/operators/and-operator.md)  
 [WPF belgeleri](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Yazdırma genel bakış](../../../../docs/framework/wpf/advanced/printing-overview.md)
