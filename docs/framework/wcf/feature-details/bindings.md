---
title: "Windows Communication Foundation Bağlamaları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF [WCF], bindings
- Windows Communication Foundation [WCF], bindings
- bindings [WCF]
ms.assetid: 83639133-89f7-43f0-b4ef-8d9e57c08d25
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 977bc032d62856673994e07a71b77d3b668ce7af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="windows-communcation-foundation-bindings"></a><span data-ttu-id="91b6f-102">Windows Communication Foundation Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="91b6f-102">Windows Communcation Foundation Bindings</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="91b6f-103">bir uygulama için yazılım nasıl onu diğer yazılımlarla iletişim kurduğu gelen nasıl yazılmış ayırır.</span><span class="sxs-lookup"><span data-stu-id="91b6f-103"> separates how the software for an application is written from how it communicates with other software.</span></span> <span data-ttu-id="91b6f-104">Bağlamaları Aktarım, kodlama ve istemcileri ve Hizmetleri birbirleri ile iletişim kurması gereken protokol ayrıntılarını belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="91b6f-104">Bindings are used to specify the transport, encoding, and protocol details required for clients and services to communicate with each other.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="91b6f-105">temel alınan hat gösterimine uç noktanın bağlama ayrıntıları çoğunu iletişim kuran tarafların üzerinde anlaşmaya varılan gerekir böylece oluşturmak için bağlamaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="91b6f-105"> uses bindings to generate the underlying wire representation of the endpoint, so most of the binding details must be agreed upon by the parties that are communicating.</span></span> <span data-ttu-id="91b6f-106">Bunu elde etmenin en kolay yolu, bir hizmet bağlaması aynı hizmet kullandığı için uç nokta kullanmak istemcileri içindir.</span><span class="sxs-lookup"><span data-stu-id="91b6f-106">The easiest way to achieve this is for clients of a service to use the same binding that the endpoint for the service uses.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="91b6f-107">Bunu yapmak için bkz: nasıl [kullanarak bağlamaları yapılandırma Windows Communication Foundation Hizmetleri ve istemcilere](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb).</span><span class="sxs-lookup"><span data-stu-id="91b6f-107"> how to do this, see [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb).</span></span>  
  
 <span data-ttu-id="91b6f-108">Bir bağlama bağlama öğelerinin koleksiyonu yapılır.</span><span class="sxs-lookup"><span data-stu-id="91b6f-108">A binding is made up of a collection of binding elements.</span></span> <span data-ttu-id="91b6f-109">Her uç nokta istemcileri ile nasıl iletişim kurduğu, bazı yönlerinin açıklar.</span><span class="sxs-lookup"><span data-stu-id="91b6f-109">Each element describes some aspect of how the endpoint communicates with clients.</span></span> <span data-ttu-id="91b6f-110">Bir bağlama en az bir aktarım bağlama öğesi, (sağlayabilen aktarım bağlama öğesi varsayılan olarak) en az bir ileti kodlama bağlama öğesi içermelidir ve diğer herhangi bir sayıda Protokolü bağlama öğeleri.</span><span class="sxs-lookup"><span data-stu-id="91b6f-110">A binding must include at least one transport binding element, at least one message-encoding binding element (which the transport binding element can provide by default), and any number of other protocol binding elements.</span></span> <span data-ttu-id="91b6f-111">Bu açıklama dışında bir çalışma zamanı derlemeleri işlem kodu, çalışma zamanının katkıda bulunmak her bağlama öğesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="91b6f-111">The process that builds a runtime out of this description allows each binding element to contribute code to that runtime.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="91b6f-112">bağlama öğelerinin ortak seçimleri içeren bağlamaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="91b6f-112"> provides bindings that contain common selections of binding elements.</span></span> <span data-ttu-id="91b6f-113">Bu varsayılan ayarlarla kullanılabilir veya kullanıcı gereksinimlerine göre bu varsayılan değerleri değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91b6f-113">These can be used with their default settings or you can modify those default values according to user requirements.</span></span> <span data-ttu-id="91b6f-114">Bu sistem tarafından sağlanan bağlamalar bağlama öğelerini ve ayarlarını doğrudan denetime izin veren özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="91b6f-114">These system-provided bindings have properties that allow direct control over the binding elements and their settings.</span></span> <span data-ttu-id="91b6f-115">Bağlama her sürümü vererek yana birimi bağlaması birden çok sürümü ile de kolayca çalışabilirsiniz kendi adı.</span><span class="sxs-lookup"><span data-stu-id="91b6f-115">You can also easily work side-by-side with multiple versions of a binding by giving each version of the binding its own name.</span></span> <span data-ttu-id="91b6f-116">Ayrıntılar için bkz [Configuring System-Provided bağlamaları](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="91b6f-116">For details, see [Configuring System-Provided Bindings](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md).</span></span>  
  
 <span data-ttu-id="91b6f-117">Bir koleksiyonu gerekiyorsa bağlama öğeleri sağlanmamış bu sistem tarafından sağlanan bağlamalar biri tarafından bağlama gerekli öğelerinin koleksiyonunu içeren özel bir bağlama oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91b6f-117">If you need a collection of binding elements not provided by one of these system-provided bindings, you can create a custom binding that consists of the collection of binding elements required.</span></span> <span data-ttu-id="91b6f-118">Bu özel bağlama oluşturma yapmak kolaydır ve yeni bir sınıf gerekmez, ancak özellikleri bağlama öğeleri veya ayarlarını denetlemek için sağladıkları değil.</span><span class="sxs-lookup"><span data-stu-id="91b6f-118">These custom bindings are easy to create and do not require a new class, but they do not provide properties for controlling the binding elements or their settings.</span></span> <span data-ttu-id="91b6f-119">Bağlama öğeleri erişmek ve onları içeren koleksiyonu aracılığıyla ayarlarını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="91b6f-119">You can access the binding elements and modify their settings through the collection that contains them.</span></span> <span data-ttu-id="91b6f-120">Ayrıntılar için bkz [özel bağlamaları](../../../../docs/framework/wcf/extending/custom-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="91b6f-120">For details, see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="91b6f-121">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="91b6f-121">In This Section</span></span>  
 [<span data-ttu-id="91b6f-122">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="91b6f-122">Configuring System-Provided Bindings</span></span>](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 <span data-ttu-id="91b6f-123">Kullanın ve bağlamaları değiştirmek açıklar, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] senaryoları desteklemek için sağlar.</span><span class="sxs-lookup"><span data-stu-id="91b6f-123">Describes how to use and modify the bindings that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides to support common scenarios.</span></span>  
  
 [<span data-ttu-id="91b6f-124">Windows Communication Foundation Hizmetleri ve istemcileri yapılandırmak için bağlamaları kullanma</span><span class="sxs-lookup"><span data-stu-id="91b6f-124">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 <span data-ttu-id="91b6f-125">Nasıl tanımlanacağını açıklar [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmetler ve istemcileri imperatively kodu ve bildirimli olarak Yapılandırması'nı kullanarak bağlamaları.</span><span class="sxs-lookup"><span data-stu-id="91b6f-125">Describes how to define [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] bindings for services and clients imperatively in code and declaratively using configuration.</span></span>  
  
 [<span data-ttu-id="91b6f-126">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="91b6f-126">Custom Bindings</span></span>](../../../../docs/framework/wcf/extending/custom-bindings.md)  
 <span data-ttu-id="91b6f-127">Ne açıklayan bir <xref:System.ServiceModel.Channels.CustomBinding> olduğu ve ne zaman kullanılır.</span><span class="sxs-lookup"><span data-stu-id="91b6f-127">Describes what a <xref:System.ServiceModel.Channels.CustomBinding> is and when it is used.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="91b6f-128">Başvuru</span><span class="sxs-lookup"><span data-stu-id="91b6f-128">Reference</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
  
 <xref:System.ServiceModel.Channels.BindingElement>  
  
 <xref:System.ServiceModel.Channels.CustomBinding>  
  
## <a name="related-sections"></a><span data-ttu-id="91b6f-129">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="91b6f-129">Related Sections</span></span>  
 [<span data-ttu-id="91b6f-130">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="91b6f-130">Extending Bindings</span></span>](../../../../docs/framework/wcf/extending/extending-bindings.md)
