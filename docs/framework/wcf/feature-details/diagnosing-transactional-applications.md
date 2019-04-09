---
title: İşlemsel Uygulamaları Tanılama
ms.date: 03/30/2017
ms.assetid: 4a993492-1088-4d10-871b-0c09916af05f
ms.openlocfilehash: aca5f95e2085dfadf06da35dfd86af72c0b6092d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59101718"
---
# <a name="diagnosing-transactional-applications"></a>İşlemsel Uygulamaları Tanılama
Bu konuda, bir işlem uygulama sorunlarını gidermek için Windows Communication Foundation (WCF) yönetim ve Tanılama özelliğini kullanmayı açıklar.  
  
## <a name="performance-counters"></a>Performans Sayaçları  
 WCF performans sayaçları, işlem, uygulamanızın performansını ölçmek standart sunmaktadır. Daha fazla bilgi için [performans sayaçları](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md).  
  
 Performans sayaçları için üç farklı düzeyde kapsamlı: Hizmet, uç nokta ve işlem aşağıdaki tabloda açıklandığı gibi.  
  
### <a name="service-performance-counters"></a>Hizmet Performansı Sayaçları  
  
|Performans sayacı|Açıklama|  
|-------------------------|-----------------|  
|Akışı Yapılan İşlemler|Bu hizmet işlemleri için aktarılan işlem sayısı. Hizmete gönderilen iletinin bir işlem varsa dilediğiniz zaman bu sayaç artırılır.|  
|Saniyede Akışı Yapılan İşlem|Bu hizmet işlemleri için içinde saniyede akışı yapılan işlemler işlem sayısı. Hizmete gönderilen iletinin bir işlem varsa dilediğiniz zaman bu sayaç artırılır.|  
|Uygulaması Yapılan İşlemler|Operasyonlar sayısını, işlem sonucu bu hizmeti kaydedilmiş tamamlandı gerçekleştirdi. Bu işlemler altında çalışmanın tam olarak taahhüt eder. Kaynakları, işlemde çalışmanın uygun olarak güncelleştirilir.|  
|Uygulaması Yapılan İşlem/Saniye|Operasyonlar sayısını, işlem sonucu bu hizmet her saniye içinde kaydedilmiş tamamlandı gerçekleştirdi. Bu işlemler altında çalışmanın tam olarak taahhüt eder. Kaynakları, işlemde çalışmanın uygun olarak güncelleştirilir.|  
|İptal Edilen İşlem Yapılmış Operasyonlar|Uygulaması yapılan işlem sayısı, işlem bu hizmette iptal edildi sonucu tamamlandı gerçekleştirdi. Bu işlemler altında yapılan çalışma geri alınır. Kaynakları, önceki durumlarına geri alınır.|  
|Uygulanıp Durdurulan İşlem/Saniye|Uygulaması yapılan işlem sayısı, işlem bu hizmette her saniye içinde iptal sonucu tamamlandı gerçekleştirdi. Bu işlemler altında yapılan çalışma geri alınır. Kaynakları, önceki durumlarına geri alınır.|  
|Şüpheli Uygulanan İşlemler|Uygulaması yapılan işlem sayısı, işlem bu hizmette şüpheli sonucu tamamlandı gerçekleştirdi. Sonucu şüpheli ile çalışmanın belirsiz bir durumda. Kaynakları sonucunu tutulur.|  
|Şüpheli Uygulanan İşlem/Saniye|Uygulaması yapılan işlem sayısı, işlem bu hizmette şüpheli sonucu her saniye içinde tamamlandı gerçekleştirdi. Sonucu şüpheli ile çalışmanın belirsiz bir durumda. Kaynakları sonucunu tutulur.|  
  
### <a name="endpoint-performance-counters"></a>Uç Noktası Performans Sayaçları  
  
|Performans sayacı|Açıklama|  
|-------------------------|-----------------|  
|Akışı Yapılan İşlemler|Bu uç noktada işlemlerine aktarılan işlem sayısı. Bu sayaç, bir işlem bitiş noktasına gönderilen ileti varsa dilediğiniz zaman artırılır.|  
|Saniyede Akışı Yapılan İşlem|Bu uç noktada işlemlerine içinde saniyede akışı yapılan işlemler işlem sayısı. Bu sayaç, bir işlem bitiş noktasına gönderilen ileti varsa dilediğiniz zaman artırılır.|  
  
### <a name="operation-performance-counters"></a>İşlem Performansı Sayaçları  
  
|Performans sayacı|Açıklama|  
|-------------------------|-----------------|  
|Akışı Yapılan İşlemler|Bu uç noktada işlemlerine aktarılan işlem sayısı. Bu sayaç, bir işlem bitiş noktasına gönderilen ileti varsa dilediğiniz zaman artırılır.|  
|Saniyede Akışı Yapılan İşlem|Bu uç noktada işlemlerine içinde saniyede akışı yapılan işlemler işlem sayısı. Bu sayaç, bir işlem bitiş noktasına gönderilen ileti varsa dilediğiniz zaman artırılır.|  
  
## <a name="windows-management-instrumentation"></a>Windows Yönetim Araçları  
 WCF hizmet denetimi veri WCF Windows Yönetim Araçları (WMI) sağlayıcısı üzerinden çalışma zamanında kullanıma sunar. WMI veri erişimi hakkında daha fazla bilgi için bkz. [tanılama için Windows Yönetim araçları kullanarak](../../../../docs/framework/wcf/diagnostics/wmi/index.md).  
  
 WMI özellikleri salt okunur bir dizi hizmet için uygulanan işlem ayarlarını belirtin. Aşağıdaki tablolarda tüm bu ayarlar listelenmektedir.  
  
 Bir hizmet üzerinde `ServiceBehaviorAttribute` aşağıdaki özelliklere sahiptir.  
  
|Ad|Tür|Açıklama|  
|----------|----------|-----------------|  
|ReleaseServiceInstanceOnTransactionComplete|Boole değeri|Geçerli işlem tamamlandıktan sonra hizmet nesnesi geri olup olmadığını belirtir.|  
|TransactionAutoCompleteOnSessionClose|Boole değeri|Geçerli oturumu kapattığında bekleyen işlem tamamlanıp tamamlanmadığını belirtir.|  
|TransactionIsolationLevel|Geçerli değerini içeren bir dize <xref:System.Transactions.IsolationLevel> sabit listesi.|Bu hizmet destekleyen işlem yalıtım düzeyi belirtir.|  
|TransactionTimeout|<xref:System.DateTime>|İçinde bir işlemin tamamlanması gereken süresi belirtir.|  
  
 `ServiceTimeoutsBehavior` Şu özelliğe sahip.  
  
|Ad|Tür|Açıklama|  
|----------|----------|-----------------|  
|TransactionTimeout|<xref:System.DateTime>|İçinde bir işlemin tamamlanması gereken süresi belirtir.|  
  
 Bir bağlama üzerinde `TransactionFlowBindingElement` aşağıdaki özelliklere sahiptir.  
  
|Ad|Tür|Açıklama|  
|----------|----------|-----------------|  
|transactionProtocol|Geçerli değerini içeren bir dize <xref:System.ServiceModel.TransactionProtocol> türü.|Bir işlem akışında kullanılacak işlem protokolünü belirler.|  
|transactionFlow|Boole değeri|Gelen işlem akışı etkin olup olmadığını belirtir.|  
  
 Bir işlem üzerinde `OperationBehaviorAttribute` aşağıdaki özelliklere sahiptir:  
  
|Ad|Tür|Açıklama|  
|----------|----------|-----------------|  
|TransactionAutoComplete|Boole değeri|İşlenmeyen özel durumlar oluşursa otomatik olarak geçerli hareketi tamamlamak belirtir.|  
|TransactionScopeRequired|Boole değeri|İşlemi bir işlem gerekli olup olmadığını belirtir.|  
  
 Bir işlem üzerinde `TransactionFlowAttribute` aşağıdaki özelliklere sahiptir.  
  
|Ad|Tür|Açıklama|  
|----------|----------|-----------------|  
|TransactionFlowOption|Geçerli değerini içeren bir dize <xref:System.ServiceModel.TransactionFlowOption> sabit listesi.|Akış için hareket gereklidir kapsamı belirtir.|  
  
## <a name="tracing"></a>İzleme  
 İzlemeleri izlemek ve işlem tabanlı uygulamalarınızı hataları analiz etmek etkinleştirin. Aşağıdaki yöntemleri kullanarak izlemeyi etkinleştirebilirsiniz:  
  
-   Standart WCF izleme  
  
     Bu tür bir izleme herhangi bir WCF uygulama izleme aynıdır. Daha fazla bilgi için [yapılandırma izleme](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md).  
  
-   WS-AtomicTransaction izleme  
  
     WS-AtomicTransaction izlemeyi kullanarak etkinleştirilebilir [WS-AtomicTransaction yapılandırma yardımcı programı (wsatConfig.exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md). Bu izleme, işlemler ve katılımcıları içinde bir sistem durumu hakkında Öngörüler sağlar. Ayrıca iç hizmet modeli izlemeyi etkinleştirmek için ayarlayabileceğiniz `HKLM\SOFTWARE\Microsoft\WSAT\3.0\ServiceModelDiagnosticTracing` kayıt defteri anahtarı geçerli değerini <xref:System.Diagnostics.SourceLevels> sabit listesi. İleti günlüğe kaydetme diğer WCF uygulamaları aynı şekilde etkinleştirebilirsiniz.  
  
-   `System.Transactions` izleme  
  
     OleTransactions protokolünü kullanırken, protokol iletileri izlenemez. İzleme desteği <xref:System.Transactions> altyapı sağlar (OleTransactions kullanır) kullanıcılar hareketlerle gerçekleşen olayları görüntülemek izin verir. İzlemeyi etkinleştirmek için bir <xref:System.Transactions> uygulama, aşağıdaki kodda dahil `App.config` yapılandırma dosyası.  
  
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
  
     WCF de yararlanır gibi bu WCF izleme sağlar <xref:System.Transactions> altyapı.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetim ve Tanılama](../../../../docs/framework/wcf/diagnostics/index.md)
- [İzlemeyi Yapılandırma](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)
- [WS-AtomicTransaction Yapılandırma Yardımcı Programı (wsatConfig.exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
