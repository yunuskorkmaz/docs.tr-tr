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
# <a name="servicemodel-transaction-configuration"></a><span data-ttu-id="757b8-102">ServiceModel İşlem Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="757b8-102">ServiceModel Transaction Configuration</span></span>
<span data-ttu-id="757b8-103">Windows Communication Foundation (WCF), bir hizmet için hareketleri `transactionFlow` `transactionProtocol`yapılandırmak `transactionTimeout`için üç öznitelik sağlar: , , ve .</span><span class="sxs-lookup"><span data-stu-id="757b8-103">Windows Communication Foundation (WCF) provides three attributes for configuring transactions for a service: `transactionFlow`, `transactionProtocol`, and `transactionTimeout`.</span></span>  
  
## <a name="configuring-transactionflow"></a><span data-ttu-id="757b8-104">İşlem akışını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="757b8-104">Configuring transactionFlow</span></span>  
 <span data-ttu-id="757b8-105">WCF'nin sağladığı önceden tanımlanmış bağlamaların çoğu, belirli bir işlem akışı protokolü kullanarak gelen işlemleri belirli bir uç nokta için kabul etmek üzere bağlamayı yapılandırabilmeniz için öznitelikleri `transactionFlow` ve `transactionProtocol` öznitelikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="757b8-105">Most of the predefined bindings WCF provides contain the `transactionFlow` and `transactionProtocol` attributes, so that you can configure the binding to accept incoming transactions for a specific endpoint using a specific transaction flow protocol.</span></span> <span data-ttu-id="757b8-106">Buna ek olarak, `transactionFlow` kendi özel `transactionProtocol` bağlama oluşturmak için öğeve özniteliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="757b8-106">In addition, you can use the `transactionFlow` element and its `transactionProtocol` attribute to build your own custom binding.</span></span> <span data-ttu-id="757b8-107">Yapılandırma öğelerini ayarlama hakkında daha fazla bilgi için [ \<bağlayıcı>](../../configure-apps/file-schema/wcf/bindings.md) ve [WCF Yapılandırma Şeması'na](../../../../docs/framework/configure-apps/file-schema/wcf/index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="757b8-107">For more information about setting the configuration elements, see [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) and [WCF Configuration Schema](../../../../docs/framework/configure-apps/file-schema/wcf/index.md).</span></span>  
  
 <span data-ttu-id="757b8-108">Öznitelik, `transactionFlow` bağlamayı kullanan hizmet uç noktaları için hareket akışının etkin olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="757b8-108">The `transactionFlow` attribute specifies whether transaction flow is enabled for service endpoints that use the binding.</span></span>  
  
## <a name="configuring-transactionprotocol"></a><span data-ttu-id="757b8-109">İşlemi YapılandırmaProtokolü</span><span class="sxs-lookup"><span data-stu-id="757b8-109">Configuring transactionProtocol</span></span>  
 <span data-ttu-id="757b8-110">Öznitelik, `transactionProtocol` bağlamayı kullanan hizmet uç noktalarıyla kullanılacak işlem protokolünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="757b8-110">The `transactionProtocol` attribute specifies the transaction protocol to use with service endpoints that use the binding.</span></span>  
  
 <span data-ttu-id="757b8-111">Aşağıda, belirtilen bağlamayı hareket akışını desteklemek için yapılandıran bir yapılandırma bölümünün yanı sıra WS-AtomicTransaction protokolünü kullanan bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="757b8-111">The following is an example of a configuration section that configures the specified binding to support transaction flow, as well as a use the WS-AtomicTransaction protocol.</span></span>  
  
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
  
## <a name="configuring-transactiontimeout"></a><span data-ttu-id="757b8-112">İşlemI YapılandırmaTimeout</span><span class="sxs-lookup"><span data-stu-id="757b8-112">Configuring transactionTimeout</span></span>  
 <span data-ttu-id="757b8-113">WCF hizmetinizin özniteliğini yapılandırma dosyasının `transactionTimeout` `behavior` öğesinde yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="757b8-113">You can configure the `transactionTimeout` attribute for your WCF service in the `behavior` element of the configuration file.</span></span> <span data-ttu-id="757b8-114">Aşağıdaki kod, bunun nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="757b8-114">The following code demonstrates how to do this.</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>  
         <behavior name="NewBehavior" transactionTimeout="00:01:00" /> <!-- 1 minute timeout -->  
      </behaviors>  
   </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="757b8-115">Öznitelik, `transactionTimeout` hizmette oluşturulan yeni bir işlemin tamamlanması gereken süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="757b8-115">The `transactionTimeout` attribute specifies the time period within which a new transaction created at the service must complete.</span></span> <span data-ttu-id="757b8-116">Yeni bir işlem <xref:System.Transactions.TransactionScope> oluşturan herhangi bir işlem için zaman aşımı <xref:System.ServiceModel.OperationBehaviorAttribute> olarak kullanılır <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> ve uygulanırsa, özellik `true`.</span><span class="sxs-lookup"><span data-stu-id="757b8-116">It is used as the <xref:System.Transactions.TransactionScope> time-out for any operation that establishes a new transaction, and if <xref:System.ServiceModel.OperationBehaviorAttribute> is applied, the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property is set to `true`.</span></span>  
  
 <span data-ttu-id="757b8-117">Zaman ayırma, işlemin oluşturulmasından iki aşamalı taahhüt protokolünde faz 1'in tamamlanmasına kadar olan süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="757b8-117">The time-out specifies the duration of time from the creation of the transaction to the completion of phase 1 in the two-phase commit protocol.</span></span>  
  
 <span data-ttu-id="757b8-118">Bu öznitelik `service` bir yapılandırma bölümünde ayarlanmışsa, <xref:System.ServiceModel.OperationBehaviorAttribute> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> ilgili hizmetin en az bir yöntemini uygulamanız gerekir, özelliğin . `true`</span><span class="sxs-lookup"><span data-stu-id="757b8-118">If this attribute is set within a `service` configuration section, you should apply at least one method of the corresponding service with <xref:System.ServiceModel.OperationBehaviorAttribute>, in which the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property is set to `true`.</span></span>  
  
 <span data-ttu-id="757b8-119">Kullanılan zaman aşım değerinin, bu `transactionTimeout` yapılandırma ayarı ile <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> herhangi bir özellik arasındaki daha küçük değer olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="757b8-119">Note that the time-out value used is the smaller value between this `transactionTimeout` configuration setting and any <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="757b8-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="757b8-120">See also</span></span>

- [<span data-ttu-id="757b8-121">\<bağlayıcı></span><span class="sxs-lookup"><span data-stu-id="757b8-121">\<binding></span></span>](../../configure-apps/file-schema/wcf/bindings.md)
- [<span data-ttu-id="757b8-122">WCF Yapılandırma Şeması</span><span class="sxs-lookup"><span data-stu-id="757b8-122">WCF Configuration Schema</span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/index.md)
