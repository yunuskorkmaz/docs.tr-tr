---
title: WCF'yi Genişletme
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, extensibility
- extensibility [WCF]
- Windows Communication Foundation, extensibility
ms.assetid: c145e2f6-f402-41f5-8b5a-eee03978737b
ms.openlocfilehash: b82dd4fb6a5b41a0160df8680fb1ba65d9a5bd33
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96254603"
---
# <a name="extending-wcf"></a><span data-ttu-id="0b715-102">WCF'yi Genişletme</span><span class="sxs-lookup"><span data-stu-id="0b715-102">Extending WCF</span></span>

<span data-ttu-id="0b715-103">Windows Communication Foundation (WCF), hizmet tabanlı uygulamaları tam olarak denetlemek ve genişletmek için çalışma zamanı bileşenlerini değiştirmenize ve genişletmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="0b715-103">Windows Communication Foundation (WCF) allows you to modify and extend run time components to precisely control and extend service-based applications.</span></span> <span data-ttu-id="0b715-104">Bu bölümdeki konular, genişletilebilirlik mimarisi hakkında ayrıntılı bilgi ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="0b715-104">The topics in this section go in depth about the extensibility architecture.</span></span> <span data-ttu-id="0b715-105">Temel programlama hakkında daha fazla bilgi için bkz. [Temel WCF programlama](../basic-wcf-programming.md).</span><span class="sxs-lookup"><span data-stu-id="0b715-105">For more information about basic programming, see [Basic WCF Programming](../basic-wcf-programming.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0b715-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="0b715-106">In This Section</span></span>  

 [<span data-ttu-id="0b715-107">ServiceHost Hizmet Modeli Katmanını Genişletme</span><span class="sxs-lookup"><span data-stu-id="0b715-107">Extending ServiceHost and the Service Model Layer</span></span>](extending-servicehost-and-the-service-model-layer.md)  
 <span data-ttu-id="0b715-108">Hizmet modeli katmanı, temel alınan kanallara ait gelen iletileri çekmekten, bunları uygulama kodundaki Yöntem etkinleştirmeleri içine çevirerek ve sonuçları çağırana geri göndererek sorumludur.</span><span class="sxs-lookup"><span data-stu-id="0b715-108">The service model layer is responsible for pulling incoming messages out of the underlying channels, translating them into method invocations in application code, and sending the results back to the caller.</span></span>  <span data-ttu-id="0b715-109">Hizmet modeli uzantıları; dağıtıcı işlevselliği, özel davranışlar, ileti ve parametre yakaalımı ve diğer genişletilebilirlik işlevleri ile ilgili yürütme veya iletişim davranışlarını ve özellikleri değiştirir veya uygular.</span><span class="sxs-lookup"><span data-stu-id="0b715-109">Service model extensions modify or implement execution or communication behavior and features involving dispatcher functionality, custom behaviors, message and parameter interception, and other extensibility functionality.</span></span>  
  
 [<span data-ttu-id="0b715-110">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="0b715-110">Extending Bindings</span></span>](extending-bindings.md)  
 <span data-ttu-id="0b715-111">Bağlamalar, bir uç noktaya bağlanmak için gereken iletişim ayrıntılarını tanımlayan nesnelerdir.</span><span class="sxs-lookup"><span data-stu-id="0b715-111">Bindings are objects that describe the communication details required to connect to an endpoint.</span></span> <span data-ttu-id="0b715-112">Bağlama uzantıları veya özel bağlamalar, uygulama özelliklerini desteklemek için gereken özel iletişim işlevlerini uygular.</span><span class="sxs-lookup"><span data-stu-id="0b715-112">Binding extensions or custom bindings implement custom communication functionality required to support application features.</span></span>  
  
 [<span data-ttu-id="0b715-113">Kanal Katmanını Genişletme</span><span class="sxs-lookup"><span data-stu-id="0b715-113">Extending the Channel Layer</span></span>](extending-the-channel-layer.md)  
 <span data-ttu-id="0b715-114">Kanal katmanı, hizmet modeli katmanının altında bulunur ve istemciler ve hizmetler arasındaki ileti alışverişinin sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="0b715-114">The channel layer sits beneath the service model layer and is responsible for the exchange of messages between clients and services.</span></span> <span data-ttu-id="0b715-115">Kanal uzantıları, güvenlik gibi yeni protokol işlevleri uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="0b715-115">Channel extensions can implement new protocol functionality, such as security.</span></span> <span data-ttu-id="0b715-116">Kanal uzantıları Ayrıca, SOAP iletilerini taşımak için yeni bir ağ taşıması uygulama gibi aktarım işlevlerini de sağlar.</span><span class="sxs-lookup"><span data-stu-id="0b715-116">Channel extensions also transport functionality, such as implementing a new network transport to carry SOAP messages.</span></span>  
  
 [<span data-ttu-id="0b715-117">Güvenliği Genişletme</span><span class="sxs-lookup"><span data-stu-id="0b715-117">Extending Security</span></span>](extending-security.md)  
 <span data-ttu-id="0b715-118">WCF 'de güvenlik, aktarım güvenliği (bütünlük, gizlilik ve kimlik doğrulaması), erişim denetimi (yetkilendirme) ve denetim bilgisinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="0b715-118">Security in WCF consists of transfer security (integrity, confidentiality, and authentication), access control (authorization) and auditing.</span></span> <span data-ttu-id="0b715-119">Ad alanında bulunan sınıflar, `IdentityModel` erişim denetimi IÇIN WCF tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0b715-119">The classes found in the `IdentityModel` namespace are used by WCF for access control.</span></span> <span data-ttu-id="0b715-120">Güvenlik mimarisini anlamak, özel erişim denetimi sistemlerine uyum sağlamak için özel talep türleri oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="0b715-120">Understanding the security architecture allows you to create custom claim types to accommodate custom access control systems.</span></span>  
  
 [<span data-ttu-id="0b715-121">Meta Veri Sistemini Genişletme</span><span class="sxs-lookup"><span data-stu-id="0b715-121">Extending the Metadata System</span></span>](extending-the-metadata-system.md)  
 <span data-ttu-id="0b715-122">WCF meta veri sistemi, hizmet tabanlı uygulamaları uygulamak için gereken meta verileri temsil eden bir sınıf ve arabirim grubudur.</span><span class="sxs-lookup"><span data-stu-id="0b715-122">The WCF metadata system is a group of classes and interfaces that represent metadata required to implement service-based applications.</span></span> <span data-ttu-id="0b715-123">Sınıfları değiştirin veya genişletin ya da Web Hizmetleri Açıklama Dili (WSDL) uzantıları veya özel WS-PolicyAttachments onayları gibi özel meta verileri dışarı ve içeri aktarmak için arabirimleri uygulayın ve yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="0b715-123">Modify or extend the classes or implement and configure the interfaces to export and import custom metadata such as Web Services Description Language (WSDL) extensions or custom WS-PolicyAttachments assertions.</span></span>  
  
 [<span data-ttu-id="0b715-124">Kodlayıcılar ve Seri Hale Getiricileri Genişletme</span><span class="sxs-lookup"><span data-stu-id="0b715-124">Extending Encoders and Serializers</span></span>](extending-encoders-and-serializers.md)  
 <span data-ttu-id="0b715-125">Kodlayıcılar ve serileştiriciler verileri bir formdan diğerine çevirir.</span><span class="sxs-lookup"><span data-stu-id="0b715-125">Encoders and serializers translate data from one form to another.</span></span> <span data-ttu-id="0b715-126">Bu bölümdeki konularda, özel gereksinimleri karşılamak için sağlanan sınıfların nasıl genişletileceği ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0b715-126">The topics in this section discuss how to extend the supplied classes to meet special requirements.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="0b715-127">Başvuru</span><span class="sxs-lookup"><span data-stu-id="0b715-127">Reference</span></span>  

 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Tokens>  
  
## <a name="related-sections"></a><span data-ttu-id="0b715-128">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="0b715-128">Related Sections</span></span>  

 [<span data-ttu-id="0b715-129">Temel WCF Programlama</span><span class="sxs-lookup"><span data-stu-id="0b715-129">Basic WCF Programming</span></span>](../basic-wcf-programming.md)  
  
 [<span data-ttu-id="0b715-130">WCF özellik ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="0b715-130">WCF Feature Details</span></span>](../feature-details/index.md)  
  
 [<span data-ttu-id="0b715-131">Yönergeler ve En İyi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0b715-131">Guidelines and Best Practices</span></span>](../guidelines-and-best-practices.md)
