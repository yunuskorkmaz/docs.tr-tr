---
title: "Yapılandırma Kanal Fabrikası"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b749493-bd8a-4ccb-893e-5948901a1486
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a79a5c4997403f018ba34aea65e4c9fadab29443
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="configuration-channel-factory"></a><span data-ttu-id="d133d-102">Yapılandırma Kanal Fabrikası</span><span class="sxs-lookup"><span data-stu-id="d133d-102">Configuration Channel Factory</span></span>
<span data-ttu-id="d133d-103">Bu örnek kullanımını kapsayan <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span><span class="sxs-lookup"><span data-stu-id="d133d-103">This sample covers the usage of the <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span></span> <span data-ttu-id="d133d-104"><xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> Merkezi Yönetimi sağlayan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci yapılandırması.</span><span class="sxs-lookup"><span data-stu-id="d133d-104">The <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> allows central management of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client configuration.</span></span> <span data-ttu-id="d133d-105">Bu ayrıca yapılandırması seçili veya uygulama etki alanı yükleme sonra saati değişti senaryolarda yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="d133d-105">This can also be useful in scenarios in which configuration is selected or changed after the application domain load time.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="d133d-106">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="d133d-106">Demonstrates</span></span>  
 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>  
  
## <a name="discussion"></a><span data-ttu-id="d133d-107">Tartışma</span><span class="sxs-lookup"><span data-stu-id="d133d-107">Discussion</span></span>  
 <span data-ttu-id="d133d-108">Bu örnek nasıl kullanılacağını göstermektedir <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> varsayılan uygulama yapılandırma dosyası kullanmak zorunda kalmadan bir istemci uygulaması için belirli yapılandırma dosyası eklemek için.</span><span class="sxs-lookup"><span data-stu-id="d133d-108">This sample shows how to use <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> to add a particular configuration file to a client application, without having to use the default application configuration file.</span></span>  
  
 <span data-ttu-id="d133d-109">Örnek iki projeden oluşan.</span><span class="sxs-lookup"><span data-stu-id="d133d-109">The sample consists of two projects.</span></span> <span data-ttu-id="d133d-110">İlk proje istemcilerinden gelen iletileri yanıtlamak için çalışan basit bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="d133d-110">The first project is a simple service that runs to reply to messages coming from the clients.</span></span> <span data-ttu-id="d133d-111">İki derlemeler bir istemci uygulaması ikinci projedir <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> kullanarak nesneleri bir <xref:System.Configuration.ExeConfigurationFileMap> Test.config yapılandırma dosyası için ve bunları hizmetiyle iletişim kurmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="d133d-111">The second project is a client application that builds two <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> objects using a <xref:System.Configuration.ExeConfigurationFileMap> for the Test.config configuration file and uses them to communicate with the service.</span></span> <span data-ttu-id="d133d-112">Her iki istemcinin Test.config içinde belirtilen yapılandırma kullanılarak hizmetiyle iletişim.</span><span class="sxs-lookup"><span data-stu-id="d133d-112">Both clients communicate with the service using the configuration specified in Test.config.</span></span>  
  
 <span data-ttu-id="d133d-113">Aşağıdaki kod, bir istemci uygulaması için özel bir yapılandırma dosyasına ekler.</span><span class="sxs-lookup"><span data-stu-id="d133d-113">The following code adds a custom configuration file to a client application.</span></span>  
  
```  
ExeConfigurationFileMap fileMap = new ExeConfigurationFileMap();  
fileMap.ExeConfigFilename = "Test.config";  
Configuration newConfiguration = ConfigurationManager.OpenMappedExeConfiguration(fileMap, ConfigurationUserLevel.None);  
  
ConfigurationChannelFactory<ICalculatorChannel> factory1 = new ConfigurationChannelFactory<ICalculatorChannel>("endpoint1", newConfiguration, new EndpointAddress("http://localhost:8000/servicemodelsamples/service"));  
ICalculatorChannel client1 = factory1.CreateChannel();  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d133d-114">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="d133d-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d133d-115">Açık [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] yönetici ayrıcalıklarına sahip.</span><span class="sxs-lookup"><span data-stu-id="d133d-115">Open [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] with administrator privileges.</span></span>  
  
2.  <span data-ttu-id="d133d-116">(2 projeleri) ConfigurationChannelFactory çözüme sağ tıklayın ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="d133d-116">Right-click the ConfigurationChannelFactory solution (2 projects) and then select **Properties**.</span></span>  
  
3.  <span data-ttu-id="d133d-117">İçinde **ortak özellikleri**seçin **başlangıç projesi**ve ardından **birden fazla başlangıç projesi**.</span><span class="sxs-lookup"><span data-stu-id="d133d-117">In **Common Properties**, select **Startup Project**, and then click **Multiple startup projects**.</span></span>  
  
4.  <span data-ttu-id="d133d-118">Taşıma **hizmet** ile listenin başına proje **eylemi 'Start'**ve ardından taşıma **istemci** sonra proje **hizmet**projesi de **eylemi 'Start'**, böylece **istemci** proje sonra yürütüldüğünde **hizmet** projesi.</span><span class="sxs-lookup"><span data-stu-id="d133d-118">Move the **Service** project to the beginning of the list, with the **Action ‘Start’**, and then move the **Client** project after the **Service** project, also with the **Action ‘Start’**, so the **Client** project is executed after the **Service** project.</span></span>  
  
5.  <span data-ttu-id="d133d-119">Tıklatın **Tamam**, örneği çalıştırmak için F5'e (veya CTRL + F5'e)'tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="d133d-119">Click **OK**, and then press F5 (or CTRL+F5) to run the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d133d-120">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="d133d-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d133d-121">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d133d-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d133d-122">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="d133d-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d133d-123">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="d133d-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`
