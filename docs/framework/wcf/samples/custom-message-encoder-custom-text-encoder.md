---
title: 'Özel İleti Kodlayıcı: Özel Metin Kodlayıcı'
ms.date: 03/30/2017
ms.assetid: 68ff5c74-3d33-4b44-bcae-e1d2f5dea0de
ms.openlocfilehash: 369706ecdc2e37a5fb62a448a273b045fe424df8
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33808071"
---
# <a name="custom-message-encoder-custom-text-encoder"></a>Özel İleti Kodlayıcı: Özel Metin Kodlayıcı
Bu örnek, Windows Communication Foundation (WCF) kullanarak özel metin ileti Kodlayıcı uygulamak gösterilmiştir.  
  
> [!WARNING]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Text`  
  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> Yalnızca UTF-8, UTF-16 ve büyük Endean Unicode Kodlamalar WCF destekler. Özel metin ileti Kodlayıcı bu örnekte, tüm platform tarafından desteklenen karakter kodlaması birlikte çalışabilirlik için gerekli olabilecek destekler. Örnek bir istemci konsol program (.exe), Internet Information Services (IIS) ve bir metin ileti Kodlayıcı kitaplığı (.dll) tarafından barındırılan bir hizmet kitaplığı (.dll) oluşur. Hizmet bir istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular. Anlaşma tarafından tanımlanan `ICalculator` matematik işlemleri kullanıma sunan arabirim (eklemek, çıkarma, çarpma ve bölme). İstemci eş zamanlı istekleri verilen matematik işlemi ve sonuç ile hizmet yanıtları yapar. Hem istemci hem de hizmet kullanır `CustomTextMessageEncoder` varsayılan yerine <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.  
  
 Özel Kodlayıcı uygulama ileti Kodlayıcı Fabrika, ileti Kodlayıcı, bağlama öğesi ve yapılandırma işleyicisi kodlama bir ileti oluşur ve aşağıda gösterilmektedir:  
  
-   Özel Kodlayıcı ve Kodlayıcı Fabrika oluşturma.  
  
-   Bir bağlama öğesi için özel bir kodlayıcı oluşturuluyor.  
  
-   Özel bağlama yapılandırma özel bağlama öğeleri tümleştirmek için kullanma.  
  
-   Özel bağlama öğesi dosya yapılandırılmasına olanak verecek özel yapılandırma işleyicisi geliştirme.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Yükleme [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aşağıdaki komutu kullanarak 4.0.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="message-encoder-factory-and-the-message-encoder"></a>İleti Kodlayıcı Fabrika ve ileti kodlayıcı  
 Zaman <xref:System.ServiceModel.ServiceHost> veya istemci kanal açıldığında, tasarım zamanı bileşeni `CustomTextMessageBindingElement` oluşturur `CustomTextMessageEncoderFactory`. Üreteç oluşturur `CustomTextMessageEncoder`. İleti Kodlayıcı hem akış modunda ve arabellekli modu çalışır. Kullandığı <xref:System.Xml.XmlReader> ve <xref:System.Xml.XmlWriter> okumak ve iletileri sırasıyla yazmak için. En iyi duruma getirilmiş XML okuyucuları ve yalnızca UTF-8, UTF-16 ve büyük Endean Unicode desteği yazıcıları WCF aksine bu okuyucuları ve yazıcıları tüm desteklenen platform kodlamayı destekler.  
  
 Aşağıdaki kod örneğinde CustomTextMessageEncoder gösterir.  
  
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
  
 Aşağıdaki kod örneğinde ileti Kodlayıcı Fabrika nasıl oluşturulacağını gösterir.  
  
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
  
## <a name="message-encoding-binding-element"></a>İleti kodlama bağlama öğesi  
 Bağlama öğeleri WCF çalışma zamanı yığınının yapılandırılmasına olanak sağlar. Bir WCF uygulamaya özel ileti Kodlayıcı kullanmak için bir bağlama öğesi gereklidir, çalışma zamanı yığınında uygun düzeyde uygun ayarlarla ileti Kodlayıcı üreteci oluşturur.  
  
 `CustomTextMessageBindingElement` Türetilen <xref:System.ServiceModel.Channels.BindingElement> temel sınıfı ve devraldığı <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> sınıfı. Bu ileti kodlama bağlama öğesi olduğu bu bağlama öğesi tanımak WCF bileşenlerle sağlar. Uygulaması <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> uygun ayarlarla eşleşen ileti Kodlayıcı Fabrika örneğini döndürür.  
  
 `CustomTextMessageBindingElement` Ayarlarını gösteren `MessageVersion`, `ContentType`, ve `Encoding` özellikleri aracılığıyla. Kodlayıcı Soap11Addressing ve Soap12Addressing1 sürümlerini destekler. Soap11Addressing1 varsayılandır. Varsayılan değer olan `ContentType` "text/xml". `Encoding` Özelliği istenen karakter kodlamasını değerini ayarlamanıza olanak sağlar. Örnek istemci hem de hizmet kullanan ISO 8859-1 (Latin1) karakter kodlamasını, tarafından desteklenmeyen <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> WCF.  
  
 Aşağıdaki kod özel metin ileti Kodlayıcısı kullanarak bağlama programlı olarak oluşturulacağını gösterir.  
  
```  
ICollection<BindingElement> bindingElements = new List<BindingElement>();  
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();  
CustomTextMessageBindingElement textBindingElement = new CustomTextMessageBindingElement();  
bindingElements.Add(textBindingElement);  
bindingElements.Add(httpBindingElement);  
CustomBinding binding = new CustomBinding(bindingElements);  
```  
  
## <a name="adding-metadata-support-to-the-message-encoding-binding-element"></a>Bağlama öğesi kodlama ileti meta verileri desteği ekleme  
 Türetilen herhangi bir türü <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> hizmeti için oluşturulan WSDL belgesinde SOAP bağlama sürümünü güncelleştirmek için sorumludur. Bu uygulama tarafından yapılır `ExportEndpoint` yöntemi <xref:System.ServiceModel.Description.IWsdlExportExtension> arabirimi ve oluşturulan WSDL değiştirme. Bu örnekte `CustomTextMessageBindingElement` WSDL dışa aktarma mantığından kullanan `TextMessageEncodingBinidngElement`.  
  
 Bu örnek için elle yapılandırılmış istemci yapılandırmadır. İstemci yapılandırması oluşturulamıyor Svcutil.exe kullanamazsınız `CustomTextMessageBindingElement` davranışını açıklamak için bir ilke onaylama vermez. Genellikle uygulamalıdır <xref:System.ServiceModel.Description.IPolicyExportExtension> davranış veya bağlama öğesi tarafından uygulanan özelliği tanımlayan bir özel ilke onaylama dışarı aktarmak için bir özel bağlama öğesi üzerindeki arabirimi. Özel bağlama öğesi için bir ilke onaylama dışarı aktarma örneği için bkz: [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örnek.  
  
## <a name="message-encoding-binding-configuration-handler"></a>Kodlama bağlama yapılandırma işleyicisi iletisi  
 Önceki bölümde özel metin ileti Kodlayıcı programlı olarak kullanmayı gösterir. `CustomTextMessageEncodingBindingSection` Yapılandırma dosyasının içinde özel metin ileti kodlayıcı kullanımını belirtmenize olanak tanır yapılandırma işleyicisini uygular. `CustomTextMessageEncodingBindingSection` Sınıfı türer <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> sınıfı. `BindingElementType` Özelliği için bu bölümü oluşturmak için bağlama öğesi türünün yapılandırma sistemi bildirir.  
  
 Tarafından tanımlanan tüm ayarlar `CustomTextMessageBindingElement` özellikleri olarak sunulan `CustomTextMessageEncodingBindingSection`. <xref:System.Configuration.ConfigurationPropertyAttribute> Öznitelik ayarlanmamışsa, varsayılan değerleri ayarlama ve yapılandırma öğesi özniteliklerini eşleme için özellikleri de yardımcı olur. Yapılandırma değerleri yüklendikten ve türü özelliklerine uygulanan sonra <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> yöntemi çağrıldığında, hangi özellikler somut bir bağlama öğesi örneğine dönüştürür.  
  
 Bu yapılandırma işleyicisi hizmet veya istemci için App.config veya Web.config içinde aşağıdaki gösterimi eşler.  
  
```xml  
<customTextMessageEncoding encoding="utf-8" contentType="text/xml" messageVersion="Soap11Addressing1" />  
```  
  
 ISO 8859 1 kodlama örnek kullanır.  
  
 Aşağıdaki yapılandırma öğesini kullanarak kaydedilmelidir bu yapılandırma işleyicisi kullanmak için.  
  
```xml  
<extensions>  
    <bindingElementExtensions>  
        <add name="customTextMessageEncoding" type="   
Microsoft.ServiceModel.Samples.CustomTextMessageEncodingBindingSection,   
                  CustomTextMessageEncoder" />  
    </bindingElementExtensions>  
</extensions>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.
