---
title: 'Özel İleti Kodlayıcı: Sıkıştırma Kodlayıcısı'
ms.date: 03/30/2017
ms.assetid: 57450b6c-89fe-4b8a-8376-3d794857bfd7
ms.openlocfilehash: 5dc665da3b28a98f1b3016d38ce706bf77dce06f
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="custom-message-encoder-compression-encoder"></a>Özel İleti Kodlayıcı: Sıkıştırma Kodlayıcısı
Bu örnek, Windows Communication Foundation (WCF) platformu kullanarak özel bir kodlayıcı uygulamak gösterilmiştir.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`  
  
## <a name="sample-details"></a>Örnek Ayrıntıları  
 Bu örnek, bir istemci konsol program (.exe), kendini barındıran hizmet konsol program (.exe) ve sıkıştırma ileti Kodlayıcı kitaplığı (.dll) oluşur. Hizmet bir istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular. Anlaşma tarafından tanımlanan `ISampleServer` temel dize işlemleri Yankı kullanıma sunan arabirim (`Echo` ve `BigEcho`). İstemci eş zamanlı istekleri belirli bir işlemi ve hizmet yanıt istemciye ileti tekrarlayarak hale getirir. İstemci ve hizmet etkinliği konsol pencerelerinde görünür olur. Bu örnek amacı, özel bir kodlayıcı yazma ve bir iletinin hat üzerinde sıkıştırma etkisini tanıtmak nasıl göstermektir. İleti boyutu, işlem süresi veya her ikisini hesaplamak için sıkıştırma ileti Kodlayıcı araçları ekleyebilirsiniz.  
  
> [!NOTE]
>  Sunucu (GZip veya Deflate gibi bir algoritmayla oluşturulan) sıkıştırılmış bir yanıt gönderiyorsa, .NET Framework 4'te bir WCF istemcisi otomatik açılması etkinleştirildi. Internet Information Server (IIS) Web barındırılan hizmet ise, IIS sıkıştırılmış yanıt gönderme hizmeti için yapılandırılabilir. Bu örnek, sıkıştırma ve açma hem istemci hem de hizmet yapmak için gereksinim olması veya hizmet kendiliğinden barındırılır kullanılabilir.  
  
 Örnek nasıl oluşturulacağı ve bir WCF uygulamaya özel ileti Kodlayıcı tümleştirmek gösterir. GZipEncoder.dll Kitaplığı hem istemci hem de hizmet ile dağıtılır. Bu örnek ayrıca iletileri sıkıştırma etkisini gösterir. GZipEncoder.dll kodda şunlar gösterilmektedir:  
  
-   Özel Kodlayıcı ve Kodlayıcı Fabrika oluşturma.  
  
-   Bir bağlama öğesi için özel bir kodlayıcı geliştirme.  
  
-   Özel bağlama yapılandırma özel bağlama öğeleri tümleştirmek için kullanma.  
  
-   Özel bağlama öğesi dosya yapılandırılmasına olanak verecek özel yapılandırma işleyicisi geliştirme.  
  
 Daha önce belirtildiği gibi özel bir kodlayıcı uygulanan birkaç katmandan vardır. Bu katmanların her arasındaki ilişkiyi daha iyi anlamak için aşağıdaki listede hizmet başlangıcından için basitleştirilmiş bir olaylar dizisi gösterilmektedir:  
  
1.  Sunucu başlar.  
  
2.  Yapılandırma bilgilerini okuyun.  
  
    1.  Hizmet yapılandırması özel yapılandırma işleyicisi kaydeder.  
  
    2.  Hizmet ana bilgisayarı oluşturulur ve açılır.  
  
    3.  Özel yapılandırma öğesi oluşturur ve özel bağlama öğesi döndürür.  
  
    4.  Özel bağlama öğesi oluşturur ve bir ileti Kodlayıcı fabrikası döndürür.  
  
3.  Bir ileti alındı.  
  
4.  İleti Kodlayıcı Fabrika iletide okumak ve yanıt yazmak için bir ileti Kodlayıcı döndürür.  
  
5.  Kodlayıcı katman üreteci uygulanır. Yalnızca Kodlayıcı üreteci için özel Kodlayıcı herkese açık şekilde sunulmalıdır. Üretecini bağlama öğesi tarafından döndürülen zaman <xref:System.ServiceModel.ServiceHost> veya <xref:System.ServiceModel.ChannelFactory%601> nesnesi oluşturulur. İleti kodlayıcılar arabelleğe alınan veya akış modunda çalışır. Bu örnek arabellekli modu ve akış modu gösterir.  
  
 Her bir modu için yok bir eşlik eden `ReadMessage` ve `WriteMessage` Özet yöntemi `MessageEncoder` sınıfı. Kodlama işi çoğunu bu yöntemler gerçekleşir. Örnek var olan metin ve ikili ileti kodlayıcılar sarmalar. Bu örnek okuma ve yazma işlemini iletilerinin hat gösterimine iç kodlayıcıya temsilci ve sıkıştırmak veya sonuçları sıkıştırmasını açmak sıkıştırma Kodlayıcısı olanak sağlar. İleti kodlama için ardışık düzen yok olduğundan, bu WCF'de birden çok kodlayıcılar kullanarak yalnızca modelidir. İleti sıkıştırması sonra sonuçta elde edilen ileti işlemek için kanal yığın yığınının yukarı geçirilir. Sıkıştırma sırasında elde edilen sıkıştırılmış iletisi sağlanan akış doğrudan yazılmıştır.  
  
 Bu örnek yardımcı yöntemler kullanır (`CompressBuffer` ve `DecompressBuffer`) kullanmak akışlara arabellekleri dönüştürme gerçekleştirmek için `GZipStream` sınıfı.  
  
 Arabelleğe alınan `ReadMessage` ve `WriteMessage` sınıflarının kullanımı `BufferManager` sınıfı. Kodlayıcı yalnızca Kodlayıcı Fabrika erişilebilir. Özet `MessageEncoderFactory` SAX adlı bir özellik `Encoder` geçerli Kodlayıcı ve adlı bir yöntem erişim için `CreateSessionEncoder` oturumları destekleyen bir kodlayıcı oluşturma için. Bu tür bir kodlayıcı burada kanal oturumları destekler, sıralanır ve güvenilir bir senaryoda kullanılabilir. Bu senaryoda her oturum için kablo yazılan veriler, iyileştirme sağlar. Bu değil istenirse, temel yöntemi aşırı yüklenmiş değil. `Encoder` Özelliği oturum daha az Kodlayıcı ve varsayılan uygulaması erişim için bir mekanizma sağlar `CreateSessionEncoder` yöntemi özelliğinin değerini döndürür. Sıkıştırma, sağlamak için var olan bir kodlayıcı örnek sarmalar çünkü `MessageEncoderFactory` uygulama kabul bir `MessageEncoderFactory` , iç Kodlayıcı üretecini temsil eder.  
  
 Kodlayıcı ve Kodlayıcı Fabrika tanımlanan, bir WCF istemcisi ve hizmeti ile kullanılabilir. Ancak, bu kodlayıcılar kanal yığına eklenmesi gerekir. Sınıflardan türetilemeyeceğini <xref:System.ServiceModel.ServiceHost> ve <xref:System.ServiceModel.ChannelFactory%601> sınıfları ve geçersiz kılma `OnInitialize` bu Kodlayıcı Fabrika el ile eklemek için yöntemleri. Özel bağlama öğesi aracılığıyla Kodlayıcı Fabrika ayrıca getirebilir.  
  
 Yeni bir özel bağlama öğesi oluşturmak için öğesinden bir sınıf türetin <xref:System.ServiceModel.Channels.BindingElement> sınıfı. Ancak, çeşitli bağlama öğeleri vardır. Özel bağlama öğesi bağlama öğesi kodlama ileti olarak tanındığından emin olmak için aynı zamanda uygulamanız gereken <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>. <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> Yeni bir ileti Kodlayıcı factory oluşturmak için bir yöntemi gösterir (`CreateMessageEncoderFactory`), eşleşen ileti Kodlayıcı Fabrika örneği döndürülecek uygulanmadı. Ayrıca, <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> adresleme sürüm belirtmek üzere bir özelliğe sahiptir. Bu örnek varolan kodlayıcılar sarmalar olduğundan, örnek uygulama ayrıca bağlama öğeleri varolan Kodlayıcı sarmalar ve parametre olarak oluşturucuya bağlama öğesi bir iç Kodlayıcı alır ve bir özelliği üzerinden kullanıma sunar. Aşağıdaki örnek kod uygulamasını gösterir `GZipMessageEncodingBindingElement` sınıfı.  
  
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
  
 Unutmayın `GZipMessageEncodingBindingElement` uygulayan sınıf `IPolicyExportExtension` arabirim, böylece bu bağlama öğesi meta veri, bir ilke olarak aşağıdaki örnekte gösterildiği gibi aktarılabilir.  
  
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
  
 `GZipMessageEncodingBindingElementImporter` Uygulayan sınıf `IPolicyImportExtension` arabirimi, bu sınıf için ilke alır `GZipMessageEncodingBindingElement`. İlkeleri işlemek için yapılandırma dosyasına aktarmak için svcutil.exe aracı kullanılabilir `GZipMessageEncodingBindingElement`, aşağıdakiler için Svcutil.exe.config eklenmelidir.  
  
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
  
 Yoktur göre sıkıştırma Kodlayıcısı için eşleşen bir bağlama öğesi, bu program aracılığıyla hizmet ya da istemci yeni bir özel bağlama nesnesi oluşturma ve aşağıdaki örnek kodda gösterildiği gibi özel bağlama öğesi, ekleyerek bağlanabilir.  
  
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
  
 Bu kullanıcı senaryoları çoğunluğu için yeterli olabilir, ancak dosya yapılandırmasını destekleyen bir hizmet Web barındırılan olması durumunda kritik öneme sahiptir. Web barındırılan senaryoyu desteklemek için bir dosyada yapılandırılabilir olması bir özel bağlama öğesi izin vermek için özel yapılandırma işleyicisi geliştirmelisiniz.  
  
 Tarafından sağlanan yapılandırma sistemi üstünde bağlama öğesi için bir yapılandırma işleyicisi yapı [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)]. Bağlama öğesi için yapılandırma işleyicisi öğesinden türetilmelidir <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> sınıfı. `BindingElementType` Özelliği için bu bölümü oluşturmak için bağlama öğesi türünün yapılandırma sistemi bildirmek için kullanılır. Tüm yönlerini `BindingElement` , olabilir kümesi ortaya özellikleri olarak <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> türetilmiş sınıf. <xref:System.Configuration.ConfigurationPropertyAttribute> Özellikler için yapılandırma öğesi özniteliklerini eşleme ve öznitelikleri eksikse, varsayılan değerleri ayarlama yardımcı olmak için kullanılır. Yapılandırma değerleri yüklendikten ve özelliklerine uygulanan sonra <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> yöntemi çağrıldığında, hangi özellikler somut bir bağlama öğesi örneğine dönüştürür. <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.ApplyConfiguration%2A> Yöntemi özellikleri dönüştürmek için kullanılan <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> yaratım bağlama öğesi üzerindeki ayarlanacak değerlerinden türetilmiş sınıf.  
  
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
  
 Bu yapılandırma işleyicisi hizmet veya istemci için App.config veya Web.config içinde aşağıdaki gösterimi eşler.  
  
```xml  
<gzipMessageEncoding innerMessageEncoding="textMessageEncoding" />  
```  
  
 Bu yapılandırma işleyicisi kullanmak için onu içinde kaydedilmelidir [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) aşağıdaki örnek yapılandırmada gösterildiği gibi öğesi.  
  
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
  
 Sunucu çalıştırdığınızda, işlem isteklerini ve yanıtlarını konsol penceresinde görüntülenir. Penceresinde sunucuyu kapatmak için ENTER tuşuna basın.  
  
```  
Press Enter key to Exit.  
  
        Server Echo(string input) called:  
        Client message: Simple hello  
  
        Server BigEcho(string[] input) called:  
        64 client messages  
```  
  
 İşlem istekleri ve yanıtları istemci çalıştırdığınızda, konsol penceresinde görüntülenir. İstemcisi penceresinde istemciyi aşağı kapatmak için ENTER tuşuna basın.  
  
```  
Calling Echo(string):  
Server responds: Simple hello Simple hello  
  
Calling BigEcho(string[]):  
Server responds: Hello 0  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Yükleme [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 aşağıdaki komutu kullanarak:  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`  
  
## <a name="see-also"></a>Ayrıca Bkz.
