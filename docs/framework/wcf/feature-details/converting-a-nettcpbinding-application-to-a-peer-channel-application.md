---
title: "Bir NetTcpBinding Uygulamasını Eş Kanalı Uygulamasına Dönüştürme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4137292-a923-4b8f-8594-42276f2d3ce2
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 532171dfeba965ae30dc92f31448cf38964fc695
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="converting-a-nettcpbinding-application-to-a-peer-channel-application"></a><span data-ttu-id="8d770-102">Bir NetTcpBinding Uygulamasını Eş Kanalı Uygulamasına Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="8d770-102">Converting a NetTcpBinding Application to a Peer Channel Application</span></span>
<span data-ttu-id="8d770-103">Kullanan istemciler arasında bağlantılar oluşturabilirsiniz [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] bağlantı parametreleri açıklayan bağlamaları kullanarak.</span><span class="sxs-lookup"><span data-stu-id="8d770-103">You can create connections between clients using the [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] by using bindings that describe the parameters of the connection.</span></span> <span data-ttu-id="8d770-104">Dönüştürme bir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] eşler arası bağlantılar kullanmak için uygulama, istemci bağlantıları yaparken bu teknolojiyi destekliyorsa bir bağlama gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8d770-104">Converting a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] application to use peer-to-peer connections requires a binding that supports this technology when making client connections.</span></span> <span data-ttu-id="8d770-105">Eş kanal sağlar adlı bir bağlama <xref:System.ServiceModel.NetPeerTcpBinding>, benzer bir şekilde kullanabileceğiniz <xref:System.ServiceModel.NetTcpBinding>.</span><span class="sxs-lookup"><span data-stu-id="8d770-105">Peer Channel provides a binding called <xref:System.ServiceModel.NetPeerTcpBinding>, which you can use in a similar way to the <xref:System.ServiceModel.NetTcpBinding>.</span></span> <span data-ttu-id="8d770-106">Temel farklılıklar bir çözümleyicisini belirtme ve güvenlik ayarları tanımlama içerir.</span><span class="sxs-lookup"><span data-stu-id="8d770-106">Key differences include specifying a resolver service and defining security settings.</span></span>  
  
 <span data-ttu-id="8d770-107">Bir uygulama varsayılan çözümleyici ve güvenlik ayarlarını kullanıyorsa, eş kanalı kullanmak için normal bir istemci/sunucu tabanlı uygulamaya dönüştürme "NetTcpBinding" bağlamayı adının değiştirilmesi "NetPeerTcpBinding" uygulamanın içinde kapsar yapılandırma dosyası — uygulama kod tabanını değiştirmek zorunda değilsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d770-107">If an application is using the default resolver and security settings, converting a normal client/server-based application to use Peer Channel entails changing the name of the binding from "NetTcpBinding" to "NetPeerTcpBinding" in the application’s configuration file—you do not have to change the application code base.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d770-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8d770-108">See Also</span></span>  
 [<span data-ttu-id="8d770-109">Eş kanal uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="8d770-109">Building a Peer Channel Application</span></span>](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)  
 [<span data-ttu-id="8d770-110">Sistem tarafından sağlanan bağlamalar</span><span class="sxs-lookup"><span data-stu-id="8d770-110">System-Provided Bindings</span></span>](../../../../docs/framework/wcf/system-provided-bindings.md)
