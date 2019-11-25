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
# <a name="servicemodel-transaction-configuration"></a><span data-ttu-id="7cb3e-102">ServiceModel İşlem Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="7cb3e-102">ServiceModel Transaction Configuration</span></span>
<span data-ttu-id="7cb3e-103">Windows Communication Foundation (WCF), bir hizmetin işlemlerini yapılandırmak için üç öznitelik sağlar: `transactionFlow`, `transactionProtocol`ve `transactionTimeout`.</span><span class="sxs-lookup"><span data-stu-id="7cb3e-103">Windows Communication Foundation (WCF) provides three attributes for configuring transactions for a service: `transactionFlow`, `transactionProtocol`, and `transactionTimeout`.</span></span>  
  
## <a name="configuring-transactionflow"></a><span data-ttu-id="7cb3e-104">TransactionFlow yapılandırılıyor</span><span class="sxs-lookup"><span data-stu-id="7cb3e-104">Configuring transactionFlow</span></span>  
 <span data-ttu-id="7cb3e-105">Önceden tanımlanmış bağlamaları WCF, belirli bir işlem akış protokolünü kullanarak belirli bir uç nokta için gelen işlemleri kabul edecek şekilde yapılandırmak üzere `transactionFlow` ve `transactionProtocol` özniteliklerini içerir.</span><span class="sxs-lookup"><span data-stu-id="7cb3e-105">Most of the predefined bindings WCF provides contain the `transactionFlow` and `transactionProtocol` attributes, so that you can configure the binding to accept incoming transactions for a specific endpoint using a specific transaction flow protocol.</span></span> <span data-ttu-id="7cb3e-106">Ayrıca, kendi özel bağlamalarınızı oluşturmak için `transactionFlow` öğesini ve `transactionProtocol` özniteliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7cb3e-106">In addition, you can use the `transactionFlow` element and its `transactionProtocol` attribute to build your own custom binding.</span></span> <span data-ttu-id="7cb3e-107">Yapılandırma öğelerini ayarlama hakkında daha fazla bilgi için bkz. [\<bağlama >](../../configure-apps/file-schema/wcf/bindings.md) ve [WCF yapılandırma şeması](../../../../docs/framework/configure-apps/file-schema/wcf/index.md).</span><span class="sxs-lookup"><span data-stu-id="7cb3e-107">For more information about setting the configuration elements, see [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) and [WCF Configuration Schema](../../../../docs/framework/configure-apps/file-schema/wcf/index.md).</span></span>  
  
 <span data-ttu-id="7cb3e-108">`transactionFlow` özniteliği, işlem akışının bağlamayı kullanan hizmet uç noktaları için etkin olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7cb3e-108">The `transactionFlow` attribute specifies whether transaction flow is enabled for service endpoints that use the binding.</span></span>  
  
## <a name="configuring-transactionprotocol"></a><span data-ttu-id="7cb3e-109">TransactionProtocol yapılandırma</span><span class="sxs-lookup"><span data-stu-id="7cb3e-109">Configuring transactionProtocol</span></span>  
 <span data-ttu-id="7cb3e-110">`transactionProtocol` özniteliği, bağlamayı kullanan hizmet uç noktaları ile kullanılacak işlem protokolünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="7cb3e-110">The `transactionProtocol` attribute specifies the transaction protocol to use with service endpoints that use the binding.</span></span>  
  
 <span data-ttu-id="7cb3e-111">Aşağıda, belirli bir bağlamayı işlem akışını destekleyecek şekilde yapılandıran bir yapılandırma bölümünün yanı sıra WS-AtomicTransaction protokolünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="7cb3e-111">The following is an example of a configuration section that configures the specified binding to support transaction flow, as well as a use the WS-AtomicTransaction protocol.</span></span>  
  
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
  
## <a name="configuring-transactiontimeout"></a><span data-ttu-id="7cb3e-112">TransactionTimeout yapılandırma</span><span class="sxs-lookup"><span data-stu-id="7cb3e-112">Configuring transactionTimeout</span></span>  
 <span data-ttu-id="7cb3e-113">WCF hizmetiniz için `transactionTimeout` özniteliğini yapılandırma dosyasının `behavior` öğesinde yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7cb3e-113">You can configure the `transactionTimeout` attribute for your WCF service in the `behavior` element of the configuration file.</span></span> <span data-ttu-id="7cb3e-114">Aşağıdaki kod bunun nasıl yapılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="7cb3e-114">The following code demonstrates how to do this.</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>  
         <behavior name="NewBehavior" transactionTimeout="00:01:00" /> <!-- 1 minute timeout -->  
      </behaviors>  
   </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="7cb3e-115">`transactionTimeout` özniteliği, hizmette oluşturulan yeni bir işlemin tamamlanma süresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7cb3e-115">The `transactionTimeout` attribute specifies the time period within which a new transaction created at the service must complete.</span></span> <span data-ttu-id="7cb3e-116">Yeni bir işlem kuran tüm işlemler için <xref:System.Transactions.TransactionScope> zaman aşımı olarak kullanılır ve <xref:System.ServiceModel.OperationBehaviorAttribute> uygulanmışsa <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> özelliği `true`olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="7cb3e-116">It is used as the <xref:System.Transactions.TransactionScope> time-out for any operation that establishes a new transaction, and if <xref:System.ServiceModel.OperationBehaviorAttribute> is applied, the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property is set to `true`.</span></span>  
  
 <span data-ttu-id="7cb3e-117">Zaman aşımı, iki aşamalı işleme protokolünde işlem 1 ' in tamamlanmasına kadar işlemin oluşturulmasından geçen süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="7cb3e-117">The time-out specifies the duration of time from the creation of the transaction to the completion of phase 1 in the two-phase commit protocol.</span></span>  
  
 <span data-ttu-id="7cb3e-118">Bu öznitelik `service` yapılandırma bölümünde ayarlandıysa, karşılık gelen hizmetin <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> özelliğinin `true`olarak ayarlandığı en az bir yöntemi <xref:System.ServiceModel.OperationBehaviorAttribute>uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7cb3e-118">If this attribute is set within a `service` configuration section, you should apply at least one method of the corresponding service with <xref:System.ServiceModel.OperationBehaviorAttribute>, in which the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property is set to `true`.</span></span>  
  
 <span data-ttu-id="7cb3e-119">Kullanılan zaman aşımı değerinin bu `transactionTimeout` yapılandırma ayarı ve <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> özelliği arasındaki daha küçük bir değer olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="7cb3e-119">Note that the time-out value used is the smaller value between this `transactionTimeout` configuration setting and any <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cb3e-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7cb3e-120">See also</span></span>

- [<span data-ttu-id="7cb3e-121">bağlama > \<</span><span class="sxs-lookup"><span data-stu-id="7cb3e-121">\<binding></span></span>](../../configure-apps/file-schema/wcf/bindings.md)
- [<span data-ttu-id="7cb3e-122">WCF Yapılandırma Şeması</span><span class="sxs-lookup"><span data-stu-id="7cb3e-122">WCF Configuration Schema</span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/index.md)
