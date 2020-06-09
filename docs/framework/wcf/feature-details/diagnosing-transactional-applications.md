---
title: İşlemsel Uygulamaları Tanılama
ms.date: 03/30/2017
ms.assetid: 4a993492-1088-4d10-871b-0c09916af05f
ms.openlocfilehash: fb3a83083e876cf697621ba70dcf7dd67636f83a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599223"
---
# <a name="diagnosing-transactional-applications"></a>İşlemsel Uygulamaları Tanılama
Bu konuda, bir işlem uygulamasının sorunlarını gidermek için Windows Communication Foundation (WCF) yönetimi ve tanılama özelliğinin nasıl kullanılacağı açıklanmaktadır.  
  
## <a name="performance-counters"></a>Performans Sayaçları  
 WCF, işlemsel uygulamanızın performansını ölçmenize yönelik standart bir dizi performans sayacı sağlar. Daha fazla bilgi için bkz. [performans sayaçları](../diagnostics/performance-counters/index.md).  
  
 Performans sayaçları, aşağıdaki tablolarda açıklandığı gibi üç farklı düzeye sahiptir: hizmet, uç nokta ve işlem.  
  
### <a name="service-performance-counters"></a>Hizmet Performansı Sayaçları  
  
|Performans sayacı|Açıklama|  
|-------------------------|-----------------|  
|Akışı Yapılan İşlemler|Bu hizmette işlemlere akan işlem sayısı. Bu sayaç, hizmete gönderilen iletide bir işlem olduğunda artırılır.|  
|Saniyede Akışı Yapılan İşlem|Her saniye içinde bu hizmette işlemlere akan işlem sayısı. Bu sayaç, hizmete gönderilen iletide bir işlem olduğunda artırılır.|  
|Uygulaması Yapılan İşlemler|İşlemi bu hizmette yürütülen sonuç ile tamamlanan işlem yapılan işlem sayısı. Bu gibi işlemler altında gerçekleştirilen iş tam olarak kaydedilir. Kaynaklar, işlem sırasında yapılan işe uygun olarak güncelleştirilir.|  
|Uygulaması Yapılan İşlem/Saniye|İşlemi gerçekleştirilen işlem sayısı, her saniye içinde bu hizmette kaydedilen sonuç ile tamamlandı. Bu gibi işlemler altında gerçekleştirilen iş tam olarak kaydedilir. Kaynaklar, işlem sırasında yapılan işe uygun olarak güncelleştirilir.|  
|İptal Edilen İşlem Yapılmış Operasyonlar|İşlemi bu hizmette durdurulan sonuç ile tamamlanan işlem yapılan işlem sayısı. Bu gibi işlemler altında gerçekleştirilen iş geri alınır. Kaynaklar önceki durumlarına geri döndürülüyor.|  
|Uygulanıp Durdurulan İşlem/Saniye|İşlemi gerçekleştirilen işlem sayısı, her saniye içinde bu hizmette durdurulan sonuç ile tamamlandı. Bu gibi işlemler altında gerçekleştirilen iş geri alınır. Kaynaklar önceki durumlarına geri döndürülüyor.|  
|Şüpheli Uygulanan İşlemler|İşlemi bu hizmette şüpheli bir sonuç ile tamamlanan işlem yapılan işlem sayısı. Şüpheli bir sonuç ile yapılan iş, belirsiz bir durumda. Kaynaklar bekleyen sonuçları tutuluyor.|  
|Şüpheli Uygulanan İşlem/Saniye|İşlemi gerçekleştirilen işlem sayısı, her saniye içinde bu hizmette şüpheli bir sonuç ile tamamlanmış olan işlem sayısıdır. Şüpheli bir sonuç ile yapılan iş, belirsiz bir durumda. Kaynaklar bekleyen sonuçları tutuluyor.|  
  
### <a name="endpoint-performance-counters"></a>Uç Noktası Performans Sayaçları  
  
|Performans sayacı|Açıklama|  
|-------------------------|-----------------|  
|Akışı Yapılan İşlemler|Bu uç noktada işlemlere akan işlem sayısı. Bu sayaç, uç noktaya gönderilen iletide bir işlem olduğunda artırılır.|  
|Saniyede Akışı Yapılan İşlem|Her saniye içinde bu uç noktada işlemlere akan işlem sayısı. Bu sayaç, uç noktaya gönderilen iletide bir işlem olduğunda artırılır.|  
  
### <a name="operation-performance-counters"></a>İşlem Performansı Sayaçları  
  
|Performans sayacı|Açıklama|  
|-------------------------|-----------------|  
|Akışı Yapılan İşlemler|Bu uç noktada işlemlere akan işlem sayısı. Bu sayaç, uç noktaya gönderilen iletide bir işlem olduğunda artırılır.|  
|Saniyede Akışı Yapılan İşlem|Her saniye içinde bu uç noktada işlemlere akan işlem sayısı. Bu sayaç, uç noktaya gönderilen iletide bir işlem olduğunda artırılır.|  
  
## <a name="windows-management-instrumentation"></a>Windows Yönetim Araçları  
 WCF, bir hizmetin denetim verilerini bir WCF Windows Yönetim Araçları (WMI) sağlayıcısı aracılığıyla çalışma zamanında kullanıma sunar. WMI verilerine erişme hakkında daha fazla bilgi için bkz. [Tanılama için Windows Yönetim araçları kullanma](../diagnostics/wmi/index.md).  
  
 Bazı salt okunurdur WMI özellikleri, bir hizmet için uygulanan işlem ayarlarını gösterir. Aşağıdaki tablolarda bu ayarların hepsi listelenmektedir.  
  
 Bir hizmette, `ServiceBehaviorAttribute` aşağıdaki özelliklere sahiptir.  
  
|Name|Tür|Açıklama|  
|----------|----------|-----------------|  
|ReleaseServiceInstanceOnTransactionComplete|Boole|Geçerli işlem tamamlandığında hizmet nesnesinin geri dönüştürülüp dönüştürülmeyeceğini belirtir.|  
|TransactionAutoCompleteOnSessionClose|Boole|Geçerli oturum kapandığında bekleyen işlemlerin tamamlanıp tamamlanmadığını belirtir.|  
|TransactionIsolationLevel|Sabit listesinin geçerli bir değerini içeren bir dize <xref:System.Transactions.IsolationLevel> .|Bu hizmetin desteklediği işlem yalıtım düzeyini belirtir.|  
|Işlem zaman aşımı|<xref:System.DateTime>|Bir işlemin tamamlaması gereken süreyi belirtir.|  
  
 , `ServiceTimeoutsBehavior` Aşağıdaki özelliğe sahiptir.  
  
|Name|Tür|Açıklama|  
|----------|----------|-----------------|  
|Işlem zaman aşımı|<xref:System.DateTime>|Bir işlemin tamamlaması gereken süreyi belirtir.|  
  
 Bir bağlamada `TransactionFlowBindingElement` aşağıdaki özellikler vardır.  
  
|Name|Tür|Açıklama|  
|----------|----------|-----------------|  
|TransactionProtocol|Türün geçerli bir değerini içeren bir dize <xref:System.ServiceModel.TransactionProtocol> .|İşlem akışı sırasında kullanılacak işlem protokolünü belirtir.|  
|TransactionFlow|Boole|Gelen işlem akışının etkinleştirilip etkinleştirilmeyeceğini belirtir.|  
  
 Bir işlemde, `OperationBehaviorAttribute` aşağıdaki özelliklere sahiptir:  
  
|Name|Tür|Açıklama|  
|----------|----------|-----------------|  
|TransactionAutoComplete|Boole|İşlenmeyen özel durumlar oluşursa, geçerli işlemin otomatik olarak kaydedilip edilmeyeceğini belirtir.|  
|TransactionScopeRequired|Boole|İşlemin bir işlem gerektirip gerektirmediğini belirtir.|  
  
 Bir işlemde, `TransactionFlowAttribute` aşağıdaki özelliklere sahiptir.  
  
|Name|Tür|Açıklama|  
|----------|----------|-----------------|  
|TransactionFlowOption|Sabit listesinin geçerli bir değerini içeren bir dize <xref:System.ServiceModel.TransactionFlowOption> .|İşlem akışının gerekli olduğu kapsamı belirtir.|  
  
## <a name="tracing"></a>İzleme  
 İzlemeler, işlem uygulamalarınızda hataları izlemenizi ve analiz etmenize olanak tanır. İzlemeyi aşağıdaki yöntemlerle etkinleştirebilirsiniz:  
  
- Standart WCF izleme  
  
     Bu tür bir izleme, herhangi bir WCF uygulamasını izlemenin aynısıdır. Daha fazla bilgi için bkz. [Izlemeyi yapılandırma](../diagnostics/tracing/configuring-tracing.md).  
  
- WS-AtomicTransaction izleme  
  
     WS-AtomicTransaction izleme, [WS-AtomicTransaction Yapılandırma yardımcı programı (wsatConfig. exe)](../ws-atomictransaction-configuration-utility-wsatconfig-exe.md)kullanılarak etkinleştirilebilir. Bu izleme, bir sistem içindeki işlemlerin ve katılımcıların durumu hakkında öngörü sağlar. Ayrıca, iç hizmet modeli izlemeyi etkinleştirmek için `HKLM\SOFTWARE\Microsoft\WSAT\3.0\ServiceModelDiagnosticTracing` kayıt defteri anahtarını sabit listesinin geçerli bir değeri olarak ayarlayabilirsiniz <xref:System.Diagnostics.SourceLevels> . İleti günlüğünü diğer WCF uygulamalarıyla aynı şekilde etkinleştirebilirsiniz.  
  
- `System.Transactions`izleniyor  
  
     OleTransactions protokolü kullanılırken protokol iletileri izlenemez. Altyapıyı sağlayan izleme desteği <xref:System.Transactions> (OleTransactions kullanan), kullanıcıların işlemlerde gerçekleşen olayları görüntülemesine olanak tanır. Bir uygulama için izlemeyi etkinleştirmek üzere <xref:System.Transactions> yapılandırma dosyasına aşağıdaki kodu ekleyin `App.config` .  
  
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
  
     WCF Ayrıca altyapıyı de kullanıyorsa, bu da WCF izlemeyi da sunar <xref:System.Transactions> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetim ve tanılama](../diagnostics/index.md)
- [İzlemeyi Yapılandırma](../diagnostics/tracing/configuring-tracing.md)
- [WS-AtomicTransaction Yapılandırma Yardımcı Programı (wsatConfig.exe)](../ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
