---
title: 'Nasıl yapılır: Net.TCP Bağlantı Noktası Payalaşım Hizmetini Etkinleştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- port sharing [WCF]
- activation services [WCF]
ms.assetid: c9175af4-c27c-4765-bf45-b8f7528a7282
ms.openlocfilehash: 20db0ef427a5e791bd6b8dcef90bf7911ae0d4a9
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59343486"
---
# <a name="how-to-enable-the-nettcp-port-sharing-service"></a><span data-ttu-id="dd384-102">Nasıl yapılır: Net.TCP Bağlantı Noktası Payalaşım Hizmetini Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="dd384-102">How to: Enable the Net.TCP Port Sharing Service</span></span>
<span data-ttu-id="dd384-103">Windows Communication Foundation (WCF) Net.TCP bağlantı noktası paylaşma hizmeti adlı bir Windows hizmeti TCP bağlantı noktaları arasında birden çok işlem paylaşımını kolaylaştırmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="dd384-103">Windows Communication Foundation (WCF) uses a Windows service called the Net.TCP Port Sharing Service to facilitate the sharing of TCP ports across multiple processes.</span></span> <span data-ttu-id="dd384-104">Bu hizmet WCF'nin bir parçası yüklenir, ancak hizmet bir güvenlik önlemi olarak varsayılan olarak etkin değildir ve bu nedenle el ile ilk kullanımda önce etkinleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="dd384-104">This service is installed as part of WCF, but the service is not enabled by default as a security precaution and so must be manually enabled prior to first use.</span></span> <span data-ttu-id="dd384-105">Bu konuda, Net TCP bağlantı noktası Microsoft Yönetim Konsolu (MMC) ek bileşenini kullanarak paylaşım hizmetinin nasıl yapılandırılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dd384-105">This topic describes how to configure the Net TCP Port Sharing Service using the Microsoft Management Console (MMC) snap-In.</span></span>  
  
 <span data-ttu-id="dd384-106">Net.TCP bağlantı noktası paylaşım hizmetini etkinleştirme ve el ile başlatın, sonra bakın [nasıl yapılır: Bağlantı noktası paylaşımı kullanmak üzere bir WCF hizmetini yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md) bu hizmeti kullanmak için hizmetinizi yapılandırma hakkında daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="dd384-106">After you enable the Net.TCP Port Sharing Service and start it manually, see [How to: Configure a WCF Service to Use Port Sharing](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md) for information about how to configure your service to use this service.</span></span>  
  
 <span data-ttu-id="dd384-107">Bağlantı noktası net.tcp:// Paylaşımı kullanan bir örnek için bkz. [Net.TCP bağlantı noktası paylaşımı örneği](../../../../docs/framework/wcf/samples/net-tcp-port-sharing-sample.md).</span><span class="sxs-lookup"><span data-stu-id="dd384-107">For a sample that uses net.tcp:// port sharing, see the [Net.TCP Port Sharing Sample](../../../../docs/framework/wcf/samples/net-tcp-port-sharing-sample.md).</span></span>  
  
### <a name="to-enable-the-nettcp-port-sharing-service-using-mmc"></a><span data-ttu-id="dd384-108">Net.TCP bağlantı noktası paylaşımı kullanarak MMC hizmetini etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="dd384-108">To enable the Net.TCP Port Sharing Service using MMC</span></span>  
  
1. <span data-ttu-id="dd384-109">Başlat Menüsü'nden ya da bir komut istemi penceresi açıp ve yazarak Hizmetler Yönetimi konsolunu açın `services.msc` veya Çalıştır'ı açıp yazarak `services.msc` Aç kutusuna.</span><span class="sxs-lookup"><span data-stu-id="dd384-109">From the Start menu, open the Services Management Console either by opening a Command Prompt window and typing `services.msc` or by opening Run and typing `services.msc` into the Open box.</span></span>  
  
2. <span data-ttu-id="dd384-110">İçinde **adı** hizmetlerin listesi sütuna sağ tıklayın **Net.Tcp Bağlantı noktası paylaşma hizmeti**seçip **özellikleri** menüsünde.</span><span class="sxs-lookup"><span data-stu-id="dd384-110">In the **Name** column of the list of services, right-click the **Net.Tcp Port Sharing Service**, and select **Properties** from the menu.</span></span>  
  
3. <span data-ttu-id="dd384-111">Hizmeti el ile başlatma etkinleştirmek için **özellikleri** penceresi seçin **genel** sekmesinde ve **başlangıç türü** select el ile kutusuna ve ardından tıklayın**Uygulamak**.</span><span class="sxs-lookup"><span data-stu-id="dd384-111">To enable the manual start-up of the service, in the **Properties** window select the **General** tab, and in the **Startup type** box select Manual, and then click **Apply**.</span></span>  
  
4. <span data-ttu-id="dd384-112">Hizmet hizmet durumu alanında başlatmak için tıklatın **Başlat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="dd384-112">To start the service,  in the Service status area, click the **Start** button.</span></span> <span data-ttu-id="dd384-113">Hizmet durumu, artık "Başlarken" görüntülemelidir.</span><span class="sxs-lookup"><span data-stu-id="dd384-113">The service status should now display "Started".</span></span>  
  
5. <span data-ttu-id="dd384-114">Hizmetler listesine dönmek için **Tamam**ve MMC konsolunu çıkın.</span><span class="sxs-lookup"><span data-stu-id="dd384-114">To return to the list of services, click the **OK**, and exit the MMC Console.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd384-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="dd384-115">Example</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd384-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd384-116">See also</span></span>

- [<span data-ttu-id="dd384-117">Net.TCP Bağlantı Noktası Paylaşımı</span><span class="sxs-lookup"><span data-stu-id="dd384-117">Net.TCP Port Sharing</span></span>](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)
- [<span data-ttu-id="dd384-118">Net.TCP Bağlantı Noktası Hizmetini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="dd384-118">Configuring the Net.TCP Port Sharing Service</span></span>](../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
