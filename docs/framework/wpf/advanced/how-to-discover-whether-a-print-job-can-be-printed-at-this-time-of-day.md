---
title: 'Nasıl yapılır: Günün Bu Saatinde Yazdırmanın Yapılıp Yapılmayacağını Keşfetme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print queues [WPF], timing
- printers [WPF], availability
- print jobs [WPF], timing
ms.assetid: 7e9c8ec1-abf6-4b3d-b1c6-33b35d3c4063
ms.openlocfilehash: 859dc75169e443d07361951692a428507886fa2e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947807"
---
# <a name="how-to-discover-whether-a-print-job-can-be-printed-at-this-time-of-day"></a>Nasıl yapılır: Günün Bu Saatinde Yazdırmanın Yapılıp Yapılmayacağını Keşfetme
Yazdırma kuyrukları her zaman günde 24 saat boyunca kullanılabilir değildir. Bunlar, günün belirli saatlerinde kullanılamaz hale getirmek için ayarlanabilecekleri başlangıç ve bitiş zamanı özelliklerine sahiptirler. Bu özellik, örneğin, 5 P.M. sonra belirli bir departmanın özel kullanımı için bir yazıcı ayırmak üzere kullanılabilir. Bu bölümün, yazıcıya hizmet veren farklı bir kuyruğu vardır. Diğer Departmanlar için sıra 5 P.M. sonra kullanılamaz, ancak sık kırmızı bölüm kuyruğu her zaman kullanılabilir olacak şekilde ayarlanabilir.  
  
 Üstelik, yazdırma işlerinin kendileri yalnızca belirtilen zaman aralığında yazdırılabilir olarak ayarlanabilir.  
  
 Microsoft .net <xref:System.Printing.PrintQueue> Framework <xref:System.Printing.PrintSystemJobInfo> API 'lerinde sunulan ve sınıfları, belirli bir yazdırma işinin geçerli zamanda belirli bir sıraya göre yazdırıp yazdıramayacağını uzaktan denetlemek için bir yol sağlar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir yazdırma işiyle ilgili sorunları tanılamak için bir örnektir.  
  
 Bu tür bir işlev için aşağıdaki gibi iki önemli adım vardır.  
  
1. Geçerli saatin aralarında <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> olup olmadığını öğrenmek <xref:System.Printing.PrintQueue> için öğesinin veözellikleriniokuyun.<xref:System.Printing.PrintQueue.StartTimeOfDay%2A>  
  
2. Geçerli saatin aralarında <xref:System.Printing.PrintSystemJobInfo.UntilTimeOfDay%2A> olup olmadığını öğrenmek <xref:System.Printing.PrintSystemJobInfo> için öğesinin veözellikleriniokuyun.<xref:System.Printing.PrintSystemJobInfo.StartTimeOfDay%2A>  
  
 Ancak bu özelliklerin nesneler olmadığı <xref:System.DateTime> gerçeden karmaşıklıklar ortaya çıkar. Bunun yerine, <xref:System.Int32> günün saatini gece yarısından beri geçen dakika sayısı olarak ifade eden nesnelerdir. Üstelik, bu, geçerli saat diliminde gece yarısı, ancak gece yarısı UTC (Eşgüdümlü Evrensel Saat).  
  
 İlk kod örneği, gönderilen <xref:System.Printing.PrintSystemJobInfo> **ReportQueueAndJobAvailability**statik yöntemini gösterir ve işin geçerli saatte yazdırıp yazdıramayacağını ve ne zaman yazdırılacağını ve ne zaman yazdıramayacağını belirleyen yardımcı yöntemleri çağırır. Yöntemine bir <xref:System.Printing.PrintQueue> yönteminin geçirilmediğine dikkat edin. Bunun nedeni, <xref:System.Printing.PrintSystemJobInfo> öğesinin <xref:System.Printing.PrintSystemJobInfo.HostingPrintQueue%2A> özelliğindeki sıraya bir başvuru içereceğinden oluşur.  
  
 Alt yöntemler, bir <xref:System.Printing.PrintQueue> veya bir <xref:System.Printing.PrintSystemJobInfo> parametresini parametre olarak ele geçirebilen aşırı yüklenmiş **ReportAvailabilityAtThisTime** yöntemini içerir. Ayrıca bir **TimeConverter. ConvertToLocalHumanReadableTime**vardır. Bu yöntemlerin hepsi aşağıda ele alınmıştır.  
  
 **ReportQueueAndJobAvailability** yöntemi, sıranın veya yazdırma işinin Şu anda kullanılabilir olup olmadığını kontrol ederek başlar. Bunlardan biri kullanılamıyorsa, sıranın kullanılamıyor olup olmadığını kontrol eder. Kullanılabilir değilse, yöntemi bu olguyu ve kuyruğun yeniden kullanılabilir olacağı saati raporlar. Ardından işi denetler ve kullanılabilir değilse, bir sonraki sefer, yazdırane zaman zaman dilimi bildirir. Son olarak, yöntemi işin yazdırabileceği en erken zamanı bildirir. Bu, aşağıdaki iki kez daha oluşur.  
  
- Yazdırma sırasının bir sonraki kullanıma hazır olduğu zaman.  
  
- Yazdırma işinin bir sonraki kullanıma hazır olduğu zaman.  
  
 Günün raporlanması sırasında <xref:System.DateTime.ToShortTimeString%2A> yöntem de çağrılır, çünkü bu yöntem çıktısından yıl, ay ve günü bastırır. Bir yazdırma sırasının veya bir yazdırma işinin kullanılabilirliğini belirli yıl, ay veya günlere göre kısıtlayamazsınız.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#reportqueueandjobavailability)]
 [!code-csharp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#reportqueueandjobavailability)]
 [!code-vb[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#reportqueueandjobavailability)]  
  
 **ReportAvailabilityAtThisTime** yönteminin iki aşırı yüklemesi, geçirilen tür haricinde aynıdır, bu nedenle yalnızca <xref:System.Printing.PrintQueue> sürüm aşağıda sunulmuştur.  
  
> [!NOTE]
> Metodun tür hariç özdeş olması, örneğin, örnek **\<ReportAvailabilityAtThisTime T >** genel bir yöntem oluşturmamasının sorusunu oluşturur. Bunun nedeni, bu yöntemin, **StartTimeOfDay** ve yöntemin çağırdığı **UntilTimeOfDay** özelliklerine sahip bir sınıfla sınırlandırılmalıdır, ancak genel bir yöntem yalnızca tek bir sınıfla ve her ikisi için ortak olan tek sınıfla kısıtlanabilir Devralma ağacında Butür<xref:System.Printing.PrintSystemObject>özellikleriyoktur. <xref:System.Printing.PrintQueue> <xref:System.Printing.PrintSystemJobInfo>  
  
 **ReportAvailabilityAtThisTime** yöntemi (Aşağıdaki kod örneğinde sunulan), için <xref:System.Boolean> `true`bir Sentinel değişkeni başlatılarak başlar. Sıra kullanılamıyorsa, olarak `false`sıfırlanır.  
  
 Sonra, yöntemi başlangıç ve "Until" zamanlarının aynı olup olmadığını denetler. Varsa, kuyruk her zaman kullanılabilir olduğundan, yöntemi döndürür `true`.  
  
 Sıra her zaman kullanılabilir değilse, yöntemi geçerli saati bir <xref:System.DateTime.UtcNow%2A> <xref:System.DateTime> nesne olarak almak için static özelliğini kullanır. ( <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> Ve<xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> özellikleri UTC saat içinde olduğundan yerel saate ihtiyacım yoktur.)  
  
 Ancak, bu iki özellik nesne değildir <xref:System.DateTime> . <xref:System.Int32>Bu, saati saat-UTC-gece yarısı olarak ifade ederler. Bu nedenle nesnemizi <xref:System.DateTime> dakika sonra gece yarısından dönüştürmemiz gerekir. Bu işlem tamamlandığında, yöntemi "Şimdi" kuyruğun başlangıç ve "Until" zamanları arasında olup olmadığını denetler, "Şimdi" iki kez değilse Sentinel değerini false olarak ayarlar ve Sentinel değerini döndürür.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#printqueuestartuntil)]
 [!code-csharp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#printqueuestartuntil)]
 [!code-vb[DiagnoseProblematicPrintJob#PrintQueueStartUntil](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#printqueuestartuntil)]  
  
 **TimeConverter. ConvertToLocalHumanReadableTime** yöntemi (Aşağıdaki kod örneğinde sunulan) Microsoft .NET Framework ile tanıtılan herhangi bir yöntemi kullanmaz. bu nedenle, tartışma kısa olur. Yöntemin bir çift dönüştürme görevi vardır: dakika sonra gece yarısından sonra bir tamsayı almalıdır ve bunu insanla okunabilir bir zamana dönüştürür ve bunu yerel saate dönüştürmelidir. Önce gece yarısı UTC olarak ayarlanmış bir <xref:System.DateTime> nesne oluşturarak bunu gerçekleştirir ve ardından yöntemine geçirilen dakikaları eklemek için <xref:System.DateTime.AddMinutes%2A> yöntemini kullanır. Bu, yönteme geçirilen <xref:System.DateTime> özgün saati ifade eden yeni bir ifade döndürür. <xref:System.DateTime.ToLocalTime%2A> Yöntemi daha sonra bunu yerel saate dönüştürür.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#TimeConverter](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#timeconverter)]
 [!code-csharp[DiagnoseProblematicPrintJob#TimeConverter](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#timeconverter)]
 [!code-vb[DiagnoseProblematicPrintJob#TimeConverter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#timeconverter)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.DateTime>
- <xref:System.Printing.PrintSystemJobInfo>
- <xref:System.Printing.PrintQueue>
- [WPF'deki Belgeler](documents-in-wpf.md)
- [Yazdırmaya Genel Bakış](printing-overview.md)
