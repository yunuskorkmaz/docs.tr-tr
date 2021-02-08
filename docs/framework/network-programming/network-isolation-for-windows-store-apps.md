---
description: Hakkında daha fazla bilgi için bkz. Windows Mağazası uygulamaları için ağ yalıtımı
title: Windows Mağazası Uygulamaları için Ağ Yalıtımı
ms.date: 03/30/2017
ms.assetid: b064497c-d956-46b8-838d-7a0223c7e200
ms.openlocfilehash: cc805cb5d5d761bb79b6a307caef6c809aabed16
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785726"
---
# <a name="network-isolation-for-windows-store-apps"></a><span data-ttu-id="bafd1-103">Windows Mağazası Uygulamaları için Ağ Yalıtımı</span><span class="sxs-lookup"><span data-stu-id="bafd1-103">Network Isolation for Windows Store Apps</span></span>

<span data-ttu-id="bafd1-104"><xref:System.Net>, <xref:System.Net.Http> Ve ad alanlarındaki sınıflar, <xref:System.Net.Http.Headers> Windows Mağazası uygulamaları veya masaüstü uygulamaları geliştirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bafd1-104">Classes in the <xref:System.Net>, <xref:System.Net.Http>, and <xref:System.Net.Http.Headers> namespaces can be used to develop Windows Store  apps  or desktop apps.</span></span> <span data-ttu-id="bafd1-105">Bir Windows Mağazası uygulamasında kullanıldığında, bu ad alanlarındaki sınıflar, Windows 8 tarafından kullanılan uygulama güvenlik modelinin parçası olan ağ yalıtımıyla etkilenir.</span><span class="sxs-lookup"><span data-stu-id="bafd1-105">When used in a Windows Store app, classes in these namespaces are affected by network isolation, part of the application security model used by Windows 8.</span></span> <span data-ttu-id="bafd1-106">Sistemin ağ erişimine izin vermek için bir Windows Mağazası uygulamasının uygulama bildiriminde uygun ağ özellikleri etkinleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="bafd1-106">The appropriate network capabilities must be enabled in the app manifest for a Windows Store app for the system to allow network access.</span></span>  
  
## <a name="checklist-for-network-isolation"></a><span data-ttu-id="bafd1-107">Ağ yalıtımı için denetim listesi</span><span class="sxs-lookup"><span data-stu-id="bafd1-107">Checklist for Network Isolation</span></span>  

<span data-ttu-id="bafd1-108">Windows Mağazası uygulamanız için ağ yalıtımının yapılandırıldığından emin olmak için bu denetim listesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="bafd1-108">Use this checklist to be sure that network isolation is configured for your Windows Store app.</span></span>  
  
1. <span data-ttu-id="bafd1-109">Uygulama için gereken ağ erişim isteklerinin yönünü belirleme.</span><span class="sxs-lookup"><span data-stu-id="bafd1-109">Determine the direction of network access requests needed by the app.</span></span> <span data-ttu-id="bafd1-110">Bu, istemci tarafından başlatılan istekler veya gelen istenmeyen istekler olabilir ya da bu ağ isteği türlerinin her ikisinin bir birleşimi olabilir.</span><span class="sxs-lookup"><span data-stu-id="bafd1-110">This can be either outbound client-initiated requests or inbound unsolicited requests or it could be a combination of both of these network request types.</span></span>  
  
2. <span data-ttu-id="bafd1-111">Uygulamanın iletişim kuracağı ağ kaynaklarının türünü saptayın.</span><span class="sxs-lookup"><span data-stu-id="bafd1-111">Determine the type of network resources that the app will communicate with.</span></span> <span data-ttu-id="bafd1-112">Bir uygulamanın ev veya Iş ağı üzerinde güvenilir kaynaklarla iletişim kurması gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="bafd1-112">An app may need to communicate with trusted resources on a Home or Work network.</span></span> <span data-ttu-id="bafd1-113">Bir uygulamanın Internet 'teki kaynaklarla iletişim kurması gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="bafd1-113">An app might need to communicate with resources on the Internet.</span></span> <span data-ttu-id="bafd1-114">Bir uygulamanın her iki tür ağ kaynağına erişmesi gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="bafd1-114">An app might need access to both types of network resources.</span></span>  
  
3. <span data-ttu-id="bafd1-115">Uygulama bildiriminde gereken en düşük ağ yalıtımı özelliklerini yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="bafd1-115">Configure the minimum-required networking isolation capabilities in the app manifest.</span></span>  
  
4. <span data-ttu-id="bafd1-116">Sorun giderme için sunulan ağ yalıtımı araçlarını kullanarak test etmek için uygulamanızı dağıtın ve çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="bafd1-116">Deploy and run your app to test it using the network isolation tools provided for troubleshooting.</span></span>  
  
<span data-ttu-id="bafd1-117">Ağ yalıtımı sorunlarını gidermek için kullanılan ağ yeteneklerini ve yalıtım araçlarını yapılandırma hakkında daha ayrıntılı bilgi için, bkz. Windows 8. x mağaza geliştirici belgelerindeki [ağ yalıtımı yeteneklerini yapılandırma](/previous-versions/windows/apps/hh770532(v=win.10)) .</span><span class="sxs-lookup"><span data-stu-id="bafd1-117">For more detailed information on how to configure network capabilities and isolation tools used for troubleshooting network isolation, see [How to configure network isolation capabilities](/previous-versions/windows/apps/hh770532(v=win.10)) in the Windows 8.x Store developer documentation.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="bafd1-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bafd1-118">See also</span></span>

- <span data-ttu-id="bafd1-119">[Bir Web hizmetine bağlanma](/previous-versions/windows/apps/hh761504(v=win.10))</span><span class="sxs-lookup"><span data-stu-id="bafd1-119">[Connecting to a web service](/previous-versions/windows/apps/hh761504(v=win.10))</span></span>
- <span data-ttu-id="bafd1-120">[Ağ yalıtımı için yönergeler ve denetim listesi](/previous-versions/windows/apps/hh770532(v=win.10))</span><span class="sxs-lookup"><span data-stu-id="bafd1-120">[Guidelines and checklist for network isolation](/previous-versions/windows/apps/hh770532(v=win.10))</span></span>
- <span data-ttu-id="bafd1-121">[Hızlı başlangıç: HttpClient kullanarak bağlanma](/previous-versions/windows/apps/hh781239(v=win.10))</span><span class="sxs-lookup"><span data-stu-id="bafd1-121">[Quickstart: Connecting using HttpClient](/previous-versions/windows/apps/hh781239(v=win.10))</span></span>
- <span data-ttu-id="bafd1-122">[HttpClient işleyicilerini kullanma](/previous-versions/windows/apps/hh781241(v=win.10))</span><span class="sxs-lookup"><span data-stu-id="bafd1-122">[How to use HttpClient handlers](/previous-versions/windows/apps/hh781241(v=win.10))</span></span>
- <span data-ttu-id="bafd1-123">[HttpClient bağlantılarını güvenli hale getirme](/previous-versions/windows/apps/hh781240(v=win.10))</span><span class="sxs-lookup"><span data-stu-id="bafd1-123">[How to secure HttpClient connections](/previous-versions/windows/apps/hh781240(v=win.10))</span></span>
- [<span data-ttu-id="bafd1-124">HttpClient örneği</span><span class="sxs-lookup"><span data-stu-id="bafd1-124">HttpClient Sample</span></span>](https://code.msdn.microsoft.com/windowsapps/HttpClient-sample-55700664)
