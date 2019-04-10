---
title: WCF Bilinen Adını COM İstemcileri ile Kullanma
ms.date: 03/30/2017
ms.assetid: e2799bfe-88bd-49d7-9d6d-ac16a9b16b04
ms.openlocfilehash: 14907dd3df66478e8f84b7735a84dd500855448b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59294853"
---
# <a name="using-the-wcf-moniker-with-com-clients"></a><span data-ttu-id="42a96-102">WCF Bilinen Adını COM İstemcileri ile Kullanma</span><span class="sxs-lookup"><span data-stu-id="42a96-102">Using the WCF Moniker with COM Clients</span></span>
<span data-ttu-id="42a96-103">Bu örnek, Windows Communication Foundation (WCF) hizmet bilinen adını COM tabanlı geliştirme ortamlarına uygulamaları (Office VBA) için Microsoft Office Visual Basic veya Visual Basic 6.0 gibi Web Hizmetleri Tümleştirme için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="42a96-103">This sample demonstrates how to use the Windows Communication Foundation (WCF) service moniker to integrate Web services into COM-based development environments, such as Microsoft Office Visual Basic for Applications (Office VBA) or Visual Basic 6.0.</span></span> <span data-ttu-id="42a96-104">Bu örnek bir Windows komut dosyası ana bilgisayarı istemci (.vbs) destekleyen bir istemci kitaplığı (.dll) ve Internet Information Services (IIS) tarafından barındırılan bir hizmet kitaplığı (.dll) oluşur.</span><span class="sxs-lookup"><span data-stu-id="42a96-104">This sample consists of a Windows Script Host client (.vbs), a supporting client library (.dll), and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="42a96-105">Hizmet hesap makinesi hizmetidir ve COM istemcisi matematik işlemlerini çağıran — ekleme, çıkarma, çarpma ve bölme — hizmet.</span><span class="sxs-lookup"><span data-stu-id="42a96-105">The service is a calculator service and the COM client calls math operations—Add, Subtract, Multiply, and Divide—on the service.</span></span> <span data-ttu-id="42a96-106">İleti kutusu windows istemci etkinliği görülebilir.</span><span class="sxs-lookup"><span data-stu-id="42a96-106">Client activity is visible in the message box windows.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="42a96-107">Bu örnek için Kurulum yordamı ve derleme yönergeleri Bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="42a96-107">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="42a96-108">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="42a96-108">The samples may already be installed on your computer.</span></span> <span data-ttu-id="42a96-109">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="42a96-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="42a96-110">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="42a96-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="42a96-111">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="42a96-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\COM`  
  
 <span data-ttu-id="42a96-112">Hizmet uygulayan bir `ICalculator` sözleşme aşağıdaki kod örneğinde gösterildiği gibi tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="42a96-112">The service implements an `ICalculator` contract defined as shown in the following code example.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="42a96-113">Örneği için bilinen ad kullanarak üç alternatif yaklaşımlar gösterir:</span><span class="sxs-lookup"><span data-stu-id="42a96-113">The sample demonstrates the three alternative approaches for using the moniker:</span></span>  
  
-   <span data-ttu-id="42a96-114">Yazılı Sözleşme – Sözleşme, istemci bilgisayarda bir COM görünür türü olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="42a96-114">Typed contract – The contract is registered as a COM visible type on the client computer.</span></span>  
  
-   <span data-ttu-id="42a96-115">WSDL sözleşme – sözleşmenin bir WSDL Belgesi biçiminde sağlanır.</span><span class="sxs-lookup"><span data-stu-id="42a96-115">WSDL contract – The contract is supplied in the form of a WSDL document.</span></span>  
  
-   <span data-ttu-id="42a96-116">Çalışma zamanında bir meta veri değişimi (MEX) uç noktasından metadata Exchange Sözleşme – Sözleşme alınır.</span><span class="sxs-lookup"><span data-stu-id="42a96-116">Metadata Exchange contract – The contract is retrieved at runtime from a Metadata Exchange (MEX) endpoint.</span></span>  
  
## <a name="typed-contract"></a><span data-ttu-id="42a96-117">Yazılı sözleşme</span><span class="sxs-lookup"><span data-stu-id="42a96-117">Typed Contract</span></span>  
 <span data-ttu-id="42a96-118">Bilinen ad yazılı sözleşme ile kullanma için hizmet sözleşmesi için uygun şekilde öznitelikli türleri com ile kayıtlı olması gerekir</span><span class="sxs-lookup"><span data-stu-id="42a96-118">To use the moniker with a typed contract use, appropriately attributed types for the service contract must be registered with COM.</span></span> <span data-ttu-id="42a96-119">İlk olarak, bir istemci kullanarak oluşturulmalıdır [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="42a96-119">First, a client must be generated by using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="42a96-120">Türü belirtilmiş bir proxy oluşturmak için istemci dizininde bir komut isteminden aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="42a96-120">Run the following command from a command prompt in the client directory to generate the typed proxy.</span></span>  
  
```console  
svcutil.exe /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost/servicemodelsamples/service.svc /out:generatedClient.cs  
```  
  
 <span data-ttu-id="42a96-121">Bu sınıf, bir projede eklenmelidir ve proje yapılandırılmalıdır bir COM görünür oluşturmak için derlendiğinde derleme imzalanmış.</span><span class="sxs-lookup"><span data-stu-id="42a96-121">This class must be included in a project and the project should be configured to generate a COM-visible, signed assembly when compiled.</span></span> <span data-ttu-id="42a96-122">AssemblyInfo.cs dosyasında aşağıdaki öznitelik eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="42a96-122">The following attribute should be included in the AssemblyInfo.cs file.</span></span>  
  
```csharp
[assembly: ComVisible(true)]  
```  
  
 <span data-ttu-id="42a96-123">COM görünür türü kullanarak kaydedin projeyi oluşturduktan sonra `regasm` aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="42a96-123">After building the project, register the COM-visible types by using `regasm` as shown in the following example.</span></span>  
  
```console  
regasm.exe /tlb:CalcProxy.tlb client.dll  
```  
  
 <span data-ttu-id="42a96-124">Oluşturulan derleme Genel Derleme Önbelleği'ne eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="42a96-124">The assembly that is created should be added to the Global Assembly Cache.</span></span> <span data-ttu-id="42a96-125">Ancak bu gerekli kesinlikle olmadığında, bu çalışma zamanının bütünleştirilmiş bulma işlemini basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="42a96-125">Though not strictly required, this simplifies the process of the runtime locating the assembly.</span></span> <span data-ttu-id="42a96-126">Aşağıdaki komut, derleme Genel Derleme Önbelleği'ne ekler.</span><span class="sxs-lookup"><span data-stu-id="42a96-126">The following command adds the assembly to the Global Assembly Cache.</span></span>  
  
```  
gacutil.exe /i client.dll  
```  
  
> [!NOTE]
>  <span data-ttu-id="42a96-127">Hizmet bilinen adı, yalnızca tür kaydı gerektirir ve proxy hizmeti ile iletişim kurmak için kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="42a96-127">The service moniker requires only the type registration and does not use the proxy to communicate with the service.</span></span>  
  
 <span data-ttu-id="42a96-128">ComCalcClient.vbs istemci uygulamanın kullandığı `GetObject` bağlamayı adresini belirtmek için hizmet bilinen adı sözdizimini kullanarak bir proxy hizmeti oluşturun ve hizmet için sözleşme işlevi.</span><span class="sxs-lookup"><span data-stu-id="42a96-128">ComCalcClient.vbs client application uses the `GetObject` function to construct a proxy for the service, using the service moniker syntax to specify the address, binding, and contract for the service.</span></span>  
  
```vbscript
Set typedServiceMoniker = GetObject(  
"service4:address=http://localhost/ServiceModelSamples/service.svc, binding=wsHttpBinding,   
contractType={9213C6D2-5A6F-3D26-839B-3BA9B82228D3}")  
```  
  
 <span data-ttu-id="42a96-129">Bilinen ad tarafından kullanılan parametreleri belirtin:</span><span class="sxs-lookup"><span data-stu-id="42a96-129">The parameters used by the moniker specify:</span></span>  
  
-   <span data-ttu-id="42a96-130">Hizmet uç noktası adresi.</span><span class="sxs-lookup"><span data-stu-id="42a96-130">The address of the service endpoint.</span></span>  
  
-   <span data-ttu-id="42a96-131">İstemci uç noktasına bağlanmak için kullanması gereken bağlama.</span><span class="sxs-lookup"><span data-stu-id="42a96-131">The binding that the client should use to connect with that endpoint.</span></span> <span data-ttu-id="42a96-132">İstemci yapılandırma dosyalarında özel bağlamalar tanımlanabilir, ancak bu durumda, sistem tarafından tanımlanan wsHttpBinding kullanılır.</span><span class="sxs-lookup"><span data-stu-id="42a96-132">In this case, the system-defined wsHttpBinding is used though custom bindings can be defined in client configuration files.</span></span> <span data-ttu-id="42a96-133">Windows Script Host ile kullanım için özel bağlama Cscript.exe aynı dizine Cscript.exe.config dosyasında tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="42a96-133">For use with the Windows Script Host, the custom binding is defined in a Cscript.exe.config file in the same directory as Cscript.exe.</span></span>  
  
-   <span data-ttu-id="42a96-134">Uç noktada desteklenen sözleşme türü.</span><span class="sxs-lookup"><span data-stu-id="42a96-134">The type of the contract that is supported at the endpoint.</span></span> <span data-ttu-id="42a96-135">Bu, oluşturulan ve yukarıda kayıtlı türüdür.</span><span class="sxs-lookup"><span data-stu-id="42a96-135">This is the type that was generated and registered above.</span></span> <span data-ttu-id="42a96-136">Visual Basic komut dosyası türü kesin belirlenmiş bir COM ortam sağlamadığından, sözleşme için bir tanımlayıcı belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="42a96-136">Because Visual Basic script does not provide a strongly-typed COM environment, an identifier for the contract must be specified.</span></span> <span data-ttu-id="42a96-137">Bu GUID `interfaceID` CalcProxy.tlb hangi görüntülenebilir OLE/COM Nesne Görüntüleyicisi'ni (OleView.exe) gibi COM araçlarını kullanarak.</span><span class="sxs-lookup"><span data-stu-id="42a96-137">This GUID is the `interfaceID` from CalcProxy.tlb, which can be viewed by using COM tools such as the OLE/COM Object Viewer (OleView.exe).</span></span> <span data-ttu-id="42a96-138">Kesin tür belirtilmiş Office VBA veya Visual Basic 6.0 gibi ortamları için açık bir tür kitaplığı başvuru ekleme ve ardından proxy nesnesinin türü bildirmek yerine sözleşme parametresi kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="42a96-138">For strongly-typed environments such as Office VBA or Visual Basic 6.0, adding an explicit reference to the type library and then declaring the type of the proxy object can be used in place of the contract parameter.</span></span> <span data-ttu-id="42a96-139">Bu da istemci uygulama geliştirme sırasında IntelliSense desteği sunar.</span><span class="sxs-lookup"><span data-stu-id="42a96-139">This also provides IntelliSense support during client application development.</span></span>  
  
 <span data-ttu-id="42a96-140">Hizmet bilinen adı proxy örneğiyle çağrılamadığından istemci uygulama, hizmet bilinen adı altyapısında karşılık gelen hizmet işlemleri çağırma sonuçları proxy yöntemleri çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="42a96-140">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "Typed service moniker: 100 + 15.99 = " & typedServiceMoniker.Add(100, 15.99)  
```  
  
 Örneği çalıştırdığınızda, işlem yanıtı Windows Script Host ileti kutusu penceresinde görüntülenir. Bu, bir WCF Hizmeti ile iletişim kurmak için belirlenmiş bilinen adını kullanarak COM aramaları yapmadan bir COM istemcisi gösterir. <span data-ttu-id="42a96-143">Kullanımını COM rağmen istemci uygulama, hizmet ile iletişim yalnızca Web hizmeti çağrıları oluşur.</span><span class="sxs-lookup"><span data-stu-id="42a96-143">Despite the use of COM in the client application, the communication with the service consists only of Web service calls.</span></span>  
  
## <a name="wsdl-contract"></a><span data-ttu-id="42a96-144">WSDL Sözleşmesi</span><span class="sxs-lookup"><span data-stu-id="42a96-144">WSDL Contract</span></span>  
 <span data-ttu-id="42a96-145">WSDL sözleşme bilinen ad kullanmak için istemci kitaplığı kayıt gerekli değil ancak WSDL hizmet sözleşmesini hizmeti için WSDL uç noktasına erişmek için bir tarayıcı kullanarak gibi bir bant dışı mekanizması aracılığıyla alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="42a96-145">To use the moniker with a WSDL contract, no client library registration is required but the WSDL contract for the service must be retrieved through an out-of-band mechanism such as using a browser to access the WSDL endpoint for the service.</span></span> <span data-ttu-id="42a96-146">Bilinen ad, daha sonra bu sözleşme yürütme zamanında erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="42a96-146">The moniker can then access that contract at execution time.</span></span>  
  
 <span data-ttu-id="42a96-147">ComCalcClient.vbs istemci uygulamanın kullandığı `FileSystemObject` yerel olarak kaydedilmiş bir WSDL dosyasına erişmek için ve daha sonra tekrar kullanır `GetObject` bir proxy hizmeti oluşturmak için işlev.</span><span class="sxs-lookup"><span data-stu-id="42a96-147">The ComCalcClient.vbs client application uses the `FileSystemObject` to access the locally saved WSDL file and then again uses the `GetObject` function to construct a proxy for the service.</span></span>  
  
```vbscript  
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
  
 <span data-ttu-id="42a96-148">Bilinen ad tarafından kullanılan parametreleri belirtin:</span><span class="sxs-lookup"><span data-stu-id="42a96-148">The parameters used by the moniker specify:</span></span>  
  
-   <span data-ttu-id="42a96-149">Hizmet uç noktası adresi.</span><span class="sxs-lookup"><span data-stu-id="42a96-149">The address of the service endpoint.</span></span>  
  
-   <span data-ttu-id="42a96-150">İstemci bu uç nokta ve bu bağlama tanımlandığı ad alanı ile bağlanmak için kullanması gereken bağlama.</span><span class="sxs-lookup"><span data-stu-id="42a96-150">The binding that the client should use to connect with that endpoint and the namespace in which that binding is defined.</span></span> <span data-ttu-id="42a96-151">Bu durumda, `wsHttpBinding_ICalculator` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="42a96-151">In this case, the `wsHttpBinding_ICalculator` is used.</span></span>  
  
-   <span data-ttu-id="42a96-152">Sözleşme tanımlayan bir WSDL.</span><span class="sxs-lookup"><span data-stu-id="42a96-152">The WSDL that defines the contract.</span></span> <span data-ttu-id="42a96-153">Bu durumda serviceWsdl.xml dosyadan okunan dize budur.</span><span class="sxs-lookup"><span data-stu-id="42a96-153">In this case this is the string that has been read from the serviceWsdl.xml file.</span></span>  
  
-   <span data-ttu-id="42a96-154">Sözleşme ad alanı ve adı.</span><span class="sxs-lookup"><span data-stu-id="42a96-154">The name and namespace of the contract.</span></span> <span data-ttu-id="42a96-155">WSDL birden fazla sözleşme içeriyor olabileceğinden, bu kimliği gereklidir.</span><span class="sxs-lookup"><span data-stu-id="42a96-155">This identification is required because the WSDL may contain more than one contract.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="42a96-156">Varsayılan olarak, her ad alanı için ayrı bir WSDL dosyası WCF hizmetleri oluşturun, kullanın.</span><span class="sxs-lookup"><span data-stu-id="42a96-156">By default, WCF services generate separate WSDL files for each namespace that the use.</span></span> <span data-ttu-id="42a96-157">Bu, WSDL içeri aktarma yapısı kullanımı ile bağlantılıdır.</span><span class="sxs-lookup"><span data-stu-id="42a96-157">These are linked with the use of the WSDL import construct.</span></span> <span data-ttu-id="42a96-158">Tek bir WSDL tanımı ad beklediği için bu örnekte gösterildiği gibi hizmeti ya da tek bir ad kullanmalısınız veya ayrı dosyaları el ile birleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="42a96-158">Because the moniker expects a single WSDL definition, the service must either use a single namespace as demonstrated in this sample or the separate files must be manually merged.</span></span>  
  
 <span data-ttu-id="42a96-159">Hizmet bilinen adı proxy örneğiyle çağrılamadığından istemci uygulama, hizmet bilinen adı altyapısında karşılık gelen hizmet işlemleri çağırma sonuçları proxy yöntemleri çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="42a96-159">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
```  
  
 Örneği çalıştırdığınızda, işlem yanıtı Windows Script Host ileti kutusu penceresinde görüntülenir. <span data-ttu-id="42a96-161">Bu bir COM istemcisi bir WCF Hizmeti ile iletişim kurmak için WSDL sözleşme bilinen adını kullanarak COM çağrıları yapma gösterir.</span><span class="sxs-lookup"><span data-stu-id="42a96-161">This demonstrates a COM client making COM calls using the moniker with a WSDL contract to communicate with a WCF service.</span></span>  
  
## <a name="metadata-exchange-contract"></a><span data-ttu-id="42a96-162">Meta veri değişimi Sözleşmesi</span><span class="sxs-lookup"><span data-stu-id="42a96-162">Metadata Exchange Contract</span></span>  
 <span data-ttu-id="42a96-163">WSDL sözleşmesi gibi bilinen ad MEX sözleşme ile kullanmak için istemci kayıt gerekli değil.</span><span class="sxs-lookup"><span data-stu-id="42a96-163">To use the moniker with a MEX contract, as with the WSDL contract, no client registration is required.</span></span> <span data-ttu-id="42a96-164">Hizmet sözleşmesini meta veri değişimi iç kullanımı aracılığıyla yürütme zamanında alınır.</span><span class="sxs-lookup"><span data-stu-id="42a96-164">The contract for the service is retrieved at execution time through the internal use of Metadata Exchange.</span></span>  
  
 <span data-ttu-id="42a96-165">ComCalcClient.vbs istemci uygulamaya yeniden kullanan `GetObject` bir proxy hizmeti oluşturmak için işlev.</span><span class="sxs-lookup"><span data-stu-id="42a96-165">The ComCalcClient.vbs client application again uses the `GetObject` function to construct a proxy for the service.</span></span>  
  
```vbscript  
' Create a string for the service moniker specifying the address to retrieve the service metadata from  
mexMonikerString = "service4:mexAddress='http://localhost/servicemodelsamples/service.svc/mex'"  
mexMonikerString = mexMonikerString + ", address='http://localhost/ServiceModelSamples/service.svc'"  
mexMonikerString = mexMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
mexMonikerString = mexMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set mexServiceMoniker = GetObject(mexMonikerString)  
```  
  
 <span data-ttu-id="42a96-166">Bilinen ad tarafından kullanılan parametreleri belirtin:</span><span class="sxs-lookup"><span data-stu-id="42a96-166">The parameters used by the moniker specify:</span></span>  
  
-   <span data-ttu-id="42a96-167">Hizmet meta veri değişimi uç noktası adresi.</span><span class="sxs-lookup"><span data-stu-id="42a96-167">The address of the service metadata exchange endpoint.</span></span>  
  
-   <span data-ttu-id="42a96-168">Hizmet uç noktası adresi.</span><span class="sxs-lookup"><span data-stu-id="42a96-168">The address of the service endpoint.</span></span>  
  
-   <span data-ttu-id="42a96-169">İstemci bu uç nokta ve bu bağlama tanımlandığı ad alanı ile bağlanmak için kullanması gereken bağlama.</span><span class="sxs-lookup"><span data-stu-id="42a96-169">The binding that the client should use to connect with that endpoint and the namespace in which that binding is defined.</span></span> <span data-ttu-id="42a96-170">Bu durumda, `wsHttpBinding_ICalculator` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="42a96-170">In this case, the `wsHttpBinding_ICalculator` is used.</span></span>  
  
-   <span data-ttu-id="42a96-171">Sözleşme ad alanı ve adı.</span><span class="sxs-lookup"><span data-stu-id="42a96-171">The name and namespace of the contract.</span></span> <span data-ttu-id="42a96-172">WSDL birden fazla sözleşme içeriyor olabileceğinden, bu kimliği gereklidir.</span><span class="sxs-lookup"><span data-stu-id="42a96-172">This identification is required because the WSDL may contain more than one contract.</span></span>  
  
 <span data-ttu-id="42a96-173">Hizmet bilinen adı proxy örneğiyle çağrılamadığından istemci uygulama, hizmet bilinen adı altyapısında karşılık gelen hizmet işlemleri çağırma sonuçları proxy yöntemleri çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="42a96-173">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "MEX service moniker: 9 * 81.25 = " & mexServiceMoniker.Multiply(9, 81.25)  
```  
  
 Örneği çalıştırdığınızda, işlem yanıtı Windows Script Host ileti kutusu penceresinde görüntülenir. <span data-ttu-id="42a96-175">Bu ad, bir WCF Hizmeti ile iletişim kurmak için MEX sözleşme kullanarak COM çağrıları yapma bir COM istemcisi gösterir.</span><span class="sxs-lookup"><span data-stu-id="42a96-175">This demonstrates a COM client making COM calls using the moniker with a MEX contract to communicate with a WCF service.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="42a96-176">Ayarlama ve örneği oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="42a96-176">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="42a96-177">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="42a96-177">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="42a96-178">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="42a96-178">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="42a96-179">Visual Studio için geliştirici komut isteminden, dile özgü klasörü altında \client\bin klasörü açın.</span><span class="sxs-lookup"><span data-stu-id="42a96-179">From a Developer Command Prompt for Visual Studio, open the \client\bin folder, under the language-specific folder.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="42a96-180">Kullanıyorsanız [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], Windows 7 veya Windows Server 2008 R2'de, yönetici ayrıcalıklarına sahip komut isteminden çalıştırdığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="42a96-180">If you are using [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], Windows 7, or Windows Server 2008 R2, make sure that you run the command prompt with administrator privileges.</span></span>  
  
4. <span data-ttu-id="42a96-181">Yazın `tlbexp.exe client.dll /out:CalcProxy.tlb` dll tlb dosyasına dışarı aktarmak için.</span><span class="sxs-lookup"><span data-stu-id="42a96-181">Type in `tlbexp.exe client.dll /out:CalcProxy.tlb` to export the dll to a tlb file.</span></span> <span data-ttu-id="42a96-182">Bir "tür kitaplığı dışarı Aktarıcı Uyarısı" bekleniyordu, ancak genel tür gerekli olmadığından bir sorun değildir.</span><span class="sxs-lookup"><span data-stu-id="42a96-182">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
5. <span data-ttu-id="42a96-183">Yazın `regasm.exe /tlb:CalcProxy.tlb client.dll` türleri com ile kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="42a96-183">Type in `regasm.exe /tlb:CalcProxy.tlb client.dll` to register the types with COM.</span></span> <span data-ttu-id="42a96-184">Bir "tür kitaplığı dışarı Aktarıcı Uyarısı" bekleniyordu, ancak genel tür gerekli olmadığından bir sorun değildir.</span><span class="sxs-lookup"><span data-stu-id="42a96-184">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
6. <span data-ttu-id="42a96-185">Yazın `gacutil.exe /i client.dll` derlemesi Genel Derleme Önbelleği'ne ekleme.</span><span class="sxs-lookup"><span data-stu-id="42a96-185">Type in `gacutil.exe /i client.dll` to add the assembly to the Global Assembly Cache.</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="42a96-186">Örneği aynı bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="42a96-186">To run the sample on the same computer</span></span>  
  
1. <span data-ttu-id="42a96-187">Hizmeti şu adreste yazarak bir tarayıcı kullanarak erişebileceğiniz test: `http://localhost/servicemodelsamples/service.svc`.</span><span class="sxs-lookup"><span data-stu-id="42a96-187">Test that you can access the service using a browser by typing in the following address: `http://localhost/servicemodelsamples/service.svc`.</span></span> <span data-ttu-id="42a96-188">Yanıtta bir onay sayfası gösterilmelidir.</span><span class="sxs-lookup"><span data-stu-id="42a96-188">A confirmation page should be displayed in response.</span></span>  
  
2. <span data-ttu-id="42a96-189">ComCalcClient.vbs \client, dile özgü klasörü altında çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="42a96-189">Run ComCalcClient.vbs from \client, from under the language-specific folder.</span></span> <span data-ttu-id="42a96-190">İleti kutusu windows istemci etkinliği görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="42a96-190">Client activity is displayed in message box windows.</span></span>  
  
3. <span data-ttu-id="42a96-191">İstemci ve hizmet iletişim kurabildiğini bilmiyorsanız bkz [WCF örnekleri için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="42a96-191">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="42a96-192">Bilgisayarlar arasında örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="42a96-192">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="42a96-193">Hizmet bilgisayarda ServiceModelSamples adlı sanal bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="42a96-193">On the service computer, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="42a96-194">Disk dizini ve sanal dizin oluşturmak için örnek ile dahil Setupvroot.bat betiği kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="42a96-194">The Setupvroot.bat script included with the sample can be used to create the disk directory and virtual directory.</span></span>  
  
2. <span data-ttu-id="42a96-195">Hizmet program dosyaları %SystemDrive%\Inetpub\wwwroot\servicemodelsamples hizmeti bilgisayarında ServiceModelSamples sanal dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="42a96-195">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service computer.</span></span> <span data-ttu-id="42a96-196">\Bin dizinine dosyaları eklemeyi unutmayın.</span><span class="sxs-lookup"><span data-stu-id="42a96-196">Be sure to include the files in the \bin directory.</span></span>  
  
3. <span data-ttu-id="42a96-197">Dile özgü klasörü altında \client klasöründen istemci komut dosyasını istemci bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="42a96-197">Copy the client script file from the \client folder, under the language-specific folder, to the client computer.</span></span>  
  
4. <span data-ttu-id="42a96-198">Betik dosyasında adresi uç nokta tanımı hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="42a96-198">In the script file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="42a96-199">"Localhost" yönelik tüm başvuruları adresindeki bir tam etki alanı adı ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="42a96-199">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
5. <span data-ttu-id="42a96-200">WSDL dosyasını istemci bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="42a96-200">Copy the WSDL file to the client computer.</span></span> <span data-ttu-id="42a96-201">WSDL dosyasındaki serviceWsdl.xml, "localhost" yönelik tüm başvuruları adresindeki bir tam etki alanı adı ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="42a96-201">In the WSDL file, serviceWsdl.xml, replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
6. <span data-ttu-id="42a96-202">Dile özgü klasörü altında \client\bin klasör Client.dll kitaplık istemci bilgisayardaki bir dizine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="42a96-202">Copy the Client.dll library from the \client\bin folder, under the language-specific folder, to a directory on the client computer.</span></span>  
  
7. <span data-ttu-id="42a96-203">Bir komut istemi'nden istemci bilgisayarda, hedef dizine gidin.</span><span class="sxs-lookup"><span data-stu-id="42a96-203">From a command prompt, navigate to that destination directory on the client computer.</span></span> <span data-ttu-id="42a96-204">Kullanıyorsanız [!INCLUDE[wv](../../../../includes/wv-md.md)] veya [!INCLUDE[lserver](../../../../includes/lserver-md.md)], komut istemini yönetici olarak çalıştırdığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="42a96-204">If using [!INCLUDE[wv](../../../../includes/wv-md.md)] or [!INCLUDE[lserver](../../../../includes/lserver-md.md)], make sure to run the command prompt as Administrator.</span></span>  
  
8. <span data-ttu-id="42a96-205">Yazın `tlbexp.exe client.dll /out:CalcProxy.tlb` dll tlb dosyasına dışarı aktarmak için.</span><span class="sxs-lookup"><span data-stu-id="42a96-205">Type in `tlbexp.exe client.dll /out:CalcProxy.tlb` to export the dll to a tlb file.</span></span> <span data-ttu-id="42a96-206">Bir "tür kitaplığı dışarı Aktarıcı Uyarısı" bekleniyordu, ancak genel tür gerekli olmadığından bir sorun değildir.</span><span class="sxs-lookup"><span data-stu-id="42a96-206">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
9. <span data-ttu-id="42a96-207">Yazın `regasm.exe /tlb:CalcProxy.tlb client.dll` türleri com ile kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="42a96-207">Type in `regasm.exe /tlb:CalcProxy.tlb client.dll` to register the types with COM.</span></span> <span data-ttu-id="42a96-208">Bu yolu içeren klasöre ayarlandı olun `regasm.exe` komutu çalıştırmadan önce.</span><span class="sxs-lookup"><span data-stu-id="42a96-208">Ensure that path has been set to the folder that contains `regasm.exe` before you run the command.</span></span>  
  
10. <span data-ttu-id="42a96-209">Yazın `gacutil.exe /i client.dll` derlemesi Genel Derleme Önbelleği'ne ekleme.</span><span class="sxs-lookup"><span data-stu-id="42a96-209">Type in `gacutil.exe /i client.dll` to add the assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="42a96-210">Bu yolu içeren klasöre ayarlandı olun `gacutil.exe` komutu çalıştırmadan önce.</span><span class="sxs-lookup"><span data-stu-id="42a96-210">Ensure that path has been set to the folder that contains `gacutil.exe` before you run the command.</span></span>  
  
11. <span data-ttu-id="42a96-211">Test bir tarayıcı kullanarak istemci bilgisayardan hizmete erişebilir.</span><span class="sxs-lookup"><span data-stu-id="42a96-211">Test that you can access the service from the client computer using a browser.</span></span>  
  
12. <span data-ttu-id="42a96-212">İstemci bilgisayarda ComCalcClient.vbs başlatın.</span><span class="sxs-lookup"><span data-stu-id="42a96-212">On the client computer, launch ComCalcClient.vbs.</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="42a96-213">Sonra örnek temizlemek için</span><span class="sxs-lookup"><span data-stu-id="42a96-213">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="42a96-214">Güvenlik nedenleriyle, sanal dizin tanımını ve örneklerle tamamladığınızda Kurulumu adımları verilen izinler kaldırın.</span><span class="sxs-lookup"><span data-stu-id="42a96-214">For security purposes, remove the virtual directory definition and permissions granted in the setup steps when you are finished with the samples.</span></span>  
