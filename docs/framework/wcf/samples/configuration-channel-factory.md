---
title: Yapılandırma Kanal Fabrikası
ms.date: 03/30/2017
ms.assetid: 3b749493-bd8a-4ccb-893e-5948901a1486
ms.openlocfilehash: 1f95356b0b473b297b36c7661c849589e9c0d6ef
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43520820"
---
# <a name="configuration-channel-factory"></a><span data-ttu-id="5e541-102">Yapılandırma Kanal Fabrikası</span><span class="sxs-lookup"><span data-stu-id="5e541-102">Configuration Channel Factory</span></span>
<span data-ttu-id="5e541-103">Bu örnek kullanımını kapsayan <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span><span class="sxs-lookup"><span data-stu-id="5e541-103">This sample covers the usage of the <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span></span> <span data-ttu-id="5e541-104"><xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> WCF istemci yapılandırması merkezi yönetilmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="5e541-104">The <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> allows central management of WCF client configuration.</span></span> <span data-ttu-id="5e541-105">Bu ayrıca yapılandırma seçtikten veya uygulama etki alanı yükleme saatinden sonra değiştirildi senaryolarda yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="5e541-105">This can also be useful in scenarios in which configuration is selected or changed after the application domain load time.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="5e541-106">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="5e541-106">Demonstrates</span></span>  
 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>  
  
## <a name="discussion"></a><span data-ttu-id="5e541-107">Tartışma</span><span class="sxs-lookup"><span data-stu-id="5e541-107">Discussion</span></span>  
 <span data-ttu-id="5e541-108">Bu örnek nasıl kullanılacağını gösterir <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> varsayılan uygulama yapılandırma dosyası kullanmak zorunda kalmadan bir istemci uygulama, belirli bir yapılandırma dosyası eklemek için.</span><span class="sxs-lookup"><span data-stu-id="5e541-108">This sample shows how to use <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> to add a particular configuration file to a client application, without having to use the default application configuration file.</span></span>  
  
 <span data-ttu-id="5e541-109">Örnek, iki projeden oluşan.</span><span class="sxs-lookup"><span data-stu-id="5e541-109">The sample consists of two projects.</span></span> <span data-ttu-id="5e541-110">İlk proje istemcilerden gelen iletilere yanıt vermek için çalışan basit bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="5e541-110">The first project is a simple service that runs to reply to messages coming from the clients.</span></span> <span data-ttu-id="5e541-111">İkinci proje iki oluşturan bir istemci uygulamasıdır <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> kullanarak nesneleri bir <xref:System.Configuration.ExeConfigurationFileMap> Test.config yapılandırma dosyası için ve onları hizmetiyle iletişim kurmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="5e541-111">The second project is a client application that builds two <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> objects using a <xref:System.Configuration.ExeConfigurationFileMap> for the Test.config configuration file and uses them to communicate with the service.</span></span> <span data-ttu-id="5e541-112">Her iki istemcinin Test.config içinde belirtilen yapılandırma kullanılarak hizmetiyle iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="5e541-112">Both clients communicate with the service using the configuration specified in Test.config.</span></span>  
  
 <span data-ttu-id="5e541-113">Aşağıdaki kod, bir istemci uygulaması için özel bir yapılandırma dosyasına ekler.</span><span class="sxs-lookup"><span data-stu-id="5e541-113">The following code adds a custom configuration file to a client application.</span></span>  
  
```  
ExeConfigurationFileMap fileMap = new ExeConfigurationFileMap();  
fileMap.ExeConfigFilename = "Test.config";  
Configuration newConfiguration = ConfigurationManager.OpenMappedExeConfiguration(fileMap, ConfigurationUserLevel.None);  
  
ConfigurationChannelFactory<ICalculatorChannel> factory1 = new ConfigurationChannelFactory<ICalculatorChannel>("endpoint1", newConfiguration, new EndpointAddress("http://localhost:8000/servicemodelsamples/service"));  
ICalculatorChannel client1 = factory1.CreateChannel();  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5e541-114">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="5e541-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="5e541-115">Açık [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] yönetici ayrıcalıklarına sahip.</span><span class="sxs-lookup"><span data-stu-id="5e541-115">Open [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] with administrator privileges.</span></span>  
  
2.  <span data-ttu-id="5e541-116">(2 projeler) ConfigurationChannelFactory çözüme sağ tıklayın ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="5e541-116">Right-click the ConfigurationChannelFactory solution (2 projects) and then select **Properties**.</span></span>  
  
3.  <span data-ttu-id="5e541-117">İçinde **ortak özellikler**seçin **başlangıç projesi**ve ardından **birden fazla başlangıç projesi**.</span><span class="sxs-lookup"><span data-stu-id="5e541-117">In **Common Properties**, select **Startup Project**, and then click **Multiple startup projects**.</span></span>  
  
4.  <span data-ttu-id="5e541-118">Taşıma **hizmet** listenin başına proje ile **eylem 'Start'** ve ardından taşıyın **istemci** sonra proje **hizmet**proje ile aynı zamanda **eylem 'Start'**, bu nedenle **istemci** proje sonra yürütülür **hizmet** proje.</span><span class="sxs-lookup"><span data-stu-id="5e541-118">Move the **Service** project to the beginning of the list, with the **Action ‘Start’**, and then move the **Client** project after the **Service** project, also with the **Action ‘Start’**, so the **Client** project is executed after the **Service** project.</span></span>  
  
5.  <span data-ttu-id="5e541-119">Tıklayın **Tamam**ve ardından örneği çalıştırmak için F5'i (veya CTRL + F5) tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="5e541-119">Click **OK**, and then press F5 (or CTRL+F5) to run the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5e541-120">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="5e541-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5e541-121">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="5e541-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5e541-122">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="5e541-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5e541-123">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="5e541-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`
