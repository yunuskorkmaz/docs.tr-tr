---
title: 'Nasıl yapılır: ServiceContractGenerator için Uzantı Yazma'
ms.date: 03/30/2017
ms.assetid: 876ca823-bd16-4bdf-9e0f-02092df90e51
ms.openlocfilehash: c9e10efccf0d51e6b78aace1296d227a78a9f91d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59340626"
---
# <a name="how-to-write-an-extension-for-the-servicecontractgenerator"></a>Nasıl yapılır: ServiceContractGenerator için Uzantı Yazma
Bu konu için bir uzantı yazma açıklar <xref:System.ServiceModel.Description.ServiceContractGenerator>. Bu uygulama tarafından yapılabilir <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> bir işlem davranışı arabirimi veya uygulama <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> arabirimdeki bir sözleşme davranışı. Bu konu nasıl uygulayacağınızı gösteren <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> arabirimdeki bir sözleşme davranışı.  
  
 <xref:System.ServiceModel.Description.ServiceContractGenerator> Hizmet sözleşmeleri, istemci türlerini ve istemci yapılandırmaları <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, ve <xref:System.ServiceModel.Channels.Binding> örnekleri. Genellikle, içeri aktardığınız <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, ve <xref:System.ServiceModel.Channels.Binding> örnekleri hizmet meta verileri ve hizmeti çağırmak için kod oluşturmak için bu örnekleri kullanın. Bu örnekte, bir <xref:System.ServiceModel.Description.IWsdlImportExtension> uygulama WSDL ek açıklamaları işlemek ve kod oluşturma uzantıları oluşturulan kod açıklamaları oluşturmak için içeri aktarılan anlaşmalar eklemek için kullanılır.  
  
### <a name="to-write-an-extension-for-the-servicecontractgenerator"></a>ServiceContractGenerator için uzantı yazma  
  
1. Uygulama <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>. Oluşturulan hizmet sözleşmesi değiştirmek için <xref:System.ServiceModel.Description.ServiceContractGenerationContext> örnek geçirildi <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> yöntemi.  
  
    ```  
    public void GenerateContract(ServiceContractGenerationContext context)  
    {  
        Console.WriteLine("In generate contract.");  
    context.ContractType.Comments.AddRange(Formatter.FormatComments(commentText));  
    }  
    ```  
  
2. Uygulama <xref:System.ServiceModel.Description.IWsdlImportExtension> aynı sınıfta. <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> Yöntemi, bir kod oluşturma uzantısı için içeri aktarılan ekleyerek belirli bir WSDL uzantısı (Bu durumda açıklamalarda WSDL) işleyebilir <xref:System.ServiceModel.Description.ContractDescription> örneği.  
  
    ```  
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
  
3. WSDL içeri Aktarıcı istemci yapılandırmanıza ekleyin.  
  
    ```xml  
    <metadata>  
      <wsdlImporters>  
        <extension type="Microsoft.WCF.Documentation.WsdlDocumentationImporter, WsdlDocumentation" />  
      </wsdlImporters>  
    </metadata>  
    ```  
  
4. İstemci kod içinde oluşturma bir `MetadataExchangeClient` ve çağrı `GetMetadata`.  
  
    ```  
    MetadataExchangeClient mexClient = new MetadataExchangeClient(metadataAddress);  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet metaDocs = mexClient.GetMetadata();  
    ```  
  
5. Oluşturma bir `WsdlImporter` ve çağrı `ImportAllContracts`.  
  
    ```  
    WsdlImporter importer = new WsdlImporter(metaDocs);            System.Collections.ObjectModel.Collection<ContractDescription> contracts = importer.ImportAllContracts();  
    ```  
  
6. Oluşturma bir `ServiceContractGenerator` ve çağrı `GenerateServiceContractType` her sözleşme için.  
  
    ```  
    ServiceContractGenerator generator = new ServiceContractGenerator();  
    foreach (ContractDescription contract in contracts)  
    {  
       generator.GenerateServiceContractType(contract);  
    }  
    if (generator.Errors.Count != 0)  
       throw new Exception("There were errors during code compilation.");  
    ```  
  
7. <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> Her sözleşme davranışı uygulayan verilen bir sözleşme için otomatik olarak çağrılır <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>. Bu yöntem daha sonra değiştirebilirsiniz <xref:System.ServiceModel.Description.ServiceContractGenerationContext> geçirildi. Bu örnekte açıklama eklenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veriler](../../../../docs/framework/wcf/feature-details/metadata.md)
- [Nasıl yapılır: Özel WSDL içeri aktarma](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)
