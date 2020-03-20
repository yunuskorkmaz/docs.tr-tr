---
title: Özel WSDL Yayımı
ms.date: 03/30/2017
ms.assetid: 3b3e8103-2c95-4db3-a05b-46aa8e9d4d29
ms.openlocfilehash: ae6d5fdf243d5000090e993bd3353c6180d0ccaa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145065"
---
# <a name="custom-wsdl-publication"></a>Özel WSDL Yayımı
Bu örnek nasıl gösteriş yapılacağını gösterir:  
  
- WSDL ek <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> açıklamaları olarak öznitelik özellikleri dışa aktarmak için özel bir öznitelik <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> bir uygulayın.  
  
- Özel <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> WSDL ek açıklamalarını almak için uygulayın.  
  
- İthal <xref:System.ServiceModel.Description.IOperationContractGenerationExtension?displayProperty=nameWithType> edilen sözleşme ve işlem için CodeDom'da yorum olarak içe aktarılan ek açıklamaları yazmak için, sırasıyla özel bir sözleşme davranışı ve özel bir işlem davranışı uygulayın. <xref:System.ServiceModel.Description.IServiceContractGenerationExtension?displayProperty=nameWithType>  
  
- Özel <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> WSDL içe aktarıcısını kullanarak WSDL'yi almak <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> için WSDL'yi ve WSDL ek açıklamalarını wsdl ek açıklamaları yla birlikte Windows Communication Foundation (WCF) istemci kodunu oluşturmak <xref:System.ServiceModel.Description.ServiceContractGenerator?displayProperty=nameWithType> için C# ve Visual Basic'teki ''' yorumlarını indirmek için kullanın.  
  
> [!NOTE]
> Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
## <a name="service"></a>Hizmet  
 Bu örnekteki hizmet iki özel öznitelikile işaretlenir. İlk, `WsdlDocumentationAttribute`, oluşturucu bir dize kabul eder ve kullanımını açıklayan bir dize ile bir sözleşme arabirimi veya işlem sağlamak için uygulanabilir. İkinci,, `WsdlParamOrReturnDocumentationAttribute`işlemde bu değerleri açıklamak için değerleri veya parametreleri döndürmek için uygulanabilir. Aşağıdaki örnek, bu öznitelikleri kullanılarak açıklanan bir hizmet sözleşmesi `ICalculator`gösterir.  
  
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
  
 Uygular `WsdlDocumentationAttribute` <xref:System.ServiceModel.Description.IContractBehavior> ve <xref:System.ServiceModel.Description.IOperationBehavior>, böylece öznitelik örnekleri ilgili <xref:System.ServiceModel.Description.ContractDescription> veya <xref:System.ServiceModel.Description.OperationDescription> hizmet açıldığında eklenir. Öznitelik de <xref:System.ServiceModel.Description.IWsdlExportExtension>uygular. Çağrıldığında, <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%28System.ServiceModel.Description.WsdlExporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> <xref:System.ServiceModel.Description.WsdlExporter> meta verileri dışa aktarmak için <xref:System.ServiceModel.Description.WsdlContractConversionContext> kullanılan ve hizmet açıklaması nesneleri içeren dışa aktarılan meta verilerin modifikasyonuna olanak tanıyan parametreler olarak geçirilir.  
  
 Bu örnekte, dışa aktarma bağlam nesnesinin <xref:System.ServiceModel.Description.OperationDescription>metin özelliği kullanılarak öznitelikten bir <xref:System.ServiceModel.Description.ContractDescription> yorum alınıp alınmadığına bağlı olarak aşağıdaki kodda gösterildiği gibi WSDL ek açıklama öğesine eklenir.  
  
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
  
 Bir işlem dışa aktarılıyorsa, örnek `WsdlParamOrReturnDocumentationAttribute` parametreler ve iade değerleri için herhangi bir değer elde etmek için yansımayı kullanır ve bunları aşağıdaki gibi bu işlem için WSDL ek açıklama öğelerine ekler.  
  
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
  
 Örnek daha sonra aşağıdaki yapılandırma dosyasını kullanarak meta verileri standart şekilde yayımlar.  
  
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
 Bu örnek Svcutil.exe kullanmaz. Sözleşme, örnek özel WSDL alma ve kod oluşturma yı gösterdikten sonra hizmetin çağrılabilmesi için generatedClient.cs dosyasında sağlanır. Bu örnek için aşağıdaki özel WSDL aktarıcısını kullanmak için, Svcutil.exe'yi çalıştırabilir ve `/svcutilConfig` bu örnekte kullanılan `WsdlDocumentation.dll` ve kitaplıkla başvuran istemci yapılandırma dosyasına yol vererek seçeneği belirtebilirsiniz. `WsdlDocumentationImporter`Ancak, Svuctil.exe'yi yüklemek için `WsdlDocumentation.dll` kitaplığı bulabilmesi ve yükleyebilmesi gerekir, bu da genel montaj önbelleğinde, yolda kayıtlı olduğu veya Svcutil.exe ile aynı dizinde olduğu anlamına gelir. Bu gibi temel bir örnek için, yapılacak en kolay şey Svcutil.exe ve istemci yapılandırma `WsdlDocumentation.dll` dosyası aynı dizin içine kopyalamak ve oradan çalıştırın.  
  
## <a name="the-custom-wsdl-importer"></a>Özel WSDL İthalatçı  
 Özel <xref:System.ServiceModel.Description.IWsdlImportExtension> nesne `WsdlDocumentationImporter` de <xref:System.ServiceModel.Description.IContractBehavior> uygular <xref:System.ServiceModel.Description.IOperationBehavior> ve içe aktarılan ServiceEndpoints <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> eklenecek ve sözleşme veya işlem kodu oluşturulurken kod oluşturma değiştirmek için çağrılacak.  
  
 İlk olarak, <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> yöntemde, örnek WSDL ek açıklama sözleşme veya işlem düzeyinde olup olmadığını belirler ve içe aktarılan ek açıklama metnini oluşturucuya geçirerek kendisini uygun kapsamda bir davranış olarak ekler.  
  
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
  
 Daha sonra, kod oluşturulduğunda, sistem <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> uygun <xref:System.ServiceModel.Description.IOperationContractGenerationExtension.GenerateOperation%28System.ServiceModel.Description.OperationContractGenerationContext%29> bağlam bilgilerini geçirerek, yöntemleri ve yöntemleri çağırır. Örnek, özel WSDL ek açıklamalarını biçimlendiriyor ve CodeDom'a yorum olarak ekler.  
  
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
  
## <a name="the-client-application"></a>İstemci Başvurusu  
 İstemci uygulaması, uygulama yapılandırma dosyasında belirterek özel WSDL içe aktarıcısını yükler.  
  
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
  
 Özel içe aktarıcı belirtildikten sonra, WCF meta veri sistemi <xref:System.ServiceModel.Description.WsdlImporter> özel içe aktarıcıyı bu amaç için oluşturulan herhangi bir aygıta yükler. Bu örnek <xref:System.ServiceModel.Description.MetadataExchangeClient> meta verileri indirmek için <xref:System.ServiceModel.Description.WsdlImporter> kullanır, örnek oluşturur özel içe aktarmacı kullanarak meta veri <xref:System.ServiceModel.Description.ServiceContractGenerator> almak için düzgün yapılandırılmış ve görsel temel ve C# istemci kodu hem De görsel studio intellisense desteklemek için kullanılabilir veya XML belgelerine derlenmiş değiştirilmiş sözleşme bilgilerini derlemek için.  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
3. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\WsdlDocumentation`  
