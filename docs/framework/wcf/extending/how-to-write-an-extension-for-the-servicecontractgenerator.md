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
# <a name="how-to-write-an-extension-for-the-servicecontractgenerator"></a><span data-ttu-id="055a2-102">Nasıl yapılır: ServiceContractGenerator için UzantıYazma</span><span class="sxs-lookup"><span data-stu-id="055a2-102">How to: Write an Extension for the ServiceContractGenerator</span></span>
<span data-ttu-id="055a2-103">Bu konu, <xref:System.ServiceModel.Description.ServiceContractGenerator>için bir uzantının nasıl yazılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="055a2-103">This topic describes how to write an extension for the <xref:System.ServiceModel.Description.ServiceContractGenerator>.</span></span> <span data-ttu-id="055a2-104">Bu, bir işlem davranışındaki <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> arabirimini uygulayarak veya bir sözleşme davranışında <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> arabirimini uygulayarak yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="055a2-104">This can be done by implementing the <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> interface on an operation behavior or implementing the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> interface on a contract behavior.</span></span> <span data-ttu-id="055a2-105">Bu konu, bir sözleşme davranışındaki <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> arabiriminin nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="055a2-105">This topic shows how to implement the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> interface on a contract behavior.</span></span>  
  
 <span data-ttu-id="055a2-106"><xref:System.ServiceModel.Description.ServiceContractGenerator>, <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>ve <xref:System.ServiceModel.Channels.Binding> örneklerinden hizmet sözleşmeleri, istemci türleri ve istemci yapılandırması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="055a2-106">The <xref:System.ServiceModel.Description.ServiceContractGenerator> generates service contracts, client types, and client configurations from <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, and <xref:System.ServiceModel.Channels.Binding> instances.</span></span> <span data-ttu-id="055a2-107">Genellikle, hizmet meta verilerinden <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>ve <xref:System.ServiceModel.Channels.Binding> örnekleri içeri aktarıp ardından bu örnekleri kullanarak hizmeti çağıran kodu oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="055a2-107">Typically, you import <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, and <xref:System.ServiceModel.Channels.Binding> instances from service metadata and then use these instances to generate code to call the service.</span></span> <span data-ttu-id="055a2-108">Bu örnekte, WSDL ek açıklamalarını işlemek için bir <xref:System.ServiceModel.Description.IWsdlImportExtension> uygulama kullanılır ve ardından oluşturulan koda yorum üretmek için, içeri aktarılan sözleşmelere kod oluşturma uzantıları eklenir.</span><span class="sxs-lookup"><span data-stu-id="055a2-108">In this example, an <xref:System.ServiceModel.Description.IWsdlImportExtension> implementation is used to process WSDL annotations and then add code generation extensions to the imported contracts to generate comments on the generated code.</span></span>  
  
### <a name="to-write-an-extension-for-the-servicecontractgenerator"></a><span data-ttu-id="055a2-109">ServiceContractGenerator için bir uzantı yazmak için</span><span class="sxs-lookup"><span data-stu-id="055a2-109">To write an extension for the ServiceContractGenerator</span></span>  
  
1. <span data-ttu-id="055a2-110"><xref:System.ServiceModel.Description.IServiceContractGenerationExtension>uygulayın.</span><span class="sxs-lookup"><span data-stu-id="055a2-110">Implement <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>.</span></span> <span data-ttu-id="055a2-111">Oluşturulan hizmet sözleşmesini değiştirmek için <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> yöntemine geçirilen <xref:System.ServiceModel.Description.ServiceContractGenerationContext> örneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="055a2-111">To modify the generated service contract, use the <xref:System.ServiceModel.Description.ServiceContractGenerationContext> instance passed into the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> method.</span></span>  
  
    ```csharp
    public void GenerateContract(ServiceContractGenerationContext context)  
    {  
        Console.WriteLine("In generate contract.");  
        context.ContractType.Comments.AddRange(Formatter.FormatComments(commentText));  
    }  
    ```  
  
2. <span data-ttu-id="055a2-112">Aynı sınıfta <xref:System.ServiceModel.Description.IWsdlImportExtension> uygulayın.</span><span class="sxs-lookup"><span data-stu-id="055a2-112">Implement <xref:System.ServiceModel.Description.IWsdlImportExtension> on the same class.</span></span> <span data-ttu-id="055a2-113"><xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> yöntemi, içeri aktarılan <xref:System.ServiceModel.Description.ContractDescription> örneğine bir kod oluşturma uzantısı ekleyerek belirli bir WSDL uzantısını işleyebilir (Bu durumda WSDL ek açıklamaları).</span><span class="sxs-lookup"><span data-stu-id="055a2-113">The <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> method can process a specific WSDL extension (WSDL annotations in this case) by adding a code generation extension to the imported <xref:System.ServiceModel.Description.ContractDescription> instance.</span></span>  
  
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
  
3. <span data-ttu-id="055a2-114">İstemci yapılandırmanıza WSDL İçeri Aktarıcı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="055a2-114">Add the WSDL importer to your client configuration.</span></span>  
  
    ```xml  
    <metadata>  
      <wsdlImporters>  
        <extension type="Microsoft.WCF.Documentation.WsdlDocumentationImporter, WsdlDocumentation" />  
      </wsdlImporters>  
    </metadata>  
    ```  
  
4. <span data-ttu-id="055a2-115">İstemci kodunda bir `MetadataExchangeClient` oluşturun ve `GetMetadata`çağırın.</span><span class="sxs-lookup"><span data-stu-id="055a2-115">In the client code, create a `MetadataExchangeClient` and call `GetMetadata`.</span></span>  
  
    ```csharp
    var mexClient = new MetadataExchangeClient(metadataAddress);  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet metaDocs = mexClient.GetMetadata();  
    ```  
  
5. <span data-ttu-id="055a2-116">`WsdlImporter` oluşturun ve `ImportAllContracts`çağırın.</span><span class="sxs-lookup"><span data-stu-id="055a2-116">Create a `WsdlImporter` and call `ImportAllContracts`.</span></span>  
  
    ```csharp
    var importer = new WsdlImporter(metaDocs);
    System.Collections.ObjectModel.Collection<ContractDescription> contracts = importer.ImportAllContracts();  
    ```  
  
6. <span data-ttu-id="055a2-117">Her sözleşme için bir `ServiceContractGenerator` oluşturun ve `GenerateServiceContractType` çağırın.</span><span class="sxs-lookup"><span data-stu-id="055a2-117">Create a `ServiceContractGenerator` and call `GenerateServiceContractType` for each contract.</span></span>  
  
    ```csharp
    var generator = new ServiceContractGenerator();  
    foreach (ContractDescription contract in contracts)  
    {  
       generator.GenerateServiceContractType(contract);  
    }  
    if (generator.Errors.Count != 0)  
       throw new Exception("There were errors during code compilation.");  
    ```  
  
7. <span data-ttu-id="055a2-118"><xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29>, <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>uygulayan belirli bir sözleşmede her bir sözleşme davranışı için otomatik olarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="055a2-118"><xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> is called automatically for each contract behavior on a given contract that implements <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>.</span></span> <span data-ttu-id="055a2-119">Bu yöntem daha sonra geçirilen <xref:System.ServiceModel.Description.ServiceContractGenerationContext> değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="055a2-119">This method can then modify the <xref:System.ServiceModel.Description.ServiceContractGenerationContext> passed in.</span></span> <span data-ttu-id="055a2-120">Bu örnekte, açıklamalar eklenir.</span><span class="sxs-lookup"><span data-stu-id="055a2-120">In this example comments are added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="055a2-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="055a2-121">See also</span></span>

- [<span data-ttu-id="055a2-122">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="055a2-122">Metadata</span></span>](../feature-details/metadata.md)
- [<span data-ttu-id="055a2-123">Nasıl yapılır: Özel WSDL İçe Aktarma</span><span class="sxs-lookup"><span data-stu-id="055a2-123">How to: Import Custom WSDL</span></span>](how-to-import-custom-wsdl.md)
