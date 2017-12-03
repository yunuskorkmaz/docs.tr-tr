---
title: "ServiceModel İşlem Yapılandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: transactions [WCF], ServiceModel configuration
ms.assetid: 5636067a-7fbd-4485-aaa2-8141c502acf3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ef1d8a9e749c06701aa0a187f81b5b345518c07b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="servicemodel-transaction-configuration"></a><span data-ttu-id="062b1-102">ServiceModel İşlem Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="062b1-102">ServiceModel Transaction Configuration</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="062b1-103">bir hizmet için işlemleri yapılandırmak için üç öznitelikleri sağlar: `transactionFlow`, `transactionProtocol`, ve `transactionTimeout`.</span><span class="sxs-lookup"><span data-stu-id="062b1-103"> provides three attributes for configuring transactions for a service: `transactionFlow`, `transactionProtocol`, and `transactionTimeout`.</span></span>  
  
## <a name="configuring-transactionflow"></a><span data-ttu-id="062b1-104">TransactionFlow yapılandırma</span><span class="sxs-lookup"><span data-stu-id="062b1-104">Configuring transactionFlow</span></span>  
 <span data-ttu-id="062b1-105">Önceden tanımlanmış bağlamaları çoğu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sağlar içeren `transactionFlow` ve `transactionProtocol` öznitelikleri böylece bağlama belirli işlem akışı protokolünü kullanarak belirli bir uç noktası için gelen işlemler kabul edecek şekilde yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="062b1-105">Most of the predefined bindings [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides contain the `transactionFlow` and `transactionProtocol` attributes, so that you can configure the binding to accept incoming transactions for a specific endpoint using a specific transaction flow protocol.</span></span> <span data-ttu-id="062b1-106">Ayrıca, `transactionFlow` öğesi ve kendi `transactionProtocol` kendi özel bağlama oluşturmak için öznitelik.</span><span class="sxs-lookup"><span data-stu-id="062b1-106">In addition, you can use the `transactionFlow` element and its `transactionProtocol` attribute to build your own custom binding.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="062b1-107">yapılandırma öğelerini ayar bkz [ \<bağlama >](../../../../docs/framework/misc/binding.md) ve [WCF yapılandırma şeması](../../../../docs/framework/configure-apps/file-schema/wcf/index.md).</span><span class="sxs-lookup"><span data-stu-id="062b1-107"> setting the configuration elements, see [\<binding>](../../../../docs/framework/misc/binding.md) and [WCF Configuration Schema](../../../../docs/framework/configure-apps/file-schema/wcf/index.md).</span></span>  
  
 <span data-ttu-id="062b1-108">`transactionFlow` Özniteliği, işlem akışını bağlamayı kullanan hizmet uç noktaları için etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="062b1-108">The `transactionFlow` attribute specifies whether transaction flow is enabled for service endpoints that use the binding.</span></span>  
  
## <a name="configuring-transactionprotocol"></a><span data-ttu-id="062b1-109">TransactionProtocol yapılandırma</span><span class="sxs-lookup"><span data-stu-id="062b1-109">Configuring transactionProtocol</span></span>  
 <span data-ttu-id="062b1-110">`transactionProtocol` Özniteliği bağlamayı kullanan hizmet uç noktaları ile kullanmak için işlem protokolü belirtir.</span><span class="sxs-lookup"><span data-stu-id="062b1-110">The `transactionProtocol` attribute specifies the transaction protocol to use with service endpoints that use the binding.</span></span>  
  
 <span data-ttu-id="062b1-111">WS-AtomicTransaction protokolü, bir kullanım yanı sıra, işlem akışını desteklemek üzere belirtilen bağlama yapılandırır yapılandırma bölümünün bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="062b1-111">The following is an example of a configuration section that configures the specified binding to support transaction flow, as well as a use the WS-AtomicTransaction protocol.</span></span>  
  
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
  
## <a name="configuring-transactiontimeout"></a><span data-ttu-id="062b1-112">TransactionTimeout yapılandırma</span><span class="sxs-lookup"><span data-stu-id="062b1-112">Configuring transactionTimeout</span></span>  
 <span data-ttu-id="062b1-113">Yapılandırabileceğiniz `transactionTimeout` için özniteliği, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmeti `behavior` yapılandırma dosyası öğesi.</span><span class="sxs-lookup"><span data-stu-id="062b1-113">You can configure the `transactionTimeout` attribute for your [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service in the `behavior` element of the configuration file.</span></span> <span data-ttu-id="062b1-114">Aşağıdaki kod bunun nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="062b1-114">The following code demonstrates how to do this.</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>  
         <behavior name="NewBehavior" transactionTimeout="00:01:00" /> <!-- 1 minute timeout -->  
      </behaviors>  
   </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="062b1-115">`transactionTimeout` Özniteliği içinde hizmeti oluşturulmuş yeni bir işlem tamamlanmalıdır zaman aralığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="062b1-115">The `transactionTimeout` attribute specifies the time period within which a new transaction created at the service must complete.</span></span> <span data-ttu-id="062b1-116">Olarak kullanılan <xref:System.Transactions.TransactionScope> yeni bir işlem kurar herhangi bir işlem için zaman aşımı ve <xref:System.ServiceModel.OperationBehaviorAttribute> uygulanan <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> özelliği ayarlanmış `true`.</span><span class="sxs-lookup"><span data-stu-id="062b1-116">It is used as the <xref:System.Transactions.TransactionScope> time-out for any operation that establishes a new transaction, and if <xref:System.ServiceModel.OperationBehaviorAttribute> is applied, the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property is set to `true`.</span></span>  
  
 <span data-ttu-id="062b1-117">Zaman aşımı süreyi oluşturma işleminin tamamlanması Aşama 1 için iki aşamalı yürütme Protokolü belirtir.</span><span class="sxs-lookup"><span data-stu-id="062b1-117">The time-out specifies the duration of time from the creation of the transaction to the completion of phase 1 in the two-phase commit protocol.</span></span>  
  
 <span data-ttu-id="062b1-118">İçinde bu öznitelik ayarlanırsa bir `service` yapılandırma bölümünde, uygulamanız ile ilgili hizmetinin en az bir yöntemi <xref:System.ServiceModel.OperationBehaviorAttribute>, burada <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> özelliği ayarlanmış `true`.</span><span class="sxs-lookup"><span data-stu-id="062b1-118">If this attribute is set within a `service` configuration section, you should apply at least one method of the corresponding service with <xref:System.ServiceModel.OperationBehaviorAttribute>, in which the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property is set to `true`.</span></span>  
  
 <span data-ttu-id="062b1-119">Kullanılan zaman aşımı değeri bu arasında daha küçük olan değeri olduğuna dikkat edin `transactionTimeout` yapılandırma ayarı ve tüm <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="062b1-119">Note that the time-out value used is the smaller value between this `transactionTimeout` configuration setting and any <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="062b1-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="062b1-120">See Also</span></span>  
 [<span data-ttu-id="062b1-121">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="062b1-121">\<binding></span></span>](../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="062b1-122">WCF yapılandırma şeması</span><span class="sxs-lookup"><span data-stu-id="062b1-122">WCF Configuration Schema</span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/index.md)
