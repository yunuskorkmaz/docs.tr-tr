---
title: <transactionFlow>
ms.date: 03/30/2017
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
ms.openlocfilehash: 626ae03d622221ab3e956bd03898b6cc30482c98
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59179159"
---
# <a name="transactionflow"></a><span data-ttu-id="55e33-101">\<transactionFlow ></span><span class="sxs-lookup"><span data-stu-id="55e33-101">\<transactionFlow></span></span>
<span data-ttu-id="55e33-102">Özel bağlama için işlem akış desteğini belirler.</span><span class="sxs-lookup"><span data-stu-id="55e33-102">Specifies transaction flow support for the custom binding.</span></span>  
  
 <span data-ttu-id="55e33-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="55e33-103">\<system.serviceModel></span></span>  
<span data-ttu-id="55e33-104">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="55e33-104">\<bindings></span></span>  
<span data-ttu-id="55e33-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="55e33-105">\<customBinding></span></span>  
<span data-ttu-id="55e33-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="55e33-106">\<binding></span></span>  
<span data-ttu-id="55e33-107">\<transactionFlow ></span><span class="sxs-lookup"><span data-stu-id="55e33-107">\<transactionFlow></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55e33-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="55e33-108">Syntax</span></span>  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="55e33-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="55e33-109">Attributes and Elements</span></span>  
 <span data-ttu-id="55e33-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="55e33-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="55e33-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="55e33-111">Attributes</span></span>  
  
|<span data-ttu-id="55e33-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="55e33-112">Attribute</span></span>|<span data-ttu-id="55e33-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55e33-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="55e33-114">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="55e33-114">transactionProtocol</span></span>|<span data-ttu-id="55e33-115">Kullanılacak işlem protokolünü belirler.</span><span class="sxs-lookup"><span data-stu-id="55e33-115">Specifies the transaction protocol to be used.</span></span> <span data-ttu-id="55e33-116">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="55e33-116">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="55e33-117">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="55e33-117">-   OleTransactions</span></span><br /><span data-ttu-id="55e33-118">-   WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="55e33-118">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="55e33-119">OleTransactions varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="55e33-119">The default is OleTransactions.</span></span><br /><br /> <span data-ttu-id="55e33-120">Bu öznitelik türünde <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="55e33-120">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="55e33-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="55e33-121">Child Elements</span></span>  
 <span data-ttu-id="55e33-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="55e33-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="55e33-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="55e33-123">Parent Elements</span></span>  
  
|<span data-ttu-id="55e33-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="55e33-124">Element</span></span>|<span data-ttu-id="55e33-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55e33-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="55e33-126">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="55e33-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="55e33-127">Özel bağlama tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="55e33-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55e33-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="55e33-128">Remarks</span></span>  
 <span data-ttu-id="55e33-129">Bu öğe, etkinleştirme veya devre dışı gelen işlem akışı uç noktanın bağlama ayarları'nda, aynı zamanda gelen işlemler için istenen protokole biçimini belirtmek için sağlar.</span><span class="sxs-lookup"><span data-stu-id="55e33-129">This element allows you to enable or disable incoming transaction flow in an endpoint’s binding settings, as well as to specify the desired protocol format for incoming transactions.</span></span> <span data-ttu-id="55e33-130">Bu yapılandırma öğesi kullanma hakkında daha fazla bilgi için bkz. [ServiceModel işlem Yapılandırması](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md) ve [işlem akışını etkinleştirme](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).</span><span class="sxs-lookup"><span data-stu-id="55e33-130">For more information on using this configuration element, see [ServiceModel Transaction Configuration](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md) and [Enabling Transaction Flow](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="55e33-131">Kullanırken `OleTransactions` akış işlemleri için uç nokta endpoint protokol, hedef uç nokta yeniden dışında herhangi bir protokol kullanarak akış çalışırsa işlem zaman aşımı kaybolabilir `OleTransactions`.</span><span class="sxs-lookup"><span data-stu-id="55e33-131">When using the `OleTransactions` protocol to flow transactions from endpoint to endpoint, the transaction timeout can be lost if the destination endpoint attempts to flow again using any protocol other than `OleTransactions`.</span></span> <span data-ttu-id="55e33-132">Bu, OleTransactions atlama sonra zaman aşımına beklenenden daha sonra tüm alt düzey düğümleri neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="55e33-132">This can cause all down-level nodes after the OleTransactions hop to timeout later than expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55e33-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55e33-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactionFlowElement>
- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="55e33-134">ServiceModel İşlem Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="55e33-134">ServiceModel Transaction Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md)
- [<span data-ttu-id="55e33-135">İşlem Akışını Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="55e33-135">Enabling Transaction Flow</span></span>](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)
- [<span data-ttu-id="55e33-136">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="55e33-136">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="55e33-137">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="55e33-137">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="55e33-138">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="55e33-138">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="55e33-139">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="55e33-139">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
