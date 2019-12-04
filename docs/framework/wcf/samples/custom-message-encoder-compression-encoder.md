---
title: 'Özel İleti Kodlayıcı: Sıkıştırma Kodlayıcısı'
ms.date: 03/30/2017
ms.assetid: 57450b6c-89fe-4b8a-8376-3d794857bfd7
ms.openlocfilehash: 80dd29569897be501d76024a081f38ec5add4ff7
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716856"
---
# <a name="custom-message-encoder-compression-encoder"></a>Özel İleti Kodlayıcı: Sıkıştırma Kodlayıcısı

Bu örnek, Windows Communication Foundation (WCF) platformunu kullanarak nasıl özel bir kodlayıcı uygulanacağını gösterir.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`

## <a name="sample-details"></a>Örnek Ayrıntılar

Bu örnek, bir istemci konsolu programından (. exe), şirket içinde barındırılan bir hizmet konsolu programından (. exe) ve bir sıkıştırma ileti Kodlayıcısı kitaplığından (. dll) oluşur. Hizmet, istek-yanıt iletişim modelini tanımlayan bir sözleşme uygular. Sözleşme, temel dize yankı işlemlerini (`Echo` ve `BigEcho`) sunan `ISampleServer` arabirimi tarafından tanımlanır. İstemci, iletiyi istemciye geri tekrarlayarak, belirli bir işleme ve hizmet yanıtlarını zaman uyumlu istekler yapar. İstemci ve hizmet etkinliği konsol penceresinde görünür. Bu örneğin amacı, bir özel kodlayıcının nasıl yazılacağını ve bir iletinin kabloda sıkıştırılma etkisini gösterir. İleti boyutunu, işlem süresini veya her ikisini de hesaplamak için, sıkıştırma iletisi kodlayıcıya izleme ekleyebilirsiniz.

> [!NOTE]
> .NET Framework 4 ' te, sunucu sıkıştırılmış bir yanıt gönderiyorsa (GZip veya söndür gibi bir algoritmayla oluşturulmuş) WCF istemcisinde otomatik açma özelliği etkinleştirilmiştir. Hizmet, Internet Information Server 'da (IIS) Web 'de barındırılıyorsa, hizmetin sıkıştırılmış bir yanıt gönderebilmesi için IIS yapılandırılabilir. Bu örnek, gereksinim hem istemcide hem de hizmette sıkıştırma yapmak ve sıkıştırmayı açmak ya da hizmetin şirket içinde barındırılması durumunda kullanılabilir.

Örnek, bir WCF uygulamasında özel bir ileti Kodlayıcısı oluşturmayı ve tümleştirmeyi gösterir. GZipEncoder. dll kitaplığı hem istemci hem de hizmetle birlikte dağıtılır. Bu örnek ayrıca iletileri sıkıştırma etkisini de gösterir. GZipEncoder. dll içindeki kod şunları gösterir:

- Özel kodlayıcı ve kodlayıcı fabrikası oluşturma.

- Özel bir kodlayıcı için bağlama öğesi geliştirme.

- Özel bağlama öğelerini tümleştirmek için özel bağlama yapılandırması kullanma.

- Özel bir bağlama öğesinin dosya yapılandırmasına izin vermek için özel bir yapılandırma işleyicisi geliştirme.

Daha önce belirtildiği gibi, özel bir kodlayıcıda uygulanan birkaç katman vardır. Bu katmanların her biri arasındaki ilişkiyi daha iyi göstermek için, hizmet başlatma için daha basit bir olay sırası aşağıdaki listede verilmiştir:

1. Sunucu başlatılır.

2. Yapılandırma bilgileri okundu.

    1. Hizmet yapılandırması özel yapılandırma işleyicisini kaydeder.

    2. Hizmet ana bilgisayarı oluşturulup açılır.

    3. Özel yapılandırma öğesi, özel bağlama öğesini oluşturur ve döndürür.

    4. Özel bağlama öğesi bir ileti Kodlayıcısı fabrikası oluşturur ve döndürür.

3. İleti alındı.

4. İleti Kodlayıcısı fabrikası iletiyi okumak ve yanıtı yazmak için bir ileti Kodlayıcısı döndürür.

5. Kodlayıcı katmanı bir sınıf fabrikası olarak uygulanır. Özel Kodlayıcı için yalnızca kodlayıcı sınıf fabrikası genel kullanıma açık olmalıdır. Factory nesnesi, <xref:System.ServiceModel.ServiceHost> veya <xref:System.ServiceModel.ChannelFactory%601> nesnesi oluşturulduğunda Binding öğesi tarafından döndürülür. İleti kodlayıcıları, ara belleğe alınmış veya akış modunda çalışabilir. Bu örnek, hem arabellekli modu hem de akış modunu gösterir.

Her mod için soyut `MessageEncoder` sınıfında eşlik eden bir `ReadMessage` ve `WriteMessage` yöntemi vardır. Bu yöntemlerde kodlama işinin çoğu gerçekleşir. Örnek, varolan metni ve ikili ileti kodlayıcıları ' nı sarmalar. Bu, örneğin, iletilerin tel gösterimini okuma ve yazma yetkisini iç kodlayıcıya devredebilir ve sıkıştırma kodlayıcının sonuçları sıkıştırmak veya sıkıştırmasını açmasına olanak sağlar. İleti kodlama için bir işlem hattı olmadığından, bu, WCF 'de birden çok kodlayıcıda kullanılmasına yönelik tek modeldir. İleti açıldıktan sonra, ortaya çıkan ileti, işlemek için kanal yığınının yığınını iletilir. Sıkıştırma sırasında, elde edilen sıkıştırılmış ileti doğrudan verilen akışa yazılır.

Bu örnek, `GZipStream` sınıfını kullanmak üzere arabelleklerden akışlara dönüştürme gerçekleştirmek için yardımcı yöntemleri (`CompressBuffer` ve `DecompressBuffer`) kullanır.

Arabelleğe alınan `ReadMessage` ve `WriteMessage` sınıfları `BufferManager` sınıfını kullanır. Kodlayıcı yalnızca kodlayıcı fabrikası aracılığıyla erişilebilir. Soyut `MessageEncoderFactory` sınıfı, geçerli kodlayıcıya erişmek için `Encoder` adlı bir özellik ve oturumları destekleyen bir kodlayıcı oluşturmak için `CreateSessionEncoder` adlı bir yöntem sağlar. Bu tür bir kodlayıcı, kanalın oturumları desteklediği, sıralandığı ve güvenilir olduğu senaryolarda kullanılabilir. Bu senaryo, hatta yazılı verilerin her oturumunda iyileştirmeye olanak tanır. Bu istenmiyorsa, temel yöntemin aşırı yüklenmiş olması gerekir. `Encoder` özelliği, oturum-daha az kodlayıcıya erişim mekanizması sağlar ve `CreateSessionEncoder` yönteminin varsayılan uygulamasında özelliğin değeri döndürülür. Örnek, sıkıştırma sağlamak için mevcut bir Kodlayıcısı sarmaladığı için `MessageEncoderFactory` uygulama, iç Kodlayıcı fabrikasını temsil eden bir `MessageEncoderFactory` kabul eder.

Kodlayıcı ve kodlayıcı fabrikası tanımlandığına göre, bunlar bir WCF istemcisi ve hizmeti ile birlikte kullanılabilir. Ancak, bu kodlayıcılara kanal yığınına eklenmeleri gerekir. <xref:System.ServiceModel.ServiceHost> ve <xref:System.ServiceModel.ChannelFactory%601> sınıflarından sınıfları türetebilir ve bu kodlayıcı fabrikasını el ile eklemek için `OnInitialize` yöntemlerini geçersiz kılabilirsiniz. Ayrıca, özel bağlama öğesi aracılığıyla Kodlayıcı fabrikasını kullanıma sunabilirsiniz.

Yeni bir özel bağlama öğesi oluşturmak için <xref:System.ServiceModel.Channels.BindingElement> sınıfından bir sınıf türetebilirsiniz. Ancak birkaç tür bağlama öğesi vardır. Özel bağlama öğesinin bir ileti kodlama bağlama öğesi olarak tanındığından emin olmak için, <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>de uygulamanız gerekir. <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>, eşleşen ileti Kodlayıcısı fabrikasının bir örneğini döndürmek için uygulanan yeni bir ileti Kodlayıcısı Fabrikası (`CreateMessageEncoderFactory`) oluşturmak için bir yöntem sunar. Ayrıca, <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> adresleme sürümünü belirten bir özelliğine sahiptir. Bu örnek varolan kodlayıcıları sarmaladığı için, örnek uygulama aynı zamanda var olan Kodlayıcı bağlama öğelerini sarmalanmış ve bir iç Kodlayıcı bağlama öğesini bir parametre olarak oluşturucuya alır ve bunu bir özellik aracılığıyla gösterir. Aşağıdaki örnek kod `GZipMessageEncodingBindingElement` sınıfının uygulamasını gösterir.

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

Bu bağlama öğesinin, aşağıdaki örnekte gösterildiği gibi, meta verilerde bir ilke olarak verilebilmesi için `GZipMessageEncodingBindingElement` sınıfının `IPolicyExportExtension` arabirimini uyguladığını unutmayın.

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

`GZipMessageEncodingBindingElementImporter` sınıfı `IPolicyImportExtension` arabirimini uygular, bu sınıf `GZipMessageEncodingBindingElement`için ilkeyi içeri aktarır. Svcutil. exe aracı, ilkeleri yapılandırma dosyasına aktarmak, `GZipMessageEncodingBindingElement`işlemek için kullanılabilir, aşağıdaki, Svcutil. exe. config dosyasına eklenmelidir.

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

Artık, Sıkıştırma Kodlayıcısı için eşleşen bir bağlama öğesi olduğuna göre, aşağıdaki örnek kodda gösterildiği gibi yeni bir özel bağlama nesnesi oluşturup buna özel bağlama öğesini ekleyerek hizmet veya istemciye program aracılığıyla bağlanabilir.

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

Bu, Kullanıcı senaryolarının çoğunluğu için yeterli olabileceğinden, bir hizmetin Web 'de barındırılması durumunda dosya yapılandırmasını desteklemek kritik öneme sahiptir. Web 'de barındırılan senaryoyu desteklemek için, bir özel bağlama öğesinin bir dosyada yapılandırılabilir olmasını sağlamak üzere özel bir yapılandırma işleyicisi geliştirmeniz gerekir.

Yapılandırma sisteminin en üstünde bağlama öğesi için bir yapılandırma işleyicisi oluşturabilirsiniz. Binding öğesi için yapılandırma işleyicisi <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> sınıfından türetilmelidir. <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.BindingElementType?displayProperty=nameWithType>, bu bölüm için oluşturulacak bağlama öğesi türünün yapılandırma sistemine bildirir. `BindingElement` ayarlanmayan tüm yönleri <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> türetilmiş sınıfta özellikler olarak kullanıma sunulmalıdır. <xref:System.Configuration.ConfigurationPropertyAttribute>, yapılandırma öğesi özniteliklerinin özelliklerle eşlenmesiyle ve özniteliklerin eksik olması halinde varsayılan değerlerin ayarlanmasına yardımcı olur. Yapılandırma değerleri yüklendikten ve özelliklere uygulandıktan sonra, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A?displayProperty=nameWithType> metodu çağrılır, bu da özellikleri bağlama öğesinin somut bir örneğine dönüştürür. <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.ApplyConfiguration%2A?displayProperty=nameWithType> yöntemi, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> türetilmiş sınıftaki özellikleri yeni oluşturulan bağlama öğesinde ayarlanacak değerlere dönüştürmek için kullanılır.

Aşağıdaki örnek kod `GZipMessageEncodingElement`uygulamasını gösterir.

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

Bu yapılandırma işleyicisi, hizmet veya istemcinin App. config veya Web. config dosyasında aşağıdaki gösterimiyle eşleşir.

```xml
<gzipMessageEncoding innerMessageEncoding="textMessageEncoding" />
```

Bu yapılandırma işleyicisini kullanmak için, aşağıdaki örnek yapılandırmada gösterildiği gibi [\<System. serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) öğesi içinde kayıtlı olmalıdır.

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

Sunucuyu çalıştırdığınızda, işlem istekleri ve yanıtları konsol penceresinde görüntülenir. Sunucuyu kapatmak için pencerede ENTER tuşuna basın.

```console
Press Enter key to Exit.

        Server Echo(string input) called:
        Client message: Simple hello

        Server BigEcho(string[] input) called:
        64 client messages
```

İstemcisini çalıştırdığınızda, işlem istekleri ve yanıtları konsol penceresinde görüntülenir. İstemcisini kapatmak için istemci penceresinde ENTER tuşuna basın.

```console
Calling Echo(string):
Server responds: Simple hello Simple hello

Calling BigEcho(string[]):
Server responds: Hello 0

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. Aşağıdaki komutu kullanarak ASP.NET 4,0 'yi yükler:

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

3. Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümündeki yönergeleri izleyin.

4. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`
