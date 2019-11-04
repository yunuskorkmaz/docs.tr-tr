---
title: WCF Bilinen Adını COM İstemcileri ile Kullanma
ms.date: 03/30/2017
ms.assetid: e2799bfe-88bd-49d7-9d6d-ac16a9b16b04
ms.openlocfilehash: 321d59285b0ef86e4631634d90229a0d8e79657b
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424715"
---
# <a name="using-the-wcf-moniker-with-com-clients"></a><span data-ttu-id="842e1-102">WCF Bilinen Adını COM İstemcileri ile Kullanma</span><span class="sxs-lookup"><span data-stu-id="842e1-102">Using the WCF Moniker with COM Clients</span></span>
<span data-ttu-id="842e1-103">Bu örnek, Web hizmetlerini Microsoft Office Visual Basic for Applications (Office VBA) veya Visual Basic 6,0 gibi COM tabanlı geliştirme ortamlarında bütünleştirmek için Windows Communication Foundation (WCF) hizmet bilinen adının nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="842e1-103">This sample demonstrates how to use the Windows Communication Foundation (WCF) service moniker to integrate Web services into COM-based development environments, such as Microsoft Office Visual Basic for Applications (Office VBA) or Visual Basic 6.0.</span></span> <span data-ttu-id="842e1-104">Bu örnek, bir Windows betik ana istemcisi (. vbs), destekleyici istemci kitaplığı (. dll) ve Internet Information Services (IIS) tarafından barındırılan bir hizmet kitaplığı (. dll) içerir.</span><span class="sxs-lookup"><span data-stu-id="842e1-104">This sample consists of a Windows Script Host client (.vbs), a supporting client library (.dll), and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="842e1-105">Hizmet bir Hesaplayıcı hizmetidir ve COM istemcisi, hizmet üzerinde matematik işlemlerini (ekleme, çıkarma, çarpma ve bölme) çağırır.</span><span class="sxs-lookup"><span data-stu-id="842e1-105">The service is a calculator service and the COM client calls math operations—Add, Subtract, Multiply, and Divide—on the service.</span></span> <span data-ttu-id="842e1-106">İstemci etkinliği ileti kutusu penceresinde görünür.</span><span class="sxs-lookup"><span data-stu-id="842e1-106">Client activity is visible in the message box windows.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="842e1-107">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="842e1-107">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="842e1-108">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="842e1-108">The samples may already be installed on your computer.</span></span> <span data-ttu-id="842e1-109">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="842e1-109">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="842e1-110">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://go.microsoft.com/fwlink/?LinkId=150780) gidin.</span><span class="sxs-lookup"><span data-stu-id="842e1-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="842e1-111">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="842e1-111">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\COM`  
  
 <span data-ttu-id="842e1-112">Hizmet, aşağıdaki kod örneğinde gösterildiği gibi tanımlanan bir `ICalculator` sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="842e1-112">The service implements an `ICalculator` contract defined as shown in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="842e1-113">Örnek, bilinen adı kullanmanın üç farklı yaklaşımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="842e1-113">The sample demonstrates the three alternative approaches for using the moniker:</span></span>  
  
- <span data-ttu-id="842e1-114">Yazılı sözleşme – sözleşme, istemci bilgisayarda COM görünebilir bir tür olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="842e1-114">Typed contract – The contract is registered as a COM visible type on the client computer.</span></span>  
  
- <span data-ttu-id="842e1-115">WSDL sözleşmesi – sözleşme, WSDL belgesi biçiminde sağlanır.</span><span class="sxs-lookup"><span data-stu-id="842e1-115">WSDL contract – The contract is supplied in the form of a WSDL document.</span></span>  
  
- <span data-ttu-id="842e1-116">Meta veri değişimi sözleşmesi – sözleşme, meta veri değişimi (MEX) uç noktasından çalışma zamanında alınır.</span><span class="sxs-lookup"><span data-stu-id="842e1-116">Metadata Exchange contract – The contract is retrieved at runtime from a Metadata Exchange (MEX) endpoint.</span></span>  
  
## <a name="typed-contract"></a><span data-ttu-id="842e1-117">Yazılı sözleşme</span><span class="sxs-lookup"><span data-stu-id="842e1-117">Typed Contract</span></span>  
 <span data-ttu-id="842e1-118">Bilinen bir sözleşme kullanımıyla bilinen adı kullanmak için, hizmet sözleşmesi için uygun şekilde öznitelikli türler COM ile kaydedilmelidir.</span><span class="sxs-lookup"><span data-stu-id="842e1-118">To use the moniker with a typed contract use, appropriately attributed types for the service contract must be registered with COM.</span></span> <span data-ttu-id="842e1-119">İlk olarak, bir istemcinin [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)kullanılarak oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="842e1-119">First, a client must be generated by using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="842e1-120">Yazılan proxy 'yi oluşturmak için istemci dizinindeki bir komut isteminden aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="842e1-120">Run the following command from a command prompt in the client directory to generate the typed proxy.</span></span>  
  
```console  
svcutil.exe /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost/servicemodelsamples/service.svc /out:generatedClient.cs  
```  
  
 <span data-ttu-id="842e1-121">Bu sınıf bir projeye dahil edilmelidir ve derlendikten sonra proje, COM görünebilir ve imzalı bir derleme oluşturacak şekilde yapılandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="842e1-121">This class must be included in a project and the project should be configured to generate a COM-visible, signed assembly when compiled.</span></span> <span data-ttu-id="842e1-122">Aşağıdaki öznitelik AssemblyInfo.cs dosyasına eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="842e1-122">The following attribute should be included in the AssemblyInfo.cs file.</span></span>  
  
```csharp
[assembly: ComVisible(true)]  
```  
  
 <span data-ttu-id="842e1-123">Projeyi oluşturduktan sonra, aşağıdaki örnekte gösterildiği gibi `regasm` kullanarak COM görünebilir türleri kaydedin.</span><span class="sxs-lookup"><span data-stu-id="842e1-123">After building the project, register the COM-visible types by using `regasm` as shown in the following example.</span></span>  
  
```console  
regasm.exe /tlb:CalcProxy.tlb client.dll  
```  
  
 <span data-ttu-id="842e1-124">Oluşturulan bütünleştirilmiş kod, genel derleme önbelleğine eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="842e1-124">The assembly that is created should be added to the Global Assembly Cache.</span></span> <span data-ttu-id="842e1-125">Kesinlikle gerekli olmasa da, derlemeyi bulma çalışma zamanının sürecini basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="842e1-125">Though not strictly required, this simplifies the process of the runtime locating the assembly.</span></span> <span data-ttu-id="842e1-126">Aşağıdaki komut, derlemeyi genel derleme önbelleğine ekler.</span><span class="sxs-lookup"><span data-stu-id="842e1-126">The following command adds the assembly to the Global Assembly Cache.</span></span>  
  
```console  
gacutil.exe /i client.dll  
```  
  
> [!NOTE]
> <span data-ttu-id="842e1-127">Hizmet bilinen adı yalnızca tür kaydı gerektirir ve hizmetle iletişim kurmak için proxy kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="842e1-127">The service moniker requires only the type registration and does not use the proxy to communicate with the service.</span></span>  
  
 <span data-ttu-id="842e1-128">ComCalcClient. vbs istemci uygulaması, hizmet için bir proxy oluşturmak üzere `GetObject` işlevini kullanır ve hizmetin adresini, bağlamayı ve sözleşmesini belirtmek için hizmet bilinen kullanım sözdizimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="842e1-128">ComCalcClient.vbs client application uses the `GetObject` function to construct a proxy for the service, using the service moniker syntax to specify the address, binding, and contract for the service.</span></span>  
  
```vbscript
Set typedServiceMoniker = GetObject(  
"service4:address=http://localhost/ServiceModelSamples/service.svc, binding=wsHttpBinding,   
contractType={9213C6D2-5A6F-3D26-839B-3BA9B82228D3}")  
```  
  
 <span data-ttu-id="842e1-129">Bilinen ad tarafından kullanılan parametreler şunları belirtir:</span><span class="sxs-lookup"><span data-stu-id="842e1-129">The parameters used by the moniker specify:</span></span>  
  
- <span data-ttu-id="842e1-130">Hizmet uç noktasının adresi.</span><span class="sxs-lookup"><span data-stu-id="842e1-130">The address of the service endpoint.</span></span>  
  
- <span data-ttu-id="842e1-131">İstemcinin bu uç noktayla bağlanmak için kullanması gereken bağlama.</span><span class="sxs-lookup"><span data-stu-id="842e1-131">The binding that the client should use to connect with that endpoint.</span></span> <span data-ttu-id="842e1-132">Bu durumda, sistem tarafından tanımlanan wsHttpBinding, istemci yapılandırma dosyalarında özel bağlamalar tanımlanbilse de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="842e1-132">In this case, the system-defined wsHttpBinding is used though custom bindings can be defined in client configuration files.</span></span> <span data-ttu-id="842e1-133">Windows komut dosyası ana bilgisayarı ile kullanmak için özel bağlama, cscript. exe ile aynı dizindeki bir cscript. exe. config dosyasında tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="842e1-133">For use with the Windows Script Host, the custom binding is defined in a Cscript.exe.config file in the same directory as Cscript.exe.</span></span>  
  
- <span data-ttu-id="842e1-134">Uç noktada desteklenen sözleşmenin türü.</span><span class="sxs-lookup"><span data-stu-id="842e1-134">The type of the contract that is supported at the endpoint.</span></span> <span data-ttu-id="842e1-135">Bu, yukarıda oluşturulup kaydedilen türdür.</span><span class="sxs-lookup"><span data-stu-id="842e1-135">This is the type that was generated and registered above.</span></span> <span data-ttu-id="842e1-136">Visual Basic betiği kesin türü belirtilmiş bir COM ortamı sağlamadığından, sözleşmeye yönelik bir tanımlayıcı belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="842e1-136">Because Visual Basic script does not provide a strongly-typed COM environment, an identifier for the contract must be specified.</span></span> <span data-ttu-id="842e1-137">Bu GUID, OLE/COM Nesne Görüntüleyicisi (OleView. exe) gibi COM araçları kullanılarak görüntülenebilen CalcProxy. tlb dosyasından `interfaceID`.</span><span class="sxs-lookup"><span data-stu-id="842e1-137">This GUID is the `interfaceID` from CalcProxy.tlb, which can be viewed by using COM tools such as the OLE/COM Object Viewer (OleView.exe).</span></span> <span data-ttu-id="842e1-138">Office VBA veya Visual Basic 6,0 gibi türü kesin belirlenmiş ortamlarda, tür kitaplığına açık bir başvuru eklemek ve ardından Proxy nesnesinin türünü bildirmek, sözleşme parametresinin yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="842e1-138">For strongly-typed environments such as Office VBA or Visual Basic 6.0, adding an explicit reference to the type library and then declaring the type of the proxy object can be used in place of the contract parameter.</span></span> <span data-ttu-id="842e1-139">Bu Ayrıca, istemci uygulama geliştirme sırasında IntelliSense desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="842e1-139">This also provides IntelliSense support during client application development.</span></span>  
  
 <span data-ttu-id="842e1-140">Proxy örneğinin hizmet bilinen adıyla oluşturulması, istemci uygulama proxy üzerinde Yöntemler çağırabilir ve bu da hizmet bilinen hizmet işlemlerini çağıran hizmet adı altyapısına neden olur.</span><span class="sxs-lookup"><span data-stu-id="842e1-140">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "Typed service moniker: 100 + 15.99 = " & typedServiceMoniker.Add(100, 15.99)  
```  
  
 Örneği çalıştırdığınızda, işlem yanıtı bir Windows komut dosyası ana ileti kutusu penceresinde görüntülenir. Bu, bir WCF hizmeti ile iletişim kurmak için yazılan bilinen adı kullanarak COM çağrıları yapan bir COM istemcisini gösterir. <span data-ttu-id="842e1-143">İstemci uygulamasında COM kullanımına rağmen hizmetle iletişim yalnızca Web hizmeti çağrılarından oluşur.</span><span class="sxs-lookup"><span data-stu-id="842e1-143">Despite the use of COM in the client application, the communication with the service consists only of Web service calls.</span></span>  
  
## <a name="wsdl-contract"></a><span data-ttu-id="842e1-144">WSDL sözleşmesi</span><span class="sxs-lookup"><span data-stu-id="842e1-144">WSDL Contract</span></span>  
 <span data-ttu-id="842e1-145">Bilinen adı bir WSDL sözleşmesiyle kullanmak için, hiçbir istemci kitaplığı kaydı gerekmez, ancak hizmet için WSDL sözleşmesinin, hizmet için WSDL uç noktasına erişmek üzere bir tarayıcı kullanma gibi bir bant dışı mekanizmadan alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="842e1-145">To use the moniker with a WSDL contract, no client library registration is required but the WSDL contract for the service must be retrieved through an out-of-band mechanism such as using a browser to access the WSDL endpoint for the service.</span></span> <span data-ttu-id="842e1-146">Bilinen ad daha sonra bu sözleşmeye yürütme zamanında erişebilir.</span><span class="sxs-lookup"><span data-stu-id="842e1-146">The moniker can then access that contract at execution time.</span></span>  
  
 <span data-ttu-id="842e1-147">ComCalcClient. vbs istemci uygulaması, yerel olarak kaydedilen WSDL dosyasına erişmek için `FileSystemObject` kullanır ve ardından hizmet için bir proxy oluşturmak üzere `GetObject` işlevini yeniden kullanır.</span><span class="sxs-lookup"><span data-stu-id="842e1-147">The ComCalcClient.vbs client application uses the `FileSystemObject` to access the locally saved WSDL file and then again uses the `GetObject` function to construct a proxy for the service.</span></span>  
  
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
  
 <span data-ttu-id="842e1-148">Bilinen ad tarafından kullanılan parametreler şunları belirtir:</span><span class="sxs-lookup"><span data-stu-id="842e1-148">The parameters used by the moniker specify:</span></span>  
  
- <span data-ttu-id="842e1-149">Hizmet uç noktasının adresi.</span><span class="sxs-lookup"><span data-stu-id="842e1-149">The address of the service endpoint.</span></span>  
  
- <span data-ttu-id="842e1-150">İstemcinin bu uç nokta ile bağlanmak için kullanması gereken bağlama ve bu bağlamanın tanımlandığı ad alanı.</span><span class="sxs-lookup"><span data-stu-id="842e1-150">The binding that the client should use to connect with that endpoint and the namespace in which that binding is defined.</span></span> <span data-ttu-id="842e1-151">Bu durumda `wsHttpBinding_ICalculator` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="842e1-151">In this case, the `wsHttpBinding_ICalculator` is used.</span></span>  
  
- <span data-ttu-id="842e1-152">Sözleşmeyi tanımlayan WSDL.</span><span class="sxs-lookup"><span data-stu-id="842e1-152">The WSDL that defines the contract.</span></span> <span data-ttu-id="842e1-153">Bu durumda, serviceWsdl. xml dosyasından okunan dizedir.</span><span class="sxs-lookup"><span data-stu-id="842e1-153">In this case this is the string that has been read from the serviceWsdl.xml file.</span></span>  
  
- <span data-ttu-id="842e1-154">Sözleşmenin adı ve ad alanı.</span><span class="sxs-lookup"><span data-stu-id="842e1-154">The name and namespace of the contract.</span></span> <span data-ttu-id="842e1-155">WSDL birden fazla sözleşme içerebileceğinden bu kimlik gereklidir.</span><span class="sxs-lookup"><span data-stu-id="842e1-155">This identification is required because the WSDL may contain more than one contract.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="842e1-156">Varsayılan olarak, WCF Hizmetleri, kullanılan her ad alanı için ayrı WSDL dosyaları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="842e1-156">By default, WCF services generate separate WSDL files for each namespace that the use.</span></span> <span data-ttu-id="842e1-157">Bunlar, WSDL içeri aktarma yapısının kullanımıyla bağlantılıdır.</span><span class="sxs-lookup"><span data-stu-id="842e1-157">These are linked with the use of the WSDL import construct.</span></span> <span data-ttu-id="842e1-158">Bilinen ad tek bir WSDL tanımı beklediği için, bu örnekte gösterildiği gibi hizmetin tek bir ad alanı kullanması gerekir ya da ayrı dosyalar el ile birleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="842e1-158">Because the moniker expects a single WSDL definition, the service must either use a single namespace as demonstrated in this sample or the separate files must be manually merged.</span></span>  
  
 <span data-ttu-id="842e1-159">Proxy örneğinin hizmet bilinen adıyla oluşturulması, istemci uygulama proxy üzerinde Yöntemler çağırabilir ve bu da hizmet bilinen hizmet işlemlerini çağıran hizmet adı altyapısına neden olur.</span><span class="sxs-lookup"><span data-stu-id="842e1-159">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
```  
  
 Örneği çalıştırdığınızda, işlem yanıtı bir Windows komut dosyası ana ileti kutusu penceresinde görüntülenir. <span data-ttu-id="842e1-161">Bu, bir WCF hizmeti ile iletişim kurmak için bir WSDL sözleşmesinin bilinen adını kullanarak COM çağrısı yapan bir COM istemcisini gösterir.</span><span class="sxs-lookup"><span data-stu-id="842e1-161">This demonstrates a COM client making COM calls using the moniker with a WSDL contract to communicate with a WCF service.</span></span>  
  
## <a name="metadata-exchange-contract"></a><span data-ttu-id="842e1-162">Meta veri değişimi sözleşmesi</span><span class="sxs-lookup"><span data-stu-id="842e1-162">Metadata Exchange Contract</span></span>  
 <span data-ttu-id="842e1-163">Bilinen adı, WSDL sözleşimiyle birlikte bir MEX sözleşmesiyle birlikte kullanmak için, istemci kaydı gerekmez.</span><span class="sxs-lookup"><span data-stu-id="842e1-163">To use the moniker with a MEX contract, as with the WSDL contract, no client registration is required.</span></span> <span data-ttu-id="842e1-164">Hizmetin sözleşmesi, meta veri değişim iç kullanımı üzerinden yürütme sırasında alınır.</span><span class="sxs-lookup"><span data-stu-id="842e1-164">The contract for the service is retrieved at execution time through the internal use of Metadata Exchange.</span></span>  
  
 <span data-ttu-id="842e1-165">ComCalcClient. vbs istemci uygulaması, hizmet için bir proxy oluşturmak üzere `GetObject` işlevini kullanır.</span><span class="sxs-lookup"><span data-stu-id="842e1-165">The ComCalcClient.vbs client application again uses the `GetObject` function to construct a proxy for the service.</span></span>  
  
```vbscript  
' Create a string for the service moniker specifying the address to retrieve the service metadata from  
mexMonikerString = "service4:mexAddress='http://localhost/servicemodelsamples/service.svc/mex'"  
mexMonikerString = mexMonikerString + ", address='http://localhost/ServiceModelSamples/service.svc'"  
mexMonikerString = mexMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
mexMonikerString = mexMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set mexServiceMoniker = GetObject(mexMonikerString)  
```  
  
 <span data-ttu-id="842e1-166">Bilinen ad tarafından kullanılan parametreler şunları belirtir:</span><span class="sxs-lookup"><span data-stu-id="842e1-166">The parameters used by the moniker specify:</span></span>  
  
- <span data-ttu-id="842e1-167">Hizmet meta veri değişimi uç noktasının adresi.</span><span class="sxs-lookup"><span data-stu-id="842e1-167">The address of the service metadata exchange endpoint.</span></span>  
  
- <span data-ttu-id="842e1-168">Hizmet uç noktasının adresi.</span><span class="sxs-lookup"><span data-stu-id="842e1-168">The address of the service endpoint.</span></span>  
  
- <span data-ttu-id="842e1-169">İstemcinin bu uç nokta ile bağlanmak için kullanması gereken bağlama ve bu bağlamanın tanımlandığı ad alanı.</span><span class="sxs-lookup"><span data-stu-id="842e1-169">The binding that the client should use to connect with that endpoint and the namespace in which that binding is defined.</span></span> <span data-ttu-id="842e1-170">Bu durumda `wsHttpBinding_ICalculator` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="842e1-170">In this case, the `wsHttpBinding_ICalculator` is used.</span></span>  
  
- <span data-ttu-id="842e1-171">Sözleşmenin adı ve ad alanı.</span><span class="sxs-lookup"><span data-stu-id="842e1-171">The name and namespace of the contract.</span></span> <span data-ttu-id="842e1-172">WSDL birden fazla sözleşme içerebileceğinden bu kimlik gereklidir.</span><span class="sxs-lookup"><span data-stu-id="842e1-172">This identification is required because the WSDL may contain more than one contract.</span></span>  
  
 <span data-ttu-id="842e1-173">Proxy örneğinin hizmet bilinen adıyla oluşturulması, istemci uygulama proxy üzerinde Yöntemler çağırabilir ve bu da hizmet bilinen hizmet işlemlerini çağıran hizmet adı altyapısına neden olur.</span><span class="sxs-lookup"><span data-stu-id="842e1-173">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "MEX service moniker: 9 * 81.25 = " & mexServiceMoniker.Multiply(9, 81.25)  
```  
  
 Örneği çalıştırdığınızda, işlem yanıtı bir Windows komut dosyası ana ileti kutusu penceresinde görüntülenir. <span data-ttu-id="842e1-175">Bu, bir WCF hizmeti ile iletişim kurmak için bir MEX sözleşmesiyle bilinen bilinen bilinen bilinen bir COM istemcisini gösterir.</span><span class="sxs-lookup"><span data-stu-id="842e1-175">This demonstrates a COM client making COM calls using the moniker with a MEX contract to communicate with a WCF service.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="842e1-176">Örneği ayarlamak ve derlemek için</span><span class="sxs-lookup"><span data-stu-id="842e1-176">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="842e1-177">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="842e1-177">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="842e1-178">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="842e1-178">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="842e1-179">Visual Studio için Geliştirici Komut İstemi, dile özgü klasör altında \client\bin klasörünü açın.</span><span class="sxs-lookup"><span data-stu-id="842e1-179">From a Developer Command Prompt for Visual Studio, open the \client\bin folder, under the language-specific folder.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="842e1-180">[!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], Windows 7 veya Windows Server 2008 R2 kullanıyorsanız, komut istemi 'ni yönetici ayrıcalıklarıyla çalıştırdığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="842e1-180">If you are using [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], Windows 7, or Windows Server 2008 R2, make sure that you run the command prompt with administrator privileges.</span></span>  
  
4. <span data-ttu-id="842e1-181">Dll 'yi bir TLB dosyasına aktarmak için `tlbexp.exe client.dll /out:CalcProxy.tlb` yazın.</span><span class="sxs-lookup"><span data-stu-id="842e1-181">Type in `tlbexp.exe client.dll /out:CalcProxy.tlb` to export the dll to a tlb file.</span></span> <span data-ttu-id="842e1-182">Bir "tür kitaplığı verme programı Uyarısı" beklenmektedir, ancak genel tür gerekli olmadığından bir sorun değil.</span><span class="sxs-lookup"><span data-stu-id="842e1-182">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
5. <span data-ttu-id="842e1-183">Türleri COM 'a kaydetmek için `regasm.exe /tlb:CalcProxy.tlb client.dll` yazın.</span><span class="sxs-lookup"><span data-stu-id="842e1-183">Type in `regasm.exe /tlb:CalcProxy.tlb client.dll` to register the types with COM.</span></span> <span data-ttu-id="842e1-184">Bir "tür kitaplığı verme programı Uyarısı" beklenmektedir, ancak genel tür gerekli olmadığından bir sorun değil.</span><span class="sxs-lookup"><span data-stu-id="842e1-184">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
6. <span data-ttu-id="842e1-185">Derlemeyi genel bütünleştirilmiş kod önbelleğine eklemek için `gacutil.exe /i client.dll` yazın.</span><span class="sxs-lookup"><span data-stu-id="842e1-185">Type in `gacutil.exe /i client.dll` to add the assembly to the Global Assembly Cache.</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="842e1-186">Örneği aynı bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="842e1-186">To run the sample on the same computer</span></span>  
  
1. <span data-ttu-id="842e1-187">Aşağıdaki adresi yazarak hizmete bir tarayıcı kullanarak erişebiliyor musunuz: `http://localhost/servicemodelsamples/service.svc`.</span><span class="sxs-lookup"><span data-stu-id="842e1-187">Test that you can access the service using a browser by typing in the following address: `http://localhost/servicemodelsamples/service.svc`.</span></span> <span data-ttu-id="842e1-188">Yanıt olarak bir onay sayfası görüntülenmelidir.</span><span class="sxs-lookup"><span data-stu-id="842e1-188">A confirmation page should be displayed in response.</span></span>  
  
2. <span data-ttu-id="842e1-189">Dile özgü klasörün altındaki \Client öğesinden ComCalcClient. vbs ' yi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="842e1-189">Run ComCalcClient.vbs from \client, from under the language-specific folder.</span></span> <span data-ttu-id="842e1-190">İstemci etkinliği ileti kutusu pencereleri ' nde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="842e1-190">Client activity is displayed in message box windows.</span></span>  
  
3. <span data-ttu-id="842e1-191">İstemci ve hizmet iletişim kuramadıysanız, bkz. [WCF örnekleri Için sorun giderme ipuçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="842e1-191">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="842e1-192">Örneği bilgisayarlar arasında çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="842e1-192">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="842e1-193">Hizmet bilgisayarında, ServiceModelSamples adlı bir sanal dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="842e1-193">On the service computer, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="842e1-194">Örneğe eklenen Setupvroot. bat betiği disk dizinini ve sanal dizini oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="842e1-194">The Setupvroot.bat script included with the sample can be used to create the disk directory and virtual directory.</span></span>  
  
2. <span data-ttu-id="842e1-195">Hizmet programı dosyalarını%SystemDrive%\Inetpub\wwwroot\servicemodelsamples adresinden hizmet bilgisayarında ServiceModelSamples sanal dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="842e1-195">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service computer.</span></span> <span data-ttu-id="842e1-196">Dosyaları \Bin dizinine dahil ettiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="842e1-196">Be sure to include the files in the \bin directory.</span></span>  
  
3. <span data-ttu-id="842e1-197">İstemci komut dosyasını dile özgü klasör altındaki \İstemci klasöründen istemci bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="842e1-197">Copy the client script file from the \client folder, under the language-specific folder, to the client computer.</span></span>  
  
4. <span data-ttu-id="842e1-198">Betik dosyasında, uç nokta tanımının adres değerini hizmetinizin yeni adresiyle eşleşecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="842e1-198">In the script file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="842e1-199">"Localhost" başvurularını, adreste tam etki alanı adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="842e1-199">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
5. <span data-ttu-id="842e1-200">WSDL dosyasını istemci bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="842e1-200">Copy the WSDL file to the client computer.</span></span> <span data-ttu-id="842e1-201">ServiceWsdl. xml WSDL dosyasında, "localhost" ile ilgili tüm başvuruları adresteki tam etki alanı adıyla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="842e1-201">In the WSDL file, serviceWsdl.xml, replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
6. <span data-ttu-id="842e1-202">Client. dll kitaplığını dile özgü klasörün altındaki \client\bin klasöründen istemci bilgisayardaki bir dizine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="842e1-202">Copy the Client.dll library from the \client\bin folder, under the language-specific folder, to a directory on the client computer.</span></span>  
  
7. <span data-ttu-id="842e1-203">Bir komut isteminden, istemci bilgisayardaki bu hedef dizine gidin.</span><span class="sxs-lookup"><span data-stu-id="842e1-203">From a command prompt, navigate to that destination directory on the client computer.</span></span> <span data-ttu-id="842e1-204">[!INCLUDE[wv](../../../../includes/wv-md.md)] veya [!INCLUDE[lserver](../../../../includes/lserver-md.md)]kullanıyorsanız, komut istemi ' ni yönetici olarak çalıştırdığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="842e1-204">If using [!INCLUDE[wv](../../../../includes/wv-md.md)] or [!INCLUDE[lserver](../../../../includes/lserver-md.md)], make sure to run the command prompt as Administrator.</span></span>  
  
8. <span data-ttu-id="842e1-205">Dll 'yi bir TLB dosyasına aktarmak için `tlbexp.exe client.dll /out:CalcProxy.tlb` yazın.</span><span class="sxs-lookup"><span data-stu-id="842e1-205">Type in `tlbexp.exe client.dll /out:CalcProxy.tlb` to export the dll to a tlb file.</span></span> <span data-ttu-id="842e1-206">Bir "tür kitaplığı verme programı Uyarısı" beklenmektedir, ancak genel tür gerekli olmadığından bir sorun değil.</span><span class="sxs-lookup"><span data-stu-id="842e1-206">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
9. <span data-ttu-id="842e1-207">Türleri COM 'a kaydetmek için `regasm.exe /tlb:CalcProxy.tlb client.dll` yazın.</span><span class="sxs-lookup"><span data-stu-id="842e1-207">Type in `regasm.exe /tlb:CalcProxy.tlb client.dll` to register the types with COM.</span></span> <span data-ttu-id="842e1-208">Komutu çalıştırmadan önce yolun `regasm.exe` içeren klasöre ayarlandığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="842e1-208">Ensure that path has been set to the folder that contains `regasm.exe` before you run the command.</span></span>  
  
10. <span data-ttu-id="842e1-209">Derlemeyi genel bütünleştirilmiş kod önbelleğine eklemek için `gacutil.exe /i client.dll` yazın.</span><span class="sxs-lookup"><span data-stu-id="842e1-209">Type in `gacutil.exe /i client.dll` to add the assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="842e1-210">Komutu çalıştırmadan önce yolun `gacutil.exe` içeren klasöre ayarlandığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="842e1-210">Ensure that path has been set to the folder that contains `gacutil.exe` before you run the command.</span></span>  
  
11. <span data-ttu-id="842e1-211">Bir tarayıcı kullanarak hizmete istemci bilgisayardan erişebilmeniz için test edin.</span><span class="sxs-lookup"><span data-stu-id="842e1-211">Test that you can access the service from the client computer using a browser.</span></span>  
  
12. <span data-ttu-id="842e1-212">İstemci bilgisayarda ComCalcClient. vbs ' yi başlatın.</span><span class="sxs-lookup"><span data-stu-id="842e1-212">On the client computer, launch ComCalcClient.vbs.</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="842e1-213">Örnekten sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="842e1-213">To clean up after the sample</span></span>  
  
- <span data-ttu-id="842e1-214">Güvenlik nedenleriyle, örnekleri ile işiniz bittiğinde kurulum adımlarında verilen sanal dizin tanımını ve izinleri kaldırın.</span><span class="sxs-lookup"><span data-stu-id="842e1-214">For security purposes, remove the virtual directory definition and permissions granted in the setup steps when you are finished with the samples.</span></span>  
