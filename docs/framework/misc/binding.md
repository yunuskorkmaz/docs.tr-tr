---
title: <binding>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 666183d6-4d1f-45c7-ac64-bdf93ee8f36f
ms.openlocfilehash: fb51eb1962603439b89a203eb668dfb543049170
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271479"
---
# <a name="binding"></a><span data-ttu-id="1e33f-101">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="1e33f-101">\<binding></span></span>
<span data-ttu-id="1e33f-102">Kullanabileceğiniz `binding` farklı yapılandırma öğesi Windows Communication Foundation (WCF) tarafından sağlanan bağlamaları önceden tanımlanmış.</span><span class="sxs-lookup"><span data-stu-id="1e33f-102">You can use the `binding` element to configure different types of predefined bindings provided by Windows Communication Foundation (WCF).</span></span>  
  
## <a name="system-provided-binding"></a><span data-ttu-id="1e33f-103">Sistem tarafından sağlanan bir bağlamayı</span><span class="sxs-lookup"><span data-stu-id="1e33f-103">System-Provided Binding</span></span>  
 <span data-ttu-id="1e33f-104">Sistem tarafından sağlanan bağlamalar WCF Mesajlaşma yığını karmaşıklığını gizler.</span><span class="sxs-lookup"><span data-stu-id="1e33f-104">System-provided bindings hide the complexity of the WCF messaging stack.</span></span> <span data-ttu-id="1e33f-105">Sistem tarafından sağlanan bağlamalar kullanan uygulamalar, yığını üzerinde tam denetim gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="1e33f-105">Applications using system-provided bindings do not require full control over the stack.</span></span> <span data-ttu-id="1e33f-106">Her sistem tarafından sağlanan bir bağlamayı üzerinde kullanıma sunulan öznitelikleri olanlardır çoğu kullanım senaryosu bağlamanın adreslerin uygun.</span><span class="sxs-lookup"><span data-stu-id="1e33f-106">The attributes exposed on each system-provided binding are the ones most appropriate for the usage scenario the binding addresses.</span></span>  
  
 <span data-ttu-id="1e33f-107">Her sistem tarafından sağlanan bir bağlamayı yapılandırma bölümü yapılandırmak için kullanılan birkaç yapılandırmaları tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e33f-107">The configuration section for each system-provided binding can define several configurations used to configure the binding.</span></span> <span data-ttu-id="1e33f-108">Her yapılandırma, benzersiz bir ad tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="1e33f-108">Each configuration is identified by a unique name.</span></span>  
  
 <span data-ttu-id="1e33f-109">Öğeler veya öznitelikleri için sistem tarafından sağlanan bir bağlamayı eklemek mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="1e33f-109">It is not possible to add elements or attributes to a system-provided binding.</span></span> <span data-ttu-id="1e33f-110">Bunu yapmak için bu konunun "Özel bağlama" bölümünde açıklandığı gibi özel bir bağlama uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="1e33f-110">To do so, you should implement a custom binding as described in the "Custom Binding" section of this topic.</span></span> <span data-ttu-id="1e33f-111">Sistem tarafından sağlanan mükemmel bir şekilde bağlama taklit eder ve kullanıcı uygulaması üzerinde denetime sahip ister birkaç ayar ekleyen özel bir bağlama tanımlamak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="1e33f-111">It is possible to define a custom binding that mimics a system-provided binding perfectly and adds a few settings the user application wants to have control over.</span></span>  
  
## <a name="custom-binding"></a><span data-ttu-id="1e33f-112">Özel Bağlama</span><span class="sxs-lookup"><span data-stu-id="1e33f-112">Custom Binding</span></span>  
 <span data-ttu-id="1e33f-113">Özel bağlamalar WCF Mesajlaşma yığını üzerinde tam denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="1e33f-113">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="1e33f-114">Tek bir bağlama yığında göründükleri sırayla yığın öğeler için yapılandırma öğeleri belirterek ileti yığın tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1e33f-114">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="1e33f-115">Her öğe tanımlar ve bir öğe yığınının yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="1e33f-115">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="1e33f-116">Bir ve yalnızca bir olmalıdır `transport` her özel bir bağlama öğesi.</span><span class="sxs-lookup"><span data-stu-id="1e33f-116">There must be one and only one `transport` element in each custom binding.</span></span> <span data-ttu-id="1e33f-117">Bu öğe Mesajlaşma yığını eksik.</span><span class="sxs-lookup"><span data-stu-id="1e33f-117">Without this element, the messaging stack is incomplete.</span></span>  
  
 <span data-ttu-id="1e33f-118">Öğeleri yığında görünme sırasını çünkü bu işlem iletiyi uygulanma sırası önemlidir.</span><span class="sxs-lookup"><span data-stu-id="1e33f-118">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="1e33f-119">Önerilen yığın öğelerin sırasını aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="1e33f-119">The recommended order of stack elements is the following:</span></span>  
  
1.  <span data-ttu-id="1e33f-120">İşlemler (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="1e33f-120">Transactions (optional)</span></span>  
  
2.  <span data-ttu-id="1e33f-121">Güvenilir Mesajlaşma (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="1e33f-121">Reliable Messaging (optional)</span></span>  
  
3.  <span data-ttu-id="1e33f-122">Güvenlik (isteğe bağlı)</span><span class="sxs-lookup"><span data-stu-id="1e33f-122">Security (optional)</span></span>  
  
4.  <span data-ttu-id="1e33f-123">Kodlayıcı</span><span class="sxs-lookup"><span data-stu-id="1e33f-123">Encoder</span></span>  
  
5.  <span data-ttu-id="1e33f-124">Taşıma</span><span class="sxs-lookup"><span data-stu-id="1e33f-124">Transport</span></span>  
  
 <span data-ttu-id="1e33f-125">Özel bağlamalar tarafından tanımlanır, `name` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="1e33f-125">Custom bindings are identified by their `name` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e33f-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e33f-126">See also</span></span>
- <xref:System.ServiceModel.Configuration.BindingsSection>
- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- [<span data-ttu-id="1e33f-127">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="1e33f-127">Bindings</span></span>](../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="1e33f-128">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="1e33f-128">Custom Bindings</span></span>](../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="1e33f-129">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="1e33f-129">\<customBinding></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
