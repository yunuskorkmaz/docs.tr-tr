---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: özel WSDL alma'
title: 'Nasıl yapılır: Özel WSDL İçeri Aktarma'
ms.date: 03/30/2017
ms.assetid: ddc3718d-ce60-44f6-92af-a5c67477dd99
ms.openlocfilehash: f21e5cace532bd6d20d409f297480f65bb23cbf4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780745"
---
# <a name="how-to-import-custom-wsdl"></a><span data-ttu-id="85c30-103">Nasıl yapılır: Özel WSDL İçeri Aktarma</span><span class="sxs-lookup"><span data-stu-id="85c30-103">How to: Import Custom WSDL</span></span>

<span data-ttu-id="85c30-104">Bu konu başlığı altında, özel WSDL 'nin nasıl içeri aktarılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="85c30-104">This topic describes how to import custom WSDL.</span></span> <span data-ttu-id="85c30-105">Özel WSDL 'yi işlemek için arabirimini uygulamanız gerekir <xref:System.ServiceModel.Description.IWsdlImportExtension> .</span><span class="sxs-lookup"><span data-stu-id="85c30-105">To handle the custom WSDL, you must implement the <xref:System.ServiceModel.Description.IWsdlImportExtension> interface.</span></span>  
  
### <a name="to-import-custom-wsdl"></a><span data-ttu-id="85c30-106">Özel WSDL 'yi içeri aktarmak için</span><span class="sxs-lookup"><span data-stu-id="85c30-106">To import custom WSDL</span></span>  
  
1. <span data-ttu-id="85c30-107">Uygulayın <xref:System.ServiceModel.Description.IWsdlImportExtension> .</span><span class="sxs-lookup"><span data-stu-id="85c30-107">Implement <xref:System.ServiceModel.Description.IWsdlImportExtension>.</span></span> <span data-ttu-id="85c30-108"><xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%28System.Web.Services.Description.ServiceDescriptionCollection%2CSystem.Xml.Schema.XmlSchemaSet%2CSystem.Collections.Generic.ICollection%7BSystem.Xml.XmlElement%7D%29>İçeri aktarmadan önce meta verileri değiştirmek için yöntemini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="85c30-108">Implement the <xref:System.ServiceModel.Description.IWsdlImportExtension.BeforeImport%28System.Web.Services.Description.ServiceDescriptionCollection%2CSystem.Xml.Schema.XmlSchemaSet%2CSystem.Collections.Generic.ICollection%7BSystem.Xml.XmlElement%7D%29> method to modify the metadata before it is imported.</span></span> <span data-ttu-id="85c30-109">Meta verilerden <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlEndpointConversionContext%29> <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> içeri aktarılan sözleşmeleri ve uç noktaları değiştirmek için ve yöntemlerini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="85c30-109">Implement the <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportEndpoint%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlEndpointConversionContext%29> and <xref:System.ServiceModel.Description.IWsdlImportExtension.ImportContract%28System.ServiceModel.Description.WsdlImporter%2CSystem.ServiceModel.Description.WsdlContractConversionContext%29> methods to modify contracts and endpoints imported from the metadata.</span></span> <span data-ttu-id="85c30-110">İçeri aktarılan sözleşmeye veya uç noktaya erişmek için, karşılık gelen bağlam nesnesini kullanın ( <xref:System.ServiceModel.Description.WsdlContractConversionContext> veya <xref:System.ServiceModel.Description.WsdlEndpointConversionContext> ):</span><span class="sxs-lookup"><span data-stu-id="85c30-110">To access the imported contract or endpoint, use the corresponding context object (<xref:System.ServiceModel.Description.WsdlContractConversionContext> or <xref:System.ServiceModel.Description.WsdlEndpointConversionContext>):</span></span>  
  
    ```csharp
    public class WsdlDocumentationImporter : IWsdlImportExtension
    {
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
    }
    ```
  
2. <span data-ttu-id="85c30-111">İstemci uygulamasını özel WSDL İçeri Aktarıcı kullanacak şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="85c30-111">Configure the client application to use the custom WSDL importer.</span></span> <span data-ttu-id="85c30-112">Svcutil.exe kullanıyorsanız, bu yapılandırmayı Svcutil.exe (Svcutil.exe.config) yapılandırma dosyasına eklemeniz gerektiğini unutmayın:</span><span class="sxs-lookup"><span data-stu-id="85c30-112">Note that if you are using Svcutil.exe, you should add this configuration to the configuration file for Svcutil.exe (Svcutil.exe.config):</span></span>  
  
    ```xml  
    <system.serviceModel>  
          <client>  
            <endpoint
              address="http://localhost:8000/Fibonacci"
              binding="wsHttpBinding"  
              contract="IFibonacci"  
            />  
            <metadata>  
              <wsdlImporters>  
                <extension type="Microsoft.WCF.Documentation.WsdlDocumentationImporter, WsdlDocumentation" />  
              </wsdlImporters>  
            </metadata>  
          </client>  
        </system.serviceModel>  
    ```  
  
3. <span data-ttu-id="85c30-113">Yeni bir <xref:System.ServiceModel.Description.WsdlImporter> örnek oluşturun ( <xref:System.ServiceModel.Description.MetadataSet> içeri aktarmak istediğiniz WSDL belgelerini içeren örneği geçirerek) ve şunu çağırın <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A> :</span><span class="sxs-lookup"><span data-stu-id="85c30-113">Create a new <xref:System.ServiceModel.Description.WsdlImporter> instance (passing in the <xref:System.ServiceModel.Description.MetadataSet> instance that contains the WSDL documents that you want to import), and call <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A>:</span></span>  
  
    ```csharp
    WsdlImporter importer = new WsdlImporter(metaDocs);
    System.Collections.ObjectModel.Collection<ContractDescription> contracts = importer.ImportAllContracts();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="85c30-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85c30-114">See also</span></span>

- [<span data-ttu-id="85c30-115">Meta veri</span><span class="sxs-lookup"><span data-stu-id="85c30-115">Metadata</span></span>](../feature-details/metadata.md)
- [<span data-ttu-id="85c30-116">Meta Verileri Dışarı ve İçeri Aktarma</span><span class="sxs-lookup"><span data-stu-id="85c30-116">Exporting and Importing Metadata</span></span>](../feature-details/exporting-and-importing-metadata.md)
- [<span data-ttu-id="85c30-117">Özel WSDL Yayımı</span><span class="sxs-lookup"><span data-stu-id="85c30-117">Custom WSDL Publication</span></span>](../samples/custom-wsdl-publication.md)
