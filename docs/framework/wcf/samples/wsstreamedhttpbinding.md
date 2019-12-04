---
title: WSStreamedHttpBinding
ms.date: 03/30/2017
ms.assetid: 97ce4d3d-ca6f-45fa-b33b-2429bb84e65b
ms.openlocfilehash: 36b4db5270205aec55ad52db40500c8d434a1560
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714545"
---
# <a name="wsstreamedhttpbinding"></a><span data-ttu-id="24d98-102">WSStreamedHttpBinding</span><span class="sxs-lookup"><span data-stu-id="24d98-102">WSStreamedHttpBinding</span></span>

<span data-ttu-id="24d98-103">Örnek, HTTP taşıması kullanıldığında akış senaryolarını destekleyecek şekilde tasarlanan bir bağlamanın nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="24d98-103">The sample demonstrates how to create a binding that is designed to support streaming scenarios when the HTTP transport is used.</span></span>

> [!NOTE]
> <span data-ttu-id="24d98-104">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="24d98-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="24d98-105">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="24d98-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="24d98-106">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="24d98-106">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="24d98-107">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="24d98-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="24d98-108">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="24d98-108">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Binding\WSStreamedHttpBinding`

 <span data-ttu-id="24d98-109">Yeni bir standart bağlama oluşturma ve yapılandırma adımları aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="24d98-109">The steps to create and configure a new standard binding are as follows.</span></span>

1. <span data-ttu-id="24d98-110">Yeni bir standart bağlama oluştur</span><span class="sxs-lookup"><span data-stu-id="24d98-110">Create a new standard binding</span></span>

    <span data-ttu-id="24d98-111">BasicHttpBinding ve netTcpBinding gibi Windows Communication Foundation (WCF) içindeki standart bağlamalar, belirli gereksinimler için temel taşımaları ve kanal yığınını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="24d98-111">The standard bindings in Windows Communication Foundation (WCF) such as basicHttpBinding, and netTcpBinding configure the underlying transports and channel stack for specific requirements.</span></span> <span data-ttu-id="24d98-112">Bu örnekte `WSStreamedHttpBinding` kanal yığınını akışı destekleyecek şekilde yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="24d98-112">In this sample, `WSStreamedHttpBinding` configures the channel stack to support streaming.</span></span> <span data-ttu-id="24d98-113">Varsayılan olarak, WS-Security ve güvenilir mesajlaşma, her iki özellik de akış tarafından desteklenmediğinden kanal yığınına eklenmez.</span><span class="sxs-lookup"><span data-stu-id="24d98-113">By default, WS-Security and reliable messaging are not added to the channel stack because both features are not supported by streaming.</span></span> <span data-ttu-id="24d98-114">Yeni bağlama, <xref:System.ServiceModel.Channels.Binding>türetilen sınıf `WSStreamedHttpBinding` uygulanır.</span><span class="sxs-lookup"><span data-stu-id="24d98-114">The new binding is implemented in the class `WSStreamedHttpBinding` that derives from <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="24d98-115">`WSStreamedHttpBinding` aşağıdaki bağlama öğelerini içerir: <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>, <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>ve <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="24d98-115">The `WSStreamedHttpBinding` contains the following binding elements: <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>, <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, and <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.</span></span> <span data-ttu-id="24d98-116">Sınıfı, aşağıdaki örnek kodda gösterildiği gibi, sonuçta elde edilen bağlama yığınını yapılandırmak için bir `CreateBindingElements()` yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="24d98-116">The class provides a `CreateBindingElements()` method to configure the resulting binding stack, as shown in the following sample code.</span></span>

    ```csharp
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

2. <span data-ttu-id="24d98-117">Yapılandırma desteği ekle</span><span class="sxs-lookup"><span data-stu-id="24d98-117">Add configuration support</span></span>

    <span data-ttu-id="24d98-118">Aktarımı yapılandırma yoluyla göstermek için örnek iki sınıf daha uygular —`WSStreamedHttpBindingConfigurationElement` ve `WSStreamedHttpBindingSection`.</span><span class="sxs-lookup"><span data-stu-id="24d98-118">To expose the transport through configuration the sample implements two more classes—`WSStreamedHttpBindingConfigurationElement` and `WSStreamedHttpBindingSection`.</span></span> <span data-ttu-id="24d98-119">`WSStreamedHttpBindingSection` sınıfı, WCF yapılandırma sistemine `WSStreamedHttpBinding` sunan bir <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602>.</span><span class="sxs-lookup"><span data-stu-id="24d98-119">The class `WSStreamedHttpBindingSection` is a <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> that exposes `WSStreamedHttpBinding` to the WCF configuration system.</span></span> <span data-ttu-id="24d98-120">Uygulamanın toplu işlemi, <xref:System.ServiceModel.Configuration.StandardBindingElement>türetilen `WSStreamedHttpBindingConfigurationElement`için temsilci olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="24d98-120">The bulk of the implementation is delegated to `WSStreamedHttpBindingConfigurationElement`, which derives from <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span></span> <span data-ttu-id="24d98-121">`WSStreamedHttpBindingConfigurationElement` sınıfı, `WSStreamedHttpBinding`özelliklerine karşılık gelen özelliklere ve her yapılandırma öğesini bir bağlamaya eşlemek için işlevlere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="24d98-121">The class `WSStreamedHttpBindingConfigurationElement` has properties that correspond to the properties of `WSStreamedHttpBinding`, and functions to map each configuration element to a binding.</span></span>

    <span data-ttu-id="24d98-122">Hizmetin yapılandırma dosyasına aşağıdaki bölümü ekleyerek işleyiciyi yapılandırma sistemine kaydedin.</span><span class="sxs-lookup"><span data-stu-id="24d98-122">Register the handler with the configuration system, by adding the following section to the service's configuration file.</span></span>

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

    <span data-ttu-id="24d98-123">İşleyiciye daha sonra serviceModel yapılandırma bölümünden başvurulabilir.</span><span class="sxs-lookup"><span data-stu-id="24d98-123">The handler can then be referenced from the serviceModel configuration section.</span></span>

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

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="24d98-124">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="24d98-124">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="24d98-125">Aşağıdaki komutu kullanarak ASP.NET 4,0 ' ü yükler.</span><span class="sxs-lookup"><span data-stu-id="24d98-125">Install ASP.NET 4.0 using the following command.</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="24d98-126">[Windows Communication Foundation Örnekleri Için tek seferlik kurulum yordamında](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)listelenen adımları gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="24d98-126">Ensure that you have performed the steps listed in [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="24d98-127">[Internet Information Services (IIS) sunucu sertifikası yükleme yönergelerini](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="24d98-127">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span></span>

4. <span data-ttu-id="24d98-128">Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="24d98-128">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

5. <span data-ttu-id="24d98-129">Örneği bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="24d98-129">To run the sample in a cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

6. <span data-ttu-id="24d98-130">İstemci penceresi görüntülendiğinde "Sample. txt" yazın.</span><span class="sxs-lookup"><span data-stu-id="24d98-130">When the client window displays, type "Sample.txt".</span></span> <span data-ttu-id="24d98-131">Dizininizde bir "örnek. txt kopyası" bulmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="24d98-131">You should find a "Copy of Sample.txt" in your directory.</span></span>

## <a name="the-wsstreamedhttpbinding-sample-service"></a><span data-ttu-id="24d98-132">WSStreamedHttpBinding örnek hizmeti</span><span class="sxs-lookup"><span data-stu-id="24d98-132">The WSStreamedHttpBinding Sample Service</span></span>

<span data-ttu-id="24d98-133">`WSStreamedHttpBinding` kullanan örnek hizmet, hizmet alt dizininde bulunur.</span><span class="sxs-lookup"><span data-stu-id="24d98-133">The sample service that uses `WSStreamedHttpBinding` is located in the service subdirectory.</span></span> <span data-ttu-id="24d98-134">`OperationContract` uygulanması, `MemoryStream`döndürmeden önce gelen akıştan tüm verileri almak için bir `MemoryStream` kullanır.</span><span class="sxs-lookup"><span data-stu-id="24d98-134">The implementation of `OperationContract` uses a `MemoryStream` to first retrieve all data from the incoming stream before returning the `MemoryStream`.</span></span> <span data-ttu-id="24d98-135">Örnek hizmet Internet Information Services (IIS) tarafından barındırılır.</span><span class="sxs-lookup"><span data-stu-id="24d98-135">The sample service is hosted by Internet Information Services (IIS).</span></span>

```csharp
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

## <a name="the-wsstreamedhttpbinding-sample-client"></a><span data-ttu-id="24d98-136">WSStreamedHttpBinding örnek Istemcisi</span><span class="sxs-lookup"><span data-stu-id="24d98-136">The WSStreamedHttpBinding Sample Client</span></span>

<span data-ttu-id="24d98-137">`WSStreamedHttpBinding` kullanılarak hizmetle etkileşim kurmak için kullanılan istemci, istemci alt dizininde bulunur.</span><span class="sxs-lookup"><span data-stu-id="24d98-137">The client that is used to interact with the service using `WSStreamedHttpBinding` is located in the client subdirectory.</span></span> <span data-ttu-id="24d98-138">Bu örnekte kullanılan sertifika, MakeCert. exe ile oluşturulmuş bir test sertifikası olduğundan, tarayıcınızda https://localhost/servicemodelsamples/service.svc gibi bir HTTPS adresine erişmeye çalıştığınızda bir güvenlik uyarısı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="24d98-138">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert displays when you attempt to access an HTTPS address in your browser such as https://localhost/servicemodelsamples/service.svc.</span></span> <span data-ttu-id="24d98-139">WCF istemcisinin yerinde bir test sertifikasıyla çalışmasına izin vermek için, güvenlik uyarısını bastırmak üzere istemciye bazı ek kodlar eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="24d98-139">To allow the WCF client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="24d98-140">Üretim sertifikaları kullanılırken kod ve eşlik eden sınıf gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="24d98-140">The code and the accompanying class are not required when using production certificates.</span></span>

```csharp
// WARNING: This code is only required for test certificates such as those created by makecert. It is
// not recommended for production code.
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");
```
