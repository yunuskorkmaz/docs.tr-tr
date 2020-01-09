---
title: Kullanım ve stil özelliklerini ayarlama örnekleri
ms.date: 03/30/2017
ms.assetid: c09a0600-116f-41cf-900a-1b7e4ea4e300
ms.openlocfilehash: 36111aa05680fb8b369cde6b42d22c9c3b8474ad
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345127"
---
# <a name="setting-the-use-and-style-properties"></a>Kullanım ve Stil Özelliklerini Ayarlama

Bu örnek, <xref:System.ServiceModel.XmlSerializerFormatAttribute> ve <xref:System.ServiceModel.DataContractFormatAttribute>kullanım ve stil özelliklerinin nasıl kullanılacağını gösterir. Bu özellikler, iletilerin nasıl biçimlendirildiğini etkiler. Varsayılan olarak, ileti gövdesi <xref:System.ServiceModel.OperationFormatStyle.Document>olarak ayarlanmış stille biçimlendirilir. Bu ayarlar, hizmet sözleşmesi düzeyinde ya da işlem sözleşmesi düzeyinde belirlenebilir.

> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.

<xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> Style özelliği, hizmetin WSDL meta verilerinin nasıl biçimlendirildiğini belirler. Olası değerler <xref:System.ServiceModel.OperationFormatStyle.Document>ve <xref:System.ServiceModel.OperationFormatStyle.Rpc>. RPC, bir işlem için değiştirilen iletilerin WSDL gösteriminin, bir uzak yordam çağrımı gibi parametreler içerdiği anlamına gelir. Aşağıda bir örnek verilmiştir.

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="n1" type="xsd:double"/>
  <wsdl:part name="n2" type="xsd:double"/>
</wsdl:message>
```

Stili <xref:System.ServiceModel.OperationFormatStyle.Document> olarak ayarlamak, WSDL gösteriminin, aşağıdaki örnekte gösterildiği gibi bir işlem için alışverişi yapılan belgeyi temsil eden tek bir öğe içerdiği anlamına gelir.

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="parameters" element="tns:Add"/>
</wsdl:message>
```

<xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> özelliği iletinin biçimini belirler. Olası değerler <xref:System.ServiceModel.OperationFormatUse.Literal> ve <xref:System.ServiceModel.OperationFormatUse.Encoded>; Varsayılan değer <xref:System.ServiceModel.OperationFormatUse.Literal>. Değişmez değer, aşağıdaki belge/değişmez örnekte gösterildiği gibi, WSDL 'deki şemanın değişmez bir örneği olduğu anlamına gelir.

```xml
<Add xmlns="http://Microsoft.ServiceModel.Samples">
  <n1>100</n1>
  <n2>15.99</n2>
</Add>
```

Kodlanan, WSDL 'deki şemaların SOAP 1,1 Bölüm 5 ' te bulunan kurallara göre kodlanan soyut belirtimlerdir. Aşağıda bir RPC/kodlanmış örnek verilmiştir.

```xml
<q1:Add xmlns:q1="http://Microsoft.ServiceModel.Samples">
  <n1 xsi:type="xsd:double" xmlns="">100</n1>
  <n2 xsi:type="xsd:double" xmlns="">15.99</n2>
</q1:Add>
```

WS-ı temel profil 1,0 <xref:System.ServiceModel.OperationFormatUse.Encoded> kullanımını yasaklar ve yalnızca eski hizmetler için gerektiğinde kullanmanız gerekir. `Encoded` ileti biçimi yalnızca XmlSerializer kullanılırken kullanılabilir.

Gönderilen ve alınan iletileri görmenizi sağlamak için bu örnek, [izleme ve mesaj günlüğüne](tracing-and-message-logging.md)göre yapılır. Hizmet yapılandırması ve kaynak kodu, izleme ve ileti günlüğe kaydetme özelliğini etkinleştirmek ve kullanmak üzere değiştirilmiştir. Ayrıca, <xref:System.ServiceModel.WSHttpBinding> güvenlik olmadan yapılandırılmıştır, bu nedenle günlüğe kaydedilen iletiler şifresiz biçimde görüntülenebilir. Elde edilen izleme günlükleri (System. ServiceModel. e2e ve Message. log), [hizmet Izleme Görüntüleyicisi Aracı (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md)kullanılarak görüntülenmelidir. İzlemeler C:\LOGS klasöründe oluşturulacak şekilde yapılandırılır. Örneği çalıştırmadan önce klasörü oluşturun. Izleme Görüntüleyici aracında ileti içeriğini görüntülemek için, aracın hem sol hem de sağ bölmesindeki **iletileri** seçin.

Aşağıdaki kod, <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> özelliği <xref:System.ServiceModel.OperationFormatUse> olarak ayarlanan hizmet sözleşmesini ve ileti gövdesinin biçim varsayılan <xref:System.ServiceModel.OperationFormatStyle> <xref:System.ServiceModel.OperationFormatStyle.Document>olarak değiştirildiğini gösterir.

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"),
XmlSerializerFormat(Style = OperationFormatStyle.Rpc, 
                                 Use = OperationFormatUse.Encoded)]
public interface IUseAndStyleCalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    [OperationContract]
    double Subtract(double n1, double n2);
    [OperationContract]
    double Multiply(double n1, double n2);
    [OperationContract]
    double Divide(double n1, double n2);
}
```

Farklı <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> ve <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> ayarları arasındaki farkı görmek için, hizmette değiştirin, istemciyi yeniden oluşturun, örneği çalıştırın ve c:\logs\Message.exe dosyasını hizmet Izleme Görüntüleyicisi aracıyla inceleyin. Ayrıca, `http://localhost/ServiceModelSamples/service.svc?wsdl`görüntüleyerek meta veriler üzerindeki etkiyi gözlemleyin. Hizmetler için meta veriler genellikle birden çok sayfaya ayrılmıştır. Ana WSDL sayfası WSDL bağlamalarını içerir, ancak ileti tanımlarını gözlemlemek için `http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0` görüntüleyin.

## <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için

1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.

2. İletileri günlüğe kaydetmek için bir C:\LOGS dizini oluşturun. Bu dizin için Kullanıcı ağ hizmetine yazma izinleri verin.

3. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.

4. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.

> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.
> 
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\UseAndStyle`
