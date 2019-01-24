---
title: Kullanım ve Stil Özelliklerini Ayarlama
ms.date: 03/30/2017
ms.assetid: c09a0600-116f-41cf-900a-1b7e4ea4e300
ms.openlocfilehash: cd6f9af034f2f36c4daf808492713fcd616e3a9c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662159"
---
# <a name="setting-the-use-and-style-properties"></a>Kullanım ve Stil Özelliklerini Ayarlama
Bu örnek üzerinde kullanım ve stil özelliklerini kullanmayı gösteren <xref:System.ServiceModel.XmlSerializerFormatAttribute> ve <xref:System.ServiceModel.DataContractFormatAttribute>. Bu özellikler, iletileri nasıl biçimlendirileceğini etkiler. Varsayılan olarak, ileti gövdesi ile stil kümesi biçimlendirilmiş <xref:System.ServiceModel.OperationFormatStyle.Document>. Bu ayarlar, ya da hizmet sözleşme düzeyi veya işlem anlaşması düzeyinde belirtilebilir.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
 <xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> Style özelliği, WSDL hizmet meta verileri nasıl biçimlendirildiğini belirler. Olası değerler <xref:System.ServiceModel.OperationFormatStyle.Document>, ve <xref:System.ServiceModel.OperationFormatStyle.Rpc>. RPC uzak yordam çağrısı değilmiş gibi iletiler için bir işlem Değişimi WSDL gösterimini parametreleri içerdiğini belirtir. Bir örnek verilmiştir.  
  
```xml  
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">  
  <wsdl:part name="n1" type="xsd:double"/>  
  <wsdl:part name="n2" type="xsd:double"/>  
</wsdl:message>  
```  
  
 Style ayarını <xref:System.ServiceModel.OperationFormatStyle.Document> WSDL temsili bir işlem için aşağıdaki örnekte gösterildiği gibi değiştirilir belgeyi temsil eden tek bir öğe içerdiğini belirtir.  
  
```xml  
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">  
  <wsdl:part name="parameters" element="tns:Add"/>  
</wsdl:message>  
```  
  
 <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> Özelliği, ileti biçimi belirler. Olası değerler <xref:System.ServiceModel.OperationFormatUse.Literal> ve <xref:System.ServiceModel.OperationFormatUse.Encoded>; varsayılan değer <xref:System.ServiceModel.OperationFormatUse.Literal>. Değişmez değer anlamına gelir ileti aşağıdaki belge / sabit değer gösterildiği gibi WSDL şemada sabit bir örneğini olduğunu örnek.  
  
```xml  
<Add xmlns="http://Microsoft.ServiceModel.Samples">  
  <n1>100</n1>  
  <n2>15.99</n2>  
</Add>  
```  
  
 SOAP 1.1 5 bölümüne bulunan kurallara göre kodlanmış soyut belirtimleri WSDL şemalarda olan kodlanmış. RPC/kodlanmış örneği verilmiştir.  
  
```xml  
<q1:Add xmlns:q1="http://Microsoft.ServiceModel.Samples">  
  <n1 xsi:type="xsd:double" xmlns="">100</n1>  
  <n2 xsi:type="xsd:double" xmlns="">15.99</n2>  
</q1:Add>  
```  
  
 WS-ı temel Profil 1.0 kullanımını engeller <xref:System.ServiceModel.OperationFormatUse.Encoded> ve yalnızca bu eski Hizmetleri tarafından gerekli olduğunda kullanmalısınız. `Encoded` İleti biçimi, yalnızca kullanılabilir XmlSerializer kullanırken.  
  
 Gönderilen ve alınan iletileri görmek, izin vermek için bu örnek dayanır [izleme ve ileti günlüğe kaydetme](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md). İleti izleme ve kaydetme yazılımınız olması ve etkinleştirmek için hizmet yapılandırması ve kaynak kodu değiştirildi. Ayrıca, <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> güvenlik olmadan, günlüğe kaydedilen iletilere şifresiz bir biçimde görüntülenebilir şekilde yapılandırıldı. Sonuçta elde edilen izleme günlükleri (System.ServiceModel.e2e ve Message.log) kullanarak görülmelidir [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). İzlemeleri C:\LOGS klasöründe oluşturulması için yapılandırılır. Bu örneği çalıştırmadan önce klasörü oluşturun. İzleme Görüntüleyicisi aracı ileti içeriği görüntülemek için seçin **iletileri** sol ve sağ bölmeleri aracı.  
  
 Aşağıdaki kod ile hizmet sözleşmesini gösterir <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> özelliğini <xref:System.ServiceModel.OperationFormatUse> ve ileti gövdesi biçiminin varsayılandan <xref:System.ServiceModel.OperationFormatStyle> için <xref:System.ServiceModel.OperationFormatStyle.Document>.  
  
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
  
 Farklı arasındaki farkı görmek için <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> ve <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> ayarları, bunları hizmette değiştirmek, istemci yeniden, örneği çalıştırmak ve hizmet izleme Görüntüleyicisi aracı ile c:\logs\message.logs dosyasını inceleyin. Ayrıca görüntüleyerek meta veriler üzerindeki etkisini gözlemlemek `http://localhost/ServiceModelSamples/service.svc?wsdl`. Meta Veri Hizmetleri için genellikle birden çok sayfalarına ayrılmıştır. WSDL bağlamaları ana wsdl sayfa içeriyor, ancak görüntüleme `http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0` ileti tanımları gözlemleyin.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Günlük iletileri için bir C:\LOGS dizin oluşturun. Ağ hizmeti yazma izinleri bu dizin için kullanıcıya sağlayın.  
  
3.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\UseAndStyle`  
  
## <a name="see-also"></a>Ayrıca bkz.
