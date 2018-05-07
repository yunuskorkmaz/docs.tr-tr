---
title: Mutlak gecikmesi
ms.date: 03/30/2017
ms.assetid: b483139a-39bb-4560-8003-8969a8fc2cd1
ms.openlocfilehash: 3a104f6b879e9cdc899bad2201ad1ed320a38a2d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="absolute-delay"></a>Mutlak gecikmesi
Bu örnek için ana senaryo belirtilen kadar gecikme olduğunu <xref:System.DateTime> dayanıklı zamanlayıcılar bir iş akışı uygulamasında kullanma. Bu, yerleşik kullanmaktan farklı değildir <xref:System.Activities.Statements.Delay> gibi bu etkinlik yalnızca izni verdiği için gecikme bir verilen <xref:System.TimeSpan> (veya dakika/saniye).  
  
 Bazı gerçekçi senaryolar şunlardır Bu ayrım yapmak isteyebilirsiniz:  
  
1.  Bir posta hataları siz yapmadıysanız emin olmak 30 saniye gönderme geciktirmek istersiniz.  
  
2.  Gereğinden fazla olan ve tüm, posta kadar normal iş saatleri (örneğin 8: 00) geciktirmek istersiniz.  
  
## <a name="demonstrates"></a>Gösteriler  
  
1.  <xref:System.Activities.Statements.DurableTimerExtension> Mutlak gecikme uygulamak için  
  
2.  Kalıcılık kullanarak kurmanız <xref:System.Activities.WorkflowApplication> dayanıklı zamanlayıcılar için  
  
3.  Kullanımı <xref:System.Activities.NativeActivity%601> genişletilebilirlik noktaları kullanma  
  
4.  Kullanımı <xref:System.Activities.CodeActivity%601> SendEmail etkinliği içinde  
  
5.  <xref:System.Activities.Statements.Delay>  
  
6.  Yalnızca XAML iş akışı  
  
 Bu örnek nasıl alan içinde özel bir aktivite oluşturulduğunu gösteren bir <xref:System.DateTime> ve gecikme süresini kaydetmek için dayanıklı zamanlayıcılar kullanır. Dayanıklı zamanlayıcılar kullanırken kullanmalısınız bir <xref:System.Activities.NativeActivity> bu yer işaretinin Zamanlayıcı uzantısı ile kaydetmek ihtiyaç duyacağınız bir yer işareti oluşturmak için. Dayanıklı Zamanlayıcı süresi dolduğunda, bu örnekteki `OnTimerExpired` yöntemi çağrılır. Zamanlayıcı uzantısı'nda eklediğiniz emin olun <xref:System.Activities.NativeActivity%601.CacheMetadata%2A> bu bilgilerle çalışma zamanı sağlama emin olmak için olay. Yalnızca diğer uygulama dönüştürmek için mantığı uygulamanız gerekir olup <xref:System.DateTime> için <xref:System.TimeSpan>dayanıklı zamanlayıcılar yalnızca sürer gibi bir <xref:System.DateTime>. Küçük lapse doğruluk yaparak yoktur  
  
> [!NOTE]
>  Dönüştürme tarafından doğruluğu küçük kaybı olan <xref:System.DateTime> için <xref:System.TimeSpan>.  
  
 Bu örnek ayrıca kalıcılığını etkinleştirmek nasıl gösteren bir <xref:System.Activities.WorkflowApplication>. Bu belirli bir örnek için biz, iş akışı veri kalıcılığı veritabanına süresi dolacak şekilde Zamanlayıcı için beklenirken boşta kalma süresi sırasında bellekten kaldırılacak dayanıklı zamanlayıcılar kullanılarak. Bu uygulama, diğer Kalıcılık eylemler için de kullanılabilir. Bu örnek, iş akışı örnekleri için veri kalıcı hale getirmek için örnek deposuna oluşturma ve SQL Server ile kalıcılığı bağlantı dizesini ayarlamak nasıl gösterir. Mantığı, iş akışı örneği runnable sağlayan bir olay tetiklenir sonra iş akışını sürdürmek nasıl sağlanır.  
  
 Bu örnek adım gibi yerleşik gecikme başlar ve tamamlar, hangi sırayla zaman bir e-posta gönderilmesine neden olur görürsünüz. Buradan, AbsoluteDelay etkinlik belirtilen kadar durdurulur <xref:System.DateTime> (veya 0 saniye varsa <xref:System.DateTime> süresi doldu) hangi sırayla gönderecek sona erme bağlı bir e-posta çıkışı. Bu iki farklı kullanım yerleşik gösterir <xref:System.Activities.Statements.Delay> AbsoluteDelay aktivite kullanarak karşı işlevselliği.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  SQL Server Express (veya sonrası) makinenize yüklü olduğundan emin olun  
  
2.  (WF/Basic/Services/AbsoluteDelay/CS) Setup.cmd Çalıştır bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] komut istemi AbsoluteDelaySampleDB veritabanı oluşturma, Kalıcılık şema oluşturun ve kalıcılığı mantığı oluşturun.  
  
3.  Çözümde açmak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
4.  Gecikme etkinliğinde süreyi belirtin.  
  
5.  ExpirationTime AbsoluteDelay etkinliğinde belirtin.  
  
6.  SendMail etkinliğinde SendMailTo, SendMailFrom, SendMailSubject, SendMailBody ve SmtpHost alanları güncelleştirin.  
  
    > [!NOTE]
    >  Geçerli bir SMTP konak girmezseniz, uygulama bir SMTP özel durum oluşturur.  
  
7.  Seçerek çözümü derleme **yapı**, **yapı çözümü**.  
  
8.  Tuşlarına basarak çözümü çalıştırın **F5**.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\AbsoluteDelay`
