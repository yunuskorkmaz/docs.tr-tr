---
title: Bir NetTcpBinding Uygulamasını Eş Kanalı Uygulamasına Dönüştürme
ms.date: 03/30/2017
ms.assetid: d4137292-a923-4b8f-8594-42276f2d3ce2
ms.openlocfilehash: 42266d8c7c04e2d8f3f1e4734d9a05181c3f1ea3
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595563"
---
# <a name="converting-a-nettcpbinding-application-to-a-peer-channel-application"></a><span data-ttu-id="e0662-102">Bir NetTcpBinding Uygulamasını Eş Kanalı Uygulamasına Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="e0662-102">Converting a NetTcpBinding Application to a Peer Channel Application</span></span>
<span data-ttu-id="e0662-103">Bağlantı parametrelerini tanımlayan bağlamaları kullanarak, WinFX kullanarak istemciler arasında bağlantılar oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0662-103">You can create connections between clients using the WinFX by using bindings that describe the parameters of the connection.</span></span> <span data-ttu-id="e0662-104">Bir .NET Framework uygulamasını eşler arası bağlantıları kullanacak şekilde dönüştürmek, istemci bağlantıları yaparken bu teknolojiyi destekleyen bir bağlama gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e0662-104">Converting a .NET Framework application to use peer-to-peer connections requires a binding that supports this technology when making client connections.</span></span> <span data-ttu-id="e0662-105">Eş kanal, <xref:System.ServiceModel.NetPeerTcpBinding> ile benzer bir şekilde kullanabileceğiniz, adlı bir bağlama sağlar <xref:System.ServiceModel.NetTcpBinding> .</span><span class="sxs-lookup"><span data-stu-id="e0662-105">Peer Channel provides a binding called <xref:System.ServiceModel.NetPeerTcpBinding>, which you can use in a similar way to the <xref:System.ServiceModel.NetTcpBinding>.</span></span> <span data-ttu-id="e0662-106">Temel farklılıklar, bir çözümleyici Hizmeti belirtmeyi ve güvenlik ayarlarını tanımlamayı içerir.</span><span class="sxs-lookup"><span data-stu-id="e0662-106">Key differences include specifying a resolver service and defining security settings.</span></span>  
  
 <span data-ttu-id="e0662-107">Bir uygulama varsayılan çözümleyici ve güvenlik ayarlarını kullanıyorsa, normal bir istemci/sunucu tabanlı uygulamayı eş kanalını kullanacak şekilde dönüştürmek, uygulamanın yapılandırma dosyasında "NetTcpBinding" olan bağlamanın "NetPeerTcpBinding" olarak değiştirilmesini gerektirir; uygulama kodu tabanını değiştirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="e0662-107">If an application is using the default resolver and security settings, converting a normal client/server-based application to use Peer Channel entails changing the name of the binding from "NetTcpBinding" to "NetPeerTcpBinding" in the application’s configuration file—you do not have to change the application code base.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0662-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0662-108">See also</span></span>

- [<span data-ttu-id="e0662-109">Eş Kanal Uygulaması Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e0662-109">Building a Peer Channel Application</span></span>](building-a-peer-channel-application.md)
- [<span data-ttu-id="e0662-110">Sistem tarafından sağlanmış bağlamalar</span><span class="sxs-lookup"><span data-stu-id="e0662-110">System-Provided Bindings</span></span>](../system-provided-bindings.md)
