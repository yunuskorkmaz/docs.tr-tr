---
title: Hizmet Sözleşmelerinde Veri Aktarımını Belirtme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], data transfer
ms.assetid: 7c5a26c8-89c9-4bcb-a4bc-7131e6d01f0c
ms.openlocfilehash: ae05fb5ea0ee4962d9889e2a29399a3913a0d9d5
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600302"
---
# <a name="specifying-data-transfer-in-service-contracts"></a>Hizmet Sözleşmelerinde Veri Aktarımını Belirtme
Windows Communication Foundation (WCF) bir mesajlaşma altyapısı olarak düşünülebilir. Hizmet işlemleri iletileri alabilir, işleyebilir ve iletileri gönderebilir. İletiler, işlem sözleşmeleri kullanılarak açıklanır. Örneğin, aşağıdaki sözleşmeyi göz önünde bulundurun.  
  
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
  
 Burada işlem, `GetAirfare` ve hakkındaki bilgileri içeren bir ileti kabul `fromCity` eder `toCity` ve ardından sayı içeren bir ileti döndürür.  
  
 Bu konu başlığı altında, bir işlem sözleşmesinin iletileri nasıl açıklayabileceği çeşitli yollar açıklanmaktadır.  
  
## <a name="describing-messages-by-using-parameters"></a>Parametreleri kullanarak Iletileri açıklama  
 Bir iletiyi tanımlamanın en kolay yolu bir parametre listesi ve dönüş değeri kullanmaktır. Yukarıdaki örnekte, `fromCity` ve `toCity` dize parametreleri istek iletisini tanımlamakta kullanıldı ve yanıt iletisini anlatmak için float dönüş değeri kullanıldı. Dönüş değeri yalnızca bir yanıt iletisini anlatmak için yeterli değilse, out parametreleri kullanılabilir. Örneğin, aşağıdaki işlem `fromCity` `toCity` kendi istek iletisine sahiptir ve yanıt iletisindeki bir para birimiyle bir sayı ile birlikte bir sayıdır:  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, out string currency);  
```  
  
```vb  
<OperationContract()>  
    Function GetAirfare(fromCity As String, toCity As String) As Double  
```  
  
 Ayrıca, hem isteğin hem de yanıt iletisinin bir parametre parçasını oluşturmak için başvuru parametrelerini kullanabilirsiniz. Parametrelerin serileştirilemiyor (XML 'e dönüştürülebileceğinden) türler olmalıdır. Varsayılan olarak, WCF <xref:System.Runtime.Serialization.DataContractSerializer> bu dönüştürmeyi gerçekleştirmek için sınıfı olarak adlandırılan bir bileşeni kullanır. En basit türler (örneğin,,, `int` `string` `float` ve `DateTime` .) desteklenir. Kullanıcı tanımlı türlerin normalde bir veri anlaşması olması gerekir. Daha fazla bilgi için bkz. [Veri Sözleşmelerini Kullanma](using-data-contracts.md).  
  
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
  
 Bazen, `DataContractSerializer` türlerinizi seri hale getirmek için yeterli değildir. WCF, <xref:System.Xml.Serialization.XmlSerializer> parametreleri seri hale getirmek için de kullanabileceğiniz alternatif bir serileştirme altyapısını destekler. , Gibi <xref:System.Xml.Serialization.XmlSerializer> öznitelikleri kullanarak SONUÇTAKI XML üzerinde daha fazla denetim kullanmanıza olanak sağlar `XmlAttributeAttribute` . <xref:System.Xml.Serialization.XmlSerializer>Öğesini belirli bir işlem için veya tüm hizmet için kullanmak üzere değiştirmek için, <xref:System.ServiceModel.XmlSerializerFormatAttribute> özniteliği bir işleme veya hizmete uygulayın. Örnek:  
  
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
  
 Daha fazla bilgi için, bkz. [XmlSerializer sınıfını kullanma](using-the-xmlserializer-class.md). <xref:System.Xml.Serialization.XmlSerializer>Bu konu başlığı altında ayrıntılı olarak bazı nedenleriniz olmadığı sürece, burada gösterildiği gibi öğesine el ile geçiş yapmayı unutmayın.  
  
 .NET parametre adlarını sözleşme adlarından yalıtmak için, <xref:System.ServiceModel.MessageParameterAttribute> özniteliğini kullanabilir ve `Name` sözleşme adını ayarlamak için özelliğini kullanabilirsiniz. Örneğin, aşağıdaki işlem sözleşmesi, bu konudaki ilk örnekle eşdeğerdir.  
  
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
  
## <a name="describing-empty-messages"></a>Boş Iletileri açıklama  
 Boş bir istek iletisi, hiçbir giriş veya başvuru parametresi olmadan açıklanabilir. Örneğin, C# ' de:  
  
 `[OperationContract]`  
  
 `public int GetCurrentTemperature();`  
  
 Örneğin, Visual Basic:  
  
 `<OperationContract()>`  
  
 `Function GetCurrentTemperature() as Integer`  
  
 Boş bir yanıt iletisi, `void` dönüş türü ve çıkış ya da başvuru parametresi olmadan açıklanabilir. Örneğin:  
  
```csharp  
[OperationContract]  
public void SetTemperature(int temperature);  
```  
  
```vb  
<OperationContract()>  
Sub SetTemperature(temperature As Integer)  
```  
  
 Bu, tek yönlü bir işlemden farklıdır, örneğin:  
  
```csharp  
[OperationContract(IsOneWay=true)]  
public void SetLightbulbStatus(bool isOn);  
```  
  
```vb  
<OperationContract(IsOneWay:=True)>  
Sub SetLightbulbStatus(isOne As Boolean)  
```  
  
 `SetTemperatureStatus`İşlem boş bir ileti döndürüyor. Giriş iletisini işlerken bir sorun oluşursa bunun yerine bir hata döndürebilir. `SetLightbulbStatus`İşlem hiçbir şey döndürmüyor. Bu işlemden bir hata koşulunu iletmenin bir yolu yoktur.  
  
## <a name="describing-messages-by-using-message-contracts"></a>Ileti sözleşmelerini kullanarak Iletileri açıklama  
 Tüm iletiyi göstermek için tek bir tür kullanmak isteyebilirsiniz. Bu amaçla bir veri sözleşmesi kullanmak mümkün olsa da, bunu yapmanın önerilen yolu bir ileti sözleşmesi kullanmaktır; bu, sonuçta elde edilen XML 'de gereksiz kaydırma düzeylerini önler. Ayrıca, ileti sözleşmeleri sonuç iletileri üzerinde daha fazla denetim yapmanıza olanak sağlar. Örneğin, ileti gövdesinde hangi bilgi parçalarının olması gerektiğine ve ileti üstbilgilerinde olması gerektiğine karar verebilirsiniz. Aşağıdaki örnek, ileti sözleşmelerinin kullanımını gösterir.  
  
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
  
 Daha fazla bilgi için bkz. [Ileti sözleşmelerini kullanma](using-message-contracts.md).  
  
 Önceki örnekte, <xref:System.Runtime.Serialization.DataContractSerializer> sınıf varsayılan olarak hala kullanılmaktadır. <xref:System.Xml.Serialization.XmlSerializer>Sınıf, ileti sözleşmeleri ile de kullanılabilir. Bunu yapmak için, <xref:System.ServiceModel.XmlSerializerFormatAttribute> özniteliği işlem ya da sözleşmeye uygulayın ve <xref:System.Xml.Serialization.XmlSerializer> ileti üstbilgilerinde ve gövde üyelerinde sınıfıyla uyumlu türleri kullanın.  
  
## <a name="describing-messages-by-using-streams"></a>Akışları kullanarak Iletileri açıklama  
 İşlemler içindeki iletileri tanımlamanın bir başka yolu da bir <xref:System.IO.Stream> işlem sözleşmesindeki veya bir ileti sözleşmesi gövde üyesi olarak ya da bir ileti sözleşme gövdesi üyesi olarak türetilmiş sınıflarından birini ya da bir ileti sözleşmesi gövde üyesini (Bu durumda tek üye olmalıdır) kullanmaktır. Gelen iletilerde, türün olması gerekir; `Stream` türetilmiş sınıfları kullanamazsınız.  
  
 WCF, seri hale getirici 'yi çağırmak yerine bir akıştan veri alır ve bunu doğrudan giden bir iletiye koyar veya gelen iletiden veri alıp doğrudan bir akışa koyar. Aşağıdaki örnek, akışlarının kullanımını gösterir.  
  
```csharp  
[OperationContract]  
public Stream DownloadFile(string fileName);  
```  
  
```vb  
<OperationContract()>  
Function DownloadFile(fileName As String) As String  
```  
  
 `Stream`Tek bir ileti gövdesinde verileri birleştiremezsiniz ve akış dışı olamaz. İleti üstbilgilerinde ek verileri yerleştirmek için bir ileti sözleşmesi kullanın. Aşağıdaki örnek, işlem sözleşmesini tanımlarken akış kullanımının yanlış kullanımını gösterir.  
  
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
  
 Aşağıdaki örnek, bir işlem anlaşması tanımlarken akışlarının doğru kullanımını gösterir.  
  
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
  
 Daha fazla bilgi için bkz. [büyük veri ve akış](large-data-and-streaming.md).  
  
## <a name="using-the-message-class"></a>İleti Sınıfını Kullanma  
 Gönderilen veya alınan iletiler üzerinde tamamen programlı denetim sağlamak için, <xref:System.ServiceModel.Channels.Message> Aşağıdaki örnek kodda gösterildiği gibi, sınıfını doğrudan kullanabilirsiniz.  
  
```csharp  
[OperationContract]  
public void LogMessage(Message m);  
```  
  
```vb  
<OperationContract()>  
Sub LogMessage(m As Message)  
```  
  
 Bu, [Ileti sınıfını kullanma](using-the-message-class.md)konusunda ayrıntılı olarak açıklanan gelişmiş bir senaryodur.  
  
## <a name="describing-fault-messages"></a>Hata Iletilerini açıklama  
 Dönüş değeri ve çıkış ya da başvuru parametreleri tarafından tanımlanan iletilere ek olarak, tek yönlü olmayan tüm işlemler en az iki olası ileti döndürebilir: normal yanıt iletisi ve bir hata iletisi. Aşağıdaki işlem sözleşmesini göz önünde bulundurun.  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, DateTime date);  
```  
  
```vb  
<OperationContract()>  
Function GetAirfare(fromCity As String, toCity As String, date as DateTime)  
```  
  
 Bu işlem sayı içeren bir normal ileti `float` ya da hata kodu ve açıklama içeren bir hata iletisi döndürebilir. Bunu, hizmet uygulamanızda bir oluşturarak gerçekleştirebilirsiniz <xref:System.ServiceModel.FaultException> .  
  
 Özniteliğini kullanarak, olası hata iletileri belirtebilirsiniz <xref:System.ServiceModel.FaultContractAttribute> . Aşağıdaki örnek kodda gösterildiği gibi ek hataların kullanılarak seri hale getirilebilir olması gerekir <xref:System.Runtime.Serialization.DataContractSerializer> .  
  
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
  
 Bu ek hatalar, <xref:System.ServiceModel.FaultException%601> uygun veri sözleşmesi türünün bir kopyası çalıştırılarak oluşturulabilir. Daha fazla bilgi için bkz. [özel durumları ve hataları işleme](../extending/handling-exceptions-and-faults.md).  
  
 <xref:System.Xml.Serialization.XmlSerializer>Hataları anlatmak için sınıfını kullanamazsınız. , <xref:System.ServiceModel.XmlSerializerFormatAttribute> Hata sözleşmeleri üzerinde hiçbir etkiye sahip değildir.  
  
## <a name="using-derived-types"></a>Türetilmiş türleri kullanma  
 Bir işlemde veya bir ileti sözleşmesinde temel tür kullanmak ve ardından işlemi çağırırken türetilmiş bir tür kullanmak isteyebilirsiniz. Bu durumda, <xref:System.ServiceModel.ServiceKnownTypeAttribute> türetilmiş türlerin kullanılmasına izin vermek için özniteliği veya bazı alternatif mekanizmayı kullanmanız gerekir. Aşağıdaki işlemi göz önünde bulundurun.  
  
```csharp  
[OperationContract]  
public bool IsLibraryItemAvailable(LibraryItem item);  
```  
  
```vb
<OperationContract()>  
    Function IsLibraryItemAvailable(item As LibraryItem) As Boolean  
```  
  
 İki türün `Book` ve `Magazine` , öğesinden türet olduğunu varsayalım `LibraryItem` . Bu türleri işlem içinde kullanmak için `IsLibraryItemAvailable` , işlemi aşağıdaki şekilde değiştirebilirsiniz:  
  
 `[OperationContract]`  
  
 `[ServiceKnownType(typeof(Book))]`  
  
 `[ServiceKnownType(typeof(Magazine))]`  
  
 `public bool IsLibraryItemAvailable(LibraryItem item);`  
  
 Alternatif olarak, <xref:System.Runtime.Serialization.KnownTypeAttribute> <xref:System.Runtime.Serialization.DataContractSerializer> Aşağıdaki örnek kodda gösterildiği gibi, varsayılan kullanımda olduğunda özniteliğini kullanabilirsiniz.  
  
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
  
 <xref:System.Xml.Serialization.XmlIncludeAttribute>Kullanırken özniteliğini kullanabilirsiniz <xref:System.Xml.Serialization.XmlSerializer> .  
  
 <xref:System.ServiceModel.ServiceKnownTypeAttribute>Özniteliği bir işleme veya tüm hizmete uygulayabilirsiniz. Özniteliği gibi bilinen türlerin bir listesini almak için çağrılacak yöntemin türünü ya da adını kabul eder <xref:System.Runtime.Serialization.KnownTypeAttribute> . Daha fazla bilgi için bkz. [veri sözleşmesi bilinen türleri](data-contract-known-types.md).  
  
## <a name="specifying-the-use-and-style"></a>Kullanımı ve stili belirtme  
 Web Hizmetleri Açıklama Dili (WSDL) kullanarak hizmetleri açıkladığınızda, yaygın olarak kullanılan iki stil belge ve uzak yordam çağrısı (RPC) ' dir. Belge stilinde, tüm ileti gövdesi şema kullanılarak tanımlanır ve WSDL, bu şema içindeki öğelere başvurarak çeşitli ileti gövdesi parçalarını açıklar. RPC stilinde, WSDL bir öğesi yerine her ileti bölümü için bir şema türü anlamına gelir. Bazı durumlarda, bu stillerden birini el ile seçmeniz gerekir. Bu işlemi, <xref:System.ServiceModel.DataContractFormatAttribute> özniteliği uygulayıp `Style` özelliği ayarlayarak (kullanırken <xref:System.Runtime.Serialization.DataContractSerializer> ) veya özniteliği üzerinde ayarını yaparak yapabilirsiniz `Style` <xref:System.ServiceModel.XmlSerializerFormatAttribute> <xref:System.Xml.Serialization.XmlSerializer> .  
  
 Ayrıca, <xref:System.Xml.Serialization.XmlSerializer> iki seri hale GETIRILMIŞ XML biçimini destekler: `Literal` ve `Encoded` . `Literal`en yaygın olarak kabul edilen formdur ve desteklediği tek formdur <xref:System.Runtime.Serialization.DataContractSerializer> . `Encoded`, SOAP belirtiminin 5. bölümünde açıklanan eski bir formdur ve yeni hizmetler için önerilmez. Moda geçmek için `Encoded` , `Use` <xref:System.ServiceModel.XmlSerializerFormatAttribute> özniteliğinde özelliğini olarak ayarlayın `Encoded` .  
  
 Çoğu durumda, ve özellikleri için varsayılan ayarları değiştirmemelisiniz `Style` `Use` .  
  
## <a name="controlling-the-serialization-process"></a>Serileştirme Işlemini denetleme  
 Verilerin serileştirilme şeklini özelleştirmek için çeşitli şeyler yapabilirsiniz.  
  
### <a name="changing-server-serialization-settings"></a>Sunucu serileştirme ayarlarını değiştirme  
 Varsayılan kullanımda olduğunda <xref:System.Runtime.Serialization.DataContractSerializer> , hizmetine özniteliği uygulayarak serileştirme işleminin bazı yönlerini kontrol edebilirsiniz <xref:System.ServiceModel.ServiceBehaviorAttribute> . Özellikle, seri hale getirilen `MaxItemsInObjectGraph` en fazla nesne sayısını sınırlayan kotayı ayarlamak için özelliğini kullanabilirsiniz <xref:System.Runtime.Serialization.DataContractSerializer> . `IgnoreExtensionDataObject`Özelliği, gidiş yuvarlama sürümü özelliğini devre dışı bırakmak için kullanabilirsiniz. Kotalar hakkında daha fazla bilgi için bkz. [veriler Için güvenlik konuları](security-considerations-for-data.md). Gidiş dönüşü hakkında daha fazla bilgi için bkz. [Forward-uyumlu veri sözleşmeleri](forward-compatible-data-contracts.md).  
  
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
 WCF 'de iki davranış mevcuttur, ve, <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> belirli bir işlem için hangi seri hale getiricinin kullanımda olduğuna bağlı olarak otomatik olarak takılır. Bu davranışlar otomatik olarak uygulandığından, normalde bunların farkında olmanız gerekmez.  
  
 Ancak, `DataContractSerializerOperationBehavior` `MaxItemsInObjectGraph` `IgnoreExtensionDataObject` `DataContractSurrogate` serileştirme işlemini özelleştirmek için kullanabileceğiniz, ve özelliklerini içerir. İlk iki özellik, önceki bölümde açıklanan anlama sahiptir. `DataContractSurrogate`Özelliği, serileştirme işlemini özelleştirmek ve genişletmek için güçlü bir mekanizma olan veri sözleşmesi yedekleri 'ni etkinleştirmek için kullanabilirsiniz. Daha fazla bilgi için bkz. [veri sözleşmesi yedeklerin kapıları](../extending/data-contract-surrogates.md).  
  
 `DataContractSerializerOperationBehavior`Hem istemci hem de sunucu serileştirmesini özelleştirmek için kullanabilirsiniz. Aşağıdaki örnek, istemci üzerindeki kotanın nasıl arttıralınacağını göstermektedir `MaxItemsInObjectGraph` .  
  
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
  
Şirket içinde barındırılan durumda, hizmette eşdeğer kod aşağıda verilmiştir:
  
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
  
 Web 'de barındırılan bir durumda, yeni bir `ServiceHost` türetilmiş sınıf oluşturmanız ve bir hizmet ana bilgisayar fabrikası kullanarak içine takabilirsiniz.  
  
### <a name="controlling-serialization-settings-in-configuration"></a>Yapılandırmada serileştirme ayarlarını denetleme  
 `MaxItemsInObjectGraph`Ve, `IgnoreExtensionDataObject` `dataContractSerializer` Aşağıdaki örnekte gösterildiği gibi, uç nokta veya hizmet davranışı kullanılarak yapılandırma yoluyla denetlenebilirler.  
  
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
  
### <a name="shared-type-serialization-object-graph-preservation-and-custom-serializers"></a>Paylaşılan tür serileştirme, nesne grafik koruma ve özel serileştiriciler  
 <xref:System.Runtime.Serialization.DataContractSerializer>Veri sözleşmesi adlarını kullanarak seri hale getirir ve .net tür adları değildir. Bu, hizmet odaklı mimari olanakları ile tutarlıdır ve harika bir esneklik sağlar; .NET türleri, Tel sözleşmeyi etkilemeden değişebilir. Nadir durumlarda, gerçek .NET tür adlarını seri hale getirmek isteyebilirsiniz ve bu sayede istemci ile sunucu arasında sıkı bir şekilde iletişim kurarak, .NET Framework Remoting teknolojisine benzer. Bu, genellikle .NET Framework uzaktan iletişim 'dan WCF 'ye geçiş yapılırken oluşan nadir durumlar dışında, önerilen bir uygulama değildir. Bu durumda, sınıfı yerine sınıfını kullanmanız gerekir <xref:System.Runtime.Serialization.NetDataContractSerializer> <xref:System.Runtime.Serialization.DataContractSerializer> .  
  
 <xref:System.Runtime.Serialization.DataContractSerializer>Normalde nesne grafiklerini nesne ağaçları olarak serileştirir. Diğer bir deyişle, aynı nesneye birden çok kez bahsedildiğinde birden çok kez serileştirilir. Örneğin, `PurchaseOrder` adresi ve adı Address olan iki alanı olan bir örneği göz önünde `billTo` bulundurun `shipTo` . Her iki alan de aynı adres örneğine ayarlanmışsa serileştirme ve serisini kaldırma sonrasında iki özdeş adres örneği vardır. Bu, XML 'deki nesne grafiklerini temsil etmek için standart birlikte çalışabilen bir yol olmadığından ( <xref:System.Xml.Serialization.XmlSerializer> ve üzerinde önceki bölümde açıklandığı gibi, üzerinde bulunan eskı SOAP kodlamalı standart dışında), bu yapılır `Style` `Use` . Ağaç olarak nesne grafiklerinin serileştirilmesi, örneğin döngüsel başvuruları olan grafikler serileştirilemiyor. Bazen, birlikte çalışabilir olmasa bile, doğru nesne grafiği serileştirmesine geçiş yapmak gerekir. Bu, <xref:System.Runtime.Serialization.DataContractSerializer> `preserveObjectReferences` olarak ayarlanan parametresiyle oluşturulan kullanılarak yapılabilir `true` .  
  
 Bazen, yerleşik serileştiriciler senaryonuz için yeterli değildir. Çoğu durumda, hem hem de <xref:System.Runtime.Serialization.XmlObjectSerializer> türeten olan soyutlamayı kullanmaya devam edebilirsiniz <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.NetDataContractSerializer> .  
  
 Önceki üç durum (.NET tür koruma, nesne Graph koruması ve tamamen özel `XmlObjectSerializer` tabanlı serileştirme), hepsi özel bir seri hale getirici takılmasına gerek duyar. Bunu yapmak için şu adımları izleyin:  
  
1. Öğesinden türetilen kendi davranışınızı yazın <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> .  
  
2. `CreateSerializer`Kendi seri hale getirinizi (ya da <xref:System.Runtime.Serialization.NetDataContractSerializer> <xref:System.Runtime.Serialization.DataContractSerializer> `preserveObjectReferences` `true` kendi özel olarak ayarlanan <xref:System.Runtime.Serialization.XmlObjectSerializer> ) döndürmek için iki yöntemi geçersiz kılın.  
  
3. Hizmet konağını açmadan veya bir istemci kanalı oluşturmadan önce, mevcut <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> davranışı kaldırın ve önceki adımlarda oluşturduğunuz özel türetilmiş sınıfı takın.  
  
 Gelişmiş serileştirme kavramları hakkında daha fazla bilgi için bkz. [serileştirme ve seri durumundan çıkarma](serialization-and-deserialization.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XmlSerializer Sınıfını Kullanma](using-the-xmlserializer-class.md)
- [Nasıl yapılır: Akışı Etkinleştirme](how-to-enable-streaming.md)
- [Nasıl yapılır: Bir Sınıf veya Yapı için Temel Bir Veri Sözleşmesi Oluşturma](how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
