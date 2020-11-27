---
title: Bir NetTcpBinding Uygulamasını Eş Kanalı Uygulamasına Dönüştürme
ms.date: 03/30/2017
ms.assetid: d4137292-a923-4b8f-8594-42276f2d3ce2
ms.openlocfilehash: 5444b53f0373a2f2b06da680a53e8e5fa77d39b7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96286740"
---
# <a name="converting-a-nettcpbinding-application-to-a-peer-channel-application"></a><span data-ttu-id="5b493-102">Bir NetTcpBinding Uygulamasını Eş Kanalı Uygulamasına Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="5b493-102">Converting a NetTcpBinding Application to a Peer Channel Application</span></span>

<span data-ttu-id="5b493-103">Bağlantı parametrelerini tanımlayan bağlamaları kullanarak, WinFX kullanarak istemciler arasında bağlantılar oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b493-103">You can create connections between clients using the WinFX by using bindings that describe the parameters of the connection.</span></span> <span data-ttu-id="5b493-104">Bir .NET Framework uygulamasını eşler arası bağlantıları kullanacak şekilde dönüştürmek, istemci bağlantıları yaparken bu teknolojiyi destekleyen bir bağlama gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5b493-104">Converting a .NET Framework application to use peer-to-peer connections requires a binding that supports this technology when making client connections.</span></span> <span data-ttu-id="5b493-105">Eş kanal, <xref:System.ServiceModel.NetPeerTcpBinding> ile benzer bir şekilde kullanabileceğiniz, adlı bir bağlama sağlar <xref:System.ServiceModel.NetTcpBinding> .</span><span class="sxs-lookup"><span data-stu-id="5b493-105">Peer Channel provides a binding called <xref:System.ServiceModel.NetPeerTcpBinding>, which you can use in a similar way to the <xref:System.ServiceModel.NetTcpBinding>.</span></span> <span data-ttu-id="5b493-106">Temel farklılıklar, bir çözümleyici Hizmeti belirtmeyi ve güvenlik ayarlarını tanımlamayı içerir.</span><span class="sxs-lookup"><span data-stu-id="5b493-106">Key differences include specifying a resolver service and defining security settings.</span></span>  
  
 <span data-ttu-id="5b493-107">Bir uygulama varsayılan çözümleyici ve güvenlik ayarlarını kullanıyorsa, normal bir istemci/sunucu tabanlı uygulamayı eş kanalını kullanacak şekilde dönüştürmek, uygulamanın yapılandırma dosyasında "NetTcpBinding" olan bağlamanın "NetPeerTcpBinding" olarak değiştirilmesini gerektirir; uygulama kodu tabanını değiştirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="5b493-107">If an application is using the default resolver and security settings, converting a normal client/server-based application to use Peer Channel entails changing the name of the binding from "NetTcpBinding" to "NetPeerTcpBinding" in the application’s configuration file—you do not have to change the application code base.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b493-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b493-108">See also</span></span>

- [<span data-ttu-id="5b493-109">Eş Kanal Uygulaması Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5b493-109">Building a Peer Channel Application</span></span>](building-a-peer-channel-application.md)
- [<span data-ttu-id="5b493-110">Sistem Tarafından Sağlanan Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="5b493-110">System-Provided Bindings</span></span>](../system-provided-bindings.md)
