---
title: WCF Güvenliğinde Şifreleme Çevikliği
ms.date: 03/30/2017
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 40f4f8523d5286911216180846e94ec18e40da1c
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="cryptographic-agility-in-wcf-security"></a><span data-ttu-id="a814f-102">WCF Güvenliğinde Şifreleme Çevikliği</span><span class="sxs-lookup"><span data-stu-id="a814f-102">Cryptographic Agility in WCF Security</span></span>
<span data-ttu-id="a814f-103">Bu örnek, bir şifreleme Çevik uygulamasında bir Windows Communication Foundation (WCF) istemci ve hizmet sağlamak için bir standart/özel algoritması belirtmek üzere gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a814f-103">This sample shows how to specify in a standard/custom algorithm to provide a cryptographic agile implementation in a Windows Communication Foundation (WCF) client and service.</span></span> <span data-ttu-id="a814f-104">Örnek aşağıdaki projeleri oluşur:</span><span class="sxs-lookup"><span data-stu-id="a814f-104">The sample is composed of the following projects:</span></span>  
  
 <span data-ttu-id="a814f-105">Hizmet</span><span class="sxs-lookup"><span data-stu-id="a814f-105">Service</span></span>  
 <span data-ttu-id="a814f-106">Bu uygulayan bir kendi kendini barındıran WCF hizmetidir `ICalculator` arabirim ve kullanarak uç nokta güvenliğini sağlama <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> güvenli oturum ve güvenilir oturum devre dışı.</span><span class="sxs-lookup"><span data-stu-id="a814f-106">This is a self-hosted WCF service that implements the `ICalculator` interface and secures the endpoint using the <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> with secure session and reliable session disabled.</span></span> <span data-ttu-id="a814f-107">Özel bir hizmet tanımlar `SecurityAlgorithmSuite` ileti güvenliği için kullanılacak şifreleme algoritmalarını belirlemek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="a814f-107">The service defines a custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>  
  
 <span data-ttu-id="a814f-108">İstemci</span><span class="sxs-lookup"><span data-stu-id="a814f-108">Client</span></span>  
 <span data-ttu-id="a814f-109">Başarılı kimlik doğrulamasından sonra hizmete erişen bir WCFclient budur.</span><span class="sxs-lookup"><span data-stu-id="a814f-109">This is a WCFclient that accesses the service after successful authentication.</span></span> <span data-ttu-id="a814f-110">Tarafından sunulan işlemleri çağırır `ICalculator` arabirim ve hizmet tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="a814f-110">It invokes the operations exposed by the `ICalculator` interface and implemented by the service.</span></span> <span data-ttu-id="a814f-111">İstemci Ayrıca aynı özel tanımlar `SecurityAlgorithmSuite` ileti güvenliği için kullanılacak şifreleme algoritmalarını belirlemek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="a814f-111">The client also defines the same custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>  
  
### <a name="to-use-this-sample"></a><span data-ttu-id="a814f-112">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="a814f-112">To use this sample</span></span>  
  
1.  <span data-ttu-id="a814f-113">CryptoAgility.sln çözümde açmak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a814f-113">Open the CryptoAgility.sln solution in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="a814f-114">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="a814f-114">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="a814f-115">Açık [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] \WCF\Basic\Security\CryptoAgility\Service\bin dizine gidin ve service.exe sağ tıklayıp seçerek service.exe dosyasını yönetici ayrıcalıklarıyla çalıştırın **yönetici olarak çalıştır**.</span><span class="sxs-lookup"><span data-stu-id="a814f-115">Open [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] and navigate to the \WCF\Basic\Security\CryptoAgility\Service\bin directory and run the service.exe file with administrator privileges by right-clicking service.exe and selecting **Run as administrator**.</span></span>  
  
4.  <span data-ttu-id="a814f-116">\WCF\Basic\Security\CryptoAgility\Client\bin dizinine gidin ve client.exe dosya normal olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="a814f-116">Navigate to \WCF\Basic\Security\CryptoAgility\Client\bin directory and run the client.exe file normally.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a814f-117">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="a814f-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a814f-118">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="a814f-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a814f-119">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="a814f-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a814f-120">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="a814f-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`  
  
## <a name="see-also"></a><span data-ttu-id="a814f-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a814f-121">See Also</span></span>  
 [<span data-ttu-id="a814f-122">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="a814f-122">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
