---
title: "ServiceModel İşlem Yapılandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transactions [WCF], ServiceModel configuration
ms.assetid: 5636067a-7fbd-4485-aaa2-8141c502acf3
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 650f34c37917a7f7ce407df1a3af42d177593c33
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="servicemodel-transaction-configuration"></a>ServiceModel İşlem Yapılandırması
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]bir hizmet için işlemleri yapılandırmak için üç öznitelikleri sağlar: `transactionFlow`, `transactionProtocol`, ve `transactionTimeout`.  
  
## <a name="configuring-transactionflow"></a>TransactionFlow yapılandırma  
 Önceden tanımlanmış bağlamaları çoğu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sağlar içeren `transactionFlow` ve `transactionProtocol` öznitelikleri böylece bağlama belirli işlem akışı protokolünü kullanarak belirli bir uç noktası için gelen işlemler kabul edecek şekilde yapılandırabilirsiniz. Ayrıca, `transactionFlow` öğesi ve kendi `transactionProtocol` kendi özel bağlama oluşturmak için öznitelik. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]yapılandırma öğelerini ayar bkz [ \<bağlama >](../../../../docs/framework/misc/binding.md) ve [WCF yapılandırma şeması](../../../../docs/framework/configure-apps/file-schema/wcf/index.md).  
  
 `transactionFlow` Özniteliği, işlem akışını bağlamayı kullanan hizmet uç noktaları için etkinleştirilip etkinleştirilmeyeceğini belirtir.  
  
## <a name="configuring-transactionprotocol"></a>TransactionProtocol yapılandırma  
 `transactionProtocol` Özniteliği bağlamayı kullanan hizmet uç noktaları ile kullanmak için işlem protokolü belirtir.  
  
 WS-AtomicTransaction protokolü, bir kullanım yanı sıra, işlem akışını desteklemek üzere belirtilen bağlama yapılandırır yapılandırma bölümünün bir örnek verilmiştir.  
  
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
 Yapılandırabileceğiniz `transactionTimeout` için özniteliği, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmeti `behavior` yapılandırma dosyası öğesi. Aşağıdaki kod bunun nasıl yapılacağı gösterilmektedir.  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>  
         <behavior name="NewBehavior" transactionTimeout="00:01:00" /> <!-- 1 minute timeout -->  
      </behaviors>  
   </system.serviceModel>  
</configuration>  
```  
  
 `transactionTimeout` Özniteliği içinde hizmeti oluşturulmuş yeni bir işlem tamamlanmalıdır zaman aralığını belirtir. Olarak kullanılan <xref:System.Transactions.TransactionScope> yeni bir işlem kurar herhangi bir işlem için zaman aşımı ve <xref:System.ServiceModel.OperationBehaviorAttribute> uygulanan <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> özelliği ayarlanmış `true`.  
  
 Zaman aşımı süreyi oluşturma işleminin tamamlanması Aşama 1 için iki aşamalı yürütme Protokolü belirtir.  
  
 İçinde bu öznitelik ayarlanırsa bir `service` yapılandırma bölümünde, uygulamanız ile ilgili hizmetinin en az bir yöntemi <xref:System.ServiceModel.OperationBehaviorAttribute>, burada <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> özelliği ayarlanmış `true`.  
  
 Kullanılan zaman aşımı değeri bu arasında daha küçük olan değeri olduğuna dikkat edin `transactionTimeout` yapılandırma ayarı ve tüm <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> özelliği.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [\<bağlama >](../../../../docs/framework/misc/binding.md)  
 [WCF Yapılandırma Şeması](../../../../docs/framework/configure-apps/file-schema/wcf/index.md)
