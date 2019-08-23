---
title: <bindings>
ms.date: 01/22/2018
ms.assetid: b62cd369-5409-4030-8490-9759a462dd3a
ms.openlocfilehash: 1292bc38ce1e542086edac5539c1b29e619e2a32
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926380"
---
# <a name="bindings"></a><span data-ttu-id="86087-101">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="86087-101">\<bindings></span></span>

<span data-ttu-id="86087-102">Windows Communication Foundation (WCF) `bindings` için standart ve özel bağlamaların bir koleksiyonunu yapılandırmak için öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86087-102">You can use the `bindings` element to configure a collection of standard and custom bindings for Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="86087-103">Her giriş, benzersiz `binding` `name`tarafından tanımlanabilecek bir öğedir.</span><span class="sxs-lookup"><span data-stu-id="86087-103">Each entry is a `binding` element that can be identified by its unique `name`.</span></span> <span data-ttu-id="86087-104">Hizmetler, `name`kullanarak bağlama yoluyla bağlamaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="86087-104">Services use bindings by linking them using the `name`.</span></span> <span data-ttu-id="86087-105">İle [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]başlayarak, bağlamaların ve davranışların bir ada sahip olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="86087-105">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="86087-106">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="86087-106">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="system-provided-bindings"></a><span data-ttu-id="86087-107">Sistem tarafından sağlanmış bağlamalar</span><span class="sxs-lookup"><span data-stu-id="86087-107">System-provided bindings</span></span>
 
 <span data-ttu-id="86087-108">Sistem tarafından sağlanmış bağlamalar, WCF mesajlaşma yığınının karmaşıklığını gizler.</span><span class="sxs-lookup"><span data-stu-id="86087-108">System-provided bindings hide the complexity of the WCF messaging stack.</span></span> <span data-ttu-id="86087-109">Sistem tarafından belirtilen bağlamaları kullanan uygulamalar, yığın üzerinde tam denetim gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="86087-109">Applications using system-provided bindings do not require full control over the stack.</span></span> <span data-ttu-id="86087-110">Sistem tarafından sunulan her bağlamada sunulan öznitelikler, bağlama adresleri kullanım senaryosuna en uygun olanlardır.</span><span class="sxs-lookup"><span data-stu-id="86087-110">The attributes exposed on each system-provided binding are the ones most appropriate for the usage scenario the binding addresses.</span></span>  
  
 <span data-ttu-id="86087-111">Her sistem tarafından sağlanmış bağlamanın yapılandırma bölümü, bağlamayı yapılandırmak için kullanılan birkaç yapılandırmayı tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="86087-111">The configuration section for each system-provided binding can define several configurations used to configure the binding.</span></span> <span data-ttu-id="86087-112">Her yapılandırma benzersiz bir ad ile tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="86087-112">Each configuration is identified by a unique name.</span></span>  
  
 <span data-ttu-id="86087-113">Sistem tarafından sağlanmış bir bağlamaya öğe veya öznitelik eklemek mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="86087-113">It isn't possible to add elements or attributes to a system-provided binding.</span></span> <span data-ttu-id="86087-114">Bunu yapmak için [Özel Bağlamalar](#custom-bindings) bölümünde açıklandığı gibi özel bir bağlama uygulamalısınız.</span><span class="sxs-lookup"><span data-stu-id="86087-114">To do so, you should implement a custom binding as described in the [Custom bindings](#custom-bindings) section.</span></span> <span data-ttu-id="86087-115">Sistem tarafından sağlanmış bağlamayı kusursuz bir şekilde taklit eden özel bir bağlama tanımlayabilir ve Kullanıcı uygulamasının denetimini sağlamak istediği birkaç ayarı ekler.</span><span class="sxs-lookup"><span data-stu-id="86087-115">It's possible to define a custom binding that mimics a system-provided binding perfectly and adds a few settings the user application wants to have control over.</span></span>  
  
 <span data-ttu-id="86087-116">Sistem tarafından sunulan bağlamaların listesi için bkz. [sistem tarafından sunulan bağlamalar](../../../wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="86087-116">For a list of system-provided bindings, see [System-Provided Bindings](../../../wcf/system-provided-bindings.md).</span></span>  
  
## <a name="custom-bindings"></a><span data-ttu-id="86087-117">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="86087-117">Custom bindings</span></span>

 <span data-ttu-id="86087-118">Özel Bağlamalar, WCF mesajlaşma yığını üzerinde tam denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="86087-118">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="86087-119">Tek bir bağlama yığın öğeleri için yapılandırma öğelerini yığında göründükleri sırada belirterek ileti yığınını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="86087-119">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="86087-120">Her öğe, yığının bir öğesini tanımlar ve yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="86087-120">Each element defines and configures one element of the stack.</span></span> <span data-ttu-id="86087-121">Her özel bağlamada tek bir ve yalnızca `transport` bir öğe olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="86087-121">There must be one and only one `transport` element in each custom binding.</span></span> <span data-ttu-id="86087-122">Bu öğe olmadan mesajlaşma yığını tamamlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="86087-122">Without this element, the messaging stack is incomplete.</span></span>  
  
 <span data-ttu-id="86087-123">Öğelerin yığında görünme sırası önemli olduğundan, bu işlem, bu, işlemde hangi sırada görünecek?</span><span class="sxs-lookup"><span data-stu-id="86087-123">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="86087-124">Stack öğelerinin gereken sırası şunlardır:</span><span class="sxs-lookup"><span data-stu-id="86087-124">The required order of stack elements is the following:</span></span>  
  
1. <span data-ttu-id="86087-125">İşlemler (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="86087-125">Transactions (optional)</span></span>  
  
2. <span data-ttu-id="86087-126">Güvenilir Mesajlaşma (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="86087-126">Reliable messaging (optional)</span></span>  
  
3. <span data-ttu-id="86087-127">Güvenlik (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="86087-127">Security (optional)</span></span>  
  
4. <span data-ttu-id="86087-128">Kodlayıcısı</span><span class="sxs-lookup"><span data-stu-id="86087-128">Encoder</span></span>  
  
5. <span data-ttu-id="86087-129">Aktarım</span><span class="sxs-lookup"><span data-stu-id="86087-129">Transport</span></span>  
  
 <span data-ttu-id="86087-130">Özel bağlamalar `name` özniteliği tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="86087-130">Custom bindings are identified by their `name` attribute.</span></span> <span data-ttu-id="86087-131">Özel Bağlamalar hakkında daha fazla bilgi için bkz. [Özel Bağlamalar](../../../wcf/extending/custom-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="86087-131">For more information on custom bindings, see [Custom Bindings](../../../wcf/extending/custom-bindings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86087-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86087-132">See also</span></span>

- <xref:System.ServiceModel.Configuration.BindingsSection?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.Binding?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>  
- [<span data-ttu-id="86087-133">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="86087-133">Bindings</span></span>](../../../wcf/bindings.md)  
- [<span data-ttu-id="86087-134">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="86087-134">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)  
- [<span data-ttu-id="86087-135">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="86087-135">\<customBinding></span></span>](custombinding.md)  
- [<span data-ttu-id="86087-136">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="86087-136">\<binding></span></span>](../../../misc/binding.md)
