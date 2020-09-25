---
title: <transactionFlow>
ms.date: 03/30/2017
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
ms.openlocfilehash: c4e5cbac24e2c72791c2f5c0faed0703363c99e1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201427"
---
# \<transactionFlow>

<span data-ttu-id="5ca85-101">Özel bağlama için işlem akış desteğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5ca85-101">Specifies transaction flow support for the custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transactionFlow>**  
  
## <a name="syntax"></a><span data-ttu-id="5ca85-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="5ca85-102">Syntax</span></span>  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ca85-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ca85-103">Attributes and Elements</span></span>  

 <span data-ttu-id="5ca85-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5ca85-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ca85-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5ca85-105">Attributes</span></span>  
  
|<span data-ttu-id="5ca85-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5ca85-106">Attribute</span></span>|<span data-ttu-id="5ca85-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ca85-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5ca85-108">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="5ca85-108">transactionProtocol</span></span>|<span data-ttu-id="5ca85-109">Kullanılacak işlem protokolünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="5ca85-109">Specifies the transaction protocol to be used.</span></span> <span data-ttu-id="5ca85-110">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="5ca85-110">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="5ca85-111">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="5ca85-111">-   OleTransactions</span></span><br /><span data-ttu-id="5ca85-112">- WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="5ca85-112">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="5ca85-113">Varsayılan değer OleTransactions 'dir.</span><span class="sxs-lookup"><span data-stu-id="5ca85-113">The default is OleTransactions.</span></span><br /><br /> <span data-ttu-id="5ca85-114">Bu öznitelik türü <xref:System.ServiceModel.TransactionProtocol> .</span><span class="sxs-lookup"><span data-stu-id="5ca85-114">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5ca85-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ca85-115">Child Elements</span></span>  

 <span data-ttu-id="5ca85-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="5ca85-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5ca85-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ca85-117">Parent Elements</span></span>  
  
|<span data-ttu-id="5ca85-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="5ca85-118">Element</span></span>|<span data-ttu-id="5ca85-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ca85-119">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="5ca85-120">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5ca85-120">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ca85-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5ca85-121">Remarks</span></span>  

 <span data-ttu-id="5ca85-122">Bu öğe, bir uç noktanın bağlama ayarlarında gelen işlem akışını etkinleştirmenizi veya devre dışı bırakmanızı, ayrıca gelen işlemler için istenen protokol biçimini belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="5ca85-122">This element allows you to enable or disable incoming transaction flow in an endpoint’s binding settings, as well as to specify the desired protocol format for incoming transactions.</span></span> <span data-ttu-id="5ca85-123">Bu yapılandırma öğesini kullanma hakkında daha fazla bilgi için bkz. [ServiceModel Işlem yapılandırması](../../../wcf/feature-details/servicemodel-transaction-configuration.md) ve [işlem akışını etkinleştirme](../../../wcf/feature-details/enabling-transaction-flow.md).</span><span class="sxs-lookup"><span data-stu-id="5ca85-123">For more information on using this configuration element, see [ServiceModel Transaction Configuration](../../../wcf/feature-details/servicemodel-transaction-configuration.md) and [Enabling Transaction Flow](../../../wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="5ca85-124">Uç noktadan uç noktaya `OleTransactions` işlem akışı yapmak için protokolü kullanırken, hedef uç noktası dışında herhangi bir protokolü kullanarak yeniden akışı denerse, işlem zaman aşımı kaybolabilir `OleTransactions` .</span><span class="sxs-lookup"><span data-stu-id="5ca85-124">When using the `OleTransactions` protocol to flow transactions from endpoint to endpoint, the transaction timeout can be lost if the destination endpoint attempts to flow again using any protocol other than `OleTransactions`.</span></span> <span data-ttu-id="5ca85-125">Bu, OleTransactions atından sonra beklenden sonra zaman aşımına uğradıktan sonra tüm alt düzey düğümlerin oluşmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="5ca85-125">This can cause all down-level nodes after the OleTransactions hop to timeout later than expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ca85-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ca85-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactionFlowElement>
- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="5ca85-127">ServiceModel İşlem Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="5ca85-127">ServiceModel Transaction Configuration</span></span>](../../../wcf/feature-details/servicemodel-transaction-configuration.md)
- [<span data-ttu-id="5ca85-128">İşlem Akışını Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="5ca85-128">Enabling Transaction Flow</span></span>](../../../wcf/feature-details/enabling-transaction-flow.md)
- [<span data-ttu-id="5ca85-129">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="5ca85-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5ca85-130">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="5ca85-130">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="5ca85-131">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="5ca85-131">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
