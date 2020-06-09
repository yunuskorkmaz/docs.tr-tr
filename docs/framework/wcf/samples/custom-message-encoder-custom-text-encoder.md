---
title: 'Özel İleti Kodlayıcısı: Özel Metin Kodlayıcısı'
ms.date: 03/30/2017
ms.assetid: 68ff5c74-3d33-4b44-bcae-e1d2f5dea0de
ms.openlocfilehash: b60fa2a84520ad208d435a0c9284c19b5de8e989
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600613"
---
# <a name="custom-message-encoder-custom-text-encoder"></a><span data-ttu-id="2ab78-102">Özel İleti Kodlayıcısı: Özel Metin Kodlayıcısı</span><span class="sxs-lookup"><span data-stu-id="2ab78-102">Custom Message Encoder: Custom Text Encoder</span></span>

<span data-ttu-id="2ab78-103">Bu örnek, Windows Communication Foundation (WCF) kullanarak özel metin iletisi Kodlayıcısı 'nın nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2ab78-103">This sample demonstrates how to implement a custom text message encoder using Windows Communication Foundation (WCF).</span></span>

> [!WARNING]
> <span data-ttu-id="2ab78-104">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="2ab78-104">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2ab78-105">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="2ab78-105">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="2ab78-106">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="2ab78-106">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2ab78-107">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="2ab78-107">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Text`

<span data-ttu-id="2ab78-108"><xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>WCF 'de yalnızca UTF-8, UTF-16 ve Big-endian Unicode kodlamaları desteklenir.</span><span class="sxs-lookup"><span data-stu-id="2ab78-108">The <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> of WCF supports only the UTF-8, UTF-16 and big-endian Unicode encodings.</span></span> <span data-ttu-id="2ab78-109">Bu örnekteki özel metin iletisi Kodlayıcısı, birlikte çalışabilirlik için gerekebilecek tüm platform tarafından desteklenen karakter kodlamalarını destekler.</span><span class="sxs-lookup"><span data-stu-id="2ab78-109">The custom text message encoder in this sample supports all platform-supported character encodings that may be required for interoperability.</span></span> <span data-ttu-id="2ab78-110">Örnek, bir istemci konsol programı (. exe), Internet Information Services (IIS) tarafından barındırılan bir hizmet kitaplığı (. dll) ve bir SMS mesajı Kodlayıcı kitaplığı (. dll) içerir.</span><span class="sxs-lookup"><span data-stu-id="2ab78-110">The sample consists of a client console program (.exe), a service library (.dll) hosted by Internet Information Services (IIS), and a text message encoder library (.dll).</span></span> <span data-ttu-id="2ab78-111">Hizmet, istek-yanıt iletişim modelini tanımlayan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="2ab78-111">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="2ab78-112">Sözleşme, `ICalculator` matematik işlemlerini (ekleme, çıkarma, çarpma ve bölme) sunan arabirim tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="2ab78-112">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide).</span></span> <span data-ttu-id="2ab78-113">İstemci belirli bir matematik işlemine zaman uyumlu istekler yapar ve hizmet sonuçla yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="2ab78-113">The client makes synchronous requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="2ab78-114">Hem istemci hem de hizmet `CustomTextMessageEncoder` varsayılan yerine ' nı kullanır <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="2ab78-114">Both client and service uses the `CustomTextMessageEncoder` instead of the default <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.</span></span>

<span data-ttu-id="2ab78-115">Özel kodlayıcı uygulamasının bir ileti Kodlayıcısı fabrikası, bir ileti Kodlayıcısı, ileti kodlama bağlama öğesi ve yapılandırma işleyicisi oluşur ve şunları gösterir:</span><span class="sxs-lookup"><span data-stu-id="2ab78-115">The custom encoder implementation consists of a message encoder factory, a message encoder, a message encoding binding element and a configuration handler, and demonstrates the following:</span></span>

- <span data-ttu-id="2ab78-116">Özel kodlayıcı ve kodlayıcı fabrikası oluşturma.</span><span class="sxs-lookup"><span data-stu-id="2ab78-116">Building a custom encoder and encoder factory.</span></span>

- <span data-ttu-id="2ab78-117">Özel bir kodlayıcı için bağlama öğesi oluşturma.</span><span class="sxs-lookup"><span data-stu-id="2ab78-117">Creating a binding element for a custom encoder.</span></span>

- <span data-ttu-id="2ab78-118">Özel bağlama öğelerini tümleştirmek için özel bağlama yapılandırması kullanma.</span><span class="sxs-lookup"><span data-stu-id="2ab78-118">Using the custom binding configuration for integrating custom binding elements.</span></span>

- <span data-ttu-id="2ab78-119">Özel bir bağlama öğesinin dosya yapılandırmasına izin vermek için özel bir yapılandırma işleyicisi geliştirme.</span><span class="sxs-lookup"><span data-stu-id="2ab78-119">Developing a custom configuration handler to allow file configuration of a custom binding element.</span></span>

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2ab78-120">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="2ab78-120">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="2ab78-121">Aşağıdaki komutu kullanarak ASP.NET 4,0 ' ü yükler.</span><span class="sxs-lookup"><span data-stu-id="2ab78-121">Install ASP.NET 4.0 using the following command.</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="2ab78-122">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="2ab78-122">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="2ab78-123">Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="2ab78-123">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="2ab78-124">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="2ab78-124">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

## <a name="message-encoder-factory-and-the-message-encoder"></a><span data-ttu-id="2ab78-125">İleti Kodlayıcısı fabrikası ve Ileti Kodlayıcısı</span><span class="sxs-lookup"><span data-stu-id="2ab78-125">Message Encoder Factory and the Message Encoder</span></span>

<span data-ttu-id="2ab78-126"><xref:System.ServiceModel.ServiceHost>Veya istemci kanalı açıldığında tasarım zamanı bileşeni tarafından `CustomTextMessageBindingElement` oluşturulur `CustomTextMessageEncoderFactory` .</span><span class="sxs-lookup"><span data-stu-id="2ab78-126">When the <xref:System.ServiceModel.ServiceHost> or the client channel is opened, the design time component `CustomTextMessageBindingElement` creates the `CustomTextMessageEncoderFactory`.</span></span> <span data-ttu-id="2ab78-127">Fabrika, öğesini oluşturur `CustomTextMessageEncoder` .</span><span class="sxs-lookup"><span data-stu-id="2ab78-127">The factory creates the `CustomTextMessageEncoder`.</span></span> <span data-ttu-id="2ab78-128">İleti Kodlayıcısı hem akış modunda hem de arabelleğe alınmış modda çalışır.</span><span class="sxs-lookup"><span data-stu-id="2ab78-128">The message encoder operates both in the streaming mode and the buffered mode.</span></span> <span data-ttu-id="2ab78-129"><xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter> İletileri sırasıyla okumak ve yazmak için ve kullanır.</span><span class="sxs-lookup"><span data-stu-id="2ab78-129">It uses the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> to read and write the messages respectively.</span></span> <span data-ttu-id="2ab78-130">Yalnızca UTF-8, UTF-16 ve Big-endian Unicode 'u destekleyen, iyileştirilmiş XML okuyucuları ve WCF yazarlarının aksine, bu okuyucular ve yazarlar tüm platform tarafından desteklenen kodlamayı destekler.</span><span class="sxs-lookup"><span data-stu-id="2ab78-130">As opposed to the optimized XML readers and writers of WCF that support only UTF-8, UTF-16 and big-endian Unicode, these readers and writers support all platform-supported encoding.</span></span>

<span data-ttu-id="2ab78-131">Aşağıdaki kod örneğinde CustomTextMessageEncoder gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2ab78-131">The following code example shows the CustomTextMessageEncoder.</span></span>

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

<span data-ttu-id="2ab78-132">Aşağıdaki kod örneği, ileti Kodlayıcısı fabrikasının nasıl oluşturulacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="2ab78-132">The following code example shows how to build the message encoder factory.</span></span>

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

## <a name="message-encoding-binding-element"></a><span data-ttu-id="2ab78-133">İleti kodlama bağlama öğesi</span><span class="sxs-lookup"><span data-stu-id="2ab78-133">Message Encoding Binding Element</span></span>

<span data-ttu-id="2ab78-134">Bağlama öğeleri, WCF çalışma zamanı yığınının yapılandırmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="2ab78-134">The binding elements allow the configuration of the WCF run-time stack.</span></span> <span data-ttu-id="2ab78-135">Özel ileti Kodlayıcısı 'nı bir WCF uygulamasında kullanmak için, çalışma zamanı yığınında uygun düzeyde uygun ayarlarla ileti Kodlayıcısı fabrikasını oluşturan bir Binding öğesi gereklidir.</span><span class="sxs-lookup"><span data-stu-id="2ab78-135">To use the custom message encoder in a WCF application, a binding element is required that creates the message encoder factory with the appropriate settings at the appropriate level in the run-time stack.</span></span>

<span data-ttu-id="2ab78-136">, `CustomTextMessageBindingElement` <xref:System.ServiceModel.Channels.BindingElement> Temel sınıftan türetilir ve <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> sınıfından devralır.</span><span class="sxs-lookup"><span data-stu-id="2ab78-136">The `CustomTextMessageBindingElement` derives from the <xref:System.ServiceModel.Channels.BindingElement> base class and inherits from the <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> class.</span></span> <span data-ttu-id="2ab78-137">Bu, diğer WCF bileşenlerinin bu bağlama öğesini bir ileti kodlama bağlama öğesi olarak tanımasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="2ab78-137">This allows other WCF components to recognize this binding element as being a message encoding binding element.</span></span> <span data-ttu-id="2ab78-138">Uygulamasının uygulanması, <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> uygun ayarlarla eşleşen ileti Kodlayıcısı fabrikasının bir örneğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="2ab78-138">The implementation of <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> returns an instance of the matching message encoder factory with appropriate settings.</span></span>

<span data-ttu-id="2ab78-139">,, `CustomTextMessageBindingElement` Ve özellikleri için ayarları sunar `MessageVersion` `ContentType` `Encoding` .</span><span class="sxs-lookup"><span data-stu-id="2ab78-139">The `CustomTextMessageBindingElement` exposes settings for `MessageVersion`, `ContentType`, and `Encoding` through properties.</span></span> <span data-ttu-id="2ab78-140">Kodlayıcı hem Soap11Addressing hem de Soap12Addressing1 sürümlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="2ab78-140">The encoder supports both Soap11Addressing and Soap12Addressing1 versions.</span></span> <span data-ttu-id="2ab78-141">Varsayılan değer Soap11Addressing1 ' dir.</span><span class="sxs-lookup"><span data-stu-id="2ab78-141">The default is Soap11Addressing1.</span></span> <span data-ttu-id="2ab78-142">Varsayılan değeri `ContentType` "text/xml" dir.</span><span class="sxs-lookup"><span data-stu-id="2ab78-142">The default value of the `ContentType` is "text/xml".</span></span> <span data-ttu-id="2ab78-143">`Encoding`Özelliği, istenen karakter kodlamasının değerini ayarlamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="2ab78-143">The `Encoding` property allows you to set the value of the desired character encoding.</span></span> <span data-ttu-id="2ab78-144">Örnek istemci ve hizmet, WCF tarafından desteklenmeyen ISO-8859-1 (Latin1) karakter kodlamasını kullanır <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="2ab78-144">The sample client and service uses the ISO-8859-1 (Latin1) character encoding, which is not supported by the <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> of WCF.</span></span>

<span data-ttu-id="2ab78-145">Aşağıdaki kod, özel metin iletisi Kodlayıcısı kullanılarak bağlama programlı bir şekilde nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2ab78-145">The following code shows how to programmatically create the binding using the custom text message encoder.</span></span>

```csharp
ICollection<BindingElement> bindingElements = new List<BindingElement>();
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();
CustomTextMessageBindingElement textBindingElement = new CustomTextMessageBindingElement();
bindingElements.Add(textBindingElement);
bindingElements.Add(httpBindingElement);
CustomBinding binding = new CustomBinding(bindingElements);
```

## <a name="adding-metadata-support-to-the-message-encoding-binding-element"></a><span data-ttu-id="2ab78-146">Ileti kodlama bağlama öğesine meta veri desteği ekleniyor</span><span class="sxs-lookup"><span data-stu-id="2ab78-146">Adding Metadata Support to the Message Encoding Binding Element</span></span>

<span data-ttu-id="2ab78-147">Öğesinden türetilen herhangi bir tür, <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> hizmet için oluşturulan wsdl BELGESINDE SOAP bağlamanın sürümünü güncelleştirmekten sorumludur.</span><span class="sxs-lookup"><span data-stu-id="2ab78-147">Any type that derives from <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> is responsible for updating the version of the SOAP binding in the WSDL document generated for the service.</span></span> <span data-ttu-id="2ab78-148">Bu, `ExportEndpoint` yöntemi arabirim üzerinde uygulayarak <xref:System.ServiceModel.Description.IWsdlExportExtension> ve sonra oluşturulan wsdl 'nin değiştirilerek yapılır.</span><span class="sxs-lookup"><span data-stu-id="2ab78-148">This is done by implementing the `ExportEndpoint` method on the <xref:System.ServiceModel.Description.IWsdlExportExtension> interface and then modifying the generated WSDL.</span></span> <span data-ttu-id="2ab78-149">Bu örnekte, ' `CustomTextMessageBindingElement` den WSDL dışarı aktarma mantığını kullanır `TextMessageEncodingBindingElement` .</span><span class="sxs-lookup"><span data-stu-id="2ab78-149">In this sample, the `CustomTextMessageBindingElement` uses the WSDL export logic from the `TextMessageEncodingBindingElement`.</span></span>

<span data-ttu-id="2ab78-150">Bu örnek için, istemci yapılandırması el ile yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="2ab78-150">For this sample, the client configuration is hand configured.</span></span> <span data-ttu-id="2ab78-151">`CustomTextMessageBindingElement`Davranışını tanımlayacak bir ilke onayını dışarı aktarmadığından, istemci yapılandırmasını oluşturmak Için Svcutil. exe ' yi kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="2ab78-151">You cannot use Svcutil.exe to generate the client configuration because the `CustomTextMessageBindingElement` does not export a policy assertion to describe its behavior.</span></span> <span data-ttu-id="2ab78-152"><xref:System.ServiceModel.Description.IPolicyExportExtension>Bağlama öğesi tarafından uygulanan davranışı veya özelliği açıklayan özel bir ilke onayını dışarı aktarmak için genellikle bir özel bağlama öğesi üzerinde arabirimini uygulamalısınız.</span><span class="sxs-lookup"><span data-stu-id="2ab78-152">You should generally implement the <xref:System.ServiceModel.Description.IPolicyExportExtension> interface on a custom binding element to export a custom policy assertion that describes the behavior or capability implemented by the binding element.</span></span> <span data-ttu-id="2ab78-153">Özel bağlama öğesi için bir ilke onayını dışarı aktarmanın bir örneği için bkz. [Transport: UDP](transport-udp.md) Sample.</span><span class="sxs-lookup"><span data-stu-id="2ab78-153">For an example of how to export a policy assertion for a custom binding element, see the [Transport: UDP](transport-udp.md) sample.</span></span>

## <a name="message-encoding-binding-configuration-handler"></a><span data-ttu-id="2ab78-154">İleti kodlama bağlama yapılandırma Işleyicisi</span><span class="sxs-lookup"><span data-stu-id="2ab78-154">Message Encoding Binding Configuration Handler</span></span>
<span data-ttu-id="2ab78-155">Önceki bölümde özel metin iletisi kodlayıcının programlı olarak nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2ab78-155">The previous section shows how to use the custom text message encoder programmatically.</span></span> <span data-ttu-id="2ab78-156">, `CustomTextMessageEncodingBindingSection` Bir yapılandırma dosyası içinde özel bir metin iletisi Kodlayıcısı kullanımını belirtmenize olanak tanıyan bir yapılandırma işleyicisi uygular.</span><span class="sxs-lookup"><span data-stu-id="2ab78-156">The `CustomTextMessageEncodingBindingSection` implements a configuration handler that allows you to specify the use of a custom text message encoder within a configuration file.</span></span> <span data-ttu-id="2ab78-157">`CustomTextMessageEncodingBindingSection`Sınıf sınıfından türetilir <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> .</span><span class="sxs-lookup"><span data-stu-id="2ab78-157">The `CustomTextMessageEncodingBindingSection` class derives from the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> class.</span></span> <span data-ttu-id="2ab78-158">`BindingElementType`Özelliği, bu bölüm için oluşturulacak bağlama öğesi türünün yapılandırma sistemine bildirir.</span><span class="sxs-lookup"><span data-stu-id="2ab78-158">The `BindingElementType` property informs the configuration system of the type of binding element to create for this section.</span></span>

<span data-ttu-id="2ab78-159">Tarafından tanımlanan tüm ayarlar `CustomTextMessageBindingElement` , içindeki özellikler olarak gösterilir `CustomTextMessageEncodingBindingSection` .</span><span class="sxs-lookup"><span data-stu-id="2ab78-159">All of the settings defined by `CustomTextMessageBindingElement` are exposed as the properties in the `CustomTextMessageEncodingBindingSection`.</span></span> <span data-ttu-id="2ab78-160"><xref:System.Configuration.ConfigurationPropertyAttribute>Yapılandırma öğesi özniteliklerini özelliklerine eşleme ve özniteliği ayarlanmamışsa varsayılan değerleri ayarlama konusunda yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="2ab78-160">The <xref:System.Configuration.ConfigurationPropertyAttribute> assists in mapping the configuration element attributes to the properties and setting default values if the attribute is not set.</span></span> <span data-ttu-id="2ab78-161">Yapılandırma değerleri yüklenip, türün özelliklerine uygulandıktan sonra, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> özelliği bir bağlama öğesinin somut örneğine dönüştüren yöntemi çağırılır.</span><span class="sxs-lookup"><span data-stu-id="2ab78-161">After the values from configuration are loaded and applied to the properties of the type, the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> method is called, which converts the properties into a concrete instance of a binding element.</span></span>

<span data-ttu-id="2ab78-162">Bu yapılandırma işleyicisi, hizmet veya istemcinin App. config veya Web. config dosyasında aşağıdaki gösterimiyle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="2ab78-162">This configuration handler maps to the following representation in the App.config or Web.config for the service or client.</span></span>

```xml
<customTextMessageEncoding encoding="utf-8" contentType="text/xml" messageVersion="Soap11Addressing1" />
```

<span data-ttu-id="2ab78-163">Örnek ISO-8859-1 kodlamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="2ab78-163">The sample uses the ISO-8859-1 encoding.</span></span>

<span data-ttu-id="2ab78-164">Bu yapılandırma işleyicisini kullanmak için, aşağıdaki yapılandırma öğesi kullanılarak kaydedilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="2ab78-164">To use this configuration handler it must be registered using the following configuration element.</span></span>

```xml
<extensions>
    <bindingElementExtensions>
        <add name="customTextMessageEncoding" type="
Microsoft.ServiceModel.Samples.CustomTextMessageEncodingBindingSection,
                  CustomTextMessageEncoder" />
    </bindingElementExtensions>
</extensions>
```
