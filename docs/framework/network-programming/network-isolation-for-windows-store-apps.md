---
title: Windows Store uygulamaları için ağ yalıtımı
ms.date: 03/30/2017
ms.assetid: b064497c-d956-46b8-838d-7a0223c7e200
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 4d26b6df5d26a96bb8fa41dd3a8151fcb4a08b75
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43534054"
---
# <a name="network-isolation-for-windows-store-apps"></a><span data-ttu-id="a813d-102">Windows Store uygulamaları için ağ yalıtımı</span><span class="sxs-lookup"><span data-stu-id="a813d-102">Network Isolation for Windows Store Apps</span></span>
<span data-ttu-id="a813d-103">Sınıflar <xref:System.Net>, <xref:System.Net.Http>, ve <xref:System.Net.Http.Headers> ad alanlarında, Windows Store uygulamaları veya Masaüstü uygulamaları geliştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a813d-103">Classes in the <xref:System.Net>,  <xref:System.Net.Http>, and <xref:System.Net.Http.Headers> namespaces can be used to develop Windows Store  apps  or desktop apps.</span></span> <span data-ttu-id="a813d-104">Bir Windows Store uygulaması kullanıldığında, bu ad alanlarında sınıflar tarafından kullanılan uygulama güvenlik modelinin bir parçası olan ağ yalıtımı etkilenir [!INCLUDE[win8](../../../includes/win8-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a813d-104">When used in a Windows Store app, classes in these namespaces are affected by network isolation, part of the application security model used by the [!INCLUDE[win8](../../../includes/win8-md.md)].</span></span> <span data-ttu-id="a813d-105">Uygun ağ yeteneklerini, sistemin ağ erişimine izin ver Windows Store uygulaması için uygulama bildirimindeki etkinleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="a813d-105">The appropriate network capabilities must be enabled in the app manifest for a Windows Store app for the system to allow network access.</span></span>  
  
## <a name="checklist-for-network-isolation"></a><span data-ttu-id="a813d-106">Ağ yalıtımı için Denetim listesi</span><span class="sxs-lookup"><span data-stu-id="a813d-106">Checklist for Network Isolation</span></span>  
 <span data-ttu-id="a813d-107">Ağ yalıtımı, Windows Store uygulaması için yapılandırıldığından emin olmak için bu denetim listesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a813d-107">Use this checklist to be sure that network isolation is configured for your Windows Store app.</span></span>  
  
1.  <span data-ttu-id="a813d-108">Ağ erişimi isteklerini uygulama tarafından gereken yönü belirler.</span><span class="sxs-lookup"><span data-stu-id="a813d-108">Determine the direction of network access requests needed by the app.</span></span> <span data-ttu-id="a813d-109">Bu istemci tarafından başlatılan giden istekleri ya da istenmeyen gelen istekleri olabilir veya bu ağ istek türleri her ikisinin bir birleşimi olabilir.</span><span class="sxs-lookup"><span data-stu-id="a813d-109">This can be either outbound client-initiated requests or inbound unsolicited requests or it could be a combination of both of these network request types.</span></span>  
  
2.  <span data-ttu-id="a813d-110">Bu uygulama ile iletişim kurar ve ağ kaynaklarını türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="a813d-110">Determine the type of network resources that that app will communicate with.</span></span> <span data-ttu-id="a813d-111">Bir uygulama bir ev veya iş ağı üzerinde güvenilen kaynaklarla iletişim gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="a813d-111">An app may need to communicate with trusted resources on a Home or Work network.</span></span> <span data-ttu-id="a813d-112">Bir uygulamayı Internet'teki kaynaklarla iletişim gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="a813d-112">An app might need to communicate with resources on the Internet.</span></span> <span data-ttu-id="a813d-113">Uygulama, her iki türdeki ağ kaynaklarına erişimi gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="a813d-113">An app might need access to both types of network resources.</span></span>  
  
3.  <span data-ttu-id="a813d-114">Ağ yalıtımı gereken en düşük özellikleri uygulama bildirimine yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="a813d-114">Configure the minimum-required networking isolation capabilities in the app manifest.</span></span>  
  
4.  <span data-ttu-id="a813d-115">Dağıtın ve sorun giderme için sağlanan ağ yalıtımı araçları kullanarak test etmek için uygulamanızı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a813d-115">Deploy and run your app to test it using the network isolation tools provided for troubleshooting.</span></span>  
  
 <span data-ttu-id="a813d-116">Ağ özellikleri ve ağ yalıtımı sorun giderme için kullanılan yalıtım araçları yapılandırma hakkında daha ayrıntılı bilgi için bkz. [ağ yalıtımı özelliklerini yapılandırma](https://go.microsoft.com/fwlink/?LinkID=228265) içinde [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] Geliştirici belgeleri.</span><span class="sxs-lookup"><span data-stu-id="a813d-116">For more detailed information on how to configure network capabilities and isolation tools used for troubleshooting network isolation, see [How to configure network isolation capabilities](https://go.microsoft.com/fwlink/?LinkID=228265) in the [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] developer documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a813d-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a813d-117">See Also</span></span>  
 [<span data-ttu-id="a813d-118">Bir web hizmetine bağlanma</span><span class="sxs-lookup"><span data-stu-id="a813d-118">Connecting to a web service</span></span>](https://go.microsoft.com/fwlink/?LinkID=245696)  
 [<span data-ttu-id="a813d-119">Yönergeler ve ağ yalıtımı için Denetim listesi</span><span class="sxs-lookup"><span data-stu-id="a813d-119">Guidelines and checklist for network isolation</span></span>](https://go.microsoft.com/fwlink/?LinkID=228265)  
 [<span data-ttu-id="a813d-120">Hızlı Başlangıç: HttpClient'ı kullanarak bağlanma</span><span class="sxs-lookup"><span data-stu-id="a813d-120">Quickstart: Connecting using HttpClient</span></span>](https://go.microsoft.com/fwlink/?LinkId=245697)  
 [<span data-ttu-id="a813d-121">HttpClient işleyicilerini kullanma</span><span class="sxs-lookup"><span data-stu-id="a813d-121">How to use HttpClient handlers</span></span>](https://go.microsoft.com/fwlink/?LinkId=245699)  
 [<span data-ttu-id="a813d-122">HttpClient bağlantıları güvenliğini sağlama</span><span class="sxs-lookup"><span data-stu-id="a813d-122">How to secure HttpClient connections</span></span>](https://go.microsoft.com/fwlink/?LinkId=245698)  
 [<span data-ttu-id="a813d-123">HttpClient örneği</span><span class="sxs-lookup"><span data-stu-id="a813d-123">HttpClient Sample</span></span>](https://go.microsoft.com/fwlink/?LinkId=242550)
