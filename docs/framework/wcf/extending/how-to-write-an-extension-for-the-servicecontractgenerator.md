---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: ServiceContractGenerator için uzantı yazma'
title: 'Nasıl yapılır: ServiceContractGenerator için Uzantı Yazma'
ms.date: 03/30/2017
ms.assetid: 876ca823-bd16-4bdf-9e0f-02092df90e51
ms.openlocfilehash: 29d6d65cc3f9d29009f72b9a0c81b6cb1f472ac9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99644209"
---
# <a name="how-to-write-an-extension-for-the-servicecontractgenerator"></a>Nasıl yapılır: ServiceContractGenerator için Uzantı Yazma

Bu konuda, için bir uzantısının nasıl yazılacağı açıklanmaktadır <xref:System.ServiceModel.Description.ServiceContractGenerator> . Bu <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> işlem, arabirimi bir işlem davranışına uygulayarak veya <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> arabirimi bir sözleşme davranışına uygulayarak yapılabilir. Bu konu başlığı altında, <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> arabirimin bir sözleşme davranışında nasıl uygulanacağı gösterilmektedir.  
  
 , <xref:System.ServiceModel.Description.ServiceContractGenerator> Ve örneklerinden hizmet sözleşmeleri, istemci türleri ve istemci yapılandırması oluşturur <xref:System.ServiceModel.Description.ServiceEndpoint> <xref:System.ServiceModel.Description.ContractDescription> <xref:System.ServiceModel.Channels.Binding> . Genellikle,, <xref:System.ServiceModel.Description.ServiceEndpoint> <xref:System.ServiceModel.Description.ContractDescription> ve <xref:System.ServiceModel.Channels.Binding> örneklerini hizmet meta verilerinden içeri aktarır ve ardından hizmeti çağırmak üzere kod oluşturmak için bu örnekleri kullanın. Bu örnekte, <xref:System.ServiceModel.Description.IWsdlImportExtension> WSDL ek açıklamalarını işlemek için bir uygulama kullanılır ve ardından oluşturulan koda yorum üretmek için, içeri aktarılan sözleşmelere kod oluşturma uzantıları eklenir.  
  
### <a name="to-write-an-extension-for-the-servicecontractgenerator"></a>ServiceContractGenerator için bir uzantı yazmak için  
  
1. Uygulayın <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> . Oluşturulan hizmet sözleşmesini değiştirmek için <xref:System.ServiceModel.Description.ServiceContractGenerationContext> metoduna geçirilen örneği kullanın <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> .  
  
    ```csharp
    public void GenerateContract(ServiceContractGenerationContext context)  
    {  
        Console.WriteLine("In generate contract.");  
        context.ContractType.Comments.AddRange(Formatter.FormatComments(commentText));  
    }  
    ```  
  
2. <xref:System.ServiceModel.Description.IWsdlImportExtension>Aynı sınıfa uygulayın. <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29>Yöntemi, içeri aktarılan örneğe bir kod oluşturma uzantısı ekleyerek belirli BIR WSDL uzantısını işleyebilir (Bu durumda WSDL ek açıklamaları) <xref:System.ServiceModel.Description.ContractDescription> .  
  
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
  
4. İstemci kodunda bir `MetadataExchangeClient` ve çağrısı oluşturun `GetMetadata` .  
  
    ```csharp
    var mexClient = new MetadataExchangeClient(metadataAddress);  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet metaDocs = mexClient.GetMetadata();  
    ```  
  
5. `WsdlImporter`Ve çağrısı oluşturun `ImportAllContracts` .  
  
    ```csharp
    var importer = new WsdlImporter(metaDocs);
    System.Collections.ObjectModel.Collection<ContractDescription> contracts = importer.ImportAllContracts();  
    ```  
  
6. `ServiceContractGenerator`Her sözleşme için bir ve çağrısı oluşturun `GenerateServiceContractType` .  
  
    ```csharp
    var generator = new ServiceContractGenerator();  
    foreach (ContractDescription contract in contracts)  
    {  
       generator.GenerateServiceContractType(contract);  
    }  
    if (generator.Errors.Count != 0)  
       throw new Exception("There were errors during code compilation.");  
    ```  
  
7. <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> , uygulayan belirli bir sözleşmede her bir sözleşme davranışı için otomatik olarak çağrılır <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> . Bu yöntem daha sonra <xref:System.ServiceModel.Description.ServiceContractGenerationContext> geçirilmiş ' i değiştirebilir. Bu örnekte, açıklamalar eklenir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta veri](../feature-details/metadata.md)
- [Nasıl yapılır: Özel WSDL İçeri Aktarma](how-to-import-custom-wsdl.md)
