---
title: '&lt;TransactionFlow&gt;'
ms.date: 03/30/2017
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
ms.openlocfilehash: c708098676e5634281e29c17639304a1a9cf5afe
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="lttransactionflowgt"></a><span data-ttu-id="f3172-102">&lt;TransactionFlow&gt;</span><span class="sxs-lookup"><span data-stu-id="f3172-102">&lt;transactionFlow&gt;</span></span>
<span data-ttu-id="f3172-103">Özel bağlama için işlem akışı destek belirtir.</span><span class="sxs-lookup"><span data-stu-id="f3172-103">Specifies transaction flow support for the custom binding.</span></span>  
  
 <span data-ttu-id="f3172-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f3172-104">\<system.serviceModel></span></span>  
<span data-ttu-id="f3172-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="f3172-105">\<bindings></span></span>  
<span data-ttu-id="f3172-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="f3172-106">\<customBinding></span></span>  
<span data-ttu-id="f3172-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="f3172-107">\<binding></span></span>  
<span data-ttu-id="f3172-108">\<transactionFlow ></span><span class="sxs-lookup"><span data-stu-id="f3172-108">\<transactionFlow></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3172-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f3172-109">Syntax</span></span>  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3172-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f3172-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f3172-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f3172-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3172-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f3172-112">Attributes</span></span>  
  
|<span data-ttu-id="f3172-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f3172-113">Attribute</span></span>|<span data-ttu-id="f3172-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f3172-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f3172-115">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="f3172-115">transactionProtocol</span></span>|<span data-ttu-id="f3172-116">Kullanılacak işlem protokolü belirtir.</span><span class="sxs-lookup"><span data-stu-id="f3172-116">Specifies the transaction protocol to be used.</span></span> <span data-ttu-id="f3172-117">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f3172-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f3172-118">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="f3172-118">-   OleTransactions</span></span><br /><span data-ttu-id="f3172-119">-WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="f3172-119">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="f3172-120">OleTransactions varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="f3172-120">The default is OleTransactions.</span></span><br /><br /> <span data-ttu-id="f3172-121">Bu öznitelik türünde <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="f3172-121">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f3172-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f3172-122">Child Elements</span></span>  
 <span data-ttu-id="f3172-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="f3172-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f3172-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f3172-124">Parent Elements</span></span>  
  
|<span data-ttu-id="f3172-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="f3172-125">Element</span></span>|<span data-ttu-id="f3172-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f3172-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f3172-127">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="f3172-127">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="f3172-128">Özel bağlama tüm bağlama özelliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f3172-128">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3172-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f3172-129">Remarks</span></span>  
 <span data-ttu-id="f3172-130">Bu öğe, etkinleştirme veya devre dışı bir uç noktanın bağlama ayarları gelen işlem akışında yanı gelen işlemler için istenen protokole biçimi belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f3172-130">This element allows you to enable or disable incoming transaction flow in an endpoint’s binding settings, as well as to specify the desired protocol format for incoming transactions.</span></span> <span data-ttu-id="f3172-131">Bu yapılandırma öğesi kullanma hakkında daha fazla bilgi için bkz: [ServiceModel işlem Yapılandırması](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md) ve [işlem akışını etkinleştirme](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).</span><span class="sxs-lookup"><span data-stu-id="f3172-131">For more information on using this configuration element, see [ServiceModel Transaction Configuration](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md) and [Enabling Transaction Flow](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="f3172-132">Kullanırken `OleTransactions` akış işlemleri için uç nokta endpoint protokolü, hedef uç nokta herhangi bir iletişim kuralı dışındaki kullanarak yeniden akış denerse işlem zaman aşımı kaybolabilir `OleTransactions`.</span><span class="sxs-lookup"><span data-stu-id="f3172-132">When using the `OleTransactions` protocol to flow transactions from endpoint to endpoint, the transaction timeout can be lost if the destination endpoint attempts to flow again using any protocol other than `OleTransactions`.</span></span> <span data-ttu-id="f3172-133">Bu, OleTransactions atlama sonra zaman aşımına beklenenden daha sonra tüm alt düzey düğümleri neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="f3172-133">This can cause all down-level nodes after the OleTransactions hop to timeout later than expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3172-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f3172-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TransactionFlowElement>  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="f3172-135">ServiceModel İşlem Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="f3172-135">ServiceModel Transaction Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md)  
 [<span data-ttu-id="f3172-136">İşlem Akışını Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="f3172-136">Enabling Transaction Flow</span></span>](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)  
 [<span data-ttu-id="f3172-137">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="f3172-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="f3172-138">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="f3172-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="f3172-139">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="f3172-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="f3172-140">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="f3172-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
