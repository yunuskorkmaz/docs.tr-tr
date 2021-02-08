---
description: 'Hakkında daha fazla bilgi edinin: <transactionFlow>'
title: <transactionFlow>
ms.date: 03/30/2017
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
ms.openlocfilehash: 8a853beaec1837606ecb96156b8ec9381fa3e07a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773556"
---
# \<transactionFlow>

<span data-ttu-id="f90ca-102">Özel bağlama için işlem akış desteğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f90ca-102">Specifies transaction flow support for the custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transactionFlow>**  
  
## <a name="syntax"></a><span data-ttu-id="f90ca-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="f90ca-103">Syntax</span></span>  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f90ca-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f90ca-104">Attributes and Elements</span></span>  

 <span data-ttu-id="f90ca-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f90ca-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f90ca-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f90ca-106">Attributes</span></span>  
  
|<span data-ttu-id="f90ca-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f90ca-107">Attribute</span></span>|<span data-ttu-id="f90ca-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f90ca-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f90ca-109">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="f90ca-109">transactionProtocol</span></span>|<span data-ttu-id="f90ca-110">Kullanılacak işlem protokolünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="f90ca-110">Specifies the transaction protocol to be used.</span></span> <span data-ttu-id="f90ca-111">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f90ca-111">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f90ca-112">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="f90ca-112">-   OleTransactions</span></span><br /><span data-ttu-id="f90ca-113">- WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="f90ca-113">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="f90ca-114">Varsayılan değer OleTransactions 'dir.</span><span class="sxs-lookup"><span data-stu-id="f90ca-114">The default is OleTransactions.</span></span><br /><br /> <span data-ttu-id="f90ca-115">Bu öznitelik türü <xref:System.ServiceModel.TransactionProtocol> .</span><span class="sxs-lookup"><span data-stu-id="f90ca-115">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f90ca-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f90ca-116">Child Elements</span></span>  

 <span data-ttu-id="f90ca-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="f90ca-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f90ca-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f90ca-118">Parent Elements</span></span>  
  
|<span data-ttu-id="f90ca-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="f90ca-119">Element</span></span>|<span data-ttu-id="f90ca-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f90ca-120">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="f90ca-121">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f90ca-121">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f90ca-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f90ca-122">Remarks</span></span>  

 <span data-ttu-id="f90ca-123">Bu öğe, bir uç noktanın bağlama ayarlarında gelen işlem akışını etkinleştirmenizi veya devre dışı bırakmanızı, ayrıca gelen işlemler için istenen protokol biçimini belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f90ca-123">This element allows you to enable or disable incoming transaction flow in an endpoint’s binding settings, as well as to specify the desired protocol format for incoming transactions.</span></span> <span data-ttu-id="f90ca-124">Bu yapılandırma öğesini kullanma hakkında daha fazla bilgi için bkz. [ServiceModel Işlem yapılandırması](../../../wcf/feature-details/servicemodel-transaction-configuration.md) ve [işlem akışını etkinleştirme](../../../wcf/feature-details/enabling-transaction-flow.md).</span><span class="sxs-lookup"><span data-stu-id="f90ca-124">For more information on using this configuration element, see [ServiceModel Transaction Configuration](../../../wcf/feature-details/servicemodel-transaction-configuration.md) and [Enabling Transaction Flow](../../../wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="f90ca-125">Uç noktadan uç noktaya `OleTransactions` işlem akışı yapmak için protokolü kullanırken, hedef uç noktası dışında herhangi bir protokolü kullanarak yeniden akışı denerse, işlem zaman aşımı kaybolabilir `OleTransactions` .</span><span class="sxs-lookup"><span data-stu-id="f90ca-125">When using the `OleTransactions` protocol to flow transactions from endpoint to endpoint, the transaction timeout can be lost if the destination endpoint attempts to flow again using any protocol other than `OleTransactions`.</span></span> <span data-ttu-id="f90ca-126">Bu, OleTransactions atından sonra beklenden sonra zaman aşımına uğradıktan sonra tüm alt düzey düğümlerin oluşmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="f90ca-126">This can cause all down-level nodes after the OleTransactions hop to timeout later than expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f90ca-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f90ca-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactionFlowElement>
- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="f90ca-128">ServiceModel İşlem Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="f90ca-128">ServiceModel Transaction Configuration</span></span>](../../../wcf/feature-details/servicemodel-transaction-configuration.md)
- [<span data-ttu-id="f90ca-129">İşlem Akışını Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="f90ca-129">Enabling Transaction Flow</span></span>](../../../wcf/feature-details/enabling-transaction-flow.md)
- [<span data-ttu-id="f90ca-130">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="f90ca-130">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f90ca-131">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="f90ca-131">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="f90ca-132">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="f90ca-132">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
