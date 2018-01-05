---
title: WSStreamedHttpBinding
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97ce4d3d-ca6f-45fa-b33b-2429bb84e65b
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7d6259640bae2b4be4fac73883df8945bf1db7ff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="wsstreamedhttpbinding"></a><span data-ttu-id="22bc3-102">WSStreamedHttpBinding</span><span class="sxs-lookup"><span data-stu-id="22bc3-102">WSStreamedHttpBinding</span></span>
<span data-ttu-id="22bc3-103">Örnek, HTTP taşıma kullanıldığında akış senaryoları desteklemek üzere tasarlanmış bir bağlama oluşturun gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="22bc3-103">The sample demonstrates how to create a binding that is designed to support streaming scenarios when the HTTP transport is used.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="22bc3-104">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="22bc3-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="22bc3-105">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="22bc3-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="22bc3-106">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="22bc3-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="22bc3-107">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="22bc3-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="22bc3-108">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="22bc3-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Binding\WSStreamedHttpBinding`  
  
 <span data-ttu-id="22bc3-109">Oluşturun ve yeni bir standart bağlama yapılandırmak için adımlar aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="22bc3-109">The steps to create and configure a new standard binding are as follows.</span></span>  
  
1.  <span data-ttu-id="22bc3-110">Yeni bir standart bağlama oluşturma</span><span class="sxs-lookup"><span data-stu-id="22bc3-110">Create a new standard binding</span></span>  
  
     <span data-ttu-id="22bc3-111">Standart bağlamaları [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] gibi basicHttpBinding ve netTcpBinding arka plandaki aktarım ve kanal yığını belirli gereksinimleri için yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="22bc3-111">The standard bindings in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] such as basicHttpBinding, and netTcpBinding configure the underlying transports and channel stack for specific requirements.</span></span> <span data-ttu-id="22bc3-112">Bu örnekte `WSStreamedHttpBinding` akış desteklemek için kanal yığın yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="22bc3-112">In this sample, `WSStreamedHttpBinding` configures the channel stack to support streaming.</span></span> <span data-ttu-id="22bc3-113">Varsayılan olarak, her iki özellik akış tarafından desteklenmediğinden WS güvenliği ve güvenilir Mesajlaşma kanalı yığına eklenmez.</span><span class="sxs-lookup"><span data-stu-id="22bc3-113">By default, WS-Security and reliable messaging are not added to the channel stack because both features are not supported by streaming.</span></span> <span data-ttu-id="22bc3-114">Yeni bağlamanın sınıfında uygulanır `WSStreamedHttpBinding` , türetilen <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="22bc3-114">The new binding is implemented in the class `WSStreamedHttpBinding` that derives from <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="22bc3-115">`WSStreamedHttpBinding` Aşağıdaki bağlama öğeleri içerir: <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>, <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, ve <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="22bc3-115">The `WSStreamedHttpBinding` contains the following binding elements: <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>, <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, and <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.</span></span> <span data-ttu-id="22bc3-116">Bu sınıf sağladığı bir `CreateBindingElements()` yöntemi aşağıdaki örnek kodda gösterildiği gibi sonuçta elde edilen bağlama yığını yapılandırmak için.</span><span class="sxs-lookup"><span data-stu-id="22bc3-116">The class provides a `CreateBindingElements()` method to configure the resulting binding stack, as shown in the following sample code.</span></span>  
  
    ```  
    public override BindingElementCollection CreateBindingElements()  
    {  
         // return collection of BindingElements  
         BindingElementCollection bindingElements = new BindingElementCollection();  
  
        // the order of binding elements within the collection is important: layered channels are applied in the order included, followed by  
        // the message encoder, and finally the transport at the end  
        if (flowTransactions)  
        {  
            bindingElements.Add(transactionFlow);  
        }  
        bindingElements.Add(textEncoding);  
  
        // add transport (http or https)  
        bindingElements.Add(transport);  
        return bindingElements.Clone();  
    }  
    ```  
  
2.  <span data-ttu-id="22bc3-117">Yapılandırma desteği ekleme</span><span class="sxs-lookup"><span data-stu-id="22bc3-117">Add configuration support</span></span>  
  
     <span data-ttu-id="22bc3-118">Taşıma yapılandırma yoluyla kullanıma sunmak için iki daha fazla sınıf örneği uygulayan —`WSStreamedHttpBindingConfigurationElement` ve `WSStreamedHttpBindingSection`.</span><span class="sxs-lookup"><span data-stu-id="22bc3-118">To expose the transport through configuration the sample implements two more classes—`WSStreamedHttpBindingConfigurationElement` and `WSStreamedHttpBindingSection`.</span></span> <span data-ttu-id="22bc3-119">Sınıf `WSStreamedHttpBindingSection` olan bir <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> kullanıma sunan `WSStreamedHttpBinding` için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yapılandırma sistemi.</span><span class="sxs-lookup"><span data-stu-id="22bc3-119">The class `WSStreamedHttpBindingSection` is a <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> that exposes `WSStreamedHttpBinding` to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] configuration system.</span></span> <span data-ttu-id="22bc3-120">Uygulama toplu temsilci için `WSStreamedHttpBindingConfigurationElement`, den türetilen <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="22bc3-120">The bulk of the implementation is delegated to `WSStreamedHttpBindingConfigurationElement`, which derives from <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span></span> <span data-ttu-id="22bc3-121">Sınıf `WSStreamedHttpBindingConfigurationElement` özelliklerine karşılık gelen özelliklere sahip `WSStreamedHttpBinding`ve her yapılandırma öğesi için bir bağlama eşlemek için işlevleri.</span><span class="sxs-lookup"><span data-stu-id="22bc3-121">The class `WSStreamedHttpBindingConfigurationElement` has properties that correspond to the properties of `WSStreamedHttpBinding`, and functions to map each configuration element to a binding.</span></span>  
  
     <span data-ttu-id="22bc3-122">İşleyici, aşağıdaki bölümde hizmetin yapılandırma dosyasına ekleyerek yapılandırma sistemi ile kaydedin.</span><span class="sxs-lookup"><span data-stu-id="22bc3-122">Register the handler with the configuration system, by adding the following section to the service's configuration file.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <extensions>  
          <bindingExtensions>  
            <add name="wsStreamedHttpBinding" type="Microsoft.ServiceModel.Samples.WSStreamedHttpBindingCollectionElement, WSStreamedHttpBinding, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
          </bindingExtensions>  
        </extensions>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     <span data-ttu-id="22bc3-123">İşleyici serviceModel yapılandırması bölümünden sonra başvurulabilir.</span><span class="sxs-lookup"><span data-stu-id="22bc3-123">The handler can then be referenced from the serviceModel configuration section.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <client>  
          <endpoint  
                    address="https://localhost/servicemodelsamples/service.svc"  
                    bindingConfiguration="Binding"  
                    binding="wsStreamedHttpBinding"  
                    contract="Microsoft.ServiceModel.Samples.IStreamedEchoService"/>  
        </client>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="22bc3-124">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="22bc3-124">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="22bc3-125">Yükleme [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aşağıdaki komutu kullanarak 4.0.</span><span class="sxs-lookup"><span data-stu-id="22bc3-125">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="22bc3-126">Listelenen adımları gerçekleştirildiğinden emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="22bc3-126">Ensure that you have performed the steps listed in [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="22bc3-127">Gerçekleştirmiş emin olun [Internet Information Services (IIS) sunucu sertifikası yükleme yönergeleri](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span><span class="sxs-lookup"><span data-stu-id="22bc3-127">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span></span>  
  
4.  <span data-ttu-id="22bc3-128">Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="22bc3-128">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="22bc3-129">Makineler arası yapılandırmasında örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="22bc3-129">To run the sample in a cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
6.  <span data-ttu-id="22bc3-130">İstemci penceresi görüntülendiğinde, "Örnek.txt" yazın.</span><span class="sxs-lookup"><span data-stu-id="22bc3-130">When the client window displays, type "Sample.txt".</span></span> <span data-ttu-id="22bc3-131">Dizininizde "Örnek.txt Kopyala" bulmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="22bc3-131">You should find a "Copy of Sample.txt" in your directory.</span></span>  
  
## <a name="the-wsstreamedhttpbinding-sample-service"></a><span data-ttu-id="22bc3-132">WSStreamedHttpBinding örnek hizmeti</span><span class="sxs-lookup"><span data-stu-id="22bc3-132">The WSStreamedHttpBinding Sample Service</span></span>  
 <span data-ttu-id="22bc3-133">Kullanan örnek hizmet `WSStreamedHttpBinding` hizmet alt dizinindeki bulunur.</span><span class="sxs-lookup"><span data-stu-id="22bc3-133">The sample service that uses `WSStreamedHttpBinding` is located in the service subdirectory.</span></span> <span data-ttu-id="22bc3-134">Uygulaması `OperationContract` kullanan bir `MemoryStream` döndürmeden önce gelen akıştan ilk tüm verileri almak için `MemoryStream`.</span><span class="sxs-lookup"><span data-stu-id="22bc3-134">The implementation of `OperationContract` uses a `MemoryStream` to first retrieve all data from the incoming stream before returning the `MemoryStream`.</span></span> <span data-ttu-id="22bc3-135">Örnek hizmeti Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="22bc3-135">The sample service is hosted by Internet Information Services (IIS).</span></span>  
  
```  
[ServiceContract]  
public interface IStreamedEchoService  
{  
    [OperationContract]  
    Stream Echo(Stream data);  
}  
  
public class StreamedEchoService : IStreamedEchoService  
{  
    public Stream Echo(Stream data)  
    {  
        MemoryStream dataStorage = new MemoryStream();  
        byte[] byteArray = new byte[8192];  
        int bytesRead = data.Read(byteArray, 0, 8192);  
        while (bytesRead > 0)  
        {  
            dataStorage.Write(byteArray, 0, bytesRead);  
            bytesRead = data.Read(byteArray, 0, 8192);  
        }  
        data.Close();  
        dataStorage.Seek(0, SeekOrigin.Begin);  
  
        return dataStorage;  
    }  
}  
```  
  
## <a name="the-wsstreamedhttpbinding-sample-client"></a><span data-ttu-id="22bc3-136">WSStreamedHttpBinding örnek istemcisi</span><span class="sxs-lookup"><span data-stu-id="22bc3-136">The WSStreamedHttpBinding Sample Client</span></span>  
 <span data-ttu-id="22bc3-137">Hizmetini kullanarak ile kullanılan etkileşim kurmak için istemci `WSStreamedHttpBinding` istemci alt dizininde bulunur.</span><span class="sxs-lookup"><span data-stu-id="22bc3-137">The client that is used to interact with the service using `WSStreamedHttpBinding` is located in the client subdirectory.</span></span> <span data-ttu-id="22bc3-138">Bu örnekte kullanılan sertifikanın Makecert.exe ile oluşturulan bir test sertifikası olduğundan, bir HTTPS adresi https://localhost/servicemodelsamples/service.svc gibi tarayıcınızda erişmeyi denediğinde bir güvenlik uyarısı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="22bc3-138">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert displays when you attempt to access an HTTPS address in your browser such as https://localhost/servicemodelsamples/service.svc.</span></span> <span data-ttu-id="22bc3-139">İzin vermek için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci, yerinde bir test sertifikası ile çalışmak için bazı ek kod güvenlik uyarıyı gizlemek için istemciye eklendi.</span><span class="sxs-lookup"><span data-stu-id="22bc3-139">To allow the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="22bc3-140">Kod ve eşlik eden sınıfı üretim sertifikaları kullanırken gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="22bc3-140">The code and the accompanying class are not required when using production certificates.</span></span>  
  
```  
// WARNING: This code is only required for test certificates such as those created by makecert. It is   
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
## <a name="see-also"></a><span data-ttu-id="22bc3-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="22bc3-141">See Also</span></span>
