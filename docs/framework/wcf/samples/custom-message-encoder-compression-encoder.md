---
title: 'Özel İleti Kodlayıcı: Sıkıştırma Kodlayıcısı'
ms.date: 03/30/2017
ms.assetid: 57450b6c-89fe-4b8a-8376-3d794857bfd7
ms.openlocfilehash: b70875e385fa32256476f6d1ae53e8cc1f5ff9de
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46525311"
---
# <a name="custom-message-encoder-compression-encoder"></a>Özel İleti Kodlayıcı: Sıkıştırma Kodlayıcısı
Bu örnek, Windows Communication Foundation (WCF) platformunu kullanarak özel bir kodlayıcı uygulamak nasıl gösterir.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Bu örnek, bir istemci konsol program (.exe), şirket içinde barındırılan hizmeti bir konsol programı (.exe) ve sıkıştırma ileti Kodlayıcı kitaplığı (.dll) oluşur. Hizmet istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular. Anlaşma tarafından tanımlanan `ISampleServer` temel dize işlemleri Yankı sunan arabirimi (`Echo` ve `BigEcho`). İstemcinin istemciye ileti tekrarlayarak belirli bir işlemi ve hizmet yanıt zaman uyumlu istekleri yapar. Hizmet ve istemci etkinliği konsol pencerelerinde görünür olur. Bu örnek amacı, özel bir kodlayıcı yazma ve bir iletinin hat üzerinde sıkıştırma etkisini gösteren göstermektir. İleti boyutu, işlem süresi veya her ikisi de hesaplamak için sıkıştırma ileti Kodlayıcı için izleme ekleyebilirsiniz.  
  
> [!NOTE]
>  Sunucu (GZip veya Deflate gibi bir algoritma ile oluşturulan) sıkıştırılmış bir yanıt gönderiyorsa .NET Framework 4'te bir WCF istemcisini otomatik sıkıştırma etkinleştirildi. Internet Information Server (IIS) Web barındırılan hizmeti, IIS, sıkıştırılmış bir yanıt göndermek hizmet için yapılandırılabilir. Bu örnek, sıkıştırma ve açma hem istemci hem de hizmet yapma gereksinimi varsa veya şirket içinde barındırılan hizmet ise kullanılabilir.  
  
 Örnek oluşturma ve bir WCF uygulamaya özel ileti Kodlayıcı tümleştirme gösterir. ' % S'kitaplığı GZipEncoder.dll hem istemci hem de hizmet ile dağıtılır. Bu örnek, ayrıca ileti sıkıştırma etkisini gösterir. GZipEncoder.dll kodda şunlar gösterilmektedir:  
  
-   Özel bir kodlayıcı ve Kodlayıcı fabrikası oluşturma.  
  
-   Bir bağlama öğesi için özel bir kodlayıcı geliştirme.  
  
-   Özel bağlama yapılandırma özel bağlama öğeleri tümleştirmek için kullanma.  
  
-   Özel bağlama öğesinin dosya yapılandırması izin vermek için özel yapılandırma işleyicisi geliştirme.  
  
 Daha önce belirtildiği gibi özel bir kodlayıcı uygulanan birden fazla katman vardır. Her biri bu Katmanlar arasındaki ilişkiyi daha iyi anlamak için aşağıdaki listede hizmet başlatma için basitleştirilmiş bir olaylar dizisi şöyledir:  
  
1.  Sunucuyu başlatır.  
  
2.  Yapılandırma bilgilerini okuyun.  
  
    1.  Özel yapılandırma işleyicisi hizmeti yapılandırmasını kaydeder.  
  
    2.  Hizmet ana bilgisayarı oluşturulur ve açılır.  
  
    3.  Özel yapılandırma öğesi oluşturur ve özel bağlama öğesini döndürür.  
  
    4.  Özel bağlama öğesi oluşturur ve bir ileti Kodlayıcı üreteci döndürür.  
  
3.  Bir ileti alındı.  
  
4.  İleti Kodlayıcı fabrikası iletiyi okumak ve yanıt yazmak için bir ileti Kodlayıcı döndürür.  
  
5.  Kodlayıcı katmanı, bir sınıf üreteci uygulanır. Yalnızca Kodlayıcı sınıf üreteci için özel bir kodlayıcı herkese açık şekilde sunulmalıdır. Fabrika nesnesine bağlama öğesi tarafından döndürülen zaman <xref:System.ServiceModel.ServiceHost> veya <xref:System.ServiceModel.ChannelFactory%601> nesnesi oluşturulur. İleti Kodlayıcı arabelleğe alınan veya akış modunda çalışır. Bu örnek, hem arabellekli modu hem de akış modunu gösterir.  
  
 Her modu için yok yayarsa `ReadMessage` ve `WriteMessage` yöntemi soyut `MessageEncoder` sınıfı. Kodlama iş çoğunu, bu yöntemler de gerçekleşir. Örnek, var olan metin ve ikili ileti kodlayıcılar sarmalar. Bu örnek okuma ve yazma iletileri kablo temsilinin iç kodlayıcıya temsilci ve sıkıştırmayı veya sonuçları sıkıştırmasını sıkıştırma Kodlayıcısı olanak sağlar. İleti kodlama için herhangi bir işlem hattı olduğundan, birden çok kodlayıcılar WCF'de kullanmak için tek model budur. İleti sıkıştırması açılmış sonra elde edilen ileti işlemek kanal yığın yığında geçirilir. Sıkıştırma sırasında elde edilen sıkıştırılmış iletisi doğrudan sağlanan akışına yazılır.  
  
 Bu örnek yardımcı yöntemler kullanır (`CompressBuffer` ve `DecompressBuffer`) kullanılacak akış arabellekleri dönüştürme gerçekleştirmek için `GZipStream` sınıfı.  
  
 Arabelleğe alınan `ReadMessage` ve `WriteMessage` sınıflarının kullanımını `BufferManager` sınıfı. Kodlayıcı yalnızca Kodlayıcı factory erişilebilir. Özet `MessageEncoderFactory` SAX adlı bir özellik `Encoder` geçerli Kodlayıcı ve adlı bir yöntem erişmek için `CreateSessionEncoder` oturumları destekleyen bir kodlayıcı oluşturma için. Böyle bir kodlayıcı, burada kanal oturumları destekler, sıralanır ve güvenilir bir senaryoda kullanılabilir. Bu senaryo için kablo yazılan verilerin her bir oturumda iyileştirme sağlar. Bu istenmiyorsa, temel yöntemi aşırı. `Encoder` Özelliği, oturum olmayan Kodlayıcı ve varsayılan uygulamasını erişmek için bir mekanizma sağlar `CreateSessionEncoder` yöntemi özelliğinin değerini döndürür. Örnek sıkıştırma sağlamak için var olan bir kodlayıcı sarmalar çünkü `MessageEncoderFactory` uygulama kabul eden bir `MessageEncoderFactory` , iç Kodlayıcı üretecini temsil eder.  
  
 Kodlayıcı ve Kodlayıcı Fabrika tanımlanan, bir WCF istemcisi ve hizmet ile kullanılabilir. Ancak, bu kodlayıcılar kanal yığına eklenmesi gerekir. Sınıfları türetebilirsiniz <xref:System.ServiceModel.ServiceHost> ve <xref:System.ServiceModel.ChannelFactory%601> sınıfları ve geçersiz kılma `OnInitialize` bu Kodlayıcı Fabrika el ile eklemek için yöntemleri. Kodlayıcı factory üzerinden özel bağlama öğesinin üzerinden kullanıma sunabilirsiniz.  
  
 Yeni bir özel bağlama öğesi oluşturmak için öğesinden bir sınıf türetin <xref:System.ServiceModel.Channels.BindingElement> sınıfı. Ancak, birden fazla bağlama öğeleri vardır. Özel bağlama öğesi bir ileti kodlama bağlama öğesi değerlendirilmiştir emin olmak için aynı zamanda uygulamanız gereken <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>. <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> Yeni bir ileti Kodlayıcı fabrikası oluşturmak için bir yöntem sunar (`CreateMessageEncoderFactory`), eşleşen ileti Kodlayıcı üretecin bir örneğini döndürmek için uygulanır. Ayrıca, <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> adresleme sürümü belirtmek üzere bir özelliğe sahiptir. Bu örnek mevcut kodlayıcılarda sarmalar olduğundan, örnek uygulama ayrıca bağlama öğelerinin var olan Kodlayıcı sarmalar ve oluşturucusuna bir parametre olarak bağlama öğesi bir iç Kodlayıcı alır ve özelliği aracılığıyla kullanıma sunduğu. Aşağıdaki örnek kod uygulamasını gösterir `GZipMessageEncodingBindingElement` sınıfı.  
  
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
  
 Unutmayın `GZipMessageEncodingBindingElement` sınıfının Implements `IPolicyExportExtension` interface böylece bu bağlama öğesi meta verileri, bir ilke olarak aşağıdaki örnekte gösterildiği gibi dışarı aktarılabilir.  
  
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
  
 `GZipMessageEncodingBindingElementImporter` Sınıfının Implements `IPolicyImportExtension` arabirimi bu sınıf, ilke için alır `GZipMessageEncodingBindingElement`. İlkeleri yapılandırma dosyasına işlemek için içeri aktarmak için svcutil.exe aracını kullanılabilir `GZipMessageEncodingBindingElement`, aşağıdakiler için Svcutil.exe.config eklenmelidir.  
  
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
  
 Yoktur, sıkıştırma Kodlayıcısı için eşleşen bir bağlama öğesi, program aracılığıyla hizmet veya istemci yeni bir özel bağlama nesnesi oluşturma ve aşağıdaki örnek kodda gösterildiği gibi özel bir bağlama öğesi, ekleyerek bağlanabilir.  
  
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
  
 Bu kullanıcı senaryolarının çoğunluğu için yeterli olabilir, ancak dosya yapılandırmasını destekleyen bir hizmet Web barındırılan olması durumunda kritik öneme sahiptir. Web barındırma senaryosunda desteklemek için bir dosyada yapılandırılabilir olması bir özel bağlama öğeye izin vermek için özel yapılandırma işleyicisi geliştirmeniz gerekir.  
  
 Yapılandırma sistemi tarafından sağlanan üzerine bağlama öğesi için bir yapılandırma işleyicisi oluşturabileceğinizi [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)]. Bağlama öğesi yapılandırması işleyicisi öğesinden türetilmelidir <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> sınıfı. `BindingElementType` Özelliği, bağlama öğesi bu bölüm için oluşturulacak tür yapılandırma sistemi bildirmek için kullanılır. Tüm yönlerini `BindingElement` , olabilir set ortaya özellikleri olarak <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> türetilmiş sınıf. <xref:System.Configuration.ConfigurationPropertyAttribute> Yapılandırma öğesi özniteliklerini eşleme özelliklerini ve özniteliklerini eksikse, varsayılan değerleri ayarlama yardımcı olmak için kullanılır. Yapılandırma değerleri yüklenir ve özelliklerine uygulanan sonra <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> yöntemi çağrıldığında, hangi özellikler bir bağlama öğesi somut bir örneğine dönüştürür. <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.ApplyConfiguration%2A> Özelliklerini dönüştürmek için kullanılan yöntemi <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> yaratım bağlama öğesi üzerindeki ayarlamak için değerler türetilmiş sınıf.  
  
 Aşağıdaki örnek kod uygulamasını gösterir `GZipMessageEncodingElement`.  
  
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
  
 Bu yapılandırma işleyicisi, hizmet veya istemci için App.config veya Web.config aşağıdaki gösterimi eşler.  
  
```xml  
<gzipMessageEncoding innerMessageEncoding="textMessageEncoding" />  
```  
  
 Bu yapılandırma işleyicisi kullanmak için onu içinde kaydedilmelidir [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) aşağıdaki örnek yapılandırmada gösterildiği öğesi.  
  
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
  
 Sunucu çalıştırdığınızda, işlem isteklerini ve yanıtlarını konsol penceresinde görüntülenir. Pencerenin sunucuyu kapatmak için ENTER tuşuna basın.  
  
```  
Press Enter key to Exit.  
  
        Server Echo(string input) called:  
        Client message: Simple hello  
  
        Server BigEcho(string[] input) called:  
        64 client messages  
```  
  
 İşlem istekleri ve yanıtları, istemci çalıştırdığınızda, konsol penceresinde görüntülenir. İstemci bilgisayarı için istemci penceresinde ENTER tuşuna basın.  
  
```  
Calling Echo(string):  
Server responds: Simple hello Simple hello  
  
Calling BigEcho(string[]):  
Server responds: Hello 0  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Yükleme [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 aşağıdaki komutu kullanarak:  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`  
  
## <a name="see-also"></a>Ayrıca Bkz.
