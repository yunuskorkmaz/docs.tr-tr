---
title: Hizmet Sözleşmelerinde Veri Aktarımını Belirtme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], data transfer
ms.assetid: 7c5a26c8-89c9-4bcb-a4bc-7131e6d01f0c
ms.openlocfilehash: a3ac0f321a20624deea1fe382d04a8d4e1b6c510
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59135206"
---
# <a name="specifying-data-transfer-in-service-contracts"></a>Hizmet Sözleşmelerinde Veri Aktarımını Belirtme
Windows Communication Foundation (WCF), bir Mesajlaşma altyapısı düşünülebilir. Hizmet işlemleri iletileri almak, bunları işlemek ve bunları ileti göndermek. İletileri işlem sözleşmeleri kullanma açıklanmaktadır. Örneğin, aşağıdaki sözleşme göz önünde bulundurun.  
  
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
  
 Bu konu, bir işlem anlaşması iletileri açıklayabilirsiniz çeşitli yolları açıklar.  
  
## <a name="describing-messages-by-using-parameters"></a>Parametreleri kullanarak açıklayan ileti  
 Bir iletiyi tanımlamak için en basit yolu, bir parametre listesi ve dönüş değeri kullanmaktır. Önceki örnekte `fromCity` ve `toCity` dizesi parametreleri istek iletisi açıklamak için kullanıldığını ve kayan nokta dönüş değeri, yanıt iletisi tanımlamak için kullanıldı. Tek başına dönüş değeri bir yanıt iletisi açıklamak için yeterli değilse, out Parametreleri kullanılabilir. Örneğin, aşağıdaki işlemi sahip `fromCity` ve `toCity` , istek iletisi ve bir sayı bir para birimi, yanıt iletisi ile birlikte:  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, out string currency);  
```  
  
```vb  
<OperationContract()>  
    Function GetAirfare(fromCity As String, toCity As String) As Double  
```  
  
 Ayrıca, hem isteğin hem de yanıt iletisi parametresi bir parçası haline getirmek için başvuru parametreleri kullanabilirsiniz. Parametreler (XML biçimine dönüştürülür) seri hale getirilebilir türler olmalıdır. Varsayılan olarak, WCF adlı bir bileşen kullanır <xref:System.Runtime.Serialization.DataContractSerializer> bu dönüşümü gerçekleştirmek için sınıf. En temel türlerin (gibi `int`, `string`, `float`, ve `DateTime`.) desteklenir. Kullanıcı tanımlı türler genellikle bir veri sözleşmesi olması gerekir. Daha fazla bilgi için [kullanarak veri sözleşmeleri](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
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
  
 Bazen, `DataContractSerializer` türleri serileştirmek yeterli değil. WCF destekleyen bir alternatif serileştirme motoruna <xref:System.Xml.Serialization.XmlSerializer>, hangi parametreleri seri hale getirmek için de kullanabilirsiniz. <xref:System.Xml.Serialization.XmlSerializer> Sonuç XML öznitelikleri gibi kullanma hakkında daha fazla denetime kullanmanıza olanak tanır `XmlAttributeAttribute`. Kullanmaya geçmek <xref:System.Xml.Serialization.XmlSerializer> belirli bir işlem veya tüm hizmet geçerli <xref:System.ServiceModel.XmlSerializerFormatAttribute> öznitelik için bir işlem veya hizmet. Örneğin:  
  
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
  
 Daha fazla bilgi için [XmlSerializer sınıfını kullanarak](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md). Bu el ile geçiş unutmayın <xref:System.Xml.Serialization.XmlSerializer> gösterildiği gibi bu nedenle bu konudaki gibi ayrıntılı yapmak için belirli olmadığı sürece burada önerilmez.  
  
 .NET parametre adları sözleşme adlarından yalıtmak için kullanabileceğiniz <xref:System.ServiceModel.MessageParameterAttribute> özniteliği ve kullanma `Name` sözleşme adı ayarlamak için özellik. Örneğin, bu konudaki ilk örnek için aşağıdaki işlem anlaşması eşdeğerdir.  
  
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
  
## <a name="describing-empty-messages"></a>Boş açıklayan ileti  
 Hiçbir girdi veya başvuru parametreleri sağlayarak bir boş istek iletisi açıklanabilir. Örneğin C#:  
  
 `[OperationContract]`  
  
 `public int GetCurrentTemperature();`  
  
 Örneğin VB içinde:  
  
 `<OperationContract()>`  
  
 `Function GetCurrentTemperature() as Integer`  
  
 Bir boş bir yanıt iletisi sağlayarak tanımlanabilir bir `void` dönüş türü ve hiçbir çıktı veya başvuru parametreleri. Örneğin:  
  
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
  
 `SetTemperatureStatus` İşlem, boş bir ileti döndürür. Giriş iletisi işlenirken bir sorun varsa, bunun yerine bir hata döndürebilir. `SetLightbulbStatus` İşlem nothing döndürür. Bu işlem bir hata durumundan iletişim kurmak için hiçbir yolu yoktur.  
  
## <a name="describing-messages-by-using-message-contracts"></a>İleti sözleşmeleri'ni kullanarak açıklayan ileti  
 Tüm ileti temsil etmek için tek bir tür kullanmak isteyebilirsiniz. Bu amaç için bir veri anlaşması kullanmak mümkün olsa da, bunu yapmak için önerilen yöntem bir ileti anlaşması kullanmaktır — bu sonuç XML sarmalama gereksiz düzeyde önler. Ayrıca, ileti sözleşmeleri sonuç iletileri üzerinden daha fazla denetimle alıştırma sağlar. Örneğin, ileti gövdesindeki bilgiler olmalıdır ve ileti üst bilgilerinde olacağı karar verebilirsiniz. Aşağıdaki örnek ileti sözleşmeleri kullanımını gösterir.  
  
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
  
 Daha fazla bilgi için [kullanarak ileti sözleşmeleri](../../../../docs/framework/wcf/feature-details/using-message-contracts.md).  
  
 Önceki örnekte, <xref:System.Runtime.Serialization.DataContractSerializer> sınıfı varsayılan olarak hala kullanılmaktadır. <xref:System.Xml.Serialization.XmlSerializer> Sınıfı ileti sözleşmeleri ile de kullanılabilir. Bunu yapmak için uygulama <xref:System.ServiceModel.XmlSerializerFormatAttribute> özniteliği işlemi ya da sözleşme ve ile uyumlu türler kullanan <xref:System.Xml.Serialization.XmlSerializer> ileti üstbilgi ve gövde üyeleri sınıf.  
  
## <a name="describing-messages-by-using-streams"></a>Akışları kullanarak açıklayan ileti  
 İleti işlemleri tanımlamak için başka bir yolu <xref:System.IO.Stream> sınıf ya da işlem anlaşması veya (olmalıdır tek üyesi bu durumda) ileti anlaşması gövdesi üye olarak ondan türetilen sınıflardan biri. Gelen iletiler için tür olmalıdır `Stream`— türetilmiş sınıflar kullanamazsınız.  
  
 Seri hale getirici çağrılırken, yerine WCF bir akıştan verileri alır ve doğrudan bir giden iletisine, yerleştirir veya gelen bir iletiden verileri alır ve doğrudan bir akışa koyar. Aşağıdaki örnek, Akışlar kullanımını gösterir.  
  
```csharp  
[OperationContract]  
public Stream DownloadFile(string fileName);  
```  
  
```vb  
<OperationContract()>  
Function DownloadFile(fileName As String) As String  
```  
  
 Birleştirmeniz mümkün olmayacaktır `Stream` ve tek ileti gövdesinde veri akışı olmayan. Ek veriler ileti üst bilgilerinde koymak için bir ileti anlaşması'ı kullanın. Aşağıdaki örnek, işlem anlaşması tanımlarken akışları yanlış kullanımı gösterir.  
  
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
  
 Aşağıdaki örnek, bir işlem anlaşması tanımlarken akışları doğru kullanımını gösterir.  
  
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
  
 Daha fazla bilgi için [büyük veriler ve akış](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
## <a name="using-the-message-class"></a>İleti Sınıfını Kullanma  
 Gönderilen veya alınan iletileri üzerinde tam programlı denetim sağlamak için kullanabileceğiniz <xref:System.ServiceModel.Channels.Message> doğrudan, aşağıdaki örnekte gösterildiği gibi sınıf.  
  
```csharp  
[OperationContract]  
public void LogMessage(Message m);  
```  
  
```vb  
<OperationContract()>  
Sub LogMessage(m As Message)  
```  
  
 Ayrıntılı olarak açıklanan Gelişmiş bir senaryo budur [ileti sınıfını kullanma](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).  
  
## <a name="describing-fault-messages"></a>Açıklayıcı hata iletileri  
 Çıkış veya başvuru parametreleri ve dönüş değeri tarafından açıklanan iletileri ek olarak, tek yönlü değil herhangi bir işlem en az iki olası iletileri döndürebilir: normal yanıt iletisini ve bir hata iletisi. Aşağıdaki işlem anlaşması göz önünde bulundurun.  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, DateTime date);  
```  
  
```vb  
<OperationContract()>  
Function GetAirfare(fromCity As String, toCity As String, date as DateTime)  
```  
  
 Bu işlemi ya da içeren bir normal iletisi döndürebilir bir `float` sayı veya bir hata kodu ve açıklama içeren bir hata iletisi. Bu özel durum atma tarafından gerçekleştirmek bir <xref:System.ServiceModel.FaultException> hizmet uygulamanızda.  
  
 Olası ek hata iletileri kullanarak belirtebilirsiniz <xref:System.ServiceModel.FaultContractAttribute> özniteliği. Seri hale getirilebilir kullanarak ek hataları olmalıdır <xref:System.Runtime.Serialization.DataContractSerializer>, aşağıdaki örnekte gösterildiği gibi.  
  
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
  
 Bu ek hatalar atma tarafından oluşturulabilir. bir <xref:System.ServiceModel.FaultException%601> uygun veri anlaşması türü. Daha fazla bilgi için [özel durum işleme ve hataları](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).  
  
 Kullanamazsınız <xref:System.Xml.Serialization.XmlSerializer> hataları tanımlamak için sınıf. <xref:System.ServiceModel.XmlSerializerFormatAttribute> Hata sözleşmelerine üzerinde hiçbir etkisi olmaz.  
  
## <a name="using-derived-types"></a>Türetilmiş türleri kullanma  
 Temel tür bir işlem ya da ileti anlaşması, ve ardından türetilmiş bir tür gerçekten işlemi çağrılırken kullanmak isteyebilirsiniz. Bu durumda, kullanmanız gerekir <xref:System.ServiceModel.ServiceKnownTypeAttribute> özniteliği veya kullanımına olanak tanımak için bazı alternatif bir mekanizmaya türetilmiş tür. Şu işlem göz önünde bulundurun.  
  
```csharp  
[OperationContract]  
public bool IsLibraryItemAvailable(LibraryItem item);  
```  
  
```vb
<OperationContract()>  
    Function IsLibraryItemAvailable(item As LibraryItem) As Boolean  
```  
  
 İki, türleri, varsayar `Book` ve `Magazine`, türetilen `LibraryItem`. Bu tür olarak kullanılacak `IsLibraryItemAvailable` işlemi, işlemi aşağıdaki gibi değiştirebilirsiniz:  
  
 `[OperationContract]`  
  
 `[ServiceKnownType(typeof(Book))]`  
  
 `[ServiceKnownType(typeof(Magazine))]`  
  
 `public bool IsLibraryItemAvailable(LibraryItem item);`  
  
 Alternatif olarak, <xref:System.Runtime.Serialization.KnownTypeAttribute> ne zaman öznitelik varsayılan <xref:System.Runtime.Serialization.DataContractSerializer> , aşağıdaki örnekte gösterildiği gibi kullanılır.  
  
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
  
 Uygulayabileceğiniz <xref:System.ServiceModel.ServiceKnownTypeAttribute> özniteliği bir işlem veya tüm hizmet. Bir tür veya yöntemin adını çağırmak için olduğu gibi bilinen türlerinin bir listesini almak için kabul <xref:System.Runtime.Serialization.KnownTypeAttribute> özniteliği. Daha fazla bilgi için [veri sözleşme bilinen türleri](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
## <a name="specifying-the-use-and-style"></a>Use ve Style belirtme  
 Web Hizmetleri Açıklama Dili (WSDL), iki yaygın olarak kullanan hizmetler tanıtırken kullanılan stilleri belge ve uzak yordam çağrısı (RPC) olabilir. Belge stilinde şemayı kullanarak tüm ileti gövdesi açıklanmıştır ve o şema içindeki öğelere başvuran tarafından WSDL çeşitli ileti gövdesi bölümlerini açıklar. RPC stili bir şema türü bir öğenin yerine her ileti bölümü için WSDL ifade eder. Bazı durumlarda, el ile bu stiller birini seçmeniz gerekir. Bunu uygulayarak yapabilirsiniz <xref:System.ServiceModel.DataContractFormatAttribute> özniteliği ve ayarı `Style` özelliği (zaman <xref:System.Runtime.Serialization.DataContractSerializer> kullanılır), veya ayarlayarak `Style` üzerinde <xref:System.ServiceModel.XmlSerializerFormatAttribute> özniteliği (kullanırken <xref:System.Xml.Serialization.XmlSerializer>).  
  
 Ayrıca, <xref:System.Xml.Serialization.XmlSerializer> serileştirilmiş XML iki biçimini destekler: `Literal` ve `Encoded`. `Literal` en yaygın olarak kabul edilen form ve yalnızca form <xref:System.Runtime.Serialization.DataContractSerializer> destekler. `Encoded` SOAP belirtimine 5. bölümünde açıklanan eski biçimidir ve yeni hizmetleri için önerilmez. Geçiş yapmak `Encoded` modu ayarlamak `Use` özelliği <xref:System.ServiceModel.XmlSerializerFormatAttribute> özniteliğini `Encoded`.  
  
 Çoğu durumda, varsayılan ayarlarını değiştirmemelisiniz `Style` ve `Use` özellikleri.  
  
## <a name="controlling-the-serialization-process"></a>Seri hale getirme işlemi denetleme  
 Veri seri hale getirilmiş biçimini özelleştirmek için etmenizi yapabilirsiniz.  
  
### <a name="changing-server-serialization-settings"></a>Sunucu serileştirme ayarlarını değiştirme  
 Varsayılan <xref:System.Runtime.Serialization.DataContractSerializer> olan kullanımda uygulama tarafından seri hale getirme işlemi hizmet üzerinde bazı yönlerini denetleyebilirsiniz <xref:System.ServiceModel.ServiceBehaviorAttribute> hizmete özniteliği. Özellikle, kullandığınız `MaxItemsInObjectGraph` nesneleri maksimum sayısını sınırlayan kota ayarlamak için özellik <xref:System.Runtime.Serialization.DataContractSerializer> seri durumdan çıkarır. Kullanabileceğiniz `IgnoreExtensionDataObject` gidiş dönüşü sürüm oluşturma özelliği devre dışı bırakmak için özelliği. Kotaları hakkında daha fazla bilgi için bkz: [veriler için güvenlik konuları](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md). Gidiş dönüşü hakkında daha fazla bilgi için bkz: [İleri uyumlu veri sözleşmeleri](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
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
  
### <a name="serialization-behaviors"></a>Serileştirme davranışları  
 WCF'de, iki davranışları kullanılabilir <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> ve <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> , otomatik olarak takılıdır hangi seri hale getirici belirli bir işlem için kullanımda olduğuna bağlı olarak. Bu davranışların otomatik olarak uygulandığından, normalde bunları haberdar olmanız gerekmez.  
  
 Ancak, `DataContractSerializerOperationBehavior` sahip `MaxItemsInObjectGraph`, `IgnoreExtensionDataObject`, ve `DataContractSurrogate` seri hale getirme işlemi özelleştirmek için kullanabileceğiniz özellikleri. İlk iki özelliklere, önceki bölümde açıklandığı gibi aynı anlama sahiptir. Kullanabileceğiniz `DataContractSurrogate` özelleştirilmesini ve genişletilmesini seri hale getirme işlemi için güçlü bir mekanizma olan veri anlaşması yedekleri etkinleştirmek için özelliği. Daha fazla bilgi için [veri anlaşması yedekleri](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).  
  
 Kullanabileceğiniz `DataContractSerializerOperationBehavior` hem istemci hem de sunucu seri hale getirme özelleştirmek için. Aşağıdaki örnek nasıl gösterir `MaxItemsInObjectGraph` kota istemci üzerinde.  
  
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
  
 Hizmet, şirket içinde barındırılan durumda eşdeğer koda aşağıda verilmiştir.  
  
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
  
 Web barındırılan durumda yeni bir oluşturmalısınız `ServiceHost` türetilmiş bir sınıf ve prize takın için bir hizmet barındırma ortamı fabrikası'nı kullanın.  
  
### <a name="controlling-serialization-settings-in-configuration"></a>Yapılandırmadaki serileştirme ayarlarını denetleme  
 `MaxItemsInObjectGraph` Ve `IgnoreExtensionDataObject` kullanarak yapılandırma aracılığıyla denetlenebilir `dataContractSerializer` uç nokta veya hizmet davranışı, aşağıdaki örnekte gösterildiği gibi.  
  
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
            <endpoint address="http://example.com/myservice"  
                  behaviorConfiguration="LargeQuotaBehavior"  
                binding="basicHttpBinding" bindingConfiguration=""   
                            contract="IDataService"  
                name="" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
### <a name="shared-type-serialization-object-graph-preservation-and-custom-serializers"></a>Paylaşılan türü seri hale getirme, Nesne grafiği korunması ve özel seri hale getiricileri genişletme  
 <xref:System.Runtime.Serialization.DataContractSerializer> Veri sözleşmesi adları ve .NET türü adları kullanarak serileştirir. Bu hizmet odaklı mimari sacayakları ile tutarlıdır ve için önemli ölçüde esneklik sağlar — kablo sözleşme etkilemeden .NET türlerini değiştirebilirsiniz. Nadiren de olsa, gerçek .NET Tür adları, seri hale getirmek böylece istemci ve sunucu, .NET Framework uzaktan iletişimi teknolojisini benzer arasında sıkı bir eşleştirme giriş isteyebilirsiniz. Bu önerilen bir uygulama dışında .NET Framework uzaktan iletişimden WCF'ye taşınma genellikle oluşan nadir durumlarda geçerli değildir. Bu durumda, kullanmalısınız <xref:System.Runtime.Serialization.NetDataContractSerializer> sınıfı yerine <xref:System.Runtime.Serialization.DataContractSerializer> sınıfı.  
  
 <xref:System.Runtime.Serialization.DataContractSerializer> Normalde nesne grafiklerini nesne ağaçları olarak serileştirir. Diğer bir deyişle, aynı nesne birden çok kez başvuruda bulunulur, birden çok kez serileştirildiği. Örneğin, bir `PurchaseOrder` türündeki adresi adlı iki alan içerir örneği `billTo` ve `shipTo`. İki alana da aynı adresi örneğine ayarlarsanız, iki özdeş adres örnekler vardır serileştirme ve seri durumundan çıkarma sonra. XML nesne grafiklerini göstermek için birlikte çalışabilen standart yolu olduğundan bu gerçekleştirilir (eski kodlanmış SOAP standart kullanılabilir dışında <xref:System.Xml.Serialization.XmlSerializer>üzerinde önceki bölümde açıklandığı gibi `Style` ve `Use`). Ağaç olarak nesne grafiklerini serileştirme bazı dezavantajları vardır, örneğin, döngüsel başvurular grafiklerle seri hale getirilemiyor. Bazen, birlikte çalışabilen olmamasına rağmen doğru nesne grafiği seri hale getirme için geçiş gerekli değildir. Bu kullanarak yapılabilir <xref:System.Runtime.Serialization.DataContractSerializer> ile oluşturulan `preserveObjectReferences` parametresini `true`.  
  
 Bazen, yerleşik seri hale getiricileri genişletme senaryonuz için yeterli değildir. Çoğu durumda, kullanmaya devam edebilirsiniz <xref:System.Runtime.Serialization.XmlObjectSerializer> hangi hem Özet <xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Runtime.Serialization.NetDataContractSerializer> türetilir.  
  
 Önceki üç durumları (.NET türü korunması, Nesne grafiği korunması ve tamamen özel `XmlObjectSerializer`-serileştirme tabanlı) tüm, özel bir serileştirici prize takılı gerektirir. Bunu yapmak için şu adımları izleyin:  
  
1.  Kendi davranışını türetme yazma <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>.  
  
2.  İki geçersiz kılma `CreateSerializer` kendi seri hale getirici döndürülecek yöntemleri (ya da <xref:System.Runtime.Serialization.NetDataContractSerializer>, <xref:System.Runtime.Serialization.DataContractSerializer> ile `preserveObjectReferences` kümesine `true`, ya da kendi özel <xref:System.Runtime.Serialization.XmlObjectSerializer>).  
  
3.  Hizmet ana bilgisayarı açma veya istemci kanal oluşturmak önce varolan Kaldır <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> davranışı ve önceki adımlarda oluşturduğunuz özel bir türetilmiş sınıfta takın.  
  
 Gelişmiş serileştirme kavramları hakkında daha fazla bilgi için bkz. [serileştirme ve seri durumundan çıkarma](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XmlSerializer Sınıfını Kullanma](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)
- [Nasıl yapılır: Akışı Etkinleştirme](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)
- [Nasıl yapılır: Bir Sınıf veya Yapı için Temel Bir Veri Sözleşmesi Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
