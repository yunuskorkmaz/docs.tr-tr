---
title: "Yönetim ve Tanılama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, diagnostics
- Windows Communication Foundation, administration
- diagnostics [WCF]
- WCF, diagnostics
- administration [WCF]
- WCF, administration
ms.assetid: 34c81c08-0e0f-4fbc-9ae8-91948640ee43
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4aa9cacfaa966bbe37618406f4b1413dec433726
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="administration-and-diagnostics"></a>Yönetim ve Tanılama
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]zengin bir uygulamanın yaşam farklı aşamalarını izlemenize yardımcı olabilir işlevler sağlar. Örneğin, hizmetleri ve dağıtım istemcilerinde ayarlamak için yapılandırma kullanabilirsiniz. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]çok sayıda uygulamanızın performansını ölçmek yardımcı olması için performans sayaçları içerir. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Ayrıca İnceleme çalışma zamanında bir hizmetin kullanıma sunan bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Windows Yönetim Araçları (WMI) sağlayıcısı. Uygulama arızalanması veya hatalı davranan başlatıldığında, önemli bir şey gerçekleşip gerçekleşmediğini görmek için olay günlüğünü kullanabilirsiniz. Hangi olayların oluşmasını uçtan uca uygulamanızda olduğunu görmek için ileti günlüğe kaydetme ve izleme de kullanabilirsiniz. Bu özellikler geliştiriciler ve BT uzmanları sorun giderme için yardımcı bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] düzgün çalışmıyorsa, uygulama.  
  
> [!NOTE]
>  Ayrıntılı bilgi yok hataları alıyorsanız, etkinleştirmelisiniz `includeExceptionDetailInFaults` özniteliği [ \<serviceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) yapılandırma öğesi. Bu bildirir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] özel durum ayrıntısı, daha gelişmiş tanılama gerek kalmadan birçok ortak sorunları belirlemenize olanak tanıyan istemcilere göndermek için. Daha fazla bilgi için bkz: [gönderme ve alma hataları](../../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
## <a name="diagnostics-features-provided-by-wcf"></a>WCF tarafından sağlanan tanılama özellikleri  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Aşağıdaki Tanılama işlevleri sağlar:  
  
-   Uçtan uca izleme, bir uygulama bir hata ayıklayıcısı kullanmadan sorun giderme için izleme verileri sağlar. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]hata iletileri yanı sıra, işlem kilometre taşları izlemelerini çıkarır. Bu kanal fabrikası açma veya ileti gönderme ve hizmet ana bilgisayarı tarafından alma içerebilir. İzleme, ilerleme durumunu izlemek çalışan bir uygulama için etkinleştirilebilir. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][izleme](../../../../docs/framework/wcf/diagnostics/tracing/index.md) konu. İzleme uygulamanızda hata ayıklama için kullanabileceğinizi anlamak için bkz: [kullanarak izleme uygulamanız sorun giderme için](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md) konu.  
  
-   İleti günlüğe kaydetme öncesinde ve sonrasında iletim iletileri nasıl göründüğünü görmek sağlar. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][ileti günlüğe kaydetme](../../../../docs/framework/wcf/diagnostics/message-logging.md) konu.  
  
-   Olay izleme olayları önemli sorunlar için olay günlüğüne yazar. Ardından, anormallikleri incelemek üzere Olay Görüntüleyicisi'ni kullanabilirsiniz. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][olay günlüğü](../../../../docs/framework/wcf/diagnostics/event-logging/index.md) konu.  
  
-   Performans İzleyicisi aracılığıyla sunulan performans sayaçları, uygulamanızı ve sistemin durumunu izlemenize olanak tanır. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][performans sayaçları](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md) konu.  
  
-   <xref:System.ServiceModel.Configuration> Ad alanı yapılandırma dosyalarını yüklemek ve bir hizmet veya istemci uç nokta ayarlamayı sağlar. Güncelleştirmeleri çok sayıda bilgisayara dağıtılması gerekir, birçok uygulama betik değişiklikleri nesne modelinde kullanabilirsiniz. Alternatif olarak, kullanabileceğiniz [Yapılandırma Aracı (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) bir GUI Sihirbazı'nı kullanarak yapılandırma ayarlarını düzenlemek için. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][uygulamanızı yapılandırma](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md) konu.  
  
-   WMI hangi hizmetlerin bir makine ve kullanımda olan bağlamaları dinlediği bulmanızı sağlar. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][tanılama için Windows Yönetim araçları kullanarak](../../../../docs/framework/wcf/diagnostics/wmi/index.md) konu.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Ayrıca çeşitli GUI ve komut satırı araçları oluşturmak kolaylaştırmak için dağıtmak ve yönetmek sağlar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamalar. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Windows Communication Foundation Araçları](../../../../docs/framework/wcf/tools.md). Örneğin, kullanabileceğiniz [Yapılandırma Aracı (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) oluşturmak ve düzenlemek için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] XML doğrudan düzenlemek yerine bir Sihirbazı'nı kullanarak yapılandırma ayarları. Aynı zamanda [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) görüntülemek, Grup ve böylece tanılamak izleme iletilerini filtrelemek için onarın ve sorunları doğrulayın [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmetleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uygulamanızı yapılandırma](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md)  
 [Hizmetleri dağıtma](../../../../docs/framework/wcf/diagnostics/deploying-services.md)  
 [Özel durum başvurusu](../../../../docs/framework/wcf/diagnostics/exceptions-reference/index.md)  
 [Olay günlüğü](../../../../docs/framework/wcf/diagnostics/event-logging/index.md)  
 [İleti günlüğe kaydetme](../../../../docs/framework/wcf/diagnostics/message-logging.md)  
 [Yapılandırma Aracı (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)  
 [Hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)  
 [ServiceModel kayıt aracı](../../../../docs/framework/wcf/diagnostics/servicemodel-registration-tool.md)  
 [İzleme](../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Tanılama için Windows Yönetim Araçları'nı kullanma](../../../../docs/framework/wcf/diagnostics/wmi/index.md)  
 [Performans sayaçları](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)  
 [Windows Communication Foundation araçları](../../../../docs/framework/wcf/tools.md)
