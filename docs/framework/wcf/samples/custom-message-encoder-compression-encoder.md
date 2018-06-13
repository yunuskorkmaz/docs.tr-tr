---
title: 'Özel İleti Kodlayıcı: Sıkıştırma Kodlayıcısı'
ms.date: 03/30/2017
ms.assetid: 57450b6c-89fe-4b8a-8376-3d794857bfd7
ms.openlocfilehash: 5dc665da3b28a98f1b3016d38ce706bf77dce06f
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33808747"
---
# <a name="custom-message-encoder-compression-encoder"></a><span data-ttu-id="00c35-102">Özel İleti Kodlayıcı: Sıkıştırma Kodlayıcısı</span><span class="sxs-lookup"><span data-stu-id="00c35-102">Custom Message Encoder: Compression Encoder</span></span>
<span data-ttu-id="00c35-103">Bu örnek, Windows Communication Foundation (WCF) platformu kullanarak özel bir kodlayıcı uygulamak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="00c35-103">This sample demonstrates how to implement a custom encoder using the Windows Communication Foundation (WCF) platform.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="00c35-104">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="00c35-104">The samples may already be installed on your machine.</span></span> <span data-ttu-id="00c35-105">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="00c35-105">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="00c35-106">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="00c35-106">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="00c35-107">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="00c35-107">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`  
  
## <a name="sample-details"></a><span data-ttu-id="00c35-108">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="00c35-108">Sample Details</span></span>  
 <span data-ttu-id="00c35-109">Bu örnek, bir istemci konsol program (.exe), kendini barındıran hizmet konsol program (.exe) ve sıkıştırma ileti Kodlayıcı kitaplığı (.dll) oluşur.</span><span class="sxs-lookup"><span data-stu-id="00c35-109">This sample consists of a client console program (.exe), a self-hosted service console program (.exe) and a compression message encoder library (.dll).</span></span> <span data-ttu-id="00c35-110">Hizmet bir istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="00c35-110">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="00c35-111">Anlaşma tarafından tanımlanan `ISampleServer` temel dize işlemleri Yankı kullanıma sunan arabirim (`Echo` ve `BigEcho`).</span><span class="sxs-lookup"><span data-stu-id="00c35-111">The contract is defined by the `ISampleServer` interface, which exposes basic string echoing operations (`Echo` and `BigEcho`).</span></span> <span data-ttu-id="00c35-112">İstemci eş zamanlı istekleri belirli bir işlemi ve hizmet yanıt istemciye ileti tekrarlayarak hale getirir.</span><span class="sxs-lookup"><span data-stu-id="00c35-112">The client makes synchronous requests to a given operation and the service replies by repeating the message back to the client.</span></span> <span data-ttu-id="00c35-113">İstemci ve hizmet etkinliği konsol pencerelerinde görünür olur.</span><span class="sxs-lookup"><span data-stu-id="00c35-113">Client and service activity is visible in the console windows.</span></span> <span data-ttu-id="00c35-114">Bu örnek amacı, özel bir kodlayıcı yazma ve bir iletinin hat üzerinde sıkıştırma etkisini tanıtmak nasıl göstermektir.</span><span class="sxs-lookup"><span data-stu-id="00c35-114">The intent of this sample is to show how to write a custom encoder and demonstrate the impact of compression of a message on the wire.</span></span> <span data-ttu-id="00c35-115">İleti boyutu, işlem süresi veya her ikisini hesaplamak için sıkıştırma ileti Kodlayıcı araçları ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00c35-115">You can add instrumentation to the compression message encoder to calculate message size, processing time, or both.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="00c35-116">Sunucu (GZip veya Deflate gibi bir algoritmayla oluşturulan) sıkıştırılmış bir yanıt gönderiyorsa, .NET Framework 4'te bir WCF istemcisi otomatik açılması etkinleştirildi.</span><span class="sxs-lookup"><span data-stu-id="00c35-116">In the .NET Framework 4, automatic decompression has been enabled on a WCF client if the server is sending a compressed response (created with an algorithm such as GZip or Deflate).</span></span> <span data-ttu-id="00c35-117">Internet Information Server (IIS) Web barındırılan hizmet ise, IIS sıkıştırılmış yanıt gönderme hizmeti için yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="00c35-117">If the service is Web-hosted in Internet Information Server (IIS), then IIS can be configured for the service to send a compressed response.</span></span> <span data-ttu-id="00c35-118">Bu örnek, sıkıştırma ve açma hem istemci hem de hizmet yapmak için gereksinim olması veya hizmet kendiliğinden barındırılır kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="00c35-118">This sample can be used if the requirement is to do compression and decompression on both the client and the service or if the service is self-hosted.</span></span>  
  
 <span data-ttu-id="00c35-119">Örnek nasıl oluşturulacağı ve bir WCF uygulamaya özel ileti Kodlayıcı tümleştirmek gösterir.</span><span class="sxs-lookup"><span data-stu-id="00c35-119">The sample demonstrates how to build and integrate a custom message encoder into a WCF application.</span></span> <span data-ttu-id="00c35-120">GZipEncoder.dll Kitaplığı hem istemci hem de hizmet ile dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="00c35-120">The library GZipEncoder.dll is deployed with both the client and the service.</span></span> <span data-ttu-id="00c35-121">Bu örnek ayrıca iletileri sıkıştırma etkisini gösterir.</span><span class="sxs-lookup"><span data-stu-id="00c35-121">This sample also demonstrates the impact of compressing messages.</span></span> <span data-ttu-id="00c35-122">GZipEncoder.dll kodda şunlar gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="00c35-122">The code in GZipEncoder.dll demonstrates the following:</span></span>  
  
-   <span data-ttu-id="00c35-123">Özel Kodlayıcı ve Kodlayıcı Fabrika oluşturma.</span><span class="sxs-lookup"><span data-stu-id="00c35-123">Building a custom encoder and encoder factory.</span></span>  
  
-   <span data-ttu-id="00c35-124">Bir bağlama öğesi için özel bir kodlayıcı geliştirme.</span><span class="sxs-lookup"><span data-stu-id="00c35-124">Developing a binding element for a custom encoder.</span></span>  
  
-   <span data-ttu-id="00c35-125">Özel bağlama yapılandırma özel bağlama öğeleri tümleştirmek için kullanma.</span><span class="sxs-lookup"><span data-stu-id="00c35-125">Using the custom binding configuration for integrating custom binding elements.</span></span>  
  
-   <span data-ttu-id="00c35-126">Özel bağlama öğesi dosya yapılandırılmasına olanak verecek özel yapılandırma işleyicisi geliştirme.</span><span class="sxs-lookup"><span data-stu-id="00c35-126">Developing a custom configuration handler to allow file configuration of a custom binding element.</span></span>  
  
 <span data-ttu-id="00c35-127">Daha önce belirtildiği gibi özel bir kodlayıcı uygulanan birkaç katmandan vardır.</span><span class="sxs-lookup"><span data-stu-id="00c35-127">As indicated previously, there are several layers that are implemented in a custom encoder.</span></span> <span data-ttu-id="00c35-128">Bu katmanların her arasındaki ilişkiyi daha iyi anlamak için aşağıdaki listede hizmet başlangıcından için basitleştirilmiş bir olaylar dizisi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="00c35-128">To better illustrate the relationship between each of these layers, a simplified order of events for service start-up is in the following list:</span></span>  
  
1.  <span data-ttu-id="00c35-129">Sunucu başlar.</span><span class="sxs-lookup"><span data-stu-id="00c35-129">The server starts.</span></span>  
  
2.  <span data-ttu-id="00c35-130">Yapılandırma bilgilerini okuyun.</span><span class="sxs-lookup"><span data-stu-id="00c35-130">The configuration information is read.</span></span>  
  
    1.  <span data-ttu-id="00c35-131">Hizmet yapılandırması özel yapılandırma işleyicisi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="00c35-131">The service configuration registers the custom configuration handler.</span></span>  
  
    2.  <span data-ttu-id="00c35-132">Hizmet ana bilgisayarı oluşturulur ve açılır.</span><span class="sxs-lookup"><span data-stu-id="00c35-132">The service host is created and opened.</span></span>  
  
    3.  <span data-ttu-id="00c35-133">Özel yapılandırma öğesi oluşturur ve özel bağlama öğesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="00c35-133">The custom configuration element creates and returns the custom binding element.</span></span>  
  
    4.  <span data-ttu-id="00c35-134">Özel bağlama öğesi oluşturur ve bir ileti Kodlayıcı fabrikası döndürür.</span><span class="sxs-lookup"><span data-stu-id="00c35-134">The custom binding element creates and returns a message encoder factory.</span></span>  
  
3.  <span data-ttu-id="00c35-135">Bir ileti alındı.</span><span class="sxs-lookup"><span data-stu-id="00c35-135">A message is received.</span></span>  
  
4.  <span data-ttu-id="00c35-136">İleti Kodlayıcı Fabrika iletide okumak ve yanıt yazmak için bir ileti Kodlayıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="00c35-136">The message encoder factory returns a message encoder for reading in the message and writing out the response.</span></span>  
  
5.  <span data-ttu-id="00c35-137">Kodlayıcı katman üreteci uygulanır.</span><span class="sxs-lookup"><span data-stu-id="00c35-137">The encoder layer is implemented as a class factory.</span></span> <span data-ttu-id="00c35-138">Yalnızca Kodlayıcı üreteci için özel Kodlayıcı herkese açık şekilde sunulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="00c35-138">Only the encoder class factory must be publicly exposed for the custom encoder.</span></span> <span data-ttu-id="00c35-139">Üretecini bağlama öğesi tarafından döndürülen zaman <xref:System.ServiceModel.ServiceHost> veya <xref:System.ServiceModel.ChannelFactory%601> nesnesi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="00c35-139">The factory object is returned by the binding element when the <xref:System.ServiceModel.ServiceHost> or <xref:System.ServiceModel.ChannelFactory%601> object is created.</span></span> <span data-ttu-id="00c35-140">İleti kodlayıcılar arabelleğe alınan veya akış modunda çalışır.</span><span class="sxs-lookup"><span data-stu-id="00c35-140">Message encoders can operate in a buffered or streaming mode.</span></span> <span data-ttu-id="00c35-141">Bu örnek arabellekli modu ve akış modu gösterir.</span><span class="sxs-lookup"><span data-stu-id="00c35-141">This sample demonstrates both buffered mode and streaming mode.</span></span>  
  
 <span data-ttu-id="00c35-142">Her bir modu için yok bir eşlik eden `ReadMessage` ve `WriteMessage` Özet yöntemi `MessageEncoder` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="00c35-142">For each mode there is an accompanying `ReadMessage` and `WriteMessage` method on the abstract `MessageEncoder` class.</span></span> <span data-ttu-id="00c35-143">Kodlama işi çoğunu bu yöntemler gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="00c35-143">A majority of the encoding work takes place in these methods.</span></span> <span data-ttu-id="00c35-144">Örnek var olan metin ve ikili ileti kodlayıcılar sarmalar.</span><span class="sxs-lookup"><span data-stu-id="00c35-144">The sample wraps the existing text and binary message encoders.</span></span> <span data-ttu-id="00c35-145">Bu örnek okuma ve yazma işlemini iletilerinin hat gösterimine iç kodlayıcıya temsilci ve sıkıştırmak veya sonuçları sıkıştırmasını açmak sıkıştırma Kodlayıcısı olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="00c35-145">This allows the sample to delegate the reading and writing of the wire representation of messages to the inner encoder and allows the compression encoder to compress or decompress the results.</span></span> <span data-ttu-id="00c35-146">İleti kodlama için ardışık düzen yok olduğundan, bu WCF'de birden çok kodlayıcılar kullanarak yalnızca modelidir.</span><span class="sxs-lookup"><span data-stu-id="00c35-146">Because there is no pipeline for message encoding, this is the only model for using multiple encoders in WCF.</span></span> <span data-ttu-id="00c35-147">İleti sıkıştırması sonra sonuçta elde edilen ileti işlemek için kanal yığın yığınının yukarı geçirilir.</span><span class="sxs-lookup"><span data-stu-id="00c35-147">Once the message has been decompressed, the resulting message is passed up the stack for the channel stack to handle.</span></span> <span data-ttu-id="00c35-148">Sıkıştırma sırasında elde edilen sıkıştırılmış iletisi sağlanan akış doğrudan yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="00c35-148">During compression, the resulting compressed message is written directly to the stream provided.</span></span>  
  
 <span data-ttu-id="00c35-149">Bu örnek yardımcı yöntemler kullanır (`CompressBuffer` ve `DecompressBuffer`) kullanmak akışlara arabellekleri dönüştürme gerçekleştirmek için `GZipStream` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="00c35-149">This sample uses helper methods (`CompressBuffer` and `DecompressBuffer`) to perform conversion from buffers to streams to use the `GZipStream` class.</span></span>  
  
 <span data-ttu-id="00c35-150">Arabelleğe alınan `ReadMessage` ve `WriteMessage` sınıflarının kullanımı `BufferManager` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="00c35-150">The buffered `ReadMessage` and `WriteMessage` classes make use of the `BufferManager` class.</span></span> <span data-ttu-id="00c35-151">Kodlayıcı yalnızca Kodlayıcı Fabrika erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="00c35-151">The encoder is accessible only through the encoder factory.</span></span> <span data-ttu-id="00c35-152">Özet `MessageEncoderFactory` SAX adlı bir özellik `Encoder` geçerli Kodlayıcı ve adlı bir yöntem erişim için `CreateSessionEncoder` oturumları destekleyen bir kodlayıcı oluşturma için.</span><span class="sxs-lookup"><span data-stu-id="00c35-152">The abstract `MessageEncoderFactory` class provides a property named `Encoder` for accessing the current encoder and a method named `CreateSessionEncoder` for creating an encoder that supports sessions.</span></span> <span data-ttu-id="00c35-153">Bu tür bir kodlayıcı burada kanal oturumları destekler, sıralanır ve güvenilir bir senaryoda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="00c35-153">Such an encoder can be used in the scenario where the channel supports sessions, is ordered and is reliable.</span></span> <span data-ttu-id="00c35-154">Bu senaryoda her oturum için kablo yazılan veriler, iyileştirme sağlar.</span><span class="sxs-lookup"><span data-stu-id="00c35-154">This scenario allows for optimization in each session of the data written to the wire.</span></span> <span data-ttu-id="00c35-155">Bu değil istenirse, temel yöntemi aşırı yüklenmiş değil.</span><span class="sxs-lookup"><span data-stu-id="00c35-155">If this is not desired, the base method should not be overloaded.</span></span> <span data-ttu-id="00c35-156">`Encoder` Özelliği oturum daha az Kodlayıcı ve varsayılan uygulaması erişim için bir mekanizma sağlar `CreateSessionEncoder` yöntemi özelliğinin değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="00c35-156">The `Encoder` property provides a mechanism for accessing the session-less encoder and the default implementation of the `CreateSessionEncoder` method returns the value of the property.</span></span> <span data-ttu-id="00c35-157">Sıkıştırma, sağlamak için var olan bir kodlayıcı örnek sarmalar çünkü `MessageEncoderFactory` uygulama kabul bir `MessageEncoderFactory` , iç Kodlayıcı üretecini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="00c35-157">Because the sample wraps an existing encoder to provide compression, the `MessageEncoderFactory` implementation accepts a `MessageEncoderFactory` that represents the inner encoder factory.</span></span>  
  
 <span data-ttu-id="00c35-158">Kodlayıcı ve Kodlayıcı Fabrika tanımlanan, bir WCF istemcisi ve hizmeti ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="00c35-158">Now that the encoder and encoder factory are defined, they can be used with a WCF client and service.</span></span> <span data-ttu-id="00c35-159">Ancak, bu kodlayıcılar kanal yığına eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="00c35-159">However, these encoders must be added to the channel stack.</span></span> <span data-ttu-id="00c35-160">Sınıflardan türetilemeyeceğini <xref:System.ServiceModel.ServiceHost> ve <xref:System.ServiceModel.ChannelFactory%601> sınıfları ve geçersiz kılma `OnInitialize` bu Kodlayıcı Fabrika el ile eklemek için yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="00c35-160">You can derive classes from the <xref:System.ServiceModel.ServiceHost> and <xref:System.ServiceModel.ChannelFactory%601> classes and override the `OnInitialize` methods to add this encoder factory manually.</span></span> <span data-ttu-id="00c35-161">Özel bağlama öğesi aracılığıyla Kodlayıcı Fabrika ayrıca getirebilir.</span><span class="sxs-lookup"><span data-stu-id="00c35-161">You can also expose the encoder factory through a custom binding element.</span></span>  
  
 <span data-ttu-id="00c35-162">Yeni bir özel bağlama öğesi oluşturmak için öğesinden bir sınıf türetin <xref:System.ServiceModel.Channels.BindingElement> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="00c35-162">To create a new custom binding element, derive a class from the <xref:System.ServiceModel.Channels.BindingElement> class.</span></span> <span data-ttu-id="00c35-163">Ancak, çeşitli bağlama öğeleri vardır.</span><span class="sxs-lookup"><span data-stu-id="00c35-163">There are, however, several types of binding elements.</span></span> <span data-ttu-id="00c35-164">Özel bağlama öğesi bağlama öğesi kodlama ileti olarak tanındığından emin olmak için aynı zamanda uygulamanız gereken <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="00c35-164">To ensure that the custom binding element is recognized as a message encoding binding element, you also must implement the <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.</span></span> <span data-ttu-id="00c35-165"><xref:System.ServiceModel.Channels.MessageEncodingBindingElement> Yeni bir ileti Kodlayıcı factory oluşturmak için bir yöntemi gösterir (`CreateMessageEncoderFactory`), eşleşen ileti Kodlayıcı Fabrika örneği döndürülecek uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="00c35-165">The <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> exposes a method for creating a new message encoder factory (`CreateMessageEncoderFactory`), which is implemented to return an instance of the matching message encoder factory.</span></span> <span data-ttu-id="00c35-166">Ayrıca, <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> adresleme sürüm belirtmek üzere bir özelliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="00c35-166">Additionally, the <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> has a property to indicate the addressing version.</span></span> <span data-ttu-id="00c35-167">Bu örnek varolan kodlayıcılar sarmalar olduğundan, örnek uygulama ayrıca bağlama öğeleri varolan Kodlayıcı sarmalar ve parametre olarak oluşturucuya bağlama öğesi bir iç Kodlayıcı alır ve bir özelliği üzerinden kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="00c35-167">Because this sample wraps the existing encoders, the sample implementation also wraps the existing encoder binding elements and takes an inner encoder binding element as a parameter to the constructor and exposes it through a property.</span></span> <span data-ttu-id="00c35-168">Aşağıdaki örnek kod uygulamasını gösterir `GZipMessageEncodingBindingElement` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="00c35-168">The following sample code shows the implementation of the `GZipMessageEncodingBindingElement` class.</span></span>  
  
```  
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
  
 <span data-ttu-id="00c35-169">Unutmayın `GZipMessageEncodingBindingElement` uygulayan sınıf `IPolicyExportExtension` arabirim, böylece bu bağlama öğesi meta veri, bir ilke olarak aşağıdaki örnekte gösterildiği gibi aktarılabilir.</span><span class="sxs-lookup"><span data-stu-id="00c35-169">Note that `GZipMessageEncodingBindingElement` class implements the `IPolicyExportExtension` interface, so that this binding element can be exported as a policy in metadata, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="00c35-170">`GZipMessageEncodingBindingElementImporter` Uygulayan sınıf `IPolicyImportExtension` arabirimi, bu sınıf için ilke alır `GZipMessageEncodingBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="00c35-170">The `GZipMessageEncodingBindingElementImporter` class implements the `IPolicyImportExtension` interface, this class imports policy for `GZipMessageEncodingBindingElement`.</span></span> <span data-ttu-id="00c35-171">İlkeleri işlemek için yapılandırma dosyasına aktarmak için svcutil.exe aracı kullanılabilir `GZipMessageEncodingBindingElement`, aşağıdakiler için Svcutil.exe.config eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="00c35-171">Svcutil.exe tool can be used to import policies to the configuration file, to handle `GZipMessageEncodingBindingElement`, the following should be added to Svcutil.exe.config.</span></span>  
  
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
  
 <span data-ttu-id="00c35-172">Yoktur göre sıkıştırma Kodlayıcısı için eşleşen bir bağlama öğesi, bu program aracılığıyla hizmet ya da istemci yeni bir özel bağlama nesnesi oluşturma ve aşağıdaki örnek kodda gösterildiği gibi özel bağlama öğesi, ekleyerek bağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="00c35-172">Now that there is a matching binding element for the compression encoder, it can be programmatically hooked into the service or client by constructing a new custom binding object and adding the custom binding element to it, as shown in the following sample code.</span></span>  
  
```  
ICollection<BindingElement> bindingElements = new List<BindingElement>();  
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();  
GZipMessageEncodingBindingElement compBindingElement = new GZipMessageEncodingBindingElement ();  
bindingElements.Add(compBindingElement);  
bindingElements.Add(httpBindingElement);  
CustomBinding binding = new CustomBinding(bindingElements);  
binding.Name = "SampleBinding";  
binding.Namespace = "http://tempuri.org/bindings";  
```  
  
 <span data-ttu-id="00c35-173">Bu kullanıcı senaryoları çoğunluğu için yeterli olabilir, ancak dosya yapılandırmasını destekleyen bir hizmet Web barındırılan olması durumunda kritik öneme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="00c35-173">While this may be sufficient for the majority of user scenarios, supporting a file configuration is critical if a service is to be Web-hosted.</span></span> <span data-ttu-id="00c35-174">Web barındırılan senaryoyu desteklemek için bir dosyada yapılandırılabilir olması bir özel bağlama öğesi izin vermek için özel yapılandırma işleyicisi geliştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="00c35-174">To support the Web-hosted scenario, you must develop a custom configuration handler to allow a custom binding element to be configurable in a file.</span></span>  
  
 <span data-ttu-id="00c35-175">Tarafından sağlanan yapılandırma sistemi üstünde bağlama öğesi için bir yapılandırma işleyicisi yapı [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="00c35-175">You can build a configuration handler for the binding element on top of the configuration system provided by the [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].</span></span> <span data-ttu-id="00c35-176">Bağlama öğesi için yapılandırma işleyicisi öğesinden türetilmelidir <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="00c35-176">The configuration handler for the binding element must derive from the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> class.</span></span> <span data-ttu-id="00c35-177">`BindingElementType` Özelliği için bu bölümü oluşturmak için bağlama öğesi türünün yapılandırma sistemi bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="00c35-177">The `BindingElementType` property is used to inform the configuration system of the type of binding element to create for this section.</span></span> <span data-ttu-id="00c35-178">Tüm yönlerini `BindingElement` , olabilir kümesi ortaya özellikleri olarak <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> türetilmiş sınıf.</span><span class="sxs-lookup"><span data-stu-id="00c35-178">All aspects of the `BindingElement` that can be set should be exposed as properties in the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> derived class.</span></span> <span data-ttu-id="00c35-179"><xref:System.Configuration.ConfigurationPropertyAttribute> Özellikler için yapılandırma öğesi özniteliklerini eşleme ve öznitelikleri eksikse, varsayılan değerleri ayarlama yardımcı olmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="00c35-179">The <xref:System.Configuration.ConfigurationPropertyAttribute> is used to assist in mapping the configuration element attributes to the properties and setting default values if attributes are missing.</span></span> <span data-ttu-id="00c35-180">Yapılandırma değerleri yüklendikten ve özelliklerine uygulanan sonra <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> yöntemi çağrıldığında, hangi özellikler somut bir bağlama öğesi örneğine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="00c35-180">After the values from configuration are loaded and applied to the properties, the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> method is called, which converts the properties into a concrete instance of a binding element.</span></span> <span data-ttu-id="00c35-181"><xref:System.ServiceModel.Configuration.BindingElementExtensionElement.ApplyConfiguration%2A> Yöntemi özellikleri dönüştürmek için kullanılan <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> yaratım bağlama öğesi üzerindeki ayarlanacak değerlerinden türetilmiş sınıf.</span><span class="sxs-lookup"><span data-stu-id="00c35-181">The <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.ApplyConfiguration%2A> method is used to convert the properties on the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> derived class into the values to be set on the newlycreated binding element.</span></span>  
  
 <span data-ttu-id="00c35-182">Aşağıdaki örnek kod uygulamasını gösterir `GZipMessageEncodingElement`.</span><span class="sxs-lookup"><span data-stu-id="00c35-182">The following sample code shows the implementation of the `GZipMessageEncodingElement`.</span></span>  
  
```  
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
  
 <span data-ttu-id="00c35-183">Bu yapılandırma işleyicisi hizmet veya istemci için App.config veya Web.config içinde aşağıdaki gösterimi eşler.</span><span class="sxs-lookup"><span data-stu-id="00c35-183">This configuration handler maps to the following representation in the App.config or Web.config for the service or client.</span></span>  
  
```xml  
<gzipMessageEncoding innerMessageEncoding="textMessageEncoding" />  
```  
  
 <span data-ttu-id="00c35-184">Bu yapılandırma işleyicisi kullanmak için onu içinde kaydedilmelidir [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) aşağıdaki örnek yapılandırmada gösterildiği gibi öğesi.</span><span class="sxs-lookup"><span data-stu-id="00c35-184">To use this configuration handler, it must be registered within the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="00c35-185">Sunucu çalıştırdığınızda, işlem isteklerini ve yanıtlarını konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="00c35-185">When you run the server, the operation requests and responses are displayed in the console window.</span></span> <span data-ttu-id="00c35-186">Penceresinde sunucuyu kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="00c35-186">Press ENTER in the window to shut down the server.</span></span>  
  
```  
Press Enter key to Exit.  
  
        Server Echo(string input) called:  
        Client message: Simple hello  
  
        Server BigEcho(string[] input) called:  
        64 client messages  
```  
  
 <span data-ttu-id="00c35-187">İşlem istekleri ve yanıtları istemci çalıştırdığınızda, konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="00c35-187">When you run the client, the operation requests and responses are displayed in the console window.</span></span> <span data-ttu-id="00c35-188">İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="00c35-188">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Calling Echo(string):  
Server responds: Simple hello Simple hello  
  
Calling BigEcho(string[]):  
Server responds: Hello 0  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="00c35-189">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="00c35-189">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="00c35-190">Yükleme [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 aşağıdaki komutu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="00c35-190">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command:</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="00c35-191">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="00c35-191">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="00c35-192">Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="00c35-192">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="00c35-193">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="00c35-193">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="00c35-194">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="00c35-194">The samples may already be installed on your machine.</span></span> <span data-ttu-id="00c35-195">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="00c35-195">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="00c35-196">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="00c35-196">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="00c35-197">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="00c35-197">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`  
  
## <a name="see-also"></a><span data-ttu-id="00c35-198">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="00c35-198">See Also</span></span>
