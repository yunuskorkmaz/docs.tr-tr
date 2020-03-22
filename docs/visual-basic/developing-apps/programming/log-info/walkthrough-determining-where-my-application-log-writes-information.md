---
title: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, output location
- output, application log location
- My.Application.Log object, output location
- event logs, determining output location
- application event logs, output location
- applications [Visual Basic], output location
ms.assetid: 5b70143a-7741-45f2-ae1d-03324a3a4189
ms.openlocfilehash: f3fd0ed0388276f1400bf77d0abfb488634a45a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74353600"
---
# <a name="walkthrough-determining-where-myapplicationlog-writes-information-visual-basic"></a>İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme (Visual Basic)

Nesne `My.Application.Log` birkaç günlük dinleyiciye bilgi yazabilir. Günlük dinleyicileri bilgisayarın yapılandırma dosyası tarafından yapılandırılır ve bir uygulamanın yapılandırma dosyası tarafından geçersiz kılınabilir. Bu konu varsayılan ayarları ve uygulamanızın ayarlarını nasıl belirleyirinizi açıklar.

Varsayılan çıktı konumları hakkında daha fazla bilgi için Bkz. [Uygulama Günlükleri ile Çalışma.](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)

### <a name="to-determine-the-listeners-for-myapplicationlog"></a>My.Application.Log için dinleyici belirlemek için

1. Derlemenin yapılandırma dosyasını bulun. Montajı geliştiriyorsanız, Visual Studio'daki app.config'e **Solution Explorer'dan**erişebilirsiniz. Aksi takdirde, yapılandırma dosya adı ".config" ile eklenen derlemenin adıdır ve derlemeyle aynı dizinde bulunur.

    > [!NOTE]
    > Her derlemenin bir yapılandırma dosyası yok.

    Yapılandırma dosyası bir XML dosyasıdır.

2. Bölümde bulunan "DefaultSource" `<source>` `name` özniteliğinin bulunduğu bölümdeki bölümü bulun. `<listeners>` `<sources>` Bölüm, `<sources>` üst düzey `<system.diagnostics>` `<configuration>` bölümde yer almaktadır.

    Bu bölümler yoksa, bilgisayarın yapılandırma dosyası günlük dinleyicilerini `My.Application.Log` yapılandırabilir. Aşağıdaki adımlar, bilgisayar yapılandırma dosyasının tanımladığı nı nasıl belirleyeceklerini açıklar:

    1. Bilgisayarın makinesinin bulunduğu config dosyasını bulun. Genellikle *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* dizininde bulunur, işletim sistemi `SystemRoot` dizininin bulunduğu yerdir ve `frameworkVersion` .NET Framework'ün sürümüdür.

        machine.config'deki ayarlar, bir uygulamanın yapılandırma dosyası tarafından geçersiz kılınabilir.

        Aşağıda listelenen isteğe bağlı öğeler yoksa, bunları oluşturabilirsiniz.

    2. `<listeners>` "DefaultSource" `<source>` `name` özniteliğinin bulunduğu bölümdeki bölümü, `<sources>` `<system.diagnostics>` bölümdeki, üst düzey `<configuration>` bölümdeki bölümü bulun.

        Bu bölümler yoksa, yalnızca `My.Application.Log` varsayılan günlük dinleyicileri vardır.

3. <`add>` `listeners>` bölümündeki <öğeleri bulun.

     Bu öğeler, adı geçen `My.Application.Log` günlük dinleyicilerini kaynağa ekler.

4. Bölümdeki, `<system.diagnostics>` üst düzey `<configuration>` bölümde, günlük dinleyicilerinin adlarını içeren `<add>` öğeleri bulun. `<sharedListeners>`

5. Birçok paylaşılan dinleyici türü için dinleyicinin başlangıç verileri, dinleyicinin verileri nereye yönlendirdiğinin açıklamasını içerir:

    - Bir <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> dinleyici, girişte açıklandığı gibi bir dosya günlüğüne yazar.

    - Dinleyici, <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> `initializeData` parametre tarafından belirtilen bilgisayar olay günlüğüne bilgi yazar. Bir olay günlüğünü görüntülemek için **Server Explorer** veya Windows **Event Viewer'ı**kullanabilirsiniz. Daha fazla bilgi için [.NET Framework'deki ETW Olayları'na](../../../../framework/performance/etw-events.md)bakın.

    - Ve <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> dinleyiciler parametrede belirtilen `initializeData` dosyaya yazar.

    - Dinleyici <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> komut satırı konsoluna yazar.

    - Diğer günlük dinleyici türlerinin nerede bilgi yazdıkları hakkında bilgi için, bu türbelgelerine başvurun.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.DelimitedListTraceListener>
- <xref:System.Diagnostics.XmlWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics>
- [Uygulama Günlükleriyle Çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Nasıl Yapılır: Günlük Özel Durumları](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [Nasıl Yapılır: Günlük İletileri Yazma](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [.NET Framework'te ETW Olayları](../../../../framework/performance/etw-events.md)
- [Sorun Giderme: Günlük Dinleyicileri](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)
