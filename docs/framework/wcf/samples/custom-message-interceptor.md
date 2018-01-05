---
title: "Özel İleti Kesici"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 73f20972-53f8-475a-8bfe-c133bfa225b0
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: acac4baa5be68d042dd1b0a11d7acfe609169e10
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="custom-message-interceptor"></a><span data-ttu-id="f222b-102">Özel İleti Kesici</span><span class="sxs-lookup"><span data-stu-id="f222b-102">Custom Message Interceptor</span></span>
<span data-ttu-id="f222b-103">Bu örnek kanal genişletilebilirlik modeli kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="f222b-103">This sample demonstrates the use of the channel extensibility model.</span></span> <span data-ttu-id="f222b-104">Özellikle, kanal fabrikaları ve çalışma zamanı yığınında belirli bir noktada tüm gelen ve giden iletileri izlemesine kanal dinleyicileri oluşturur özel bağlama öğesi uygulamak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="f222b-104">In particular, it shows how to implement a custom binding element that creates channel factories and channel listeners to intercept all incoming and outgoing messages at a particular point in the run-time stack.</span></span> <span data-ttu-id="f222b-105">Örnek, bir istemci ve bu özel oluşturucuları kullanımını gösteren sunucu de içerir.</span><span class="sxs-lookup"><span data-stu-id="f222b-105">The sample also includes a client and server that demonstrate the use of these custom factories.</span></span>  
  
 <span data-ttu-id="f222b-106">Bu örnekte, hem istemci hem de hizmet konsol (.exe) programlarıdır.</span><span class="sxs-lookup"><span data-stu-id="f222b-106">In this sample, both the client and the service are console programs (.exe).</span></span> <span data-ttu-id="f222b-107">İstemci ve hizmet hem de özel bağlama öğesi ve ilişkili çalışma zamanı nesnelerini içeren bir ortak kitaplığı (.dll) kullanın.</span><span class="sxs-lookup"><span data-stu-id="f222b-107">The client and service both make use of a common library (.dll) that contains the custom binding element and its associated run-time objects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f222b-108">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="f222b-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f222b-109">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="f222b-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f222b-110">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="f222b-110">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f222b-111">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="f222b-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f222b-112">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="f222b-112">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\MessageInterceptor`  
  
 <span data-ttu-id="f222b-113">Örnek özel bir katmanlı kanalı oluşturmak için önerilen yordamı açıklar [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], kanal çerçevesi kullanarak ve aşağıdaki [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] en iyi uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="f222b-113">The sample describes the recommended procedure for creating a custom layered channel in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], by using the channel framework and following [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] best practices.</span></span> <span data-ttu-id="f222b-114">Özel bir katmanlı kanal oluşturmak için adımlar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="f222b-114">The steps to create a custom layered channel are as follows:</span></span>  
  
1.  <span data-ttu-id="f222b-115">Kanal şekillerin kanal fabrikası ve kanal dinleyicisi destekleyecek karar verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f222b-115">Decide which of the channel shapes your channel factory and channel listener will support.</span></span>  
  
2.  <span data-ttu-id="f222b-116">Kanal fabrikası ve kanal şekiller destekleyen bir kanal dinleyicisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f222b-116">Create a channel factory and a channel listener that support your channel shapes.</span></span>  
  
3.  <span data-ttu-id="f222b-117">Bir kanal yığınına özel katmanlı kanal ekler bir bağlama öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f222b-117">Add a binding element that adds the custom layered channel to a channel stack.</span></span>  
  
4.  <span data-ttu-id="f222b-118">Yapılandırma sistemi için yeni bir bağlama öğesi kullanıma sunmak için bir bağlama öğesi uzantısı bölümü ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f222b-118">Add a binding element extension section to expose the new binding element to the configuration system.</span></span>  
  
## <a name="channel-shapes"></a><span data-ttu-id="f222b-119">Kanal şekiller</span><span class="sxs-lookup"><span data-stu-id="f222b-119">Channel Shapes</span></span>  
 <span data-ttu-id="f222b-120">Özel bir katmanlı kanal yazma ilk adımı, hangi şekillere kanalı gerekli karar vermektir.</span><span class="sxs-lookup"><span data-stu-id="f222b-120">The first step in writing a custom layered channel is to decide which shapes are required for the channel.</span></span> <span data-ttu-id="f222b-121">Bizim ileti denetçisi için desteklediğimiz katmanını bize altındaki destekleyen herhangi bir şekli (örneğin, bize altında katman oluşturabilirsiniz, <xref:System.ServiceModel.Channels.IOutputChannel> ve <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, biz de kullanıma sonra <xref:System.ServiceModel.Channels.IOutputChannel> ve <xref:System.ServiceModel.Channels.IDuplexSessionChannel>).</span><span class="sxs-lookup"><span data-stu-id="f222b-121">For our message inspector, we support any shape that the layer below us supports (for example, if the layer below us can build <xref:System.ServiceModel.Channels.IOutputChannel> and <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, then we also expose <xref:System.ServiceModel.Channels.IOutputChannel> and <xref:System.ServiceModel.Channels.IDuplexSessionChannel>).</span></span>  
  
## <a name="channel-factory-and-listener-factory"></a><span data-ttu-id="f222b-122">Kanal fabrikası ve dinleyici fabrikası</span><span class="sxs-lookup"><span data-stu-id="f222b-122">Channel Factory and Listener Factory</span></span>  
 <span data-ttu-id="f222b-123">Özel bir katmanlı kanal yazma sonraki adım uygulaması oluşturmaktır <xref:System.ServiceModel.Channels.IChannelFactory> ve istemci kanallar için <xref:System.ServiceModel.Channels.IChannelListener> hizmet kanalları.</span><span class="sxs-lookup"><span data-stu-id="f222b-123">The next step in writing a custom layered channel is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels and of <xref:System.ServiceModel.Channels.IChannelListener> for service channels.</span></span>  
  
 <span data-ttu-id="f222b-124">Bu sınıfların bir iç Fabrika ve dinleyici gerçekleştirin ve temsilci dışındaki tüm `OnCreateChannel` ve `OnAcceptChannel` iç Fabrika ve dinleyici çağrıları.</span><span class="sxs-lookup"><span data-stu-id="f222b-124">These classes take an inner factory and listener, and delegate all but the `OnCreateChannel` and `OnAcceptChannel` calls to the inner factory and listener.</span></span>  
  
```  
class InterceptingChannelFactory<TChannel> : ChannelFactoryBase<TChannel>  
{ ... }  
class InterceptingChannelListener<TChannel> : ListenerFactoryBase<TChannel>  
{ ... }  
```  
  
## <a name="adding-a-binding-element"></a><span data-ttu-id="f222b-125">Bir bağlama öğesi ekleme</span><span class="sxs-lookup"><span data-stu-id="f222b-125">Adding a Binding Element</span></span>  
 <span data-ttu-id="f222b-126">Özel bağlama öğesi örneği tanımlar: `InterceptingBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="f222b-126">The sample defines a custom binding element: `InterceptingBindingElement`.</span></span> <span data-ttu-id="f222b-127">`InterceptingBindingElement`alan bir `ChannelMessageInterceptor` bir girdi olarak ve bu kullanır `ChannelMessageInterceptor` üzerinden geçirmek iletileri işlemek için.</span><span class="sxs-lookup"><span data-stu-id="f222b-127">`InterceptingBindingElement` takes a `ChannelMessageInterceptor` as an input, and uses this `ChannelMessageInterceptor` to manipulate messages that pass through it.</span></span> <span data-ttu-id="f222b-128">Genel tek sınıftır.</span><span class="sxs-lookup"><span data-stu-id="f222b-128">This is the only class that must be public.</span></span> <span data-ttu-id="f222b-129">Fabrika, dinleyiciyi ve kanallar tüm ortak çalışma zamanı arabirimlerin dahili uygulamalardan olabilir.</span><span class="sxs-lookup"><span data-stu-id="f222b-129">The factory, listener, and channels can all be internal implementations of the public run-time interfaces.</span></span>  
  
```  
public class InterceptingBindingElement : BindingElement  
```  
  
## <a name="adding-configuration-support"></a><span data-ttu-id="f222b-130">Yapılandırma desteği ekleme</span><span class="sxs-lookup"><span data-stu-id="f222b-130">Adding Configuration Support</span></span>  
 <span data-ttu-id="f222b-131">Bağlama yapılandırması ile tümleştirmek için kitaplık yapılandırma bölümü işleyicisi bağlama öğesi uzantısı bölüm olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f222b-131">To integrate with binding configuration, the library defines a configuration section handler as a binding element extension section.</span></span> <span data-ttu-id="f222b-132">İstemci ve sunucu yapılandırma dosyaları bağlama öğesi uzantısı yapılandırma sistemi ile kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f222b-132">The client and server configuration files must register the binding element extension with the configuration system.</span></span> <span data-ttu-id="f222b-133">Yapılandırma sistemi için kendi bağlama öğesi kullanıma sunmak istediğiniz Implementers bu sınıftan türeyen.</span><span class="sxs-lookup"><span data-stu-id="f222b-133">Implementers that want to expose their binding element to the configuration system can derive from this class.</span></span>  
  
```  
public abstract class InterceptingElement : BindingElementExtensionElement { ... }  
```  
  
## <a name="adding-policy"></a><span data-ttu-id="f222b-134">İlke ekleme</span><span class="sxs-lookup"><span data-stu-id="f222b-134">Adding Policy</span></span>  
 <span data-ttu-id="f222b-135">İlke sistemimizde ile tümleştirmek için `InterceptingBindingElement` biz ilkesi oluşturma alması gereken sinyal IPolicyExportExtension uygular.</span><span class="sxs-lookup"><span data-stu-id="f222b-135">To integrate with our policy system, `InterceptingBindingElement` implements IPolicyExportExtension to signal that we should participate in generating policy.</span></span> <span data-ttu-id="f222b-136">İçeri aktarma İlkesi oluşturulan bir istemcide desteklemek için kullanıcı, türetilmiş bir sınıf kaydedebilirsiniz `InterceptingBindingElementImporter` ve geçersiz kılma `CreateMessageInterceptor`kendi ilke etkinleştirilmiş oluşturmak için () `ChannelMessageInterceptor` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f222b-136">To support importing policy on a generated client, the user can register a derived class of `InterceptingBindingElementImporter` and override `CreateMessageInterceptor`() to generate their policy-enabled `ChannelMessageInterceptor` class.</span></span>  
  
## <a name="example-droppable-message-inspector"></a><span data-ttu-id="f222b-137">Örnek: Droppable ileti denetçisi</span><span class="sxs-lookup"><span data-stu-id="f222b-137">Example: Droppable Message Inspector</span></span>  
 <span data-ttu-id="f222b-138">Aşağıdaki örnekte dahil bir örnek uygulamasıdır `ChannelMessageInspector` iletilerini bırakır.</span><span class="sxs-lookup"><span data-stu-id="f222b-138">Included in the sample is an example implementation of `ChannelMessageInspector` which drops messages.</span></span>  
  
```  
class DroppingServerElement : InterceptingElement  
{  
    protected override ChannelMessageInterceptor CreateMessageInterceptor()  
    {  
        return new DroppingServerInterceptor();  
    }  
}  
```  
  
 <span data-ttu-id="f222b-139">Yapılandırmasından gibi erişebildiğinizi:</span><span class="sxs-lookup"><span data-stu-id="f222b-139">You can access it from configuration as follows:</span></span>  
  
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
  
 <span data-ttu-id="f222b-140">İstemci ve sunucu kendi çalışma zamanı kanal yığınları (yukarıda aktarım düzeyi) en düşük-düzeyi özel oluşturucuları eklemek için bu yeni oluşturulan yapılandırma bölümü kullanın.</span><span class="sxs-lookup"><span data-stu-id="f222b-140">The client and server both use this newly created configuration section to insert the custom factories into the lowest-level of their run-time channel stacks (above the transport level).</span></span>  
  
```xml  
<customBinding>  
  <binding name="sampleBinding">  
    <droppingInterceptor/>  
    <httpTransport/>  
  </binding>  
</customBinding>  
```  
  
 <span data-ttu-id="f222b-141">İstemcinin kullandığı `MessageInterceptor` özel bir üstbilgisi bile eklemek için kitaplık numaralı iletileri.</span><span class="sxs-lookup"><span data-stu-id="f222b-141">The client uses the `MessageInterceptor` library to add a custom header to even numbered messages.</span></span> <span data-ttu-id="f222b-142">Öte yandan hizmetin kullandığı `MessageInterceptor` kitaplığı bu özel üstbilgi olmayan herhangi bir iletisi bırakın.</span><span class="sxs-lookup"><span data-stu-id="f222b-142">The service on the other hand uses `MessageInterceptor` library to drop any messages that do not have this special header.</span></span>  
  
 <span data-ttu-id="f222b-143">Hizmet ve istemci çalıştırdıktan sonra aşağıdaki istemci çıktı görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f222b-143">You should see the following client output after running the service and then the client.</span></span>  
  
```  
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
  
 <span data-ttu-id="f222b-144">İstemci hizmete 10 farklı Rüzgar hızı raporlar, ancak yalnızca özel üstbilgi bunlarla yarısı etiketler.</span><span class="sxs-lookup"><span data-stu-id="f222b-144">The client reports 10 different wind speeds to the service, but only tags half of them with the special header.</span></span>  
  
 <span data-ttu-id="f222b-145">Hizmette şu çıktı görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="f222b-145">On the service, you should see the following output:</span></span>  
  
```  
Press ENTER to exit.  
Dangerous wind detected! Reported speed (90) is greater than 64 kph.  
Dangerous wind detected! Reported speed (70) is greater than 64 kph.  
5 wind speed reports have been received.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f222b-146">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="f222b-146">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="f222b-147">Yükleme [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aşağıdaki komutu kullanarak 4.0.</span><span class="sxs-lookup"><span data-stu-id="f222b-147">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="f222b-148">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f222b-148">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="f222b-149">Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f222b-149">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="f222b-150">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f222b-150">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="f222b-151">Client.exe çalıştırın ve her iki konsol penceresi çıktısı için izleme Service.exe önce çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f222b-151">Run Service.exe first then run Client.exe and watch both console windows for output.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f222b-152">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f222b-152">See Also</span></span>
