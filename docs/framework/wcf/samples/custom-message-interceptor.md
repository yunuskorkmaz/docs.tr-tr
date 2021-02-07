---
description: 'Daha fazla bilgi edinin: özel Ileti yakalayıcısı'
title: Özel İleti Kesici
ms.date: 03/30/2017
ms.assetid: 73f20972-53f8-475a-8bfe-c133bfa225b0
ms.openlocfilehash: 916e608e9f5bee66c5d2b56304af0255ace5b827
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752476"
---
# <a name="custom-message-interceptor"></a><span data-ttu-id="ad8a1-103">Özel İleti Kesici</span><span class="sxs-lookup"><span data-stu-id="ad8a1-103">Custom Message Interceptor</span></span>

<span data-ttu-id="ad8a1-104">Bu örnek, kanal genişletilebilirlik modelinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ad8a1-104">This sample demonstrates the use of the channel extensibility model.</span></span> <span data-ttu-id="ad8a1-105">Özellikle, çalışma zamanı yığınında belirli bir noktada tüm gelen ve giden iletileri kesmeye yönelik kanal fabrikaları ve kanal dinleyicileri oluşturan özel bir bağlama öğesinin nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ad8a1-105">In particular, it shows how to implement a custom binding element that creates channel factories and channel listeners to intercept all incoming and outgoing messages at a particular point in the run-time stack.</span></span> <span data-ttu-id="ad8a1-106">Örnek ayrıca, bu özel fabrikaların kullanımını gösteren bir istemci ve sunucu içerir.</span><span class="sxs-lookup"><span data-stu-id="ad8a1-106">The sample also includes a client and server that demonstrate the use of these custom factories.</span></span>  
  
 <span data-ttu-id="ad8a1-107">Bu örnekte, hem istemci hem de hizmet konsol programlarıdır (. exe).</span><span class="sxs-lookup"><span data-stu-id="ad8a1-107">In this sample, both the client and the service are console programs (.exe).</span></span> <span data-ttu-id="ad8a1-108">İstemci ve hizmet, özel bağlama öğesini ve ilişkili çalışma zamanı nesnelerini içeren ortak bir kitaplığı (. dll) kullanır.</span><span class="sxs-lookup"><span data-stu-id="ad8a1-108">The client and service both make use of a common library (.dll) that contains the custom binding element and its associated run-time objects.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ad8a1-109">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="ad8a1-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ad8a1-110">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="ad8a1-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ad8a1-111">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="ad8a1-111">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="ad8a1-112">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ad8a1-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ad8a1-113">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="ad8a1-113">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\MessageInterceptor`  
  
 <span data-ttu-id="ad8a1-114">Örnek, kanal çerçevesini ve aşağıdaki WCF en iyi yöntemlerini kullanarak Windows Communication Foundation (WCF) içinde özel bir katmanlı kanal oluşturmak için önerilen yordamı açıklar.</span><span class="sxs-lookup"><span data-stu-id="ad8a1-114">The sample describes the recommended procedure for creating a custom layered channel in Windows Communication Foundation (WCF), by using the channel framework and following WCF best practices.</span></span> <span data-ttu-id="ad8a1-115">Özel katmanlı Kanal oluşturma adımları aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="ad8a1-115">The steps to create a custom layered channel are as follows:</span></span>  
  
1. <span data-ttu-id="ad8a1-116">Kanal fabrikasının ve kanal dinleyicinizin hangi kanal şekillerinde destekleyeceği belirleyin.</span><span class="sxs-lookup"><span data-stu-id="ad8a1-116">Decide which of the channel shapes your channel factory and channel listener will support.</span></span>  
  
2. <span data-ttu-id="ad8a1-117">Kanal fabrikası ve kanal şekillerinizi destekleyen bir kanal dinleyicisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ad8a1-117">Create a channel factory and a channel listener that support your channel shapes.</span></span>  
  
3. <span data-ttu-id="ad8a1-118">Özel katmanlı kanalı bir kanal yığınına ekleyen bir bağlama öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ad8a1-118">Add a binding element that adds the custom layered channel to a channel stack.</span></span>  
  
4. <span data-ttu-id="ad8a1-119">Yeni bağlama öğesini yapılandırma sistemine göstermek için bağlama öğesi uzantısı bölümü ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ad8a1-119">Add a binding element extension section to expose the new binding element to the configuration system.</span></span>  
  
## <a name="channel-shapes"></a><span data-ttu-id="ad8a1-120">Kanal şekilleri</span><span class="sxs-lookup"><span data-stu-id="ad8a1-120">Channel Shapes</span></span>  

 <span data-ttu-id="ad8a1-121">Özel katmanlı kanal yazmanın ilk adımı, kanal için hangi şekillerin gerekli olduğuna karar vermeye yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="ad8a1-121">The first step in writing a custom layered channel is to decide which shapes are required for the channel.</span></span> <span data-ttu-id="ad8a1-122">İleti denetçimiz için, altındaki katmanın desteklediği herhangi bir şekli destekliyoruz (örneğin, ABD altındaki katmanın <xref:System.ServiceModel.Channels.IOutputChannel> ve oluşturup <xref:System.ServiceModel.Channels.IDuplexSessionChannel> , daha sonra da kullanıma sunduğumuz <xref:System.ServiceModel.Channels.IOutputChannel> <xref:System.ServiceModel.Channels.IDuplexSessionChannel> ).</span><span class="sxs-lookup"><span data-stu-id="ad8a1-122">For our message inspector, we support any shape that the layer below us supports (for example, if the layer below us can build <xref:System.ServiceModel.Channels.IOutputChannel> and <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, then we also expose <xref:System.ServiceModel.Channels.IOutputChannel> and <xref:System.ServiceModel.Channels.IDuplexSessionChannel>).</span></span>  
  
## <a name="channel-factory-and-listener-factory"></a><span data-ttu-id="ad8a1-123">Kanal fabrikası ve dinleyici fabrikası</span><span class="sxs-lookup"><span data-stu-id="ad8a1-123">Channel Factory and Listener Factory</span></span>  

 <span data-ttu-id="ad8a1-124">Özel katmanlı kanal yazmanın bir sonraki adımı, <xref:System.ServiceModel.Channels.IChannelFactory> İstemci kanalları ve hizmet kanalları için bir uygulama oluşturmaktır <xref:System.ServiceModel.Channels.IChannelListener> .</span><span class="sxs-lookup"><span data-stu-id="ad8a1-124">The next step in writing a custom layered channel is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels and of <xref:System.ServiceModel.Channels.IChannelListener> for service channels.</span></span>  
  
 <span data-ttu-id="ad8a1-125">Bu sınıflar bir iç fabrika ve dinleyici alır ve tüm, `OnCreateChannel` `OnAcceptChannel` iç fabrika ve dinleyiciye çağrıları hariç tüm bunları devredebilir.</span><span class="sxs-lookup"><span data-stu-id="ad8a1-125">These classes take an inner factory and listener, and delegate all but the `OnCreateChannel` and `OnAcceptChannel` calls to the inner factory and listener.</span></span>  
  
```csharp
class InterceptingChannelFactory<TChannel> : ChannelFactoryBase<TChannel>  
{
    //...
}

class InterceptingChannelListener<TChannel> : ListenerFactoryBase<TChannel>  
{
    //...
}  
```  
  
## <a name="adding-a-binding-element"></a><span data-ttu-id="ad8a1-126">Bağlama öğesi ekleme</span><span class="sxs-lookup"><span data-stu-id="ad8a1-126">Adding a Binding Element</span></span>  

 <span data-ttu-id="ad8a1-127">Örnek, özel bir bağlama öğesi tanımlar: `InterceptingBindingElement` .</span><span class="sxs-lookup"><span data-stu-id="ad8a1-127">The sample defines a custom binding element: `InterceptingBindingElement`.</span></span> <span data-ttu-id="ad8a1-128">`InterceptingBindingElement` bir `ChannelMessageInterceptor` giriş olarak alır ve `ChannelMessageInterceptor` bunu, üzerinden geçen iletileri işlemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="ad8a1-128">`InterceptingBindingElement` takes a `ChannelMessageInterceptor` as an input, and uses this `ChannelMessageInterceptor` to manipulate messages that pass through it.</span></span> <span data-ttu-id="ad8a1-129">Bu, genel olması gereken tek sınıftır.</span><span class="sxs-lookup"><span data-stu-id="ad8a1-129">This is the only class that must be public.</span></span> <span data-ttu-id="ad8a1-130">Fabrika, dinleyici ve kanalların hepsi, genel çalışma zamanı arabirimlerinin iç uygulamaları olabilir.</span><span class="sxs-lookup"><span data-stu-id="ad8a1-130">The factory, listener, and channels can all be internal implementations of the public run-time interfaces.</span></span>  
  
```csharp
public class InterceptingBindingElement : BindingElement
{
}
```  
  
## <a name="adding-configuration-support"></a><span data-ttu-id="ad8a1-131">Yapılandırma desteği ekleme</span><span class="sxs-lookup"><span data-stu-id="ad8a1-131">Adding Configuration Support</span></span>  

 <span data-ttu-id="ad8a1-132">Bağlama yapılandırması ile tümleştirme için, kitaplık bir yapılandırma bölümü işleyicisini bağlama öğesi uzantısı bölümü olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ad8a1-132">To integrate with binding configuration, the library defines a configuration section handler as a binding element extension section.</span></span> <span data-ttu-id="ad8a1-133">İstemci ve sunucu yapılandırma dosyaları, bağlama öğesi uzantısını yapılandırma sistemine kaydetmelidir.</span><span class="sxs-lookup"><span data-stu-id="ad8a1-133">The client and server configuration files must register the binding element extension with the configuration system.</span></span> <span data-ttu-id="ad8a1-134">Bağlama öğelerini yapılandırma sistemine sunmak isteyen uygulayıcılar bu sınıftan türetilebilir.</span><span class="sxs-lookup"><span data-stu-id="ad8a1-134">Implementers that want to expose their binding element to the configuration system can derive from this class.</span></span>  
  
```csharp
public abstract class InterceptingElement : BindingElementExtensionElement
{
    //...
}
```  
  
## <a name="adding-policy"></a><span data-ttu-id="ad8a1-135">Ilke ekleniyor</span><span class="sxs-lookup"><span data-stu-id="ad8a1-135">Adding Policy</span></span>  

 <span data-ttu-id="ad8a1-136">İlke sistemimizi tümleştirmek için, `InterceptingBindingElement` ilke oluşturmaya katılabilmemiz Için IPolicyExportExtension 'ı uygular.</span><span class="sxs-lookup"><span data-stu-id="ad8a1-136">To integrate with our policy system, `InterceptingBindingElement` implements IPolicyExportExtension to signal that we should participate in generating policy.</span></span> <span data-ttu-id="ad8a1-137">Oluşturulan bir istemcide ilke içeri aktarmayı desteklemek için Kullanıcı, `InterceptingBindingElementImporter` İlke etkin sınıfını oluşturmak üzere türetilmiş bir sınıfı kaydedebilir ve geçersiz kılabilir `CreateMessageInterceptor` () `ChannelMessageInterceptor` .</span><span class="sxs-lookup"><span data-stu-id="ad8a1-137">To support importing policy on a generated client, the user can register a derived class of `InterceptingBindingElementImporter` and override `CreateMessageInterceptor`() to generate their policy-enabled `ChannelMessageInterceptor` class.</span></span>  
  
## <a name="example-droppable-message-inspector"></a><span data-ttu-id="ad8a1-138">Örnek: açılan Ileti denetçisi</span><span class="sxs-lookup"><span data-stu-id="ad8a1-138">Example: Droppable Message Inspector</span></span>  

 <span data-ttu-id="ad8a1-139">Örneğe dahil edilen örnek, `ChannelMessageInspector` iletileri bırakılanlar örnek uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="ad8a1-139">Included in the sample is an example implementation of `ChannelMessageInspector` which drops messages.</span></span>  
  
```csharp
class DroppingServerElement : InterceptingElement  
{  
    protected override ChannelMessageInterceptor CreateMessageInterceptor()  
    {  
        return new DroppingServerInterceptor();  
    }  
}  
```  
  
 <span data-ttu-id="ad8a1-140">Bu yapılandırmaya aşağıdaki gibi erişebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ad8a1-140">You can access it from configuration as follows:</span></span>  
  
```xml  
<configuration>  
    ...  
    <system.serviceModel>  
        ...  
        <extensions>  
            <bindingElementExtensions>  
                <add name="droppingInterceptor"
                   type=  
          "Microsoft.ServiceModel.Samples.DroppingServerElement, library"/>  
            </bindingElementExtensions>  
        </extensions>  
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="ad8a1-141">İstemci ve sunucu, bu yeni oluşturulan yapılandırma bölümünü, özel fabrikaları çalışma zamanı kanal yığınlarının en düşük düzeyine (aktarım düzeyinin üzerinde) eklemek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="ad8a1-141">The client and server both use this newly created configuration section to insert the custom factories into the lowest-level of their run-time channel stacks (above the transport level).</span></span>  
  
```xml  
<customBinding>  
  <binding name="sampleBinding">  
    <droppingInterceptor/>  
    <httpTransport/>  
  </binding>  
</customBinding>  
```  
  
 <span data-ttu-id="ad8a1-142">İstemci, `MessageInterceptor` hatta numaralandırılmış iletilere özel bir üst bilgi eklemek için kitaplığı kullanır.</span><span class="sxs-lookup"><span data-stu-id="ad8a1-142">The client uses the `MessageInterceptor` library to add a custom header to even numbered messages.</span></span> <span data-ttu-id="ad8a1-143">Diğer taraftaki hizmet, `MessageInterceptor` Bu özel üst bilgisine sahip olmayan iletileri bırakmak için kitaplığı kullanır.</span><span class="sxs-lookup"><span data-stu-id="ad8a1-143">The service on the other hand uses `MessageInterceptor` library to drop any messages that do not have this special header.</span></span>  
  
 <span data-ttu-id="ad8a1-144">Hizmetini ve ardından istemcisini çalıştırdıktan sonra aşağıdaki istemci çıktısını görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ad8a1-144">You should see the following client output after running the service and then the client.</span></span>  
  
```console  
Reporting the next 10 wind speed  
100 kph  
Server dropped a message.  
90 kph  
80 kph  
Server dropped a message.  
70 kph  
60 kph  
Server dropped a message.  
50 kph  
40 kph  
Server dropped a message.  
30 kph  
20 kph  
Server dropped a message.  
10 kph  
Press ENTER to shut down client  
```  
  
 <span data-ttu-id="ad8a1-145">İstemci, hizmete farklı bir rüzgar hızı bildirir, ancak yalnızca özel üst bilgiyle bu etiketlerin yarısını Etiketler.</span><span class="sxs-lookup"><span data-stu-id="ad8a1-145">The client reports 10 different wind speeds to the service, but only tags half of them with the special header.</span></span>  
  
 <span data-ttu-id="ad8a1-146">Hizmette aşağıdaki çıktıyı görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="ad8a1-146">On the service, you should see the following output:</span></span>  
  
```console  
Press ENTER to exit.  
Dangerous wind detected! Reported speed (90) is greater than 64 kph.  
Dangerous wind detected! Reported speed (70) is greater than 64 kph.  
5 wind speed reports have been received.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ad8a1-147">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="ad8a1-147">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ad8a1-148">Aşağıdaki komutu kullanarak ASP.NET 4,0 ' ü yükler.</span><span class="sxs-lookup"><span data-stu-id="ad8a1-148">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="ad8a1-149">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="ad8a1-149">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="ad8a1-150">Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="ad8a1-150">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="ad8a1-151">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="ad8a1-151">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
5. <span data-ttu-id="ad8a1-152">Service.exe çalıştırın ve ardından Client.exe çalıştırıp çıkış için konsol pencerelerini izleyin.</span><span class="sxs-lookup"><span data-stu-id="ad8a1-152">Run Service.exe first then run Client.exe and watch both console windows for output.</span></span>  
