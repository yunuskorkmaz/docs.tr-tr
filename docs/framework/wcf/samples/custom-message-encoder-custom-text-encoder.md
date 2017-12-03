---
title: "Özel İleti Kodlayıcı: Özel Metin Kodlayıcı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68ff5c74-3d33-4b44-bcae-e1d2f5dea0de
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ea35904fe038bdeac528254e476e799369b8b013
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="custom-message-encoder-custom-text-encoder"></a><span data-ttu-id="74afb-102">Özel İleti Kodlayıcı: Özel Metin Kodlayıcı</span><span class="sxs-lookup"><span data-stu-id="74afb-102">Custom Message Encoder: Custom Text Encoder</span></span>
<span data-ttu-id="74afb-103">Bu örnek nasıl kullanarak özel metin ileti Kodlayıcı uygulanacağını gösterilen [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="74afb-103">This sample demonstrates how to implement a custom text message encoder using [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="74afb-104">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="74afb-104">The samples may already be installed on your machine.</span></span> <span data-ttu-id="74afb-105">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="74afb-105">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="74afb-106">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="74afb-106">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="74afb-107">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="74afb-107">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Text`  
  
 <span data-ttu-id="74afb-108"><xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> , [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Yalnızca UTF-8, UTF-16 ve büyük Endean Unicode Kodlamalar destekler.</span><span class="sxs-lookup"><span data-stu-id="74afb-108">The <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] supports only the UTF-8, UTF-16 and Big Endean Unicode encodings.</span></span> <span data-ttu-id="74afb-109">Özel metin ileti Kodlayıcı bu örnekte, tüm platform tarafından desteklenen karakter kodlaması birlikte çalışabilirlik için gerekli olabilecek destekler.</span><span class="sxs-lookup"><span data-stu-id="74afb-109">The custom text message encoder in this sample supports all platform-supported character encoding that may be required for interoperability.</span></span> <span data-ttu-id="74afb-110">Örnek bir istemci konsol program (.exe), Internet Information Services (IIS) ve bir metin ileti Kodlayıcı kitaplığı (.dll) tarafından barındırılan bir hizmet kitaplığı (.dll) oluşur.</span><span class="sxs-lookup"><span data-stu-id="74afb-110">The sample consists of a client console program (.exe), a service library (.dll) hosted by Internet Information Services (IIS) and a text message encoder library (.dll).</span></span> <span data-ttu-id="74afb-111">Hizmet bir istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="74afb-111">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="74afb-112">Anlaşma tarafından tanımlanan `ICalculator` matematik işlemleri kullanıma sunan arabirim (eklemek, çıkarma, çarpma ve bölme).</span><span class="sxs-lookup"><span data-stu-id="74afb-112">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide).</span></span> <span data-ttu-id="74afb-113">İstemci eş zamanlı istekleri verilen matematik işlemi ve sonuç ile hizmet yanıtları yapar.</span><span class="sxs-lookup"><span data-stu-id="74afb-113">The client makes synchronous requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="74afb-114">Hem istemci hem de hizmet kullanır `CustomTextMessageEncoder` varsayılan yerine <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="74afb-114">Both client and service uses the `CustomTextMessageEncoder` instead of the default <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.</span></span>  
  
 <span data-ttu-id="74afb-115">Özel Kodlayıcı uygulama ileti Kodlayıcı Fabrika, ileti Kodlayıcı, bağlama öğesi ve yapılandırma işleyicisi kodlama bir ileti oluşur ve aşağıda gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="74afb-115">The custom encoder implementation consists of a message encoder factory, a message encoder, a message encoding binding element and a configuration handler, and demonstrates the following:</span></span>  
  
-   <span data-ttu-id="74afb-116">Özel Kodlayıcı ve Kodlayıcı Fabrika oluşturma.</span><span class="sxs-lookup"><span data-stu-id="74afb-116">Building a custom encoder and encoder factory.</span></span>  
  
-   <span data-ttu-id="74afb-117">Bir bağlama öğesi için özel bir kodlayıcı oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="74afb-117">Creating a binding element for a custom encoder.</span></span>  
  
-   <span data-ttu-id="74afb-118">Özel bağlama yapılandırma özel bağlama öğeleri tümleştirmek için kullanma.</span><span class="sxs-lookup"><span data-stu-id="74afb-118">Using the custom binding configuration for integrating custom binding elements.</span></span>  
  
-   <span data-ttu-id="74afb-119">Özel bağlama öğesi dosya yapılandırılmasına olanak verecek özel yapılandırma işleyicisi geliştirme.</span><span class="sxs-lookup"><span data-stu-id="74afb-119">Developing a custom configuration handler to allow file configuration of a custom binding element.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="74afb-120">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="74afb-120">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="74afb-121">Yükleme [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aşağıdaki komutu kullanarak 4.0.</span><span class="sxs-lookup"><span data-stu-id="74afb-121">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="74afb-122">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="74afb-122">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="74afb-123">Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="74afb-123">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="74afb-124">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="74afb-124">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="message-encoder-factory-and-the-message-encoder"></a><span data-ttu-id="74afb-125">İleti Kodlayıcı Fabrika ve ileti kodlayıcı</span><span class="sxs-lookup"><span data-stu-id="74afb-125">Message Encoder Factory and the Message Encoder</span></span>  
 <span data-ttu-id="74afb-126">Zaman <xref:System.ServiceModel.ServiceHost> veya istemci kanal açıldığında, tasarım zamanı bileşeni `CustomTextMessageBindingElement` oluşturur `CustomTextMessageEncoderFactory`.</span><span class="sxs-lookup"><span data-stu-id="74afb-126">When the <xref:System.ServiceModel.ServiceHost> or the client channel is opened, the design time component `CustomTextMessageBindingElement` creates the `CustomTextMessageEncoderFactory`.</span></span> <span data-ttu-id="74afb-127">Üreteç oluşturur `CustomTextMessageEncoder`.</span><span class="sxs-lookup"><span data-stu-id="74afb-127">The factory creates the `CustomTextMessageEncoder`.</span></span> <span data-ttu-id="74afb-128">İleti Kodlayıcı hem akış modunda ve arabellekli modu çalışır.</span><span class="sxs-lookup"><span data-stu-id="74afb-128">The message encoder operates both in the streaming mode and the buffered mode.</span></span> <span data-ttu-id="74afb-129">Kullandığı <xref:System.Xml.XmlReader> ve <xref:System.Xml.XmlWriter> okumak ve iletileri sırasıyla yazmak için.</span><span class="sxs-lookup"><span data-stu-id="74afb-129">It uses the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> to read and write the messages respectively.</span></span> <span data-ttu-id="74afb-130">En iyi duruma getirilmiş XML okuyucuları ve yazıcıları, aksine [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] destekleyen yalnızca UTF-8, UTF-16 ve büyük Endean Unicode bu okuyucular ve yazıcılarının destek tüm desteklenen platform kodlama.</span><span class="sxs-lookup"><span data-stu-id="74afb-130">As opposed to the optimized XML readers and writers of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] that support only UTF-8, UTF-16 and Big-Endean Unicode these readers and writers support all platform supported encoding.</span></span>  
  
 <span data-ttu-id="74afb-131">Aşağıdaki kod örneğinde CustomTextMessageEncoder gösterir.</span><span class="sxs-lookup"><span data-stu-id="74afb-131">The following code example shows the CustomTextMessageEncoder.</span></span>  
  
```csharp  
public class CustomTextMessageEncoder : MessageEncoder  
{  
    private CustomTextMessageEncoderFactory factory;  
    private XmlWriterSettings writerSettings;  
    private string contentType;  
  
    public CustomTextMessageEncoder(CustomTextMessageEncoderFactory factory)  
    {  
        this.factory = factory;  
  
        this.writerSettings = new XmlWriterSettings();  
        this.writerSettings.Encoding = Encoding.GetEncoding(factory.CharSet);  
        this.contentType = string.Format("{0}; charset={1}",   
            this.factory.MediaType, this.writerSettings.Encoding.HeaderName);  
    }  
  
    public override string ContentType  
    {  
        get  
        {  
            return this.contentType;  
        }  
    }  
  
    public override string MediaType  
    {  
        get   
        {  
            return factory.MediaType;  
        }  
    }  
  
    public override MessageVersion MessageVersion  
    {  
        get   
        {  
            return this.factory.MessageVersion;  
        }  
    }  
  
    public override Message ReadMessage(ArraySegment<byte> buffer, BufferManager bufferManager, string contentType)  
    {     
        byte[] msgContents = new byte[buffer.Count];  
        Array.Copy(buffer.Array, buffer.Offset, msgContents, 0, msgContents.Length);  
        bufferManager.ReturnBuffer(buffer.Array);  
  
        MemoryStream stream = new MemoryStream(msgContents);  
        return ReadMessage(stream, int.MaxValue);  
    }  
  
    public override Message ReadMessage(Stream stream, int maxSizeOfHeaders, string contentType)  
    {  
        XmlReader reader = XmlReader.Create(stream);  
        return Message.CreateMessage(reader, maxSizeOfHeaders, this.MessageVersion);  
    }  
  
    public override ArraySegment<byte> WriteMessage(Message message, int maxMessageSize, BufferManager bufferManager, int messageOffset)  
    {  
        MemoryStream stream = new MemoryStream();  
        XmlWriter writer = XmlWriter.Create(stream, this.writerSettings);  
        message.WriteMessage(writer);  
        writer.Close();  
  
        byte[] messageBytes = stream.GetBuffer();  
        int messageLength = (int)stream.Position;  
        stream.Close();  
  
        int totalLength = messageLength + messageOffset;  
        byte[] totalBytes = bufferManager.TakeBuffer(totalLength);  
        Array.Copy(messageBytes, 0, totalBytes, messageOffset, messageLength);  
  
        ArraySegment<byte> byteArray = new ArraySegment<byte>(totalBytes, messageOffset, messageLength);  
        return byteArray;  
    }  
  
    public override void WriteMessage(Message message, Stream stream)  
    {  
        XmlWriter writer = XmlWriter.Create(stream, this.writerSettings);  
        message.WriteMessage(writer);  
        writer.Close();  
    }  
}  
```  
  
 <span data-ttu-id="74afb-132">Aşağıdaki kod örneğinde ileti Kodlayıcı Fabrika nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="74afb-132">The following code example shows how to build the message encoder factory.</span></span>  
  
```csharp  
public class CustomTextMessageEncoderFactory : MessageEncoderFactory  
{  
    private MessageEncoder encoder;  
    private MessageVersion version;  
    private string mediaType;  
    private string charSet;  
  
    internal CustomTextMessageEncoderFactory(string mediaType, string charSet,  
        MessageVersion version)  
    {  
        this.version = version;  
        this.mediaType = mediaType;  
        this.charSet = charSet;  
        this.encoder = new CustomTextMessageEncoder(this);  
    }  
  
    public override MessageEncoder Encoder  
    {  
        get   
        {   
            return this.encoder;  
        }  
    }  
  
    public override MessageVersion MessageVersion  
    {  
        get   
        {   
            return this.version;  
        }  
    }  
  
    internal string MediaType  
    {  
        get  
        {  
            return this.mediaType;  
        }  
    }  
  
    internal string CharSet  
    {  
        get  
        {  
            return this.charSet;  
        }  
    }  
}  
```  
  
## <a name="message-encoding-binding-element"></a><span data-ttu-id="74afb-133">İleti kodlama bağlama öğesi</span><span class="sxs-lookup"><span data-stu-id="74afb-133">Message Encoding Binding Element</span></span>  
 <span data-ttu-id="74afb-134">Bağlama öğeleri yapılandırmasına izin ver [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] çalışma zamanı yığını.</span><span class="sxs-lookup"><span data-stu-id="74afb-134">The binding elements allow the configuration of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] run-time stack.</span></span> <span data-ttu-id="74afb-135">Özel ileti Kodlayıcı kullanmak için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulama, bir bağlama öğesi gereklidir, çalışma zamanı yığınında uygun düzeyde uygun ayarlarla ileti Kodlayıcı üreteci oluşturur.</span><span class="sxs-lookup"><span data-stu-id="74afb-135">To use the custom message encoder in a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application, a binding element is required that creates the message encoder factory with the appropriate settings at the appropriate level in the run-time stack.</span></span>  
  
 <span data-ttu-id="74afb-136">`CustomTextMessageBindingElement` Türetilen <xref:System.ServiceModel.Channels.BindingElement> temel sınıfı ve devraldığı <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="74afb-136">The `CustomTextMessageBindingElement` derives from the <xref:System.ServiceModel.Channels.BindingElement> base class and inherits from the <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> class.</span></span> <span data-ttu-id="74afb-137">Bu diğer sağlar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bağlama öğesi kodlama bir ileti olduğu bu bağlama öğesi tanımak için bileşenleri.</span><span class="sxs-lookup"><span data-stu-id="74afb-137">This allows other [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] components to recognize this binding element as being a message encoding binding element.</span></span> <span data-ttu-id="74afb-138">Uygulaması <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> uygun ayarlarla eşleşen ileti Kodlayıcı Fabrika örneğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="74afb-138">The implementation of <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> returns an instance of the matching message encoder factory with appropriate settings.</span></span>  
  
 <span data-ttu-id="74afb-139">`CustomTextMessageBindingElement` Ayarlarını gösteren `MessageVersion`, `ContentType`, ve `Encoding` özellikleri aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="74afb-139">The `CustomTextMessageBindingElement` exposes settings for `MessageVersion`, `ContentType`, and `Encoding` through properties.</span></span> <span data-ttu-id="74afb-140">Kodlayıcı Soap11Addressing ve Soap12Addressing1 sürümlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="74afb-140">The encoder supports both Soap11Addressing and Soap12Addressing1 versions.</span></span> <span data-ttu-id="74afb-141">Soap11Addressing1 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="74afb-141">The default is Soap11Addressing1.</span></span> <span data-ttu-id="74afb-142">Varsayılan değer olan `ContentType` "text/xml".</span><span class="sxs-lookup"><span data-stu-id="74afb-142">The default value of the `ContentType` is "text/xml".</span></span> <span data-ttu-id="74afb-143">`Encoding` Özelliği istenen karakter kodlamasını değerini ayarlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="74afb-143">The `Encoding` property allows you to set the value of the desired character encoding.</span></span> <span data-ttu-id="74afb-144">Örnek istemci hem de hizmet kullanan ISO 8859-1 (Latin1) karakter kodlamasını, tarafından desteklenmeyen <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> , [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="74afb-144">The sample client and service uses the ISO-8859-1 (Latin1) character encoding, which is not supported by the <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 <span data-ttu-id="74afb-145">Aşağıdaki kod özel metin ileti Kodlayıcısı kullanarak bağlama programlı olarak oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="74afb-145">The following code shows how to programmatically create the binding using the custom text message encoder.</span></span>  
  
```  
ICollection<BindingElement> bindingElements = new List<BindingElement>();  
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();  
CustomTextMessageBindingElement textBindingElement = new CustomTextMessageBindingElement();  
bindingElements.Add(textBindingElement);  
bindingElements.Add(httpBindingElement);  
CustomBinding binding = new CustomBinding(bindingElements);  
```  
  
## <a name="adding-metadata-support-to-the-message-encoding-binding-element"></a><span data-ttu-id="74afb-146">Bağlama öğesi kodlama ileti meta verileri desteği ekleme</span><span class="sxs-lookup"><span data-stu-id="74afb-146">Adding Metadata Support to the Message Encoding Binding Element</span></span>  
 <span data-ttu-id="74afb-147">Türetilen herhangi bir türü <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> hizmeti için oluşturulan WSDL belgesinde SOAP bağlama sürümünü güncelleştirmek için sorumludur.</span><span class="sxs-lookup"><span data-stu-id="74afb-147">Any type that derives from <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> is responsible for updating the version of the SOAP binding in the WSDL document generated for the service.</span></span> <span data-ttu-id="74afb-148">Bu uygulama tarafından yapılır `ExportEndpoint` yöntemi <xref:System.ServiceModel.Description.IWsdlExportExtension> arabirimi ve oluşturulan WSDL değiştirme.</span><span class="sxs-lookup"><span data-stu-id="74afb-148">This is done by implementing the `ExportEndpoint` method on the <xref:System.ServiceModel.Description.IWsdlExportExtension> interface and then modifying the generated WSDL.</span></span> <span data-ttu-id="74afb-149">Bu örnekte `CustomTextMessageBindingElement` WSDL dışa aktarma mantığından kullanan `TextMessageEncodingBinidngElement`.</span><span class="sxs-lookup"><span data-stu-id="74afb-149">In this sample, the `CustomTextMessageBindingElement` uses the WSDL export logic from the `TextMessageEncodingBinidngElement`.</span></span>  
  
 <span data-ttu-id="74afb-150">Bu örnek için elle yapılandırılmış istemci yapılandırmadır.</span><span class="sxs-lookup"><span data-stu-id="74afb-150">For this sample, the client configuration is hand configured.</span></span> <span data-ttu-id="74afb-151">İstemci yapılandırması oluşturulamıyor Svcutil.exe kullanamazsınız `CustomTextMessageBindingElement` davranışını açıklamak için bir ilke onaylama vermez.</span><span class="sxs-lookup"><span data-stu-id="74afb-151">You cannot use Svcutil.exe to generate the client configuration because the `CustomTextMessageBindingElement` does not export a policy assertion to describe its behavior.</span></span> <span data-ttu-id="74afb-152">Genellikle uygulamalıdır <xref:System.ServiceModel.Description.IPolicyExportExtension> davranış veya bağlama öğesi tarafından uygulanan özelliği tanımlayan bir özel ilke onaylama dışarı aktarmak için bir özel bağlama öğesi üzerindeki arabirimi.</span><span class="sxs-lookup"><span data-stu-id="74afb-152">You should generally implement the <xref:System.ServiceModel.Description.IPolicyExportExtension> interface on a custom binding element to export a custom policy assertion that describes the behavior or capability implemented by the binding element.</span></span> <span data-ttu-id="74afb-153">Özel bağlama öğesi için bir ilke onaylama dışarı aktarma örneği için bkz: [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="74afb-153">For an example of how to export a policy assertion for a custom binding element, see the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>  
  
## <a name="message-encoding-binding-configuration-handler"></a><span data-ttu-id="74afb-154">Kodlama bağlama yapılandırma işleyicisi iletisi</span><span class="sxs-lookup"><span data-stu-id="74afb-154">Message Encoding Binding Configuration Handler</span></span>  
 <span data-ttu-id="74afb-155">Önceki bölümde özel metin ileti Kodlayıcı programlı olarak kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="74afb-155">The previous section shows how to use the custom text message encoder programmatically.</span></span> <span data-ttu-id="74afb-156">`CustomTextMessageEncodingBindingSection` Yapılandırma dosyasının içinde özel metin ileti kodlayıcı kullanımını belirtmenize olanak tanır yapılandırma işleyicisini uygular.</span><span class="sxs-lookup"><span data-stu-id="74afb-156">The `CustomTextMessageEncodingBindingSection` implements a configuration handler that allows you to specify the use of a custom text message encoder within a configuration file.</span></span> <span data-ttu-id="74afb-157">`CustomTextMessageEncodingBindingSection` Sınıfı türer <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="74afb-157">The `CustomTextMessageEncodingBindingSection` class derives from the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> class.</span></span> <span data-ttu-id="74afb-158">`BindingElementType` Özelliği için bu bölümü oluşturmak için bağlama öğesi türünün yapılandırma sistemi bildirir.</span><span class="sxs-lookup"><span data-stu-id="74afb-158">The `BindingElementType` property informs the configuration system of the type of binding element to create for this section.</span></span>  
  
 <span data-ttu-id="74afb-159">Tarafından tanımlanan tüm ayarlar `CustomTextMessageBindingElement` özellikleri olarak sunulan `CustomTextMessageEncodingBindingSection`.</span><span class="sxs-lookup"><span data-stu-id="74afb-159">All of the settings defined by `CustomTextMessageBindingElement` are exposed as the properties in the `CustomTextMessageEncodingBindingSection`.</span></span> <span data-ttu-id="74afb-160"><xref:System.Configuration.ConfigurationPropertyAttribute> Öznitelik ayarlanmamışsa, varsayılan değerleri ayarlama ve yapılandırma öğesi özniteliklerini eşleme için özellikleri de yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="74afb-160">The <xref:System.Configuration.ConfigurationPropertyAttribute> assists in mapping the configuration element attributes to the properties and setting default values if the attribute is not set.</span></span> <span data-ttu-id="74afb-161">Yapılandırma değerleri yüklendikten ve türü özelliklerine uygulanan sonra <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> yöntemi çağrıldığında, hangi özellikler somut bir bağlama öğesi örneğine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="74afb-161">After the values from configuration are loaded and applied to the properties of the type, the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> method is called, which converts the properties into a concrete instance of a binding element.</span></span>  
  
 <span data-ttu-id="74afb-162">Bu yapılandırma işleyicisi hizmet veya istemci için App.config veya Web.config içinde aşağıdaki gösterimi eşler.</span><span class="sxs-lookup"><span data-stu-id="74afb-162">This configuration handler maps to the following representation in the App.config or Web.config for the service or client.</span></span>  
  
```xml  
<customTextMessageEncoding encoding="utf-8" contentType="text/xml" messageVersion="Soap11Addressing1" />  
```  
  
 <span data-ttu-id="74afb-163">ISO 8859 1 kodlama örnek kullanır.</span><span class="sxs-lookup"><span data-stu-id="74afb-163">The sample uses the ISO-8859-1 encoding.</span></span>  
  
 <span data-ttu-id="74afb-164">Aşağıdaki yapılandırma öğesini kullanarak kaydedilmelidir bu yapılandırma işleyicisi kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="74afb-164">To use this configuration handler it must be registered using the following configuration element.</span></span>  
  
```xml  
<extensions>  
    <bindingElementExtensions>  
        <add name="customTextMessageEncoding" type="   
Microsoft.ServiceModel.Samples.CustomTextMessageEncodingBindingSection,   
                  CustomTextMessageEncoder" />  
    </bindingElementExtensions>  
</extensions>  
```  
  
## <a name="see-also"></a><span data-ttu-id="74afb-165">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="74afb-165">See Also</span></span>
