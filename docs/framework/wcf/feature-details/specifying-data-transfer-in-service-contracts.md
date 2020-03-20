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
# <a name="specifying-data-transfer-in-service-contracts"></a><span data-ttu-id="03c36-102">Hizmet Sözleşmelerinde Veri Aktarımını Belirtme</span><span class="sxs-lookup"><span data-stu-id="03c36-102">Specifying Data Transfer in Service Contracts</span></span>
<span data-ttu-id="03c36-103">Windows Communication Foundation (WCF) bir mesajlaşma altyapısı olarak düşünülebilir.</span><span class="sxs-lookup"><span data-stu-id="03c36-103">The Windows Communication Foundation (WCF) can be thought of as a messaging infrastructure.</span></span> <span data-ttu-id="03c36-104">Hizmet işlemleri iletileri alabilir, işleyebilir ve ileti gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="03c36-104">Service operations can receive messages, process them, and send them messages.</span></span> <span data-ttu-id="03c36-105">İletiler işlem sözleşmeleri kullanılarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="03c36-105">Messages are described using operation contracts.</span></span> <span data-ttu-id="03c36-106">Örneğin, aşağıdaki sözleşmeyi göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="03c36-106">For example, consider the following contract.</span></span>  
  
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
  
 <span data-ttu-id="03c36-107">Burada, `GetAirfare` işlem hakkında `fromCity` bilgi içeren bir `toCity`iletiyi kabul eder ve sonra bir sayı içeren bir iletiyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="03c36-107">Here, the `GetAirfare` operation accepts a message with information about `fromCity` and `toCity`, and then returns a message that contains a number.</span></span>  
  
 <span data-ttu-id="03c36-108">Bu konu, bir işlem sözleşmesinin iletileri açıklayabileceği çeşitli yolları açıklar.</span><span class="sxs-lookup"><span data-stu-id="03c36-108">This topic explains the various ways in which an operation contract can describe messages.</span></span>  
  
## <a name="describing-messages-by-using-parameters"></a><span data-ttu-id="03c36-109">Parametreleri Kullanarak İletileri Açıklama</span><span class="sxs-lookup"><span data-stu-id="03c36-109">Describing Messages by Using Parameters</span></span>  
 <span data-ttu-id="03c36-110">İletiyi açıklamanın en basit yolu parametre listesi ve iade değeri kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="03c36-110">The simplest way to describe a message is to use a parameter list and the return value.</span></span> <span data-ttu-id="03c36-111">Önceki örnekte, istek `fromCity` `toCity` iletisini tanımlamak için ve dize parametreleri kullanıldı ve yanıt iletisini açıklamak için float return value kullanıldı.</span><span class="sxs-lookup"><span data-stu-id="03c36-111">In the preceding example, the `fromCity` and `toCity` string parameters were used to describe the request message, and the float return value was used to describe the reply message.</span></span> <span data-ttu-id="03c36-112">Tek başına iade değeri bir yanıt iletisini açıklamak için yeterli değilse, çıkış parametreleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="03c36-112">If the return value alone is not enough to describe a reply message, out parameters may be used.</span></span> <span data-ttu-id="03c36-113">Örneğin, aşağıdaki işlem `fromCity` ve `toCity` istek iletisinde ve yanıt iletisinde para birimiyle birlikte bir sayı vardır:</span><span class="sxs-lookup"><span data-stu-id="03c36-113">For example, the following operation has `fromCity` and `toCity` in its request message, and a number together with a currency in its reply message:</span></span>  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, out string currency);  
```  
  
```vb  
<OperationContract()>  
    Function GetAirfare(fromCity As String, toCity As String) As Double  
```  
  
 <span data-ttu-id="03c36-114">Ayrıca, hem isteğin hem de yanıt iletisinin parametre parçasını yapmak için başvuru parametrelerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="03c36-114">Additionally, you may use reference parameters to make a parameter part of both the request and the reply message.</span></span> <span data-ttu-id="03c36-115">Parametreler serihale edilebilen (XML'e dönüştürülebilen) türlerden olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="03c36-115">The parameters must be of types that can be serialized (converted to XML).</span></span> <span data-ttu-id="03c36-116">Varsayılan olarak, WCF bu <xref:System.Runtime.Serialization.DataContractSerializer> dönüşümü gerçekleştirmek için sınıf adlı bir bileşen kullanır.</span><span class="sxs-lookup"><span data-stu-id="03c36-116">By default, WCF uses a component called the <xref:System.Runtime.Serialization.DataContractSerializer> class to perform this conversion.</span></span> <span data-ttu-id="03c36-117">Çoğu ilkel tür `int`(, `float`, `DateTime` `string`, ve .) desteklenir.</span><span class="sxs-lookup"><span data-stu-id="03c36-117">Most primitive types (such as `int`, `string`, `float`, and `DateTime`.) are supported.</span></span> <span data-ttu-id="03c36-118">Kullanıcı tanımlı türlerin normalde bir veri sözleşmesi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="03c36-118">User-defined types must normally have a data contract.</span></span> <span data-ttu-id="03c36-119">Daha fazla bilgi için [bkz.](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)</span><span class="sxs-lookup"><span data-stu-id="03c36-119">For more information, see [Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span></span>  
  
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
  
 <span data-ttu-id="03c36-120">Bazen, türlerinizi seri hale getirmek için yeterli `DataContractSerializer` değildir.</span><span class="sxs-lookup"><span data-stu-id="03c36-120">Occasionally, the `DataContractSerializer` is not adequate to serialize your types.</span></span> <span data-ttu-id="03c36-121">WCF alternatif bir serileştirme <xref:System.Xml.Serialization.XmlSerializer>motoru destekler, , ayrıca parametreleri serileştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="03c36-121">WCF supports an alternative serialization engine, the <xref:System.Xml.Serialization.XmlSerializer>, which you can also use to serialize parameters.</span></span> <span data-ttu-id="03c36-122">Bu <xref:System.Xml.Serialization.XmlSerializer> gibi öznitelikleri kullanarak ortaya çıkan XML üzerinde `XmlAttributeAttribute`daha fazla kontrol kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="03c36-122">The <xref:System.Xml.Serialization.XmlSerializer> allows you to use more control over the resultant XML using attributes such as the `XmlAttributeAttribute`.</span></span> <span data-ttu-id="03c36-123">Belirli bir işlem <xref:System.Xml.Serialization.XmlSerializer> için veya tüm hizmet için kullanmaya <xref:System.ServiceModel.XmlSerializerFormatAttribute> geçmek için, özniteliği bir işlem veya hizmetiçin uygulayın.</span><span class="sxs-lookup"><span data-stu-id="03c36-123">To switch to using the <xref:System.Xml.Serialization.XmlSerializer> for a particular operation or for the entire service, apply the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to an operation or a service.</span></span> <span data-ttu-id="03c36-124">Örnek:</span><span class="sxs-lookup"><span data-stu-id="03c36-124">For example:</span></span>  
  
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
  
 <span data-ttu-id="03c36-125">Daha fazla bilgi için Bkz. [XmlSerializer Sınıfını Kullanma.](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)</span><span class="sxs-lookup"><span data-stu-id="03c36-125">For more information, see [Using the XmlSerializer Class](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).</span></span> <span data-ttu-id="03c36-126">Bu konuda ayrıntılı olarak <xref:System.Xml.Serialization.XmlSerializer> ayrıntılı olarak bunu yapmak için özel nedenler yoksa burada gösterildiği gibi el ile geçiş tavsiye edilmez unutmayın.</span><span class="sxs-lookup"><span data-stu-id="03c36-126">Remember that manually switching to the <xref:System.Xml.Serialization.XmlSerializer> as shown here is not recommended unless you have specific reasons to do so as detailed in that topic.</span></span>  
  
 <span data-ttu-id="03c36-127">.NET parametre adlarını sözleşme adlarından yalıtmak için özniteliği kullanabilir <xref:System.ServiceModel.MessageParameterAttribute> ve sözleşme adını ayarlamak için `Name` özelliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="03c36-127">To isolate .NET parameter names from contract names, you can use the <xref:System.ServiceModel.MessageParameterAttribute> attribute, and use the `Name` property to set the contract name.</span></span> <span data-ttu-id="03c36-128">Örneğin, aşağıdaki işlem sözleşmesi bu konudaki ilk örneğe eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="03c36-128">For example, the following operation contract is equivalent to the first example in this topic.</span></span>  
  
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
  
## <a name="describing-empty-messages"></a><span data-ttu-id="03c36-129">Boş İletileri Açıklama</span><span class="sxs-lookup"><span data-stu-id="03c36-129">Describing Empty Messages</span></span>  
 <span data-ttu-id="03c36-130">Boş bir istek iletisi, giriş veya başvuru parametreleri olmadan açıklanabilir.</span><span class="sxs-lookup"><span data-stu-id="03c36-130">An empty request message can be described by having no input or reference parameters.</span></span> <span data-ttu-id="03c36-131">Örneğin, C#'da:</span><span class="sxs-lookup"><span data-stu-id="03c36-131">For example, in C#:</span></span>  
  
 `[OperationContract]`  
  
 `public int GetCurrentTemperature();`  
  
 <span data-ttu-id="03c36-132">Örneğin, Visual Basic'te:</span><span class="sxs-lookup"><span data-stu-id="03c36-132">For example, in Visual Basic:</span></span>  
  
 `<OperationContract()>`  
  
 `Function GetCurrentTemperature() as Integer`  
  
 <span data-ttu-id="03c36-133">Boş bir `void` yanıt iletisi, bir iade türüne sahip olarak açıklanabilir ve çıktı veya başvuru parametreleri yoktur.</span><span class="sxs-lookup"><span data-stu-id="03c36-133">An empty reply message can be described by having a `void` return type and no output or reference parameters.</span></span> <span data-ttu-id="03c36-134">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="03c36-134">For example in:</span></span>  
  
```csharp  
[OperationContract]  
public void SetTemperature(int temperature);  
```  
  
```vb  
<OperationContract()>  
Sub SetTemperature(temperature As Integer)  
```  
  
 <span data-ttu-id="03c36-135">Bu, tek yönlü bir işlemden farklıdır:</span><span class="sxs-lookup"><span data-stu-id="03c36-135">This is different from a one-way operation, such as:</span></span>  
  
```csharp  
[OperationContract(IsOneWay=true)]  
public void SetLightbulbStatus(bool isOn);  
```  
  
```vb  
<OperationContract(IsOneWay:=True)>  
Sub SetLightbulbStatus(isOne As Boolean)  
```  
  
 <span data-ttu-id="03c36-136">İşlem `SetTemperatureStatus` boş bir ileti döndürür.</span><span class="sxs-lookup"><span data-stu-id="03c36-136">The `SetTemperatureStatus` operation returns an empty message.</span></span> <span data-ttu-id="03c36-137">Giriş iletisini işlerken bir sorun varsa, bunun yerine bir hata döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="03c36-137">It may return a fault instead if there is a problem processing the input message.</span></span> <span data-ttu-id="03c36-138">Operasyon `SetLightbulbStatus` hiçbir şey döndürür.</span><span class="sxs-lookup"><span data-stu-id="03c36-138">The `SetLightbulbStatus` operation returns nothing.</span></span> <span data-ttu-id="03c36-139">Bu işlemden kaynaklanan bir hata durumunu iletmenin bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="03c36-139">There is no way to communicate a fault condition from this operation.</span></span>  
  
## <a name="describing-messages-by-using-message-contracts"></a><span data-ttu-id="03c36-140">İleti Sözleşmelerini Kullanarak İletileri Açıklama</span><span class="sxs-lookup"><span data-stu-id="03c36-140">Describing Messages by Using Message Contracts</span></span>  
 <span data-ttu-id="03c36-141">İletinin tamamını temsil etmek için tek bir tür kullanmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="03c36-141">You may want to use a single type to represent the entire message.</span></span> <span data-ttu-id="03c36-142">Bu amaçla bir veri sözleşmesi kullanmak mümkün olsa da, bunu yapmanın önerilen yolu bir ileti sözleşmesi kullanmaktır—bu, ortaya çıkan XML'de gereksiz kaydırma düzeylerini önler.</span><span class="sxs-lookup"><span data-stu-id="03c36-142">While it is possible to use a data contract for this purpose, the recommended way to do this is to use a message contract—this avoids unnecessary levels of wrapping in the resultant XML.</span></span> <span data-ttu-id="03c36-143">Ayrıca, ileti sözleşmeleri, ortaya çıkan iletiler üzerinde daha fazla denetim uygulamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="03c36-143">Additionally, message contracts allow you to exercise more control over resultant messages.</span></span> <span data-ttu-id="03c36-144">Örneğin, ileti gövdesinde hangi bilgilerin ve hangilerinin ileti üstbilgilerinde olması gerektiğine karar verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="03c36-144">For instance, you can decide which pieces of information should be in the message body and which should be in the message headers.</span></span> <span data-ttu-id="03c36-145">Aşağıdaki örnek, ileti sözleşmelerinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="03c36-145">The following example shows the use of message contracts.</span></span>  
  
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
  
 <span data-ttu-id="03c36-146">Daha fazla bilgi için [İleti Sözleşmelerini Kullanma'ya](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="03c36-146">For more information, see [Using Message Contracts](../../../../docs/framework/wcf/feature-details/using-message-contracts.md).</span></span>  
  
 <span data-ttu-id="03c36-147">Önceki örnekte, <xref:System.Runtime.Serialization.DataContractSerializer> sınıf yine varsayılan olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="03c36-147">In the previous example, the <xref:System.Runtime.Serialization.DataContractSerializer> class is still used by default.</span></span> <span data-ttu-id="03c36-148">Sınıf <xref:System.Xml.Serialization.XmlSerializer> ileti sözleşmeleri ile de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="03c36-148">The <xref:System.Xml.Serialization.XmlSerializer> class can also be used with message contracts.</span></span> <span data-ttu-id="03c36-149">Bunu yapmak için, <xref:System.ServiceModel.XmlSerializerFormatAttribute> özniteliği işlem veya sözleşmeye uygulayın ve <xref:System.Xml.Serialization.XmlSerializer> ileti üstbilgilerinde ve gövde üyelerindeki sınıfla uyumlu türleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="03c36-149">To do this, apply the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to either the operation or the contract, and use types compatible with the <xref:System.Xml.Serialization.XmlSerializer> class in the message headers and body members.</span></span>  
  
## <a name="describing-messages-by-using-streams"></a><span data-ttu-id="03c36-150">Akışları Kullanarak İletileri Açıklama</span><span class="sxs-lookup"><span data-stu-id="03c36-150">Describing Messages by Using Streams</span></span>  
 <span data-ttu-id="03c36-151">İşlemlerde iletileri açıklamanın başka bir <xref:System.IO.Stream> yolu da sınıfı veya türetilmiş sınıflarından birini bir işlem sözleşmesinde veya ileti sözleşmesi gövdesi üyesi olarak kullanmaktır (bu durumda tek üye olmalıdır).</span><span class="sxs-lookup"><span data-stu-id="03c36-151">Another way to describe messages in operations is to use the <xref:System.IO.Stream> class or one of its derived classes in an operation contract or as a message contract body member (it must be the only member in this case).</span></span> <span data-ttu-id="03c36-152">Gelen iletiler için tür `Stream`,türetilmiş sınıfları kullanamazsınız olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="03c36-152">For incoming messages, the type must be `Stream`—you cannot use derived classes.</span></span>  
  
 <span data-ttu-id="03c36-153">WCF, serilaştırıcıyı çağırmak yerine, bir akıştan veri alır ve doğrudan giden bir iletiye koyar veya gelen bir iletiden veri alır ve doğrudan bir akışa koyar.</span><span class="sxs-lookup"><span data-stu-id="03c36-153">Instead of invoking the serializer, WCF retrieves data from a stream and puts it directly into an outgoing message, or retrieves data from an incoming message and puts it directly into a stream.</span></span> <span data-ttu-id="03c36-154">Aşağıdaki örnek, akışların kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="03c36-154">The following sample shows the use of streams.</span></span>  
  
```csharp  
[OperationContract]  
public Stream DownloadFile(string fileName);  
```  
  
```vb  
<OperationContract()>  
Function DownloadFile(fileName As String) As String  
```  
  
 <span data-ttu-id="03c36-155">Tek bir `Stream` ileti gövdesinde verileri birleştiremezsiniz ve akış dışı verileri birleştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="03c36-155">You cannot combine `Stream` and non-stream data in a single message body.</span></span> <span data-ttu-id="03c36-156">İleti üstbilgilerine ek verileri koymak için bir ileti sözleşmesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="03c36-156">Use a message contract to put the extra data in message headers.</span></span> <span data-ttu-id="03c36-157">Aşağıdaki örnek, işlem sözleşmesini tanımlarken akışların yanlış kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="03c36-157">The following example shows the incorrect usage of streams when defining the operation contract.</span></span>  
  
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
  
 <span data-ttu-id="03c36-158">Aşağıdaki örnek, bir işlem sözleşmesi tanımlarken akışların doğru kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="03c36-158">The following sample shows the correct usage of streams when defining an operation contract.</span></span>  
  
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
  
 <span data-ttu-id="03c36-159">Daha fazla bilgi için [Bkz. Büyük Veri ve Akış.](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)</span><span class="sxs-lookup"><span data-stu-id="03c36-159">For more information, see [Large Data and Streaming](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).</span></span>  
  
## <a name="using-the-message-class"></a><span data-ttu-id="03c36-160">İleti Sınıfını Kullanma</span><span class="sxs-lookup"><span data-stu-id="03c36-160">Using the Message Class</span></span>  
 <span data-ttu-id="03c36-161">Gönderilen veya alınan iletiler üzerinde tam programlı denetime sahip olmak için, aşağıdaki örnek kodda gösterildiği gibi <xref:System.ServiceModel.Channels.Message> sınıfı doğrudan kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="03c36-161">To have complete programmatic control over messages sent or received, you can use the <xref:System.ServiceModel.Channels.Message> class directly, as shown in the following example code.</span></span>  
  
```csharp  
[OperationContract]  
public void LogMessage(Message m);  
```  
  
```vb  
<OperationContract()>  
Sub LogMessage(m As Message)  
```  
  
 <span data-ttu-id="03c36-162">Bu, [İleti Sınıfı'nı kullanırken](../../../../docs/framework/wcf/feature-details/using-the-message-class.md)ayrıntılı olarak açıklanan gelişmiş bir senaryodur.</span><span class="sxs-lookup"><span data-stu-id="03c36-162">This is an advanced scenario, which is described in detail in [Using the Message Class](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).</span></span>  
  
## <a name="describing-fault-messages"></a><span data-ttu-id="03c36-163">Hata İletilerini Açıklama</span><span class="sxs-lookup"><span data-stu-id="03c36-163">Describing Fault Messages</span></span>  
 <span data-ttu-id="03c36-164">İade değeri ve çıktı veya başvuru parametreleri tarafından açıklanan iletilere ek olarak, tek yönlü olmayan herhangi bir işlem en az iki olası ileti döndürebilir: normal yanıt iletisi ve hata iletisi.</span><span class="sxs-lookup"><span data-stu-id="03c36-164">In addition to the messages that are described by the return value and output or reference parameters, any operation that is not one-way can return at least two possible messages: its normal response message and a fault message.</span></span> <span data-ttu-id="03c36-165">Aşağıdaki işlem sözleşmesini göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="03c36-165">Consider the following operation contract.</span></span>  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, DateTime date);  
```  
  
```vb  
<OperationContract()>  
Function GetAirfare(fromCity As String, toCity As String, date as DateTime)  
```  
  
 <span data-ttu-id="03c36-166">Bu işlem, bir sayı içeren `float` normal bir ileti veya bir hata kodu ve açıklama içeren bir hata iletisi döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="03c36-166">This operation may either return a normal message that contains a `float` number, or a fault message that contains a fault code and a description.</span></span> <span data-ttu-id="03c36-167">Bunu, hizmet uygulamanızda <xref:System.ServiceModel.FaultException> bir atarak başarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="03c36-167">You can accomplish this by throwing a <xref:System.ServiceModel.FaultException> in your service implementation.</span></span>  
  
 <span data-ttu-id="03c36-168">Özniteliği kullanarak <xref:System.ServiceModel.FaultContractAttribute> ek olası hata iletileri belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="03c36-168">You can specify additional possible fault messages by using the <xref:System.ServiceModel.FaultContractAttribute> attribute.</span></span> <span data-ttu-id="03c36-169">Ek <xref:System.Runtime.Serialization.DataContractSerializer>hatalar, aşağıdaki örnek kodda gösterildiği gibi , kullanılarak serileştirilebilir olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="03c36-169">The additional faults must be serializable using the <xref:System.Runtime.Serialization.DataContractSerializer>, as shown in the following example code.</span></span>  
  
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
  
 <span data-ttu-id="03c36-170">Bu ek hatalar, uygun veri <xref:System.ServiceModel.FaultException%601> sözleşmesi türünden bir hata atılarak oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="03c36-170">These additional faults can be generated by throwing a <xref:System.ServiceModel.FaultException%601> of the appropriate data contract type.</span></span> <span data-ttu-id="03c36-171">Daha fazla bilgi için [bkz.](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)</span><span class="sxs-lookup"><span data-stu-id="03c36-171">For more information, see [Handling Exceptions and Faults](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).</span></span>  
  
 <span data-ttu-id="03c36-172">Hataları açıklamak <xref:System.Xml.Serialization.XmlSerializer> için sınıfı kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="03c36-172">You cannot use the <xref:System.Xml.Serialization.XmlSerializer> class to describe faults.</span></span> <span data-ttu-id="03c36-173">Hata <xref:System.ServiceModel.XmlSerializerFormatAttribute> sözleşmeleri üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="03c36-173">The <xref:System.ServiceModel.XmlSerializerFormatAttribute> has no effect on fault contracts.</span></span>  
  
## <a name="using-derived-types"></a><span data-ttu-id="03c36-174">Türemiş Türleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="03c36-174">Using Derived Types</span></span>  
 <span data-ttu-id="03c36-175">Bir işlemde veya ileti sözleşmesinde bir temel türü kullanmak ve ardından işlemi gerçekten çağırırken türetilmiş bir tür kullanmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="03c36-175">You may want to use a base type in an operation or a message contract, and then use a derived type when actually invoking the operation.</span></span> <span data-ttu-id="03c36-176">Bu durumda, türemiş <xref:System.ServiceModel.ServiceKnownTypeAttribute> türlerin kullanımına izin vermek için öznitelik veya bazı alternatif mekanizma kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="03c36-176">In this case, you must use either the <xref:System.ServiceModel.ServiceKnownTypeAttribute> attribute or some alternative mechanism to allow the use of derived types.</span></span> <span data-ttu-id="03c36-177">Aşağıdaki işlemi göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="03c36-177">Consider the following operation.</span></span>  
  
```csharp  
[OperationContract]  
public bool IsLibraryItemAvailable(LibraryItem item);  
```  
  
```vb
<OperationContract()>  
    Function IsLibraryItemAvailable(item As LibraryItem) As Boolean  
```  
  
 <span data-ttu-id="03c36-178">Varsayalım ki `Book` iki `Magazine`tür, `LibraryItem`ve , türetilmiştir .</span><span class="sxs-lookup"><span data-stu-id="03c36-178">Assume that two types, `Book` and `Magazine`, derive from `LibraryItem`.</span></span> <span data-ttu-id="03c36-179">`IsLibraryItemAvailable` Bu tür işlemleri kullanmak için işlemi aşağıdaki gibi değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="03c36-179">To use these types in the `IsLibraryItemAvailable` operation, you can change the operation as follows:</span></span>  
  
 `[OperationContract]`  
  
 `[ServiceKnownType(typeof(Book))]`  
  
 `[ServiceKnownType(typeof(Magazine))]`  
  
 `public bool IsLibraryItemAvailable(LibraryItem item);`  
  
 <span data-ttu-id="03c36-180">Alternatif olarak, aşağıdaki <xref:System.Runtime.Serialization.KnownTypeAttribute> örnek kodda <xref:System.Runtime.Serialization.DataContractSerializer> gösterildiği gibi, varsayılan kullanımda özniteliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="03c36-180">Alternatively, you can use the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute when the default <xref:System.Runtime.Serialization.DataContractSerializer> is in use, as shown in the following example code.</span></span>  
  
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
  
 <span data-ttu-id="03c36-181">Özniteliği kullanırken <xref:System.Xml.Serialization.XmlIncludeAttribute> <xref:System.Xml.Serialization.XmlSerializer>kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="03c36-181">You can use the <xref:System.Xml.Serialization.XmlIncludeAttribute> attribute when using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
 <span data-ttu-id="03c36-182">Özniteliği bir <xref:System.ServiceModel.ServiceKnownTypeAttribute> işlemiçin veya tüm hizmete uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="03c36-182">You can apply the <xref:System.ServiceModel.ServiceKnownTypeAttribute> attribute to an operation or to the entire service.</span></span> <span data-ttu-id="03c36-183">Öznitelik gibi <xref:System.Runtime.Serialization.KnownTypeAttribute> bilinen türlerin listesini almak için aramak için bir tür veya yöntemin adını kabul eder.</span><span class="sxs-lookup"><span data-stu-id="03c36-183">It accepts either a type or the name of the method to call to get a list of known types, just like the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute.</span></span> <span data-ttu-id="03c36-184">Daha fazla bilgi için [bkz.](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)</span><span class="sxs-lookup"><span data-stu-id="03c36-184">For more information, see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="specifying-the-use-and-style"></a><span data-ttu-id="03c36-185">Kullanım ve Stil belirtme</span><span class="sxs-lookup"><span data-stu-id="03c36-185">Specifying the Use and Style</span></span>  
 <span data-ttu-id="03c36-186">Web Hizmetleri Açıklama Dili (WSDL) kullanarak hizmetleri açıklarken, sık kullanılan iki stil Belge ve uzak yordam çağrısı (RPC) olur.</span><span class="sxs-lookup"><span data-stu-id="03c36-186">When describing services using Web Services Description Language (WSDL), the two commonly used styles are Document and remote procedure call (RPC).</span></span> <span data-ttu-id="03c36-187">Belge stilinde, tüm ileti gövdesi şema kullanılarak tanımlanır ve WSDL, bu şemadaki öğelere atıfta bulunarak çeşitli ileti gövdesi parçalarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="03c36-187">In the Document style, the entire message body is described using the schema, and the WSDL describes the various message body parts by referring to elements within that schema.</span></span> <span data-ttu-id="03c36-188">RPC stilinde, WSDL bir öğe yerine her ileti parçası için bir şema türü anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="03c36-188">In the RPC style, the WSDL refers to a schema type for each message part rather than an element.</span></span> <span data-ttu-id="03c36-189">Bazı durumlarda, bu stillerden birini el ile seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="03c36-189">In some cases, you have to manually select one of these styles.</span></span> <span data-ttu-id="03c36-190">Bunu, özniteliği uygulayarak <xref:System.ServiceModel.DataContractFormatAttribute> ve `Style` özelliği ayarlayarak (kullanımda olduğunda) <xref:System.Runtime.Serialization.DataContractSerializer> veya `Style` <xref:System.ServiceModel.XmlSerializerFormatAttribute> özniteliği ayarlayarak (kullanırken) <xref:System.Xml.Serialization.XmlSerializer>yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="03c36-190">You can do this by applying the <xref:System.ServiceModel.DataContractFormatAttribute> attribute and setting the `Style` property (when the <xref:System.Runtime.Serialization.DataContractSerializer> is in use), or by setting `Style` on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute (when using the <xref:System.Xml.Serialization.XmlSerializer>).</span></span>  
  
 <span data-ttu-id="03c36-191">Ayrıca, serixml iki form <xref:System.Xml.Serialization.XmlSerializer> destekler: `Literal` `Encoded`ve .</span><span class="sxs-lookup"><span data-stu-id="03c36-191">Additionally, the <xref:System.Xml.Serialization.XmlSerializer> supports two forms of serialized XML: `Literal` and `Encoded`.</span></span> <span data-ttu-id="03c36-192">`Literal`en yaygın olarak kabul edilen formdur ve <xref:System.Runtime.Serialization.DataContractSerializer> tek form destekler.</span><span class="sxs-lookup"><span data-stu-id="03c36-192">`Literal` is the most commonly accepted form, and is the only form the <xref:System.Runtime.Serialization.DataContractSerializer> supports.</span></span> <span data-ttu-id="03c36-193">`Encoded`SOAP belirtiminin bölüm 5'inde açıklanan eski bir formdur ve yeni hizmetler için önerilmez.</span><span class="sxs-lookup"><span data-stu-id="03c36-193">`Encoded` is a legacy form described in section 5 of the SOAP specification, and is not recommended for new services.</span></span> <span data-ttu-id="03c36-194">Moda geçmek `Encoded` için özelliği `Use` öznitelikte <xref:System.ServiceModel.XmlSerializerFormatAttribute> ' `Encoded`ye ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="03c36-194">To switch to `Encoded` mode, set the `Use` property on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to `Encoded`.</span></span>  
  
 <span data-ttu-id="03c36-195">Çoğu durumda, ve `Style` `Use` özellikleri için varsayılan ayarları değiştirmemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="03c36-195">In most cases, you should not change the default settings for the `Style` and `Use` properties.</span></span>  
  
## <a name="controlling-the-serialization-process"></a><span data-ttu-id="03c36-196">Serileştirme İşlemini Denetleme</span><span class="sxs-lookup"><span data-stu-id="03c36-196">Controlling the Serialization Process</span></span>  
 <span data-ttu-id="03c36-197">Verilerin seri hale getiriş biçimini özelleştirmek için bir dizi şey yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="03c36-197">You can do a number of things to customize the way data is serialized.</span></span>  
  
### <a name="changing-server-serialization-settings"></a><span data-ttu-id="03c36-198">Sunucu Serileştirme Ayarlarını Değiştirme</span><span class="sxs-lookup"><span data-stu-id="03c36-198">Changing Server Serialization Settings</span></span>  
 <span data-ttu-id="03c36-199">Varsayılan <xref:System.Runtime.Serialization.DataContractSerializer> kullanımda yken, hizmete öznitelik uygulayarak <xref:System.ServiceModel.ServiceBehaviorAttribute> hizmetteki serileştirme işleminin bazı yönlerini denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="03c36-199">When the default <xref:System.Runtime.Serialization.DataContractSerializer> is in use, you can control some aspects of the serialization process on the service by applying the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to the service.</span></span> <span data-ttu-id="03c36-200">Özellikle, <xref:System.Runtime.Serialization.DataContractSerializer> deserialize `MaxItemsInObjectGraph` nesnelerin maksimum sayısını sınırlayan kota ayarlamak için özelliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="03c36-200">Specifically, you may use the `MaxItemsInObjectGraph` property to set the quota that limits the maximum number of objects the <xref:System.Runtime.Serialization.DataContractSerializer> deserializes.</span></span> <span data-ttu-id="03c36-201">Yuvarlak tripping `IgnoreExtensionDataObject` sürüm özelliğini kapatmak için özelliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="03c36-201">You can use the `IgnoreExtensionDataObject` property to turn off the round-tripping versioning feature.</span></span> <span data-ttu-id="03c36-202">Kotalar hakkında daha fazla bilgi için, [Veriler için Güvenlik Hususları'na](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="03c36-202">For more information about quotas, see [Security Considerations for Data](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).</span></span> <span data-ttu-id="03c36-203">Yuvarlama hakkında daha fazla bilgi için [İleri Uyumlu Veri Sözleşmeleri'ne](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="03c36-203">For more information about round-tripping, see [Forward-Compatible Data Contracts](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).</span></span>  
  
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
  
### <a name="serialization-behaviors"></a><span data-ttu-id="03c36-204">Serileştirme Davranışları</span><span class="sxs-lookup"><span data-stu-id="03c36-204">Serialization Behaviors</span></span>  
 <span data-ttu-id="03c36-205">WCF'de, <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> belirli bir işlem için hangi serileştiricinin kullanıldığına bağlı olarak otomatik olarak takılı olan iki davranış mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="03c36-205">Two behaviors are available in WCF, the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> and the <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> that are automatically plugged in depending on which serializer is in use for a particular operation.</span></span> <span data-ttu-id="03c36-206">Bu davranışlar otomatik olarak uygulandığından, normalde bunların farkında olmak zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="03c36-206">Because these behaviors are applied automatically, you normally do not have to be aware of them.</span></span>  
  
 <span data-ttu-id="03c36-207">Ancak, `DataContractSerializerOperationBehavior` serileştirme `MaxItemsInObjectGraph` `IgnoreExtensionDataObject`işlemini `DataContractSurrogate` özelleştirmek için kullanabileceğiniz , ve özellikleri vardır.</span><span class="sxs-lookup"><span data-stu-id="03c36-207">However, the `DataContractSerializerOperationBehavior` has the `MaxItemsInObjectGraph`, `IgnoreExtensionDataObject`, and `DataContractSurrogate` properties that you may use to customize the serialization process.</span></span> <span data-ttu-id="03c36-208">İlk iki özellik önceki bölümde tartışılan aynı anlama sahiptir.</span><span class="sxs-lookup"><span data-stu-id="03c36-208">The first two properties have the same meaning as discussed in the previous section.</span></span> <span data-ttu-id="03c36-209">Serileştirme işlemini `DataContractSurrogate` özelleştirmek ve genişletmek için güçlü bir mekanizma olan veri sözleşmesi vekillerini etkinleştirmek için özelliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="03c36-209">You can use the `DataContractSurrogate` property to enable data contract surrogates, which are a powerful mechanism for customizing and extending the serialization process.</span></span> <span data-ttu-id="03c36-210">Daha fazla bilgi için [Bkz. Veri Sözleşmesi Suretleri.](../../../../docs/framework/wcf/extending/data-contract-surrogates.md)</span><span class="sxs-lookup"><span data-stu-id="03c36-210">For more information, see [Data Contract Surrogates](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).</span></span>  
  
 <span data-ttu-id="03c36-211">Hem istemci `DataContractSerializerOperationBehavior` hem de sunucu serileştirmesini özelleştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="03c36-211">You can use the `DataContractSerializerOperationBehavior` to customize both client and server serialization.</span></span> <span data-ttu-id="03c36-212">Aşağıdaki örnek, istemcideki `MaxItemsInObjectGraph` kotanın nasıl artırılabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="03c36-212">The following example shows how to increase the `MaxItemsInObjectGraph` quota on the client.</span></span>  
  
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
  
<span data-ttu-id="03c36-213">Aşağıda, kendi barındırılan durumda, hizmetteki eşdeğer kod veeşdeğer kod vereb vardır:</span><span class="sxs-lookup"><span data-stu-id="03c36-213">The following is the equivalent code on the service, in the self-hosted case:</span></span>
  
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
  
 <span data-ttu-id="03c36-214">Web tarafından barındırılan durumda, yeni `ServiceHost` bir türetilmiş sınıf oluşturmanız ve bunu takmak için bir hizmet ana bilgisayar fabrikası kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="03c36-214">In the Web-hosted case, you must create a new `ServiceHost` derived class and use a service host factory to plug it in.</span></span>  
  
### <a name="controlling-serialization-settings-in-configuration"></a><span data-ttu-id="03c36-215">Yapılandırmada Serileştirme Ayarlarını Denetleme</span><span class="sxs-lookup"><span data-stu-id="03c36-215">Controlling Serialization Settings in Configuration</span></span>  
 <span data-ttu-id="03c36-216">Ve `MaxItemsInObjectGraph` `IgnoreExtensionDataObject` aşağıdaki örnekte gösterildiği `dataContractSerializer` gibi, bitiş noktası veya hizmet davranışı kullanılarak yapılandırma yoluyla denetlenebilir.</span><span class="sxs-lookup"><span data-stu-id="03c36-216">The `MaxItemsInObjectGraph` and `IgnoreExtensionDataObject` can be controlled through configuration by using the `dataContractSerializer` endpoint or service behavior, as shown in the following example.</span></span>  
  
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
  
### <a name="shared-type-serialization-object-graph-preservation-and-custom-serializers"></a><span data-ttu-id="03c36-217">Paylaşılan Tür Serileştirme, Nesne Grafiği Koruma ve Özel Serializers</span><span class="sxs-lookup"><span data-stu-id="03c36-217">Shared Type Serialization, Object Graph Preservation, and Custom Serializers</span></span>  
 <span data-ttu-id="03c36-218">Seri, <xref:System.Runtime.Serialization.DataContractSerializer> .NET türü adlarını değil, veri sözleşme adlarını kullanarak serihale eder.</span><span class="sxs-lookup"><span data-stu-id="03c36-218">The <xref:System.Runtime.Serialization.DataContractSerializer> serializes using data contract names and not .NET type names.</span></span> <span data-ttu-id="03c36-219">Bu, hizmet odaklı mimari ilkeleriyle tutarlıdır ve büyük ölçüde esneklik sağlar—.NET türleri tel sözleşmesini etkilemeden değişebilir.</span><span class="sxs-lookup"><span data-stu-id="03c36-219">This is consistent with service-oriented architecture tenets and allows for a great degree of flexibility—the .NET types can change without affecting the wire contract.</span></span> <span data-ttu-id="03c36-220">Nadir durumlarda, gerçek .NET türü adlarını seri hale getirmek, böylelikle istemci ve sunucu arasında .NET Framework remoting teknolojisine benzer sıkı bir bağlantı sağlamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="03c36-220">In rare cases, you may want to serialize actual .NET type names, thereby introducing a tight coupling between the client and the server, similar to the .NET Framework remoting technology.</span></span> <span data-ttu-id="03c36-221">Bu, genellikle .NET Framework remoting'den WCF'ye geçiş yaparken meydana gelen nadir durumlar dışında önerilen bir uygulama değildir.</span><span class="sxs-lookup"><span data-stu-id="03c36-221">This is not a recommended practice, except in rare cases that usually occur when migrating to WCF from .NET Framework remoting.</span></span> <span data-ttu-id="03c36-222">Bu durumda, <xref:System.Runtime.Serialization.NetDataContractSerializer> <xref:System.Runtime.Serialization.DataContractSerializer> sınıf yerine sınıfı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="03c36-222">In this case, you must use the <xref:System.Runtime.Serialization.NetDataContractSerializer> class instead of the <xref:System.Runtime.Serialization.DataContractSerializer> class.</span></span>  
  
 <span data-ttu-id="03c36-223">Normalde <xref:System.Runtime.Serialization.DataContractSerializer> nesne grafiklerini nesne ağaçları olarak serihale eder.</span><span class="sxs-lookup"><span data-stu-id="03c36-223">The <xref:System.Runtime.Serialization.DataContractSerializer> normally serializes object graphs as object trees.</span></span> <span data-ttu-id="03c36-224">Diğer bir yerde, aynı nesneye birden çok kez atıfta bulunulması durumunda, birden çok kez seri hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="03c36-224">That is, if the same object is referred to more than once, it is serialized more than once.</span></span> <span data-ttu-id="03c36-225">Örneğin, tür `PurchaseOrder` Adresi adlı `billTo` iki alan ait `shipTo`bir örnek düşünün ve .</span><span class="sxs-lookup"><span data-stu-id="03c36-225">For example, consider a `PurchaseOrder` instance that has two fields of type Address called `billTo` and `shipTo`.</span></span> <span data-ttu-id="03c36-226">Her iki alan da aynı Adres örneğine ayarlanmışsa, serileştirme ve deserialization sonra iki özdeş Adres örnekleri vardır.</span><span class="sxs-lookup"><span data-stu-id="03c36-226">If both fields are set to the same Address instance, there are two identical Address instances after serialization and deserialization.</span></span> <span data-ttu-id="03c36-227">XML'deki nesne grafiklerini temsil etmenin standart bir birlikte çalışabilir yolu olmadığı için bu işlem yapılır <xref:System.Xml.Serialization.XmlSerializer>(önceki bölümde `Style` açıklandığı gibi, eski SOAP kodlanmış standart `Use`dışında).</span><span class="sxs-lookup"><span data-stu-id="03c36-227">This is done because there is no standard interoperable way to represent object graphs in XML (except for the legacy SOAP encoded standard available on the <xref:System.Xml.Serialization.XmlSerializer>, as described in the previous section on `Style` and `Use`).</span></span> <span data-ttu-id="03c36-228">Nesne grafiklerini ağaç olarak serihale getirmenin belirli dezavantajları vardır, örneğin dairesel referanslı grafikler serileştirilemez.</span><span class="sxs-lookup"><span data-stu-id="03c36-228">Serializing object graphs as trees has certain disadvantages, for example, graphs with circular references cannot be serialized.</span></span> <span data-ttu-id="03c36-229">Bazen, birlikte çalışabilir olmasa bile gerçek nesne grafiği serileştirme geçmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="03c36-229">Occasionally, it is necessary to switch to true object graph serialization, even though it is not interoperable.</span></span> <span data-ttu-id="03c36-230">Bu <xref:System.Runtime.Serialization.DataContractSerializer> `preserveObjectReferences` parametre kümesi ile inşa kullanılarak `true`yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="03c36-230">This can be done by using the <xref:System.Runtime.Serialization.DataContractSerializer> constructed with the `preserveObjectReferences` parameter set to `true`.</span></span>  
  
 <span data-ttu-id="03c36-231">Bazen, yerleşik serializers senaryonuz için yeterli değildir.</span><span class="sxs-lookup"><span data-stu-id="03c36-231">Occasionally, the built-in serializers are not enough for your scenario.</span></span> <span data-ttu-id="03c36-232">Çoğu durumda, hala hem <xref:System.Runtime.Serialization.XmlObjectSerializer> de <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.NetDataContractSerializer> türetilmiştir soyutlama kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="03c36-232">In most cases, you can still use the <xref:System.Runtime.Serialization.XmlObjectSerializer> abstraction from which both the <xref:System.Runtime.Serialization.DataContractSerializer> and the <xref:System.Runtime.Serialization.NetDataContractSerializer> derive.</span></span>  
  
 <span data-ttu-id="03c36-233">Önceki üç durumda (.NET türü koruma, nesne `XmlObjectSerializer`grafiği koruma ve tamamen özel tabanlı serileştirme) tüm özel bir serializer takılı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="03c36-233">The previous three cases (.NET type preservation, object graph preservation, and completely custom `XmlObjectSerializer`-based serialization) all require a custom serializer be plugged in.</span></span> <span data-ttu-id="03c36-234">Bunu yapmak için şu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="03c36-234">To do this, perform the following steps:</span></span>  
  
1. <span data-ttu-id="03c36-235">Kendi davranışınızı <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>yazın.</span><span class="sxs-lookup"><span data-stu-id="03c36-235">Write your own behavior deriving from the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>.</span></span>  
  
2. <span data-ttu-id="03c36-236">Kendi serializer dönmek için `CreateSerializer` iki yöntem geçersiz <xref:System.Runtime.Serialization.NetDataContractSerializer>kılın <xref:System.Runtime.Serialization.DataContractSerializer> `preserveObjectReferences` (ya `true`, ile <xref:System.Runtime.Serialization.XmlObjectSerializer>ayarlanmış , ya da kendi özel).</span><span class="sxs-lookup"><span data-stu-id="03c36-236">Override the two `CreateSerializer` methods to return your own serializer (either the <xref:System.Runtime.Serialization.NetDataContractSerializer>, the <xref:System.Runtime.Serialization.DataContractSerializer> with `preserveObjectReferences` set to `true`, or your own custom <xref:System.Runtime.Serialization.XmlObjectSerializer>).</span></span>  
  
3. <span data-ttu-id="03c36-237">Hizmet ana bilgisayarını açmadan veya istemci <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> kanalı oluşturmadan önce, varolan davranışı kaldırın ve önceki adımlarda oluşturduğunuz özel türemiş sınıfı takın.</span><span class="sxs-lookup"><span data-stu-id="03c36-237">Before opening the service host or creating a client channel, remove the existing <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> behavior and plug in the custom derived class that you created in the previous steps.</span></span>  
  
 <span data-ttu-id="03c36-238">Gelişmiş serileştirme kavramları hakkında daha fazla bilgi için [serileştirme ve deserialization](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="03c36-238">For more information about advanced serialization concepts, see [Serialization and Deserialization](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03c36-239">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="03c36-239">See also</span></span>

- [<span data-ttu-id="03c36-240">XmlSerializer Sınıfını Kullanma</span><span class="sxs-lookup"><span data-stu-id="03c36-240">Using the XmlSerializer Class</span></span>](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)
- [<span data-ttu-id="03c36-241">Nasıl yapılır: Akışı Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="03c36-241">How to: Enable Streaming</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)
- [<span data-ttu-id="03c36-242">Nasıl yapılır: Bir Sınıf veya Yapı için Temel Bir Veri Sözleşmesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="03c36-242">How to: Create a Basic Data Contract for a Class or Structure</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
