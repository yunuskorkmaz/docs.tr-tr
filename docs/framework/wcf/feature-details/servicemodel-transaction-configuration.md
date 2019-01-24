---
title: ServiceModel İşlem Yapılandırması
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF], ServiceModel configuration
ms.assetid: 5636067a-7fbd-4485-aaa2-8141c502acf3
ms.openlocfilehash: ee35b6c02637c3013a42303dcd7aa7c813bd183c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54693168"
---
# <a name="servicemodel-transaction-configuration"></a>ServiceModel İşlem Yapılandırması
Windows Communication Foundation (WCF) hizmeti için işlem yapılandırmak için üç öznitelikleri sağlar: `transactionFlow`, `transactionProtocol`, ve `transactionTimeout`.  
  
## <a name="configuring-transactionflow"></a>TransactionFlow yapılandırma  
 WCF sağlar içeren önceden tanımlanmış bağlamaları çoğu `transactionFlow` ve `transactionProtocol` öznitelikleri böylece bağlama gelen işlemleri belirli işlem akış protokolü kullanarak belirli bir uç nokta için kabul edecek şekilde yapılandırabilirsiniz. Ayrıca, kullanabileceğiniz `transactionFlow` öğesi ve kendi `transactionProtocol` kendi özel bağlama oluşturmak için öznitelik. Yapılandırma öğeleri ayarlama hakkında daha fazla bilgi için bkz. [ \<bağlama >](../../../../docs/framework/misc/binding.md) ve [WCF yapılandırma şeması](../../../../docs/framework/configure-apps/file-schema/wcf/index.md).  
  
 `transactionFlow` Özniteliği, işlem akışı bağlamayı kullanan hizmet uç noktaları için etkin olup olmadığını belirtir.  
  
## <a name="configuring-transactionprotocol"></a>TransactionProtocol yapılandırma  
 `transactionProtocol` Özniteliği bağlamayı kullanan hizmet uç noktaları ile kullanılacak işlem protokolünü belirler.  
  
 Bir kullanım yanı sıra, işlem akışını desteklemek için belirtilen bağlama WS-AtomicTransaction Protokolü yapılandıran bir yapılandırma bölümünü örneği verilmiştir.  
  
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
 Yapılandırabileceğiniz `transactionTimeout` özniteliği için WCF hizmetinizi `behavior` yapılandırma dosyasının öğesi. Aşağıdaki kod, bunun nasıl yapılacağı gösterilmektedir.  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>  
         <behavior name="NewBehavior" transactionTimeout="00:01:00" /> <!-- 1 minute timeout -->  
      </behaviors>  
   </system.serviceModel>  
</configuration>  
```  
  
 `transactionTimeout` Özniteliği içinde yeni bir işlem hizmeti oluşturulan tamamlamalısınız süreyi belirtir. Olarak kullanılan <xref:System.Transactions.TransactionScope> yeni bir işlem oluşturur herhangi bir işlem için zaman aşımı ve <xref:System.ServiceModel.OperationBehaviorAttribute> uygulanan <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> özelliği `true`.  
  
 Zaman aşımı süre oluşturma işleminin tamamlanması 1. Aşama için iki aşamalı tamamlama protokolü belirtir.  
  
 İçinde bu öznitelik ayarlanırsa bir `service` yapılandırma bölümü, en az bir yöntem ile ilgili hizmetin uygulanacağını <xref:System.ServiceModel.OperationBehaviorAttribute>, hangi <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> özelliği `true`.  
  
 Kullanılan zaman aşımı değeri bu arasında daha küçük değer olduğunu unutmayın `transactionTimeout` yapılandırma ayarı ve tüm <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> özelliği.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [\<bağlama >](../../../../docs/framework/misc/binding.md)
- [WCF Yapılandırma Şeması](../../../../docs/framework/configure-apps/file-schema/wcf/index.md)
