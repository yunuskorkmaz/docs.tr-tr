---
title: 'Özel İleti Kodlayıcı: Özel Metin Kodlayıcı'
ms.date: 03/30/2017
ms.assetid: 68ff5c74-3d33-4b44-bcae-e1d2f5dea0de
ms.openlocfilehash: aeb1690d7ead9116bd9c4afe3c64d65d8f51ad50
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43732228"
---
# <a name="custom-message-encoder-custom-text-encoder"></a><span data-ttu-id="739ec-102">Özel İleti Kodlayıcı: Özel Metin Kodlayıcı</span><span class="sxs-lookup"><span data-stu-id="739ec-102">Custom Message Encoder: Custom Text Encoder</span></span>
<span data-ttu-id="739ec-103">Bu örnek, Windows Communication Foundation (WCF) kullanarak bir özel metin ileti Kodlayıcı uygulamak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="739ec-103">This sample demonstrates how to implement a custom text message encoder using Windows Communication Foundation (WCF).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="739ec-104">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="739ec-104">The samples may already be installed on your machine.</span></span> <span data-ttu-id="739ec-105">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="739ec-105">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="739ec-106">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="739ec-106">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="739ec-107">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="739ec-107">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Text`  
  
 <span data-ttu-id="739ec-108"><xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> WCF yalnızca UTF-8, UTF-16 ve büyük Endean Unicode kodlamaları destekler.</span><span class="sxs-lookup"><span data-stu-id="739ec-108">The <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> of WCF supports only the UTF-8, UTF-16 and Big Endean Unicode encodings.</span></span> <span data-ttu-id="739ec-109">Bu örnekte metin özel ileti Kodlayıcı, tüm platform tarafından desteklenen karakter kodlaması birlikte çalışabilirlik için gerekli olabilecek destekler.</span><span class="sxs-lookup"><span data-stu-id="739ec-109">The custom text message encoder in this sample supports all platform-supported character encoding that may be required for interoperability.</span></span> <span data-ttu-id="739ec-110">Örnek, bir istemci konsol programı (.exe), Internet Information Services (IIS) ve bir metin iletisi Kodlayıcı kitaplığı (.dll) tarafından barındırılan bir hizmet kitaplığı (.dll) oluşur.</span><span class="sxs-lookup"><span data-stu-id="739ec-110">The sample consists of a client console program (.exe), a service library (.dll) hosted by Internet Information Services (IIS) and a text message encoder library (.dll).</span></span> <span data-ttu-id="739ec-111">Hizmet istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="739ec-111">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="739ec-112">Anlaşma tarafından tanımlanan `ICalculator` matematik işlemlerinden sunan arabirimi (ekleme, çıkarma, çarpma ve bölme).</span><span class="sxs-lookup"><span data-stu-id="739ec-112">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide).</span></span> <span data-ttu-id="739ec-113">İstemci verilen matematik işlemi ve hizmet yanıt sonucu zaman uyumlu istekleri yapar.</span><span class="sxs-lookup"><span data-stu-id="739ec-113">The client makes synchronous requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="739ec-114">Hem istemci hem de hizmet kullanan `CustomTextMessageEncoder` varsayılan yerine <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="739ec-114">Both client and service uses the `CustomTextMessageEncoder` instead of the default <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.</span></span>  
  
 <span data-ttu-id="739ec-115">Özel bir kodlayıcı uygulama, ileti Kodlayıcı Fabrika, ileti Kodlayıcı, bir ileti bağlama öğesi ve yapılandırma işleyicisi kodlama oluşur ve aşağıda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="739ec-115">The custom encoder implementation consists of a message encoder factory, a message encoder, a message encoding binding element and a configuration handler, and demonstrates the following:</span></span>  
  
-   <span data-ttu-id="739ec-116">Özel bir kodlayıcı ve Kodlayıcı fabrikası oluşturma.</span><span class="sxs-lookup"><span data-stu-id="739ec-116">Building a custom encoder and encoder factory.</span></span>  
  
-   <span data-ttu-id="739ec-117">Bir bağlama öğesi için özel bir kodlayıcı oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="739ec-117">Creating a binding element for a custom encoder.</span></span>  
  
-   <span data-ttu-id="739ec-118">Özel bağlama yapılandırma özel bağlama öğeleri tümleştirmek için kullanma.</span><span class="sxs-lookup"><span data-stu-id="739ec-118">Using the custom binding configuration for integrating custom binding elements.</span></span>  
  
-   <span data-ttu-id="739ec-119">Özel bağlama öğesinin dosya yapılandırması izin vermek için özel yapılandırma işleyicisi geliştirme.</span><span class="sxs-lookup"><span data-stu-id="739ec-119">Developing a custom configuration handler to allow file configuration of a custom binding element.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="739ec-120">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="739ec-120">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="739ec-121">Yükleme [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aşağıdaki komutu kullanarak 4.0.</span><span class="sxs-lookup"><span data-stu-id="739ec-121">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="739ec-122">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="739ec-122">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="739ec-123">Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="739ec-123">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="739ec-124">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="739ec-124">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="message-encoder-factory-and-the-message-encoder"></a><span data-ttu-id="739ec-125">İleti Kodlayıcı fabrikası ve ileti kodlayıcı</span><span class="sxs-lookup"><span data-stu-id="739ec-125">Message Encoder Factory and the Message Encoder</span></span>  
 <span data-ttu-id="739ec-126">Zaman <xref:System.ServiceModel.ServiceHost> veya istemci kanal açıldığında, tasarım zamanı bileşeni `CustomTextMessageBindingElement` oluşturur `CustomTextMessageEncoderFactory`.</span><span class="sxs-lookup"><span data-stu-id="739ec-126">When the <xref:System.ServiceModel.ServiceHost> or the client channel is opened, the design time component `CustomTextMessageBindingElement` creates the `CustomTextMessageEncoderFactory`.</span></span> <span data-ttu-id="739ec-127">Üreteç oluşturur `CustomTextMessageEncoder`.</span><span class="sxs-lookup"><span data-stu-id="739ec-127">The factory creates the `CustomTextMessageEncoder`.</span></span> <span data-ttu-id="739ec-128">İleti Kodlayıcı hem akış hem arabellekli modu çalışır.</span><span class="sxs-lookup"><span data-stu-id="739ec-128">The message encoder operates both in the streaming mode and the buffered mode.</span></span> <span data-ttu-id="739ec-129">Kullandığı <xref:System.Xml.XmlReader> ve <xref:System.Xml.XmlWriter> sırasıyla iletileri yazma ve okuma için.</span><span class="sxs-lookup"><span data-stu-id="739ec-129">It uses the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> to read and write the messages respectively.</span></span> <span data-ttu-id="739ec-130">En iyi duruma getirilmiş XML okuyucular ve yalnızca UTF-8, UTF-16 ve BIG-Endean Unicode destekleyen yazıcılar WCF aksine bu okuyucular ve yazıcılar tüm desteklenen platform kodlamayı destekler.</span><span class="sxs-lookup"><span data-stu-id="739ec-130">As opposed to the optimized XML readers and writers of WCF that support only UTF-8, UTF-16 and Big-Endean Unicode these readers and writers support all platform supported encoding.</span></span>  
  
 <span data-ttu-id="739ec-131">Aşağıdaki kod örneği CustomTextMessageEncoder gösterir.</span><span class="sxs-lookup"><span data-stu-id="739ec-131">The following code example shows the CustomTextMessageEncoder.</span></span>  
  
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
  
 <span data-ttu-id="739ec-132">Aşağıdaki kod örneği, ileti Kodlayıcı fabrikası oluşturma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="739ec-132">The following code example shows how to build the message encoder factory.</span></span>  
  
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
  
## <a name="message-encoding-binding-element"></a><span data-ttu-id="739ec-133">İleti kodlama bağlama öğesi</span><span class="sxs-lookup"><span data-stu-id="739ec-133">Message Encoding Binding Element</span></span>  
 <span data-ttu-id="739ec-134">Bağlama öğeleri WCF çalışma zamanı yığını yapılandırmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="739ec-134">The binding elements allow the configuration of the WCF run-time stack.</span></span> <span data-ttu-id="739ec-135">Özel ileti Kodlayıcı WCF kullanmak için bir bağlama öğesi gereklidir, çalışma zamanı yığını uygun düzeyde uygun ayarlarla ileti Kodlayıcı fabrikası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="739ec-135">To use the custom message encoder in a WCF application, a binding element is required that creates the message encoder factory with the appropriate settings at the appropriate level in the run-time stack.</span></span>  
  
 <span data-ttu-id="739ec-136">`CustomTextMessageBindingElement` Türetildiği <xref:System.ServiceModel.Channels.BindingElement> devralan ve temel sınıf <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="739ec-136">The `CustomTextMessageBindingElement` derives from the <xref:System.ServiceModel.Channels.BindingElement> base class and inherits from the <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> class.</span></span> <span data-ttu-id="739ec-137">Bu, diğer WCF bileşenleri bu bağlama öğesi bir ileti kodlama bağlama öğesi olarak tanımasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="739ec-137">This allows other WCF components to recognize this binding element as being a message encoding binding element.</span></span> <span data-ttu-id="739ec-138">Uygulamasını <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> uygun ayarlarla eşleşen ileti Kodlayıcı üretecin bir örneğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="739ec-138">The implementation of <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> returns an instance of the matching message encoder factory with appropriate settings.</span></span>  
  
 <span data-ttu-id="739ec-139">`CustomTextMessageBindingElement` Ayarlarını sunan `MessageVersion`, `ContentType`, ve `Encoding` özellikleri aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="739ec-139">The `CustomTextMessageBindingElement` exposes settings for `MessageVersion`, `ContentType`, and `Encoding` through properties.</span></span> <span data-ttu-id="739ec-140">Kodlayıcı Soap11Addressing hem Soap12Addressing1 sürümlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="739ec-140">The encoder supports both Soap11Addressing and Soap12Addressing1 versions.</span></span> <span data-ttu-id="739ec-141">Soap11Addressing1 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="739ec-141">The default is Soap11Addressing1.</span></span> <span data-ttu-id="739ec-142">Varsayılan değer olan `ContentType` "metin/XML".</span><span class="sxs-lookup"><span data-stu-id="739ec-142">The default value of the `ContentType` is "text/xml".</span></span> <span data-ttu-id="739ec-143">`Encoding` Özellik istenen karakter kodlama değeri ayarlamanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="739ec-143">The `Encoding` property allows you to set the value of the desired character encoding.</span></span> <span data-ttu-id="739ec-144">Örnek istemci ve hizmet kullanan ISO-8859-1 (Latin1) karakter kodlaması, tarafından desteklenmeyen <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> WCF.</span><span class="sxs-lookup"><span data-stu-id="739ec-144">The sample client and service uses the ISO-8859-1 (Latin1) character encoding, which is not supported by the <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> of WCF.</span></span>  
  
 <span data-ttu-id="739ec-145">Aşağıdaki kod, program aracılığıyla metin özel ileti Kodlayıcı kullanarak bağlama nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="739ec-145">The following code shows how to programmatically create the binding using the custom text message encoder.</span></span>  
  
```  
ICollection<BindingElement> bindingElements = new List<BindingElement>();  
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();  
CustomTextMessageBindingElement textBindingElement = new CustomTextMessageBindingElement();  
bindingElements.Add(textBindingElement);  
bindingElements.Add(httpBindingElement);  
CustomBinding binding = new CustomBinding(bindingElements);  
```  
  
## <a name="adding-metadata-support-to-the-message-encoding-binding-element"></a><span data-ttu-id="739ec-146">İleti kodlama bağlama öğesi meta veri desteği ekleme</span><span class="sxs-lookup"><span data-stu-id="739ec-146">Adding Metadata Support to the Message Encoding Binding Element</span></span>  
 <span data-ttu-id="739ec-147">Öğesinden türetilen herhangi bir türü <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> SOAP bağlama hizmeti için oluşturulan WSDL belgesinde sürümünü güncelleştirmek için sorumludur.</span><span class="sxs-lookup"><span data-stu-id="739ec-147">Any type that derives from <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> is responsible for updating the version of the SOAP binding in the WSDL document generated for the service.</span></span> <span data-ttu-id="739ec-148">Bu uygulama tarafından gerçekleştirilir `ExportEndpoint` metodunda <xref:System.ServiceModel.Description.IWsdlExportExtension> arabirimi ve sonra oluşturulan WSDL değiştirme.</span><span class="sxs-lookup"><span data-stu-id="739ec-148">This is done by implementing the `ExportEndpoint` method on the <xref:System.ServiceModel.Description.IWsdlExportExtension> interface and then modifying the generated WSDL.</span></span> <span data-ttu-id="739ec-149">Bu örnekte `CustomTextMessageBindingElement` WSDL dışarı aktarma mantığından kullanan `TextMessageEncodingBinidngElement`.</span><span class="sxs-lookup"><span data-stu-id="739ec-149">In this sample, the `CustomTextMessageBindingElement` uses the WSDL export logic from the `TextMessageEncodingBinidngElement`.</span></span>  
  
 <span data-ttu-id="739ec-150">Bu örnek için elle yapılandırılmış istemci yapılandırmadır.</span><span class="sxs-lookup"><span data-stu-id="739ec-150">For this sample, the client configuration is hand configured.</span></span> <span data-ttu-id="739ec-151">İstemci yapılandırması nedeniyle üretmek için Svcutil.exe kullanamazsınız `CustomTextMessageBindingElement` davranışını açıklamak için bir ilke onaylama vermez.</span><span class="sxs-lookup"><span data-stu-id="739ec-151">You cannot use Svcutil.exe to generate the client configuration because the `CustomTextMessageBindingElement` does not export a policy assertion to describe its behavior.</span></span> <span data-ttu-id="739ec-152">Genellikle uygulamalıdır <xref:System.ServiceModel.Description.IPolicyExportExtension> arabirimi davranış veya bağlama öğesi tarafından uygulanan özellik açıklayan bir özel ilke onaylama dışarı aktarmak için bir özel bağlama öğesinin.</span><span class="sxs-lookup"><span data-stu-id="739ec-152">You should generally implement the <xref:System.ServiceModel.Description.IPolicyExportExtension> interface on a custom binding element to export a custom policy assertion that describes the behavior or capability implemented by the binding element.</span></span> <span data-ttu-id="739ec-153">Özel bağlama öğesi için bir ilke onaylama dışarı aktarmak nasıl bir örnek için bkz [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="739ec-153">For an example of how to export a policy assertion for a custom binding element, see the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>  
  
## <a name="message-encoding-binding-configuration-handler"></a><span data-ttu-id="739ec-154">İleti kodlama bağlama yapılandırma işleyicisi</span><span class="sxs-lookup"><span data-stu-id="739ec-154">Message Encoding Binding Configuration Handler</span></span>  
 <span data-ttu-id="739ec-155">Önceki bölümde, özel metin ileti Kodlayıcı programsal olarak nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="739ec-155">The previous section shows how to use the custom text message encoder programmatically.</span></span> <span data-ttu-id="739ec-156">`CustomTextMessageEncodingBindingSection` Bir yapılandırma dosyası içinde bir özel metin ileti Kodlayıcı kullanılmasını belirtmenizi sağlar bir yapılandırma işleyicisi uygular.</span><span class="sxs-lookup"><span data-stu-id="739ec-156">The `CustomTextMessageEncodingBindingSection` implements a configuration handler that allows you to specify the use of a custom text message encoder within a configuration file.</span></span> <span data-ttu-id="739ec-157">`CustomTextMessageEncodingBindingSection` Sınıf türetilir <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="739ec-157">The `CustomTextMessageEncodingBindingSection` class derives from the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> class.</span></span> <span data-ttu-id="739ec-158">`BindingElementType` Özelliği bağlama öğesi bu bölüm için oluşturulacak tür yapılandırma sistemi bildirir.</span><span class="sxs-lookup"><span data-stu-id="739ec-158">The `BindingElementType` property informs the configuration system of the type of binding element to create for this section.</span></span>  
  
 <span data-ttu-id="739ec-159">Tüm tarafından tanımlanan ayarlara `CustomTextMessageBindingElement` özellikleri olarak gösterilen `CustomTextMessageEncodingBindingSection`.</span><span class="sxs-lookup"><span data-stu-id="739ec-159">All of the settings defined by `CustomTextMessageBindingElement` are exposed as the properties in the `CustomTextMessageEncodingBindingSection`.</span></span> <span data-ttu-id="739ec-160"><xref:System.Configuration.ConfigurationPropertyAttribute> Öznitelik ayarlanmamışsa, varsayılan değerleri ayarlama ve yapılandırma öğesi özniteliklerini eşleme özellikleri için de yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="739ec-160">The <xref:System.Configuration.ConfigurationPropertyAttribute> assists in mapping the configuration element attributes to the properties and setting default values if the attribute is not set.</span></span> <span data-ttu-id="739ec-161">Yapılandırma değerleri yüklenir ve türünün özelliklerine uygulanan sonra <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> yöntemi çağrıldığında, hangi özellikler bir bağlama öğesi somut bir örneğine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="739ec-161">After the values from configuration are loaded and applied to the properties of the type, the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> method is called, which converts the properties into a concrete instance of a binding element.</span></span>  
  
 <span data-ttu-id="739ec-162">Bu yapılandırma işleyicisi, hizmet veya istemci için App.config veya Web.config aşağıdaki gösterimi eşler.</span><span class="sxs-lookup"><span data-stu-id="739ec-162">This configuration handler maps to the following representation in the App.config or Web.config for the service or client.</span></span>  
  
```xml  
<customTextMessageEncoding encoding="utf-8" contentType="text/xml" messageVersion="Soap11Addressing1" />  
```  
  
 <span data-ttu-id="739ec-163">Örnek, ISO-8859-1 kodlamayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="739ec-163">The sample uses the ISO-8859-1 encoding.</span></span>  
  
 <span data-ttu-id="739ec-164">Bu yapılandırma işleyicisi aşağıdaki yapılandırma öğesini kullanarak kaydedilmelidir kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="739ec-164">To use this configuration handler it must be registered using the following configuration element.</span></span>  
  
```xml  
<extensions>  
    <bindingElementExtensions>  
        <add name="customTextMessageEncoding" type="   
Microsoft.ServiceModel.Samples.CustomTextMessageEncodingBindingSection,   
                  CustomTextMessageEncoder" />  
    </bindingElementExtensions>  
</extensions>  
```  
  
## <a name="see-also"></a><span data-ttu-id="739ec-165">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="739ec-165">See Also</span></span>
