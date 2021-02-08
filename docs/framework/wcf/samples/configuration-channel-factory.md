---
description: 'Daha fazla bilgi edinin: yapılandırma kanalı fabrikası'
title: Yapılandırma Kanal Fabrikası
ms.date: 03/30/2017
ms.assetid: 3b749493-bd8a-4ccb-893e-5948901a1486
ms.openlocfilehash: 7868f9b9e3a97a67ac513668be09de4d9c5073bf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778418"
---
# <a name="configuration-channel-factory"></a><span data-ttu-id="b1cdd-103">Yapılandırma Kanal Fabrikası</span><span class="sxs-lookup"><span data-stu-id="b1cdd-103">Configuration Channel Factory</span></span>

<span data-ttu-id="b1cdd-104">Bu örnek, kullanımını ele almaktadır <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> .</span><span class="sxs-lookup"><span data-stu-id="b1cdd-104">This sample covers the usage of the <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span></span> <span data-ttu-id="b1cdd-105">, <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> WCF istemci yapılandırmasının merkezi yönetimine izin verir.</span><span class="sxs-lookup"><span data-stu-id="b1cdd-105">The <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> allows central management of WCF client configuration.</span></span> <span data-ttu-id="b1cdd-106">Bu Ayrıca, uygulamanın etki alanı yükleme zamanından sonra yapılandırmanın seçildiği veya değiştiği senaryolarda yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="b1cdd-106">This can also be useful in scenarios in which configuration is selected or changed after the application domain load time.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="b1cdd-107">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="b1cdd-107">Demonstrates</span></span>

 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>

## <a name="discussion"></a><span data-ttu-id="b1cdd-108">Tartışma</span><span class="sxs-lookup"><span data-stu-id="b1cdd-108">Discussion</span></span>

 <span data-ttu-id="b1cdd-109">Bu örnek <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> , varsayılan uygulama yapılandırma dosyasını kullanmak zorunda kalmadan, belirli bir yapılandırma dosyasını istemci uygulamasına eklemek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b1cdd-109">This sample shows how to use <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> to add a particular configuration file to a client application, without having to use the default application configuration file.</span></span>

 <span data-ttu-id="b1cdd-110">Örnek iki projeden oluşur.</span><span class="sxs-lookup"><span data-stu-id="b1cdd-110">The sample consists of two projects.</span></span> <span data-ttu-id="b1cdd-111">İlk proje, istemcilerden gelen iletileri yanıtlamak için çalışan basit bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="b1cdd-111">The first project is a simple service that runs to reply to messages coming from the clients.</span></span> <span data-ttu-id="b1cdd-112">İkinci proje, <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> Test.config yapılandırma dosyası için bir kullanarak iki nesne oluşturan <xref:System.Configuration.ExeConfigurationFileMap> ve hizmeti ile iletişim kurmak için bunları kullanan bir istemci uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="b1cdd-112">The second project is a client application that builds two <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> objects using a <xref:System.Configuration.ExeConfigurationFileMap> for the Test.config configuration file and uses them to communicate with the service.</span></span> <span data-ttu-id="b1cdd-113">Her iki istemci de Test.config belirtilen yapılandırmayı kullanarak hizmetle iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="b1cdd-113">Both clients communicate with the service using the configuration specified in Test.config.</span></span>

 <span data-ttu-id="b1cdd-114">Aşağıdaki kod, bir istemci uygulamasına özel bir yapılandırma dosyası ekler.</span><span class="sxs-lookup"><span data-stu-id="b1cdd-114">The following code adds a custom configuration file to a client application.</span></span>

```csharp
ExeConfigurationFileMap fileMap = new ExeConfigurationFileMap();
fileMap.ExeConfigFilename = "Test.config";
Configuration newConfiguration = ConfigurationManager.OpenMappedExeConfiguration(fileMap, ConfigurationUserLevel.None);

ConfigurationChannelFactory<ICalculatorChannel> factory1 = new ConfigurationChannelFactory<ICalculatorChannel>("endpoint1", newConfiguration, new EndpointAddress("http://localhost:8000/servicemodelsamples/service"));
ICalculatorChannel client1 = factory1.CreateChannel();
```

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b1cdd-115">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="b1cdd-115">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="b1cdd-116">Yönetici ayrıcalıklarıyla Visual Studio 2012 ' i açın.</span><span class="sxs-lookup"><span data-stu-id="b1cdd-116">Open Visual Studio 2012 with administrator privileges.</span></span>

2. <span data-ttu-id="b1cdd-117">ConfigurationChannelFactory çözümüne (2 proje) sağ tıklayın ve ardından **Özellikler**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="b1cdd-117">Right-click the ConfigurationChannelFactory solution (2 projects) and then select **Properties**.</span></span>

3. <span data-ttu-id="b1cdd-118">**Ortak özellikler**' de **Başlangıç projesi**' ni seçin ve ardından **birden fazla başlangıç** projesi ' ne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b1cdd-118">In **Common Properties**, select **Startup Project**, and then click **Multiple startup projects**.</span></span>

4. <span data-ttu-id="b1cdd-119">**Hizmet** **projesini listenin** başına **' Başlat ' eylemiyle** taşıyın ve ardından **' Başlat ' eylemine** sahip **Istemci** projesini **, hizmet projesinden** sonra, bu nedenle **istemci** projesi yürütülür.</span><span class="sxs-lookup"><span data-stu-id="b1cdd-119">Move the **Service** project to the beginning of the list, with the **Action ‘Start’**, and then move the **Client** project after the **Service** project, also with the **Action ‘Start’**, so the **Client** project is executed after the **Service** project.</span></span>

5. <span data-ttu-id="b1cdd-120">**Tamam**' a tıklayın ve ardından örnek çalıştırmak için F5 tuşuna basın (veya CTRL + F5).</span><span class="sxs-lookup"><span data-stu-id="b1cdd-120">Click **OK**, and then press F5 (or CTRL+F5) to run the sample.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b1cdd-121">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="b1cdd-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b1cdd-122">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="b1cdd-122">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="b1cdd-123">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="b1cdd-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b1cdd-124">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="b1cdd-124">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`
