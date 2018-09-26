---
title: WCF Güvenliğinde Şifreleme Çevikliği
ms.date: 03/30/2017
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
author: BrucePerlerMS
ms.openlocfilehash: df40a87e2fe58b93a963d53fc79f88bbc7bdb805
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47171627"
---
# <a name="cryptographic-agility-in-wcf-security"></a><span data-ttu-id="66340-102">WCF Güvenliğinde Şifreleme Çevikliği</span><span class="sxs-lookup"><span data-stu-id="66340-102">Cryptographic Agility in WCF Security</span></span>
<span data-ttu-id="66340-103">Bu örnek, bir Windows Communication Foundation (WCF) istemci ve hizmet şifreleme ve Çevik bir uygulama sağlamak için bir standart/özel algoritması belirtin gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="66340-103">This sample shows how to specify in a standard/custom algorithm to provide a cryptographic agile implementation in a Windows Communication Foundation (WCF) client and service.</span></span> <span data-ttu-id="66340-104">Örnek, aşağıdaki projelerin oluşur:</span><span class="sxs-lookup"><span data-stu-id="66340-104">The sample is composed of the following projects:</span></span>  
  
 <span data-ttu-id="66340-105">Hizmet</span><span class="sxs-lookup"><span data-stu-id="66340-105">Service</span></span>  
 <span data-ttu-id="66340-106">Bu uygulayan şirket içinde barındırılan bir WCF hizmeti, `ICalculator` arabirim ve uç noktayı kullanarak güvenliğini sağlar <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> güvenli oturum ve güvenilir oturum devre dışı.</span><span class="sxs-lookup"><span data-stu-id="66340-106">This is a self-hosted WCF service that implements the `ICalculator` interface and secures the endpoint using the <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> with secure session and reliable session disabled.</span></span> <span data-ttu-id="66340-107">Özel bir hizmet tanımlar `SecurityAlgorithmSuite` ileti güvenliği için kullanılacak şifreleme algoritmalarını belirlemek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="66340-107">The service defines a custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>  
  
 <span data-ttu-id="66340-108">İstemci</span><span class="sxs-lookup"><span data-stu-id="66340-108">Client</span></span>  
 <span data-ttu-id="66340-109">Başarılı kimlik doğrulamasından sonra hizmete erişen bir WCFclient budur.</span><span class="sxs-lookup"><span data-stu-id="66340-109">This is a WCFclient that accesses the service after successful authentication.</span></span> <span data-ttu-id="66340-110">Tarafından sunulan işlemleri çağırır `ICalculator` arabirim ve hizmet tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="66340-110">It invokes the operations exposed by the `ICalculator` interface and implemented by the service.</span></span> <span data-ttu-id="66340-111">İstemci Ayrıca, aynı özel tanımlar `SecurityAlgorithmSuite` ileti güvenliği için kullanılacak şifreleme algoritmalarını belirlemek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="66340-111">The client also defines the same custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>  
  
### <a name="to-use-this-sample"></a><span data-ttu-id="66340-112">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="66340-112">To use this sample</span></span>  
  
1.  <span data-ttu-id="66340-113">CryptoAgility.sln çözümde açık [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="66340-113">Open the CryptoAgility.sln solution in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="66340-114">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="66340-114">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="66340-115">Açık [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] \WCF\Basic\Security\CryptoAgility\Service\bin dizine gidin ve service.exe sağ tıklatıp seçerek service.exe dosyasını yönetici ayrıcalıklarıyla çalıştırın **yönetici olarak çalıştır**.</span><span class="sxs-lookup"><span data-stu-id="66340-115">Open [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] and navigate to the \WCF\Basic\Security\CryptoAgility\Service\bin directory and run the service.exe file with administrator privileges by right-clicking service.exe and selecting **Run as administrator**.</span></span>  
  
4.  <span data-ttu-id="66340-116">\WCF\Basic\Security\CryptoAgility\Client\bin dizine gidin ve normalde client.exe dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="66340-116">Navigate to \WCF\Basic\Security\CryptoAgility\Client\bin directory and run the client.exe file normally.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="66340-117">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="66340-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="66340-118">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="66340-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="66340-119">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="66340-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="66340-120">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="66340-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`  
  
## <a name="see-also"></a><span data-ttu-id="66340-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="66340-121">See Also</span></span>  
 [<span data-ttu-id="66340-122">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="66340-122">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
