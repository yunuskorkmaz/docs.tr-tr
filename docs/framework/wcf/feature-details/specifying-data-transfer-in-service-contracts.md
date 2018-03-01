---
title: "Hizmet Sözleşmelerinde Veri Aktarımını Belirtme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], data transfer
ms.assetid: 7c5a26c8-89c9-4bcb-a4bc-7131e6d01f0c
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c650a59402099e1fe71a0292dd0ccfc409d3448d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="specifying-data-transfer-in-service-contracts"></a>Hizmet Sözleşmelerinde Veri Aktarımını Belirtme
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] , Bir Mesajlaşma altyapısı düşünülebilir. Hizmet işlemleri iletilerini işlemek ve iletileri göndermek. İletileri işlemi sözleşmeleri kullanma açıklanmaktadır. Örneğin, aşağıdaki sözleşme göz önünde bulundurun.  
  
```csharp  
[ServiceContract]  
public interface IAirfareQuoteService  
{  
    [OperationContract]  
    float GetAirfare(string fromCity, string toCity);  
}  
```  
  
```vb  
<ServiceContract()>  
Public Interface IAirfareQuoteService  
  
    <OperationContract()>  
    Function GetAirfare(fromCity As String, toCity As String) As Double  
End Interface  
```  
  
 Burada, `GetAirfare` işlemi hakkında bilgi içeren bir ileti kabul `fromCity` ve `toCity`ve ardından bir sayı içeren bir ileti döndürür.  
  
 Bu konuda, bir işlem sözleşmesi iletileri açıklayabilirsiniz çeşitli yolları açıklanmaktadır.  
  
## <a name="describing-messages-by-using-parameters"></a>Parametreleri kullanarak açıklayan iletiler  
 Bir ileti açıklamak için en basit yolu, bir parametre listesi ve dönüş değeri kullanmaktır. Önceki örnekte `fromCity` ve `toCity` dizesi parametreleri, istek iletisi açıklamak için kullanıldı ve float dönüş değeri yanıt iletisi açıklamak için kullanıldı. Dönüş değeri tek başına bir yanıt iletisi açıklamak için yeterli değilse, out Parametreleri kullanılabilir. Örneğin, aşağıdaki işlemi sahip `fromCity` ve `toCity` istek iletisi ve bir sayı bir para birimi yanıt iletisi ile birlikte:  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, out string currency);  
```  
  
```vb  
<OperationContract()>  
    Function GetAirfare(fromCity As String, toCity As String) As Double  
```  
  
 Ayrıca, istek ve yanıt iletisi parametresi parçası haline getirmek için başvuru parametreleri kullanabilirsiniz. Parametreler (XML biçimine dönüştürülen) seri hale getirilebilir türler olmalıdır. Varsayılan olarak, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] adında bir bileşen <xref:System.Runtime.Serialization.DataContractSerializer> bu dönüştürme gerçekleştirmek için sınıf. En basit türler (gibi `int`, `string`, `float`, ve `DateTime`.) desteklenir. Kullanıcı tanımlı türler, normalde bir veri sözleşmesi olması gerekir. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Veri sözleşmelerini kullanma](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
```csharp
public interface IAirfareQuoteService  
{  
    [OperationContract]  
    float GetAirfare(Itinerary itinerary, DateTime date);  
  
    [DataContract]  
    public class Itinerary  
    {  
        [DataMember]  
        public string fromCity;  
        [DataMember]  
        public string toCity;  
   }  
}  
```  
  
```vb  
Public Interface IAirfareQuoteService  
    <OperationContract()>  
    GetAirfare(itinerary as Itinerary, date as DateTime) as Double  
  
    <DataContract()>  
    Class Itinerary  
  
        <DataMember()>  
        Public fromCity As String  
        <DataMember()>  
        Public toCity As String  
    End Class  
End Interface  
```  
  
 Bazen, `DataContractSerializer` türlerinizi serileştirmek yeterli değil. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]bir alternatif serileştirme motoruna destekleyen <xref:System.Xml.Serialization.XmlSerializer>, hangi parametreleri seri hale getirmek için de kullanabilirsiniz. <xref:System.Xml.Serialization.XmlSerializer> Sonuç XML öznitelikleri gibi kullanma hakkında daha fazla denetime kullanmanıza olanak sağlayan `XmlAttributeAttribute`. Kullanmaya geçmek <xref:System.Xml.Serialization.XmlSerializer> belirli bir işlem veya tüm hizmet için uygulama <xref:System.ServiceModel.XmlSerializerFormatAttribute> özniteliği bir işlem veya bir hizmet. Örneğin:  
  
```csharp  
[ServiceContract]  
public interface IAirfareQuoteService  
{  
    [OperationContract]  
    [XmlSerializerFormat]  
    float GetAirfare(Itinerary itinerary, DateTime date);  
}  
public class Itinerary  
{  
    public string fromCity;  
    public string toCity;  
    [XmlAttribute]  
    public bool isFirstClass;  
}  
```  
  
```vb  
<ServiceContract()>  
Public Interface IAirfareQuoteService  
    <OperationContract()>  
    <XmlSerializerFormat>  
    GetAirfare(itinerary as Itinerary, date as DateTime) as Double  
  
End Interface  
  
Class Itinerary  
  
    Public fromCity As String  
    Public toCity As String  
    <XmlSerializerFormat()>  
    Public isFirstClass As Boolean  
End Class  
```  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][XmlSerializer sınıfını kullanma](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md). Bu el ile geçiş unutmayın <xref:System.Xml.Serialization.XmlSerializer> gösterildiği şekilde bu konudaki olarak ayrıntılı yapmak için belirli nedenleri yoksa burada önerilmez.  
  
 .NET parametre adları sözleşme adlarından yalıtmak için kullanabileceğiniz <xref:System.ServiceModel.MessageParameterAttribute> özniteliği ve kullanmak `Name` sözleşme adı ayarlamak için özellik. Örneğin, bu konudaki ilk örnek için aşağıdaki işlemi sözleşme eşdeğerdir.  
  
```csharp  
[OperationContract]  
public float GetAirfare(  
    [MessageParameter(Name="fromCity")] string originCity,  
    [MessageParameter(Name="toCity")] string destinationCity);  
```  
  
```vb  
<OperationContract()>  
  Function GetAirfare(<MessageParameter(Name := "fromCity")> fromCity As String, <MessageParameter(Name := "toCity")> toCity As String) As Double  
```  
  
## <a name="describing-empty-messages"></a>Açıklayan boş iletileri  
 Hiçbir giriş veya başvuru parametreleri sağlayarak bir boş istek iletisi açıklanabilir. Örneğin C# ' de:  
  
 `[OperationContract]`  
  
 `public int GetCurrentTemperature();`  
  
 Örneğin VB içinde:  
  
 `<OperationContract()>`  
  
 `Function GetCurrentTemperature() as Integer`  
  
 Bir boş yanıt iletisi sağlayarak açıklanabilir bir `void` dönüş türü ve hiçbir çıktı veya başvuru parametreleri. Örnek için:  
  
```csharp  
[OperationContract]  
public void SetTemperature(int temperature);  
```  
  
```vb  
<OperationContract()>  
Sub SetTemperature(temperature As Integer)  
```  
  
 Bu gibi bir tek yönlü işleminden farklıdır:  
  
```csharp  
[OperationContract(IsOneWay=true)]  
public void SetLightbulbStatus(bool isOn);  
```  
  
```vb  
<OperationContract(IsOneWay:=True)>  
Sub SetLightbulbStatus(isOne As Boolean)  
```  
  
 `SetTemperatureStatus` İşlemi boş bir ileti döndürür. Giriş ileti işlenirken bir sorun varsa, bunun yerine bir hata döndürebilir. `SetLightbulbStatus` İşlemi hiçbir şey döndürür. Bu işlem hata durumundan iletişim kurmak için bir yolu yoktur.  
  
## <a name="describing-messages-by-using-message-contracts"></a>İleti sözleşmeleri kullanarak açıklayan iletiler  
 İletinin tamamını temsil etmek için tek bir türü kullanmak isteyebilirsiniz. Bu amaç için bir veri sözleşmesi kullanmak mümkün olsa da, bunu yapmak için önerilen yöntem ileti sözleşmesi kullanmaktır — bu sonuç XML kaydırma gereksiz düzeylerini önler. Ayrıca, ileti sözleşmeleri sonuç iletileri üzerinden daha fazla denetim izin verir. Örneğin, ileti gövdesi içinde bilgi parçalarını olmalıdır ve ileti üstbilgilerini olacağı karar verebilirsiniz. Aşağıdaki örnek ileti sözleşmeleri kullanımını göstermektedir.  
  
```csharp  
[ServiceContract]  
public interface IAirfareQuoteService  
{  
    [OperationContract]  
    GetAirfareResponse GetAirfare(GetAirfareRequest request);  
}  
  
[MessageContract]  
public class GetAirfareRequest  
{  
    [MessageHeader] public DateTime date;  
    [MessageBodyMember] public Itinerary itinerary;  
}  
  
[MessageContract]  
public class GetAirfareResponse  
{  
    [MessageBodyMember] public float airfare;  
    [MessageBodyMember] public string currency;  
}  
  
[DataContract]  
public class Itinerary  
{  
    [DataMember] public string fromCity;  
    [DataMember] public string toCity;  
}  
```  
  
```vb  
<ServiceContract()>  
Public Interface IAirfareQuoteService  
    <OperationContract()>  
    Function GetAirfare(request As GetAirfareRequest) As GetAirfareResponse  
End Interface  
  
<MessageContract()>  
Public Class GetAirfareRequest  
    <MessageHeader()>   
    Public Property date as DateTime  
    <MessageBodyMember()>  
    Public Property itinerary As Itinerary  
End Class  
  
<MessageContract()>  
Public Class GetAirfareResponse  
    <MessageBodyMember()>  
    Public Property airfare As Double  
    <MessageBodyMember()> Public Property currency As String  
End Class  
  
<DataContract()>  
Public Class Itinerary  
    <DataMember()> Public Property fromCity As String  
    <DataMember()> Public Property toCity As String  
End Class  
```  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][İleti sözleşmeleri kullanılıyor](../../../../docs/framework/wcf/feature-details/using-message-contracts.md).  
  
 Önceki örnekte, <xref:System.Runtime.Serialization.DataContractSerializer> sınıfı varsayılan olarak hala kullanılmaktadır. <xref:System.Xml.Serialization.XmlSerializer> Sınıfı ileti sözleşmeleri ile de kullanılabilir. Bunu yapmak için uygulamanız <xref:System.ServiceModel.XmlSerializerFormatAttribute> özniteliği işlemi ya da sözleşme ve türleri ile uyumlu kullanın <xref:System.Xml.Serialization.XmlSerializer> ileti üstbilgilerini ve gövde üyeler sınıfta.  
  
## <a name="describing-messages-by-using-streams"></a>Akışlar kullanarak açıklayan iletiler  
 İşlem iletileri açıklamak için başka bir yolu kullanmaktır <xref:System.IO.Stream> sınıf veya türetilmiş sınıflarından işlemi sözleşme veya (olmalıdır yalnızca üye bu durumda) bir ileti sözleşmesi gövde üye olarak biri. Gelen iletiler için tür olmalıdır `Stream`— türetilen sınıflar kullanamazsınız.  
  
 Seri hale getirici, çağırma yerine [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bir akışından verileri alır ve giden iletisine doğrudan bir yerleştirir veya bir gelen iletisinden verileri alır ve bir akışa doğrudan yerleştirir. Aşağıdaki örnek akışları kullanımını göstermektedir.  
  
```csharp  
[OperationContract]  
public Stream DownloadFile(string fileName);  
```  
  
```vb  
<OperationContract()>  
Function DownloadFile(fileName As String) As String  
```  
  
 Birleştiremez `Stream` ve akış olmayan verileri tek bir ileti gövdesi. Ek veriler ileti üstbilgilerinde yerleştirmek için bir ileti sözleşmesi kullanın. Aşağıdaki örnek, işlem sözleşmesi tanımlarken akışları yanlış kullanımını gösterir.  
  
```csharp  
//Incorrect:  
// [OperationContract]  
// public void UploadFile (string fileName, Stream fileData);  
```  
  
```vb  
'Incorrect:  
    '<OperationContract()>  
    Public Sub UploadFile(fileName As String, fileData As StreamingContext)  
```  
  
 Aşağıdaki örnek, bir işlem sözleşmesi tanımlarken akışları doğru kullanımını gösterir.  
  
```csharp  
[OperationContract]  
public void UploadFile (UploadFileMessage message);  
//code omitted  
[MessageContract]  
public class UploadFileMessage  
{  
    [MessageHeader] public string fileName;  
    [MessageBodyMember] public Stream fileData;  
}  
```  
  
```vb  
<OperationContract()>  
Public Sub UploadFile(fileName As String, fileData As StreamingContext)  
'Code Omitted  
<MessageContract()>  
Public Class UploadFileMessage  
   <MessageHeader()>  
    Public Property fileName As String  
    <MessageBodyMember()>  
    Public Property fileData As Stream  
End Class  
```  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Büyük veriler ve akış](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
## <a name="using-the-message-class"></a>İleti Sınıfını Kullanma  
 Gönderilen veya alınan iletiler üzerinde tam programsal denetim sağlamak için kullanabileceğiniz <xref:System.ServiceModel.Channels.Message> doğrudan, aşağıdaki örnek kodda gösterildiği gibi sınıfı.  
  
```csharp  
[OperationContract]  
public void LogMessage(Message m);  
```  
  
```vb  
<OperationContract()>  
Sub LogMessage(m As Message)  
```  
  
 İçinde ayrıntılı olarak açıklanmıştır Gelişmiş bir senaryo budur [ileti sınıfını kullanma](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).  
  
## <a name="describing-fault-messages"></a>Açıklayan hata iletileri  
 Çıkış veya başvuru parametre ve dönüş değeri açıklanan iletileri ek olarak, en az iki olası iletileri tek yönlü değil herhangi bir işlem döndürebilirsiniz: kendi normal yanıt iletisi ve bir hata iletisi. Aşağıdaki işlem sözleşmesi göz önünde bulundurun.  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, DateTime date);  
```  
  
```vb  
<OperationContract()>  
Function GetAirfare(fromCity As String, toCity As String, date as DateTime)  
```  
  
 Bu işlem ya da içeren normal bir ileti döndürebilir bir `float` sayı veya bir hata kodu ve açıklama içeren bir hata iletisi. Bunu atma tarafından gerçekleştirmek bir <xref:System.ServiceModel.FaultException> hizmet uygulamanızda.  
  
 Kullanarak ek olası hata iletileri belirtebilirsiniz <xref:System.ServiceModel.FaultContractAttribute> özniteliği. Seri hale getirilebilir kullanarak ek hataları olmalıdır <xref:System.Runtime.Serialization.DataContractSerializer>, aşağıdaki örnek kodda gösterildiği gibi.  
  
```csharp  
[OperationContract]  
[FaultContract(typeof(ItineraryNotAvailableFault))]  
float GetAirfare(string fromCity, string toCity, DateTime date);  
  
//code omitted  
  
[DataContract]  
public class ItineraryNotAvailableFault  
{  
    [DataMember]  
    public bool IsAlternativeDateAvailable;  
  
    [DataMember]  
    public DateTime alternativeSuggestedDate;  
}  
```  
  
```vb  
<OperationContract()>  
<FaultContract(GetType(ItineraryNotAvailableFault))>  
Function GetAirfare(fromCity As String, toCity As String, date as DateTime) As Double  
  
'Code Omitted  
<DataContract()>  
Public Class  
  <DataMember()>  
  Public Property IsAlternativeDateAvailable As Boolean  
  <DataMember()>  
  Public Property alternativeSuggestedDate As DateTime  
End Class  
```  
  
 Bu ek hataları atma tarafından oluşturulabilir. bir <xref:System.ServiceModel.FaultException%601> uygun veri sözleşmesi türü. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Özel durumları ve hataları işleme](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).  
  
 Kullanamazsınız <xref:System.Xml.Serialization.XmlSerializer> hataları tanımlamak için sınıf. <xref:System.ServiceModel.XmlSerializerFormatAttribute> Hataya sözleşmeleri üzerinde hiçbir etkisi olmaz.  
  
## <a name="using-derived-types"></a>Türetilmiş türler kullanma  
 Bir işlem veya ileti sözleşmesi temel türü kullanın ve sonra işlemi gerçekte çağrılırken, türetilmiş bir tür kullanın isteyebilirsiniz. Bu durumda, ya da kullanmalıdır <xref:System.ServiceModel.ServiceKnownTypeAttribute> özniteliği ya da bazı alternatif bir mekanizma kullanımına izin vermek için türetilen türlerle. Aşağıdaki işlem göz önünde bulundurun.  
  
```csharp  
[OperationContract]  
public bool IsLibraryItemAvailable(LibraryItem item);  
```  
  
```vb
<OperationContract()>  
    Function IsLibraryItemAvailable(item As LibraryItem) As Boolean  
```  
  
 İki yazdığı, varsayın `Book` ve `Magazine`, türetilen `LibraryItem`. Bu türlerini kullanmak için `IsLibraryItemAvailable` işlemi, işlemi aşağıdaki gibi değiştirebilirsiniz:  
  
 `[OperationContract]`  
  
 `[ServiceKnownType(typeof(Book))]`  
  
 `[ServiceKnownType(typeof(Magazine))]`  
  
 `public bool IsLibraryItemAvailable(LibraryItem item);`  
  
 Alternatif olarak, kullanabileceğiniz <xref:System.Runtime.Serialization.KnownTypeAttribute> ne zaman özniteliği varsayılan <xref:System.Runtime.Serialization.DataContractSerializer> , aşağıdaki örnek kodda gösterildiği gibi kullanılıyor.  
  
```csharp  
[OperationContract]  
public bool IsLibraryItemAvailable(LibraryItem item);  
  
// code omitted   
  
[DataContract]  
[KnownType(typeof(Book))]  
[KnownType(typeof(Magazine))]  
public class LibraryItem  
{  
    //code omitted  
}  
```  
  
```vb  
<OperationContract()>  
Function IsLibraryItemAvailable(item As LibraryItem) As Boolean  
  
'Code Omitted  
<DataContract()>  
<KnownType(GetType(Book))>  
<KnownType(GetType(Magazine))>  
Public Class LibraryItem  
  'Code Omitted  
End Class  
```  
  
 Kullanabileceğiniz <xref:System.Xml.Serialization.XmlIncludeAttribute> özniteliği kullanırken <xref:System.Xml.Serialization.XmlSerializer>.  
  
 Uygulayabileceğiniz <xref:System.ServiceModel.ServiceKnownTypeAttribute> özniteliği bir işlem veya tüm hizmet. Bir türü veya yöntemin adını çağrılacak gibi bilinen türlerinin bir listesini almak için kabul <xref:System.Runtime.Serialization.KnownTypeAttribute> özniteliği. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Veri sözleşmesi bilinen türler](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
## <a name="specifying-the-use-and-style"></a>Kullanım ve stil belirtme  
 Web Hizmetleri Açıklama Dili (WSDL), iki yaygın olarak kullanarak Hizmetleri açıklanırken kullanılan belge ve uzak yordam çağrısı (RPC) stillerdir. Belge stilde tüm ileti gövdesi şema kullanılarak tanımlanır ve bu şema öğeleri başvurarak çeşitli ileti gövdesi bölümleri WSDL açıklar. RPC stilinde WSDL öğenin yerine, her ileti parçası için bir şema türü ifade eder. Bazı durumlarda, el ile bu stiller birini seçmeniz gerekir. Bunu uygulayarak yapmak <xref:System.ServiceModel.DataContractFormatAttribute> özniteliği ve ayarı `Style` özelliği (zaman <xref:System.Runtime.Serialization.DataContractSerializer> kullanımda), veya ayarlayarak `Style` üzerinde <xref:System.ServiceModel.XmlSerializerFormatAttribute> özniteliği (kullanırken <xref:System.Xml.Serialization.XmlSerializer>).  
  
 Ayrıca, <xref:System.Xml.Serialization.XmlSerializer> serileştirilmiş XML iki tür destekler: `Literal` ve `Encoded`. `Literal`en yaygın olarak kabul edilen biçimidir ve yalnızca form <xref:System.Runtime.Serialization.DataContractSerializer> destekler. `Encoded`SOAP belirtimi 5 bölümünde açıklanan eski bir form ve yeni hizmetler için önerilmez. Geçiş yapmak için `Encoded` modunu ayarlama `Use` özelliği <xref:System.ServiceModel.XmlSerializerFormatAttribute> özniteliğini `Encoded`.  
  
 Çoğu durumda, varsayılan ayarları değiştirmemelisiniz `Style` ve `Use` özellikleri.  
  
## <a name="controlling-the-serialization-process"></a>Seri hale getirme işlemi denetleme  
 Veri seri hale getirilmiş biçimini özelleştirmek için değişik yapabilirsiniz.  
  
### <a name="changing-server-serialization-settings"></a>Sunucu serileştirme ayarlarını değiştirme  
 Zaman varsayılan <xref:System.Runtime.Serialization.DataContractSerializer> olan kullanımda uygulayarak için seri hale getirme işlemi hizmet üzerinde bazı yönlerini denetleyebilirsiniz <xref:System.ServiceModel.ServiceBehaviorAttribute> hizmete özniteliği. Özellikle, kullanabilir `MaxItemsInObjectGraph` nesneleri sayısının üst sınırını belirler kota ayarlamak için özellik <xref:System.Runtime.Serialization.DataContractSerializer> seri durumdan çıkarır. Kullanabileceğiniz `IgnoreExtensionDataObject` gidiş sürüm oluşturma özelliği devre dışı bırakmak için özelliği. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Kotalar, bkz: [veriler için güvenlik konuları](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]gidiş, bkz: [İleri uyumlu veri sözleşmeleri](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
```csharp  
[ServiceBehavior(MaxItemsInObjectGraph=100000)]  
public class MyDataService:IDataService  
{  
    public DataPoint[] GetData()  
    {  
       // Implementation omitted  
    }  
}  
```  
  
```vb  
<ServiceBehavior(MaxItemsInObjectGraph:=100000)>  
Public Class MyDataService Implements IDataService  
  
    Function GetData() As DataPoint()  
         ‘ Implementation omitted  
    End Function  
End Interface  
```  
  
### <a name="serialization-behaviors"></a>Seri hale getirme davranışları  
 İki davranışları kullanılabilir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> ve <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> , otomatik olarak takılı olduğundan hangi seri hale getirici, belirli bir işlem için kullanılmakta olan bağlı. Bu davranışların otomatik olarak uygulandığından, normalde bunları haberdar olmanız gerekmez.  
  
 Ancak, `DataContractSerializerOperationBehavior` sahip `MaxItemsInObjectGraph`, `IgnoreExtensionDataObject`, ve `DataContractSurrogate` özellikleri seri hale getirme işlemi özelleştirmek için kullanabilirsiniz. İlk iki özellikleri, önceki bölümde açıklandığı gibi aynı anlamı yoktur. Kullanabileceğiniz `DataContractSurrogate` özelleştirilmesini ve genişletilmesini seri hale getirme işlemi için güçlü bir mekanizma olan veri sözleşmesi yedekleri etkinleştirmek için özellik. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Veri sözleşmesi yedekleri](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).  
  
 Kullanabileceğiniz `DataContractSerializerOperationBehavior` istemci ve sunucu serileştirme özelleştirmek için. Aşağıdaki örnek artırmak nasıl gösterir `MaxItemsInObjectGraph` kota istemci üzerinde.  
  
```csharp  
ChannelFactory<IDataService> factory = new ChannelFactory<IDataService>(binding, address);  
foreach (OperationDescription op in factory.Endpoint.Contract.Operations)  
{  
    DataContractSerializerOperationBehavior dataContractBehavior =  
                op.Behaviors.Find<DataContractSerializerOperationBehavior>()  
                as DataContractSerializerOperationBehavior;  
    if (dataContractBehavior != null)  
    {  
        dataContractBehavior.MaxItemsInObjectGraph = 100000;  
    }  
}  
IDataService client = factory.CreateChannel();  
```  
  
```vb  
Dim factory As ChannelFactory(Of IDataService) = New ChannelFactory(Of IDataService)(binding, address)  
For Each op As OperationDescription In factory.Endpoint.Contract.Operations  
        Dim dataContractBehavior As DataContractSerializerOperationBehavior = op.Behaviors.Find(Of DataContractSerializerOperationBehavior)()  
        If dataContractBehavior IsNot Nothing Then  
            dataContractBehavior.MaxItemsInObjectGraph = 100000  
        End If  
     Next  
    Dim client As IDataService = factory.CreateChannel  
```  
  
 Kendini barındıran durumda hizmet eşdeğer kod aşağıdadır.  
  
```csharp  
ServiceHost serviceHost = new ServiceHost(typeof(IDataService))  
foreach (ServiceEndpoint ep in serviceHost.Description.Endpoints)  
{  
foreach (OperationDescription op in ep.Contract.Operations)  
{  
        DataContractSerializerOperationBehavior dataContractBehavior =  
           op.Behaviors.Find<DataContractSerializerOperationBehavior>()  
                as DataContractSerializerOperationBehavior;  
        if (dataContractBehavior != null)  
        {  
            dataContractBehavior.MaxItemsInObjectGraph = 100000;  
        }  
}  
}  
serviceHost.Open();  
```  
  
```vb  
Dim serviceHost As ServiceHost = New ServiceHost(GetType(IDataService))  
        For Each ep As ServiceEndpoint In serviceHost.Description.Endpoints  
            For Each op As OperationDescription In ep.Contract.Operations  
                Dim dataContractBehavior As DataContractSerializerOperationBehavior = op.Behaviors.Find(Of DataContractSerializerOperationBehavior)()  
  
                If dataContractBehavior IsNot Nothing Then  
                    dataContractBehavior.MaxItemsInObjectGraph = 100000  
                End If  
            Next  
        Next  
        serviceHost.Open()  
```  
  
 Web barındırılan durumda, yeni bir oluşturmalısınız `ServiceHost` türetilmiş sınıf ve hizmet ana bilgisayar üreteci prize takın için kullanın.  
  
### <a name="controlling-serialization-settings-in-configuration"></a>Yapılandırmadaki serileştirme ayarlarını denetleme  
 `MaxItemsInObjectGraph` Ve `IgnoreExtensionDataObject` kullanarak yapılandırma aracılığıyla denetlenebilir `dataContractSerializer` uç noktası veya hizmet davranışı, aşağıdaki örnekte gösterildiği gibi.  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name="LargeQuotaBehavior">  
                    <dataContractSerializer  
                      maxItemsInObjectGraph="100000" />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
        <client>  
            <endpoint address=http://example.com/myservice  
                  behaviorConfiguration="LargeQuotaBehavior"  
                binding="basicHttpBinding" bindingConfiguration=""   
                            contract="IDataService"  
                name="" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
### <a name="shared-type-serialization-object-graph-preservation-and-custom-serializers"></a>Türü seri hale getirme, Nesne grafiği korunması ve özel serileştiricileri paylaşılan  
 <xref:System.Runtime.Serialization.DataContractSerializer> Veri sözleşmesi adları ve .NET Tür adları kullanarak serileştirir. Bu hizmet odaklı mimari tenets ile tutarlıdır ve esneklik için önemli ölçüde sağlar — .NET türleri kablo sözleşme etkilemeden değiştirebilirsiniz. Nadir durumlarda, gerçek .NET Tür adları, seri hale getirmek böylece istemci ve sunucu, .NET Framework remoting teknolojisine benzer arasında sıkı bağ Tanıtımı isteyebilirsiniz. Bu önerilen bir uygulama dışında geçiş genellikle ortaya nadir durumlarda değil [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] .NET Framework remoting gelen. Bu durumda, kullanmalısınız <xref:System.Runtime.Serialization.NetDataContractSerializer> sınıfının yerine <xref:System.Runtime.Serialization.DataContractSerializer> sınıfı.  
  
 <xref:System.Runtime.Serialization.DataContractSerializer> Normalde nesne grafik nesnesi ağaçları olarak serileştirir. Diğer bir deyişle, aynı nesne için birden çok kez geçer, birden çok kez sıralanır. Örneğin, göz önünde bulundurun bir `PurchaseOrder` türü adresi adlı iki alan örnek `billTo` ve `shipTo`. Her iki alan aynı adres örneğini ayarlarsanız, iki aynı adres örneği vardır seri hale getirme ve seri durumdan sonra. Nesne grafiklerinin XML temsil etmek için standart birlikte çalışabilir yolu olduğundan bu yapılır (eski kodlanmış SOAP standart kullanılabilir dışında <xref:System.Xml.Serialization.XmlSerializer>, önceki bölümde açıklandığı gibi `Style` ve `Use`). Nesne grafiklerinin ağaçlar seri hale getirme belirli dezavantajları vardır, örneğin, döngüsel başvurulara grafiklerle seri hale getirilemez. Bazen, birlikte çalışabilen olmasa da doğru nesne grafiğinin seri hale getirme için geçiş gerekli değildir. Bu kullanılarak yapılabilir <xref:System.Runtime.Serialization.DataContractSerializer> ile oluşturulan `preserveObjectReferences` parametre kümesine `true`.  
  
 Bazen, yerleşik serileştiricileri senaryonuz için yeterli değildir. Çoğu durumda, kullanmaya devam edebilirsiniz <xref:System.Runtime.Serialization.XmlObjectSerializer> hangi hem Özet <xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Runtime.Serialization.NetDataContractSerializer> türetilir.  
  
 Önceki üç durumda (.NET türü korunması, Nesne grafiği korunması ve tamamen özel `XmlObjectSerializer`-seri hale getirme tabanlı) tüm özel bir seri hale getirici prize takılı gerekir. Bunu yapmak için şu adımları izleyin:  
  
1.  Türetme kendi davranışı yazma <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>.  
  
2.  İki geçersiz kılma `CreateSerializer` kendi seri hale getirici döndürülecek yöntemleri (ya da <xref:System.Runtime.Serialization.NetDataContractSerializer>, <xref:System.Runtime.Serialization.DataContractSerializer> ile `preserveObjectReferences` kümesine `true`, veya kendi özel <xref:System.Runtime.Serialization.XmlObjectSerializer>).  
  
3.  Hizmet ana bilgisayarını açma veya bir istemci kanal oluşturma önce varolan kaldırmak <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> davranışı ve önceki adımlarda oluşturduğunuz özel türetilen sınıfta takın.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]seri hale getirme kavramları gelişmiş, bkz: [seri hale getirme ve seri durumdan çıkarma](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XmlSerializer Sınıfını Kullanma](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)  
 [Nasıl yapılır: Akışı Etkinleştirme](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)  
 [Nasıl yapılır: Bir Sınıf veya Yapı için Temel Bir Veri Anlaşması Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
