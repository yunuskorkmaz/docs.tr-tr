---
title: 'Özel İleti Kodlayıcı: Özel Metin Kodlayıcı'
ms.date: 03/30/2017
ms.assetid: 68ff5c74-3d33-4b44-bcae-e1d2f5dea0de
ms.openlocfilehash: aeb1690d7ead9116bd9c4afe3c64d65d8f51ad50
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43732228"
---
# <a name="custom-message-encoder-custom-text-encoder"></a>Özel İleti Kodlayıcı: Özel Metin Kodlayıcı
Bu örnek, Windows Communication Foundation (WCF) kullanarak bir özel metin ileti Kodlayıcı uygulamak nasıl gösterir.  
  
> [!WARNING]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Text`  
  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> WCF yalnızca UTF-8, UTF-16 ve büyük Endean Unicode kodlamaları destekler. Bu örnekte metin özel ileti Kodlayıcı, tüm platform tarafından desteklenen karakter kodlaması birlikte çalışabilirlik için gerekli olabilecek destekler. Örnek, bir istemci konsol programı (.exe), Internet Information Services (IIS) ve bir metin iletisi Kodlayıcı kitaplığı (.dll) tarafından barındırılan bir hizmet kitaplığı (.dll) oluşur. Hizmet istek-yanıt iletişim deseni tanımlayan bir sözleşme uygular. Anlaşma tarafından tanımlanan `ICalculator` matematik işlemlerinden sunan arabirimi (ekleme, çıkarma, çarpma ve bölme). İstemci verilen matematik işlemi ve hizmet yanıt sonucu zaman uyumlu istekleri yapar. Hem istemci hem de hizmet kullanan `CustomTextMessageEncoder` varsayılan yerine <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.  
  
 Özel bir kodlayıcı uygulama, ileti Kodlayıcı Fabrika, ileti Kodlayıcı, bir ileti bağlama öğesi ve yapılandırma işleyicisi kodlama oluşur ve aşağıda gösterilmiştir:  
  
-   Özel bir kodlayıcı ve Kodlayıcı fabrikası oluşturma.  
  
-   Bir bağlama öğesi için özel bir kodlayıcı oluşturuluyor.  
  
-   Özel bağlama yapılandırma özel bağlama öğeleri tümleştirmek için kullanma.  
  
-   Özel bağlama öğesinin dosya yapılandırması izin vermek için özel yapılandırma işleyicisi geliştirme.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Yükleme [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aşağıdaki komutu kullanarak 4.0.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="message-encoder-factory-and-the-message-encoder"></a>İleti Kodlayıcı fabrikası ve ileti kodlayıcı  
 Zaman <xref:System.ServiceModel.ServiceHost> veya istemci kanal açıldığında, tasarım zamanı bileşeni `CustomTextMessageBindingElement` oluşturur `CustomTextMessageEncoderFactory`. Üreteç oluşturur `CustomTextMessageEncoder`. İleti Kodlayıcı hem akış hem arabellekli modu çalışır. Kullandığı <xref:System.Xml.XmlReader> ve <xref:System.Xml.XmlWriter> sırasıyla iletileri yazma ve okuma için. En iyi duruma getirilmiş XML okuyucular ve yalnızca UTF-8, UTF-16 ve BIG-Endean Unicode destekleyen yazıcılar WCF aksine bu okuyucular ve yazıcılar tüm desteklenen platform kodlamayı destekler.  
  
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
  
 Aşağıdaki kod örneği, ileti Kodlayıcı fabrikası oluşturma gösterilmektedir.  
  
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
 Bağlama öğeleri WCF çalışma zamanı yığını yapılandırmasını sağlar. Özel ileti Kodlayıcı WCF kullanmak için bir bağlama öğesi gereklidir, çalışma zamanı yığını uygun düzeyde uygun ayarlarla ileti Kodlayıcı fabrikası oluşturur.  
  
 `CustomTextMessageBindingElement` Türetildiği <xref:System.ServiceModel.Channels.BindingElement> devralan ve temel sınıf <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> sınıfı. Bu, diğer WCF bileşenleri bu bağlama öğesi bir ileti kodlama bağlama öğesi olarak tanımasını sağlar. Uygulamasını <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> uygun ayarlarla eşleşen ileti Kodlayıcı üretecin bir örneğini döndürür.  
  
 `CustomTextMessageBindingElement` Ayarlarını sunan `MessageVersion`, `ContentType`, ve `Encoding` özellikleri aracılığıyla. Kodlayıcı Soap11Addressing hem Soap12Addressing1 sürümlerini destekler. Soap11Addressing1 varsayılandır. Varsayılan değer olan `ContentType` "metin/XML". `Encoding` Özellik istenen karakter kodlama değeri ayarlamanıza olanak tanır. Örnek istemci ve hizmet kullanan ISO-8859-1 (Latin1) karakter kodlaması, tarafından desteklenmeyen <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> WCF.  
  
 Aşağıdaki kod, program aracılığıyla metin özel ileti Kodlayıcı kullanarak bağlama nasıl oluşturulacağını gösterir.  
  
```  
ICollection<BindingElement> bindingElements = new List<BindingElement>();  
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();  
CustomTextMessageBindingElement textBindingElement = new CustomTextMessageBindingElement();  
bindingElements.Add(textBindingElement);  
bindingElements.Add(httpBindingElement);  
CustomBinding binding = new CustomBinding(bindingElements);  
```  
  
## <a name="adding-metadata-support-to-the-message-encoding-binding-element"></a>İleti kodlama bağlama öğesi meta veri desteği ekleme  
 Öğesinden türetilen herhangi bir türü <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> SOAP bağlama hizmeti için oluşturulan WSDL belgesinde sürümünü güncelleştirmek için sorumludur. Bu uygulama tarafından gerçekleştirilir `ExportEndpoint` metodunda <xref:System.ServiceModel.Description.IWsdlExportExtension> arabirimi ve sonra oluşturulan WSDL değiştirme. Bu örnekte `CustomTextMessageBindingElement` WSDL dışarı aktarma mantığından kullanan `TextMessageEncodingBinidngElement`.  
  
 Bu örnek için elle yapılandırılmış istemci yapılandırmadır. İstemci yapılandırması nedeniyle üretmek için Svcutil.exe kullanamazsınız `CustomTextMessageBindingElement` davranışını açıklamak için bir ilke onaylama vermez. Genellikle uygulamalıdır <xref:System.ServiceModel.Description.IPolicyExportExtension> arabirimi davranış veya bağlama öğesi tarafından uygulanan özellik açıklayan bir özel ilke onaylama dışarı aktarmak için bir özel bağlama öğesinin. Özel bağlama öğesi için bir ilke onaylama dışarı aktarmak nasıl bir örnek için bkz [taşıma: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) örnek.  
  
## <a name="message-encoding-binding-configuration-handler"></a>İleti kodlama bağlama yapılandırma işleyicisi  
 Önceki bölümde, özel metin ileti Kodlayıcı programsal olarak nasıl kullanılacağını gösterir. `CustomTextMessageEncodingBindingSection` Bir yapılandırma dosyası içinde bir özel metin ileti Kodlayıcı kullanılmasını belirtmenizi sağlar bir yapılandırma işleyicisi uygular. `CustomTextMessageEncodingBindingSection` Sınıf türetilir <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> sınıfı. `BindingElementType` Özelliği bağlama öğesi bu bölüm için oluşturulacak tür yapılandırma sistemi bildirir.  
  
 Tüm tarafından tanımlanan ayarlara `CustomTextMessageBindingElement` özellikleri olarak gösterilen `CustomTextMessageEncodingBindingSection`. <xref:System.Configuration.ConfigurationPropertyAttribute> Öznitelik ayarlanmamışsa, varsayılan değerleri ayarlama ve yapılandırma öğesi özniteliklerini eşleme özellikleri için de yardımcı olur. Yapılandırma değerleri yüklenir ve türünün özelliklerine uygulanan sonra <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> yöntemi çağrıldığında, hangi özellikler bir bağlama öğesi somut bir örneğine dönüştürür.  
  
 Bu yapılandırma işleyicisi, hizmet veya istemci için App.config veya Web.config aşağıdaki gösterimi eşler.  
  
```xml  
<customTextMessageEncoding encoding="utf-8" contentType="text/xml" messageVersion="Soap11Addressing1" />  
```  
  
 Örnek, ISO-8859-1 kodlamayı kullanır.  
  
 Bu yapılandırma işleyicisi aşağıdaki yapılandırma öğesini kullanarak kaydedilmelidir kullanılacak.  
  
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
