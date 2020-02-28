---
title: XML Web Hizmetleri ile XML Serileştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XML Web services, XML serialization
- XML serialization, XML Web services
- SOAP, XML serialization
- asmx files
- serialization, SOAP
- XML serialization, attributes
- attributes [.NET Framework], XML serialization
- .asmx files
- encoded XML serialization
- literal XML serialization
- serialization, attributes
ms.assetid: a416192f-8102-458e-bc0a-0b8f3f784da9
ms.openlocfilehash: 2301f30a55e136b9a75a414d9325e4cf71c161da
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159539"
---
# <a name="xml-serialization-with-xml-web-services"></a>XML Web Hizmetleri ile XML Serileştirme
XML serileştirme, <xref:System.Xml.Serialization.XmlSerializer> sınıfı tarafından gerçekleştirilen XML Web Hizmetleri mimarisinde kullanılan temel taşıma mekanizmasıdır. Bir XML Web hizmeti tarafından oluşturulan XML 'yi denetlemek için, XML serileştirme ve XML Web hizmeti (. asmx) oluşturmak için kullanılan bir dosyanın sınıflarına, dönüş değerlerine, parametrelere ve alanlara [KODLANMıŞ SOAP serileştirmesini](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md) denetleyen öznitelikleri, her iki [özniteliğe](../../../docs/standard/serialization/attributes-that-control-xml-serialization.md) de uygulayabilirsiniz. XML Web hizmeti oluşturma hakkında daha fazla bilgi için bkz. [ASP.net using XML Web Services](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ba0z6a33(v=vs.100)).  
  
## <a name="literal-and-encoded-styles"></a>Değişmez değer ve kodlanmış stilleri  
 Bir XML Web hizmeti tarafından oluşturulan XML, [SOAP Ileti biçimlendirmesini özelleştirme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dkwy2d72(v=vs.100))bölümünde açıklandığı gibi, değişmez değer veya kodlanmış iki şekilde biçimlendirilebilir. Bu nedenle, XML serileştirmesini denetleyen iki öznitelik kümesi vardır. [XML serileştirmesini denetleyen özniteliklerde](../../../docs/standard/serialization/attributes-that-control-xml-serialization.md) listelenen öznitelikler, DEĞIŞMEZ stil XML 'i denetlemek için tasarlanmıştır. [KODLANMıŞ SOAP serileştirmesini denetleyen özniteliklerde](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md) listelenen öznitelikler kodlanmış stili. Bu öznitelikleri seçmeli olarak uygulayarak bir uygulamayı ya da her iki stili de döndürecek şekilde uyarlayabilirsiniz. Ayrıca, bu öznitelikler (uygun şekilde) değerleri ve parametreleri döndürmek için uygulanabilir.  
  
### <a name="example-of-using-both-styles"></a>Her iki stil kullanarak örneği  
 Bir XML Web hizmeti oluştururken, yöntemler üzerinde her iki öznitelik kümesini de kullanabilirsiniz. Aşağıdaki kod örneğinde adlı sınıfı `MyService` iki XML Web hizmeti yöntemlerini içeren `MyLiteralMethod` ve `MyEncodedMethod`. Her iki yöntem aynı işlevi gerçekleştirmek: örneği döndüren `Order` sınıfı. `Order` sınıfında, <xref:System.Xml.Serialization.XmlTypeAttribute> ve <xref:System.Xml.Serialization.SoapTypeAttribute> özniteliklerinin her ikisi de `OrderID` alanına uygulanır ve her iki özniteliğin da `ElementName` özelliği farklı değerlere ayarlanır.  
  
 Örneği çalıştırmak için bir dosya uzantısı olan bir .asmx kodu yapıştırın ve Internet Information Services (IIS) tarafından yönetilen bir sanal dizin dosyası yerleştirin. Internet Explorer gibi bir HTML tarayıcısından bilgisayar, sanal dizin ve dosya adını yazın.  
  
```vb  
<%@ WebService Language="VB" Class="MyService" %>  
Imports System  
Imports System.Web.Services  
Imports System.Web.Services.Protocols  
Imports System.Xml.Serialization  
Public Class Order  
    ' Both types of attributes can be applied. Depending on which type  
    ' the method used, either one will affect the call.  
    <SoapElement(ElementName:= "EncodedOrderID"), _  
    XmlElement(ElementName:= "LiteralOrderID")> _  
    public OrderID As String  
End Class  
  
Public Class MyService  
    <WebMethod, SoapDocumentMethod> _  
    public Function MyLiteralMethod() As Order
        Dim myOrder As Order = New Order()  
        return myOrder  
    End Function  
    <WebMethod, SoapRpcMethod> _  
    public Function MyEncodedMethod() As Order
        Dim myOrder As Order = New Order()  
        return myOrder  
    End Function  
End Class  
```  
  
```csharp  
<%@ WebService Language="C#" Class="MyService" %>  
using System;  
using System.Web.Services;  
using System.Web.Services.Protocols;  
using System.Xml.Serialization;  
public class Order {  
    // Both types of attributes can be applied. Depending on which type  
    // the method used, either one will affect the call.  
    [SoapElement(ElementName = "EncodedOrderID")]  
    [XmlElement(ElementName = "LiteralOrderID")]  
    public String OrderID;  
}  
public class MyService {  
    [WebMethod][SoapDocumentMethod]  
    public Order MyLiteralMethod(){  
        Order myOrder = new Order();  
        return myOrder;  
    }  
    [WebMethod][SoapRpcMethod]  
    public Order MyEncodedMethod(){  
        Order myOrder = new Order();  
        return myOrder;  
    }  
}  
```  
  
 Aşağıdaki kod örneği çağrıları `MyLiteralMethod`. Öğe adı "LiteralOrderID için" değiştirilir.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
    <soap:Body>  
        <MyLiteralMethodResponse xmlns="http://tempuri.org/">  
            <MyLiteralMethodResult>  
                <LiteralOrderID>string</LiteralOrderID>  
            </MyLiteralMethodResult>  
        </MyLiteralMethodResponse>  
    </soap:Body>  
</soap:Envelope>  
```  
  
 Aşağıdaki kod örneği çağrıları `MyEncodedMethod`. Öğe adı "EncodedOrderID" dir.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/" xmlns:tns="http://tempuri.org/" xmlns:types="http://tempuri.org/encodedTypes" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
    <soap:Body soap:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">  
        <tns:MyEncodedMethodResponse>  
            <MyEncodedMethodResult href="#id1" />  
        </tns:MyEncodedMethodResponse>  
        <types:Order id="id1" xsi:type="types:Order">  
            <EncodedOrderID xsi:type="xsd:string">string</EncodedOrderID>  
        </types:Order>  
    </soap:Body>  
</soap:Envelope>  
```  
  
### <a name="applying-attributes-to-return-values"></a>Değerleri döndürmek için öznitelikler uygulanıyor  
 Ayrıca, ad alanı, öğe adı vb. denetlemek için değerleri döndürmek için öznitelikler de uygulayabilirsiniz. Aşağıdaki kod örneği, `MyLiteralMethod` yönteminin dönüş değerine `XmlElementAttribute` özniteliğini uygular. Bunun yapılması ad alanını ve öğe adını denetlemenizi sağlar.  
  
```vb  
<WebMethod, SoapDocumentMethod> _  
public Function MyLiteralMethod() As _  
<XmlElement(Namespace:="http://www.cohowinery.com", _  
ElementName:= "BookOrder")> _  
Order
    Dim myOrder As Order = New Order()  
    return myOrder  
End Function  
```  
  
```csharp  
[return: XmlElement(Namespace = "http://www.cohowinery.com",  
ElementName = "BookOrder")]  
[WebMethod][SoapDocumentMethod]  
public Order MyLiteralMethod(){  
    Order myOrder = new Order();  
    return myOrder;  
}  
```  
  
 Çağrıldığında, aşağıdakine benzer XML kodu döndürür.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
    <soap:Body>  
        <MyLiteralMethodResponse xmlns="http://tempuri.org/">  
            <BookOrder xmlns="http://www.cohowinery.com">  
                <LiteralOrderID>string</LiteralOrderID>  
            </BookOrder>  
        </MyLiteralMethodResponse>  
    </soap:Body>  
</soap:Envelope>  
```  
  
### <a name="attributes-applied-to-parameters"></a>Parametrelere uygulanan öznitelikler  
 Ayrıca, ad alanı, öğe adı ve benzeri belirtmek için parametrelere öznitelikler de uygulayabilirsiniz. Aşağıdaki kod örneği `MyLiteralMethodResponse` yöntemine bir parametre ekler ve `XmlAttributeAttribute` özniteliğini parametresine uygular. Öğe adı ve ad alanı her iki parameTRe için kümesidir.  
  
```vb  
<WebMethod, SoapDocumentMethod> _  
public Function MyLiteralMethod(<XmlElement _  
("MyOrderID", Namespace:="http://www.microsoft.com")>ID As String) As _  
<XmlElement(Namespace:="http://www.cohowinery.com", _  
ElementName:= "BookOrder")> _  
Order
    Dim myOrder As Order = New Order()  
    myOrder.OrderID = ID  
    return myOrder  
End Function  
```  
  
```csharp  
[return: XmlElement(Namespace = "http://www.cohowinery.com",  
ElementName = "BookOrder")]  
[WebMethod][SoapDocumentMethod]  
public Order MyLiteralMethod([XmlElement("MyOrderID",
Namespace="http://www.microsoft.com")] string ID){  
    Order myOrder = new Order();  
    myOrder.OrderID = ID;  
    return myOrder;  
}
```  
  
 SOAP isteği aşağıdakine benzer.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
    <soap:Body>  
        <MyLiteralMethod xmlns="http://tempuri.org/">  
            <MyOrderID xmlns="http://www.microsoft.com">string</MyOrderID>  
        </MyLiteralMethod>  
    </soap:Body>  
</soap:Envelope>  
```  
  
### <a name="applying-attributes-to-classes"></a>Öznitelikleri sınıflara uygulama  
 Sınıflarla bağıntılı öğelerin ad alanını denetetmeniz gerekiyorsa, uygun şekilde `XmlTypeAttribute`, `XmlRootAttribute`ve `SoapTypeAttribute`uygulayabilirsiniz. Aşağıdaki kod örneği için üç uygular `Order` sınıfı.  
  
```vb  
<XmlType("BigBookService"), _  
SoapType("SoapBookService"), _  
XmlRoot("BookOrderForm")> _  
Public Class Order  
    ' Both types of attributes can be applied. Depending on which  
    ' the method used, either one will affect the call.  
    <SoapElement(ElementName:= "EncodedOrderID"), _  
    XmlElement(ElementName:= "LiteralOrderID")> _  
    public OrderID As String  
End Class  
```  
  
```csharp  
[XmlType("BigBooksService", Namespace = "http://www.cpandl.com")]  
[SoapType("SoapBookService")]  
[XmlRoot("BookOrderForm")]  
public class Order {  
    // Both types of attributes can be applied. Depending on which  
    // the method used, either one will affect the call.  
    [SoapElement(ElementName = "EncodedOrderID")]  
    [XmlElement(ElementName = "LiteralOrderID")]  
    public String OrderID;  
}  
```  
  
 Uygulama sonuçlarını `XmlTypeAttribute` ve `SoapTypeAttribute` olduğunda, hizmet açıklamasını inceleyin aşağıdaki kod örneğinde gösterildiği gibi görülebilir.  
  
```xml
<s:element name="BookOrderForm" type="s0:BigBookService" />
<s:complexType name="BigBookService">
  <s:sequence>
    <s:element minOccurs="0" maxOccurs="1" name="LiteralOrderID" type="s:string" />
  </s:sequence>

  <s:schema targetNamespace="http://tempuri.org/encodedTypes">
    <s:complexType name="SoapBookService">
      <s:sequence>
        <s:element minOccurs="1" maxOccurs="1" name="EncodedOrderID" type="s:string" />
      </s:sequence>
    </s:complexType>
  </s:schema>
</s:complexType>
```
  
 Etkisini `XmlRootAttribute` Ayrıca HTTP GET ve HTTP POST sonuçları gibi görülebilir.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<BookOrderForm xmlns="http://tempuri.org/">  
    <LiteralOrderID>string</LiteralOrderID>  
</BookOrderForm>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML ve SOAP Serileştirme](xml-and-soap-serialization.md)
- [Kodlanmış SOAP Serileştirmesini Denetleyen Öznitelikler](attributes-that-control-encoded-soap-serialization.md)
- [Nasıl yapılır: SOAP Kodlu XML Akışı Olarak Nesneyi Serileştirme](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)
- [Nasıl yapılır: Kodlanmış SOAP XML Serileştirmesini Geçersiz Kılma](how-to-override-encoded-soap-xml-serialization.md)
- [XML Serileştirmeye Giriş](introducing-xml-serialization.md)
- [Nasıl yapılır: Nesne Serileştirme](how-to-serialize-an-object.md)
- [Nasıl yapılır: Nesneyi Seri Durumdan Çıkarma](how-to-deserialize-an-object.md)
