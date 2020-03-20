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
# <a name="how-to-remotely-survey-the-status-of-printers"></a>Nasıl yapılır: Uzaktan Yazıcıların Durumunu Araştırma
Orta ve büyük şirketlerde herhangi bir zamanda bir kağıt sıkışması veya kağıt veya başka bir sorunlu durum dışında olması nedeniyle çalışmıyor birden fazla yazıcı olabilir. Microsoft .NET Framework API'lerinde ortaya çıkarılan zengin yazıcı özellikleri kümesi, yazıcıların durumları hakkında hızlı bir anket yapmak için bir araç sağlar.  
  
## <a name="example"></a>Örnek  
 Bu tür bir yardımcı program oluşturmak için önemli adımlar aşağıdaki gibidir.  
  
1. Tüm yazdırma sunucularının listesini alın.  
  
2. Yazdırma kuyruklarını sorgulamak için sunucular arasında geçiş yapmayı niçin.  
  
3. Sunucu döngüsünün her geçişinde, sunucunun tüm kuyruklarını iletin ve sıranın şu anda çalışmadığını gösteren her özelliği okuyun.  
  
 Aşağıdaki kod bir dizi parçacıktır. Basitlik için, bu örnek, yazdırma sunucularının CRLF'ye bağlı bir listesi olduğunu varsayar. Değişken `fileOfPrintServers` bu <xref:System.IO.StreamReader> dosya için bir nesnedir. Her sunucu adı kendi satırında olduğundan, <xref:System.IO.StreamReader.ReadLine%2A> herhangi bir çağrı sonraki sunucunun adını alır ve <xref:System.IO.StreamReader>'imleci bir sonraki satırın başına taşır.  
  
 Dış döngü içinde, kod en <xref:System.Printing.PrintServer> son yazdırma sunucusu için bir nesne oluşturur ve uygulamanın sunucuya yönetim haklarına sahip olduğunu belirtir.  
  
> [!NOTE]
> Çok sayıda sunucu varsa, yalnızca gereksinim duyduğunuz <xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> özellikleri ilke açan oluşturucuları kullanarak performansı artırabilirsiniz.  
  
 Örnek daha <xref:System.Printing.PrintServer.GetPrintQueues%2A> sonra sunucunun tüm kuyrukları bir koleksiyon oluşturmak için kullanır ve bunların üzerinden döngü başlar. Bu iç döngü, yazıcının durumunu denetlemenin iki yoluna karşılık gelen bir dallanma yapısı içerir:  
  
- Türünde olan özelliğin <xref:System.Printing.PrintQueue.QueueStatus%2A> bayraklarını <xref:System.Printing.PrintQueueStatus>okuyabilirsiniz.  
  
- Gibi her ilgili özelliği <xref:System.Printing.PrintQueue.IsOutOfPaper%2A>okuyabilirsiniz <xref:System.Printing.PrintQueue.IsPaperJammed%2A>ve .  
  
 Bu örnek, her iki yöntemi de gösterdiğinden, kullanıcıya daha önce hangi yöntemin kullanılacağı sorulmuş ve <xref:System.Printing.PrintQueue.QueueStatus%2A> özelliğin bayraklarını kullanmak isterse "y" ile yanıt verilmiştir. İki yöntemin ayrıntıları için aşağıya bakın.  
  
 Son olarak, sonuçlar kullanıcıya sunulur.  
  
 [!code-cpp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#surveyqueues)]
 [!code-csharp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#surveyqueues)]
 [!code-vb[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#surveyqueues)]  
  
 <xref:System.Printing.PrintQueue.QueueStatus%2A> Özelliğin bayraklarını kullanarak yazıcı durumunu denetlemek için, ayarlı olup olmadığını görmek için ilgili her bayrağı denetlersiniz. Bir bit bit bayrakları kümesi nde ayarlanmış olup olmadığını görmek için standart yolu bir operand ve diğer olarak bayrak kendisi olarak bayrak kümesi ile mantıksal ve işlem gerçekleştirmektir. Bayrağın kendisi yalnızca bir bit kümesine sahip olduğundan, mantıksal VE sonucu, en fazla, aynı bit ayarlanır. Olup olmadığını öğrenmek için, sadece mantıksal ve bayrağın kendisi ile sonucu karşılaştırın. Daha fazla bilgi <xref:System.Printing.PrintQueueStatus>için bkz:& [Operatörü (C# Reference)](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)ve <xref:System.FlagsAttribute>.  
  
 Biti ayarlanmış her öznitelik için kod, kullanıcıya sunulacak son rapora bir bildirim ekler. (Kodun sonunda çağrılan **ReportAvailabilityAtThisTime** yöntemi aşağıda tartışılmıştır.)  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueattributes)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueattributes)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueattributes)]  
  
 Her özelliği kullanarak yazıcı durumunu denetlemek için, her özelliği okumanız ve son rapora, özellik. `true` (Kodun sonunda çağrılan **ReportAvailabilityAtThisTime** yöntemi aşağıda tartışılmıştır.)  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueproperties)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueproperties)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueproperties)]  
  
 Sıranın günün geçerli saatinde kullanılabilir olup olmadığını belirlemeniz gerektiğinde **ReportAvailabilityAtThisTime** yöntemi oluşturuldu.  
  
 Yöntem <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> ve <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> özellikleri eşit ise hiçbir şey yapmaz; çünkü bu durumda yazıcı her zaman kullanılabilir. Farklıysalar, yöntem geçerli zamanı alır ve bu süre gece yarısını geçen <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> toplam <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> dakikaya dönüştürülür, çünkü ve <xref:System.Int32> <xref:System.DateTime> özellikler nesneleri değil, gece yarısından sonra dakikaları temsil eder. Son olarak, yöntem geçerli saatin başlangıç ve "kadar" saatleri arasında olup olmadığını görmek için denetler.  
  
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
- [& Operatörü (C# Referans)](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)
- [WPF'deki Belgeler](documents-in-wpf.md)
- [Yazdırmaya Genel Bakış](printing-overview.md)
