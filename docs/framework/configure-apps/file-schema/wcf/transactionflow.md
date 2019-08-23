---
title: <transactionFlow>
ms.date: 03/30/2017
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
ms.openlocfilehash: 206a684e1279871eee4aed95a087921123f8efb9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918656"
---
# <a name="transactionflow"></a><span data-ttu-id="1c876-101">\<transactionFlow ></span><span class="sxs-lookup"><span data-stu-id="1c876-101">\<transactionFlow></span></span>
<span data-ttu-id="1c876-102">Özel bağlama için işlem akış desteğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1c876-102">Specifies transaction flow support for the custom binding.</span></span>  
  
 <span data-ttu-id="1c876-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1c876-103">\<system.serviceModel></span></span>  
<span data-ttu-id="1c876-104">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="1c876-104">\<bindings></span></span>  
<span data-ttu-id="1c876-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="1c876-105">\<customBinding></span></span>  
<span data-ttu-id="1c876-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="1c876-106">\<binding></span></span>  
<span data-ttu-id="1c876-107">\<transactionFlow ></span><span class="sxs-lookup"><span data-stu-id="1c876-107">\<transactionFlow></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c876-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1c876-108">Syntax</span></span>  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1c876-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1c876-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1c876-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1c876-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1c876-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1c876-111">Attributes</span></span>  
  
|<span data-ttu-id="1c876-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1c876-112">Attribute</span></span>|<span data-ttu-id="1c876-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1c876-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1c876-114">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="1c876-114">transactionProtocol</span></span>|<span data-ttu-id="1c876-115">Kullanılacak işlem protokolünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="1c876-115">Specifies the transaction protocol to be used.</span></span> <span data-ttu-id="1c876-116">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="1c876-116">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1c876-117">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="1c876-117">-   OleTransactions</span></span><br /><span data-ttu-id="1c876-118">- WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="1c876-118">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="1c876-119">Varsayılan değer OleTransactions 'dir.</span><span class="sxs-lookup"><span data-stu-id="1c876-119">The default is OleTransactions.</span></span><br /><br /> <span data-ttu-id="1c876-120">Bu öznitelik türü <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="1c876-120">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1c876-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1c876-121">Child Elements</span></span>  
 <span data-ttu-id="1c876-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="1c876-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1c876-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1c876-123">Parent Elements</span></span>  
  
|<span data-ttu-id="1c876-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="1c876-124">Element</span></span>|<span data-ttu-id="1c876-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1c876-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1c876-126">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="1c876-126">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="1c876-127">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1c876-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c876-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1c876-128">Remarks</span></span>  
 <span data-ttu-id="1c876-129">Bu öğe, bir uç noktanın bağlama ayarlarında gelen işlem akışını etkinleştirmenizi veya devre dışı bırakmanızı, ayrıca gelen işlemler için istenen protokol biçimini belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="1c876-129">This element allows you to enable or disable incoming transaction flow in an endpoint’s binding settings, as well as to specify the desired protocol format for incoming transactions.</span></span> <span data-ttu-id="1c876-130">Bu yapılandırma öğesini kullanma hakkında daha fazla bilgi için bkz. [ServiceModel Işlem yapılandırması](../../../wcf/feature-details/servicemodel-transaction-configuration.md) ve [işlem akışını etkinleştirme](../../../wcf/feature-details/enabling-transaction-flow.md).</span><span class="sxs-lookup"><span data-stu-id="1c876-130">For more information on using this configuration element, see [ServiceModel Transaction Configuration](../../../wcf/feature-details/servicemodel-transaction-configuration.md) and [Enabling Transaction Flow](../../../wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="1c876-131">Uç noktadan uç `OleTransactions` noktaya işlem akışı yapmak için protokolü kullanırken, hedef uç noktası dışında `OleTransactions`herhangi bir protokolü kullanarak yeniden akışı denerse, işlem zaman aşımı kaybolabilir.</span><span class="sxs-lookup"><span data-stu-id="1c876-131">When using the `OleTransactions` protocol to flow transactions from endpoint to endpoint, the transaction timeout can be lost if the destination endpoint attempts to flow again using any protocol other than `OleTransactions`.</span></span> <span data-ttu-id="1c876-132">Bu, OleTransactions atından sonra beklenden sonra zaman aşımına uğradıktan sonra tüm alt düzey düğümlerin oluşmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="1c876-132">This can cause all down-level nodes after the OleTransactions hop to timeout later than expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c876-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c876-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactionFlowElement>
- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="1c876-134">ServiceModel İşlem Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="1c876-134">ServiceModel Transaction Configuration</span></span>](../../../wcf/feature-details/servicemodel-transaction-configuration.md)
- [<span data-ttu-id="1c876-135">İşlem Akışını Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="1c876-135">Enabling Transaction Flow</span></span>](../../../wcf/feature-details/enabling-transaction-flow.md)
- [<span data-ttu-id="1c876-136">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="1c876-136">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1c876-137">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="1c876-137">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="1c876-138">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="1c876-138">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="1c876-139">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="1c876-139">\<customBinding></span></span>](custombinding.md)
