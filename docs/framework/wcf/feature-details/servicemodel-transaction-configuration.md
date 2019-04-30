---
title: ServiceModel İşlem Yapılandırması
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF], ServiceModel configuration
ms.assetid: 5636067a-7fbd-4485-aaa2-8141c502acf3
ms.openlocfilehash: d5bb81c618e3b27df32763948dbe56c9b37995e6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61747712"
---
# <a name="servicemodel-transaction-configuration"></a><span data-ttu-id="e7ef4-102">ServiceModel İşlem Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="e7ef4-102">ServiceModel Transaction Configuration</span></span>
<span data-ttu-id="e7ef4-103">Windows Communication Foundation (WCF) hizmeti için işlem yapılandırmak için üç öznitelikleri sağlar: `transactionFlow`, `transactionProtocol`, ve `transactionTimeout`.</span><span class="sxs-lookup"><span data-stu-id="e7ef4-103">Windows Communication Foundation (WCF) provides three attributes for configuring transactions for a service: `transactionFlow`, `transactionProtocol`, and `transactionTimeout`.</span></span>  
  
## <a name="configuring-transactionflow"></a><span data-ttu-id="e7ef4-104">TransactionFlow yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e7ef4-104">Configuring transactionFlow</span></span>  
 <span data-ttu-id="e7ef4-105">WCF sağlar içeren önceden tanımlanmış bağlamaları çoğu `transactionFlow` ve `transactionProtocol` öznitelikleri böylece bağlama gelen işlemleri belirli işlem akış protokolü kullanarak belirli bir uç nokta için kabul edecek şekilde yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7ef4-105">Most of the predefined bindings WCF provides contain the `transactionFlow` and `transactionProtocol` attributes, so that you can configure the binding to accept incoming transactions for a specific endpoint using a specific transaction flow protocol.</span></span> <span data-ttu-id="e7ef4-106">Ayrıca, kullanabileceğiniz `transactionFlow` öğesi ve kendi `transactionProtocol` kendi özel bağlama oluşturmak için öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e7ef4-106">In addition, you can use the `transactionFlow` element and its `transactionProtocol` attribute to build your own custom binding.</span></span> <span data-ttu-id="e7ef4-107">Yapılandırma öğeleri ayarlama hakkında daha fazla bilgi için bkz. [ \<bağlama >](../../../../docs/framework/misc/binding.md) ve [WCF yapılandırma şeması](../../../../docs/framework/configure-apps/file-schema/wcf/index.md).</span><span class="sxs-lookup"><span data-stu-id="e7ef4-107">For more information about setting the configuration elements, see [\<binding>](../../../../docs/framework/misc/binding.md) and [WCF Configuration Schema](../../../../docs/framework/configure-apps/file-schema/wcf/index.md).</span></span>  
  
 <span data-ttu-id="e7ef4-108">`transactionFlow` Özniteliği, işlem akışı bağlamayı kullanan hizmet uç noktaları için etkin olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e7ef4-108">The `transactionFlow` attribute specifies whether transaction flow is enabled for service endpoints that use the binding.</span></span>  
  
## <a name="configuring-transactionprotocol"></a><span data-ttu-id="e7ef4-109">TransactionProtocol yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e7ef4-109">Configuring transactionProtocol</span></span>  
 <span data-ttu-id="e7ef4-110">`transactionProtocol` Özniteliği bağlamayı kullanan hizmet uç noktaları ile kullanılacak işlem protokolünü belirler.</span><span class="sxs-lookup"><span data-stu-id="e7ef4-110">The `transactionProtocol` attribute specifies the transaction protocol to use with service endpoints that use the binding.</span></span>  
  
 <span data-ttu-id="e7ef4-111">Bir kullanım yanı sıra, işlem akışını desteklemek için belirtilen bağlama WS-AtomicTransaction Protokolü yapılandıran bir yapılandırma bölümünü örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e7ef4-111">The following is an example of a configuration section that configures the specified binding to support transaction flow, as well as a use the WS-AtomicTransaction protocol.</span></span>  
  
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
  
## <a name="configuring-transactiontimeout"></a><span data-ttu-id="e7ef4-112">TransactionTimeout yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e7ef4-112">Configuring transactionTimeout</span></span>  
 <span data-ttu-id="e7ef4-113">Yapılandırabileceğiniz `transactionTimeout` özniteliği için WCF hizmetinizi `behavior` yapılandırma dosyasının öğesi.</span><span class="sxs-lookup"><span data-stu-id="e7ef4-113">You can configure the `transactionTimeout` attribute for your WCF service in the `behavior` element of the configuration file.</span></span> <span data-ttu-id="e7ef4-114">Aşağıdaki kod, bunun nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e7ef4-114">The following code demonstrates how to do this.</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>  
         <behavior name="NewBehavior" transactionTimeout="00:01:00" /> <!-- 1 minute timeout -->  
      </behaviors>  
   </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="e7ef4-115">`transactionTimeout` Özniteliği içinde yeni bir işlem hizmeti oluşturulan tamamlamalısınız süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="e7ef4-115">The `transactionTimeout` attribute specifies the time period within which a new transaction created at the service must complete.</span></span> <span data-ttu-id="e7ef4-116">Olarak kullanılan <xref:System.Transactions.TransactionScope> yeni bir işlem oluşturur herhangi bir işlem için zaman aşımı ve <xref:System.ServiceModel.OperationBehaviorAttribute> uygulanan <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> özelliği `true`.</span><span class="sxs-lookup"><span data-stu-id="e7ef4-116">It is used as the <xref:System.Transactions.TransactionScope> time-out for any operation that establishes a new transaction, and if <xref:System.ServiceModel.OperationBehaviorAttribute> is applied, the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property is set to `true`.</span></span>  
  
 <span data-ttu-id="e7ef4-117">Zaman aşımı süre oluşturma işleminin tamamlanması 1. Aşama için iki aşamalı tamamlama protokolü belirtir.</span><span class="sxs-lookup"><span data-stu-id="e7ef4-117">The time-out specifies the duration of time from the creation of the transaction to the completion of phase 1 in the two-phase commit protocol.</span></span>  
  
 <span data-ttu-id="e7ef4-118">İçinde bu öznitelik ayarlanırsa bir `service` yapılandırma bölümü, en az bir yöntem ile ilgili hizmetin uygulanacağını <xref:System.ServiceModel.OperationBehaviorAttribute>, hangi <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> özelliği `true`.</span><span class="sxs-lookup"><span data-stu-id="e7ef4-118">If this attribute is set within a `service` configuration section, you should apply at least one method of the corresponding service with <xref:System.ServiceModel.OperationBehaviorAttribute>, in which the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property is set to `true`.</span></span>  
  
 <span data-ttu-id="e7ef4-119">Kullanılan zaman aşımı değeri bu arasında daha küçük değer olduğunu unutmayın `transactionTimeout` yapılandırma ayarı ve tüm <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="e7ef4-119">Note that the time-out value used is the smaller value between this `transactionTimeout` configuration setting and any <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7ef4-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7ef4-120">See also</span></span>

- [<span data-ttu-id="e7ef4-121">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="e7ef4-121">\<binding></span></span>](../../../../docs/framework/misc/binding.md)
- [<span data-ttu-id="e7ef4-122">WCF Yapılandırma Şeması</span><span class="sxs-lookup"><span data-stu-id="e7ef4-122">WCF Configuration Schema</span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/index.md)
