---
title: 'Özel Ileti Kodlayıcısı: özel metin Kodlayıcısı-WCF'
ms.date: 03/30/2017
ms.assetid: 68ff5c74-3d33-4b44-bcae-e1d2f5dea0de
ms.openlocfilehash: 3d421aa40488deac487418b5ecc83c5dd420fdf4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74281677"
---
# <a name="custom-message-encoder-custom-text-encoder"></a>Özel İleti Kodlayıcı: Özel Metin Kodlayıcı

Bu örnek, Windows Communication Foundation (WCF) kullanarak özel metin iletisi Kodlayıcısı 'nın nasıl uygulanacağını gösterir.

> [!WARNING]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
> 
> `<InstallDrive>:\WF_WCF_Samples`
> 
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://go.microsoft.com/fwlink/?LinkId=150780) gidin. Bu örnek, aşağıdaki dizinde bulunur.
> 
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Text`

WCF <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> yalnızca UTF-8, UTF-16 ve Big-endian Unicode kodlamalarını destekler. Bu örnekteki özel metin iletisi Kodlayıcısı, birlikte çalışabilirlik için gerekebilecek tüm platform tarafından desteklenen karakter kodlamalarını destekler. Örnek, bir istemci konsol programı (. exe), Internet Information Services (IIS) tarafından barındırılan bir hizmet kitaplığı (. dll) ve bir SMS mesajı Kodlayıcı kitaplığı (. dll) içerir. Hizmet, istek-yanıt iletişim modelini tanımlayan bir sözleşme uygular. Sözleşme, matematik işlemlerini (ekleme, çıkarma, çarpma ve bölme) sunan `ICalculator` arabirimi tarafından tanımlanır. İstemci belirli bir matematik işlemine zaman uyumlu istekler yapar ve hizmet sonuçla yanıt verir. İstemci ve hizmet, varsayılan <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>yerine `CustomTextMessageEncoder` kullanır.

Özel kodlayıcı uygulamasının bir ileti Kodlayıcısı fabrikası, bir ileti Kodlayıcısı, ileti kodlama bağlama öğesi ve yapılandırma işleyicisi oluşur ve şunları gösterir:

- Özel kodlayıcı ve kodlayıcı fabrikası oluşturma.

- Özel bir kodlayıcı için bağlama öğesi oluşturma.

- Özel bağlama öğelerini tümleştirmek için özel bağlama yapılandırması kullanma.

- Özel bir bağlama öğesinin dosya yapılandırmasına izin vermek için özel bir yapılandırma işleyicisi geliştirme.

## <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. Aşağıdaki komutu kullanarak ASP.NET 4,0 ' ü yükler.

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

3. Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümündeki yönergeleri izleyin.

4. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.

## <a name="message-encoder-factory-and-the-message-encoder"></a>İleti Kodlayıcısı fabrikası ve Ileti Kodlayıcısı

<xref:System.ServiceModel.ServiceHost> veya istemci kanalı açıldığında, tasarım zamanı bileşeni `CustomTextMessageBindingElement` `CustomTextMessageEncoderFactory`oluşturur. Fabrika `CustomTextMessageEncoder`oluşturur. İleti Kodlayıcısı hem akış modunda hem de arabelleğe alınmış modda çalışır. Sırasıyla iletileri okumak ve yazmak için <xref:System.Xml.XmlReader> ve <xref:System.Xml.XmlWriter> kullanır. Yalnızca UTF-8, UTF-16 ve Big-endian Unicode 'u destekleyen, iyileştirilmiş XML okuyucuları ve WCF yazarlarının aksine, bu okuyucular ve yazarlar tüm platform tarafından desteklenen kodlamayı destekler.

Aşağıdaki kod örneğinde CustomTextMessageEncoder gösterilmektedir.

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

Aşağıdaki kod örneği, ileti Kodlayıcısı fabrikasının nasıl oluşturulacağını göstermektedir.

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

Bağlama öğeleri, WCF çalışma zamanı yığınının yapılandırmasına izin verir. Özel ileti Kodlayıcısı 'nı bir WCF uygulamasında kullanmak için, çalışma zamanı yığınında uygun düzeyde uygun ayarlarla ileti Kodlayıcısı fabrikasını oluşturan bir Binding öğesi gereklidir.

`CustomTextMessageBindingElement`, <xref:System.ServiceModel.Channels.BindingElement> temel sınıfından türetilir ve <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> sınıfından devralır. Bu, diğer WCF bileşenlerinin bu bağlama öğesini bir ileti kodlama bağlama öğesi olarak tanımasını sağlar. <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> uygulanması, uygun ayarlarla eşleşen ileti Kodlayıcısı fabrikasının bir örneğini döndürür.

`CustomTextMessageBindingElement`, `MessageVersion`, `ContentType`ve `Encoding` özellikleriyle ilgili ayarları kullanıma sunar. Kodlayıcı hem Soap11Addressing hem de Soap12Addressing1 sürümlerini destekler. Varsayılan değer Soap11Addressing1 ' dir. `ContentType` varsayılan değeri "text/xml" dir. `Encoding` özelliği, istenen karakter kodlamasının değerini ayarlamanıza olanak sağlar. Örnek istemci ve hizmet, WCF <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> tarafından desteklenmeyen ISO-8859-1 (Latin1) karakter kodlamasını kullanır.

Aşağıdaki kod, özel metin iletisi Kodlayıcısı kullanılarak bağlama programlı bir şekilde nasıl oluşturulacağını gösterir.

```csharp
ICollection<BindingElement> bindingElements = new List<BindingElement>();
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();
CustomTextMessageBindingElement textBindingElement = new CustomTextMessageBindingElement();
bindingElements.Add(textBindingElement);
bindingElements.Add(httpBindingElement);
CustomBinding binding = new CustomBinding(bindingElements);
```

## <a name="adding-metadata-support-to-the-message-encoding-binding-element"></a>Ileti kodlama bağlama öğesine meta veri desteği ekleniyor

<xref:System.ServiceModel.Channels.MessageEncodingBindingElement> türetilen herhangi bir tür, hizmet için oluşturulan WSDL belgesinde SOAP bağlamanın sürümünün güncelleştirilmesinden sorumludur. Bu, <xref:System.ServiceModel.Description.IWsdlExportExtension> arabirimindeki `ExportEndpoint` yöntemi uygulayarak ve sonra oluşturulan WSDL 'nin değiştirilerek yapılır. Bu örnekte, `CustomTextMessageBindingElement` `TextMessageEncodingBindingElement`WSDL dışarı aktarma mantığını kullanır.

Bu örnek için, istemci yapılandırması el ile yapılandırılmıştır. `CustomTextMessageBindingElement`, davranışını tanımlayacak bir ilke onayını dışarı aktarmadığından, istemci yapılandırmasını oluşturmak için Svcutil. exe ' yi kullanamazsınız. Bağlama öğesi tarafından uygulanan davranışı veya yeteneği açıklayan özel bir ilke onayını dışarı aktarmak için genellikle <xref:System.ServiceModel.Description.IPolicyExportExtension> arabirimini özel bir bağlama öğesine uygulamalısınız. Özel bağlama öğesi için bir ilke onayını dışarı aktarmanın bir örneği için bkz. [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) Sample.

## <a name="message-encoding-binding-configuration-handler"></a>İleti kodlama bağlama yapılandırma Işleyicisi
Önceki bölümde özel metin iletisi kodlayıcının programlı olarak nasıl kullanılacağı gösterilmektedir. `CustomTextMessageEncodingBindingSection`, bir yapılandırma dosyası içinde özel bir metin iletisi Kodlayıcısı kullanımını belirtmenize olanak tanıyan bir yapılandırma işleyicisi uygular. `CustomTextMessageEncodingBindingSection` sınıfı <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> sınıfından türetilir. `BindingElementType` özelliği, bu bölüm için oluşturulacak bağlama öğesi türünün yapılandırma sistemine bildirir.

`CustomTextMessageBindingElement` tarafından tanımlanan tüm ayarlar `CustomTextMessageEncodingBindingSection`özellikler olarak gösterilir. <xref:System.Configuration.ConfigurationPropertyAttribute>, yapılandırma öğesi özniteliklerinin özelliklerle eşlenmesiyle ve özniteliği ayarlanmamışsa varsayılan değerleri ayarlamada yardımcı olur. Yapılandırma değerleri yüklendikten ve bu türün özelliklerine uygulandıktan sonra, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> metodu çağrılır ve bu, özellikleri bir bağlama öğesinin somut örneğine dönüştürür.

Bu yapılandırma işleyicisi, hizmet veya istemcinin App. config veya Web. config dosyasında aşağıdaki gösterimiyle eşleşir.

```xml
<customTextMessageEncoding encoding="utf-8" contentType="text/xml" messageVersion="Soap11Addressing1" />
```

Örnek ISO-8859-1 kodlamasını kullanır.

Bu yapılandırma işleyicisini kullanmak için, aşağıdaki yapılandırma öğesi kullanılarak kaydedilmesi gerekir.

```xml
<extensions>
    <bindingElementExtensions>
        <add name="customTextMessageEncoding" type=" 
Microsoft.ServiceModel.Samples.CustomTextMessageEncodingBindingSection, 
                  CustomTextMessageEncoder" />
    </bindingElementExtensions>
</extensions>
```
