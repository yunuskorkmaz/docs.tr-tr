---
title: 'Özel İleti Kodlayıcısı: Özel Metin Kodlayıcısı'
description: WCF kullanarak özel bir metin ileti Kodlayıcısı uygulamak için bu örneği kullanın. Bu kodlayıcı, birlikte çalışabilirlik için platformun desteklediği tüm karakter kodlamalarını destekler.
ms.date: 03/30/2017
ms.assetid: 68ff5c74-3d33-4b44-bcae-e1d2f5dea0de
ms.openlocfilehash: 88ddc79e6cc1df654aea851cedb0e60c6fbcd017
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246278"
---
# <a name="custom-message-encoder-custom-text-encoder"></a>Özel İleti Kodlayıcısı: Özel Metin Kodlayıcısı

Bu örnek, Windows Communication Foundation (WCF) kullanarak özel metin iletisi Kodlayıcısı 'nın nasıl uygulanacağını gösterir.

> [!WARNING]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Text`

<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>WCF 'de yalnızca UTF-8, UTF-16 ve Big-endian Unicode kodlamaları desteklenir. Bu örnekteki özel metin iletisi Kodlayıcısı, birlikte çalışabilirlik için gerekebilecek tüm platform tarafından desteklenen karakter kodlamalarını destekler. Örnek, bir istemci konsol programı (. exe), Internet Information Services (IIS) tarafından barındırılan bir hizmet kitaplığı (. dll) ve bir SMS mesajı Kodlayıcı kitaplığı (. dll) içerir. Hizmet, istek-yanıt iletişim modelini tanımlayan bir sözleşme uygular. Sözleşme, `ICalculator` matematik işlemlerini (ekleme, çıkarma, çarpma ve bölme) sunan arabirim tarafından tanımlanır. İstemci belirli bir matematik işlemine zaman uyumlu istekler yapar ve hizmet sonuçla yanıt verir. Hem istemci hem de hizmet `CustomTextMessageEncoder` varsayılan yerine ' nı kullanır <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> .

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

2. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

3. Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümündeki yönergeleri izleyin.

4. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.

## <a name="message-encoder-factory-and-the-message-encoder"></a>İleti Kodlayıcısı fabrikası ve Ileti Kodlayıcısı

<xref:System.ServiceModel.ServiceHost>Veya istemci kanalı açıldığında tasarım zamanı bileşeni tarafından `CustomTextMessageBindingElement` oluşturulur `CustomTextMessageEncoderFactory` . Fabrika, öğesini oluşturur `CustomTextMessageEncoder` . İleti Kodlayıcısı hem akış modunda hem de arabelleğe alınmış modda çalışır. <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter> İletileri sırasıyla okumak ve yazmak için ve kullanır. Yalnızca UTF-8, UTF-16 ve Big-endian Unicode 'u destekleyen, iyileştirilmiş XML okuyucuları ve WCF yazarlarının aksine, bu okuyucular ve yazarlar tüm platform tarafından desteklenen kodlamayı destekler.

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

, `CustomTextMessageBindingElement` <xref:System.ServiceModel.Channels.BindingElement> Temel sınıftan türetilir ve <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> sınıfından devralır. Bu, diğer WCF bileşenlerinin bu bağlama öğesini bir ileti kodlama bağlama öğesi olarak tanımasını sağlar. Uygulamasının uygulanması, <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> uygun ayarlarla eşleşen ileti Kodlayıcısı fabrikasının bir örneğini döndürür.

,, `CustomTextMessageBindingElement` Ve özellikleri için ayarları sunar `MessageVersion` `ContentType` `Encoding` . Kodlayıcı hem Soap11Addressing hem de Soap12Addressing1 sürümlerini destekler. Varsayılan değer Soap11Addressing1 ' dir. Varsayılan değeri `ContentType` "text/xml" dir. `Encoding`Özelliği, istenen karakter kodlamasının değerini ayarlamanıza olanak sağlar. Örnek istemci ve hizmet, WCF tarafından desteklenmeyen ISO-8859-1 (Latin1) karakter kodlamasını kullanır <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> .

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

Öğesinden türetilen herhangi bir tür, <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> hizmet için oluşturulan wsdl BELGESINDE SOAP bağlamanın sürümünü güncelleştirmekten sorumludur. Bu, `ExportEndpoint` yöntemi arabirim üzerinde uygulayarak <xref:System.ServiceModel.Description.IWsdlExportExtension> ve sonra oluşturulan wsdl 'nin değiştirilerek yapılır. Bu örnekte, ' `CustomTextMessageBindingElement` den WSDL dışarı aktarma mantığını kullanır `TextMessageEncodingBindingElement` .

Bu örnek için, istemci yapılandırması el ile yapılandırılmıştır. `CustomTextMessageBindingElement`Davranışını tanımlayacak bir ilke onayını dışarı aktarmadığından, istemci yapılandırmasını oluşturmak için Svcutil.exe kullanamazsınız. <xref:System.ServiceModel.Description.IPolicyExportExtension>Bağlama öğesi tarafından uygulanan davranışı veya özelliği açıklayan özel bir ilke onayını dışarı aktarmak için genellikle bir özel bağlama öğesi üzerinde arabirimini uygulamalısınız. Özel bağlama öğesi için bir ilke onayını dışarı aktarmanın bir örneği için bkz. [Transport: UDP](transport-udp.md) Sample.

## <a name="message-encoding-binding-configuration-handler"></a>İleti kodlama bağlama yapılandırma Işleyicisi
Önceki bölümde özel metin iletisi kodlayıcının programlı olarak nasıl kullanılacağı gösterilmektedir. , `CustomTextMessageEncodingBindingSection` Bir yapılandırma dosyası içinde özel bir metin iletisi Kodlayıcısı kullanımını belirtmenize olanak tanıyan bir yapılandırma işleyicisi uygular. `CustomTextMessageEncodingBindingSection`Sınıf sınıfından türetilir <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> . `BindingElementType`Özelliği, bu bölüm için oluşturulacak bağlama öğesi türünün yapılandırma sistemine bildirir.

Tarafından tanımlanan tüm ayarlar `CustomTextMessageBindingElement` , içindeki özellikler olarak gösterilir `CustomTextMessageEncodingBindingSection` . <xref:System.Configuration.ConfigurationPropertyAttribute>Yapılandırma öğesi özniteliklerini özelliklerine eşleme ve özniteliği ayarlanmamışsa varsayılan değerleri ayarlama konusunda yardımcı olur. Yapılandırma değerleri yüklenip, türün özelliklerine uygulandıktan sonra, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> özelliği bir bağlama öğesinin somut örneğine dönüştüren yöntemi çağırılır.

Bu yapılandırma işleyicisi, hizmet veya istemci için App.config ya da Web.config aşağıdaki gösterimiyle eşlenir.

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
