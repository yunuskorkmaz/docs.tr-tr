---
title: Kullanım ve Stil özellikleri örneklerini ayarlama
ms.date: 03/30/2017
ms.assetid: c09a0600-116f-41cf-900a-1b7e4ea4e300
ms.openlocfilehash: f400c0bc08588afa951ae33f221663b47b37602c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144038"
---
# <a name="setting-the-use-and-style-properties"></a>Kullanım ve Stil Özelliklerini Ayarlama

Bu örnek, Kullanım ve Stil özelliklerinin <xref:System.ServiceModel.XmlSerializerFormatAttribute> nasıl <xref:System.ServiceModel.DataContractFormatAttribute>kullanılacağını gösterir. Bu özellikler iletilerin biçimlendirme şeklini etkiler. Varsayılan olarak, ileti gövdesi stil olarak ayarlanmış <xref:System.ServiceModel.OperationFormatStyle.Document>olarak biçimlendirilir. Bu ayarlar hizmet sözleşmesi düzeyinde veya işlem sözleşmesi düzeyinde belirtilebilir.

> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.

Stil <xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> özelliği, hizmetiçin WSDL meta verilerinin nasıl biçimlendirilir olduğunu belirler. Olası değerler <xref:System.ServiceModel.OperationFormatStyle.Document>ve <xref:System.ServiceModel.OperationFormatStyle.Rpc>. RPC, bir işlem için değiştirilen iletilerin WSDL gösteriminin uzaktan yordam çağrısı gibi parametreler içerdiği anlamına gelir. Bir örnek verilmiştir.

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="n1" type="xsd:double"/>
  <wsdl:part name="n2" type="xsd:double"/>
</wsdl:message>
```

Stili, <xref:System.ServiceModel.OperationFormatStyle.Document> WSDL gösteriminin, aşağıdaki örnekte gösterildiği gibi bir işlemiçin değiştirilen belgeyi temsil eden tek bir öğe içerdiği anlamına gelir.

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="parameters" element="tns:Add"/>
</wsdl:message>
```

Özellik <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> iletinin biçimini belirler. Olası değerler <xref:System.ServiceModel.OperationFormatUse.Literal> <xref:System.ServiceModel.OperationFormatUse.Encoded>ve; varsayılan değer. <xref:System.ServiceModel.OperationFormatUse.Literal> Literal, iletinin aşağıdaki Belge/Literal örnekte gösterildiği gibi WSDL'deki şemanın gerçek bir örneği olduğu anlamına gelir.

```xml
<Add xmlns="http://Microsoft.ServiceModel.Samples">
  <n1>100</n1>
  <n2>15.99</n2>
</Add>
```

Kodlanmış, WSDL'deki şemaların SOAP 1.1 bölüm 5'te bulunan kurallara göre kodlanmış soyut özellikler olduğu anlamına gelir. Aşağıda bir RPC / Kodlanmış örnektir.

```xml
<q1:Add xmlns:q1="http://Microsoft.ServiceModel.Samples">
  <n1 xsi:type="xsd:double" xmlns="">100</n1>
  <n2 xsi:type="xsd:double" xmlns="">15.99</n2>
</q1:Add>
```

WS-I Temel Profil 1.0 kullanımını <xref:System.ServiceModel.OperationFormatUse.Encoded> yasaklar ve yalnızca eski hizmetler tarafından gerekli olduğunda kullanmanız gerekir. İleti `Encoded` biçimi yalnızca XmlSerializer kullanırken kullanılabilir.

Gönderilen ve alınan iletileri görmenizi sağlamak için, bu örnek [İzleme ve İleti Günlüğe kaydetmeyi](tracing-and-message-logging.md)temel alar. Hizmet yapılandırması ve kaynak kodu, izleme ve ileti günlüğe kaydetmeyi etkinleştirmek ve kullanmak için değiştirildi. Buna ek <xref:System.ServiceModel.WSHttpBinding> olarak, güvenlik olmadan yapılandırıldı, böylece günlüğe kaydedilen iletiler şifrelenmemiş bir biçimde görüntülenebilir. Ortaya çıkan izleme günlükleri (System.ServiceModel.e2e ve Message.log) [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md)kullanılarak görüntülenmelidir. İzlemeler C:\LOGS klasöründe oluşturulacak şekilde yapılandırılır. Örneği çalıştırmadan önce klasörü oluşturun. Görüntüleyici'yi İzle aracında ileti içeriğini görüntülemek için, aracın hem sol hem de sağ bölmelerinde **İletiler'i** seçin.

Aşağıdaki kod, <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> ayarlanan özellikle hizmet <xref:System.ServiceModel.OperationFormatUse> sözleşmesini gösterir ve ileti gövdesinin <xref:System.ServiceModel.OperationFormatStyle> <xref:System.ServiceModel.OperationFormatStyle.Document>biçimi varsayılandan .

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

Farklı <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> ve <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> ayarlar arasındaki farkı görmek için, bunları hizmette değiştirin, istemciyi yeniden oluşturun, örneği çalıştırın ve Servis İzleyici aracıyla c:\logs\message.logs dosyasını inceleyin. Ayrıca görüntüleyerek `http://localhost/ServiceModelSamples/service.svc?wsdl`meta veriler üzerindeki etkisini gözlemleyin. Hizmetlerin meta verileri genellikle birden çok sayfaya ayrılır. Ana wsdl sayfası WSDL bağlamalarını içerir, ancak ileti tanımlarını gözlemlemek için görüntüleyin. `http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0`

## <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için

1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.

2. İletileri günlüğe kaydetmek için C:\LOGS dizini oluşturun. Kullanıcı Ağ Hizmeti'ne bu dizini yazma izinleri verin.

3. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](building-the-samples.md)yönergeleri izleyin.

4. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](running-the-samples.md)yönergeleri izleyin.

> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\UseAndStyle`
