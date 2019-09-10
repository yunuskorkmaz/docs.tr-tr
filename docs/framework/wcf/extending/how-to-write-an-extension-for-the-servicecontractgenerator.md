---
title: 'Nasıl yapılır: ServiceContractGenerator için Uzantı Yazma'
ms.date: 03/30/2017
ms.assetid: 876ca823-bd16-4bdf-9e0f-02092df90e51
ms.openlocfilehash: af23babd9255c45b9fa89b5c167de6960f0f690e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855727"
---
# <a name="how-to-write-an-extension-for-the-servicecontractgenerator"></a>Nasıl yapılır: ServiceContractGenerator için Uzantı Yazma
Bu konuda, <xref:System.ServiceModel.Description.ServiceContractGenerator>için bir uzantısının nasıl yazılacağı açıklanmaktadır. Bu işlem, <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> arabirimi bir işlem davranışına uygulayarak veya <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> arabirimi bir sözleşme davranışına uygulayarak yapılabilir. Bu konu başlığı altında, <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> arabirimin bir sözleşme davranışında nasıl uygulanacağı gösterilmektedir.  
  
 , Ve <xref:System.ServiceModel.Description.ServiceEndpoint> <xref:System.ServiceModel.Description.ContractDescription> <xref:System.ServiceModel.Description.ServiceContractGenerator>örneklerindenhizmetsözleşmeleri, istemcitürlerive<xref:System.ServiceModel.Channels.Binding> istemci yapılandırması oluşturur. Genellikle,, ve <xref:System.ServiceModel.Description.ServiceEndpoint> <xref:System.ServiceModel.Channels.Binding> örneklerini <xref:System.ServiceModel.Description.ContractDescription>hizmet meta verilerinden içeri aktarır ve ardından hizmeti çağırmak üzere kod oluşturmak için bu örnekleri kullanın. Bu örnekte, WSDL ek <xref:System.ServiceModel.Description.IWsdlImportExtension> açıklamalarını işlemek için bir uygulama kullanılır ve ardından oluşturulan koda yorum üretmek için, içeri aktarılan sözleşmelere kod oluşturma uzantıları eklenir.  
  
### <a name="to-write-an-extension-for-the-servicecontractgenerator"></a>ServiceContractGenerator için bir uzantı yazmak için  
  
1. Uygulayın <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>. Oluşturulan hizmet sözleşmesini değiştirmek için <xref:System.ServiceModel.Description.ServiceContractGenerationContext> <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> metoduna geçirilen örneği kullanın.  
  
    ```csharp
    public void GenerateContract(ServiceContractGenerationContext context)  
    {  
        Console.WriteLine("In generate contract.");  
    context.ContractType.Comments.AddRange(Formatter.FormatComments(commentText));  
    }  
    ```  
  
2. Aynı <xref:System.ServiceModel.Description.IWsdlImportExtension> sınıfa uygulayın. Yöntemi <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> , içeri aktarılan <xref:System.ServiceModel.Description.ContractDescription> örneğe bir kod oluşturma uzantısı ekleyerek belirli bir wsdl uzantısını işleyebilir (Bu durumda WSDL ek açıklamaları).  
  
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
  
4. İstemci kodunda bir `MetadataExchangeClient` ve çağrısı `GetMetadata`oluşturun.  
  
    ```csharp  
    MetadataExchangeClient mexClient = new MetadataExchangeClient(metadataAddress);  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet metaDocs = mexClient.GetMetadata();  
    ```  
  
5. `WsdlImporter` Ve çağrısı`ImportAllContracts`oluşturun.  
  
    ```csharp  
    WsdlImporter importer = new WsdlImporter(metaDocs);            System.Collections.ObjectModel.Collection<ContractDescription> contracts = importer.ImportAllContracts();  
    ```  
  
6. Her sözleşme `ServiceContractGenerator` için bir `GenerateServiceContractType` ve çağrısı oluşturun.  
  
    ```csharp  
    ServiceContractGenerator generator = new ServiceContractGenerator();  
    foreach (ContractDescription contract in contracts)  
    {  
       generator.GenerateServiceContractType(contract);  
    }  
    if (generator.Errors.Count != 0)  
       throw new Exception("There were errors during code compilation.");  
    ```  
  
7. <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29>, uygulayan <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>belirli bir sözleşmede her bir sözleşme davranışı için otomatik olarak çağrılır. Bu yöntem daha sonra <xref:System.ServiceModel.Description.ServiceContractGenerationContext> geçirilmiş ' i değiştirebilir. Bu örnekte, açıklamalar eklenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veriler](../feature-details/metadata.md)
- [Nasıl yapılır: Özel WSDL 'yi içeri aktar](how-to-import-custom-wsdl.md)
