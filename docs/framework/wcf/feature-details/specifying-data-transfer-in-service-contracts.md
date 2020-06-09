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
# <a name="specifying-data-transfer-in-service-contracts"></a><span data-ttu-id="848ec-102">Hizmet Sözleşmelerinde Veri Aktarımını Belirtme</span><span class="sxs-lookup"><span data-stu-id="848ec-102">Specifying Data Transfer in Service Contracts</span></span>
<span data-ttu-id="848ec-103">Windows Communication Foundation (WCF) bir mesajlaşma altyapısı olarak düşünülebilir.</span><span class="sxs-lookup"><span data-stu-id="848ec-103">The Windows Communication Foundation (WCF) can be thought of as a messaging infrastructure.</span></span> <span data-ttu-id="848ec-104">Hizmet işlemleri iletileri alabilir, işleyebilir ve iletileri gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="848ec-104">Service operations can receive messages, process them, and send them messages.</span></span> <span data-ttu-id="848ec-105">İletiler, işlem sözleşmeleri kullanılarak açıklanır.</span><span class="sxs-lookup"><span data-stu-id="848ec-105">Messages are described using operation contracts.</span></span> <span data-ttu-id="848ec-106">Örneğin, aşağıdaki sözleşmeyi göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="848ec-106">For example, consider the following contract.</span></span>  
  
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
  
 <span data-ttu-id="848ec-107">Burada işlem, `GetAirfare` ve hakkındaki bilgileri içeren bir ileti kabul `fromCity` eder `toCity` ve ardından sayı içeren bir ileti döndürür.</span><span class="sxs-lookup"><span data-stu-id="848ec-107">Here, the `GetAirfare` operation accepts a message with information about `fromCity` and `toCity`, and then returns a message that contains a number.</span></span>  
  
 <span data-ttu-id="848ec-108">Bu konu başlığı altında, bir işlem sözleşmesinin iletileri nasıl açıklayabileceği çeşitli yollar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="848ec-108">This topic explains the various ways in which an operation contract can describe messages.</span></span>  
  
## <a name="describing-messages-by-using-parameters"></a><span data-ttu-id="848ec-109">Parametreleri kullanarak Iletileri açıklama</span><span class="sxs-lookup"><span data-stu-id="848ec-109">Describing Messages by Using Parameters</span></span>  
 <span data-ttu-id="848ec-110">Bir iletiyi tanımlamanın en kolay yolu bir parametre listesi ve dönüş değeri kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="848ec-110">The simplest way to describe a message is to use a parameter list and the return value.</span></span> <span data-ttu-id="848ec-111">Yukarıdaki örnekte, `fromCity` ve `toCity` dize parametreleri istek iletisini tanımlamakta kullanıldı ve yanıt iletisini anlatmak için float dönüş değeri kullanıldı.</span><span class="sxs-lookup"><span data-stu-id="848ec-111">In the preceding example, the `fromCity` and `toCity` string parameters were used to describe the request message, and the float return value was used to describe the reply message.</span></span> <span data-ttu-id="848ec-112">Dönüş değeri yalnızca bir yanıt iletisini anlatmak için yeterli değilse, out parametreleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="848ec-112">If the return value alone is not enough to describe a reply message, out parameters may be used.</span></span> <span data-ttu-id="848ec-113">Örneğin, aşağıdaki işlem `fromCity` `toCity` kendi istek iletisine sahiptir ve yanıt iletisindeki bir para birimiyle bir sayı ile birlikte bir sayıdır:</span><span class="sxs-lookup"><span data-stu-id="848ec-113">For example, the following operation has `fromCity` and `toCity` in its request message, and a number together with a currency in its reply message:</span></span>  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, out string currency);  
```  
  
```vb  
<OperationContract()>  
    Function GetAirfare(fromCity As String, toCity As String) As Double  
```  
  
 <span data-ttu-id="848ec-114">Ayrıca, hem isteğin hem de yanıt iletisinin bir parametre parçasını oluşturmak için başvuru parametrelerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="848ec-114">Additionally, you may use reference parameters to make a parameter part of both the request and the reply message.</span></span> <span data-ttu-id="848ec-115">Parametrelerin serileştirilemiyor (XML 'e dönüştürülebileceğinden) türler olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="848ec-115">The parameters must be of types that can be serialized (converted to XML).</span></span> <span data-ttu-id="848ec-116">Varsayılan olarak, WCF <xref:System.Runtime.Serialization.DataContractSerializer> bu dönüştürmeyi gerçekleştirmek için sınıfı olarak adlandırılan bir bileşeni kullanır.</span><span class="sxs-lookup"><span data-stu-id="848ec-116">By default, WCF uses a component called the <xref:System.Runtime.Serialization.DataContractSerializer> class to perform this conversion.</span></span> <span data-ttu-id="848ec-117">En basit türler (örneğin,,, `int` `string` `float` ve `DateTime` .) desteklenir.</span><span class="sxs-lookup"><span data-stu-id="848ec-117">Most primitive types (such as `int`, `string`, `float`, and `DateTime`.) are supported.</span></span> <span data-ttu-id="848ec-118">Kullanıcı tanımlı türlerin normalde bir veri anlaşması olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="848ec-118">User-defined types must normally have a data contract.</span></span> <span data-ttu-id="848ec-119">Daha fazla bilgi için bkz. [Veri Sözleşmelerini Kullanma](using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="848ec-119">For more information, see [Using Data Contracts](using-data-contracts.md).</span></span>  
  
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
  
 <span data-ttu-id="848ec-120">Bazen, `DataContractSerializer` türlerinizi seri hale getirmek için yeterli değildir.</span><span class="sxs-lookup"><span data-stu-id="848ec-120">Occasionally, the `DataContractSerializer` is not adequate to serialize your types.</span></span> <span data-ttu-id="848ec-121">WCF, <xref:System.Xml.Serialization.XmlSerializer> parametreleri seri hale getirmek için de kullanabileceğiniz alternatif bir serileştirme altyapısını destekler.</span><span class="sxs-lookup"><span data-stu-id="848ec-121">WCF supports an alternative serialization engine, the <xref:System.Xml.Serialization.XmlSerializer>, which you can also use to serialize parameters.</span></span> <span data-ttu-id="848ec-122">, Gibi <xref:System.Xml.Serialization.XmlSerializer> öznitelikleri kullanarak SONUÇTAKI XML üzerinde daha fazla denetim kullanmanıza olanak sağlar `XmlAttributeAttribute` .</span><span class="sxs-lookup"><span data-stu-id="848ec-122">The <xref:System.Xml.Serialization.XmlSerializer> allows you to use more control over the resultant XML using attributes such as the `XmlAttributeAttribute`.</span></span> <span data-ttu-id="848ec-123"><xref:System.Xml.Serialization.XmlSerializer>Öğesini belirli bir işlem için veya tüm hizmet için kullanmak üzere değiştirmek için, <xref:System.ServiceModel.XmlSerializerFormatAttribute> özniteliği bir işleme veya hizmete uygulayın.</span><span class="sxs-lookup"><span data-stu-id="848ec-123">To switch to using the <xref:System.Xml.Serialization.XmlSerializer> for a particular operation or for the entire service, apply the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to an operation or a service.</span></span> <span data-ttu-id="848ec-124">Örnek:</span><span class="sxs-lookup"><span data-stu-id="848ec-124">For example:</span></span>  
  
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
  
 <span data-ttu-id="848ec-125">Daha fazla bilgi için, bkz. [XmlSerializer sınıfını kullanma](using-the-xmlserializer-class.md).</span><span class="sxs-lookup"><span data-stu-id="848ec-125">For more information, see [Using the XmlSerializer Class](using-the-xmlserializer-class.md).</span></span> <span data-ttu-id="848ec-126"><xref:System.Xml.Serialization.XmlSerializer>Bu konu başlığı altında ayrıntılı olarak bazı nedenleriniz olmadığı sürece, burada gösterildiği gibi öğesine el ile geçiş yapmayı unutmayın.</span><span class="sxs-lookup"><span data-stu-id="848ec-126">Remember that manually switching to the <xref:System.Xml.Serialization.XmlSerializer> as shown here is not recommended unless you have specific reasons to do so as detailed in that topic.</span></span>  
  
 <span data-ttu-id="848ec-127">.NET parametre adlarını sözleşme adlarından yalıtmak için, <xref:System.ServiceModel.MessageParameterAttribute> özniteliğini kullanabilir ve `Name` sözleşme adını ayarlamak için özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="848ec-127">To isolate .NET parameter names from contract names, you can use the <xref:System.ServiceModel.MessageParameterAttribute> attribute, and use the `Name` property to set the contract name.</span></span> <span data-ttu-id="848ec-128">Örneğin, aşağıdaki işlem sözleşmesi, bu konudaki ilk örnekle eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="848ec-128">For example, the following operation contract is equivalent to the first example in this topic.</span></span>  
  
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
  
## <a name="describing-empty-messages"></a><span data-ttu-id="848ec-129">Boş Iletileri açıklama</span><span class="sxs-lookup"><span data-stu-id="848ec-129">Describing Empty Messages</span></span>  
 <span data-ttu-id="848ec-130">Boş bir istek iletisi, hiçbir giriş veya başvuru parametresi olmadan açıklanabilir.</span><span class="sxs-lookup"><span data-stu-id="848ec-130">An empty request message can be described by having no input or reference parameters.</span></span> <span data-ttu-id="848ec-131">Örneğin, C# ' de:</span><span class="sxs-lookup"><span data-stu-id="848ec-131">For example, in C#:</span></span>  
  
 `[OperationContract]`  
  
 `public int GetCurrentTemperature();`  
  
 <span data-ttu-id="848ec-132">Örneğin, Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="848ec-132">For example, in Visual Basic:</span></span>  
  
 `<OperationContract()>`  
  
 `Function GetCurrentTemperature() as Integer`  
  
 <span data-ttu-id="848ec-133">Boş bir yanıt iletisi, `void` dönüş türü ve çıkış ya da başvuru parametresi olmadan açıklanabilir.</span><span class="sxs-lookup"><span data-stu-id="848ec-133">An empty reply message can be described by having a `void` return type and no output or reference parameters.</span></span> <span data-ttu-id="848ec-134">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="848ec-134">For example in:</span></span>  
  
```csharp  
[OperationContract]  
public void SetTemperature(int temperature);  
```  
  
```vb  
<OperationContract()>  
Sub SetTemperature(temperature As Integer)  
```  
  
 <span data-ttu-id="848ec-135">Bu, tek yönlü bir işlemden farklıdır, örneğin:</span><span class="sxs-lookup"><span data-stu-id="848ec-135">This is different from a one-way operation, such as:</span></span>  
  
```csharp  
[OperationContract(IsOneWay=true)]  
public void SetLightbulbStatus(bool isOn);  
```  
  
```vb  
<OperationContract(IsOneWay:=True)>  
Sub SetLightbulbStatus(isOne As Boolean)  
```  
  
 <span data-ttu-id="848ec-136">`SetTemperatureStatus`İşlem boş bir ileti döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="848ec-136">The `SetTemperatureStatus` operation returns an empty message.</span></span> <span data-ttu-id="848ec-137">Giriş iletisini işlerken bir sorun oluşursa bunun yerine bir hata döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="848ec-137">It may return a fault instead if there is a problem processing the input message.</span></span> <span data-ttu-id="848ec-138">`SetLightbulbStatus`İşlem hiçbir şey döndürmüyor.</span><span class="sxs-lookup"><span data-stu-id="848ec-138">The `SetLightbulbStatus` operation returns nothing.</span></span> <span data-ttu-id="848ec-139">Bu işlemden bir hata koşulunu iletmenin bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="848ec-139">There is no way to communicate a fault condition from this operation.</span></span>  
  
## <a name="describing-messages-by-using-message-contracts"></a><span data-ttu-id="848ec-140">Ileti sözleşmelerini kullanarak Iletileri açıklama</span><span class="sxs-lookup"><span data-stu-id="848ec-140">Describing Messages by Using Message Contracts</span></span>  
 <span data-ttu-id="848ec-141">Tüm iletiyi göstermek için tek bir tür kullanmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="848ec-141">You may want to use a single type to represent the entire message.</span></span> <span data-ttu-id="848ec-142">Bu amaçla bir veri sözleşmesi kullanmak mümkün olsa da, bunu yapmanın önerilen yolu bir ileti sözleşmesi kullanmaktır; bu, sonuçta elde edilen XML 'de gereksiz kaydırma düzeylerini önler.</span><span class="sxs-lookup"><span data-stu-id="848ec-142">While it is possible to use a data contract for this purpose, the recommended way to do this is to use a message contract—this avoids unnecessary levels of wrapping in the resultant XML.</span></span> <span data-ttu-id="848ec-143">Ayrıca, ileti sözleşmeleri sonuç iletileri üzerinde daha fazla denetim yapmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="848ec-143">Additionally, message contracts allow you to exercise more control over resultant messages.</span></span> <span data-ttu-id="848ec-144">Örneğin, ileti gövdesinde hangi bilgi parçalarının olması gerektiğine ve ileti üstbilgilerinde olması gerektiğine karar verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="848ec-144">For instance, you can decide which pieces of information should be in the message body and which should be in the message headers.</span></span> <span data-ttu-id="848ec-145">Aşağıdaki örnek, ileti sözleşmelerinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="848ec-145">The following example shows the use of message contracts.</span></span>  
  
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
  
 <span data-ttu-id="848ec-146">Daha fazla bilgi için bkz. [Ileti sözleşmelerini kullanma](using-message-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="848ec-146">For more information, see [Using Message Contracts](using-message-contracts.md).</span></span>  
  
 <span data-ttu-id="848ec-147">Önceki örnekte, <xref:System.Runtime.Serialization.DataContractSerializer> sınıf varsayılan olarak hala kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="848ec-147">In the previous example, the <xref:System.Runtime.Serialization.DataContractSerializer> class is still used by default.</span></span> <span data-ttu-id="848ec-148"><xref:System.Xml.Serialization.XmlSerializer>Sınıf, ileti sözleşmeleri ile de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="848ec-148">The <xref:System.Xml.Serialization.XmlSerializer> class can also be used with message contracts.</span></span> <span data-ttu-id="848ec-149">Bunu yapmak için, <xref:System.ServiceModel.XmlSerializerFormatAttribute> özniteliği işlem ya da sözleşmeye uygulayın ve <xref:System.Xml.Serialization.XmlSerializer> ileti üstbilgilerinde ve gövde üyelerinde sınıfıyla uyumlu türleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="848ec-149">To do this, apply the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to either the operation or the contract, and use types compatible with the <xref:System.Xml.Serialization.XmlSerializer> class in the message headers and body members.</span></span>  
  
## <a name="describing-messages-by-using-streams"></a><span data-ttu-id="848ec-150">Akışları kullanarak Iletileri açıklama</span><span class="sxs-lookup"><span data-stu-id="848ec-150">Describing Messages by Using Streams</span></span>  
 <span data-ttu-id="848ec-151">İşlemler içindeki iletileri tanımlamanın bir başka yolu da bir <xref:System.IO.Stream> işlem sözleşmesindeki veya bir ileti sözleşmesi gövde üyesi olarak ya da bir ileti sözleşme gövdesi üyesi olarak türetilmiş sınıflarından birini ya da bir ileti sözleşmesi gövde üyesini (Bu durumda tek üye olmalıdır) kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="848ec-151">Another way to describe messages in operations is to use the <xref:System.IO.Stream> class or one of its derived classes in an operation contract or as a message contract body member (it must be the only member in this case).</span></span> <span data-ttu-id="848ec-152">Gelen iletilerde, türün olması gerekir; `Stream` türetilmiş sınıfları kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="848ec-152">For incoming messages, the type must be `Stream`—you cannot use derived classes.</span></span>  
  
 <span data-ttu-id="848ec-153">WCF, seri hale getirici 'yi çağırmak yerine bir akıştan veri alır ve bunu doğrudan giden bir iletiye koyar veya gelen iletiden veri alıp doğrudan bir akışa koyar.</span><span class="sxs-lookup"><span data-stu-id="848ec-153">Instead of invoking the serializer, WCF retrieves data from a stream and puts it directly into an outgoing message, or retrieves data from an incoming message and puts it directly into a stream.</span></span> <span data-ttu-id="848ec-154">Aşağıdaki örnek, akışlarının kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="848ec-154">The following sample shows the use of streams.</span></span>  
  
```csharp  
[OperationContract]  
public Stream DownloadFile(string fileName);  
```  
  
```vb  
<OperationContract()>  
Function DownloadFile(fileName As String) As String  
```  
  
 <span data-ttu-id="848ec-155">`Stream`Tek bir ileti gövdesinde verileri birleştiremezsiniz ve akış dışı olamaz.</span><span class="sxs-lookup"><span data-stu-id="848ec-155">You cannot combine `Stream` and non-stream data in a single message body.</span></span> <span data-ttu-id="848ec-156">İleti üstbilgilerinde ek verileri yerleştirmek için bir ileti sözleşmesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="848ec-156">Use a message contract to put the extra data in message headers.</span></span> <span data-ttu-id="848ec-157">Aşağıdaki örnek, işlem sözleşmesini tanımlarken akış kullanımının yanlış kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="848ec-157">The following example shows the incorrect usage of streams when defining the operation contract.</span></span>  
  
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
  
 <span data-ttu-id="848ec-158">Aşağıdaki örnek, bir işlem anlaşması tanımlarken akışlarının doğru kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="848ec-158">The following sample shows the correct usage of streams when defining an operation contract.</span></span>  
  
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
  
 <span data-ttu-id="848ec-159">Daha fazla bilgi için bkz. [büyük veri ve akış](large-data-and-streaming.md).</span><span class="sxs-lookup"><span data-stu-id="848ec-159">For more information, see [Large Data and Streaming](large-data-and-streaming.md).</span></span>  
  
## <a name="using-the-message-class"></a><span data-ttu-id="848ec-160">İleti Sınıfını Kullanma</span><span class="sxs-lookup"><span data-stu-id="848ec-160">Using the Message Class</span></span>  
 <span data-ttu-id="848ec-161">Gönderilen veya alınan iletiler üzerinde tamamen programlı denetim sağlamak için, <xref:System.ServiceModel.Channels.Message> Aşağıdaki örnek kodda gösterildiği gibi, sınıfını doğrudan kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="848ec-161">To have complete programmatic control over messages sent or received, you can use the <xref:System.ServiceModel.Channels.Message> class directly, as shown in the following example code.</span></span>  
  
```csharp  
[OperationContract]  
public void LogMessage(Message m);  
```  
  
```vb  
<OperationContract()>  
Sub LogMessage(m As Message)  
```  
  
 <span data-ttu-id="848ec-162">Bu, [Ileti sınıfını kullanma](using-the-message-class.md)konusunda ayrıntılı olarak açıklanan gelişmiş bir senaryodur.</span><span class="sxs-lookup"><span data-stu-id="848ec-162">This is an advanced scenario, which is described in detail in [Using the Message Class](using-the-message-class.md).</span></span>  
  
## <a name="describing-fault-messages"></a><span data-ttu-id="848ec-163">Hata Iletilerini açıklama</span><span class="sxs-lookup"><span data-stu-id="848ec-163">Describing Fault Messages</span></span>  
 <span data-ttu-id="848ec-164">Dönüş değeri ve çıkış ya da başvuru parametreleri tarafından tanımlanan iletilere ek olarak, tek yönlü olmayan tüm işlemler en az iki olası ileti döndürebilir: normal yanıt iletisi ve bir hata iletisi.</span><span class="sxs-lookup"><span data-stu-id="848ec-164">In addition to the messages that are described by the return value and output or reference parameters, any operation that is not one-way can return at least two possible messages: its normal response message and a fault message.</span></span> <span data-ttu-id="848ec-165">Aşağıdaki işlem sözleşmesini göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="848ec-165">Consider the following operation contract.</span></span>  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, DateTime date);  
```  
  
```vb  
<OperationContract()>  
Function GetAirfare(fromCity As String, toCity As String, date as DateTime)  
```  
  
 <span data-ttu-id="848ec-166">Bu işlem sayı içeren bir normal ileti `float` ya da hata kodu ve açıklama içeren bir hata iletisi döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="848ec-166">This operation may either return a normal message that contains a `float` number, or a fault message that contains a fault code and a description.</span></span> <span data-ttu-id="848ec-167">Bunu, hizmet uygulamanızda bir oluşturarak gerçekleştirebilirsiniz <xref:System.ServiceModel.FaultException> .</span><span class="sxs-lookup"><span data-stu-id="848ec-167">You can accomplish this by throwing a <xref:System.ServiceModel.FaultException> in your service implementation.</span></span>  
  
 <span data-ttu-id="848ec-168">Özniteliğini kullanarak, olası hata iletileri belirtebilirsiniz <xref:System.ServiceModel.FaultContractAttribute> .</span><span class="sxs-lookup"><span data-stu-id="848ec-168">You can specify additional possible fault messages by using the <xref:System.ServiceModel.FaultContractAttribute> attribute.</span></span> <span data-ttu-id="848ec-169">Aşağıdaki örnek kodda gösterildiği gibi ek hataların kullanılarak seri hale getirilebilir olması gerekir <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="848ec-169">The additional faults must be serializable using the <xref:System.Runtime.Serialization.DataContractSerializer>, as shown in the following example code.</span></span>  
  
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
  
 <span data-ttu-id="848ec-170">Bu ek hatalar, <xref:System.ServiceModel.FaultException%601> uygun veri sözleşmesi türünün bir kopyası çalıştırılarak oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="848ec-170">These additional faults can be generated by throwing a <xref:System.ServiceModel.FaultException%601> of the appropriate data contract type.</span></span> <span data-ttu-id="848ec-171">Daha fazla bilgi için bkz. [özel durumları ve hataları işleme](../extending/handling-exceptions-and-faults.md).</span><span class="sxs-lookup"><span data-stu-id="848ec-171">For more information, see [Handling Exceptions and Faults](../extending/handling-exceptions-and-faults.md).</span></span>  
  
 <span data-ttu-id="848ec-172"><xref:System.Xml.Serialization.XmlSerializer>Hataları anlatmak için sınıfını kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="848ec-172">You cannot use the <xref:System.Xml.Serialization.XmlSerializer> class to describe faults.</span></span> <span data-ttu-id="848ec-173">, <xref:System.ServiceModel.XmlSerializerFormatAttribute> Hata sözleşmeleri üzerinde hiçbir etkiye sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="848ec-173">The <xref:System.ServiceModel.XmlSerializerFormatAttribute> has no effect on fault contracts.</span></span>  
  
## <a name="using-derived-types"></a><span data-ttu-id="848ec-174">Türetilmiş türleri kullanma</span><span class="sxs-lookup"><span data-stu-id="848ec-174">Using Derived Types</span></span>  
 <span data-ttu-id="848ec-175">Bir işlemde veya bir ileti sözleşmesinde temel tür kullanmak ve ardından işlemi çağırırken türetilmiş bir tür kullanmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="848ec-175">You may want to use a base type in an operation or a message contract, and then use a derived type when actually invoking the operation.</span></span> <span data-ttu-id="848ec-176">Bu durumda, <xref:System.ServiceModel.ServiceKnownTypeAttribute> türetilmiş türlerin kullanılmasına izin vermek için özniteliği veya bazı alternatif mekanizmayı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="848ec-176">In this case, you must use either the <xref:System.ServiceModel.ServiceKnownTypeAttribute> attribute or some alternative mechanism to allow the use of derived types.</span></span> <span data-ttu-id="848ec-177">Aşağıdaki işlemi göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="848ec-177">Consider the following operation.</span></span>  
  
```csharp  
[OperationContract]  
public bool IsLibraryItemAvailable(LibraryItem item);  
```  
  
```vb
<OperationContract()>  
    Function IsLibraryItemAvailable(item As LibraryItem) As Boolean  
```  
  
 <span data-ttu-id="848ec-178">İki türün `Book` ve `Magazine` , öğesinden türet olduğunu varsayalım `LibraryItem` .</span><span class="sxs-lookup"><span data-stu-id="848ec-178">Assume that two types, `Book` and `Magazine`, derive from `LibraryItem`.</span></span> <span data-ttu-id="848ec-179">Bu türleri işlem içinde kullanmak için `IsLibraryItemAvailable` , işlemi aşağıdaki şekilde değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="848ec-179">To use these types in the `IsLibraryItemAvailable` operation, you can change the operation as follows:</span></span>  
  
 `[OperationContract]`  
  
 `[ServiceKnownType(typeof(Book))]`  
  
 `[ServiceKnownType(typeof(Magazine))]`  
  
 `public bool IsLibraryItemAvailable(LibraryItem item);`  
  
 <span data-ttu-id="848ec-180">Alternatif olarak, <xref:System.Runtime.Serialization.KnownTypeAttribute> <xref:System.Runtime.Serialization.DataContractSerializer> Aşağıdaki örnek kodda gösterildiği gibi, varsayılan kullanımda olduğunda özniteliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="848ec-180">Alternatively, you can use the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute when the default <xref:System.Runtime.Serialization.DataContractSerializer> is in use, as shown in the following example code.</span></span>  
  
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
  
 <span data-ttu-id="848ec-181"><xref:System.Xml.Serialization.XmlIncludeAttribute>Kullanırken özniteliğini kullanabilirsiniz <xref:System.Xml.Serialization.XmlSerializer> .</span><span class="sxs-lookup"><span data-stu-id="848ec-181">You can use the <xref:System.Xml.Serialization.XmlIncludeAttribute> attribute when using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
 <span data-ttu-id="848ec-182"><xref:System.ServiceModel.ServiceKnownTypeAttribute>Özniteliği bir işleme veya tüm hizmete uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="848ec-182">You can apply the <xref:System.ServiceModel.ServiceKnownTypeAttribute> attribute to an operation or to the entire service.</span></span> <span data-ttu-id="848ec-183">Özniteliği gibi bilinen türlerin bir listesini almak için çağrılacak yöntemin türünü ya da adını kabul eder <xref:System.Runtime.Serialization.KnownTypeAttribute> .</span><span class="sxs-lookup"><span data-stu-id="848ec-183">It accepts either a type or the name of the method to call to get a list of known types, just like the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute.</span></span> <span data-ttu-id="848ec-184">Daha fazla bilgi için bkz. [veri sözleşmesi bilinen türleri](data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="848ec-184">For more information, see [Data Contract Known Types](data-contract-known-types.md).</span></span>  
  
## <a name="specifying-the-use-and-style"></a><span data-ttu-id="848ec-185">Kullanımı ve stili belirtme</span><span class="sxs-lookup"><span data-stu-id="848ec-185">Specifying the Use and Style</span></span>  
 <span data-ttu-id="848ec-186">Web Hizmetleri Açıklama Dili (WSDL) kullanarak hizmetleri açıkladığınızda, yaygın olarak kullanılan iki stil belge ve uzak yordam çağrısı (RPC) ' dir.</span><span class="sxs-lookup"><span data-stu-id="848ec-186">When describing services using Web Services Description Language (WSDL), the two commonly used styles are Document and remote procedure call (RPC).</span></span> <span data-ttu-id="848ec-187">Belge stilinde, tüm ileti gövdesi şema kullanılarak tanımlanır ve WSDL, bu şema içindeki öğelere başvurarak çeşitli ileti gövdesi parçalarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="848ec-187">In the Document style, the entire message body is described using the schema, and the WSDL describes the various message body parts by referring to elements within that schema.</span></span> <span data-ttu-id="848ec-188">RPC stilinde, WSDL bir öğesi yerine her ileti bölümü için bir şema türü anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="848ec-188">In the RPC style, the WSDL refers to a schema type for each message part rather than an element.</span></span> <span data-ttu-id="848ec-189">Bazı durumlarda, bu stillerden birini el ile seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="848ec-189">In some cases, you have to manually select one of these styles.</span></span> <span data-ttu-id="848ec-190">Bu işlemi, <xref:System.ServiceModel.DataContractFormatAttribute> özniteliği uygulayıp `Style` özelliği ayarlayarak (kullanırken <xref:System.Runtime.Serialization.DataContractSerializer> ) veya özniteliği üzerinde ayarını yaparak yapabilirsiniz `Style` <xref:System.ServiceModel.XmlSerializerFormatAttribute> <xref:System.Xml.Serialization.XmlSerializer> .</span><span class="sxs-lookup"><span data-stu-id="848ec-190">You can do this by applying the <xref:System.ServiceModel.DataContractFormatAttribute> attribute and setting the `Style` property (when the <xref:System.Runtime.Serialization.DataContractSerializer> is in use), or by setting `Style` on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute (when using the <xref:System.Xml.Serialization.XmlSerializer>).</span></span>  
  
 <span data-ttu-id="848ec-191">Ayrıca, <xref:System.Xml.Serialization.XmlSerializer> iki seri hale GETIRILMIŞ XML biçimini destekler: `Literal` ve `Encoded` .</span><span class="sxs-lookup"><span data-stu-id="848ec-191">Additionally, the <xref:System.Xml.Serialization.XmlSerializer> supports two forms of serialized XML: `Literal` and `Encoded`.</span></span> <span data-ttu-id="848ec-192">`Literal`en yaygın olarak kabul edilen formdur ve desteklediği tek formdur <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="848ec-192">`Literal` is the most commonly accepted form, and is the only form the <xref:System.Runtime.Serialization.DataContractSerializer> supports.</span></span> <span data-ttu-id="848ec-193">`Encoded`, SOAP belirtiminin 5. bölümünde açıklanan eski bir formdur ve yeni hizmetler için önerilmez.</span><span class="sxs-lookup"><span data-stu-id="848ec-193">`Encoded` is a legacy form described in section 5 of the SOAP specification, and is not recommended for new services.</span></span> <span data-ttu-id="848ec-194">Moda geçmek için `Encoded` , `Use` <xref:System.ServiceModel.XmlSerializerFormatAttribute> özniteliğinde özelliğini olarak ayarlayın `Encoded` .</span><span class="sxs-lookup"><span data-stu-id="848ec-194">To switch to `Encoded` mode, set the `Use` property on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to `Encoded`.</span></span>  
  
 <span data-ttu-id="848ec-195">Çoğu durumda, ve özellikleri için varsayılan ayarları değiştirmemelisiniz `Style` `Use` .</span><span class="sxs-lookup"><span data-stu-id="848ec-195">In most cases, you should not change the default settings for the `Style` and `Use` properties.</span></span>  
  
## <a name="controlling-the-serialization-process"></a><span data-ttu-id="848ec-196">Serileştirme Işlemini denetleme</span><span class="sxs-lookup"><span data-stu-id="848ec-196">Controlling the Serialization Process</span></span>  
 <span data-ttu-id="848ec-197">Verilerin serileştirilme şeklini özelleştirmek için çeşitli şeyler yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="848ec-197">You can do a number of things to customize the way data is serialized.</span></span>  
  
### <a name="changing-server-serialization-settings"></a><span data-ttu-id="848ec-198">Sunucu serileştirme ayarlarını değiştirme</span><span class="sxs-lookup"><span data-stu-id="848ec-198">Changing Server Serialization Settings</span></span>  
 <span data-ttu-id="848ec-199">Varsayılan kullanımda olduğunda <xref:System.Runtime.Serialization.DataContractSerializer> , hizmetine özniteliği uygulayarak serileştirme işleminin bazı yönlerini kontrol edebilirsiniz <xref:System.ServiceModel.ServiceBehaviorAttribute> .</span><span class="sxs-lookup"><span data-stu-id="848ec-199">When the default <xref:System.Runtime.Serialization.DataContractSerializer> is in use, you can control some aspects of the serialization process on the service by applying the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to the service.</span></span> <span data-ttu-id="848ec-200">Özellikle, seri hale getirilen `MaxItemsInObjectGraph` en fazla nesne sayısını sınırlayan kotayı ayarlamak için özelliğini kullanabilirsiniz <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="848ec-200">Specifically, you may use the `MaxItemsInObjectGraph` property to set the quota that limits the maximum number of objects the <xref:System.Runtime.Serialization.DataContractSerializer> deserializes.</span></span> <span data-ttu-id="848ec-201">`IgnoreExtensionDataObject`Özelliği, gidiş yuvarlama sürümü özelliğini devre dışı bırakmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="848ec-201">You can use the `IgnoreExtensionDataObject` property to turn off the round-tripping versioning feature.</span></span> <span data-ttu-id="848ec-202">Kotalar hakkında daha fazla bilgi için bkz. [veriler Için güvenlik konuları](security-considerations-for-data.md).</span><span class="sxs-lookup"><span data-stu-id="848ec-202">For more information about quotas, see [Security Considerations for Data](security-considerations-for-data.md).</span></span> <span data-ttu-id="848ec-203">Gidiş dönüşü hakkında daha fazla bilgi için bkz. [Forward-uyumlu veri sözleşmeleri](forward-compatible-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="848ec-203">For more information about round-tripping, see [Forward-Compatible Data Contracts](forward-compatible-data-contracts.md).</span></span>  
  
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
  
### <a name="serialization-behaviors"></a><span data-ttu-id="848ec-204">Serileştirme davranışları</span><span class="sxs-lookup"><span data-stu-id="848ec-204">Serialization Behaviors</span></span>  
 <span data-ttu-id="848ec-205">WCF 'de iki davranış mevcuttur, ve, <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> belirli bir işlem için hangi seri hale getiricinin kullanımda olduğuna bağlı olarak otomatik olarak takılır.</span><span class="sxs-lookup"><span data-stu-id="848ec-205">Two behaviors are available in WCF, the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> and the <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> that are automatically plugged in depending on which serializer is in use for a particular operation.</span></span> <span data-ttu-id="848ec-206">Bu davranışlar otomatik olarak uygulandığından, normalde bunların farkında olmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="848ec-206">Because these behaviors are applied automatically, you normally do not have to be aware of them.</span></span>  
  
 <span data-ttu-id="848ec-207">Ancak, `DataContractSerializerOperationBehavior` `MaxItemsInObjectGraph` `IgnoreExtensionDataObject` `DataContractSurrogate` serileştirme işlemini özelleştirmek için kullanabileceğiniz, ve özelliklerini içerir.</span><span class="sxs-lookup"><span data-stu-id="848ec-207">However, the `DataContractSerializerOperationBehavior` has the `MaxItemsInObjectGraph`, `IgnoreExtensionDataObject`, and `DataContractSurrogate` properties that you may use to customize the serialization process.</span></span> <span data-ttu-id="848ec-208">İlk iki özellik, önceki bölümde açıklanan anlama sahiptir.</span><span class="sxs-lookup"><span data-stu-id="848ec-208">The first two properties have the same meaning as discussed in the previous section.</span></span> <span data-ttu-id="848ec-209">`DataContractSurrogate`Özelliği, serileştirme işlemini özelleştirmek ve genişletmek için güçlü bir mekanizma olan veri sözleşmesi yedekleri 'ni etkinleştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="848ec-209">You can use the `DataContractSurrogate` property to enable data contract surrogates, which are a powerful mechanism for customizing and extending the serialization process.</span></span> <span data-ttu-id="848ec-210">Daha fazla bilgi için bkz. [veri sözleşmesi yedeklerin kapıları](../extending/data-contract-surrogates.md).</span><span class="sxs-lookup"><span data-stu-id="848ec-210">For more information, see [Data Contract Surrogates](../extending/data-contract-surrogates.md).</span></span>  
  
 <span data-ttu-id="848ec-211">`DataContractSerializerOperationBehavior`Hem istemci hem de sunucu serileştirmesini özelleştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="848ec-211">You can use the `DataContractSerializerOperationBehavior` to customize both client and server serialization.</span></span> <span data-ttu-id="848ec-212">Aşağıdaki örnek, istemci üzerindeki kotanın nasıl arttıralınacağını göstermektedir `MaxItemsInObjectGraph` .</span><span class="sxs-lookup"><span data-stu-id="848ec-212">The following example shows how to increase the `MaxItemsInObjectGraph` quota on the client.</span></span>  
  
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
  
<span data-ttu-id="848ec-213">Şirket içinde barındırılan durumda, hizmette eşdeğer kod aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="848ec-213">The following is the equivalent code on the service, in the self-hosted case:</span></span>
  
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
  
 <span data-ttu-id="848ec-214">Web 'de barındırılan bir durumda, yeni bir `ServiceHost` türetilmiş sınıf oluşturmanız ve bir hizmet ana bilgisayar fabrikası kullanarak içine takabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="848ec-214">In the Web-hosted case, you must create a new `ServiceHost` derived class and use a service host factory to plug it in.</span></span>  
  
### <a name="controlling-serialization-settings-in-configuration"></a><span data-ttu-id="848ec-215">Yapılandırmada serileştirme ayarlarını denetleme</span><span class="sxs-lookup"><span data-stu-id="848ec-215">Controlling Serialization Settings in Configuration</span></span>  
 <span data-ttu-id="848ec-216">`MaxItemsInObjectGraph`Ve, `IgnoreExtensionDataObject` `dataContractSerializer` Aşağıdaki örnekte gösterildiği gibi, uç nokta veya hizmet davranışı kullanılarak yapılandırma yoluyla denetlenebilirler.</span><span class="sxs-lookup"><span data-stu-id="848ec-216">The `MaxItemsInObjectGraph` and `IgnoreExtensionDataObject` can be controlled through configuration by using the `dataContractSerializer` endpoint or service behavior, as shown in the following example.</span></span>  
  
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
  
### <a name="shared-type-serialization-object-graph-preservation-and-custom-serializers"></a><span data-ttu-id="848ec-217">Paylaşılan tür serileştirme, nesne grafik koruma ve özel serileştiriciler</span><span class="sxs-lookup"><span data-stu-id="848ec-217">Shared Type Serialization, Object Graph Preservation, and Custom Serializers</span></span>  
 <span data-ttu-id="848ec-218"><xref:System.Runtime.Serialization.DataContractSerializer>Veri sözleşmesi adlarını kullanarak seri hale getirir ve .net tür adları değildir.</span><span class="sxs-lookup"><span data-stu-id="848ec-218">The <xref:System.Runtime.Serialization.DataContractSerializer> serializes using data contract names and not .NET type names.</span></span> <span data-ttu-id="848ec-219">Bu, hizmet odaklı mimari olanakları ile tutarlıdır ve harika bir esneklik sağlar; .NET türleri, Tel sözleşmeyi etkilemeden değişebilir.</span><span class="sxs-lookup"><span data-stu-id="848ec-219">This is consistent with service-oriented architecture tenets and allows for a great degree of flexibility—the .NET types can change without affecting the wire contract.</span></span> <span data-ttu-id="848ec-220">Nadir durumlarda, gerçek .NET tür adlarını seri hale getirmek isteyebilirsiniz ve bu sayede istemci ile sunucu arasında sıkı bir şekilde iletişim kurarak, .NET Framework Remoting teknolojisine benzer.</span><span class="sxs-lookup"><span data-stu-id="848ec-220">In rare cases, you may want to serialize actual .NET type names, thereby introducing a tight coupling between the client and the server, similar to the .NET Framework remoting technology.</span></span> <span data-ttu-id="848ec-221">Bu, genellikle .NET Framework uzaktan iletişim 'dan WCF 'ye geçiş yapılırken oluşan nadir durumlar dışında, önerilen bir uygulama değildir.</span><span class="sxs-lookup"><span data-stu-id="848ec-221">This is not a recommended practice, except in rare cases that usually occur when migrating to WCF from .NET Framework remoting.</span></span> <span data-ttu-id="848ec-222">Bu durumda, sınıfı yerine sınıfını kullanmanız gerekir <xref:System.Runtime.Serialization.NetDataContractSerializer> <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="848ec-222">In this case, you must use the <xref:System.Runtime.Serialization.NetDataContractSerializer> class instead of the <xref:System.Runtime.Serialization.DataContractSerializer> class.</span></span>  
  
 <span data-ttu-id="848ec-223"><xref:System.Runtime.Serialization.DataContractSerializer>Normalde nesne grafiklerini nesne ağaçları olarak serileştirir.</span><span class="sxs-lookup"><span data-stu-id="848ec-223">The <xref:System.Runtime.Serialization.DataContractSerializer> normally serializes object graphs as object trees.</span></span> <span data-ttu-id="848ec-224">Diğer bir deyişle, aynı nesneye birden çok kez bahsedildiğinde birden çok kez serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="848ec-224">That is, if the same object is referred to more than once, it is serialized more than once.</span></span> <span data-ttu-id="848ec-225">Örneğin, `PurchaseOrder` adresi ve adı Address olan iki alanı olan bir örneği göz önünde `billTo` bulundurun `shipTo` .</span><span class="sxs-lookup"><span data-stu-id="848ec-225">For example, consider a `PurchaseOrder` instance that has two fields of type Address called `billTo` and `shipTo`.</span></span> <span data-ttu-id="848ec-226">Her iki alan de aynı adres örneğine ayarlanmışsa serileştirme ve serisini kaldırma sonrasında iki özdeş adres örneği vardır.</span><span class="sxs-lookup"><span data-stu-id="848ec-226">If both fields are set to the same Address instance, there are two identical Address instances after serialization and deserialization.</span></span> <span data-ttu-id="848ec-227">Bu, XML 'deki nesne grafiklerini temsil etmek için standart birlikte çalışabilen bir yol olmadığından ( <xref:System.Xml.Serialization.XmlSerializer> ve üzerinde önceki bölümde açıklandığı gibi, üzerinde bulunan eskı SOAP kodlamalı standart dışında), bu yapılır `Style` `Use` .</span><span class="sxs-lookup"><span data-stu-id="848ec-227">This is done because there is no standard interoperable way to represent object graphs in XML (except for the legacy SOAP encoded standard available on the <xref:System.Xml.Serialization.XmlSerializer>, as described in the previous section on `Style` and `Use`).</span></span> <span data-ttu-id="848ec-228">Ağaç olarak nesne grafiklerinin serileştirilmesi, örneğin döngüsel başvuruları olan grafikler serileştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="848ec-228">Serializing object graphs as trees has certain disadvantages, for example, graphs with circular references cannot be serialized.</span></span> <span data-ttu-id="848ec-229">Bazen, birlikte çalışabilir olmasa bile, doğru nesne grafiği serileştirmesine geçiş yapmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="848ec-229">Occasionally, it is necessary to switch to true object graph serialization, even though it is not interoperable.</span></span> <span data-ttu-id="848ec-230">Bu, <xref:System.Runtime.Serialization.DataContractSerializer> `preserveObjectReferences` olarak ayarlanan parametresiyle oluşturulan kullanılarak yapılabilir `true` .</span><span class="sxs-lookup"><span data-stu-id="848ec-230">This can be done by using the <xref:System.Runtime.Serialization.DataContractSerializer> constructed with the `preserveObjectReferences` parameter set to `true`.</span></span>  
  
 <span data-ttu-id="848ec-231">Bazen, yerleşik serileştiriciler senaryonuz için yeterli değildir.</span><span class="sxs-lookup"><span data-stu-id="848ec-231">Occasionally, the built-in serializers are not enough for your scenario.</span></span> <span data-ttu-id="848ec-232">Çoğu durumda, hem hem de <xref:System.Runtime.Serialization.XmlObjectSerializer> türeten olan soyutlamayı kullanmaya devam edebilirsiniz <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.NetDataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="848ec-232">In most cases, you can still use the <xref:System.Runtime.Serialization.XmlObjectSerializer> abstraction from which both the <xref:System.Runtime.Serialization.DataContractSerializer> and the <xref:System.Runtime.Serialization.NetDataContractSerializer> derive.</span></span>  
  
 <span data-ttu-id="848ec-233">Önceki üç durum (.NET tür koruma, nesne Graph koruması ve tamamen özel `XmlObjectSerializer` tabanlı serileştirme), hepsi özel bir seri hale getirici takılmasına gerek duyar.</span><span class="sxs-lookup"><span data-stu-id="848ec-233">The previous three cases (.NET type preservation, object graph preservation, and completely custom `XmlObjectSerializer`-based serialization) all require a custom serializer be plugged in.</span></span> <span data-ttu-id="848ec-234">Bunu yapmak için şu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="848ec-234">To do this, perform the following steps:</span></span>  
  
1. <span data-ttu-id="848ec-235">Öğesinden türetilen kendi davranışınızı yazın <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> .</span><span class="sxs-lookup"><span data-stu-id="848ec-235">Write your own behavior deriving from the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>.</span></span>  
  
2. <span data-ttu-id="848ec-236">`CreateSerializer`Kendi seri hale getirinizi (ya da <xref:System.Runtime.Serialization.NetDataContractSerializer> <xref:System.Runtime.Serialization.DataContractSerializer> `preserveObjectReferences` `true` kendi özel olarak ayarlanan <xref:System.Runtime.Serialization.XmlObjectSerializer> ) döndürmek için iki yöntemi geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="848ec-236">Override the two `CreateSerializer` methods to return your own serializer (either the <xref:System.Runtime.Serialization.NetDataContractSerializer>, the <xref:System.Runtime.Serialization.DataContractSerializer> with `preserveObjectReferences` set to `true`, or your own custom <xref:System.Runtime.Serialization.XmlObjectSerializer>).</span></span>  
  
3. <span data-ttu-id="848ec-237">Hizmet konağını açmadan veya bir istemci kanalı oluşturmadan önce, mevcut <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> davranışı kaldırın ve önceki adımlarda oluşturduğunuz özel türetilmiş sınıfı takın.</span><span class="sxs-lookup"><span data-stu-id="848ec-237">Before opening the service host or creating a client channel, remove the existing <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> behavior and plug in the custom derived class that you created in the previous steps.</span></span>  
  
 <span data-ttu-id="848ec-238">Gelişmiş serileştirme kavramları hakkında daha fazla bilgi için bkz. [serileştirme ve seri durumundan çıkarma](serialization-and-deserialization.md).</span><span class="sxs-lookup"><span data-stu-id="848ec-238">For more information about advanced serialization concepts, see [Serialization and Deserialization](serialization-and-deserialization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="848ec-239">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="848ec-239">See also</span></span>

- [<span data-ttu-id="848ec-240">XmlSerializer Sınıfını Kullanma</span><span class="sxs-lookup"><span data-stu-id="848ec-240">Using the XmlSerializer Class</span></span>](using-the-xmlserializer-class.md)
- [<span data-ttu-id="848ec-241">Nasıl yapılır: Akışı Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="848ec-241">How to: Enable Streaming</span></span>](how-to-enable-streaming.md)
- [<span data-ttu-id="848ec-242">Nasıl yapılır: Bir Sınıf veya Yapı için Temel Bir Veri Sözleşmesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="848ec-242">How to: Create a Basic Data Contract for a Class or Structure</span></span>](how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
