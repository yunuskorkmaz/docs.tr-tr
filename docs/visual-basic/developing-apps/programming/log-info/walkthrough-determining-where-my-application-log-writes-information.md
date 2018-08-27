---
title: My.Application.Log (Visual Basic) bilgileri nereye yazdığını belirleme
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, output location
- output, application log location
- My.Application.Log object, outpout location
- event logs, determining output location
- application event logs, output location
- applications [Visual Basic], output location
ms.assetid: 5b70143a-7741-45f2-ae1d-03324a3a4189
ms.openlocfilehash: fa177fa1f07c52d900f57e5bf61c967f06203c4f
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2018
ms.locfileid: "42908231"
---
# <a name="walkthrough-determining-where-myapplicationlog-writes-information-visual-basic"></a>İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme (Visual Basic)
`My.Application.Log` Nesne için birkaç günlük dinleyicileri bilgileri yazabilirsiniz. Günlük dinleyicileri bilgisayarın yapılandırma dosyası tarafından yapılandırılır ve bir uygulamanın yapılandırma dosyası tarafından geçersiz kılınabilir. Bu konu başlığı altında varsayılan ayarları ve uygulama ayarlarını belirlemek nasıl açıklar.  
  
 Varsayılan çıkış konumları hakkında daha fazla bilgi için bkz. [uygulama günlükleriyle çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).  
  
### <a name="to-determine-the-listeners-for-myapplicationlog"></a>My.Application.Log için dinleyicileri belirlemek için  
  
1.  Derlemenin yapılandırma dosyasını bulun. Derleme geliştiriyorsanız app.config dosyasında Visual Studio'dan erişebilirsiniz **Çözüm Gezgini**. Aksi takdirde, yapılandırma dosyası adı "ile .config" eklenmiş derlemenin adıdır ve derleme olarak aynı dizinde bulunur.  
  
    > [!NOTE]
    >  Her derleme, bir yapılandırma dosyası vardır.  
  
     Yapılandırma dosyasını bir XML dosyasıdır.  
  
2.  Bulun `<listeners>` bölümünde `<source>` ile bölümünde `name` "DefaultSource bulunan", öznitelik `<sources>` bölümü. `<sources>` Bölümünde bulunan `<system.diagnostics>` bölümünde, üst düzey `<configuration>` bölümü.  
  
     Bu bölümler mevcut sonra bilgisayarın yapılandırma dosyası yapılandırabilirsiniz `My.Application.Log` günlük dinleyicileri. Aşağıdaki adımlarda, bilgisayar yapılandırma dosyasını tanımlar belirleme açıklanmıştır:  
  
    1.  Bilgisayar bir machine.config dosyasını bulun. Genellikle, bulunur *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* dizin, burada `SystemRoot` işletim sistemi dizin ve `frameworkVersion` sürümü [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].  
  
         Machine.config ayarlarında bir uygulamanın yapılandırma dosyası tarafından geçersiz kılınabilir.  
  
         Aşağıda listelenen isteğe bağlı öğeler mevcut değilse bunları oluşturabilirsiniz.  
  
    2.  Bulun `<listeners>` bölümünde `<source>` ile bölümünde `name` "DefaultSource" özniteliğini `<sources>` bölümünde `<system.diagnostics>` bölümünde, üst düzey `<configuration>` bölümü.  
  
         Bu bölüm yoksa, ardından `My.Application.Log` yalnızca varsayılan günlük dinleyicileri sahiptir.  
  
3.  Bulun <`add>` öğelerinde <`listeners>` bölümü.  
  
     Bu öğeleri eklemek için adlandırılmış günlük dinleyicileri `My.Application.Log` kaynak.  
  
4.  Bulun `<add>` öğeleri içinde günlük dinleyicileri adlarıyla `<sharedListeners>` bölümünde `<system.diagnostics>` bölümünde, üst düzey `<configuration>` bölümü.  
  
5.  Paylaşılan dinleyiciler birçok tür için burada verileri dinleyici yönlendirir açıklaması dinleyicinin başlatma verilerini içerir:  
  
    -   A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> dinleyicisi giriş açıklandığı bir dosyayı günlüğe yazar.  
  
    -   A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> dinleyici bilgileri tarafından belirtilen bilgisayarın olay günlüğüne yazdığı `initializeData` parametresi. Olay günlüğünü görüntülemek için kullanabileceğiniz **Sunucu Gezgini** veya **Windows Olay Görüntüleyicisi'ni**. Daha fazla bilgi için [.NET Framework ETW olayları](../../../../framework/performance/etw-events.md).  
  
    -   <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> Ve <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> dinleyicileri yazma belirtilen dosyaya `initializeData` parametresi.  
  
    -   A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> dinleyici komut satırı konsola yazar.  
  
    -   Burada günlük dinleyicileri diğer tür bilgilerini yazma hakkında daha fazla bilgi için bu türün belgelerine bakın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 <xref:System.Diagnostics.DelimitedListTraceListener>  
 <xref:System.Diagnostics.XmlWriterTraceListener>  
 <xref:System.Diagnostics.ConsoleTraceListener>  
 <xref:System.Diagnostics>  
 [Uygulama Günlükleriyle Çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [Nasıl Yapılır: Günlük Özel Durumları](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)  
 [Nasıl Yapılır: Günlük İletileri Yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)  
 [İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)  
 [.NET Framework'te ETW Olayları](../../../../framework/performance/etw-events.md)  
 [Sorun Giderme: Günlük Dinleyicileri](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)
