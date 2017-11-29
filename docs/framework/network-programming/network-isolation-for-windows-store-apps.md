---
title: "Windows mağazası uygulamaları için ağ yalıtımı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b064497c-d956-46b8-838d-7a0223c7e200
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b6c0665a379f02a74bd0f3631aa26b41dd6ece5a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="network-isolation-for-windows-store-apps"></a><span data-ttu-id="61a75-102">Windows mağazası uygulamaları için ağ yalıtımı</span><span class="sxs-lookup"><span data-stu-id="61a75-102">Network Isolation for Windows Store Apps</span></span>
<span data-ttu-id="61a75-103">Sınıfları <xref:System.Net>, <xref:System.Net.Http>, ve <xref:System.Net.Http.Headers> ad alanları, Windows mağazası uygulamaları veya Masaüstü uygulamaları geliştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="61a75-103">Classes in the <xref:System.Net>,  <xref:System.Net.Http>, and <xref:System.Net.Http.Headers> namespaces can be used to develop Windows Store  apps  or desktop apps.</span></span> <span data-ttu-id="61a75-104">Ağ yalıtımı, uygulama güvenlik modeli tarafından kullanılan bir parçası olarak bu ad alanındaki sınıflar, bir Windows mağazası uygulamasında kullanıldığında, etkilenen [!INCLUDE[win8](../../../includes/win8-md.md)].</span><span class="sxs-lookup"><span data-stu-id="61a75-104">When used in a Windows Store app, classes in these namespaces are affected by network isolation, part of the application security model used by the [!INCLUDE[win8](../../../includes/win8-md.md)].</span></span> <span data-ttu-id="61a75-105">Sistem ağ erişimine izin vermek için Windows mağazası uygulaması için uygulama bildiriminde uygun ağ yeteneklerini etkinleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="61a75-105">The appropriate network capabilities must be enabled in the app manifest for a Windows Store app for the system to allow network access.</span></span>  
  
## <a name="checklist-for-network-isolation"></a><span data-ttu-id="61a75-106">Ağ yalıtımı için Denetim listesi</span><span class="sxs-lookup"><span data-stu-id="61a75-106">Checklist for Network Isolation</span></span>  
 <span data-ttu-id="61a75-107">Ağ yalıtımı Windows mağazası uygulamanız için yapılandırıldığından emin olmak için bu denetim listesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="61a75-107">Use this checklist to be sure that network isolation is configured for your Windows Store app.</span></span>  
  
1.  <span data-ttu-id="61a75-108">Uygulama tarafından gerekli ağ erişimi isteklerini yönünü belirler.</span><span class="sxs-lookup"><span data-stu-id="61a75-108">Determine the direction of network access requests needed by the app.</span></span> <span data-ttu-id="61a75-109">Bu istemci tarafından başlatılan giden istekleri veya gelen istenmeyen istekleri olabilir veya bu ağ isteği türlerinin her ikisinin bir birleşimi olabilir.</span><span class="sxs-lookup"><span data-stu-id="61a75-109">This can be either outbound client-initiated requests or inbound unsolicited requests or it could be a combination of both of these network request types.</span></span>  
  
2.  <span data-ttu-id="61a75-110">Bu uygulama ile iletişim kuracak ağ kaynak türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="61a75-110">Determine the type of network resources that that app will communicate with.</span></span> <span data-ttu-id="61a75-111">Bir uygulama, bir ev veya iş ağı üzerindeki güvenilen kaynakları ile iletişim kurmak gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="61a75-111">An app may need to communicate with trusted resources on a Home or Work network.</span></span> <span data-ttu-id="61a75-112">Bir uygulama, Internet üzerindeki kaynaklara ile iletişim kurmak gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="61a75-112">An app might need to communicate with resources on the Internet.</span></span> <span data-ttu-id="61a75-113">Bir uygulama, her iki tür ağ kaynaklarına erişimi gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="61a75-113">An app might need access to both types of network resources.</span></span>  
  
3.  <span data-ttu-id="61a75-114">Ağ yalıtımı gereken en düşük özellikleri uygulama bildiriminde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="61a75-114">Configure the minimum-required networking isolation capabilities in the app manifest.</span></span>  
  
4.  <span data-ttu-id="61a75-115">Dağıtma ve sorun giderme için sağlanan ağ yalıtımı araçlar kullanılarak test etmek için uygulamanızı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="61a75-115">Deploy and run your app to test it using the network isolation tools provided for troubleshooting.</span></span>  
  
 <span data-ttu-id="61a75-116">Ağ özelliklerini ve ağ yalıtımı sorun giderme için kullanılan yalıtım araçları yapılandırma hakkında daha ayrıntılı bilgi için bkz: [ağ yalıtımı özelliklerini yapılandırmak nasıl](http://go.microsoft.com/fwlink/?LinkID=228265) içinde [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] Geliştirici belgeler.</span><span class="sxs-lookup"><span data-stu-id="61a75-116">For more detailed information on how to configure network capabilities and isolation tools used for troubleshooting network isolation, see [How to configure network isolation capabilities](http://go.microsoft.com/fwlink/?LinkID=228265) in the [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] developer documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61a75-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="61a75-117">See Also</span></span>  
 [<span data-ttu-id="61a75-118">Bir web hizmetine bağlanma</span><span class="sxs-lookup"><span data-stu-id="61a75-118">Connecting to a web service</span></span>](http://go.microsoft.com/fwlink/?LinkID=245696)  
 [<span data-ttu-id="61a75-119">Kılavuzları ve ağ yalıtımı için Denetim listesi</span><span class="sxs-lookup"><span data-stu-id="61a75-119">Guidelines and checklist for network isolation</span></span>](http://go.microsoft.com/fwlink/?LinkID=228265)  
 [<span data-ttu-id="61a75-120">Hızlı Başlangıç: HttpClient kullanarak bağlanma</span><span class="sxs-lookup"><span data-stu-id="61a75-120">Quickstart: Connecting using HttpClient</span></span>](http://go.microsoft.com/fwlink/?LinkId=245697)  
 [<span data-ttu-id="61a75-121">HttpClient işleyicileri kullanma</span><span class="sxs-lookup"><span data-stu-id="61a75-121">How to use HttpClient handlers</span></span>](http://go.microsoft.com/fwlink/?LinkId=245699)  
 [<span data-ttu-id="61a75-122">HttpClient bağlantıları güvenliğini sağlama</span><span class="sxs-lookup"><span data-stu-id="61a75-122">How to secure HttpClient connections</span></span>](http://go.microsoft.com/fwlink/?LinkId=245698)  
 [<span data-ttu-id="61a75-123">HttpClient örnek</span><span class="sxs-lookup"><span data-stu-id="61a75-123">HttpClient Sample</span></span>](http://go.microsoft.com/fwlink/?LinkId=242550)
