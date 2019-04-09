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
ms.openlocfilehash: dab836af8ba3d177719d910142cd93f8f6de0002
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59099865"
---
# <a name="how-to-discover-whether-a-print-job-can-be-printed-at-this-time-of-day"></a>Nasıl yapılır: Günün Bu Saatinde Yazdırmanın Yapılıp Yapılmayacağını Keşfetme
Yazdırma sıralarını her zaman günde 24 saat kullanılabilir değil. Günün belirli zamanlarında kullanılamaz duruma getirmek için ayarlanabilir başlangıç ve bitiş zamanı özellikleri sahiptirler. Bu özellik, örneğin, belirli bir bölüm 17: 00 sonra özel kullanım için bir yazıcı ayırmak için kullanılabilir. Bu bölüm Kullan yazıcı diğer departmanlardan bakım farklı bir sıra yoktur. Sıra diğer bölümler için 17: 00 sonra kullanılamaz olarak ayarlanması, ayrıcalıklı bölümün sırası olarak ayarlanması sırada her kullanılabilir zaman.  
  
 Ayrıca, yazdırma işlerini kendilerini yalnızca bir belirtilen bir zaman aralığı içinde yazdırılabilir olacak şekilde ayarlanabilir.  
  
 <xref:System.Printing.PrintQueue> Ve <xref:System.Printing.PrintSystemJobInfo> sınıfları ortaya çıkarılan [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] uzaktan bir yazdırma işi şu anda belirli bir kuyruğa yazdırabilir olup olmadığını denetlemek için Microsoft .NET Framework'ü bir yol sağlar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir yazdırma işi sorunlarını tanılayabilirsiniz bir örnektir.  
  
 Aşağıdaki şekilde bu tür bir işlev için iki ana adım vardır.  
  
1.  Okuma <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> ve <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> özelliklerini <xref:System.Printing.PrintQueue> geçerli saati bunlar arasında olup olmadığını belirlemek için.  
  
2.  Okuma <xref:System.Printing.PrintSystemJobInfo.StartTimeOfDay%2A> ve <xref:System.Printing.PrintSystemJobInfo.UntilTimeOfDay%2A> özelliklerini <xref:System.Printing.PrintSystemJobInfo> geçerli saati bunlar arasında olup olmadığını belirlemek için.  
  
 Ancak zorluklar bu özellikleri olmayan zorluk ortaya çıkan <xref:System.DateTime> nesneleri. Bunun yerine oldukları <xref:System.Int32> gece yarısından itibaren dakika sayısı arttıkça günün saatini express nesneleri. Ayrıca, bu gece yarısı geçerli saat dilimi ancak gece yarısı UTC (Eşgüdümlü Evrensel Saat) değil.  
  
 Statik yöntemini ilk kod örneği sunar **ReportQueueAndJobAvailability**, hangi geçirilen bir <xref:System.Printing.PrintSystemJobInfo> ve iş şu anda yazdırabilir olup olmadığını belirlemek için yardımcı yöntemler çağırır ve değil, ne zaman yazdırabilirsiniz. Dikkat bir <xref:System.Printing.PrintQueue> yöntemine geçirilir. Bunun nedeni, <xref:System.Printing.PrintSystemJobInfo> kuyrukta bir başvuru içeriyor, <xref:System.Printing.PrintSystemJobInfo.HostingPrintQueue%2A> özelliği.  
  
 İkincil yöntemler Aşırı yüklenen dahil **ReportAvailabilityAtThisTime** alabilen yöntemi bir <xref:System.Printing.PrintQueue> veya <xref:System.Printing.PrintSystemJobInfo> bir parametre olarak. Ayrıca bir **TimeConverter.ConvertToLocalHumanReadableTime**. Bu yöntemlerin tümü, aşağıda ele alınmıştır.  
  
 **ReportQueueAndJobAvailability** yöntemi, kuyruk veya yazdırma işi şu anda kullanılabilir olup olmadığını kontrol ederek başlar. Bunlardan birini kullanılamıyorsa, ardından bakar sıranın kullanılamaz. Kullanılabilir durumda değilse, yöntem bu olgu ve ne zaman sıranın tekrar kullanılabilir hale gelecektir zaman bildirir. Ardından işin denetler ve kullanılabilir durumda değilse, sonraki açışınızda rapor yazdırabileceği sırasında yazdırabilirsiniz. Son olarak, yöntem, işin ne zaman yazdırabilir en erken zamanı raporlar. Sonraki iki kez budur.  
  
-   Yazdırma sırasını sonraki kullanılabilir olduğunda zaman.  
  
-   Yazdırma işi sonraki kullanılabilir olduğunda zaman.  
  
 Saatlerinde bildirirken <xref:System.DateTime.ToShortTimeString%2A> yöntemi olarak da adlandırılır çünkü bu yöntem, yıl, ay ve gün çıktısından bastırır. Belirli bir yıl, ay ve gün için yazdırma sırası ya da bir yazdırma işi kullanılabilirliğini kısıtlayamazsınız.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#reportqueueandjobavailability)]
 [!code-csharp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#reportqueueandjobavailability)]
 [!code-vb[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#reportqueueandjobavailability)]  
  
 İki overloads biri **ReportAvailabilityAtThisTime** yöntemi yalnızca bunların geçirilen türler hariç aynıdır <xref:System.Printing.PrintQueue> sürümü aşağıda sunulur.  
  
> [!NOTE]
>  Neden bir genel yöntem yöntem türü dışında aynı olması, soru başlatır **ReportAvailabilityAtThisTime\<T >**. Böyle bir yöntemi olan bir sınıf olması gerekirdi nedeni **StartTimeOfDay** ve **UntilTimeOfDay** yöntemi çağıran özellikleri, ancak genel bir yöntem yalnızca sınırlı bir tek bir sınıf ve ortak tek sınıf <xref:System.Printing.PrintQueue> ve <xref:System.Printing.PrintSystemJobInfo> devralma ağacıdır <xref:System.Printing.PrintSystemObject> gibi özellikleri vardır.  
  
 **ReportAvailabilityAtThisTime** yöntemi (aşağıdaki kod örneğinde gösterilen) başlar başlatarak bir <xref:System.Boolean> sentinel değişkenine `true`. İçin sıfırlanır `false`, kuyruk yoksa.  
  
 Ardından, yöntemi olup olmadığını denetler başlangıç ve "kadar" kez aynıdır. Böyle bir durumda, yöntem döndürecek şekilde sıranın her zaman kullanılabilir `true`.  
  
 Sıranın her zaman kullanılabilir durumda değilse, statik kullanmaktadır <xref:System.DateTime.UtcNow%2A> özelliği olarak geçerli zamanı almak için bir <xref:System.DateTime> nesne. (Yerel saat çünkü ihtiyacımız yok <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> ve <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> özelliklerdir kendilerini UTC saati.)  
  
 Ancak, bu iki özellik olmayan <xref:System.DateTime> nesneleri. Bunlar <xref:System.Int32>zamanı dakika sonra UTC gece sayıda ifade s. Biz dönüştürmek zorunda bizim <xref:System.DateTime> dakika sonra gece yarısına nesne. Tamamlandığında, yöntemi yalnızca "şimdi olmadığını" görmek için "kadar" false "şimdi ise" sentinel arasında iki kez değildir ve sentinel döndürür kümeleri kez sıranın başlangıç arasında denetler.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#printqueuestartuntil)]
 [!code-csharp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#printqueuestartuntil)]
 [!code-vb[DiagnoseProblematicPrintJob#PrintQueueStartUntil](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#printqueuestartuntil)]  
  
 **TimeConverter.ConvertToLocalHumanReadableTime** yöntemi (aşağıdaki kod örneğinde gösterilen) tartışma kısa, bu nedenle, Microsoft .NET Framework ile sunulan tüm yöntemleri kullanamaz. Çift dönüştürme görevi yöntemi vardır: dakika sonra gece yarısı ifade eden bir tamsayı olması gerekir ve bir kullanıcı tarafından okunabilen saate dönüştürün ve bu yerel saate dönüştürmeniz gerekir. Bu ilk oluşturarak gerçekleştirir bir <xref:System.DateTime> ve sonra kullanan gece yarısı olarak ayarlıdır nesne <xref:System.DateTime.AddMinutes%2A> yöntemine iletilmiş dakika eklemek için yöntemi. Bu yeni bir döndürür <xref:System.DateTime> metoduna geçirildi özgün zamanı ifade. <xref:System.DateTime.ToLocalTime%2A> Yöntemi sonra yerel saat olarak bu dönüştürür.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#TimeConverter](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#timeconverter)]
 [!code-csharp[DiagnoseProblematicPrintJob#TimeConverter](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#timeconverter)]
 [!code-vb[DiagnoseProblematicPrintJob#TimeConverter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#timeconverter)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.DateTime>
- <xref:System.Printing.PrintSystemJobInfo>
- <xref:System.Printing.PrintQueue>
- [WPF'deki Belgeler](documents-in-wpf.md)
- [Yazdırmaya Genel Bakış](printing-overview.md)
