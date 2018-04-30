---
title: Hizmet Sözleşmelerinde Veri Aktarımını Belirtme
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], data transfer
ms.assetid: 7c5a26c8-89c9-4bcb-a4bc-7131e6d01f0c
caps.latest.revision: 38
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 852519dc1edc499511652f4027f4cd4eed6eef98
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="specifying-data-transfer-in-service-contracts"></a><span data-ttu-id="0e32a-102">Hizmet Sözleşmelerinde Veri Aktarımını Belirtme</span><span class="sxs-lookup"><span data-stu-id="0e32a-102">Specifying Data Transfer in Service Contracts</span></span>
<span data-ttu-id="0e32a-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] , Bir Mesajlaşma altyapısı düşünülebilir.</span><span class="sxs-lookup"><span data-stu-id="0e32a-103">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] can be thought of as a messaging infrastructure.</span></span> <span data-ttu-id="0e32a-104">Hizmet işlemleri iletilerini işlemek ve iletileri göndermek.</span><span class="sxs-lookup"><span data-stu-id="0e32a-104">Service operations can receive messages, process them, and send them messages.</span></span> <span data-ttu-id="0e32a-105">İletileri işlemi sözleşmeleri kullanma açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0e32a-105">Messages are described using operation contracts.</span></span> <span data-ttu-id="0e32a-106">Örneğin, aşağıdaki sözleşme göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="0e32a-106">For example, consider the following contract.</span></span>  
  
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
  
 <span data-ttu-id="0e32a-107">Burada, `GetAirfare` işlemi hakkında bilgi içeren bir ileti kabul `fromCity` ve `toCity`ve ardından bir sayı içeren bir ileti döndürür.</span><span class="sxs-lookup"><span data-stu-id="0e32a-107">Here, the `GetAirfare` operation accepts a message with information about `fromCity` and `toCity`, and then returns a message that contains a number.</span></span>  
  
 <span data-ttu-id="0e32a-108">Bu konuda, bir işlem sözleşmesi iletileri açıklayabilirsiniz çeşitli yolları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0e32a-108">This topic explains the various ways in which an operation contract can describe messages.</span></span>  
  
## <a name="describing-messages-by-using-parameters"></a><span data-ttu-id="0e32a-109">Parametreleri kullanarak açıklayan iletiler</span><span class="sxs-lookup"><span data-stu-id="0e32a-109">Describing Messages by Using Parameters</span></span>  
 <span data-ttu-id="0e32a-110">Bir ileti açıklamak için en basit yolu, bir parametre listesi ve dönüş değeri kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="0e32a-110">The simplest way to describe a message is to use a parameter list and the return value.</span></span> <span data-ttu-id="0e32a-111">Önceki örnekte `fromCity` ve `toCity` dizesi parametreleri, istek iletisi açıklamak için kullanıldı ve float dönüş değeri yanıt iletisi açıklamak için kullanıldı.</span><span class="sxs-lookup"><span data-stu-id="0e32a-111">In the preceding example, the `fromCity` and `toCity` string parameters were used to describe the request message, and the float return value was used to describe the reply message.</span></span> <span data-ttu-id="0e32a-112">Dönüş değeri tek başına bir yanıt iletisi açıklamak için yeterli değilse, out Parametreleri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0e32a-112">If the return value alone is not enough to describe a reply message, out parameters may be used.</span></span> <span data-ttu-id="0e32a-113">Örneğin, aşağıdaki işlemi sahip `fromCity` ve `toCity` istek iletisi ve bir sayı bir para birimi yanıt iletisi ile birlikte:</span><span class="sxs-lookup"><span data-stu-id="0e32a-113">For example, the following operation has `fromCity` and `toCity` in its request message, and a number together with a currency in its reply message:</span></span>  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, out string currency);  
```  
  
```vb  
<OperationContract()>  
    Function GetAirfare(fromCity As String, toCity As String) As Double  
```  
  
 <span data-ttu-id="0e32a-114">Ayrıca, istek ve yanıt iletisi parametresi parçası haline getirmek için başvuru parametreleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e32a-114">Additionally, you may use reference parameters to make a parameter part of both the request and the reply message.</span></span> <span data-ttu-id="0e32a-115">Parametreler (XML biçimine dönüştürülen) seri hale getirilebilir türler olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0e32a-115">The parameters must be of types that can be serialized (converted to XML).</span></span> <span data-ttu-id="0e32a-116">Varsayılan olarak, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] adında bir bileşen <xref:System.Runtime.Serialization.DataContractSerializer> bu dönüştürme gerçekleştirmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="0e32a-116">By default, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses a component called the <xref:System.Runtime.Serialization.DataContractSerializer> class to perform this conversion.</span></span> <span data-ttu-id="0e32a-117">En basit türler (gibi `int`, `string`, `float`, ve `DateTime`.) desteklenir.</span><span class="sxs-lookup"><span data-stu-id="0e32a-117">Most primitive types (such as `int`, `string`, `float`, and `DateTime`.) are supported.</span></span> <span data-ttu-id="0e32a-118">Kullanıcı tanımlı türler, normalde bir veri sözleşmesi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0e32a-118">User-defined types must normally have a data contract.</span></span> <span data-ttu-id="0e32a-119">Daha fazla bilgi için bkz: [kullanarak veri sözleşmeleri](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="0e32a-119">For more information, see [Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span></span>  
  
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
  
 <span data-ttu-id="0e32a-120">Bazen, `DataContractSerializer` türlerinizi serileştirmek yeterli değil.</span><span class="sxs-lookup"><span data-stu-id="0e32a-120">Occasionally, the `DataContractSerializer` is not adequate to serialize your types.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="0e32a-121"> bir alternatif serileştirme motoruna destekleyen <xref:System.Xml.Serialization.XmlSerializer>, hangi parametreleri seri hale getirmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e32a-121"> supports an alternative serialization engine, the <xref:System.Xml.Serialization.XmlSerializer>, which you can also use to serialize parameters.</span></span> <span data-ttu-id="0e32a-122"><xref:System.Xml.Serialization.XmlSerializer> Sonuç XML öznitelikleri gibi kullanma hakkında daha fazla denetime kullanmanıza olanak sağlayan `XmlAttributeAttribute`.</span><span class="sxs-lookup"><span data-stu-id="0e32a-122">The <xref:System.Xml.Serialization.XmlSerializer> allows you to use more control over the resultant XML using attributes such as the `XmlAttributeAttribute`.</span></span> <span data-ttu-id="0e32a-123">Kullanmaya geçmek <xref:System.Xml.Serialization.XmlSerializer> belirli bir işlem veya tüm hizmet için uygulama <xref:System.ServiceModel.XmlSerializerFormatAttribute> özniteliği bir işlem veya bir hizmet.</span><span class="sxs-lookup"><span data-stu-id="0e32a-123">To switch to using the <xref:System.Xml.Serialization.XmlSerializer> for a particular operation or for the entire service, apply the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to an operation or a service.</span></span> <span data-ttu-id="0e32a-124">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="0e32a-124">For example:</span></span>  
  
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
  
 <span data-ttu-id="0e32a-125">Daha fazla bilgi için bkz: [XmlSerializer sınıfını kullanma](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).</span><span class="sxs-lookup"><span data-stu-id="0e32a-125">For more information, see [Using the XmlSerializer Class](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).</span></span> <span data-ttu-id="0e32a-126">Bu el ile geçiş unutmayın <xref:System.Xml.Serialization.XmlSerializer> gösterildiği şekilde bu konudaki olarak ayrıntılı yapmak için belirli nedenleri yoksa burada önerilmez.</span><span class="sxs-lookup"><span data-stu-id="0e32a-126">Remember that manually switching to the <xref:System.Xml.Serialization.XmlSerializer> as shown here is not recommended unless you have specific reasons to do so as detailed in that topic.</span></span>  
  
 <span data-ttu-id="0e32a-127">.NET parametre adları sözleşme adlarından yalıtmak için kullanabileceğiniz <xref:System.ServiceModel.MessageParameterAttribute> özniteliği ve kullanmak `Name` sözleşme adı ayarlamak için özellik.</span><span class="sxs-lookup"><span data-stu-id="0e32a-127">To isolate .NET parameter names from contract names, you can use the <xref:System.ServiceModel.MessageParameterAttribute> attribute, and use the `Name` property to set the contract name.</span></span> <span data-ttu-id="0e32a-128">Örneğin, bu konudaki ilk örnek için aşağıdaki işlemi sözleşme eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="0e32a-128">For example, the following operation contract is equivalent to the first example in this topic.</span></span>  
  
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
  
## <a name="describing-empty-messages"></a><span data-ttu-id="0e32a-129">Açıklayan boş iletileri</span><span class="sxs-lookup"><span data-stu-id="0e32a-129">Describing Empty Messages</span></span>  
 <span data-ttu-id="0e32a-130">Hiçbir giriş veya başvuru parametreleri sağlayarak bir boş istek iletisi açıklanabilir.</span><span class="sxs-lookup"><span data-stu-id="0e32a-130">An empty request message can be described by having no input or reference parameters.</span></span> <span data-ttu-id="0e32a-131">Örneğin C# ' de:</span><span class="sxs-lookup"><span data-stu-id="0e32a-131">For example in C#:</span></span>  
  
 `[OperationContract]`  
  
 `public int GetCurrentTemperature();`  
  
 <span data-ttu-id="0e32a-132">Örneğin VB içinde:</span><span class="sxs-lookup"><span data-stu-id="0e32a-132">For example in VB:</span></span>  
  
 `<OperationContract()>`  
  
 `Function GetCurrentTemperature() as Integer`  
  
 <span data-ttu-id="0e32a-133">Bir boş yanıt iletisi sağlayarak açıklanabilir bir `void` dönüş türü ve hiçbir çıktı veya başvuru parametreleri.</span><span class="sxs-lookup"><span data-stu-id="0e32a-133">An empty reply message can be described by having a `void` return type and no output or reference parameters.</span></span> <span data-ttu-id="0e32a-134">Örnek için:</span><span class="sxs-lookup"><span data-stu-id="0e32a-134">For example in:</span></span>  
  
```csharp  
[OperationContract]  
public void SetTemperature(int temperature);  
```  
  
```vb  
<OperationContract()>  
Sub SetTemperature(temperature As Integer)  
```  
  
 <span data-ttu-id="0e32a-135">Bu gibi bir tek yönlü işleminden farklıdır:</span><span class="sxs-lookup"><span data-stu-id="0e32a-135">This is different from a one-way operation, such as:</span></span>  
  
```csharp  
[OperationContract(IsOneWay=true)]  
public void SetLightbulbStatus(bool isOn);  
```  
  
```vb  
<OperationContract(IsOneWay:=True)>  
Sub SetLightbulbStatus(isOne As Boolean)  
```  
  
 <span data-ttu-id="0e32a-136">`SetTemperatureStatus` İşlemi boş bir ileti döndürür.</span><span class="sxs-lookup"><span data-stu-id="0e32a-136">The `SetTemperatureStatus` operation returns an empty message.</span></span> <span data-ttu-id="0e32a-137">Giriş ileti işlenirken bir sorun varsa, bunun yerine bir hata döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="0e32a-137">It may return a fault instead if there is a problem processing the input message.</span></span> <span data-ttu-id="0e32a-138">`SetLightbulbStatus` İşlemi hiçbir şey döndürür.</span><span class="sxs-lookup"><span data-stu-id="0e32a-138">The `SetLightbulbStatus` operation returns nothing.</span></span> <span data-ttu-id="0e32a-139">Bu işlem hata durumundan iletişim kurmak için bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="0e32a-139">There is no way to communicate a fault condition from this operation.</span></span>  
  
## <a name="describing-messages-by-using-message-contracts"></a><span data-ttu-id="0e32a-140">İleti sözleşmeleri kullanarak açıklayan iletiler</span><span class="sxs-lookup"><span data-stu-id="0e32a-140">Describing Messages by Using Message Contracts</span></span>  
 <span data-ttu-id="0e32a-141">İletinin tamamını temsil etmek için tek bir türü kullanmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e32a-141">You may want to use a single type to represent the entire message.</span></span> <span data-ttu-id="0e32a-142">Bu amaç için bir veri sözleşmesi kullanmak mümkün olsa da, bunu yapmak için önerilen yöntem ileti sözleşmesi kullanmaktır — bu sonuç XML kaydırma gereksiz düzeylerini önler.</span><span class="sxs-lookup"><span data-stu-id="0e32a-142">While it is possible to use a data contract for this purpose, the recommended way to do this is to use a message contract—this avoids unnecessary levels of wrapping in the resultant XML.</span></span> <span data-ttu-id="0e32a-143">Ayrıca, ileti sözleşmeleri sonuç iletileri üzerinden daha fazla denetim izin verir.</span><span class="sxs-lookup"><span data-stu-id="0e32a-143">Additionally, message contracts allow you to exercise more control over resultant messages.</span></span> <span data-ttu-id="0e32a-144">Örneğin, ileti gövdesi içinde bilgi parçalarını olmalıdır ve ileti üstbilgilerini olacağı karar verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e32a-144">For instance, you can decide which pieces of information should be in the message body and which should be in the message headers.</span></span> <span data-ttu-id="0e32a-145">Aşağıdaki örnek ileti sözleşmeleri kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="0e32a-145">The following example shows the use of message contracts.</span></span>  
  
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
  
 <span data-ttu-id="0e32a-146">Daha fazla bilgi için bkz: [kullanarak ileti sözleşmeleri](../../../../docs/framework/wcf/feature-details/using-message-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="0e32a-146">For more information, see [Using Message Contracts](../../../../docs/framework/wcf/feature-details/using-message-contracts.md).</span></span>  
  
 <span data-ttu-id="0e32a-147">Önceki örnekte, <xref:System.Runtime.Serialization.DataContractSerializer> sınıfı varsayılan olarak hala kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0e32a-147">In the previous example, the <xref:System.Runtime.Serialization.DataContractSerializer> class is still used by default.</span></span> <span data-ttu-id="0e32a-148"><xref:System.Xml.Serialization.XmlSerializer> Sınıfı ileti sözleşmeleri ile de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0e32a-148">The <xref:System.Xml.Serialization.XmlSerializer> class can also be used with message contracts.</span></span> <span data-ttu-id="0e32a-149">Bunu yapmak için uygulamanız <xref:System.ServiceModel.XmlSerializerFormatAttribute> özniteliği işlemi ya da sözleşme ve türleri ile uyumlu kullanın <xref:System.Xml.Serialization.XmlSerializer> ileti üstbilgilerini ve gövde üyeler sınıfta.</span><span class="sxs-lookup"><span data-stu-id="0e32a-149">To do this, apply the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to either the operation or the contract, and use types compatible with the <xref:System.Xml.Serialization.XmlSerializer> class in the message headers and body members.</span></span>  
  
## <a name="describing-messages-by-using-streams"></a><span data-ttu-id="0e32a-150">Akışlar kullanarak açıklayan iletiler</span><span class="sxs-lookup"><span data-stu-id="0e32a-150">Describing Messages by Using Streams</span></span>  
 <span data-ttu-id="0e32a-151">İşlem iletileri açıklamak için başka bir yolu kullanmaktır <xref:System.IO.Stream> sınıf veya türetilmiş sınıflarından işlemi sözleşme veya (olmalıdır yalnızca üye bu durumda) bir ileti sözleşmesi gövde üye olarak biri.</span><span class="sxs-lookup"><span data-stu-id="0e32a-151">Another way to describe messages in operations is to use the <xref:System.IO.Stream> class or one of its derived classes in an operation contract or as a message contract body member (it must be the only member in this case).</span></span> <span data-ttu-id="0e32a-152">Gelen iletiler için tür olmalıdır `Stream`— türetilen sınıflar kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="0e32a-152">For incoming messages, the type must be `Stream`—you cannot use derived classes.</span></span>  
  
 <span data-ttu-id="0e32a-153">Seri hale getirici, çağırma yerine [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bir akışından verileri alır ve giden iletisine doğrudan bir yerleştirir veya bir gelen iletisinden verileri alır ve bir akışa doğrudan yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="0e32a-153">Instead of invoking the serializer, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] retrieves data from a stream and puts it directly into an outgoing message, or retrieves data from an incoming message and puts it directly into a stream.</span></span> <span data-ttu-id="0e32a-154">Aşağıdaki örnek akışları kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="0e32a-154">The following sample shows the use of streams.</span></span>  
  
```csharp  
[OperationContract]  
public Stream DownloadFile(string fileName);  
```  
  
```vb  
<OperationContract()>  
Function DownloadFile(fileName As String) As String  
```  
  
 <span data-ttu-id="0e32a-155">Birleştiremez `Stream` ve akış olmayan verileri tek bir ileti gövdesi.</span><span class="sxs-lookup"><span data-stu-id="0e32a-155">You cannot combine `Stream` and non-stream data in a single message body.</span></span> <span data-ttu-id="0e32a-156">Ek veriler ileti üstbilgilerinde yerleştirmek için bir ileti sözleşmesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="0e32a-156">Use a message contract to put the extra data in message headers.</span></span> <span data-ttu-id="0e32a-157">Aşağıdaki örnek, işlem sözleşmesi tanımlarken akışları yanlış kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0e32a-157">The following example shows the incorrect usage of streams when defining the operation contract.</span></span>  
  
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
  
 <span data-ttu-id="0e32a-158">Aşağıdaki örnek, bir işlem sözleşmesi tanımlarken akışları doğru kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0e32a-158">The following sample shows the correct usage of streams when defining an operation contract.</span></span>  
  
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
  
 <span data-ttu-id="0e32a-159">Daha fazla bilgi için bkz: [büyük veriler ve akış](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).</span><span class="sxs-lookup"><span data-stu-id="0e32a-159">For more information, see [Large Data and Streaming](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).</span></span>  
  
## <a name="using-the-message-class"></a><span data-ttu-id="0e32a-160">İleti Sınıfını Kullanma</span><span class="sxs-lookup"><span data-stu-id="0e32a-160">Using the Message Class</span></span>  
 <span data-ttu-id="0e32a-161">Gönderilen veya alınan iletiler üzerinde tam programsal denetim sağlamak için kullanabileceğiniz <xref:System.ServiceModel.Channels.Message> doğrudan, aşağıdaki örnek kodda gösterildiği gibi sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0e32a-161">To have complete programmatic control over messages sent or received, you can use the <xref:System.ServiceModel.Channels.Message> class directly, as shown in the following example code.</span></span>  
  
```csharp  
[OperationContract]  
public void LogMessage(Message m);  
```  
  
```vb  
<OperationContract()>  
Sub LogMessage(m As Message)  
```  
  
 <span data-ttu-id="0e32a-162">İçinde ayrıntılı olarak açıklanmıştır Gelişmiş bir senaryo budur [ileti sınıfını kullanma](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).</span><span class="sxs-lookup"><span data-stu-id="0e32a-162">This is an advanced scenario, which is described in detail in [Using the Message Class](../../../../docs/framework/wcf/feature-details/using-the-message-class.md).</span></span>  
  
## <a name="describing-fault-messages"></a><span data-ttu-id="0e32a-163">Açıklayan hata iletileri</span><span class="sxs-lookup"><span data-stu-id="0e32a-163">Describing Fault Messages</span></span>  
 <span data-ttu-id="0e32a-164">Çıkış veya başvuru parametre ve dönüş değeri açıklanan iletileri ek olarak, en az iki olası iletileri tek yönlü değil herhangi bir işlem döndürebilirsiniz: kendi normal yanıt iletisi ve bir hata iletisi.</span><span class="sxs-lookup"><span data-stu-id="0e32a-164">In addition to the messages that are described by the return value and output or reference parameters, any operation that is not one-way can return at least two possible messages: its normal response message and a fault message.</span></span> <span data-ttu-id="0e32a-165">Aşağıdaki işlem sözleşmesi göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="0e32a-165">Consider the following operation contract.</span></span>  
  
```csharp  
[OperationContract]  
float GetAirfare(string fromCity, string toCity, DateTime date);  
```  
  
```vb  
<OperationContract()>  
Function GetAirfare(fromCity As String, toCity As String, date as DateTime)  
```  
  
 <span data-ttu-id="0e32a-166">Bu işlem ya da içeren normal bir ileti döndürebilir bir `float` sayı veya bir hata kodu ve açıklama içeren bir hata iletisi.</span><span class="sxs-lookup"><span data-stu-id="0e32a-166">This operation may either return a normal message that contains a `float` number, or a fault message that contains a fault code and a description.</span></span> <span data-ttu-id="0e32a-167">Bunu atma tarafından gerçekleştirmek bir <xref:System.ServiceModel.FaultException> hizmet uygulamanızda.</span><span class="sxs-lookup"><span data-stu-id="0e32a-167">You can accomplish this by throwing a <xref:System.ServiceModel.FaultException> in your service implementation.</span></span>  
  
 <span data-ttu-id="0e32a-168">Kullanarak ek olası hata iletileri belirtebilirsiniz <xref:System.ServiceModel.FaultContractAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="0e32a-168">You can specify additional possible fault messages by using the <xref:System.ServiceModel.FaultContractAttribute> attribute.</span></span> <span data-ttu-id="0e32a-169">Seri hale getirilebilir kullanarak ek hataları olmalıdır <xref:System.Runtime.Serialization.DataContractSerializer>, aşağıdaki örnek kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="0e32a-169">The additional faults must be serializable using the <xref:System.Runtime.Serialization.DataContractSerializer>, as shown in the following example code.</span></span>  
  
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
  
 <span data-ttu-id="0e32a-170">Bu ek hataları atma tarafından oluşturulabilir. bir <xref:System.ServiceModel.FaultException%601> uygun veri sözleşmesi türü.</span><span class="sxs-lookup"><span data-stu-id="0e32a-170">These additional faults can be generated by throwing a <xref:System.ServiceModel.FaultException%601> of the appropriate data contract type.</span></span> <span data-ttu-id="0e32a-171">Daha fazla bilgi için bkz: [özel durum işleme ve hataları](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).</span><span class="sxs-lookup"><span data-stu-id="0e32a-171">For more information, see [Handling Exceptions and Faults](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).</span></span>  
  
 <span data-ttu-id="0e32a-172">Kullanamazsınız <xref:System.Xml.Serialization.XmlSerializer> hataları tanımlamak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="0e32a-172">You cannot use the <xref:System.Xml.Serialization.XmlSerializer> class to describe faults.</span></span> <span data-ttu-id="0e32a-173"><xref:System.ServiceModel.XmlSerializerFormatAttribute> Hataya sözleşmeleri üzerinde hiçbir etkisi olmaz.</span><span class="sxs-lookup"><span data-stu-id="0e32a-173">The <xref:System.ServiceModel.XmlSerializerFormatAttribute> has no effect on fault contracts.</span></span>  
  
## <a name="using-derived-types"></a><span data-ttu-id="0e32a-174">Türetilmiş türler kullanma</span><span class="sxs-lookup"><span data-stu-id="0e32a-174">Using Derived Types</span></span>  
 <span data-ttu-id="0e32a-175">Bir işlem veya ileti sözleşmesi temel türü kullanın ve sonra işlemi gerçekte çağrılırken, türetilmiş bir tür kullanın isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e32a-175">You may want to use a base type in an operation or a message contract, and then use a derived type when actually invoking the operation.</span></span> <span data-ttu-id="0e32a-176">Bu durumda, ya da kullanmalıdır <xref:System.ServiceModel.ServiceKnownTypeAttribute> özniteliği ya da bazı alternatif bir mekanizma kullanımına izin vermek için türetilen türlerle.</span><span class="sxs-lookup"><span data-stu-id="0e32a-176">In this case, you must use either the <xref:System.ServiceModel.ServiceKnownTypeAttribute> attribute or some alternative mechanism to allow the use of derived types.</span></span> <span data-ttu-id="0e32a-177">Aşağıdaki işlem göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="0e32a-177">Consider the following operation.</span></span>  
  
```csharp  
[OperationContract]  
public bool IsLibraryItemAvailable(LibraryItem item);  
```  
  
```vb
<OperationContract()>  
    Function IsLibraryItemAvailable(item As LibraryItem) As Boolean  
```  
  
 <span data-ttu-id="0e32a-178">İki yazdığı, varsayın `Book` ve `Magazine`, türetilen `LibraryItem`.</span><span class="sxs-lookup"><span data-stu-id="0e32a-178">Assume that two types, `Book` and `Magazine`, derive from `LibraryItem`.</span></span> <span data-ttu-id="0e32a-179">Bu türlerini kullanmak için `IsLibraryItemAvailable` işlemi, işlemi aşağıdaki gibi değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0e32a-179">To use these types in the `IsLibraryItemAvailable` operation, you can change the operation as follows:</span></span>  
  
 `[OperationContract]`  
  
 `[ServiceKnownType(typeof(Book))]`  
  
 `[ServiceKnownType(typeof(Magazine))]`  
  
 `public bool IsLibraryItemAvailable(LibraryItem item);`  
  
 <span data-ttu-id="0e32a-180">Alternatif olarak, kullanabileceğiniz <xref:System.Runtime.Serialization.KnownTypeAttribute> ne zaman özniteliği varsayılan <xref:System.Runtime.Serialization.DataContractSerializer> , aşağıdaki örnek kodda gösterildiği gibi kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="0e32a-180">Alternatively, you can use the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute when the default <xref:System.Runtime.Serialization.DataContractSerializer> is in use, as shown in the following example code.</span></span>  
  
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
  
 <span data-ttu-id="0e32a-181">Kullanabileceğiniz <xref:System.Xml.Serialization.XmlIncludeAttribute> özniteliği kullanırken <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="0e32a-181">You can use the <xref:System.Xml.Serialization.XmlIncludeAttribute> attribute when using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
 <span data-ttu-id="0e32a-182">Uygulayabileceğiniz <xref:System.ServiceModel.ServiceKnownTypeAttribute> özniteliği bir işlem veya tüm hizmet.</span><span class="sxs-lookup"><span data-stu-id="0e32a-182">You can apply the <xref:System.ServiceModel.ServiceKnownTypeAttribute> attribute to an operation or to the entire service.</span></span> <span data-ttu-id="0e32a-183">Bir türü veya yöntemin adını çağrılacak gibi bilinen türlerinin bir listesini almak için kabul <xref:System.Runtime.Serialization.KnownTypeAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="0e32a-183">It accepts either a type or the name of the method to call to get a list of known types, just like the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute.</span></span> <span data-ttu-id="0e32a-184">Daha fazla bilgi için bkz: [veri sözleşmesi bilinen türleri](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="0e32a-184">For more information, see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="specifying-the-use-and-style"></a><span data-ttu-id="0e32a-185">Kullanım ve stil belirtme</span><span class="sxs-lookup"><span data-stu-id="0e32a-185">Specifying the Use and Style</span></span>  
 <span data-ttu-id="0e32a-186">Web Hizmetleri Açıklama Dili (WSDL), iki yaygın olarak kullanarak Hizmetleri açıklanırken kullanılan belge ve uzak yordam çağrısı (RPC) stillerdir.</span><span class="sxs-lookup"><span data-stu-id="0e32a-186">When describing services using Web Services Description Language (WSDL), the two commonly used styles are Document and remote procedure call (RPC).</span></span> <span data-ttu-id="0e32a-187">Belge stilde tüm ileti gövdesi şema kullanılarak tanımlanır ve bu şema öğeleri başvurarak çeşitli ileti gövdesi bölümleri WSDL açıklar.</span><span class="sxs-lookup"><span data-stu-id="0e32a-187">In the Document style, the entire message body is described using the schema, and the WSDL describes the various message body parts by referring to elements within that schema.</span></span> <span data-ttu-id="0e32a-188">RPC stilinde WSDL öğenin yerine, her ileti parçası için bir şema türü ifade eder.</span><span class="sxs-lookup"><span data-stu-id="0e32a-188">In the RPC style, the WSDL refers to a schema type for each message part rather than an element.</span></span> <span data-ttu-id="0e32a-189">Bazı durumlarda, el ile bu stiller birini seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0e32a-189">In some cases, you have to manually select one of these styles.</span></span> <span data-ttu-id="0e32a-190">Bunu uygulayarak yapmak <xref:System.ServiceModel.DataContractFormatAttribute> özniteliği ve ayarı `Style` özelliği (zaman <xref:System.Runtime.Serialization.DataContractSerializer> kullanımda), veya ayarlayarak `Style` üzerinde <xref:System.ServiceModel.XmlSerializerFormatAttribute> özniteliği (kullanırken <xref:System.Xml.Serialization.XmlSerializer>).</span><span class="sxs-lookup"><span data-stu-id="0e32a-190">You can do this by applying the <xref:System.ServiceModel.DataContractFormatAttribute> attribute and setting the `Style` property (when the <xref:System.Runtime.Serialization.DataContractSerializer> is in use), or by setting `Style` on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute (when using the <xref:System.Xml.Serialization.XmlSerializer>).</span></span>  
  
 <span data-ttu-id="0e32a-191">Ayrıca, <xref:System.Xml.Serialization.XmlSerializer> serileştirilmiş XML iki tür destekler: `Literal` ve `Encoded`.</span><span class="sxs-lookup"><span data-stu-id="0e32a-191">Additionally, the <xref:System.Xml.Serialization.XmlSerializer> supports two forms of serialized XML: `Literal` and `Encoded`.</span></span> <span data-ttu-id="0e32a-192">`Literal` en yaygın olarak kabul edilen biçimidir ve yalnızca form <xref:System.Runtime.Serialization.DataContractSerializer> destekler.</span><span class="sxs-lookup"><span data-stu-id="0e32a-192">`Literal` is the most commonly accepted form, and is the only form the <xref:System.Runtime.Serialization.DataContractSerializer> supports.</span></span> <span data-ttu-id="0e32a-193">`Encoded` SOAP belirtimi 5 bölümünde açıklanan eski bir form ve yeni hizmetler için önerilmez.</span><span class="sxs-lookup"><span data-stu-id="0e32a-193">`Encoded` is a legacy form described in section 5 of the SOAP specification, and is not recommended for new services.</span></span> <span data-ttu-id="0e32a-194">Geçiş yapmak için `Encoded` modunu ayarlama `Use` özelliği <xref:System.ServiceModel.XmlSerializerFormatAttribute> özniteliğini `Encoded`.</span><span class="sxs-lookup"><span data-stu-id="0e32a-194">To switch to `Encoded` mode, set the `Use` property on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> attribute to `Encoded`.</span></span>  
  
 <span data-ttu-id="0e32a-195">Çoğu durumda, varsayılan ayarları değiştirmemelisiniz `Style` ve `Use` özellikleri.</span><span class="sxs-lookup"><span data-stu-id="0e32a-195">In most cases, you should not change the default settings for the `Style` and `Use` properties.</span></span>  
  
## <a name="controlling-the-serialization-process"></a><span data-ttu-id="0e32a-196">Seri hale getirme işlemi denetleme</span><span class="sxs-lookup"><span data-stu-id="0e32a-196">Controlling the Serialization Process</span></span>  
 <span data-ttu-id="0e32a-197">Veri seri hale getirilmiş biçimini özelleştirmek için değişik yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e32a-197">You can do a number of things to customize the way data is serialized.</span></span>  
  
### <a name="changing-server-serialization-settings"></a><span data-ttu-id="0e32a-198">Sunucu serileştirme ayarlarını değiştirme</span><span class="sxs-lookup"><span data-stu-id="0e32a-198">Changing Server Serialization Settings</span></span>  
 <span data-ttu-id="0e32a-199">Zaman varsayılan <xref:System.Runtime.Serialization.DataContractSerializer> olan kullanımda uygulayarak için seri hale getirme işlemi hizmet üzerinde bazı yönlerini denetleyebilirsiniz <xref:System.ServiceModel.ServiceBehaviorAttribute> hizmete özniteliği.</span><span class="sxs-lookup"><span data-stu-id="0e32a-199">When the default <xref:System.Runtime.Serialization.DataContractSerializer> is in use, you can control some aspects of the serialization process on the service by applying the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to the service.</span></span> <span data-ttu-id="0e32a-200">Özellikle, kullanabilir `MaxItemsInObjectGraph` nesneleri sayısının üst sınırını belirler kota ayarlamak için özellik <xref:System.Runtime.Serialization.DataContractSerializer> seri durumdan çıkarır.</span><span class="sxs-lookup"><span data-stu-id="0e32a-200">Specifically, you may use the `MaxItemsInObjectGraph` property to set the quota that limits the maximum number of objects the <xref:System.Runtime.Serialization.DataContractSerializer> deserializes.</span></span> <span data-ttu-id="0e32a-201">Kullanabileceğiniz `IgnoreExtensionDataObject` gidiş sürüm oluşturma özelliği devre dışı bırakmak için özelliği.</span><span class="sxs-lookup"><span data-stu-id="0e32a-201">You can use the `IgnoreExtensionDataObject` property to turn off the round-tripping versioning feature.</span></span> <span data-ttu-id="0e32a-202">Kotalar hakkında daha fazla bilgi için bkz: [veriler için güvenlik konuları](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).</span><span class="sxs-lookup"><span data-stu-id="0e32a-202">For more information about quotas, see [Security Considerations for Data](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).</span></span> <span data-ttu-id="0e32a-203">Gidiş hakkında daha fazla bilgi için bkz: [İleri uyumlu veri sözleşmeleri](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="0e32a-203">For more information about round-tripping, see [Forward-Compatible Data Contracts](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).</span></span>  
  
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
  
### <a name="serialization-behaviors"></a><span data-ttu-id="0e32a-204">Seri hale getirme davranışları</span><span class="sxs-lookup"><span data-stu-id="0e32a-204">Serialization Behaviors</span></span>  
 <span data-ttu-id="0e32a-205">İki davranışları kullanılabilir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> ve <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> , otomatik olarak takılı olduğundan hangi seri hale getirici, belirli bir işlem için kullanılmakta olan bağlı.</span><span class="sxs-lookup"><span data-stu-id="0e32a-205">Two behaviors are available in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> and the <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> that are automatically plugged in depending on which serializer is in use for a particular operation.</span></span> <span data-ttu-id="0e32a-206">Bu davranışların otomatik olarak uygulandığından, normalde bunları haberdar olmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="0e32a-206">Because these behaviors are applied automatically, you normally do not have to be aware of them.</span></span>  
  
 <span data-ttu-id="0e32a-207">Ancak, `DataContractSerializerOperationBehavior` sahip `MaxItemsInObjectGraph`, `IgnoreExtensionDataObject`, ve `DataContractSurrogate` özellikleri seri hale getirme işlemi özelleştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e32a-207">However, the `DataContractSerializerOperationBehavior` has the `MaxItemsInObjectGraph`, `IgnoreExtensionDataObject`, and `DataContractSurrogate` properties that you may use to customize the serialization process.</span></span> <span data-ttu-id="0e32a-208">İlk iki özellikleri, önceki bölümde açıklandığı gibi aynı anlamı yoktur.</span><span class="sxs-lookup"><span data-stu-id="0e32a-208">The first two properties have the same meaning as discussed in the previous section.</span></span> <span data-ttu-id="0e32a-209">Kullanabileceğiniz `DataContractSurrogate` özelleştirilmesini ve genişletilmesini seri hale getirme işlemi için güçlü bir mekanizma olan veri sözleşmesi yedekleri etkinleştirmek için özellik.</span><span class="sxs-lookup"><span data-stu-id="0e32a-209">You can use the `DataContractSurrogate` property to enable data contract surrogates, which are a powerful mechanism for customizing and extending the serialization process.</span></span> <span data-ttu-id="0e32a-210">Daha fazla bilgi için bkz: [veri sözleşmesi yedekleri](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).</span><span class="sxs-lookup"><span data-stu-id="0e32a-210">For more information, see [Data Contract Surrogates](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).</span></span>  
  
 <span data-ttu-id="0e32a-211">Kullanabileceğiniz `DataContractSerializerOperationBehavior` istemci ve sunucu serileştirme özelleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="0e32a-211">You can use the `DataContractSerializerOperationBehavior` to customize both client and server serialization.</span></span> <span data-ttu-id="0e32a-212">Aşağıdaki örnek artırmak nasıl gösterir `MaxItemsInObjectGraph` kota istemci üzerinde.</span><span class="sxs-lookup"><span data-stu-id="0e32a-212">The following example shows how to increase the `MaxItemsInObjectGraph` quota on the client.</span></span>  
  
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
  
 <span data-ttu-id="0e32a-213">Kendini barındıran durumda hizmet eşdeğer kod aşağıdadır.</span><span class="sxs-lookup"><span data-stu-id="0e32a-213">Following is the equivalent code on the service, in the self-hosted case.</span></span>  
  
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
  
 <span data-ttu-id="0e32a-214">Web barındırılan durumda, yeni bir oluşturmalısınız `ServiceHost` türetilmiş sınıf ve hizmet ana bilgisayar üreteci prize takın için kullanın.</span><span class="sxs-lookup"><span data-stu-id="0e32a-214">In the Web-hosted case, you must create a new `ServiceHost` derived class and use a service host factory to plug it in.</span></span>  
  
### <a name="controlling-serialization-settings-in-configuration"></a><span data-ttu-id="0e32a-215">Yapılandırmadaki serileştirme ayarlarını denetleme</span><span class="sxs-lookup"><span data-stu-id="0e32a-215">Controlling Serialization Settings in Configuration</span></span>  
 <span data-ttu-id="0e32a-216">`MaxItemsInObjectGraph` Ve `IgnoreExtensionDataObject` kullanarak yapılandırma aracılığıyla denetlenebilir `dataContractSerializer` uç noktası veya hizmet davranışı, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="0e32a-216">The `MaxItemsInObjectGraph` and `IgnoreExtensionDataObject` can be controlled through configuration by using the `dataContractSerializer` endpoint or service behavior, as shown in the following example.</span></span>  
  
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
  
### <a name="shared-type-serialization-object-graph-preservation-and-custom-serializers"></a><span data-ttu-id="0e32a-217">Türü seri hale getirme, Nesne grafiği korunması ve özel serileştiricileri paylaşılan</span><span class="sxs-lookup"><span data-stu-id="0e32a-217">Shared Type Serialization, Object Graph Preservation, and Custom Serializers</span></span>  
 <span data-ttu-id="0e32a-218"><xref:System.Runtime.Serialization.DataContractSerializer> Veri sözleşmesi adları ve .NET Tür adları kullanarak serileştirir.</span><span class="sxs-lookup"><span data-stu-id="0e32a-218">The <xref:System.Runtime.Serialization.DataContractSerializer> serializes using data contract names and not .NET type names.</span></span> <span data-ttu-id="0e32a-219">Bu hizmet odaklı mimari tenets ile tutarlıdır ve esneklik için önemli ölçüde sağlar — .NET türleri kablo sözleşme etkilemeden değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e32a-219">This is consistent with service-oriented architecture tenets and allows for a great degree of flexibility—the .NET types can change without affecting the wire contract.</span></span> <span data-ttu-id="0e32a-220">Nadir durumlarda, gerçek .NET Tür adları, seri hale getirmek böylece istemci ve sunucu, .NET Framework remoting teknolojisine benzer arasında sıkı bağ Tanıtımı isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e32a-220">In rare cases, you may want to serialize actual .NET type names, thereby introducing a tight coupling between the client and the server, similar to the .NET Framework remoting technology.</span></span> <span data-ttu-id="0e32a-221">Bu önerilen bir uygulama dışında geçiş genellikle ortaya nadir durumlarda değil [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] .NET Framework remoting gelen.</span><span class="sxs-lookup"><span data-stu-id="0e32a-221">This is not a recommended practice, except in rare cases that usually occur when migrating to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] from .NET Framework remoting.</span></span> <span data-ttu-id="0e32a-222">Bu durumda, kullanmalısınız <xref:System.Runtime.Serialization.NetDataContractSerializer> sınıfının yerine <xref:System.Runtime.Serialization.DataContractSerializer> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0e32a-222">In this case, you must use the <xref:System.Runtime.Serialization.NetDataContractSerializer> class instead of the <xref:System.Runtime.Serialization.DataContractSerializer> class.</span></span>  
  
 <span data-ttu-id="0e32a-223"><xref:System.Runtime.Serialization.DataContractSerializer> Normalde nesne grafik nesnesi ağaçları olarak serileştirir.</span><span class="sxs-lookup"><span data-stu-id="0e32a-223">The <xref:System.Runtime.Serialization.DataContractSerializer> normally serializes object graphs as object trees.</span></span> <span data-ttu-id="0e32a-224">Diğer bir deyişle, aynı nesne için birden çok kez geçer, birden çok kez sıralanır.</span><span class="sxs-lookup"><span data-stu-id="0e32a-224">That is, if the same object is referred to more than once, it is serialized more than once.</span></span> <span data-ttu-id="0e32a-225">Örneğin, göz önünde bulundurun bir `PurchaseOrder` türü adresi adlı iki alan örnek `billTo` ve `shipTo`.</span><span class="sxs-lookup"><span data-stu-id="0e32a-225">For example, consider a `PurchaseOrder` instance that has two fields of type Address called `billTo` and `shipTo`.</span></span> <span data-ttu-id="0e32a-226">Her iki alan aynı adres örneğini ayarlarsanız, iki aynı adres örneği vardır seri hale getirme ve seri durumdan sonra.</span><span class="sxs-lookup"><span data-stu-id="0e32a-226">If both fields are set to the same Address instance, there are two identical Address instances after serialization and deserialization.</span></span> <span data-ttu-id="0e32a-227">Nesne grafiklerinin XML temsil etmek için standart birlikte çalışabilir yolu olduğundan bu yapılır (eski kodlanmış SOAP standart kullanılabilir dışında <xref:System.Xml.Serialization.XmlSerializer>, önceki bölümde açıklandığı gibi `Style` ve `Use`).</span><span class="sxs-lookup"><span data-stu-id="0e32a-227">This is done because there is no standard interoperable way to represent object graphs in XML (except for the legacy SOAP encoded standard available on the <xref:System.Xml.Serialization.XmlSerializer>, as described in the previous section on `Style` and `Use`).</span></span> <span data-ttu-id="0e32a-228">Nesne grafiklerinin ağaçlar seri hale getirme belirli dezavantajları vardır, örneğin, döngüsel başvurulara grafiklerle seri hale getirilemez.</span><span class="sxs-lookup"><span data-stu-id="0e32a-228">Serializing object graphs as trees has certain disadvantages, for example, graphs with circular references cannot be serialized.</span></span> <span data-ttu-id="0e32a-229">Bazen, birlikte çalışabilen olmasa da doğru nesne grafiğinin seri hale getirme için geçiş gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="0e32a-229">Occasionally, it is necessary to switch to true object graph serialization, even though it is not interoperable.</span></span> <span data-ttu-id="0e32a-230">Bu kullanılarak yapılabilir <xref:System.Runtime.Serialization.DataContractSerializer> ile oluşturulan `preserveObjectReferences` parametre kümesine `true`.</span><span class="sxs-lookup"><span data-stu-id="0e32a-230">This can be done by using the <xref:System.Runtime.Serialization.DataContractSerializer> constructed with the `preserveObjectReferences` parameter set to `true`.</span></span>  
  
 <span data-ttu-id="0e32a-231">Bazen, yerleşik serileştiricileri senaryonuz için yeterli değildir.</span><span class="sxs-lookup"><span data-stu-id="0e32a-231">Occasionally, the built-in serializers are not enough for your scenario.</span></span> <span data-ttu-id="0e32a-232">Çoğu durumda, kullanmaya devam edebilirsiniz <xref:System.Runtime.Serialization.XmlObjectSerializer> hangi hem Özet <xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Runtime.Serialization.NetDataContractSerializer> türetilir.</span><span class="sxs-lookup"><span data-stu-id="0e32a-232">In most cases, you can still use the <xref:System.Runtime.Serialization.XmlObjectSerializer> abstraction from which both the <xref:System.Runtime.Serialization.DataContractSerializer> and the <xref:System.Runtime.Serialization.NetDataContractSerializer> derive.</span></span>  
  
 <span data-ttu-id="0e32a-233">Önceki üç durumda (.NET türü korunması, Nesne grafiği korunması ve tamamen özel `XmlObjectSerializer`-seri hale getirme tabanlı) tüm özel bir seri hale getirici prize takılı gerekir.</span><span class="sxs-lookup"><span data-stu-id="0e32a-233">The previous three cases (.NET type preservation, object graph preservation, and completely custom `XmlObjectSerializer`-based serialization) all require a custom serializer be plugged in.</span></span> <span data-ttu-id="0e32a-234">Bunu yapmak için şu adımları izleyin:</span><span class="sxs-lookup"><span data-stu-id="0e32a-234">To do this, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="0e32a-235">Türetme kendi davranışı yazma <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>.</span><span class="sxs-lookup"><span data-stu-id="0e32a-235">Write your own behavior deriving from the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>.</span></span>  
  
2.  <span data-ttu-id="0e32a-236">İki geçersiz kılma `CreateSerializer` kendi seri hale getirici döndürülecek yöntemleri (ya da <xref:System.Runtime.Serialization.NetDataContractSerializer>, <xref:System.Runtime.Serialization.DataContractSerializer> ile `preserveObjectReferences` kümesine `true`, veya kendi özel <xref:System.Runtime.Serialization.XmlObjectSerializer>).</span><span class="sxs-lookup"><span data-stu-id="0e32a-236">Override the two `CreateSerializer` methods to return your own serializer (either the <xref:System.Runtime.Serialization.NetDataContractSerializer>, the <xref:System.Runtime.Serialization.DataContractSerializer> with `preserveObjectReferences` set to `true`, or your own custom <xref:System.Runtime.Serialization.XmlObjectSerializer>).</span></span>  
  
3.  <span data-ttu-id="0e32a-237">Hizmet ana bilgisayarını açma veya bir istemci kanal oluşturma önce varolan kaldırmak <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> davranışı ve önceki adımlarda oluşturduğunuz özel türetilen sınıfta takın.</span><span class="sxs-lookup"><span data-stu-id="0e32a-237">Before opening the service host or creating a client channel, remove the existing <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> behavior and plug in the custom derived class that you created in the previous steps.</span></span>  
  
 <span data-ttu-id="0e32a-238">Gelişmiş serileştirme kavramları hakkında daha fazla bilgi için bkz: [seri hale getirme ve seri durumdan çıkarma](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).</span><span class="sxs-lookup"><span data-stu-id="0e32a-238">For more information about advanced serialization concepts, see [Serialization and Deserialization](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e32a-239">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0e32a-239">See Also</span></span>  
 [<span data-ttu-id="0e32a-240">XmlSerializer Sınıfını Kullanma</span><span class="sxs-lookup"><span data-stu-id="0e32a-240">Using the XmlSerializer Class</span></span>](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)  
 [<span data-ttu-id="0e32a-241">Nasıl yapılır: Akışı Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="0e32a-241">How to: Enable Streaming</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)  
 [<span data-ttu-id="0e32a-242">Nasıl yapılır: Bir Sınıf veya Yapı için Temel Bir Veri Anlaşması Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0e32a-242">How to: Create a Basic Data Contract for a Class or Structure</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
