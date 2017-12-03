---
title: "İşlem Akışını Etkinleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: transactions [WCF], enabling flow
ms.assetid: a03f5041-5049-43f4-897c-e0292d4718f7
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4b5d0b90ed28928e734089265cb8c58839b6d0cd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="enabling-transaction-flow"></a>İşlem Akışını Etkinleştirme
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]işlem akışını denetlemek için yüksek oranda esnek seçenekler sunar. Bir hizmetin işlem akışı ayarlarını öznitelikleri ve yapılandırma birleşimini kullanarak ifade edilebilir.  
  
## <a name="transaction-flow-settings"></a>İşlem akışını ayarları  
 İşlem akışını ayarlar, aşağıdaki üç değerlerinin kesişimini sonucu olarak hizmet uç noktası için oluşturulur:  
  
-   <xref:System.ServiceModel.TransactionFlowAttribute> Her bir yöntemin hizmet sözleşmesinde belirtilen özniteliği.  
  
-   `TransactionFlow` Özelliğini belirli bağlamasında bağlama.  
  
-   `TransactionFlowProtocol` Özelliğini belirli bağlamasında bağlama. `TransactionFlowProtocol` Özelliğini bağlama, iki farklı işlem protokolleri arasında bir işlem akış için kullanabileceğiniz seçmenize olanak sağlar. Aşağıdaki bölümler bunların her birini kısaca açıklanmaktadır.  
  
### <a name="ws-atomictransaction-protocol"></a>WS-AtomicTransaction Protokolü  
 Üçüncü taraf protokol yığını ile birlikte çalışabilirlik gerekli olduğunda WS-AtomicTransaction (WS-AT) senaryoları için kullanışlıdırlar protokolüdür.  
  
### <a name="oletransactions-protocol"></a>OleTransactions Protokolü  
 OleTransactions Protokolü üçüncü taraf protokol yığını ile birlikte çalışabilirlik gerekli değildir ve bir hizmet dağıtıcı önceden WS-AT protokolü hizmeti yerel olarak devre dışı bırakılmış veya var olan ağ topolojisi mu bilir senaryoları için faydalıdır WS-AT kullanımını favor değil.  
  
 Aşağıdaki tabloda bu çeşitli bileşimlerini kullanarak oluşturulan işlem akışları farklı türleri gösterilmektedir.  
  
|TransactionFlow<br /><br /> bağlama|TransactionFlow bağlama özelliği|TransactionFlowProtocol bağlama Protokolü|İşlem akışını türü|  
|---------------------------------|--------------------------------------|----------------------------------------------|------------------------------|  
|Zorunlu|true|WS-AT|İşlem birlikte çalışabilen WS-AT biçiminde aktarılan gerekir.|  
|Zorunlu|true|OleTransactions|İşlem aktarılan, içinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] OleTransactions biçimi.|  
|Zorunlu|false|Geçerli değil|Bu geçersiz bir yapılandırma olduğundan geçerli değil.|  
|İzin verilen|true|WS-AT|İşlem birlikte çalışabilen WS-AT biçiminde akışı yapılan işlem.|  
|İzin verilen|true|OleTransactions|İşlem akışı yapılan işlem içinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] OleTransactions biçimi.|  
|İzin verilen|false|Herhangi bir değer|Bir işlem akıtılan değil.|  
|QueuedDeliveryRequirements|Herhangi bir değer|Herhangi bir değer|Bir işlem akıtılan değil.|  
  
 Aşağıdaki tabloda ileti sonuç işleme özetler.  
  
|Gelen ileti|TransactionFlow ayarı|İşlem üstbilgisi|İleti işleme sonucu|  
|----------------------|-----------------------------|------------------------|-------------------------------|  
|İşlem beklenen Protokolü biçimle eşleştiğinden|İzin verilen veya zorunlu|`MustUnderstand`eşittir `true`.|İşlem|  
|İşlem beklenen Protokolü biçimiyle eşleşmiyor|Zorunlu|`MustUnderstand`eşittir `false`.|Bir işlem gerekli olduğu için reddedildi|  
|İşlem beklenen Protokolü biçimiyle eşleşmiyor|İzin verilen|`MustUnderstand`eşittir `false`.|Üstbilgi değil anlaşılır olmadığından reddetti|  
|Herhangi bir protokolü biçimini kullanarak işlem|QueuedDeliveryRequirements|`MustUnderstand`eşittir `false`.|Üstbilgi değil anlaşılır olmadığından reddetti|  
|İşlem yok|Zorunlu|Yok|Bir işlem gerekli olduğu için reddedildi|  
|İşlem yok|İzin verilen|Yok|İşlem|  
|İşlem yok|QueuedDeliveryRequirements|Yok|İşlem|  
  
 Her bir sözleşme yöntemini farklı işlem akışı gereksinimlerini varken işlem akışı protokolünü bağlama düzeyinde kapsamlıdır. Bu, aynı uç noktası (ve bu nedenle aynı bağlamayı) paylaşan tüm yöntemleri de izin verme veya uygulanabilirse aynı işlem protokolü yanı sıra, işlem akışını gerektirmeden aynı ilke paylaşmak anlamına gelir.  
  
## <a name="enabling-transaction-flow-at-the-method-level"></a>Yöntem düzeyinde işlem akışını etkinleştirme  
 İşlem akışını gereksinimlerini her zaman bir hizmet sözleşmesinde tüm yöntemleri için aynı değildir. Bu nedenle, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ayrıca her yöntemin işlem akışı Tercihler ifade izin vermek için bir öznitelik tabanlı mekanizması sağlar. Bu tarafından sağlanır <xref:System.ServiceModel.TransactionFlowAttribute> bir hizmet işlemi işlem üstbilgi kabul düzeyini belirtir. İşlem akışını etkinleştirmek istiyorsanız, bu öznitelik, hizmet sözleşmesi yöntemleriyle işaretlemeniz gerekir. Bu öznitelik değerlerini birini alır <xref:System.ServiceModel.TransactionFlowOption> varsayılan değer olan numaralandırma <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>. Dışında herhangi bir değer varsa <xref:System.ServiceModel.TransactionFlowOption.NotAllowed> belirtilirse, yöntem, tek yönlü olmaması için gereklidir. Bir geliştirici bu özniteliği tasarım zamanında yöntemi düzeyi işlem akışı gereksinimlerini veya kısıtlamaları belirtmek için kullanabilirsiniz.  
  
## <a name="enabling-transaction-flow-at-the-endpoint-level"></a>Uç nokta düzeyinde işlem akışını etkinleştirme  
 Yöntem düzeyinde işlem akışı ayarı yanı sıra <xref:System.ServiceModel.TransactionFlowAttribute> özniteliği sağlar, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] daha yüksek düzeyde işlem akışını denetlemek yöneticilerin izin vermek için işlem akışı için bir uç nokta genelinde ayarı sağlar.  
  
 Bu tarafından sağlanır <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, etkinleştirme veya devre dışı bir uç nokta gelen işlem akışında olanak sağlayan ayarları, de gelen işlemler için istenen işlem protokolü biçimi belirtmek için bağlama.  
  
 Bağlama işlem akışını devre dışı bıraktı, ancak bir hizmet sözleşmesini işlemlerden biri, gelen bir işlem gerekiyor, bir doğrulama özel hizmetin başlatılması sırasında durum oluşur.  
  
 Durumu bağlamaları çoğu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sağlar içeren `transactionFlow` ve `transactionProtocol` gelen işlemler kabul etmek için belirli bağlama yapılandırmanızı sağlayan öznitelikler. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]yapılandırma öğelerini ayar bkz [ \<bağlama >](../../../../docs/framework/misc/binding.md).  
  
 Bir yönetici veya dağıtıcı uç nokta düzeyine işlem akışı işlem akışı gereksinimlerini veya kısıtlamalarını yapılandırma dosyası kullanarak dağıtım sırasında yapılandırmak için kullanabilirsiniz.  
  
## <a name="security"></a>Güvenlik  
 Sistem güvenliğini ve bütünlüğünü sağlamak için ileti alışverişlerinde akan güvenliğini gerekir uygulamalar arasında işlemler. Değil akış veya aynı işlemde yetkili değil herhangi bir uygulama için işlem ayrıntılarını belirtmesi gerekir.  
  
 Oluştururken [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bilinmeyen veya güvenilmeyen Web hizmeti meta veri değişimi, bu Web hizmetleri üzerinde işlem çağrıları kullanımı ile istemcilere bastırmak geçerli işlem mümkünse. Aşağıdaki örnek bunun nasıl yapılacağını göstermektedir.  
  
```  
//client code which has an ambient transaction  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Suppress))  
{  
    // No transaction will flow to this operation  
    untrustedProxy.Operation1(...);  
    scope.Complete();  
}  
//remainder of client code  
```  
  
 Ayrıca, hizmetleri, yalnızca yetkili kimlik doğrulaması ve sahip istemcilerden gelen işlemler kabul edecek şekilde yapılandırılmalıdır. Yüksek oranda güvenilir istemcilerden gelse gelen işlemleri yalnızca kabul edilmemelidir.  
  
## <a name="policy-assertions"></a>İlke onaylamalarını  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]işlem akışını denetlemek için ilke onaylamalarını kullanır. İlke onaylamalarını toplayarak sözleşmeleri, yapılandırma ve öznitelikleri tarafından oluşturulan bir hizmetin ilke belgesi bulunabilir. İstemci bir HTTP GET veya bir WS-MetadataExchange istek-yanıt kullanarak hizmetin ilke belgesi elde edebilirsiniz. İstemciler daha sonra bir hizmet sözleşmesini hangi işlemleri gerektirebilir desteklemek veya işlem akışını belirlemek için ilke belgesi işleyebilir.  
  
 İşlem akışını ilke onaylamalarını SOAP üstbilgileri belirterek işlem akışı etkileyen bir işlem temsil etmek için bir istemci bir hizmete göndermesi gerekir. Tüm işlem üstbilgileri ile işaretlenmelidir `MustUnderstand` eşit `true`. Aksi takdirde olarak işaretlenmiş bir üstbilgiyle herhangi bir iletisi, bir SOAP hatası reddedilir.  
  
 Yalnızca bir işlem güvenlikle ilgili ilke onaylama üzerinde tek bir işlem mevcut olabilir. Bir işlem üzerinde birden fazla işlem onaylama İlkesi belgelerle geçersiz olarak kabul edilir ve tarafından reddedilen [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Ayrıca, yalnızca bir tek işlem protokolü her bağlantı noktası türü içinde bulunabilir. Bir tek bağlantı noktası türü içinde birden fazla işlem protokolü başvuran işlemlerle ilke belgeleri geçersiz olarak kabul edilir ve tarafından reddedilen [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). İşlem onaylar İlkesi belgelerle çıktı iletileri sunmak veya tek yönlü giriş iletileri de geçersiz olarak kabul edilir.
