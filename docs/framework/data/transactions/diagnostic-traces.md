---
title: Tanılama İzlemeleri
description: .NET 'teki tanılama izlemeleri hakkında bilgi edinin. İzlemeler, uygulama yürütme sırasında oluşturulan belirli iletilerin yayımlaması.
ms.date: 03/30/2017
ms.assetid: 28e77a63-d20d-4b6a-9caf-ddad86550427
ms.openlocfilehash: 1999cd922b9e7299cbf3c10a702eb4d2dc6c3fbb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177247"
---
# <a name="diagnostic-traces"></a>Tanılama İzlemeleri

İzlemeler, uygulama yürütme sırasında oluşturulan belirli iletilerin yayımlaması. İzlemeyi kullanırken, gönderilen iletileri toplama ve kaydetme mekanizmasına sahip olmanız gerekir. İzleme iletileri dinleyiciler tarafından alınır. Bir dinleyicinin amacı, izleme iletilerini toplamak, depolamak ve yönlendirmaktır. Dinleyiciler izleme çıkışını günlük, pencere veya metin dosyası gibi uygun bir hedefe yönlendirir.  
  
 Bu tür bir dinleyici, <xref:System.Diagnostics.DefaultTraceListener> izleme etkinleştirildiğinde otomatik olarak oluşturulur ve başlatılır. İzleme çıktısının herhangi bir ek kaynağa yönlendirilmesini istiyorsanız, ek izleme dinleyicileri oluşturup başlatmalısınız. Oluşturduğunuz dinleyicileri ihtiyaçlarınıza uygun olmalıdır. Örneğin, tüm izleme çıktısının metin kaydını isteyebilirsiniz. Bu durumda, tüm çıktı yazdı etkinleştirildiğinde yeni bir metin dosyası için bir dinleyici oluşturun. Diğer yandan, yalnızca uygulama yürütme sırasında çıkış görüntülemek isteyebilirsiniz. Bu durumda, tüm çıkış için bir konsol penceresi yönlendirilmiş bir dinleyici oluşturabilirsiniz. , <xref:System.Diagnostics.EventLogTraceListener> İzleme çıkışını bir olay günlüğüne yönlendirebilir ve <xref:System.Diagnostics.TextWriterTraceListener> bir akışa izleme çıktısı yazabilir.  
  
## <a name="enabling-tracing"></a>Izlemeyi etkinleştirme  

 İşlem işlemleri sırasında izlemeleri etkinleştirmek için uygulamanızın yapılandırma dosyasını düzenlemeniz gerekir. Bir örnek verilmiştir.  
  
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
  
 <xref:System.Transactions> izlemeler "System. Transactions" adlı kaynağa yazılır. `add`Kullanmak istediğiniz izleme dinleyicisinin adını ve türünü belirtmek için ' i kullanabilirsiniz. Örnek yapılandırmanızda, "TX" dinleyicisini adlandırdık ve standart .NET Framework İzleme dinleyicisi ( <xref:System.Diagnostics.XmlWriterTraceListener> ) öğesini kullanmak istediğimiz tür olarak ekledik. Kullanım `initializeData` günlük dosyasının adı için bu dinleyici ayarlamak için. Buna ek olarak, bir basit dosya adı için tam yol yerine kullanabilirsiniz.  
  
 Her izleme iletisi türüne önem derecesini göstermek için bir düzey atanır. Uygulama etki alanının izleme düzeyi bir olay türü düzeyine eşitse veya daha düşükse, bu ileti oluşturulur. İzleme düzeyi `switchValue` yapılandırma dosyasındaki ayarıyla denetlenir. Tanılama izleme iletileriyle ilişkili düzeyler aşağıdaki tabloda tanımlanmıştır.  
  
|İzleme düzeyi|Açıklama|  
|-----------------|-----------------|  
|Kritik|Aşağıdaki gibi önemli hataları oluştu:<br /><br /> -Kullanıcı işlevselliğinde anında kayıp oluşmasına neden olabilecek bir hata.<br />-Bir yöneticinin işlevsellik kaybını önlemek için işlem yapması gereken bir olay.<br />-Kod askıda kalır.<br />-Bu izleme düzeyi, diğer kritik izlemeleri yorumlamak için yeterli bağlam da sağlayabilir. Bu işlemleri için ciddi bir arıza öndeki dizisini tanımasına yardımcı olabilir.|  
|Hata|Bir hata (örneğin, geçersiz yapılandırma veya ağ davranış gibi) kullanıcı işlevselliği kaybına neden.|  
|Uyarı|Bir koşul bulunduğunu daha sonra bir hata veya kritik hatası (başarısız veya bir sınır yaklaştığı Örneğin, ayırma) neden olabilir. Kullanıcı kodundaki hataların normal işlenmesi (örneğin, işlem iptal edildi, zaman aşımları, kimlik doğrulama başarısız oldu) Ayrıca bir uyarı oluşturabilir.|  
|Bilgi|İzleme ve tanılama sistem durumu, performans ölçüm veya profil oluşturma için faydalı iletileri üretilir. Bunlar, oluşturulan veya yürütülen bir işlem, önemli bir sınırın kesişmesi veya önemli kaynakların ayrılması gibi işlem ve kayıt yaşam süresi olaylarını içerebilir. Bir geliştirici sonra gibi bilgileri kapasite planlama ve performans yönetimi için kullanabilir.|  
  
## <a name="trace-codes"></a>İzleme kodları  

 Aşağıdaki tabloda altyapı tarafından oluşturulan izleme kodları listelenmektedir <xref:System.Transactions> . Tabloya dahil olmak üzere, izleme kod tanımlayıcısı, <xref:System.Diagnostics.EventTypeFilter.EventType%2A> izleme için numaralandırma düzeyi ve izleme için Izleme **ecord** içindeki ek veriler yer alır. Ayrıca, izlemenin karşılık gelen izleme düzeyi de izleme **ecord**' de depolanır.  
  
|TraceCode|Olay türü|İzleme ecord ' de ek veriler|  
|---------------|---------------|-------------------------------|  
|TransactionCreated|Bilgi|Transactiontraceıd|  
|Transactionyükseltilen|Bilgi|Yerel Transactiontraceıd, dağıtılmış Transactiontraceıd|  
|EnlistmentCreated|Bilgi|Transactiontraceıd, Enlistmenttraceıd, EnlistmentType (dayanıklı/volatile), EnlistmentOptions|  
|EnlistmentCallbackNegative|Uyarı|Transactiontraceıd, Enlistmenttraceıd,<br /><br /> Geri çağırma (forcerollback/iptal/nin şüpheli işlemi olmadığından)|  
|Transactionrollbackçağırılır|Uyarı|Transactiontraceıd|  
|Işlem Iptal edildi|Uyarı|Transactiontraceıd|  
|Transactionınşüpheli|Uyarı|Transactiontraceıd|  
|Işlem Scopecreated|Bilgi|TransactionScopeResult, aşağıdakiler olabilir:<br /><br /> -Yeni işlem.<br />-İşlem geçildi.<br />-Bağımlı işlem geçirildi.<br />-Geçerli işlem kullanılıyor.<br />-İşlem yok.<br /><br /> Yeni geçerli Transactiontraceıd|  
|Transactionscopeatıldı|Bilgi|Kapsamın "beklenen" geçerli işlemin işlem Izleme kimliği.|  
|Transactionscopecomplete|Uyarı|Kapsamın "beklenen" geçerli işlemin işlem Izleme kimliği.|  
|Transactionscopenestedyanlış|Uyarı|Kapsamın "beklenen" geçerli işlemin işlem Izleme kimliği.|  
|TransactionScopeCurrentTransactionChanged|Uyarı|Eski geçerli Transactiontraceıd, diğer Transactiontraceıd|  
|TransactionScopeTimeout|Uyarı|Kapsamın "beklenen" geçerli işlemin işlem Izleme kimliği.|  
|DependentCloneCreated|Bilgi|Transactiontraceıd, bağımlı işlem türü oluşturuldu (Rollbackifnottamam/Blockcommituntiltamamlanmamış)|  
|DependentCloneComplete|Bilgi|Transactiontraceıd|  
|RecoveryComplete'in|Bilgi|Kaynak Yöneticisi GUID (değerinden tabanı)|  
|Reenlist|Bilgi|Kaynak Yöneticisi GUID (değerinden tabanı)|  
|Işlem serileştirilmiş|Bilgi|Transactiontraceıd.|  
|TransactionException|Hata|Özel durum iletisi|  
|InvalidOperationException|Hata|Özel durum iletisi|  
|InternalError|Kritik|Özel durum iletisi|  
|TransferEvent||Bir işlemin serisi kaldırıldığında veya bir işlemden dağıtılan bir işlem olduğunda <xref:System.Transactions> , ExecutionContext 'ten geçerli ActivityId ve dağıtılmış Işlem kimliği yazılır.<br /><br /> DTC yönetilen koda geri çağrı yaparken, dağıtılmış işlem KIMLIĞI, geri çağırma süresince ExecutionContext öğesinde ActivityId olarak ayarlanır.|  
|ConfiguredDefaultTimeoutAdjusted|Uyarı|Ek veri yok|  
|Işlem zaman aşımı|Uyarı|Zaman aşımına uğrayan işlemin işlem Izleme kimliği.|  
  
 Önceki ek veri öğelerinin her biri için XML şeması aşağıdaki biçimdedir.  
  
### <a name="transactiontraceidentifier"></a>Transactiontraceıdentifier  

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
  
## <a name="security-issues-for-tracing"></a>Izleme Için güvenlik sorunları  

 Bir yönetici, izlemeyi açtığınızda, hassas bilgiler, varsayılan olarak genel olarak görüntülenebilen bir izleme günlüğüne yazılabilir. Olası bir güvenlik tehdidi riskini azaltmak için, izleme günlüğünü, paylaşma ve dosya sistemi erişim izinleri tarafından denetlenen güvenli bir konumda depolamayı göz önünde bulundurmanız gerekir.
