---
title: '&lt;Bağlama&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 666183d6-4d1f-45c7-ac64-bdf93ee8f36f
ms.openlocfilehash: d72b3a34e0696df944b2338c89f167c8bfa06400
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33392258"
---
# <a name="ltbindinggt"></a><span data-ttu-id="72afb-102">&lt;Bağlama&gt;</span><span class="sxs-lookup"><span data-stu-id="72afb-102">&lt;binding&gt;</span></span>
<span data-ttu-id="72afb-103">Kullanabileceğiniz `binding` öğesi farklı türlerde yapılandırmak için Windows Communication Foundation (WCF) tarafından sağlanan bağlamaları önceden tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="72afb-103">You can use the `binding` element to configure different types of predefined bindings provided by Windows Communication Foundation (WCF).</span></span>  
  
## <a name="system-provided-binding"></a><span data-ttu-id="72afb-104">Sistem tarafından sağlanan bağlama</span><span class="sxs-lookup"><span data-stu-id="72afb-104">System-Provided Binding</span></span>  
 <span data-ttu-id="72afb-105">Sistem tarafından sağlanan bağlamalar WCF ileti yığını karmaşıklığını gizleyin.</span><span class="sxs-lookup"><span data-stu-id="72afb-105">System-provided bindings hide the complexity of the WCF messaging stack.</span></span> <span data-ttu-id="72afb-106">Sistem tarafından sağlanan bağlamalar kullanan uygulamalar yığın üzerinde tam denetim gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="72afb-106">Applications using system-provided bindings do not require full control over the stack.</span></span> <span data-ttu-id="72afb-107">Her sistem tarafından sağlanan bir bağlamayı üzerinde gösterilen öznitelikleri olanlardır en uygun kullanım senaryosu için bağlama adresleri.</span><span class="sxs-lookup"><span data-stu-id="72afb-107">The attributes exposed on each system-provided binding are the ones most appropriate for the usage scenario the binding addresses.</span></span>  
  
 <span data-ttu-id="72afb-108">Her sistem tarafından sağlanan bir bağlamayı yapılandırma bölümü bağlama yapılandırmak için kullanılan birkaç yapılandırmaları tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72afb-108">The configuration section for each system-provided binding can define several configurations used to configure the binding.</span></span> <span data-ttu-id="72afb-109">Her yapılandırma benzersiz bir ad tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="72afb-109">Each configuration is identified by a unique name.</span></span>  
  
 <span data-ttu-id="72afb-110">Öğe veya öznitelik sistem tarafından sağlanan bir bağlamayı eklemek mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="72afb-110">It is not possible to add elements or attributes to a system-provided binding.</span></span> <span data-ttu-id="72afb-111">Bunu yapmak için bu konunun "Özel bağlama" bölümünde açıklandığı gibi özel bağlama uygulamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="72afb-111">To do so, you should implement a custom binding as described in the "Custom Binding" section of this topic.</span></span> <span data-ttu-id="72afb-112">Sistem tarafından sağlanan mükemmel bağlama taklit eder ve kullanıcı uygulaması üzerinde denetime sahip olmasını istiyor birkaç ayar ekleyen özel bir bağlama tanımlamak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="72afb-112">It is possible to define a custom binding that mimics a system-provided binding perfectly and adds a few settings the user application wants to have control over.</span></span>  
  
## <a name="custom-binding"></a><span data-ttu-id="72afb-113">Özel Bağlama</span><span class="sxs-lookup"><span data-stu-id="72afb-113">Custom Binding</span></span>  
 <span data-ttu-id="72afb-114">Özel bağlamalar WCF ileti yığın üzerinde tam denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="72afb-114">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="72afb-115">Tek bir bağlama yığında göründükleri sırada yığını öğeleri için yapılandırma öğeleri belirterek ileti yığını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="72afb-115">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="72afb-116">Her öğe tanımlar ve bir öğe yığınının yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="72afb-116">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="72afb-117">Yalnızca tek olmalıdır `transport` her özel bağlama öğesinde.</span><span class="sxs-lookup"><span data-stu-id="72afb-117">There must be one and only one `transport` element in each custom binding.</span></span> <span data-ttu-id="72afb-118">Bu öğe Mesajlaşma yığını eksik.</span><span class="sxs-lookup"><span data-stu-id="72afb-118">Without this element, the messaging stack is incomplete.</span></span>  
  
 <span data-ttu-id="72afb-119">Öğeleri yığında görünme sırasını işlemleri iletiye uygulanma sırası olduğundan önemlidir.</span><span class="sxs-lookup"><span data-stu-id="72afb-119">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="72afb-120">Önerilen yığını öğelerin sırasını aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="72afb-120">The recommended order of stack elements is the following:</span></span>  
  
1.  <span data-ttu-id="72afb-121">İşlemler (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="72afb-121">Transactions (optional)</span></span>  
  
2.  <span data-ttu-id="72afb-122">Güvenilir Mesajlaşma (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="72afb-122">Reliable Messaging (optional)</span></span>  
  
3.  <span data-ttu-id="72afb-123">Güvenlik (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="72afb-123">Security (optional)</span></span>  
  
4.  <span data-ttu-id="72afb-124">Kodlayıcı</span><span class="sxs-lookup"><span data-stu-id="72afb-124">Encoder</span></span>  
  
5.  <span data-ttu-id="72afb-125">Taşıma</span><span class="sxs-lookup"><span data-stu-id="72afb-125">Transport</span></span>  
  
 <span data-ttu-id="72afb-126">Özel bağlamalar tanımlanır kendi `name` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="72afb-126">Custom bindings are identified by their `name` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72afb-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="72afb-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BindingsSection>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 [<span data-ttu-id="72afb-128">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="72afb-128">Bindings</span></span>](../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="72afb-129">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="72afb-129">Custom Bindings</span></span>](../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="72afb-130">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="72afb-130">\<customBinding></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
