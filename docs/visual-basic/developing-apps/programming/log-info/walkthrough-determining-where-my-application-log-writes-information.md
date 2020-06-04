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
ms.openlocfilehash: 00b543dbe96ca99446f6797a13b66ee62c422b93
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398285"
---
# <a name="walkthrough-determining-where-myapplicationlog-writes-information-visual-basic"></a>İzlenecek Yol: My.Application.Log Günlüğünün Bilgileri Nereye Yazdığını Belirleme (Visual Basic)

`My.Application.Log`Nesnesi, çeşitli günlük dinleyicilerine bilgi yazabilir. Günlük dinleyicileri bilgisayarın yapılandırma dosyası tarafından yapılandırılır ve bir uygulamanın yapılandırma dosyası tarafından geçersiz kılınabilir. Bu konu, varsayılan ayarları ve uygulamanızın ayarlarının nasıl belirleneceğini açıklar.

Varsayılan çıkış konumları hakkında daha fazla bilgi için bkz. [Uygulama Günlükleriyle Çalışma](working-with-application-logs.md).

### <a name="to-determine-the-listeners-for-myapplicationlog"></a>My. Application. log için dinleyicileri belirleme

1. Derlemenin yapılandırma dosyasını bulun. Derlemeyi geliştiriyorsanız, **Çözüm Gezgini**Visual Studio 'da App. config dosyasına erişebilirsiniz. Aksi takdirde, yapılandırma dosya adı ". config" ile eklenen derlemenin adıdır ve derlemeyle aynı dizinde bulunur.

    > [!NOTE]
    > Her derlemenin bir yapılandırma dosyası yoktur.

    Yapılandırma dosyası bir XML dosyasıdır.

2. Bölümünde `<listeners>` `<source>` `name` yer alan "DefaultSource" özniteliğine sahip bölümünde bölümünü bulun `<sources>` . Bölümü, bölümünde `<sources>` `<system.diagnostics>` , üst düzey `<configuration>` bölümünde bulunur.

    Bu bölümler yoksa, bilgisayarın yapılandırma dosyası `My.Application.Log` günlük dinleyicilerini yapılandırabilir. Aşağıdaki adımlarda, bilgisayar yapılandırma dosyasının neyi tanımladığı nasıl belirleneceği açıklanır:

    1. Bilgisayarın Machine. config dosyasını bulun. Genellikle, *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* dizininde bulunur, burada `SystemRoot` işletim sistemi dizinidir ve `frameworkVersion` .NET Framework sürümüdür.

        Machine. config dosyasındaki ayarlar bir uygulamanın yapılandırma dosyası tarafından geçersiz kılınabilir.

        Aşağıda listelenen isteğe bağlı öğeler yoksa, bunları oluşturabilirsiniz.

    2. Bölümündeki bölümünde bulunan bölümündeki `<listeners>` `<source>` `name` "DefaultSource" özniteliği, bölümündeki `<sources>` `<system.diagnostics>` en üst düzey `<configuration>` bölümünde bulunan bölümü bulun.

        Bu bölümler yoksa, `My.Application.Log` yalnızca varsayılan günlük dinleyicilerine sahiptir.

3. `add>`<bölümünde <öğelerini bulun `listeners>` .

     Bu öğeler, kaynak için adlandırılmış günlük dinleyicileri ekler `My.Application.Log` .

4. Bölümünde, `<add>` `<sharedListeners>` `<system.diagnostics>` üst düzey bölümündeki bölümünde bulunan günlük dinleyicilerinin adlarını içeren öğeleri bulun `<configuration>` .

5. Birçok türdeki paylaşılan dinleyici için, dinleyicinin başlatma verileri, dinleyicinin verileri nerede yönlendirdiği hakkında bir açıklama içerir.

    - Bir <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> dinleyici, giriş bölümünde açıklandığı gibi bir dosya günlüğüne yazar.

    - Bir <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> dinleyici, parametre tarafından belirtilen bilgisayar olay günlüğüne bilgi Yazar `initializeData` . Bir olay günlüğünü görüntülemek için **Sunucu Gezgini** veya **Windows Olay Görüntüleyicisi**kullanabilirsiniz. Daha fazla bilgi için [.NET Framework ETW olayları](../../../../framework/performance/etw-events.md)bölümüne bakın.

    - <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>Ve <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> dinleyicileri, parametresinde belirtilen dosyaya yazar `initializeData` .

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
- [Uygulama Günlükleriyle Çalışma](working-with-application-logs.md)
- [Nasıl yapılır: Özel Durumları Günlüğe Kaydetme](how-to-log-exceptions.md)
- [Nasıl yapılır: Günlük İletileri Yazma](how-to-write-log-messages.md)
- [İzlenecek yol: My.Application.Log Günlüğünün Bilgileri Yazdığı Yeri Değiştirme](walkthrough-changing-where-my-application-log-writes-information.md)
- [.NET Framework'te ETW Olayları](../../../../framework/performance/etw-events.md)
- [Sorun Giderme: Günlük Dinleyicileri](troubleshooting-log-listeners.md)
