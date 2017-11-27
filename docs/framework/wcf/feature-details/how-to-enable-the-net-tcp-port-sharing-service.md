---
title: "Nasıl yapılır: Net.TCP Bağlantı Noktası Payalaşım Hizmetini Etkinleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- port sharing [WCF]
- activation services [WCF]
ms.assetid: c9175af4-c27c-4765-bf45-b8f7528a7282
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e9934d198b8f3e30a4dc350c968263851ebeab1e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enable-the-nettcp-port-sharing-service"></a><span data-ttu-id="fcf2c-102">Nasıl yapılır: Net.TCP Bağlantı Noktası Payalaşım Hizmetini Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="fcf2c-102">How to: Enable the Net.TCP Port Sharing Service</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="fcf2c-103">TCP bağlantı noktaları birden çok işlem paylaşımı kolaylaştırmak için Net.TCP bağlantı noktası Paylaşımı hizmeti adlı bir Windows hizmeti kullanır.</span><span class="sxs-lookup"><span data-stu-id="fcf2c-103"> uses a Windows service called the Net.TCP Port Sharing Service to facilitate the sharing of TCP ports across multiple processes.</span></span> <span data-ttu-id="fcf2c-104">Bu hizmet parçası olarak yüklenen [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], ancak hizmet güvenlik önlemi olarak varsayılan olarak etkin değildir ve öncesinde el ile etkinleştirilmesi gerekir böylece ilk olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="fcf2c-104">This service is installed as part of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], but the service is not enabled by default as a security precaution and so must be manually enabled prior to first use.</span></span> <span data-ttu-id="fcf2c-105">Bu konuda Net TCP bağlantı noktası Microsoft Yönetim Konsolu (MMC) ek bileşenini kullanarak Paylaşımı hizmetinin nasıl yapılandırılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fcf2c-105">This topic describes how to configure the Net TCP Port Sharing Service using the Microsoft Management Console (MMC) snap-In.</span></span>  
  
 <span data-ttu-id="fcf2c-106">Net.TCP bağlantı noktası Paylaşımı hizmeti etkinleştirmek ve el ile başlatmak sonra bkz [nasıl yapılır: bir WCF Hizmeti bağlantı noktası paylaşımı kullanmak üzere yapılandırmak](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md) bu hizmeti kullanmak için hizmetinin nasıl yapılandırılacağı hakkında bilgi için.</span><span class="sxs-lookup"><span data-stu-id="fcf2c-106">After you enable the Net.TCP Port Sharing Service and start it manually, see [How to: Configure a WCF Service to Use Port Sharing](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md) for information about how to configure your service to use this service.</span></span>  
  
 <span data-ttu-id="fcf2c-107">Net.tcp:// bağlantı noktası Paylaşımı kullanan bir örnek için bkz: [Net.TCP bağlantı noktası paylaşımı örneği](../../../../docs/framework/wcf/samples/net-tcp-port-sharing-sample.md).</span><span class="sxs-lookup"><span data-stu-id="fcf2c-107">For a sample that uses net.tcp:// port sharing, see the [Net.TCP Port Sharing Sample](../../../../docs/framework/wcf/samples/net-tcp-port-sharing-sample.md).</span></span>  
  
### <a name="to-enable-the-nettcp-port-sharing-service-using-mmc"></a><span data-ttu-id="fcf2c-108">Net.TCP bağlantı noktası paylaşımı MMC kullanarak hizmeti etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="fcf2c-108">To enable the Net.TCP Port Sharing Service using MMC</span></span>  
  
1.  <span data-ttu-id="fcf2c-109">Başlat menüsünden ya da bir komut istemi penceresini açarak ve yazarak Hizmetler Yönetimi konsolunu açın `services.msc` veya Çalıştır açarak ve yazarak `services.msc` açık kutusuna.</span><span class="sxs-lookup"><span data-stu-id="fcf2c-109">From the Start menu, open the Services Management Console either by opening a Command Prompt window and typing `services.msc` or by opening Run and typing `services.msc` into the Open box.</span></span>  
  
2.  <span data-ttu-id="fcf2c-110">İçinde **adı** sütun hizmetleri listesinin sağ **Net.Tcp Bağlantı Noktası Paylaşımı hizmeti**ve seçin **özellikleri** menüsünde.</span><span class="sxs-lookup"><span data-stu-id="fcf2c-110">In the **Name** column of the list of services, right-click the **Net.Tcp Port Sharing Service**, and select **Properties** from the menu.</span></span>  
  
3.  <span data-ttu-id="fcf2c-111">El ile başlatma hizmeti etkinleştirmek için **özellikleri** penceresi seçin **genel** sekmesi hem de **başlangıç türü** select el ile kutusuna ve ardından tıklatın**Uygulamak**.</span><span class="sxs-lookup"><span data-stu-id="fcf2c-111">To enable the manual start-up of the service, in the **Properties** window select the **General** tab, and in the **Startup type** box select Manual, and then click **Apply**.</span></span>  
  
4.  <span data-ttu-id="fcf2c-112">Hizmet durumu alanında hizmetini başlatmak için tıklatın **Başlat** düğmesi.</span><span class="sxs-lookup"><span data-stu-id="fcf2c-112">To start the service,  in the Service status area, click the **Start** button.</span></span> <span data-ttu-id="fcf2c-113">Hizmet durumu "Başlatıldı" şimdi görüntülemelidir.</span><span class="sxs-lookup"><span data-stu-id="fcf2c-113">The service status should now display "Started".</span></span>  
  
5.  <span data-ttu-id="fcf2c-114">Hizmetleri listesine geri dönmek için tıklatın **Tamam**ve MMC konsolunu çıkın.</span><span class="sxs-lookup"><span data-stu-id="fcf2c-114">To return to the list of services, click the **OK**, and exit the MMC Console.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fcf2c-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="fcf2c-115">Example</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcf2c-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fcf2c-116">See Also</span></span>  
 [<span data-ttu-id="fcf2c-117">Net.TCP bağlantı noktası paylaşımı</span><span class="sxs-lookup"><span data-stu-id="fcf2c-117">Net.TCP Port Sharing</span></span>](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)  
 [<span data-ttu-id="fcf2c-118">Net.TCP bağlantı noktası hizmetini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="fcf2c-118">Configuring the Net.TCP Port Sharing Service</span></span>](../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
