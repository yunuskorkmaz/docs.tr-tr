---
title: <transactionFlow>
ms.date: 03/30/2017
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
ms.openlocfilehash: f5bcd142fb2b032ea179bcbba68fee53b98d2d77
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736307"
---
# \<transactionFlow>
<span data-ttu-id="7ae76-101">Özel bağlama için işlem akış desteğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7ae76-101">Specifies transaction flow support for the custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transactionFlow>**  
  
## <a name="syntax"></a><span data-ttu-id="7ae76-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7ae76-102">Syntax</span></span>  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7ae76-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7ae76-103">Attributes and Elements</span></span>  
 <span data-ttu-id="7ae76-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7ae76-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7ae76-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7ae76-105">Attributes</span></span>  
  
|<span data-ttu-id="7ae76-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7ae76-106">Attribute</span></span>|<span data-ttu-id="7ae76-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7ae76-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7ae76-108">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="7ae76-108">transactionProtocol</span></span>|<span data-ttu-id="7ae76-109">Kullanılacak işlem protokolünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="7ae76-109">Specifies the transaction protocol to be used.</span></span> <span data-ttu-id="7ae76-110">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="7ae76-110">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="7ae76-111">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="7ae76-111">-   OleTransactions</span></span><br /><span data-ttu-id="7ae76-112">- WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="7ae76-112">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="7ae76-113">Varsayılan değer OleTransactions 'dir.</span><span class="sxs-lookup"><span data-stu-id="7ae76-113">The default is OleTransactions.</span></span><br /><br /> <span data-ttu-id="7ae76-114">Bu öznitelik türü <xref:System.ServiceModel.TransactionProtocol> .</span><span class="sxs-lookup"><span data-stu-id="7ae76-114">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7ae76-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7ae76-115">Child Elements</span></span>  
 <span data-ttu-id="7ae76-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="7ae76-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7ae76-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7ae76-117">Parent Elements</span></span>  
  
|<span data-ttu-id="7ae76-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="7ae76-118">Element</span></span>|<span data-ttu-id="7ae76-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7ae76-119">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="7ae76-120">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7ae76-120">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ae76-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7ae76-121">Remarks</span></span>  
 <span data-ttu-id="7ae76-122">Bu öğe, bir uç noktanın bağlama ayarlarında gelen işlem akışını etkinleştirmenizi veya devre dışı bırakmanızı, ayrıca gelen işlemler için istenen protokol biçimini belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="7ae76-122">This element allows you to enable or disable incoming transaction flow in an endpoint’s binding settings, as well as to specify the desired protocol format for incoming transactions.</span></span> <span data-ttu-id="7ae76-123">Bu yapılandırma öğesini kullanma hakkında daha fazla bilgi için bkz. [ServiceModel Işlem yapılandırması](../../../wcf/feature-details/servicemodel-transaction-configuration.md) ve [işlem akışını etkinleştirme](../../../wcf/feature-details/enabling-transaction-flow.md).</span><span class="sxs-lookup"><span data-stu-id="7ae76-123">For more information on using this configuration element, see [ServiceModel Transaction Configuration](../../../wcf/feature-details/servicemodel-transaction-configuration.md) and [Enabling Transaction Flow](../../../wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="7ae76-124">Uç noktadan uç noktaya `OleTransactions` işlem akışı yapmak için protokolü kullanırken, hedef uç noktası dışında herhangi bir protokolü kullanarak yeniden akışı denerse, işlem zaman aşımı kaybolabilir `OleTransactions` .</span><span class="sxs-lookup"><span data-stu-id="7ae76-124">When using the `OleTransactions` protocol to flow transactions from endpoint to endpoint, the transaction timeout can be lost if the destination endpoint attempts to flow again using any protocol other than `OleTransactions`.</span></span> <span data-ttu-id="7ae76-125">Bu, OleTransactions atından sonra beklenden sonra zaman aşımına uğradıktan sonra tüm alt düzey düğümlerin oluşmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="7ae76-125">This can cause all down-level nodes after the OleTransactions hop to timeout later than expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ae76-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ae76-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactionFlowElement>
- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="7ae76-127">ServiceModel İşlem Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="7ae76-127">ServiceModel Transaction Configuration</span></span>](../../../wcf/feature-details/servicemodel-transaction-configuration.md)
- [<span data-ttu-id="7ae76-128">İşlem Akışını Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="7ae76-128">Enabling Transaction Flow</span></span>](../../../wcf/feature-details/enabling-transaction-flow.md)
- [<span data-ttu-id="7ae76-129">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="7ae76-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="7ae76-130">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="7ae76-130">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="7ae76-131">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="7ae76-131">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
