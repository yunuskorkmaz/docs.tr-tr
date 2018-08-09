---
title: Kullanım ve Stil Özelliklerini Ayarlama
ms.date: 03/30/2017
ms.assetid: c09a0600-116f-41cf-900a-1b7e4ea4e300
ms.openlocfilehash: 74d5baca77fd1af6260def762094b3ce01816179
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33506822"
---
# <a name="setting-the-use-and-style-properties"></a>Kullanım ve Stil Özelliklerini Ayarlama
Bu örnek kullanım ve stil özelliklerini kullanmak gösterilmiştir <xref:System.ServiceModel.XmlSerializerFormatAttribute> ve <xref:System.ServiceModel.DataContractFormatAttribute>. Bu özellikler, iletileri nasıl biçimlendirileceğini etkiler. Varsayılan olarak, ileti gövdesi kümesine stiliyle biçimlendirilmiş <xref:System.ServiceModel.OperationFormatStyle.Document>. Bu ayarlar, hizmet sözleşmesi düzeyi veya işlemi sözleşme düzeyinde ya da belirtilebilir.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
 <xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> Stil özelliği belirler WSDL meta veri hizmeti için nasıl biçimlendirilir. Olası değerler şunlardır: <xref:System.ServiceModel.OperationFormatStyle.Document>, ve <xref:System.ServiceModel.OperationFormatStyle.Rpc>. RPC için bir işlem değiştirilen iletilerin WSDL gösterimini uzaktan yordam çağrısı değilmiş gibi parametreleri içeren anlamına gelir. Bir örnek verilmiştir.  
  
```xml  
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">  
  <wsdl:part name="n1" type="xsd:double"/>  
  <wsdl:part name="n2" type="xsd:double"/>  
</wsdl:message>  
```  
  
 Stil ayarını <xref:System.ServiceModel.OperationFormatStyle.Document> WSDL temsili bir işlem için aşağıdaki örnekte gösterildiği gibi değiştirilir belgeyi temsil tek bir öğesi içerir anlamına gelir.  
  
```xml  
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">  
  <wsdl:part name="parameters" element="tns:Add"/>  
</wsdl:message>  
```  
  
 <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> Özelliği, ileti biçimi belirler. Olası değerler şunlardır: <xref:System.ServiceModel.OperationFormatUse.Literal> ve <xref:System.ServiceModel.OperationFormatUse.Encoded>; varsayılan değer <xref:System.ServiceModel.OperationFormatUse.Literal>. Değişmez değeri anlamına gelir ileti aşağıdaki belgede / değişmez değer gösterildiği gibi WSDL şemada değişmez değer örneği olduğunu örnek.  
  
```xml  
<Add xmlns="http://Microsoft.ServiceModel.Samples">  
  <n1>100</n1>  
  <n2>15.99</n2>  
</Add>  
```  
  
 SOAP 1.1 Bölüm 5 bulunan kurallarına göre kodlanmış soyut belirtimleri WSDL şemalarda olan kodlanmış. RPC/kodlanmış örneği verilmiştir.  
  
```xml  
<q1:Add xmlns:q1="http://Microsoft.ServiceModel.Samples">  
  <n1 xsi:type="xsd:double" xmlns="">100</n1>  
  <n2 xsi:type="xsd:double" xmlns="">15.99</n2>  
</q1:Add>  
```  
  
 WS-ı temel Profil 1.0 kullanımını yasaklar <xref:System.ServiceModel.OperationFormatUse.Encoded> ve yalnızca bunu eski Hizmetleri tarafından gerekli olduğunda kullanmalısınız. `Encoded` İleti biçimi kullanılabilir yalnızca XmlSerializer kullanırken.  
  
 Gönderilen ve alınan iletileri görmenize olanak sağlamak için bu örnek dayanır [izleme ve ileti günlüğe kaydetme](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md). Hizmet yapılandırması ve kaynak kodu, etkinleştirme ve ileti izleme ve kaydetme kullanma değiştirildi. Ayrıca, <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> güvenlik olmadan, günlüğe kaydedilen iletilere şifresiz bir biçimde görüntülenebilir şekilde yapılandırıldı. Sonuçta elde edilen izleme günlükleri (System.ServiceModel.e2e ve Message.log) kullanarak görülmelidir [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). İzlemeler C:\LOGS klasöründe oluşturulması için yapılandırılır. Örneği çalıştırmadan önce klasörü oluşturun. İzleme Görüntüleyicisi aracı ileti içeriğini görüntülemek için seçin **iletileri** sol ve sağ bölmeleri aracı.  
  
 Aşağıdaki kod ile hizmet sözleşmesini gösterir <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> özelliğini <xref:System.ServiceModel.OperationFormatUse> ve ileti gövdesinin biçimi değiştirdi varsayılandan <xref:System.ServiceModel.OperationFormatStyle> için <xref:System.ServiceModel.OperationFormatStyle.Document>.  
  
```  
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
  
 Farklı arasındaki farkı görmek için <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> ve <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> ayarları hizmetinde değiştirmek, istemci yeniden, örneği çalıştırmak ve hizmet izleme Görüntüleyicisi aracı ile c:\logs\message.logs dosyasını inceleyin. Ayrıca meta veriler üzerindeki etkisini görüntüleyerek gözlemlemek http://localhost/ServiceModelSamples/service.svc?wsdl. Hizmetler için meta verileri genellikle birden çok sayfaya bozuk. Ana wsdl sayfa WSDL bağlamalar içeriyor, ancak görüntülemek http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0 ileti tanımları izlemek için.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Günlük iletileri için C:\LOGS dizin oluşturun. Ağ hizmeti yazma izinleri bu dizin için kullanıcı verin.  
  
3.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\UseAndStyle`  
  
## <a name="see-also"></a>Ayrıca Bkz.
