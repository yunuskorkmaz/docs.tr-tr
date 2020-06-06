---
title: <bindings>
ms.date: 01/22/2018
ms.assetid: b62cd369-5409-4030-8490-9759a462dd3a
ms.openlocfilehash: fe8f620668e35183890b8bba1f254a74c962f8d3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74139669"
---
# \<bindings>

<span data-ttu-id="7e102-101">`bindings`Windows Communication Foundation (WCF) için standart ve özel bağlamaların bir koleksiyonunu yapılandırmak için öğesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7e102-101">You can use the `bindings` element to configure a collection of standard and custom bindings for Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="7e102-102">Her giriş, `binding` benzersiz tarafından tanımlanabilecek bir öğedir `name` .</span><span class="sxs-lookup"><span data-stu-id="7e102-102">Each entry is a `binding` element that can be identified by its unique `name`.</span></span> <span data-ttu-id="7e102-103">Hizmetler, kullanarak bağlama yoluyla bağlamaları kullanır `name` .</span><span class="sxs-lookup"><span data-stu-id="7e102-103">Services use bindings by linking them using the `name`.</span></span> <span data-ttu-id="7e102-104">.NET Framework 4 ' den başlayarak bağlamalar ve davranışlar bir ada sahip olmak için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="7e102-104">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="7e102-105">Varsayılan yapılandırma ve ad Less bağlamaları ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](../../../wcf/simplified-configuration.md) ve Basitleştirilmiş yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="7e102-105">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>

## <a name="system-provided-bindings"></a><span data-ttu-id="7e102-106">Sistem tarafından sağlanmış bağlamalar</span><span class="sxs-lookup"><span data-stu-id="7e102-106">System-provided bindings</span></span>

<span data-ttu-id="7e102-107">Sistem tarafından sağlanmış bağlamalar, WCF mesajlaşma yığınının karmaşıklığını gizler.</span><span class="sxs-lookup"><span data-stu-id="7e102-107">System-provided bindings hide the complexity of the WCF messaging stack.</span></span> <span data-ttu-id="7e102-108">Sistem tarafından belirtilen bağlamaları kullanan uygulamalar, yığın üzerinde tam denetim gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="7e102-108">Applications using system-provided bindings do not require full control over the stack.</span></span> <span data-ttu-id="7e102-109">Sistem tarafından sunulan her bağlamada sunulan öznitelikler, bağlama adresleri kullanım senaryosuna en uygun olanlardır.</span><span class="sxs-lookup"><span data-stu-id="7e102-109">The attributes exposed on each system-provided binding are the ones most appropriate for the usage scenario the binding addresses.</span></span>

<span data-ttu-id="7e102-110">Her sistem tarafından sağlanmış bağlamanın yapılandırma bölümü, bağlamayı yapılandırmak için kullanılan birkaç yapılandırmayı tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="7e102-110">The configuration section for each system-provided binding can define several configurations used to configure the binding.</span></span> <span data-ttu-id="7e102-111">Her yapılandırma benzersiz bir ad ile tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="7e102-111">Each configuration is identified by a unique name.</span></span>

<span data-ttu-id="7e102-112">Sistem tarafından sağlanmış bir bağlamaya öğe veya öznitelik eklemek mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="7e102-112">It isn't possible to add elements or attributes to a system-provided binding.</span></span> <span data-ttu-id="7e102-113">Bunu yapmak için [Özel Bağlamalar](#custom-bindings) bölümünde açıklandığı gibi özel bir bağlama uygulamalısınız.</span><span class="sxs-lookup"><span data-stu-id="7e102-113">To do so, you should implement a custom binding as described in the [Custom bindings](#custom-bindings) section.</span></span> <span data-ttu-id="7e102-114">Sistem tarafından sağlanmış bağlamayı kusursuz bir şekilde taklit eden özel bir bağlama tanımlayabilir ve Kullanıcı uygulamasının denetimini sağlamak istediği birkaç ayarı ekler.</span><span class="sxs-lookup"><span data-stu-id="7e102-114">It's possible to define a custom binding that mimics a system-provided binding perfectly and adds a few settings the user application wants to have control over.</span></span>  

<span data-ttu-id="7e102-115">Sistem tarafından sunulan bağlamaların listesi için bkz. [sistem tarafından sunulan bağlamalar](../../../wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="7e102-115">For a list of system-provided bindings, see [System-Provided Bindings](../../../wcf/system-provided-bindings.md).</span></span>

## <a name="custom-bindings"></a><span data-ttu-id="7e102-116">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="7e102-116">Custom bindings</span></span>

<span data-ttu-id="7e102-117">Özel Bağlamalar, WCF mesajlaşma yığını üzerinde tam denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="7e102-117">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="7e102-118">Tek bir bağlama yığın öğeleri için yapılandırma öğelerini yığında göründükleri sırada belirterek ileti yığınını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7e102-118">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="7e102-119">Her öğe, yığının bir öğesini tanımlar ve yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="7e102-119">Each element defines and configures one element of the stack.</span></span> <span data-ttu-id="7e102-120">Her özel bağlamada tek bir ve yalnızca bir `transport` öğe olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7e102-120">There must be one and only one `transport` element in each custom binding.</span></span> <span data-ttu-id="7e102-121">Bu öğe olmadan mesajlaşma yığını tamamlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="7e102-121">Without this element, the messaging stack is incomplete.</span></span>

<span data-ttu-id="7e102-122">Öğelerin yığında görünme sırası önemli olduğundan, bu işlem, bu, işlemde hangi sırada görünecek?</span><span class="sxs-lookup"><span data-stu-id="7e102-122">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="7e102-123">Stack öğelerinin gereken sırası şunlardır:</span><span class="sxs-lookup"><span data-stu-id="7e102-123">The required order of stack elements is the following:</span></span>  

1. <span data-ttu-id="7e102-124">İşlemler (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="7e102-124">Transactions (optional)</span></span>  

2. <span data-ttu-id="7e102-125">Güvenilir Mesajlaşma (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="7e102-125">Reliable messaging (optional)</span></span>  

3. <span data-ttu-id="7e102-126">Güvenlik (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="7e102-126">Security (optional)</span></span>  

4. <span data-ttu-id="7e102-127">Kodlayıcısı</span><span class="sxs-lookup"><span data-stu-id="7e102-127">Encoder</span></span>  

5. <span data-ttu-id="7e102-128">Aktarım</span><span class="sxs-lookup"><span data-stu-id="7e102-128">Transport</span></span>  

 <span data-ttu-id="7e102-129">Özel Bağlamalar özniteliği tarafından tanımlanır `name` .</span><span class="sxs-lookup"><span data-stu-id="7e102-129">Custom bindings are identified by their `name` attribute.</span></span> <span data-ttu-id="7e102-130">Özel Bağlamalar hakkında daha fazla bilgi için bkz. [Özel Bağlamalar](../../../wcf/extending/custom-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="7e102-130">For more information on custom bindings, see [Custom Bindings](../../../wcf/extending/custom-bindings.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7e102-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7e102-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.BindingsSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.Binding?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>
- [<span data-ttu-id="7e102-132">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="7e102-132">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="7e102-133">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="7e102-133">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
