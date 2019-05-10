---
title: İşlem Akışını Etkinleştirme
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF], enabling flow
ms.assetid: a03f5041-5049-43f4-897c-e0292d4718f7
ms.openlocfilehash: 560b03b8e2788c88e6c92c64834bf36c750575ea
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626937"
---
# <a name="enabling-transaction-flow"></a>İşlem Akışını Etkinleştirme
Windows Communication Foundation (WCF) işlem akışını denetlemek için son derece esnek seçenekler sunar. Bir hizmetin işlem akış ayarları, öznitelikleri ve yapılandırma bir birleşimini kullanarak ifade edilebilir.  
  
## <a name="transaction-flow-settings"></a>İşlem akış ayarları  
 İşlem akışı ayarlarında, aşağıdaki üç değerlerinin kesişimini sonucu olarak bir hizmet uç noktası için oluşturulur:  
  
- <xref:System.ServiceModel.TransactionFlowAttribute> Özniteliği hizmet sözleşmesindeki her bir yöntemin belirtildi.  
  
- `TransactionFlow` Belirli bağlamasında özelliği bağlama.  
  
- `TransactionFlowProtocol` Belirli bağlamasında özelliği bağlama. `TransactionFlowProtocol` Özelliği bağlama, bir işlem akış için kullanabileceğiniz iki farklı işlem protokolleri seçin olanak sağlar. Aşağıdaki bölümler bunların her biri kısaca açıklayın.  
  
### <a name="ws-atomictransaction-protocol"></a>WS-AtomicTransaction Protokolü  
 Üçüncü taraf protokol yığınlarının ile birlikte çalışabilirlik gerektiğinde WS-AtomicTransaction (WS-AT) protokolü senaryoları için kullanışlıdır.  
  
### <a name="oletransactions-protocol"></a>OleTransactions Protokolü  
 Üçüncü taraf protokol yığınlarının ile birlikte çalışabilirlik gerekli değildir ve bir hizmetin dağıtıcı önceden WS-AT protokolü hizmetini yerel olarak devre dışı bırakılmış veya mevcut ağ topolojisini mu bilir OleTransactions Protokolü senaryoları için yararlı olur WS-AT kullanımını favor değil.  
  
 Aşağıdaki tabloda bu çeşitli birleşimlerini kullanarak oluşturulan işlem akışları farklı türleri gösterilmektedir.  
  
|transactionFlow<br /><br /> bağlama|TransactionFlow bağlama özelliği|TransactionFlowProtocol bağlama Protokolü|İşlem akışı türü|  
|---------------------------------|--------------------------------------|----------------------------------------------|------------------------------|  
|Zorunlu|true|WS-AT|İşlem, birlikte çalışabilen WS-AT biçiminde aktarılan gerekir.|  
|Zorunlu|true|OleTransactions|İşlem, WCF OleTransactions biçiminde aktarılan gerekir.|  
|Zorunlu|false|Geçerli değil|Bu geçersiz bir yapılandırma olduğundan geçerli değil.|  
|İzin Verildi|true|WS-AT|İşlem akışını birlikte çalışabilen WS-AT biçiminde.|  
|İzin Verildi|true|OleTransactions|İşlem, WCF OleTransactions biçiminde aktarılan.|  
|İzin Verildi|false|Herhangi bir değer|Bir işlem aktarılan değil.|  
|Noktayla|Herhangi bir değer|Herhangi bir değer|Bir işlem aktarılan değil.|  
  
 İleti işleme sonuç aşağıdaki tabloda özetlenmiştir.  
  
|Gelen ileti|TransactionFlow ayarı|İşlem üst bilgisi|İleti işleme sonucu|  
|----------------------|-----------------------------|------------------------|-------------------------------|  
|İşlem beklenen Protokolü biçimle eşleşmesi|İzin verilen veya zorunlu|`MustUnderstand` eşittir `true`.|İşlem|  
|İşlem protokolü beklenen biçimle eşleşmiyor|Zorunlu|`MustUnderstand` eşittir `false`.|Bir işlem gerekli olduğu için reddedildi|  
|İşlem protokolü beklenen biçimle eşleşmiyor|İzin Verildi|`MustUnderstand` eşittir `false`.|Üstbilgisi anlaşılamadı nedeniyle reddedildi|  
|Herhangi bir protokol biçimini kullanarak işlem|Noktayla|`MustUnderstand` eşittir `false`.|Üstbilgisi anlaşılamadı nedeniyle reddedildi|  
|İşlem yok|Zorunlu|Yok|Bir işlem gerekli olduğu için reddedildi|  
|İşlem yok|İzin Verildi|Yok|İşlem|  
|İşlem yok|Noktayla|Yok|İşlem|  
  
 Her bir sözleşme metodunda farklı işlem akışı gereksinimlerini varken işlem akışı protokolünü bağlama düzeyinde kapsama alınır. Bu, aynı uç noktasına (ve bu nedenle aynı bağlamayı) paylaşan tüm yöntemleri de aynı ilke izin verme veya varsa aynı işlem protokolünü yanı sıra, işlem akışı gerektiren paylaşmak anlamına gelir.  
  
## <a name="enabling-transaction-flow-at-the-method-level"></a>Yöntem düzeyinde işlem akışını etkinleştirme  
 İşlem akışını gereksinimleri her zaman bir hizmet sözleşmesini tüm yöntemler için aynı değildir. Bu nedenle, WCF, ayrıca her yöntemin ifade işlem akış tercihleri izin vermek için öznitelik tabanlı bir mekanizma sağlar. Bu tarafından sağlanır <xref:System.ServiceModel.TransactionFlowAttribute> bir hizmet işlemi bir işlem üst bilgisi kabul düzeyini belirtir. İşlem akışını etkinleştirmek istiyorsanız bu öznitelik, hizmet sözleşmesi yöntemleriyle işaretlemeniz gerekir. Bu öznitelik değerlerinden alan <xref:System.ServiceModel.TransactionFlowOption> numaralandırma, varsayılan değer olan <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>. Dışında herhangi bir değer varsa <xref:System.ServiceModel.TransactionFlowOption.NotAllowed> belirtilirse, yöntem, tek yönlü olmaması için gereklidir. Bir geliştirici, tasarım zamanında yöntem düzeyi işlem akışı gereksinimlerini veya kısıtlamaları belirtmek için bu özniteliği kullanabilirsiniz.  
  
## <a name="enabling-transaction-flow-at-the-endpoint-level"></a>Uç nokta düzeyinde işlem akışını etkinleştirme  
 Yöntem düzeyi işlem akışı ayarı yanı sıra <xref:System.ServiceModel.TransactionFlowAttribute> öznitelik sağlar, WCF, yöneticilerin işlem akışını daha yüksek düzeyde denetim sağlamak için işlem akışı için bir uç nokta genelinde ayarı sağlar.  
  
 Bu tarafından sağlanır <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, etkinleştirme veya devre dışı bir uç nokta gelen işlem akışı sağlar ayarları de gelen işlemler için istenen işlem protokolü biçimini belirtmek için farklı bağlama.  
  
 Bağlama işlem akışı devre dışı bırakıldı, ancak bir hizmet sözleşmesini işlemlerden biri, gelen bir işlem gerektirir, doğrulama özel'ün hizmetin başlatılması sırasında durum oluşturulur.  
  
 WCF sağlar içeren ayakta bağlamaları çoğu `transactionFlow` ve `transactionProtocol` özniteliklerini gelen işlem kabul etmek için belirli bağlama yapılandırmanıza olanak sağlar. Yapılandırma öğeleri ayarlama hakkında daha fazla bilgi için bkz. [ \<bağlama >](../../../../docs/framework/misc/binding.md).  
  
 Bir yönetici ya da dağıtıcı uç nokta düzeyine işlem akışı yapılandırma dosyası kullanarak dağıtım sırasında işlem akışı gereksinimlerini veya kısıtlamaları yapılandırmak için kullanabilirsiniz.  
  
## <a name="security"></a>Güvenlik  
 Sistem güvenliğini ve bütünlüğünü sağlamak için ileti alışverişlerinde zaman güvenli gereken uygulamalar arasında işlemler. Değil, aynı işlemde katılmak için yetkili değil herhangi bir uygulama için işlem ayrıntılarını ifşa akış veya gerekir.  
  
 Bilinmeyen veya güvenilmeyen Web hizmetlerine meta veri değişimi kullanarak WCF istemci oluştururken, bu Web hizmetleri üzerinde işlem çağrıları mümkünse geçerli işlem göndermeme. Aşağıdaki örnek bunun nasıl yapılacağını göstermektedir.  
  
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
  
 Ayrıca, hizmetleri, yalnızca yetkili kimlik doğrulaması ve sahip istemcilerden gelen işlem kabul edecek şekilde yapılandırılmalıdır. Yüksek derecede güvenilen istemcilerden gelen gelen işlem yalnızca kabul edilmesi.  
  
## <a name="policy-assertions"></a>İlke onaylamalarını  
 WCF işlem akışını denetlemek için ilke onaylamalarını kullanır. İlke onaylamalarını toplama sözleşmeleri, yapılandırma ve öznitelikleri tarafından oluşturulan bir hizmetin ilke belgesi bulunabilir. İstemci, hizmetin ilke belgesi bir HTTP GET veya bir WS-MetadataExchange istek-yanıt kullanarak elde edebilirsiniz. İstemciler daha sonra hangi işlemlerin bir hizmet sözleşmesini desteklemiyor veya işlem akışı gerektiren belirlemek için ilke belgesi işleyebilir.  
  
 İşlem akışı ilke onaylamalarını SOAP üstbilgileri belirterek işlem akışını etkileyen bir işlemi temsil etmek için bir istemci bir hizmete göndermelisiniz. Tüm işlem üst bilgileri ile işaretlenmelidir `MustUnderstand` eşit `true`. Tersi durumda işaretlenmiş bir üstbilgiyle herhangi bir ileti ile bir SOAP hatası reddedilir.  
  
 Tek bir işlemle ilgili İlkesi onayını sunucuda tek bir işlem tarafından bulunabilir. Bir işlem birden fazla işlem onayına ilke belgelerle geçersiz olarak kabul edilir ve WCF tarafından reddedilir. Ayrıca, yalnızca tek bir işlem protokolü bağlantı noktası türü içinde bulunabilir. İlke belgeleri tek bağlantı noktası türü içinde birden fazla işlem protokolünü başvuran işlemleri geçersiz olarak kabul edilir ve tarafından reddedilen [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). İlke belgeleri işlem onaylar ile çıkış iletileri sunmak veya tek yönlü giriş iletileri de geçersiz olarak kabul edilir.
