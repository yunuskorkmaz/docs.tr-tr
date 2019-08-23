---
title: My. Application. log bilgisinin nereden yazabileceğini belirleme (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, output location
- output, application log location
- My.Application.Log object, output location
- event logs, determining output location
- application event logs, output location
- applications [Visual Basic], output location
ms.assetid: 5b70143a-7741-45f2-ae1d-03324a3a4189
ms.openlocfilehash: 305c29e33f6cd421f39004e09d27c75b02ba8354
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912551"
---
# <a name="walkthrough-determining-where-myapplicationlog-writes-information-visual-basic"></a>İzlenecek yol: My. Application. log bilgisinin nereden yazabileceğini belirleme (Visual Basic)

Nesnesi `My.Application.Log` , çeşitli günlük dinleyicilerine bilgi yazabilir. Günlük dinleyicileri bilgisayarın yapılandırma dosyası tarafından yapılandırılır ve bir uygulamanın yapılandırma dosyası tarafından geçersiz kılınabilir. Bu konu, varsayılan ayarları ve uygulamanızın ayarlarının nasıl belirleneceğini açıklar.

Varsayılan çıkış konumları hakkında daha fazla bilgi için bkz. [Uygulama Günlükleriyle Çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).

### <a name="to-determine-the-listeners-for-myapplicationlog"></a>My. Application. log için dinleyicileri belirleme

1. Derlemenin yapılandırma dosyasını bulun. Derlemeyi geliştiriyorsanız, **Çözüm Gezgini**Visual Studio 'da App. config dosyasına erişebilirsiniz. Aksi takdirde, yapılandırma dosya adı ". config" ile eklenen derlemenin adıdır ve derlemeyle aynı dizinde bulunur.

    > [!NOTE]
    > Her derlemenin bir yapılandırma dosyası yoktur.

    Yapılandırma dosyası bir XML dosyasıdır.

2. Bölümünde yer `name` alan "DefaultSource"özniteliğinesahipbölümündebölümünübulun`<sources>`. `<listeners>` `<source>` Bölümü, bölümünde, üst düzey `<system.diagnostics>` `<configuration>` bölümünde bulunur. `<sources>`

    Bu bölümler yoksa, bilgisayarın yapılandırma dosyası `My.Application.Log` günlük dinleyicilerini yapılandırabilir. Aşağıdaki adımlarda, bilgisayar yapılandırma dosyasının neyi tanımladığı nasıl belirleneceği açıklanır:

    1. Bilgisayarın Machine. config dosyasını bulun. Genellikle, *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* dizininde bulunur, burada `SystemRoot` işletim sistemi dizinidir ve `frameworkVersion` .NET Framework sürümüdür.

        Machine. config dosyasındaki ayarlar bir uygulamanın yapılandırma dosyası tarafından geçersiz kılınabilir.

        Aşağıda listelenen isteğe bağlı öğeler yoksa, bunları oluşturabilirsiniz.

    2. `<listeners>` Bölümündeki`name`bölümünde bulunan bölümündeki " `<configuration>` DefaultSource `<sources>` " özniteliği, bölümündeki en üst düzey bölümünde bulunan bölümü bulun. `<system.diagnostics>` `<source>`

        Bu bölümler yoksa, `My.Application.Log` yalnızca varsayılan günlük dinleyicilerine sahiptir.

3. `add>` <`listeners>` Bölümünde < öğelerini bulun.

     Bu öğeler, kaynak için `My.Application.Log` adlandırılmış günlük dinleyicileri ekler.

4. Bölümünde, üst düzey `<system.diagnostics>` `<sharedListeners>` bölümündekibölümünde`<configuration>` bulunan günlük dinleyicilerinin adlarını içeren `<add>` öğeleri bulun.

5. Birçok türdeki paylaşılan dinleyici için, dinleyicinin başlatma verileri, dinleyicinin verileri nerede yönlendirdiği hakkında bir açıklama içerir.

    - Bir <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> dinleyici, giriş bölümünde açıklandığı gibi bir dosya günlüğüne yazar.

    - Bir <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> dinleyici, `initializeData` parametre tarafından belirtilen bilgisayar olay günlüğüne bilgi yazar. Bir olay günlüğünü görüntülemek için **Sunucu Gezgini** veya **Windows Olay Görüntüleyicisi**kullanabilirsiniz. Daha fazla bilgi için [.NET Framework ETW olayları](../../../../framework/performance/etw-events.md)bölümüne bakın.

    - `initializeData` Ve <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> dinleyicileri,parametresinde<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> belirtilen dosyaya yazar.

    - Bir <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> dinleyici, komut satırı konsoluna yazar.

    - Diğer günlük dinleyicisi türlerinin yazma bilgileri hakkında daha fazla bilgi için, bu türün belgelerine başvurun.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.DelimitedListTraceListener>
- <xref:System.Diagnostics.XmlWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics>
- [Uygulama Günlükleriyle Çalışma](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [Nasıl yapılır: Günlük özel durumları](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [Nasıl yapılır: Yazma günlüğü Iletileri](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [İzlenecek yol: My. Application. log dosyası yazma bilgilerini değiştirme](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [.NET Framework'te ETW Olayları](../../../../framework/performance/etw-events.md)
- [Sorun giderme: Günlük dinleyicileri](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)
