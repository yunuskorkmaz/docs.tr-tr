---
title: 'Nasıl yapılır: Net.TCP Bağlantı Noktası Payalaşım Hizmetini Etkinleştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- port sharing [WCF]
- activation services [WCF]
ms.assetid: c9175af4-c27c-4765-bf45-b8f7528a7282
ms.openlocfilehash: 4b5a18e11d9fc15f23b5353883a63d838face58a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490766"
---
# <a name="how-to-enable-the-nettcp-port-sharing-service"></a><span data-ttu-id="05acb-102">Nasıl yapılır: Net.TCP Bağlantı Noktası Payalaşım Hizmetini Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="05acb-102">How to: Enable the Net.TCP Port Sharing Service</span></span>
<span data-ttu-id="05acb-103">Windows Communication Foundation (WCF) TCP bağlantı noktaları birden çok işlem paylaşımı kolaylaştırmak için Net.TCP bağlantı noktası Paylaşımı hizmeti adlı bir Windows hizmeti kullanır.</span><span class="sxs-lookup"><span data-stu-id="05acb-103">Windows Communication Foundation (WCF) uses a Windows service called the Net.TCP Port Sharing Service to facilitate the sharing of TCP ports across multiple processes.</span></span> <span data-ttu-id="05acb-104">Bu hizmet WCF bir parçası olarak yüklenir, ancak hizmet güvenlik önlemi olarak varsayılan olarak etkin değildir ve bu nedenle el ile ilk kullanım önce etkinleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="05acb-104">This service is installed as part of WCF, but the service is not enabled by default as a security precaution and so must be manually enabled prior to first use.</span></span> <span data-ttu-id="05acb-105">Bu konuda Net TCP bağlantı noktası Microsoft Yönetim Konsolu (MMC) ek bileşenini kullanarak Paylaşımı hizmetinin nasıl yapılandırılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="05acb-105">This topic describes how to configure the Net TCP Port Sharing Service using the Microsoft Management Console (MMC) snap-In.</span></span>  
  
 <span data-ttu-id="05acb-106">Net.TCP bağlantı noktası Paylaşımı hizmeti etkinleştirmek ve el ile başlatmak sonra bkz [nasıl yapılır: bir WCF Hizmeti bağlantı noktası paylaşımı kullanmak üzere yapılandırmak](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md) bu hizmeti kullanmak için hizmetinin nasıl yapılandırılacağı hakkında bilgi için.</span><span class="sxs-lookup"><span data-stu-id="05acb-106">After you enable the Net.TCP Port Sharing Service and start it manually, see [How to: Configure a WCF Service to Use Port Sharing](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md) for information about how to configure your service to use this service.</span></span>  
  
 <span data-ttu-id="05acb-107">Net.tcp:// bağlantı noktası Paylaşımı kullanan bir örnek için bkz: [Net.TCP bağlantı noktası paylaşımı örneği](../../../../docs/framework/wcf/samples/net-tcp-port-sharing-sample.md).</span><span class="sxs-lookup"><span data-stu-id="05acb-107">For a sample that uses net.tcp:// port sharing, see the [Net.TCP Port Sharing Sample](../../../../docs/framework/wcf/samples/net-tcp-port-sharing-sample.md).</span></span>  
  
### <a name="to-enable-the-nettcp-port-sharing-service-using-mmc"></a><span data-ttu-id="05acb-108">Net.TCP bağlantı noktası paylaşımı MMC kullanarak hizmeti etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="05acb-108">To enable the Net.TCP Port Sharing Service using MMC</span></span>  
  
1.  <span data-ttu-id="05acb-109">Başlat menüsünden ya da bir komut istemi penceresini açarak ve yazarak Hizmetler Yönetimi konsolunu açın `services.msc` veya Çalıştır açarak ve yazarak `services.msc` açık kutusuna.</span><span class="sxs-lookup"><span data-stu-id="05acb-109">From the Start menu, open the Services Management Console either by opening a Command Prompt window and typing `services.msc` or by opening Run and typing `services.msc` into the Open box.</span></span>  
  
2.  <span data-ttu-id="05acb-110">İçinde **adı** sütun hizmetleri listesinin sağ **Net.Tcp Bağlantı Noktası Paylaşımı hizmeti**ve seçin **özellikleri** menüsünde.</span><span class="sxs-lookup"><span data-stu-id="05acb-110">In the **Name** column of the list of services, right-click the **Net.Tcp Port Sharing Service**, and select **Properties** from the menu.</span></span>  
  
3.  <span data-ttu-id="05acb-111">El ile başlatma hizmeti etkinleştirmek için **özellikleri** penceresi seçin **genel** sekmesi hem de **başlangıç türü** select el ile kutusuna ve ardından tıklatın**Uygulamak**.</span><span class="sxs-lookup"><span data-stu-id="05acb-111">To enable the manual start-up of the service, in the **Properties** window select the **General** tab, and in the **Startup type** box select Manual, and then click **Apply**.</span></span>  
  
4.  <span data-ttu-id="05acb-112">Hizmet durumu alanında hizmetini başlatmak için tıklatın **Başlat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="05acb-112">To start the service,  in the Service status area, click the **Start** button.</span></span> <span data-ttu-id="05acb-113">Hizmet durumu "Başlatıldı" şimdi görüntülemelidir.</span><span class="sxs-lookup"><span data-stu-id="05acb-113">The service status should now display "Started".</span></span>  
  
5.  <span data-ttu-id="05acb-114">Hizmetleri listesine geri dönmek için tıklatın **Tamam**ve MMC konsolunu çıkın.</span><span class="sxs-lookup"><span data-stu-id="05acb-114">To return to the list of services, click the **OK**, and exit the MMC Console.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05acb-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="05acb-115">Example</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05acb-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="05acb-116">See Also</span></span>  
 [<span data-ttu-id="05acb-117">Net.TCP Bağlantı Noktası Paylaşımı</span><span class="sxs-lookup"><span data-stu-id="05acb-117">Net.TCP Port Sharing</span></span>](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)  
 [<span data-ttu-id="05acb-118">Net.TCP Bağlantı Noktası Hizmetini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="05acb-118">Configuring the Net.TCP Port Sharing Service</span></span>](../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
