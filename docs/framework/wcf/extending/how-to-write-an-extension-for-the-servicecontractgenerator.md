---
title: "Nasıl yapılır: ServiceContractGenerator için UzantıYazma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 876ca823-bd16-4bdf-9e0f-02092df90e51
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e40ea594c7743dfec06876515a1165da1a16d4e5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-write-an-extension-for-the-servicecontractgenerator"></a>Nasıl yapılır: ServiceContractGenerator için UzantıYazma
Bu konu için uzantıyazma açıklar <xref:System.ServiceModel.Description.ServiceContractGenerator>. Bu uygulama tarafından yapılabilir <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> arabirim üzerinde bir işlemi davranışı veya uygulama <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> sözleşme davranışına arabirimi. Bu konuda nasıl uygulandığını gösterir <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> sözleşme davranışına arabirimi.  
  
 <xref:System.ServiceModel.Description.ServiceContractGenerator> Hizmet sözleşmelerini, istemci türlerini ve istemci yapılandırmalardan üretir <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, ve <xref:System.ServiceModel.Channels.Binding> örnekleri. Genellikle, içeri aktardığınız <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, ve <xref:System.ServiceModel.Channels.Binding> örnekleri hizmeti meta verileri ve bu örnekleri hizmeti çağırmak için kodu oluşturmak için kullanın. Bu örnekte, bir <xref:System.ServiceModel.Description.IWsdlImportExtension> uygulaması WSDL ek açıklamaları işlemek ve oluşturulan kodu açıklamalarını oluşturmak için içe aktarılan sözleşmeleri kod oluşturma uzantıları eklemek için kullanılır.  
  
### <a name="to-write-an-extension-for-the-servicecontractgenerator"></a>ServiceContractGenerator için uzantıyazma için  
  
1.  Uygulama <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>. Oluşturulan hizmet sözleşmesi değiştirmek için <xref:System.ServiceModel.Description.ServiceContractGenerationContext> örnek geçirildi <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> yöntemi.  
  
    ```  
    public void GenerateContract(ServiceContractGenerationContext context)  
    {  
        Console.WriteLine("In generate contract.");  
    context.ContractType.Comments.AddRange(Formatter.FormatComments(commentText));  
    }  
    ```  
  
2.  Uygulama <xref:System.ServiceModel.Description.IWsdlImportExtension> aynı sınıfta. <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> Yöntemi, belirli bir WSDL uzantısı (Bu durumda ek açıklamalar WSDL) bir kod oluşturma uzantısı alınan ekleyerek işlenebilecek <xref:System.ServiceModel.Description.ContractDescription> örneği.  
  
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
  
3.  WSDL alma istemci yapılandırmanıza ekleyebilirsiniz.  
  
    ```xml  
    <metadata>  
      <wsdlImporters>  
        <extension type="Microsoft.WCF.Documentation.WsdlDocumentationImporter, WsdlDocumentation" />  
      </wsdlImporters>  
    </metadata>  
    ```  
  
4.  İstemci kodu oluşturmak bir `MetadataExchangeClient` ve arama `GetMetadata`.  
  
    ```  
    MetadataExchangeClient mexClient = new MetadataExchangeClient(metadataAddress);  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet metaDocs = mexClient.GetMetadata();  
    ```  
  
5.  Oluşturma bir `WsdlImporter` ve arama `ImportAllContracts`.  
  
    ```  
    WsdlImporter importer = new WsdlImporter(metaDocs);            System.Collections.ObjectModel.Collection<ContractDescription> contracts = importer.ImportAllContracts();  
    ```  
  
6.  Oluşturma bir `ServiceContractGenerator` ve arama `GenerateServiceContractType` her sözleşme için.  
  
    ```  
    ServiceContractGenerator generator = new ServiceContractGenerator();  
    foreach (ContractDescription contract in contracts)  
    {  
       generator.GenerateServiceContractType(contract);  
    }  
    if (generator.Errors.Count != 0)  
       throw new Exception("There were errors during code compilation.");  
    ```  
  
7.  <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29>Her sözleşme davranışı uygulayan belirli bir sözleşme için otomatik olarak adlandırılan <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>. Bu yöntem daha sonra değiştirebilirsiniz <xref:System.ServiceModel.Description.ServiceContractGenerationContext> geçirildi. Bu örnekte açıklamaları eklenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta veriler](../../../../docs/framework/wcf/feature-details/metadata.md)  
 [Nasıl yapılır: özel WSDL içe aktarma](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)
