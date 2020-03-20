---
title: Hizmet Sözleşmelerinde Veri Aktarımını Belirtme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], data transfer
ms.assetid: 7c5a26c8-89c9-4bcb-a4bc-7131e6d01f0c
ms.openlocfilehash: e68ca46f9d2c562491063ae66754c469dbe0898e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184435"
---
# <a name="specifying-data-transfer-in-service-contracts"></a>Hizmet Sözleşmelerinde Veri Aktarımını Belirtme
Windows Communication Foundation (WCF) bir mesajlaşma altyapısı olarak düşünülebilir. Hizmet işlemleri iletileri alabilir, işleyebilir ve ileti gönderebilir. İletiler işlem sözleşmeleri kullanılarak tanımlanır. Örneğin, aşağıdaki sözleşmeyi göz önünde bulundurun.  
  
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
  
 Burada, `GetAirfare` işlem hakkında `fromCity` bilgi içeren bir `toCity`iletiyi kabul eder ve sonra bir sayı içeren bir iletiyi döndürür.  
  
 Bu konu, bir işlem sözleşmesinin iletileri açıklayabileceği çeşitli yolları açıklar.  
  
## <a name="describing-messages-by-using-parameters"></a>Parametreleri Kullanarak İletileri Açıklama  
 İletiyi açıklamanın en basit yolu parametre listesi ve iade değeri kullanmaktır. Önceki örnekte, istek `fromCity` `toCity` iletisini tanımlamak için ve dize parametreleri kullanıldı ve yanıt iletisini açıklamak için float return value kullanıldı. Tek başına iade değeri bir yanıt iletisini açıklamak için yeterli değilse, çıkış parametreleri kullanılabilir. Örneğin, aşağıdaki işlem `fromCity` ve `toCity` istek iletisinde ve yanıt iletisinde para birimiyle birlikte bir sayı vardır:  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, out string currency);  
```  
  
```vb  
<OperationContract()>  
    Function GetAirfare(fromCity As String, toCity As String) As Double  
```  
  
 Ayrıca, hem isteğin hem de yanıt iletisinin parametre parçasını yapmak için başvuru parametrelerini kullanabilirsiniz. Parametreler serihale edilebilen (XML'e dönüştürülebilen) türlerden olmalıdır. Varsayılan olarak, WCF bu <xref:System.Runtime.Serialization.DataContractSerializer> dönüşümü gerçekleştirmek için sınıf adlı bir bileşen kullanır. Çoğu ilkel tür `int`(, `float`, `DateTime` `string`, ve .) desteklenir. Kullanıcı tanımlı türlerin normalde bir veri sözleşmesi olmalıdır. Daha fazla bilgi için [bkz.](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
  
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
  
 Bazen, türlerinizi seri hale getirmek için yeterli `DataContractSerializer` değildir. WCF alternatif bir serileştirme <xref:System.Xml.Serialization.XmlSerializer>motoru destekler, , ayrıca parametreleri serileştirmek için kullanabilirsiniz. Bu <xref:System.Xml.Serialization.XmlSerializer> gibi öznitelikleri kullanarak ortaya çıkan XML üzerinde `XmlAttributeAttribute`daha fazla kontrol kullanmanıza olanak sağlar. Belirli bir işlem <xref:System.Xml.Serialization.XmlSerializer> için veya tüm hizmet için kullanmaya <xref:System.ServiceModel.XmlSerializerFormatAttribute> geçmek için, özniteliği bir işlem veya hizmetiçin uygulayın. Örnek:  
  
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
  
 Daha fazla bilgi için Bkz. [XmlSerializer Sınıfını Kullanma.](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md) Bu konuda ayrıntılı olarak <xref:System.Xml.Serialization.XmlSerializer> ayrıntılı olarak bunu yapmak için özel nedenler yoksa burada gösterildiği gibi el ile geçiş tavsiye edilmez unutmayın.  
  
 .NET parametre adlarını sözleşme adlarından yalıtmak için özniteliği kullanabilir <xref:System.ServiceModel.MessageParameterAttribute> ve sözleşme adını ayarlamak için `Name` özelliği kullanabilirsiniz. Örneğin, aşağıdaki işlem sözleşmesi bu konudaki ilk örneğe eşdeğerdir.  
  
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
  
## <a name="describing-empty-messages"></a>Boş İletileri Açıklama  
 Boş bir istek iletisi, giriş veya başvuru parametreleri olmadan açıklanabilir. Örneğin, C#'da:  
  
 `[OperationContract]`  
  
 `public int GetCurrentTemperature();`  
  
 Örneğin, Visual Basic'te:  
  
 `<OperationContract()>`  
  
 `Function GetCurrentTemperature() as Integer`  
  
 Boş bir `void` yanıt iletisi, bir iade türüne sahip olarak açıklanabilir ve çıktı veya başvuru parametreleri yoktur. Örneğin:  
  
```csharp  
[OperationContract]  
public void SetTemperature(int temperature);  
```  
  
```vb  
<OperationContract()>  
Sub SetTemperature(temperature As Integer)  
```  
  
 Bu, tek yönlü bir işlemden farklıdır:  
  
```csharp  
[OperationContract(IsOneWay=true)]  
public void SetLightbulbStatus(bool isOn);  
```  
  
```vb  
<OperationContract(IsOneWay:=True)>  
Sub SetLightbulbStatus(isOne As Boolean)  
```  
  
 İşlem `SetTemperatureStatus` boş bir ileti döndürür. Giriş iletisini işlerken bir sorun varsa, bunun yerine bir hata döndürebilir. Operasyon `SetLightbulbStatus` hiçbir şey döndürür. Bu işlemden kaynaklanan bir hata durumunu iletmenin bir yolu yoktur.  
  
## <a name="describing-messages-by-using-message-contracts"></a>İleti Sözleşmelerini Kullanarak İletileri Açıklama  
 İletinin tamamını temsil etmek için tek bir tür kullanmak isteyebilirsiniz. Bu amaçla bir veri sözleşmesi kullanmak mümkün olsa da, bunu yapmanın önerilen yolu bir ileti sözleşmesi kullanmaktır—bu, ortaya çıkan XML'de gereksiz kaydırma düzeylerini önler. Ayrıca, ileti sözleşmeleri, ortaya çıkan iletiler üzerinde daha fazla denetim uygulamanıza olanak sağlar. Örneğin, ileti gövdesinde hangi bilgilerin ve hangilerinin ileti üstbilgilerinde olması gerektiğine karar verebilirsiniz. Aşağıdaki örnek, ileti sözleşmelerinin kullanımını gösterir.  
  
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
  
 Daha fazla bilgi için [İleti Sözleşmelerini Kullanma'ya](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)bakın.  
  
 Önceki örnekte, <xref:System.Runtime.Serialization.DataContractSerializer> sınıf yine varsayılan olarak kullanılır. Sınıf <xref:System.Xml.Serialization.XmlSerializer> ileti sözleşmeleri ile de kullanılabilir. Bunu yapmak için, <xref:System.ServiceModel.XmlSerializerFormatAttribute> özniteliği işlem veya sözleşmeye uygulayın ve <xref:System.Xml.Serialization.XmlSerializer> ileti üstbilgilerinde ve gövde üyelerindeki sınıfla uyumlu türleri kullanın.  
  
## <a name="describing-messages-by-using-streams"></a>Akışları Kullanarak İletileri Açıklama  
 İşlemlerde iletileri açıklamanın başka bir <xref:System.IO.Stream> yolu da sınıfı veya türetilmiş sınıflarından birini bir işlem sözleşmesinde veya ileti sözleşmesi gövdesi üyesi olarak kullanmaktır (bu durumda tek üye olmalıdır). Gelen iletiler için tür `Stream`,türetilmiş sınıfları kullanamazsınız olmalıdır.  
  
 WCF, serilaştırıcıyı çağırmak yerine, bir akıştan veri alır ve doğrudan giden bir iletiye koyar veya gelen bir iletiden veri alır ve doğrudan bir akışa koyar. Aşağıdaki örnek, akışların kullanımını gösterir.  
  
```csharp  
[OperationContract]  
public Stream DownloadFile(string fileName);  
```  
  
```vb  
<OperationContract()>  
Function DownloadFile(fileName As String) As String  
```  
  
 Tek bir `Stream` ileti gövdesinde verileri birleştiremezsiniz ve akış dışı verileri birleştiremezsiniz. İleti üstbilgilerine ek verileri koymak için bir ileti sözleşmesi kullanın. Aşağıdaki örnek, işlem sözleşmesini tanımlarken akışların yanlış kullanımını gösterir.  
  
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
  
 Aşağıdaki örnek, bir işlem sözleşmesi tanımlarken akışların doğru kullanımını gösterir.  
  
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
  
 Daha fazla bilgi için [Bkz. Büyük Veri ve Akış.](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)  
  
## <a name="using-the-message-class"></a>İleti Sınıfını Kullanma  
 Gönderilen veya alınan iletiler üzerinde tam programlı denetime sahip olmak için, aşağıdaki örnek kodda gösterildiği gibi <xref:System.ServiceModel.Channels.Message> sınıfı doğrudan kullanabilirsiniz.  
  
```csharp  
[OperationContract]  
public void LogMessage(Message m);  
```  
  
```vb  
<OperationContract()>  
Sub LogMessage(m As Message)  
```  
  
 Bu, [İleti Sınıfı'nı kullanırken](../../../../docs/framework/wcf/feature-details/using-the-message-class.md)ayrıntılı olarak açıklanan gelişmiş bir senaryodur.  
  
## <a name="describing-fault-messages"></a>Hata İletilerini Açıklama  
 İade değeri ve çıktı veya başvuru parametreleri tarafından açıklanan iletilere ek olarak, tek yönlü olmayan herhangi bir işlem en az iki olası ileti döndürebilir: normal yanıt iletisi ve hata iletisi. Aşağıdaki işlem sözleşmesini göz önünde bulundurun.  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, DateTime date);  
```  
  
```vb  
<OperationContract()>  
Function GetAirfare(fromCity As String, toCity As String, date as DateTime)  
```  
  
 Bu işlem, bir sayı içeren `float` normal bir ileti veya bir hata kodu ve açıklama içeren bir hata iletisi döndürebilir. Bunu, hizmet uygulamanızda <xref:System.ServiceModel.FaultException> bir atarak başarabilirsiniz.  
  
 Özniteliği kullanarak <xref:System.ServiceModel.FaultContractAttribute> ek olası hata iletileri belirtebilirsiniz. Ek <xref:System.Runtime.Serialization.DataContractSerializer>hatalar, aşağıdaki örnek kodda gösterildiği gibi , kullanılarak serileştirilebilir olmalıdır.  
  
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
  
 Bu ek hatalar, uygun veri <xref:System.ServiceModel.FaultException%601> sözleşmesi türünden bir hata atılarak oluşturulabilir. Daha fazla bilgi için [bkz.](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)  
  
 Hataları açıklamak <xref:System.Xml.Serialization.XmlSerializer> için sınıfı kullanamazsınız. Hata <xref:System.ServiceModel.XmlSerializerFormatAttribute> sözleşmeleri üzerinde hiçbir etkisi yoktur.  
  
## <a name="using-derived-types"></a>Türemiş Türleri Kullanma  
 Bir işlemde veya ileti sözleşmesinde bir temel türü kullanmak ve ardından işlemi gerçekten çağırırken türetilmiş bir tür kullanmak isteyebilirsiniz. Bu durumda, türemiş <xref:System.ServiceModel.ServiceKnownTypeAttribute> türlerin kullanımına izin vermek için öznitelik veya bazı alternatif mekanizma kullanmanız gerekir. Aşağıdaki işlemi göz önünde bulundurun.  
  
```csharp  
[OperationContract]  
public bool IsLibraryItemAvailable(LibraryItem item);  
```  
  
```vb
<OperationContract()>  
    Function IsLibraryItemAvailable(item As LibraryItem) As Boolean  
```  
  
 Varsayalım ki `Book` iki `Magazine`tür, `LibraryItem`ve , türetilmiştir . `IsLibraryItemAvailable` Bu tür işlemleri kullanmak için işlemi aşağıdaki gibi değiştirebilirsiniz:  
  
 `[OperationContract]`  
  
 `[ServiceKnownType(typeof(Book))]`  
  
 `[ServiceKnownType(typeof(Magazine))]`  
  
 `public bool IsLibraryItemAvailable(LibraryItem item);`  
  
 Alternatif olarak, aşağıdaki <xref:System.Runtime.Serialization.KnownTypeAttribute> örnek kodda <xref:System.Runtime.Serialization.DataContractSerializer> gösterildiği gibi, varsayılan kullanımda özniteliği kullanabilirsiniz.  
  
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
  
 Özniteliği kullanırken <xref:System.Xml.Serialization.XmlIncludeAttribute> <xref:System.Xml.Serialization.XmlSerializer>kullanabilirsiniz.  
  
 Özniteliği bir <xref:System.ServiceModel.ServiceKnownTypeAttribute> işlemiçin veya tüm hizmete uygulayabilirsiniz. Öznitelik gibi <xref:System.Runtime.Serialization.KnownTypeAttribute> bilinen türlerin listesini almak için aramak için bir tür veya yöntemin adını kabul eder. Daha fazla bilgi için [bkz.](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
  
## <a name="specifying-the-use-and-style"></a>Kullanım ve Stil belirtme  
 Web Hizmetleri Açıklama Dili (WSDL) kullanarak hizmetleri açıklarken, sık kullanılan iki stil Belge ve uzak yordam çağrısı (RPC) olur. Belge stilinde, tüm ileti gövdesi şema kullanılarak tanımlanır ve WSDL, bu şemadaki öğelere atıfta bulunarak çeşitli ileti gövdesi parçalarını açıklar. RPC stilinde, WSDL bir öğe yerine her ileti parçası için bir şema türü anlamına gelir. Bazı durumlarda, bu stillerden birini el ile seçmeniz gerekir. Bunu, özniteliği uygulayarak <xref:System.ServiceModel.DataContractFormatAttribute> ve `Style` özelliği ayarlayarak (kullanımda olduğunda) <xref:System.Runtime.Serialization.DataContractSerializer> veya `Style` <xref:System.ServiceModel.XmlSerializerFormatAttribute> özniteliği ayarlayarak (kullanırken) <xref:System.Xml.Serialization.XmlSerializer>yapabilirsiniz.  
  
 Ayrıca, serixml iki form <xref:System.Xml.Serialization.XmlSerializer> destekler: `Literal` `Encoded`ve . `Literal`en yaygın olarak kabul edilen formdur ve <xref:System.Runtime.Serialization.DataContractSerializer> tek form destekler. `Encoded`SOAP belirtiminin bölüm 5'inde açıklanan eski bir formdur ve yeni hizmetler için önerilmez. Moda geçmek `Encoded` için özelliği `Use` öznitelikte <xref:System.ServiceModel.XmlSerializerFormatAttribute> ' `Encoded`ye ayarlayın.  
  
 Çoğu durumda, ve `Style` `Use` özellikleri için varsayılan ayarları değiştirmemelisiniz.  
  
## <a name="controlling-the-serialization-process"></a>Serileştirme İşlemini Denetleme  
 Verilerin seri hale getiriş biçimini özelleştirmek için bir dizi şey yapabilirsiniz.  
  
### <a name="changing-server-serialization-settings"></a>Sunucu Serileştirme Ayarlarını Değiştirme  
 Varsayılan <xref:System.Runtime.Serialization.DataContractSerializer> kullanımda yken, hizmete öznitelik uygulayarak <xref:System.ServiceModel.ServiceBehaviorAttribute> hizmetteki serileştirme işleminin bazı yönlerini denetleyebilirsiniz. Özellikle, <xref:System.Runtime.Serialization.DataContractSerializer> deserialize `MaxItemsInObjectGraph` nesnelerin maksimum sayısını sınırlayan kota ayarlamak için özelliği kullanabilirsiniz. Yuvarlak tripping `IgnoreExtensionDataObject` sürüm özelliğini kapatmak için özelliği kullanabilirsiniz. Kotalar hakkında daha fazla bilgi için, [Veriler için Güvenlik Hususları'na](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)bakın. Yuvarlama hakkında daha fazla bilgi için [İleri Uyumlu Veri Sözleşmeleri'ne](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)bakın.  
  
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
  
### <a name="serialization-behaviors"></a>Serileştirme Davranışları  
 WCF'de, <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> belirli bir işlem için hangi serileştiricinin kullanıldığına bağlı olarak otomatik olarak takılı olan iki davranış mevcuttur. Bu davranışlar otomatik olarak uygulandığından, normalde bunların farkında olmak zorunda değildir.  
  
 Ancak, `DataContractSerializerOperationBehavior` serileştirme `MaxItemsInObjectGraph` `IgnoreExtensionDataObject`işlemini `DataContractSurrogate` özelleştirmek için kullanabileceğiniz , ve özellikleri vardır. İlk iki özellik önceki bölümde tartışılan aynı anlama sahiptir. Serileştirme işlemini `DataContractSurrogate` özelleştirmek ve genişletmek için güçlü bir mekanizma olan veri sözleşmesi vekillerini etkinleştirmek için özelliği kullanabilirsiniz. Daha fazla bilgi için [Bkz. Veri Sözleşmesi Suretleri.](../../../../docs/framework/wcf/extending/data-contract-surrogates.md)  
  
 Hem istemci `DataContractSerializerOperationBehavior` hem de sunucu serileştirmesini özelleştirmek için kullanabilirsiniz. Aşağıdaki örnek, istemcideki `MaxItemsInObjectGraph` kotanın nasıl artırılabildiğini gösterir.  
  
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
  
Aşağıda, kendi barındırılan durumda, hizmetteki eşdeğer kod veeşdeğer kod vereb vardır:
  
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
  
 Web tarafından barındırılan durumda, yeni `ServiceHost` bir türetilmiş sınıf oluşturmanız ve bunu takmak için bir hizmet ana bilgisayar fabrikası kullanmanız gerekir.  
  
### <a name="controlling-serialization-settings-in-configuration"></a>Yapılandırmada Serileştirme Ayarlarını Denetleme  
 Ve `MaxItemsInObjectGraph` `IgnoreExtensionDataObject` aşağıdaki örnekte gösterildiği `dataContractSerializer` gibi, bitiş noktası veya hizmet davranışı kullanılarak yapılandırma yoluyla denetlenebilir.  
  
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
  
### <a name="shared-type-serialization-object-graph-preservation-and-custom-serializers"></a>Paylaşılan Tür Serileştirme, Nesne Grafiği Koruma ve Özel Serializers  
 Seri, <xref:System.Runtime.Serialization.DataContractSerializer> .NET türü adlarını değil, veri sözleşme adlarını kullanarak serihale eder. Bu, hizmet odaklı mimari ilkeleriyle tutarlıdır ve büyük ölçüde esneklik sağlar—.NET türleri tel sözleşmesini etkilemeden değişebilir. Nadir durumlarda, gerçek .NET türü adlarını seri hale getirmek, böylelikle istemci ve sunucu arasında .NET Framework remoting teknolojisine benzer sıkı bir bağlantı sağlamak isteyebilirsiniz. Bu, genellikle .NET Framework remoting'den WCF'ye geçiş yaparken meydana gelen nadir durumlar dışında önerilen bir uygulama değildir. Bu durumda, <xref:System.Runtime.Serialization.NetDataContractSerializer> <xref:System.Runtime.Serialization.DataContractSerializer> sınıf yerine sınıfı kullanmanız gerekir.  
  
 Normalde <xref:System.Runtime.Serialization.DataContractSerializer> nesne grafiklerini nesne ağaçları olarak serihale eder. Diğer bir yerde, aynı nesneye birden çok kez atıfta bulunulması durumunda, birden çok kez seri hale getirilir. Örneğin, tür `PurchaseOrder` Adresi adlı `billTo` iki alan ait `shipTo`bir örnek düşünün ve . Her iki alan da aynı Adres örneğine ayarlanmışsa, serileştirme ve deserialization sonra iki özdeş Adres örnekleri vardır. XML'deki nesne grafiklerini temsil etmenin standart bir birlikte çalışabilir yolu olmadığı için bu işlem yapılır <xref:System.Xml.Serialization.XmlSerializer>(önceki bölümde `Style` açıklandığı gibi, eski SOAP kodlanmış standart `Use`dışında). Nesne grafiklerini ağaç olarak serihale getirmenin belirli dezavantajları vardır, örneğin dairesel referanslı grafikler serileştirilemez. Bazen, birlikte çalışabilir olmasa bile gerçek nesne grafiği serileştirme geçmek gerekir. Bu <xref:System.Runtime.Serialization.DataContractSerializer> `preserveObjectReferences` parametre kümesi ile inşa kullanılarak `true`yapılabilir.  
  
 Bazen, yerleşik serializers senaryonuz için yeterli değildir. Çoğu durumda, hala hem <xref:System.Runtime.Serialization.XmlObjectSerializer> de <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.NetDataContractSerializer> türetilmiştir soyutlama kullanabilirsiniz.  
  
 Önceki üç durumda (.NET türü koruma, nesne `XmlObjectSerializer`grafiği koruma ve tamamen özel tabanlı serileştirme) tüm özel bir serializer takılı gerektirir. Bunu yapmak için şu adımları izleyin:  
  
1. Kendi davranışınızı <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>yazın.  
  
2. Kendi serializer dönmek için `CreateSerializer` iki yöntem geçersiz <xref:System.Runtime.Serialization.NetDataContractSerializer>kılın <xref:System.Runtime.Serialization.DataContractSerializer> `preserveObjectReferences` (ya `true`, ile <xref:System.Runtime.Serialization.XmlObjectSerializer>ayarlanmış , ya da kendi özel).  
  
3. Hizmet ana bilgisayarını açmadan veya istemci <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> kanalı oluşturmadan önce, varolan davranışı kaldırın ve önceki adımlarda oluşturduğunuz özel türemiş sınıfı takın.  
  
 Gelişmiş serileştirme kavramları hakkında daha fazla bilgi için [serileştirme ve deserialization](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)bölümüne bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XmlSerializer Sınıfını Kullanma](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)
- [Nasıl yapılır: Akışı Etkinleştirme](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)
- [Nasıl yapılır: Bir Sınıf veya Yapı için Temel Bir Veri Sözleşmesi Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
