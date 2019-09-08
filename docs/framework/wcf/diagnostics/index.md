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
ms.openlocfilehash: dfe169cd6c8d9a643e90e98fc9f22bf116d4335f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795981"
---
# <a name="administration-and-diagnostics"></a>Yönetim ve Tanılama
Windows Communication Foundation (WCF), bir uygulamanın ömrünün farklı aşamalarını izlemenize yardımcı olabilecek zengin bir işlevler kümesi sağlar. Örneğin, dağıtımdaki Hizmetleri ve istemcileri ayarlamak için yapılandırmayı kullanabilirsiniz. WCF, uygulamanızın performansını ölçgetirmenize yardımcı olacak büyük bir performans sayacı kümesi içerir. WCF Ayrıca bir hizmetin denetim verilerini bir WCF Windows Yönetim Araçları (WMI) sağlayıcısı aracılığıyla çalışma zamanında kullanıma sunar. Uygulama bir hata yaşadığında veya yanlış davranmaya başladığında, önemli bir şeyin olup olmadığını görmek için olay günlüğünü kullanabilirsiniz. Ayrıca, uygulamanızda uçtan uca olayları görmek için Ileti günlüğe kaydetme ve Izleme özelliğini de kullanabilirsiniz. Bu özellikler, geliştiricilerin ve BT uzmanlarının doğru davranmayan bir WCF uygulamasında sorun gidermeye yardımcı olur.  
  
> [!NOTE]
> Özel ayrıntı bilgisi olmayan hatalar alıyorsanız, `includeExceptionDetailInFaults` [ \<serviceDebug >](../../configure-apps/file-schema/wcf/servicedebug.md) yapılandırma öğesinin özniteliğini etkinleştirmelisiniz. Bu, WCF 'ye, daha gelişmiş tanılama gerektirmeden birçok yaygın sorunu saptamanızı sağlayan istemcilere özel durum ayrıntısı göndermesini sağlar. Daha fazla bilgi için bkz. [hata gönderme ve alma](../sending-and-receiving-faults.md).  
  
## <a name="diagnostics-features-provided-by-wcf"></a>WCF tarafından sunulan tanılama özellikleri  
 WCF aşağıdaki tanılama işlevlerini sağlar:  
  
- Uçtan uca izleme, bir hata ayıklayıcı kullanmadan bir uygulamanın sorunlarını gidermeye yönelik izleme verileri sağlar. WCF, işlem kilometre taşları ve hata iletileri için izlemeleri çıktı. Bu, bir kanal fabrikası açmaya veya bir hizmet ana bilgisayarı tarafından ileti göndermeye ve almaya dahil olabilir. Çalışan bir uygulama için izleme, ilerleme durumunu izlemek üzere etkinleştirilebilir. Daha fazla bilgi için [izleme](./tracing/index.md) konusuna bakın. Uygulamanızda hata ayıklamak için izlemeyi nasıl kullanabileceğinizi anlamak için, bkz. [Izleme kullanarak uygulamanızın sorunlarını giderme](./tracing/using-tracing-to-troubleshoot-your-application.md) konusunda bilgi edinin.  
  
- İleti günlüğü, iletilerin, iletimden önce ve sonra nasıl görüneceğini görmenizi sağlar. Daha fazla bilgi için [Ileti günlüğe kaydetme](message-logging.md) konusuna bakın.  
  
- Olay izleme, önemli sorunlara yönelik olayları olay günlüğüne yazar. Daha sonra tüm normalleştirimler incelemek için Olay Görüntüleyicisi kullanabilirsiniz. Daha fazla bilgi için [olay günlüğü](./event-logging/index.md) konusuna bakın.  
  
- Performans Izleyicisi aracılığıyla sunulan performans sayaçları, uygulamanızı ve sisteminizin sistem durumunu izlemenize olanak tanır. Daha fazla bilgi için bkz. [performans sayaçları](./performance-counters/index.md) konusu.  
  
- Ad <xref:System.ServiceModel.Configuration> alanı, yapılandırma dosyalarını yüklemenize ve bir hizmet veya istemci uç noktası ayarlamanıza olanak sağlar. Güncelleştirmelerin birçok bilgisayara dağıtılması gerektiğinde birçok uygulamada değişiklikler yapmak için nesne modelini kullanabilirsiniz. Alternatif olarak, bir GUI Sihirbazı kullanarak yapılandırma ayarlarını düzenlemek için [yapılandırma Düzenleyicisi aracını (SvcConfigEditor. exe)](../configuration-editor-tool-svcconfigeditor-exe.md) kullanabilirsiniz. Daha fazla bilgi için, [uygulamanızı yapılandırma](configuring-your-application.md) konusuna bakın.  
  
- WMI, bir makinede hangi hizmetlerin dinlediğini ve kullanımda olan bağlamaları bulmanıza olanak sağlar. Daha fazla bilgi için [Tanılama için Windows Yönetim araçları kullanma](./wmi/index.md) konusuna bakın.  
  
 WCF Ayrıca WCF uygulamaları oluşturmanızı, dağıtmanızı ve yönetmenizi kolaylaştırmak için çeşitli GUI ve komut satırı araçları sağlar. Daha fazla bilgi için bkz. [Windows Communication Foundation araçları](../tools.md). Örneğin, doğrudan XML düzenlemek yerine bir sihirbaz kullanarak WCF yapılandırma ayarlarını oluşturmak ve düzenlemek için [yapılandırma Düzenleyicisi aracını (SvcConfigEditor. exe)](../configuration-editor-tool-svcconfigeditor-exe.md) kullanabilirsiniz. Ayrıca, WCF hizmetleriyle ilgili sorunları tanılamak, onarmak ve doğrulamak üzere izleme iletilerini görüntülemek, gruplamak ve filtrelemek için [hizmet Izleme Görüntüleyicisi aracı 'nı (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) de kullanabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulamanızı Yapılandırma](configuring-your-application.md)
- [Hizmet Dağıtma](deploying-services.md)
- [Özel Durum Başvurusu](./exceptions-reference/index.md)
- [Günlüğe Olay Kaydetme](./event-logging/index.md)
- [Günlüğe İleti Kaydetme](message-logging.md)
- [Yapılandırma Düzenleme Aracı (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md)
- [Hizmet İzleme Görüntüleyicisi Aracı (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md)
- [ServiceModel Kayıt Aracı](servicemodel-registration-tool.md)
- [İzleme](./tracing/index.md)
- [Tanılama için Windows Yönetim Araçlarını Kullanma](./wmi/index.md)
- [Performans Sayaçları](./performance-counters/index.md)
- [Windows Communication Foundation Araçları](../tools.md)
