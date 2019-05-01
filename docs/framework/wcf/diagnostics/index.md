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
ms.openlocfilehash: 351d133215343e07e849ad1045eba601dd8cce56
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797533"
---
# <a name="administration-and-diagnostics"></a>Yönetim ve Tanılama
Windows Communication Foundation (WCF) zengin bir uygulamanın ömrü farklı aşamalarında izlemenize yardımcı olacak işlevler sunar. Örneğin, yapılandırma, hizmetler ve istemcileri dağıtımı ayarlamak için kullanabilirsiniz. WCF performans sayaçları, uygulamanızın performansını ölçmek amacıyla büyük bir kümesini içerir. WCF ayrıca İnceleme veri hizmetinin çalışma zamanında WCF Windows Yönetim Araçları (WMI) sağlayıcısı üzerinden kullanıma sunar. Uygulama bir hatayla karşılaştığında veya hatalı davranan başlatır, önemli şey gerçekleşip gerçekleşmediğini görmek için olay günlüğünü kullanabilirsiniz. İleti günlüğe kaydetme ve izleme gerçekleşmesini için uçtan uca, uygulamanızda hangi olayların olduğunu görmek için kullanabilirsiniz. Bu özellikler, geliştiricilerin ve BT uzmanlarının düzgün çalışmıyorsa, bir WCF uygulamada sorun gidermek için yardımcı olur.  
  
> [!NOTE]
>  Ayrıntılı bilgi hataları alıyorsanız, etkinleştirmelisiniz `includeExceptionDetailInFaults` özniteliği [ \<serviceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) yapılandırma öğesi. Bu, bu sayede daha gelişmiş tanılama gerek kalmadan Sık karşılaşılan birçok sorun algılamak özel durum ayrıntısı, istemcilere göndermek için WCF bildirir. Daha fazla bilgi için [gönderme ve alma hataları](../../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
## <a name="diagnostics-features-provided-by-wcf"></a>WCF tarafından sağlanan tanılama özellikleri  
 WCF aşağıdaki tanılama işlevleri sağlar:  
  
- Uçtan uca izleme, bir uygulama bir hata ayıklayıcı kullanmadan sorun giderme için izleme verileri sağlar. WCF hata iletileri yanı sıra, işlem kilometre taşları için izlemeler çıkarır. Bu kanal fabrikası açma veya gönderme ve bir hizmet konağı ile iletiler almaya içerebilir. İzleme, ilerleme durumunu izlemek çalışan bir uygulama için etkinleştirilebilir. Daha fazla bilgi için [izleme](../../../../docs/framework/wcf/diagnostics/tracing/index.md) konu. İzleme uygulamanızda hata ayıklamak için kullanabileceğinizi anlamak için bkz [uygulamanız sorun giderme için izleme kullanarak](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md) konu.  
  
- Günlüğe ileti kaydetme öncesinde ve sonrasında iletim iletileri nasıl göründüğünü görmek sağlar. Daha fazla bilgi için [ileti günlüğe kaydetme](../../../../docs/framework/wcf/diagnostics/message-logging.md) konu.  
  
- Olay izleme olayları herhangi bir önemli sorunlar için olay günlüğüne yazar. Ardından, davranışlarındaki incelemek için Olay Görüntüleyicisi'ni kullanabilirsiniz. Daha fazla bilgi için [olay günlüğü](../../../../docs/framework/wcf/diagnostics/event-logging/index.md) konu.  
  
- Performans sayaçlarını Performans İzleyicisi kullanıma sunulan uygulama ve sistemin durumunu izlemenize olanak tanır. Daha fazla bilgi için [performans sayaçları](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md) konu.  
  
- <xref:System.ServiceModel.Configuration> Ad alanı yapılandırma dosyalarını yükleme ve bir hizmet veya istemcinin uç nokta ayarlamayı olanak tanır. Güncelleştirmeleri çok sayıda bilgisayara dağıtılması gerektiğinde, birçok uygulama için kod değişiklikleri nesne modelinde kullanabilirsiniz. Alternatif olarak, [Yapılandırma Aracı (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) bir GUI Sihirbazı'nı kullanarak yapılandırma ayarlarını düzenlemek için. Daha fazla bilgi için [uygulamanızı yapılandırma](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md) konu.  
  
- WMI, hangi hizmetlerin bir makine ve kullanımda olan bağlamaları dinlediği bulmanıza olanak sağlar. Daha fazla bilgi için [tanılama için Windows Yönetim araçları kullanarak](../../../../docs/framework/wcf/diagnostics/wmi/index.md) konu.  
  
 WCF oluşturmanıza, dağıtmanıza ve WCF uygulamalarını yönetmek kolaylaştırmak için çeşitli GUI ve komut satırı araçlar da sağlar. Daha fazla bilgi için [Windows Communication Foundation Araçları](../../../../docs/framework/wcf/tools.md). Örneğin, kullanabileceğiniz [Yapılandırma Aracı (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) oluşturmak ve XML düzenleme yerine doğrudan bir Sihirbazı'nı kullanarak WCF yapılandırma ayarlarını düzenlemek için. Ayrıca [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) görüntülemek, Grup ve tanılamak izleme iletileri filtre için onarın ve WCF hizmetleri ile ilgili sorunlar doğrulayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulamanızı Yapılandırma](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md)
- [Hizmet Dağıtma](../../../../docs/framework/wcf/diagnostics/deploying-services.md)
- [Özel Durum Başvurusu](../../../../docs/framework/wcf/diagnostics/exceptions-reference/index.md)
- [Günlüğe Olay Kaydetme](../../../../docs/framework/wcf/diagnostics/event-logging/index.md)
- [Günlüğe İleti Kaydetme](../../../../docs/framework/wcf/diagnostics/message-logging.md)
- [Yapılandırma Düzenleme Aracı (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)
- [Hizmet İzleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
- [ServiceModel Kayıt Aracı](../../../../docs/framework/wcf/diagnostics/servicemodel-registration-tool.md)
- [İzleme](../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Tanılama için Windows Yönetim Araçlarını Kullanma](../../../../docs/framework/wcf/diagnostics/wmi/index.md)
- [Performans Sayaçları](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
- [Windows Communication Foundation Araçları](../../../../docs/framework/wcf/tools.md)
