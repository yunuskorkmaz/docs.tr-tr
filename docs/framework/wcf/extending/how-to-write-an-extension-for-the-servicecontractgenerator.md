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
# <a name="how-to-write-an-extension-for-the-servicecontractgenerator"></a><span data-ttu-id="d1b02-102">Nasıl yapılır: ServiceContractGenerator için Uzantı Yazma</span><span class="sxs-lookup"><span data-stu-id="d1b02-102">How to: Write an Extension for the ServiceContractGenerator</span></span>
<span data-ttu-id="d1b02-103">Bu konu için bir uzantı yazma açıklar <xref:System.ServiceModel.Description.ServiceContractGenerator>.</span><span class="sxs-lookup"><span data-stu-id="d1b02-103">This topic describes how to write an extension for the <xref:System.ServiceModel.Description.ServiceContractGenerator>.</span></span> <span data-ttu-id="d1b02-104">Bu uygulama tarafından yapılabilir <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> bir işlem davranışı arabirimi veya uygulama <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> arabirimdeki bir sözleşme davranışı.</span><span class="sxs-lookup"><span data-stu-id="d1b02-104">This can be done by implementing the <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> interface on an operation behavior or implementing the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> interface on a contract behavior.</span></span> <span data-ttu-id="d1b02-105">Bu konu nasıl uygulayacağınızı gösteren <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> arabirimdeki bir sözleşme davranışı.</span><span class="sxs-lookup"><span data-stu-id="d1b02-105">This topic shows how to implement the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> interface on a contract behavior.</span></span>  
  
 <span data-ttu-id="d1b02-106"><xref:System.ServiceModel.Description.ServiceContractGenerator> Hizmet sözleşmeleri, istemci türlerini ve istemci yapılandırmaları <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, ve <xref:System.ServiceModel.Channels.Binding> örnekleri.</span><span class="sxs-lookup"><span data-stu-id="d1b02-106">The <xref:System.ServiceModel.Description.ServiceContractGenerator> generates service contracts, client types, and client configurations from <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, and <xref:System.ServiceModel.Channels.Binding> instances.</span></span> <span data-ttu-id="d1b02-107">Genellikle, içeri aktardığınız <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, ve <xref:System.ServiceModel.Channels.Binding> örnekleri hizmet meta verileri ve hizmeti çağırmak için kod oluşturmak için bu örnekleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="d1b02-107">Typically, you import <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, and <xref:System.ServiceModel.Channels.Binding> instances from service metadata and then use these instances to generate code to call the service.</span></span> <span data-ttu-id="d1b02-108">Bu örnekte, bir <xref:System.ServiceModel.Description.IWsdlImportExtension> uygulama WSDL ek açıklamaları işlemek ve kod oluşturma uzantıları oluşturulan kod açıklamaları oluşturmak için içeri aktarılan anlaşmalar eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d1b02-108">In this example, an <xref:System.ServiceModel.Description.IWsdlImportExtension> implementation is used to process WSDL annotations and then add code generation extensions to the imported contracts to generate comments on the generated code.</span></span>  
  
### <a name="to-write-an-extension-for-the-servicecontractgenerator"></a><span data-ttu-id="d1b02-109">ServiceContractGenerator için uzantı yazma</span><span class="sxs-lookup"><span data-stu-id="d1b02-109">To write an extension for the ServiceContractGenerator</span></span>  
  
1. <span data-ttu-id="d1b02-110">Uygulama <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>.</span><span class="sxs-lookup"><span data-stu-id="d1b02-110">Implement <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>.</span></span> <span data-ttu-id="d1b02-111">Oluşturulan hizmet sözleşmesi değiştirmek için <xref:System.ServiceModel.Description.ServiceContractGenerationContext> örnek geçirildi <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d1b02-111">To modify the generated service contract, use the <xref:System.ServiceModel.Description.ServiceContractGenerationContext> instance passed into the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> method.</span></span>  
  
    ```  
    public void GenerateContract(ServiceContractGenerationContext context)  
    {  
        Console.WriteLine("In generate contract.");  
    context.ContractType.Comments.AddRange(Formatter.FormatComments(commentText));  
    }  
    ```  
  
2. <span data-ttu-id="d1b02-112">Uygulama <xref:System.ServiceModel.Description.IWsdlImportExtension> aynı sınıfta.</span><span class="sxs-lookup"><span data-stu-id="d1b02-112">Implement <xref:System.ServiceModel.Description.IWsdlImportExtension> on the same class.</span></span> <span data-ttu-id="d1b02-113"><xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> Yöntemi, bir kod oluşturma uzantısı için içeri aktarılan ekleyerek belirli bir WSDL uzantısı (Bu durumda açıklamalarda WSDL) işleyebilir <xref:System.ServiceModel.Description.ContractDescription> örneği.</span><span class="sxs-lookup"><span data-stu-id="d1b02-113">The <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> method can process a specific WSDL extension (WSDL annotations in this case) by adding a code generation extension to the imported <xref:System.ServiceModel.Description.ContractDescription> instance.</span></span>  
  
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
  
3. <span data-ttu-id="d1b02-114">WSDL içeri Aktarıcı istemci yapılandırmanıza ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d1b02-114">Add the WSDL importer to your client configuration.</span></span>  
  
    ```xml  
    <metadata>  
      <wsdlImporters>  
        <extension type="Microsoft.WCF.Documentation.WsdlDocumentationImporter, WsdlDocumentation" />  
      </wsdlImporters>  
    </metadata>  
    ```  
  
4. <span data-ttu-id="d1b02-115">İstemci kod içinde oluşturma bir `MetadataExchangeClient` ve çağrı `GetMetadata`.</span><span class="sxs-lookup"><span data-stu-id="d1b02-115">In the client code, create a `MetadataExchangeClient` and call `GetMetadata`.</span></span>  
  
    ```  
    MetadataExchangeClient mexClient = new MetadataExchangeClient(metadataAddress);  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet metaDocs = mexClient.GetMetadata();  
    ```  
  
5. <span data-ttu-id="d1b02-116">Oluşturma bir `WsdlImporter` ve çağrı `ImportAllContracts`.</span><span class="sxs-lookup"><span data-stu-id="d1b02-116">Create a `WsdlImporter` and call `ImportAllContracts`.</span></span>  
  
    ```  
    WsdlImporter importer = new WsdlImporter(metaDocs);            System.Collections.ObjectModel.Collection<ContractDescription> contracts = importer.ImportAllContracts();  
    ```  
  
6. <span data-ttu-id="d1b02-117">Oluşturma bir `ServiceContractGenerator` ve çağrı `GenerateServiceContractType` her sözleşme için.</span><span class="sxs-lookup"><span data-stu-id="d1b02-117">Create a `ServiceContractGenerator` and call `GenerateServiceContractType` for each contract.</span></span>  
  
    ```  
    ServiceContractGenerator generator = new ServiceContractGenerator();  
    foreach (ContractDescription contract in contracts)  
    {  
       generator.GenerateServiceContractType(contract);  
    }  
    if (generator.Errors.Count != 0)  
       throw new Exception("There were errors during code compilation.");  
    ```  
  
7. <span data-ttu-id="d1b02-118"><xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> Her sözleşme davranışı uygulayan verilen bir sözleşme için otomatik olarak çağrılır <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>.</span><span class="sxs-lookup"><span data-stu-id="d1b02-118"><xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> is called automatically for each contract behavior on a given contract that implements <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>.</span></span> <span data-ttu-id="d1b02-119">Bu yöntem daha sonra değiştirebilirsiniz <xref:System.ServiceModel.Description.ServiceContractGenerationContext> geçirildi.</span><span class="sxs-lookup"><span data-stu-id="d1b02-119">This method can then modify the <xref:System.ServiceModel.Description.ServiceContractGenerationContext> passed in.</span></span> <span data-ttu-id="d1b02-120">Bu örnekte açıklama eklenir.</span><span class="sxs-lookup"><span data-stu-id="d1b02-120">In this example comments are added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1b02-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1b02-121">See also</span></span>

- [<span data-ttu-id="d1b02-122">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="d1b02-122">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)
- [<span data-ttu-id="d1b02-123">Nasıl yapılır: Özel WSDL içeri aktarma</span><span class="sxs-lookup"><span data-stu-id="d1b02-123">How to: Import Custom WSDL</span></span>](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)
