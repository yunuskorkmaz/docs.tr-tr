---
title: <transactionFlow>
ms.date: 03/30/2017
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
ms.openlocfilehash: f5bcd142fb2b032ea179bcbba68fee53b98d2d77
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736307"
---
# <a name="transactionflow"></a><span data-ttu-id="1c39d-101">\<transactionFlow ></span><span class="sxs-lookup"><span data-stu-id="1c39d-101">\<transactionFlow></span></span>
<span data-ttu-id="1c39d-102">Özel bağlama için işlem akış desteğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1c39d-102">Specifies transaction flow support for the custom binding.</span></span>  
  
<span data-ttu-id="1c39d-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="1c39d-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1c39d-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="1c39d-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="1c39d-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="1c39d-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="1c39d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="1c39d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="1c39d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="1c39d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="1c39d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<transactionFlow >**</span><span class="sxs-lookup"><span data-stu-id="1c39d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transactionFlow>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c39d-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1c39d-109">Syntax</span></span>  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1c39d-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1c39d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1c39d-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1c39d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1c39d-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1c39d-112">Attributes</span></span>  
  
|<span data-ttu-id="1c39d-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1c39d-113">Attribute</span></span>|<span data-ttu-id="1c39d-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1c39d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1c39d-115">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="1c39d-115">transactionProtocol</span></span>|<span data-ttu-id="1c39d-116">Kullanılacak işlem protokolünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="1c39d-116">Specifies the transaction protocol to be used.</span></span> <span data-ttu-id="1c39d-117">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="1c39d-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1c39d-118">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="1c39d-118">-   OleTransactions</span></span><br /><span data-ttu-id="1c39d-119">- WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="1c39d-119">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="1c39d-120">Varsayılan değer OleTransactions 'dir.</span><span class="sxs-lookup"><span data-stu-id="1c39d-120">The default is OleTransactions.</span></span><br /><br /> <span data-ttu-id="1c39d-121">Bu öznitelik <xref:System.ServiceModel.TransactionProtocol>türündedir.</span><span class="sxs-lookup"><span data-stu-id="1c39d-121">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1c39d-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1c39d-122">Child Elements</span></span>  
 <span data-ttu-id="1c39d-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="1c39d-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1c39d-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1c39d-124">Parent Elements</span></span>  
  
|<span data-ttu-id="1c39d-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="1c39d-125">Element</span></span>|<span data-ttu-id="1c39d-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1c39d-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1c39d-127">\< bağlama ></span><span class="sxs-lookup"><span data-stu-id="1c39d-127">\<binding></span></span>](bindings.md)|<span data-ttu-id="1c39d-128">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1c39d-128">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c39d-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1c39d-129">Remarks</span></span>  
 <span data-ttu-id="1c39d-130">Bu öğe, bir uç noktanın bağlama ayarlarında gelen işlem akışını etkinleştirmenizi veya devre dışı bırakmanızı, ayrıca gelen işlemler için istenen protokol biçimini belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="1c39d-130">This element allows you to enable or disable incoming transaction flow in an endpoint’s binding settings, as well as to specify the desired protocol format for incoming transactions.</span></span> <span data-ttu-id="1c39d-131">Bu yapılandırma öğesini kullanma hakkında daha fazla bilgi için bkz. [ServiceModel Işlem yapılandırması](../../../wcf/feature-details/servicemodel-transaction-configuration.md) ve [işlem akışını etkinleştirme](../../../wcf/feature-details/enabling-transaction-flow.md).</span><span class="sxs-lookup"><span data-stu-id="1c39d-131">For more information on using this configuration element, see [ServiceModel Transaction Configuration](../../../wcf/feature-details/servicemodel-transaction-configuration.md) and [Enabling Transaction Flow](../../../wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="1c39d-132">Uç noktadan uç noktaya işlem akışı için `OleTransactions` protokolü kullanılırken, hedef uç nokta `OleTransactions`dışındaki herhangi bir protokolü kullanarak yeniden akışı denerse, işlem zaman aşımı kaybolabilir.</span><span class="sxs-lookup"><span data-stu-id="1c39d-132">When using the `OleTransactions` protocol to flow transactions from endpoint to endpoint, the transaction timeout can be lost if the destination endpoint attempts to flow again using any protocol other than `OleTransactions`.</span></span> <span data-ttu-id="1c39d-133">Bu, OleTransactions atından sonra beklenden sonra zaman aşımına uğradıktan sonra tüm alt düzey düğümlerin oluşmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="1c39d-133">This can cause all down-level nodes after the OleTransactions hop to timeout later than expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c39d-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c39d-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactionFlowElement>
- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="1c39d-135">ServiceModel İşlem Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="1c39d-135">ServiceModel Transaction Configuration</span></span>](../../../wcf/feature-details/servicemodel-transaction-configuration.md)
- [<span data-ttu-id="1c39d-136">İşlem Akışını Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="1c39d-136">Enabling Transaction Flow</span></span>](../../../wcf/feature-details/enabling-transaction-flow.md)
- [<span data-ttu-id="1c39d-137">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="1c39d-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1c39d-138">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="1c39d-138">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="1c39d-139">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="1c39d-139">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="1c39d-140">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="1c39d-140">\<customBinding></span></span>](custombinding.md)
