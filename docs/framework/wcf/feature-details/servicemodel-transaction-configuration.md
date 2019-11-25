---
title: ServiceModel İşlem Yapılandırması
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF], ServiceModel configuration
ms.assetid: 5636067a-7fbd-4485-aaa2-8141c502acf3
ms.openlocfilehash: e8c8c9ebff259ccd991768afb8cdf9925a66aad0
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141617"
---
# <a name="servicemodel-transaction-configuration"></a>ServiceModel İşlem Yapılandırması
Windows Communication Foundation (WCF), bir hizmetin işlemlerini yapılandırmak için üç öznitelik sağlar: `transactionFlow`, `transactionProtocol`ve `transactionTimeout`.  
  
## <a name="configuring-transactionflow"></a>TransactionFlow yapılandırılıyor  
 Önceden tanımlanmış bağlamaları WCF, belirli bir işlem akış protokolünü kullanarak belirli bir uç nokta için gelen işlemleri kabul edecek şekilde yapılandırmak üzere `transactionFlow` ve `transactionProtocol` özniteliklerini içerir. Ayrıca, kendi özel bağlamalarınızı oluşturmak için `transactionFlow` öğesini ve `transactionProtocol` özniteliğini kullanabilirsiniz. Yapılandırma öğelerini ayarlama hakkında daha fazla bilgi için bkz. [\<bağlama >](../../configure-apps/file-schema/wcf/bindings.md) ve [WCF yapılandırma şeması](../../../../docs/framework/configure-apps/file-schema/wcf/index.md).  
  
 `transactionFlow` özniteliği, işlem akışının bağlamayı kullanan hizmet uç noktaları için etkin olup olmadığını belirtir.  
  
## <a name="configuring-transactionprotocol"></a>TransactionProtocol yapılandırma  
 `transactionProtocol` özniteliği, bağlamayı kullanan hizmet uç noktaları ile kullanılacak işlem protokolünü belirtir.  
  
 Aşağıda, belirli bir bağlamayı işlem akışını destekleyecek şekilde yapılandıran bir yapılandırma bölümünün yanı sıra WS-AtomicTransaction protokolünü kullanın.  
  
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
  
## <a name="configuring-transactiontimeout"></a>TransactionTimeout yapılandırma  
 WCF hizmetiniz için `transactionTimeout` özniteliğini yapılandırma dosyasının `behavior` öğesinde yapılandırabilirsiniz. Aşağıdaki kod bunun nasıl yapılacağını göstermektedir.  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>  
         <behavior name="NewBehavior" transactionTimeout="00:01:00" /> <!-- 1 minute timeout -->  
      </behaviors>  
   </system.serviceModel>  
</configuration>  
```  
  
 `transactionTimeout` özniteliği, hizmette oluşturulan yeni bir işlemin tamamlanma süresini belirtir. Yeni bir işlem kuran tüm işlemler için <xref:System.Transactions.TransactionScope> zaman aşımı olarak kullanılır ve <xref:System.ServiceModel.OperationBehaviorAttribute> uygulanmışsa <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> özelliği `true`olarak ayarlanır.  
  
 Zaman aşımı, iki aşamalı işleme protokolünde işlem 1 ' in tamamlanmasına kadar işlemin oluşturulmasından geçen süreyi belirtir.  
  
 Bu öznitelik `service` yapılandırma bölümünde ayarlandıysa, karşılık gelen hizmetin <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> özelliğinin `true`olarak ayarlandığı en az bir yöntemi <xref:System.ServiceModel.OperationBehaviorAttribute>uygulamanız gerekir.  
  
 Kullanılan zaman aşımı değerinin bu `transactionTimeout` yapılandırma ayarı ve <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> özelliği arasındaki daha küçük bir değer olduğunu unutmayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [bağlama > \<](../../configure-apps/file-schema/wcf/bindings.md)
- [WCF Yapılandırma Şeması](../../../../docs/framework/configure-apps/file-schema/wcf/index.md)
