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
ms.openlocfilehash: d8a8d86f312c0c707ff9f60d4106cc2b5784c6a0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963072"
---
# <a name="administration-and-diagnostics"></a>Yönetim ve Tanılama
Windows Communication Foundation (WCF), bir uygulamanın ömrünün farklı aşamalarını izlemenize yardımcı olabilecek zengin bir işlevler kümesi sağlar. Örneğin, dağıtımdaki Hizmetleri ve istemcileri ayarlamak için yapılandırmayı kullanabilirsiniz. WCF, uygulamanızın performansını ölçgetirmenize yardımcı olacak büyük bir performans sayacı kümesi içerir. WCF Ayrıca bir hizmetin denetim verilerini bir WCF Windows Yönetim Araçları (WMI) sağlayıcısı aracılığıyla çalışma zamanında kullanıma sunar. Uygulama bir hata yaşadığında veya yanlış davranmaya başladığında, önemli bir şeyin olup olmadığını görmek için olay günlüğünü kullanabilirsiniz. Ayrıca, uygulamanızda uçtan uca olayları görmek için Ileti günlüğe kaydetme ve Izleme özelliğini de kullanabilirsiniz. Bu özellikler, geliştiricilerin ve BT uzmanlarının doğru davranmayan bir WCF uygulamasında sorun gidermeye yardımcı olur.  
  
> [!NOTE]
> Özel ayrıntı bilgisi olmayan hatalar alıyorsanız, `includeExceptionDetailInFaults` [ \<serviceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) yapılandırma öğesinin özniteliğini etkinleştirmelisiniz. Bu, WCF 'ye, daha gelişmiş tanılama gerektirmeden birçok yaygın sorunu saptamanızı sağlayan istemcilere özel durum ayrıntısı göndermesini sağlar. Daha fazla bilgi için bkz. [hata gönderme ve alma](../../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
## <a name="diagnostics-features-provided-by-wcf"></a>WCF tarafından sunulan tanılama özellikleri  
 WCF aşağıdaki tanılama işlevlerini sağlar:  
  
- Uçtan uca izleme, bir hata ayıklayıcı kullanmadan bir uygulamanın sorunlarını gidermeye yönelik izleme verileri sağlar. WCF, işlem kilometre taşları ve hata iletileri için izlemeleri çıktı. Bu, bir kanal fabrikası açmaya veya bir hizmet ana bilgisayarı tarafından ileti göndermeye ve almaya dahil olabilir. Çalışan bir uygulama için izleme, ilerleme durumunu izlemek üzere etkinleştirilebilir. Daha fazla bilgi için [izleme](../../../../docs/framework/wcf/diagnostics/tracing/index.md) konusuna bakın. Uygulamanızda hata ayıklamak için izlemeyi nasıl kullanabileceğinizi anlamak için, bkz. [Izleme kullanarak uygulamanızın sorunlarını giderme](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md) konusunda bilgi edinin.  
  
- İleti günlüğü, iletilerin, iletimden önce ve sonra nasıl görüneceğini görmenizi sağlar. Daha fazla bilgi için [Ileti günlüğe kaydetme](../../../../docs/framework/wcf/diagnostics/message-logging.md) konusuna bakın.  
  
- Olay izleme, önemli sorunlara yönelik olayları olay günlüğüne yazar. Daha sonra tüm normalleştirimler incelemek için Olay Görüntüleyicisi kullanabilirsiniz. Daha fazla bilgi için [olay günlüğü](../../../../docs/framework/wcf/diagnostics/event-logging/index.md) konusuna bakın.  
  
- Performans Izleyicisi aracılığıyla sunulan performans sayaçları, uygulamanızı ve sisteminizin sistem durumunu izlemenize olanak tanır. Daha fazla bilgi için bkz. [performans sayaçları](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md) konusu.  
  
- Ad <xref:System.ServiceModel.Configuration> alanı, yapılandırma dosyalarını yüklemenize ve bir hizmet veya istemci uç noktası ayarlamanıza olanak sağlar. Güncelleştirmelerin birçok bilgisayara dağıtılması gerektiğinde birçok uygulamada değişiklikler yapmak için nesne modelini kullanabilirsiniz. Alternatif olarak, bir GUI Sihirbazı kullanarak yapılandırma ayarlarını düzenlemek için [yapılandırma Düzenleyicisi aracını (SvcConfigEditor. exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) kullanabilirsiniz. Daha fazla bilgi için, [uygulamanızı yapılandırma](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md) konusuna bakın.  
  
- WMI, bir makinede hangi hizmetlerin dinlediğini ve kullanımda olan bağlamaları bulmanıza olanak sağlar. Daha fazla bilgi için [Tanılama için Windows Yönetim araçları kullanma](../../../../docs/framework/wcf/diagnostics/wmi/index.md) konusuna bakın.  
  
 WCF Ayrıca WCF uygulamaları oluşturmanızı, dağıtmanızı ve yönetmenizi kolaylaştırmak için çeşitli GUI ve komut satırı araçları sağlar. Daha fazla bilgi için bkz. [Windows Communication Foundation araçları](../../../../docs/framework/wcf/tools.md). Örneğin, doğrudan XML düzenlemek yerine bir sihirbaz kullanarak WCF yapılandırma ayarlarını oluşturmak ve düzenlemek için [yapılandırma Düzenleyicisi aracını (SvcConfigEditor. exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) kullanabilirsiniz. Ayrıca, WCF hizmetleriyle ilgili sorunları tanılamak, onarmak ve doğrulamak üzere izleme iletilerini görüntülemek, gruplamak ve filtrelemek için [hizmet Izleme Görüntüleyicisi aracı 'nı (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) de kullanabilirsiniz.  
  
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
