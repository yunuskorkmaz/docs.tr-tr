---
title: Kullanım ve stil özelliklerini ayarlama-WCF örnekleri
ms.date: 03/30/2017
ms.assetid: c09a0600-116f-41cf-900a-1b7e4ea4e300
ms.openlocfilehash: 946f8f6aab253eb881faaba7adfdc68dc54d7f0b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958799"
---
# <a name="setting-the-use-and-style-properties"></a><span data-ttu-id="32380-102">Kullanım ve Stil Özelliklerini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="32380-102">Setting the Use and Style Properties</span></span>

<span data-ttu-id="32380-103">Bu örnek, <xref:System.ServiceModel.XmlSerializerFormatAttribute> <xref:System.ServiceModel.DataContractFormatAttribute>ve ' de kullanımı ve stil özelliklerinin nasıl kullanıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="32380-103">This sample demonstrates how to use the Use and Style properties on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> and the <xref:System.ServiceModel.DataContractFormatAttribute>.</span></span> <span data-ttu-id="32380-104">Bu özellikler, iletilerin nasıl biçimlendirildiğini etkiler.</span><span class="sxs-lookup"><span data-stu-id="32380-104">These properties affect how messages are formatted.</span></span> <span data-ttu-id="32380-105">Varsayılan olarak, ileti gövdesi olarak <xref:System.ServiceModel.OperationFormatStyle.Document>ayarlanmış stille biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="32380-105">By default, the message body is formatted with the style set to <xref:System.ServiceModel.OperationFormatStyle.Document>.</span></span> <span data-ttu-id="32380-106">Bu ayarlar, hizmet sözleşmesi düzeyinde ya da işlem sözleşmesi düzeyinde belirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="32380-106">These settings can be specified at either the service contract level or the operation contract level.</span></span>

> [!NOTE]
> <span data-ttu-id="32380-107">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="32380-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="32380-108"><xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> Style özelliği, hizmetin WSDL meta verilerinin nasıl biçimlendirildiğini belirler.</span><span class="sxs-lookup"><span data-stu-id="32380-108">The <xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> style property determines how the WSDL metadata for the service is formatted.</span></span> <span data-ttu-id="32380-109">Olası değerler, <xref:System.ServiceModel.OperationFormatStyle.Document>ve <xref:System.ServiceModel.OperationFormatStyle.Rpc>' dir.</span><span class="sxs-lookup"><span data-stu-id="32380-109">Possible values are <xref:System.ServiceModel.OperationFormatStyle.Document>, and <xref:System.ServiceModel.OperationFormatStyle.Rpc>.</span></span> <span data-ttu-id="32380-110">RPC, bir işlem için değiştirilen iletilerin WSDL gösteriminin, bir uzak yordam çağrımı gibi parametreler içerdiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="32380-110">RPC means that the WSDL representation of messages exchanged for an operation contains parameters as if it were a remote procedure call.</span></span> <span data-ttu-id="32380-111">Bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="32380-111">The following is an example.</span></span>

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="n1" type="xsd:double"/>
  <wsdl:part name="n2" type="xsd:double"/>
</wsdl:message>
```

<span data-ttu-id="32380-112">Stilin ayarlanması, WSDL <xref:System.ServiceModel.OperationFormatStyle.Document> gösteriminin, aşağıdaki örnekte gösterildiği gibi bir işlem için değiştirilen belgeyi temsil eden tek bir öğe içerdiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="32380-112">Setting the style to <xref:System.ServiceModel.OperationFormatStyle.Document> means that the WSDL representation contains a single element that represents the document that is exchanged for an operation as shown in the following example.</span></span>

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="parameters" element="tns:Add"/>
</wsdl:message>
```

<span data-ttu-id="32380-113"><xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> Özelliği iletinin biçimini belirler.</span><span class="sxs-lookup"><span data-stu-id="32380-113">The <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> property determines the format of the message.</span></span> <span data-ttu-id="32380-114">Olası değerler şunlardır <xref:System.ServiceModel.OperationFormatUse.Literal> ve <xref:System.ServiceModel.OperationFormatUse.Encoded>varsayılan değerdir <xref:System.ServiceModel.OperationFormatUse.Literal>.</span><span class="sxs-lookup"><span data-stu-id="32380-114">Possible values are <xref:System.ServiceModel.OperationFormatUse.Literal> and <xref:System.ServiceModel.OperationFormatUse.Encoded>; the default value is <xref:System.ServiceModel.OperationFormatUse.Literal>.</span></span> <span data-ttu-id="32380-115">Değişmez değer, aşağıdaki belge/değişmez örnekte gösterildiği gibi, WSDL 'deki şemanın değişmez bir örneği olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="32380-115">Literal means that the message is a literal instance of the schema in the WSDL as shown in the following Document/ Literal example.</span></span>

```xml
<Add xmlns="http://Microsoft.ServiceModel.Samples">
  <n1>100</n1>
  <n2>15.99</n2>
</Add>
```

<span data-ttu-id="32380-116">Kodlanan, WSDL 'deki şemaların SOAP 1,1 Bölüm 5 ' te bulunan kurallara göre kodlanan soyut belirtimlerdir.</span><span class="sxs-lookup"><span data-stu-id="32380-116">Encoded means that the schemas in the WSDL are abstract specifications that are encoded according to the rules found in SOAP 1.1 section 5.</span></span> <span data-ttu-id="32380-117">Aşağıda bir RPC/kodlanmış örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="32380-117">The following is an RPC/Encoded example.</span></span>

```xml
<q1:Add xmlns:q1="http://Microsoft.ServiceModel.Samples">
  <n1 xsi:type="xsd:double" xmlns="">100</n1>
  <n2 xsi:type="xsd:double" xmlns="">15.99</n2>
</q1:Add>
```

<span data-ttu-id="32380-118">WS-ı temel profil 1,0, kullanımını yasaklar <xref:System.ServiceModel.OperationFormatUse.Encoded> ve yalnızca eski hizmetler için gerektiğinde kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="32380-118">The WS-I Basic Profile 1.0 prohibits the use of <xref:System.ServiceModel.OperationFormatUse.Encoded> and you should only use it when required by legacy services.</span></span> <span data-ttu-id="32380-119">`Encoded` İleti biçimi yalnızca XmlSerializer kullanılırken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="32380-119">The `Encoded` message format is only available when using the XmlSerializer.</span></span>

<span data-ttu-id="32380-120">Gönderilen ve alınan iletileri görmenizi sağlamak için bu örnek, [izleme ve mesaj günlüğüne](tracing-and-message-logging.md)göre yapılır.</span><span class="sxs-lookup"><span data-stu-id="32380-120">To allow you to see the messages being sent and received, this sample is based on the [Tracing and Message Logging](tracing-and-message-logging.md).</span></span> <span data-ttu-id="32380-121">Hizmet yapılandırması ve kaynak kodu, izleme ve ileti günlüğe kaydetme özelliğini etkinleştirmek ve kullanmak üzere değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="32380-121">The service configuration and source code have been modified to enable and utilize tracing and message logging.</span></span> <span data-ttu-id="32380-122">Ayrıca <xref:System.ServiceModel.WSHttpBinding> , güvenlik olmadan yapılandırılmış, bu nedenle günlüğe kaydedilen iletiler şifresiz biçimde görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="32380-122">In addition, the <xref:System.ServiceModel.WSHttpBinding> has been configured without security, so the logged messages can be viewed in an unencrypted format.</span></span> <span data-ttu-id="32380-123">Elde edilen izleme günlükleri (System. ServiceModel. e2e ve Message. log), [hizmet Izleme Görüntüleyicisi Aracı (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md)kullanılarak görüntülenmelidir.</span><span class="sxs-lookup"><span data-stu-id="32380-123">The resulting trace logs (System.ServiceModel.e2e and Message.log) should be viewed by using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="32380-124">İzlemeler C:\LOGS klasöründe oluşturulacak şekilde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="32380-124">The traces are configured to be created in the C:\LOGS folder.</span></span> <span data-ttu-id="32380-125">Örneği çalıştırmadan önce klasörü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="32380-125">Create the folder before running the sample.</span></span> <span data-ttu-id="32380-126">Izleme Görüntüleyici aracında ileti içeriğini görüntülemek için, aracın hem sol hem de sağ bölmesindeki **iletileri** seçin.</span><span class="sxs-lookup"><span data-stu-id="32380-126">To view message contents in the Trace Viewer tool, select **Messages** in both the left and the right panes of the tool.</span></span>

<span data-ttu-id="32380-127">Aşağıdaki kod, <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> özelliği olarak <xref:System.ServiceModel.OperationFormatUse> ayarlanan hizmet sözleşmesini ve varsayılan <xref:System.ServiceModel.OperationFormatStyle> olarak olarak <xref:System.ServiceModel.OperationFormatStyle.Document>değiştirilen ileti gövdesinin biçimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="32380-127">The following code shows the service contract with the <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> property set to <xref:System.ServiceModel.OperationFormatUse> and the format of the message body changed from the default <xref:System.ServiceModel.OperationFormatStyle> to <xref:System.ServiceModel.OperationFormatStyle.Document>.</span></span>

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

<span data-ttu-id="32380-128">Farklı <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> ve<xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> ayarlar arasındaki farkı görmek için, hizmette değişiklik yapın, istemciyi yeniden oluşturun, örneği çalıştırın ve c:\logs\Message.exe dosyasını hizmet izleme Görüntüleyicisi aracı ile inceleyin.</span><span class="sxs-lookup"><span data-stu-id="32380-128">To see the difference between the different <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> and <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> settings, modify them in the service, regenerate the client, run the sample, and examine the c:\logs\message.logs file with the Service Trace Viewer tool.</span></span> <span data-ttu-id="32380-129">Ayrıca, görüntüleme `http://localhost/ServiceModelSamples/service.svc?wsdl`yoluyla meta veriler üzerindeki etkiyi gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="32380-129">Also observe the impact on the metadata by viewing `http://localhost/ServiceModelSamples/service.svc?wsdl`.</span></span> <span data-ttu-id="32380-130">Hizmetler için meta veriler genellikle birden çok sayfaya ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="32380-130">The metadata for services is typically broken up into multiple pages.</span></span> <span data-ttu-id="32380-131">Ana WSDL sayfası WSDL bağlamalarını içerir, ancak ileti tanımlarını gözlemlemek için görünümünü görüntüleyin `http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0` .</span><span class="sxs-lookup"><span data-stu-id="32380-131">The main wsdl page contains the WSDL bindings, but view `http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0` to observe the message definitions.</span></span>

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="32380-132">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="32380-132">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="32380-133">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="32380-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="32380-134">İletileri günlüğe kaydetmek için bir C:\LOGS dizini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="32380-134">Create a C:\LOGS directory for logging messages.</span></span> <span data-ttu-id="32380-135">Bu dizin için Kullanıcı ağ hizmetine yazma izinleri verin.</span><span class="sxs-lookup"><span data-stu-id="32380-135">Give the user Network Service write permissions for this directory.</span></span>

3. <span data-ttu-id="32380-136">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="32380-136">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="32380-137">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="32380-137">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="32380-138">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="32380-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="32380-139">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="32380-139">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="32380-140">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="32380-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="32380-141">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="32380-141">This sample is located in the following directory.</span></span>
> 
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\UseAndStyle`
