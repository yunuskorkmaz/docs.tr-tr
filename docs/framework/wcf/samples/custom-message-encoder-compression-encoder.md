---
title: 'Özel İleti Kodlayıcısı: Sıkıştırma Kodlayıcısı'
ms.date: 03/30/2017
ms.assetid: 57450b6c-89fe-4b8a-8376-3d794857bfd7
ms.openlocfilehash: db20ec20579d6fcb0ec202920db0d7781b0676df
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600626"
---
# <a name="custom-message-encoder-compression-encoder"></a><span data-ttu-id="cc7ee-102">Özel İleti Kodlayıcısı: Sıkıştırma Kodlayıcısı</span><span class="sxs-lookup"><span data-stu-id="cc7ee-102">Custom Message Encoder: Compression Encoder</span></span>

<span data-ttu-id="cc7ee-103">Bu örnek, Windows Communication Foundation (WCF) platformunu kullanarak nasıl özel bir kodlayıcı uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-103">This sample demonstrates how to implement a custom encoder using the Windows Communication Foundation (WCF) platform.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cc7ee-104">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-104">The samples may already be installed on your machine.</span></span> <span data-ttu-id="cc7ee-105">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-105">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="cc7ee-106">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="cc7ee-106">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cc7ee-107">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-107">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`

## <a name="sample-details"></a><span data-ttu-id="cc7ee-108">Örnek Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="cc7ee-108">Sample Details</span></span>

<span data-ttu-id="cc7ee-109">Bu örnek, bir istemci konsolu programından (. exe), şirket içinde barındırılan bir hizmet konsolu programından (. exe) ve bir sıkıştırma ileti Kodlayıcısı kitaplığından (. dll) oluşur.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-109">This sample consists of a client console program (.exe), a self-hosted service console program (.exe) and a compression message encoder library (.dll).</span></span> <span data-ttu-id="cc7ee-110">Hizmet, istek-yanıt iletişim modelini tanımlayan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-110">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="cc7ee-111">Sözleşme, `ISampleServer` temel dize yankılanma işlemlerini (ve) kullanıma sunan arabirim tarafından tanımlanır `Echo` `BigEcho` .</span><span class="sxs-lookup"><span data-stu-id="cc7ee-111">The contract is defined by the `ISampleServer` interface, which exposes basic string echoing operations (`Echo` and `BigEcho`).</span></span> <span data-ttu-id="cc7ee-112">İstemci, iletiyi istemciye geri tekrarlayarak, belirli bir işleme ve hizmet yanıtlarını zaman uyumlu istekler yapar.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-112">The client makes synchronous requests to a given operation and the service replies by repeating the message back to the client.</span></span> <span data-ttu-id="cc7ee-113">İstemci ve hizmet etkinliği konsol penceresinde görünür.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-113">Client and service activity is visible in the console windows.</span></span> <span data-ttu-id="cc7ee-114">Bu örneğin amacı, bir özel kodlayıcının nasıl yazılacağını ve bir iletinin kabloda sıkıştırılma etkisini gösterir.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-114">The intent of this sample is to show how to write a custom encoder and demonstrate the impact of compression of a message on the wire.</span></span> <span data-ttu-id="cc7ee-115">İleti boyutunu, işlem süresini veya her ikisini de hesaplamak için, sıkıştırma iletisi kodlayıcıya izleme ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-115">You can add instrumentation to the compression message encoder to calculate message size, processing time, or both.</span></span>

> [!NOTE]
> <span data-ttu-id="cc7ee-116">.NET Framework 4 ' te, sunucu sıkıştırılmış bir yanıt gönderiyorsa (GZip veya söndür gibi bir algoritmayla oluşturulmuş) WCF istemcisinde otomatik açma özelliği etkinleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-116">In the .NET Framework 4, automatic decompression has been enabled on a WCF client if the server is sending a compressed response (created with an algorithm such as GZip or Deflate).</span></span> <span data-ttu-id="cc7ee-117">Hizmet, Internet Information Server 'da (IIS) Web 'de barındırılıyorsa, hizmetin sıkıştırılmış bir yanıt gönderebilmesi için IIS yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-117">If the service is Web-hosted in Internet Information Server (IIS), then IIS can be configured for the service to send a compressed response.</span></span> <span data-ttu-id="cc7ee-118">Bu örnek, gereksinim hem istemcide hem de hizmette sıkıştırma yapmak ve sıkıştırmayı açmak ya da hizmetin şirket içinde barındırılması durumunda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-118">This sample can be used if the requirement is to do compression and decompression on both the client and the service or if the service is self-hosted.</span></span>

<span data-ttu-id="cc7ee-119">Örnek, bir WCF uygulamasında özel bir ileti Kodlayıcısı oluşturmayı ve tümleştirmeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-119">The sample demonstrates how to build and integrate a custom message encoder into a WCF application.</span></span> <span data-ttu-id="cc7ee-120">GZipEncoder. dll kitaplığı hem istemci hem de hizmetle birlikte dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-120">The library GZipEncoder.dll is deployed with both the client and the service.</span></span> <span data-ttu-id="cc7ee-121">Bu örnek ayrıca iletileri sıkıştırma etkisini de gösterir.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-121">This sample also demonstrates the impact of compressing messages.</span></span> <span data-ttu-id="cc7ee-122">GZipEncoder. dll içindeki kod şunları gösterir:</span><span class="sxs-lookup"><span data-stu-id="cc7ee-122">The code in GZipEncoder.dll demonstrates the following:</span></span>

- <span data-ttu-id="cc7ee-123">Özel kodlayıcı ve kodlayıcı fabrikası oluşturma.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-123">Building a custom encoder and encoder factory.</span></span>

- <span data-ttu-id="cc7ee-124">Özel bir kodlayıcı için bağlama öğesi geliştirme.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-124">Developing a binding element for a custom encoder.</span></span>

- <span data-ttu-id="cc7ee-125">Özel bağlama öğelerini tümleştirmek için özel bağlama yapılandırması kullanma.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-125">Using the custom binding configuration for integrating custom binding elements.</span></span>

- <span data-ttu-id="cc7ee-126">Özel bir bağlama öğesinin dosya yapılandırmasına izin vermek için özel bir yapılandırma işleyicisi geliştirme.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-126">Developing a custom configuration handler to allow file configuration of a custom binding element.</span></span>

<span data-ttu-id="cc7ee-127">Daha önce belirtildiği gibi, özel bir kodlayıcıda uygulanan birkaç katman vardır.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-127">As indicated previously, there are several layers that are implemented in a custom encoder.</span></span> <span data-ttu-id="cc7ee-128">Bu katmanların her biri arasındaki ilişkiyi daha iyi göstermek için, hizmet başlatma için daha basit bir olay sırası aşağıdaki listede verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="cc7ee-128">To better illustrate the relationship between each of these layers, a simplified order of events for service start-up is in the following list:</span></span>

1. <span data-ttu-id="cc7ee-129">Sunucu başlatılır.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-129">The server starts.</span></span>

2. <span data-ttu-id="cc7ee-130">Yapılandırma bilgileri okundu.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-130">The configuration information is read.</span></span>

    1. <span data-ttu-id="cc7ee-131">Hizmet yapılandırması özel yapılandırma işleyicisini kaydeder.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-131">The service configuration registers the custom configuration handler.</span></span>

    2. <span data-ttu-id="cc7ee-132">Hizmet ana bilgisayarı oluşturulup açılır.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-132">The service host is created and opened.</span></span>

    3. <span data-ttu-id="cc7ee-133">Özel yapılandırma öğesi, özel bağlama öğesini oluşturur ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-133">The custom configuration element creates and returns the custom binding element.</span></span>

    4. <span data-ttu-id="cc7ee-134">Özel bağlama öğesi bir ileti Kodlayıcısı fabrikası oluşturur ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-134">The custom binding element creates and returns a message encoder factory.</span></span>

3. <span data-ttu-id="cc7ee-135">İleti alındı.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-135">A message is received.</span></span>

4. <span data-ttu-id="cc7ee-136">İleti Kodlayıcısı fabrikası iletiyi okumak ve yanıtı yazmak için bir ileti Kodlayıcısı döndürür.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-136">The message encoder factory returns a message encoder for reading in the message and writing out the response.</span></span>

5. <span data-ttu-id="cc7ee-137">Kodlayıcı katmanı bir sınıf fabrikası olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-137">The encoder layer is implemented as a class factory.</span></span> <span data-ttu-id="cc7ee-138">Özel Kodlayıcı için yalnızca kodlayıcı sınıf fabrikası genel kullanıma açık olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-138">Only the encoder class factory must be publicly exposed for the custom encoder.</span></span> <span data-ttu-id="cc7ee-139">Factory nesnesi, <xref:System.ServiceModel.ServiceHost> veya nesnesi oluşturulduğunda Binding öğesi tarafından döndürülür <xref:System.ServiceModel.ChannelFactory%601> .</span><span class="sxs-lookup"><span data-stu-id="cc7ee-139">The factory object is returned by the binding element when the <xref:System.ServiceModel.ServiceHost> or <xref:System.ServiceModel.ChannelFactory%601> object is created.</span></span> <span data-ttu-id="cc7ee-140">İleti kodlayıcıları, ara belleğe alınmış veya akış modunda çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-140">Message encoders can operate in a buffered or streaming mode.</span></span> <span data-ttu-id="cc7ee-141">Bu örnek, hem arabellekli modu hem de akış modunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-141">This sample demonstrates both buffered mode and streaming mode.</span></span>

<span data-ttu-id="cc7ee-142">Her mod için soyut sınıfta bir eşlik eden `ReadMessage` ve `WriteMessage` yöntemi vardır `MessageEncoder` .</span><span class="sxs-lookup"><span data-stu-id="cc7ee-142">For each mode there is an accompanying `ReadMessage` and `WriteMessage` method on the abstract `MessageEncoder` class.</span></span> <span data-ttu-id="cc7ee-143">Bu yöntemlerde kodlama işinin çoğu gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-143">A majority of the encoding work takes place in these methods.</span></span> <span data-ttu-id="cc7ee-144">Örnek, varolan metni ve ikili ileti kodlayıcıları ' nı sarmalar.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-144">The sample wraps the existing text and binary message encoders.</span></span> <span data-ttu-id="cc7ee-145">Bu, örneğin, iletilerin tel gösterimini okuma ve yazma yetkisini iç kodlayıcıya devredebilir ve sıkıştırma kodlayıcının sonuçları sıkıştırmak veya sıkıştırmasını açmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-145">This allows the sample to delegate the reading and writing of the wire representation of messages to the inner encoder and allows the compression encoder to compress or decompress the results.</span></span> <span data-ttu-id="cc7ee-146">İleti kodlama için bir işlem hattı olmadığından, bu, WCF 'de birden çok kodlayıcıda kullanılmasına yönelik tek modeldir.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-146">Because there is no pipeline for message encoding, this is the only model for using multiple encoders in WCF.</span></span> <span data-ttu-id="cc7ee-147">İleti açıldıktan sonra, ortaya çıkan ileti, işlemek için kanal yığınının yığınını iletilir.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-147">Once the message has been decompressed, the resulting message is passed up the stack for the channel stack to handle.</span></span> <span data-ttu-id="cc7ee-148">Sıkıştırma sırasında, elde edilen sıkıştırılmış ileti doğrudan verilen akışa yazılır.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-148">During compression, the resulting compressed message is written directly to the stream provided.</span></span>

<span data-ttu-id="cc7ee-149">Bu örnek `CompressBuffer` `DecompressBuffer` , sınıfını kullanmak üzere arabelleklerden akışlara dönüştürme gerçekleştirmek için yardımcı yöntemleri (ve) kullanır `GZipStream` .</span><span class="sxs-lookup"><span data-stu-id="cc7ee-149">This sample uses helper methods (`CompressBuffer` and `DecompressBuffer`) to perform conversion from buffers to streams to use the `GZipStream` class.</span></span>

<span data-ttu-id="cc7ee-150">Arabelleğe alınmış `ReadMessage` ve `WriteMessage` sınıflar `BufferManager` sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-150">The buffered `ReadMessage` and `WriteMessage` classes make use of the `BufferManager` class.</span></span> <span data-ttu-id="cc7ee-151">Kodlayıcı yalnızca kodlayıcı fabrikası aracılığıyla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-151">The encoder is accessible only through the encoder factory.</span></span> <span data-ttu-id="cc7ee-152">Soyut `MessageEncoderFactory` sınıf, `Encoder` geçerli kodlayıcıya ve `CreateSessionEncoder` oturumları destekleyen bir kodlayıcı oluşturmak için adlı bir yönteme erişim için adlı bir özellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-152">The abstract `MessageEncoderFactory` class provides a property named `Encoder` for accessing the current encoder and a method named `CreateSessionEncoder` for creating an encoder that supports sessions.</span></span> <span data-ttu-id="cc7ee-153">Bu tür bir kodlayıcı, kanalın oturumları desteklediği, sıralandığı ve güvenilir olduğu senaryolarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-153">Such an encoder can be used in the scenario where the channel supports sessions, is ordered and is reliable.</span></span> <span data-ttu-id="cc7ee-154">Bu senaryo, hatta yazılı verilerin her oturumunda iyileştirmeye olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-154">This scenario allows for optimization in each session of the data written to the wire.</span></span> <span data-ttu-id="cc7ee-155">Bu istenmiyorsa, temel yöntemin aşırı yüklenmiş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-155">If this is not desired, the base method should not be overloaded.</span></span> <span data-ttu-id="cc7ee-156">`Encoder`Özelliği, oturum-daha az kodlayıcıya erişim mekanizması sağlar ve yöntemin varsayılan uygulanması `CreateSessionEncoder` özelliğin değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-156">The `Encoder` property provides a mechanism for accessing the session-less encoder and the default implementation of the `CreateSessionEncoder` method returns the value of the property.</span></span> <span data-ttu-id="cc7ee-157">Örnek, sıkıştırma sağlamak için mevcut bir Kodlayıcısı sarmaladığı için, `MessageEncoderFactory` uygulama `MessageEncoderFactory` iç Kodlayıcı fabrikasını temsil eden bir öğesini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-157">Because the sample wraps an existing encoder to provide compression, the `MessageEncoderFactory` implementation accepts a `MessageEncoderFactory` that represents the inner encoder factory.</span></span>

<span data-ttu-id="cc7ee-158">Kodlayıcı ve kodlayıcı fabrikası tanımlandığına göre, bunlar bir WCF istemcisi ve hizmeti ile birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-158">Now that the encoder and encoder factory are defined, they can be used with a WCF client and service.</span></span> <span data-ttu-id="cc7ee-159">Ancak, bu kodlayıcılara kanal yığınına eklenmeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-159">However, these encoders must be added to the channel stack.</span></span> <span data-ttu-id="cc7ee-160">Ve sınıflarından sınıfları türetebilirsiniz <xref:System.ServiceModel.ServiceHost> <xref:System.ServiceModel.ChannelFactory%601> ve `OnInitialize` Bu kodlayıcı fabrikasını el ile eklemek için yöntemleri geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-160">You can derive classes from the <xref:System.ServiceModel.ServiceHost> and <xref:System.ServiceModel.ChannelFactory%601> classes and override the `OnInitialize` methods to add this encoder factory manually.</span></span> <span data-ttu-id="cc7ee-161">Ayrıca, özel bağlama öğesi aracılığıyla Kodlayıcı fabrikasını kullanıma sunabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-161">You can also expose the encoder factory through a custom binding element.</span></span>

<span data-ttu-id="cc7ee-162">Yeni bir özel bağlama öğesi oluşturmak için sınıfından bir sınıf türetebilirsiniz <xref:System.ServiceModel.Channels.BindingElement> .</span><span class="sxs-lookup"><span data-stu-id="cc7ee-162">To create a new custom binding element, derive a class from the <xref:System.ServiceModel.Channels.BindingElement> class.</span></span> <span data-ttu-id="cc7ee-163">Ancak birkaç tür bağlama öğesi vardır.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-163">There are, however, several types of binding elements.</span></span> <span data-ttu-id="cc7ee-164">Özel bağlama öğesinin bir ileti kodlama bağlama öğesi olarak tanındığından emin olmak için, öğesini de uygulamanız gerekir <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="cc7ee-164">To ensure that the custom binding element is recognized as a message encoding binding element, you also must implement the <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.</span></span> <span data-ttu-id="cc7ee-165">, <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> `CreateMessageEncoderFactory` Eşleşen ileti Kodlayıcısı fabrikasının bir örneğini döndürmek için uygulanan yeni bir ileti Kodlayıcısı Fabrikası () oluşturmak için bir yöntem sunar.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-165">The <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> exposes a method for creating a new message encoder factory (`CreateMessageEncoderFactory`), which is implemented to return an instance of the matching message encoder factory.</span></span> <span data-ttu-id="cc7ee-166">Ek olarak,, <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> adresleme sürümünü belirten bir özelliğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-166">Additionally, the <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> has a property to indicate the addressing version.</span></span> <span data-ttu-id="cc7ee-167">Bu örnek varolan kodlayıcıları sarmaladığı için, örnek uygulama aynı zamanda var olan Kodlayıcı bağlama öğelerini sarmalanmış ve bir iç Kodlayıcı bağlama öğesini bir parametre olarak oluşturucuya alır ve bunu bir özellik aracılığıyla gösterir.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-167">Because this sample wraps the existing encoders, the sample implementation also wraps the existing encoder binding elements and takes an inner encoder binding element as a parameter to the constructor and exposes it through a property.</span></span> <span data-ttu-id="cc7ee-168">Aşağıdaki örnek kod, sınıfının uygulamasını gösterir `GZipMessageEncodingBindingElement` .</span><span class="sxs-lookup"><span data-stu-id="cc7ee-168">The following sample code shows the implementation of the `GZipMessageEncodingBindingElement` class.</span></span>

```csharp
public sealed class GZipMessageEncodingBindingElement
                        : MessageEncodingBindingElement //BindingElement
                        , IPolicyExportExtension
{

    //We use an inner binding element to store information
    //required for the inner encoder.
    MessageEncodingBindingElement innerBindingElement;

        //By default, use the default text encoder as the inner encoder.
        public GZipMessageEncodingBindingElement()
            : this(new TextMessageEncodingBindingElement()) { }

    public GZipMessageEncodingBindingElement(MessageEncodingBindingElement messageEncoderBindingElement)
    {
        this.innerBindingElement = messageEncoderBindingElement;
    }

    public MessageEncodingBindingElement InnerMessageEncodingBindingElement
    {
        get { return innerBindingElement; }
        set { innerBindingElement = value; }
    }

    //Main entry point into the encoder binding element.
    // Called by WCF to get the factory that creates the
    //message encoder.
    public override MessageEncoderFactory CreateMessageEncoderFactory()
    {
        return new
GZipMessageEncoderFactory(innerBindingElement.CreateMessageEncoderFactory());
    }

    public override MessageVersion MessageVersion
    {
        get { return innerBindingElement.MessageVersion; }
        set { innerBindingElement.MessageVersion = value; }
    }

    public override BindingElement Clone()
    {
        return new
        GZipMessageEncodingBindingElement(this.innerBindingElement);
    }

    public override T GetProperty<T>(BindingContext context)
    {
        if (typeof(T) == typeof(XmlDictionaryReaderQuotas))
        {
            return innerBindingElement.GetProperty<T>(context);
        }
        else
        {
            return base.GetProperty<T>(context);
        }
    }

    public override IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)
    {
        if (context == null)
            throw new ArgumentNullException("context");

        context.BindingParameters.Add(this);
        return context.BuildInnerChannelFactory<TChannel>();
    }

    public override IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)
    {
        if (context == null)
            throw new ArgumentNullException("context");

        context.BindingParameters.Add(this);
        return context.BuildInnerChannelListener<TChannel>();
    }

    public override bool CanBuildChannelListener<TChannel>(BindingContext context)
    {
        if (context == null)
            throw new ArgumentNullException("context");

        context.BindingParameters.Add(this);
        return context.CanBuildInnerChannelListener<TChannel>();
    }

    void IPolicyExportExtension.ExportPolicy(MetadataExporter exporter, PolicyConversionContext policyContext)
    {
        if (policyContext == null)
        {
            throw new ArgumentNullException("policyContext");
        }
       XmlDocument document = new XmlDocument();
       policyContext.GetBindingAssertions().Add(document.CreateElement(
            GZipMessageEncodingPolicyConstants.GZipEncodingPrefix,
            GZipMessageEncodingPolicyConstants.GZipEncodingName,
            GZipMessageEncodingPolicyConstants.GZipEncodingNamespace));
    }
}
```

<span data-ttu-id="cc7ee-169">`GZipMessageEncodingBindingElement` `IPolicyExportExtension` Bu bağlama öğesinin, aşağıdaki örnekte gösterildiği gibi, meta verilerde bir ilke olarak verilebilmesi için, sınıfın arabirimini uyguladığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-169">Note that `GZipMessageEncodingBindingElement` class implements the `IPolicyExportExtension` interface, so that this binding element can be exported as a policy in metadata, as shown in the following example.</span></span>

```xml
<wsp:Policy wsu:Id="BufferedHttpSampleServer_ISampleServer_policy">
    <wsp:ExactlyOne>
      <wsp:All>
        <gzip:text xmlns:gzip=
        "http://schemas.microsoft.com/ws/06/2004/mspolicy/netgzip1" />
       <wsaw:UsingAddressing />
     </wsp:All>
   </wsp:ExactlyOne>
</wsp:Policy>
```

<span data-ttu-id="cc7ee-170">`GZipMessageEncodingBindingElementImporter`Sınıfı `IPolicyImportExtension` arabirimini uygular, bu sınıf için ilkeyi içeri aktarır `GZipMessageEncodingBindingElement` .</span><span class="sxs-lookup"><span data-stu-id="cc7ee-170">The `GZipMessageEncodingBindingElementImporter` class implements the `IPolicyImportExtension` interface, this class imports policy for `GZipMessageEncodingBindingElement`.</span></span> <span data-ttu-id="cc7ee-171">Svcutil. exe aracı, ilkeleri yapılandırma dosyasına aktarmak için kullanılabilir, işlemek için `GZipMessageEncodingBindingElement` aşağıdaki, Svcutil. exe. config dosyasına eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-171">Svcutil.exe tool can be used to import policies to the configuration file, to handle `GZipMessageEncodingBindingElement`, the following should be added to Svcutil.exe.config.</span></span>

```xml
<configuration>
  <system.serviceModel>
    <extensions>
      <bindingElementExtensions>
        <add name="gzipMessageEncoding"
          type=
            "Microsoft.ServiceModel.Samples.GZipMessageEncodingElement, GZipEncoder, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
      </bindingElementExtensions>
    </extensions>
    <client>
      <metadata>
        <policyImporters>
          <remove type=
"System.ServiceModel.Channels.MessageEncodingBindingElementImporter, System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
          <extension type=
"Microsoft.ServiceModel.Samples.GZipMessageEncodingBindingElementImporter, GZipEncoder, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
        </policyImporters>
      </metadata>
    </client>
  </system.serviceModel>
</configuration>
```

<span data-ttu-id="cc7ee-172">Artık, Sıkıştırma Kodlayıcısı için eşleşen bir bağlama öğesi olduğuna göre, aşağıdaki örnek kodda gösterildiği gibi yeni bir özel bağlama nesnesi oluşturup buna özel bağlama öğesini ekleyerek hizmet veya istemciye program aracılığıyla bağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-172">Now that there is a matching binding element for the compression encoder, it can be programmatically hooked into the service or client by constructing a new custom binding object and adding the custom binding element to it, as shown in the following sample code.</span></span>

```csharp
ICollection<BindingElement> bindingElements = new List<BindingElement>();
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();
GZipMessageEncodingBindingElement compBindingElement = new GZipMessageEncodingBindingElement ();
bindingElements.Add(compBindingElement);
bindingElements.Add(httpBindingElement);
CustomBinding binding = new CustomBinding(bindingElements);
binding.Name = "SampleBinding";
binding.Namespace = "http://tempuri.org/bindings";
```

<span data-ttu-id="cc7ee-173">Bu, Kullanıcı senaryolarının çoğunluğu için yeterli olabileceğinden, bir hizmetin Web 'de barındırılması durumunda dosya yapılandırmasını desteklemek kritik öneme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-173">While this may be sufficient for the majority of user scenarios, supporting a file configuration is critical if a service is to be Web-hosted.</span></span> <span data-ttu-id="cc7ee-174">Web 'de barındırılan senaryoyu desteklemek için, bir özel bağlama öğesinin bir dosyada yapılandırılabilir olmasını sağlamak üzere özel bir yapılandırma işleyicisi geliştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-174">To support the Web-hosted scenario, you must develop a custom configuration handler to allow a custom binding element to be configurable in a file.</span></span>

<span data-ttu-id="cc7ee-175">Yapılandırma sisteminin en üstünde bağlama öğesi için bir yapılandırma işleyicisi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-175">You can build a configuration handler for the binding element on top of the configuration system.</span></span> <span data-ttu-id="cc7ee-176">Binding öğesi için yapılandırma işleyicisi <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> sınıfından türetilmelidir.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-176">The configuration handler for the binding element must derive from the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> class.</span></span> <span data-ttu-id="cc7ee-177">, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.BindingElementType?displayProperty=nameWithType> Bu bölüm için oluşturulacak bağlama öğesi türünün yapılandırma sistemine bildirir.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-177">The <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.BindingElementType?displayProperty=nameWithType> informs the configuration system of the type of binding element to create for this section.</span></span> <span data-ttu-id="cc7ee-178">Öğesinin `BindingElement` ayarlanbileceği tüm yönleri türetilmiş sınıfta özellikler olarak kullanıma sunulmalıdır <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> .</span><span class="sxs-lookup"><span data-stu-id="cc7ee-178">All aspects of the `BindingElement` that can be set should be exposed as properties in the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> derived class.</span></span> <span data-ttu-id="cc7ee-179"><xref:System.Configuration.ConfigurationPropertyAttribute>Yapılandırma öğesi özniteliklerinin özelliklerle eşlenmesiyle ve özniteliklerin eksik olması halinde varsayılan değerlerin ayarlanmasına yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-179">The <xref:System.Configuration.ConfigurationPropertyAttribute> assists in mapping the configuration element attributes to the properties and setting default values if attributes are missing.</span></span> <span data-ttu-id="cc7ee-180">Yapılandırma değerleri yüklenip özelliklerine uygulandıktan sonra, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A?displayProperty=nameWithType> özelliği bir bağlama öğesinin somut örneğine dönüştüren yöntemi çağırılır.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-180">After the values from configuration are loaded and applied to the properties, the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A?displayProperty=nameWithType> method is called, which converts the properties into a concrete instance of a binding element.</span></span> <span data-ttu-id="cc7ee-181"><xref:System.ServiceModel.Configuration.BindingElementExtensionElement.ApplyConfiguration%2A?displayProperty=nameWithType>Yöntemi, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> türetilmiş sınıftaki özellikleri yeni oluşturulan bağlama öğesinde ayarlanacak değerlere dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-181">The <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.ApplyConfiguration%2A?displayProperty=nameWithType> method is used to convert the properties on the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> derived class into the values to be set on the newly created binding element.</span></span>

<span data-ttu-id="cc7ee-182">Aşağıdaki örnek kod, uygulamasının uygulamasını gösterir `GZipMessageEncodingElement` .</span><span class="sxs-lookup"><span data-stu-id="cc7ee-182">The following sample code shows the implementation of the `GZipMessageEncodingElement`.</span></span>

```csharp
public class GZipMessageEncodingElement : BindingElementExtensionElement
{
    public GZipMessageEncodingElement()
    {
    }

//Called by the WCF to discover the type of binding element this
//config section enables
    public override Type BindingElementType
    {
        get { return typeof(GZipMessageEncodingBindingElement); }
    }

    //The only property we need to configure for our binding element is
    //the type of inner encoder to use. Here, we support text and
    //binary.
    [ConfigurationProperty("innerMessageEncoding",
                         DefaultValue = "textMessageEncoding")]
    public string InnerMessageEncoding
    {
        get { return (string)base["innerMessageEncoding"]; }
        set { base["innerMessageEncoding"] = value; }
    }

    //Called by the WCF to apply the configuration settings (the
    //property above) to the binding element
    public override void ApplyConfiguration(BindingElement bindingElement)
    {
        GZipMessageEncodingBindingElement binding =
                (GZipMessageEncodingBindingElement)bindingElement;
        PropertyInformationCollection propertyInfo =
                    this.ElementInformation.Properties;
        if (propertyInfo["innerMessageEncoding"].ValueOrigin !=
                                     PropertyValueOrigin.Default)
        {
            switch (this.InnerMessageEncoding)
            {
                case "textMessageEncoding":
                    binding.InnerMessageEncodingBindingElement =
                      new TextMessageEncodingBindingElement();
                    break;
                case "binaryMessageEncoding":
                    binding.InnerMessageEncodingBindingElement =
                         new BinaryMessageEncodingBindingElement();
                    break;
            }
        }
    }

    //Called by the WCF to create the binding element
    protected override BindingElement CreateBindingElement()
    {
        GZipMessageEncodingBindingElement bindingElement =
                new GZipMessageEncodingBindingElement();
        this.ApplyConfiguration(bindingElement);
        return bindingElement;
    }
}
```

<span data-ttu-id="cc7ee-183">Bu yapılandırma işleyicisi, hizmet veya istemcinin App. config veya Web. config dosyasında aşağıdaki gösterimiyle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-183">This configuration handler maps to the following representation in the App.config or Web.config for the service or client.</span></span>

```xml
<gzipMessageEncoding innerMessageEncoding="textMessageEncoding" />
```

<span data-ttu-id="cc7ee-184">Bu yapılandırma işleyicisini kullanmak için, [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) Aşağıdaki örnek yapılandırmada gösterildiği gibi öğesinin öğesi içinde kayıtlı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-184">To use this configuration handler, it must be registered within the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element, as shown in the following sample configuration.</span></span>

```xml
<extensions>
    <bindingElementExtensions>
       <add
           name="gzipMessageEncoding"
           type=
           "Microsoft.ServiceModel.Samples.GZipMessageEncodingElement,
           GZipEncoder, Version=1.0.0.0, Culture=neutral,
           PublicKeyToken=null" />
      </bindingElementExtensions>
</extensions>
```

<span data-ttu-id="cc7ee-185">Sunucuyu çalıştırdığınızda, işlem istekleri ve yanıtları konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-185">When you run the server, the operation requests and responses are displayed in the console window.</span></span> <span data-ttu-id="cc7ee-186">Sunucuyu kapatmak için pencerede ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-186">Press ENTER in the window to shut down the server.</span></span>

```console
Press Enter key to Exit.

        Server Echo(string input) called:
        Client message: Simple hello

        Server BigEcho(string[] input) called:
        64 client messages
```

<span data-ttu-id="cc7ee-187">İstemcisini çalıştırdığınızda, işlem istekleri ve yanıtları konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-187">When you run the client, the operation requests and responses are displayed in the console window.</span></span> <span data-ttu-id="cc7ee-188">İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-188">Press ENTER in the client window to shut down the client.</span></span>

```console
Calling Echo(string):
Server responds: Simple hello Simple hello

Calling BigEcho(string[]):
Server responds: Hello 0

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="cc7ee-189">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="cc7ee-189">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="cc7ee-190">Aşağıdaki komutu kullanarak ASP.NET 4,0 'yi yükler:</span><span class="sxs-lookup"><span data-stu-id="cc7ee-190">Install ASP.NET 4.0 using the following command:</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="cc7ee-191">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-191">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="cc7ee-192">Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-192">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="cc7ee-193">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-193">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cc7ee-194">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-194">The samples may already be installed on your machine.</span></span> <span data-ttu-id="cc7ee-195">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-195">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="cc7ee-196">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="cc7ee-196">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cc7ee-197">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="cc7ee-197">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`
