---
title: 'Özel İleti Kodlayıcı: Özel Metin Kodlayıcı'
ms.date: 03/30/2017
ms.assetid: 68ff5c74-3d33-4b44-bcae-e1d2f5dea0de
ms.openlocfilehash: 88aeeb4f1d09795b768441d2a572d959f27e0226
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145117"
---
# <a name="custom-message-encoder-custom-text-encoder"></a>Özel İleti Kodlayıcı: Özel Metin Kodlayıcı

Bu örnek, Windows Communication Foundation (WCF) kullanarak özel bir metin iletisi kodlayıcısının nasıl uygulanacağını gösterir.

> [!WARNING]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Text`

<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> WCF sadece UTF-8, UTF-16 ve big-endian Unicode kodlamaları destekler. Bu örnekteki özel metin iletisi kodlayıcısı, birlikte çalışabilirlik için gerekli olabilecek tüm platform destekli karakter kodlamalarını destekler. Örnek, Internet Information Services (IIS) tarafından barındırılan bir istemci konsol programı (.exe), bir hizmet kitaplığı (.dll) ve bir kısa mesaj kodlayıcısı kitaplığından (.dll) oluşur. Hizmet, istek-yanıt iletişim modelini tanımlayan bir sözleşme uygular. Sözleşme, matematik işlemlerini `ICalculator` (Ekle, Çıkar, Çarp ve Böl) ortaya çıkaran arabirim tarafından tanımlanır. İstemci belirli bir matematik işlemi için eşzamanlı isteklerde bulunmaz ve sonuç ile hizmet yanıtları. Hem istemci hem `CustomTextMessageEncoder` de hizmet <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>varsayılan yerine kullanır.

Özel kodlayıcı uygulaması bir ileti kodlayıcısı fabrikası, ileti kodlayıcısı, bağlayıcı öğeyi kodlayan bir ileti öğesi ve yapılandırma işleyicisi oluşur ve aşağıdakileri gösterir:

- Özel bir kodlayıcı ve kodlayıcı fabrikası oluşturma.

- Özel bir kodlayıcı için bağlayıcı bir öğe oluşturma.

- Özel bağlama öğelerini tümleştirmek için özel bağlama yapılandırmasını kullanma.

- Özel bağlama öğesinin dosya yapılandırmasına izin vermek için özel bir yapılandırma işleyicisi geliştirme.

## <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için

1. Aşağıdaki komutu kullanarak 4.0 ASP.NET yükleyin.

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.

3. Çözümü oluşturmak için, Windows [Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.

4. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.

## <a name="message-encoder-factory-and-the-message-encoder"></a>İleti Kodlayıcı Fabrikası ve İleti Kodlayıcısı

<xref:System.ServiceModel.ServiceHost> Veya istemci kanalı açıldığında, tasarım süresi `CustomTextMessageBindingElement` bileşeni `CustomTextMessageEncoderFactory`. Fabrika oluşturur `CustomTextMessageEncoder`. İleti kodlayıcısı hem akış modunda hem de arabelleğe alınan modda çalışır. İletileri <xref:System.Xml.XmlReader> sırasıyla okumak ve yazmak <xref:System.Xml.XmlWriter> için kullanır. Sadece UTF-8, UTF-16 ve big-endian Unicode'u destekleyen WCF'nin optimize edilmiş XML okuyucuları ve yazarlarının aksine, bu okuyucular ve yazarlar tüm platform destekli kodlamayı destekler.

Aşağıdaki kod örneği CustomTextMessageEncoder gösterir.

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

Aşağıdaki kod örneği, ileti kodlayıcısı fabrikasının nasıl inşa edilebildiğini gösterir.

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

## <a name="message-encoding-binding-element"></a>İleti Kodlama Bağlama Öğesi

Bağlama öğeleri WCF çalışma zamanı yığınının yapılandırmasını sağlar. Bir WCF uygulamasında özel ileti kodlayıcısını kullanmak için, çalışma zamanı yığınında uygun düzeyde uygun ayarlarla ileti kodlayıcı fabrikasını oluşturan bağlayıcı bir öğe gereklidir.

Taban `CustomTextMessageBindingElement` sınıftan <xref:System.ServiceModel.Channels.BindingElement> türetilmiştir ve <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> sınıftan devralır. Bu, diğer WCF bileşenlerinin bu bağlayıcı öğeyi ileti kodlama bağlayıcı öğesi olarak tanımasına olanak tanır. Uygun ayarlarla eşleşen ileti kodlayıcı fabrikasının bir örneğini <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> döndürür.

" `CustomTextMessageBindingElement` ve özellikler `MessageVersion` `ContentType` `Encoding` aracılığıyla ayarlar ortaya çıkarır. Kodlayıcı hem Soap11Addressing hem de Soap12Addressing1 sürümlerini destekler. Varsayılan sabun11Addressing1'dir. Varsayılan değeri `ContentType` "text/xml"dir. Özellik, `Encoding` istenen karakter kodlama değerini ayarlamanızı sağlar. Örnek istemci ve hizmet, WCF tarafından desteklenmeyen ISO-8859-1 (Latin1) karakter kodlamasını <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> kullanır.

Aşağıdaki kod, özel metin iletisi kodlayıcısını kullanarak bağlamanın nasıl programlanabilir bir şekilde oluşturulacak şekilde oluşturulabildiğini gösterir.

```csharp
ICollection<BindingElement> bindingElements = new List<BindingElement>();
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();
CustomTextMessageBindingElement textBindingElement = new CustomTextMessageBindingElement();
bindingElements.Add(textBindingElement);
bindingElements.Add(httpBindingElement);
CustomBinding binding = new CustomBinding(bindingElements);
```

## <a name="adding-metadata-support-to-the-message-encoding-binding-element"></a>İleti Kodlama Bağlama Öğesine Meta veri desteği ekleme

Bu tür, <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> hizmet için oluşturulan WSDL belgesinde SOAP bağlama sürümünü güncelleştirmekiçin sorumludur. Bu, `ExportEndpoint` <xref:System.ServiceModel.Description.IWsdlExportExtension> yöntemin arabirimde uygulanması ve ardından oluşturulan WSDL değiştirerek yapılır. Bu örnekte, `CustomTextMessageBindingElement` WSDL dışa aktarma `TextMessageEncodingBindingElement`mantığını kullanır.

Bu örnek için istemci yapılandırması el yapılandırılır. Svcutil.exe'yi istemci yapılandırmasını oluşturmak `CustomTextMessageBindingElement` için kullanamazsınız, çünkü davranışını açıklamak için bir ilke iddiası dışa aktarılamıyor. Bağlama öğesi tarafından <xref:System.ServiceModel.Description.IPolicyExportExtension> uygulanan davranışı veya yeteneği açıklayan özel bir ilke iddiası dışa aktarmak için genellikle özel bir bağlama öğesi üzerinde arabirimi uygulamanız gerekir. Özel bir bağlama öğesi için ilke iddiasının nasıl dışa aktarılacak lığına bir örnek için, [Taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örneğine bakın.

## <a name="message-encoding-binding-configuration-handler"></a>İleti Kodlama Bağlama Yapılandırma Işleyicisi
Önceki bölümde, özel metin iletisi kodlayıcısının programlı olarak nasıl kullanılacağı gösterilmektedir. Yapılandırma `CustomTextMessageEncodingBindingSection` dosyasıiçinde özel bir metin iletisi kodlayıcısının kullanımını belirtmenize olanak tanıyan bir yapılandırma işleyicisi uygular. Sınıf `CustomTextMessageEncodingBindingSection` sınıftan <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> türetilmiştir. Özellik, `BindingElementType` bu bölüm için oluşturmak üzere bağlama öğesi türünü yapılandırma sistemi bildirir.

Tarafından `CustomTextMessageBindingElement` tanımlanan tüm `CustomTextMessageEncodingBindingSection`ayarlar. Yapılandırma <xref:System.Configuration.ConfigurationPropertyAttribute> öğesi özellikleri öznitelikleri eşleme ve öznitelik ayarlanmaz sayar yardımcıları. Yapılandırmadaki değerler yüklendikten ve türün özelliklerine uygulandıktan <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> sonra, özellikleri bağlayıcı öğenin somut bir örneğine dönüştüren yöntem emeği denir.

Bu yapılandırma işleyicisi, hizmet veya istemci için App.config veya Web.config'deki aşağıdaki gösterimle eşler.

```xml
<customTextMessageEncoding encoding="utf-8" contentType="text/xml" messageVersion="Soap11Addressing1" />
```

Örnek iso-8859-1 kodlama kullanır.

Bu yapılandırma işleyicisini kullanmak için aşağıdaki yapılandırma öğesi kullanılarak kaydedilmesi gerekir.

```xml
<extensions>
    <bindingElementExtensions>
        <add name="customTextMessageEncoding" type="
Microsoft.ServiceModel.Samples.CustomTextMessageEncodingBindingSection,
                  CustomTextMessageEncoder" />
    </bindingElementExtensions>
</extensions>
```
