---
title: WSStreamedHttpBinding
ms.date: 03/30/2017
ms.assetid: 97ce4d3d-ca6f-45fa-b33b-2429bb84e65b
ms.openlocfilehash: f771886192e85cc7e34f0ace4fd95ca04bdb89c9
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881480"
---
# <a name="wsstreamedhttpbinding"></a><span data-ttu-id="667cc-102">WSStreamedHttpBinding</span><span class="sxs-lookup"><span data-stu-id="667cc-102">WSStreamedHttpBinding</span></span>
<span data-ttu-id="667cc-103">Örnek HTTP aktarımı kullanıldığında akış senaryoları desteklemek için tasarlanan bir bağlama oluşturma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="667cc-103">The sample demonstrates how to create a binding that is designed to support streaming scenarios when the HTTP transport is used.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="667cc-104">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="667cc-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="667cc-105">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="667cc-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="667cc-106">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="667cc-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="667cc-107">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="667cc-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="667cc-108">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="667cc-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Binding\WSStreamedHttpBinding`  
  
 <span data-ttu-id="667cc-109">Oluşturma ve yeni bir standart bağlama yapılandırma adımları aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="667cc-109">The steps to create and configure a new standard binding are as follows.</span></span>  
  
1. <span data-ttu-id="667cc-110">Yeni standart bir bağlama oluşturma</span><span class="sxs-lookup"><span data-stu-id="667cc-110">Create a new standard binding</span></span>  
  
     <span data-ttu-id="667cc-111">Windows Communication Foundation (WCF) basicHttpBinding ve netTcpBinding gibi standart bağlamaları temel alınan aktarımları ve kanal yığınında belirli gereksinimleri için yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="667cc-111">The standard bindings in Windows Communication Foundation (WCF) such as basicHttpBinding, and netTcpBinding configure the underlying transports and channel stack for specific requirements.</span></span> <span data-ttu-id="667cc-112">Bu örnekte `WSStreamedHttpBinding` akış desteklemek için kanal yığın yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="667cc-112">In this sample, `WSStreamedHttpBinding` configures the channel stack to support streaming.</span></span> <span data-ttu-id="667cc-113">Varsayılan olarak, her iki özellik, akış tarafından desteklenmediği için WS-güvenlik ve güvenilir Mesajlaşma kanalı yığına eklenmez.</span><span class="sxs-lookup"><span data-stu-id="667cc-113">By default, WS-Security and reliable messaging are not added to the channel stack because both features are not supported by streaming.</span></span> <span data-ttu-id="667cc-114">Yeni bağlamanın sınıfta uygulandığını `WSStreamedHttpBinding` türetilen <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="667cc-114">The new binding is implemented in the class `WSStreamedHttpBinding` that derives from <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="667cc-115">`WSStreamedHttpBinding` Aşağıdaki bağlama öğeleri içerir: <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>, <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, ve <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="667cc-115">The `WSStreamedHttpBinding` contains the following binding elements: <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>, <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, and <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.</span></span> <span data-ttu-id="667cc-116">Sağlar sınıfını bir `CreateBindingElements()` aşağıdaki örnek kodda gösterildiği gibi ortaya çıkan bağlama yığını yapılandırmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="667cc-116">The class provides a `CreateBindingElements()` method to configure the resulting binding stack, as shown in the following sample code.</span></span>  
  
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
  
2. <span data-ttu-id="667cc-117">Yapılandırma desteği eklendi</span><span class="sxs-lookup"><span data-stu-id="667cc-117">Add configuration support</span></span>  
  
     <span data-ttu-id="667cc-118">Taşıma yapılandırma aracılığıyla kullanıma sunmak için iki daha fazla sınıf örneği uygular —`WSStreamedHttpBindingConfigurationElement` ve `WSStreamedHttpBindingSection`.</span><span class="sxs-lookup"><span data-stu-id="667cc-118">To expose the transport through configuration the sample implements two more classes—`WSStreamedHttpBindingConfigurationElement` and `WSStreamedHttpBindingSection`.</span></span> <span data-ttu-id="667cc-119">Sınıf `WSStreamedHttpBindingSection` olduğu bir <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> kullanıma sunan `WSStreamedHttpBinding` WCF yapılandırma sistemi için.</span><span class="sxs-lookup"><span data-stu-id="667cc-119">The class `WSStreamedHttpBindingSection` is a <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> that exposes `WSStreamedHttpBinding` to the WCF configuration system.</span></span> <span data-ttu-id="667cc-120">Toplu uygulama için temsilci `WSStreamedHttpBindingConfigurationElement`, öğesinden türetildiğini <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="667cc-120">The bulk of the implementation is delegated to `WSStreamedHttpBindingConfigurationElement`, which derives from <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span></span> <span data-ttu-id="667cc-121">Sınıf `WSStreamedHttpBindingConfigurationElement` özelliklerine karşılık gelen özelliklerle sahip `WSStreamedHttpBinding`ve her yapılandırma öğesi için bir bağlama eşlemek için işlev.</span><span class="sxs-lookup"><span data-stu-id="667cc-121">The class `WSStreamedHttpBindingConfigurationElement` has properties that correspond to the properties of `WSStreamedHttpBinding`, and functions to map each configuration element to a binding.</span></span>  
  
     <span data-ttu-id="667cc-122">İşleyici, aşağıdaki bölümde bu hizmetin yapılandırma dosyasına ekleyerek yapılandırma sistemi ile kaydedin.</span><span class="sxs-lookup"><span data-stu-id="667cc-122">Register the handler with the configuration system, by adding the following section to the service's configuration file.</span></span>  
  
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
  
     <span data-ttu-id="667cc-123">İşleyici serviceModel Yapılandırma bölümünden sonra başvurulabilir.</span><span class="sxs-lookup"><span data-stu-id="667cc-123">The handler can then be referenced from the serviceModel configuration section.</span></span>  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="667cc-124">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="667cc-124">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="667cc-125">ASP.NET 4. 0 aşağıdaki komutu kullanarak yükleyin.</span><span class="sxs-lookup"><span data-stu-id="667cc-125">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="667cc-126">Listelenen adımları gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="667cc-126">Ensure that you have performed the steps listed in [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="667cc-127">Gerçekleştirdiğinizden emin olmak [Internet Information Services (IIS) sunucu sertifikası yükleme yönergeleri](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span><span class="sxs-lookup"><span data-stu-id="667cc-127">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span></span>  
  
4. <span data-ttu-id="667cc-128">Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="667cc-128">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
5. <span data-ttu-id="667cc-129">Çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="667cc-129">To run the sample in a cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
6. <span data-ttu-id="667cc-130">İstemci penceresi görüntülendiğinde, "Örnek.txt" yazın.</span><span class="sxs-lookup"><span data-stu-id="667cc-130">When the client window displays, type "Sample.txt".</span></span> <span data-ttu-id="667cc-131">Dizininizde "Örnek.txt Kopyala" bulmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="667cc-131">You should find a "Copy of Sample.txt" in your directory.</span></span>  
  
## <a name="the-wsstreamedhttpbinding-sample-service"></a><span data-ttu-id="667cc-132">WSStreamedHttpBinding örnek hizmeti</span><span class="sxs-lookup"><span data-stu-id="667cc-132">The WSStreamedHttpBinding Sample Service</span></span>  
 <span data-ttu-id="667cc-133">Kullanan örnek hizmet `WSStreamedHttpBinding` hizmet alt dizinindeki yer alır.</span><span class="sxs-lookup"><span data-stu-id="667cc-133">The sample service that uses `WSStreamedHttpBinding` is located in the service subdirectory.</span></span> <span data-ttu-id="667cc-134">Uygulamasını `OperationContract` kullanan bir `MemoryStream` döndürmeden önce gelen akıştan önce tüm verileri almak için `MemoryStream`.</span><span class="sxs-lookup"><span data-stu-id="667cc-134">The implementation of `OperationContract` uses a `MemoryStream` to first retrieve all data from the incoming stream before returning the `MemoryStream`.</span></span> <span data-ttu-id="667cc-135">Örnek hizmeti Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="667cc-135">The sample service is hosted by Internet Information Services (IIS).</span></span>  
  
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
  
## <a name="the-wsstreamedhttpbinding-sample-client"></a><span data-ttu-id="667cc-136">WSStreamedHttpBinding örnek istemci</span><span class="sxs-lookup"><span data-stu-id="667cc-136">The WSStreamedHttpBinding Sample Client</span></span>  
 <span data-ttu-id="667cc-137">Hizmeti kullanmaya kullanılan etkileşim kurmak için istemci `WSStreamedHttpBinding` istemci alt dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="667cc-137">The client that is used to interact with the service using `WSStreamedHttpBinding` is located in the client subdirectory.</span></span> <span data-ttu-id="667cc-138">Bu örnekte kullanılan sertifika Makecert.exe ile oluşturulan bir test sertifikası olduğundan, tarayıcınızda bir HTTPS adresi gibi erişmeye çalıştığınızda bir güvenlik uyarısı görüntüler https://localhost/servicemodelsamples/service.svc.</span><span class="sxs-lookup"><span data-stu-id="667cc-138">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert displays when you attempt to access an HTTPS address in your browser such as https://localhost/servicemodelsamples/service.svc.</span></span> <span data-ttu-id="667cc-139">Yerinde bir test sertifikası ile çalışmak için WCF istemcisini izin vermek için güvenlik uyarıyı gizlemek için istemci için bazı ek kod eklendi.</span><span class="sxs-lookup"><span data-stu-id="667cc-139">To allow the WCF client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="667cc-140">Kod ve eşlik eden sınıfı üretim sertifikaları kullanırken gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="667cc-140">The code and the accompanying class are not required when using production certificates.</span></span>  
  
```  
// WARNING: This code is only required for test certificates such as those created by makecert. It is   
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
