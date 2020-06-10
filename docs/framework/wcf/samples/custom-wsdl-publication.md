---
title: Özel WSDL Yayımı
ms.date: 03/30/2017
ms.assetid: 3b3e8103-2c95-4db3-a05b-46aa8e9d4d29
ms.openlocfilehash: b18ac2f72d58c768b3784e1c414a71cdaec50c01
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596701"
---
# <a name="custom-wsdl-publication"></a>Özel WSDL Yayımı
Bu örnekte nasıl yapılacağı gösterilmektedir:  
  
- <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> ÖZNITELIK özelliklerini WSDL ek açıklamaları olarak dışarı aktarmak için özel bir özniteliğe uygulayın.  
  
- <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType>Özel wsdl ek açıklamalarını içeri aktarmak için uygulayın.  
  
- İçeri <xref:System.ServiceModel.Description.IServiceContractGenerationExtension?displayProperty=nameWithType> aktarılan <xref:System.ServiceModel.Description.IOperationContractGenerationExtension?displayProperty=nameWithType> ek açıklamaları, içeri aktarılan sözleşme ve Işlem için CodeDOM içinde açıklama olarak yazmak üzere özel bir sözleşme davranışını ve sırasıyla özel bir işlem davranışını uygulayın.  
  
- WSDL <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> 'yi indirmek için, <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> özel wsdl İçeri Aktarıcı 'Yı kullanarak WSDL 'yi içeri aktarmak üzere, ve <xref:System.ServiceModel.Description.ServiceContractGenerator?displayProperty=nameWithType> WSDL ek açıklamaları ile bırlıkte Windows Communication Foundation (WCF) istemci kodu oluşturmak Için ve C# ve Visual Basic ' ' ' açıklamaları kullanın.  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
## <a name="service"></a>Hizmet  
 Bu örnekteki hizmet iki özel öznitelikle işaretlenir. İlki, `WsdlDocumentationAttribute` oluşturucuda bir dizeyi kabul eder ve bir sözleşme arabirimi ya da kullanımını açıklayan bir dize içeren bir işlem sağlamak için uygulanabilir. İkinci, `WsdlParamOrReturnDocumentationAttribute` ,, işlem içindeki değerleri betimleyen değerleri veya parametreleri döndürmek için uygulanabilir. Aşağıdaki örnek, `ICalculator` Bu öznitelikler kullanılarak açıklanan bir hizmet sözleşmesini gösterir.  
  
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
  
 , `WsdlDocumentationAttribute` <xref:System.ServiceModel.Description.IContractBehavior> Ve uygular <xref:System.ServiceModel.Description.IOperationBehavior> , bu nedenle öznitelik örnekleri karşılık gelen <xref:System.ServiceModel.Description.ContractDescription> veya <xref:System.ServiceModel.Description.OperationDescription> hizmet açıldığında eklenir. Özniteliği de uygular <xref:System.ServiceModel.Description.IWsdlExportExtension> . <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%28System.ServiceModel.Description.WsdlExporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29>Çağrıldığında, <xref:System.ServiceModel.Description.WsdlExporter> meta verileri dışarı aktarmak için kullanılan ve <xref:System.ServiceModel.Description.WsdlContractConversionContext> hizmet açıklaması nesnelerini içeren ve, dışarı aktarılan meta verilerin değiştirilmesini sağlayan parametre olarak geçirilir.  
  
 Bu örnekte, dışa aktarma bağlamı nesnesinin bir veya ' a sahip olmasına bağlı olarak <xref:System.ServiceModel.Description.ContractDescription> <xref:System.ServiceModel.Description.OperationDescription> , metin özelliği kullanılarak öznitelikten bir açıklama ayıklanır ve aşağıdaki kodda GÖSTERILDIĞI gibi WSDL Annotation öğesine eklenir.  
  
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
  
 Bir işlem aktarılıyorsa, örnek, parametreler ve dönüş değerleri için herhangi bir değer elde etmek üzere yansıma kullanır `WsdlParamOrReturnDocumentationAttribute` ve bu işlem için aşağıdaki gıbı WSDL ek açıklama öğelerine ekler.  
  
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
 Bu örnek Svcutil. exe kullanmaz. Sözleşme, generatedClient.cs dosyasında sağlanır, böylece örnek özel WSDL içeri aktarma ve kod oluşturmayı gösterir, hizmet çağrılabilir. Bu örnek için aşağıdaki özel WSDL İçeri Aktarıcı 'yı kullanmak için, Svcutil. exe ' yi çalıştırabilir ve `/svcutilConfig` Bu örnekte kullanılan istemci yapılandırma dosyasının yolunu vererek kitaplığa başvuruda bulunan bu seçeneği belirtebilirsiniz `WsdlDocumentation.dll` . Bununla birlikte, yüklemek için, `WsdlDocumentationImporter` Svuctil. exe ' nin kitaplığı bulması ve yüklemesi gerekir, bu da `WsdlDocumentation.dll` genel derleme önbelleğinde, yoldaki veya Svcutil. exe ile aynı dizinde olduğu anlamına gelir. Bunun gibi basit bir örnek için en kolay şey, Svcutil. exe ' yi ve istemci yapılandırma dosyasını aynı dizine kopyalamak `WsdlDocumentation.dll` ve oradan çalıştırmak içindir.  
  
## <a name="the-custom-wsdl-importer"></a>Özel WSDL Içeri aktarıcı  
 Özel <xref:System.ServiceModel.Description.IWsdlImportExtension> nesne `WsdlDocumentationImporter` Ayrıca <xref:System.ServiceModel.Description.IContractBehavior> <xref:System.ServiceModel.Description.IOperationBehavior> içeri aktarılan hizmet uç noktalarına eklenmek üzere ve <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> anlaşma ya da işlem kodu oluşturulurken kod oluşturmayı değiştirmek için çağrılabilir.  
  
 İlk olarak, <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> yönteminde, WSDL ek açıklamanın anlaşma ya da işlem düzeyinde olup olmadığını ve kendisini uygun kapsamda bir davranış olarak ekleyerek içeri aktarılan ek açıklama metnini oluşturucuya geçirerek, örnek.  
  
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
  
 Ardından, kod oluşturulduğunda, sistem <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> ve <xref:System.ServiceModel.Description.IOperationContractGenerationExtension.GenerateOperation%28System.ServiceModel.Description.OperationContractGenerationContext%29> yöntemlerini, uygun bağlam bilgilerini geçirerek çağırır. Örnek, özel WSDL ek açıklamalarını biçimlendirir ve bunları CodeDom öğesine açıklama olarak ekler.  
  
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
  
 Özel İçeri Aktarıcı belirtildiğinde, WCF meta veri sistemi özel İçeri Aktarıcı 'yı <xref:System.ServiceModel.Description.WsdlImporter> Bu amaçla oluşturulan herhangi bir için yükler. Bu örnek, <xref:System.ServiceModel.Description.MetadataExchangeClient> meta verileri indirmek için, örnek tarafından <xref:System.ServiceModel.Description.WsdlImporter> oluşturulan özel içe aktarıcı kullanılarak meta verileri içeri aktarmak üzere yapılandırılan doğru şekilde yapılandırılmış ve <xref:System.ServiceModel.Description.ServiceContractGenerator> değiştirilen sözleşme BILGILERINI IntelliSense veya XML belgelerine derlenmiş şekilde Visual Studio 'da kullanılabilecek Visual Basic ve C# istemci koduna derlemek için kullanır.  
  
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
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\WsdlDocumentation`  
