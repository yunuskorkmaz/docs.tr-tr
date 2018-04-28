---
title: İşlemsel Uygulamaları Tanılama
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a993492-1088-4d10-871b-0c09916af05f
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a730daeadbed0f7453b8312612c096846d4e2cda
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="diagnosing-transactional-applications"></a>İşlemsel Uygulamaları Tanılama
Bu konuda nasıl kullanılacağını açıklar [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] işlem uygulamada sorun gidermek için yönetim ve tanılama özelliği.  
  
## <a name="performance-counters"></a>Performans Sayaçları  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] performans sayaçları, işlem uygulamanızın performansını ölçmek standart bir dizi sağlar. Daha fazla bilgi için bkz: [performans sayaçları](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md).  
  
 Performans sayaçları üç farklı düzeylere kapsamlı: Hizmet, uç nokta ve işlem, aşağıdaki tabloda açıklandığı gibi.  
  
### <a name="service-performance-counters"></a>Hizmet Performansı Sayaçları  
  
|Performans sayacı|Açıklama|  
|-------------------------|-----------------|  
|Akışı Yapılan İşlemler|Bu hizmet işlemlerinde aktarılan işlem sayısı. Bu sayaç, bir işlemin hizmete gönderilen ileti bulunur dilediğiniz zaman artırılır.|  
|Saniyede Akışı Yapılan İşlem|Bu hizmet işlemleri için her saniye içinde aktarılan işlem sayısı. Bu sayaç, bir işlemin hizmete gönderilen ileti bulunur dilediğiniz zaman artırılır.|  
|Uygulaması Yapılan İşlemler|Uygulaması yapılan işlem sayısı, işlem sonucu bu hizmetinde kaydedilmiş tamamlandı gerçekleştirilir. Bu tür işlemler altında yapılan çalışmalar tam olarak kaydedilir. Kaynaklar işlemde çalışmanın uygun olarak güncelleştirilir.|  
|Uygulaması Yapılan İşlem/Saniye|Uygulaması yapılan işlem sayısı, işlem sonucu her saniye içinde bu hizmetinde kaydedilmiş tamamlandı gerçekleştirilir. Bu tür işlemler altında yapılan çalışmalar tam olarak kaydedilir. Kaynaklar işlemde çalışmanın uygun olarak güncelleştirilir.|  
|İptal Edilen İşlem Yapılmış Operasyonlar|Uygulaması yapılan işlem sayısı, işlem bu hizmette iptal sonucu tamamlandı gerçekleştirilir. Bu tür işlemler altında yapılan çalışmalar geri alınır. Kaynaklar önceki durumlarına geri alınır.|  
|Uygulanıp Durdurulan İşlem/Saniye|Uygulaması yapılan işlem sayısı, işlem bu hizmette her saniye içinde iptal sonucu tamamlandı gerçekleştirilir. Bu tür işlemler altında yapılan çalışmalar geri alınır. Kaynaklar önceki durumlarına geri alınır.|  
|Şüpheli Uygulanan İşlemler|Uygulaması yapılan işlem sayısı, işlem bu hizmet şüpheli sonucu tamamlandı gerçekleştirilir. Sonucu şüpheli ile yapılan iş belirsiz bir durumda. Kaynakları sonucu tutulur.|  
|Şüpheli Uygulanan İşlem/Saniye|Uygulaması yapılan işlem sayısı, işlem bu hizmet şüpheli sonucu her saniye içinde tamamlandı gerçekleştirilir. Sonucu şüpheli ile yapılan iş belirsiz bir durumda. Kaynakları sonucu tutulur.|  
  
### <a name="endpoint-performance-counters"></a>Uç Noktası Performans Sayaçları  
  
|Performans sayacı|Açıklama|  
|-------------------------|-----------------|  
|Akışı Yapılan İşlemler|Bu uç noktadaki işlemlere aktarılan işlem sayısı. Bu sayaç, bir işlem bitiş noktasına gönderilen ileti bulunur dilediğiniz zaman artırılır.|  
|Saniyede Akışı Yapılan İşlem|Bu uç noktada işlemlerine içinde saniyede akışı yapılan işlem işlem sayısı. Bu sayaç, bir işlem bitiş noktasına gönderilen ileti bulunur dilediğiniz zaman artırılır.|  
  
### <a name="operation-performance-counters"></a>İşlem Performansı Sayaçları  
  
|Performans sayacı|Açıklama|  
|-------------------------|-----------------|  
|Akışı Yapılan İşlemler|Bu uç noktadaki işlemlere aktarılan işlem sayısı. Bu sayaç, bir işlem bitiş noktasına gönderilen ileti bulunur dilediğiniz zaman artırılır.|  
|Saniyede Akışı Yapılan İşlem|Bu uç noktada işlemlerine içinde saniyede akışı yapılan işlem işlem sayısı. Bu sayaç, bir işlem bitiş noktasına gönderilen ileti bulunur dilediğiniz zaman artırılır.|  
  
## <a name="windows-management-instrumentation"></a>Windows Yönetim Araçları  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] İnceleme, bir hizmetin aracılığıyla çalışma zamanında kullanıma sunan bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Windows Yönetim Araçları (WMI) sağlayıcısı. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] bkz: WMI veri erişme, [tanılama için Windows Yönetim araçları kullanarak](../../../../docs/framework/wcf/diagnostics/wmi/index.md).  
  
 Salt okunur WMI özellikleri sayısı bir hizmeti için uygulanan işlem ayarlarını belirtin. Aşağıdaki tablolarda tüm bu ayarlar listelenmektedir.  
  
 Bir hizmete `ServiceBehaviorAttribute` aşağıdaki özelliklere sahiptir.  
  
|Ad|Tür|Açıklama|  
|----------|----------|-----------------|  
|ReleaseServiceInstanceOnTransactionComplete|Boole değeri|Geçerli işlem tamamlandıktan sonra hizmeti nesnesi geri dönüştürüldüğünde olup olmadığını belirtir.|  
|TransactionAutoCompleteOnSessionClose|Boole değeri|Geçerli oturumu kapattığında bekleyen işlem tamamlandı olup olmadığını belirtir.|  
|TransactionIsolationLevel|Geçerli bir değeri içeren bir dize <xref:System.Transactions.IsolationLevel> numaralandırması.|Bu hizmet destekleyen işlem yalıtım düzeyini belirtir.|  
|TransactionTimeout|<xref:System.DateTime>|İçinde bir işlemin tamamlanması gereken süreyi belirtir.|  
  
 `ServiceTimeoutsBehavior` Aşağıdaki özelliğine sahiptir.  
  
|Ad|Tür|Açıklama|  
|----------|----------|-----------------|  
|TransactionTimeout|<xref:System.DateTime>|İçinde bir işlemin tamamlanması gereken süreyi belirtir.|  
  
 Bir bağlama üzerinde `TransactionFlowBindingElement` aşağıdaki özelliklere sahiptir.  
  
|Ad|Tür|Açıklama|  
|----------|----------|-----------------|  
|transactionProtocol|Geçerli bir değeri içeren bir dize <xref:System.ServiceModel.TransactionProtocol> türü.|İşlem akışında kullanmak için işlem protokolü belirtir.|  
|TransactionFlow|Boole değeri|Gelen işlem akışını etkinleştirilip etkinleştirilmeyeceğini belirtir.|  
  
 Bir işlem üzerinde `OperationBehaviorAttribute` aşağıdaki özelliklere sahiptir:  
  
|Ad|Tür|Açıklama|  
|----------|----------|-----------------|  
|TransactionAutoComplete|Boole değeri|İşlenmeyen özel durumlar oluşursa geçerli işlem otomatik olarak gerçekleştirmeyi belirtir.|  
|TransactionScopeRequired|Boole değeri|İşlemi bir işlem gerekli olup olmadığını belirtir.|  
  
 Bir işlem üzerinde `TransactionFlowAttribute` aşağıdaki özelliklere sahiptir.  
  
|Ad|Tür|Açıklama|  
|----------|----------|-----------------|  
|TransactionFlowOption|Geçerli bir değeri içeren bir dize <xref:System.ServiceModel.TransactionFlowOption> numaralandırması.|Hangi işlemin akış gereklidir ölçüde belirtir.|  
  
## <a name="tracing"></a>İzleme  
 İzlemeler izlemek ve işlem uygulamalarınızda hatalarını çözümlemek etkinleştirin. Aşağıdaki yöntemlerle kullanarak izlemeyi etkinleştirebilirsiniz:  
  
-   Standart [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] izleme  
  
     Bu izleme türünü herhangi izleme aynıdır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulama. Daha fazla bilgi için bkz: [yapılandırma izleme](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md).  
  
-   WS-AtomicTransaction izleme  
  
     WS-AtomicTransaction izleme kullanılarak etkinleştirilebilir [WS-AtomicTransaction yapılandırma yardımcı programı (wsatConfig.exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md). Bu tür izleme işlemleri ve katılımcıları sistemi içindeki durumu hakkında bilgi sağlar. Ayrıca iç hizmet modeli izlemeyi etkinleştirmek için ayarlayabileceğiniz `HKLM\SOFTWARE\Microsoft\WSAT\3.0\ServiceModelDiagnosticTracing` kayıt defteri anahtarı geçerli bir değere <xref:System.Diagnostics.SourceLevels> numaralandırması. Aynı şekilde diğer günlük iletisi etkinleştirebilirsiniz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamalar.  
  
-   `System.Transactions` İzleme  
  
     OleTransactions Protokolü kullanılırken protokol iletilerini izlenemez. İzleme desteği <xref:System.Transactions> altyapı sağlar (OleTransactions kullanan) kullanıcıların hareketleri oluşan olaylarla görüntülemesine izin verir. İzlemeyi etkinleştirmek için bir <xref:System.Transactions> uygulama, aşağıdaki kodda dahil `App.config` yapılandırma dosyası.  
  
    ```xml  
    <configuration>  
      <system.diagnostics>  
         <sources>  
            <source name="System.Transactions" switchValue="Verbose, ActivityTracing">  
               <listeners>  
                  <add name="Text"  
                     type="System.Diagnostics.XmlWriterTraceListener"  
                     initializeData="SysTx.log"  
                     traceOutputOptions="Callstack" />  
               </listeners>  
            </source>  
         </sources>  
         <trace autoflush="true" indentsize="4">  
         </trace>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
     Bu özellik ayrıca sağlar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] izleme, olarak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de yararlanan <xref:System.Transactions> altyapı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetim ve Tanılama](../../../../docs/framework/wcf/diagnostics/index.md)  
 [İzlemeyi Yapılandırma](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [WS-AtomicTransaction Yapılandırma Yardımcı Programı (wsatConfig.exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
