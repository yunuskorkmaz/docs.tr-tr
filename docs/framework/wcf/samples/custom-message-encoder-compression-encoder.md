---
title: 'Özel İleti Kodlayıcı: Sıkıştırma Kodlayıcısı'
ms.date: 03/30/2017
ms.assetid: 57450b6c-89fe-4b8a-8376-3d794857bfd7
ms.openlocfilehash: b70875e385fa32256476f6d1ae53e8cc1f5ff9de
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "45989936"
---
# <a name="custom-message-encoder-compression-encoder"></a><span data-ttu-id="5cec4-102">Özel İleti Kodlayıcı: Sıkıştırma Kodlayıcısı</span><span class="sxs-lookup"><span data-stu-id="5cec4-102">Custom Message Encoder: Compression Encoder</span></span>
<span data-ttu-id="5cec4-103">Bu örnek, Windows Communication Foundation (WCF) platformunu kullanarak özel bir kodlayıcı uygulamak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="5cec4-103">This sample demonstrates how to implement a custom encoder using the Windows Communication Foundation (WCF) platform.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5cec4-104">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="5cec4-104">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5cec4-105">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="5cec4-105">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5cec4-106">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="5cec4-106">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5cec4-107">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="5cec4-107">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`  
  
## <a name="sample-details"></a><span data-ttu-id="5cec4-108">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="5cec4-108">Sample Details</span></span>  
 <span data-ttu-id="5cec4-109">Bu örnek, bir istemci konsol program (.exe), şirket içinde barındırılan hizmeti bir konsol programı (.exe) ve sıkıştırma ileti Kodlayıcı kitaplığı (.dll) oluşur.</span><span class="sxs-lookup"><span data-stu-id="5cec4-109">This sample consists of a client console program (.exe), a self-hosted service console program (.exe) and a compression message encoder library (.dll).</span></span> <span data-ttu-id="5cec4-110">Hizmet istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="5cec4-110">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="5cec4-111">Anlaşma tarafından tanımlanan `ISampleServer` temel dize işlemleri Yankı sunan arabirimi (`Echo` ve `BigEcho`).</span><span class="sxs-lookup"><span data-stu-id="5cec4-111">The contract is defined by the `ISampleServer` interface, which exposes basic string echoing operations (`Echo` and `BigEcho`).</span></span> <span data-ttu-id="5cec4-112">İstemcinin istemciye ileti tekrarlayarak belirli bir işlemi ve hizmet yanıt zaman uyumlu istekleri yapar.</span><span class="sxs-lookup"><span data-stu-id="5cec4-112">The client makes synchronous requests to a given operation and the service replies by repeating the message back to the client.</span></span> <span data-ttu-id="5cec4-113">Hizmet ve istemci etkinliği konsol pencerelerinde görünür olur.</span><span class="sxs-lookup"><span data-stu-id="5cec4-113">Client and service activity is visible in the console windows.</span></span> <span data-ttu-id="5cec4-114">Bu örnek amacı, özel bir kodlayıcı yazma ve bir iletinin hat üzerinde sıkıştırma etkisini gösteren göstermektir.</span><span class="sxs-lookup"><span data-stu-id="5cec4-114">The intent of this sample is to show how to write a custom encoder and demonstrate the impact of compression of a message on the wire.</span></span> <span data-ttu-id="5cec4-115">İleti boyutu, işlem süresi veya her ikisi de hesaplamak için sıkıştırma ileti Kodlayıcı için izleme ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5cec4-115">You can add instrumentation to the compression message encoder to calculate message size, processing time, or both.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5cec4-116">Sunucu (GZip veya Deflate gibi bir algoritma ile oluşturulan) sıkıştırılmış bir yanıt gönderiyorsa .NET Framework 4'te bir WCF istemcisini otomatik sıkıştırma etkinleştirildi.</span><span class="sxs-lookup"><span data-stu-id="5cec4-116">In the .NET Framework 4, automatic decompression has been enabled on a WCF client if the server is sending a compressed response (created with an algorithm such as GZip or Deflate).</span></span> <span data-ttu-id="5cec4-117">Internet Information Server (IIS) Web barındırılan hizmeti, IIS, sıkıştırılmış bir yanıt göndermek hizmet için yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="5cec4-117">If the service is Web-hosted in Internet Information Server (IIS), then IIS can be configured for the service to send a compressed response.</span></span> <span data-ttu-id="5cec4-118">Bu örnek, sıkıştırma ve açma hem istemci hem de hizmet yapma gereksinimi varsa veya şirket içinde barındırılan hizmet ise kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5cec4-118">This sample can be used if the requirement is to do compression and decompression on both the client and the service or if the service is self-hosted.</span></span>  
  
 <span data-ttu-id="5cec4-119">Örnek oluşturma ve bir WCF uygulamaya özel ileti Kodlayıcı tümleştirme gösterir.</span><span class="sxs-lookup"><span data-stu-id="5cec4-119">The sample demonstrates how to build and integrate a custom message encoder into a WCF application.</span></span> <span data-ttu-id="5cec4-120">' % S'kitaplığı GZipEncoder.dll hem istemci hem de hizmet ile dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="5cec4-120">The library GZipEncoder.dll is deployed with both the client and the service.</span></span> <span data-ttu-id="5cec4-121">Bu örnek, ayrıca ileti sıkıştırma etkisini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5cec4-121">This sample also demonstrates the impact of compressing messages.</span></span> <span data-ttu-id="5cec4-122">GZipEncoder.dll kodda şunlar gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="5cec4-122">The code in GZipEncoder.dll demonstrates the following:</span></span>  
  
-   <span data-ttu-id="5cec4-123">Özel bir kodlayıcı ve Kodlayıcı fabrikası oluşturma.</span><span class="sxs-lookup"><span data-stu-id="5cec4-123">Building a custom encoder and encoder factory.</span></span>  
  
-   <span data-ttu-id="5cec4-124">Bir bağlama öğesi için özel bir kodlayıcı geliştirme.</span><span class="sxs-lookup"><span data-stu-id="5cec4-124">Developing a binding element for a custom encoder.</span></span>  
  
-   <span data-ttu-id="5cec4-125">Özel bağlama yapılandırma özel bağlama öğeleri tümleştirmek için kullanma.</span><span class="sxs-lookup"><span data-stu-id="5cec4-125">Using the custom binding configuration for integrating custom binding elements.</span></span>  
  
-   <span data-ttu-id="5cec4-126">Özel bağlama öğesinin dosya yapılandırması izin vermek için özel yapılandırma işleyicisi geliştirme.</span><span class="sxs-lookup"><span data-stu-id="5cec4-126">Developing a custom configuration handler to allow file configuration of a custom binding element.</span></span>  
  
 <span data-ttu-id="5cec4-127">Daha önce belirtildiği gibi özel bir kodlayıcı uygulanan birden fazla katman vardır.</span><span class="sxs-lookup"><span data-stu-id="5cec4-127">As indicated previously, there are several layers that are implemented in a custom encoder.</span></span> <span data-ttu-id="5cec4-128">Her biri bu Katmanlar arasındaki ilişkiyi daha iyi anlamak için aşağıdaki listede hizmet başlatma için basitleştirilmiş bir olaylar dizisi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="5cec4-128">To better illustrate the relationship between each of these layers, a simplified order of events for service start-up is in the following list:</span></span>  
  
1.  <span data-ttu-id="5cec4-129">Sunucuyu başlatır.</span><span class="sxs-lookup"><span data-stu-id="5cec4-129">The server starts.</span></span>  
  
2.  <span data-ttu-id="5cec4-130">Yapılandırma bilgilerini okuyun.</span><span class="sxs-lookup"><span data-stu-id="5cec4-130">The configuration information is read.</span></span>  
  
    1.  <span data-ttu-id="5cec4-131">Özel yapılandırma işleyicisi hizmeti yapılandırmasını kaydeder.</span><span class="sxs-lookup"><span data-stu-id="5cec4-131">The service configuration registers the custom configuration handler.</span></span>  
  
    2.  <span data-ttu-id="5cec4-132">Hizmet ana bilgisayarı oluşturulur ve açılır.</span><span class="sxs-lookup"><span data-stu-id="5cec4-132">The service host is created and opened.</span></span>  
  
    3.  <span data-ttu-id="5cec4-133">Özel yapılandırma öğesi oluşturur ve özel bağlama öğesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="5cec4-133">The custom configuration element creates and returns the custom binding element.</span></span>  
  
    4.  <span data-ttu-id="5cec4-134">Özel bağlama öğesi oluşturur ve bir ileti Kodlayıcı üreteci döndürür.</span><span class="sxs-lookup"><span data-stu-id="5cec4-134">The custom binding element creates and returns a message encoder factory.</span></span>  
  
3.  <span data-ttu-id="5cec4-135">Bir ileti alındı.</span><span class="sxs-lookup"><span data-stu-id="5cec4-135">A message is received.</span></span>  
  
4.  <span data-ttu-id="5cec4-136">İleti Kodlayıcı fabrikası iletiyi okumak ve yanıt yazmak için bir ileti Kodlayıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="5cec4-136">The message encoder factory returns a message encoder for reading in the message and writing out the response.</span></span>  
  
5.  <span data-ttu-id="5cec4-137">Kodlayıcı katmanı, bir sınıf üreteci uygulanır.</span><span class="sxs-lookup"><span data-stu-id="5cec4-137">The encoder layer is implemented as a class factory.</span></span> <span data-ttu-id="5cec4-138">Yalnızca Kodlayıcı sınıf üreteci için özel bir kodlayıcı herkese açık şekilde sunulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5cec4-138">Only the encoder class factory must be publicly exposed for the custom encoder.</span></span> <span data-ttu-id="5cec4-139">Fabrika nesnesine bağlama öğesi tarafından döndürülen zaman <xref:System.ServiceModel.ServiceHost> veya <xref:System.ServiceModel.ChannelFactory%601> nesnesi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5cec4-139">The factory object is returned by the binding element when the <xref:System.ServiceModel.ServiceHost> or <xref:System.ServiceModel.ChannelFactory%601> object is created.</span></span> <span data-ttu-id="5cec4-140">İleti Kodlayıcı arabelleğe alınan veya akış modunda çalışır.</span><span class="sxs-lookup"><span data-stu-id="5cec4-140">Message encoders can operate in a buffered or streaming mode.</span></span> <span data-ttu-id="5cec4-141">Bu örnek, hem arabellekli modu hem de akış modunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="5cec4-141">This sample demonstrates both buffered mode and streaming mode.</span></span>  
  
 <span data-ttu-id="5cec4-142">Her modu için yok yayarsa `ReadMessage` ve `WriteMessage` yöntemi soyut `MessageEncoder` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5cec4-142">For each mode there is an accompanying `ReadMessage` and `WriteMessage` method on the abstract `MessageEncoder` class.</span></span> <span data-ttu-id="5cec4-143">Kodlama iş çoğunu, bu yöntemler de gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="5cec4-143">A majority of the encoding work takes place in these methods.</span></span> <span data-ttu-id="5cec4-144">Örnek, var olan metin ve ikili ileti kodlayıcılar sarmalar.</span><span class="sxs-lookup"><span data-stu-id="5cec4-144">The sample wraps the existing text and binary message encoders.</span></span> <span data-ttu-id="5cec4-145">Bu örnek okuma ve yazma iletileri kablo temsilinin iç kodlayıcıya temsilci ve sıkıştırmayı veya sonuçları sıkıştırmasını sıkıştırma Kodlayıcısı olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="5cec4-145">This allows the sample to delegate the reading and writing of the wire representation of messages to the inner encoder and allows the compression encoder to compress or decompress the results.</span></span> <span data-ttu-id="5cec4-146">İleti kodlama için herhangi bir işlem hattı olduğundan, birden çok kodlayıcılar WCF'de kullanmak için tek model budur.</span><span class="sxs-lookup"><span data-stu-id="5cec4-146">Because there is no pipeline for message encoding, this is the only model for using multiple encoders in WCF.</span></span> <span data-ttu-id="5cec4-147">İleti sıkıştırması açılmış sonra elde edilen ileti işlemek kanal yığın yığında geçirilir.</span><span class="sxs-lookup"><span data-stu-id="5cec4-147">Once the message has been decompressed, the resulting message is passed up the stack for the channel stack to handle.</span></span> <span data-ttu-id="5cec4-148">Sıkıştırma sırasında elde edilen sıkıştırılmış iletisi doğrudan sağlanan akışına yazılır.</span><span class="sxs-lookup"><span data-stu-id="5cec4-148">During compression, the resulting compressed message is written directly to the stream provided.</span></span>  
  
 <span data-ttu-id="5cec4-149">Bu örnek yardımcı yöntemler kullanır (`CompressBuffer` ve `DecompressBuffer`) kullanılacak akış arabellekleri dönüştürme gerçekleştirmek için `GZipStream` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5cec4-149">This sample uses helper methods (`CompressBuffer` and `DecompressBuffer`) to perform conversion from buffers to streams to use the `GZipStream` class.</span></span>  
  
 <span data-ttu-id="5cec4-150">Arabelleğe alınan `ReadMessage` ve `WriteMessage` sınıflarının kullanımını `BufferManager` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5cec4-150">The buffered `ReadMessage` and `WriteMessage` classes make use of the `BufferManager` class.</span></span> <span data-ttu-id="5cec4-151">Kodlayıcı yalnızca Kodlayıcı factory erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="5cec4-151">The encoder is accessible only through the encoder factory.</span></span> <span data-ttu-id="5cec4-152">Özet `MessageEncoderFactory` SAX adlı bir özellik `Encoder` geçerli Kodlayıcı ve adlı bir yöntem erişmek için `CreateSessionEncoder` oturumları destekleyen bir kodlayıcı oluşturma için.</span><span class="sxs-lookup"><span data-stu-id="5cec4-152">The abstract `MessageEncoderFactory` class provides a property named `Encoder` for accessing the current encoder and a method named `CreateSessionEncoder` for creating an encoder that supports sessions.</span></span> <span data-ttu-id="5cec4-153">Böyle bir kodlayıcı, burada kanal oturumları destekler, sıralanır ve güvenilir bir senaryoda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5cec4-153">Such an encoder can be used in the scenario where the channel supports sessions, is ordered and is reliable.</span></span> <span data-ttu-id="5cec4-154">Bu senaryo için kablo yazılan verilerin her bir oturumda iyileştirme sağlar.</span><span class="sxs-lookup"><span data-stu-id="5cec4-154">This scenario allows for optimization in each session of the data written to the wire.</span></span> <span data-ttu-id="5cec4-155">Bu istenmiyorsa, temel yöntemi aşırı.</span><span class="sxs-lookup"><span data-stu-id="5cec4-155">If this is not desired, the base method should not be overloaded.</span></span> <span data-ttu-id="5cec4-156">`Encoder` Özelliği, oturum olmayan Kodlayıcı ve varsayılan uygulamasını erişmek için bir mekanizma sağlar `CreateSessionEncoder` yöntemi özelliğinin değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="5cec4-156">The `Encoder` property provides a mechanism for accessing the session-less encoder and the default implementation of the `CreateSessionEncoder` method returns the value of the property.</span></span> <span data-ttu-id="5cec4-157">Örnek sıkıştırma sağlamak için var olan bir kodlayıcı sarmalar çünkü `MessageEncoderFactory` uygulama kabul eden bir `MessageEncoderFactory` , iç Kodlayıcı üretecini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5cec4-157">Because the sample wraps an existing encoder to provide compression, the `MessageEncoderFactory` implementation accepts a `MessageEncoderFactory` that represents the inner encoder factory.</span></span>  
  
 <span data-ttu-id="5cec4-158">Kodlayıcı ve Kodlayıcı Fabrika tanımlanan, bir WCF istemcisi ve hizmet ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5cec4-158">Now that the encoder and encoder factory are defined, they can be used with a WCF client and service.</span></span> <span data-ttu-id="5cec4-159">Ancak, bu kodlayıcılar kanal yığına eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="5cec4-159">However, these encoders must be added to the channel stack.</span></span> <span data-ttu-id="5cec4-160">Sınıfları türetebilirsiniz <xref:System.ServiceModel.ServiceHost> ve <xref:System.ServiceModel.ChannelFactory%601> sınıfları ve geçersiz kılma `OnInitialize` bu Kodlayıcı Fabrika el ile eklemek için yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="5cec4-160">You can derive classes from the <xref:System.ServiceModel.ServiceHost> and <xref:System.ServiceModel.ChannelFactory%601> classes and override the `OnInitialize` methods to add this encoder factory manually.</span></span> <span data-ttu-id="5cec4-161">Kodlayıcı factory üzerinden özel bağlama öğesinin üzerinden kullanıma sunabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5cec4-161">You can also expose the encoder factory through a custom binding element.</span></span>  
  
 <span data-ttu-id="5cec4-162">Yeni bir özel bağlama öğesi oluşturmak için öğesinden bir sınıf türetin <xref:System.ServiceModel.Channels.BindingElement> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5cec4-162">To create a new custom binding element, derive a class from the <xref:System.ServiceModel.Channels.BindingElement> class.</span></span> <span data-ttu-id="5cec4-163">Ancak, birden fazla bağlama öğeleri vardır.</span><span class="sxs-lookup"><span data-stu-id="5cec4-163">There are, however, several types of binding elements.</span></span> <span data-ttu-id="5cec4-164">Özel bağlama öğesi bir ileti kodlama bağlama öğesi değerlendirilmiştir emin olmak için aynı zamanda uygulamanız gereken <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="5cec4-164">To ensure that the custom binding element is recognized as a message encoding binding element, you also must implement the <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.</span></span> <span data-ttu-id="5cec4-165"><xref:System.ServiceModel.Channels.MessageEncodingBindingElement> Yeni bir ileti Kodlayıcı fabrikası oluşturmak için bir yöntem sunar (`CreateMessageEncoderFactory`), eşleşen ileti Kodlayıcı üretecin bir örneğini döndürmek için uygulanır.</span><span class="sxs-lookup"><span data-stu-id="5cec4-165">The <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> exposes a method for creating a new message encoder factory (`CreateMessageEncoderFactory`), which is implemented to return an instance of the matching message encoder factory.</span></span> <span data-ttu-id="5cec4-166">Ayrıca, <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> adresleme sürümü belirtmek üzere bir özelliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="5cec4-166">Additionally, the <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> has a property to indicate the addressing version.</span></span> <span data-ttu-id="5cec4-167">Bu örnek mevcut kodlayıcılarda sarmalar olduğundan, örnek uygulama ayrıca bağlama öğelerinin var olan Kodlayıcı sarmalar ve oluşturucusuna bir parametre olarak bağlama öğesi bir iç Kodlayıcı alır ve özelliği aracılığıyla kullanıma sunduğu.</span><span class="sxs-lookup"><span data-stu-id="5cec4-167">Because this sample wraps the existing encoders, the sample implementation also wraps the existing encoder binding elements and takes an inner encoder binding element as a parameter to the constructor and exposes it through a property.</span></span> <span data-ttu-id="5cec4-168">Aşağıdaki örnek kod uygulamasını gösterir `GZipMessageEncodingBindingElement` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5cec4-168">The following sample code shows the implementation of the `GZipMessageEncodingBindingElement` class.</span></span>  
  
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
  
 <span data-ttu-id="5cec4-169">Unutmayın `GZipMessageEncodingBindingElement` sınıfının Implements `IPolicyExportExtension` interface böylece bu bağlama öğesi meta verileri, bir ilke olarak aşağıdaki örnekte gösterildiği gibi dışarı aktarılabilir.</span><span class="sxs-lookup"><span data-stu-id="5cec4-169">Note that `GZipMessageEncodingBindingElement` class implements the `IPolicyExportExtension` interface, so that this binding element can be exported as a policy in metadata, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="5cec4-170">`GZipMessageEncodingBindingElementImporter` Sınıfının Implements `IPolicyImportExtension` arabirimi bu sınıf, ilke için alır `GZipMessageEncodingBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="5cec4-170">The `GZipMessageEncodingBindingElementImporter` class implements the `IPolicyImportExtension` interface, this class imports policy for `GZipMessageEncodingBindingElement`.</span></span> <span data-ttu-id="5cec4-171">İlkeleri yapılandırma dosyasına işlemek için içeri aktarmak için svcutil.exe aracını kullanılabilir `GZipMessageEncodingBindingElement`, aşağıdakiler için Svcutil.exe.config eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="5cec4-171">Svcutil.exe tool can be used to import policies to the configuration file, to handle `GZipMessageEncodingBindingElement`, the following should be added to Svcutil.exe.config.</span></span>  
  
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
  
 <span data-ttu-id="5cec4-172">Yoktur, sıkıştırma Kodlayıcısı için eşleşen bir bağlama öğesi, program aracılığıyla hizmet veya istemci yeni bir özel bağlama nesnesi oluşturma ve aşağıdaki örnek kodda gösterildiği gibi özel bir bağlama öğesi, ekleyerek bağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="5cec4-172">Now that there is a matching binding element for the compression encoder, it can be programmatically hooked into the service or client by constructing a new custom binding object and adding the custom binding element to it, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="5cec4-173">Bu kullanıcı senaryolarının çoğunluğu için yeterli olabilir, ancak dosya yapılandırmasını destekleyen bir hizmet Web barındırılan olması durumunda kritik öneme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="5cec4-173">While this may be sufficient for the majority of user scenarios, supporting a file configuration is critical if a service is to be Web-hosted.</span></span> <span data-ttu-id="5cec4-174">Web barındırma senaryosunda desteklemek için bir dosyada yapılandırılabilir olması bir özel bağlama öğeye izin vermek için özel yapılandırma işleyicisi geliştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5cec4-174">To support the Web-hosted scenario, you must develop a custom configuration handler to allow a custom binding element to be configurable in a file.</span></span>  
  
 <span data-ttu-id="5cec4-175">Yapılandırma sistemi tarafından sağlanan üzerine bağlama öğesi için bir yapılandırma işleyicisi oluşturabileceğinizi [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5cec4-175">You can build a configuration handler for the binding element on top of the configuration system provided by the [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].</span></span> <span data-ttu-id="5cec4-176">Bağlama öğesi yapılandırması işleyicisi öğesinden türetilmelidir <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5cec4-176">The configuration handler for the binding element must derive from the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> class.</span></span> <span data-ttu-id="5cec4-177">`BindingElementType` Özelliği, bağlama öğesi bu bölüm için oluşturulacak tür yapılandırma sistemi bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5cec4-177">The `BindingElementType` property is used to inform the configuration system of the type of binding element to create for this section.</span></span> <span data-ttu-id="5cec4-178">Tüm yönlerini `BindingElement` , olabilir set ortaya özellikleri olarak <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> türetilmiş sınıf.</span><span class="sxs-lookup"><span data-stu-id="5cec4-178">All aspects of the `BindingElement` that can be set should be exposed as properties in the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> derived class.</span></span> <span data-ttu-id="5cec4-179"><xref:System.Configuration.ConfigurationPropertyAttribute> Yapılandırma öğesi özniteliklerini eşleme özelliklerini ve özniteliklerini eksikse, varsayılan değerleri ayarlama yardımcı olmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5cec4-179">The <xref:System.Configuration.ConfigurationPropertyAttribute> is used to assist in mapping the configuration element attributes to the properties and setting default values if attributes are missing.</span></span> <span data-ttu-id="5cec4-180">Yapılandırma değerleri yüklenir ve özelliklerine uygulanan sonra <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> yöntemi çağrıldığında, hangi özellikler bir bağlama öğesi somut bir örneğine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="5cec4-180">After the values from configuration are loaded and applied to the properties, the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> method is called, which converts the properties into a concrete instance of a binding element.</span></span> <span data-ttu-id="5cec4-181"><xref:System.ServiceModel.Configuration.BindingElementExtensionElement.ApplyConfiguration%2A> Özelliklerini dönüştürmek için kullanılan yöntemi <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> yaratım bağlama öğesi üzerindeki ayarlamak için değerler türetilmiş sınıf.</span><span class="sxs-lookup"><span data-stu-id="5cec4-181">The <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.ApplyConfiguration%2A> method is used to convert the properties on the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> derived class into the values to be set on the newlycreated binding element.</span></span>  
  
 <span data-ttu-id="5cec4-182">Aşağıdaki örnek kod uygulamasını gösterir `GZipMessageEncodingElement`.</span><span class="sxs-lookup"><span data-stu-id="5cec4-182">The following sample code shows the implementation of the `GZipMessageEncodingElement`.</span></span>  
  
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
  
 <span data-ttu-id="5cec4-183">Bu yapılandırma işleyicisi, hizmet veya istemci için App.config veya Web.config aşağıdaki gösterimi eşler.</span><span class="sxs-lookup"><span data-stu-id="5cec4-183">This configuration handler maps to the following representation in the App.config or Web.config for the service or client.</span></span>  
  
```xml  
<gzipMessageEncoding innerMessageEncoding="textMessageEncoding" />  
```  
  
 <span data-ttu-id="5cec4-184">Bu yapılandırma işleyicisi kullanmak için onu içinde kaydedilmelidir [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) aşağıdaki örnek yapılandırmada gösterildiği öğesi.</span><span class="sxs-lookup"><span data-stu-id="5cec4-184">To use this configuration handler, it must be registered within the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="5cec4-185">Sunucu çalıştırdığınızda, işlem isteklerini ve yanıtlarını konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5cec4-185">When you run the server, the operation requests and responses are displayed in the console window.</span></span> <span data-ttu-id="5cec4-186">Pencerenin sunucuyu kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="5cec4-186">Press ENTER in the window to shut down the server.</span></span>  
  
```  
Press Enter key to Exit.  
  
        Server Echo(string input) called:  
        Client message: Simple hello  
  
        Server BigEcho(string[] input) called:  
        64 client messages  
```  
  
 <span data-ttu-id="5cec4-187">İşlem istekleri ve yanıtları, istemci çalıştırdığınızda, konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5cec4-187">When you run the client, the operation requests and responses are displayed in the console window.</span></span> <span data-ttu-id="5cec4-188">İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="5cec4-188">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Calling Echo(string):  
Server responds: Simple hello Simple hello  
  
Calling BigEcho(string[]):  
Server responds: Hello 0  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5cec4-189">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="5cec4-189">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="5cec4-190">Yükleme [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 aşağıdaki komutu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="5cec4-190">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command:</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="5cec4-191">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5cec4-191">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="5cec4-192">Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5cec4-192">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="5cec4-193">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5cec4-193">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5cec4-194">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="5cec4-194">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5cec4-195">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="5cec4-195">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5cec4-196">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="5cec4-196">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5cec4-197">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="5cec4-197">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`  
  
## <a name="see-also"></a><span data-ttu-id="5cec4-198">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5cec4-198">See Also</span></span>
