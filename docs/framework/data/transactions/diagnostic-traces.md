---
title: Tanılama İzlemeleri
ms.date: 03/30/2017
ms.assetid: 28e77a63-d20d-4b6a-9caf-ddad86550427
ms.openlocfilehash: 56f79fb9140785188996cc413eca4dd530037ccd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934803"
---
# <a name="diagnostic-traces"></a>Tanılama İzlemeleri
Uygulama yürütme sırasında oluşturulan özel iletilerinin yayımlama izlemeleri var. İzleme kullanırken, toplama ve gönderilen iletilerin kaydetmek için bir mekanizma olması gerekir. İzleme iletilerini dinleyicileri tarafından alınır. Toplamak, depolamak ve izleme iletilerini yönlendirmek için bir dinleyici amacı olan. Dinleyiciler bir günlük, pencere veya metin dosyası gibi uygun bir hedef izleme çıkışa doğrudan.  
  
 Tür bir dinleyici <xref:System.Diagnostics.DefaultTraceListener>, otomatik olarak oluşturulur ve izleme etkin olduğunda başlatılır. Herhangi bir ek kaynaklar için yönlendirilmesine İzleme çıkışı istiyorsanız, oluşturun ve ek izleme dinleyicileri başlatır. Oluşturduğunuz dinleyicileri ihtiyaçlarınıza uygun olmalıdır. Örneğin, bir metin kayıt tüm izleme çıkış isteyebilirsiniz. Bu durumda, tüm çıktı yazdı etkinleştirildiğinde yeni bir metin dosyası için bir dinleyici oluşturun. Diğer yandan, yalnızca uygulama yürütme sırasında çıkış görüntülemek isteyebilirsiniz. Bu durumda, tüm çıkış için bir konsol penceresi yönlendirilmiş bir dinleyici oluşturabilirsiniz. <xref:System.Diagnostics.EventLogTraceListener> Bir olay günlüğüne izleme çıkış yönlendirebilir ve <xref:System.Diagnostics.TextWriterTraceListener> İzleme çıkışı bir akışa yazabilirsiniz.  
  
## <a name="enabling-tracing"></a>İzlemeyi etkinleştirme  
 İşlem sırasında izlemeleri etkinleştirmek için uygulamanızın yapılandırma dosyasını düzenlemeniz gerekir. Bir örnek verilmiştir.  
  
```xml  
<configuration>  
<system.diagnostics>  
     <sources>  
          <source name="System.Transactions" switchValue="Warning">  
               <listeners>  
                    <add name="tx"   
                     type="System.Diagnostics.XmlWriterTraceListener"   
                     initializeData= "tx.log" />  
               </listeners>  
          </source>  
     </sources>  
</system.diagnostics>  
</configuration>  
```  
  
 <xref:System.Transactions> izlemeleri "System.Transactions" adlı kaynağına yazılır. Kullanabileceğiniz `add` adını ve kullanmak istediğiniz İzleme dinleyicisi türünü belirtmek için. Bizim örnek yapılandırma, biz dinleyicisi "tx" adlı ve standart .NET Framework İzleme dinleyicisi eklenen (<xref:System.Diagnostics.XmlWriterTraceListener>) olarak kullanılacak istiyoruz türü. Kullanım `initializeData` günlük dosyasının adı için bu dinleyici ayarlamak için. Buna ek olarak, bir basit dosya adı için tam yol yerine kullanabilirsiniz.  
  
 Her izleme iletisi türü önem derecesini belirtmek için bir düzeyi atanır. App-etki alanı izleme düzeyi eşit veya daha düşük bir olay türü düzeyi ise, bu ileti sonra oluşturulur. İzleme düzeyini tarafından denetlenir `switchValue` yapılandırma dosyasında ayarı. Tanılama izleme iletilerini ile ilişkili olan düzeyleri aşağıdaki tabloda tanımlanır.  
  
|İzleme düzeyi|Açıklama|  
|-----------------|-----------------|  
|Kritik|Aşağıdaki gibi önemli hataları oluştu:<br /><br /> -Hemen bir kaybına kullanıcı işlevindeki neden olabilir bir hata oluştu.<br />-İşlevsellik kaybını önlemek amacıyla eyleme geçmek bir yönetici gerektirir bir olay.<br />-Kod kapatır.<br />-Bu izleme düzeyini kritik diğer izlemeleri yorumlanması için yeterli bağlamı da sağlayabilir. Bu işlemleri için ciddi bir arıza öndeki dizisini tanımasına yardımcı olabilir.|  
|Hata|Bir hata (örneğin, geçersiz yapılandırma veya ağ davranış gibi) kullanıcı işlevselliği kaybına neden.|  
|Uyarı|Bir koşul bulunduğunu daha sonra bir hata veya kritik hatası (başarısız veya bir sınır yaklaştığı Örneğin, ayırma) neden olabilir. Kullanıcı kodu (örneğin, işlem iptal edildi, zaman aşımları, kimlik doğrulaması başarısız oldu) hatalarını normal işlenmesi ayrıca bir uyarı üretir.|  
|Bilgiler|İzleme ve tanılama sistem durumu, performans ölçüm veya profil oluşturma için faydalı iletileri üretilir. Bunlar, işlem ve liste ömrü gibi olayları oluşturulamaz veya kaydedilmiş, önemli kaynak ayırma veya önemli sınırının kesen bir işlem içerebilir. Bir geliştirici sonra gibi bilgileri kapasite planlama ve performans yönetimi için kullanabilir.|  
  
## <a name="trace-codes"></a>İzleme kodları  
 Aşağıdaki tablo tarafından oluşturulan izleme kodları listeler <xref:System.Transactions> altyapı. İzleme kodu tanımlayıcısını içerir tabloda <xref:System.Diagnostics.EventTypeFilter.EventType%2A> izleme ve içerdiği ek veriler için numaralandırma düzeyi **TraceRecord** izlemeye. Ayrıca, izleme karşılık gelen izleme düzeyini de depolanan **TraceRecord**.  
  
|TraceCode|Olay türü|Tracerecord ek verileri|  
|---------------|---------------|-------------------------------|  
|TransactionCreated|Bilgi|Transactiontraceıd|  
|TransactionPromoted|Bilgi|Yerel Transactiontraceıd, dağıtılmış Transactiontraceıd|  
|EnlistmentCreated|Bilgi|Transactiontraceıd, Enlistmenttraceıd, EnlistmentType (dayanıklı/geçici) EnlistmentOptions|  
|EnlistmentCallbackNegative|Uyarı|Transactiontraceıd, Enlistmenttraceıd,<br /><br /> Geri çağırma (forcerollback/iptal/nin şüpheli işlemi olmadığından)|  
|TransactionRollbackCalled|Uyarı|Transactiontraceıd|  
|TransactionAborted|Uyarı|Transactiontraceıd|  
|TransactionInDoubt|Uyarı|Transactiontraceıd|  
|TransactionScopeCreated|Bilgi|TransactionScopeResult şu olabilir:<br /><br /> -Yeni bir işlem.<br />-İşlem geçirildi.<br />-Bağımlı işlem geçirildi.<br />-Geçerli işlem kullanıyor.<br />-İşlem yok.<br /><br /> Yeni geçerli Transactiontraceıd|  
|TransactionScopeDisposed|Bilgi|Transactiontraceıd kapsamın, "geçerli işlem beklenen".|  
|TransactionScopeIncomplete|Uyarı|Transactiontraceıd kapsamın, "geçerli işlem beklenen".|  
|TransactionScopeNestedIncorrectly|Uyarı|Transactiontraceıd kapsamın, "geçerli işlem beklenen".|  
|TransactionScopeCurrentTransactionChanged|Uyarı|Eski geçerli Transactiontraceıd, diğer Transactiontraceıd|  
|TransactionScopeTimeout|Uyarı|Transactiontraceıd kapsamın, "geçerli işlem beklenen".|  
|DependentCloneCreated|Bilgi|Transactiontraceıd, bağımlı işlem türü (Rollbackıfnotcomplete/BlockCommitUntilComplete) oluşturuldu|  
|DependentCloneComplete|Bilgi|Transactiontraceıd|  
|RecoveryComplete'in|Bilgi|Kaynak Yöneticisi GUID (değerinden tabanı)|  
|Reenlist|Bilgi|Kaynak Yöneticisi GUID (değerinden tabanı)|  
|TransactionSerialized|Bilgi|Transactiontraceıd.|  
|TransactionException|Hata|Özel durum iletisi|  
|InvalidOperationException|Hata|Özel durum iletisi|  
|InternalError|Kritik|Özel durum iletisi|  
|TransferEvent||Ne zaman bir işlem seri durumdan veya öğesinden yükseltilmiş bir <xref:System.Transactions> işlem dağıtılmış bir ExecutionContext ve dağıtılmış işlem kimliği geçerli etkinlik kimliği yazılır.<br /><br /> DTC yönetilen koda geri çağırır dağıtılmış işlem kimliği olarak etkinlik kimliği ExecutionContext içinde geri çağırma süresi için ayarlanır.|  
|ConfiguredDefaultTimeoutAdjusted|Uyarı|Ek veri yok|  
|TransactionTimeout|Uyarı|Transactiontraceıd işlemin zaman aşımına uğradı.|  
  
 Önceki ek veri öğelerinin her biri için XML Şeması aşağıdaki biçime sahiptir.  
  
### <a name="transactiontraceidentifier"></a>TransactionTraceIdentifier  
 `<TransactionTraceIdentifier>`  
  
 `<TransactionIdentifier >`  
  
 `string representation of transaction id`  
  
 `</TransactionIdentifier>`  
  
 `< CloneIdentifier >`  
  
 `the clone id number`  
  
 `</CloneIdentifier>`  
  
 `</TransactionTraceIdentifier>`  
  
### <a name="enlistmenttraceidentifier"></a>EnlistmentTraceIdentifier  
 `<EnlistmentTraceIdentifier>`  
  
 `<ResourceManagerId>`  
  
 `string form of guid`  
  
 `</ResourceManagerId>`  
  
 `<TransactionTraceIdentifier>`  
  
 `<TransactionIdentifier >`  
  
 `string representation of transaction id`  
  
 `</TransactionIdentifier>`  
  
 `<CloneIdentifier >`  
  
 `the clone id number`  
  
 `</CloneIdentifier>`  
  
 `<TransactionTraceIdentifier>`  
  
 `<EnlistmentIdentifier>`  
  
 `the enlistment id number`  
  
 `</EnlistmentIdentifier>`  
  
 `</EnlistmentTraceIdentifier>`  
  
### <a name="resource-manager-identifier"></a>Kaynak Yöneticisi tanımlayıcısı  
 `<ResourceManagerId>`  
  
 `string form of guid`  
  
 `</ResourceManagerId>`  
  
## <a name="security-issues-for-tracing"></a>İzleme için güvenlik sorunları  
 Yönetici olarak izlemeyi etkinleştirdiğinizde, hassas bilgiler herkes tarafından izlenen bir izleme günlüğü varsayılan olarak yazılmış olabilir. Tüm olası bir güvenlik tehdidi azaltmak için izleme günlüğü paylaşımı ve dosya sistemi erişim izinleri tarafından denetlenen güvenli bir konumda depolamanız gerekir.
