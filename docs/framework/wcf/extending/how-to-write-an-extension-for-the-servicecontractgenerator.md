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
# <a name="how-to-write-an-extension-for-the-servicecontractgenerator"></a><span data-ttu-id="86c2b-102">Nasıl yapılır: ServiceContractGenerator için UzantıYazma</span><span class="sxs-lookup"><span data-stu-id="86c2b-102">How to: Write an Extension for the ServiceContractGenerator</span></span>
<span data-ttu-id="86c2b-103">Bu konu için uzantıyazma açıklar <xref:System.ServiceModel.Description.ServiceContractGenerator>.</span><span class="sxs-lookup"><span data-stu-id="86c2b-103">This topic describes how to write an extension for the <xref:System.ServiceModel.Description.ServiceContractGenerator>.</span></span> <span data-ttu-id="86c2b-104">Bu uygulama tarafından yapılabilir <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> arabirim üzerinde bir işlemi davranışı veya uygulama <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> sözleşme davranışına arabirimi.</span><span class="sxs-lookup"><span data-stu-id="86c2b-104">This can be done by implementing the <xref:System.ServiceModel.Description.IOperationContractGenerationExtension> interface on an operation behavior or implementing the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> interface on a contract behavior.</span></span> <span data-ttu-id="86c2b-105">Bu konuda nasıl uygulandığını gösterir <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> sözleşme davranışına arabirimi.</span><span class="sxs-lookup"><span data-stu-id="86c2b-105">This topic shows how to implement the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension> interface on a contract behavior.</span></span>  
  
 <span data-ttu-id="86c2b-106"><xref:System.ServiceModel.Description.ServiceContractGenerator> Hizmet sözleşmelerini, istemci türlerini ve istemci yapılandırmalardan üretir <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, ve <xref:System.ServiceModel.Channels.Binding> örnekleri.</span><span class="sxs-lookup"><span data-stu-id="86c2b-106">The <xref:System.ServiceModel.Description.ServiceContractGenerator> generates service contracts, client types, and client configurations from <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, and <xref:System.ServiceModel.Channels.Binding> instances.</span></span> <span data-ttu-id="86c2b-107">Genellikle, içeri aktardığınız <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, ve <xref:System.ServiceModel.Channels.Binding> örnekleri hizmeti meta verileri ve bu örnekleri hizmeti çağırmak için kodu oluşturmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="86c2b-107">Typically, you import <xref:System.ServiceModel.Description.ServiceEndpoint>, <xref:System.ServiceModel.Description.ContractDescription>, and <xref:System.ServiceModel.Channels.Binding> instances from service metadata and then use these instances to generate code to call the service.</span></span> <span data-ttu-id="86c2b-108">Bu örnekte, bir <xref:System.ServiceModel.Description.IWsdlImportExtension> uygulaması WSDL ek açıklamaları işlemek ve oluşturulan kodu açıklamalarını oluşturmak için içe aktarılan sözleşmeleri kod oluşturma uzantıları eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="86c2b-108">In this example, an <xref:System.ServiceModel.Description.IWsdlImportExtension> implementation is used to process WSDL annotations and then add code generation extensions to the imported contracts to generate comments on the generated code.</span></span>  
  
### <a name="to-write-an-extension-for-the-servicecontractgenerator"></a><span data-ttu-id="86c2b-109">ServiceContractGenerator için uzantıyazma için</span><span class="sxs-lookup"><span data-stu-id="86c2b-109">To write an extension for the ServiceContractGenerator</span></span>  
  
1.  <span data-ttu-id="86c2b-110">Uygulama <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>.</span><span class="sxs-lookup"><span data-stu-id="86c2b-110">Implement <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>.</span></span> <span data-ttu-id="86c2b-111">Oluşturulan hizmet sözleşmesi değiştirmek için <xref:System.ServiceModel.Description.ServiceContractGenerationContext> örnek geçirildi <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="86c2b-111">To modify the generated service contract, use the <xref:System.ServiceModel.Description.ServiceContractGenerationContext> instance passed into the <xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> method.</span></span>  
  
    ```  
    public void GenerateContract(ServiceContractGenerationContext context)  
    {  
        Console.WriteLine("In generate contract.");  
    context.ContractType.Comments.AddRange(Formatter.FormatComments(commentText));  
    }  
    ```  
  
2.  <span data-ttu-id="86c2b-112">Uygulama <xref:System.ServiceModel.Description.IWsdlImportExtension> aynı sınıfta.</span><span class="sxs-lookup"><span data-stu-id="86c2b-112">Implement <xref:System.ServiceModel.Description.IWsdlImportExtension> on the same class.</span></span> <span data-ttu-id="86c2b-113"><xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> Yöntemi, belirli bir WSDL uzantısı (Bu durumda ek açıklamalar WSDL) bir kod oluşturma uzantısı alınan ekleyerek işlenebilecek <xref:System.ServiceModel.Description.ContractDescription> örneği.</span><span class="sxs-lookup"><span data-stu-id="86c2b-113">The <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> method can process a specific WSDL extension (WSDL annotations in this case) by adding a code generation extension to the imported <xref:System.ServiceModel.Description.ContractDescription> instance.</span></span>  
  
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
  
3.  <span data-ttu-id="86c2b-114">WSDL alma istemci yapılandırmanıza ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86c2b-114">Add the WSDL importer to your client configuration.</span></span>  
  
    ```xml  
    <metadata>  
      <wsdlImporters>  
        <extension type="Microsoft.WCF.Documentation.WsdlDocumentationImporter, WsdlDocumentation" />  
      </wsdlImporters>  
    </metadata>  
    ```  
  
4.  <span data-ttu-id="86c2b-115">İstemci kodu oluşturmak bir `MetadataExchangeClient` ve arama `GetMetadata`.</span><span class="sxs-lookup"><span data-stu-id="86c2b-115">In the client code, create a `MetadataExchangeClient` and call `GetMetadata`.</span></span>  
  
    ```  
    MetadataExchangeClient mexClient = new MetadataExchangeClient(metadataAddress);  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet metaDocs = mexClient.GetMetadata();  
    ```  
  
5.  <span data-ttu-id="86c2b-116">Oluşturma bir `WsdlImporter` ve arama `ImportAllContracts`.</span><span class="sxs-lookup"><span data-stu-id="86c2b-116">Create a `WsdlImporter` and call `ImportAllContracts`.</span></span>  
  
    ```  
    WsdlImporter importer = new WsdlImporter(metaDocs);            System.Collections.ObjectModel.Collection<ContractDescription> contracts = importer.ImportAllContracts();  
    ```  
  
6.  <span data-ttu-id="86c2b-117">Oluşturma bir `ServiceContractGenerator` ve arama `GenerateServiceContractType` her sözleşme için.</span><span class="sxs-lookup"><span data-stu-id="86c2b-117">Create a `ServiceContractGenerator` and call `GenerateServiceContractType` for each contract.</span></span>  
  
    ```  
    ServiceContractGenerator generator = new ServiceContractGenerator();  
    foreach (ContractDescription contract in contracts)  
    {  
       generator.GenerateServiceContractType(contract);  
    }  
    if (generator.Errors.Count != 0)  
       throw new Exception("There were errors during code compilation.");  
    ```  
  
7.  <span data-ttu-id="86c2b-118"><xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29>Her sözleşme davranışı uygulayan belirli bir sözleşme için otomatik olarak adlandırılan <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>.</span><span class="sxs-lookup"><span data-stu-id="86c2b-118"><xref:System.ServiceModel.Description.IServiceContractGenerationExtension.GenerateContract%28System.ServiceModel.Description.ServiceContractGenerationContext%29> is called automatically for each contract behavior on a given contract that implements <xref:System.ServiceModel.Description.IServiceContractGenerationExtension>.</span></span> <span data-ttu-id="86c2b-119">Bu yöntem daha sonra değiştirebilirsiniz <xref:System.ServiceModel.Description.ServiceContractGenerationContext> geçirildi.</span><span class="sxs-lookup"><span data-stu-id="86c2b-119">This method can then modify the <xref:System.ServiceModel.Description.ServiceContractGenerationContext> passed in.</span></span> <span data-ttu-id="86c2b-120">Bu örnekte açıklamaları eklenir.</span><span class="sxs-lookup"><span data-stu-id="86c2b-120">In this example comments are added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86c2b-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="86c2b-121">See Also</span></span>  
 [<span data-ttu-id="86c2b-122">Meta veriler</span><span class="sxs-lookup"><span data-stu-id="86c2b-122">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)  
 [<span data-ttu-id="86c2b-123">Nasıl yapılır: özel WSDL içe aktarma</span><span class="sxs-lookup"><span data-stu-id="86c2b-123">How to: Import Custom WSDL</span></span>](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)
