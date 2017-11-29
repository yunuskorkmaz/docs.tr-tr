---
title: '&lt;transactionFlow&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8c40b3a79567ccc1ca5a83631253d3ff6ead0f84
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="lttransactionflowgt"></a><span data-ttu-id="49624-102">&lt;transactionFlow&gt;</span><span class="sxs-lookup"><span data-stu-id="49624-102">&lt;transactionFlow&gt;</span></span>
<span data-ttu-id="49624-103">Özel bağlama için işlem akışı destek belirtir.</span><span class="sxs-lookup"><span data-stu-id="49624-103">Specifies transaction flow support for the custom binding.</span></span>  
  
 <span data-ttu-id="49624-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="49624-104">\<system.serviceModel></span></span>  
<span data-ttu-id="49624-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="49624-105">\<bindings></span></span>  
<span data-ttu-id="49624-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="49624-106">\<customBinding></span></span>  
<span data-ttu-id="49624-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="49624-107">\<binding></span></span>  
<span data-ttu-id="49624-108">\<transactionFlow ></span><span class="sxs-lookup"><span data-stu-id="49624-108">\<transactionFlow></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49624-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="49624-109">Syntax</span></span>  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="49624-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="49624-110">Attributes and Elements</span></span>  
 <span data-ttu-id="49624-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="49624-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="49624-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="49624-112">Attributes</span></span>  
  
|<span data-ttu-id="49624-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="49624-113">Attribute</span></span>|<span data-ttu-id="49624-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="49624-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="49624-115">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="49624-115">transactionProtocol</span></span>|<span data-ttu-id="49624-116">Kullanılacak işlem protokolü belirtir.</span><span class="sxs-lookup"><span data-stu-id="49624-116">Specifies the transaction protocol to be used.</span></span> <span data-ttu-id="49624-117">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="49624-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="49624-118">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="49624-118">-   OleTransactions</span></span><br /><span data-ttu-id="49624-119">-WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="49624-119">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="49624-120">OleTransactions varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="49624-120">The default is OleTransactions.</span></span><br /><br /> <span data-ttu-id="49624-121">Bu öznitelik türünde <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="49624-121">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="49624-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="49624-122">Child Elements</span></span>  
 <span data-ttu-id="49624-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="49624-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="49624-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="49624-124">Parent Elements</span></span>  
  
|<span data-ttu-id="49624-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="49624-125">Element</span></span>|<span data-ttu-id="49624-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="49624-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="49624-127">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="49624-127">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="49624-128">Özel bağlama tüm bağlama özelliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="49624-128">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="49624-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="49624-129">Remarks</span></span>  
 <span data-ttu-id="49624-130">Bu öğe, etkinleştirme veya devre dışı bir uç noktanın bağlama ayarları gelen işlem akışında yanı gelen işlemler için istenen protokole biçimi belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="49624-130">This element allows you to enable or disable incoming transaction flow in an endpoint’s binding settings, as well as to specify the desired protocol format for incoming transactions.</span></span> <span data-ttu-id="49624-131">Bu yapılandırma öğesi kullanma hakkında daha fazla bilgi için bkz: [ServiceModel işlem Yapılandırması](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md) ve [işlem akışını etkinleştirme](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).</span><span class="sxs-lookup"><span data-stu-id="49624-131">For more information on using this configuration element, see [ServiceModel Transaction Configuration](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md) and [Enabling Transaction Flow](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="49624-132">Kullanırken `OleTransactions` akış işlemleri için uç nokta endpoint protokolü, hedef uç nokta herhangi bir iletişim kuralı dışındaki kullanarak yeniden akış denerse işlem zaman aşımı kaybolabilir `OleTransactions`.</span><span class="sxs-lookup"><span data-stu-id="49624-132">When using the `OleTransactions` protocol to flow transactions from endpoint to endpoint, the transaction timeout can be lost if the destination endpoint attempts to flow again using any protocol other than `OleTransactions`.</span></span> <span data-ttu-id="49624-133">Bu, OleTransactions atlama sonra zaman aşımına beklenenden daha sonra tüm alt düzey düğümleri neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="49624-133">This can cause all down-level nodes after the OleTransactions hop to timeout later than expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49624-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="49624-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TransactionFlowElement>  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="49624-135">ServiceModel işlem yapılandırması</span><span class="sxs-lookup"><span data-stu-id="49624-135">ServiceModel Transaction Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md)  
 [<span data-ttu-id="49624-136">İşlem akışını etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="49624-136">Enabling Transaction Flow</span></span>](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)  
 [<span data-ttu-id="49624-137">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="49624-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="49624-138">Bağlamaları genişletme</span><span class="sxs-lookup"><span data-stu-id="49624-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="49624-139">Özel bağlamalar</span><span class="sxs-lookup"><span data-stu-id="49624-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="49624-140">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="49624-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
