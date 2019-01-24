---
title: '&lt;Bağlama&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 666183d6-4d1f-45c7-ac64-bdf93ee8f36f
ms.openlocfilehash: fb4fafda31205e2ce5efd01ab265fcacfa70bdf6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539200"
---
# <a name="ltbindinggt"></a><span data-ttu-id="81df1-102">&lt;Bağlama&gt;</span><span class="sxs-lookup"><span data-stu-id="81df1-102">&lt;binding&gt;</span></span>
<span data-ttu-id="81df1-103">Kullanabileceğiniz `binding` farklı yapılandırma öğesi Windows Communication Foundation (WCF) tarafından sağlanan bağlamaları önceden tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="81df1-103">You can use the `binding` element to configure different types of predefined bindings provided by Windows Communication Foundation (WCF).</span></span>  
  
## <a name="system-provided-binding"></a><span data-ttu-id="81df1-104">Sistem tarafından sağlanan bir bağlamayı</span><span class="sxs-lookup"><span data-stu-id="81df1-104">System-Provided Binding</span></span>  
 <span data-ttu-id="81df1-105">Sistem tarafından sağlanan bağlamalar WCF Mesajlaşma yığını karmaşıklığını gizler.</span><span class="sxs-lookup"><span data-stu-id="81df1-105">System-provided bindings hide the complexity of the WCF messaging stack.</span></span> <span data-ttu-id="81df1-106">Sistem tarafından sağlanan bağlamalar kullanan uygulamalar, yığını üzerinde tam denetim gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="81df1-106">Applications using system-provided bindings do not require full control over the stack.</span></span> <span data-ttu-id="81df1-107">Her sistem tarafından sağlanan bir bağlamayı üzerinde kullanıma sunulan öznitelikleri olanlardır çoğu kullanım senaryosu bağlamanın adreslerin uygun.</span><span class="sxs-lookup"><span data-stu-id="81df1-107">The attributes exposed on each system-provided binding are the ones most appropriate for the usage scenario the binding addresses.</span></span>  
  
 <span data-ttu-id="81df1-108">Her sistem tarafından sağlanan bir bağlamayı yapılandırma bölümü yapılandırmak için kullanılan birkaç yapılandırmaları tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="81df1-108">The configuration section for each system-provided binding can define several configurations used to configure the binding.</span></span> <span data-ttu-id="81df1-109">Her yapılandırma, benzersiz bir ad tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="81df1-109">Each configuration is identified by a unique name.</span></span>  
  
 <span data-ttu-id="81df1-110">Öğeler veya öznitelikleri için sistem tarafından sağlanan bir bağlamayı eklemek mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="81df1-110">It is not possible to add elements or attributes to a system-provided binding.</span></span> <span data-ttu-id="81df1-111">Bunu yapmak için bu konunun "Özel bağlama" bölümünde açıklandığı gibi özel bir bağlama uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="81df1-111">To do so, you should implement a custom binding as described in the "Custom Binding" section of this topic.</span></span> <span data-ttu-id="81df1-112">Sistem tarafından sağlanan mükemmel bir şekilde bağlama taklit eder ve kullanıcı uygulaması üzerinde denetime sahip ister birkaç ayar ekleyen özel bir bağlama tanımlamak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="81df1-112">It is possible to define a custom binding that mimics a system-provided binding perfectly and adds a few settings the user application wants to have control over.</span></span>  
  
## <a name="custom-binding"></a><span data-ttu-id="81df1-113">Özel Bağlama</span><span class="sxs-lookup"><span data-stu-id="81df1-113">Custom Binding</span></span>  
 <span data-ttu-id="81df1-114">Özel bağlamalar WCF Mesajlaşma yığını üzerinde tam denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="81df1-114">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="81df1-115">Tek bir bağlama yığında göründükleri sırayla yığın öğeler için yapılandırma öğeleri belirterek ileti yığın tanımlar.</span><span class="sxs-lookup"><span data-stu-id="81df1-115">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="81df1-116">Her öğe tanımlar ve bir öğe yığınının yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="81df1-116">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="81df1-117">Bir ve yalnızca bir olmalıdır `transport` her özel bir bağlama öğesi.</span><span class="sxs-lookup"><span data-stu-id="81df1-117">There must be one and only one `transport` element in each custom binding.</span></span> <span data-ttu-id="81df1-118">Bu öğe Mesajlaşma yığını eksik.</span><span class="sxs-lookup"><span data-stu-id="81df1-118">Without this element, the messaging stack is incomplete.</span></span>  
  
 <span data-ttu-id="81df1-119">Öğeleri yığında görünme sırasını çünkü bu işlem iletiyi uygulanma sırası önemlidir.</span><span class="sxs-lookup"><span data-stu-id="81df1-119">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="81df1-120">Önerilen yığın öğelerin sırasını aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="81df1-120">The recommended order of stack elements is the following:</span></span>  
  
1.  <span data-ttu-id="81df1-121">İşlemler (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="81df1-121">Transactions (optional)</span></span>  
  
2.  <span data-ttu-id="81df1-122">Güvenilir Mesajlaşma (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="81df1-122">Reliable Messaging (optional)</span></span>  
  
3.  <span data-ttu-id="81df1-123">Güvenlik (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="81df1-123">Security (optional)</span></span>  
  
4.  <span data-ttu-id="81df1-124">Kodlayıcı</span><span class="sxs-lookup"><span data-stu-id="81df1-124">Encoder</span></span>  
  
5.  <span data-ttu-id="81df1-125">Taşıma</span><span class="sxs-lookup"><span data-stu-id="81df1-125">Transport</span></span>  
  
 <span data-ttu-id="81df1-126">Özel bağlamalar tarafından tanımlanır, `name` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="81df1-126">Custom bindings are identified by their `name` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81df1-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="81df1-127">See also</span></span>
- <xref:System.ServiceModel.Configuration.BindingsSection>
- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- [<span data-ttu-id="81df1-128">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="81df1-128">Bindings</span></span>](../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="81df1-129">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="81df1-129">Custom Bindings</span></span>](../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="81df1-130">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="81df1-130">\<customBinding></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
