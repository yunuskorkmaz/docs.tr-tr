---
title: ServiceModel İşlem Yapılandırması
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF], ServiceModel configuration
ms.assetid: 5636067a-7fbd-4485-aaa2-8141c502acf3
ms.openlocfilehash: 2c724e3f67bbf6554abffb44f101d2f28f748023
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498351"
---
# <a name="servicemodel-transaction-configuration"></a><span data-ttu-id="c4eb8-102">ServiceModel İşlem Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="c4eb8-102">ServiceModel Transaction Configuration</span></span>
<span data-ttu-id="c4eb8-103">Windows Communication Foundation (WCF) işlemleri için bir hizmeti yapılandırmak için üç öznitelikleri sağlar: `transactionFlow`, `transactionProtocol`, ve `transactionTimeout`.</span><span class="sxs-lookup"><span data-stu-id="c4eb8-103">Windows Communication Foundation (WCF) provides three attributes for configuring transactions for a service: `transactionFlow`, `transactionProtocol`, and `transactionTimeout`.</span></span>  
  
## <a name="configuring-transactionflow"></a><span data-ttu-id="c4eb8-104">TransactionFlow yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c4eb8-104">Configuring transactionFlow</span></span>  
 <span data-ttu-id="c4eb8-105">WCF sağlar içeren önceden tanımlanmış bağlamaları çoğu `transactionFlow` ve `transactionProtocol` öznitelikleri böylece bağlama belirli işlem akışı protokolünü kullanarak belirli bir uç noktası için gelen işlemler kabul edecek şekilde yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4eb8-105">Most of the predefined bindings WCF provides contain the `transactionFlow` and `transactionProtocol` attributes, so that you can configure the binding to accept incoming transactions for a specific endpoint using a specific transaction flow protocol.</span></span> <span data-ttu-id="c4eb8-106">Ayrıca, `transactionFlow` öğesi ve kendi `transactionProtocol` kendi özel bağlama oluşturmak için öznitelik.</span><span class="sxs-lookup"><span data-stu-id="c4eb8-106">In addition, you can use the `transactionFlow` element and its `transactionProtocol` attribute to build your own custom binding.</span></span> <span data-ttu-id="c4eb8-107">Yapılandırma öğelerini ayarlama hakkında daha fazla bilgi için bkz: [ \<bağlama >](../../../../docs/framework/misc/binding.md) ve [WCF yapılandırma şeması](../../../../docs/framework/configure-apps/file-schema/wcf/index.md).</span><span class="sxs-lookup"><span data-stu-id="c4eb8-107">For more information about setting the configuration elements, see [\<binding>](../../../../docs/framework/misc/binding.md) and [WCF Configuration Schema](../../../../docs/framework/configure-apps/file-schema/wcf/index.md).</span></span>  
  
 <span data-ttu-id="c4eb8-108">`transactionFlow` Özniteliği, işlem akışını bağlamayı kullanan hizmet uç noktaları için etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4eb8-108">The `transactionFlow` attribute specifies whether transaction flow is enabled for service endpoints that use the binding.</span></span>  
  
## <a name="configuring-transactionprotocol"></a><span data-ttu-id="c4eb8-109">TransactionProtocol yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c4eb8-109">Configuring transactionProtocol</span></span>  
 <span data-ttu-id="c4eb8-110">`transactionProtocol` Özniteliği bağlamayı kullanan hizmet uç noktaları ile kullanmak için işlem protokolü belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4eb8-110">The `transactionProtocol` attribute specifies the transaction protocol to use with service endpoints that use the binding.</span></span>  
  
 <span data-ttu-id="c4eb8-111">WS-AtomicTransaction protokolü, bir kullanım yanı sıra, işlem akışını desteklemek üzere belirtilen bağlama yapılandırır yapılandırma bölümünün bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c4eb8-111">The following is an example of a configuration section that configures the specified binding to support transaction flow, as well as a use the WS-AtomicTransaction protocol.</span></span>  
  
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
  
## <a name="configuring-transactiontimeout"></a><span data-ttu-id="c4eb8-112">TransactionTimeout yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c4eb8-112">Configuring transactionTimeout</span></span>  
 <span data-ttu-id="c4eb8-113">Yapılandırabileceğiniz `transactionTimeout` WCF hizmetiniz için öznitelik `behavior` yapılandırma dosyası öğesi.</span><span class="sxs-lookup"><span data-stu-id="c4eb8-113">You can configure the `transactionTimeout` attribute for your WCF service in the `behavior` element of the configuration file.</span></span> <span data-ttu-id="c4eb8-114">Aşağıdaki kod bunun nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c4eb8-114">The following code demonstrates how to do this.</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>  
         <behavior name="NewBehavior" transactionTimeout="00:01:00" /> <!-- 1 minute timeout -->  
      </behaviors>  
   </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="c4eb8-115">`transactionTimeout` Özniteliği içinde hizmeti oluşturulmuş yeni bir işlem tamamlanmalıdır zaman aralığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4eb8-115">The `transactionTimeout` attribute specifies the time period within which a new transaction created at the service must complete.</span></span> <span data-ttu-id="c4eb8-116">Olarak kullanılan <xref:System.Transactions.TransactionScope> yeni bir işlem kurar herhangi bir işlem için zaman aşımı ve <xref:System.ServiceModel.OperationBehaviorAttribute> uygulanan <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> özelliği ayarlanmış `true`.</span><span class="sxs-lookup"><span data-stu-id="c4eb8-116">It is used as the <xref:System.Transactions.TransactionScope> time-out for any operation that establishes a new transaction, and if <xref:System.ServiceModel.OperationBehaviorAttribute> is applied, the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property is set to `true`.</span></span>  
  
 <span data-ttu-id="c4eb8-117">Zaman aşımı süreyi oluşturma işleminin tamamlanması Aşama 1 için iki aşamalı yürütme Protokolü belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4eb8-117">The time-out specifies the duration of time from the creation of the transaction to the completion of phase 1 in the two-phase commit protocol.</span></span>  
  
 <span data-ttu-id="c4eb8-118">İçinde bu öznitelik ayarlanırsa bir `service` yapılandırma bölümünde, uygulamanız ile ilgili hizmetinin en az bir yöntemi <xref:System.ServiceModel.OperationBehaviorAttribute>, burada <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> özelliği ayarlanmış `true`.</span><span class="sxs-lookup"><span data-stu-id="c4eb8-118">If this attribute is set within a `service` configuration section, you should apply at least one method of the corresponding service with <xref:System.ServiceModel.OperationBehaviorAttribute>, in which the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property is set to `true`.</span></span>  
  
 <span data-ttu-id="c4eb8-119">Kullanılan zaman aşımı değeri bu arasında daha küçük olan değeri olduğuna dikkat edin `transactionTimeout` yapılandırma ayarı ve tüm <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="c4eb8-119">Note that the time-out value used is the smaller value between this `transactionTimeout` configuration setting and any <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4eb8-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c4eb8-120">See Also</span></span>  
 [<span data-ttu-id="c4eb8-121">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="c4eb8-121">\<binding></span></span>](../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="c4eb8-122">WCF Yapılandırma Şeması</span><span class="sxs-lookup"><span data-stu-id="c4eb8-122">WCF Configuration Schema</span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/index.md)
