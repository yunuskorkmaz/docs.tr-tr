---
title: Özel WSDL Yayımı
ms.date: 03/30/2017
ms.assetid: 3b3e8103-2c95-4db3-a05b-46aa8e9d4d29
ms.openlocfilehash: 725b62a26d640e242010a01ff810ea90d5cc53bc
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43508426"
---
# <a name="custom-wsdl-publication"></a>Özel WSDL Yayımı
Bu örnek gösterir nasıl yapılır:  
  
-   Uygulama bir <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> özel üzerinde <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> WSDL ek açıklama olarak öznitelik özelliklerini dışa aktarmak için özniteliği.  
  
-   Uygulama <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> özel WSDL ek açıklamaları içeri aktarmak için.  
  
-   Uygulama <xref:System.ServiceModel.Description.IServiceContractGenerationExtension?displayProperty=nameWithType> ve <xref:System.ServiceModel.Description.IOperationContractGenerationExtension?displayProperty=nameWithType> özel üzerinde ve bir özel işlem davranışlarını sırasıyla, içeri aktarılan ek açıklamaları içeri aktarılan sözleşme ve işlem için CodeDom açıklamaları olarak yazmak için sözleşme.  
  
-   Kullanım <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> WSDL indirmek için bir <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> özel WSDL içeri Aktarıcı kullanarak WSDL içeri aktarmak için ve <xref:System.ServiceModel.Description.ServiceContractGenerator?displayProperty=nameWithType> olarak / / / WSDL ek açıklamalar ile Windows Communication Foundation (WCF) istemci kodu oluşturmak üzere ve ''' açıklamaları C# ve Visual Temel.  
  
> [!NOTE]
>  Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.  
  
## <a name="service"></a>Hizmet  
 Bu hizmet, iki özel öznitelikler ile işaretlenir. Birincisi, `WsdlDocumentationAttribute`, oluşturucuda bir dizesini kabul eder ve bir sözleşme arabirimi veya kullanımını açıklayan bir dize işleme sağlamak için uygulanabilir. İkinci `WsdlParamOrReturnDocumentationAttribute`, değerler ya da işlemi o değerleri tanımlamak için parametreleri döndürmek için uygulanabilir. Aşağıdaki örnek, bir hizmet sözleşmesini gösterir `ICalculator`açıklandığı gibi bu öznitelikleri kullanma.  
  
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
  
 `WsdlDocumentationAttribute` Uygulayan <xref:System.ServiceModel.Description.IContractBehavior> ve <xref:System.ServiceModel.Description.IOperationBehavior>, karşılık gelen öznitelik örnekleri eklenen <xref:System.ServiceModel.Description.ContractDescription> veya <xref:System.ServiceModel.Description.OperationDescription> hizmet açıldığında. İmplements özniteliği de <xref:System.ServiceModel.Description.IWsdlExportExtension>. Zaman <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%28System.ServiceModel.Description.WsdlExporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> çağrıldığında <xref:System.ServiceModel.Description.WsdlExporter> meta verileri dışarı aktarmak için kullanılır ve <xref:System.ServiceModel.Description.WsdlContractConversionContext> nesneleri dışarı aktarılan meta veri değişikliği etkinleştirme parametre olarak geçirilir hizmet açıklaması içerir.  
  
 Bu örnekte, dışarı aktarma bağlam nesnesi bağlı olup bağlı olarak bir <xref:System.ServiceModel.Description.ContractDescription> veya bir <xref:System.ServiceModel.Description.OperationDescription>, yorum metin özelliğini kullanarak özniteliğinden ayıklanmış ve aşağıdaki kodda gösterildiği gibi WSDL ek açıklama öğesine eklenir.  
  
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
  
 Bir işlem dışarı aktardıysanız, örnek yansıma herhangi almak için kullanır. `WsdlParamOrReturnDocumentationAttribute` parametreler ve dönüş değerleri için değerleri ve bunları bu işlem için WSDL ek açıklama öğeleri gibi ekler.  
  
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
  
 Örnek, ardından aşağıdaki yapılandırma dosyası kullanarak standart biçiminde meta verileri yayımlar.  
  
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
 Bu örnek Svcutil.exe kullanmaz. Sözleşme, dosya, daha sonra örnek gösterir şekilde özel WSDL içeri aktarma ve kod oluşturma, hizmet içinde generatedClient.cs çağrılabilir sağlanır. Bu örnek için aşağıdaki özel WSDL içeri Aktarıcı kullanmak için Svcutil.exe çalıştırın ve belirtin `/svcutilConfig` başvuran Bu örnekte kullanılan istemci yapılandırma dosyasının yolu verme seçeneğini `WsdlDocumentation.dll` kitaplığı. Yüklenecek `WsdlDocumentationImporter`, ancak Svuctil.exe bulmak ve yüklemek gereken `WsdlDocumentation.dll` kitaplığı, ya yolu genel derleme önbelleğinde kayıtlı veya Svcutil.exe ile aynı dizinde olduğu anlamına gelir. Bunun gibi bir temel örnek için kolay bir şey yapmak için Svcutil.exe ve istemci yapılandırma dosyasını aynı dizine kopyalayın olmaktır `WsdlDocumentation.dll` ve oradan çalıştırın.  
  
## <a name="the-custom-wsdl-importer"></a>Özel WSDL içeri Aktarıcı  
 Özel <xref:System.ServiceModel.Description.IWsdlImportExtension> nesne `WsdlDocumentationImporter` ayrıca uygulayan <xref:System.ServiceModel.Description.IContractBehavior> ve <xref:System.ServiceModel.Description.IOperationBehavior> için içeri aktarılan ServiceEndpoints eklenecek ve <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> ve <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> kod oluşturma değiştirmek için çağrılacak olduğunda sözleşme veya işlemi kod oluşturuluyor.  
  
 İlk olarak <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> örnek yöntemi, WSDL ek açıklama sözleşme veya işlem düzeyinde ve kendisini bir davranış yapıcısına içeri aktarılan ek açıklama metni geçirerek uygun kapsam olarak ekler olup olmadığını belirler.  
  
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
  
 Ardından, kodu oluşturulduğunda Sistem çağırır <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> ve <xref:System.ServiceModel.Description.IOperationContractGenerationExtension.GenerateOperation%28System.ServiceModel.Description.OperationContractGenerationContext%29> uygun bağlam bilgilerini geçirme yöntemleri. Örnek özel WSDL ek açıklamalar biçimlendirir ve bunları CodeDom yorum olarak ekler.  
  
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
  
 Özel içeri Aktarıcı belirtilen sonra WCF Meta veri sistemini özel içeri Aktarıcı hiçbir yükler <xref:System.ServiceModel.Description.WsdlImporter> bu amaç için oluşturulan. Bu örnekte <xref:System.ServiceModel.Description.MetadataExchangeClient> meta verileri indirilemedi <xref:System.ServiceModel.Description.WsdlImporter> düzgün bir şekilde yapılandırılmış bir örnek oluşturur, özel alma kullanarak meta verileri içeri aktarmak için ve <xref:System.ServiceModel.Description.ServiceContractGenerator> hem Visual Basic içinde değiştirilen sözleşme bilgileriniz derlemek için ve Visual Studio IntelliSense desteklemek için kullanılan veya XML belgeleme derlenmiş C# istemci kodu.  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1.  Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\WsdlDocumentation`  
  
## <a name="see-also"></a>Ayrıca Bkz.
