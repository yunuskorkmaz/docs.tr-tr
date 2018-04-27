---
title: 'Nasıl yapılır: Günün Bu Saatinde Yazdırmanın Yapılıp Yapılmayacağını Keşfetme'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print queues [WPF], timing
- printers [WPF], availability
- print jobs [WPF], timing
ms.assetid: 7e9c8ec1-abf6-4b3d-b1c6-33b35d3c4063
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: eef74cfa290614e530fa22a34533c7924d4af1b4
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-discover-whether-a-print-job-can-be-printed-at-this-time-of-day"></a>Nasıl yapılır: Günün Bu Saatinde Yazdırmanın Yapılıp Yapılmayacağını Keşfetme
Yazdırma sıralarını her zaman günde 24 saat için kullanılabilir değil. Günün belirli zamanlarında kullanılamaz duruma getirmek için ayarlanabilir başlangıç ve bitiş zamanı özellikleri sahiptirler. Bu özellik, örneğin, belirli bir bölüm 17: 00 sonra özel kullanım için bir yazıcı ayırmak için kullanılabilir. Bu bölüm Kullan yazıcı diğer departmanlardan daha bakım farklı bir sıra gerekir. Diğer bölümler için sıra 17: 00 sonra kullanılamaz hale gelmesine ayarlanması, ayrıcalıklı bölümün sırası olacak şekilde ayarlanması kullanılabilir hiç uğruyor.  
  
 Ayrıca, yazdırma işleri kendilerini yalnızca bir belirtilen zaman dilimi içinde yazdırılabilir olarak ayarlanabilir.  
  
 <xref:System.Printing.PrintQueue> Ve <xref:System.Printing.PrintSystemJobInfo> sınıfları ortaya çıkarılan [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] uzaktan belirli bir yazdırma işi şu anda üzerinde belirli bir sıradaki yazdırabilir olup olmadığını denetlemek için Microsoft .NET Framework'ü bir yol sağlar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir yazdırma işi sorunları tanılayabilirsiniz bir örnektir.  
  
 Aşağıdaki gibi bu tür bir işlev için iki ana adım vardır.  
  
1.  Okuma <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> ve <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> özelliklerini <xref:System.Printing.PrintQueue> geçerli zamanın aralarında olup olmadığını belirlemek için.  
  
2.  Okuma <xref:System.Printing.PrintSystemJobInfo.StartTimeOfDay%2A> ve <xref:System.Printing.PrintSystemJobInfo.UntilTimeOfDay%2A> özelliklerini <xref:System.Printing.PrintSystemJobInfo> geçerli zamanın aralarında olup olmadığını belirlemek için.  
  
 Ancak zorluklar bu özellikleri olmayan zorluk ortaya çıkan <xref:System.DateTime> nesneleri. Bunun yerine oldukları <xref:System.Int32> günün saatini gece yarısından itibaren dakika sayısı olarak ifade nesneleri. Ayrıca, bu gece geçerli saat dilimi, ancak gece yarısı UTC (Eşgüdümlü Evrensel Saat) içinde değil.  
  
 İlk örnek kod statik yöntemini sunar **ReportQueueAndJobAvailability**, hangi geçirilen bir <xref:System.Printing.PrintSystemJobInfo> ve iş şu anda yazdırabilir olup olmadığını belirlemek için yardımcı yöntemler çağırır ve değil, ne zaman yazdırabilirsiniz. Dikkat bir <xref:System.Printing.PrintQueue> yönteme geçirilen değil. Bunun nedeni, <xref:System.Printing.PrintSystemJobInfo> sırada için referans içeriyor, <xref:System.Printing.PrintSystemJobInfo.HostingPrintQueue%2A> özelliği.  
  
 Bağımlı yöntemlerini aşırı yüklenmiş dahil **ReportAvailabilityAtThisTime** alabilen yöntemi bir <xref:System.Printing.PrintQueue> veya <xref:System.Printing.PrintSystemJobInfo> bir parametre olarak. Ayrıca bir **TimeConverter.ConvertToLocalHumanReadableTime**. Tüm bu yöntemleri aşağıda ele alınmıştır.  
  
 **ReportQueueAndJobAvailability** yöntemi başlar sıranın veya yazdırma işi şu anda kullanılamaz durumda olup olmadığını kontrol ederek. İkisinden biri kullanılamıyorsa, ardından bakar sıranın kullanılamaz. Kullanılabilir durumda değilse, yöntem bu olgu ve ne zaman sıranın yeniden kullanılabilir olacağı zamanı raporlar. Sonra işi denetler ve kullanılabilir durumda değilse, sonraki raporlar yazdırabileceği yazdırabilirsiniz sırasında. Son olarak, yöntem işin ne zaman yazdırabilir erken zamanı raporlar. Bu sonraki iki kez olur.  
  
-   Yazdırma sırasını sonraki kullanılabilir olduğunda süre.  
  
-   Yazdırma işi sonraki kullanılabilir olduğunda süre.  
  
 Saatlerinde bildirilirken <xref:System.DateTime.ToShortTimeString%2A> yöntemi olarak da adlandırılır çünkü bu yöntem yıl, ay ve gün çıktısından bastırır. Bir yazdırma sırası veya yazdırma işi kullanılabilirliğini belirli yıl, ay ve gün için kısıtlayamazsınız.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#reportqueueandjobavailability)]
 [!code-csharp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#reportqueueandjobavailability)]
 [!code-vb[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#reportqueueandjobavailability)]  
  
 İki overloads **ReportAvailabilityAtThisTime** yöntemi yalnızca onlara, geçirilen türü dışında aynı <xref:System.Printing.PrintQueue> sürümü aşağıda sunulur.  
  
> [!NOTE]
>  Örnek bir genel yöntem oluşturmaz neden yöntemleri dışında birbirinin olgu sorunuz başlatır **ReportAvailabilityAtThisTime\<T >**. Bu tür bir yöntem olan bir sınıfı kısıtlı olması gerektiğini nedeni **StartTimeOfDay** ve **UntilTimeOfDay** yöntemini çağırır özellikler, ancak genel yöntem yalnızca olabilir sınırlı bir tek ve ortak yalnızca sınıf <xref:System.Printing.PrintQueue> ve <xref:System.Printing.PrintSystemJobInfo> devralma ağacıdır <xref:System.Printing.PrintSystemObject> gibi özellikleri vardır.  
  
 **ReportAvailabilityAtThisTime** yöntemi (aşağıdaki kod örneğinde sunulan) başlar başlatarak bir <xref:System.Boolean> sentinel değişkenini `true`. İçin sıfırlanır `false`, sıranın kullanılabilir değilse.  
  
 Ardından, yöntem bakar Başlat ve "kadar" kez aynıdır. Olmaları durumunda yöntemi döndürecek şekilde sıranın her zaman kullanılabilir `true`.  
  
 Sıranın her zaman kullanılabilir durumda değilse, statik kullanmaktadır <xref:System.DateTime.UtcNow%2A> geçerli saati olarak alma özelliği bir <xref:System.DateTime> nesnesi. (Yerel saat çünkü ihtiyacımız değil <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> ve <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> özelliklerdir kendilerini UTC saati.)  
  
 Ancak, bu iki özellik olmayan <xref:System.DateTime> nesneleri. Bunlar <xref:System.Int32>zamanı dakika sonra UTC gece sayısı olarak ifade s. Biz dönüştürmeniz gerekir böylece bizim <xref:System.DateTime> dakika sonra gece yarısına nesnesi. Yapıldığında, yöntemi yalnızca "şimdi olup olmadığını" görmek için "kadar" false "şimdi ise" sentinel arasında iki kez değil ve sentinel döndürür kümeleri zamanlarının sıranın başlangıcı arasında olduğunu denetler.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#printqueuestartuntil)]
 [!code-csharp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#printqueuestartuntil)]
 [!code-vb[DiagnoseProblematicPrintJob#PrintQueueStartUntil](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#printqueuestartuntil)]  
  
 **TimeConverter.ConvertToLocalHumanReadableTime** yöntemi (aşağıdaki kod örneğinde sunulan) tartışma kısa olacak şekilde Microsoft .NET Framework ile sunulan tüm yöntemleri kullanmaz. Çift dönüştürme görevi yöntemi vardır: dakika sonra gece yarısı ifade eden bir tamsayı olması gerekir ve okunabilir bir zamana dönüştürmek ve bunu bunu yerel saat dönüştürmeniz gerekir. Bu ilk oluşturarak tamamlanır bir <xref:System.DateTime> ve sonra kullanan gece yarısına ayarlanmış nesne <xref:System.DateTime.AddMinutes%2A> yöntemine iletilmiş dakika ekleme yöntemi. Bu yeni bir döndürür <xref:System.DateTime> yönteme geçirilen özgün zamanı ifade. <xref:System.DateTime.ToLocalTime%2A> Yöntemi sonra yerel saate bu dönüştürür.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#TimeConverter](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#timeconverter)]
 [!code-csharp[DiagnoseProblematicPrintJob#TimeConverter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#timeconverter)]
 [!code-vb[DiagnoseProblematicPrintJob#TimeConverter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#timeconverter)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.DateTime>  
 <xref:System.Printing.PrintSystemJobInfo>  
 <xref:System.Printing.PrintQueue>  
 [WPF'deki Belgeler](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Yazdırmaya Genel Bakış](../../../../docs/framework/wpf/advanced/printing-overview.md)
