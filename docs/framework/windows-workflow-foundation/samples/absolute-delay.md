---
title: Mutlak gecikme
ms.date: 03/30/2017
ms.assetid: b483139a-39bb-4560-8003-8969a8fc2cd1
ms.openlocfilehash: 30719a4340b738a7462584c4dca00f6d5d90ac72
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486108"
---
# <a name="absolute-delay"></a>Mutlak gecikme
Bu örnek için ana senaryo kadar belirtilen bir gecikme olduğunu <xref:System.DateTime> dayanıklı zamanlayıcılar bir iş akışı uygulamasında kullanma. Bu yerleşik kullanımından farklı <xref:System.Activities.Statements.Delay> etkinliği olarak bu işlem yalnızca sonrasında için gecikme bir verilen <xref:System.TimeSpan> (veya kaç dakika/saniye).  
  
 Bazı gerçek durum senaryolarının şunlar Bu ayrım yapmak isteyebilirsiniz:  
  
1.  Hataları yapmadım emin olmak 30 saniye için bir e-posta göndermeye gecikme istiyorsunuz.  
  
2.  Gereğinden fazla ve tüm postalarınızı kadar normal çalışma saatleri (örneğin 8: 00) geciktirmek istiyorsanız.  
  
## <a name="demonstrates"></a>Gösteriler  
  
1.  <xref:System.Activities.Statements.DurableTimerExtension> Mutlak gecikme uygulamak için  
  
2.  Kalıcılık kullanarak ayarı <xref:System.Activities.WorkflowApplication> dayanıklı zamanlayıcılar için  
  
3.  Kullanım <xref:System.Activities.NativeActivity%601> genişletilebilirlik noktaları kullanma  
  
4.  Kullanım <xref:System.Activities.CodeActivity%601> SendEmail etkinliği içinde  
  
5.  <xref:System.Activities.Statements.Delay>  
  
6.  Yalnızca XAML iş akışı  
  
 Bu örnek alan olarak özel etkinlik oluşturma işlemini gösterir. bir <xref:System.DateTime> ve dayanıklı zamanlayıcılar gecikme süresi kaydetmek için kullanır. Dayanıklı zamanlayıcılar kullanırken kullanmalısınız bir <xref:System.Activities.NativeActivity> bu yer işaretinin Zamanlayıcı uzantısı ile kaydetmek ihtiyacınız olacak şekilde bir yer işareti oluşturmak için. Dayanıklı süreölçerdeki Süre dolduğunda, bu örnekteki `OnTimerExpired` yöntemi çağrılır. Zamanlayıcı uzantı eklemekte olduğunuz emin <xref:System.Activities.NativeActivity%601.CacheMetadata%2A> bu bilgilerle çalışma zamanı sağlama emin olmak için olay. Dönüştürmek için mantığını gerekecektir yalnızca diğer uygulama ayrıntısı olduğunu <xref:System.DateTime> için <xref:System.TimeSpan>dayanıklı zamanlayıcılar yalnızca almak gibi bir <xref:System.DateTime>. Küçük lapse doğruluk yaparak unutmayın  
  
> [!NOTE]
>  Dönüştürme göre küçük bir doğruluk kaybı olan <xref:System.DateTime> için <xref:System.TimeSpan>.  
  
 Bu örnek ayrıca kalıcılığını etkinleştirme gösterir bir <xref:System.Activities.WorkflowApplication>. Bu belirli bir örnek için sizi, iş akışı verileri Kalıcılık veritabanına boşta kalma süresi dolmak üzere Zamanlayıcı için beklenirken sırasında bellekten kaldırılacak dayanıklı zamanlayıcılar kullanacaklardır. Bu uygulama, diğer Kalıcılık eylemler için de kullanılabilir. Bu örnek, SQL Server Kalıcılık bağlantı dizesiyle kurma ve iş akışı örnekleri için verileri kalıcı hale getirmek için örnek deposu oluşturma işlemini gösterir. Mantıksal iş akışı örneği çalıştırılabilir sağlayan bir olay tetiklenir sonra iş akışını sürdürmek nasıl sağlanır.  
  
 Bu örnek adım olarak, yerleşik gecikme başlar ve tamamlar, hangi sırayla zaman gönderilecek e-posta iletisine neden olur görürsünüz. Burada, AbsoluteDelay etkinlik belirtilen kadar durdurulur <xref:System.DateTime> (veya 0 saniye, <xref:System.DateTime> süresi doldu) hangi sırayla göndermek sona erme üzerine bir e-posta. Bu iki farklı kullanım örnekleri yerleşik gösterir <xref:System.Activities.Statements.Delay> AbsoluteDelay etkinlik kullanma ve işlevleri.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  SQL Server Express (veya üzeri), makinenizde yüklü olduğundan emin olun  
  
2.  Setup.cmd (WF/Basic/Services/AbsoluteDelay/CS) içinde çalışan bir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] AbsoluteDelaySampleDB veritabanı oluşturma, kalıcı şema oluşturmak ve Kalıcılık mantığı oluşturmak için bir komut istemi.  
  
3.  Bir çözüm açın [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
4.  Delay etkinlik süreyi belirtin.  
  
5.  ExpirationTime AbsoluteDelay etkinliğinde belirtin.  
  
6.  SendMail etkinliğinde SendMailTo, SendMailFrom SendMailSubject SendMailBody ve SmtpHost alanlarını güncelleştirin.  
  
    > [!NOTE]
    >  Geçerli bir SMTP konağı girmezseniz, uygulama bir SMTP özel durum oluşturur.  
  
7.  Çözüm seçerek yapı **derleme**, **Çözümü Derle**.  
  
8.  Tuşlarına basarak çözümü çalıştırın **F5**.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\AbsoluteDelay`
