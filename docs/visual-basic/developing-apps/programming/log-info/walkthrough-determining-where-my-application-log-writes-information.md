---
title: My.Application.Log bilgileri (Visual Basic) nereye yazdığını belirleme
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Log object, output location
- output, application log location
- My.Application.Log object, outpout location
- event logs, determining output location
- application event logs, output location
- applications [Visual Basic], output location
ms.assetid: 5b70143a-7741-45f2-ae1d-03324a3a4189
caps.latest.revision: 24
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d15dc02f9b5c2728ea447b5a1969ea40753258f9
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="walkthrough-determining-where-myapplicationlog-writes-information-visual-basic"></a>İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme (Visual Basic)
`My.Application.Log` Nesne için birden fazla günlük dinleyicileri bilgileri yazabilirsiniz. Günlük dinleyicileri bilgisayarın yapılandırma dosyası tarafından yapılandırılır ve bir uygulamanın yapılandırma dosyasına göre geçersiz kılınabilir. Bu konu varsayılan ayarları ve uygulamanızın ayarlarını belirleme açıklar.  
  
 Varsayılan çıkış konumları hakkında daha fazla bilgi için bkz: [uygulama günlükleriyle çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).  
  
### <a name="to-determine-the-listeners-for-myapplicationlog"></a>My.Application.Log dinleyicileri belirlemek için  
  
1.  Derlemenin yapılandırma dosyasını bulun. Derleme geliştiriyorsanız, app.config dosyasında Visual Studio'dan erişebilirsiniz **Çözüm Gezgini**. Aksi durumda yapılandırma dosyasının adını ".config" ile eklenen derlemenin adıdır ve derleme aynı dizinde bulunur.  
  
    > [!NOTE]
    >  Her derlemesi bir yapılandırma dosyası içeriyor.  
  
     Yapılandırma dosyasını bir XML dosyasıdır.  
  
2.  Bulun `<listeners>` bölümünde `<source>` ile bölümünde `name` "DefaultSource bulunan", öznitelik `<sources>` bölümü. `<sources>` Bölüm bulunduğu `<system.diagnostics>` bölümünde, üst düzey `<configuration>` bölümü.  
  
     Bu bölümler mevcut sonra bilgisayarın yapılandırma dosyasını yapılandırabilir `My.Application.Log` günlük dinleyicileri. Aşağıdaki adımlar, hangi bilgisayar yapılandırma dosyası tanımlar belirlemek açıklanmaktadır:  
  
    1.  Bilgisayarın machine.config dosyasını bulun. Genellikle, bulunur *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* dizin, burada `SystemRoot` işletim sistemi dizindir ve `frameworkVersion` sürümü [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].  
  
         Machine.config ayarlarında, bir uygulamanın yapılandırma dosyasına göre geçersiz kılınabilir.  
  
         Aşağıda listelenen isteğe bağlı öğeleri yoksa, bunları oluşturabilirsiniz.  
  
    2.  Bulun `<listeners>` bölümünde `<source>` ile bölümünde `name` "DefaultSource" özniteliğini `<sources>` bölümünde `<system.diagnostics>` bölümünde, üst düzey `<configuration>` bölümü.  
  
         Bu bölümler yoksa sonra `My.Application.Log` yalnızca varsayılan günlük dinleyicileri sahiptir.  
  
3.  Bulun <`add>` öğelerinde <`listeners>` bölümü.  
  
     Bu öğeler için adlandırılmış günlük dinleyicileri eklemek `My.Application.Log` kaynak.  
  
4.  Bulun `<add>` öğeleri günlük dinleyicileri adlarıyla `<sharedListeners>` bölümünde `<system.diagnostics>` bölümünde, üst düzey `<configuration>` bölümü.  
  
5.  Paylaşılan dinleyiciler birçok türleri için dinleyici'nın başlatma verileri nerede verileri dinleyicisi yönlendirir açıklaması şunları içerir:  
  
    -   A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> dinleyicisi giriş açıklandığı gibi bir dosyayı günlüğe yazar.  
  
    -   A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> dinleyicisi tarafından belirtilen bilgisayarda olay günlüğü için bilgi Yazar `initializeData` parametresi. Olay günlüğünü görüntülemek için kullanabileceğiniz **Sunucu Gezgini** veya **Windows Olay Görüntüleyicisi'ni**. Daha fazla bilgi için bkz: [.NET Framework'te ETW olayları](../../../../framework/performance/etw-events.md).  
  
    -   <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> Ve <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> dinleyicileri yazma belirtilen dosyaya `initializeData` parametresi.  
  
    -   A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> dinleyicisi komut satırı konsola yazar.  
  
    -   Burada günlük dinleyicileri diğer tür bilgilerini yazma hakkında daha fazla bilgi için bu tür belgelerine başvurun.  
  
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
