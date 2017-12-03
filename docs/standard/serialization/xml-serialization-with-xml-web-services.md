---
title: "XML Web Hizmetleri ile XML serileştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0f174ef3ada619e20d375035bee82b0ed9bbc145
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="xml-serialization-with-xml-web-services"></a>XML Web Hizmetleri ile XML serileştirme
XML serileştirme olduğu tarafından gerçekleştirilen XML Web Hizmetleri mimarisi kullanılan temelindeki iletim mekanizması <xref:System.Xml.Serialization.XmlSerializer> sınıfı. XML Web hizmeti tarafından oluşturulan XML denetlemek için ikisi de listelenen öznitelikleri uygulayabilirsiniz [öznitelikleri, Denetim XML serileştirme](../../../docs/standard/serialization/attributes-that-control-xml-serialization.md) ve [öznitelikleri, Denetim kodlanmış SOAP seri hale getirme](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md) için sınıfları, dönüş değerleri, parametreler ve XML Web Hizmetleri (.asmx) oluşturmak için kullanılan bir dosya alanları. XML Web hizmeti oluşturma hakkında daha fazla bilgi için bkz: [yapı XML Web Hizmetleri kullanarak ASP.NET](http://msdn.microsoft.com/en-us/01dfc27c-c68e-4910-a0aa-5e4c2a766b0c).  
  
## <a name="literal-and-encoded-styles"></a>Değişmez değer ve kodlanmış stilleri  
 XML Web hizmeti tarafından oluşturulan XML ya da sabit değer iki yoldan birini biçimlendirilmiş ya da açıklandığı gibi kodlanmış [özelleştirme SOAP iletilerine](http://msdn.microsoft.com/en-us/1d777288-c0d9-4e6a-b638-f010da031952). Bu nedenle iki XML serileştirme denetim öznitelikleri kümesi vardır. Listelenen öznitelikleri [öznitelikleri, Denetim XML serileştirme](../../../docs/standard/serialization/attributes-that-control-xml-serialization.md) değişmez değer stili XML denetlemek için tasarlanmıştır. Listelenen öznitelikleri [öznitelikleri, Denetim kodlanmış SOAP seri hale getirme](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md) kodlanmış stili denetim. Seçime bağlı olarak bu öznitelikler uygulayarak, her ikisi de stilleri döndürmek için bir uygulama uyarlayabilirsiniz. Ayrıca, bu öznitelikler (uygun şekilde) değerleri ve parametreleri döndürmek için uygulanabilir.  
  
### <a name="example-of-using-both-styles"></a>Her iki stil kullanarak örneği  
 XML Web Hizmetleri oluştururken, iki özniteliklerin yöntemlerini kullanabilirsiniz. Aşağıdaki kod örneğinde adlı sınıfı `MyService` iki XML Web hizmeti yöntemlerini içeren `MyLiteralMethod` ve `MyEncodedMethod`. Her iki yöntem aynı işlevi gerçekleştirmek: örneği döndüren `Order` sınıfı. İçinde `Order` sınıfı, <xref:System.Xml.Serialization.XmlTypeAttribute> ve <xref:System.Xml.Serialization.SoapTypeAttribute> öznitelikler için her ikisini de uygulanır `OrderID` alan ve her iki öznitelik sahip kendi `ElementName` özelliği farklı bir değere ayarlanmış.  
  
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
public class Order{  
    // Both types of attributes can be applied. Depending on which type  
    // the method used, either one will affect the call.  
    [SoapElement(ElementName = "EncodedOrderID")]  
    [XmlElement(ElementName = "LiteralOrderID")]  
    public String OrderID;  
}  
public class MyService{  
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
  
### <a name="applying-attributes-to-return-values"></a>Dönüş değerleri öznitelikleri uygulama  
 Ad alanı, öğe adı ve benzeri denetlemek için değer döndürmek için öznitelikler de uygulayabilirsiniz. Aşağıdaki kod örneğinde geçerlidir `XmlElementAttribute` özniteliği dönüş değerini `MyLiteralMethod` yöntemi. Bunun yapılması, ad alanı ve öğe adı denetlemenizi sağlar.  
  
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
  
### <a name="attributes-applied-to-parameters"></a>Parametreleri uygulanan öznitelikleri  
 Ad alanı, öğe adı ve benzeri belirtmek üzere parametreler için öznitelikler de uygulayabilirsiniz. Aşağıdaki kod örneği için bir parametre ekler `MyLiteralMethodResponse` yöntemi, geçerli ve `XmlAttributeAttribute` özniteliği parametresi. Öğe adı ve ad alanı her iki parameTRe için kümesidir.  
  
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
  
### <a name="applying-attributes-to-classes"></a>Sınıflara öznitelikleri uygulama  
 Ad alanı sınıflarına ilişkilendirmek öğelerinin denetlemeye ihtiyacınız varsa, uygulamadan `XmlTypeAttribute`, `XmlRootAttribute`, ve `SoapTypeAttribute`uygun şekilde. Aşağıdaki kod örneği için üç uygular `Order` sınıfı.  
  
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
public class Order{  
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
- <s:complexType name="BigBookService">  
- <s:sequence>  
    <s:element minOccurs="0" maxOccurs="1" name="LiteralOrderID" type="s:string" />   
    </s:sequence>  
  
- <s:schema targetNamespace="http://tempuri.org/encodedTypes">  
- <s:complexType name="SoapBookService">  
- <s:sequence>  
    <s:element minOccurs="1" maxOccurs="1" name="EncodedOrderID" type="s:string" />   
    </s:sequence>  
    </s:complexType>  
    </s:schema>  
```  
  
 Etkisini `XmlRootAttribute` Ayrıca HTTP GET ve HTTP POST sonuçları gibi görülebilir.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<BookOrderForm xmlns="http://tempuri.org/">  
    <LiteralOrderID>string</LiteralOrderID>  
</BookOrderForm>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML ve SOAP seri hale getirme](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 [Kodlanmış SOAP serileştirme denetim öznitelikleri](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)  
 [Nasıl yapılır: bir SOAP kodlanmış XML akışı olarak bir nesneyi serileştirme](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)  
 [Nasıl yapılır: Kodlanmış SOAP XML serileştirmesi için geçersiz kılma](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)  
 [Giriş XML serileştirme](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [Nasıl yapılır: bir nesneyi serileştirme](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [Nasıl yapılır: bir nesne seri durumdan](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
