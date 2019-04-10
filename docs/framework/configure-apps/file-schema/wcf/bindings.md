---
title: <bindings>
ms.date: 01/22/2018
ms.assetid: b62cd369-5409-4030-8490-9759a462dd3a
ms.openlocfilehash: 479941593b1abefe637525703140b02917c6692b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59316797"
---
# <a name="bindings"></a><span data-ttu-id="c94b0-101">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="c94b0-101">\<bindings></span></span>

<span data-ttu-id="c94b0-102">Kullanabileceğiniz `bindings` standart ve özel bağlamalar için Windows Communication Foundation (WCF) koleksiyonu yapılandırmak için öğesi.</span><span class="sxs-lookup"><span data-stu-id="c94b0-102">You can use the `bindings` element to configure a collection of standard and custom bindings for Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="c94b0-103">Her Giriş bir `binding` kendi benzersiz tarafından tanımlanabilir öğesi `name`.</span><span class="sxs-lookup"><span data-stu-id="c94b0-103">Each entry is a `binding` element that can be identified by its unique `name`.</span></span> <span data-ttu-id="c94b0-104">Hizmetlerini kullanan bağlamaları bağlayarak kullanarak `name`.</span><span class="sxs-lookup"><span data-stu-id="c94b0-104">Services use bindings by linking them using the `name`.</span></span> <span data-ttu-id="c94b0-105">İle başlayarak [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bağlamalar ve davranışları için gerekli değildir bir ada sahip.</span><span class="sxs-lookup"><span data-stu-id="c94b0-105">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="c94b0-106">Varsayılan yapılandırma ve adsız bağlamaları ve davranışları hakkında daha fazla bilgi için bkz: [Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="c94b0-106">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="system-provided-bindings"></a><span data-ttu-id="c94b0-107">Sistem tarafından sağlanan bağlamalar</span><span class="sxs-lookup"><span data-stu-id="c94b0-107">System-provided bindings</span></span>
 
 <span data-ttu-id="c94b0-108">Sistem tarafından sağlanan bağlamalar WCF Mesajlaşma yığını karmaşıklığını gizler.</span><span class="sxs-lookup"><span data-stu-id="c94b0-108">System-provided bindings hide the complexity of the WCF messaging stack.</span></span> <span data-ttu-id="c94b0-109">Sistem tarafından sağlanan bağlamalar kullanan uygulamalar, yığını üzerinde tam denetim gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="c94b0-109">Applications using system-provided bindings do not require full control over the stack.</span></span> <span data-ttu-id="c94b0-110">Her sistem tarafından sağlanan bir bağlamayı üzerinde kullanıma sunulan öznitelikleri olanlardır çoğu kullanım senaryosu bağlamanın adreslerin uygun.</span><span class="sxs-lookup"><span data-stu-id="c94b0-110">The attributes exposed on each system-provided binding are the ones most appropriate for the usage scenario the binding addresses.</span></span>  
  
 <span data-ttu-id="c94b0-111">Her sistem tarafından sağlanan bir bağlamayı yapılandırma bölümü yapılandırmak için kullanılan birkaç yapılandırmaları tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c94b0-111">The configuration section for each system-provided binding can define several configurations used to configure the binding.</span></span> <span data-ttu-id="c94b0-112">Her yapılandırma, benzersiz bir ad tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="c94b0-112">Each configuration is identified by a unique name.</span></span>  
  
 <span data-ttu-id="c94b0-113">Öğeler veya öznitelikleri için sistem tarafından sağlanan bir bağlamayı eklemek mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="c94b0-113">It isn't possible to add elements or attributes to a system-provided binding.</span></span> <span data-ttu-id="c94b0-114">Bunu yapmak için özel bir bağlama açıklandığı uygulamalıdır [özel bağlamalar](#custom-bindings) bölümü.</span><span class="sxs-lookup"><span data-stu-id="c94b0-114">To do so, you should implement a custom binding as described in the [Custom bindings](#custom-bindings) section.</span></span> <span data-ttu-id="c94b0-115">Sistem tarafından sağlanan mükemmel bir şekilde bağlama taklit eder ve kullanıcı uygulaması üzerinde denetime sahip ister birkaç ayar ekleyen özel bir bağlama tanımlamak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="c94b0-115">It's possible to define a custom binding that mimics a system-provided binding perfectly and adds a few settings the user application wants to have control over.</span></span>  
  
 <span data-ttu-id="c94b0-116">Sistem tarafından sağlanan bağlamalar bir listesi için bkz. [System-Provided bağlamaları](../../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="c94b0-116">For a list of system-provided bindings, see [System-Provided Bindings](../../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>  
  
## <a name="custom-bindings"></a><span data-ttu-id="c94b0-117">Özel bağlamalar</span><span class="sxs-lookup"><span data-stu-id="c94b0-117">Custom bindings</span></span>

 <span data-ttu-id="c94b0-118">Özel bağlamalar WCF Mesajlaşma yığını üzerinde tam denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="c94b0-118">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="c94b0-119">Tek bir bağlama yığında göründükleri sırayla yığın öğeler için yapılandırma öğeleri belirterek ileti yığın tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c94b0-119">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="c94b0-120">Her öğe tanımlar ve bir öğe yığınının yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="c94b0-120">Each element defines and configures one element of the stack.</span></span> <span data-ttu-id="c94b0-121">Bir ve yalnızca bir olmalıdır `transport` her özel bir bağlama öğesi.</span><span class="sxs-lookup"><span data-stu-id="c94b0-121">There must be one and only one `transport` element in each custom binding.</span></span> <span data-ttu-id="c94b0-122">Bu öğe Mesajlaşma yığını eksik.</span><span class="sxs-lookup"><span data-stu-id="c94b0-122">Without this element, the messaging stack is incomplete.</span></span>  
  
 <span data-ttu-id="c94b0-123">Öğeleri yığında görünme sırasını çünkü bu işlem iletiyi uygulanma sırası önemlidir.</span><span class="sxs-lookup"><span data-stu-id="c94b0-123">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="c94b0-124">Gerekli yığın öğelerin sırasını aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="c94b0-124">The required order of stack elements is the following:</span></span>  
  
1. <span data-ttu-id="c94b0-125">İşlemler (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="c94b0-125">Transactions (optional)</span></span>  
  
2. <span data-ttu-id="c94b0-126">Güvenilir Mesajlaşma (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="c94b0-126">Reliable messaging (optional)</span></span>  
  
3. <span data-ttu-id="c94b0-127">Güvenlik (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="c94b0-127">Security (optional)</span></span>  
  
4. <span data-ttu-id="c94b0-128">Kodlayıcı</span><span class="sxs-lookup"><span data-stu-id="c94b0-128">Encoder</span></span>  
  
5. <span data-ttu-id="c94b0-129">Taşıma</span><span class="sxs-lookup"><span data-stu-id="c94b0-129">Transport</span></span>  
  
 <span data-ttu-id="c94b0-130">Özel bağlamalar tarafından tanımlanır, `name` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="c94b0-130">Custom bindings are identified by their `name` attribute.</span></span> <span data-ttu-id="c94b0-131">Özel bağlamalar hakkında daha fazla bilgi için bkz. [özel bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="c94b0-131">For more information on custom bindings, see [Custom Bindings](../../../../../docs/framework/wcf/extending/custom-bindings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c94b0-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c94b0-132">See also</span></span>

- <xref:System.ServiceModel.Configuration.BindingsSection?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.Binding?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>  
- [<span data-ttu-id="c94b0-133">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="c94b0-133">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
- [<span data-ttu-id="c94b0-134">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="c94b0-134">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
- [<span data-ttu-id="c94b0-135">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="c94b0-135">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
- [<span data-ttu-id="c94b0-136">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="c94b0-136">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
