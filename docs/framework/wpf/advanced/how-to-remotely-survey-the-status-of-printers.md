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
# <a name="how-to-remotely-survey-the-status-of-printers"></a>Nasıl yapılır: Uzaktan Yazıcıların Durumunu Araştırma
Orta ve büyük şirketlerde herhangi bir zamanda, kağıt sıkıştı veya kağıt kalmadı ya da başka bir sorun olması nedeniyle çalışmayan birden çok yazıcı olabilir. Microsoft .NET Framework API 'Lerinde kullanıma sunulan zengin yazıcı özellikleri kümesi, yazıcıların durumlarının hızlı bir anketini gerçekleştirmek için bir yol sağlar.  
  
## <a name="example"></a>Örnek  
 Bu tür bir yardımcı program oluşturmak için önemli adımlar aşağıda verilmiştir.  
  
1. Tüm yazdırma sunucularının bir listesini alın.  
  
2. Yazdırma kuyruklarını sorgulamak için sunucular aracılığıyla döngü gerçekleştirin.  
  
3. Sunucu döngüsünün her geçişinde, tüm sunucu kuyrukları boyunca ilerleyin ve kuyruğun Şu anda çalışmadığını gösterebilen her bir özelliği okuyun.  
  
 Aşağıdaki kod bir dizi kod parçacıdır. Kolaylık olması için bu örnek, yazdırma sunucularının CRLF ile ayrılmış bir listesi olduğunu varsayar. Değişken `fileOfPrintServers` , bu dosya <xref:System.IO.StreamReader> için bir nesnedir. Her sunucu adı kendi satırında olduğundan, herhangi bir çağrısı <xref:System.IO.StreamReader.ReadLine%2A> sonraki sunucunun adını alır ve imleci sonraki satırın başlangıcına <xref:System.IO.StreamReader>taşıdır.  
  
 Dış döngü içinde, kod en son yazdırma sunucusu <xref:System.Printing.PrintServer> için bir nesne oluşturur ve uygulamanın sunucuda yönetici haklarına sahip olduğunu belirtir.  
  
> [!NOTE]
> Çok sayıda sunucu varsa, yalnızca ihtiyacınız olan özellikleri başlatacak <xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> oluşturucuları kullanarak performansı artırabilirsiniz.  
  
 Örnek daha sonra tüm <xref:System.Printing.PrintServer.GetPrintQueues%2A> sunucu sıralarının bir koleksiyonunu oluşturmak için kullanır ve bunlar üzerinden döngüye geçer. Bu iç döngüde, bir yazıcının durumunu denetlemenin iki yolu ile ilgili bir dallanma yapısı bulunur:  
  
- <xref:System.Printing.PrintQueue.QueueStatus%2A> Türünde<xref:System.Printing.PrintQueueStatus>olan özelliğinin bayraklarını okuyabilirsiniz.  
  
- <xref:System.Printing.PrintQueue.IsOutOfPaper%2A> Ve<xref:System.Printing.PrintQueue.IsPaperJammed%2A>gibi ilgili her özelliği okuyabilirsiniz.  
  
 Bu örnekte her iki yöntem de gösterilmektedir. bu nedenle, Kullanıcı daha önce hangi yöntemin kullanılacağı ve <xref:System.Printing.PrintQueue.QueueStatus%2A> özelliğin bayraklarını kullanmak istiyorlarsa "y" ile yanıt veren bir yöntem olarak istenir. İki yöntemin ayrıntıları için aşağıya bakın.  
  
 Son olarak, sonuçlar kullanıcıya sunulur.  
  
 [!code-cpp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#surveyqueues)]
 [!code-csharp[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#surveyqueues)]
 [!code-vb[PrinterStatusSurvey#SurveyQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#surveyqueues)]  
  
 <xref:System.Printing.PrintQueue.QueueStatus%2A> Özelliğin bayraklarını kullanarak yazıcı durumunu denetlemek için, ayarlanmış olup olmadığını görmek için ilgili her bayrağı kontrol edersiniz. Bir bit bayrakları kümesinde bir bit ayarlanmış olup olmadığını görmenin standart yolu, bir işlenen olarak bayrak kümesi ve diğerinin kendisi olarak bir mantıksal ve işlem gerçekleştirmesidir. Bayrağın kendisi yalnızca bir bit kümesine sahip olduğundan, mantıksal ve bu, en çok, aynı bitin ayarlandığı bir sonucudur. Olup olmadığını öğrenmek için, mantıksal ve yalnızca bayrağın sonucunu karşılaştırın. Daha fazla bilgi için bkz <xref:System.Printing.PrintQueueStatus>. [& işleci (C# başvuru)](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)ve. <xref:System.FlagsAttribute>  
  
 Biti ayarlanan her öznitelik için, kod kullanıcıya sunulacak son rapora bir bildirim ekler. (Kodun sonunda çağrılan **ReportAvailabilityAtThisTime** yöntemi aşağıda ele alınmıştır.)  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueattributes)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueattributes)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueattributes)]  
  
 Her bir özelliği kullanarak yazıcı durumunu denetlemek için, her bir özelliği okumanız ve son rapora, özelliği ise `true`kullanıcıya sunulacak bir Note eklemeniz yeterlidir. (Kodun sonunda çağrılan **ReportAvailabilityAtThisTime** yöntemi aşağıda ele alınmıştır.)  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueproperties)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueproperties)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueproperties)]  
  
 **ReportAvailabilityAtThisTime** yöntemi, kuyruğun günün geçerli saatinde kullanılabilir olup olmadığını belirlemeniz gereken durumlarda oluşturulmuştur.  
  
 , <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> Ve<xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> özellikleri eşitse yöntem hiçbir şey yapmaz; çünkü bu durumda yazıcı her zaman kullanılabilir durumda olur. Bu değerler farklıysa, yöntemi son gece yarısı geçen süreyi <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> alır, çünkü ve <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> özellikleri <xref:System.Int32>, hafta içi <xref:System.DateTime> dakikaları temsil ettiğinden nesneyi. Son olarak yöntemi, geçerli saatin başlangıç ve "Until" zamanları arasında olup olmadığını denetler.  
  
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
- [& Işleci (C# başvuru)](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-)
- [WPF'deki Belgeler](documents-in-wpf.md)
- [Yazdırmaya Genel Bakış](printing-overview.md)
