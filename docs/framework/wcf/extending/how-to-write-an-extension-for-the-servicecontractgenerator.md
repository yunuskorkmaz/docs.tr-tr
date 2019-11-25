---
title: 'Nasıl yapılır: ServiceContractGenerator için UzantıYazma'
ms.date: 03/30/2017
ms.assetid: 876ca823-bd16-4bdf-9e0f-02092df90e51
ms.openlocfilehash: 68b380a40448f21ba770aa47c7188b818fa8f9e7
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975872"
---
# <a name="how-to-write-an-extension-for-the-servicecontractgenerator"></a>Nasıl yapılır: ServiceContractGenerator için UzantıYazma
Bu konu, <xref:System.ServiceModel.Description.ServiceContractGenerator>için bir uzantının nasıl yazılacağını açıklar. Bu, bir işlem davranışındaki <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> arabirimini uygulayarak veya bir sözleşme davranışında <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> arabirimini uygulayarak yapılabilir. Bu konu, bir sözleşme davranışındaki <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> arabiriminin nasıl uygulanacağını gösterir.  
  
 <xref:System.ServiceModel.Description.ServiceContractGenerator>, <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>ve <xref:System.ServiceModel.Channels.Binding> örneklerinden hizmet sözleşmeleri, istemci türleri ve istemci yapılandırması oluşturur. Genellikle, hizmet meta verilerinden <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>ve <xref:System.ServiceModel.Channels.Binding> örnekleri içeri aktarıp ardından bu örnekleri kullanarak hizmeti çağıran kodu oluşturabilirsiniz. Bu örnekte, WSDL ek açıklamalarını işlemek için bir <xref:System.ServiceModel.Description.IWsdlImportExtension> uygulama kullanılır ve ardından oluşturulan koda yorum üretmek için, içeri aktarılan sözleşmelere kod oluşturma uzantıları eklenir.  
  
### <a name="to-write-an-extension-for-the-servicecontractgenerator"></a>ServiceContractGenerator için bir uzantı yazmak için  
  
1. <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>uygulayın. Oluşturulan hizmet sözleşmesini değiştirmek için <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> yöntemine geçirilen <xref:System.ServiceModel.Description.ServiceContractGenerationContext> örneğini kullanın.  
  
    ```csharp
    public void GenerateContract(ServiceContractGenerationContext context)  
    {  
        Console.WriteLine("In generate contract.");  
        context.ContractType.Comments.AddRange(Formatter.FormatComments(commentText));  
    }  
    ```  
  
2. Aynı sınıfta <xref:System.ServiceModel.Description.IWsdlImportExtension> uygulayın. <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> yöntemi, içeri aktarılan <xref:System.ServiceModel.Description.ContractDescription> örneğine bir kod oluşturma uzantısı ekleyerek belirli bir WSDL uzantısını işleyebilir (Bu durumda WSDL ek açıklamaları).  
  
    ```csharp
    public void ImportContract(WsdlImporter importer, WsdlContractConversionContext context)
    {
        // Contract documentation
        if (context.WsdlPortType.Documentation != null)
        {
            context.Contract.Behaviors.Add(new WsdlDocumentationImporter(context.WsdlPortType.Documentation));
        }
        // Operation documentation
        foreach (Operation operation in context.WsdlPortType.Operations)
        {
            if (operation.Documentation != null)
            {
                OperationDescription operationDescription = context.Contract.Operations.Find(operation.Name);
                if (operationDescription != null)
                {
                    operationDescription.Behaviors.Add(new WsdlDocumentationImporter(operation.Documentation));
                }
            }
        }
    }
    public void BeforeImport(ServiceDescriptionCollection wsdlDocuments, XmlSchemaSet xmlSchemas, ICollection<XmlElement> policy)
    {
        Console.WriteLine("BeforeImport called.");
    }

    public void ImportEndpoint(WsdlImporter importer, WsdlEndpointConversionContext context)
    {
        Console.WriteLine("ImportEndpoint called.");
    }
    ```  
  
3. İstemci yapılandırmanıza WSDL İçeri Aktarıcı ekleyin.  
  
    ```xml  
    <metadata>  
      <wsdlImporters>  
        <extension type="Microsoft.WCF.Documentation.WsdlDocumentationImporter, WsdlDocumentation" />  
      </wsdlImporters>  
    </metadata>  
    ```  
  
4. İstemci kodunda bir `MetadataExchangeClient` oluşturun ve `GetMetadata`çağırın.  
  
    ```csharp
    var mexClient = new MetadataExchangeClient(metadataAddress);  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet metaDocs = mexClient.GetMetadata();  
    ```  
  
5. `WsdlImporter` oluşturun ve `ImportAllContracts`çağırın.  
  
    ```csharp
    var importer = new WsdlImporter(metaDocs);
    System.Collections.ObjectModel.Collection<ContractDescription> contracts = importer.ImportAllContracts();  
    ```  
  
6. Her sözleşme için bir `ServiceContractGenerator` oluşturun ve `GenerateServiceContractType` çağırın.  
  
    ```csharp
    var generator = new ServiceContractGenerator();  
    foreach (ContractDescription contract in contracts)  
    {  
       generator.GenerateServiceContractType(contract);  
    }  
    if (generator.Errors.Count != 0)  
       throw new Exception("There were errors during code compilation.");  
    ```  
  
7. <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29>, <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>uygulayan belirli bir sözleşmede her bir sözleşme davranışı için otomatik olarak çağrılır. Bu yöntem daha sonra geçirilen <xref:System.ServiceModel.Description.ServiceContractGenerationContext> değiştirebilir. Bu örnekte, açıklamalar eklenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veriler](../feature-details/metadata.md)
- [Nasıl yapılır: Özel WSDL İçe Aktarma](how-to-import-custom-wsdl.md)
