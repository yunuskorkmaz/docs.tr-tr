---
title: "Tanılama izleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 28e77a63-d20d-4b6a-9caf-ddad86550427
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 59e91b76245c7bdfd40f6fc449edbbcd47449f3f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="diagnostic-traces"></a>Tanılama izleri
İzlemeler uygulama yürütmesi sırasında oluşturulan belirli iletileri yayımlanmasıyla ' dir. İzleme kullanırken, toplama ve gönderilen iletileri kaydetmek için bir mekanizma olması gerekir. İzleme iletileri dinleyicileri tarafından alınır. Toplamak, depolamak ve izleme iletilerini yönlendirmek için bir dinleyici amacı budur. Dinleyicileri İzleme çıktısı günlüğü, pencere veya metin dosyası gibi uygun bir hedefe yönlendirir.  
  
 Bu tür bir dinleyici <xref:System.Diagnostics.DefaultTraceListener>, otomatik olarak oluşturulur ve izleme etkinleştirildiğinde başlatıldı. Herhangi bir ek kaynağına yönlendirilmesi için izleme çıktısı istiyorsanız oluşturmalı ve ek izleme dinleyicileri başlatılamıyor. Oluşturduğunuz dinleyicileri ihtiyaçlarınıza uygun olmalıdır. Örneğin, metin kaydı tüm izleme çıktısını isteyebilirsiniz. Bu durumda, tüm çıktı yazdı etkinleştirildiğinde yeni bir metin dosyası için bir dinleyici oluşturun. Diğer yandan, yalnızca uygulama yürütme sırasında çıkış görüntülemek isteyebilirsiniz. Bu durumda, tüm çıkış için bir konsol penceresi yönlendirilmiş bir dinleyici oluşturabilirsiniz. <xref:System.Diagnostics.EventLogTraceListener> İzleme çıktısı için bir olay günlüğüne yönlendirebilir ve <xref:System.Diagnostics.TextWriterTraceListener> İzleme çıktısı bir akışa yazabilirsiniz.  
  
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
  
 <xref:System.Transactions>izlemeler "System.Transactions" adlı kaynak yazılır. Kullanabileceğiniz `add` adını ve kullanmak istediğiniz İzleme dinleyicisi türünü belirtmek için. Bizim örnek yapılandırmada, biz dinleyicisi "tx" adlı ve standart .NET Framework İzleme dinleyicisi eklenen (<xref:System.Diagnostics.XmlWriterTraceListener>) istiyoruz kullanılacak türü. Kullanım `initializeData` günlük dosyasının adı için bu dinleyici ayarlamak için. Buna ek olarak, bir basit dosya adı için tam yol yerine kullanabilirsiniz.  
  
 Her izleme ileti türü önem derecesini belirtmek için bir düzeyi atanır. App-etki alanı izleme düzeyi eşit veya daha düşük bir olay türü düzeyini ise, bu mesajı oluşturulur. İzleme düzeyini tarafından denetlenen `switchValue` yapılandırma dosyasında ayarlama. Tanılama izleme iletilerini kaynaklarıyla ilişkili düzeyleri aşağıdaki tabloda tanımlanır.  
  
|İzleme düzeyi|Açıklama|  
|-----------------|-----------------|  
|Kritik|Aşağıdaki gibi önemli hataları oluştu:<br /><br /> -Kullanıcı işlevindeki bir hemen kaybına neden olabilir bir hata oluştu.<br />-Yönetici işlev kaybı olmaması için işlem yapmanızı gerektiren bir olay.<br />-Kod askıda kalır.<br />-Bu izleme düzeyi, kritik diğer izlemeleri yorumlanması için yeterli içerik de sağlayabilirsiniz. Bu işlemleri için ciddi bir arıza öndeki dizisini tanımasına yardımcı olabilir.|  
|Hata|Bir hata (örneğin, geçersiz yapılandırma veya ağ davranış gibi) kullanıcı işlevselliği kaybına neden.|  
|Uyarı|Bir koşul bulunduğunu daha sonra bir hata veya kritik hatası (başarısız veya bir sınır yaklaştığı Örneğin, ayırma) neden olabilir. Normal kullanıcı kodundan (örneğin, işlem iptal edildi, zaman aşımı, kimlik doğrulama başarısız oldu) hatalarının işlenmesini de bir uyarı oluşturabilir.|  
|Bilgiler|İzleme ve tanılama sistem durumu, performans ölçüm veya profil oluşturma için faydalı iletileri üretilir. Bu işlem ve kaydı ömrü gibi olaylar oluşturulmakta veya kaydedilmiş, önemli bir sınır aşma veya önemli miktarda kaynak ayırma bir işlem içerebilir. Bir geliştirici sonra gibi bilgileri kapasite planlama ve performans yönetimi için kullanabilir.|  
  
## <a name="trace-codes"></a>İzleme kodları  
 Aşağıdaki tablo tarafından oluşturulan izleme kodlarını listeler <xref:System.Transactions> altyapı. İzleme kodu tanıtıcısı tablosuna dahil olan <xref:System.Diagnostics.EventTypeFilter.EventType%2A> izleme ve içinde yer alan ek veriler için numaralandırma düzeyi **TraceRecord** izleme için. Ayrıca, izleme karşılık gelen izleme düzeyini ayrıca depolanan **TraceRecord**.  
  
|TraceCode|Olay türü|TraceRecord fazladan verileri|  
|---------------|---------------|-------------------------------|  
|TransactionCreated|Bilgi|TransactionTraceId|  
|TransactionPromoted|Bilgi|Yerel TransactionTraceId, dağıtılmış TransactionTraceId|  
|EnlistmentCreated|Bilgi|TransactionTraceId, EnlistmentTraceId, EnlistmentType (dayanıklı/volatile) EnlistmentOptions|  
|EnlistmentCallbackNegative|Uyarı|TransactionTraceId, EnlistmentTraceId,<br /><br /> Geri çağırma (forcerollback/iptal/nin şüpheli işlemi olmadığından)|  
|TransactionRollbackCalled|Uyarı|TransactionTraceId|  
|TransactionAborted|Uyarı|TransactionTraceId|  
|TransactionInDoubt|Uyarı|TransactionTraceId|  
|TransactionScopeCreated|Bilgi|TransactionScopeResult aşağıdaki olabilir:<br /><br /> -Yeni bir işlem.<br />-İşlem geçirildi.<br />-Bağımlı işlem geçirildi.<br />-Geçerli hareket kullanarak.<br />-İşlem yok.<br /><br /> Yeni geçerli TransactionTraceId|  
|TransactionScopeDisposed|Bilgi|Kapsamın TransactionTraceId "geçerli işlem beklenen".|  
|TransactionScopeIncomplete|Uyarı|Kapsamın TransactionTraceId "geçerli işlem beklenen".|  
|TransactionScopeNestedIncorrectly|Uyarı|Kapsamın TransactionTraceId "geçerli işlem beklenen".|  
|TransactionScopeCurrentTransactionChanged|Uyarı|Eski geçerli TransactionTraceId, diğer TransactionTraceId|  
|TransactionScopeTimeout|Uyarı|Kapsamın TransactionTraceId "geçerli işlem beklenen".|  
|DependentCloneCreated|Bilgi|TransactionTraceId, bağımlı işlem türünü (RollbackIfNotComplete/BlockCommitUntilComplete) oluşturuldu|  
|DependentCloneComplete|Bilgi|TransactionTraceId|  
|RecoveryComplete'in|Bilgi|Kaynak Yöneticisi GUID (değerinden tabanı)|  
|Reenlist|Bilgi|Kaynak Yöneticisi GUID (değerinden tabanı)|  
|TransactionSerialized|Bilgi|TransactionTraceId.|  
|TransactionException|Hata|Özel durum iletisi|  
|InvalidOperationException|Hata|Özel durum iletisi|  
|InternalError|Kritik|Özel durum iletisi|  
|TransferEvent||Ne zaman bir işlem serisi veya den yükseltilen bir <xref:System.Transactions> dağıtılmış bir işlem, geçerli etkinlik kimliğini ExecutionContext ve dağıtılmış işlem Kimliğini yazılır.<br /><br /> DTC geri yönetilen koda aradığında, dağıtılmış işlem kimliği olarak ActivityID ExecutionContext içinde geri çağırma süresince ayarlanır.|  
|ConfiguredDefaultTimeoutAdjusted|Uyarı|Ek veri yok|  
|TransactionTimeout|Uyarı|İşlemin zaman aşımına uğradı TransactionTraceId.|  
  
 Önceki ek veriler öğelerin her biri için XML Şeması aşağıdaki biçime sahiptir.  
  
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
 Bir yönetici olarak izlemeyi etkinleştirdiğinizde, hassas bilgiler herkes tarafından izlenen bir izleme günlüğü varsayılan olarak yazılmış olabilir. Tüm olası güvenlik tehdidi azaltmak için izleme günlüğü paylaşım ve dosya sistemi erişim izinleri tarafından denetlenen güvenli bir yerde depolamanız gerekir.
