---
title: Özel WSDL Yayımı
ms.date: 03/30/2017
ms.assetid: 3b3e8103-2c95-4db3-a05b-46aa8e9d4d29
ms.openlocfilehash: b75aa2269d9c21a6f6d7f579d3c0b6f547a92332
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33807885"
---
# <a name="custom-wsdl-publication"></a>Özel WSDL Yayımı
Bu örnek gösterilmektedir nasıl yapılır:  
  
-   Uygulama bir <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> özel üzerinde <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> öznitelik özelliklerini WSDL ek açıklama olarak dışa aktarmak için öznitelik.  
  
-   Uygulama <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> özel WSDL ek açıklamaları içeri aktarmak için.  
  
-   Uygulama <xref:System.ServiceModel.Description.IServiceContractGenerationExtension?displayProperty=nameWithType> ve <xref:System.ServiceModel.Description.IOperationContractGenerationExtension?displayProperty=nameWithType> üzerinde özel ve bir özel işlem davranışlarını sırasıyla alınan sözleşme ve işlem için CodeDom açıklamaları olarak içeri aktarılan ek açıklamaları yazmak için sözleşme.  
  
-   Kullanım <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> WSDL indirmek için bir <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> özel WSDL içeri Aktarıcı kullanarak WSDL içe aktarmak için ve <xref:System.ServiceModel.Description.ServiceContractGenerator?displayProperty=nameWithType> olarak / / / WSDL ek açıklamalar ile Windows Communication Foundation (WCF) istemci kodu oluşturmak üzere ve ''' C# ve Visual açıklamaları Temel.  
  
> [!NOTE]
>  Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.  
  
## <a name="service"></a>Hizmet  
 Bu örnek hizmetinde iki özel özniteliklerle işaretlenmiş. İlk `WsdlDocumentationAttribute`, oluşturucuda bir dizesini kabul eder ve bir sözleşme arabirimi veya kullanım tanımlayan bir dize işlemiyle sağlamak için uygulanabilir. İkinci `WsdlParamOrReturnDocumentationAttribute`, değerler döndürürse veya bu değerleri işlemde açıklamak için parametreleri uygulanabilir. Aşağıdaki örnek, bir hizmet sözleşmesini gösterir `ICalculator`, açıklanan bu öznitelikleri kullanma.  
  
```  
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
  
 `WsdlDocumentationAttribute` Uygulayan <xref:System.ServiceModel.Description.IContractBehavior> ve <xref:System.ServiceModel.Description.IOperationBehavior>, karşılık gelen öznitelik örnekleri eklenen <xref:System.ServiceModel.Description.ContractDescription> veya <xref:System.ServiceModel.Description.OperationDescription> hizmet açıldığında. İmplements özniteliği de <xref:System.ServiceModel.Description.IWsdlExportExtension>. Zaman <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%28System.ServiceModel.Description.WsdlExporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> olarak adlandırılır, <xref:System.ServiceModel.Description.WsdlExporter> meta verilerini dışa aktarmak için kullanılır ve <xref:System.ServiceModel.Description.WsdlContractConversionContext> nesneler geçirilir dışarı aktarılan meta veri değişikliği etkinleştirme parametre olarak hizmet açıklaması içerir.  
  
 Dışarı aktarma bağlam nesnesi olup bağlı bağlı olarak, bu örnekteki bir <xref:System.ServiceModel.Description.ContractDescription> veya bir <xref:System.ServiceModel.Description.OperationDescription>, bir açıklama metin özelliğini kullanarak özniteliğinden ayıklanmış ve WSDL ek açıklama öğesi için aşağıdaki kodda gösterildiği gibi eklenir.  
  
```  
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
```  
  
 Bir işlem dışa aktardıysanız, örnek yansıma herhangi elde etmek için kullanır. `WsdlParamOrReturnDocumentationAttribute` parametreler ve dönüş değerleri için değerleri ve bunları bu işlem için WSDL ek açıklama öğeleri gibi ekler.  
  
```  
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
  
 Örnek, ardından aşağıdaki yapılandırma dosyası kullanarak standart şekilde meta verileri yayımlar.  
  
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
  
## <a name="svcutil-client"></a>Svcutil istemci  
 Bu örnek Svcutil.exe kullanmaz. Sözleşme generatedClient.cs örnek sonra gösterir şekilde özel WSDL içe aktarma ve kod oluşturma, hizmet dosya çağrılabilir sağlanır. Bu örnek için aşağıdaki özel WSDL alma aracını kullanmak için Svcutil.exe çalıştırın ve belirtin `/svcutilConfig` başvuruyor Bu örnekte kullanılan istemci yapılandırma dosyasının yolu vermiş seçeneği `WsdlDocumentation.dll` kitaplığı. Yüklemek için `WsdlDocumentationImporter`, ancak Svuctil.exe bulun ve yükleyemediğini olmalıdır `WsdlDocumentation.dll` kitaplığı, ya da genel derleme önbelleğinde yolu kayıtlı ya da Svcutil.exe ile aynı dizinde olduğu anlamına gelir. Bu gibi temel bir örnek için yapmak için kolay Svcutil.exe ve istemci yapılandırma dosyası ile aynı dizinde içine kopyalamak için şeydir `WsdlDocumentation.dll` ve oradan çalıştırın.  
  
## <a name="the-custom-wsdl-importer"></a>Özel WSDL içeri Aktarıcı  
 Özel <xref:System.ServiceModel.Description.IWsdlImportExtension> nesne `WsdlDocumentationImporter` de uygulayan <xref:System.ServiceModel.Description.IContractBehavior> ve <xref:System.ServiceModel.Description.IOperationBehavior> için içe aktarılan ServiceEndpoints öğelerinin eklenecek ve <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> ve <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> kod oluşturma değiştirmek için çağrılacak zaman sözleşme veya işlem kod oluşturuldu.  
  
 İlk olarak <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> yöntemi, örnek WSDL ek açıklama sözleşme veya işlem düzeyinde ve kendisi bir davranış içeri aktarılan ek açıklama metni kendi oluşturucusuna geçirerek uygun kapsamındaki olarak ekler olup olmadığını belirler.  
  
```  
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
  
 Ardından, kodu oluşturulduğunda Sistem çağırır <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> ve <xref:System.ServiceModel.Description.IOperationContractGenerationExtension.GenerateOperation%28System.ServiceModel.Description.OperationContractGenerationContext%29> uygun bağlam bilgilerini geçirme yöntemleri. Örnek özel WSDL ek açıklamaları biçimlendirir ve bunları CodeDom yorum olarak ekler.  
  
```  
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
  
## <a name="the-client-application"></a>İstemci uygulaması  
 İstemci uygulama, uygulama yapılandırma dosyasında belirterek özel WSDL içeri Aktarıcı yükler.  
  
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
  
 Özel içeri Aktarıcı belirtilen sonra WCF Meta verileri sistem özel içeri Aktarıcı hiçbir yükler <xref:System.ServiceModel.Description.WsdlImporter> bu amaçla oluşturulmuş. Bu örnekte <xref:System.ServiceModel.Description.MetadataExchangeClient> meta veri indirmek için <xref:System.ServiceModel.Description.WsdlImporter> bir örnek oluşturur, özel içeri Aktarıcı kullanarak meta verileri almak için düzgün şekilde yapılandırılmış ve <xref:System.ServiceModel.Description.ServiceContractGenerator> hem Visual Basic değiştirilmiş sözleşme bilgileri derlemek için ve IntelliSense desteklemek için Visual Studio'da kullanılan veya XML belgeleri derlenmiş C# istemci kodu.  
  
```  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\WsdlDocumentation`  
  
## <a name="see-also"></a>Ayrıca Bkz.
