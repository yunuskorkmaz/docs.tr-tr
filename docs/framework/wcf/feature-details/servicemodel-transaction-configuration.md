---
description: 'Daha fazla bilgi edinin: ServiceModel Işlem yapılandırması'
title: ServiceModel İşlem Yapılandırması
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF], ServiceModel configuration
ms.assetid: 5636067a-7fbd-4485-aaa2-8141c502acf3
ms.openlocfilehash: 260e3cbe94ce0d22887554705134eef72a031981
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793473"
---
# <a name="servicemodel-transaction-configuration"></a><span data-ttu-id="251b2-103">ServiceModel İşlem Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="251b2-103">ServiceModel Transaction Configuration</span></span>

<span data-ttu-id="251b2-104">Windows Communication Foundation (WCF), bir hizmetin işlemlerini yapılandırmak için üç öznitelik sağlar: `transactionFlow` , `transactionProtocol` ve `transactionTimeout` .</span><span class="sxs-lookup"><span data-stu-id="251b2-104">Windows Communication Foundation (WCF) provides three attributes for configuring transactions for a service: `transactionFlow`, `transactionProtocol`, and `transactionTimeout`.</span></span>  
  
## <a name="configuring-transactionflow"></a><span data-ttu-id="251b2-105">TransactionFlow yapılandırılıyor</span><span class="sxs-lookup"><span data-stu-id="251b2-105">Configuring transactionFlow</span></span>  

 <span data-ttu-id="251b2-106">Önceden tanımlanmış bağlamaların çoğu, `transactionFlow` ve `transactionProtocol` özniteliklerini içerir, böylece bağlamayı belirli bir işlem akış protokolünü kullanarak belirli bir uç nokta için gelen işlemleri kabul edecek şekilde yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="251b2-106">Most of the predefined bindings WCF provides contain the `transactionFlow` and `transactionProtocol` attributes, so that you can configure the binding to accept incoming transactions for a specific endpoint using a specific transaction flow protocol.</span></span> <span data-ttu-id="251b2-107">Buna ek olarak, `transactionFlow` `transactionProtocol` kendi özel bağlamalarınızı oluşturmak için öğesini ve özniteliğini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="251b2-107">In addition, you can use the `transactionFlow` element and its `transactionProtocol` attribute to build your own custom binding.</span></span> <span data-ttu-id="251b2-108">Yapılandırma öğelerini ayarlama hakkında daha fazla bilgi için bkz [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) . ve [WCF yapılandırma şeması](../../configure-apps/file-schema/wcf/index.md).</span><span class="sxs-lookup"><span data-stu-id="251b2-108">For more information about setting the configuration elements, see [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) and [WCF Configuration Schema](../../configure-apps/file-schema/wcf/index.md).</span></span>  
  
 <span data-ttu-id="251b2-109">`transactionFlow`Özniteliği, işlem akışının bağlamayı kullanan hizmet uç noktaları için etkin olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="251b2-109">The `transactionFlow` attribute specifies whether transaction flow is enabled for service endpoints that use the binding.</span></span>  
  
## <a name="configuring-transactionprotocol"></a><span data-ttu-id="251b2-110">TransactionProtocol yapılandırma</span><span class="sxs-lookup"><span data-stu-id="251b2-110">Configuring transactionProtocol</span></span>  

 <span data-ttu-id="251b2-111">`transactionProtocol`Özniteliği, bağlamayı kullanan hizmet uç noktaları ile kullanılacak işlem protokolünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="251b2-111">The `transactionProtocol` attribute specifies the transaction protocol to use with service endpoints that use the binding.</span></span>  
  
 <span data-ttu-id="251b2-112">Aşağıda, işlem akışını desteklemek için belirtilen bağlamayı yapılandıran bir yapılandırma bölümünün yanı sıra WS-AtomicTransaction protokolünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="251b2-112">The following is an example of a configuration section that configures the specified binding to support transaction flow, as well as a use the WS-AtomicTransaction protocol.</span></span>  
  
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
  
## <a name="configuring-transactiontimeout"></a><span data-ttu-id="251b2-113">TransactionTimeout yapılandırma</span><span class="sxs-lookup"><span data-stu-id="251b2-113">Configuring transactionTimeout</span></span>  

 <span data-ttu-id="251b2-114">`transactionTimeout`Yapılandırma dosyasının ÖĞESINDE WCF hizmetiniz için özniteliği yapılandırabilirsiniz `behavior` .</span><span class="sxs-lookup"><span data-stu-id="251b2-114">You can configure the `transactionTimeout` attribute for your WCF service in the `behavior` element of the configuration file.</span></span> <span data-ttu-id="251b2-115">Aşağıdaki kod bunun nasıl yapılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="251b2-115">The following code demonstrates how to do this.</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>  
         <behavior name="NewBehavior" transactionTimeout="00:01:00" /> <!-- 1 minute timeout -->  
      </behaviors>  
   </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="251b2-116">`transactionTimeout`Öznitelik, hizmette oluşturulan yeni bir işlemin tamamlanma süresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="251b2-116">The `transactionTimeout` attribute specifies the time period within which a new transaction created at the service must complete.</span></span> <span data-ttu-id="251b2-117"><xref:System.Transactions.TransactionScope>Yeni bir işlem kuran tüm işlemler için zaman aşımı olarak kullanılır ve <xref:System.ServiceModel.OperationBehaviorAttribute> uygulanmışsa, <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> özelliği olarak ayarlanır `true` .</span><span class="sxs-lookup"><span data-stu-id="251b2-117">It is used as the <xref:System.Transactions.TransactionScope> time-out for any operation that establishes a new transaction, and if <xref:System.ServiceModel.OperationBehaviorAttribute> is applied, the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property is set to `true`.</span></span>  
  
 <span data-ttu-id="251b2-118">Zaman aşımı, iki aşamalı işleme protokolünde işlem 1 ' in tamamlanmasına kadar işlemin oluşturulmasından geçen süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="251b2-118">The time-out specifies the duration of time from the creation of the transaction to the completion of phase 1 in the two-phase commit protocol.</span></span>  
  
 <span data-ttu-id="251b2-119">Bu öznitelik bir yapılandırma bölümünde ayarlandıysa, `service` karşılık gelen hizmetin, özelliği olarak ayarlandığı en az bir yöntemi uygulamanız gerekir <xref:System.ServiceModel.OperationBehaviorAttribute> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> `true` .</span><span class="sxs-lookup"><span data-stu-id="251b2-119">If this attribute is set within a `service` configuration section, you should apply at least one method of the corresponding service with <xref:System.ServiceModel.OperationBehaviorAttribute>, in which the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property is set to `true`.</span></span>  
  
 <span data-ttu-id="251b2-120">Kullanılan zaman aşımı değerinin bu `transactionTimeout` yapılandırma ayarı ile herhangi bir özellik arasındaki daha küçük bir değer olduğunu unutmayın <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> .</span><span class="sxs-lookup"><span data-stu-id="251b2-120">Note that the time-out value used is the smaller value between this `transactionTimeout` configuration setting and any <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="251b2-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="251b2-121">See also</span></span>

- [\<binding>](../../configure-apps/file-schema/wcf/bindings.md)
- [<span data-ttu-id="251b2-122">WCF yapılandırma şeması</span><span class="sxs-lookup"><span data-stu-id="251b2-122">WCF Configuration Schema</span></span>](../../configure-apps/file-schema/wcf/index.md)
