---
title: "ServiceHost Hizmet Modeli Katmanını Genişletme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: extending service models [WCF]
ms.assetid: 954c138a-1cd0-45a0-8abe-e4d2b8ff5400
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 67ed4be3211af141af87da2406e81ff5e2fbb767
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="extending-servicehost-and-the-service-model-layer"></a><span data-ttu-id="61020-102">ServiceHost Hizmet Modeli Katmanını Genişletme</span><span class="sxs-lookup"><span data-stu-id="61020-102">Extending ServiceHost and the Service Model Layer</span></span>
<span data-ttu-id="61020-103">Temel alınan kanalları dışında gelen iletileri çekme, bunları yöntem çağrılarına uygulama kodundaki içine çevirme ve sonuçları çağırana geri göndermek için hizmet modeli katmanını sorumludur.</span><span class="sxs-lookup"><span data-stu-id="61020-103">The service model layer is responsible for pulling incoming messages out of the underlying channels, translating them into method invocations in application code, and sending the results back to the caller.</span></span> <span data-ttu-id="61020-104">Hizmet modeli uzantıları değiştirebilir veya yürütme veya iletişim davranışı ve istemci veya dağıtıcısı işlevi, özel davranışları, ileti ve parametre kişiler tarafından ele ve diğer genişletilebilirlik işlevleri içeren özellikler uygular.</span><span class="sxs-lookup"><span data-stu-id="61020-104">Service model extensions modify or implement execution or communication behavior and features involving client or dispatcher functionality, custom behaviors, message and parameter interception, and other extensibility functionality.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="61020-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="61020-105">In This Section</span></span>  
 [<span data-ttu-id="61020-106">İstemcileri genişletme</span><span class="sxs-lookup"><span data-stu-id="61020-106">Extending Clients</span></span>](../../../../docs/framework/wcf/extending/extending-clients.md)  
 <span data-ttu-id="61020-107">Kesebilen ve istemci çalışma zamanı olarak özel uzantılarınızın istemci uygulamalarında ekleyebilirsiniz sınıfları değiştirme arabirimler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="61020-107">Describes the interfaces that can intercept and modify the client runtime, as well as the classes into which you can insert your custom extensions in client applications.</span></span> <span data-ttu-id="61020-108">Örneğin, özel istemci ileti günlüğe kaydetme gerçekleştirmek, özel ileti serileştirme gerçekleştirmek ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="61020-108">For example, you can perform custom client message logging, perform custom message serialization, and so on.</span></span>  
  
 [<span data-ttu-id="61020-109">Dağıtıcıları genişletme</span><span class="sxs-lookup"><span data-stu-id="61020-109">Extending Dispatchers</span></span>](../../../../docs/framework/wcf/extending/extending-dispatchers.md)  
 <span data-ttu-id="61020-110">Kesebilen ve hizmet çalışma zamanı olarak özel uzantılarınızın hizmet uygulamalarını ekleyebilirsiniz sınıfları değiştirme arabirimler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="61020-110">Describes the interfaces that can intercept and modify the service runtime, as well as the classes into which you can insert your custom extensions in service applications.</span></span> <span data-ttu-id="61020-111">Örneğin, özel hizmet günlüğü, hizmet tarafı ileti doğrulama, özel göndermeyi ve benzeri gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="61020-111">For example, you can perform custom service logging, service-side message validation, custom dispatching, and so on.</span></span>  
  
 [<span data-ttu-id="61020-112">Genişletilebilen nesneler</span><span class="sxs-lookup"><span data-stu-id="61020-112">Extensible Objects</span></span>](../../../../docs/framework/wcf/extending/extensible-objects.md)  
 <span data-ttu-id="61020-113">Beş genişletilebilen nesneler açıklar ve <xref:System.ServiceModel.IExtensibleObject%601> düzeni.</span><span class="sxs-lookup"><span data-stu-id="61020-113">Describes the five extensible objects and the <xref:System.ServiceModel.IExtensibleObject%601> pattern.</span></span> <span data-ttu-id="61020-114">Genişletilebilir object deseni ya da varolan çalışma zamanı sınıflarını yeni işlevselliği ile genişletmek veya bir nesne için yeni durum eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="61020-114">The extensible object pattern is used to either extend existing runtime classes with new functionality or to add new state to an object.</span></span> <span data-ttu-id="61020-115">Genişletilebilen nesneler birine ekli uzantılar, paylaşılan durum ve bunlar erişebileceği bir ortak Genişletilebilir nesneye iliştirilmiş işlevlerine erişimini işleme çok farklı aşamalarında davranışları etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="61020-115">Extensions, attached to one of the extensible objects, enable behaviors at very different stages in processing to access shared state and functionality attached to a common extensible object that they can access.</span></span>  
  
 [<span data-ttu-id="61020-116">Yapılandırma ve çalışma zamanını davranışlarla genişletme</span><span class="sxs-lookup"><span data-stu-id="61020-116">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)  
 <span data-ttu-id="61020-117">Ayarları değiştirmek veya uzantıları eklemeyi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] çalışma zamanı, davranışları kullanın.</span><span class="sxs-lookup"><span data-stu-id="61020-117">To change settings on or insert extensions in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] runtime, you use Behaviors.</span></span> <span data-ttu-id="61020-118">WCF sistem uygulanan davranış azaltma, depolamasına ve birçok diğer yönlerini Hizmetleri ve işlemleri denetleme içerir.</span><span class="sxs-lookup"><span data-stu-id="61020-118">WCF includes system-implemented behaviors for controlling throttling, instancing, and many other aspects of services and operations.</span></span> <span data-ttu-id="61020-119">Bu bölümde, kendi özel davranışları ve bunları her iki program aracılığıyla kullanımına nasıl ve yapılandırma dosyaları kullanılarak nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="61020-119">This section describes how to create your own custom behaviors and how to make them available for use both programmatically and using configuration files.</span></span>  
  
 [<span data-ttu-id="61020-120">ServiceHostFactory kullanarak barındırmayı genişletme</span><span class="sxs-lookup"><span data-stu-id="61020-120">Extending Hosting Using ServiceHostFactory</span></span>](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)  
 <span data-ttu-id="61020-121">Nasıl genişletileceğini açıklar <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType>, <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>ve <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> ana bilgisayar ortamının özelleştirmek için sınıflar.</span><span class="sxs-lookup"><span data-stu-id="61020-121">Describes how to extend <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType>, <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>, and use the <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> classes to customize the host environment.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="61020-122">Başvuru</span><span class="sxs-lookup"><span data-stu-id="61020-122">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="61020-123">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="61020-123">Related Sections</span></span>
