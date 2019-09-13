---
title: İşlem Akışını Etkinleştirme
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF], enabling flow
ms.assetid: a03f5041-5049-43f4-897c-e0292d4718f7
ms.openlocfilehash: 2443e82dd9c6d8b5447c2fa16b537a9feed8ddaf
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895162"
---
# <a name="enabling-transaction-flow"></a>İşlem Akışını Etkinleştirme
Windows Communication Foundation (WCF), işlem akışını denetlemek için oldukça esnek seçenekler sağlar. Bir hizmetin işlem akış ayarları, özniteliklerin ve yapılandırmanın bir birleşimi kullanılarak ifade edilebilir.  
  
## <a name="transaction-flow-settings"></a>İşlem akışı ayarları  
 İşlem akışı ayarları, bir hizmet uç noktası için aşağıdaki üç değerin kesişimine neden olarak oluşturulur:  
  
- Hizmet sözleşmesindeki her yöntem için belirtilen öznitelik.<xref:System.ServiceModel.TransactionFlowAttribute>  
  
- Belirli `TransactionFlow` bağlamadaki Binding özelliği.  
  
- Belirli `TransactionFlowProtocol` bağlamadaki Binding özelliği. Binding `TransactionFlowProtocol` özelliği, bir işlemi Flow için kullanabileceğiniz iki farklı işlem protokolü arasından seçim yapmanızı sağlar. Aşağıdaki bölümlerde bunların her biri kısaca açıklanmıştır.  
  
### <a name="ws-atomictransaction-protocol"></a>WS-AtomicTransaction Protokolü  
 WS-AtomicTransaction (WS-AT) protokolü, üçüncü taraf protokol yığınları ile birlikte çalışabilirlik gerektiğinde senaryolar için yararlıdır.  
  
### <a name="oletransactions-protocol"></a>OleTransactions Protokolü  
 OleTransactions Protokolü, üçüncü taraf protokol yığınları ile birlikte çalışabilirlik gerekli değildir ve bir hizmetin dağıtıcı, WS-AT protokol hizmetinin yerel olarak devre dışı bırakıldığını veya var olan ağ topolojisi olduğunu önceden bilir. WS-AT kullanımını tercih etmez.  
  
 Aşağıdaki tabloda, bu çeşitli birleşimler kullanılarak oluşturulabilecek farklı türde işlem akışları gösterilmektedir.  
  
|TransactionFlow<br /><br /> bağlama|TransactionFlow bağlama özelliği|TransactionFlowProtocol bağlama protokolü|İşlem akışı türü|  
|---------------------------------|--------------------------------------|----------------------------------------------|------------------------------|  
|Zorunlu|true|WS-AT|İşlem, birlikte çalışabilen WS-AT biçiminde akışlı olmalıdır.|  
|Zorunlu|true|OleTransactions|İşlem, WCF OleTransactions biçiminde akışlı olmalıdır.|  
|Zorunlu|false|Geçerli değil|Geçerli değil çünkü geçersiz bir yapılandırma.|  
|İzin Verildi|true|WS-AT|İşlem, birlikte çalışabilen WS-AT biçiminde akışlı olabilir.|  
|İzin Verildi|true|OleTransactions|İşlem, WCF OleTransactions biçiminde akışlı olabilir.|  
|İzin Verildi|false|Herhangi bir değer|İşlem akışlı değil.|  
|NotAllowed|Herhangi bir değer|Herhangi bir değer|İşlem akışlı değil.|  
  
 Aşağıdaki tabloda ileti işleme sonucu özetlenmektedir.  
  
|Gelen ileti|TransactionFlow ayarı|İşlem üst bilgisi|İleti işleme sonucu|  
|----------------------|-----------------------------|------------------------|-------------------------------|  
|İşlem beklenen protokol biçimiyle eşleşiyor|İzin verilen veya zorunlu|`MustUnderstand`eşittir `true`.|İşlem|  
|İşlem beklenen protokol biçimiyle eşleşmiyor|Zorunlu|`MustUnderstand`eşittir `false`.|İşlem gerekli olduğundan reddedildi|  
|İşlem beklenen protokol biçimiyle eşleşmiyor|İzin Verildi|`MustUnderstand`eşittir `false`.|Üst bilgi anlaşılmadığı için reddedildi|  
|Herhangi bir protokol biçimi kullanan işlem|NotAllowed|`MustUnderstand`eşittir `false`.|Üst bilgi anlaşılmadığı için reddedildi|  
|İşlem yok|Zorunlu|Yok|İşlem gerekli olduğundan reddedildi|  
|İşlem yok|İzin Verildi|Yok|İşlem|  
|İşlem yok|NotAllowed|Yok|İşlem|  
  
 Bir sözleşmede her yöntemin farklı işlem akışı gereksinimleri olsa da, işlem akışı Protokolü ayarı bağlama düzeyinde kapsamlandırılır. Bu, aynı uç noktayı paylaşan tüm yöntemlerin (ve dolayısıyla aynı bağlamanın) aynı zamanda aynı ilkeyi ve varsa aynı işlem protokolünü de aynı şekilde paylaştığı anlamına gelir.  
  
## <a name="enabling-transaction-flow-at-the-method-level"></a>Yöntem düzeyinde Işlem akışını etkinleştirme  
 İşlem akışı gereksinimleri, hizmet sözleşmesindeki tüm yöntemler için her zaman aynı değildir. Bu nedenle, WCF Ayrıca her yöntemin işlem akışı tercihlerinin belirtilmesine izin veren öznitelik tabanlı bir mekanizma sağlar. Bu, <xref:System.ServiceModel.TransactionFlowAttribute> bir hizmet işleminin bir işlem üst bilgisini kabul ettiği düzeyi belirten tarafından gerçekleştirilir. İşlem akışını etkinleştirmek istiyorsanız, hizmet sözleşmesi yöntemlerinizi Bu öznitelikle işaretlemelisiniz. Bu öznitelik, varsayılan değerin olduğu <xref:System.ServiceModel.TransactionFlowOption> <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>, numaralandırmanın değerlerinden birini alır. Eğer hariç <xref:System.ServiceModel.TransactionFlowOption.NotAllowed> herhangi bir değer belirtilmişse, yöntemin tek yönlü olmaması gerekir. Geliştirici, bu özniteliği, tasarım zamanında Yöntem düzeyi işlem akışı gereksinimlerini veya kısıtlamalarını belirtmek için kullanabilir.  
  
## <a name="enabling-transaction-flow-at-the-endpoint-level"></a>Uç nokta düzeyinde Işlem akışını etkinleştirme  
 <xref:System.ServiceModel.TransactionFlowAttribute> Özniteliğin sağladığı Yöntem düzeyi işlem akışı ayarına ek olarak, WCF işlem akışı için, yöneticilerin işlem akışını daha yüksek bir düzeyde denetlemesine olanak tanımak için uç nokta genelinde bir ayar sağlar.  
  
 Bu, bir uç noktanın <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>bağlama ayarlarında gelen işlem akışını etkinleştirmenizi veya devre dışı bırakmanızı ve gelen işlemler için istenen işlem protokolü biçimini belirtmenizi sağlayan tarafından gerçekleştirilir.  
  
 Bağlama işlem akışını devre dışı bırakmış, ancak hizmet sözleşmesindeki işlemlerden biri gelen işlem gerektiriyorsa, hizmet başlangıcında bir doğrulama özel durumu oluşturulur.  
  
 Oluşan bağlamaların çoğu, gelen işlemleri kabul etmek `transactionFlow` üzere `transactionProtocol` belirli bağlamayı yapılandırmanıza olanak sağlayan ve özniteliklerini içerir. Yapılandırma öğelerini ayarlama hakkında daha fazla bilgi için bkz [ \<. Binding >](../../../../docs/framework/misc/binding.md).  
  
 Yönetici veya dağıtıcı, yapılandırma dosyasını kullanarak dağıtım zamanında işlem akışı gereksinimlerini veya kısıtlamalarını yapılandırmak için uç nokta düzeyi işlem akışını kullanabilir.  
  
## <a name="security"></a>Güvenlik  
 Sistem güvenliğinin ve bütünlüğünden emin olmak için, uygulamalar arasında işlem akışı yaparken ileti değişimlerinin güvenliğini sağlamalısınız. Aynı işleme dahil olmayan herhangi bir uygulamaya işlem ayrıntılarını Flow veya açıklamayamalısınız.  
  
 Meta veri değişimi kullanılarak bilinmeyen veya güvenilmeyen Web hizmetlerinde WCF istemcileri oluştururken, bu Web Hizmetleri üzerinde işlemlere yapılan çağrılar mümkünse geçerli işlemi bastırmalıdır. Aşağıdaki örnek bunun nasıl yapılacağını göstermektedir.  
  
```csharp
//client code which has an ambient transaction  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Suppress))  
{  
    // No transaction will flow to this operation  
    untrustedProxy.Operation1(...);  
    scope.Complete();  
}  
//remainder of client code  
```  
  
 Ayrıca hizmetler, yalnızca kimliği doğrulanmış ve yetkilendirildiği istemcilerden gelen işlemleri kabul edecek şekilde yapılandırılmalıdır. Gelen işlemler yalnızca son derece güvenilen istemcilerden geliyorsa kabul edilmelidir.  
  
## <a name="policy-assertions"></a>İlke onayları  
 WCF, işlem akışını denetlemek için ilke onayları kullanır. İlke onayları, sözleşmelerin, yapılandırmanın ve özniteliklerin toplayarak oluşturulan bir hizmetin ilke belgesinde bulunabilir. İstemci, bir HTTP GET veya WS-MetadataExchange isteği-Yanıtla kullanarak hizmetin ilke belgesini alabilir. İstemciler daha sonra bir hizmet sözleşmesindeki hangi işlemlerin işlem akışını destekleyebildiğini veya gerektirmesini belirlemede ilke belgesini işleyebilir.  
  
 İşlem akışı ilke onayları, bir istemcinin bir işlemi temsil etmek için bir hizmete gönderilmesi gereken SOAP üstbilgilerini belirterek işlem akışını etkiler. Tüm işlem üst bilgileri, `MustUnderstand` `true`değerine eşit olarak işaretlenmelidir. Aksi halde işaretli bir üst bilgi içeren herhangi bir ileti bir SOAP hatası ile reddedilir.  
  
 Tek bir işlemde yalnızca bir işlemle ilgili ilke onayı bulunabilir. Bir işlemde birden fazla işlem onaylama işlemi olan ilke belgeleri geçersiz sayılır ve WCF tarafından reddedilir. Ayrıca, her bağlantı noktası türünün içinde yalnızca tek bir işlem protokolü bulunabilir. Tek bir bağlantı noktası türü içinde birden fazla işlem protokolüne başvuran işlemler içeren ilke belgeleri geçersiz sayılır ve [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)tarafından reddedilir. Çıkış iletilerinde veya tek yönlü giriş iletilerinde bulunan işlem onayları olan ilke belgeleri de geçersiz sayılır.
