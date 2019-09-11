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
# <a name="how-to-write-an-extension-for-the-servicecontractgenerator"></a><span data-ttu-id="8cec6-102">Nasıl yapılır: ServiceContractGenerator için Uzantı Yazma</span><span class="sxs-lookup"><span data-stu-id="8cec6-102">How to: Write an Extension for the ServiceContractGenerator</span></span>
<span data-ttu-id="8cec6-103">Bu konuda, <xref:System.ServiceModel.Description.ServiceContractGenerator>için bir uzantısının nasıl yazılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8cec6-103">This topic describes how to write an extension for the <xref:System.ServiceModel.Description.ServiceContractGenerator>.</span></span> <span data-ttu-id="8cec6-104">Bu işlem, <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> arabirimi bir işlem davranışına uygulayarak veya <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> arabirimi bir sözleşme davranışına uygulayarak yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="8cec6-104">This can be done by implementing the <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> interface on an operation behavior or implementing the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> interface on a contract behavior.</span></span> <span data-ttu-id="8cec6-105">Bu konu başlığı altında, <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> arabirimin bir sözleşme davranışında nasıl uygulanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8cec6-105">This topic shows how to implement the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> interface on a contract behavior.</span></span>  
  
 <span data-ttu-id="8cec6-106">, Ve <xref:System.ServiceModel.Description.ServiceEndpoint> <xref:System.ServiceModel.Description.ContractDescription> <xref:System.ServiceModel.Description.ServiceContractGenerator>örneklerindenhizmetsözleşmeleri, istemcitürlerive<xref:System.ServiceModel.Channels.Binding> istemci yapılandırması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8cec6-106">The <xref:System.ServiceModel.Description.ServiceContractGenerator> generates service contracts, client types, and client configurations from <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, and <xref:System.ServiceModel.Channels.Binding> instances.</span></span> <span data-ttu-id="8cec6-107">Genellikle,, ve <xref:System.ServiceModel.Description.ServiceEndpoint> <xref:System.ServiceModel.Channels.Binding> örneklerini <xref:System.ServiceModel.Description.ContractDescription>hizmet meta verilerinden içeri aktarır ve ardından hizmeti çağırmak üzere kod oluşturmak için bu örnekleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="8cec6-107">Typically, you import <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, and <xref:System.ServiceModel.Channels.Binding> instances from service metadata and then use these instances to generate code to call the service.</span></span> <span data-ttu-id="8cec6-108">Bu örnekte, WSDL ek <xref:System.ServiceModel.Description.IWsdlImportExtension> açıklamalarını işlemek için bir uygulama kullanılır ve ardından oluşturulan koda yorum üretmek için, içeri aktarılan sözleşmelere kod oluşturma uzantıları eklenir.</span><span class="sxs-lookup"><span data-stu-id="8cec6-108">In this example, an <xref:System.ServiceModel.Description.IWsdlImportExtension> implementation is used to process WSDL annotations and then add code generation extensions to the imported contracts to generate comments on the generated code.</span></span>  
  
### <a name="to-write-an-extension-for-the-servicecontractgenerator"></a><span data-ttu-id="8cec6-109">ServiceContractGenerator için bir uzantı yazmak için</span><span class="sxs-lookup"><span data-stu-id="8cec6-109">To write an extension for the ServiceContractGenerator</span></span>  
  
1. <span data-ttu-id="8cec6-110">Uygulayın <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>.</span><span class="sxs-lookup"><span data-stu-id="8cec6-110">Implement <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>.</span></span> <span data-ttu-id="8cec6-111">Oluşturulan hizmet sözleşmesini değiştirmek için <xref:System.ServiceModel.Description.ServiceContractGenerationContext> <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> metoduna geçirilen örneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="8cec6-111">To modify the generated service contract, use the <xref:System.ServiceModel.Description.ServiceContractGenerationContext> instance passed into the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> method.</span></span>  
  
    ```csharp
    public void GenerateContract(ServiceContractGenerationContext context)  
    {  
        Console.WriteLine("In generate contract.");  
    context.ContractType.Comments.AddRange(Formatter.FormatComments(commentText));  
    }  
    ```  
  
2. <span data-ttu-id="8cec6-112">Aynı <xref:System.ServiceModel.Description.IWsdlImportExtension> sınıfa uygulayın.</span><span class="sxs-lookup"><span data-stu-id="8cec6-112">Implement <xref:System.ServiceModel.Description.IWsdlImportExtension> on the same class.</span></span> <span data-ttu-id="8cec6-113">Yöntemi <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> , içeri aktarılan <xref:System.ServiceModel.Description.ContractDescription> örneğe bir kod oluşturma uzantısı ekleyerek belirli bir wsdl uzantısını işleyebilir (Bu durumda WSDL ek açıklamaları).</span><span class="sxs-lookup"><span data-stu-id="8cec6-113">The <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> method can process a specific WSDL extension (WSDL annotations in this case) by adding a code generation extension to the imported <xref:System.ServiceModel.Description.ContractDescription> instance.</span></span>  
  
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
  
3. <span data-ttu-id="8cec6-114">İstemci yapılandırmanıza WSDL İçeri Aktarıcı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8cec6-114">Add the WSDL importer to your client configuration.</span></span>  
  
    ```xml  
    <metadata>  
      <wsdlImporters>  
        <extension type="Microsoft.WCF.Documentation.WsdlDocumentationImporter, WsdlDocumentation" />  
      </wsdlImporters>  
    </metadata>  
    ```  
  
4. <span data-ttu-id="8cec6-115">İstemci kodunda bir `MetadataExchangeClient` ve çağrısı `GetMetadata`oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8cec6-115">In the client code, create a `MetadataExchangeClient` and call `GetMetadata`.</span></span>  
  
    ```csharp  
    MetadataExchangeClient mexClient = new MetadataExchangeClient(metadataAddress);  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet metaDocs = mexClient.GetMetadata();  
    ```  
  
5. <span data-ttu-id="8cec6-116">`WsdlImporter` Ve çağrısı`ImportAllContracts`oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8cec6-116">Create a `WsdlImporter` and call `ImportAllContracts`.</span></span>  
  
    ```csharp  
    WsdlImporter importer = new WsdlImporter(metaDocs);            System.Collections.ObjectModel.Collection<ContractDescription> contracts = importer.ImportAllContracts();  
    ```  
  
6. <span data-ttu-id="8cec6-117">Her sözleşme `ServiceContractGenerator` için bir `GenerateServiceContractType` ve çağrısı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8cec6-117">Create a `ServiceContractGenerator` and call `GenerateServiceContractType` for each contract.</span></span>  
  
    ```csharp  
    ServiceContractGenerator generator = new ServiceContractGenerator();  
    foreach (ContractDescription contract in contracts)  
    {  
       generator.GenerateServiceContractType(contract);  
    }  
    if (generator.Errors.Count != 0)  
       throw new Exception("There were errors during code compilation.");  
    ```  
  
7. <span data-ttu-id="8cec6-118"><xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29>, uygulayan <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>belirli bir sözleşmede her bir sözleşme davranışı için otomatik olarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="8cec6-118"><xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> is called automatically for each contract behavior on a given contract that implements <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>.</span></span> <span data-ttu-id="8cec6-119">Bu yöntem daha sonra <xref:System.ServiceModel.Description.ServiceContractGenerationContext> geçirilmiş ' i değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="8cec6-119">This method can then modify the <xref:System.ServiceModel.Description.ServiceContractGenerationContext> passed in.</span></span> <span data-ttu-id="8cec6-120">Bu örnekte, açıklamalar eklenir.</span><span class="sxs-lookup"><span data-stu-id="8cec6-120">In this example comments are added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cec6-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8cec6-121">See also</span></span>

- [<span data-ttu-id="8cec6-122">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="8cec6-122">Metadata</span></span>](../feature-details/metadata.md)
- [<span data-ttu-id="8cec6-123">Nasıl yapılır: Özel WSDL 'yi içeri aktar</span><span class="sxs-lookup"><span data-stu-id="8cec6-123">How to: Import Custom WSDL</span></span>](how-to-import-custom-wsdl.md)
