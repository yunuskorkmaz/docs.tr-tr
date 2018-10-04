---
title: WCF Güvenliğinde Şifreleme Çevikliği
ms.date: 03/30/2017
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
author: BrucePerlerMS
ms.openlocfilehash: ebc1b51e2e16f1414f2ed1f4a49a69e26583a17b
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48579468"
---
# <a name="cryptographic-agility-in-wcf-security"></a><span data-ttu-id="0687b-102">WCF Güvenliğinde Şifreleme Çevikliği</span><span class="sxs-lookup"><span data-stu-id="0687b-102">Cryptographic Agility in WCF Security</span></span>
<span data-ttu-id="0687b-103">Bu örnek, bir Windows Communication Foundation (WCF) istemci ve hizmet şifreleme ve Çevik bir uygulama sağlamak için bir standart/özel algoritması belirtin gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0687b-103">This sample shows how to specify in a standard/custom algorithm to provide a cryptographic agile implementation in a Windows Communication Foundation (WCF) client and service.</span></span> <span data-ttu-id="0687b-104">Örnek, aşağıdaki projelerin oluşur:</span><span class="sxs-lookup"><span data-stu-id="0687b-104">The sample is composed of the following projects:</span></span>

 <span data-ttu-id="0687b-105">Bu, uygulayan şirket içinde barındırılan bir WCF hizmeti hizmet `ICalculator` arabirim ve uç noktayı kullanarak güvenliğini sağlar <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> güvenli oturum ve güvenilir oturum devre dışı.</span><span class="sxs-lookup"><span data-stu-id="0687b-105">Service This is a self-hosted WCF service that implements the `ICalculator` interface and secures the endpoint using the <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> with secure session and reliable session disabled.</span></span> <span data-ttu-id="0687b-106">Özel bir hizmet tanımlar `SecurityAlgorithmSuite` ileti güvenliği için kullanılacak şifreleme algoritmalarını belirlemek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="0687b-106">The service defines a custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>

 <span data-ttu-id="0687b-107">İstemci başarılı kimlik doğrulamasından sonra hizmete erişen bir WCFclient budur.</span><span class="sxs-lookup"><span data-stu-id="0687b-107">Client This is a WCFclient that accesses the service after successful authentication.</span></span> <span data-ttu-id="0687b-108">Tarafından sunulan işlemleri çağırır `ICalculator` arabirim ve hizmet tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="0687b-108">It invokes the operations exposed by the `ICalculator` interface and implemented by the service.</span></span> <span data-ttu-id="0687b-109">İstemci Ayrıca, aynı özel tanımlar `SecurityAlgorithmSuite` ileti güvenliği için kullanılacak şifreleme algoritmalarını belirlemek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="0687b-109">The client also defines the same custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>

### <a name="to-use-this-sample"></a><span data-ttu-id="0687b-110">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="0687b-110">To use this sample</span></span>

1.  <span data-ttu-id="0687b-111">Visual Studio 2012'de CryptoAgility.sln çözümü açın.</span><span class="sxs-lookup"><span data-stu-id="0687b-111">Open the CryptoAgility.sln solution in Visual Studio 2012.</span></span>

2.  <span data-ttu-id="0687b-112">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="0687b-112">Press CTRL+SHIFT+B to build the solution.</span></span>

3.  <span data-ttu-id="0687b-113">Açık [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] \WCF\Basic\Security\CryptoAgility\Service\bin dizine gidin ve service.exe sağ tıklatıp seçerek service.exe dosyasını yönetici ayrıcalıklarıyla çalıştırın **yönetici olarak çalıştır**.</span><span class="sxs-lookup"><span data-stu-id="0687b-113">Open [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] and navigate to the \WCF\Basic\Security\CryptoAgility\Service\bin directory and run the service.exe file with administrator privileges by right-clicking service.exe and selecting **Run as administrator**.</span></span>

4.  <span data-ttu-id="0687b-114">\WCF\Basic\Security\CryptoAgility\Client\bin dizine gidin ve normalde client.exe dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0687b-114">Navigate to \WCF\Basic\Security\CryptoAgility\Client\bin directory and run the client.exe file normally.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="0687b-115">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="0687b-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0687b-116">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="0687b-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0687b-117">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="0687b-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0687b-118">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="0687b-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`  
  
## <a name="see-also"></a><span data-ttu-id="0687b-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0687b-119">See Also</span></span>  
 [<span data-ttu-id="0687b-120">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="0687b-120">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
