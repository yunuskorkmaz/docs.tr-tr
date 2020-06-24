---
title: 'Nasıl yapılır: Net.TCP Bağlantı Noktası Payalaşım Hizmetini Etkinleştirme'
description: Varsayılan olarak devre dışı bırakılan net. TCP ' yi etkinleştirmek için, MMC kullanarak net TCP bağlantı noktası paylaşım hizmetini nasıl yapılandıracağınızı öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- port sharing [WCF]
- activation services [WCF]
ms.assetid: c9175af4-c27c-4765-bf45-b8f7528a7282
ms.openlocfilehash: 0292559e3befde7f0b00b36aa10a2d9615daf049
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247006"
---
# <a name="how-to-enable-the-nettcp-port-sharing-service"></a><span data-ttu-id="b4b03-103">Nasıl yapılır: Net.TCP Bağlantı Noktası Payalaşım Hizmetini Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="b4b03-103">How to: Enable the Net.TCP Port Sharing Service</span></span>
<span data-ttu-id="b4b03-104">Windows Communication Foundation (WCF), TCP bağlantı noktalarının birden çok işlem arasında paylaşılmasını kolaylaştırmak için net. TCP bağlantı noktası paylaşma hizmeti adlı bir Windows hizmeti kullanır.</span><span class="sxs-lookup"><span data-stu-id="b4b03-104">Windows Communication Foundation (WCF) uses a Windows service called the Net.TCP Port Sharing Service to facilitate the sharing of TCP ports across multiple processes.</span></span> <span data-ttu-id="b4b03-105">Bu hizmet, WCF 'nin bir parçası olarak yüklenir, ancak hizmet varsayılan olarak bir güvenlik önlemi olarak etkinleştirilmemiştir ve bu nedenle, ilk kullanılmadan önce el ile etkinleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="b4b03-105">This service is installed as part of WCF, but the service is not enabled by default as a security precaution and so must be manually enabled prior to first use.</span></span> <span data-ttu-id="b4b03-106">Bu konuda, Microsoft Yönetim Konsolu (MMC) ek bileşenini kullanarak net TCP bağlantı noktası paylaşım hizmeti 'nin nasıl yapılandırılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b4b03-106">This topic describes how to configure the Net TCP Port Sharing Service using the Microsoft Management Console (MMC) snap-In.</span></span>  
  
 <span data-ttu-id="b4b03-107">Net. TCP bağlantı noktası paylaşım hizmetini etkinleştirip el ile başlattıktan sonra, bu hizmeti kullanmak için hizmetinizi yapılandırma hakkında bilgi için bkz. [nasıl yapılır: WCF hizmetini bağlantı noktası Paylaşımı kullanmak üzere yapılandırma](how-to-configure-a-wcf-service-to-use-port-sharing.md) .</span><span class="sxs-lookup"><span data-stu-id="b4b03-107">After you enable the Net.TCP Port Sharing Service and start it manually, see [How to: Configure a WCF Service to Use Port Sharing](how-to-configure-a-wcf-service-to-use-port-sharing.md) for information about how to configure your service to use this service.</span></span>  
  
 <span data-ttu-id="b4b03-108">Net. TCP://bağlantı noktası Paylaşımı kullanan bir örnek için bkz. [net. TCP bağlantı noktası paylaşma örneği](../samples/net-tcp-port-sharing-sample.md).</span><span class="sxs-lookup"><span data-stu-id="b4b03-108">For a sample that uses net.tcp:// port sharing, see the [Net.TCP Port Sharing Sample](../samples/net-tcp-port-sharing-sample.md).</span></span>  
  
### <a name="to-enable-the-nettcp-port-sharing-service-using-mmc"></a><span data-ttu-id="b4b03-109">MMC kullanarak net. TCP bağlantı noktası paylaşma hizmetini etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="b4b03-109">To enable the Net.TCP Port Sharing Service using MMC</span></span>  
  
1. <span data-ttu-id="b4b03-110">Başlat menüsünde, bir komut Istemi penceresi açıp `services.msc` ya da Çalıştır ' ı açıp Aç kutusuna yazarak hizmetler yönetimi konsolunu açın `services.msc` .</span><span class="sxs-lookup"><span data-stu-id="b4b03-110">From the Start menu, open the Services Management Console either by opening a Command Prompt window and typing `services.msc` or by opening Run and typing `services.msc` into the Open box.</span></span>  
  
2. <span data-ttu-id="b4b03-111">Hizmetler listesinin **ad** sütununda, **net. TCP bağlantı noktası paylaşım hizmeti**' ne sağ tıklayın ve menüden **Özellikler** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="b4b03-111">In the **Name** column of the list of services, right-click the **Net.Tcp Port Sharing Service**, and select **Properties** from the menu.</span></span>  
  
3. <span data-ttu-id="b4b03-112">Hizmetin el ile başlamasını etkinleştirmek için, **Özellikler** penceresinde **genel** sekmesini seçin ve **Başlangıç türü** kutusunda el Ile ' yi seçin ve ardından **Uygula**' ya tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b4b03-112">To enable the manual start-up of the service, in the **Properties** window select the **General** tab, and in the **Startup type** box select Manual, and then click **Apply**.</span></span>  
  
4. <span data-ttu-id="b4b03-113">Hizmeti başlatmak için, hizmet durumu alanında **Başlat** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b4b03-113">To start the service,  in the Service status area, click the **Start** button.</span></span> <span data-ttu-id="b4b03-114">Hizmet durumu şimdi "başlatıldı" olarak görüntülenmelidir.</span><span class="sxs-lookup"><span data-stu-id="b4b03-114">The service status should now display "Started".</span></span>  
  
5. <span data-ttu-id="b4b03-115">Hizmetler listesine geri dönmek için **Tamam**' a tıklayın ve MMC konsolundan çıkın.</span><span class="sxs-lookup"><span data-stu-id="b4b03-115">To return to the list of services, click the **OK**, and exit the MMC Console.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4b03-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="b4b03-116">Example</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4b03-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b4b03-117">See also</span></span>

- [<span data-ttu-id="b4b03-118">Net.TCP Bağlantı Noktası Paylaşımı</span><span class="sxs-lookup"><span data-stu-id="b4b03-118">Net.TCP Port Sharing</span></span>](net-tcp-port-sharing.md)
- [<span data-ttu-id="b4b03-119">Net.TCP Bağlantı Noktası Hizmetini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b4b03-119">Configuring the Net.TCP Port Sharing Service</span></span>](configuring-the-net-tcp-port-sharing-service.md)
