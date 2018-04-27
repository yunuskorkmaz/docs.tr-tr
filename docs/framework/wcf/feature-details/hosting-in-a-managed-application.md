---
title: Yönetilen Bir Uygulamada Barındırma
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af70132d-e9e1-4f32-b20f-f0014629758a
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1e81a8eb27725edeccf3e5c7489109ba47b70dec
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="hosting-in-a-managed-application"></a><span data-ttu-id="3b1ec-102">Yönetilen Bir Uygulamada Barındırma</span><span class="sxs-lookup"><span data-stu-id="3b1ec-102">Hosting in a Managed Application</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="3b1ec-103"> Hizmetler barındırılması birinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="3b1ec-103"> services can be hosted in any [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] application.</span></span> <span data-ttu-id="3b1ec-104">Kendi kendine barındırma hizmetleri en esnek barındırma seçenektir; çünkü dağıtmak için en az altyapısı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3b1ec-104">Self-hosting services is the most flexible hosting option because it requires the least infrastructure to deploy.</span></span> <span data-ttu-id="3b1ec-105">Yönetilen uygulamaların farklı barındırma seçenekleri Gelişmiş barındırma ve yönetim özellikleri sağlıyor mu ancak ayrıca en az sağlam barındırma seçeneği demektir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], Internet Information Services (IIS) ve Windows Hizmetleri gibi.</span><span class="sxs-lookup"><span data-stu-id="3b1ec-105">However, it is also the least robust hosting option, because managed applications do not provide the advanced hosting and management features of other hosting options in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], such as Internet Information Services (IIS) and Windows services.</span></span>  
  
 <span data-ttu-id="3b1ec-106">Kendini barındıran hizmet oluşturmak için oluşturun ve bir örneği açın <xref:System.ServiceModel.ServiceHost>, iletiler için dinleme bir hizmetini başlatır.</span><span class="sxs-lookup"><span data-stu-id="3b1ec-106">To create a self-hosted service, create and open an instance of the <xref:System.ServiceModel.ServiceHost>, which starts a service listening for messages.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="3b1ec-107"> [Nasıl yapılır: yönetilen bir uygulamada bir WCF Hizmeti barındırma](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md).</span><span class="sxs-lookup"><span data-stu-id="3b1ec-107"> [How to: Host a WCF Service in a Managed Application](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md).</span></span>  
  
 <span data-ttu-id="3b1ec-108">Bir sözleşme tanımlama, sözleşmeyi uyguladıktan ve yönetilen bir uygulama içinde bir hizmet barındırmak nasıl tam bir örnek için bkz: [başlangıç Öğreticisi](../../../../docs/framework/wcf/getting-started-tutorial.md) ve [kendini barındırma](../../../../docs/framework/wcf/samples/self-host.md).</span><span class="sxs-lookup"><span data-stu-id="3b1ec-108">For a complete example on how to define a contract, implement the contract, and host a service inside of a managed application see the [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md) and the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md).</span></span>  
  
 <span data-ttu-id="3b1ec-109">Aşağıdaki bölümlerde barındırma bu seçeneği kullanın yaygın senaryolar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3b1ec-109">The following sections describe common scenarios that use this hosting option.</span></span>  
  
## <a name="console-applications"></a><span data-ttu-id="3b1ec-110">Konsol uygulamaları</span><span class="sxs-lookup"><span data-stu-id="3b1ec-110">Console Applications</span></span>  
 <span data-ttu-id="3b1ec-111">Kendi kendine barındırma etkinleştirir olan yaygın senaryolar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] içinde çalışan Hizmetleri konsol uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="3b1ec-111">Common scenarios that self-hosting enables are [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services running inside console applications.</span></span> <span data-ttu-id="3b1ec-112">Barındırma bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmeti bir konsol uygulaması içinde yararlıdır genellikle hizmeti geliştirme aşamasında.</span><span class="sxs-lookup"><span data-stu-id="3b1ec-112">Hosting a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service inside a console application is typically useful during the development phase of the service.</span></span> <span data-ttu-id="3b1ec-113">Bu onları kolay hata ayıklamak, uygulama içinde neler olduğunu çıkışı bulmak için izleme bilgilerini almak kolay ve yeni konumlara kopyalayarak hareket etmek kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="3b1ec-113">This makes them easy to debug, easy to get trace information from to find out what is happening inside of the application, and easy to move around by copying them to new locations.</span></span>  
  
## <a name="rich-client-applications"></a><span data-ttu-id="3b1ec-114">Zengin istemci uygulamaları</span><span class="sxs-lookup"><span data-stu-id="3b1ec-114">Rich Client Applications</span></span>  
 <span data-ttu-id="3b1ec-115">Kendi kendine barındırma sağlayan diğer yaygın senaryolar, Windows Presentation Foundation (WPF) veya Windows Forms (WinForms) tabanlı olanlar gibi zengin istemci uygulamaları verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3b1ec-115">Other common scenarios that self-hosting enables are rich client applications, such as those based on Windows Presentation Foundation (WPF) or Windows Forms (WinForms).</span></span> <span data-ttu-id="3b1ec-116">Barındırma bu seçenek ayrıca zengin istemci uygulamaları gibi kolaylaştırır [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] ve dış dünyayla iletişim kurmak için WinForms uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="3b1ec-116">This hosting option also makes it easy for rich client applications, such as [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] and WinForms applications, to communicate with the outside world.</span></span> <span data-ttu-id="3b1ec-117">Örneğin, kullanan eşler arası işbirliği istemci [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] kendi kullanıcı arabirimi ve ayrıca ana bilgisayarlar için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bağlanmak ve bilgi paylaşmak diğer istemciler sağlayan hizmet.</span><span class="sxs-lookup"><span data-stu-id="3b1ec-117">For example, a peer-to-peer collaboration client that uses [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] for its user interface and also hosts a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service that allows other clients to connect to it and share information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b1ec-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3b1ec-118">See Also</span></span>  
 [<span data-ttu-id="3b1ec-119">Barındırma Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="3b1ec-119">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)  
 [<span data-ttu-id="3b1ec-120">Başlangıç Öğreticisi</span><span class="sxs-lookup"><span data-stu-id="3b1ec-120">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)
