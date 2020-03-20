---
title: ServiceModel İşlem Yapılandırması
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF], ServiceModel configuration
ms.assetid: 5636067a-7fbd-4485-aaa2-8141c502acf3
ms.openlocfilehash: 79772d19ddaec041aa1fac936b9951731507b6e6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184459"
---
# <a name="servicemodel-transaction-configuration"></a>ServiceModel İşlem Yapılandırması
Windows Communication Foundation (WCF), bir hizmet için hareketleri `transactionFlow` `transactionProtocol`yapılandırmak `transactionTimeout`için üç öznitelik sağlar: , , ve .  
  
## <a name="configuring-transactionflow"></a>İşlem akışını yapılandırma  
 WCF'nin sağladığı önceden tanımlanmış bağlamaların çoğu, belirli bir işlem akışı protokolü kullanarak gelen işlemleri belirli bir uç nokta için kabul etmek üzere bağlamayı yapılandırabilmeniz için öznitelikleri `transactionFlow` ve `transactionProtocol` öznitelikleri içerir. Buna ek olarak, `transactionFlow` kendi özel `transactionProtocol` bağlama oluşturmak için öğeve özniteliği kullanabilirsiniz. Yapılandırma öğelerini ayarlama hakkında daha fazla bilgi için [ \<bağlayıcı>](../../configure-apps/file-schema/wcf/bindings.md) ve [WCF Yapılandırma Şeması'na](../../../../docs/framework/configure-apps/file-schema/wcf/index.md)bakın.  
  
 Öznitelik, `transactionFlow` bağlamayı kullanan hizmet uç noktaları için hareket akışının etkin olup olmadığını belirtir.  
  
## <a name="configuring-transactionprotocol"></a>İşlemi YapılandırmaProtokolü  
 Öznitelik, `transactionProtocol` bağlamayı kullanan hizmet uç noktalarıyla kullanılacak işlem protokolünü belirtir.  
  
 Aşağıda, belirtilen bağlamayı hareket akışını desteklemek için yapılandıran bir yapılandırma bölümünün yanı sıra WS-AtomicTransaction protokolünü kullanan bir örnek verilmiştir.  
  
```xml  
<netNamedPipeBinding>  
   <binding name="test"  
      closeTimeout="00:00:10"  
      openTimeout="00:00:20"
      receiveTimeout="00:00:30"  
      sendTimeout="00:00:40"  
      transactionFlow="true"  
      transactionProtocol="WSAtomicTransactionOctober2004"  
      hostNameComparisonMode="WeakWildcard"  
      maxBufferSize="1001"  
      maxConnections="123"
      maxReceivedMessageSize="1000">  
   </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="configuring-transactiontimeout"></a>İşlemI YapılandırmaTimeout  
 WCF hizmetinizin özniteliğini yapılandırma dosyasının `transactionTimeout` `behavior` öğesinde yapılandırabilirsiniz. Aşağıdaki kod, bunun nasıl yapılacağını gösterir.  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>  
         <behavior name="NewBehavior" transactionTimeout="00:01:00" /> <!-- 1 minute timeout -->  
      </behaviors>  
   </system.serviceModel>  
</configuration>  
```  
  
 Öznitelik, `transactionTimeout` hizmette oluşturulan yeni bir işlemin tamamlanması gereken süreyi belirtir. Yeni bir işlem <xref:System.Transactions.TransactionScope> oluşturan herhangi bir işlem için zaman aşımı <xref:System.ServiceModel.OperationBehaviorAttribute> olarak kullanılır <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> ve uygulanırsa, özellik `true`.  
  
 Zaman ayırma, işlemin oluşturulmasından iki aşamalı taahhüt protokolünde faz 1'in tamamlanmasına kadar olan süreyi belirtir.  
  
 Bu öznitelik `service` bir yapılandırma bölümünde ayarlanmışsa, <xref:System.ServiceModel.OperationBehaviorAttribute> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> ilgili hizmetin en az bir yöntemini uygulamanız gerekir, özelliğin . `true`  
  
 Kullanılan zaman aşım değerinin, bu `transactionTimeout` yapılandırma ayarı ile <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> herhangi bir özellik arasındaki daha küçük değer olduğunu unutmayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [\<bağlayıcı>](../../configure-apps/file-schema/wcf/bindings.md)
- [WCF Yapılandırma Şeması](../../../../docs/framework/configure-apps/file-schema/wcf/index.md)
