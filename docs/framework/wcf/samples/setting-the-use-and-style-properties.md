---
title: Kullanım ve Stil Özelliklerini Ayarlama
ms.date: 03/30/2017
ms.assetid: c09a0600-116f-41cf-900a-1b7e4ea4e300
ms.openlocfilehash: d5e6409e3921d40b14b940786f6344aea657b84b
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43865546"
---
# <a name="setting-the-use-and-style-properties"></a><span data-ttu-id="ef078-102">Kullanım ve Stil Özelliklerini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="ef078-102">Setting the Use and Style Properties</span></span>
<span data-ttu-id="ef078-103">Bu örnek üzerinde kullanım ve stil özelliklerini kullanmayı gösteren <xref:System.ServiceModel.XmlSerializerFormatAttribute> ve <xref:System.ServiceModel.DataContractFormatAttribute>.</span><span class="sxs-lookup"><span data-stu-id="ef078-103">This sample demonstrates how to use the Use and Style properties on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> and the <xref:System.ServiceModel.DataContractFormatAttribute>.</span></span> <span data-ttu-id="ef078-104">Bu özellikler, iletileri nasıl biçimlendirileceğini etkiler.</span><span class="sxs-lookup"><span data-stu-id="ef078-104">These properties affect how messages are formatted.</span></span> <span data-ttu-id="ef078-105">Varsayılan olarak, ileti gövdesi ile stil kümesi biçimlendirilmiş <xref:System.ServiceModel.OperationFormatStyle.Document>.</span><span class="sxs-lookup"><span data-stu-id="ef078-105">By default, the message body is formatted with the style set to <xref:System.ServiceModel.OperationFormatStyle.Document>.</span></span> <span data-ttu-id="ef078-106">Bu ayarlar, ya da hizmet sözleşme düzeyi veya işlem anlaşması düzeyinde belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="ef078-106">These settings can be specified at either the service contract level or the operation contract level.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ef078-107">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="ef078-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ef078-108"><xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> Style özelliği, WSDL hizmet meta verileri nasıl biçimlendirildiğini belirler.</span><span class="sxs-lookup"><span data-stu-id="ef078-108">The <xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> style property determines how the WSDL metadata for the service is formatted.</span></span> <span data-ttu-id="ef078-109">Olası değerler <xref:System.ServiceModel.OperationFormatStyle.Document>, ve <xref:System.ServiceModel.OperationFormatStyle.Rpc>.</span><span class="sxs-lookup"><span data-stu-id="ef078-109">Possible values are <xref:System.ServiceModel.OperationFormatStyle.Document>, and <xref:System.ServiceModel.OperationFormatStyle.Rpc>.</span></span> <span data-ttu-id="ef078-110">RPC uzak yordam çağrısı değilmiş gibi iletiler için bir işlem Değişimi WSDL gösterimini parametreleri içerdiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ef078-110">RPC means that the WSDL representation of messages exchanged for an operation contains parameters as if it were a remote procedure call.</span></span> <span data-ttu-id="ef078-111">Bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ef078-111">The following is an example.</span></span>  
  
```xml  
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">  
  <wsdl:part name="n1" type="xsd:double"/>  
  <wsdl:part name="n2" type="xsd:double"/>  
</wsdl:message>  
```  
  
 <span data-ttu-id="ef078-112">Style ayarını <xref:System.ServiceModel.OperationFormatStyle.Document> WSDL temsili bir işlem için aşağıdaki örnekte gösterildiği gibi değiştirilir belgeyi temsil eden tek bir öğe içerdiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ef078-112">Setting the style to <xref:System.ServiceModel.OperationFormatStyle.Document> means that the WSDL representation contains a single element that represents the document that is exchanged for an operation as shown in the following example.</span></span>  
  
```xml  
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">  
  <wsdl:part name="parameters" element="tns:Add"/>  
</wsdl:message>  
```  
  
 <span data-ttu-id="ef078-113"><xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> Özelliği, ileti biçimi belirler.</span><span class="sxs-lookup"><span data-stu-id="ef078-113">The <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> property determines the format of the message.</span></span> <span data-ttu-id="ef078-114">Olası değerler <xref:System.ServiceModel.OperationFormatUse.Literal> ve <xref:System.ServiceModel.OperationFormatUse.Encoded>; varsayılan değer <xref:System.ServiceModel.OperationFormatUse.Literal>.</span><span class="sxs-lookup"><span data-stu-id="ef078-114">Possible values are <xref:System.ServiceModel.OperationFormatUse.Literal> and <xref:System.ServiceModel.OperationFormatUse.Encoded>; the default value is <xref:System.ServiceModel.OperationFormatUse.Literal>.</span></span> <span data-ttu-id="ef078-115">Değişmez değer anlamına gelir ileti aşağıdaki belge / sabit değer gösterildiği gibi WSDL şemada sabit bir örneğini olduğunu örnek.</span><span class="sxs-lookup"><span data-stu-id="ef078-115">Literal means that the message is a literal instance of the schema in the WSDL as shown in the following Document/ Literal example.</span></span>  
  
```xml  
<Add xmlns="http://Microsoft.ServiceModel.Samples">  
  <n1>100</n1>  
  <n2>15.99</n2>  
</Add>  
```  
  
 <span data-ttu-id="ef078-116">SOAP 1.1 5 bölümüne bulunan kurallara göre kodlanmış soyut belirtimleri WSDL şemalarda olan kodlanmış.</span><span class="sxs-lookup"><span data-stu-id="ef078-116">Encoded means that the schemas in the WSDL are abstract specifications that are encoded according to the rules found in SOAP 1.1 section 5.</span></span> <span data-ttu-id="ef078-117">RPC/kodlanmış örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ef078-117">The following is an RPC/Encoded example.</span></span>  
  
```xml  
<q1:Add xmlns:q1="http://Microsoft.ServiceModel.Samples">  
  <n1 xsi:type="xsd:double" xmlns="">100</n1>  
  <n2 xsi:type="xsd:double" xmlns="">15.99</n2>  
</q1:Add>  
```  
  
 <span data-ttu-id="ef078-118">WS-ı temel Profil 1.0 kullanımını engeller <xref:System.ServiceModel.OperationFormatUse.Encoded> ve yalnızca bu eski Hizmetleri tarafından gerekli olduğunda kullanmalısınız.</span><span class="sxs-lookup"><span data-stu-id="ef078-118">The WS-I Basic Profile 1.0 prohibits the use of <xref:System.ServiceModel.OperationFormatUse.Encoded> and you should only use it when required by legacy services.</span></span> <span data-ttu-id="ef078-119">`Encoded` İleti biçimi, yalnızca kullanılabilir XmlSerializer kullanırken.</span><span class="sxs-lookup"><span data-stu-id="ef078-119">The `Encoded` message format is only available when using the XmlSerializer.</span></span>  
  
 <span data-ttu-id="ef078-120">Gönderilen ve alınan iletileri görmek, izin vermek için bu örnek dayanır [izleme ve ileti günlüğe kaydetme](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span><span class="sxs-lookup"><span data-stu-id="ef078-120">To allow you to see the messages being sent and received, this sample is based on the [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span></span> <span data-ttu-id="ef078-121">İleti izleme ve kaydetme yazılımınız olması ve etkinleştirmek için hizmet yapılandırması ve kaynak kodu değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="ef078-121">The service configuration and source code have been modified to enable and utilize tracing and message logging.</span></span> <span data-ttu-id="ef078-122">Ayrıca, <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> güvenlik olmadan, günlüğe kaydedilen iletilere şifresiz bir biçimde görüntülenebilir şekilde yapılandırıldı.</span><span class="sxs-lookup"><span data-stu-id="ef078-122">In addition, the <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> has been configured without security, so the logged messages can be viewed in an unencrypted format.</span></span> <span data-ttu-id="ef078-123">Sonuçta elde edilen izleme günlükleri (System.ServiceModel.e2e ve Message.log) kullanarak görülmelidir [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="ef078-123">The resulting trace logs (System.ServiceModel.e2e and Message.log) should be viewed by using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="ef078-124">İzlemeleri C:\LOGS klasöründe oluşturulması için yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="ef078-124">The traces are configured to be created in the C:\LOGS folder.</span></span> <span data-ttu-id="ef078-125">Bu örneği çalıştırmadan önce klasörü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ef078-125">Create the folder before running the sample.</span></span> <span data-ttu-id="ef078-126">İzleme Görüntüleyicisi aracı ileti içeriği görüntülemek için seçin **iletileri** sol ve sağ bölmeleri aracı.</span><span class="sxs-lookup"><span data-stu-id="ef078-126">To view message contents in the Trace Viewer tool, select **Messages** in both the left and the right panes of the tool.</span></span>  
  
 <span data-ttu-id="ef078-127">Aşağıdaki kod ile hizmet sözleşmesini gösterir <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> özelliğini <xref:System.ServiceModel.OperationFormatUse> ve ileti gövdesi biçiminin varsayılandan <xref:System.ServiceModel.OperationFormatStyle> için <xref:System.ServiceModel.OperationFormatStyle.Document>.</span><span class="sxs-lookup"><span data-stu-id="ef078-127">The following code shows the service contract with the <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> property set to <xref:System.ServiceModel.OperationFormatUse> and the format of the message body changed from the default <xref:System.ServiceModel.OperationFormatStyle> to <xref:System.ServiceModel.OperationFormatStyle.Document>.</span></span>  
  
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
  
 <span data-ttu-id="ef078-128">Farklı arasındaki farkı görmek için <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> ve <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> ayarları, bunları hizmette değiştirmek, istemci yeniden, örneği çalıştırmak ve hizmet izleme Görüntüleyicisi aracı ile c:\logs\message.logs dosyasını inceleyin.</span><span class="sxs-lookup"><span data-stu-id="ef078-128">To see the difference between the different <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> and <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> settings, modify them in the service, regenerate the client, run the sample, and examine the c:\logs\message.logs file with the Service Trace Viewer tool.</span></span> <span data-ttu-id="ef078-129">Ayrıca görüntüleyerek meta veriler üzerindeki etkisini gözlemlemek http://localhost/ServiceModelSamples/service.svc?wsdl.</span><span class="sxs-lookup"><span data-stu-id="ef078-129">Also observe the impact on the metadata by viewing http://localhost/ServiceModelSamples/service.svc?wsdl.</span></span> <span data-ttu-id="ef078-130">Meta Veri Hizmetleri için genellikle birden çok sayfalarına ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="ef078-130">The metadata for services is typically broken up into multiple pages.</span></span> <span data-ttu-id="ef078-131">WSDL bağlamaları ana wsdl sayfa içeriyor, ancak görüntüleme http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0 ileti tanımları gözlemleyin.</span><span class="sxs-lookup"><span data-stu-id="ef078-131">The main wsdl page contains the WSDL bindings, but view http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0 to observe the message definitions.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ef078-132">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="ef078-132">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ef078-133">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ef078-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="ef078-134">Günlük iletileri için bir C:\LOGS dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ef078-134">Create a C:\LOGS directory for logging messages.</span></span> <span data-ttu-id="ef078-135">Ağ hizmeti yazma izinleri bu dizin için kullanıcıya sağlayın.</span><span class="sxs-lookup"><span data-stu-id="ef078-135">Give the user Network Service write permissions for this directory.</span></span>  
  
3.  <span data-ttu-id="ef078-136">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ef078-136">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="ef078-137">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ef078-137">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ef078-138">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="ef078-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ef078-139">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="ef078-139">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ef078-140">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="ef078-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ef078-141">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="ef078-141">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\UseAndStyle`  
  
## <a name="see-also"></a><span data-ttu-id="ef078-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ef078-142">See Also</span></span>
