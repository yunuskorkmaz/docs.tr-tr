---
title: Özel WSDL Yayımı
ms.date: 03/30/2017
ms.assetid: 3b3e8103-2c95-4db3-a05b-46aa8e9d4d29
ms.openlocfilehash: 9d753ca30bdcf66f5225700245b9688c5226613e
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73978286"
---
# <a name="custom-wsdl-publication"></a><span data-ttu-id="8eb40-102">Özel WSDL Yayımı</span><span class="sxs-lookup"><span data-stu-id="8eb40-102">Custom WSDL Publication</span></span>
<span data-ttu-id="8eb40-103">Bu örnekte nasıl yapılacağı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="8eb40-103">This sample demonstrates how to:</span></span>  
  
- <span data-ttu-id="8eb40-104">Öznitelik özelliklerini WSDL ek açıklamaları olarak dışarı aktarmak için özel bir <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> özniteliğinde <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> uygulayın.</span><span class="sxs-lookup"><span data-stu-id="8eb40-104">Implement a <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> on a custom <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> attribute to export attribute properties as WSDL annotations.</span></span>  
  
- <span data-ttu-id="8eb40-105">Özel WSDL ek açıklamalarını içeri aktarmak için <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> uygulayın.</span><span class="sxs-lookup"><span data-stu-id="8eb40-105">Implement <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> to import the custom WSDL annotations.</span></span>  
  
- <span data-ttu-id="8eb40-106">İçeri aktarılan ek açıklamaları, içeri aktarılan sözleşme ve işlem için CodeDom içinde açıklama olarak yazmak üzere bir özel sözleşme davranışına ve sırasıyla özel bir işlem davranışına <xref:System.ServiceModel.Description.IServiceContractGenerationExtension?displayProperty=nameWithType> ve <xref:System.ServiceModel.Description.IOperationContractGenerationExtension?displayProperty=nameWithType> uygulayın.</span><span class="sxs-lookup"><span data-stu-id="8eb40-106">Implement <xref:System.ServiceModel.Description.IServiceContractGenerationExtension?displayProperty=nameWithType> and <xref:System.ServiceModel.Description.IOperationContractGenerationExtension?displayProperty=nameWithType> on a custom contract behavior and a custom operation behavior, respectively, to write imported annotations as comments in the CodeDom for the imported contract and operation.</span></span>  
  
- <span data-ttu-id="8eb40-107">WSDL 'yi indirmek için <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType>, özel WSDL İçeri Aktarıcısı kullanılarak WSDL 'yi içeri aktarmak için bir <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> ve ' a C# ve Visual Basic ' ' ' ve ' ' ' AÇıKLAMALARı olarak WSDL ek açıklamaları ile WINDOWS COMMUNICATION FOUNDATION (WCF) istemci kodu oluşturmak için <xref:System.ServiceModel.Description.ServiceContractGenerator?displayProperty=nameWithType> kullanın.</span><span class="sxs-lookup"><span data-stu-id="8eb40-107">Use the <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> to download the WSDL, a <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> to import the WSDL using the custom WSDL importer, and the <xref:System.ServiceModel.Description.ServiceContractGenerator?displayProperty=nameWithType> to generate Windows Communication Foundation (WCF) client code with the WSDL annotations as /// and ''' comments in C# and Visual Basic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8eb40-108">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="8eb40-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="service"></a><span data-ttu-id="8eb40-109">Hizmet</span><span class="sxs-lookup"><span data-stu-id="8eb40-109">Service</span></span>  
 <span data-ttu-id="8eb40-110">Bu örnekteki hizmet iki özel öznitelikle işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="8eb40-110">The service in this sample is marked with two custom attributes.</span></span> <span data-ttu-id="8eb40-111">İlki `WsdlDocumentationAttribute`, oluşturucuda bir dize kabul eder ve bir sözleşme arabirimi ya da kullanımını açıklayan bir dize içeren bir işlem sağlamak için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="8eb40-111">The first, the `WsdlDocumentationAttribute`, accepts a string in the constructor and can be applied to provide a contract interface or operation with a string that describes its usage.</span></span> <span data-ttu-id="8eb40-112">İkinci, `WsdlParamOrReturnDocumentationAttribute`, işlem içindeki değerleri tanımlayacak şekilde dönüş değerleri veya parametrelerine uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="8eb40-112">The second, `WsdlParamOrReturnDocumentationAttribute`, can be applied to return values or parameters to describe those values in the operation.</span></span> <span data-ttu-id="8eb40-113">Aşağıdaki örnek, bu öznitelikler kullanılarak açıklanan `ICalculator`bir hizmet sözleşmesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8eb40-113">The following example shows a service contract, `ICalculator`, described using these attributes.</span></span>  
  
```csharp  
// Define a service contract.      
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
// Document it.  
[WsdlDocumentation("The ICalculator contract performs basic calculation services.")]  
public interface ICalculator  
{  
    [OperationContract]  
    [WsdlDocumentation("The Add operation adds two numbers and returns the result.")]  
    [return:WsdlParamOrReturnDocumentation("The result of adding the two arguments together.")]  
    double Add(  
      [WsdlParamOrReturnDocumentation("The first value to add.")]double n1,   
      [WsdlParamOrReturnDocumentation("The second value to add.")]double n2  
    );  
  
    [OperationContract]  
    [WsdlDocumentation("The Subtract operation subtracts the second argument from the first.")]  
    [return:WsdlParamOrReturnDocumentation("The result of the second argument subtracted from the first.")]  
    double Subtract(  
      [WsdlParamOrReturnDocumentation("The value from which the second is subtracted.")]double n1,   
      [WsdlParamOrReturnDocumentation("The value that is subtracted from the first.")]double n2  
    );  
  
    [OperationContract]  
    [WsdlDocumentation("The Multiply operation multiplies two values.")]  
    [return:WsdlParamOrReturnDocumentation("The result of multiplying the first and second arguments.")]  
    double Multiply(  
      [WsdlParamOrReturnDocumentation("The first value to multiply.")]double n1,   
      [WsdlParamOrReturnDocumentation("The second value to multiply.")]double n2  
    );  
  
    [OperationContract]  
    [WsdlDocumentation("The Divide operation returns the value of the first argument divided by the second argument.")]  
    [return:WsdlParamOrReturnDocumentation("The result of dividing the first argument by the second.")]  
    double Divide(  
      [WsdlParamOrReturnDocumentation("The numerator.")]double n1,   
      [WsdlParamOrReturnDocumentation("The denominator.")]double n2  
    );  
}  
```  
  
 <span data-ttu-id="8eb40-114">`WsdlDocumentationAttribute`, <xref:System.ServiceModel.Description.IContractBehavior> ve <xref:System.ServiceModel.Description.IOperationBehavior>uygular, bu nedenle öznitelik örnekleri, hizmet açıldığında karşılık gelen <xref:System.ServiceModel.Description.ContractDescription> veya <xref:System.ServiceModel.Description.OperationDescription> eklenir.</span><span class="sxs-lookup"><span data-stu-id="8eb40-114">The `WsdlDocumentationAttribute` implements <xref:System.ServiceModel.Description.IContractBehavior> and <xref:System.ServiceModel.Description.IOperationBehavior>, so the attribute instances are added to the corresponding <xref:System.ServiceModel.Description.ContractDescription> or <xref:System.ServiceModel.Description.OperationDescription> when the service is opened.</span></span> <span data-ttu-id="8eb40-115">Öznitelik <xref:System.ServiceModel.Description.IWsdlExportExtension>de uygular.</span><span class="sxs-lookup"><span data-stu-id="8eb40-115">The attribute also implements <xref:System.ServiceModel.Description.IWsdlExportExtension>.</span></span> <span data-ttu-id="8eb40-116"><xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%28System.ServiceModel.Description.WsdlExporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> çağrıldığında, meta verileri dışarı aktarmak için kullanılan <xref:System.ServiceModel.Description.WsdlExporter> ve hizmet açıklaması nesnelerini içeren <xref:System.ServiceModel.Description.WsdlContractConversionContext>, dışarı aktarılan meta verilerin değiştirilmesini etkinleştiren parametreler olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="8eb40-116">When <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%28System.ServiceModel.Description.WsdlExporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> is called, the <xref:System.ServiceModel.Description.WsdlExporter> that is used to export the metadata and the <xref:System.ServiceModel.Description.WsdlContractConversionContext> that contains the service description objects are passed in as parameters enabling the modification of the exported metadata.</span></span>  
  
 <span data-ttu-id="8eb40-117">Bu örnekte, dışa aktarma bağlamı nesnesinin bir <xref:System.ServiceModel.Description.ContractDescription> veya <xref:System.ServiceModel.Description.OperationDescription>sahip olmasına bağlı olarak, metin özelliği kullanılarak öznitelikten bir açıklama ayıklanır ve aşağıdaki kodda gösterildiği gibi WSDL Annotation öğesine eklenir.</span><span class="sxs-lookup"><span data-stu-id="8eb40-117">In this sample, depending upon whether the export context object has a <xref:System.ServiceModel.Description.ContractDescription> or an <xref:System.ServiceModel.Description.OperationDescription>, a comment is extracted from the attribute using the text property and is added to the WSDL annotation element as shown in the following code.</span></span>  
  
```csharp
public void ExportContract(WsdlExporter exporter, WsdlContractConversionContext context)
{
    if (contractDescription != null)
    {
        // Inside this block it is the contract-level comment attribute.
        // This.Text returns the string for the contract attribute.
        // Set the doc element; if this isn't done first, there is no XmlElement in the
        // DocumentElement property.
        context.WsdlPortType.Documentation = string.Empty;
        // Contract comments.
        XmlDocument owner = context.WsdlPortType.DocumentationElement.OwnerDocument;
        XmlElement summaryElement = owner.CreateElement("summary");
        summaryElement.InnerText = this.Text;
        context.WsdlPortType.DocumentationElement.AppendChild(summaryElement);
    }
    else
    {
        Operation operation = context.GetOperation(operationDescription);
        if (operation != null)
        {
            // We are dealing strictly with the operation here.
            // This.Text returns the string for the operation-level attributes.
            // Set the doc element; if this isn't done first, there is no XmlElement in the
            // DocumentElement property.
            operation.Documentation = String.Empty;

            // Operation C# triple comments.
            XmlDocument owner = operation.DocumentationElement.OwnerDocument;
            XmlElement newSummaryElement = owner.CreateElement("summary");
            newSummaryElement.InnerText = this.Text;
            operation.DocumentationElement.AppendChild(newSummaryElement);
        }
    }
}
```  
  
 <span data-ttu-id="8eb40-118">Bir işlem aktarılıyorsa, örnek, parametreler ve dönüş değerleri için `WsdlParamOrReturnDocumentationAttribute` değerler elde etmek üzere yansıma kullanır ve bu işlem için aşağıdaki gibi WSDL ek açıklama öğelerine ekler.</span><span class="sxs-lookup"><span data-stu-id="8eb40-118">If an operation is being exported, the sample uses reflection to obtain any `WsdlParamOrReturnDocumentationAttribute` values for parameters and return values and adds them to the WSDL annotation elements for that operation as follows.</span></span>  
  
```csharp
// Get returns information  
ParameterInfo returnValue = operationDescription.SyncMethod.ReturnParameter;  
object[] returnAttrs = returnValue.GetCustomAttributes(typeof(WsdlParamOrReturnDocumentationAttribute), false);  
if (returnAttrs.Length != 0)  
{  
    // <returns>text.</returns>  
    XmlElement returnsElement = owner.CreateElement("returns");  
    returnsElement.InnerText = ((WsdlParamOrReturnDocumentationAttribute)returnAttrs[0]).ParamComment;  
    operation.DocumentationElement.AppendChild(returnsElement);  
}  
  
// Get parameter information.  
ParameterInfo[] args = operationDescription.SyncMethod.GetParameters();  
for (int i = 0; i < args.Length; i++)  
{  
    object[] docAttrs = args[i].GetCustomAttributes(typeof(WsdlParamOrReturnDocumentationAttribute), false);  
    if (docAttrs.Length == 1)  
    {  
        // <param name="Int1">Text.</param>  
        XmlElement newParamElement = owner.CreateElement("param");  
        XmlAttribute paramName = owner.CreateAttribute("name");  
        paramName.Value = args[i].Name;  
        newParamElement.InnerText = ((WsdlParamOrReturnDocumentationAttribute)docAttrs[0]).ParamComment;  
        newParamElement.Attributes.Append(paramName);  
        operation.DocumentationElement.AppendChild(newParamElement);  
    }  
}  
```  
  
 <span data-ttu-id="8eb40-119">Örnek, aşağıdaki yapılandırma dosyasını kullanarak meta verileri standart şekilde yayımlar.</span><span class="sxs-lookup"><span data-stu-id="8eb40-119">The sample then publishes metadata in the standard way, using the following configuration file.</span></span>  
  
```xml  
<services>  
  <service   
      name="Microsoft.ServiceModel.Samples.CalculatorService"  
      behaviorConfiguration="CalculatorServiceBehavior">  
    <!-- ICalculator is exposed at the base address provided by host: http://localhost/servicemodelsamples/service.svc  -->  
    <endpoint address=""  
              binding="wsHttpBinding"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    <!-- the mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex -->  
    <endpoint address="mex"  
              binding="mexHttpBinding"  
              contract="IMetadataExchange" />  
  </service>  
</services>  
  
<!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="svcutil-client"></a><span data-ttu-id="8eb40-120">Svcutil istemcisi</span><span class="sxs-lookup"><span data-stu-id="8eb40-120">Svcutil client</span></span>  
 <span data-ttu-id="8eb40-121">Bu örnek Svcutil. exe kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="8eb40-121">This sample does not use Svcutil.exe.</span></span> <span data-ttu-id="8eb40-122">Sözleşme, generatedClient.cs dosyasında sağlanır, böylece örnek özel WSDL içeri aktarma ve kod oluşturmayı gösterir, hizmet çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="8eb40-122">The contract is provided in the generatedClient.cs file so that after the sample demonstrates custom WSDL import and code generation, the service can be invoked.</span></span> <span data-ttu-id="8eb40-123">Bu örnek için aşağıdaki özel WSDL İçeri Aktarıcı 'yı kullanmak için Svcutil. exe ' yi çalıştırabilir ve bu örnekte kullanılan istemci yapılandırma dosyasının yolunu vererek, `WsdlDocumentation.dll` kitaplığına başvuran `/svcutilConfig` seçeneğini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8eb40-123">To use the following custom WSDL importer for this example, you can run Svcutil.exe and specify the `/svcutilConfig` option, giving the path to the client configuration file used in this sample, which references the `WsdlDocumentation.dll` library.</span></span> <span data-ttu-id="8eb40-124">`WsdlDocumentationImporter`yüklemek için, Svuctil. exe ' nin `WsdlDocumentation.dll` kitaplığını bulması ve yükleyebilmeleri gerekir. Bu, genel derleme önbelleğinde, yoldaki veya Svcutil. exe ile aynı dizinde olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="8eb40-124">To load the `WsdlDocumentationImporter`, however, Svuctil.exe must be able to locate and load the `WsdlDocumentation.dll` library, which means either that it is registered in the global assembly cache, in the path, or is in the same directory as Svcutil.exe.</span></span> <span data-ttu-id="8eb40-125">Bunun gibi temel bir örnek için, en kolay şey, Svcutil. exe ' yi ve istemci yapılandırma dosyasını `WsdlDocumentation.dll` ile aynı dizine kopyalamak ve oradan çalıştırmak içindir.</span><span class="sxs-lookup"><span data-stu-id="8eb40-125">For a basic sample such as this, the easiest thing to do is to copy Svcutil.exe and the client configuration file into the same directory as `WsdlDocumentation.dll` and run it from there.</span></span>  
  
## <a name="the-custom-wsdl-importer"></a><span data-ttu-id="8eb40-126">Özel WSDL Içeri aktarıcı</span><span class="sxs-lookup"><span data-stu-id="8eb40-126">The Custom WSDL Importer</span></span>  
 <span data-ttu-id="8eb40-127">Özel <xref:System.ServiceModel.Description.IWsdlImportExtension> nesnesi `WsdlDocumentationImporter` Ayrıca içeri aktarılan ServiceEndpoints ve <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> eklemek için <xref:System.ServiceModel.Description.IContractBehavior> ve <xref:System.ServiceModel.Description.IOperationBehavior> ve anlaşma ya da işlem kodu oluşturulurken kod oluşturmayı değiştirmek üzere çağrılacak <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> uygular.</span><span class="sxs-lookup"><span data-stu-id="8eb40-127">The custom <xref:System.ServiceModel.Description.IWsdlImportExtension> object `WsdlDocumentationImporter` also implements <xref:System.ServiceModel.Description.IContractBehavior> and <xref:System.ServiceModel.Description.IOperationBehavior> to be added to the imported ServiceEndpoints and <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> and <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> to be invoked to modify the code generation when the contract or operation code is being created.</span></span>  
  
 <span data-ttu-id="8eb40-128">İlk olarak, <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> yönteminde, WSDL ek açıklamanın anlaşma veya işlem düzeyinde olup olmadığını ve kendisini uygun kapsamda bir davranış olarak ekleyerek içeri aktarılan ek açıklama metnini oluşturucuya geçirerek, örnek.</span><span class="sxs-lookup"><span data-stu-id="8eb40-128">First, in the <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> method, the sample determines whether the WSDL annotation is at the contract or operation level, and adds itself as a behavior at the appropriate scope, passing the imported annotation text to its constructor.</span></span>  
  
```csharp
public void ImportContract(WsdlImporter importer, WsdlContractConversionContext context)  
{  
    // Contract Documentation  
    if (context.WsdlPortType.Documentation != null)  
    {  
        // System examines the contract behaviors to see whether any implement IWsdlImportExtension.  
        context.Contract.Behaviors.Add(new WsdlDocumentationImporter(context.WsdlPortType.Documentation));  
    }  
    // Operation Documentation  
    foreach (Operation operation in context.WsdlPortType.Operations)  
    {  
        if (operation.Documentation != null)  
        {  
            OperationDescription operationDescription = context.Contract.Operations.Find(operation.Name);  
            if (operationDescription != null)  
            {  
                // System examines the operation behaviors to see whether any implement IWsdlImportExtension.  
                operationDescription.Behaviors.Add(new WsdlDocumentationImporter(operation.Documentation));  
            }  
        }  
    }  
}  
```  
  
 <span data-ttu-id="8eb40-129">Ardından, kod oluşturulduğunda, sistem <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> ve <xref:System.ServiceModel.Description.IOperationContractGenerationExtension.GenerateOperation%28System.ServiceModel.Description.OperationContractGenerationContext%29> yöntemlerini çağırır ve uygun bağlam bilgilerini geçirir.</span><span class="sxs-lookup"><span data-stu-id="8eb40-129">Then, when the code is generated, the system invokes the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> and <xref:System.ServiceModel.Description.IOperationContractGenerationExtension.GenerateOperation%28System.ServiceModel.Description.OperationContractGenerationContext%29> methods, passing the appropriate context information.</span></span> <span data-ttu-id="8eb40-130">Örnek, özel WSDL ek açıklamalarını biçimlendirir ve bunları CodeDom öğesine açıklama olarak ekler.</span><span class="sxs-lookup"><span data-stu-id="8eb40-130">The sample formats the custom WSDL annotations and inserts them as comments into the CodeDom.</span></span>  
  
```csharp
public void GenerateContract(ServiceContractGenerationContext context)  
{  
    Debug.WriteLine("In generate contract.");  
    context.ContractType.Comments.AddRange(FormatComments(text));  
}  
  
public void GenerateOperation(OperationContractGenerationContext context)  
{  
    context.SyncMethod.Comments.AddRange(FormatComments(text));  
    Debug.WriteLine("In generate operation.");  
}  
```  
  
## <a name="the-client-application"></a><span data-ttu-id="8eb40-131">Istemci uygulaması</span><span class="sxs-lookup"><span data-stu-id="8eb40-131">The Client Application</span></span>  
 <span data-ttu-id="8eb40-132">İstemci uygulaması, uygulama yapılandırma dosyasında belirterek özel WSDL İçeri Aktarıcı yükler.</span><span class="sxs-lookup"><span data-stu-id="8eb40-132">The client application loads the custom WSDL importer by specifying it in the application configuration file.</span></span>  
  
```xml  
<client>  
  <endpoint address="http://localhost/servicemodelsamples/service.svc"   
  binding="wsHttpBinding"   
  contract="ICalculator" />  
  <metadata>  
    <wsdlImporters>  
      <extension type="Microsoft.ServiceModel.Samples.WsdlDocumentationImporter, WsdlDocumentation"/>  
    </wsdlImporters>  
  </metadata>  
</client>  
```  
  
 <span data-ttu-id="8eb40-133">Özel İçeri Aktarıcı belirtildiğinde, WCF meta veri sistemi özel İçeri Aktarıcı 'yı bu amaçla oluşturulan herhangi bir <xref:System.ServiceModel.Description.WsdlImporter> yükler.</span><span class="sxs-lookup"><span data-stu-id="8eb40-133">Once the custom importer has been specified, the WCF metadata system loads the custom importer into any <xref:System.ServiceModel.Description.WsdlImporter> created for that purpose.</span></span> <span data-ttu-id="8eb40-134">Bu örnek <xref:System.ServiceModel.Description.WsdlImporter>, meta verileri indirmek için <xref:System.ServiceModel.Description.MetadataExchangeClient> kullanır, örnek tarafından oluşturulan özel İçeri Aktarıcı kullanılarak meta verileri içeri aktarmak üzere düzgün şekilde yapılandırılmıştır ve "IntelliSense 'i desteklemek ya da XML belgelerine derlemek için Visual Studio C# 'da kullanılabilecek hem Visual Basic hem de istemci kodunda değiştirilen sözleşme bilgilerini derlemek için <xref:System.ServiceModel.Description.ServiceContractGenerator>.</span><span class="sxs-lookup"><span data-stu-id="8eb40-134">This sample uses the <xref:System.ServiceModel.Description.MetadataExchangeClient> to download the metadata, the <xref:System.ServiceModel.Description.WsdlImporter> properly configured to import the metadata using the custom importer the sample creates, and the <xref:System.ServiceModel.Description.ServiceContractGenerator> to compile the modified contract information into both Visual Basic and C# client code that can be used in Visual Studio to support Intellisense or compiled into XML documentation.</span></span>  
  
```csharp
/// From WSDL Documentation:  
///   
/// <summary>The ICalculator contract performs basic calculation   
/// services.</summary>   
///   
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.ServiceContractAttribute(Namespace="http://Microsoft.ServiceModel.Samples", ConfigurationName="ICalculator")]  
public interface ICalculator  
{  
  
    /// From WSDL Documentation:  
    ///   
    /// <summary>The Add operation adds two numbers and returns the   
    /// result.</summary><returns>The result of adding the two arguments   
    /// together.</returns><param name="n1">The first value to add.</param><param   
    /// name="n2">The second value to add.</param>   
    ///   
    [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.ServiceModel.Samples/ICalculator/Add", ReplyAction="http://Microsoft.ServiceModel.Samples/ICalculator/AddResponse")]  
    double Add(double n1, double n2);  
  
    /// From WSDL Documentation:  
    ///   
    /// <summary>The Subtract operation subtracts the second argument from the   
    /// first.</summary><returns>The result of the second argument subtracted from the   
    /// first.</returns><param name="n1">The value from which the second is   
    /// subtracted.</param><param name="n2">The value that is subtracted from the   
    /// first.</param>   
    ///   
    [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.ServiceModel.Samples/ICalculator/Subtract", ReplyAction="http://Microsoft.ServiceModel.Samples/ICalculator/SubtractResponse")]  
    double Subtract(double n1, double n2);  
  
    /// From WSDL Documentation:  
    ///   
    /// <summary>The Multiply operation multiplies two values.</summary><returns>The   
    /// result of multiplying the first and second arguments.</returns><param   
    /// name="n1">The first value to multiply.</param><param name="n2">The second value   
    /// to multiply.</param>   
    ///   
    [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.ServiceModel.Samples/ICalculator/Multiply", ReplyAction="http://Microsoft.ServiceModel.Samples/ICalculator/MultiplyResponse")]  
    double Multiply(double n1, double n2);  
  
    /// From WSDL Documentation:  
    ///   
    /// <summary>The Divide operation returns the value of the first argument divided   
    /// by the second argument.</summary><returns>The result of dividing the first   
    /// argument by the second.</returns><param name="n1">The numerator.</param><param   
    /// name="n2">The denominator.</param>   
    ///   
    [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.ServiceModel.Samples/ICalculator/Divide", ReplyAction="http://Microsoft.ServiceModel.Samples/ICalculator/DivideResponse")]  
    double Divide(double n1, double n2);  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8eb40-135">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="8eb40-135">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="8eb40-136">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="8eb40-136">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="8eb40-137">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="8eb40-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="8eb40-138">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="8eb40-138">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8eb40-139">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="8eb40-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8eb40-140">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="8eb40-140">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="8eb40-141">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://go.microsoft.com/fwlink/?LinkId=150780) gidin.</span><span class="sxs-lookup"><span data-stu-id="8eb40-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8eb40-142">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="8eb40-142">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\WsdlDocumentation`  
