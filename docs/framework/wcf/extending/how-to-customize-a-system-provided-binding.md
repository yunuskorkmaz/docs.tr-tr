---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: System-Provided bağlamayı özelleştirme'
title: 'Nasıl yapılır: Sistem Tarafından Sağlanan Bir Bağlamayı Özelleştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f8b97862-e8bb-470d-8b96-07733c21fe26
ms.openlocfilehash: c0463a8e427e6503f0e68bc58eb488f9b0bad15a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668961"
---
# <a name="how-to-customize-a-system-provided-binding"></a><span data-ttu-id="3e6af-103">Nasıl yapılır: Sistem Tarafından Sağlanan Bir Bağlamayı Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="3e6af-103">How to: Customize a System-Provided Binding</span></span>

<span data-ttu-id="3e6af-104">Windows Communication Foundation (WCF), temel bağlama öğelerinin bazı özelliklerini yapılandırmanıza imkan tanıyan, ancak özelliklerin tümünü değil, sistem tarafından sunulan birçok bağlama içerir.</span><span class="sxs-lookup"><span data-stu-id="3e6af-104">Windows Communication Foundation (WCF) includes several system-provided bindings that allow you to configure some of the properties of the underlying binding elements, but not all of the properties.</span></span> <span data-ttu-id="3e6af-105">Bu konu başlığı altında, bağlama öğelerinde nasıl özel bir bağlama oluşturacağınız özelliklerinin nasıl ayarlanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3e6af-105">This topic demonstrates how to set properties on the binding elements to create a custom binding.</span></span>  
  
 <span data-ttu-id="3e6af-106">Bağlama öğelerinin sistem tarafından sağlanmış bağlamaları kullanılmadan doğrudan oluşturulması ve yapılandırılması hakkında daha fazla bilgi için bkz. [Özel Bağlamalar](custom-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="3e6af-106">For more information about how to directly create and configure binding elements without using the system-provided bindings, see [Custom Bindings](custom-bindings.md).</span></span>  
  
 <span data-ttu-id="3e6af-107">Özel Bağlamalar Oluşturma ve genişletme hakkında daha fazla bilgi için bkz. [bağlamaları genişletme](extending-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="3e6af-107">For more information about creating and extending custom bindings, see [Extending Bindings](extending-bindings.md).</span></span>  
  
 <span data-ttu-id="3e6af-108">WCF 'de tüm bağlamalar *bağlama öğelerinden* oluşur.</span><span class="sxs-lookup"><span data-stu-id="3e6af-108">In WCF all bindings are made up of *binding elements*.</span></span> <span data-ttu-id="3e6af-109">Her bağlama öğesi <xref:System.ServiceModel.Channels.BindingElement> sınıfından türetilir.</span><span class="sxs-lookup"><span data-stu-id="3e6af-109">Each binding element derives from the <xref:System.ServiceModel.Channels.BindingElement> class.</span></span> <span data-ttu-id="3e6af-110"><xref:System.ServiceModel.BasicHttpBinding>Kendi bağlama öğelerini oluşturma ve yapılandırma gibi sistem tarafından sağlanmış bağlamalar.</span><span class="sxs-lookup"><span data-stu-id="3e6af-110">System-provided bindings such as <xref:System.ServiceModel.BasicHttpBinding> create and configure their own binding elements.</span></span> <span data-ttu-id="3e6af-111">Bu konu başlığı altında, bağlama üzerinde doğrudan gösterilmeyen bu bağlama öğelerinin özelliklerine erişme ve değiştirme işlemlerinin nasıl yapılacağı gösterilmektedir. Özellikle, <xref:System.ServiceModel.BasicHttpBinding> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="3e6af-111">This topic shows you how to access and change the properties of these binding elements, which are not directly exposed on the binding; specifically, the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="3e6af-112">Tek tek bağlama öğeleri, sınıfı tarafından temsil edilen bir koleksiyonda bulunur <xref:System.ServiceModel.Channels.BindingElementCollection> ve şu sıraya eklenir: Işlem akışı, güvenilir oturum, güvenlik, bileşik çift yönlü, tek yönlü, akış güvenliği, Ileti kodlama ve taşıma.</span><span class="sxs-lookup"><span data-stu-id="3e6af-112">The individual binding elements are contained in a collection represented by the <xref:System.ServiceModel.Channels.BindingElementCollection> class and are added in this order: Transaction Flow, Reliable Session, Security, Composite Duplex, One-way, Stream Security, Message Encoding, and Transport.</span></span> <span data-ttu-id="3e6af-113">Her bağlamada listelenen tüm bağlama öğelerinin gerekli olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3e6af-113">Note that not all the binding elements listed are required in every binding.</span></span> <span data-ttu-id="3e6af-114">Kullanıcı tanımlı bağlama öğeleri, bu bağlama öğesi koleksiyonunda de görünebilir ve daha önce açıklanan sırada görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="3e6af-114">User-defined binding elements can also appear in this binding element collection and must appear in the same order as previously described.</span></span> <span data-ttu-id="3e6af-115">Örneğin, Kullanıcı tanımlı bir taşımanın bağlama öğesi koleksiyonunun son öğesi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e6af-115">For example, a user-defined transport must be the last element of the binding element collection.</span></span>  
  
 <span data-ttu-id="3e6af-116"><xref:System.ServiceModel.BasicHttpBinding>Sınıfı üç bağlama öğesi içerir:</span><span class="sxs-lookup"><span data-stu-id="3e6af-116">The <xref:System.ServiceModel.BasicHttpBinding> class contains three binding elements:</span></span>  
  
1. <span data-ttu-id="3e6af-117">Bir isteğe bağlı güvenlik bağlama öğesi, <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> http taşıması (ileti düzeyi güvenliği) veya <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> Aktarım katmanı güvenlik sağlar, bu durumda https aktarımının kullanıldığı durumlarda kullanılan sınıfı.</span><span class="sxs-lookup"><span data-stu-id="3e6af-117">An optional security binding element, either the <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> class used with the HTTP transport (message level security) or the <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> class, which is used when the transport layer provides security, in which case the HTTPS transport is used.</span></span>  
  
2. <span data-ttu-id="3e6af-118">Ya da veya için gerekli bir ileti Kodlayıcısı bağlama öğesi <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="3e6af-118">A required message encoder binding element, either <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> or <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>.</span></span>  
  
3. <span data-ttu-id="3e6af-119">Gerekli bir taşıma bağlama öğesi, ya da <xref:System.ServiceModel.Channels.HttpTransportBindingElement> <xref:System.ServiceModel.Channels.HttpsTransportBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="3e6af-119">A required transport binding element, either <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, or <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>.</span></span>  
  
 <span data-ttu-id="3e6af-120">Bu örnekte, bağlamanın bir örneğini oluşturur, bundan *özel bir bağlama* oluşturur, özel bağlamadaki bağlama öğelerini INCELER ve http bağlama öğesini bulduğumuz, `KeepAliveEnabled` özelliğini olarak ayarlayacağız `false` .</span><span class="sxs-lookup"><span data-stu-id="3e6af-120">In this example we create an instance of the binding, generate a *custom binding* from it, examine the binding elements in the custom binding, and when we find the HTTP binding element, we set its `KeepAliveEnabled` property to `false`.</span></span> <span data-ttu-id="3e6af-121">`KeepAliveEnabled`Özelliği doğrudan üzerinde gösterilmez `BasicHttpBinding` , bu nedenle bağlama öğesine gitmek ve bu özelliği ayarlamak için özel bir bağlama oluşturuyoruz.</span><span class="sxs-lookup"><span data-stu-id="3e6af-121">The `KeepAliveEnabled` property is not exposed directly on the `BasicHttpBinding`, so we must create a custom binding to navigate down to the binding element and set this property.</span></span>  
  
### <a name="to-modify-a-system-provided-binding"></a><span data-ttu-id="3e6af-122">Sistem tarafından sağlanmış bir bağlamayı değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="3e6af-122">To modify a system-provided binding</span></span>  
  
1. <span data-ttu-id="3e6af-123">Sınıfının bir örneğini oluşturun <xref:System.ServiceModel.BasicHttpBinding> ve güvenlik modunu ileti düzeyi olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="3e6af-123">Create an instance of the <xref:System.ServiceModel.BasicHttpBinding> class and set its security mode to message-level.</span></span>  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#1)]
     [!code-vb[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#1)]  
  
2. <span data-ttu-id="3e6af-124">Bağlamadan özel bir bağlama oluşturun ve <xref:System.ServiceModel.Channels.BindingElementCollection> özel bağlamanın özelliklerinden birinden bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3e6af-124">Create a custom binding from the binding and create a <xref:System.ServiceModel.Channels.BindingElementCollection> class from one of the custom binding's properties.</span></span>  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#2)]
     [!code-vb[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#2)]  
  
3. <span data-ttu-id="3e6af-125"><xref:System.ServiceModel.Channels.BindingElementCollection>Sınıfından döngü yapın ve <xref:System.ServiceModel.Channels.HttpTransportBindingElement> sınıfını bulduğunuzda <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> özelliğini olarak ayarlayın `false` .</span><span class="sxs-lookup"><span data-stu-id="3e6af-125">Loop through the <xref:System.ServiceModel.Channels.BindingElementCollection> class, and when you find the <xref:System.ServiceModel.Channels.HttpTransportBindingElement> class, set its <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> property to `false`.</span></span>  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#3)]
     [!code-vb[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="3e6af-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e6af-126">See also</span></span>

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="3e6af-127">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="3e6af-127">Custom Bindings</span></span>](custom-bindings.md)
