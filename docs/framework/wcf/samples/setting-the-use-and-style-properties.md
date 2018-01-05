---
title: "Kullanım ve Stil Özelliklerini Ayarlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c09a0600-116f-41cf-900a-1b7e4ea4e300
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6f69ce60e6c9ab98ef773fa54b1c057d3c2b3b48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="setting-the-use-and-style-properties"></a><span data-ttu-id="251b8-102">Kullanım ve Stil Özelliklerini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="251b8-102">Setting the Use and Style Properties</span></span>
<span data-ttu-id="251b8-103">Bu örnek kullanım ve stil özelliklerini kullanmak gösterilmiştir <xref:System.ServiceModel.XmlSerializerFormatAttribute> ve <xref:System.ServiceModel.DataContractFormatAttribute>.</span><span class="sxs-lookup"><span data-stu-id="251b8-103">This sample demonstrates how to use the Use and Style properties on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> and the <xref:System.ServiceModel.DataContractFormatAttribute>.</span></span> <span data-ttu-id="251b8-104">Bu özellikler, iletileri nasıl biçimlendirileceğini etkiler.</span><span class="sxs-lookup"><span data-stu-id="251b8-104">These properties affect how messages are formatted.</span></span> <span data-ttu-id="251b8-105">Varsayılan olarak, ileti gövdesi kümesine stiliyle biçimlendirilmiş <xref:System.ServiceModel.OperationFormatStyle.Document>.</span><span class="sxs-lookup"><span data-stu-id="251b8-105">By default, the message body is formatted with the style set to <xref:System.ServiceModel.OperationFormatStyle.Document>.</span></span> <span data-ttu-id="251b8-106">Bu ayarlar, hizmet sözleşmesi düzeyi veya işlemi sözleşme düzeyinde ya da belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="251b8-106">These settings can be specified at either the service contract level or the operation contract level.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="251b8-107">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="251b8-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="251b8-108"><xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> Stil özelliği belirler WSDL meta veri hizmeti için nasıl biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="251b8-108">The <xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> style property determines how the WSDL metadata for the service is formatted.</span></span> <span data-ttu-id="251b8-109">Olası değerler şunlardır: <xref:System.ServiceModel.OperationFormatStyle.Document>, ve <xref:System.ServiceModel.OperationFormatStyle.Rpc>.</span><span class="sxs-lookup"><span data-stu-id="251b8-109">Possible values are <xref:System.ServiceModel.OperationFormatStyle.Document>, and <xref:System.ServiceModel.OperationFormatStyle.Rpc>.</span></span> <span data-ttu-id="251b8-110">RPC için bir işlem değiştirilen iletilerin WSDL gösterimini uzaktan yordam çağrısı değilmiş gibi parametreleri içeren anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="251b8-110">RPC means that the WSDL representation of messages exchanged for an operation contains parameters as if it were a remote procedure call.</span></span> <span data-ttu-id="251b8-111">Bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="251b8-111">The following is an example.</span></span>  
  
```xml  
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">  
  <wsdl:part name="n1" type="xsd:double"/>  
  <wsdl:part name="n2" type="xsd:double"/>  
</wsdl:message>  
```  
  
 <span data-ttu-id="251b8-112">Stil ayarını <xref:System.ServiceModel.OperationFormatStyle.Document> WSDL temsili bir işlem için aşağıdaki örnekte gösterildiği gibi değiştirilir belgeyi temsil tek bir öğesi içerir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="251b8-112">Setting the style to <xref:System.ServiceModel.OperationFormatStyle.Document> means that the WSDL representation contains a single element that represents the document that is exchanged for an operation as shown in the following example.</span></span>  
  
```xml  
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">  
  <wsdl:part name="parameters" element="tns:Add"/>  
</wsdl:message>  
```  
  
 <span data-ttu-id="251b8-113"><xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> Özelliği, ileti biçimi belirler.</span><span class="sxs-lookup"><span data-stu-id="251b8-113">The <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> property determines the format of the message.</span></span> <span data-ttu-id="251b8-114">Olası değerler şunlardır: <xref:System.ServiceModel.OperationFormatUse.Literal> ve <xref:System.ServiceModel.OperationFormatUse.Encoded>; varsayılan değer <xref:System.ServiceModel.OperationFormatUse.Literal>.</span><span class="sxs-lookup"><span data-stu-id="251b8-114">Possible values are <xref:System.ServiceModel.OperationFormatUse.Literal> and <xref:System.ServiceModel.OperationFormatUse.Encoded>; the default value is <xref:System.ServiceModel.OperationFormatUse.Literal>.</span></span> <span data-ttu-id="251b8-115">Değişmez değeri anlamına gelir ileti aşağıdaki belgede / değişmez değer gösterildiği gibi WSDL şemada değişmez değer örneği olduğunu örnek.</span><span class="sxs-lookup"><span data-stu-id="251b8-115">Literal means that the message is a literal instance of the schema in the WSDL as shown in the following Document/ Literal example.</span></span>  
  
```xml  
<Add xmlns="http://Microsoft.ServiceModel.Samples">  
  <n1>100</n1>  
  <n2>15.99</n2>  
</Add>  
```  
  
 <span data-ttu-id="251b8-116">SOAP 1.1 Bölüm 5 bulunan kurallarına göre kodlanmış soyut belirtimleri WSDL şemalarda olan kodlanmış.</span><span class="sxs-lookup"><span data-stu-id="251b8-116">Encoded means that the schemas in the WSDL are abstract specifications that are encoded according to the rules found in SOAP 1.1 section 5.</span></span> <span data-ttu-id="251b8-117">RPC/kodlanmış örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="251b8-117">The following is an RPC/Encoded example.</span></span>  
  
```xml  
<q1:Add xmlns:q1="http://Microsoft.ServiceModel.Samples">  
  <n1 xsi:type="xsd:double" xmlns="">100</n1>  
  <n2 xsi:type="xsd:double" xmlns="">15.99</n2>  
</q1:Add>  
```  
  
 <span data-ttu-id="251b8-118">WS-ı temel Profil 1.0 kullanımını yasaklar <xref:System.ServiceModel.OperationFormatUse.Encoded> ve yalnızca bunu eski Hizmetleri tarafından gerekli olduğunda kullanmalısınız.</span><span class="sxs-lookup"><span data-stu-id="251b8-118">The WS-I Basic Profile 1.0 prohibits the use of <xref:System.ServiceModel.OperationFormatUse.Encoded> and you should only use it when required by legacy services.</span></span> <span data-ttu-id="251b8-119">`Encoded` İleti biçimi kullanılabilir yalnızca XmlSerializer kullanırken.</span><span class="sxs-lookup"><span data-stu-id="251b8-119">The `Encoded` message format is only available when using the XmlSerializer.</span></span>  
  
 <span data-ttu-id="251b8-120">Gönderilen ve alınan iletileri görmenize olanak sağlamak için bu örnek dayanır [izleme ve ileti günlüğe kaydetme](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span><span class="sxs-lookup"><span data-stu-id="251b8-120">To allow you to see the messages being sent and received, this sample is based on the [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span></span> <span data-ttu-id="251b8-121">Hizmet yapılandırması ve kaynak kodu, etkinleştirme ve ileti izleme ve kaydetme kullanma değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="251b8-121">The service configuration and source code have been modified to enable and utilize tracing and message logging.</span></span> <span data-ttu-id="251b8-122">Ayrıca, <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> güvenlik olmadan, günlüğe kaydedilen iletilere şifresiz bir biçimde görüntülenebilir şekilde yapılandırıldı.</span><span class="sxs-lookup"><span data-stu-id="251b8-122">In addition, the <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> has been configured without security, so the logged messages can be viewed in an unencrypted format.</span></span> <span data-ttu-id="251b8-123">Sonuçta elde edilen izleme günlükleri (System.ServiceModel.e2e ve Message.log) kullanarak görülmelidir [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="251b8-123">The resulting trace logs (System.ServiceModel.e2e and Message.log) should be viewed by using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="251b8-124">İzlemeler C:\LOGS klasöründe oluşturulması için yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="251b8-124">The traces are configured to be created in the C:\LOGS folder.</span></span> <span data-ttu-id="251b8-125">Örneği çalıştırmadan önce klasörü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="251b8-125">Create the folder before running the sample.</span></span> <span data-ttu-id="251b8-126">İzleme Görüntüleyicisi aracı ileti içeriğini görüntülemek için seçin **iletileri** sol ve sağ bölmeleri aracı.</span><span class="sxs-lookup"><span data-stu-id="251b8-126">To view message contents in the Trace Viewer tool, select **Messages** in both the left and the right panes of the tool.</span></span>  
  
 <span data-ttu-id="251b8-127">Aşağıdaki kod ile hizmet sözleşmesini gösterir <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> özelliğini <xref:System.ServiceModel.OperationFormatUse> ve ileti gövdesinin biçimi değiştirdi varsayılandan <xref:System.ServiceModel.OperationFormatStyle> için <xref:System.ServiceModel.OperationFormatStyle.Document>.</span><span class="sxs-lookup"><span data-stu-id="251b8-127">The following code shows the service contract with the <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> property set to <xref:System.ServiceModel.OperationFormatUse> and the format of the message body changed from the default <xref:System.ServiceModel.OperationFormatStyle> to <xref:System.ServiceModel.OperationFormatStyle.Document>.</span></span>  
  
```  
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
  
 <span data-ttu-id="251b8-128">Farklı arasındaki farkı görmek için <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> ve <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> ayarları hizmetinde değiştirmek, istemci yeniden, örneği çalıştırmak ve hizmet izleme Görüntüleyicisi aracı ile c:\logs\message.logs dosyasını inceleyin.</span><span class="sxs-lookup"><span data-stu-id="251b8-128">To see the difference between the different <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> and <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> settings, modify them in the service, regenerate the client, run the sample, and examine the c:\logs\message.logs file with the Service Trace Viewer tool.</span></span> <span data-ttu-id="251b8-129">Ayrıca meta veriler üzerindeki etkisini http://localhost/ServiceModelSamples/service.svc?wsdl görüntüleyerek inceleyin.</span><span class="sxs-lookup"><span data-stu-id="251b8-129">Also observe the impact on the metadata by viewing http://localhost/ServiceModelSamples/service.svc?wsdl.</span></span> <span data-ttu-id="251b8-130">Hizmetler için meta verileri genellikle birden çok sayfaya bozuk.</span><span class="sxs-lookup"><span data-stu-id="251b8-130">The metadata for services is typically broken up into multiple pages.</span></span> <span data-ttu-id="251b8-131">Ana wsdl sayfa WSDL bağlamalar içeriyor, ancak ileti tanımları izlemek için http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0 görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="251b8-131">The main wsdl page contains the WSDL bindings, but view http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0 to observe the message definitions.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="251b8-132">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="251b8-132">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="251b8-133">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="251b8-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="251b8-134">Günlük iletileri için C:\LOGS dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="251b8-134">Create a C:\LOGS directory for logging messages.</span></span> <span data-ttu-id="251b8-135">Ağ hizmeti yazma izinleri bu dizin için kullanıcı verin.</span><span class="sxs-lookup"><span data-stu-id="251b8-135">Give the user Network Service write permissions for this directory.</span></span>  
  
3.  <span data-ttu-id="251b8-136">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="251b8-136">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="251b8-137">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="251b8-137">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="251b8-138">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="251b8-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="251b8-139">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="251b8-139">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="251b8-140">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="251b8-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="251b8-141">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="251b8-141">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\UseAndStyle`  
  
## <a name="see-also"></a><span data-ttu-id="251b8-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="251b8-142">See Also</span></span>
