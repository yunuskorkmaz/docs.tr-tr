---
title: "WCF Güvenliğinde Şifreleme Çevikliği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
caps.latest.revision: "9"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 8b07b23f4428053964fa33150c4300645242f918
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="cryptographic-agility-in-wcf-security"></a><span data-ttu-id="695dc-102">WCF Güvenliğinde Şifreleme Çevikliği</span><span class="sxs-lookup"><span data-stu-id="695dc-102">Cryptographic Agility in WCF Security</span></span>
<span data-ttu-id="695dc-103">Bu örnek, bir şifreleme Çevik uygulamasında sağlamak için bir standart/özel algoritması belirtmek üzere gösterilmiştir bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] istemci ve hizmet.</span><span class="sxs-lookup"><span data-stu-id="695dc-103">This sample shows how to specify in a standard/custom algorithm to provide a cryptographic agile implementation in a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client and service.</span></span> <span data-ttu-id="695dc-104">Örnek aşağıdaki projeleri oluşur:</span><span class="sxs-lookup"><span data-stu-id="695dc-104">The sample is composed of the following projects:</span></span>  
  
 <span data-ttu-id="695dc-105">Hizmet</span><span class="sxs-lookup"><span data-stu-id="695dc-105">Service</span></span>  
 <span data-ttu-id="695dc-106">Kendini barındıran budur [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulayan hizmet `ICalculator` arabirim ve kullanarak uç nokta güvenliğini sağlama <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> güvenli oturum ve güvenilir oturum devre dışı.</span><span class="sxs-lookup"><span data-stu-id="695dc-106">This is a self-hosted [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service that implements the `ICalculator` interface and secures the endpoint using the <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> with secure session and reliable session disabled.</span></span> <span data-ttu-id="695dc-107">Özel bir hizmet tanımlar `SecurityAlgorithmSuite` ileti güvenliği için kullanılacak şifreleme algoritmalarını belirlemek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="695dc-107">The service defines a custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>  
  
 <span data-ttu-id="695dc-108">İstemci</span><span class="sxs-lookup"><span data-stu-id="695dc-108">Client</span></span>  
 <span data-ttu-id="695dc-109">Bu bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]başarılı kimlik doğrulamasından sonra hizmete erişen istemci.</span><span class="sxs-lookup"><span data-stu-id="695dc-109">This is a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]client that accesses the service after successful authentication.</span></span> <span data-ttu-id="695dc-110">Tarafından sunulan işlemleri çağırır `ICalculator` arabirim ve hizmet tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="695dc-110">It invokes the operations exposed by the `ICalculator` interface and implemented by the service.</span></span> <span data-ttu-id="695dc-111">İstemci Ayrıca aynı özel tanımlar `SecurityAlgorithmSuite` ileti güvenliği için kullanılacak şifreleme algoritmalarını belirlemek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="695dc-111">The client also defines the same custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>  
  
### <a name="to-use-this-sample"></a><span data-ttu-id="695dc-112">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="695dc-112">To use this sample</span></span>  
  
1.  <span data-ttu-id="695dc-113">CryptoAgility.sln çözümde açmak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="695dc-113">Open the CryptoAgility.sln solution in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="695dc-114">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="695dc-114">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="695dc-115">Açık [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] \WCF\Basic\Security\CryptoAgility\Service\bin dizine gidin ve service.exe sağ tıklayıp seçerek service.exe dosyasını yönetici ayrıcalıklarıyla çalıştırın **yönetici olarak çalıştır**.</span><span class="sxs-lookup"><span data-stu-id="695dc-115">Open [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] and navigate to the \WCF\Basic\Security\CryptoAgility\Service\bin directory and run the service.exe file with administrator privileges by right-clicking service.exe and selecting **Run as administrator**.</span></span>  
  
4.  <span data-ttu-id="695dc-116">\WCF\Basic\Security\CryptoAgility\Client\bin dizinine gidin ve client.exe dosya normal olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="695dc-116">Navigate to \WCF\Basic\Security\CryptoAgility\Client\bin directory and run the client.exe file normally.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="695dc-117">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="695dc-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="695dc-118">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="695dc-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="695dc-119">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="695dc-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="695dc-120">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="695dc-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`  
  
## <a name="see-also"></a><span data-ttu-id="695dc-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="695dc-121">See Also</span></span>  
 [<span data-ttu-id="695dc-122">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="695dc-122">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
