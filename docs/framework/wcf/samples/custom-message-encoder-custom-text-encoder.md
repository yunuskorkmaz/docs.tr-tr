---
title: 'Özel Ileti Kodlayıcısı: özel metin Kodlayıcısı-WCF'
ms.date: 03/30/2017
ms.assetid: 68ff5c74-3d33-4b44-bcae-e1d2f5dea0de
ms.openlocfilehash: 17ad1f2ab557c470a39ab5fff6c1c52d5e41a2a5
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716834"
---
# <a name="custom-message-encoder-custom-text-encoder"></a><span data-ttu-id="28aa5-102">Özel İleti Kodlayıcı: Özel Metin Kodlayıcı</span><span class="sxs-lookup"><span data-stu-id="28aa5-102">Custom Message Encoder: Custom Text Encoder</span></span>

<span data-ttu-id="28aa5-103">Bu örnek, Windows Communication Foundation (WCF) kullanarak özel metin iletisi Kodlayıcısı 'nın nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="28aa5-103">This sample demonstrates how to implement a custom text message encoder using Windows Communication Foundation (WCF).</span></span>

> [!WARNING]
> <span data-ttu-id="28aa5-104">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="28aa5-104">The samples may already be installed on your machine.</span></span> <span data-ttu-id="28aa5-105">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="28aa5-105">Check for the following (default) directory before continuing.</span></span>
> 
> `<InstallDrive>:\WF_WCF_Samples`
> 
> <span data-ttu-id="28aa5-106">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="28aa5-106">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="28aa5-107">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="28aa5-107">This sample is located in the following directory.</span></span>
> 
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Text`

<span data-ttu-id="28aa5-108">WCF <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> yalnızca UTF-8, UTF-16 ve Big-endian Unicode kodlamalarını destekler.</span><span class="sxs-lookup"><span data-stu-id="28aa5-108">The <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> of WCF supports only the UTF-8, UTF-16 and big-endian Unicode encodings.</span></span> <span data-ttu-id="28aa5-109">Bu örnekteki özel metin iletisi Kodlayıcısı, birlikte çalışabilirlik için gerekebilecek tüm platform tarafından desteklenen karakter kodlamalarını destekler.</span><span class="sxs-lookup"><span data-stu-id="28aa5-109">The custom text message encoder in this sample supports all platform-supported character encodings that may be required for interoperability.</span></span> <span data-ttu-id="28aa5-110">Örnek, bir istemci konsol programı (. exe), Internet Information Services (IIS) tarafından barındırılan bir hizmet kitaplığı (. dll) ve bir SMS mesajı Kodlayıcı kitaplığı (. dll) içerir.</span><span class="sxs-lookup"><span data-stu-id="28aa5-110">The sample consists of a client console program (.exe), a service library (.dll) hosted by Internet Information Services (IIS), and a text message encoder library (.dll).</span></span> <span data-ttu-id="28aa5-111">Hizmet, istek-yanıt iletişim modelini tanımlayan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="28aa5-111">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="28aa5-112">Sözleşme, matematik işlemlerini (ekleme, çıkarma, çarpma ve bölme) sunan `ICalculator` arabirimi tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="28aa5-112">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide).</span></span> <span data-ttu-id="28aa5-113">İstemci belirli bir matematik işlemine zaman uyumlu istekler yapar ve hizmet sonuçla yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="28aa5-113">The client makes synchronous requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="28aa5-114">İstemci ve hizmet, varsayılan <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>yerine `CustomTextMessageEncoder` kullanır.</span><span class="sxs-lookup"><span data-stu-id="28aa5-114">Both client and service uses the `CustomTextMessageEncoder` instead of the default <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.</span></span>

<span data-ttu-id="28aa5-115">Özel kodlayıcı uygulamasının bir ileti Kodlayıcısı fabrikası, bir ileti Kodlayıcısı, ileti kodlama bağlama öğesi ve yapılandırma işleyicisi oluşur ve şunları gösterir:</span><span class="sxs-lookup"><span data-stu-id="28aa5-115">The custom encoder implementation consists of a message encoder factory, a message encoder, a message encoding binding element and a configuration handler, and demonstrates the following:</span></span>

- <span data-ttu-id="28aa5-116">Özel kodlayıcı ve kodlayıcı fabrikası oluşturma.</span><span class="sxs-lookup"><span data-stu-id="28aa5-116">Building a custom encoder and encoder factory.</span></span>

- <span data-ttu-id="28aa5-117">Özel bir kodlayıcı için bağlama öğesi oluşturma.</span><span class="sxs-lookup"><span data-stu-id="28aa5-117">Creating a binding element for a custom encoder.</span></span>

- <span data-ttu-id="28aa5-118">Özel bağlama öğelerini tümleştirmek için özel bağlama yapılandırması kullanma.</span><span class="sxs-lookup"><span data-stu-id="28aa5-118">Using the custom binding configuration for integrating custom binding elements.</span></span>

- <span data-ttu-id="28aa5-119">Özel bir bağlama öğesinin dosya yapılandırmasına izin vermek için özel bir yapılandırma işleyicisi geliştirme.</span><span class="sxs-lookup"><span data-stu-id="28aa5-119">Developing a custom configuration handler to allow file configuration of a custom binding element.</span></span>

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="28aa5-120">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="28aa5-120">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="28aa5-121">Aşağıdaki komutu kullanarak ASP.NET 4,0 ' ü yükler.</span><span class="sxs-lookup"><span data-stu-id="28aa5-121">Install ASP.NET 4.0 using the following command.</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="28aa5-122">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="28aa5-122">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="28aa5-123">Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="28aa5-123">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="28aa5-124">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="28aa5-124">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

## <a name="message-encoder-factory-and-the-message-encoder"></a><span data-ttu-id="28aa5-125">İleti Kodlayıcısı fabrikası ve Ileti Kodlayıcısı</span><span class="sxs-lookup"><span data-stu-id="28aa5-125">Message Encoder Factory and the Message Encoder</span></span>

<span data-ttu-id="28aa5-126"><xref:System.ServiceModel.ServiceHost> veya istemci kanalı açıldığında, tasarım zamanı bileşeni `CustomTextMessageBindingElement` `CustomTextMessageEncoderFactory`oluşturur.</span><span class="sxs-lookup"><span data-stu-id="28aa5-126">When the <xref:System.ServiceModel.ServiceHost> or the client channel is opened, the design time component `CustomTextMessageBindingElement` creates the `CustomTextMessageEncoderFactory`.</span></span> <span data-ttu-id="28aa5-127">Fabrika `CustomTextMessageEncoder`oluşturur.</span><span class="sxs-lookup"><span data-stu-id="28aa5-127">The factory creates the `CustomTextMessageEncoder`.</span></span> <span data-ttu-id="28aa5-128">İleti Kodlayıcısı hem akış modunda hem de arabelleğe alınmış modda çalışır.</span><span class="sxs-lookup"><span data-stu-id="28aa5-128">The message encoder operates both in the streaming mode and the buffered mode.</span></span> <span data-ttu-id="28aa5-129">Sırasıyla iletileri okumak ve yazmak için <xref:System.Xml.XmlReader> ve <xref:System.Xml.XmlWriter> kullanır.</span><span class="sxs-lookup"><span data-stu-id="28aa5-129">It uses the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> to read and write the messages respectively.</span></span> <span data-ttu-id="28aa5-130">Yalnızca UTF-8, UTF-16 ve Big-endian Unicode 'u destekleyen, iyileştirilmiş XML okuyucuları ve WCF yazarlarının aksine, bu okuyucular ve yazarlar tüm platform tarafından desteklenen kodlamayı destekler.</span><span class="sxs-lookup"><span data-stu-id="28aa5-130">As opposed to the optimized XML readers and writers of WCF that support only UTF-8, UTF-16 and big-endian Unicode, these readers and writers support all platform-supported encoding.</span></span>

<span data-ttu-id="28aa5-131">Aşağıdaki kod örneğinde CustomTextMessageEncoder gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="28aa5-131">The following code example shows the CustomTextMessageEncoder.</span></span>

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
        this.contentType = $"{this.factory.MediaType}; charset={this.writerSettings.Encoding.HeaderName}";
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

<span data-ttu-id="28aa5-132">Aşağıdaki kod örneği, ileti Kodlayıcısı fabrikasının nasıl oluşturulacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="28aa5-132">The following code example shows how to build the message encoder factory.</span></span>

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

## <a name="message-encoding-binding-element"></a><span data-ttu-id="28aa5-133">İleti kodlama bağlama öğesi</span><span class="sxs-lookup"><span data-stu-id="28aa5-133">Message Encoding Binding Element</span></span>

<span data-ttu-id="28aa5-134">Bağlama öğeleri, WCF çalışma zamanı yığınının yapılandırmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="28aa5-134">The binding elements allow the configuration of the WCF run-time stack.</span></span> <span data-ttu-id="28aa5-135">Özel ileti Kodlayıcısı 'nı bir WCF uygulamasında kullanmak için, çalışma zamanı yığınında uygun düzeyde uygun ayarlarla ileti Kodlayıcısı fabrikasını oluşturan bir Binding öğesi gereklidir.</span><span class="sxs-lookup"><span data-stu-id="28aa5-135">To use the custom message encoder in a WCF application, a binding element is required that creates the message encoder factory with the appropriate settings at the appropriate level in the run-time stack.</span></span>

<span data-ttu-id="28aa5-136">`CustomTextMessageBindingElement`, <xref:System.ServiceModel.Channels.BindingElement> temel sınıfından türetilir ve <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> sınıfından devralır.</span><span class="sxs-lookup"><span data-stu-id="28aa5-136">The `CustomTextMessageBindingElement` derives from the <xref:System.ServiceModel.Channels.BindingElement> base class and inherits from the <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> class.</span></span> <span data-ttu-id="28aa5-137">Bu, diğer WCF bileşenlerinin bu bağlama öğesini bir ileti kodlama bağlama öğesi olarak tanımasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="28aa5-137">This allows other WCF components to recognize this binding element as being a message encoding binding element.</span></span> <span data-ttu-id="28aa5-138"><xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> uygulanması, uygun ayarlarla eşleşen ileti Kodlayıcısı fabrikasının bir örneğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="28aa5-138">The implementation of <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> returns an instance of the matching message encoder factory with appropriate settings.</span></span>

<span data-ttu-id="28aa5-139">`CustomTextMessageBindingElement`, `MessageVersion`, `ContentType`ve `Encoding` özellikleriyle ilgili ayarları kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="28aa5-139">The `CustomTextMessageBindingElement` exposes settings for `MessageVersion`, `ContentType`, and `Encoding` through properties.</span></span> <span data-ttu-id="28aa5-140">Kodlayıcı hem Soap11Addressing hem de Soap12Addressing1 sürümlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="28aa5-140">The encoder supports both Soap11Addressing and Soap12Addressing1 versions.</span></span> <span data-ttu-id="28aa5-141">Varsayılan değer Soap11Addressing1 ' dir.</span><span class="sxs-lookup"><span data-stu-id="28aa5-141">The default is Soap11Addressing1.</span></span> <span data-ttu-id="28aa5-142">`ContentType` varsayılan değeri "text/xml" dir.</span><span class="sxs-lookup"><span data-stu-id="28aa5-142">The default value of the `ContentType` is "text/xml".</span></span> <span data-ttu-id="28aa5-143">`Encoding` özelliği, istenen karakter kodlamasının değerini ayarlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="28aa5-143">The `Encoding` property allows you to set the value of the desired character encoding.</span></span> <span data-ttu-id="28aa5-144">Örnek istemci ve hizmet, WCF <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> tarafından desteklenmeyen ISO-8859-1 (Latin1) karakter kodlamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="28aa5-144">The sample client and service uses the ISO-8859-1 (Latin1) character encoding, which is not supported by the <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> of WCF.</span></span>

<span data-ttu-id="28aa5-145">Aşağıdaki kod, özel metin iletisi Kodlayıcısı kullanılarak bağlama programlı bir şekilde nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="28aa5-145">The following code shows how to programmatically create the binding using the custom text message encoder.</span></span>

```csharp
ICollection<BindingElement> bindingElements = new List<BindingElement>();
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();
CustomTextMessageBindingElement textBindingElement = new CustomTextMessageBindingElement();
bindingElements.Add(textBindingElement);
bindingElements.Add(httpBindingElement);
CustomBinding binding = new CustomBinding(bindingElements);
```

## <a name="adding-metadata-support-to-the-message-encoding-binding-element"></a><span data-ttu-id="28aa5-146">Ileti kodlama bağlama öğesine meta veri desteği ekleniyor</span><span class="sxs-lookup"><span data-stu-id="28aa5-146">Adding Metadata Support to the Message Encoding Binding Element</span></span>

<span data-ttu-id="28aa5-147"><xref:System.ServiceModel.Channels.MessageEncodingBindingElement> türetilen herhangi bir tür, hizmet için oluşturulan WSDL belgesinde SOAP bağlamanın sürümünün güncelleştirilmesinden sorumludur.</span><span class="sxs-lookup"><span data-stu-id="28aa5-147">Any type that derives from <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> is responsible for updating the version of the SOAP binding in the WSDL document generated for the service.</span></span> <span data-ttu-id="28aa5-148">Bu, <xref:System.ServiceModel.Description.IWsdlExportExtension> arabirimindeki `ExportEndpoint` yöntemi uygulayarak ve sonra oluşturulan WSDL 'nin değiştirilerek yapılır.</span><span class="sxs-lookup"><span data-stu-id="28aa5-148">This is done by implementing the `ExportEndpoint` method on the <xref:System.ServiceModel.Description.IWsdlExportExtension> interface and then modifying the generated WSDL.</span></span> <span data-ttu-id="28aa5-149">Bu örnekte, `CustomTextMessageBindingElement` `TextMessageEncodingBindingElement`WSDL dışarı aktarma mantığını kullanır.</span><span class="sxs-lookup"><span data-stu-id="28aa5-149">In this sample, the `CustomTextMessageBindingElement` uses the WSDL export logic from the `TextMessageEncodingBindingElement`.</span></span>

<span data-ttu-id="28aa5-150">Bu örnek için, istemci yapılandırması el ile yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="28aa5-150">For this sample, the client configuration is hand configured.</span></span> <span data-ttu-id="28aa5-151">`CustomTextMessageBindingElement`, davranışını tanımlayacak bir ilke onayını dışarı aktarmadığından, istemci yapılandırmasını oluşturmak için Svcutil. exe ' yi kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="28aa5-151">You cannot use Svcutil.exe to generate the client configuration because the `CustomTextMessageBindingElement` does not export a policy assertion to describe its behavior.</span></span> <span data-ttu-id="28aa5-152">Bağlama öğesi tarafından uygulanan davranışı veya yeteneği açıklayan özel bir ilke onayını dışarı aktarmak için genellikle <xref:System.ServiceModel.Description.IPolicyExportExtension> arabirimini özel bir bağlama öğesine uygulamalısınız.</span><span class="sxs-lookup"><span data-stu-id="28aa5-152">You should generally implement the <xref:System.ServiceModel.Description.IPolicyExportExtension> interface on a custom binding element to export a custom policy assertion that describes the behavior or capability implemented by the binding element.</span></span> <span data-ttu-id="28aa5-153">Özel bağlama öğesi için bir ilke onayını dışarı aktarmanın bir örneği için bkz. [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) Sample.</span><span class="sxs-lookup"><span data-stu-id="28aa5-153">For an example of how to export a policy assertion for a custom binding element, see the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>

## <a name="message-encoding-binding-configuration-handler"></a><span data-ttu-id="28aa5-154">İleti kodlama bağlama yapılandırma Işleyicisi</span><span class="sxs-lookup"><span data-stu-id="28aa5-154">Message Encoding Binding Configuration Handler</span></span>
<span data-ttu-id="28aa5-155">Önceki bölümde özel metin iletisi kodlayıcının programlı olarak nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="28aa5-155">The previous section shows how to use the custom text message encoder programmatically.</span></span> <span data-ttu-id="28aa5-156">`CustomTextMessageEncodingBindingSection`, bir yapılandırma dosyası içinde özel bir metin iletisi Kodlayıcısı kullanımını belirtmenize olanak tanıyan bir yapılandırma işleyicisi uygular.</span><span class="sxs-lookup"><span data-stu-id="28aa5-156">The `CustomTextMessageEncodingBindingSection` implements a configuration handler that allows you to specify the use of a custom text message encoder within a configuration file.</span></span> <span data-ttu-id="28aa5-157">`CustomTextMessageEncodingBindingSection` sınıfı <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> sınıfından türetilir.</span><span class="sxs-lookup"><span data-stu-id="28aa5-157">The `CustomTextMessageEncodingBindingSection` class derives from the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> class.</span></span> <span data-ttu-id="28aa5-158">`BindingElementType` özelliği, bu bölüm için oluşturulacak bağlama öğesi türünün yapılandırma sistemine bildirir.</span><span class="sxs-lookup"><span data-stu-id="28aa5-158">The `BindingElementType` property informs the configuration system of the type of binding element to create for this section.</span></span>

<span data-ttu-id="28aa5-159">`CustomTextMessageBindingElement` tarafından tanımlanan tüm ayarlar `CustomTextMessageEncodingBindingSection`özellikler olarak gösterilir.</span><span class="sxs-lookup"><span data-stu-id="28aa5-159">All of the settings defined by `CustomTextMessageBindingElement` are exposed as the properties in the `CustomTextMessageEncodingBindingSection`.</span></span> <span data-ttu-id="28aa5-160"><xref:System.Configuration.ConfigurationPropertyAttribute>, yapılandırma öğesi özniteliklerinin özelliklerle eşlenmesiyle ve özniteliği ayarlanmamışsa varsayılan değerleri ayarlamada yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="28aa5-160">The <xref:System.Configuration.ConfigurationPropertyAttribute> assists in mapping the configuration element attributes to the properties and setting default values if the attribute is not set.</span></span> <span data-ttu-id="28aa5-161">Yapılandırma değerleri yüklendikten ve bu türün özelliklerine uygulandıktan sonra, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> metodu çağrılır ve bu, özellikleri bir bağlama öğesinin somut örneğine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="28aa5-161">After the values from configuration are loaded and applied to the properties of the type, the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> method is called, which converts the properties into a concrete instance of a binding element.</span></span>

<span data-ttu-id="28aa5-162">Bu yapılandırma işleyicisi, hizmet veya istemcinin App. config veya Web. config dosyasında aşağıdaki gösterimiyle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="28aa5-162">This configuration handler maps to the following representation in the App.config or Web.config for the service or client.</span></span>

```xml
<customTextMessageEncoding encoding="utf-8" contentType="text/xml" messageVersion="Soap11Addressing1" />
```

<span data-ttu-id="28aa5-163">Örnek ISO-8859-1 kodlamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="28aa5-163">The sample uses the ISO-8859-1 encoding.</span></span>

<span data-ttu-id="28aa5-164">Bu yapılandırma işleyicisini kullanmak için, aşağıdaki yapılandırma öğesi kullanılarak kaydedilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="28aa5-164">To use this configuration handler it must be registered using the following configuration element.</span></span>

```xml
<extensions>
    <bindingElementExtensions>
        <add name="customTextMessageEncoding" type=" 
Microsoft.ServiceModel.Samples.CustomTextMessageEncodingBindingSection, 
                  CustomTextMessageEncoder" />
    </bindingElementExtensions>
</extensions>
```
