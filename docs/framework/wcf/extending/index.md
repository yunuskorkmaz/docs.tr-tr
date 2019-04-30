---
title: WCF'yi Genişletme
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, extensibility
- extensibility [WCF]
- Windows Communication Foundation, extensibility
ms.assetid: c145e2f6-f402-41f5-8b5a-eee03978737b
ms.openlocfilehash: 24ad74f04a3ac31d0b0d0d87f0d74f88c0521f50
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768725"
---
# <a name="extending-wcf"></a><span data-ttu-id="01538-102">WCF'yi Genişletme</span><span class="sxs-lookup"><span data-stu-id="01538-102">Extending WCF</span></span>
<span data-ttu-id="01538-103">Windows Communication Foundation (WCF) değiştirmek, tam olarak denetlemek için çalışma zamanı bileşenleri'ni genişletin ve hizmet tabanlı uygulamaları genişletmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="01538-103">Windows Communication Foundation (WCF) allows you to modify and extend run time components to precisely control and extend service-based applications.</span></span> <span data-ttu-id="01538-104">Bu bölümdeki konular, derinlemesine genişletilebilirlik mimarisi hakkında gidin.</span><span class="sxs-lookup"><span data-stu-id="01538-104">The topics in this section go in depth about the extensibility architecture.</span></span> <span data-ttu-id="01538-105">Temel programlama hakkında daha fazla bilgi için bkz. [temel WCF programlama](../../../../docs/framework/wcf/basic-wcf-programming.md).</span><span class="sxs-lookup"><span data-stu-id="01538-105">For more information about basic programming, see [Basic WCF Programming](../../../../docs/framework/wcf/basic-wcf-programming.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="01538-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="01538-106">In This Section</span></span>  
 [<span data-ttu-id="01538-107">ServiceHost ve Hizmet Modeli Katmanını Genişletme</span><span class="sxs-lookup"><span data-stu-id="01538-107">Extending ServiceHost and the Service Model Layer</span></span>](../../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md)  
 <span data-ttu-id="01538-108">Hizmet modeli katmanını çağırana geri göndererek arka plandaki kanal gelen iletileri çekerek ve bunları yöntem çağrıları uygulama kodunda içine çevirme sorumludur.</span><span class="sxs-lookup"><span data-stu-id="01538-108">The service model layer is responsible for pulling incoming messages out of the underlying channels, translating them into method invocations in application code, and sending the results back to the caller.</span></span>  <span data-ttu-id="01538-109">Hizmet modeli uzantıları değiştirebilir veya yürütme veya iletişim davranışı ve dağıtıcı işlevi, özel davranışlar, ileti ve parametre durdurma ve diğer genişletilebilirlik işlevlerini içeren özellikler uygular.</span><span class="sxs-lookup"><span data-stu-id="01538-109">Service model extensions modify or implement execution or communication behavior and features involving dispatcher functionality, custom behaviors, message and parameter interception, and other extensibility functionality.</span></span>  
  
 [<span data-ttu-id="01538-110">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="01538-110">Extending Bindings</span></span>](../../../../docs/framework/wcf/extending/extending-bindings.md)  
 <span data-ttu-id="01538-111">Bağlamaları bir uç noktaya bağlanmak için gereken iletişim ayrıntılarını açıklayan nesneleridir.</span><span class="sxs-lookup"><span data-stu-id="01538-111">Bindings are objects that describe the communication details required to connect to an endpoint.</span></span> <span data-ttu-id="01538-112">Bağlama uzantıları veya özel bağlamalar uygulama özellikleri desteklemek için gereken özel iletişim işlevselliğini uygular.</span><span class="sxs-lookup"><span data-stu-id="01538-112">Binding extensions or custom bindings implement custom communication functionality required to support application features.</span></span>  
  
 [<span data-ttu-id="01538-113">Kanal Katmanını Genişletme</span><span class="sxs-lookup"><span data-stu-id="01538-113">Extending the Channel Layer</span></span>](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md)  
 <span data-ttu-id="01538-114">Kanal katmanını hizmet modeli katmanını altında yer alan ve istemciler ve hizmetler arasında ileti alışverişi sorumludur.</span><span class="sxs-lookup"><span data-stu-id="01538-114">The channel layer sits beneath the service model layer and is responsible for the exchange of messages between clients and services.</span></span> <span data-ttu-id="01538-115">Kanal uzantıları güvenlik gibi yeni Protokolü işlevi uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01538-115">Channel extensions can implement new protocol functionality, such as security.</span></span> <span data-ttu-id="01538-116">Kanal uzantıları SOAP iletilerini gerçekleştirmek için yeni bir ağ aktarımı uygulama gibi işlevler de taşıma.</span><span class="sxs-lookup"><span data-stu-id="01538-116">Channel extensions also transport functionality, such as implementing a new network transport to carry SOAP messages.</span></span>  
  
 [<span data-ttu-id="01538-117">Güvenliği Genişletme</span><span class="sxs-lookup"><span data-stu-id="01538-117">Extending Security</span></span>](../../../../docs/framework/wcf/extending/extending-security.md)  
 <span data-ttu-id="01538-118">Wcf'de güvenlik aktarımını oluşur (bütünlüğü, gizlilik ve kimlik doğrulaması) güvenlik erişim denetimi (yetkilendirme) ve denetimi.</span><span class="sxs-lookup"><span data-stu-id="01538-118">Security in WCF consists of transfer security (integrity, confidentiality, and authentication), access control (authorization) and auditing.</span></span> <span data-ttu-id="01538-119">Bulunan sınıflar `IdentityModel` ad alanı, erişim denetimi için WCF tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="01538-119">The classes found in the `IdentityModel` namespace are used by WCF for access control.</span></span> <span data-ttu-id="01538-120">Güvenlik mimarisini anlama, özel erişim denetimi sistemlerine uyum sağlamak için özel talep türleri oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="01538-120">Understanding the security architecture allows you to create custom claim types to accommodate custom access control systems.</span></span>  
  
 [<span data-ttu-id="01538-121">Meta Veri Sistemini Genişletme</span><span class="sxs-lookup"><span data-stu-id="01538-121">Extending the Metadata System</span></span>](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)  
 <span data-ttu-id="01538-122">WCF Meta veri sistemini sınıfları ve arabirimleri hizmet tabanlı uygulamaları uygulamak için gereken meta verileri temsil eden bir grubudur.</span><span class="sxs-lookup"><span data-stu-id="01538-122">The WCF metadata system is a group of classes and interfaces that represent metadata required to implement service-based applications.</span></span> <span data-ttu-id="01538-123">Değiştirin veya sınıflarını genişletmek veya uygulama ve Web Hizmetleri Açıklama Dili (WSDL) uzantıları veya özel bir WS-PolicyAttachments onaylar gibi özel meta verileri içeri ve dışarı aktarmak arabirimler yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="01538-123">Modify or extend the classes or implement and configure the interfaces to export and import custom metadata such as Web Services Description Language (WSDL) extensions or custom WS-PolicyAttachments assertions.</span></span>  
  
 [<span data-ttu-id="01538-124">Kodlayıcılar ve Seri Hale Getiricileri Genişletme</span><span class="sxs-lookup"><span data-stu-id="01538-124">Extending Encoders and Serializers</span></span>](../../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md)  
 <span data-ttu-id="01538-125">Kodlayıcılar ve seri hale getiricileri genişletme verileri bir biçimden diğerine çevir.</span><span class="sxs-lookup"><span data-stu-id="01538-125">Encoders and serializers translate data from one form to another.</span></span> <span data-ttu-id="01538-126">Bu bölümdeki konular, özel gereksinimleri karşılamak için sağlanan sınıflarını genişletmek nasıl ele almaktadır.</span><span class="sxs-lookup"><span data-stu-id="01538-126">The topics in this section discuss how to extend the supplied classes to meet special requirements.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="01538-127">Başvuru</span><span class="sxs-lookup"><span data-stu-id="01538-127">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Tokens>  
  
## <a name="related-sections"></a><span data-ttu-id="01538-128">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="01538-128">Related Sections</span></span>  
 [<span data-ttu-id="01538-129">Temel WCF Programlama</span><span class="sxs-lookup"><span data-stu-id="01538-129">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
 [<span data-ttu-id="01538-130">WCF Özellik Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="01538-130">WCF Feature Details</span></span>](../../../../docs/framework/wcf/feature-details/index.md)  
  
 [<span data-ttu-id="01538-131">Yönergeler ve En İyi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="01538-131">Guidelines and Best Practices</span></span>](../../../../docs/framework/wcf/guidelines-and-best-practices.md)
