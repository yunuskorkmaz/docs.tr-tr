---
title: WCF Bilinen Adını COM İstemcileri ile Kullanma
ms.date: 03/30/2017
ms.assetid: e2799bfe-88bd-49d7-9d6d-ac16a9b16b04
ms.openlocfilehash: 6d47b9c655db932bb9a4243533fbd01bcf25e0df
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="using-the-wcf-moniker-with-com-clients"></a><span data-ttu-id="0411b-102">WCF Bilinen Adını COM İstemcileri ile Kullanma</span><span class="sxs-lookup"><span data-stu-id="0411b-102">Using the WCF Moniker with COM Clients</span></span>
<span data-ttu-id="0411b-103">Bu örnek, Windows Communication Foundation (WCF) hizmet bilinen adı Microsoft Office Visual Basic for Applications (Office VBA) veya Visual Basic 6.0 gibi COM tabanlı geliştirme ortamlara Web services tümleştirme için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0411b-103">This sample demonstrates how to use the Windows Communication Foundation (WCF) service moniker to integrate Web services into COM-based development environments, such as Microsoft Office Visual Basic for Applications (Office VBA) or Visual Basic 6.0.</span></span> <span data-ttu-id="0411b-104">Bu örnek bir Windows Script Host istemci (.vbs) destekleyen bir istemci kitaplığı (.dll) ve Internet Information Services (IIS) tarafından barındırılan bir hizmet kitaplığı (.dll) oluşur.</span><span class="sxs-lookup"><span data-stu-id="0411b-104">This sample consists of a Windows Script Host client (.vbs), a supporting client library (.dll), and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="0411b-105">Hizmeti bir hesaplama hizmetidir ve COM istemcisi matematik işlemleri çağırır — ekleme, çıkarma, çarpma ve bölme — hizmet üzerinde.</span><span class="sxs-lookup"><span data-stu-id="0411b-105">The service is a calculator service and the COM client calls math operations—Add, Subtract, Multiply, and Divide—on the service.</span></span> <span data-ttu-id="0411b-106">İstemci etkinliği ileti kutusu pencerelerinde görünür olur.</span><span class="sxs-lookup"><span data-stu-id="0411b-106">Client activity is visible in the message box windows.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0411b-107">Kurulum yordam ve yapılandırma yönergeleri Bu örneği için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="0411b-107">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0411b-108">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="0411b-108">The samples may already be installed on your computer.</span></span> <span data-ttu-id="0411b-109">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="0411b-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0411b-110">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="0411b-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0411b-111">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="0411b-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\COM`  
  
 <span data-ttu-id="0411b-112">Hizmet uygulayan bir `ICalculator` aşağıdaki kod örneğinde gösterildiği gibi tanımlanan sözleşme.</span><span class="sxs-lookup"><span data-stu-id="0411b-112">The service implements an `ICalculator` contract defined as shown in the following code example.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
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
  
 <span data-ttu-id="0411b-113">Örnek adı kullanılarak üç alternatif yaklaşımlar gösterir:</span><span class="sxs-lookup"><span data-stu-id="0411b-113">The sample demonstrates the three alternative approaches for using the moniker:</span></span>  
  
-   <span data-ttu-id="0411b-114">Yazılı Sözleşme – Sözleşme, istemci bilgisayardaki COM görünebilir tür olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="0411b-114">Typed contract – The contract is registered as a COM visible type on the client computer.</span></span>  
  
-   <span data-ttu-id="0411b-115">WSDL Sözleşme – Sözleşme WSDL Belgesi biçiminde sağlanır.</span><span class="sxs-lookup"><span data-stu-id="0411b-115">WSDL contract – The contract is supplied in the form of a WSDL document.</span></span>  
  
-   <span data-ttu-id="0411b-116">Meta veri değişimi Sözleşme – Sözleşme çalışma zamanında meta veri değişimi (MEX) uç noktasından alınır.</span><span class="sxs-lookup"><span data-stu-id="0411b-116">Metadata Exchange contract – The contract is retrieved at runtime from a Metadata Exchange (MEX) endpoint.</span></span>  
  
## <a name="typed-contract"></a><span data-ttu-id="0411b-117">Yazılı sözleşme</span><span class="sxs-lookup"><span data-stu-id="0411b-117">Typed Contract</span></span>  
 <span data-ttu-id="0411b-118">Ad bir yazılı sözleşme ile kullanmayı, hizmet sözleşmesi için uygun şekilde öznitelikli türleri com ile kayıtlı olması gerekir</span><span class="sxs-lookup"><span data-stu-id="0411b-118">To use the moniker with a typed contract use, appropriately attributed types for the service contract must be registered with COM.</span></span> <span data-ttu-id="0411b-119">İlk olarak, bir istemci kullanarak oluşturulması gerektiğini [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="0411b-119">First, a client must be generated by using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="0411b-120">Yazılı proxy oluşturmak için istemci dizininde bir komut isteminden aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0411b-120">Run the following command from a command prompt in the client directory to generate the typed proxy.</span></span>  
  
```  
svcutil.exe /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost/servicemodelsamples/service.svc /out:generatedClient.cs  
```  
  
 <span data-ttu-id="0411b-121">Bu sınıf bir proje ile eklenmelidir ve projeyi yapılandırılmalıdır bir COM görünür oluşturmak için derlendiğinde derleme imzalanmamış.</span><span class="sxs-lookup"><span data-stu-id="0411b-121">This class must be included in a project and the project should be configured to generate a COM-visible, signed assembly when compiled.</span></span> <span data-ttu-id="0411b-122">Aşağıdaki öznitelik AssemblyInfo.cs dosyasında bulunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0411b-122">The following attribute should be included in the AssemblyInfo.cs file.</span></span>  
  
```  
[assembly: ComVisible(true)]  
```  
  
 <span data-ttu-id="0411b-123">COM görünebilir türler kullanarak kaydedin projesi oluşturduktan sonra `regasm` aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="0411b-123">After building the project, register the COM-visible types by using `regasm` as shown in the following example.</span></span>  
  
```  
regasm.exe /tlb:CalcProxy.tlb client.dll  
```  
  
 <span data-ttu-id="0411b-124">Oluşturulan derleme genel derleme önbelleği eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="0411b-124">The assembly that is created should be added to the Global Assembly Cache.</span></span> <span data-ttu-id="0411b-125">Kesinlikle olmadığında gerekli ancak bu çalışma zamanı derlemesi bulma işlemini basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="0411b-125">Though not strictly required, this simplifies the process of the runtime locating the assembly.</span></span> <span data-ttu-id="0411b-126">Aşağıdaki komut derlemeyi genel derleme önbelleği ekler.</span><span class="sxs-lookup"><span data-stu-id="0411b-126">The following command adds the assembly to the Global Assembly Cache.</span></span>  
  
```  
gacutil.exe /i client.dll  
```  
  
> [!NOTE]
>  <span data-ttu-id="0411b-127">Hizmet bilinen adı yalnızca türü kayıt gerektirir ve proxy hizmeti ile iletişim kurmak için kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="0411b-127">The service moniker requires only the type registration and does not use the proxy to communicate with the service.</span></span>  
  
 <span data-ttu-id="0411b-128">ComCalcClient.vbs istemci uygulamanın kullandığı `GetObject` işlev bağlama, adresini belirtmek için hizmet adının sözdizimi kullanarak hizmeti için bir proxy oluşturmak ve hizmet için sözleşme.</span><span class="sxs-lookup"><span data-stu-id="0411b-128">ComCalcClient.vbs client application uses the `GetObject` function to construct a proxy for the service, using the service moniker syntax to specify the address, binding, and contract for the service.</span></span>  
  
```  
Set typedServiceMoniker = GetObject(  
"service4:address=http://localhost/ServiceModelSamples/service.svc, binding=wsHttpBinding,   
contractType={9213C6D2-5A6F-3D26-839B-3BA9B82228D3}")  
```  
  
 <span data-ttu-id="0411b-129">Bilinen ad tarafından kullanılan parametreleri belirtin:</span><span class="sxs-lookup"><span data-stu-id="0411b-129">The parameters used by the moniker specify:</span></span>  
  
-   <span data-ttu-id="0411b-130">Hizmet uç noktası adresi.</span><span class="sxs-lookup"><span data-stu-id="0411b-130">The address of the service endpoint.</span></span>  
  
-   <span data-ttu-id="0411b-131">İstemci bu bitiş noktası ile bağlanmak için kullanması gereken bağlama.</span><span class="sxs-lookup"><span data-stu-id="0411b-131">The binding that the client should use to connect with that endpoint.</span></span> <span data-ttu-id="0411b-132">Özel bağlamalar istemci yapılandırma dosyalarında tanımlanabilir ancak bu durumda, sistem tarafından tanımlanan wsHttpBinding kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0411b-132">In this case, the system-defined wsHttpBinding is used though custom bindings can be defined in client configuration files.</span></span> <span data-ttu-id="0411b-133">Windows Script Host ile kullanım için özel bağlama Cscript.exe aynı dizine Cscript.exe.config dosyasında tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="0411b-133">For use with the Windows Script Host, the custom binding is defined in a Cscript.exe.config file in the same directory as Cscript.exe.</span></span>  
  
-   <span data-ttu-id="0411b-134">Uç noktada desteklenen sözleşme türü.</span><span class="sxs-lookup"><span data-stu-id="0411b-134">The type of the contract that is supported at the endpoint.</span></span> <span data-ttu-id="0411b-135">Bu, oluşturulan ve yukarıdaki kayıtlı türüdür.</span><span class="sxs-lookup"><span data-stu-id="0411b-135">This is the type that was generated and registered above.</span></span> <span data-ttu-id="0411b-136">Visual Basic komut dosyası türü kesin belirlenmiş bir COM ortamı sağlamadığından sözleşme için bir tanımlayıcı belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="0411b-136">Because Visual Basic script does not provide a strongly-typed COM environment, an identifier for the contract must be specified.</span></span> <span data-ttu-id="0411b-137">Bu GUID `interfaceID` CalcProxy.tlb hangi görüntülenebilir COM OLE/COM Nesne Görüntüleyicisi'ni (OleView.exe) gibi araçları kullanarak.</span><span class="sxs-lookup"><span data-stu-id="0411b-137">This GUID is the `interfaceID` from CalcProxy.tlb, which can be viewed by using COM tools such as the OLE/COM Object Viewer (OleView.exe).</span></span> <span data-ttu-id="0411b-138">Kesin türü belirtilmiş Office VBA veya Visual Basic 6.0 gibi ortamları için tür kitaplığı için açık bir başvuru ekleyerek ve proxy nesne türünü bildirme yerine sözleşme parametresinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0411b-138">For strongly-typed environments such as Office VBA or Visual Basic 6.0, adding an explicit reference to the type library and then declaring the type of the proxy object can be used in place of the contract parameter.</span></span> <span data-ttu-id="0411b-139">Bu aynı zamanda istemci uygulama geliştirme sırasında IntelliSense desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="0411b-139">This also provides IntelliSense support during client application development.</span></span>  
  
 <span data-ttu-id="0411b-140">Hizmet adının proxy örneğiyle oluşturulmamalıdır istemci uygulaması, karşılık gelen hizmet işlemlerini çağırma hizmet bilinen adı altyapısında sonuçları proxy yöntemleri çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="0411b-140">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```  
' Call the service operations using the moniker object  
WScript.Echo "Typed service moniker: 100 + 15.99 = " & typedServiceMoniker.Add(100, 15.99)  
```  
  
 İşlem yanıtı örneği çalıştırdığınızda, Windows Script Host ileti kutusu penceresinde görüntülenir. Bu bir WCF Hizmeti ile iletişim kurmak için yazılan ad kullanarak COM çağrıları yapma COM istemcisi gösterir. <span data-ttu-id="0411b-143">Kullanımı COM rağmen istemci uygulamasında, yalnızca Web hizmeti çağrıları hizmet ile iletişim oluşur.</span><span class="sxs-lookup"><span data-stu-id="0411b-143">Despite the use of COM in the client application, the communication with the service consists only of Web service calls.</span></span>  
  
## <a name="wsdl-contract"></a><span data-ttu-id="0411b-144">WSDL sözleşme</span><span class="sxs-lookup"><span data-stu-id="0411b-144">WSDL Contract</span></span>  
 <span data-ttu-id="0411b-145">Ad WSDL sözleşme ile kullanmak için istemci kitaplığı kayıt gerekli değil ancak hizmet WSDL sözleşmesini hizmeti WSDL uç noktasına erişmek için bir tarayıcı kullanarak gibi bir bant dışı mekanizması aracılığıyla alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0411b-145">To use the moniker with a WSDL contract, no client library registration is required but the WSDL contract for the service must be retrieved through an out-of-band mechanism such as using a browser to access the WSDL endpoint for the service.</span></span> <span data-ttu-id="0411b-146">Ad, daha sonra bu sözleşme, yürütme esnasında erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0411b-146">The moniker can then access that contract at execution time.</span></span>  
  
 <span data-ttu-id="0411b-147">ComCalcClient.vbs istemci uygulamanın kullandığı `FileSystemObject` yerel olarak kaydedilmiş WSDL dosyaya erişmek için ve daha sonra tekrar kullanır `GetObject` hizmeti için bir proxy oluşturmak için işlevi.</span><span class="sxs-lookup"><span data-stu-id="0411b-147">The ComCalcClient.vbs client application uses the `FileSystemObject` to access the locally saved WSDL file and then again uses the `GetObject` function to construct a proxy for the service.</span></span>  
  
```  
' Open the WSDL contract file and read it all into the wsdlContract string  
Const ForReading = 1  
Set objFSO = CreateObject("Scripting.FileSystemObject")  
Set objFile = objFSO.OpenTextFile("serviceWsdl.xml", ForReading)  
wsdlContract = objFile.ReadAll  
objFile.Close  
  
' Create a string for the service moniker including the content of the WSDL contract file  
wsdlMonikerString = "service4:address='http://localhost/ServiceModelSamples/service.svc'"  
wsdlMonikerString = wsdlMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
wsdlMonikerString = wsdlMonikerString + ", wsdl='" & wsdlContract & "'"  
wsdlMonikerString = wsdlMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set wsdlServiceMoniker = GetObject(wsdlMonikerString)  
```  
  
 <span data-ttu-id="0411b-148">Bilinen ad tarafından kullanılan parametreleri belirtin:</span><span class="sxs-lookup"><span data-stu-id="0411b-148">The parameters used by the moniker specify:</span></span>  
  
-   <span data-ttu-id="0411b-149">Hizmet uç noktası adresi.</span><span class="sxs-lookup"><span data-stu-id="0411b-149">The address of the service endpoint.</span></span>  
  
-   <span data-ttu-id="0411b-150">İstemci bu uç hem de bu bağlamayı tanımlandığı ad alanı ile bağlanmak için kullanması gereken bağlama.</span><span class="sxs-lookup"><span data-stu-id="0411b-150">The binding that the client should use to connect with that endpoint and the namespace in which that binding is defined.</span></span> <span data-ttu-id="0411b-151">Bu durumda, `wsHttpBinding_ICalculator` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0411b-151">In this case, the `wsHttpBinding_ICalculator` is used.</span></span>  
  
-   <span data-ttu-id="0411b-152">Sözleşmesini tanımlayan WSDL.</span><span class="sxs-lookup"><span data-stu-id="0411b-152">The WSDL that defines the contract.</span></span> <span data-ttu-id="0411b-153">Bu durumda serviceWsdl.xml dosyadan okunan dize budur.</span><span class="sxs-lookup"><span data-stu-id="0411b-153">In this case this is the string that has been read from the serviceWsdl.xml file.</span></span>  
  
-   <span data-ttu-id="0411b-154">Ad alanı sözleşmenin ve adını.</span><span class="sxs-lookup"><span data-stu-id="0411b-154">The name and namespace of the contract.</span></span> <span data-ttu-id="0411b-155">WSDL birden fazla sözleşme içerebileceğinden bu kimliği gereklidir.</span><span class="sxs-lookup"><span data-stu-id="0411b-155">This identification is required because the WSDL may contain more than one contract.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0411b-156">Varsayılan olarak, her ad alanı için ayrı WSDL dosyası WCF hizmetleri oluşturmak, kullanın.</span><span class="sxs-lookup"><span data-stu-id="0411b-156">By default, WCF services generate separate WSDL files for each namespace that the use.</span></span> <span data-ttu-id="0411b-157">Bunlar WSDL içe aktarma yapı kullanımı ile bağlanır.</span><span class="sxs-lookup"><span data-stu-id="0411b-157">These are linked with the use of the WSDL import construct.</span></span> <span data-ttu-id="0411b-158">Tek bir WSDL tanımı ad beklediği için bu örnekte gösterildiği gibi hizmet ya da tek bir ad alanı kullanmalısınız veya ayrı dosyalarını el ile birleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="0411b-158">Because the moniker expects a single WSDL definition, the service must either use a single namespace as demonstrated in this sample or the separate files must be manually merged.</span></span>  
  
 <span data-ttu-id="0411b-159">Hizmet adının proxy örneğiyle oluşturulmamalıdır istemci uygulaması, karşılık gelen hizmet işlemlerini çağırma hizmet bilinen adı altyapısında sonuçları proxy yöntemleri çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="0411b-159">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```  
' Call the service operations using the moniker object  
WScript.Echo "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
```  
  
 İşlem yanıtı örneği çalıştırdığınızda, Windows Script Host ileti kutusu penceresinde görüntülenir. <span data-ttu-id="0411b-161">Bu ad, bir WCF Hizmeti ile iletişim kurmak için WSDL sözleşmeyle kullanarak COM aramaları yapmadan COM istemcisi gösterir.</span><span class="sxs-lookup"><span data-stu-id="0411b-161">This demonstrates a COM client making COM calls using the moniker with a WSDL contract to communicate with a WCF service.</span></span>  
  
## <a name="metadata-exchange-contract"></a><span data-ttu-id="0411b-162">Meta veri değişimi sözleşme</span><span class="sxs-lookup"><span data-stu-id="0411b-162">Metadata Exchange Contract</span></span>  
 <span data-ttu-id="0411b-163">WSDL sözleşme olarak bilinen ad MEX sözleşme ile kullanmak için istemci kayıt gerekli değil.</span><span class="sxs-lookup"><span data-stu-id="0411b-163">To use the moniker with a MEX contract, as with the WSDL contract, no client registration is required.</span></span> <span data-ttu-id="0411b-164">Hizmet sözleşmesini meta veri değişimi iç kullanımı aracılığıyla yürütme zamanında alınır.</span><span class="sxs-lookup"><span data-stu-id="0411b-164">The contract for the service is retrieved at execution time through the internal use of Metadata Exchange.</span></span>  
  
 <span data-ttu-id="0411b-165">Yeniden ComCalcClient.vbs istemci uygulamanın kullandığı `GetObject` hizmeti için bir proxy oluşturmak için işlevi.</span><span class="sxs-lookup"><span data-stu-id="0411b-165">The ComCalcClient.vbs client application again uses the `GetObject` function to construct a proxy for the service.</span></span>  
  
```  
' Create a string for the service moniker specifying the address to retrieve the service metadata from  
mexMonikerString = "service4:mexAddress='http://localhost/servicemodelsamples/service.svc/mex'"  
mexMonikerString = mexMonikerString + ", address='http://localhost/ServiceModelSamples/service.svc'"  
mexMonikerString = mexMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
mexMonikerString = mexMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set mexServiceMoniker = GetObject(mexMonikerString)  
```  
  
 <span data-ttu-id="0411b-166">Bilinen ad tarafından kullanılan parametreleri belirtin:</span><span class="sxs-lookup"><span data-stu-id="0411b-166">The parameters used by the moniker specify:</span></span>  
  
-   <span data-ttu-id="0411b-167">Hizmet meta verileri exchange uç adresidir.</span><span class="sxs-lookup"><span data-stu-id="0411b-167">The address of the service metadata exchange endpoint.</span></span>  
  
-   <span data-ttu-id="0411b-168">Hizmet uç noktası adresi.</span><span class="sxs-lookup"><span data-stu-id="0411b-168">The address of the service endpoint.</span></span>  
  
-   <span data-ttu-id="0411b-169">İstemci bu uç hem de bu bağlamayı tanımlandığı ad alanı ile bağlanmak için kullanması gereken bağlama.</span><span class="sxs-lookup"><span data-stu-id="0411b-169">The binding that the client should use to connect with that endpoint and the namespace in which that binding is defined.</span></span> <span data-ttu-id="0411b-170">Bu durumda, `wsHttpBinding_ICalculator` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0411b-170">In this case, the `wsHttpBinding_ICalculator` is used.</span></span>  
  
-   <span data-ttu-id="0411b-171">Ad alanı sözleşmenin ve adını.</span><span class="sxs-lookup"><span data-stu-id="0411b-171">The name and namespace of the contract.</span></span> <span data-ttu-id="0411b-172">WSDL birden fazla sözleşme içerebileceğinden bu kimliği gereklidir.</span><span class="sxs-lookup"><span data-stu-id="0411b-172">This identification is required because the WSDL may contain more than one contract.</span></span>  
  
 <span data-ttu-id="0411b-173">Hizmet adının proxy örneğiyle oluşturulmamalıdır istemci uygulaması, karşılık gelen hizmet işlemlerini çağırma hizmet bilinen adı altyapısında sonuçları proxy yöntemleri çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="0411b-173">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```  
' Call the service operations using the moniker object  
WScript.Echo "MEX service moniker: 9 * 81.25 = " & mexServiceMoniker.Multiply(9, 81.25)  
```  
  
 İşlem yanıtı örneği çalıştırdığınızda, Windows Script Host ileti kutusu penceresinde görüntülenir. <span data-ttu-id="0411b-175">Bu ad, bir WCF Hizmeti ile iletişim kurmak için MEX sözleşmeyle kullanarak COM aramaları yapmadan COM istemcisi gösterir.</span><span class="sxs-lookup"><span data-stu-id="0411b-175">This demonstrates a COM client making COM calls using the moniker with a MEX contract to communicate with a WCF service.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="0411b-176">Ayarlamak ve örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="0411b-176">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="0411b-177">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0411b-177">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="0411b-178">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0411b-178">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="0411b-179">Visual Studio komut isteminden, dile özgü klasörü altında \client\bin klasörünü açın.</span><span class="sxs-lookup"><span data-stu-id="0411b-179">From a Visual Studio command prompt, open the \client\bin folder, under the language-specific folder.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0411b-180">Kullanıyorsanız [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], Windows 7 veya Windows Server 2008 R2, komut istemini yönetici ayrıcalıklarıyla çalıştırın emin olun.</span><span class="sxs-lookup"><span data-stu-id="0411b-180">If you are using [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], Windows 7, or Windows Server 2008 R2, make sure that you run the command prompt with administrator privileges.</span></span>  
  
4.  <span data-ttu-id="0411b-181">Yazın `tlbexp.exe client.dll /out:CalcProxy.tlb` dll tlb dosyaya vermek için.</span><span class="sxs-lookup"><span data-stu-id="0411b-181">Type in `tlbexp.exe client.dll /out:CalcProxy.tlb` to export the dll to a tlb file.</span></span> <span data-ttu-id="0411b-182">Bir "tür kitaplığı dışarı Aktarıcı Uyarısı" bekleniyordu, ancak genel tür gerekli olmadığı için bir sorun değildir.</span><span class="sxs-lookup"><span data-stu-id="0411b-182">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
5.  <span data-ttu-id="0411b-183">Yazın `regasm.exe /tlb:CalcProxy.tlb client.dll` türleri com ile kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="0411b-183">Type in `regasm.exe /tlb:CalcProxy.tlb client.dll` to register the types with COM.</span></span> <span data-ttu-id="0411b-184">Bir "tür kitaplığı dışarı Aktarıcı Uyarısı" bekleniyordu, ancak genel tür gerekli olmadığı için bir sorun değildir.</span><span class="sxs-lookup"><span data-stu-id="0411b-184">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
6.  <span data-ttu-id="0411b-185">Yazın `gacutil.exe /i client.dll` derleme genel derleme önbelleğine eklemek için.</span><span class="sxs-lookup"><span data-stu-id="0411b-185">Type in `gacutil.exe /i client.dll` to add the assembly to the Global Assembly Cache.</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="0411b-186">Aynı bilgisayara örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="0411b-186">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="0411b-187">Hizmeti aşağıdaki adresi yazarak bir tarayıcı kullanarak erişebilirsiniz test: `http://localhost/servicemodelsamples/service.svc`.</span><span class="sxs-lookup"><span data-stu-id="0411b-187">Test that you can access the service using a browser by typing in the following address: `http://localhost/servicemodelsamples/service.svc`.</span></span> <span data-ttu-id="0411b-188">Bir onay sayfasına yanıtta görüntülenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="0411b-188">A confirmation page should be displayed in response.</span></span>  
  
2.  <span data-ttu-id="0411b-189">Dile özgü klasörü altında \client ComCalcClient.vbs çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0411b-189">Run ComCalcClient.vbs from \client, from under the language-specific folder.</span></span> <span data-ttu-id="0411b-190">İstemci etkinliği ileti kutusu Windows'da görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="0411b-190">Client activity is displayed in message box windows.</span></span>  
  
3.  <span data-ttu-id="0411b-191">İstemci ve hizmet iletişim kurabildiğinden değilseniz bkz [sorun giderme ipuçları](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="0411b-191">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="0411b-192">Bilgisayarlar arasında örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="0411b-192">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="0411b-193">Hizmet bilgisayarda ServiceModelSamples adlı bir sanal dizini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0411b-193">On the service computer, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="0411b-194">Örnekle dahil Setupvroot.bat komut dosyası disk dizini ve sanal dizini oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0411b-194">The Setupvroot.bat script included with the sample can be used to create the disk directory and virtual directory.</span></span>  
  
2.  <span data-ttu-id="0411b-195">Hizmet program dosyalarını %SystemDrive%\Inetpub\wwwroot\servicemodelsamples hizmeti bilgisayarında ServiceModelSamples sanal dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="0411b-195">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service computer.</span></span> <span data-ttu-id="0411b-196">Dosyaları \bin dizinine eklediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="0411b-196">Be sure to include the files in the \bin directory.</span></span>  
  
3.  <span data-ttu-id="0411b-197">İstemci komut dosyası \client klasöründen dile özgü klasörü altında istemci bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="0411b-197">Copy the client script file from the \client folder, under the language-specific folder, to the client computer.</span></span>  
  
4.  <span data-ttu-id="0411b-198">Komut dosyasında hizmetinizin yeni adresi ile eşleşmesi için uç nokta tanımındaki adresi değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="0411b-198">In the script file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="0411b-199">Tüm başvuruları "localhost" adresi bir tam etki alanı adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="0411b-199">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
5.  <span data-ttu-id="0411b-200">WSDL dosyasını istemci bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="0411b-200">Copy the WSDL file to the client computer.</span></span> <span data-ttu-id="0411b-201">WSDL dosyasında serviceWsdl.xml, "localhost" yönelik tüm başvuruları adresindeki bir tam etki alanı adı ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="0411b-201">In the WSDL file, serviceWsdl.xml, replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
6.  <span data-ttu-id="0411b-202">Dile özgü klasörü altındaki \client\bin klasöründen Client.dll kitaplığı istemci bilgisayarda bir dizine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="0411b-202">Copy the Client.dll library from the \client\bin folder, under the language-specific folder, to a directory on the client computer.</span></span>  
  
7.  <span data-ttu-id="0411b-203">Bir komut isteminden, istemci bilgisayarda, hedef dizinine gidin.</span><span class="sxs-lookup"><span data-stu-id="0411b-203">From a command prompt, navigate to that destination directory on the client computer.</span></span> <span data-ttu-id="0411b-204">Kullanıyorsanız [!INCLUDE[wv](../../../../includes/wv-md.md)] veya [!INCLUDE[lserver](../../../../includes/lserver-md.md)], komut istemini yönetici olarak çalıştırdığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="0411b-204">If using [!INCLUDE[wv](../../../../includes/wv-md.md)] or [!INCLUDE[lserver](../../../../includes/lserver-md.md)], make sure to run the command prompt as Administrator.</span></span>  
  
8.  <span data-ttu-id="0411b-205">Yazın `tlbexp.exe client.dll /out:CalcProxy.tlb` dll tlb dosyaya vermek için.</span><span class="sxs-lookup"><span data-stu-id="0411b-205">Type in `tlbexp.exe client.dll /out:CalcProxy.tlb` to export the dll to a tlb file.</span></span> <span data-ttu-id="0411b-206">Bir "tür kitaplığı dışarı Aktarıcı Uyarısı" bekleniyordu, ancak genel tür gerekli olmadığı için bir sorun değildir.</span><span class="sxs-lookup"><span data-stu-id="0411b-206">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
9. <span data-ttu-id="0411b-207">Yazın `regasm.exe /tlb:CalcProxy.tlb client.dll` türleri com ile kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="0411b-207">Type in `regasm.exe /tlb:CalcProxy.tlb client.dll` to register the types with COM.</span></span> <span data-ttu-id="0411b-208">Bu yolu içeren klasöre ayarlanmış olun `regasm.exe` komutu çalıştırmadan önce.</span><span class="sxs-lookup"><span data-stu-id="0411b-208">Ensure that path has been set to the folder that contains `regasm.exe` before you run the command.</span></span>  
  
10. <span data-ttu-id="0411b-209">Yazın `gacutil.exe /i client.dll` derleme genel derleme önbelleğine eklemek için.</span><span class="sxs-lookup"><span data-stu-id="0411b-209">Type in `gacutil.exe /i client.dll` to add the assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="0411b-210">Bu yolu içeren klasöre ayarlanmış olun `gacutil.exe` komutu çalıştırmadan önce.</span><span class="sxs-lookup"><span data-stu-id="0411b-210">Ensure that path has been set to the folder that contains `gacutil.exe` before you run the command.</span></span>  
  
11. <span data-ttu-id="0411b-211">Test, hizmet istemci bilgisayar ile bir tarayıcı kullanarak erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0411b-211">Test that you can access the service from the client computer using a browser.</span></span>  
  
12. <span data-ttu-id="0411b-212">İstemci bilgisayarda ComCalcClient.vbs başlatın.</span><span class="sxs-lookup"><span data-stu-id="0411b-212">On the client computer, launch ComCalcClient.vbs.</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="0411b-213">Örnek sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="0411b-213">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="0411b-214">Güvenlik nedeniyle, sanal dizin tanımı ve örnekleri ile işiniz bittiğinde Kurulum adımlarında'ı izinler kaldırın.</span><span class="sxs-lookup"><span data-stu-id="0411b-214">For security purposes, remove the virtual directory definition and permissions granted in the setup steps when you are finished with the samples.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0411b-215">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0411b-215">See Also</span></span>
