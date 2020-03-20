---
title: Yapılandırma Kanal Fabrikası
ms.date: 03/30/2017
ms.assetid: 3b749493-bd8a-4ccb-893e-5948901a1486
ms.openlocfilehash: 0f00ba5e217420fe416100071d380e413c3df118
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183943"
---
# <a name="configuration-channel-factory"></a><span data-ttu-id="f8a58-102">Yapılandırma Kanal Fabrikası</span><span class="sxs-lookup"><span data-stu-id="f8a58-102">Configuration Channel Factory</span></span>
<span data-ttu-id="f8a58-103">Bu örnek, <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>..</span><span class="sxs-lookup"><span data-stu-id="f8a58-103">This sample covers the usage of the <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span></span> <span data-ttu-id="f8a58-104">WCF <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> istemci yapılandırmasının merkezi yönetimine izin verir.</span><span class="sxs-lookup"><span data-stu-id="f8a58-104">The <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> allows central management of WCF client configuration.</span></span> <span data-ttu-id="f8a58-105">Bu, uygulama etki alanı yükleme süresinden sonra yapılandırmanın seçildiği veya değiştirildiği senaryolarda da yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="f8a58-105">This can also be useful in scenarios in which configuration is selected or changed after the application domain load time.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="f8a58-106">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="f8a58-106">Demonstrates</span></span>
 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>

## <a name="discussion"></a><span data-ttu-id="f8a58-107">Tartışma</span><span class="sxs-lookup"><span data-stu-id="f8a58-107">Discussion</span></span>
 <span data-ttu-id="f8a58-108">Bu örnek, varsayılan <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> uygulama yapılandırma dosyasını kullanmak zorunda kalmadan, istemci uygulamasına belirli bir yapılandırma dosyası eklemek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f8a58-108">This sample shows how to use <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> to add a particular configuration file to a client application, without having to use the default application configuration file.</span></span>

 <span data-ttu-id="f8a58-109">Örnek iki projeden oluşur.</span><span class="sxs-lookup"><span data-stu-id="f8a58-109">The sample consists of two projects.</span></span> <span data-ttu-id="f8a58-110">İlk proje, istemcilerden gelen iletileri yanıtlamak için çalışan basit bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="f8a58-110">The first project is a simple service that runs to reply to messages coming from the clients.</span></span> <span data-ttu-id="f8a58-111">İkinci proje, Test.config yapılandırma <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> dosyası için <xref:System.Configuration.ExeConfigurationFileMap> bir kullanarak iki nesne oluşturan ve bunları hizmetle iletişim kurmak için kullanan bir istemci uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="f8a58-111">The second project is a client application that builds two <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> objects using a <xref:System.Configuration.ExeConfigurationFileMap> for the Test.config configuration file and uses them to communicate with the service.</span></span> <span data-ttu-id="f8a58-112">Her iki istemci de Test.config'de belirtilen yapılandırmayı kullanarak hizmetle iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="f8a58-112">Both clients communicate with the service using the configuration specified in Test.config.</span></span>

 <span data-ttu-id="f8a58-113">Aşağıdaki kod istemci uygulamasına özel bir yapılandırma dosyası ekler.</span><span class="sxs-lookup"><span data-stu-id="f8a58-113">The following code adds a custom configuration file to a client application.</span></span>

```csharp
ExeConfigurationFileMap fileMap = new ExeConfigurationFileMap();
fileMap.ExeConfigFilename = "Test.config";
Configuration newConfiguration = ConfigurationManager.OpenMappedExeConfiguration(fileMap, ConfigurationUserLevel.None);

ConfigurationChannelFactory<ICalculatorChannel> factory1 = new ConfigurationChannelFactory<ICalculatorChannel>("endpoint1", newConfiguration, new EndpointAddress("http://localhost:8000/servicemodelsamples/service"));
ICalculatorChannel client1 = factory1.CreateChannel();
```

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f8a58-114">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="f8a58-114">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="f8a58-115">Yönetici ayrıcalıkları ile Visual Studio 2012'yi açın.</span><span class="sxs-lookup"><span data-stu-id="f8a58-115">Open Visual Studio 2012 with administrator privileges.</span></span>

2. <span data-ttu-id="f8a58-116">ConfigurationChannelFactory çözümünü (2 proje) sağ tıklatın ve ardından **Özellikler'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="f8a58-116">Right-click the ConfigurationChannelFactory solution (2 projects) and then select **Properties**.</span></span>

3. <span data-ttu-id="f8a58-117">**Ortak**Özellikler'de, **Başlangıç Projesi'ni**seçin ve ardından **Birden Çok Başlangıç projesi'ni**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="f8a58-117">In **Common Properties**, select **Startup Project**, and then click **Multiple startup projects**.</span></span>

4. <span data-ttu-id="f8a58-118">**Hizmet** projesini, **'Başlat'** eylemiyle listenin başına taşıyın ve Hizmet projesinden sonra Da **bir** de **Eylem 'Başlat'** ile **Istemci** projesini taşıyın, böylece **İstemci** projesi **Hizmet** projesinden sonra yürütülür.</span><span class="sxs-lookup"><span data-stu-id="f8a58-118">Move the **Service** project to the beginning of the list, with the **Action ‘Start’**, and then move the **Client** project after the **Service** project, also with the **Action ‘Start’**, so the **Client** project is executed after the **Service** project.</span></span>

5. <span data-ttu-id="f8a58-119">**Tamam'ı**tıklatın ve ardından örneği çalıştırmak için F5 (veya CTRL+F5) tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="f8a58-119">Click **OK**, and then press F5 (or CTRL+F5) to run the sample.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f8a58-120">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="f8a58-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f8a58-121">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="f8a58-121">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="f8a58-122">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="f8a58-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f8a58-123">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="f8a58-123">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`
