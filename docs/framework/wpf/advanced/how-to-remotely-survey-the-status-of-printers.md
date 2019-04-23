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
ms.openlocfilehash: dc187a4ea120661e8118ce79a966d3d4a3b40711
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59340795"
---
# <a name="how-to-remotely-survey-the-status-of-printers"></a>Nasıl yapılır: Uzaktan Yazıcıların Durumunu Araştırma
Orta ve büyük şirketler belirli bir zamanda en nedeniyle bir kağıt sıkıştı çalışma veya kağıt veya diğer bazı sorunlu durum dışında olan birden çok yazıcılar olabilir. Zengin, kullanıma sunulan yazıcı Özellikler [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] hızlı yazıcıların durumunu araştırma gerçekleştirmek için Microsoft .NET Framework'ü bir yol sağlar.  
  
## <a name="example"></a>Örnek  
 Bu tür bir yardımcı programı oluşturmak için önemli adımlar aşağıdaki gibidir.  
  
1. Tüm yazdırma sunucularının bir listesini alın.  
  
2. Kendi yazdırma sorgulamak için sunucular üzerinden döngü.  
  
3. Sunucu döngüsünün her geçişinde sunucunun tüm kuyruklar üzerinden döngü ve kuyruk şu anda çalışmadığını gösterebilir her bir özellik okuyun.  
  
 Aşağıdaki kod parçacıkları dizisidir. Kolaylık olması için bu örnek, yazdırma sunucularını CRLF ayrılmış bir listesi olduğunu varsayar. Değişken `fileOfPrintServers` olduğu bir <xref:System.IO.StreamReader> bu dosya için nesne. Her bir sunucu adı, kendi satırında olduğundan, tüm çağrısı <xref:System.IO.StreamReader.ReadLine%2A> sonraki sunucunun adını alır ve taşır <xref:System.IO.StreamReader>'s imleci sonraki satırın başlangıcına.  
  
 Dış döngü içinde kod oluşturur bir <xref:System.Printing.PrintServer> nesne en yeni yazdırma sunucusunu ve uygulama sunucusuna yönetici haklarına sahip olduğunu belirtir.  
  
> [!NOTE]
>  Çok sunucu varsa, kullanarak performansı artırabilirsiniz <xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> oluşturucular yalnızca gerek seçeceğiz özelliklerini başlatır.  
  
 Ardından örnekte <xref:System.Printing.PrintServer.GetPrintQueues%2A> tüm sunucuların bir koleksiyonunu oluşturmak üzere kuyruğa alır ve bu bloblarda döngü başlatır günceller. Bu iç döngü, iki yolla yazıcının durumu denetleme, karşılık gelen bir dallandırma yapısını içerir:  
  
-   Bayraklarını edinebilirsiniz <xref:System.Printing.PrintQueue.QueueStatus%2A> tür özelliği <xref:System.Printing.PrintQueueStatus>.  
  
-   Her bir ilgili özellik gibi edinebilirsiniz <xref:System.Printing.PrintQueue.IsOutOfPaper%2A>, ve <xref:System.Printing.PrintQueue.IsPaperJammed%2A>.  
  
 Bu örnekte, her iki yöntem gösterir, böylece kullanıcı daha önce hangi metodu kullanmak için istenir ve bayraklarını kullanmak istiyordu, "y" ile yanıt verdi <xref:System.Printing.PrintQueue.QueueStatus%2A> özelliği. İki yöntemden biriyle ayrıntıları için aşağıya bakın.  
  
 Son olarak, sonuçları kullanıcıya gösterilir.  
  
 [!code-cpp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#surveyqueues)]
 [!code-csharp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#surveyqueues)]
 [!code-vb[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#surveyqueues)]  
  
 Bayraklarını kullanarak yazıcı durumunu denetlemek için <xref:System.Printing.PrintQueue.QueueStatus%2A> özelliği, ilgili her bayrağı ayarlanmış olup olmadığını görmek için denetleyin. Bir bit bit bayrakları kümesi içinde ayarlanmış olup olmadığını görmek için standart bayrakları kümesini tek bir işlenen ve diğer bayrağını kendisini olarak bir mantıksal AND işlemini gerçekleştirmek için yoludur. En fazla bayrağı ayarlayın, mantıksal sonucunu bir bit varsa ve bu yana aynı söz konusu bit ayarlanır. Bunu veya olduğunu bulmak için yalnızca sonuç mantıksal AND bayrağı ile karşılaştırın. Daha fazla bilgi için <xref:System.Printing.PrintQueueStatus>, [& işleci (C# başvuru)](~/docs/csharp/language-reference/operators/and-operator.md), ve <xref:System.FlagsAttribute>.  
  
 Kod biti ayarlanmış her öznitelik için bir bildirim kullanıcıya sunulan raporun son hali ekler. ( **ReportAvailabilityAtThisTime** kod sonunda çağrılan yöntem aşağıda ele alınmıştır.)  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueattributes)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueattributes)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueattributes)]  
  
 Her bir özellik kullanarak yazıcı durumunu denetlemek için yalnızca her bir özellik okuma ve özellik ise, kullanıcıya sunulan son rapora Not ekleme `true`. ( **ReportAvailabilityAtThisTime** kod sonunda çağrılan yöntem aşağıda ele alınmıştır.)  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueproperties)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueproperties)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueproperties)]  
  
 **ReportAvailabilityAtThisTime** durumda kuyruğun geçerli günün saatini kullanılabilir olup olmadığını belirlemek gereken yöntemini oluşturuldu.  
  
 Yöntemi, hiçbir şey yapmaz, <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> ve <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> özellikleri eşit; çünkü bu durumda yazıcıyı her zaman kullanılabilir. Farklı olmaları durumunda yöntemi olduğundan toplam dakika son gece yarısı dönüştürülmesi gereken geçerli saati alır <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> ve <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> özellikleri <xref:System.Int32>dakika-sonra-gece yarısı temsil eden değil s <xref:System.DateTime> nesneleri. Son olarak, yöntem geçerli saati "kadar" kez başlangıç arasında olup olmadığını denetler.  
  
 [!code-cpp[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#usingstartanduntiltimes)]
 [!code-csharp[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#usingstartanduntiltimes)]
 [!code-vb[PrinterStatusSurvey#UsingStartAndUntilTimes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#usingstartanduntiltimes)]  
  
## <a name="see-also"></a>Ayrıca bkz.

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
- [& İşleci (C# Başvurusu)](~/docs/csharp/language-reference/operators/and-operator.md)
- [WPF'deki Belgeler](documents-in-wpf.md)
- [Yazdırmaya Genel Bakış](printing-overview.md)
