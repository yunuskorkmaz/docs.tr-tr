---
title: <transactionFlow>
ms.date: 03/30/2017
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
ms.openlocfilehash: ef3d92e07aaf4d4ba9d90e381017db104f2cc8fe
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55276999"
---
# <a name="transactionflow"></a><span data-ttu-id="26246-101">\<transactionFlow ></span><span class="sxs-lookup"><span data-stu-id="26246-101">\<transactionFlow></span></span>
<span data-ttu-id="26246-102">Özel bağlama için işlem akış desteğini belirler.</span><span class="sxs-lookup"><span data-stu-id="26246-102">Specifies transaction flow support for the custom binding.</span></span>  
  
 <span data-ttu-id="26246-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="26246-103">\<system.serviceModel></span></span>  
<span data-ttu-id="26246-104">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="26246-104">\<bindings></span></span>  
<span data-ttu-id="26246-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="26246-105">\<customBinding></span></span>  
<span data-ttu-id="26246-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="26246-106">\<binding></span></span>  
<span data-ttu-id="26246-107">\<transactionFlow ></span><span class="sxs-lookup"><span data-stu-id="26246-107">\<transactionFlow></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26246-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="26246-108">Syntax</span></span>  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="26246-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="26246-109">Attributes and Elements</span></span>  
 <span data-ttu-id="26246-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="26246-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="26246-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="26246-111">Attributes</span></span>  
  
|<span data-ttu-id="26246-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="26246-112">Attribute</span></span>|<span data-ttu-id="26246-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="26246-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="26246-114">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="26246-114">transactionProtocol</span></span>|<span data-ttu-id="26246-115">Kullanılacak işlem protokolünü belirler.</span><span class="sxs-lookup"><span data-stu-id="26246-115">Specifies the transaction protocol to be used.</span></span> <span data-ttu-id="26246-116">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="26246-116">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="26246-117">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="26246-117">-   OleTransactions</span></span><br /><span data-ttu-id="26246-118">-   WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="26246-118">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="26246-119">OleTransactions varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="26246-119">The default is OleTransactions.</span></span><br /><br /> <span data-ttu-id="26246-120">Bu öznitelik türünde <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="26246-120">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="26246-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="26246-121">Child Elements</span></span>  
 <span data-ttu-id="26246-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="26246-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="26246-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="26246-123">Parent Elements</span></span>  
  
|<span data-ttu-id="26246-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="26246-124">Element</span></span>|<span data-ttu-id="26246-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="26246-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="26246-126">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="26246-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="26246-127">Özel bağlama tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="26246-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26246-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="26246-128">Remarks</span></span>  
 <span data-ttu-id="26246-129">Bu öğe, etkinleştirme veya devre dışı gelen işlem akışı uç noktanın bağlama ayarları'nda, aynı zamanda gelen işlemler için istenen protokole biçimini belirtmek için sağlar.</span><span class="sxs-lookup"><span data-stu-id="26246-129">This element allows you to enable or disable incoming transaction flow in an endpoint’s binding settings, as well as to specify the desired protocol format for incoming transactions.</span></span> <span data-ttu-id="26246-130">Bu yapılandırma öğesi kullanma hakkında daha fazla bilgi için bkz. [ServiceModel işlem Yapılandırması](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md) ve [işlem akışını etkinleştirme](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).</span><span class="sxs-lookup"><span data-stu-id="26246-130">For more information on using this configuration element, see [ServiceModel Transaction Configuration](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md) and [Enabling Transaction Flow](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="26246-131">Kullanırken `OleTransactions` akış işlemleri için uç nokta endpoint protokol, hedef uç nokta yeniden dışında herhangi bir protokol kullanarak akış çalışırsa işlem zaman aşımı kaybolabilir `OleTransactions`.</span><span class="sxs-lookup"><span data-stu-id="26246-131">When using the `OleTransactions` protocol to flow transactions from endpoint to endpoint, the transaction timeout can be lost if the destination endpoint attempts to flow again using any protocol other than `OleTransactions`.</span></span> <span data-ttu-id="26246-132">Bu, OleTransactions atlama sonra zaman aşımına beklenenden daha sonra tüm alt düzey düğümleri neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="26246-132">This can cause all down-level nodes after the OleTransactions hop to timeout later than expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26246-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26246-133">See also</span></span>
- <xref:System.ServiceModel.Configuration.TransactionFlowElement>
- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="26246-134">ServiceModel İşlem Yapılandırması</span><span class="sxs-lookup"><span data-stu-id="26246-134">ServiceModel Transaction Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md)
- [<span data-ttu-id="26246-135">İşlem Akışını Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="26246-135">Enabling Transaction Flow</span></span>](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)
- [<span data-ttu-id="26246-136">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="26246-136">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="26246-137">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="26246-137">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="26246-138">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="26246-138">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="26246-139">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="26246-139">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
