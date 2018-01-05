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
ms.workload: dotnet
ms.openlocfilehash: 5c73af3b9187fa5365d7ea99474ea182d5f5ae86
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="extending-servicehost-and-the-service-model-layer"></a><span data-ttu-id="69317-102">ServiceHost Hizmet Modeli Katmanını Genişletme</span><span class="sxs-lookup"><span data-stu-id="69317-102">Extending ServiceHost and the Service Model Layer</span></span>
<span data-ttu-id="69317-103">Temel alınan kanalları dışında gelen iletileri çekme, bunları yöntem çağrılarına uygulama kodundaki içine çevirme ve sonuçları çağırana geri göndermek için hizmet modeli katmanını sorumludur.</span><span class="sxs-lookup"><span data-stu-id="69317-103">The service model layer is responsible for pulling incoming messages out of the underlying channels, translating them into method invocations in application code, and sending the results back to the caller.</span></span> <span data-ttu-id="69317-104">Hizmet modeli uzantıları değiştirebilir veya yürütme veya iletişim davranışı ve istemci veya dağıtıcısı işlevi, özel davranışları, ileti ve parametre kişiler tarafından ele ve diğer genişletilebilirlik işlevleri içeren özellikler uygular.</span><span class="sxs-lookup"><span data-stu-id="69317-104">Service model extensions modify or implement execution or communication behavior and features involving client or dispatcher functionality, custom behaviors, message and parameter interception, and other extensibility functionality.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="69317-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="69317-105">In This Section</span></span>  
 [<span data-ttu-id="69317-106">İstemcileri Genişletme</span><span class="sxs-lookup"><span data-stu-id="69317-106">Extending Clients</span></span>](../../../../docs/framework/wcf/extending/extending-clients.md)  
 <span data-ttu-id="69317-107">Kesebilen ve istemci çalışma zamanı olarak özel uzantılarınızın istemci uygulamalarında ekleyebilirsiniz sınıfları değiştirme arabirimler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="69317-107">Describes the interfaces that can intercept and modify the client runtime, as well as the classes into which you can insert your custom extensions in client applications.</span></span> <span data-ttu-id="69317-108">Örneğin, özel istemci ileti günlüğe kaydetme gerçekleştirmek, özel ileti serileştirme gerçekleştirmek ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="69317-108">For example, you can perform custom client message logging, perform custom message serialization, and so on.</span></span>  
  
 [<span data-ttu-id="69317-109">Dağıtıcıları Genişletme</span><span class="sxs-lookup"><span data-stu-id="69317-109">Extending Dispatchers</span></span>](../../../../docs/framework/wcf/extending/extending-dispatchers.md)  
 <span data-ttu-id="69317-110">Kesebilen ve hizmet çalışma zamanı olarak özel uzantılarınızın hizmet uygulamalarını ekleyebilirsiniz sınıfları değiştirme arabirimler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="69317-110">Describes the interfaces that can intercept and modify the service runtime, as well as the classes into which you can insert your custom extensions in service applications.</span></span> <span data-ttu-id="69317-111">Örneğin, özel hizmet günlüğü, hizmet tarafı ileti doğrulama, özel göndermeyi ve benzeri gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="69317-111">For example, you can perform custom service logging, service-side message validation, custom dispatching, and so on.</span></span>  
  
 [<span data-ttu-id="69317-112">Genişletilebilen Nesneler</span><span class="sxs-lookup"><span data-stu-id="69317-112">Extensible Objects</span></span>](../../../../docs/framework/wcf/extending/extensible-objects.md)  
 <span data-ttu-id="69317-113">Beş genişletilebilen nesneler açıklar ve <xref:System.ServiceModel.IExtensibleObject%601> düzeni.</span><span class="sxs-lookup"><span data-stu-id="69317-113">Describes the five extensible objects and the <xref:System.ServiceModel.IExtensibleObject%601> pattern.</span></span> <span data-ttu-id="69317-114">Genişletilebilir object deseni ya da varolan çalışma zamanı sınıflarını yeni işlevselliği ile genişletmek veya bir nesne için yeni durum eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="69317-114">The extensible object pattern is used to either extend existing runtime classes with new functionality or to add new state to an object.</span></span> <span data-ttu-id="69317-115">Genişletilebilen nesneler birine ekli uzantılar, paylaşılan durum ve bunlar erişebileceği bir ortak Genişletilebilir nesneye iliştirilmiş işlevlerine erişimini işleme çok farklı aşamalarında davranışları etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="69317-115">Extensions, attached to one of the extensible objects, enable behaviors at very different stages in processing to access shared state and functionality attached to a common extensible object that they can access.</span></span>  
  
 [<span data-ttu-id="69317-116">Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme</span><span class="sxs-lookup"><span data-stu-id="69317-116">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)  
 <span data-ttu-id="69317-117">Ayarları değiştirmek veya uzantıları eklemeyi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] çalışma zamanı, davranışları kullanın.</span><span class="sxs-lookup"><span data-stu-id="69317-117">To change settings on or insert extensions in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] runtime, you use Behaviors.</span></span> <span data-ttu-id="69317-118">WCF sistem uygulanan davranış azaltma, depolamasına ve birçok diğer yönlerini Hizmetleri ve işlemleri denetleme içerir.</span><span class="sxs-lookup"><span data-stu-id="69317-118">WCF includes system-implemented behaviors for controlling throttling, instancing, and many other aspects of services and operations.</span></span> <span data-ttu-id="69317-119">Bu bölümde, kendi özel davranışları ve bunları her iki program aracılığıyla kullanımına nasıl ve yapılandırma dosyaları kullanılarak nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="69317-119">This section describes how to create your own custom behaviors and how to make them available for use both programmatically and using configuration files.</span></span>  
  
 [<span data-ttu-id="69317-120">ServiceHostFactory Kullanarak Barındırmayı Genişletme</span><span class="sxs-lookup"><span data-stu-id="69317-120">Extending Hosting Using ServiceHostFactory</span></span>](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)  
 <span data-ttu-id="69317-121">Nasıl genişletileceğini açıklar <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType>, <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>ve <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> ana bilgisayar ortamının özelleştirmek için sınıflar.</span><span class="sxs-lookup"><span data-stu-id="69317-121">Describes how to extend <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType>, <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>, and use the <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> classes to customize the host environment.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="69317-122">Başvuru</span><span class="sxs-lookup"><span data-stu-id="69317-122">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="69317-123">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="69317-123">Related Sections</span></span>
