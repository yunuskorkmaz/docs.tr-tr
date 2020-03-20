---
title: Kullanım ve Stil özellikleri örneklerini ayarlama
ms.date: 03/30/2017
ms.assetid: c09a0600-116f-41cf-900a-1b7e4ea4e300
ms.openlocfilehash: f400c0bc08588afa951ae33f221663b47b37602c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144038"
---
# <a name="setting-the-use-and-style-properties"></a><span data-ttu-id="fef30-102">Kullanım ve Stil Özelliklerini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="fef30-102">Setting the Use and Style Properties</span></span>

<span data-ttu-id="fef30-103">Bu örnek, Kullanım ve Stil özelliklerinin <xref:System.ServiceModel.XmlSerializerFormatAttribute> nasıl <xref:System.ServiceModel.DataContractFormatAttribute>kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fef30-103">This sample demonstrates how to use the Use and Style properties on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> and the <xref:System.ServiceModel.DataContractFormatAttribute>.</span></span> <span data-ttu-id="fef30-104">Bu özellikler iletilerin biçimlendirme şeklini etkiler.</span><span class="sxs-lookup"><span data-stu-id="fef30-104">These properties affect how messages are formatted.</span></span> <span data-ttu-id="fef30-105">Varsayılan olarak, ileti gövdesi stil olarak ayarlanmış <xref:System.ServiceModel.OperationFormatStyle.Document>olarak biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="fef30-105">By default, the message body is formatted with the style set to <xref:System.ServiceModel.OperationFormatStyle.Document>.</span></span> <span data-ttu-id="fef30-106">Bu ayarlar hizmet sözleşmesi düzeyinde veya işlem sözleşmesi düzeyinde belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="fef30-106">These settings can be specified at either the service contract level or the operation contract level.</span></span>

> [!NOTE]
> <span data-ttu-id="fef30-107">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="fef30-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="fef30-108">Stil <xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> özelliği, hizmetiçin WSDL meta verilerinin nasıl biçimlendirilir olduğunu belirler.</span><span class="sxs-lookup"><span data-stu-id="fef30-108">The <xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> style property determines how the WSDL metadata for the service is formatted.</span></span> <span data-ttu-id="fef30-109">Olası değerler <xref:System.ServiceModel.OperationFormatStyle.Document>ve <xref:System.ServiceModel.OperationFormatStyle.Rpc>.</span><span class="sxs-lookup"><span data-stu-id="fef30-109">Possible values are <xref:System.ServiceModel.OperationFormatStyle.Document>, and <xref:System.ServiceModel.OperationFormatStyle.Rpc>.</span></span> <span data-ttu-id="fef30-110">RPC, bir işlem için değiştirilen iletilerin WSDL gösteriminin uzaktan yordam çağrısı gibi parametreler içerdiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="fef30-110">RPC means that the WSDL representation of messages exchanged for an operation contains parameters as if it were a remote procedure call.</span></span> <span data-ttu-id="fef30-111">Bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="fef30-111">The following is an example.</span></span>

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="n1" type="xsd:double"/>
  <wsdl:part name="n2" type="xsd:double"/>
</wsdl:message>
```

<span data-ttu-id="fef30-112">Stili, <xref:System.ServiceModel.OperationFormatStyle.Document> WSDL gösteriminin, aşağıdaki örnekte gösterildiği gibi bir işlemiçin değiştirilen belgeyi temsil eden tek bir öğe içerdiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="fef30-112">Setting the style to <xref:System.ServiceModel.OperationFormatStyle.Document> means that the WSDL representation contains a single element that represents the document that is exchanged for an operation as shown in the following example.</span></span>

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="parameters" element="tns:Add"/>
</wsdl:message>
```

<span data-ttu-id="fef30-113">Özellik <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> iletinin biçimini belirler.</span><span class="sxs-lookup"><span data-stu-id="fef30-113">The <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> property determines the format of the message.</span></span> <span data-ttu-id="fef30-114">Olası değerler <xref:System.ServiceModel.OperationFormatUse.Literal> <xref:System.ServiceModel.OperationFormatUse.Encoded>ve; varsayılan değer. <xref:System.ServiceModel.OperationFormatUse.Literal></span><span class="sxs-lookup"><span data-stu-id="fef30-114">Possible values are <xref:System.ServiceModel.OperationFormatUse.Literal> and <xref:System.ServiceModel.OperationFormatUse.Encoded>; the default value is <xref:System.ServiceModel.OperationFormatUse.Literal>.</span></span> <span data-ttu-id="fef30-115">Literal, iletinin aşağıdaki Belge/Literal örnekte gösterildiği gibi WSDL'deki şemanın gerçek bir örneği olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="fef30-115">Literal means that the message is a literal instance of the schema in the WSDL as shown in the following Document/ Literal example.</span></span>

```xml
<Add xmlns="http://Microsoft.ServiceModel.Samples">
  <n1>100</n1>
  <n2>15.99</n2>
</Add>
```

<span data-ttu-id="fef30-116">Kodlanmış, WSDL'deki şemaların SOAP 1.1 bölüm 5'te bulunan kurallara göre kodlanmış soyut özellikler olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="fef30-116">Encoded means that the schemas in the WSDL are abstract specifications that are encoded according to the rules found in SOAP 1.1 section 5.</span></span> <span data-ttu-id="fef30-117">Aşağıda bir RPC / Kodlanmış örnektir.</span><span class="sxs-lookup"><span data-stu-id="fef30-117">The following is an RPC/Encoded example.</span></span>

```xml
<q1:Add xmlns:q1="http://Microsoft.ServiceModel.Samples">
  <n1 xsi:type="xsd:double" xmlns="">100</n1>
  <n2 xsi:type="xsd:double" xmlns="">15.99</n2>
</q1:Add>
```

<span data-ttu-id="fef30-118">WS-I Temel Profil 1.0 kullanımını <xref:System.ServiceModel.OperationFormatUse.Encoded> yasaklar ve yalnızca eski hizmetler tarafından gerekli olduğunda kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fef30-118">The WS-I Basic Profile 1.0 prohibits the use of <xref:System.ServiceModel.OperationFormatUse.Encoded> and you should only use it when required by legacy services.</span></span> <span data-ttu-id="fef30-119">İleti `Encoded` biçimi yalnızca XmlSerializer kullanırken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fef30-119">The `Encoded` message format is only available when using the XmlSerializer.</span></span>

<span data-ttu-id="fef30-120">Gönderilen ve alınan iletileri görmenizi sağlamak için, bu örnek [İzleme ve İleti Günlüğe kaydetmeyi](tracing-and-message-logging.md)temel alar.</span><span class="sxs-lookup"><span data-stu-id="fef30-120">To allow you to see the messages being sent and received, this sample is based on the [Tracing and Message Logging](tracing-and-message-logging.md).</span></span> <span data-ttu-id="fef30-121">Hizmet yapılandırması ve kaynak kodu, izleme ve ileti günlüğe kaydetmeyi etkinleştirmek ve kullanmak için değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="fef30-121">The service configuration and source code have been modified to enable and utilize tracing and message logging.</span></span> <span data-ttu-id="fef30-122">Buna ek <xref:System.ServiceModel.WSHttpBinding> olarak, güvenlik olmadan yapılandırıldı, böylece günlüğe kaydedilen iletiler şifrelenmemiş bir biçimde görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="fef30-122">In addition, the <xref:System.ServiceModel.WSHttpBinding> has been configured without security, so the logged messages can be viewed in an unencrypted format.</span></span> <span data-ttu-id="fef30-123">Ortaya çıkan izleme günlükleri (System.ServiceModel.e2e ve Message.log) [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md)kullanılarak görüntülenmelidir.</span><span class="sxs-lookup"><span data-stu-id="fef30-123">The resulting trace logs (System.ServiceModel.e2e and Message.log) should be viewed by using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="fef30-124">İzlemeler C:\LOGS klasöründe oluşturulacak şekilde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="fef30-124">The traces are configured to be created in the C:\LOGS folder.</span></span> <span data-ttu-id="fef30-125">Örneği çalıştırmadan önce klasörü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fef30-125">Create the folder before running the sample.</span></span> <span data-ttu-id="fef30-126">Görüntüleyici'yi İzle aracında ileti içeriğini görüntülemek için, aracın hem sol hem de sağ bölmelerinde **İletiler'i** seçin.</span><span class="sxs-lookup"><span data-stu-id="fef30-126">To view message contents in the Trace Viewer tool, select **Messages** in both the left and the right panes of the tool.</span></span>

<span data-ttu-id="fef30-127">Aşağıdaki kod, <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> ayarlanan özellikle hizmet <xref:System.ServiceModel.OperationFormatUse> sözleşmesini gösterir ve ileti gövdesinin <xref:System.ServiceModel.OperationFormatStyle> <xref:System.ServiceModel.OperationFormatStyle.Document>biçimi varsayılandan .</span><span class="sxs-lookup"><span data-stu-id="fef30-127">The following code shows the service contract with the <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> property set to <xref:System.ServiceModel.OperationFormatUse> and the format of the message body changed from the default <xref:System.ServiceModel.OperationFormatStyle> to <xref:System.ServiceModel.OperationFormatStyle.Document>.</span></span>

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

<span data-ttu-id="fef30-128">Farklı <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> ve <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> ayarlar arasındaki farkı görmek için, bunları hizmette değiştirin, istemciyi yeniden oluşturun, örneği çalıştırın ve Servis İzleyici aracıyla c:\logs\message.logs dosyasını inceleyin.</span><span class="sxs-lookup"><span data-stu-id="fef30-128">To see the difference between the different <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> and <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> settings, modify them in the service, regenerate the client, run the sample, and examine the c:\logs\message.logs file with the Service Trace Viewer tool.</span></span> <span data-ttu-id="fef30-129">Ayrıca görüntüleyerek `http://localhost/ServiceModelSamples/service.svc?wsdl`meta veriler üzerindeki etkisini gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="fef30-129">Also observe the impact on the metadata by viewing `http://localhost/ServiceModelSamples/service.svc?wsdl`.</span></span> <span data-ttu-id="fef30-130">Hizmetlerin meta verileri genellikle birden çok sayfaya ayrılır.</span><span class="sxs-lookup"><span data-stu-id="fef30-130">The metadata for services is typically broken up into multiple pages.</span></span> <span data-ttu-id="fef30-131">Ana wsdl sayfası WSDL bağlamalarını içerir, ancak ileti tanımlarını gözlemlemek için görüntüleyin. `http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0`</span><span class="sxs-lookup"><span data-stu-id="fef30-131">The main wsdl page contains the WSDL bindings, but view `http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0` to observe the message definitions.</span></span>

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="fef30-132">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="fef30-132">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="fef30-133">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="fef30-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="fef30-134">İletileri günlüğe kaydetmek için C:\LOGS dizini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fef30-134">Create a C:\LOGS directory for logging messages.</span></span> <span data-ttu-id="fef30-135">Kullanıcı Ağ Hizmeti'ne bu dizini yazma izinleri verin.</span><span class="sxs-lookup"><span data-stu-id="fef30-135">Give the user Network Service write permissions for this directory.</span></span>

3. <span data-ttu-id="fef30-136">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="fef30-136">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="fef30-137">Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="fef30-137">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fef30-138">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="fef30-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fef30-139">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="fef30-139">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="fef30-140">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="fef30-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fef30-141">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="fef30-141">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\UseAndStyle`
