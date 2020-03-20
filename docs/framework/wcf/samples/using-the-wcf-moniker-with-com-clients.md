---
title: WCF Bilinen Adını COM İstemcileri ile Kullanma
ms.date: 03/30/2017
ms.assetid: e2799bfe-88bd-49d7-9d6d-ac16a9b16b04
ms.openlocfilehash: d4d812c59a504f365eb3ad63ddd45ba5a66296e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183229"
---
# <a name="using-the-wcf-moniker-with-com-clients"></a><span data-ttu-id="d06f0-102">WCF Bilinen Adını COM İstemcileri ile Kullanma</span><span class="sxs-lookup"><span data-stu-id="d06f0-102">Using the WCF Moniker with COM Clients</span></span>
<span data-ttu-id="d06f0-103">Bu örnek, Windows Communication Foundation (WCF) hizmet lakabının, Web hizmetlerini Microsoft Office Visual Basic for Applications (Office VBA) veya Visual Basic 6.0 gibi COM tabanlı geliştirme ortamlarına entegre etmek için nasıl kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="d06f0-103">This sample demonstrates how to use the Windows Communication Foundation (WCF) service moniker to integrate Web services into COM-based development environments, such as Microsoft Office Visual Basic for Applications (Office VBA) or Visual Basic 6.0.</span></span> <span data-ttu-id="d06f0-104">Bu örnek, Bir Windows Script Host istemcisi (.vbs), destekleyen istemci kitaplığı (.dll) ve Internet Information Services (IIS) tarafından barındırılan bir hizmet kitaplığından (.dll) oluşur.</span><span class="sxs-lookup"><span data-stu-id="d06f0-104">This sample consists of a Windows Script Host client (.vbs), a supporting client library (.dll), and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="d06f0-105">Hizmet bir hesap makinesi hizmetidir ve COM istemcisi hizmette matematik işlemlerini çağırır-Ekle, Çıkar, Çarpve Böl- çağırır.</span><span class="sxs-lookup"><span data-stu-id="d06f0-105">The service is a calculator service and the COM client calls math operations—Add, Subtract, Multiply, and Divide—on the service.</span></span> <span data-ttu-id="d06f0-106">İstemci etkinliği ileti kutusu pencerelerinde görünür.</span><span class="sxs-lookup"><span data-stu-id="d06f0-106">Client activity is visible in the message box windows.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d06f0-107">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="d06f0-107">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d06f0-108">Örnekler bilgisayarınıza zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="d06f0-108">The samples may already be installed on your computer.</span></span> <span data-ttu-id="d06f0-109">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d06f0-109">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="d06f0-110">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="d06f0-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d06f0-111">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="d06f0-111">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\COM`  
  
 <span data-ttu-id="d06f0-112">Hizmet, aşağıdaki `ICalculator` kod örneğinde gösterildiği gibi tanımlanan bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="d06f0-112">The service implements an `ICalculator` contract defined as shown in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="d06f0-113">Örnek, lakabı kullanmak için üç alternatif yaklaşımı göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="d06f0-113">The sample demonstrates the three alternative approaches for using the moniker:</span></span>  
  
- <span data-ttu-id="d06f0-114">Dakti-iş sözleşmesi – Sözleşme istemci bilgisayarda COM görünür türü olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="d06f0-114">Typed contract – The contract is registered as a COM visible type on the client computer.</span></span>  
  
- <span data-ttu-id="d06f0-115">WSDL sözleşmesi – Sözleşme bir WSDL belgesi şeklinde sağlanır.</span><span class="sxs-lookup"><span data-stu-id="d06f0-115">WSDL contract – The contract is supplied in the form of a WSDL document.</span></span>  
  
- <span data-ttu-id="d06f0-116">Meta veri değişimi sözleşmesi – Sözleşme çalışma zamanında Meta veri değişimi (MEX) bitiş noktasından alınır.</span><span class="sxs-lookup"><span data-stu-id="d06f0-116">Metadata Exchange contract – The contract is retrieved at runtime from a Metadata Exchange (MEX) endpoint.</span></span>  
  
## <a name="typed-contract"></a><span data-ttu-id="d06f0-117">Yazılı Sözleşme</span><span class="sxs-lookup"><span data-stu-id="d06f0-117">Typed Contract</span></span>  
 <span data-ttu-id="d06f0-118">Lakabı yazılı sözleşme kullanımıyla kullanmak için, hizmet sözleşmesi için uygun şekilde atfedilen türlerin COM'a kaydedilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="d06f0-118">To use the moniker with a typed contract use, appropriately attributed types for the service contract must be registered with COM.</span></span> <span data-ttu-id="d06f0-119">İlk olarak, bir istemci [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)kullanılarak oluşturulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d06f0-119">First, a client must be generated by using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="d06f0-120">Yazılan proxy'yi oluşturmak için istemci dizinindeki bir komut isteminden aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d06f0-120">Run the following command from a command prompt in the client directory to generate the typed proxy.</span></span>  
  
```console  
svcutil.exe /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost/servicemodelsamples/service.svc /out:generatedClient.cs  
```  
  
 <span data-ttu-id="d06f0-121">Bu sınıf bir projeye dahil edilmeli ve proje derlendiğinde COM görünür, imzalı bir derleme oluşturacak şekilde yapılandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d06f0-121">This class must be included in a project and the project should be configured to generate a COM-visible, signed assembly when compiled.</span></span> <span data-ttu-id="d06f0-122">Aşağıdaki öznitelik AssemblyInfo.cs dosyasına eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="d06f0-122">The following attribute should be included in the AssemblyInfo.cs file.</span></span>  
  
```csharp
[assembly: ComVisible(true)]  
```  
  
 <span data-ttu-id="d06f0-123">Projeyi yaptıktan sonra, aşağıdaki örnekte `regasm` gösterildiği gibi kullanarak COM-görünür türlerini kaydedin.</span><span class="sxs-lookup"><span data-stu-id="d06f0-123">After building the project, register the COM-visible types by using `regasm` as shown in the following example.</span></span>  
  
```console  
regasm.exe /tlb:CalcProxy.tlb client.dll  
```  
  
 <span data-ttu-id="d06f0-124">Oluşturulan derleme, Genel Montaj Önbelleğine eklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="d06f0-124">The assembly that is created should be added to the Global Assembly Cache.</span></span> <span data-ttu-id="d06f0-125">Kesinlikle gerekli olmasa da, bu, derlemeyi bulma çalışma zamanı işlemini kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="d06f0-125">Though not strictly required, this simplifies the process of the runtime locating the assembly.</span></span> <span data-ttu-id="d06f0-126">Aşağıdaki komut, derlemeyi Genel Montaj Önbelleğine ekler.</span><span class="sxs-lookup"><span data-stu-id="d06f0-126">The following command adds the assembly to the Global Assembly Cache.</span></span>  
  
```console  
gacutil.exe /i client.dll  
```  
  
> [!NOTE]
> <span data-ttu-id="d06f0-127">Hizmet lakabı yalnızca tür kaydı gerektirir ve hizmetle iletişim kurmak için proxy'yi kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="d06f0-127">The service moniker requires only the type registration and does not use the proxy to communicate with the service.</span></span>  
  
 <span data-ttu-id="d06f0-128">ComCalcClient.vbs istemci uygulaması, hizmetin adresini, bağlamasını ve sözleşmesini belirtmek için hizmet ad sözdizimini kullanarak hizmet için bir proxy oluşturmak için `GetObject` işlevi kullanır.</span><span class="sxs-lookup"><span data-stu-id="d06f0-128">ComCalcClient.vbs client application uses the `GetObject` function to construct a proxy for the service, using the service moniker syntax to specify the address, binding, and contract for the service.</span></span>  
  
```vbscript
Set typedServiceMoniker = GetObject(  
"service4:address=http://localhost/ServiceModelSamples/service.svc, binding=wsHttpBinding,
contractType={9213C6D2-5A6F-3D26-839B-3BA9B82228D3}")  
```  
  
 <span data-ttu-id="d06f0-129">Takma alakadar kullanılan parametreler şunları belirtir:</span><span class="sxs-lookup"><span data-stu-id="d06f0-129">The parameters used by the moniker specify:</span></span>  
  
- <span data-ttu-id="d06f0-130">Hizmet bitiş noktasının adresi.</span><span class="sxs-lookup"><span data-stu-id="d06f0-130">The address of the service endpoint.</span></span>  
  
- <span data-ttu-id="d06f0-131">İstemcinin bu uç noktaya bağlanmak için kullanması gereken bağlama.</span><span class="sxs-lookup"><span data-stu-id="d06f0-131">The binding that the client should use to connect with that endpoint.</span></span> <span data-ttu-id="d06f0-132">Bu durumda, sistem tanımlı wsHttpBinding istemci yapılandırma dosyalarında özel bağlamalar tanımlanabilir rağmen kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d06f0-132">In this case, the system-defined wsHttpBinding is used though custom bindings can be defined in client configuration files.</span></span> <span data-ttu-id="d06f0-133">Windows Script Ana Bilgisayarı'nda kullanım için özel bağlama, Cscript.exe ile aynı dizinde bir Cscript.exe.config dosyasında tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="d06f0-133">For use with the Windows Script Host, the custom binding is defined in a Cscript.exe.config file in the same directory as Cscript.exe.</span></span>  
  
- <span data-ttu-id="d06f0-134">Bitiş noktasında desteklenen sözleşmenin türü.</span><span class="sxs-lookup"><span data-stu-id="d06f0-134">The type of the contract that is supported at the endpoint.</span></span> <span data-ttu-id="d06f0-135">Bu, yukarıda oluşturulan ve kaydedilmiş türdür.</span><span class="sxs-lookup"><span data-stu-id="d06f0-135">This is the type that was generated and registered above.</span></span> <span data-ttu-id="d06f0-136">Visual Basic komut dosyası güçlü bir şekilde yazılmış bir COM ortamı sağlamadığından, sözleşme için bir tanımlayıcı belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="d06f0-136">Because Visual Basic script does not provide a strongly-typed COM environment, an identifier for the contract must be specified.</span></span> <span data-ttu-id="d06f0-137">Bu GUID `interfaceID` CalcProxy.tlb, OLE / COM Nesne Görüntüleyici (OleView.exe) gibi COM araçları kullanılarak görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="d06f0-137">This GUID is the `interfaceID` from CalcProxy.tlb, which can be viewed by using COM tools such as the OLE/COM Object Viewer (OleView.exe).</span></span> <span data-ttu-id="d06f0-138">Office VBA veya Visual Basic 6.0 gibi güçlü bir şekilde yazılan ortamlar için, tür kitaplığına açık bir başvuru eklemek ve ardından proxy nesnesinin türünü bildiren sözleşme parametresi yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d06f0-138">For strongly-typed environments such as Office VBA or Visual Basic 6.0, adding an explicit reference to the type library and then declaring the type of the proxy object can be used in place of the contract parameter.</span></span> <span data-ttu-id="d06f0-139">Bu da istemci uygulama geliştirme sırasında IntelliSense desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="d06f0-139">This also provides IntelliSense support during client application development.</span></span>  
  
 <span data-ttu-id="d06f0-140">Hizmet lakabını içeren proxy örneğini oluşturan istemci uygulaması, proxy'deki yöntemleri arayabilir ve bu da servis takma altyapısının ilgili hizmet işlemlerini çağırmasıyla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="d06f0-140">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "Typed service moniker: 100 + 15.99 = " & typedServiceMoniker.Add(100, 15.99)  
```  
  
 Örneği çalıştırdığınızda, işlem yanıtı bir Windows Script Ana Bilgisayar ileti kutusu penceresinde görüntülenir. Bu, bir WCF hizmetiyle iletişim kurmak için yazılan takma ad kullanarak COM çağrıları yapan bir COM istemcisini gösterir. <span data-ttu-id="d06f0-143">Müşteri uygulamasında COM kullanımına rağmen, hizmetle iletişim yalnızca Web servis çağrılarından oluşur.</span><span class="sxs-lookup"><span data-stu-id="d06f0-143">Despite the use of COM in the client application, the communication with the service consists only of Web service calls.</span></span>  
  
## <a name="wsdl-contract"></a><span data-ttu-id="d06f0-144">WSDL Sözleşmesi</span><span class="sxs-lookup"><span data-stu-id="d06f0-144">WSDL Contract</span></span>  
 <span data-ttu-id="d06f0-145">WsDL sözleşmesi yle takma adı kullanmak için istemci kitaplığı kaydı gerekmez, ancak hizmet için WSDL sözleşmesi, hizmet için WSDL bitiş noktasına erişmek için bir tarayıcı kullanmak gibi bant dışı bir mekanizma aracılığıyla alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d06f0-145">To use the moniker with a WSDL contract, no client library registration is required but the WSDL contract for the service must be retrieved through an out-of-band mechanism such as using a browser to access the WSDL endpoint for the service.</span></span> <span data-ttu-id="d06f0-146">Takma adı daha sonra yürütme sırasında bu sözleşmeerişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d06f0-146">The moniker can then access that contract at execution time.</span></span>  
  
 <span data-ttu-id="d06f0-147">ComCalcClient.vbs istemci uygulaması `FileSystemObject` yerel olarak kaydedilen WSDL dosyasına erişmek `GetObject` için kullanır ve sonra tekrar hizmet için bir proxy oluşturmak için işlevi kullanır.</span><span class="sxs-lookup"><span data-stu-id="d06f0-147">The ComCalcClient.vbs client application uses the `FileSystemObject` to access the locally saved WSDL file and then again uses the `GetObject` function to construct a proxy for the service.</span></span>  
  
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
  
 <span data-ttu-id="d06f0-148">Takma alakadar kullanılan parametreler şunları belirtir:</span><span class="sxs-lookup"><span data-stu-id="d06f0-148">The parameters used by the moniker specify:</span></span>  
  
- <span data-ttu-id="d06f0-149">Hizmet bitiş noktasının adresi.</span><span class="sxs-lookup"><span data-stu-id="d06f0-149">The address of the service endpoint.</span></span>  
  
- <span data-ttu-id="d06f0-150">İstemcinin bu uç noktayla bağlantı kurmak için kullanması gereken bağlama ve bu bağlamanın tanımlandığı ad alanı.</span><span class="sxs-lookup"><span data-stu-id="d06f0-150">The binding that the client should use to connect with that endpoint and the namespace in which that binding is defined.</span></span> <span data-ttu-id="d06f0-151">Bu durumda, `wsHttpBinding_ICalculator` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d06f0-151">In this case, the `wsHttpBinding_ICalculator` is used.</span></span>  
  
- <span data-ttu-id="d06f0-152">Sözleşmeyi tanımlayan WSDL.</span><span class="sxs-lookup"><span data-stu-id="d06f0-152">The WSDL that defines the contract.</span></span> <span data-ttu-id="d06f0-153">Bu durumda serviceWsdl.xml dosyasından okunan dizedir.</span><span class="sxs-lookup"><span data-stu-id="d06f0-153">In this case this is the string that has been read from the serviceWsdl.xml file.</span></span>  
  
- <span data-ttu-id="d06f0-154">Sözleşmenin adı ve ad alanı.</span><span class="sxs-lookup"><span data-stu-id="d06f0-154">The name and namespace of the contract.</span></span> <span data-ttu-id="d06f0-155">WSDL birden fazla sözleşme içerebileceğinden bu tanımlama gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d06f0-155">This identification is required because the WSDL may contain more than one contract.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="d06f0-156">Varsayılan olarak, WCF hizmetleri, kullanıldığı her ad alanı için ayrı WSDL dosyaları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d06f0-156">By default, WCF services generate separate WSDL files for each namespace that the use.</span></span> <span data-ttu-id="d06f0-157">Bunlar WSDL alma yapısının kullanımıyla bağlantılıdır.</span><span class="sxs-lookup"><span data-stu-id="d06f0-157">These are linked with the use of the WSDL import construct.</span></span> <span data-ttu-id="d06f0-158">Takma ad tek bir WSDL tanımı beklediğinden, hizmetin bu örnekte gösterildiği gibi tek bir ad alanı kullanması veya ayrı dosyaların el ile birleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="d06f0-158">Because the moniker expects a single WSDL definition, the service must either use a single namespace as demonstrated in this sample or the separate files must be manually merged.</span></span>  
  
 <span data-ttu-id="d06f0-159">Hizmet lakabını içeren proxy örneğini oluşturan istemci uygulaması, proxy'deki yöntemleri arayabilir ve bu da servis takma altyapısının ilgili hizmet işlemlerini çağırmasıyla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="d06f0-159">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
```  
  
 Örneği çalıştırdığınızda, işlem yanıtı bir Windows Script Ana Bilgisayar ileti kutusu penceresinde görüntülenir. <span data-ttu-id="d06f0-161">Bu, bir WCF hizmetiyle iletişim kurmak için WSDL sözleşmesi olan takma ad kullanan com istemcisinin COM aramaları yaptığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d06f0-161">This demonstrates a COM client making COM calls using the moniker with a WSDL contract to communicate with a WCF service.</span></span>  
  
## <a name="metadata-exchange-contract"></a><span data-ttu-id="d06f0-162">Meta veri değişim sözleşmesi</span><span class="sxs-lookup"><span data-stu-id="d06f0-162">Metadata Exchange Contract</span></span>  
 <span data-ttu-id="d06f0-163">WSDL sözleşmesinde olduğu gibi, bir MEX sözleşmesi ile takma takma kullanmak için, hiçbir istemci kaydı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d06f0-163">To use the moniker with a MEX contract, as with the WSDL contract, no client registration is required.</span></span> <span data-ttu-id="d06f0-164">Hizmet sözleşmesi, Meta veri exchange'in dahili kullanımı yoluyla yürütme sırasında alınır.</span><span class="sxs-lookup"><span data-stu-id="d06f0-164">The contract for the service is retrieved at execution time through the internal use of Metadata Exchange.</span></span>  
  
 <span data-ttu-id="d06f0-165">ComCalcClient.vbs istemci uygulaması yine `GetObject` hizmet için bir proxy oluşturmak için işlevi kullanır.</span><span class="sxs-lookup"><span data-stu-id="d06f0-165">The ComCalcClient.vbs client application again uses the `GetObject` function to construct a proxy for the service.</span></span>  
  
```vbscript  
' Create a string for the service moniker specifying the address to retrieve the service metadata from  
mexMonikerString = "service4:mexAddress='http://localhost/servicemodelsamples/service.svc/mex'"  
mexMonikerString = mexMonikerString + ", address='http://localhost/ServiceModelSamples/service.svc'"  
mexMonikerString = mexMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
mexMonikerString = mexMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set mexServiceMoniker = GetObject(mexMonikerString)  
```  
  
 <span data-ttu-id="d06f0-166">Takma alakadar kullanılan parametreler şunları belirtir:</span><span class="sxs-lookup"><span data-stu-id="d06f0-166">The parameters used by the moniker specify:</span></span>  
  
- <span data-ttu-id="d06f0-167">Hizmet meta veri alışverişi bitiş noktasının adresi.</span><span class="sxs-lookup"><span data-stu-id="d06f0-167">The address of the service metadata exchange endpoint.</span></span>  
  
- <span data-ttu-id="d06f0-168">Hizmet bitiş noktasının adresi.</span><span class="sxs-lookup"><span data-stu-id="d06f0-168">The address of the service endpoint.</span></span>  
  
- <span data-ttu-id="d06f0-169">İstemcinin bu uç noktayla bağlantı kurmak için kullanması gereken bağlama ve bu bağlamanın tanımlandığı ad alanı.</span><span class="sxs-lookup"><span data-stu-id="d06f0-169">The binding that the client should use to connect with that endpoint and the namespace in which that binding is defined.</span></span> <span data-ttu-id="d06f0-170">Bu durumda, `wsHttpBinding_ICalculator` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d06f0-170">In this case, the `wsHttpBinding_ICalculator` is used.</span></span>  
  
- <span data-ttu-id="d06f0-171">Sözleşmenin adı ve ad alanı.</span><span class="sxs-lookup"><span data-stu-id="d06f0-171">The name and namespace of the contract.</span></span> <span data-ttu-id="d06f0-172">WSDL birden fazla sözleşme içerebileceğinden bu tanımlama gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d06f0-172">This identification is required because the WSDL may contain more than one contract.</span></span>  
  
 <span data-ttu-id="d06f0-173">Hizmet lakabını içeren proxy örneğini oluşturan istemci uygulaması, proxy'deki yöntemleri arayabilir ve bu da servis takma altyapısının ilgili hizmet işlemlerini çağırmasıyla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="d06f0-173">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "MEX service moniker: 9 * 81.25 = " & mexServiceMoniker.Multiply(9, 81.25)  
```  
  
 Örneği çalıştırdığınızda, işlem yanıtı bir Windows Script Ana Bilgisayar ileti kutusu penceresinde görüntülenir. <span data-ttu-id="d06f0-175">Bu, bir COM istemcisinin bir WCF hizmetiyle iletişim kurmak için bir MEX sözleşmesi olan takma ad kullanarak COM aramaları yaptığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d06f0-175">This demonstrates a COM client making COM calls using the moniker with a MEX contract to communicate with a WCF service.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="d06f0-176">Örneği ayarlamak ve oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d06f0-176">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="d06f0-177">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="d06f0-177">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="d06f0-178">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="d06f0-178">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="d06f0-179">Visual Studio için Geliştirici Komut Komut Ustem'den, dile özgü klasörün altında \client\bin klasörünü açın.</span><span class="sxs-lookup"><span data-stu-id="d06f0-179">From a Developer Command Prompt for Visual Studio, open the \client\bin folder, under the language-specific folder.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="d06f0-180">Windows Vista, Windows Server 2008, Windows 7 veya Windows Server 2008 R2 kullanıyorsanız, komut istemini yönetici ayrıcalıklarıyla çalıştırdığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="d06f0-180">If you are using Windows Vista, Windows Server 2008, Windows 7, or Windows Server 2008 R2, make sure that you run the command prompt with administrator privileges.</span></span>  
  
4. <span data-ttu-id="d06f0-181">tlb `tlbexp.exe client.dll /out:CalcProxy.tlb` dosyasına dll'yi dışa aktarmak için yazın.</span><span class="sxs-lookup"><span data-stu-id="d06f0-181">Type in `tlbexp.exe client.dll /out:CalcProxy.tlb` to export the dll to a tlb file.</span></span> <span data-ttu-id="d06f0-182">Genel tür gerekli olmadığından bir "Tür kitaplığı ihracatçısı uyarısı" beklenir, ancak bir sorun değildir.</span><span class="sxs-lookup"><span data-stu-id="d06f0-182">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
5. <span data-ttu-id="d06f0-183">Türleri `regasm.exe /tlb:CalcProxy.tlb client.dll` COM'a kaydetmek için yazın.</span><span class="sxs-lookup"><span data-stu-id="d06f0-183">Type in `regasm.exe /tlb:CalcProxy.tlb client.dll` to register the types with COM.</span></span> <span data-ttu-id="d06f0-184">Genel tür gerekli olmadığından bir "Tür kitaplığı ihracatçısı uyarısı" beklenir, ancak bir sorun değildir.</span><span class="sxs-lookup"><span data-stu-id="d06f0-184">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
6. <span data-ttu-id="d06f0-185">`gacutil.exe /i client.dll` Derlemeyi Genel Montaj Önbelleğine eklemek için yazın.</span><span class="sxs-lookup"><span data-stu-id="d06f0-185">Type in `gacutil.exe /i client.dll` to add the assembly to the Global Assembly Cache.</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="d06f0-186">Örneği aynı bilgisayarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="d06f0-186">To run the sample on the same computer</span></span>  
  
1. <span data-ttu-id="d06f0-187">Aşağıdaki adresi yazarak bir tarayıcı kullanarak hizmete erişebileceğinizi test edin: `http://localhost/servicemodelsamples/service.svc`.</span><span class="sxs-lookup"><span data-stu-id="d06f0-187">Test that you can access the service using a browser by typing in the following address: `http://localhost/servicemodelsamples/service.svc`.</span></span> <span data-ttu-id="d06f0-188">Yanıt olarak bir onay sayfası görüntülenmelidir.</span><span class="sxs-lookup"><span data-stu-id="d06f0-188">A confirmation page should be displayed in response.</span></span>  
  
2. <span data-ttu-id="d06f0-189">ComCalcClient.vbs'yi \client'dan, dile özgü klasörün altından çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d06f0-189">Run ComCalcClient.vbs from \client, from under the language-specific folder.</span></span> <span data-ttu-id="d06f0-190">İstemci etkinliği ileti kutusu pencerelerinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d06f0-190">Client activity is displayed in message box windows.</span></span>  
  
3. <span data-ttu-id="d06f0-191">İstemci ve hizmet iletişim kuramazsa, [WCF Örnekleri için Sorun Giderme İpuçları'na](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))bakın.</span><span class="sxs-lookup"><span data-stu-id="d06f0-191">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="d06f0-192">Örneği bilgisayarlarda çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="d06f0-192">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="d06f0-193">Hizmet bilgisayarında ServiceModelSamples adlı sanal bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d06f0-193">On the service computer, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="d06f0-194">Örnekle birlikte verilen Setupvroot.bat komut dosyası, disk dizini ve sanal dizini oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d06f0-194">The Setupvroot.bat script included with the sample can be used to create the disk directory and virtual directory.</span></span>  
  
2. <span data-ttu-id="d06f0-195">Hizmet programı dosyalarını %SystemDrive%\Inetpub\wwwroot\servicemodelsamples'ten serviceModelSamples sanal dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="d06f0-195">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service computer.</span></span> <span data-ttu-id="d06f0-196">Dosyaları \bin dizinine eklediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="d06f0-196">Be sure to include the files in the \bin directory.</span></span>  
  
3. <span data-ttu-id="d06f0-197">İstemci komut dosyası dosyasını dile özgü klasörün altındaki \client klasöründen istemci bilgisayarına kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="d06f0-197">Copy the client script file from the \client folder, under the language-specific folder, to the client computer.</span></span>  
  
4. <span data-ttu-id="d06f0-198">Komut dosyası dosyasında, hizmetinyeni adresiyle eşleşecek şekilde bitiş noktası tanımının adres değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d06f0-198">In the script file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="d06f0-199">"Localhost" için yapılan başvuruları adreste tam nitelikli bir etki alanı adı ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d06f0-199">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
5. <span data-ttu-id="d06f0-200">WSDL dosyasını istemci bilgisayara kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="d06f0-200">Copy the WSDL file to the client computer.</span></span> <span data-ttu-id="d06f0-201">WSDL dosyasında serviceWsdl.xml, "localhost" için yapılan tüm başvuruları adreste tam nitelikli bir etki alanı adı ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d06f0-201">In the WSDL file, serviceWsdl.xml, replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
6. <span data-ttu-id="d06f0-202">İstemci.dll kitaplığını \client\bin klasöründen, dile özgü klasörün altından istemci bilgisayardaki bir dizine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="d06f0-202">Copy the Client.dll library from the \client\bin folder, under the language-specific folder, to a directory on the client computer.</span></span>  
  
7. <span data-ttu-id="d06f0-203">Komut isteminden istemci bilgisayardaki hedef dizine gidin.</span><span class="sxs-lookup"><span data-stu-id="d06f0-203">From a command prompt, navigate to that destination directory on the client computer.</span></span> <span data-ttu-id="d06f0-204">Windows Vista veya Windows Server 2008 kullanıyorsanız, komut istemini Administrator olarak çalıştırkullandığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="d06f0-204">If using Windows Vista or Windows Server 2008, make sure to run the command prompt as Administrator.</span></span>  
  
8. <span data-ttu-id="d06f0-205">tlb `tlbexp.exe client.dll /out:CalcProxy.tlb` dosyasına dll'yi dışa aktarmak için yazın.</span><span class="sxs-lookup"><span data-stu-id="d06f0-205">Type in `tlbexp.exe client.dll /out:CalcProxy.tlb` to export the dll to a tlb file.</span></span> <span data-ttu-id="d06f0-206">Genel tür gerekli olmadığından bir "Tür kitaplığı ihracatçısı uyarısı" beklenir, ancak bir sorun değildir.</span><span class="sxs-lookup"><span data-stu-id="d06f0-206">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
9. <span data-ttu-id="d06f0-207">Türleri `regasm.exe /tlb:CalcProxy.tlb client.dll` COM'a kaydetmek için yazın.</span><span class="sxs-lookup"><span data-stu-id="d06f0-207">Type in `regasm.exe /tlb:CalcProxy.tlb client.dll` to register the types with COM.</span></span> <span data-ttu-id="d06f0-208">Komutu çalıştırmadan önce yolun içeren `regasm.exe` klasöre ayarlandığını emin olun.</span><span class="sxs-lookup"><span data-stu-id="d06f0-208">Ensure that path has been set to the folder that contains `regasm.exe` before you run the command.</span></span>  
  
10. <span data-ttu-id="d06f0-209">`gacutil.exe /i client.dll` Derlemeyi Genel Montaj Önbelleğine eklemek için yazın.</span><span class="sxs-lookup"><span data-stu-id="d06f0-209">Type in `gacutil.exe /i client.dll` to add the assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="d06f0-210">Komutu çalıştırmadan önce yolun içeren `gacutil.exe` klasöre ayarlandığını emin olun.</span><span class="sxs-lookup"><span data-stu-id="d06f0-210">Ensure that path has been set to the folder that contains `gacutil.exe` before you run the command.</span></span>  
  
11. <span data-ttu-id="d06f0-211">Bir tarayıcı kullanarak istemci bilgisayardan hizmete erişebileceğinizi test edin.</span><span class="sxs-lookup"><span data-stu-id="d06f0-211">Test that you can access the service from the client computer using a browser.</span></span>  
  
12. <span data-ttu-id="d06f0-212">İstemci bilgisayarında ComCalcClient.vbs'i başlatın.</span><span class="sxs-lookup"><span data-stu-id="d06f0-212">On the client computer, launch ComCalcClient.vbs.</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="d06f0-213">Örnekten sonra temizlemek için</span><span class="sxs-lookup"><span data-stu-id="d06f0-213">To clean up after the sample</span></span>  
  
- <span data-ttu-id="d06f0-214">Güvenlik amacıyla, örnekleri bitirdikten sonra kurulum adımlarında verilen sanal dizin tanımını ve izinleri kaldırın.</span><span class="sxs-lookup"><span data-stu-id="d06f0-214">For security purposes, remove the virtual directory definition and permissions granted in the setup steps when you are finished with the samples.</span></span>  
