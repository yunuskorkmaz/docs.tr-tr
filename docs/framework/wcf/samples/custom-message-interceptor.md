---
title: Özel İleti Kesici
ms.date: 03/30/2017
ms.assetid: 73f20972-53f8-475a-8bfe-c133bfa225b0
ms.openlocfilehash: 5a72a964c571cf68d4b215f4029ff95c52cba0e2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486746"
---
# <a name="custom-message-interceptor"></a><span data-ttu-id="eb301-102">Özel İleti Kesici</span><span class="sxs-lookup"><span data-stu-id="eb301-102">Custom Message Interceptor</span></span>
<span data-ttu-id="eb301-103">Bu örnek, kanal genişletilebilirlik modeli kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="eb301-103">This sample demonstrates the use of the channel extensibility model.</span></span> <span data-ttu-id="eb301-104">Özellikle, kanal fabrikaları ve tüm gelen ve giden iletileri çalışma zamanı yığını olarak belirli bir noktada ele alınması için kanal dinleyicileri oluşturan özel bağlama öğesinin uygulanması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="eb301-104">In particular, it shows how to implement a custom binding element that creates channel factories and channel listeners to intercept all incoming and outgoing messages at a particular point in the run-time stack.</span></span> <span data-ttu-id="eb301-105">Örnek, bir istemci ve sunucu bu özel fabrikaları kullanımını gösteren de içerir.</span><span class="sxs-lookup"><span data-stu-id="eb301-105">The sample also includes a client and server that demonstrate the use of these custom factories.</span></span>  
  
 <span data-ttu-id="eb301-106">Bu örnekte, hem istemci hem de hizmet Konsolu programlar (.exe) var.</span><span class="sxs-lookup"><span data-stu-id="eb301-106">In this sample, both the client and the service are console programs (.exe).</span></span> <span data-ttu-id="eb301-107">Hem de hizmet ve istemci özel bir bağlama öğesi ve onun ilişkili çalışma zamanı nesneleri içeren bir ortak kitaplığı (.dll) kullanın.</span><span class="sxs-lookup"><span data-stu-id="eb301-107">The client and service both make use of a common library (.dll) that contains the custom binding element and its associated run-time objects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eb301-108">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="eb301-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="eb301-109">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="eb301-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="eb301-110">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="eb301-110">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="eb301-111">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="eb301-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="eb301-112">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="eb301-112">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\MessageInterceptor`  
  
 <span data-ttu-id="eb301-113">Örnek kanal çerçevesi kullanarak ve WCF en iyi uygulamaları izleyerek Windows Communication Foundation (WCF) özel katmanlı bir kanal oluşturmak için önerilen yordamı açıklar.</span><span class="sxs-lookup"><span data-stu-id="eb301-113">The sample describes the recommended procedure for creating a custom layered channel in Windows Communication Foundation (WCF), by using the channel framework and following WCF best practices.</span></span> <span data-ttu-id="eb301-114">Özel bir katmanlı kanal oluşturmak için adımlar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="eb301-114">The steps to create a custom layered channel are as follows:</span></span>  
  
1.  <span data-ttu-id="eb301-115">Kanal şekillerinin kanal fabrikası ve kanal dinleyicisi destekleyecek karar verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb301-115">Decide which of the channel shapes your channel factory and channel listener will support.</span></span>  
  
2.  <span data-ttu-id="eb301-116">Kanal fabrikası ve kanal şekillerinizi destekleyen bir kanal dinleyicisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="eb301-116">Create a channel factory and a channel listener that support your channel shapes.</span></span>  
  
3.  <span data-ttu-id="eb301-117">Bir kanal yığınına özel katmanlı kanal ekleyen bir bağlama öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="eb301-117">Add a binding element that adds the custom layered channel to a channel stack.</span></span>  
  
4.  <span data-ttu-id="eb301-118">Yeni bağlama öğesi yapılandırma sistemi için kullanıma sunmak için bir bağlama öğesi uzantısı bölümü ekleyin.</span><span class="sxs-lookup"><span data-stu-id="eb301-118">Add a binding element extension section to expose the new binding element to the configuration system.</span></span>  
  
## <a name="channel-shapes"></a><span data-ttu-id="eb301-119">Kanal şekiller</span><span class="sxs-lookup"><span data-stu-id="eb301-119">Channel Shapes</span></span>  
 <span data-ttu-id="eb301-120">Özel bir katmanlı kanal yazarken ilk adım, hangi şekiller kanal için gerekli olduğuna karar sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="eb301-120">The first step in writing a custom layered channel is to decide which shapes are required for the channel.</span></span> <span data-ttu-id="eb301-121">Aşağıda bize katmanı destekleyen herhangi bir şekil destekliyoruz bizim ileti denetçisi için (örneğin, aşağıda bize katman oluşturabilirsiniz, <xref:System.ServiceModel.Channels.IOutputChannel> ve <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, sonra da kullanıma sunuyoruz <xref:System.ServiceModel.Channels.IOutputChannel> ve <xref:System.ServiceModel.Channels.IDuplexSessionChannel>).</span><span class="sxs-lookup"><span data-stu-id="eb301-121">For our message inspector, we support any shape that the layer below us supports (for example, if the layer below us can build <xref:System.ServiceModel.Channels.IOutputChannel> and <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, then we also expose <xref:System.ServiceModel.Channels.IOutputChannel> and <xref:System.ServiceModel.Channels.IDuplexSessionChannel>).</span></span>  
  
## <a name="channel-factory-and-listener-factory"></a><span data-ttu-id="eb301-122">Kanal fabrikası ve dinleyici fabrikası</span><span class="sxs-lookup"><span data-stu-id="eb301-122">Channel Factory and Listener Factory</span></span>  
 <span data-ttu-id="eb301-123">Sonraki adım özel bir katmanlı kanal yazma uygulaması oluşturmaktır <xref:System.ServiceModel.Channels.IChannelFactory> ve istemci kanallar için <xref:System.ServiceModel.Channels.IChannelListener> hizmet kanalları için.</span><span class="sxs-lookup"><span data-stu-id="eb301-123">The next step in writing a custom layered channel is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels and of <xref:System.ServiceModel.Channels.IChannelListener> for service channels.</span></span>  
  
 <span data-ttu-id="eb301-124">Bu sınıfların bir iç Fabrika ve dinleyici ve temsilci dışındaki tüm `OnCreateChannel` ve `OnAcceptChannel` iç Fabrika ve dinleyici çağrıları.</span><span class="sxs-lookup"><span data-stu-id="eb301-124">These classes take an inner factory and listener, and delegate all but the `OnCreateChannel` and `OnAcceptChannel` calls to the inner factory and listener.</span></span>  
  
```  
class InterceptingChannelFactory<TChannel> : ChannelFactoryBase<TChannel>  
{ ... }  
class InterceptingChannelListener<TChannel> : ListenerFactoryBase<TChannel>  
{ ... }  
```  
  
## <a name="adding-a-binding-element"></a><span data-ttu-id="eb301-125">Bir bağlama öğesi ekleniyor</span><span class="sxs-lookup"><span data-stu-id="eb301-125">Adding a Binding Element</span></span>  
 <span data-ttu-id="eb301-126">Örnek bir özel bağlama öğesi tanımlar: `InterceptingBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="eb301-126">The sample defines a custom binding element: `InterceptingBindingElement`.</span></span> <span data-ttu-id="eb301-127">`InterceptingBindingElement` alan bir `ChannelMessageInterceptor` girdi olarak ve bu kullanır `ChannelMessageInterceptor` aracılığıyla iletileri işlemek için.</span><span class="sxs-lookup"><span data-stu-id="eb301-127">`InterceptingBindingElement` takes a `ChannelMessageInterceptor` as an input, and uses this `ChannelMessageInterceptor` to manipulate messages that pass through it.</span></span> <span data-ttu-id="eb301-128">Bu ortak olmalıdır, yalnızca bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="eb301-128">This is the only class that must be public.</span></span> <span data-ttu-id="eb301-129">Fabrika, dinleyici ve kanalları tüm ortak arabirimlerin çalışma zamanı iç uygulamaları olabilir.</span><span class="sxs-lookup"><span data-stu-id="eb301-129">The factory, listener, and channels can all be internal implementations of the public run-time interfaces.</span></span>  
  
```  
public class InterceptingBindingElement : BindingElement  
```  
  
## <a name="adding-configuration-support"></a><span data-ttu-id="eb301-130">Yapılandırma desteği ekleme</span><span class="sxs-lookup"><span data-stu-id="eb301-130">Adding Configuration Support</span></span>  
 <span data-ttu-id="eb301-131">Bağlama yapılandırması ile tümleştirmek için bir yapılandırma bölümü işleyicisi kitaplığı bir bağlama öğesi uzantısı bölümü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="eb301-131">To integrate with binding configuration, the library defines a configuration section handler as a binding element extension section.</span></span> <span data-ttu-id="eb301-132">İstemci ve sunucu yapılandırma dosyalarını bağlama öğesi uzantısı yapılandırma sistemi ile kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="eb301-132">The client and server configuration files must register the binding element extension with the configuration system.</span></span> <span data-ttu-id="eb301-133">Yapılandırma sistemi için kendi bağlama öğesi kullanıma sunmak istiyorsanız uygulayıcılar, bu sınıftan türetebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb301-133">Implementers that want to expose their binding element to the configuration system can derive from this class.</span></span>  
  
```  
public abstract class InterceptingElement : BindingElementExtensionElement { ... }  
```  
  
## <a name="adding-policy"></a><span data-ttu-id="eb301-134">İlke ekleme</span><span class="sxs-lookup"><span data-stu-id="eb301-134">Adding Policy</span></span>  
 <span data-ttu-id="eb301-135">İlke sistemimiz ile tümleştirmek için `InterceptingBindingElement` biz ilkesi oluşturmak alması gereken sinyal IPolicyExportExtension uygular.</span><span class="sxs-lookup"><span data-stu-id="eb301-135">To integrate with our policy system, `InterceptingBindingElement` implements IPolicyExportExtension to signal that we should participate in generating policy.</span></span> <span data-ttu-id="eb301-136">İçeri aktarma İlkesi oluşturulan bir istemcide desteklemek için kullanıcı, türetilmiş bir sınıf kaydedebilirsiniz `InterceptingBindingElementImporter` ve geçersiz kılma `CreateMessageInterceptor`kendi ilke etkin oluşturmak için () `ChannelMessageInterceptor` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="eb301-136">To support importing policy on a generated client, the user can register a derived class of `InterceptingBindingElementImporter` and override `CreateMessageInterceptor`() to generate their policy-enabled `ChannelMessageInterceptor` class.</span></span>  
  
## <a name="example-droppable-message-inspector"></a><span data-ttu-id="eb301-137">Örnek: Droppable ileti denetçisi</span><span class="sxs-lookup"><span data-stu-id="eb301-137">Example: Droppable Message Inspector</span></span>  
 <span data-ttu-id="eb301-138">Örnekte bulunan örnek uygulamasıdır `ChannelMessageInspector` iletilerini bırakır.</span><span class="sxs-lookup"><span data-stu-id="eb301-138">Included in the sample is an example implementation of `ChannelMessageInspector` which drops messages.</span></span>  
  
```  
class DroppingServerElement : InterceptingElement  
{  
    protected override ChannelMessageInterceptor CreateMessageInterceptor()  
    {  
        return new DroppingServerInterceptor();  
    }  
}  
```  
  
 <span data-ttu-id="eb301-139">Bunu yapılandırmasından aşağıdaki gibi erişebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="eb301-139">You can access it from configuration as follows:</span></span>  
  
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
  
 <span data-ttu-id="eb301-140">İstemci ve sunucu en düşük düzey (yukarıda aktarım düzeyi), çalışma zamanı kanal yığınlarının özel fabrikaları eklemek için bu yeni oluşturulan yapılandırma bölümü kullanın.</span><span class="sxs-lookup"><span data-stu-id="eb301-140">The client and server both use this newly created configuration section to insert the custom factories into the lowest-level of their run-time channel stacks (above the transport level).</span></span>  
  
```xml  
<customBinding>  
  <binding name="sampleBinding">  
    <droppingInterceptor/>  
    <httpTransport/>  
  </binding>  
</customBinding>  
```  
  
 <span data-ttu-id="eb301-141">İstemcinin kullandığı `MessageInterceptor` bile özel bir başlık eklemek için kitaplık numaralı iletileri.</span><span class="sxs-lookup"><span data-stu-id="eb301-141">The client uses the `MessageInterceptor` library to add a custom header to even numbered messages.</span></span> <span data-ttu-id="eb301-142">Öte yandan hizmetin kullandığı `MessageInterceptor` kitaplığını kullanarak bu özel üstbilgi olmayan herhangi bir iletiyi bırak.</span><span class="sxs-lookup"><span data-stu-id="eb301-142">The service on the other hand uses `MessageInterceptor` library to drop any messages that do not have this special header.</span></span>  
  
 <span data-ttu-id="eb301-143">Hizmet ve istemci çalıştırdıktan sonra istemci aşağıdaki çıktıyı görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="eb301-143">You should see the following client output after running the service and then the client.</span></span>  
  
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
  
 <span data-ttu-id="eb301-144">İstemci hizmete 10 farklı Rüzgar hızı raporları, ancak yalnızca yarısını özel üstbilginin onlarla etiketler.</span><span class="sxs-lookup"><span data-stu-id="eb301-144">The client reports 10 different wind speeds to the service, but only tags half of them with the special header.</span></span>  
  
 <span data-ttu-id="eb301-145">Hizmette aşağıdaki çıktıyı görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="eb301-145">On the service, you should see the following output:</span></span>  
  
```  
Press ENTER to exit.  
Dangerous wind detected! Reported speed (90) is greater than 64 kph.  
Dangerous wind detected! Reported speed (70) is greater than 64 kph.  
5 wind speed reports have been received.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="eb301-146">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="eb301-146">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="eb301-147">Yükleme [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aşağıdaki komutu kullanarak 4.0.</span><span class="sxs-lookup"><span data-stu-id="eb301-147">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="eb301-148">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="eb301-148">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="eb301-149">Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="eb301-149">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="eb301-150">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="eb301-150">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="eb301-151">Client.exe çalıştırın ve her iki konsol penceresi çıktısı için izleme Service.exe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="eb301-151">Run Service.exe first then run Client.exe and watch both console windows for output.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb301-152">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="eb301-152">See Also</span></span>
