---
title: ServiceModel İşlem Yapılandırması
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF], ServiceModel configuration
ms.assetid: 5636067a-7fbd-4485-aaa2-8141c502acf3
ms.openlocfilehash: 1d04a7bb756cccb33b436c1f57decc0249764828
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600341"
---
# <a name="servicemodel-transaction-configuration"></a>ServiceModel İşlem Yapılandırması
Windows Communication Foundation (WCF), bir hizmetin işlemlerini yapılandırmak için üç öznitelik sağlar: `transactionFlow` , `transactionProtocol` ve `transactionTimeout` .  
  
## <a name="configuring-transactionflow"></a>TransactionFlow yapılandırılıyor  
 Önceden tanımlanmış bağlamaların çoğu, `transactionFlow` ve `transactionProtocol` özniteliklerini içerir, böylece bağlamayı belirli bir işlem akış protokolünü kullanarak belirli bir uç nokta için gelen işlemleri kabul edecek şekilde yapılandırabilirsiniz. Buna ek olarak, `transactionFlow` `transactionProtocol` kendi özel bağlamalarınızı oluşturmak için öğesini ve özniteliğini de kullanabilirsiniz. Yapılandırma öğelerini ayarlama hakkında daha fazla bilgi için bkz [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) . ve [WCF yapılandırma şeması](../../configure-apps/file-schema/wcf/index.md).  
  
 `transactionFlow`Özniteliği, işlem akışının bağlamayı kullanan hizmet uç noktaları için etkin olup olmadığını belirtir.  
  
## <a name="configuring-transactionprotocol"></a>TransactionProtocol yapılandırma  
 `transactionProtocol`Özniteliği, bağlamayı kullanan hizmet uç noktaları ile kullanılacak işlem protokolünü belirtir.  
  
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
 `transactionTimeout`Yapılandırma dosyasının ÖĞESINDE WCF hizmetiniz için özniteliği yapılandırabilirsiniz `behavior` . Aşağıdaki kod bunun nasıl yapılacağını göstermektedir.  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>  
         <behavior name="NewBehavior" transactionTimeout="00:01:00" /> <!-- 1 minute timeout -->  
      </behaviors>  
   </system.serviceModel>  
</configuration>  
```  
  
 `transactionTimeout`Öznitelik, hizmette oluşturulan yeni bir işlemin tamamlanma süresini belirtir. <xref:System.Transactions.TransactionScope>Yeni bir işlem kuran tüm işlemler için zaman aşımı olarak kullanılır ve <xref:System.ServiceModel.OperationBehaviorAttribute> uygulanmışsa, <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> özelliği olarak ayarlanır `true` .  
  
 Zaman aşımı, iki aşamalı işleme protokolünde işlem 1 ' in tamamlanmasına kadar işlemin oluşturulmasından geçen süreyi belirtir.  
  
 Bu öznitelik bir yapılandırma bölümünde ayarlandıysa, `service` karşılık gelen hizmetin, özelliği olarak ayarlandığı en az bir yöntemi uygulamanız gerekir <xref:System.ServiceModel.OperationBehaviorAttribute> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> `true` .  
  
 Kullanılan zaman aşımı değerinin bu `transactionTimeout` yapılandırma ayarı ile herhangi bir özellik arasındaki daha küçük bir değer olduğunu unutmayın <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [\<binding>](../../configure-apps/file-schema/wcf/bindings.md)
- [WCF Yapılandırma Şeması](../../configure-apps/file-schema/wcf/index.md)
