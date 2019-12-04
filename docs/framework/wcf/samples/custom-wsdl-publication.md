---
title: Özel WSDL Yayımı
ms.date: 03/30/2017
ms.assetid: 3b3e8103-2c95-4db3-a05b-46aa8e9d4d29
ms.openlocfilehash: 173deaf280c052b76e6937b2cec44ebdeafc57f9
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714912"
---
# <a name="custom-wsdl-publication"></a>Özel WSDL Yayımı
Bu örnekte nasıl yapılacağı gösterilmektedir:  
  
- Öznitelik özelliklerini WSDL ek açıklamaları olarak dışarı aktarmak için özel bir <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> özniteliğinde <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> uygulayın.  
  
- Özel WSDL ek açıklamalarını içeri aktarmak için <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> uygulayın.  
  
- İçeri aktarılan ek açıklamaları, içeri aktarılan sözleşme ve işlem için CodeDom içinde açıklama olarak yazmak üzere bir özel sözleşme davranışına ve sırasıyla özel bir işlem davranışına <xref:System.ServiceModel.Description.IServiceContractGenerationExtension?displayProperty=nameWithType> ve <xref:System.ServiceModel.Description.IOperationContractGenerationExtension?displayProperty=nameWithType> uygulayın.  
  
- WSDL 'yi indirmek için <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType>, özel WSDL İçeri Aktarıcısı kullanılarak WSDL 'yi içeri aktarmak için bir <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> ve ' a C# ve Visual Basic ' ' ' ve ' ' ' AÇıKLAMALARı olarak WSDL ek açıklamaları ile WINDOWS COMMUNICATION FOUNDATION (WCF) istemci kodu oluşturmak için <xref:System.ServiceModel.Description.ServiceContractGenerator?displayProperty=nameWithType> kullanın.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
## <a name="service"></a>Hizmet  
 Bu örnekteki hizmet iki özel öznitelikle işaretlenir. İlki `WsdlDocumentationAttribute`, oluşturucuda bir dize kabul eder ve bir sözleşme arabirimi ya da kullanımını açıklayan bir dize içeren bir işlem sağlamak için uygulanabilir. İkinci, `WsdlParamOrReturnDocumentationAttribute`, işlem içindeki değerleri tanımlayacak şekilde dönüş değerleri veya parametrelerine uygulanabilir. Aşağıdaki örnek, bu öznitelikler kullanılarak açıklanan `ICalculator`bir hizmet sözleşmesini gösterir.  
  
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
  
 `WsdlDocumentationAttribute`, <xref:System.ServiceModel.Description.IContractBehavior> ve <xref:System.ServiceModel.Description.IOperationBehavior>uygular, bu nedenle öznitelik örnekleri, hizmet açıldığında karşılık gelen <xref:System.ServiceModel.Description.ContractDescription> veya <xref:System.ServiceModel.Description.OperationDescription> eklenir. Öznitelik <xref:System.ServiceModel.Description.IWsdlExportExtension>de uygular. <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%28System.ServiceModel.Description.WsdlExporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> çağrıldığında, meta verileri dışarı aktarmak için kullanılan <xref:System.ServiceModel.Description.WsdlExporter> ve hizmet açıklaması nesnelerini içeren <xref:System.ServiceModel.Description.WsdlContractConversionContext>, dışarı aktarılan meta verilerin değiştirilmesini etkinleştiren parametreler olarak geçirilir.  
  
 Bu örnekte, dışa aktarma bağlamı nesnesinin bir <xref:System.ServiceModel.Description.ContractDescription> veya <xref:System.ServiceModel.Description.OperationDescription>sahip olmasına bağlı olarak, metin özelliği kullanılarak öznitelikten bir açıklama ayıklanır ve aşağıdaki kodda gösterildiği gibi WSDL Annotation öğesine eklenir.  
  
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
  
 Bir işlem aktarılıyorsa, örnek, parametreler ve dönüş değerleri için `WsdlParamOrReturnDocumentationAttribute` değerler elde etmek üzere yansıma kullanır ve bu işlem için aşağıdaki gibi WSDL ek açıklama öğelerine ekler.  
  
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
  
 Örnek, aşağıdaki yapılandırma dosyasını kullanarak meta verileri standart şekilde yayımlar.  
  
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
  
## <a name="svcutil-client"></a>Svcutil istemcisi  
 Bu örnek Svcutil. exe kullanmaz. Sözleşme, generatedClient.cs dosyasında sağlanır, böylece örnek özel WSDL içeri aktarma ve kod oluşturmayı gösterir, hizmet çağrılabilir. Bu örnek için aşağıdaki özel WSDL İçeri Aktarıcı 'yı kullanmak için Svcutil. exe ' yi çalıştırabilir ve bu örnekte kullanılan istemci yapılandırma dosyasının yolunu vererek, `WsdlDocumentation.dll` kitaplığına başvuran `/svcutilConfig` seçeneğini belirtebilirsiniz. `WsdlDocumentationImporter`yüklemek için, Svuctil. exe ' nin `WsdlDocumentation.dll` kitaplığını bulması ve yükleyebilmeleri gerekir. Bu, genel derleme önbelleğinde, yoldaki veya Svcutil. exe ile aynı dizinde olduğu anlamına gelir. Bunun gibi temel bir örnek için, en kolay şey, Svcutil. exe ' yi ve istemci yapılandırma dosyasını `WsdlDocumentation.dll` ile aynı dizine kopyalamak ve oradan çalıştırmak içindir.  
  
## <a name="the-custom-wsdl-importer"></a>Özel WSDL Içeri aktarıcı  
 Özel <xref:System.ServiceModel.Description.IWsdlImportExtension> nesnesi `WsdlDocumentationImporter` Ayrıca içeri aktarılan ServiceEndpoints ve <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> eklemek için <xref:System.ServiceModel.Description.IContractBehavior> ve <xref:System.ServiceModel.Description.IOperationBehavior> ve anlaşma ya da işlem kodu oluşturulurken kod oluşturmayı değiştirmek üzere çağrılacak <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> uygular.  
  
 İlk olarak, <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> yönteminde, WSDL ek açıklamanın anlaşma veya işlem düzeyinde olup olmadığını ve kendisini uygun kapsamda bir davranış olarak ekleyerek içeri aktarılan ek açıklama metnini oluşturucuya geçirerek, örnek.  
  
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
  
 Ardından, kod oluşturulduğunda, sistem <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> ve <xref:System.ServiceModel.Description.IOperationContractGenerationExtension.GenerateOperation%28System.ServiceModel.Description.OperationContractGenerationContext%29> yöntemlerini çağırır ve uygun bağlam bilgilerini geçirir. Örnek, özel WSDL ek açıklamalarını biçimlendirir ve bunları CodeDom öğesine açıklama olarak ekler.  
  
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
  
## <a name="the-client-application"></a>Istemci uygulaması  
 İstemci uygulaması, uygulama yapılandırma dosyasında belirterek özel WSDL İçeri Aktarıcı yükler.  
  
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
  
 Özel İçeri Aktarıcı belirtildiğinde, WCF meta veri sistemi özel İçeri Aktarıcı 'yı bu amaçla oluşturulan herhangi bir <xref:System.ServiceModel.Description.WsdlImporter> yükler. Bu örnek <xref:System.ServiceModel.Description.WsdlImporter>, meta verileri indirmek için <xref:System.ServiceModel.Description.MetadataExchangeClient> kullanır, örnek tarafından oluşturulan özel İçeri Aktarıcı kullanılarak meta verileri içeri aktarmak üzere düzgün şekilde yapılandırılmıştır ve "IntelliSense 'i desteklemek ya da XML belgelerine derlemek için Visual Studio C# 'da kullanılabilecek hem Visual Basic hem de istemci kodunda değiştirilen sözleşme bilgilerini derlemek için <xref:System.ServiceModel.Description.ServiceContractGenerator>.  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\WsdlDocumentation`  
