---
title: "&lt;bağlamaları&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b62cd369-5409-4030-8490-9759a462dd3a
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ed672ee918ad969feb8be6d20c9206e6b5d12278
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltbindingsgt"></a><span data-ttu-id="6d89a-102">&lt;bağlamaları&gt;</span><span class="sxs-lookup"><span data-stu-id="6d89a-102">&lt;bindings&gt;</span></span>
<span data-ttu-id="6d89a-103">Bu bölümde, standart ve özel bağlamaları koleksiyonu tutar.</span><span class="sxs-lookup"><span data-stu-id="6d89a-103">This section holds a collection of standard and custom bindings.</span></span> <span data-ttu-id="6d89a-104">Her Giriş bir `binding` kendi benzersiz tanımlanabilir öğesi `name`.</span><span class="sxs-lookup"><span data-stu-id="6d89a-104">Each entry is a `binding` element that can be identified by its unique `name`.</span></span> <span data-ttu-id="6d89a-105">Hizmetlerini kullanan bağlamaları bağlayarak kullanarak `name`.</span><span class="sxs-lookup"><span data-stu-id="6d89a-105">Services use bindings by linking them using the `name`.</span></span> <span data-ttu-id="6d89a-106">İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları olmayan bir adı olması için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="6d89a-106">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="6d89a-107">Varsayılan yapılandırma ve adsız bağlamalar ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="6d89a-107">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="system-provided-binding"></a><span data-ttu-id="6d89a-108">Sistem tarafından sağlanan bağlama</span><span class="sxs-lookup"><span data-stu-id="6d89a-108">System-Provided Binding</span></span>  
 <span data-ttu-id="6d89a-109">Sistem tarafından sağlanan bağlamalar WCF ileti yığını karmaşıklığını gizleyin.</span><span class="sxs-lookup"><span data-stu-id="6d89a-109">System-provided bindings hide the complexity of the WCF messaging stack.</span></span> <span data-ttu-id="6d89a-110">Sistem tarafından sağlanan bağlamalar kullanan uygulamalar yığın üzerinde tam denetim gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="6d89a-110">Applications using system-provided bindings do not require full control over the stack.</span></span> <span data-ttu-id="6d89a-111">Her sistem tarafından sağlanan bir bağlamayı üzerinde gösterilen öznitelikleri olanlardır en uygun kullanım senaryosu için bağlama adresleri.</span><span class="sxs-lookup"><span data-stu-id="6d89a-111">The attributes exposed on each system-provided binding are the ones most appropriate for the usage scenario the binding addresses.</span></span>  
  
 <span data-ttu-id="6d89a-112">Her sistem tarafından sağlanan bir bağlamayı yapılandırma bölümü bağlama yapılandırmak için kullanılan birkaç yapılandırmaları tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d89a-112">The configuration section for each system-provided binding can define several configurations used to configure the binding.</span></span> <span data-ttu-id="6d89a-113">Her yapılandırma benzersiz bir ad tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="6d89a-113">Each configuration is identified by a unique name.</span></span>  
  
 <span data-ttu-id="6d89a-114">Öğe veya öznitelik sistem tarafından sağlanan bir bağlamayı eklemek mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="6d89a-114">It is not possible to add elements or attributes to a system-provided binding.</span></span> <span data-ttu-id="6d89a-115">Bunu yapmak için bu konunun "Özel bağlama" bölümünde açıklandığı gibi özel bağlama uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6d89a-115">To do so, you should implement a custom binding as described in the "Custom Binding" section of this topic.</span></span> <span data-ttu-id="6d89a-116">Sistem tarafından sağlanan mükemmel bağlama taklit eder ve kullanıcı uygulaması üzerinde denetime sahip olmasını istiyor birkaç ayar ekleyen özel bir bağlama tanımlamak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="6d89a-116">It is possible to define a custom binding that mimics a system-provided binding perfectly and adds a few settings the user application wants to have control over.</span></span>  
  
 <span data-ttu-id="6d89a-117">Sistem tarafından sağlanan bağlamalar listesi için bkz: [System-Provided bağlamaları](../../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="6d89a-117">For a list of system-provided bindings, see [System-Provided Bindings](../../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>  
  
## <a name="custom-binding"></a><span data-ttu-id="6d89a-118">Özel Bağlama</span><span class="sxs-lookup"><span data-stu-id="6d89a-118">Custom Binding</span></span>  
 <span data-ttu-id="6d89a-119">Özel bağlamalar WCF ileti yığın üzerinde tam denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="6d89a-119">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="6d89a-120">Tek bir bağlama yığında göründükleri sırada yığını öğeleri için yapılandırma öğeleri belirterek ileti yığını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6d89a-120">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="6d89a-121">Her öğe tanımlar ve bir öğe yığınının yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="6d89a-121">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="6d89a-122">Yalnızca tek olmalıdır `transport` her özel bağlama öğesinde.</span><span class="sxs-lookup"><span data-stu-id="6d89a-122">There must be one and only one `transport` element in each custom binding.</span></span> <span data-ttu-id="6d89a-123">Bu öğe Mesajlaşma yığını eksik.</span><span class="sxs-lookup"><span data-stu-id="6d89a-123">Without this element, the messaging stack is incomplete.</span></span>  
  
 <span data-ttu-id="6d89a-124">Öğeleri yığında görünme sırasını işlemleri iletiye uygulanma sırası olduğundan önemlidir.</span><span class="sxs-lookup"><span data-stu-id="6d89a-124">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="6d89a-125">Gerekli yığını öğelerin sırasını aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="6d89a-125">The required order of stack elements is the following:</span></span>  
  
1.  <span data-ttu-id="6d89a-126">İşlemler (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="6d89a-126">Transactions (optional)</span></span>  
  
2.  <span data-ttu-id="6d89a-127">Güvenilir Mesajlaşma (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="6d89a-127">Reliable Messaging (optional)</span></span>  
  
3.  <span data-ttu-id="6d89a-128">Güvenlik (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="6d89a-128">Security (optional)</span></span>  
  
4.  <span data-ttu-id="6d89a-129">Kodlayıcı</span><span class="sxs-lookup"><span data-stu-id="6d89a-129">Encoder</span></span>  
  
5.  <span data-ttu-id="6d89a-130">Taşıma</span><span class="sxs-lookup"><span data-stu-id="6d89a-130">Transport</span></span>  
  
 <span data-ttu-id="6d89a-131">Özel bağlamalar tanımlanır kendi `name` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="6d89a-131">Custom bindings are identified by their `name` attribute.</span></span> <span data-ttu-id="6d89a-132">Özel bağlama hakkında daha fazla bilgi için bkz: [özel bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="6d89a-132">For more information on custom bindings, see [Custom Bindings](../../../../../docs/framework/wcf/extending/custom-bindings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d89a-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6d89a-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BindingsSection>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 [<span data-ttu-id="6d89a-134">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="6d89a-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="6d89a-135">Özel bağlamalar</span><span class="sxs-lookup"><span data-stu-id="6d89a-135">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="6d89a-136">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="6d89a-136">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="6d89a-137">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="6d89a-137">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
