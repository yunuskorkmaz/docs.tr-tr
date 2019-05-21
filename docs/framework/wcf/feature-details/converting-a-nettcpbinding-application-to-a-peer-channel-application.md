---
title: Bir NetTcpBinding Uygulamasını Eş Kanalı Uygulamasına Dönüştürme
ms.date: 03/30/2017
ms.assetid: d4137292-a923-4b8f-8594-42276f2d3ce2
ms.openlocfilehash: 362945959a781fac360c42475148fee1e47a1183
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65960126"
---
# <a name="converting-a-nettcpbinding-application-to-a-peer-channel-application"></a><span data-ttu-id="18c6d-102">Bir NetTcpBinding Uygulamasını Eş Kanalı Uygulamasına Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="18c6d-102">Converting a NetTcpBinding Application to a Peer Channel Application</span></span>
<span data-ttu-id="18c6d-103">Bağlantı parametrelerini açıklayan bağlamaları kullanarak WinFX istemciler arasında bağlantılar oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="18c6d-103">You can create connections between clients using the WinFX by using bindings that describe the parameters of the connection.</span></span> <span data-ttu-id="18c6d-104">Eşler arası bağlantıları kullanmak için bir .NET Framework uygulamasına dönüştürme istemci bağlantıları yaparken bu teknolojiyi destekliyorsa bir bağlama gerektirir.</span><span class="sxs-lookup"><span data-stu-id="18c6d-104">Converting a .NET Framework application to use peer-to-peer connections requires a binding that supports this technology when making client connections.</span></span> <span data-ttu-id="18c6d-105">Eş kanal adlı bir bağlama sağlar <xref:System.ServiceModel.NetPeerTcpBinding>, benzer bir şekilde kullanabileceğiniz <xref:System.ServiceModel.NetTcpBinding>.</span><span class="sxs-lookup"><span data-stu-id="18c6d-105">Peer Channel provides a binding called <xref:System.ServiceModel.NetPeerTcpBinding>, which you can use in a similar way to the <xref:System.ServiceModel.NetTcpBinding>.</span></span> <span data-ttu-id="18c6d-106">Temel farklılıklar çözümleyici hizmetini belirtme ve güvenlik ayarlarını tanımlama içerir.</span><span class="sxs-lookup"><span data-stu-id="18c6d-106">Key differences include specifying a resolver service and defining security settings.</span></span>  
  
 <span data-ttu-id="18c6d-107">Uygulamanın varsayılan çözümleyici ve güvenlik ayarlarını kullanıyorsa, eş kanaldan kullanmak için normal bir istemci/sunucu tabanlı uygulamaya dönüştürme "NetTcpBinding" bağlamayı adının değiştirilmesi "NetPeerTcpBinding için" içinde uygulamanın kapsar yapılandırma dosyası — uygulama kod tabanını değiştirmek zorunda değilsiniz.</span><span class="sxs-lookup"><span data-stu-id="18c6d-107">If an application is using the default resolver and security settings, converting a normal client/server-based application to use Peer Channel entails changing the name of the binding from "NetTcpBinding" to "NetPeerTcpBinding" in the application’s configuration file—you do not have to change the application code base.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18c6d-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="18c6d-108">See also</span></span>

- [<span data-ttu-id="18c6d-109">Eş Kanal Uygulaması Oluşturma</span><span class="sxs-lookup"><span data-stu-id="18c6d-109">Building a Peer Channel Application</span></span>](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
- [<span data-ttu-id="18c6d-110">Sistem Tarafından Sağlanan Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="18c6d-110">System-Provided Bindings</span></span>](../../../../docs/framework/wcf/system-provided-bindings.md)
