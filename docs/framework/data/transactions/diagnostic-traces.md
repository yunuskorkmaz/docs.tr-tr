---
title: Tanılama İzlemeleri
ms.date: 03/30/2017
ms.assetid: 28e77a63-d20d-4b6a-9caf-ddad86550427
ms.openlocfilehash: 76712710bf42f498ba859c7b1cd18a261387078c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174426"
---
# <a name="diagnostic-traces"></a>Tanılama İzlemeleri
İzlemeler, uygulama yürütme sırasında oluşturulan belirli iletilerin yayımıdır. İzlemeyi kullanırken, gönderilen iletileri toplamak ve kaydetmek için bir mekanizmanız olmalıdır. İzleme iletileri dinleyiciler tarafından alınır. Dinleyicinin amacı, izleme iletilerini toplamak, depolamak ve yönlendirmektir. Dinleyiciler izleme çıktısını günlük, pencere veya metin dosyası gibi uygun bir hedefe yönlendirir.  
  
 Böyle bir dinleyici, <xref:System.Diagnostics.DefaultTraceListener>, , otomatik olarak oluşturulur ve izleme etkinleştirildiğinde baş harfe. İzleme çıktının herhangi bir ek kaynağa yönlendirilmesini istiyorsanız, ek izleme dinleyicileri oluşturmanız ve başlatmanız gerekir. Oluşturduğunuz dinleyicileri ihtiyaçlarınıza uygun olmalıdır. Örneğin, tüm izleme çıktısının metin kaydını isteyebilirsiniz. Bu durumda, tüm çıktı yazdı etkinleştirildiğinde yeni bir metin dosyası için bir dinleyici oluşturun. Diğer yandan, yalnızca uygulama yürütme sırasında çıkış görüntülemek isteyebilirsiniz. Bu durumda, tüm çıkış için bir konsol penceresi yönlendirilmiş bir dinleyici oluşturabilirsiniz. İzleme <xref:System.Diagnostics.EventLogTraceListener> çıktısını olay günlüğüne yönlendirebilir <xref:System.Diagnostics.TextWriterTraceListener> ve bir akışa izleme çıktısı yazabilir.  
  
## <a name="enabling-tracing"></a>İzlemeyi Etkinleştirme  
 İşlem işleme sırasında izlemeleri etkinleştirmek için uygulamanızın yapılandırma dosyasını düzenlemeniz gerekir. Bir örnek verilmiştir.  
  
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
  
 <xref:System.Transactions>izleri "System.Transactions" adlı kaynağa yazılır. Kullanmak istediğiniz `add` izleme dinleyicisinin adını ve türünü belirtmek için kullanabilirsiniz. Örnek yapılandırmamızda Dinleyiciye "tx" adını verdik ve standart .NET Framework<xref:System.Diagnostics.XmlWriterTraceListener>trace dinleyicisini ( ) kullanmak istediğimiz tür olarak ekledik. Kullanım `initializeData` günlük dosyasının adı için bu dinleyici ayarlamak için. Buna ek olarak, bir basit dosya adı için tam yol yerine kullanabilirsiniz.  
  
 Her izleme iletisi türüne önem derecesini belirtmek için bir düzey atanır. Uygulama etki alanının izleme düzeyi olay türü düzeyinden eşit veya daha düşükse, bu ileti oluşturulur. İzleme düzeyi yapılandırma dosyasındaki `switchValue` ayar tarafından denetlenir. Tanılama izleme iletileri ile ilişkili düzeyleri aşağıdaki tabloda tanımlanır.  
  
|İzleme Düzeyi|Açıklama|  
|-----------------|-----------------|  
|Kritik|Aşağıdaki gibi önemli hataları oluştu:<br /><br /> - Kullanıcı işlevselliğinde ani bir kayba neden olabilecek bir hata.<br />- İşlev kaybını önlemek için yöneticinin harekete geçmesini gerektiren bir olay.<br />- Kod askıda kalır.<br />- Bu izleme düzeyi aynı zamanda diğer kritik izleri yorumlamak için yeterli bağlam sağlayabilir. Bu işlemleri için ciddi bir arıza öndeki dizisini tanımasına yardımcı olabilir.|  
|Hata|Bir hata (örneğin, geçersiz yapılandırma veya ağ davranış gibi) kullanıcı işlevselliği kaybına neden.|  
|Uyarı|Bir koşul bulunduğunu daha sonra bir hata veya kritik hatası (başarısız veya bir sınır yaklaştığı Örneğin, ayırma) neden olabilir. Kullanıcı kodundan hataların normal olarak işlenmesi (örneğin, işlem iptal edildi, zaman eklenmeleri, kimlik doğrulama başarısız oldu) da bir uyarı oluşturabilir.|  
|Bilgi|İzleme ve tanılama sistem durumu, performans ölçüm veya profil oluşturma için faydalı iletileri üretilir. Bunlar, oluşturulan veya işlenen bir işlem, önemli bir sınırın geçişi veya önemli kaynakların tahsisi gibi işlem ve kayıt ömür boyu olayları içerebilir. Bir geliştirici sonra gibi bilgileri kapasite planlama ve performans yönetimi için kullanabilir.|  
  
## <a name="trace-codes"></a>İzleme Kodları  
 Aşağıdaki tablo, <xref:System.Transactions> altyapı tarafından oluşturulan izleme kodlarını listeler. Tabloda izleme kodu tanımlayıcısı, <xref:System.Diagnostics.EventTypeFilter.EventType%2A> izleme için numaralandırma düzeyi ve izleme için **TraceRecord'da** bulunan ek veriler yer almaktadır. Buna ek olarak, izlemenin karşılık gelen izleme düzeyi de **TraceRecord**saklanır.  
  
|İzleme Kodu|Olay türü|TraceRecord'da ekstra veri|  
|---------------|---------------|-------------------------------|  
|İşlemLer Oluşturuldu|Bilgi|İşlemTraceId|  
|Tanıtılan İşlemler|Bilgi|Yerel İşlemTraceId, Dağıtılmış İşlemTraceId|  
|EnlistmentCreated|Bilgi|TransactionTraceId, EnlistmentTraceId, EnlistmentType (dayanıklı/uçucu), EnlistmentOptions|  
|EnlistmentCallbackNegative|Uyarı|TransactionTraceId, EnlistmentTraceId,<br /><br /> Geri çağırma (forcerollback/iptal/nin şüpheli işlemi olmadığından)|  
|İşlemRollbackCalled|Uyarı|İşlemTraceId|  
|İşlemİptal edİlM|Uyarı|İşlemTraceId|  
|İşlem Şüphe|Uyarı|İşlemTraceId|  
|İşlemKapsamı Oluşturuldu|Bilgi|TransactionScopeResult, aşağıdakilerden hangisi olabilir:<br /><br /> - Yeni işlem.<br />- İşlem geçti.<br />- Bağımlı işlem geçti.<br />- Geçerli hareketi kullanma.<br />- İşlem yok.<br /><br /> yeni geçerli TransactionTraceId|  
|TransactionScopeDisposed|Bilgi|Kapsamın "beklenen" geçerli hareketinin TransactionTraceId'i.|  
|İşlemScopeEksik|Uyarı|Kapsamın "beklenen" geçerli hareketinin TransactionTraceId'i.|  
|İşlemScopeNestedYanlış|Uyarı|Kapsamın "beklenen" geçerli hareketinin TransactionTraceId'i.|  
|TransactionScopeCurrentTransactionChanged|Uyarı|Eski cari TransactionTraceId, diğer TransactionTraceId|  
|TransactionScopeTimeout|Uyarı|Kapsamın "beklenen" geçerli hareketinin TransactionTraceId'i.|  
|DependentCloneCreated|Bilgi|TransactionTraceId, oluşturulan bağımlı işlem türü (RollbackIfNotComplete/BlockCommitUntilComplete)|  
|DependentCloneComplete|Bilgi|İşlemTraceId|  
|RecoveryComplete'in|Bilgi|Kaynak Yöneticisi GUID (değerinden tabanı)|  
|Reenlist|Bilgi|Kaynak Yöneticisi GUID (değerinden tabanı)|  
|İşlemSerileştirilmiş|Bilgi|İşlemTraceId.|  
|Transactionexception|Hata|Özel durum iletisi|  
|InvalidOperationException|Hata|Özel durum iletisi|  
|InternalError|Kritik|Özel durum iletisi|  
|TransferEtkinliği||Bir hareket deserialized veya bir <xref:System.Transactions> hareket dağıtılan bir terfi, Yürütme Bağlamından geçerli ActivityID ve dağıtılmış hareket kimliği yazılır.<br /><br /> DTC yönetilen koda geri çağırdığında, dağıtılmış hareket kimliği geri arama süresi boyunca Yürütme Bağlamında Etkinlik Kimliği olarak ayarlanır.|  
|ConfiguredDefaultTimeoutAdjusted|Uyarı|Ekstra veri yok|  
|İşlemZaman Ları|Uyarı|İşlemin TransactionTraceId'i zaman doldu.|  
  
 Önceki ek veri öğelerinin her biri için XML şeması aşağıdaki biçime sahiptir.  
  
### <a name="transactiontraceidentifier"></a>İşlemTraceIdentifier  
 `<TransactionTraceIdentifier>`  
  
 `<TransactionIdentifier >`  
  
 `string representation of transaction id`  
  
 `</TransactionIdentifier>`  
  
 `< CloneIdentifier >`  
  
 `the clone id number`  
  
 `</CloneIdentifier>`  
  
 `</TransactionTraceIdentifier>`  
  
### <a name="enlistmenttraceidentifier"></a>Askere AlmaTraceIdentifier  
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
  
## <a name="security-issues-for-tracing"></a>İzleme için Güvenlik Sorunları  
 Yönetici olarak izlemeyi açtığınızda, hassas bilgiler varsayılan olarak genel olarak görüntülenebilir bir izleme günlüğüne yazılabilir. Olası güvenlik tehditlerini azaltmak için, izleme günlüğünü paylaşım ve dosya sistemi erişim izinleri tarafından denetlenen güvenli bir konumda depolamayı düşünmelisiniz.
