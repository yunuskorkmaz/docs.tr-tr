---
title: Yönetim ve Tanılama
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, diagnostics
- Windows Communication Foundation, administration
- diagnostics [WCF]
- WCF, diagnostics
- administration [WCF]
- WCF, administration
ms.assetid: 34c81c08-0e0f-4fbc-9ae8-91948640ee43
ms.openlocfilehash: c69d5681b186fdfae168ceea8b35f5786eaf02c9
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33810011"
---
# <a name="administration-and-diagnostics"></a>Yönetim ve Tanılama
Windows Communication Foundation (WCF) zengin bir uygulamanın yaşam farklı aşamalarını izlemenize yardımcı olabilir işlevler sağlar. Örneğin, hizmetleri ve dağıtım istemcilerinde ayarlamak için yapılandırma kullanabilirsiniz. WCF performans sayaçları, uygulamanızın performansını ölçmek amacıyla büyük bir dizi içerir. WCF ayrıca İnceleme veri WCF Windows Yönetim Araçları (WMI) sağlayıcısı üzerinden çalışma zamanında bir hizmet sunar. Uygulama arızalanması veya hatalı davranan başlatıldığında, önemli bir şey gerçekleşip gerçekleşmediğini görmek için olay günlüğünü kullanabilirsiniz. Hangi olayların oluşmasını uçtan uca uygulamanızda olduğunu görmek için ileti günlüğe kaydetme ve izleme de kullanabilirsiniz. Bu özellikler, geliştiriciler ve BT uzmanları düzgün çalışmıyorsa, bir WCF uygulaması sorun giderme için yardımcı.  
  
> [!NOTE]
>  Ayrıntılı bilgi yok hataları alıyorsanız, etkinleştirmelisiniz `includeExceptionDetailInFaults` özniteliği [ \<serviceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) yapılandırma öğesi. Bu, daha gelişmiş tanılama gerek kalmadan birçok ortak sorunları belirlemenize olanak sağlayan özel durum ayrıntısı, istemcilere göndermek için WCF bildirir. Daha fazla bilgi için bkz: [gönderme ve alma hataları](../../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
## <a name="diagnostics-features-provided-by-wcf"></a>WCF tarafından sağlanan tanılama özellikleri  
 WCF aşağıdaki tanılama işlevleri sağlar:  
  
-   Uçtan uca izleme, bir uygulama bir hata ayıklayıcısı kullanmadan sorun giderme için izleme verileri sağlar. WCF işlemi kilometre taşları gibi hata iletileri için izlemeleri çıkarır. Bu kanal fabrikası açma veya ileti gönderme ve hizmet ana bilgisayarı tarafından alma içerebilir. İzleme, ilerleme durumunu izlemek çalışan bir uygulama için etkinleştirilebilir. Daha fazla bilgi için bkz: [izleme](../../../../docs/framework/wcf/diagnostics/tracing/index.md) konu. İzleme uygulamanızda hata ayıklama için kullanabileceğinizi anlamak için bkz: [kullanarak izleme uygulamanız sorun giderme için](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md) konu.  
  
-   İleti günlüğe kaydetme öncesinde ve sonrasında iletim iletileri nasıl göründüğünü görmek sağlar. Daha fazla bilgi için bkz: [ileti günlüğe kaydetme](../../../../docs/framework/wcf/diagnostics/message-logging.md) konu.  
  
-   Olay izleme olayları önemli sorunlar için olay günlüğüne yazar. Ardından, anormallikleri incelemek üzere Olay Görüntüleyicisi'ni kullanabilirsiniz. Daha fazla bilgi için bkz: [olay günlüğü](../../../../docs/framework/wcf/diagnostics/event-logging/index.md) konu.  
  
-   Performans İzleyicisi aracılığıyla sunulan performans sayaçları, uygulamanızı ve sistemin durumunu izlemenize olanak tanır. Daha fazla bilgi için bkz: [performans sayaçları](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md) konu.  
  
-   <xref:System.ServiceModel.Configuration> Ad alanı yapılandırma dosyalarını yüklemek ve bir hizmet veya istemci uç nokta ayarlamayı sağlar. Güncelleştirmeleri çok sayıda bilgisayara dağıtılması gerekir, birçok uygulama betik değişiklikleri nesne modelinde kullanabilirsiniz. Alternatif olarak, kullanabileceğiniz [Yapılandırma Aracı (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) bir GUI Sihirbazı'nı kullanarak yapılandırma ayarlarını düzenlemek için. Daha fazla bilgi için bkz: [uygulamanızı yapılandırma](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md) konu.  
  
-   WMI hangi hizmetlerin bir makine ve kullanımda olan bağlamaları dinlediği bulmanızı sağlar. Daha fazla bilgi için bkz: [tanılama için Windows Yönetim araçları kullanarak](../../../../docs/framework/wcf/diagnostics/wmi/index.md) konu.  
  
 WCF oluşturmak, dağıtmak ve WCF uygulamalarını yönetmek kolaylaştırmak için çeşitli GUI ve komut satırı araçlar da sağlar. Daha fazla bilgi için bkz: [Windows Communication Foundation Araçları](../../../../docs/framework/wcf/tools.md). Örneğin, kullanabileceğiniz [Yapılandırma Aracı (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) oluşturmak ve XML doğrudan düzenlemek yerine bir Sihirbazı'nı kullanarak WCF yapılandırma ayarlarını düzenlemek için. Aynı zamanda [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) görüntülemek, Grup ve böylece tanılamak izleme iletilerini filtrelemek için onarın ve WCF hizmetleri ile ilgili sorunları doğrulayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uygulamanızı Yapılandırma](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md)  
 [Hizmet Dağıtma](../../../../docs/framework/wcf/diagnostics/deploying-services.md)  
 [Özel Durum Başvurusu](../../../../docs/framework/wcf/diagnostics/exceptions-reference/index.md)  
 [Günlüğe Olay Kaydetme](../../../../docs/framework/wcf/diagnostics/event-logging/index.md)  
 [Günlüğe İleti Kaydetme](../../../../docs/framework/wcf/diagnostics/message-logging.md)  
 [Yapılandırma Düzenleme Aracı (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)  
 [Hizmet İzleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)  
 [ServiceModel Kayıt Aracı](../../../../docs/framework/wcf/diagnostics/servicemodel-registration-tool.md)  
 [İzleme](../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Tanılama için Windows Yönetim Araçlarını Kullanma](../../../../docs/framework/wcf/diagnostics/wmi/index.md)  
 [Performans Sayaçları](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)  
 [Windows Communication Foundation Araçları](../../../../docs/framework/wcf/tools.md)
